# Guia de revisão e lacunas

## 1. Como revisar sem precisar ler tudo de uma vez

### Primeira rodada — produto

Leia:

1. `README.md`;
2. `docs/00-documento-mestre-produto.md`;
3. este guia.

Confirme se a história e a visão representam o que você quer construir.

### Segunda rodada — operação

Leia:

1. `docs/01-contexto-operacional.md`;
2. `docs/04-medicoes-unidades-e-fontes.md`;
3. `docs/05-riscos-seguranca-e-limites.md`.

Marque qualquer afirmação sobre a planta que esteja errada, incompleta ou sensível.

### Terceira rodada — software

Leia:

1. `docs/02-arquitetura-atual.md`;
2. `docs/03-regras-negocio-e-dominio.md`;
3. `docs/07-testes-ambientes-e-operacao.md`;
4. `docs/11-contexto-atual.md`.

### Quarta rodada — futuro

Leia:

1. `docs/06-mvp-roadmap-e-criterios.md`;
2. `docs/adr/`;
3. `CONTRIBUTING.md` e `AGENTS.md`.

## 2. Perguntas essenciais sobre produto

- Quem você imagina usando a primeira versão?
- O principal problema é ronda, passagem de turno, histórico, ocorrência ou outro?
- Qual seria o menor resultado útil em uma área piloto?
- O projeto será apenas portfólio/aprendizado ou pretende ser usado na operação?
- Há autorização para conversar com outros operadores?
- Qual problema faria alguém realmente abrir o sistema todos os dias?
- O que você não quer que o RefrigOps se torne?

## 3. Perguntas essenciais sobre a operação

- Quantas salas existem e como são chamadas?
- Como começa e termina uma ronda?
- Qual periodicidade?
- Existe roteiro por turno?
- Quais campos são registrados atualmente?
- Quais observações qualitativas são importantes?
- O que acontece quando uma leitura não pode ser feita?
- Como se registra equipamento parado, evacuado ou em manutenção?
- Como funciona a passagem de turno?
- Quais registros são oficiais e quais são informais?

### Respostas já obtidas

- a ronda segue uma rota física entre as salas 1 e 2;
- a expectativa local é uma leitura horária, sete ou oito vezes por turno;
- outra sala aparentemente usa frequência diferente;
- a folha possui horários fixos e continua no verso;
- compressor desligado e leitura não realizada ficam igualmente em branco;
- a área de não conformidade/ação não é usada pelo operador consultado;
- identificação do executor não é praticada;
- alguém transfere posteriormente dados para um computador;
- manutenção externa já consultou o caderno para analisar data específica;
- um aplicativo móvel anterior existiu e foi abandonado por motivo desconhecido;
- em 2026-08-29 foram registrados 12 compressores como ativos no inventário observado, mas a contagem precisa ser reconfirmada devido à divergência do COMP-09;
- foram observadas pelo menos três famílias de IHM/controlador local;
- equipamentos ativos no inventário podem estar parados durante a ronda;
- as famílias de IHM não apresentam exatamente o mesmo conjunto de siglas e campos;
- a rota foi registrada com 13 posições; o COMP-07 não foi fotografado porque está desmontado e em manutenção, mas a contagem total depende da confirmação do COMP-09;
- COMP-13 e COMP-01, cujas placas não apareciam nas fotos, foram confirmados pelo operador;
- existem 12 fotos de controladores; a atribuição da sexta ao COMP-09, assim como sala e regime, precisa ser reconfirmada;
- existem regimes operacionais denominados -35 °C, -10 °C e -5 °C;
- foi registrada uma associação de 13 posições aos regimes, com 12 ativos e o COMP-07 em manutenção; a divergência do COMP-09 impede tratar a contagem completa como confirmada;
- **[PENDENTE]** confirmar se o COMP-09 pertence ao inventário e, em caso positivo, sua sala e seu regime;
- os COMP-04 e COMP-06 possuem inversor de frequência; a afirmação sobre o COMP-09 permanece pendente;
- COMP-15 e COMP-16 são exclusivos para água gelada;
- COMP-06 e COMP-10 normalmente atendem água gelada e ambiente;
- COMP-06 pode ser direcionado exclusivamente para ambiente, enquanto COMP-10 pode ajudar o regime de alta de -10 °C;
- existe uma interligação operacional relatada entre as redes de -10 °C e -5 °C;
- segundo o registro de 2026-08-29, depois da sequência dos compressores a ronda segue para os recipientes/manômetros; a completude das 13 posições depende da confirmação do COMP-09;
- mudanças de atendimento dos COMP-06 e COMP-10 são anotadas no Caderno dos Turnos e também informadas verbalmente;
- o conteúdo verbal da passagem varia entre operadores; alguns comunicam somente quebras ou situações que não conseguiram resolver;
- existe um registro chamado Caderno dos Turnos, separado do caderno de leituras, para anotar data sem horário, acontecimentos e atividades realizadas e informar os turnos seguintes;
- o preenchimento esperado do Caderno dos Turnos inclui os nomes dos operadores presentes no dia, mas a consistência dessa prática ainda não foi confirmada;
- acontecimentos e atividades são anotados no Caderno dos Turnos em texto livre, usando linhas comuns;
- quando uma pendência é resolvida, a anotação original permanece e uma linha posterior cita o problema e destaca a correção ou resolução;
- o turno seguinte consulta o Caderno dos Turnos sem registrar confirmação de leitura;
- atividades atribuídas a um turno futuro podem ser esquecidas e precisar de adiamento;
- restrições registradas com antecedência para data futura podem perder visibilidade quando a data chega;
- o caderno de leituras contém somente os dados solicitados em sua folha, sem relatos livres ou ocorrências;
- exemplos de anotações incluem conferência das salas, degelo em câmaras e lavagem de condensadores;
- foram relatadas substituições temporárias entre compressores e retorno posterior à condição normal;
- o regime de -35 °C atende aplicações como túneis, girofreezer e câmaras de estocagem;
- para o regime de -5 °C foi relatada sucção positiva aproximada entre 2,9 e 3,4, ainda sem unidade validada;
- desde a origem existe preocupação com cansaço e excesso de digitação durante a ronda;
- opções rápidas foram sugeridas para situações recorrentes, sem aprovação para preenchimento automático de valores;
- existem relatos divergentes sobre a natureza da Pressão de Descarga Geral.

### Perguntas refinadas para operadores experientes e supervisão

- Existe alguma identificação explícita do turno além de data e nomes?
- Quais acontecimentos, atividades e pendências precisam obrigatoriamente ser registrados?
- Quem define e autoriza tarefas ou restrições destinadas a outro turno?
- Em quais situações excepcionais uma tarefa reagendada muda de turno responsável?
- Como uma restrição futura permanece visível na data correta?
- Onde os dados são digitados no computador, por quem e com qual finalidade?
- Existe procedimento escrito que define a frequência horária?
- Como a supervisão distingue compressor desligado de ronda não realizada?
- Qual variável e unidade correspondem ao `SETP.` de cada compressor?
- Quem altera o setpoint e como sua mudança é registrada?
- A seção de não conformidade pertence a outro processo ou deveria ser utilizada?
- Por que o aplicativo anterior foi descontinuado e onde ficaram seus dados?
- Quais parâmetros a manutenção externa observa para avaliar o compressor historicamente?
- Cada compressor possui controlador local semelhante ou existem modelos diferentes?
- O controlador guarda histórico ou mostra somente valores instantâneos?
- O `set-point` corresponde à pressão de sucção? Qual é a unidade e quem o define?
- O que significam oficialmente `SP`, `DP`, `OP`, `OF`, `IP`, `SH-SP`, `SH-DP`, `ST`, `DT`, `OT`, `IT`, `OST` e `SV`?
- A corrente exibida está em ampères e `Pot.` está em quilowatts?
- Nos COMP-04 e COMP-06, onde a frequência é consultada e existe registro histórico? O COMP-09 pertence ao inventário e possui inversor? Algum outro compressor possui inversor?
- O regime de -5 °C é chamado apenas de água gelada/ambiente ou também recebe o nome de alta em algum contexto?
- Quais condições, autorizações e registros se aplicam às mudanças de atendimento dos COMP-06 e COMP-10?
- Qual é a topologia e a finalidade oficial da interligação entre as redes de -10 °C e -5 °C?
- Outros compressores também podem mudar de regime ou serviço?
- Quais são as unidades e o significado das referências de sucção `-10` e `1,9` a `2,4`?
- Qual é a unidade e a finalidade da referência de sucção `2,9` a `3,4` do regime de -5 °C?
- Quais compressores usam MYCOM legada, CPIV e MYPRO TOUCH?
- O texto `kgf` das telas novas corresponde a `kgf/cm²`?
- `Amônia` e `Água Gelada` identificam serviço, circuito, regime ou outra classificação?
- Qual campo de cada família de IHM alimenta cada linha do caderno?
- É possível obter de forma autorizada os manuais e versões exatas dos MBR-2, MBR-4 e CPIV?
- Quais recursos de histórico e comunicação MYPRO estão habilitados localmente?

## 4. Equipamentos e estados

- O padrão `COMP-13`, `COND-03`, `REC-01` corresponde às tags reais?
- `RECEIVER` é o termo certo para todos os recipientes?
- Bombas precisam entrar em `EquipmentType`?
- Quais outros tipos existem?
- `RUNNING`, `STOPPED`, `MAINTENANCE`, `EVACUATED` e `DEACTIVATED` são suficientes?
- `EVACUATED` se aplica apenas a recipientes?
- Qual a diferença entre `DEACTIVATED` e `active = false`?
- É permitido apagar equipamento ou somente desativar?
- Precisamos guardar histórico de estado?
- fabricante, modelo de controlador, aplicação e presença de inversor pertencem ao cadastro do equipamento?

## 5. Medições

- Qual é a fonte oficial da tabela NH₃?
- Ela usa pressão absoluta ou manométrica?
- A IHM apresenta bar absoluto ou manométrico?
- Qual é a localização exata de cada transmissor?
- O que significa tecnicamente Pressão de Descarga Geral?
- Ela é medida em coletor/recipiente, escolhida de um ponto específico ou calculada a partir de várias descargas?
- O PT100 mede superfície, ambiente ou possui poço térmico?
- Há calibração documentada?
- As leituras são simultâneas?
- Qual arredondamento é usado?
- Existe procedimento oficial para não condensáveis?

## 6. Usuários e UX

- Celular pessoal, corporativo, tablet ou computador?
- Existe internet/Wi-Fi nas salas?
- Precisa funcionar offline?
- Operadores usam luvas?
- Autenticação individual é viável?
- Dispositivos são compartilhados?
- Tamanho de fonte e contraste necessários?
- Qual tempo máximo aceitável para registrar cada ponto?
- Áudio/foto podem ser usados ou são proibidos?

## 7. Segurança, privacidade e organização

- Quais informações da planta podem aparecer em um repositório público?
- O repositório continuará público?
- O nome da empresa/local deve ser omitido?
- Fotos e tags são sensíveis?
- Dados de operadores podem ser armazenados?
- Quem pode visualizar, corrigir e exportar registros?
- Há política de retenção?
- Há responsáveis de TI/OT para futuras integrações?

## 8. Software e arquitetura

- O próximo passo continuará sendo `EquipmentResponse`?
- Quais campos do Equipment são públicos?
- Criação deve retornar 200 ou 201?
- Localização permanecerá texto?
- É desejável CI agora?
- O README deve ensinar a subir aplicação e banco?
- A aplicação será apenas backend por enquanto?
- Qual estratégia de autenticação será considerada futuramente?

## 9. Informações possivelmente ausentes

- objetivos comerciais;
- nome e identidade visual;
- licença do repositório;
- público fora da planta atual;
- concorrentes e sistemas já usados;
- normas e procedimentos aplicáveis;
- inventário completo de equipamentos;
- diagramas de processo e instrumentação autorizados;
- estrutura de turnos;
- fluxo de manutenção;
- modelo de implantação;
- requisitos offline;
- backup, retenção e auditoria;
- governança dos dados;
- critérios de sucesso mensuráveis.

## 10. O que não foi incluído propositalmente

- nomes da empresa e pessoas;
- dados industriais detalhados;
- endereços de rede e tags completas;
- fórmula apresentada como verdade para “% de ar”;
- limites de segurança;
- procedimentos de purga;
- arquitetura de produção inventada;
- cronograma e custo sem evidência;
- personas fictícias detalhadas.

## 11. Resultado esperado da revisão

Ao final, classifique cada documento:

```text
APROVADO
APROVADO COM CORREÇÕES
PRECISA DE MAIS DESCOBERTA
NÃO DEVE ENTRAR NO REPOSITÓRIO
```

Depois consolidaremos somente o que estiver suficientemente claro.
