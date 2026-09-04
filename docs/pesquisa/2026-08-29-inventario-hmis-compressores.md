# Evidência — inventário visual das IHMs dos compressores

- Data do registro: 2026-08-29
- Tipo: conjunto de artefatos operacionais + relato do operador
- Fonte: 12 fotografias de controladores locais dos compressores
- Sensibilidade: fotografias não incluídas no repositório

## Contexto do registro

Em 2026-08-29 foi registrado que existiam **12 compressores ativos nas salas** e foram analisadas 12 fotografias de telas locais. Neste registro, `ativo` significava pertencente ao inventário operacional; não significava necessariamente que o compressor estava funcionando no instante da fotografia. A contagem e a correspondência completa entre fotos e equipamentos precisam ser reconfirmadas devido à divergência do COMP-09.

A rota registrada também passa pelo COMP-07, que não foi fotografado porque se encontrava desmontado e em manutenção. O total histórico de 13 posições incluía uma foto atribuída ao COMP-09; por isso, a contagem atual permanece pendente até essa identificação ser validada.

As fotografias são evidência de interface e de diversidade dos equipamentos. Os valores mostrados são instantâneos e não foram usados para diagnosticar condição, desempenho ou segurança.

## O que foi confirmado

Foram observadas pelo menos três famílias de interface:

| Família provisória | Quantidade observada | Características visuais |
|---|---:|---|
| MYCOM legada, modelos de tela `MBR-2`/`MBR-4` | 5 | tela textual, teclado numérico e teclas de função |
| MAYEKAWA `CONTROL SYSTEM CPIV` | 5 | desenho gráfico do compressor, quadro lateral de variáveis e teclas físicas |
| MAYEKAWA `MYPRO TOUCH` | 2 | tela colorida sensível ao toque, desenho do compressor e quadros de variáveis |

## Relação das fotografias

| Ordem no conjunto | Compressor | Família observada | Confiança da identificação |
|---:|---|---|---|
| 1 | COMP-14 | MYCOM legada | identificação visível |
| 2 | COMP-13 | MYCOM legada | confirmado pelo operador |
| 3 | COMP-08 | CPIV | identificação visível |
| 4 | COMP-06 | MYPRO TOUCH | identificação manuscrita visível |
| 5 | COMP-05 | CPIV | identificação visível |
| 6 | identificação atribuída ao COMP-09 — **[PENDENTE]** | CPIV, tela com `COMP 52.8 Hz` | registro histórico; reconfirmar equipamento, sala e regime |
| 7 | COMP-04 | CPIV | identificação manuscrita visível |
| 8 | COMP-11 | MYCOM legada | identificação visível |
| 9 | COMP-10 | MYPRO TOUCH | identificação visível |
| 10 | COMP-15 | MYCOM legada | identificação visível |
| 11 | COMP-16 | MYCOM legada | identificação visível |
| 12 | COMP-01 | CPIV | confirmado pelo operador |

O compressor 7 não integra a tabela porque não foi fotografado. Ele está desmontado e seu estado operacional foi confirmado como manutenção.

A associação historicamente registrada entre salas, regimes e compressores está em [`2026-08-29-salas-regimes-e-classificacao-dos-compressores.md`](2026-08-29-salas-regimes-e-classificacao-dos-compressores.md), com a divergência do COMP-09 explicitada.

Também foi confirmado que:

- os COMP-04 e COMP-06 possuem inversor de frequência;
- a identificação da foto atribuída ao COMP-09 e a presença de inversor nesse equipamento permanecem pendentes;
- a presença de inversor nos demais compressores ainda é desconhecida;
- equipamentos do inventário podem estar parados no momento da ronda;
- algumas telas exibem mensagens ou estados como `STOPPED`, `MANUAL`, `NORMAL`, manutenção e alarme;
- telas CPIV e MYPRO TOUCH podem exibir a frequência do compressor em hertz quando aplicável;
- telas mais novas apresentam contadores de partidas/paradas e horas de funcionamento;
- as interfaces oferecem campos de pressões, temperaturas, corrente e posição/capacidade, mas usam conjuntos de siglas diferentes;
- algumas identificações indicam aplicações ou serviços diferentes, como `Amônia` e `Água Gelada`, cuja modelagem ainda precisa ser confirmada;
- os controladores exibem comandos locais, como partida, parada e limpeza de alarme. Isso **não** transforma o RefrigOps em sistema de controle.

## Vocabulário bruto observado

### MYCOM legada

```text
SP, DP, OP, OF, IP, MA, Pot., SH-SP, SH-DP,
ST, DT, OT, IT, OST, SV, set-point
```

### CONTROL SYSTEM CPIV

```text
COMP (Hz), SP, ST, SSH, DP, DT, DSH,
ΔOP/dOP, OP, OT, FP, AFP/BFP, OS, MA, LSV
```

Nem todas as siglas estavam presentes ou legíveis em todas as telas.

### MYPRO TOUCH

```text
SP, DP, OP, AFP, ST, DT, OT, dOP,
SVP, dFP, MA, LSV, COMP (Hz)
```

## Interpretação provisória

As três famílias parecem representar conceitos semelhantes com rótulos e agrupamentos diferentes. Por exemplo, pressão de sucção, pressão de descarga, pressão do óleo, temperatura do óleo, corrente, frequência e capacidade podem existir em mais de uma interface sem usar exatamente o mesmo nome.

Essa correspondência ainda precisa de manual ou validação técnica. A semelhança visual ou linguística não autoriza afirmar que duas siglas são equivalentes, que usam a mesma unidade ou que representam o mesmo ponto físico.

Uma consulta posterior a mapas oficiais da família MYPRO confirmou o significado de várias siglas desse grupo. As definições e os links estão registrados em [`2026-08-29-fontes-oficiais-controladores-mayekawa.md`](2026-08-29-fontes-oficiais-controladores-mayekawa.md). A compatibilidade com MBR-2, MBR-4 e CPIV permanece pendente.

## O que isto não prova

- significado oficial de cada sigla;
- unidade completa de cada campo — algumas telas abreviam pressão apenas como `kgf`;
- se a pressão apresentada é manométrica ou absoluta;
- correspondência exata entre todos os 12 equipamentos e a sequência das fotos;
- condição operacional correta ou incorreta dos equipamentos;
- existência, retenção ou confiabilidade de histórico interno;
- autorização ou viabilidade de comunicação digital com os controladores;
- que os comandos exibidos possam ou devam ser reproduzidos pelo RefrigOps.

## Impacto no produto

### Cadastro de equipamento

O cadastro poderá futuramente precisar de:

```text
fabricante
família/modelo do controlador
aplicação ou serviço
possui inversor
perfil de pontos aplicáveis à ronda
```

Esses campos são candidatos de descoberta, não requisitos aprovados para a API atual.

### Formulário de ronda

O formulário não deve presumir que todos os compressores possuem os mesmos campos. Um perfil por equipamento deve indicar:

- quais medições se aplicam;
- rótulo amigável usado pelo operador;
- sigla original exibida na fonte;
- unidade esperada;
- ordem de coleta;
- campo opcional, obrigatório ou indisponível;
- existência de inversor e leitura de frequência.

### Dicionário canônico de medições

O sistema deve distinguir:

```text
conceito canônico do RefrigOps
        ↕ mapeamento validado
rótulo bruto da IHM + modelo do controlador
```

Até a validação, o rótulo bruto e a origem devem ser preservados. O sistema não deve converter automaticamente siglas diferentes em uma única variável.

### Estados

É necessário separar:

```text
cadastro ativo/inativo do equipamento
estado operacional no instante da ronda
estado da coleta daquela medição
```

Um compressor ativo no inventário pode estar parado, em manutenção ou sem uma leitura aplicável. Esses conceitos não podem compartilhar um único campo.

### Limite de segurança

O RefrigOps permanece uma ferramenta de registro, consulta e apoio. A existência de botões de comando nas IHMs não autoriza controle remoto, alteração de setpoint, partida, parada, reconhecimento ou limpeza de alarmes pelo aplicativo.

## Perguntas abertas

1. Quais outros compressores são classificados como de alta, de baixa ou por outro regime?
2. `Amônia` e `Água Gelada` identificam serviço, circuito, regime ou outra classificação?
3. Quais siglas são usadas efetivamente para preencher cada linha do caderno?
4. O valor apresentado como `kgf` nas telas novas significa `kgf/cm²`?
5. O COMP-09 pertence ao inventário e possui inversor? Além dos COMP-04 e COMP-06, quais equipamentos possuem inversor?
6. Os contadores e eventos são consultados pela operação ou apenas pela manutenção?
7. Existem manuais e modelos exatos de cada controlador disponíveis para consulta autorizada?

## Próxima validação

- confirmar a classificação de estágio/regime dos demais compressores;
- montar uma matriz por compressor com sala, aplicação, controlador, inversor e campos do caderno;
- consultar documentação autorizada ou profissional experiente para validar siglas e unidades;
- observar uma ronda sem registrar valores sensíveis, relacionando cada linha do papel ao campo realmente lido na tela.
