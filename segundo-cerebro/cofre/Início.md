---
tipo: painel
atualizado: 2026-10-09
---
> [!tip] Comece por aqui
> Painel central do segundo cérebro da Oyster. O combinado de como o Claude usa este cofre está em [[CLAUDE]].

## Frentes
- [[Oyster Deli]] — massas frescas artesanais: delivery, balcão e Clube Oyster
- [[Oyster Pasta Bar]] — salão, de quarta a sábado
- Consultoria B2B — [[Arena UFG]]

## Cozinha
[[Cozinha]] · [[Engenharia de Cardápio]] · [[Receituário Oyster Deli]] · [[Sugestões do Chef]] · [[Massa Especial do Mês]] · [[Padrões e Nomenclatura]] · [[Resumo Cozinha Oyster]] · [[Manual da Cozinha]] · [[Caderno de Referências]] · [[Equipamentos da Cozinha]]

### Fichas fora da meta (CMV acima de 26%)
![[Painel de Fichas.base#Fora da meta]]

## Oyster Prep — o app
**https://app.oprep.com.br** · o app guarda o número, o cofre guarda o porquê → [[Integração com o Oyster Prep]] · onde está cada coisa → [[Inventário do conhecimento]]

[Fichas técnicas](https://app.oprep.com.br/dashboard/fichas-tecnicas) · [Pré-preparos](https://app.oprep.com.br/dashboard/pre-preparos) · [Insumos](https://app.oprep.com.br/dashboard/cadastros/insumos) · [Fornecedores](https://app.oprep.com.br/dashboard/cadastros/fornecedores) · [Compras](https://app.oprep.com.br/dashboard/estoque/entrada-produtos) · [Cardápio](https://app.oprep.com.br/dashboard/cardapio) · [Relatórios](https://app.oprep.com.br/dashboard/relatorios) · [POPs](https://app.oprep.com.br/pops)

### Decisões grandes
```base
filters:
  and:
    - 'tipo == "decisao"'
views:
  - type: table
    name: Decisões
    limit: 10
    order:
      - file.name
      - note.status
      - note.area
      - note.revisar_em
    sort:
      - property: file.name
        direction: DESC
```

## Conselho
Reunião toda segunda, 9h · [[Pauta do Conselho]] · [[Regimento do Conselho]] · [[Quem é quem no Conselho]] · atas em `70 Conselho/Atas/` · [[Fontes Confiáveis do Conselho]] · [[Biblioteca da Oyster]]

## Projetos ativos
- [[Evento Jessica e Rafael]] — catering para 60 pessoas, menu único
- [[Implantação da gestão no Saipos]] — fichas, insumos, estoque e baixa automática
- [[Oyster Prep]] — app de gestão da Oyster
- [[Painel pessoal]] — agenda e radar de custos

## Áreas
[[CMV e Precificação]] · [[Ponto de Equilíbrio]] · [[Financeiro]] · [[Compras e Fornecedores]] · [[Equipe]] · [[Marketing]] · [[Tráfego Pago]] · [[Sistemas e Ferramentas]] · [[Integração com o Oyster Prep]]

## Conversas recentes
```base
filters:
  and:
    - 'tipo == "conversa"'
    - file.inFolder("15 Conversas")
views:
  - type: table
    name: Conversas
    limit: 10
    order:
      - file.name
      - note.assunto
    sort:
      - property: file.name
        direction: DESC
```

## Para revisar
Notas que o Claude montou a partir do que você já tinha contado. Confira cada uma e apague a tag `revisar` quando estiver certa — ela some desta lista.

```base
filters:
  and:
    - file.hasTag("revisar")
views:
  - type: table
    name: Para revisar
    order:
      - file.name
      - note.tipo
      - file.folder
```

## Atalhos
- **Capturar algo rápido:** Ctrl+N — a nota nasce em `00 Caixa de Entrada`
- **Nota do dia:** ícone de calendário na barra da esquerda
- **Usar um modelo:** Ctrl+P → digite "modelo" → escolha (Ficha Técnica, Pré-preparo, POP, Teste de Receita, Insumo, Nota de Compra, Decisão, Relatório B2B…)
