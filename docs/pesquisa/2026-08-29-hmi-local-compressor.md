# Evidência — HMI local de compressor

- Data do registro: 2026-08-29
- Tipo: artefato operacional + relato do usuário
- Fonte: fotografia do controlador local e explicação do operador
- Sensibilidade: fotografia não incluída no repositório

## O que foi confirmado

- os dados numéricos anotados durante a ronda são retirados da HMI/controlador local;
- equipamentos com inversor têm a frequência de trabalho registrada em hertz;
- foram fornecidos exemplos de `40 Hz` e `60 Hz`;
- a tela observada exibe estado, condição, horário/data, setpoint, pressões, temperaturas e outros parâmetros.

## Valores visíveis no exemplo

```text
set-point 1.95
SP 2.10 kgf/cm²
DP 9.47 kgf/cm²
OP 2.87 kgf/cm²
ST -2.7 °C
DT 66.9 °C
OT 40.6 °C
SV 99.6 %
```

Outras siglas visíveis: `OF`, `IP`, `SH-SP`, `SH-DP`, `IT`, `OST` e `Pot.`.

## Interpretação provisória

Com base em nomenclatura usual, `SP`, `DP` e `OP` provavelmente correspondem às pressões de sucção, descarga e óleo. `ST`, `DT` e `OT` provavelmente correspondem às temperaturas de sucção, descarga e óleo. `SV` pode representar a posição/capacidade da válvula deslizante.

Essas interpretações não foram confirmadas por manual ou profissional experiente.

O valor do setpoint próximo ao `SP` e aos setpoints impressos no caderno sugere relação com pressão de sucção, mas isso permanece hipótese.

## O que isto não prova

- significado oficial das siglas;
- unidade de todos os campos;
- que todos os compressores usem o mesmo controlador;
- existência de histórico interno;
- possibilidade ou autorização de integração;
- qualidade/calibração dos sensores;
- que a frequência esteja nesta mesma tela.

## Impacto no produto

- registrar `LOCAL_HMI` como origem da medição;
- manter unidade explícita por variável;
- não confundir frequência, capacidade e setpoint;
- preservar inspeção visual mesmo com futura integração;
- investigar se dados digitais podem ser consultados de forma somente leitura;
- mapear modelos de controlador antes de desenhar integração.

## Próxima validação

Consultar manual/legenda do controlador ou operador/técnico experiente para confirmar siglas, unidades, histórico e significado do setpoint.
