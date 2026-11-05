# tasks-md

Leia este README em [inglês](README.md).

Uma convenção leve, baseada em arquivos, para acompanhar tarefas locais de
desenvolvimento de software.

Cada tarefa é um único arquivo Markdown. O diretório contém texto simples, não
depende de ferramentas e pode ser lido e atualizado tanto por pessoas quanto por
agentes de código. A estrutura é pequena para continuar útil ao longo do tempo,
sem acrescentar burocracia de gestão de projetos.

## O que é

- **Um arquivo por tarefa**, no diretório `tasks-md/` da raiz do projeto.
- **Um template mínimo**: objetivo, critérios de conclusão e uma síntese viva do
  estado atual. Nada além disso é obrigatório.
- **Um fluxo mínimo**: criar, atualizar, encerrar. Tarefas concluídas vão para
  `archived/`; canceladas, para `deleted/`.
- **Um lugar para anotações de trabalho** detalhadas demais para a tarefa, mas que
  merecem ser preservadas: `tasks-md/notes/`.

## O que não é

- Não é um gerenciador de tarefas. Não há banco de dados, CLI ou sincronização.
- Não substitui rastreadores de issues. Pode complementá-los; um ID do Jira ou
  Linear pode constar no arquivo, mas é opcional.
- Não é um log. O histórico de progresso é opcional. Se precisar de registros
  datados para auditoria, escreva-os no arquivo — mas uma síntese curta do estado
  atual é o padrão.

## Como adotar

Escolha um idioma e copie o diretório correspondente para a raiz do seu projeto
com o nome `tasks-md/`:

- [English](tasks-md-en/README.md): copie `tasks-md-en/` como `tasks-md/`.
- [Português do Brasil](tasks-md-pt-BR/README.md): copie `tasks-md-pt-BR/` como `tasks-md/`.

Leia `tasks-md/README.md` no diretório copiado. Cada diretório de idioma contém o
padrão completo e pode ser adotado de forma independente. As duas versões usam
as mesmas regras, nomes de campos do front matter e valores de status; os textos
e títulos de seção são traduzidos. Todos os caminhos internos usam o nome
adotado, `tasks-md/`.

Se o projeto já tiver `tasks-md/`, incorpore as convenções ao README e ao template
existentes, preservando as orientações específicas do projeto. Siga as regras de
compatibilidade de `tasks-md/README.md` para tarefas existentes.

Mantenha `tasks-md/README.md` como guia compartilhado entre pessoas e agentes de
código. No `AGENTS.md` da raiz do projeto, acrescente esta instrução para que os
agentes saibam onde encontrar as convenções de tarefas:

```md
Antes de criar ou atualizar tarefas locais, leia `tasks-md/README.md` e siga
suas convenções.
```

Para projetos em inglês, a instrução equivalente é:

```md
Before creating or updating local tasks, read `tasks-md/README.md` and follow
its conventions.
```

```
seu-projeto/
  tasks-md/
    README.md     # convenções e fluxo de trabalho
    TEMPLATE.md   # modelo para novas tarefas
    # notes/      # anotações de trabalho (criar quando necessário)
    # archived/   # tarefas concluídas (criar quando necessário)
    # deleted/    # tarefas canceladas (criar quando necessário)
```

Adapte à vontade: renomeie seções, acrescente ou remova um campo. O critério é
que criar uma tarefa continue levando menos de um minuto e que uma tarefa de
três meses atrás ainda seja fácil de retomar.

## Princípios

- **Texto em primeiro lugar.** Arquivos Markdown em um diretório. Qualquer editor,
  agente ou `grep` serve.
- **Arquivos pequenos.** A tarefa registra o objetivo, quando estará concluída e
  o que vale agora. Material maior vai para `notes/`.
- **Estado acima de formalidades.** O estado atual é uma síntese substituível do
  que importa hoje, sem um fluxo formal de status.
- **Sem IDs artificiais.** Os nomes de arquivo são curtos e descritivos, com
  palavras separadas por hífens, no idioma de trabalho do projeto. Sem prefixos
  aleatórios ou números sequenciais.
- **Encerre e mova.** Crie `archived/` e `deleted/` apenas quando a primeira tarefa
  precisar deles.

## Licença

Este projeto está disponível sob [CC0 1.0 Universal](LICENSE). Você pode copiar,
adaptar e redistribuir o material, inclusive para fins comerciais, sem precisar
de autorização ou atribuição.

Atribuição é bem-vinda, mas não é obrigatória.
