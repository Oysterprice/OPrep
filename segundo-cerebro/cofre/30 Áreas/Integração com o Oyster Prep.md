---
tipo: area
atualizado: 2026-10-09
tags:
  - area
  - sistemas
  - revisar
---
Como o cofre e o app **Oyster Prep** (https://app.oprep.com.br) conversam. Regra curta: **o app guarda o número, o cofre guarda o porquê.** Área-mãe: [[Sistemas e Ferramentas]] · projeto: [[Oyster Prep]].

## O que manda em cada lado
| Assunto | Fonte de verdade no **app** | O que fica no **cofre** |
|---|---|---|
| Insumo (matéria-prima) | cadastro, unidade, fator de correção (FC), custo médio, saldo de estoque | por que esse insumo, marca ou corte; testes; ocorrências |
| Pré-preparo | composição, rendimento, custo padrão (pela ficha) e custo real (pela produção) | técnica, testes, decisões de validade e de método |
| Ficha técnica (prato) | composição, custo, CMV %, preço de venda, ficha que vai para a praça | desenvolvimento, por que entrou, histórico de mudanças, fotos de teste |
| Compra | a nota lançada (é ela que forma o custo) | cotação, negociação, problema com entrega — só o que foge do normal |
| Fornecedor | cadastro: CNPJ, contato, produtos ligados | avaliação, ocorrências, condições combinadas |
| POP | Manual de POPs (46 documentos, os vigentes saem impressos de lá) | ideia e rascunho de POP novo, até ele entrar no app |
| Faturamento, CMV do mês, folha, DRE | vendas, notas e cadastro de pessoas do app | o resumo do mês, com fonte e data, e o que se decidiu a partir dele |
| Consultoria B2B | — (o app é da Oyster) | cliente, escopo, relatórios e entregas → `50 Consultoria B2B/` |
| Conselho, Diário, Conversas, Biblioteca | — | tudo |

**Quando os dois discordam num número, vale o app** — ele recalcula pela receita e pelas notas; o cofre tem uma cópia com data. Quando discordam numa decisão ou num método, vale o cofre, que é o que o Marcus escreve e corrige.

## O ciclo de um prato
1. **Ideia e teste** → nota em `40 Cozinha/Desenvolvimento/` (modelo Teste de Receita). Aqui a receita mora no cofre.
2. **Aprovado** → cadastra no app: insumos novos, pré-preparos e a ficha técnica. A partir daqui **a receita mora no app**.
3. **Ficha no cofre** → nota em `40 Cozinha/Fichas Técnicas/` (modelo Ficha Técnica) com `app_codigo` e `app_tela` preenchidos. Ela guarda decisões e histórico, e os números como cópia datada.
4. **Mudou a receita?** → muda no app primeiro; no cofre entra só a linha em **Decisões** dizendo o que mudou e por quê.

## Como uma nota aponta para o app
Três propriedades, já nos modelos Ficha Técnica, Pré-preparo, Insumo, Fornecedor, POP e Nota de Compra:

| Propriedade | O que vai | Exemplo |
|---|---|---|
| `app_codigo` | o código do item no app (o app cria sozinho ao salvar) | `PP011` |
| `app_tela` | o endereço da tela no app | ver tabela abaixo |
| `app_conferido` | data em que os números da nota foram copiados do app | `2026-10-09` |

Endereços que funcionam hoje (precisa estar logado):

| O quê | Endereço |
|---|---|
| Ficha técnica de um prato | `https://app.oprep.com.br/dashboard/fichas-tecnicas?busca=<nome do prato>` |
| Pré-preparos | `https://app.oprep.com.br/dashboard/pre-preparos` |
| Insumos | `https://app.oprep.com.br/dashboard/cadastros/insumos` |
| Fornecedores | `https://app.oprep.com.br/dashboard/cadastros/fornecedores` |
| Entrada de produtos (compras) | `https://app.oprep.com.br/dashboard/estoque/entrada-produtos` |
| Uma nota fiscal conferida | `https://app.oprep.com.br/dashboard/estoque/notas/<id>` |
| Um POP do manual | `https://app.oprep.com.br/pops/manual/<id>` |
| Relatórios (CMV, compras, vendas, estoque) | `https://app.oprep.com.br/dashboard/relatorios` |
| Cardápio | `https://app.oprep.com.br/dashboard/cardapio` |

> [!note] Limite de hoje
> Só a ficha técnica abre direto pelo nome. Pré-preparo, insumo e fornecedor abrem na lista, e é preciso buscar. Abrir cada um direto pelo código é uma mudança pequena no app — fica como pedido, não foi feita.

## Os números do Painel de Fichas
O [[Painel de Fichas.base|Painel de Fichas]] calcula CMV %, preço sugerido e margem a partir de `custo_porcao` e `preco_venda`. Esses dois são **cópia do app**: ao copiar, anote a data em `app_conferido` e `fonte_custos: Oyster Prep, DD/MM/AAAA`. Nada de digitar custo de cabeça no cofre — custo sem nota lançada no app é "a informar".

## Metas: os dois lados precisam dizer o mesmo
- Cofre ([[CMV e Precificação]]): CMV alvo 26%, mão de obra 22%, Prime Cost 48%, lucro **15%** (era 17% até 09/10/2026).
- No app, a meta de lucro é editável por empresa (Configurações) e tem de estar em **15%**. Se a meta mudar, muda no app, em [[CMV e Precificação]] e nesta nota. Os números 0.26 e 0.924 do Painel de Fichas só mudam se mudar a meta de CMV ou a alíquota.

## Onde mais vive conhecimento da Oyster
Mapa completo em [[Inventário do conhecimento]].

## Decisões
| Data | Decisão | Por quê |
|---|---|---|
| 09/10/2026 | O app é a fonte de verdade dos números; o cofre, do porquê | evitar dois custos diferentes para o mesmo prato em dois lugares |
| 09/10/2026 | Toda nota de cadastro leva `app_codigo`, `app_tela` e `app_conferido` | achar o item no app em um clique e saber de quando é a cópia |
