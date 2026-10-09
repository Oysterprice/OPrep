---
tipo: decisao
data: 2026-10-09
assunto: Projeto Oyster Deli no Claude e a divisão entre as duas janelas
area: "[[Sistemas e Ferramentas]]"
status: decidida
origem: Marcus
revisar_em: 2026-11-09
atualizado: 2026-10-09
tags:
  - decisao
---
**Decisão:** abrir no app do Claude um projeto próprio, **Oyster Deli**, para a gestão da casa. O projeto "Controle e Gestão Oyster" fica só com o app **OPrep** (app.oprep.com.br). O projeto de **Consultoria B2B** só nasce quando aparecer o terceiro cliente.
**Quem decidiu:** Marcus, em 09/10/2026
**Área:** [[Sistemas e Ferramentas]] · [[Integração com o Oyster Prep]]

## Por quê
- Gestão da casa e desenvolvimento do app são conversas diferentes; misturadas, uma atrapalha a outra.
- Um projeto de consultoria com um cliente só ([[Arena UFG]]) é estrutura antes da hora.

## Como as duas janelas conversam
- **Projeto Oyster Deli → OPrep:** quando a gestão concluir que falta algo no sistema (relatório, tela, integração), o Marcus copia a frase para o projeto do OPrep.
- **OPrep → Oyster Deli:** quando o OPrep entregar algo que muda a operação (o resumo por e-mail, a importação da Saipos), o Claude de lá entrega um parágrafo pronto para colar no projeto Oyster Deli.
- Nenhum dos dois precisa saber como o outro funciona por dentro.

## O que vai no projeto Oyster Deli
**Habilidades:** os oito conselheiros e a reunião semanal (`conselho-*`), ficha técnica gerencial, Saipos, Yes Chef, docs, Excel, PDF, deep-research.
**Plugins da Anthropic:** manter Small Business e Operations. Tirar Product Management, Sales, Data e Productivity, que concorrem com os conselheiros e não sabem nada da casa.
**Conectores:** Google Drive, Gmail e Agenda.
**Arquivos do projeto:** as notas principais deste cofre, trocadas uma vez por mês. A lista do pacote está abaixo.

## Instruções do projeto (o bloco que o Marcus cola)
> [!warning] Conferir antes de colar
> O bloco diz **Curitiba**. O cofre inteiro diz que a casa é em **Londrina (PR)** → [[Oyster Deli]]. Se for Londrina, troque a palavra antes de colar.

```
Você é o braço de gestão da Oyster Deli, uma casa de massas artesanais em Curitiba, do Marcus. O Marcus é o dono, não programa, e precisa de respostas diretas, em português do Brasil, com a conta à mostra e a fonte de cada número.

As frentes da casa, e cada uma tem dono e ritmo:
1. Operação: compras, estoque, produção, POPs. Sistema: OPrep (app.oprep.com.br). Perguntas de custo, CMV, ficha técnica e preço usam as fórmulas do OPrep (fator de correção, custo médio ponderado, markup divisor, curva ABC por margem).
2. Vendas e caixa: Saipos (só PDV hoje). Nenhum número de custo do Saipos vale enquanto o estoque não for implantado lá.
3. Etiquetas e validade: Yes Chef.
4. Marketing e tráfego pago: Instagram, iFood, canais próprios, Meta Ads e Google Ads. O Marcus opera sozinho; o papel aqui é ensinar e planejar, nunca prometer resultado sem dado.
5. Conselho: reunião toda segunda às 9h, com os oito conselheiros (habilidades conselho-*). Toda decisão sai com parecer, risco apontado pelo Pessimista e ata.

Regras permanentes:
- Preço é por canal: balcão e iFood têm multiplicadores diferentes. Nunca decidir cardápio pela margem bruta do Saipos.
- Toda recomendação diz o que o Marcus faz, onde e em quanto tempo. Uma melhoria por vez, sem aumentar o mise en place da cozinha de três cozinheiros.
- Número sem fonte e data não entra em decisão. Se o dado não existe, dizer que não existe, não estimar calado.
- Os arquivos do projeto são o Cérebro da casa: ler antes de propor algo que já foi decidido.
- O desenvolvimento do OPrep não acontece aqui. Pedido de tela, correção ou relatório novo no sistema vai para a sessão do Code.
- Quando o Marcus trouxer um problema solto (tráfego, marketing, custo), primeiro dizer de qual frente ele é e qual conselheiro responde, depois responder.
```

**Primeira mensagem do projeto:**
```
Vamos começar. Leia os arquivos do projeto e me devolva, em uma página: (1) o que você entendeu de cada uma das cinco frentes e o que está faltando de informação em cada uma; (2) as três coisas que mais travam a casa hoje, na sua leitura; (3) um plano da primeira semana, com uma ação por dia, começando pelo tráfego pago e pelo marketing, que é onde eu mais tenho dificuldade. Não faça nada ainda, só o diagnóstico.
```

## O pacote mensal de arquivos
Montado em 09/10/2026. Para refazer no mês seguinte, copiar de novo estas notas, já atualizadas, e trocar no projeto:
- **Conselho:** as atas em `70 Conselho/Atas/` (todas), [[Regimento do Conselho]], [[Quem é quem no Conselho]], [[Pauta do Conselho]]
- **Cardápio:** [[Receituário Oyster Deli]], [[Sugestões do Chef]], [[Massa Especial do Mês]], [[Engenharia de Cardápio]]
- **Preço e dinheiro:** [[CMV e Precificação]], [[Ponto de Equilíbrio]], [[Financeiro]]
- **Casa e canais:** [[Oyster Deli]], [[Oyster Pasta Bar]], [[Tráfego Pago]], [[Marketing]], [[Equipe]]
- **Sistemas:** [[Sistemas e Ferramentas]], [[Integração com o Oyster Prep]], e o [[CLAUDE|manual]] (como "Manual do Cérebro")

Ficaram de fora de propósito: a [[Cartilha da Cozinha]] e o Manual da Cozinha (material de praça, longo), os 27 fichamentos, as notas dos membros do Conselho (as skills já carregam), Conversas e Diários, modelos, PDFs e a consultoria B2B. **"Planilha de canais" não existe no cofre**: o que há sobre canais está em [[Oyster Deli]], [[Ponto de Equilíbrio]] e [[CMV e Precificação]].

## Revisões
| Data | O que mudou | Por quê |
|---|---|---|
|  |  |  |
