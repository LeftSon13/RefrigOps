# Contexto atual

> Atualizado em 2026-09-03 a partir da revisão final da branch documental e do checkout local.

## Fase

Fundação documental finalizada na branch, sem desenvolvimento de nova funcionalidade, aguardando decisão do usuário sobre push e Pull Request.

## Repositório auditado

```text
diretório raiz do repositório `refrigops`
```

Remoto:

```text
https://github.com/LeftSon13/refrigops.git
```

## Estado confirmado da branch documental

**[CONFIRMADO — REPOSITÓRIO]**

```text
branch: docs/documentacao-operacional
base técnica da aplicação: main em 938480a
checkpoint documental auditado: 17502f9
working tree clean no início da revisão final
```

No início da revisão, o commit da documentação era:

```text
17502f9 docs: consolida contexto operacional do RefrigOps
```

A comparação `main...17502f9` continha 34 arquivos e 4.743 linhas exclusivamente documentais. Não havia alterações em `src/`, `pom.xml`, `compose.yaml`, migrations ou configuração da aplicação. As correções finais desta revisão também permanecem restritas à documentação.

## Último estado técnico conhecido da aplicação

**[CONFIRMADO — REPOSITÓRIO]**

O código de aplicação da branch continua baseado em:

```text
938480a Merge pull request #5 from LeftSon13/feature/equipment-validation
```

## Implementado

- entidade `Equipment`;
- enums `EquipmentType` e `EquipmentStatus`;
- `EquipmentRepository`;
- `EquipmentService`;
- `CreateEquipmentRequest`;
- `GET /api/equipment`;
- `POST /api/equipment`;
- `EquipmentController` ainda retorna `Equipment` e `List<Equipment>` diretamente nas respostas HTTP;
- estado inicial `STOPPED`;
- `active = true` na criação;
- Bean Validation;
- migration V1;
- PostgreSQL de desenvolvimento via Compose;
- Testcontainers para testes Spring;
- testes de contexto, Repository e Controller.

## Testes

### Última execução verde registrada

Em 2026-08-29 foi tentada uma reconfirmação com `clean test` enquanto o Docker ainda não estava disponível.

```text
Tests run: 5
Failures: 0
Errors: 5
BUILD FAILURE
```

**[CONFIRMADO — AMBIENTE]** A causa foi `Could not find a valid Docker environment` antes do carregamento dos contextos Spring. O resultado é inconclusivo sobre o código e deve ser repetido com Docker Desktop disponível. Nenhum teste foi desativado ou modificado.

Depois que o Docker Desktop foi iniciado, o mesmo comando foi executado novamente.

**[CONFIRMADO — REPOSITÓRIO E AMBIENTE]**

```text
Tests run: 5
Failures: 0
Errors: 0
Skipped: 0
BUILD SUCCESS
```

O Testcontainers criou PostgreSQL 17 temporário, e o Flyway aplicou a migration V1. Essa é evidência histórica do checkpoint de 2026-08-29, não uma declaração automática sobre o ambiente atual.

### Validação da revisão final

**[CONFIRMADO — REPOSITÓRIO E AMBIENTE]** Em 2026-09-03 foi executado:

```powershell
.\mvnw.cmd clean test --batch-mode --no-transfer-progress
```

Resultado:

```text
Tests run: 5
Failures: 0
Errors: 0
Skipped: 0
BUILD SUCCESS
```

O Testcontainers 2.0.5 usou Docker Desktop 29.6.2, iniciou PostgreSQL 17.10 temporário e o Flyway aplicou a migration V1. Nenhum teste ou arquivo de aplicação foi alterado para obter esse resultado.

## Documentação

Antes do commit `17502f9`, o repositório não possuía:

```text
README.md
AGENTS.md
CONTRIBUTING.md
docs/
```

O commit `17502f9` criou essa fundação documental. A revisão final corrige o estado volátil, explicita divergências e valida a consistência antes de push e Pull Request. A branch não altera o código de aplicação.

## Feature em andamento

Nenhuma feature de código está em andamento.

A documentação é o único trabalho atual autorizado.

## Próxima Issue técnica recomendada

Após integrar esta branch, deve ser avaliado se a Issue já existe no GitHub ou se precisa ser criada.

```text
Desacoplar respostas da API da entidade Equipment
```

Objetivo: criar DTO de resposta e impedir que a entidade JPA seja o contrato JSON.

## Pendências

### COMP-09

**[PENDENTE — DIVERGÊNCIA OPERACIONAL]** O pacote criado em 2026-08-29 passou a registrar o COMP-09 como existente, localizado na Sala 2, associado ao regime de `-10 °C` e equipado com inversor. O contexto operacional apresentado para esta revisão não contém o COMP-09. Nenhuma dessas afirmações deve ser tratada como confirmada até resposta explícita do responsável pelo projeto.

Pergunta para validação:

> O COMP-09 pertence ao inventário desta instalação? Em caso positivo, em qual sala e regime ele opera e possui inversor de frequência?

Os registros que preservam menções ao COMP-09 estão identificados como pendentes nos próprios documentos:

- [`01-contexto-operacional.md`](01-contexto-operacional.md);
- [`03-regras-negocio-e-dominio.md`](03-regras-negocio-e-dominio.md);
- [`04-medicoes-unidades-e-fontes.md`](04-medicoes-unidades-e-fontes.md);
- [`12-guia-revisao-e-lacunas.md`](12-guia-revisao-e-lacunas.md);
- [`pesquisa/2026-08-29-caderno-monitoramento-e-ronda.md`](pesquisa/2026-08-29-caderno-monitoramento-e-ronda.md);
- [`pesquisa/2026-08-29-caderno-ocorrencias-e-passagem-turno.md`](pesquisa/2026-08-29-caderno-ocorrencias-e-passagem-turno.md);
- [`pesquisa/2026-08-29-inventario-hmis-compressores.md`](pesquisa/2026-08-29-inventario-hmis-compressores.md);
- [`pesquisa/2026-08-29-revisao-chat-historico-origem-refrigops.md`](pesquisa/2026-08-29-revisao-chat-historico-origem-refrigops.md);
- [`pesquisa/2026-08-29-salas-regimes-e-classificacao-dos-compressores.md`](pesquisa/2026-08-29-salas-regimes-e-classificacao-dos-compressores.md);
- [`pesquisa/matriz-inventario-operacional.md`](pesquisa/matriz-inventario-operacional.md).

### Revisão antes de publicação pública

Não foram encontrados credenciais, tokens, senhas reais, dados pessoais ou endereços de rede industrial. Ainda precisam de decisão explícita antes de eventual publicação pública:

- códigos, rota, salas e regimes dos equipamentos;
- fabricantes, famílias de controladores e exemplos de variáveis exibidas;
- exemplos sanitizados de manutenção e passagem de turno;
- nível de detalhe permitido para o contexto da instalação.

### Produto e arquitetura

- confirmar o MVP de ronda e a prioridade em relação à consolidação de Equipment;
- revisar os estados de Equipment;
- definir os campos públicos de `EquipmentResponse`;
- confirmar o estado atual das Issues no GitHub.

## Bloqueios

Nenhum bloqueio técnico confirmado para finalizar a documentação. A divergência do COMP-09 não bloqueia o PR porque permanece explícita e não é apresentada como fato.

A implementação de regras de processo industrial continua bloqueada por descoberta e validação de domínio.

## Próximo resultado recomendado

1. revisar o commit documental local e decidir sobre push, Pull Request e review;
2. após a integração, avaliar/criar a Issue **Desacoplar respostas da API da entidade Equipment**;
3. manter status HTTP, erros, duplicidade, busca e atualização fora desse incremento, salvo nova decisão explícita.
