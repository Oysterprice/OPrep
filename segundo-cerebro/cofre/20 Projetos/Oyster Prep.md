---
tipo: projeto
status: ativo
area: "[[Sistemas e Ferramentas]]"
repositorio: github.com/Oysterprice/oyster-prep
atualizado: 2026-10-09
tags:
  - projeto
  - revisar
---
App de gestão da Oyster feito com o Claude Code — React + Vite (localhost:3000), no ar em ~~oyster-turnos.vercel.app~~ **https://app.oprep.com.br** (domínio próprio desde 15/09/2026; registrado em 09/10/2026), banco no Supabase. Roteiro de pôr no ar: `docs/ponha-no-ar.html`. Como o app conversa com este cofre: [[Integração com o Oyster Prep]].

## Como trabalhamos
- Fatias numeradas (e com letra, ex.: C3); cada uma mira **um** defeito e fecha com prova de tela no navegador.
- Defeito que aparece no meio de uma fatia vai para a fatia seguinte — nada de conserto "de carona".
- Prova que falha é refeita do zero. Vale contra o app rodando: carimbo do rodapé "Oyster Prep · hash · data/hora".
- Correção chega como dossiê com causa-raiz e código pronto para colar; conserta a **classe** do defeito, não o sintoma.
- Fatia nova espera a reconferência da anterior voltar.
- Migrations numeradas e configuração do painel do Supabase são do Marcus — o Claude não roda.

## Regras de produto
- Zero nunca aparece mudo: vem com o motivo ao lado. CMV sem compras lançadas = "a informar".
- "Mês não lançado" não é zero — nem nos gráficos.
- DRE e Painel Geral separados: simulação de CMV no DRE não contamina o Painel.
- Razão de estoque (kardex) só acrescenta: estorno cria lançamento novo; nada é apagado.
- O campo de cocção chama-se IC (índice de cocção), nunca FC → [[Padrões e Nomenclatura]]
- "Prateleira sobrando": prato que está nas Fichas e não no Cardápio (ou o contrário) tem de gerar aviso.
- Inativar pré-preparo em uso mostra em quantas receitas ele entra e exige digitar `INATIVAR`.
- Melhor não ter botão de seed/importação do que ter um que apague o trabalho de outra pessoa.
- Textos do app com voz humana, sem "cara de IA".
- Visual: entrada dos blocos escalonada e sutil (8px); com movimento reduzido a tela abre inteira de uma vez.

## Backup (Fase 19)
- Backup diário cifrado no GitHub Actions (90 dias de retenção) + ensaio automático.
- Só fecha com o ensaio **manual** de restauração, com o app na frente.
- Regra 3-2-1: terceira cópia mensal fora do GitHub, baixada à mão (disco externo ou nuvem diferente do Supabase).

## Fila
- [ ] Fechar a Fase 21 (inclui a fatia 10: "mês não lançado" × zero nos gráficos)
- [ ] Ensaio manual de restauração (fecha a Fase 19)
- [ ] Passphrase do backup

## Planejado
- Onboarding por tour interativo no app: faturamento → despesas → mão de obra → CMV ideal → cardápio → métricas completas.
- Trazer o radar do [[Painel pessoal]] para dentro do app: janela que se atualiza a cada login, com projeção e alertas de alta de insumo, chuva e tendências.
