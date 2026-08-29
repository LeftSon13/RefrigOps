# Medições, unidades e fontes

## 1. Objetivo

Impedir que números de origens e unidades diferentes sejam comparados ou apresentados como equivalentes sem contexto.

## 2. Regra central

**[DECISÃO]** Toda medição futura deve preservar, quando aplicável:

- valor original;
- unidade original;
- fonte;
- instrumento ou tag;
- instante da medição;
- instante do registro;
- responsável pelo registro;
- conversão aplicada;
- método e versão de cálculo;
- qualidade, observação ou incerteza.

## 3. Fontes observadas

### IHM

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Apresenta valores como Pressão de Saída do Condensador 3 e Pressão de Descarga Geral. Foi confirmado verbalmente que os valores observados estavam em bar.

Existem pelo menos duas categorias de interface:

1. IHM/supervisão da sala, com variáveis gerais;
2. HMI/controlador local de cada compressor, usada durante a ronda.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Os dados numéricos anotados para os compressores são retirados do controlador local. A frequência de equipamentos com inversor é registrada em hertz, com exemplos de `40 Hz` e `60 Hz`.

### Tela de controlador de compressor observada

**[CONFIRMADO — ARTEFATO OPERACIONAL]** Uma fotografia analisada em 2026-08-29 mostrou uma tela com horário/data, estado `RUNNING`, condição `NORMAL`, modo `Auto-Local`, setpoint e diversas siglas.

Valores/unidades legíveis no exemplo:

| Sigla/tela | Exemplo observado | Interpretação provisória |
|---|---:|---|
| `set-point` | `1.95` | referência de controle; variável/unidade a confirmar |
| `SP` | `2.10 kgf/cm²` | provavelmente pressão de sucção |
| `DP` | `9.47 kgf/cm²` | provavelmente pressão de descarga |
| `OP` | `2.87 kgf/cm²` | provavelmente pressão do óleo |
| `OF` | `0.20` | provavelmente parâmetro de filtro de óleo; unidade/definição a confirmar |
| `IP` | sem valor | significado a confirmar |
| corrente | `319` | unidade não legível; relato indica corrente |
| `Pot.` | `207.0` | potência; unidade não confirmada na foto |
| `SH-SP` | `11.8 °C` | sigla/definição a confirmar |
| `SH-DP` | `81.4 °C` | sigla/definição a confirmar |
| `ST` | `-2.7 °C` | provavelmente temperatura de sucção |
| `DT` | `66.9 °C` | provavelmente temperatura de descarga |
| `OT` | `40.6 °C` | provavelmente temperatura do óleo |
| `IT` | sem valor | significado a confirmar |
| `OST` | sem valor | significado a confirmar |
| `SV` | `99.6 %` | provavelmente capacidade/posição de válvula deslizante |

As expansões das siglas são inferências usuais e **não devem virar contrato definitivo** sem manual do controlador, documentação do fabricante ou validação de profissional experiente.

### Diversidade dos controladores locais

**[CONFIRMADO — ARTEFATOS OPERACIONAIS]** O inventário visual de 12 compressores mostrou pelo menos três famílias de interface:

| Família provisória | Rótulos observados |
|---|---|
| MYCOM legada `MBR-2`/`MBR-4` | `SP`, `DP`, `OP`, `OF`, `IP`, `MA`, `Pot.`, `SH-SP`, `SH-DP`, `ST`, `DT`, `OT`, `IT`, `OST`, `SV` |
| MAYEKAWA `CONTROL SYSTEM CPIV` | `COMP`, `SP`, `ST`, `SSH`, `DP`, `DT`, `DSH`, `ΔOP/dOP`, `OP`, `OT`, `FP`, `AFP/BFP`, `OS`, `MA`, `LSV` |
| MAYEKAWA `MYPRO TOUCH` | `COMP`, `SP`, `DP`, `OP`, `AFP`, `ST`, `DT`, `OT`, `dOP`, `SVP`, `dFP`, `MA`, `LSV` |

Essa tabela registra somente o texto visível. Ela **não afirma equivalência técnica** entre rótulos de famílias diferentes.

Uma futura definição de ponto de medição deve preservar:

```text
canonicalConcept     → conceito validado usado pelo RefrigOps
sourceLabel          → sigla exatamente como aparece na IHM
controllerFamily     → família/modelo que dá contexto à sigla
rawUnit              → unidade exatamente apresentada
sourceReference      → equipamento e tela de origem
mappingStatus        → provisório ou validado
```

**[PENDENTE CRÍTICO]** Algumas telas recentes abreviam a unidade de pressão como `kgf`. Confirmar por manual ou documentação da planta se isso representa `kgf/cm²` antes de normalizar ou comparar os valores.

### Significados confirmados em documentação oficial MYPRO

**[CONFIRMADO — FONTE DO FABRICANTE]** Mapas de dispositivos da Mayekawa para a família MYPRO relacionam:

| Sigla | Significado confirmado para essa família |
|---|---|
| `SP` | pressão de sucção |
| `DP` | pressão de descarga |
| `OP` | pressão de alimentação de óleo |
| `AFP` | pressão após o filtro |
| `ST` | temperatura de sucção |
| `DT` | temperatura de descarga |
| `OT` | temperatura de alimentação de óleo |
| `IP` / `IT` | pressão / temperatura intermediária |
| `MA` | corrente elétrica do motor do compressor |
| `LSV` | posição da válvula deslizante do estágio baixo |
| `SSH` / `ISH` / `DSH` | superaquecimento de sucção / intermediário / descarga |
| `dOP` | pressão diferencial de óleo |
| `dFP` | pressão diferencial do filtro |
| `CAP` | capacidade ou saída do inversor, conforme configuração |
| `SVP` | percentual da válvula deslizante |

Essas definições foram confirmadas para os documentos MYPRO consultados. Elas não devem ser copiadas automaticamente para MBR-2, MBR-4 ou CPIV sem confirmar compatibilidade de modelo e versão.

**[CONFIRMADO — FONTE DO FABRICANTE]** A família MYPRO diferencia variáveis de frequência, capacidade e posição da válvula. Também pode disponibilizar estados detalhados, registro de dados, alarmes e comunicação. A presença do recurso no produto não confirma que ele esteja configurado ou autorizado na planta.

Consulte o registro de fontes em [`pesquisa/2026-08-29-fontes-oficiais-controladores-mayekawa.md`](pesquisa/2026-08-29-fontes-oficiais-controladores-mayekawa.md).

### Frequência do inversor

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Quando o compressor possui inversor, o operador anota a frequência efetiva de funcionamento em hertz. Esse valor é diferente da capacidade percentual e do setpoint.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Os COMP-04, COMP-06 e COMP-09 possuem inversor de frequência. A presença de inversor nos demais compressores ainda não foi confirmada.

### Manômetro local

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Mede pressão nos recipientes. Os mostradores fotografados tinham escala de pressão em kgf/cm² e escala de temperatura equivalente da NH₃.

### PT100 externo

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Instalado externamente próximo ao visor de líquido de um recipiente. Produz leitura, mas sua representatividade térmica é duvidosa.

### Tabela pressão × temperatura

**[HISTÓRICO — CONVERSA]** Tabela operacional que relaciona temperatura da amônia e pressão equivalente.

### Formulário legado

**[HISTÓRICO — CONVERSA]** Recebia valores digitados e apresentava um “Percentual de Ar”. O significado e a validade metrológica não estão confirmados.

## 4. Pressão e temperatura de saturação

Para uma substância pura em equilíbrio, pressão e temperatura de saturação estão relacionadas.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Exemplos lidos na tabela fotografada:

```text
29,0 °C → 10,32 kgf/cm²
31,3 °C → 11,12 kgf/cm²
```

Esses exemplos não devem virar tabela oficial do software sem confirmar fonte, edição, arredondamento e tipo de pressão.

## 5. Escala de NH₃ do manômetro

**[DECISÃO DE INTERPRETAÇÃO]** A escala em °C do manômetro não representa um segundo sensor. Ela converte a pressão medida para temperatura de saturação correspondente à NH₃.

```text
pressão medida
     ├── escala de pressão
     └── escala equivalente de temperatura NH3
```

Logo, pressão e temperatura lidas do mesmo ponteiro não são duas observações independentes para validar uma condição termodinâmica.

## 6. Unidades de pressão

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Houve mistura entre valores da IHM em bar e campos/tabela em kgf/cm².

Conversões matemáticas:

```text
1 kgf/cm² = 0,980665 bar
1 bar     ≈ 1,019716 kgf/cm²
```

Mesmo sendo numericamente próximas, não são intercambiáveis.

## 7. Pressão manométrica e absoluta

**[PENDENTE CRÍTICO]** Confirmar se cada fonte representa:

- pressão manométrica, relativa à atmosfera;
- pressão absoluta;
- outra convenção interna do sistema.

Comparações termodinâmicas podem exigir pressão absoluta. O software não deve assumir conversão sem conhecer altitude/pressão atmosférica, convenção da tabela e instrumento.

## 8. Fórmula inferida do formulário

Pelos números históricos, foi reproduzida:

```text
percentual aparente =
  (pressão do recipiente - pressão equivalente)
  / pressão equivalente
  × 100
```

Exemplo:

```text
(10,00 - 9,90) / 9,90 × 100 ≈ 1,01%
```

**[DECISÃO]** Isso prova apenas qual conta pode ter gerado o número. Não prova que o resultado seja a fração real de ar ou de não condensáveis.

## 9. Viés no dado de entrada

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Foi relatado que um valor podia ser digitado de modo a produzir aproximadamente 1% no formulário.

Consequência:

```text
resultado desejado
      ↓
entrada ajustada
      ↓
fórmula devolve o resultado desejado
```

Esse procedimento não mede independentemente a condição.

## 10. Não condensáveis — hipótese física

**[HIPÓTESE TÉCNICA]** Diferenças entre pressão real do lado de alta e pressão de saturação esperada para uma temperatura independentemente medida podem indicar condição que merece investigação.

Isso depende de:

- ponto e instante das medições;
- equilíbrio térmico;
- representatividade da temperatura;
- unidades e convenção de pressão;
- composição;
- erro dos instrumentos;
- condição operacional;
- procedimento técnico adotado.

Não converter essa hipótese em regra operacional sem validação especializada.

## 11. Modelo de dados recomendado

Exemplo conceitual:

| Campo | Exemplo | Motivo |
|---|---|---|
| `rawValue` | `10.10` | preserva leitura |
| `rawUnit` | `BAR_GAUGE` | evita ambiguidade |
| `sourceType` | `HMI` | informa origem |
| `sourceRef` | `Saída Condensador 3` | identifica tag/ponto |
| `measuredAt` | instante | separa leitura de digitação |
| `recordedAt` | instante | auditoria |
| `recordedBy` | operador | autoria |
| `normalizedValue` | valor convertido | comparação |
| `normalizedUnit` | unidade canônica | consistência |
| `conversionMethod` | versão | rastreabilidade |
| `quality` | `UNVERIFIED` | explicita confiança |
| `notes` | texto | contexto |

## 12. Estados de qualidade possíveis

**[HIPÓTESE]**

```text
OBSERVED
UNVERIFIED
SUSPECT
ESTIMATED
CALCULATED
INVALIDATED
```

Os nomes precisam ser traduzidos para a linguagem da operação e definidos antes do uso.

## 13. Perguntas pendentes

- referência completa da tabela de NH₃;
- calibração e classe dos manômetros;
- tags da IHM e unidades oficiais;
- natureza da Pressão de Descarga Geral;
- posição e montagem do PT100;
- frequência e simultaneidade das leituras;
- pressão absoluta ou manométrica;
- política de arredondamento;
- procedimento oficial sobre não condensáveis;
- dados que podem ser usados apenas para registro e os que podem acionar alertas.
- todos os significados e unidades das siglas do controlador local;
- existência de histórico interno no controlador;
- existência de interface de comunicação e autorização para consulta somente leitura;
- localização e rótulo exatos da leitura de frequência nos COMP-04, COMP-06 e COMP-09;
- existência de inversor nos demais compressores.
- relação validada entre siglas de MYCOM legada, CPIV e MYPRO TOUCH;
- significado da unidade abreviada `kgf` nas telas recentes;
- perfil de medições aplicável a cada compressor.
- manual e versão exatos dos controladores MBR-2, MBR-4 e CPIV observados;
- quais recursos de histórico e comunicação estão habilitados e autorizados localmente.

## 14. Referências operacionais por regime

**[RELATO OPERACIONAL]** Para o regime de `-35 °C`, foi mencionada sucção negativa próxima de `-10`. Para o regime de `-10 °C`, foi mencionada sucção positiva aproximadamente entre `1,9` e `2,4`. Para o regime de `-5 °C`, foi mencionada sucção positiva aproximadamente entre `2,9` e `3,4`.

Esses números permanecem sem unidade e sem classificação como valor típico, setpoint ou limite. Não devem ser convertidos, comparados ou usados em alerta até confirmar:

- unidade;
- pressão manométrica ou absoluta;
- ponto de medição;
- condição operacional;
- finalidade da referência;
- fonte técnica aprovada.

**[QUALIDADE DA EVIDÊNCIA]** O operador informou que valores recuperados de celular/fotografias durante a descoberta não eram totalmente exatos. Eles ajudam a compreender sinal e ordem de grandeza, mas não devem configurar setpoints, limites ou alertas.
