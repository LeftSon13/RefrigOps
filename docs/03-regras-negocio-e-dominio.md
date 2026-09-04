# Regras de negócio e domínio

## 1. Escopo

Este documento separa:

- comportamento confirmado no código;
- decisões de modelagem;
- hipóteses de domínio;
- regras que ainda exigem validação operacional.

## 2. Glossário provisório

| Termo | Significado atual | Evidência |
|---|---|---|
| Equipamento | Ativo cadastrado no RefrigOps | Confirmado no código |
| Compressor | Tipo de equipamento | Confirmado no enum |
| Recipiente / Receiver | Tipo de equipamento; chamado informalmente de garrafa | Código + relato operacional |
| Condensador | Tipo de equipamento | Confirmado no enum |
| Ronda | Percurso/verificação presencial da operação | Relato operacional; ainda não modelado |
| Leitura | Valor observado com contexto e unidade | Hipótese de domínio; ainda não modelado |
| Ocorrência | Evento/anomalia relevante à operação | Histórico de conversa; ainda não modelado |
| Passagem de turno | Transferência de contexto entre equipes | Relato operacional; ainda não modelado |
| IHM | Interface que apresenta sinais do processo | Relato operacional |
| Perfil de coleta | Conjunto de medições aplicáveis a um equipamento/controlador | Proposta a partir do inventário visual; não implementado |
| PT100 | Sensor resistivo de temperatura | Relato operacional |
| Não condensáveis | Gases presentes no lado de alta que não condensam nas condições do sistema | Tema em investigação |

## 3. Agregado atual: Equipment

**[CONFIRMADO — REPOSITÓRIO]**

Campos:

```text
id
code
name
type
status
active
location
```

### Identidade

- `id` é gerado pelo banco;
- `code` é obrigatório e único no banco;
- ainda não existe validação de formato do código no Java.

### Tipo

Valores confirmados:

```text
COMPRESSOR
RECEIVER
CONDENSER
```

### Estado

Valores confirmados:

```text
RUNNING
STOPPED
MAINTENANCE
EVACUATED
DEACTIVATED
```

**[PENDENTE]** Esses estados foram modelados, mas ainda não existe definição formal de:

- significado de cada um;
- quem pode alterá-los;
- transições permitidas;
- diferença entre `DEACTIVATED` e `active = false`;
- aplicação de `EVACUATED` somente a recipientes ou a qualquer equipamento;
- registro do histórico de estado.
- critérios gerais de entrada e saída de manutenção e possibilidade de retorno à operação.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** O COMP-07 está fisicamente desmontado e foi classificado pela operação como `MAINTENANCE`. Esse caso valida o uso de manutenção para um equipamento desmontado, mas não define sozinho todas as condições que levam a esse estado.

### Ativo no cadastro × estado operacional

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Os 12 compressores foram descritos como ativos, embora alguns estivessem parados no instante das fotografias.

**[DECISÃO DE MODELAGEM PROPOSTA]** Separar três dimensões:

```text
active           → pertence ou não ao inventário vigente
operatingStatus  → condição operacional em determinado instante
collectionStatus → resultado da tentativa de coleta de um ponto
```

O campo atual `status` ainda não possui histórico temporal e não deve ser tratado como substituto automático do estado observado durante uma ronda.

## 4. Regras confirmadas na criação

**[CONFIRMADO — REPOSITÓRIO]**

Ao criar equipamento:

- `code` não pode ser nulo, vazio ou somente espaços;
- `name` não pode ser nulo, vazio ou somente espaços;
- `type` deve ser informado;
- `location` não pode ser nula, vazia ou somente espaços;
- `status` é definido como `STOPPED` pelo Service;
- `active` é definido como `true` pelo Service;
- o equipamento é persistido;
- código duplicado viola a restrição única do banco.

## 5. Regras ainda não implementadas

**[PENDENTE]**

- normalização de espaços;
- tamanho máximo validado na API;
- formato de `code`;
- tratamento amigável de código duplicado;
- alteração de dados cadastrais;
- desativação sem apagar histórico;
- busca por código;
- paginação e ordenação;
- estados e transições;
- auditoria de alterações;
- associação a sala/local estruturado.

## 6. Localização

**[CONFIRMADO — REPOSITÓRIO]** `location` é texto livre.

**[HIPÓTESE]** A localização pode evoluir para entidade ou value object se existirem regras próprias, hierarquia de planta ou necessidade de evitar variações como `Sala 1`, `sala 1` e `SALA-01`.

Não realizar essa alteração sem inventário dos locais reais e casos de uso.

## 7. Ronda — modelo provisório

**[HIPÓTESE]** Um modelo inicial pode conter:

```text
Round
├── id
├── area/location
├── scheduledAt
├── startedAt
├── finishedAt
├── operator
├── status
├── entries
└── notes
```

Possíveis estados:

```text
PLANNED → IN_PROGRESS → COMPLETED
                    └→ INTERRUPTED
```

Nenhum desses nomes ou fluxos está aprovado.

O fluxo observado exige separar três instantes:

```text
scheduledAt → horário previsto na grade
measuredAt  → horário real da observação
recordedAt  → horário em que o dado entrou no sistema
```

No papel atual existe somente a coluna de horário previsto. O sistema não deve presumir que uma anotação na coluna `10:00` foi realmente medida às `10:00`.

Perguntas obrigatórias antes de implementar:

- a ronda é definida por sala, roteiro, turno ou horário?
- pode haver mais de um operador?
- uma ronda pode ser concluída parcialmente?
- quem pode corrigir uma leitura?
- como funciona atraso ou impossibilidade de acesso?
- existe assinatura ou conferência?
- o que é obrigatório e o que é opcional?

## 8. Leitura — modelo provisório

**[DECISÃO DE MODELAGEM PROPOSTA]** Nunca armazenar apenas um número quando sua interpretação depende de contexto.

Uma leitura futura pode precisar de:

```text
Measurement
├── id
├── equipmentId / measurementPointId
├── measuredAt
├── recordedAt
├── recordedBy
├── rawValue
├── rawUnit
├── normalizedValue
├── normalizedUnit
├── origin
├── instrument
├── quality/status
├── calculationMethod/version
└── notes
```

Origens possíveis, ainda não aprovadas:

```text
MANUAL_LOCAL_INSTRUMENT
MANUAL_HMI
SENSOR_IMPORT
CALCULATED
LEGACY_FORM
```

Estados de coleta necessários a partir do processo observado:

```text
MEASURED
EQUIPMENT_STOPPED
NOT_APPLICABLE
COULD_NOT_MEASURE
NOT_PERFORMED
RECORDED_LATE
```

Os nomes e transições precisam ser traduzidos e validados. O requisito é semântico: compressor desligado e leitura não realizada não podem continuar indistinguíveis.

### Setpoint

**[CONFIRMADO — ARTEFATO OPERACIONAL]** O formulário apresenta `SETP.` por compressor. Foi confirmado que significa setpoint.

**[PENDENTE]** Identificar:

- variável controlada;
- unidade;
- origem do valor;
- quem pode alterá-lo;
- validade temporal;
- se é configuração fixa ou muda com o regime operacional.

**[DECISÃO DE MODELAGEM PROPOSTA]** Setpoint é referência/configuração, não leitura do operador. Se puder mudar, deve ter período de vigência para permitir interpretar corretamente o histórico.

Uma fotografia do controlador mostrou `set-point: 1.95` e, na mesma tela, `SP 2.10 kgf/cm²`. Como o formulário traz setpoints próximos associados aos compressores, existe uma **inferência forte**, ainda não confirmada, de que o setpoint se relaciona à pressão de sucção. Manual, legenda oficial ou operador experiente deve confirmar variável e unidade.

### Fonte dos dados do compressor

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Os valores numéricos registrados na ronda são lidos na HMI/controlador local do compressor. Isso deve ser modelado como fonte distinta de manômetro, sensor importado ou observação visual.

```text
sourceType: LOCAL_HMI
sourceReference: controlador do compressor
```

Nos compressores com inversor, a frequência é registrada em hertz. A presença de inversor foi confirmada operacionalmente para COMP-04 e COMP-06; a afirmação sobre o COMP-09 e os demais equipamentos permanece pendente.

### Perfis diferentes de controlador

**[CONFIRMADO — ARTEFATOS OPERACIONAIS]** Foram observadas pelo menos três famílias de interface entre os 12 compressores fotografados. Elas exibem conjuntos e rótulos diferentes para variáveis semelhantes.

**[DECISÃO DE MODELAGEM PROPOSTA]** Uma futura ronda não deve usar uma lista rígida e idêntica de campos para todos os compressores. Cada equipamento poderá referenciar um perfil de coleta com pontos aplicáveis, rótulo usado pelo operador, sigla bruta da IHM e unidade esperada.

O mapeamento entre sigla bruta e conceito canônico só poderá ser considerado válido depois de confirmação por manual, documentação técnica autorizada ou profissional experiente.

Campos futuros candidatos no cadastro, ainda não aprovados:

```text
manufacturer
controllerFamily
applicationOrService
compressionStageOrRegime
hasVariableFrequencyDrive
measurementProfile
```

**[PENDENTE — DIVERGÊNCIA OPERACIONAL]** O pacote documental de 2026-08-29 associou o COMP-09 ao regime de alta de `-10 °C`, mas o contexto fornecido na revisão de 2026-09-03 não contém esse equipamento. A associação não deve orientar modelagem enquanto existência, sala e regime não forem confirmados.

### Regime e atribuição operacional

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Foram relatadas associações entre compressores e regimes `-35 °C`, `-10 °C` e `-5 °C`. A lista confirmada nesta revisão não inclui o COMP-09; sua associação histórica ao regime de `-10 °C` permanece pendente.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** COMP-15 e COMP-16 são exclusivos para água gelada. COMP-06 e COMP-10 normalmente atendem água gelada e ambiente, mas podem receber atribuições diferentes: COMP-06 exclusivo para ambiente e COMP-10 ajudando o regime de alta de `-10 °C`. Também foi relatada interligação entre as redes de `-10 °C` e `-5 °C`.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** A mudança de atendimento dos COMP-06 e COMP-10 é registrada no Caderno dos Turnos e também comunicada verbalmente. O caderno de leituras contém somente os dados solicitados na folha.

**[DECISÃO DE MODELAGEM]** Não transformar as associações de regime diretamente em atributo permanente e imutável de `Equipment`. A flexibilidade relatada exige separar o equipamento de sua atribuição operacional e preservar vigência e motivo. As condições técnicas e autorizações das mudanças ainda precisam ser validadas.

Conceitos candidatos, ainda não aprovados:

```text
OperatingRegime
EquipmentRegimeAssignment
validFrom / validUntil
assignmentReason
assignedService
```

O nome de regime, sua temperatura de referência e a atribuição do equipamento são conceitos distintos.

O histórico futuro da atribuição deve permitir que o turno seguinte identifique qual configuração permanece vigente. Isso não significa substituir automaticamente a comunicação verbal antes de mapear quais informações adicionais são transmitidas por ela.

## 9. Ocorrências e anomalias

**[HIPÓTESE]** Uma ocorrência deve ser separada de uma leitura fora de faixa. Pode registrar observação qualitativa, severidade provisória, equipamento relacionado, horário, responsável e ação tomada.

**[PENDENTE]** Antes de modelar, mapear:

- categorias reais;
- quem classifica severidade;
- diferença entre ocorrência, alarme, defeito e ordem de manutenção;
- integrações com processos existentes;
- exigências de retenção e auditoria.

Exemplos reais relatados para descoberta incluem parada aguardando eletricista, substituição temporária por outro compressor e posterior normalização. O histórico deve permitir reconstruir a sequência sem sobrescrever o estado anterior.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Existe um registro separado do caderno de leituras, chamado Caderno dos Turnos, com data sem horário e nomes esperados dos operadores presentes. O que aconteceu e o que foi realizado são escritos em texto livre, em linhas comuns. O caderno dá continuidade da informação para os turnos seguintes.

Exemplos relatados incluem conferência das salas, degelo em câmaras e lavagem de condensadores. Esses exemplos representam atividades registradas, não regras ou procedimentos do sistema.

**[DECISÃO DE MODELAGEM]** Medição periódica, ocorrência, atividade realizada e pendência de turno não devem ser representadas como um único tipo de registro.

**[DECISÃO DE MODELAGEM]** O formulário digital de leitura não deve receber campos livres de ocorrência apenas por conveniência. A ligação entre uma leitura e uma ocorrência deve ser explícita, preservando os dois registros como conceitos separados.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Quando uma pendência é resolvida, a anotação inicial permanece. Em uma linha posterior, os operadores citam o problema e destacam a correção ou resolução.

**[DECISÃO DE MODELAGEM]** Resolver uma pendência deve acrescentar um novo evento relacionado ao registro anterior e identificar o problema resolvido. O sistema deve preservar o texto e o estado históricos em vez de sobrescrever silenciosamente a anotação original.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** O turno seguinte consulta o Caderno dos Turnos sem registrar confirmação de leitura. Foram relatados esquecimento de atividade atribuída a turno futuro e perda de visibilidade de restrição válida para uma data posterior.

**[DECISÃO DE MODELAGEM]** Anotação, tarefa futura e restrição operacional não devem ser o mesmo conceito. Uma tarefa pode precisar de turno responsável, data e estado. Uma restrição pode precisar de origem, vigência e confirmação de ciência. Esses campos são candidatos de descoberta, não autorização para implementar controle de equipamento.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Uma atividade adiada recebe uma nova data. Assim, `ADIADA` deve preservar o histórico do compromisso anterior e produzir um novo agendamento relacionado, sem ser confundida com `CONCLUÍDA` ou `CANCELADA`. Geralmente, o turno responsável é mantido. A modelagem não deve tornar essa permanência obrigatória enquanto possíveis exceções não forem validadas.

## 10. Passagem de turno

**[CONFIRMADO — CONTEXTO OPERACIONAL]** O conteúdo da passagem verbal varia conforme o operador. Alguns comunicam apenas quebras ou situações que não conseguiram resolver no turno.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** O Caderno dos Turnos funciona como fonte escrita para os turnos seguintes acompanharem acontecimentos e atividades realizadas.

**[HIPÓTESE]** A futura passagem de turno deve ser uma visão derivada de ocorrências, equipamentos indisponíveis, rondas pendentes e observações, evitando duplicação manual. Antes de definir campos obrigatórios, é necessário validar com outros operadores e supervisão quais informações realmente precisam atravessar todos os turnos.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Atualmente não existe confirmação registrada de leitura pelo turno seguinte.

**[HIPÓTESE]** Uma futura confirmação de ciência pode reduzir ambiguidade, mas não comprova execução e não substitui procedimentos ou comunicação verbal exigida.

## 11. Não condensáveis

**[DECISÃO]** Não existe regra de negócio aprovada para calcular percentual real de ar.

O formulário histórico e a fórmula inferida podem ser documentados como prática observada, nunca como diagnóstico validado.

Qualquer feature relacionada exige:

- método técnico aprovado;
- pontos de medição definidos;
- unidades normalizadas;
- pressão absoluta/manométrica esclarecida;
- temperatura independente e representativa;
- condições de equilíbrio conhecidas;
- validação com engenharia e procedimento da planta;
- linguagem de interface que não induza certeza falsa.

## 12. Eventos de domínio futuros

**[HIPÓTESE]** Eventos que podem se tornar relevantes:

```text
EquipmentRegistered
EquipmentStatusChanged
RoundStarted
MeasurementRecorded
AnomalyReported
RoundCompleted
ShiftHandoverAcknowledged
```

Não implementar event sourcing ou mensageria apenas por essa lista. Os nomes ajudam a compreender comportamentos, não prescrevem arquitetura.
