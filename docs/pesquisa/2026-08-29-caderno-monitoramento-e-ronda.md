# Evidência — caderno de monitoramento e relato da ronda

- Data do registro: 2026-08-29
- Tipo: artefato operacional + relato do usuário
- Fonte: fotografia compartilhada em conversa e respostas do operador
- Sensibilidade: contém marca e dados operacionais; fotografia não incluída no repositório

## O que foi observado no artefato

- título “Monitoramento de Compressores Sala 01 e 02 — DIA”;
- grade horária fixa de `00:00` a `23:00`;
- agrupamento por compressor e parâmetro;
- valor `SETP.` em cabeçalhos;
- campos inferiores para não conformidade, causa, correção, ações e responsáveis;
- controle de documento/revisão;
- grande densidade de anotações manuscritas.

## Relato associado

- a mesma folha é usada; os outros compressores ficam no verso;
- a rota segue o layout físico das salas 1 e 2;
- a sequência contém 13 posições de compressores classificados;
- depois dos compressores, a ronda segue para os recipientes de amônia, chamados informalmente de garrafas, para leitura de um manômetro aplicável;
- mudanças de atendimento dos COMP-06 e COMP-10 são anotadas no Caderno dos Turnos e também comunicadas verbalmente;
- a ronda registra compressores ligados;
- campos de desligados ficam vazios;
- leituras não realizadas também devem permanecer vazias;
- a seção de não conformidade não é utilizada pelo operador consultado;
- identificação do executor não é realizada na prática;
- `SETP.` significa setpoint, variável e unidade ainda desconhecidas;
- expectativa local de uma ronda por hora;
- frequência histórica definida por técnicos e supervisão;
- alguém transfere dados para um computador;
- manutenção externa já consultou o caderno;
- aplicativo móvel anterior foi abandonado sem causa conhecida.

## Sequência confirmada da ronda

**[CONFIRMADO — CONTEXTO OPERACIONAL]** O COMP-09 pertence à Sala de Máquinas 2, trabalha no regime de `-10 °C` e é classificado operacionalmente como compressor de alta.

```text
Sala 1: COMP-14 → COMP-13
Sala 2: COMP-08 → COMP-07 → COMP-06 → COMP-05 → COMP-04 → COMP-09
Sala 1: COMP-11 → COMP-10 → COMP-15 → COMP-16
Sala 2: COMP-01
Recipientes de amônia / garrafas: leitura de um manômetro aplicável
Retorno à sala: consulta da tabela de pressão equivalente da amônia
```

O COMP-07 integra a rota, mas estava desmontado e em manutenção no momento do registro.

## Interpretação provisória

O formulário prioriza uma matriz equipamento × parâmetro × hora. Ele não registra horário real, origem detalhada, motivo de ausência ou autoria por leitura.

O histórico tem valor potencial para manutenção, mas a finalidade e o consumidor não são transparentes para o operador que coleta os dados.

O caderno de leituras é usado somente para preencher os dados solicitados na folha. Acontecimentos, atividades realizadas, mudanças de atendimento e continuidade entre turnos são registrados no Caderno dos Turnos.

O conteúdo da comunicação verbal varia conforme o operador. Foi relatado que alguns comunicam apenas quando houve quebra ou quando ficou alguma situação sem solução. Isso não prova ausência de informações em todos os outros turnos nem existência de um padrão oficial.

O Caderno dos Turnos está registrado em [`2026-08-29-caderno-ocorrencias-e-passagem-turno.md`](2026-08-29-caderno-ocorrencias-e-passagem-turno.md). A comunicação verbal permanece como outro canal e pode carregar contexto que ainda não foi mapeado.

## O que isto não prova

- que a rota atual seja um procedimento oficial imutável;
- que a frequência horária esteja em procedimento vigente;
- qual variável o setpoint controla;
- quem usa a transcrição no computador;
- que a seção de não conformidade nunca seja usada por ninguém;
- causa da descontinuação do aplicativo anterior;
- qualidade metrológica das leituras.

## Impacto no produto

- mobile deve respeitar rota física;
- concluir a etapa dos compressores antes de apresentar a etapa dos recipientes/manômetros;
- separar horário previsto, medido e registrado;
- distinguir equipamento parado de leitura não realizada;
- preservar ausência em vez de inventar dado;
- permitir observação qualitativa;
- não acrescentar ao formulário de leitura campos de ocorrência apenas porque ambos usam papel atualmente;
- apresentar mudanças vigentes de regime ou serviço na passagem de turno derivada do registro separado;
- não transformar o hábito de um operador em regra universal de passagem de turno;
- manter medições periódicas separadas de acontecimentos, atividades e pendências do turno;
- desktop deve apoiar histórico e análise;
- setpoints precisam de significado, unidade e vigência;
- autoria e auditabilidade devem ser introduzidas de forma prática;
- não reproduzir automaticamente campos de não conformidade sem validar o processo.

## Próxima validação

Entrevistar operador experiente, técnico/supervisão e responsável pela transcrição para o computador usando as perguntas de `docs/12-guia-revisao-e-lacunas.md`.
