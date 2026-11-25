---
name: product-docs
description: Creates and maintains the living product documentation of an application — PRD, functional docs per module, CHANGELOG and optional decision records — in plain Brazilian Portuguese, tied to the Spec Kit flow. Use when starting a new application, after specify/implement of a feature, when a feature changes existing behavior, when releasing a version, or when the person asks for PRD, documentação funcional, changelog or "documentar o projeto".
---

# Documentação viva do produto

## Pré-requisito

Leia [DOCUMENTATION.md](../../DOCUMENTATION.md) antes. Ele define os documentos, onde ficam e as regras.

Esta skill **não** cobre aplicação existente sem documentação. Nesse caso use `docs-retrofit` quando existir, ou siga o passo "Aplicação existente" abaixo.

Todos os arquivos são criados **na pasta da aplicação**, nunca no repositório do Golden Path. Modelos em `templates/docs/` (cópia) ou `documentation/templates/` (fonte).

## Quando usar

| Momento | O que fazer |
|---|---|
| Aplicação nova, logo após `/speckit-specify` da primeira funcionalidade | Passo 1 |
| Funcionalidade nova ou alterada, antes de fechar `/speckit-implement` | Passos 2 e 3 |
| Entrega ou versão | Passo 3 |
| Decisão que alguém vai estranhar depois | Passo 4 |

**Não use** para escrever spec, plano ou tarefas (isso é do Spec Kit) nem documentação técnica de código.

## Passos

### 1. Criar a base (aplicação nova)

1. Crie `docs/PRD.md` a partir de `PRD.md`, `docs/funcional/README.md` a partir de `FUNCIONAL-INDICE.md` e `CHANGELOG.md` a partir de `CHANGELOG.md`.
2. Preencha o PRD com o que a pessoa já disse no pedido e no `spec.md`: problema, objetivo, quem usa, escopo, fora de escopo.
3. Tudo que faltar vira `[A CONFIRMAR]`. **Não pergunte além do limite de 2 perguntas de negócio por etapa** (`SPECKIT.md`). Se a dúvida for essencial, faça a pergunta; se não, deixe marcada.
4. Em "Funcionalidades" do PRD, liste cada funcionalidade com status `Planejada` e o link para o `spec.md`.

### 2. Atualizar o funcional

Para cada funcionalidade tocada:

1. Abra o módulo correspondente em `docs/funcional/`. Se não existir, crie a partir de `FUNCIONAL.md` e acrescente uma linha no índice.
2. Reescreva o que mudou para refletir **o comportamento atual** (não acrescente "agora também faz…").
3. Fontes, nesta ordem: `spec.md` da funcionalidade, o que foi realmente implementado, resposta da pessoa. Se o implementado divergir do `spec.md`, descreva o implementado e avise a pessoa.
4. Regras de negócio numeradas (`RN-1`, `RN-2`…), cada uma verificável. Não renumere regras existentes: acrescente no fim ou marque como removida.
5. Estados vazios, de erro e de carregamento entram na seção "Estados e mensagens".
6. Atualize `Última revisão` e o status do módulo.

### 3. Atualizar PRD e changelog

1. No PRD: ajuste o status da funcionalidade (`Planejada` → `No ar`), e revise escopo, perfis e métricas **só se** a funcionalidade os alterou. Atualize `Última revisão` e `Versão do produto`.
2. No `CHANGELOG.md`: acrescente itens em `[Não lançado]` sob `Adicionado`, `Alterado`, `Corrigido`, `Removido` ou `Segurança`. Texto para quem usa o produto, uma linha por mudança, com `(spec NNN-nome)` quando houver.
3. Ao fechar uma versão: troque `[Não lançado]` por `[x.y.z] — AAAA-MM-DD`, abra um novo `[Não lançado]` vazio e alinhe a versão no PRD. Escolha o número pela regra de SemVer do guia e avise a pessoa do que escolheu.

### 4. Registrar decisão (quando couber)

Só quando a escolha for não óbvia (trocou o padrão da constituição, descartou uma alternativa razoável, aceitou um limite). Crie `docs/decisoes/NNN-nome-curto.md` a partir de `DECISAO.md`, numerando em sequência. Uma página, linguagem simples.

### 5. Aplicação existente sem documentação

Enquanto `docs-retrofit` não existir:

1. Leia o repositório (README, telas, rotas, regras de negócio, migrations) e a documentação que o time já tiver.
2. Gere o PRD e um módulo funcional por área principal, **marcando como `Inferido do código — validar`** tudo que não estiver confirmado.
3. Apresente a lista de pontos `[A CONFIRMAR]` à pessoa e só marque o documento como `Validado` depois da resposta.
4. Crie o `CHANGELOG.md` com uma entrada `0.1.0` descrevendo o estado atual. Não reconstrua histórico passado que você não consegue comprovar.

## Fechamento

Termine no formato do `SPECKIT.md`, em linguagem simples:

```text
Escolhi: [o que foi documentado, em uma frase]
Por quê: [o motivo, em uma frase]
Posso seguir?
```

## Checklist

- [ ] Documentos criados na pasta da aplicação, não no Golden Path.
- [ ] `docs/PRD.md` com problema, objetivo, perfis, escopo e fora de escopo.
- [ ] Todo módulo tocado em `docs/funcional/` reflete o comportamento atual e está no índice.
- [ ] Regras de negócio numeradas e verificáveis.
- [ ] `CHANGELOG.md` com a mudança em `[Não lançado]` (ou na versão fechada) e link para a spec.
- [ ] Nada técnico (tabela, rota, biblioteca) nos documentos de negócio.
- [ ] Todo item duvidoso está como `[A CONFIRMAR]`, nada inventado.
- [ ] Datas e versão revisadas no PRD e nos módulos.
