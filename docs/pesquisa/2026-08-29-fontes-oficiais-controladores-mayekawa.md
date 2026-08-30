# Pesquisa técnica — fontes oficiais dos controladores Mayekawa

- Data da consulta: 2026-08-29
- Tipo: fonte técnica pública do fabricante
- Fabricante: Mayekawa / MYCOM
- Escopo: MYPRO TOUCH e materiais de integração relacionados
- Limite: os documentos encontrados não foram confirmados como manuais exatos de todos os controladores fotografados

## Fontes consultadas

1. [MAYEKAWA — Device List CP4 Area, MYPRO TOUCH+](https://americas.mayekawa.com/mna/downloads/pdf/CP%20Integration/MYPRO%20Touchplus/DEVICELISTCP4AREA.pdf)
2. [MAYEKAWA — Device List MYPRO TOUCH Area](https://americas.mayekawa.com/mna/downloads/pdf/CP%20Integration/MYPRO%20Touch/MYPROTOUCHDeviceListMYPROTouchAreaManual.pdf)
3. [MAYEKAWA — apresentação do painel MYPRO TOUCH em espanhol](https://americas.mayekawa.com/mpe/downloads/pdf/Automatizacion%20y%20Control/Panel%20Mypro%20Touch_ESP%202024.pdf)
4. [MAYEKAWA Global — ICT e especificações do MYPRO TOUCH](https://mayekawa.com/products/ict/)
5. [MAYEKAWA North America — ferramentas de integração](https://americas.mayekawa.com/mna/cpintegration/)

## Siglas confirmadas para a família MYPRO

Os documentos oficiais relacionam:

| Sigla | Nome em inglês no documento | Tradução de trabalho |
|---|---|---|
| `SP` | Suction Pressure | pressão de sucção |
| `DP` | Discharge Pressure | pressão de descarga |
| `OP` | Oil Supply Pressure | pressão de alimentação de óleo |
| `AFP` | After Filter Pressure | pressão após o filtro |
| `ST` | Suction Temperature | temperatura de sucção |
| `DT` | Discharge Temperature | temperatura de descarga |
| `OT` | Oil Supply Temperature | temperatura de alimentação de óleo |
| `IP` | Intermediate Pressure | pressão intermediária |
| `IT` | Intermediate Temperature | temperatura intermediária |
| `MA` | Compressor Motor Electric Current | corrente elétrica do motor do compressor |
| `LSV` | Low Stage Slide Valve Position | posição da válvula deslizante do estágio baixo |
| `SSH` | Suction Superheat | superaquecimento de sucção |
| `ISH` | Intermediate Superheat | superaquecimento intermediário |
| `DSH` | Discharge Superheat | superaquecimento de descarga |
| `dOP` | Oil Differential Pressure | pressão diferencial de óleo |
| `dFP` | Filter Differential Pressure | pressão diferencial do filtro |
| `CAP` | Capacity/VFD Output | capacidade/saída do inversor, conforme configuração |
| `SVP` | Slide Valve Percent | percentual da válvula deslizante |

O documento também descreve `OS` de formas dependentes de plataforma/configuração. Por isso, esse rótulo não deve receber um significado único no RefrigOps sem confirmar a versão do equipamento.

## Relações calculadas confirmadas

O documento do MYPRO TOUCH+ apresenta:

- `dFP` como diferença entre pressão de descarga e pressão após o filtro;
- `SSH` como superaquecimento de sucção;
- `DSH` como superaquecimento de descarga;
- uma variável específica para percentual da válvula deslizante;
- uma variável específica para capacidade ou saída do inversor.

A apresentação oficial também diferencia pressão, temperatura, amperagem, frequência, nível e capacidade de compressão. Portanto, frequência, capacidade e posição da válvula não devem ser tratadas como sinônimos.

## Setpoints e estados

O mapa oficial contém setpoints distintos para:

- entrada em operação (`cut-in`);
- controle de pressão;
- controle de temperatura;
- saída de operação (`cut-out`).

Isso demonstra que a palavra `setpoint`, sozinha, não identifica necessariamente uma única variável. O valor mostrado no caderno ou em uma tela específica só poderá ser nomeado após confirmar a configuração daquele controlador.

Também existem estados de operação mais detalhados do que apenas ligado/desligado, incluindo parada, anti-ciclo, parada automática, início de sequência, partida da bomba de óleo, pré-partida, funcionamento e recolhimento/pump-out. Esses estados são conhecimento útil, mas não serão copiados automaticamente para o modelo de domínio antes de validar quais são usados pela operação local.

## Histórico e comunicação

Fontes oficiais confirmam que a família MYPRO TOUCH pode oferecer:

- registro de dados em cartão SD;
- registro de falhas e alarmes;
- Ethernet;
- comunicação serial;
- Modbus;
- monitoramento por sistemas externos.

Os mapas de comunicação contêm pontos somente leitura e também pontos que permitem escrita/comando.

**Decisão de segurança:** a existência técnica de comunicação não significa autorização de acesso. Qualquer futura integração do RefrigOps deve ser aprovada por TI/OT e limitada, por arquitetura e credenciais, à leitura dos pontos necessários. O RefrigOps não deve escrever comandos, alterar setpoints, partir/parar equipamentos ou limpar alarmes.

## O que permanece sem confirmação

- manual exato do controlador MYCOM legado `MBR-2`/`MBR-4`;
- manual exato da interface identificada visualmente como `CONTROL SYSTEM CPIV`;
- versão de software e configuração de cada controlador fotografado;
- unidade completa exibida como `kgf` nas telas;
- tipo de pressão: manométrica ou absoluta;
- significado de `BFP`, `FP`, `OF`, `SH-SP`, `SH-DP`, `OST` e outros campos legados;
- qual setpoint aparece no cabeçalho do caderno;
- quais funções de histórico estão habilitadas nos equipamentos da planta;
- autorização para acesso a dados ou rede industrial.

## Impacto documental

- algumas siglas da família MYPRO deixam de ser apenas inferência;
- a família/modelo e a configuração continuam fazendo parte do contexto obrigatório;
- o aplicativo deve preservar sigla e unidade brutas;
- um mesmo nome canônico só deve reunir pontos com mapeamento validado;
- capacidade, frequência e posição da válvula devem permanecer conceitos separados;
- setpoint precisa registrar a variável-alvo e a vigência, não apenas um número;
- possibilidade de integração fica registrada como pesquisa futura, não como escopo do MVP.
