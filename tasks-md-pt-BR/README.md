# tasks-md

Um backlog leve para trabalho local de desenvolvimento: tarefas que precisam ser
retomadas, acompanhadas ou documentadas. Ajustes pequenos concluídos na mesma
sessão não precisam de um arquivo de tarefa, salvo quando a decisão merece ser
preservada.

## Organização

- `tasks-md/`: tarefas abertas.
- `tasks-md/TEMPLATE.md`: modelo para novas tarefas.
- `tasks-md/notes/`: anotações de trabalho — investigações, saídas de comandos,
  comparações e resultados específicos de um ambiente. Crie quando necessário.
- `tasks-md/archived/`: tarefas concluídas. Crie quando necessário.
- `tasks-md/deleted/`: tarefas canceladas. Crie quando necessário.

## Tarefas existentes

Use este padrão para novas tarefas. Tarefas existentes podem manter seu formato,
nomes de arquivo, campos e valores de status; não reformate o backlog em massa
apenas para adequá-lo ao padrão. Para tarefas legadas, mantenha status e localização
consistentes com as convenções existentes do projeto (por exemplo, `closed` em
`archived/` e `tombstone` em `deleted/`). Ao migrar uma tarefa intencionalmente, use
o template e os valores de status atuais, preserve conteúdo útil e referências a
issues externas e atualize os links afetados.

## Fluxo

1. Antes de criar uma tarefa, procure uma relacionada em `tasks-md/`.
2. Se ela existir, atualize o mesmo arquivo.
3. Se não existir, copie `TEMPLATE.md` para um nome curto e descritivo, por exemplo,
   `corrigir-timeout-de-upload.md` ou `fix-upload-timeout.md`.
4. Mantenha `Estado atual` curto e atualizado. Coloque material detalhado em
   `notes/` e faça referência a ele na tarefa.
5. Para concluir: atualize `Estado atual` com o resultado e a validação, defina
   `status: done` e mova o arquivo para `archived/`.
6. Para cancelar: registre brevemente o motivo em `Estado atual`, defina
   `status: cancelled` e mova o arquivo para `deleted/`.

Sempre que uma tarefa ou anotação for movida ou renomeada, atualize os caminhos
relativos dentro dela e as referências a ela em outros arquivos. Por exemplo,
após arquivar uma tarefa, sua referência a uma tarefa aberta muda de
`outra-tarefa.md` para `../outra-tarefa.md`.

## Arquivo de tarefa

Três seções, nesta ordem:

- **Objetivo** — o problema ou resultado desejado e o limite do trabalho.
  Mantenha relativamente estável; explica *o quê* e *até onde*.
- **Pronto quando** — critérios verificáveis de conclusão.
- **Estado atual** — uma síntese substituível do que vale agora e do próximo
  passo. Atualize sempre que o estado da tarefa mudar; remova decisões superadas.
  No fechamento, passa a registrar o resultado, a validação realizada e qualquer
  limitação relevante.

Não crie seções extras por padrão. Se houver material que não cabe nessas seções,
use `notes/`.

## Front matter

Campos mínimos, já presentes em `TEMPLATE.md`:

```yaml
title: "Título curto e claro"
status: "open"
created_at: "YYYY-MM-DD"
updated_at: "YYYY-MM-DD"
```

- `status` aceita `open`, `deferred`, `done` ou `cancelled`.
  `done` corresponde a `archived/`; `cancelled`, a `deleted/`.
- Datas usam `YYYY-MM-DD`. Quando horários exatos importarem, `git log` já os registra.
- Atualize `updated_at` sempre que o arquivo da tarefa mudar.

Campos opcionais — acrescente apenas quando forem úteis:

```yaml
labels: [api, bug]      # ajuda no agrupamento e na busca
tracker: AX-123         # ID de issue externa (Jira, Linear, ...)
```

Não acrescente campos vazios. `priority`, `owner` e `issue_type` não fazem parte
do padrão por decisão de projeto.

## Anotações (`notes/`)

Anotações são arquivos Markdown de formato livre, sem template nem front matter.

- Use para qualquer material grande demais para uma tarefa: investigações
  extensas, saídas de comandos, comparação de alternativas e resultados
  específicos de uma máquina ou ambiente.
- Faça referência a partir da tarefa usando um caminho relativo:
  `notes/investigacao-timeout-de-upload.md`.
- Não duplique: a tarefa registra objetivo, critérios e estado atual; a anotação
  guarda o material de apoio. A anotação não repete o estado vivo da tarefa.
- Quando uma tarefa for arquivada ou cancelada, mova suas anotações para
  `archived/notes/` ou `deleted/notes/` se merecerem ser preservadas e nenhuma
  tarefa aberta ainda as utilizar. Mantenha anotações compartilhadas em `notes/`
  enquanto tarefas abertas precisarem delas; tarefas arquivadas ou canceladas
  podem referenciá-las como `../notes/<anotacao>.md`.

## Nomes

- Nomes curtos e descritivos, em minúsculas e com palavras separadas por hífens,
  no idioma de trabalho do projeto. `corrigir-timeout-de-upload.md` e
  `fix-upload-timeout.md` são válidos.
- Sem IDs aleatórios, números sequenciais ou status no nome do arquivo.
- Se a tarefa tiver um ID de issue externa, registre-o no front matter
  (`tracker:`), não no nome do arquivo.

## Associação entre tarefas

- Faça referência a tarefas por caminho relativo apenas quando a relação
  esclarecer escopo, dependência ou histórico (relativo ao arquivo da tarefa,
  por exemplo, `archived/tarefa-maior.md`):
  - Relacionada: `outra-tarefa.md`
  - Desdobrada de: `archived/tarefa-maior.md`
- Não associe tarefas apenas por compartilharem um tema vago.

## Validação

Para mudanças exclusivas em `tasks-md/`, valide por leitura dos arquivos.
O status do Git não verifica o conteúdo Markdown.
