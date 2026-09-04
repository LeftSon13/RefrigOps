# Evidência — revisão do chat histórico de origem do RefrigOps

- Data da revisão: 2026-08-29
- Tipo: histórico de descoberta, relatos operacionais e desenvolvimento do projeto
- Fonte: conversa compartilhada pelo autor do RefrigOps
- Título da conversa: `Automatizar monitoramento industrial`
- Sensibilidade: URL, imagens, nome da empresa e localização não reproduzidos no repositório

## Finalidade

Comparar a conversa em que a ideia surgiu com a documentação atual, recuperando informações ausentes sem tratar respostas antigas do assistente como verdade automática.

Foram priorizados:

1. relatos escritos pelo operador;
2. imagens posteriormente confirmadas pelo operador;
3. evidência do repositório atual;
4. decisões explicitamente aceitas;
5. respostas do assistente apenas como histórico, hipótese ou orientação a revalidar.

## Limitações da revisão

- algumas mensagens continham somente imagens ou arquivos sem descrição textual suficiente;
- logs e capturas representam estados históricos, não o ambiente atual;
- respostas antigas podem conter inferências incorretas;
- valores operacionais relatados não são limites técnicos aprovados;
- a conversa pública contém informações que não devem ser replicadas em documentação pública.

## Origem do produto confirmada

O RefrigOps nasceu da tentativa de responder a três necessidades relacionadas:

```text
reduzir registro manual repetitivo
        +
criar histórico consultável
        +
investigar integração futura com IHMs
```

A primeira visão considerava enviar dados de controladores para uma infraestrutura central, acompanhar variáveis e apoiar manutenção preventiva. A evolução posterior priorizou registro estruturado e compreensão do domínio antes de telemetria.

## Regimes e aplicações recuperados

### -35 °C — baixa

Aplicações citadas:

- túneis;
- girofreezer;
- câmaras de estocagem.

Referência de sucção relatada: negativa, próxima de `-10`, sem unidade confirmada.

### -10 °C — alta

Referência de sucção relatada: positiva, aproximadamente entre `1,9` e `2,4`, sem unidade confirmada.

**[CONFIRMADO — CONTEXTO OPERACIONAL]** O responsável pelo projeto confirmou que o COMP-09 pertence à Sala de Máquinas 2, trabalha no regime de `-10 °C` e é classificado operacionalmente como compressor de alta.

### -5 °C — água gelada e ambiente

Aplicações citadas:

- água gelada;
- ambiente/climatização.

Referência de sucção relatada: positiva, aproximadamente entre `2,9` e `3,4`, sem unidade confirmada.

## Ergonomia e esforço de registro

Desde o início existia preocupação com o volume de digitação. Foi sugerido permitir seleção rápida para situações recorrentes e escrita livre quando algo fugisse do padrão.

Essa ideia deve ser desenvolvida com cuidado:

- opções rápidas podem funcionar bem para estado e observação qualitativa;
- valores numéricos não devem ser preenchidos por padrão como se fossem medidos;
- copiar a última leitura pode induzir registro falso;
- qualquer sugestão deve exigir confirmação clara e preservar horário/origem;
- o piloto precisa medir tempo, cansaço e compreensão do operador.

## Recipientes e fontes de pressão

O chat confirma o relato de cinco recipientes, quatro com manômetros, com alguns evacuados e, em certos períodos, somente dois em uso.

Também aparecem as seguintes referências:

- `Pressão de Saída do Condensador 3`, usada operacionalmente como referência de pressão de condensação;
- `Pressão de Descarga Geral`;
- manômetros dos recipientes;
- PT100 externo próximo ao visor de líquido;
- tabela de pressão equivalente da amônia.

### Divergência preservada

Em uma mensagem, a Pressão de Descarga Geral foi descrita como média da descarga dos compressores de alta. Em esclarecimento posterior, foi dito que a pressão podia ser observada em um recipiente/manômetro e que os manômetros mediam a pressão do recipiente.

Portanto, não está confirmado se o valor é:

- cálculo aritmético de várias descargas;
- transmissor em coletor comum;
- pressão de um recipiente conectado ao lado de alta;
- outra referência do sistema.

O RefrigOps não deve calcular nem rotular esse ponto sem diagrama, tag e confirmação técnica.

## Qualidade dos dados históricos

O operador alertou que leituras feitas a partir de celular/fotografias não estavam totalmente exatas. Isso reforça a separação entre:

```text
valor demonstrativo de descoberta
valor operacional observado
dado validado para regra/limite
```

Valores recuperados do chat servem para compreender formato, sinal e ordem de grandeza, não para configurar alertas.

## Desenvolvimento e aprendizagem

O chat também confirma as preferências de trabalho:

- avançar com calma, uma etapa por vez;
- explicações e PRs em português brasileiro;
- atuação do assistente como instrutor sênior;
- GitHub como registro da evolução;
- uso de Issues, branches, commits, testes, PRs e review;
- aprendizado e capacidade de explicar decisões acima de copiar código.

Os estados do Git, Docker, banco e testes presentes no chat são históricos e devem ser conferidos no repositório real antes de qualquer implementação.

## Pendências resolvidas por esta revisão

- aplicações do regime de -35 °C registradas;
- referência de sucção do regime de -5 °C recuperada;
- preocupação original com cansaço e digitação registrada;
- ideia de opções rápidas separada de preenchimento automático de medição;
- divergência sobre Pressão de Descarga Geral explicitada;
- natureza histórica e não exata dos valores de fotos/celular registrada.

## Pendências que permanecem

- unidades das três referências de sucção;
- pressão manométrica ou absoluta;
- diferença entre nome do regime e variável física que o origina;
- limites e setpoints oficiais;
- arquitetura e interligações entre regimes;
- natureza exata da Pressão de Descarga Geral;
- representatividade do PT100 externo;
- finalidade e fonte oficial da tabela;
- quais opções rápidas realmente reduzem esforço sem piorar a qualidade do dado.
