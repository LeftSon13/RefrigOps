# Evidência — salas, regimes e classificação dos compressores

- Data do registro: 2026-08-29
- Tipo: contexto operacional reapresentado e confirmado pelo usuário
- Fonte: conversas anteriores do projeto RefrigOps
- Sensibilidade: resumo sanitizado; sem valores instantâneos, pessoas ou detalhes de rede

## Limite desta evidência

Esta classificação representa o conhecimento operacional relatado. Ela ainda não foi confrontada com cadastro patrimonial, fluxograma frigorífico, P&ID, manual de operação ou documentação oficial da instalação.

As expressões `-35 °C`, `-10 °C` e `-5 °C` são usadas como nomes de regimes/aplicações. Elas não devem ser interpretadas automaticamente como:

- temperatura medida no compressor;
- temperatura instantânea da câmara;
- temperatura de evaporação comprovada;
- pressão de sucção;
- setpoint único e imutável.

## Organização conhecida

Foram relatadas pelo menos duas salas de máquinas:

- Sala de Máquinas 1;
- Sala de Máquinas 2.

## Regime de -35 °C

Classificação operacional relatada: **baixa temperatura / sistema de baixa**.

Aplicações relatadas: túneis, girofreezer e câmaras de estocagem.

| Sala | Compressores associados |
|---|---|
| Sala 1 | COMP-13 |
| Sala 2 | COMP-08, COMP-07 e COMP-04 |

O COMP-07 está desmontado e em manutenção no momento deste registro.

Foi mencionada sucção negativa próxima de `-10`, mas a unidade, o tipo de pressão e a faixa oficial não foram confirmados. Esse número não deve virar limite ou regra automática.

## Regime de -10 °C

Classificação operacional relatada: **regime de alta**, atendendo cargas menos frias que o regime de -35 °C.

| Sala | Compressores associados |
|---|---|
| Sala 1 | COMP-14 e COMP-11 |
| Sala 2 | COMP-05, COMP-01 e COMP-09 |

O COMP-10, normalmente associado ao regime de `-5 °C`, pode ser direcionado para ajudar os compressores de alta no regime de `-10 °C`. Isso representa uma atribuição operacional alternativa, não a associação normal mostrada na tabela.

Foi mencionada sucção positiva aproximadamente entre `1,9` e `2,4`, mas a unidade, o tipo de pressão e o caráter da faixa — típico, desejado ou limite — permanecem pendentes.

## Regime de -5 °C

Aplicações relatadas:

- água gelada;
- climatização/ambiente;
- outras necessidades de refrigeração de temperatura mais elevada.

Foi anteriormente descrito junto aos sistemas de alta em sentido amplo, mas a resposta operacional mais específica identifica o **regime de alta como -10 °C**. Por isso, `-5 °C` permanece documentado principalmente como água gelada/ambiente até refinarmos a terminologia.

| Sala | Compressores associados |
|---|---|
| Sala 1 | COMP-10, COMP-15 e COMP-16 |
| Sala 2 | COMP-06 |

Funções relatadas nesse grupo:

- COMP-15 e COMP-16 são exclusivos para água gelada;
- COMP-06 e COMP-10 normalmente atendem água gelada e ambiente;
- por meio de manobras autorizadas da instalação, o COMP-06 pode ficar exclusivo para ambiente;
- o COMP-10 pode sair do regime de `-5 °C` e ajudar o regime de alta de `-10 °C`.

Foi mencionada sucção positiva aproximadamente entre `2,9` e `3,4`, mas sua unidade e seu significado como faixa típica, setpoint ou limite não foram confirmados.

## Interligação entre as redes de -10 °C e -5 °C

Foi relatada a existência de uma interligação que permite à rede de `-10 °C` ajudar a rede de `-5 °C`.

O efeito operacional percebido foi descrito como:

- redução da carga e da pressão nos compressores de `-5 °C`;
- aumento da carga e da pressão nos compressores de `-10 °C`.

Este registro documenta a percepção operacional, mas não estabelece causalidade quantitativa, sequência de manobra, limite, setpoint ou procedimento. A topologia, as condições de uso e as autorizações precisam ser confirmadas em documentação técnica e procedimento da instalação.

## COMP-09 — classificação confirmada

O COMP-09 foi confirmado como **compressor do regime de alta**, correspondente ao regime de `-10 °C`. Ele fica na Sala de Máquinas 2 conforme a rota observada.

## Visão consolidada do que possui regime identificado

| Regime | Classificação relatada | Sala | Compressores |
|---|---|---|---|
| -35 °C | baixa | Sala 1 | 13 |
| -35 °C | baixa | Sala 2 | 8, 7 e 4 |
| -10 °C | alta | Sala 1 | 14 e 11 |
| -10 °C | alta | Sala 2 | 5, 1 e 9 |
| -5 °C | água gelada / ambiente | Sala 1 | 10, 15 e 16 |
| -5 °C | água gelada / ambiente | Sala 2 | 6 |

## Inspeção além dos números

Além das leituras do controlador, foram relatadas observações de:

- condição e distribuição de gelo na sucção;
- percepção de equipamento quente ou frio;
- nível e temperatura do óleo;
- condição ou pressão do filtro de óleo;
- alarmes;
- sons anormais;
- funcionamento de bombas;
- comportamento geral da sala.

Esses elementos reforçam que telemetria futura não substitui automaticamente a ronda presencial.

## Exemplos de eventos operacionais relatados

Foram citadas ações e acontecimentos como:

- adicionar óleo quando necessário, seguindo o procedimento da planta;
- acompanhar temperatura do óleo;
- trocar filtro;
- solicitar eletricista após desarme;
- retirar equipamento de operação;
- colocar outro compressor como substituto;
- registrar retorno à condição normal.

Exemplo histórico de sequência:

```text
COMP-07 parado aguardando eletricista
→ COMP-08 colocado em operação como substituição
→ COMP-07 posteriormente normalizado
```

Esse exemplo demonstra a necessidade futura de histórico de estado e ocorrências, mas não define procedimento operacional nem autoriza ações pelo RefrigOps.

## Impacto na modelagem futura

Não criar imediatamente uma propriedade fixa como:

```text
equipment.regime = MINUS_35
```

O relato sobre COMP-06, COMP-10 e a interligação entre `-10 °C` e `-5 °C` confirma que pelo menos parte da associação pode mudar ao longo da operação. Ainda é necessário validar tecnicamente quais outras atribuições são possíveis.

Uma modelagem mais flexível pode precisar distinguir:

```text
equipamento físico
regime/aplicação
atribuição do equipamento ao regime
vigência da atribuição
estado operacional
ocorrência e substituição
```

Essa estrutura é apenas direção de descoberta, não decisão de implementação.

## Perguntas abertas

1. O regime de -5 °C recebe apenas o nome água gelada/ambiente ou também é chamado de alta em algum contexto?
2. Quais outros compressores podem mudar de regime ou serviço?
3. Quais condições e autorizações governam as atribuições alternativas dos COMP-06 e COMP-10?
4. Qual é a topologia e a finalidade oficial da interligação entre `-10 °C` e `-5 °C`?
5. Qual é a unidade da sucção negativa próxima de `-10`?
6. Qual é a unidade da faixa `1,9` a `2,4`?
7. Qual é a unidade da faixa `2,9` a `3,4`?
8. Essas referências são valores típicos, setpoints ou limites?
9. As pressões são manométricas ou absolutas?
10. Quais documentos técnicos autorizados confirmam a arquitetura dos regimes?
