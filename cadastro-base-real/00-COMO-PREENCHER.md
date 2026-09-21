# Cadastrar a base real da Oyster Deli no app — o roteiro

Levantado em 21/09/2026, lendo o código do app que está no ar em
`app.oprep.com.br`. O que está escrito aqui foi conferido no código, não
suposto; onde eu não pude medir, está dito com todas as letras.

---

## O que descobri antes de montar as planilhas

**O repositório `OPrep` está vazio.** O app que está no ar é o `oyster-prep`.
Foi nele que li tudo. (O domínio `oprep.com.br` aponta para o projeto
`oyster-prep` no Vercel — é o mesmo sistema, nome diferente.)

**Três dos cinco cadastros têm importação em massa, e cada um com um formato
diferente.** Não existe uma importação única. É por isso que são seis
planilhas e não uma com seis abas.

| cadastro | como entra | formato |
|---|---|---|
| Fornecedores | **tela a tela** — não tem importação | — |
| Matérias-primas | arquivo Excel | 17 colunas numa aba `INSUMOS` |
| Embalagens | arquivo Excel | as mesmas 17 colunas |
| Pré-preparos | arquivo Excel | **uma aba por pré-preparo** |
| Fichas técnicas (pratos) | **colar** do Excel | 6 colunas, 1 linha por ingrediente |
| Compras (o custo) | arquivo Excel | 16 colunas numa aba `COMPRAS` |

**As planilhas 02, 03 e 06 foram geradas pelo código do próprio app**, não
escritas por mim à mão. São o mesmo arquivo que o botão "Baixar modelo" produz,
só que vazio em vez de vir com os dados fictícios dentro. Conferi depois: o
cabeçalho bate coluna por coluna com o que o app espera, e uma linha preenchida
passa pela validação dele sem erro nem aviso.

---

## 🔴 As três coisas que mudam o plano

### 1. Cadastrar insumo NÃO define preço

Está escrito na aba de instruções do próprio app: *"Custo médio, último custo e
saldo NÃO têm coluna aqui, e é de propósito: eles vêm do razão de estoque, na
entrada da nota. Cadastrar um insumo nunca definiu preço — o preço vem da
primeira compra."*

Quer dizer: você pode cadastrar as 200 matérias-primas hoje e **o CMV de todos
os pratos vai dar zero**, porque nenhum insumo tem custo. O custo entra pela
planilha **06 — COMPRAS**, que é uma entrada de nota fiscal.

É por isso que a 06 existe e é o último passo. Sem ela o sistema fica bonito e
não responde a pergunta que interessa.

### 2. Prato que leva pré-preparo não pode ser importado

A importação de fichas só aceita ingrediente que seja **matéria-prima**. Se o
prato leva um molho da casa, uma base, uma massa sua, a linha é recusada.

Esses pratos precisam ser montados na tela, um por um. Sugestão: separe o
cardápio em duas listas antes de começar — os que só levam MP (vão pela
colagem, rápido) e os que levam pré-preparo (vão na mão).

### 3. Pré-preparo importado entra pela metade

A importação traz os **ingredientes** certos, mas carimba rendimento `1 KG` e
categoria `Importado` em todos. Depois de importar, cada pré-preparo precisa
ser aberto na tela para você declarar o rendimento de verdade (quanto o lote
rende), a unidade e a categoria.

O rendimento errado joga o custo do pré-preparo — e o custo de todo prato que
o leva — para o lugar errado. Não dá para pular.

---

## A ordem, e por que ela é essa

Cada passo depende do anterior. Fora de ordem, o sistema recusa a linha ou
aceita com o vínculo em branco.

```
1. FORNECEDORES   →  a matéria-prima cita o fornecedor pelo nome ou CNPJ
2. MATÉRIAS-PRIMAS →  o pré-preparo e o prato citam o insumo pelo nome
3. EMBALAGENS      →  (pode ser junto com a 2, não depende de nada novo)
4. PRÉ-PREPAROS    →  citam matéria-prima
5. FICHAS TÉCNICAS →  citam matéria-prima (e pré-preparo, esses na tela)
6. COMPRAS         →  é o que dá custo a tudo que está acima
```

---

## Passo a passo, com onde clicar

### 1 · Fornecedores — na tela, um por um

**Onde:** `app.oprep.com.br` → menu **Cadastros** → **Fornecedores** → botão
**Novo fornecedor**.

Preencha a planilha `01-FORNECEDORES.xlsx` primeiro, para ter tudo à mão e para
os nomes ficarem consistentes. Depois digite na tela.

**Só o nome é obrigatório.** Mas dois campos valem o esforço:
- `documento` (CNPJ, só números) — o app confere o dígito verificador. CNPJ
  errado é recusado na hora, o que é bom: evita fornecedor duplicado.
- `lead_time_dias` — sem ele o ponto de pedido não calcula e o alerta de
  ruptura fica mudo.

⚠️ **Fornecedor não pode ser apagado, só inativado.** É de propósito: ele é a
origem do custo médio, e apagá-lo faria o custo dos meses anteriores perder a
procedência.

### 2 · Matérias-primas — planilha

**Onde:** **Cadastros** → **Insumos** → botão de **importar**.

Preencha `02-MATERIAS-PRIMAS.xlsx`, aba **INSUMOS**. A aba **INSTRUCOES** do
próprio arquivo explica cada coluna — ela veio do app, não de mim.

**As duas colunas que mais erram:**

- `fator_conversao_compra` — quantas unidades de **estoque** cabem em **uma** de
  compra. Caixa com 12 unidades = 12. Comprou e estoca igual = 1.
  Fator errado multiplica saldo e custo, e ninguém percebe.
- `fator_correcao` (FC) — peso **bruto** ÷ peso **líquido**, **nunca menor que
  1**. 1 kg comprado que rende 800 g limpos = **1,25**, não 0,8. É o campo
  direto da meta de 15%: ele é o que diz quanto do que você paga vira comida.

**Obrigatórias numa linha nova:** `nome` e `unidade_estoque`.
`unidade_estoque` só aceita **KG, L ou UN** — g e ml viram kg e l, o resto vira
UN.

**`codigo` em branco = insumo novo**, o sistema numera (MP001, MP002…).
**Código preenchido = alterar aquele insumo.**

⚠️ **Célula em branco numa linha que já existe significa MANTÉM, nunca apaga.**

⚠️ **Não deixe a aba INSUMOS vazia.** O app recusa com "A aba INSUMOS está
vazia — só tem o cabeçalho". É a mensagem certa, não um defeito.

### 3 · Embalagens — mesma planilha, outra tela

**Onde:** **Cadastros** → **Embalagens** → importar.

`03-EMBALAGENS.xlsx` é a mesma planilha. Muda só o prefixo do código (EMB).

### 4 · Pré-preparos — planilha com uma aba por preparo

**Onde:** **Pré-preparos** → botão **Importar**.

`04-PRE-PREPAROS.xlsx`: **o nome da aba é o nome do pré-preparo**. Dentro de
cada aba, uma linha por ingrediente, com as colunas
`ingrediente | quantidade | unidade`.

🔴 **A aba `APAGUE-ESTA-ABA-EXEMPLO` tem de sair antes de você subir o
arquivo.** O app marca **todas** as abas para importar por padrão — se ela
ficar, você ganha um pré-preparo chamado "APAGUE-ESTA-ABA-EXEMPLO" com tomate
pelado dentro. (Dá para desmarcar na tela também, mas apagar é mais seguro.)

Depois de importar: abra cada pré-preparo e corrija **rendimento**, **unidade**
e **categoria** — ver o ponto 3 lá em cima.

### 5 · Fichas técnicas — colando, não subindo arquivo

**Onde:** **Fichas Técnicas** → **Importar em lote**.

`05-FICHAS-TECNICAS.xlsx`, aba **FICHAS**. Selecione as linhas no Excel
(com o cabeçalho), **Ctrl+C**, e cole na caixa do app. Ele mostra a prévia antes
de gravar.

Seis colunas, nesta ordem exata:
`nome_prato | categoria | preco_venda | ingrediente | quantidade | unidade`

**Uma linha por ingrediente.** Linhas com o mesmo `nome_prato` viram um prato
só. Repita o nome do prato em todas as linhas dele; `categoria` e `preco_venda`
só precisam aparecer na primeira.

`ingrediente` tem de ser o nome **exato** de uma matéria-prima já cadastrada.
`quantidade` é a quantidade **líquida** que entra no prato — 120 g de arroz se
escreve `0,12` com unidade `KG`.

### 6 · Compras — o passo que dá custo a tudo

**Onde:** **Estoque** → **Entrada de Produtos** → importar.

`06-COMPRAS-CUSTO-INICIAL.xlsx`, aba **COMPRAS**. Uma linha por item comprado.
Itens da mesma nota repetem o mesmo fornecedor e o mesmo `documento`.

Isto é uma **entrada de estoque de verdade**: gera movimento no razão, forma o
custo médio ponderado e é o que faz o CMV existir. Lance as últimas notas reais
de cada insumo — quanto mais recentes, mais verdadeiro fica o custo.

⚠️ `documento` (o número da nota) é o que impede importar a mesma compra duas
vezes. Não deixe em branco.

---

## Como tirar os dados fictícios

**Pratos e pré-preparos:** dá para excluir na tela, no botão de excluir de cada
um. O app confere o histórico antes e recusa se houver venda, movimento de
estoque, nota, ordem de produção ou uso como ingrediente de outra ficha.

Por isso a ordem importa: **apague os pratos primeiro, depois os
pré-preparos** — um pré-preparo usado dentro de um prato não sai enquanto o
prato existir.

**Matérias-primas e fornecedores:** a tela **não apaga, só inativa**. Insumo
inativo some das listas e para de aparecer no seletor de ingredientes, mas
continua no banco. Para uma base nova isso basta.

🔴 **Apagar insumo de verdade exige SQL no Supabase, e quem roda isso é você.**
Se decidir por esse caminho, eu preparo o bloco pronto para colar, com um
`select` de conferência no fim. Não mexo no banco daqui.

⚠️ **Uma coisa que eu não pude medir:** quanto de dado fictício ainda está lá.
O registro da última limpeza (18/09) diz que os movimentos de estoque foram
zerados e o cadastro ficou — algo em torno de 89 itens. Mas isso é o que o
arquivo de migração afirma, não o que o banco respondeu hoje. Antes de apagar
qualquer coisa, abra **Cadastros → Insumos** e **Fichas Técnicas** e veja o que
tem lá.

---

## O que eu preciso de você para seguir

1. **Quer apagar os itens fictícios ou aproveitar os que servirem?** Se algum
   insumo fictício tem o nome certo, editar é mais barato que apagar e recriar.
2. **Por onde começamos:** a lista de fornecedores ou a de matérias-primas?
3. Se quiser, me passe uma foto ou um arquivo do que já existe em papel
   (lista de compras, fichas antigas, planilha do Saipos) — eu transformo no
   formato dessas planilhas em vez de você redigitar.

---

*Levantado por Claude em 21/09/2026, lendo o código de `oyster-prep`.
As planilhas 02, 03 e 06 foram geradas pelo código do próprio app e conferidas
de volta pela validação dele.*
