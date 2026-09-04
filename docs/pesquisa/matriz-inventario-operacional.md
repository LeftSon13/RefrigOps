# Matriz de inventário operacional dos compressores

- Data da consolidação: 2026-08-29
- Tipo: síntese de relatos operacionais e evidências visuais
- Escopo: compressores percorridos na ronda das Salas de Máquinas 1 e 2
- Responsável pela validação operacional: pendente
- Sensibilidade: resumo sanitizado; fotografias e valores instantâneos não estão incluídos

## Objetivo

Consolidar, em uma única visão, o que já é conhecido sobre cada compressor e tornar as lacunas explícitas antes de transformar o conhecimento operacional em cadastro, regra de software ou formulário digital.

Esta matriz não é cadastro patrimonial, diagrama frigorífico, procedimento de operação nem autorização para manobras.

## Como interpretar a matriz

Os campos usam quatro classificações:

| Classificação | Significado |
|---|---|
| Confirmado por relato | informação fornecida diretamente pelo operador |
| Observado em fotografia | informação visível no conjunto de imagens, sem diagnóstico do equipamento |
| Fonte técnica | informação sustentada por documento do fabricante já registrado |
| Pendente | informação que ainda precisa de validação humana ou documental |

Também é necessário separar três conceitos:

```text
pertence ao inventário operacional
≠ estado instantâneo ligado/parado
≠ disponibilidade para coleta
```

Existem 13 compressores classificados neste inventário operacional. O COMP-07 estava desmontado e em manutenção no momento do registro. O responsável pelo projeto confirmou o COMP-09 na Sala de Máquinas 2, no regime de `-10 °C`, como compressor de alta.

## Matriz consolidada

| Ordem na ronda | Equipamento | Sala | Regime/aplicação relatada | Situação conhecida no inventário | Estado operacional confirmado | Família de IHM observada | Ordem da foto | Evidência de frequência/inversor | Validações pendentes principais |
|---:|---|---|---|---|---|---|---:|---|---|
| 1 | COMP-14 | Sala 1 | -10 °C — alta | ativo no inventário | não registrado | MYCOM legada | 1 | não confirmada | inversor; modelo exato; dedicação ao regime |
| 2 | COMP-13 | Sala 1 | -35 °C — baixa | ativo no inventário | não registrado | MYCOM legada | 2 | não confirmada | inversor; modelo exato; dedicação ao regime |
| 3 | COMP-08 | Sala 2 | -35 °C — baixa | ativo no inventário | não registrado | CPIV | 3 | não confirmada | inversor; modelo exato; dedicação ao regime |
| 4 | COMP-07 | Sala 2 | -35 °C — baixa | indisponível para a ronda no registro | manutenção; desmontado | não fotografada | — | não confirmada | IHM; inversor; motivo/categoria da manutenção; dedicação ao regime |
| 5 | COMP-06 | Sala 2 | normalmente -5 °C — água gelada/ambiente; pode ficar exclusivo para ambiente | ativo no inventário | não registrado | MYPRO TOUCH | 4 | inversor confirmado pelo operador | modelo exato; condições e vigência da atribuição ao serviço |
| 6 | COMP-05 | Sala 2 | -10 °C — alta | ativo no inventário | não registrado | CPIV | 5 | não confirmada | inversor; modelo exato; dedicação ao regime |
| 7 | COMP-04 | Sala 2 | -35 °C — baixa | ativo no inventário | não registrado | CPIV | 7 | inversor confirmado pelo operador | modelo exato; dedicação ao regime |
| 8 | COMP-09 | Sala 2 | -10 °C — alta | ativo no inventário | não registrado | CPIV | 6 | inversor confirmado pelo operador | modelo exato; dedicação ao regime |
| 9 | COMP-11 | Sala 1 | -10 °C — alta | ativo no inventário | não registrado | MYCOM legada | 8 | não confirmada | inversor; modelo exato; dedicação ao regime |
| 10 | COMP-10 | Sala 1 | normalmente -5 °C — água gelada/ambiente; pode ajudar o regime de -10 °C | ativo no inventário | não registrado | MYPRO TOUCH | 9 | não confirmada | inversor; modelo exato; condições e vigência da mudança de regime |
| 11 | COMP-15 | Sala 1 | -5 °C — exclusivo para água gelada | ativo no inventário | não registrado | MYCOM legada | 10 | não confirmada | inversor; modelo exato; dedicação física a confirmar documentalmente |
| 12 | COMP-16 | Sala 1 | -5 °C — exclusivo para água gelada | ativo no inventário | não registrado | MYCOM legada | 11 | não confirmada | inversor; modelo exato; dedicação física a confirmar documentalmente |
| 13 | COMP-01 | Sala 2 | -10 °C — alta | ativo no inventário | não registrado | CPIV | 12 | não confirmada | inversor; modelo exato; dedicação ao regime |

### Observações sobre a coluna de frequência

A presença de inversor permanece confirmada no contexto atual para:

- COMP-04;
- COMP-06;
- COMP-09.

Para os demais compressores, essa informação permanece desconhecida. Nos três equipamentos com inversor confirmado, ainda precisa ser verificado se:

- o valor corresponde à frequência efetiva do motor principal;
- essa é a mesma leitura anotada no caderno;
- o campo está disponível em todas as condições de funcionamento.

## Perfil mínimo da ronda relatado

Quando um compressor está ligado, a planilha solicita:

| Conceito usado pelo operador | Fonte relatada | Unidade conhecida | Aplicabilidade atual |
|---|---|---|---|
| pressão de sucção | controlador local | pendente por família/tela | compressores ligados |
| pressão de descarga | controlador local | pendente por família/tela | compressores ligados |
| pressão do óleo | controlador local | pendente por família/tela | compressores ligados |
| capacidade | controlador local | percentual relatado; significado exato por controlador pendente | compressores ligados |
| corrente | controlador local | ampère relatado; apresentação por controlador pendente | compressores ligados |
| frequência | controlador local | hertz | somente quando houver inversor e o campo for aplicável |

Os campos de equipamento desligado permanecem em branco na prática relatada. Uma leitura não realizada também deve permanecer em branco. O sistema futuro precisa registrar motivos diferentes para essas ausências sem inventar valores.

## Inspeções complementares relatadas

Além das linhas numéricas do caderno, o operador observa durante a ronda:

- nível do óleo pelo visor;
- temperatura do óleo na IHM;
- condição ou pressão do filtro de óleo;
- quantidade e distribuição de gelo na sucção;
- percepção de compressor quente ou frio;
- erros ou alarmes exibidos;
- sons anormais;
- funcionamento de bombas;
- comportamento geral da sala.

Essas observações ainda não formam um checklist aprovado. Elas devem ser validadas antes de se tornarem campos obrigatórios, opções rápidas ou gatilhos de alerta.

## Relação provisória entre o caderno e as IHMs

| Conceito do caderno | MYCOM legada — rótulo candidato | CPIV — rótulo candidato | MYPRO TOUCH — rótulo confirmado para a família | Estado do mapeamento |
|---|---|---|---|---|
| pressão de sucção | `SP` | `SP` | `SP` | confirmado apenas para MYPRO; validar legada e CPIV |
| pressão de descarga | `DP` | `DP` | `DP` | confirmado apenas para MYPRO; validar legada e CPIV |
| pressão do óleo | `OP` | `OP` | `OP` | MYPRO define pressão de alimentação de óleo; validar significado local e demais famílias |
| capacidade | `SV` | `LSV` ou outro campo | `SVP`, `LSV`, `CAP` ou configuração equivalente | pendente; não tratar os rótulos como equivalentes |
| corrente | `MA` | `MA` | `MA` | confirmado para MYPRO; validar legada e CPIV |
| frequência | campo a confirmar | `COMP (Hz)` quando exibido | `COMP (Hz)` ou configuração equivalente | confirmar por equipamento e versão |
| condição do filtro de óleo | `OF` — significado pendente | `FP`, `AFP/BFP` ou diferencial — relação pendente | `AFP` e `dFP` possuem definições da família | pendente por tela e prática local |
| temperatura do óleo | `OT` | `OT` | `OT` | confirmado para MYPRO; validar legada e CPIV |

Este quadro serve para orientar a entrevista e a observação. Rótulos parecidos não provam que o ponto físico, a escala, a unidade ou a semântica sejam iguais.

## Aplicações conhecidas por regime

| Regime | Classificação operacional relatada | Aplicações relatadas | Compressores |
|---|---|---|---|
| -35 °C | baixa | túneis, girofreezer e câmaras de estocagem | 13, 8, 7 e 4 |
| -10 °C | alta | cargas menos frias que o regime de -35 °C; pode receber ajuda do COMP-10 em configuração relatada | 14, 11, 5, 1 e 9 normalmente; COMP-10 em atribuição alternativa |
| -5 °C | água gelada/ambiente | COMP-15 e COMP-16 exclusivos para água gelada; COMP-06 e COMP-10 normalmente atendem água gelada e ambiente | 10, 15, 16 e 6 na configuração normal relatada |

Os nomes dos regimes são classificações operacionais. Não representam automaticamente temperatura instantânea, temperatura de evaporação, pressão de sucção ou setpoint.

## Flexibilidade e interligação relatadas

Foi confirmado pelo operador que a associação ao regime não é inteiramente fixa:

- o COMP-06 pode ser direcionado exclusivamente para ambiente;
- o COMP-10 pode sair do atendimento de `-5 °C` e ajudar os compressores de alta no regime de `-10 °C`;
- existe uma interligação pela qual a rede de `-10 °C` pode ajudar a rede de `-5 °C`.

O efeito operacional relatado dessa interligação é reduzir carga e pressão nos compressores de `-5 °C` e aumentar carga e pressão nos compressores de `-10 °C`.

Esse relato confirma a necessidade de atribuições com vigência no histórico, mas não define sequência de manobra, condições de autorização, limites seguros nem relação física quantitativa. Esses elementos exigem procedimento e validação técnica da instalação.

Quando COMP-06 ou COMP-10 muda de atendimento, a mudança é anotada no **Caderno dos Turnos** para alertar a equipe seguinte e também é comunicada verbalmente. O caderno de leituras não recebe esse tipo de anotação.

## Limite da rota de compressores

A rota dos compressores contém 13 posições classificadas. Depois do COMP-01, a ronda segue para os recipientes de amônia, chamados informalmente de garrafas, onde é feita a leitura de um manômetro aplicável.

## Lacunas que impedem uma modelagem definitiva

### Por equipamento

- fabricante e modelo completo do compressor;
- modelo e versão exatos do controlador;
- presença de inversor nos compressores além de COMP-04, COMP-06 e COMP-09;
- serviço ou carga atendida individualmente;
- campos realmente aplicáveis na ronda;
- unidades exibidas em cada tela;
- identificação oficial/patrimonial permitida para o projeto;
- estado normal, limites e alarmes oficiais — somente com fonte técnica autorizada.

### Da instalação

- quais compressores, além do COMP-06 e do COMP-10, podem mudar de atribuição;
- topologia, condições autorizadas e registro das interligações relatadas;
- significado oficial de `-35 °C`, `-10 °C` e `-5 °C` na planta;
- diferença local entre “alta”, “baixa”, “água gelada” e “ambiente”;
- unidades e convenção manométrica/absoluta das referências de sucção;
- consumidor, finalidade e retenção dos dados transcritos do papel para o computador.

## Perguntas para a próxima validação

### Ao operador

1. Além dos COMP-04, COMP-06 e COMP-09, algum outro compressor possui inversor de frequência?
2. Em cada compressor com inversor, qual campo da IHM é copiado para o caderno?
3. No caderno, “capacidade” corresponde a qual sigla em cada uma das três famílias de IHM?

### Aos operadores experientes, técnicos ou supervisão

1. Quais condições, autorizações e registros se aplicam à mudança de atendimento dos COMP-06 e COMP-10?
2. Qual é a topologia e a finalidade oficial da interligação entre as redes de `-10 °C` e `-5 °C`?
3. Outros compressores também podem mudar de regime ou serviço?
4. O que os nomes `-35 °C`, `-10 °C` e `-5 °C` representam oficialmente?
5. Quais são as unidades das referências de sucção e elas são manométricas ou absolutas?
6. As referências relatadas são valores típicos, setpoints operacionais ou limites?
7. O `SETP.` impresso no caderno corresponde a qual variável, unidade e período de validade?
8. Quem recebe a transcrição no computador e para quais decisões ou relatórios ela é usada?

## Impacto possível no produto

A futura modelagem deve permitir, sem fixar decisões prematuras:

```text
equipamento físico
├── localização
├── perfil de controlador
├── perfil de medições aplicáveis
├── configuração de inversor
├── atribuição a regime/aplicação com vigência
├── estado operacional observado
└── estado da coleta
```

A matriz não autoriza implementar esses campos agora. Ela organiza a descoberta necessária para que uma Issue futura tenha escopo e regras verificáveis.

## Evidências relacionadas

- [Caderno de monitoramento e relato da ronda](2026-08-29-caderno-monitoramento-e-ronda.md)
- [Inventário visual das IHMs](2026-08-29-inventario-hmis-compressores.md)
- [Salas, regimes e classificação dos compressores](2026-08-29-salas-regimes-e-classificacao-dos-compressores.md)
- [Fontes oficiais dos controladores Mayekawa](2026-08-29-fontes-oficiais-controladores-mayekawa.md)
