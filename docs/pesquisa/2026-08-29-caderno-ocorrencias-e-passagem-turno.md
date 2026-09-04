# Evidência — Caderno dos Turnos

- Data do registro: 2026-08-29
- Tipo: relato operacional
- Fonte: operador participante da descoberta do RefrigOps
- Nome usado pela equipe: `Caderno dos Turnos`
- Sensibilidade: resumo sanitizado; nenhuma página ou anotação real foi incluída

## O que foi confirmado

Existe um caderno separado do caderno de leituras periódicas, chamado pela equipe de **Caderno dos Turnos**.

Nesse segundo caderno, os operadores anotam:

- data, sem horário;
- nomes dos operadores presentes no dia, conforme o preenchimento esperado;
- relatos em texto livre, escritos em linhas comuns;
- o que aconteceu durante o turno;
- o que foi realizado durante o turno;
- informações que ajudam os turnos seguintes a entender o que cada turno está fazendo.

O conteúdo verbal da passagem varia conforme o operador. Alguns comunicam somente quando algo quebrou ou quando não conseguiram resolver uma situação.

O turno seguinte apenas consulta o Caderno dos Turnos. Não há assinatura, visto ou outra confirmação registrada de que a informação foi lida.

## Exemplos de anotações relatadas

Para um turno tranquilo, foram fornecidos exemplos como:

```text
Conferidas as salas 1 e 2
Feito degelo nas câmaras 1 e 4
Lavados os condensadores
```

Os exemplos registram inspeções e atividades concluídas. Eles documentam a linguagem usada no caderno, não constituem procedimento, checklist obrigatório ou autorização para executar essas atividades.

## Dois registros com finalidades diferentes

```text
caderno de leituras
→ valores periódicos da ronda
→ matriz por compressor, parâmetro e horário

Caderno dos Turnos
→ acontecimentos
→ atividades realizadas
→ continuidade entre turnos
```

Os dois registros podem se relacionar, mas não devem ser tratados como a mesma fonte de informação.

O caderno de leituras é preenchido somente com os dados solicitados em sua própria folha. Acontecimentos, atividades e mudanças de atendimento pertencem ao Caderno dos Turnos.

## Interpretação provisória

O segundo caderno funciona como memória operacional compartilhada entre turnos. Ele reúne eventos e ações que não cabem naturalmente na grade numérica do caderno de leituras.

As atividades e acontecimentos são escritos em linhas comuns, em texto livre. Os exemplos mostram frases curtas descrevendo ações no passado.

Quando uma situação é registrada como pendente e depois é resolvida, a anotação original permanece. Em uma linha posterior é informado que a situação foi corrigida ou resolvida.

```text
linha anterior → situação pendente
linha posterior → situação corrigida ou resolvida
```

Isso indica pelo menos quatro conceitos diferentes para o produto:

```text
medição periódica
ocorrência ou acontecimento
atividade ou ação realizada
pendência ou continuidade para outro turno
```

Uma atividade realizada pode responder a uma ocorrência, mas essa relação ainda precisa ser observada. Uma anotação também pode permanecer relevante para mais de um turno.

O caderno preserva uma sequência cronológica em vez de reescrever o passado. Na linha posterior, os operadores citam o problema e destacam que ele foi resolvido.

## Problemas de comunicação relatados

Foram relatadas perdas de continuidade mesmo quando a informação havia sido escrita.

### Tarefa atribuída a um turno futuro

Exemplo sanitizado:

```text
Turno 1 registra que o terceiro turno deve “fazer vazio” no COMP-09
→ o terceiro turno esquece
→ a atividade precisa ser adiada
```

“Fazer vazio” foi preservado como expressão operacional do relato. Seu significado técnico, condições e procedimento não foram definidos neste documento.

Esse exemplo histórico também não confirma por si só a existência, a identificação, a sala ou o regime do COMP-09. Esses pontos permanecem pendentes devido à divergência registrada em `docs/11-contexto-atual.md`.

### Restrição válida para uma data futura

Exemplo sanitizado:

```text
primeiro turno registra que o segundo turno,
em uma data futura, não poderá ligar o COMP-X
→ a anotação foi feita com muita antecedência
→ quando a data chega, a informação já não está presente na atenção do turno
```

O exemplo registra uma falha de comunicação. Não define quando um equipamento pode ser ligado e não autoriza o RefrigOps a comandar, bloquear ou liberar equipamentos.

## Causas operacionais percebidas

Pelo relato, o caderno possui pelo menos estas limitações:

- não registra confirmação de leitura;
- uma anotação futura pode ficar distante das páginas consultadas no dia;
- não há lembrete associado à data;
- não há acompanhamento estruturado por turno responsável;
- uma tarefa pode ser esquecida e precisar ser adiada;
- uma restrição importante pode perder visibilidade antes de sua data de validade.

Esses itens descrevem problemas percebidos, não causas-raiz formalmente investigadas.

## O que isto não prova

- quais informações são obrigatórias;
- se toda inspeção, quebra, ação ou pendência é registrada;
- quem pode escrever, corrigir ou consultar;
- se os nomes de todos os operadores presentes são preenchidos de forma consistente na prática;
- se existe assinatura ou identificação explícita do turno;
- por quanto tempo o caderno é guardado;
- se existe procedimento formal que define a passagem de turno.

## Impacto possível no produto

O RefrigOps não deve misturar uma leitura numérica com o relato de um acontecimento. Uma modelagem futura pode precisar distinguir, sem aprovação de implementação neste momento:

```text
ocorreu algo
→ o que aconteceu
→ equipamento ou área relacionada
→ quando foi percebido

foi realizada uma atividade
→ o que foi feito
→ por quem ou por qual equipe
→ quando foi realizado

ficou uma continuidade
→ situação atual
→ pendência para o turno seguinte
→ acompanhamento necessário

foi atribuído para depois
→ turno responsável
→ data de referência
→ situação pendente, realizada, adiada ou cancelada

existe uma restrição futura
→ equipamento relacionado
→ período de validade
→ origem e responsável pela orientação
→ confirmação de ciência

foi resolvido depois
→ preservar a anotação original
→ adicionar registro posterior de correção ou resolução
→ relacionar os dois registros
```

A futura tela de passagem de turno pode reunir essas informações, mas os campos obrigatórios precisam ser definidos com operadores e supervisão. O sistema não deve concluir automaticamente que uma ocorrência foi resolvida apenas porque uma atividade foi registrada.

Uma correção ou resolução futura deve ser acrescentada ao histórico e relacionada à pendência anterior, sem apagar ou alterar silenciosamente o registro original. O novo registro deve identificar o problema resolvido, seguindo o comportamento já observado no caderno.

Uma futura solução pode precisar destacar tarefas e restrições na data correta e registrar ciência do turno responsável. Isso ainda exige validação com operadores, supervisão e procedimentos. Uma confirmação no aplicativo não garante execução da atividade nem substitui comunicação, treinamento ou controles de segurança.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** Quando uma atividade é adiada, uma nova data é anotada. Portanto, o adiamento mantém a atividade em acompanhamento e altera sua data prevista; ele não deve ser tratado como conclusão ou cancelamento. Geralmente, o turno responsável continua sendo o mesmo. Como o relato descreve uma prática habitual, isso não deve ser transformado em regra imutável sem validar possíveis exceções.

## Perguntas abertas

1. Os nomes de todos os operadores presentes são preenchidos consistentemente?
2. Existe identificação explícita do turno além da data?
3. As anotações diferenciam acontecimento, ação realizada e pendência?
4. Quem define e autoriza tarefas ou restrições destinadas a outro turno?
5. Em quais situações excepcionais uma atividade reagendada muda de turno responsável?
6. Qual antecedência é comum para anotações futuras?
7. Quem consulta o histórico e por quanto tempo ele é guardado?

## Próxima validação

Confirmar se os nomes são preenchidos consistentemente, como tarefas e restrições futuras são autorizadas e em quais exceções uma atividade reagendada muda de turno responsável. Se houver autorização, observar apenas a organização geral da página, sem incluir conteúdo real no repositório.

## Evidência relacionada

- [Caderno de monitoramento e relato da ronda](2026-08-29-caderno-monitoramento-e-ronda.md)
