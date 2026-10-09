---
tipo: manual
atualizado: 2026-10-09
---
# Manual do Claude neste cofre

Este cofre é o **segundo cérebro da Oyster** — Oyster Deli, Oyster Pasta Bar e Consultoria B2B. O Marcus escreve aqui; o Claude lê para ter contexto e escreve para registrar o trabalho. Este arquivo é o combinado entre os dois: mudou a regra, muda aqui.

Local no computador do Marcus: ~~`C:\Users\user\Desktop\OYSTER DELLI\Oyster Cerebro`~~ `C:\Users\user\OYSTER\Oyster Cerebro` (mudou em 15/09/2026; a pasta antiga no Desktop ficou só com o `.obsidian/`, corrigido em 09/10/2026)

## Três regras de ouro
1. **Toda conversa fica registrada** em `15 Conversas/` (ver "Conversas").
2. **Tudo que é de cozinha mora em `40 Cozinha/`**: ficha, pré-preparo, POP, mise en place, teste de receita, técnica, equipamento, segurança dos alimentos, cardápio. Se uma conversa gerou algo de cozinha, isso vai também para a nota certa de lá — não fica só na conversa.
3. **Nada se apaga**: acrescenta, risca ou move para `99 Arquivo/`.

## Ao começar uma tarefa
1. Ler este manual e a nota [[Início]].
2. Abrir as notas do assunto (projeto, área, cliente, ficha) antes de responder.
3. Olhar o Diário e as Conversas dos últimos dias para ver o que ficou pendente.
4. Se o cofre e a memória do Claude discordarem, vale o cofre — é o que o Marcus vê e corrige. Na dúvida, perguntar.

## Onde cada coisa mora
| Pasta | O que vai |
|---|---|
| `00 Caixa de Entrada/` | captura rápida, ainda sem lugar |
| `10 Diário/` | uma nota por dia (`AAAA-MM-DD`) e as reuniões (`AAAA-MM-DD Reunião <assunto>`) |
| `15 Conversas/` | uma nota por conversa com o Claude (`AAAA-MM-DD <assunto>`) |
| `20 Projetos/` | tem objetivo e data para acabar |
| `30 Áreas/` | responsabilidade contínua: negócio, finanças, equipe, marketing, sistemas; fornecedores em `30 Áreas/Fornecedores/` (insumos com história em `Fornecedores/Insumos/`), compras fora do normal em `30 Áreas/Compras/`, decisões grandes em `30 Áreas/Decisões/` |
| `40 Cozinha/` | tudo de cozinha — mapa em [[Cozinha]] |
| `50 Consultoria B2B/` | uma nota por cliente; relatórios em `50 Consultoria B2B/Relatórios/` |
| `60 Recursos/` | referência geral, a [[Biblioteca da Oyster]] (livros e fichamentos) e anexos |
| `70 Conselho/` | [[Regimento do Conselho]], membros, [[Pauta do Conselho|pauta]] e atas |
| `90 Modelos/` | modelos das notas |
| `99 Arquivo/` | o que terminou ou saiu de uso |

Projeto × área: se tem data para acabar, é **projeto**; se é para sempre, é **área**.

## Como escrever
- Português do Brasil, direto, sem floreio. No texto: R$ 12,50 e 11/09/2026. Em nome de arquivo e em propriedade de data: 2026-09-11.
- Nota nova nasce de um modelo de `90 Modelos/` e mantém as propriedades dele.
- Propriedade numérica usa **ponto** decimal (`12.5`) — o Obsidian só faz conta assim. No texto, vírgula normal.
- Toda nota aponta com `[[link]]` para a área ou o projeto a que pertence.
- Nome do arquivo = nome do prato, cliente ou projeto do jeito que o Marcus fala.
- Decisão vira linha na tabela **Decisões** (data · decisão · por quê). Decisão revista não se apaga: risca (~~assim~~) e a nova entra embaixo.
- Nota escrita pelo Claude sem conferência do Marcus leva a tag `revisar`; o Marcus tira a tag quando conferir.
- Número sem fonte não entra: sem dado, escreve "a informar" — nunca zero mudo.

### Valores de `status`
- projeto: ativo · pausado · concluído
- ficha-tecnica: rascunho · ativa · fora do cardápio
- teste-receita: proposta · em estudo · em teste · aprovado · descartado
- cliente-b2b: proposta · ativo · concluído
- evento: orçamento · fechado · realizado

### Regras permanentes de material de cozinha
Valem para toda ficha, apostila, cartilha ou manual que sair daqui — do Conselho ou do Claude:
1. **Rendimento em toda ficha, sem exceção.** Quanto sai de produto pronto, na unidade certa. Ficha sem rendimento não entra.
2. **Nada em inglês.** Só ficam sem tradução os nomes próprios (autor, título de livro, instituição, na linha de fonte) e os termos que a brigada já usa — mise en place, roux, nappage, brunoise, mirepoix, confit, ragu, mantecatura, sous vide.
3. **Tudo por quilo ou por litro**, em gramas e mililitros. Percentual sempre dizendo sobre o que incide. Nunca "a gosto", nunca colher, nunca xícara.
4. **Material de praça é curto.** O cozinheiro consulta de pé, no meio do turno. Seleção do que é fundamental, em tabela e ficha curta — o compêndio longo fica no escritório. A [[Cartilha da Cozinha]] é o padrão de referência deste formato.

### Propriedades da ficha técnica
`classe` (prato ou pre-preparo) · `categoria` · `casa` · `codigo` · `status` · `rendimento` + `unidade_rendimento` · `custo_total_receita` · `custo_porcao` · `preco_venda` · `vendas_mes` · `curva_abc` · `matriz` · `fonte_custos` (origem e data dos custos) · `planilha` · `atualizado`. O [[Painel de Fichas.base|Painel de Fichas]] calcula CMV %, faixa, preço sugerido, margem e MC do mês a partir delas.

## Integração com o Oyster Prep (combinado em 09/10/2026)
O app (https://app.oprep.com.br) guarda o número; o cofre guarda o porquê. Detalhe em [[Integração com o Oyster Prep]].
- Custo, CMV, preço, composição, rendimento, saldo e notas de compra: **vale o app**. O cofre guarda cópia com data em `app_conferido`.
- Nota de ficha, pré-preparo, insumo, fornecedor e POP leva `app_codigo` e `app_tela` para abrir o cadastro no app.
- Prato em teste mora no cofre; aprovado, a receita passa para o app e o cofre guarda decisões e histórico.

## Conversas
Ao fim de cada conversa com o Marcus (ou quando ele pedir), criar ou atualizar a nota em `15 Conversas/` pelo modelo **Conversa**:
- no topo: resumo, decisões, entregas, pendências e notas que mudaram;
- embaixo: a conversa na íntegra — mensagens do Marcus e respostas do Claude, sem os bastidores técnicos (buscas, comandos, arquivos intermediários);
- linkar a conversa no Diário do dia.
Conversa que aconteceu longe do cofre (celular, claude.ai) é registrada na próxima vez que o cofre estiver conectado, com o que se tiver dela.

## Quando o Claude escreve (combinado em 11/09/2026)
**Decisão confirmada pelo Marcus entra no cofre sempre.** Ele confirma toda decisão que toma; o Claude anota e registra na nota do assunto e no Diário. Se a decisão foi confirmada longe do cofre (celular, claude.ai), ela é lançada no primeiro trabalho com o cofre conectado, com a marca "(decidido em DD/MM, registrado em DD/MM)". Quando a decisão e o registro caem no mesmo dia, fica só uma data — duas datas só quando houve atraso.

Ao terminar uma tarefa relevante:
1. Atualiza a nota do assunto: decisões, números e próximos passos.
2. Deixa um resumo curto no Diário do dia, em **Registro das sessões com o Claude** (cria a nota do dia pelo modelo **Diário** se ela ainda não existir).
3. Registra a conversa em `15 Conversas/`.
4. O que não tiver lugar certo vai para `00 Caixa de Entrada/`.

## Conselho
- Sete conselheiros — Marketing, Pessimista, Estrategista, Confeiteiro, Saucier, Financeiro e Chef de Criação —, cada um com skill própria (`conselho-...`). Regras em [[Regimento do Conselho]].
- Reunião toda segunda às 9h, com ata pronta em `70 Conselho/Atas/`: alertas, recomendações, a Sugestão do Chef de sábado e, na última reunião do mês, a Massa Especial do mês seguinte. Quem decide é o Marcus.
- O Marcus anota assuntos para a reunião na [[Pauta do Conselho]].

## Limites
- Nunca apagar nem reescrever texto do Marcus: acrescentar, riscar ou mover para `99 Arquivo/`.
- Nunca guardar senha, token, dado de cartão ou de conta bancária no cofre.
- Número que vem de fora (Saipos, planilha, nota fiscal, cotação) leva a origem e a data ao lado.
- Dado de exemplo sempre identificado como exemplo.
- Não mexer em `.obsidian/` sem avisar o Marcus.
- Os números vivos ficam nos sistemas da casa — **Stone** (faturamento de cartão e Pix, taxas e prazos), **DDA do banco** (contas a pagar e despesas fixas), **Saipos** (vendas por canal e por item, compras) e **Oyster Prep** (turnos e folha; fichas, CMV e DRE quando pronto). O cofre guarda método, decisões, histórico e o resumo dos números, sempre com fonte e data. Mapa completo em [[Ponto de Equilíbrio]].

## Parâmetros da casa
Detalhe em [[CMV e Precificação]].
- Prime Cost 48% = mão de obra 22% + compra 26%, sobre o faturamento bruto; despesas até 35% (com Simples 6% e maquininha 1,6% dentro); lucro ~~17%~~ **15%** (decidido pelo Marcus em 09/10/2026); os 2 pontos que saíram do lucro ainda não têm destino → [[CMV e Precificação]]
- CMV alvo de 26% → preço sugerido = custo da porção ÷ 0,26 (≈ custo × 3,85)
- Faixas: 🟢 até 26% · 🟡 de 26% a 30% · 🔴 acima de 30%
- Cozinha com 3 cozinheiros: prato novo tem de caber nessa brigada → [[Equipamentos da Cozinha]]
