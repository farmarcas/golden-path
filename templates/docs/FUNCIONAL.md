# [Nome do módulo ou tela]

> **Status**: No ar | Em desenvolvimento | Descontinuado
> **Última revisão**: [AAAA-MM-DD]
> **Origem**: `specs/NNN-nome/spec.md` (ou `Inferido do código — validar`, no caso de retrofit)

<!--
  Este documento descreve o que existe HOJE, em linguagem de negócio.
  Ele é reescrito quando a funcionalidade muda; o histórico fica no CHANGELOG.md.
  Não descreva código, tabelas ou endpoints. Descreva o que a pessoa vê e o que o sistema decide.
-->

## Para que serve
Uma ou duas frases: qual necessidade este módulo atende e para quem.

## Quem acessa
| Perfil | Pode | Não pode |
|---|---|---|
| [perfil] | [ver / criar / editar / excluir ...] | [restrição] |

## O que a pessoa vê
Descreva a tela de cima para baixo: cada bloco, campo, botão e o que ele mostra ou faz.

## Fluxos principais
### [Nome do fluxo, ex.: Criar pedido]
1. A pessoa [ação].
2. O sistema [resposta].
3. [...]

**Resultado esperado**: [o que está certo ao final].

## Regras de negócio
Numere. Cada regra deve poder ser verificada.

| # | Regra |
|---|---|
| RN-1 | [ex.: Pedido cancelado não entra no faturamento] |

## Estados e mensagens
| Situação | O que a pessoa vê |
|---|---|
| Carregando | [ex.: indicador de carregamento] |
| Sem dados | [mensagem] |
| Erro | [mensagem] |

## Dados exibidos e de onde vêm
| Informação | Significado | Origem (sistema ou área) |
|---|---|---|
| [ex.: Faturamento] | [definição de negócio] | [de onde vem] |

## O que este módulo não faz
- [limite conhecido, para evitar suposição errada]

## Pontos a confirmar
- [ ] [item inferido ou duvidoso que ainda precisa de validação]
