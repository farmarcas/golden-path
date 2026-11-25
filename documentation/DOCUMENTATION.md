# Documentação viva — guia

Política de documentação de toda aplicação criada ou mantida com o Golden Path. Vale para projetos novos e para aplicações da Farmarcas que já existem.

Quem usa pode não ser desenvolvedor. Os documentos são em português simples, em linguagem de negócio, sem jargão técnico.

## Por que existe

O Spec Kit gera `spec.md`, `plan.md` e `tasks.md` por funcionalidade. Eles servem para construir, mas não respondem, meses depois: *o que este produto faz hoje? por que existe? o que mudou e quando?* Três documentos respondem isso e vivem junto com o código.

## Os três documentos

Ficam na pasta da aplicação (a pasta irmã do Golden Path, ou o repositório existente).

```text
<aplicacao>/
├── CHANGELOG.md
└── docs/
    ├── PRD.md
    ├── funcional/
    │   ├── README.md          índice dos módulos
    │   └── <modulo>.md        um por módulo ou tela
    └── decisoes/              opcional
        └── NNN-nome-curto.md
```

| Documento | Responde | Escopo | Quando muda |
|---|---|---|---|
| `docs/PRD.md` | Por quê, para quem, o que entra e o que fica de fora | O produto inteiro | Quando o escopo, o público ou os objetivos mudam |
| `docs/funcional/<modulo>.md` | O que o produto faz **hoje**: telas, fluxos, regras de negócio | Um módulo ou tela | A cada funcionalidade nova ou alterada que toque o módulo |
| `CHANGELOG.md` | O que mudou, quando e em qual versão | O histórico | A cada entrega |
| `docs/decisoes/` | Por que uma escolha foi feita, quando não é óbvia | Uma decisão | Quando surgir uma decisão que alguém vai estranhar depois |

### Relação com os arquivos do Spec Kit

| Arquivo do Spec Kit | Papel | Relação com a documentação viva |
|---|---|---|
| `specs/NNN-nome/spec.md` | O que **uma funcionalidade** vai fazer (histórico de construção) | Fonte para atualizar o PRD e o funcional. Não é substituído por eles. |
| `plan.md` / `tasks.md` | Como construir | Fora da documentação viva. Decisão técnica relevante vira item em `docs/decisoes/`. |

Regra de ouro: **o `spec.md` conta como a funcionalidade foi pedida; o funcional conta como o produto é hoje.** Se divergirem, vale o funcional, e quem mudou o comportamento atualiza os dois.

## Modelos

Fonte: `documentation/templates/`. Cópia para levar a outros projetos: `templates/docs/` (gerada por `scripts/sync-templates.sh`; não edite à mão).

| Modelo | Vira |
|---|---|
| `PRD.md` | `docs/PRD.md` |
| `FUNCIONAL-INDICE.md` | `docs/funcional/README.md` |
| `FUNCIONAL.md` | `docs/funcional/<modulo>.md` |
| `CHANGELOG.md` | `CHANGELOG.md` |
| `DECISAO.md` | `docs/decisoes/NNN-nome-curto.md` |

## Regras

1. **Linguagem de negócio.** Descreva o que a pessoa vê e o que o sistema decide. Tabelas, endpoints e bibliotecas ficam fora.
2. **Nunca invente.** O que não está no pedido, no código ou na resposta da pessoa vira `[A CONFIRMAR]`, não suposição.
3. **Um lugar para cada coisa.** Escopo no PRD, comportamento no funcional, histórico no changelog. Não repita o conteúdo entre eles; aponte com link.
4. **Documentação faz parte do pronto.** Funcionalidade nova ou alterada só termina com o funcional e o changelog atualizados (princípio X da [constituição](../.specify/memory/constitution.md)).
5. **Changelog em SemVer.** Funcionalidade nova é versão menor, correção é versão de correção, mudança que quebra o que existia é versão maior. Cada item aponta para a spec de origem quando houver.
6. **Termos do negócio.** Use o vocabulário que o time já usa. Em aplicação existente, mantenha os nomes que a documentação do time já adota.
7. **Correção pequena** (texto, cor, bug simples) não exige spec, mas se mudar algo que o funcional descreve, ele é atualizado e o changelog ganha uma linha em *Corrigido*.

## Procedimentos

| Atividade | Skill |
|---|---|
| Criar e manter PRD, funcional e changelog de um projeto | [`product-docs`](skills/product-docs/SKILL.md) |
| Gerar a primeira versão da documentação de uma aplicação que já existe | `docs-retrofit` (em desenvolvimento) |
