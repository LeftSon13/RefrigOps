# Contexto operacional

## 1. Finalidade

Este documento registra o conhecimento operacional que originou o RefrigOps. Ele não é procedimento de operação, manual de segurança nem especificação de engenharia.

As informações devem ser revisadas por pessoas responsáveis pela planta antes de virarem requisitos ou regras automáticas.

## 2. Ambiente descrito

**[CONFIRMADO — CONTEXTO OPERACIONAL]**

O contexto envolve refrigeração industrial com amônia R717. Foram mencionados:

- múltiplas salas de máquinas;
- compressores operando em diferentes condições;
- condensadores;
- recipientes de líquido, chamados informalmente de garrafas;
- bombas;
- IHM/sistema de supervisão;
- manômetros e instrumentos locais;
- sensores como PT100;
- rondas presenciais;
- registros manuais e passagem de turno.

O nível exato de instrumentação, automação e integração de cada equipamento ainda não está inventariado.

**[CONFIRMADO — RELATO E ARTEFATOS OPERACIONAIS]** O operador informou a existência de 12 compressores ativos no inventário atual das salas observadas. Um conjunto de 12 fotografias mostrou pelo menos três famílias de controlador local: MYCOM legada (`MBR-2`/`MBR-4`), MAYEKAWA `CONTROL SYSTEM CPIV` e MAYEKAWA `MYPRO TOUCH`.

Neste contexto, equipamento ativo não é sinônimo de equipamento funcionando. Algumas telas estavam paradas ou em outro estado no instante da fotografia.

## 3. Papel da ronda presencial

**[CONFIRMADO — CONTEXTO OPERACIONAL]**

A ronda não se resume a transcrever números. O operador percebe sinais que podem não existir na IHM ou não estar representados adequadamente:

- ruído incomum;
- vibração percebida;
- formação de gelo;
- temperatura e condição ambiente;
- nível e temperatura de óleo;
- estado de filtros;
- alarmes locais;
- vazamentos aparentes ou odores, sempre observados conforme procedimentos de segurança;
- condição visual de equipamentos e sala;
- comportamento geral comparado à experiência da equipe.

**[DECISÃO]** O produto deve preservar campos de observação qualitativa e ocorrência, em vez de aceitar somente números.

## 3.1 Fluxo observado de uma ronda de leitura

**[CONFIRMADO — CONTEXTO OPERACIONAL]**

O operador pega o caderno e percorre os equipamentos conforme o layout físico, não por ordem numérica:

```text
Sala 1: COMP-14 → COMP-13
Sala 2: COMP-08 → COMP-07 → COMP-06 → COMP-05 → COMP-04 → COMP-09
Sala 1: COMP-11 → COMP-10 → COMP-15 → COMP-16
Sala 2: COMP-01
Recipientes de amônia
Retorno à sala para consultar a tabela de pressão equivalente
```

**[CONFIRMADO — RELATO OPERACIONAL]** Essa sequência representa a rota completa atual dos compressores. Depois dela, o operador segue para os recipientes de amônia, chamados informalmente de garrafas, e lê um manômetro aplicável antes de consultar a tabela.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Foram relatados três regimes/aplicações, identificados como `-35 °C`, `-10 °C` e `-5 °C`. Esses valores são nomes operacionais de regime e não devem ser tratados automaticamente como temperatura instantânea, pressão ou setpoint.

| Regime | Classificação relatada | Sala 1 | Sala 2 |
|---|---|---|---|
| -35 °C | baixa | COMP-13 | COMP-08, COMP-07 e COMP-04 |
| -10 °C | alta | COMP-14 e COMP-11 | COMP-05, COMP-01 e COMP-09 |
| -5 °C | água gelada / ambiente | COMP-10, COMP-15 e COMP-16 | COMP-06 |

**[CONFIRMADO — RELATO OPERACIONAL]** O COMP-09 pertence ao regime de alta, correspondente a `-10 °C`.

**[CONFIRMADO — RELATO OPERACIONAL]** Os COMP-04, COMP-06 e COMP-09 possuem inversor de frequência. A existência de inversor nos demais compressores ainda não foi confirmada.

No grupo normalmente associado a `-5 °C`:

- COMP-15 e COMP-16 são exclusivos para água gelada;
- COMP-06 e COMP-10 normalmente atendem água gelada e ambiente;
- o COMP-06 pode ser direcionado exclusivamente para ambiente;
- o COMP-10 pode sair do atendimento de `-5 °C` e ajudar o regime de alta de `-10 °C`.

Também foi relatada uma interligação pela qual a rede de `-10 °C` pode ajudar a rede de `-5 °C`. O efeito percebido foi descrito como redução de carga e pressão nos compressores de `-5 °C`, com aumento de carga e pressão nos compressores de `-10 °C`. Isso é contexto operacional, não procedimento de manobra nem regra quantitativa validada.

Quando COMP-06 ou COMP-10 muda de atendimento, a configuração é registrada no **Caderno dos Turnos** para alertar a equipe seguinte e também informada verbalmente. O caderno de leituras contém somente os dados solicitados em sua folha.

O regime de `-5 °C` havia sido descrito anteriormente junto aos sistemas de alta em sentido amplo. A terminologia específica desse grupo ainda deve ser refinada; por enquanto ele é identificado como água gelada/ambiente.

Aplicações relatadas para o regime de `-35 °C` incluem túneis, girofreezer e câmaras de estocagem. Essas associações são contexto operacional e não substituem o inventário oficial das cargas frigoríficas.

Quando o compressor está ligado, os campos solicitados incluem:

- pressão de sucção;
- pressão de descarga;
- pressão do óleo;
- capacidade;
- corrente;
- frequência do inversor, quando existente.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Os valores numéricos dos compressores são consultados na HMI/controlador local. Nos equipamentos com inversor, o operador também registra a frequência de trabalho, com exemplos relatados de `40 Hz` e `60 Hz`.

O operador também observa, embora nem tudo seja registrado no quadro principal:

- nível de óleo pelo visor;
- temperatura do óleo na IHM;
- pressão do filtro de óleo;
- congelamento visual na sucção;
- condição térmica percebida do equipamento;
- erros ou alarmes exibidos;
- condição visual geral.

Portanto, mesmo que dados numéricos possam futuramente ser integrados, a presença física continua tendo finalidade para observações visuais, alarmes locais e condições não representadas pelos números.

**[DECISÃO DE PRODUTO]** O roteiro mobile deve acompanhar a rota física e permitir observações qualitativas, não apenas reproduzir a grade numérica do papel.

**[CONFIRMADO — RELATO OPERACIONAL]** A rota contém 13 posições, mas foram fotografados 12 compressores porque o COMP-07 está desmontado e em manutenção.

## 4. Fragmentação atual da informação

**[CONFIRMADO — CONTEXTO OPERACIONAL]**

As informações podem estar distribuídas entre:

- formulários ou folhas;
- IHM;
- manômetros e sensores locais;
- registros periódicos;
- relatos verbais;
- passagem de turno;
- conhecimento acumulado dos operadores;
- Caderno dos Turnos para acontecimentos, atividades realizadas e continuidade entre turnos.

**[HIPÓTESE]** Essa fragmentação pode dificultar pesquisa histórica, comparação entre turnos e reconstrução de eventos. Ainda é necessário mapear exemplos concretos, frequência e impacto.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Existe relato de que alguém transfere posteriormente as leituras do papel para um computador. Ainda não se sabe quem realiza a transcrição, qual sistema recebe os dados, por quanto tempo são guardados ou quem os consulta.

Um uso histórico foi confirmado por relato: equipes externas de manutenção de compressores já pediram o caderno para consultar como um equipamento estava trabalhando em determinada data.

## 5. Equipamentos e identificação

**[HISTÓRICO — CONVERSA]**

Foi proposta uma identificação estável por prefixo e número:

```text
COMP-13 → Compressor 13
COND-03 → Condensador 3
REC-01  → Recipiente 1
BOMB-02 → Bomba 2
```

**[DECISÃO]** O código serve ao sistema e ao histórico; a interface pode continuar mostrando nomes naturais usados pela equipe.

**[PENDENTE]** Confirmar:

- padrão oficial de identificação já existente na planta;
- diferenças entre tag de automação, número patrimonial e nome operacional;
- possibilidade de um equipamento mudar de sala ou função;
- ativos desativados e substituídos;
- relação entre equipamento físico e ponto de medição;
- fabricante e família/modelo do controlador local;
- aplicação ou serviço indicado na identificação, como amônia ou água gelada;
- presença de inversor nos compressores além de COMP-04, COMP-06 e COMP-09;
- conjunto de pontos aplicáveis a cada equipamento.
- regime/aplicação normalmente atendido;
- condições, autorizações, topologia e registro das interligações e mudanças de regime relatadas;
- significado preciso de alta e baixa em cada contexto.

## 5.1 Substituição e eventos operacionais

**[RELATO OPERACIONAL]** Foram citados eventos como desarme, solicitação de eletricista, retirada de operação, substituição temporária por outro compressor e retorno à condição normal.

Um exemplo histórico relatado foi:

```text
COMP-07 parado aguardando eletricista
→ COMP-08 colocado em operação como substituição
→ COMP-07 posteriormente normalizado
```

Esse fluxo reforça a necessidade de histórico de estado, ocorrências e relação de substituição. Ele não constitui procedimento operacional nem autorização para o RefrigOps comandar equipamentos.

## 6. Recipientes de amônia

**[CONFIRMADO — CONTEXTO OPERACIONAL]**

- Foram relatados cinco recipientes de amônia.
- Quatro possuíam manômetro no contexto observado.
- Nem todos ficam em uso ao mesmo tempo.
- Alguns podem estar evacuados.
- Em certos períodos, apenas dois recipientes podem estar em operação por condição de inventário de amônia.

**[PENDENTE]** O significado operacional de “em uso”, “evacuado”, “isolado”, “desativado” e “em manutenção” precisa ser formalizado com estados, transições e responsáveis.

## 7. Pressões observadas

**[CONFIRMADO — CONTEXTO OPERACIONAL]**

Foram citados:

- Pressão de Saída do Condensador 3 na IHM;
- Pressão de Descarga Geral na IHM;
- manômetros locais dos recipientes;
- pressão equivalente obtida por tabela em função de temperatura.

A Pressão de Descarga Geral foi descrita como relacionada à descarga dos compressores de alta. A relação exata, agregação e posição do transmissor precisam ser confirmadas no diagrama e na instrumentação.

**[DIVERGÊNCIA NO RELATO HISTÓRICO]** Em um momento ela foi descrita como média das descargas dos compressores de alta; posteriormente foi associada à pressão observável em um recipiente/manômetro. Não assumir que seja média aritmética. Pode se tratar de um ponto comum do lado de alta, mas isso exige confirmação técnica.

**[RELATO OPERACIONAL]** A `Pressão de Saída do Condensador 3` é usada localmente como referência da pressão de condensação. A equivalência exata entre nome operacional, posição do sensor e grandeza termodinâmica permanece pendente.

## 8. Temperaturas observadas

**[CONFIRMADO — CONTEXTO OPERACIONAL]**

Foram descritas duas fontes diferentes:

1. escala de temperatura de NH₃ impressa no manômetro;
2. PT100 posicionado externamente próximo ao visor de líquido.

A primeira é uma conversão da própria pressão para temperatura de saturação equivalente, não uma medição independente. A segunda é fisicamente independente, mas sua montagem pode não representar a temperatura real do fluido.

## 9. Passagem de turno

A passagem de turno foi identificada como oportunidade de produto: consolidar estado, ocorrências, equipamentos indisponíveis, anomalias e pendências.

**[CONFIRMADO — RELATO OPERACIONAL]** Mudanças de atendimento dos COMP-06 e COMP-10 são anotadas no Caderno dos Turnos e também comunicadas verbalmente. O caderno de leituras não é utilizado para relatos livres ou ocorrências.

**[CONFIRMADO — RELATO OPERACIONAL]** O conteúdo verbal da passagem não é uniforme e varia conforme o operador. Alguns operadores comunicam somente quando ocorreu uma quebra ou quando não conseguiram resolver uma situação durante o próprio turno.

**[CONFIRMADO — RELATO OPERACIONAL]** O turno seguinte consulta o Caderno dos Turnos sem registrar assinatura, visto ou confirmação de leitura.

**[CONFIRMADO — RELATO OPERACIONAL]** Existe um registro separado do caderno de leituras, chamado pela equipe de Caderno dos Turnos. Nele são anotados a data, sem horário, e os nomes esperados dos operadores presentes. Acontecimentos e atividades são registrados em texto livre, em linhas comuns. Ainda não foi confirmado se os nomes são preenchidos consistentemente.

Exemplos relatados de anotações incluem conferência das Salas 1 e 2, degelo em câmaras e lavagem de condensadores. São exemplos de registro, não procedimentos definidos pelo RefrigOps.

Quando uma anotação permanece pendente e é resolvida depois, a anotação original é preservada. Em uma linha posterior, os operadores citam o problema e destacam que ele foi corrigido ou resolvido.

Quando uma atividade é adiada, os operadores anotam uma nova data. Geralmente, o mesmo turno continua responsável, mas a existência de possíveis exceções ainda precisa ser validada.

Foram relatadas falhas de comunicação em dois tipos de situação:

- uma atividade atribuída a um turno futuro pode ser esquecida e precisar ser adiada;
- uma restrição operacional anotada com antecedência para uma data futura pode perder visibilidade quando a data chega.

Um exemplo citou a expressão operacional “fazer vazio” no COMP-09. O significado técnico não foi interpretado. Outro exemplo tratou de não ligar um compressor em determinada data. O RefrigOps pode apoiar registro, validade e confirmação de ciência, mas não pode decidir, bloquear, liberar ou comandar o equipamento.

**[HIPÓTESE]** Um resumo estruturado poderia reduzir perda de contexto. O restante do processo atual ainda precisa ser observado e descrito sem suposições, inclusive o conteúdo que fica apenas na comunicação verbal.

**[DECISÃO DE PRODUTO]** A passagem de turno é considerada mais adequada à interface desktop, enquanto a coleta durante a ronda é prioridade mobile. Essa preferência ainda precisa ser validada com outros operadores.

Perguntas de descoberta:

- quem prepara e quem recebe a passagem?
- existe formulário oficial?
- quais informações são obrigatórias?
- o que costuma ser dito verbalmente e não registrado?
- como são tratadas pendências de manutenção?
- como registrar ciência do turno seguinte sem confundir ciência com execução?
- como tarefas futuras são atribuídas e confirmadas, e em quais exceções o turno responsável muda no reagendamento?
- como restrições com data de validade permanecem visíveis para o turno correto?

## 10. Usuários e ergonomia

**[HISTÓRICO — CONVERSA]**

Foi demonstrada preocupação com simplicidade e com operadores de diferentes idades e níveis de familiaridade digital.

**[HIPÓTESE]** O uso pode ocorrer em celular ou dispositivo móvel durante a ronda e em tela maior para consulta e supervisão.

Aspectos a validar:

- conectividade nas salas;
- uso de luvas;
- iluminação;
- ruído e impossibilidade de usar áudio;
- necessidade de operação offline;
- tamanho mínimo de texto e alvos de toque;
- tempo aceitável por registro;
- idioma, termos e abreviações reais;
- autenticação em dispositivo compartilhado.

## 11. Primeiro piloto recomendado

**[HIPÓTESE]** Escolher uma área pequena e conhecida:

- uma sala;
- um turno;
- poucos equipamentos;
- um conjunto curto de verificações;
- um período limitado;
- acompanhamento direto do usuário.

O piloto deve medir clareza e aderência antes de ampliar o modelo.

## 11.1 Formulário atual de monitoramento

**[CONFIRMADO — ARTEFATO OPERACIONAL]** Uma fotografia analisada em 2026-08-29 mostrou o formulário “Monitoramento de Compressores Sala 01 e 02 — DIA”. A imagem não foi adicionada ao repositório por conter marca, identificação documental e dados reais.

Estrutura confirmada:

- mesma folha usada durante o turno, sem versão separada para noite;
- um lado contém parte dos compressores e o verso contém os demais;
- colunas horárias fixas de `00:00` a `23:00`;
- linhas agrupadas por compressor e parâmetro;
- valor de `SETP.` no cabeçalho de alguns compressores;
- área para não conformidade, causa, correção, ações e responsável;
- área de identificação/execução no rodapé.

Prática relatada:

- campos de compressor desligado ficam vazios;
- leitura não realizada também deve ficar vazia;
- a área de não conformidade e ação nunca foi vista preenchida pelo operador consultado;
- identificação ou assinatura do executor não é usada na prática;
- `SETP.` significa setpoint, mas ainda não se sabe qual variável/unidade ele representa;
- a frequência esperada na sala é horária, resultando em cerca de sete ou oito rondas por turno;
- outra sala da mesma unidade aparentemente realiza aproximadamente três rondas por turno;
- técnicos de refrigeração e supervisão definiram historicamente a prática;
- não foi localizado ainda um procedimento escrito nem a justificativa técnica da periodicidade.

### Ambiguidade crítica do campo vazio

No papel, o mesmo vazio pode significar:

```text
compressor desligado
ou
leitura não realizada
ou
leitura ainda pendente
```

**[DECISÃO DE PRODUTO]** O aplicativo deve registrar estados distintos e preservar lacunas. Não deve inventar medições para preencher horários ausentes.

### Aplicativo anterior

**[RELATO OPERACIONAL]** Operadores antigos informaram que as leituras já foram feitas por celular. O aplicativo foi abandonado sem motivo conhecido pela equipe atual. Nome, fornecedor, plataforma, dados e causa da descontinuação permanecem pendentes.

## 12. O que falta observar

- fluxo completo de uma ronda real;
- formulário atual e campos obrigatórios;
- periodicidade e exceções;
- tipos de anomalia e prioridade;
- passagem de turno;
- nomenclatura oficial dos equipamentos;
- unidades e resolução dos instrumentos;
- responsabilidades e aprovações;
- tratamento de indisponibilidade do sistema;
- quais dados podem ser registrados sem expor informações sensíveis.
