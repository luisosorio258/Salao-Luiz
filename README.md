# Salão Luiz — Página de Agendamento

Página única (`salao-luiz.html`), estática e autocontida — sem dependências externas além das fontes do Google Fonts. Todas as fotos da galeria já estão embutidas no próprio arquivo (base64), então basta abrir o HTML em qualquer navegador ou subir para uma hospedagem simples (Netlify, GitHub Pages, Vercel, FTP, etc.).

**Artifact publicado:** https://claude.ai/code/artifact/851ffa28-f8e4-4dd4-83ca-7eced769a608

## Estrutura da página

1. **Topo (hero)** — nome, "Since 2021", botão "Agendar agora" em destaque e aviso de pico de demanda.
2. **Serviços** — 11 cards numerados (Nº 01–11), cada um com nome PT/EN, descrição, preço "from", duração e botão próprio de agendar.
3. **Galeria** — grade de 6 fotos reais do salão, com lightbox (toque/clique para ampliar; Esc ou clique fora fecha).
4. **A casa** — texto sobre o salão + 3 diferenciais (agenda pontual, produtos veganos, ambiente climatizado).
5. **Horário & Localização** — tabela de horários (destaca automaticamente o dia de hoje via JavaScript), endereço e link para o Google Maps.
6. **Barra fixa mobile** — botão "Agendar agora no WhatsApp" sempre visível no rodapé em telas pequenas.

## Serviços cadastrados

| Nº | Serviço | Preço | Duração |
|----|---------|-------|---------|
| 01 | Corte masculino (Men's Haircut) | 16€ | 35min–1h |
| 02 | Corte e barba (Cut and Beard) | 25€ | 1h |
| 03 | Cabelo médio (Medium Hair) | 24€ | 45min |
| 04 | Cabelo longo (Long Hair) | 29€ | 45min |
| 05 | Corte feminino (Women's Haircut) | 20€ | 35min–1h |
| 06 | Escova (Brushing) | 10€ | 35min–1h |
| 07 | Coloração (Color) | 22€ | 1h–1h40min |
| 08 | Highlights | 60€ | 1h30min–2h |
| 09 | Balayage | 110€ | 1h–2h |
| 10 | Hidratação (Treatment) | 26€ | 50min–1h |
| 11 | Penteado (Hair Style) | 30€ | 1h–1h30min |

## Agendamento via WhatsApp

- Número: **961944270** (Portugal, `+351`), usado como `wa.me/351961944270`.
- Todo botão de agendar (topo, cada serviço e a barra fixa mobile) monta o link do WhatsApp em tempo real via JavaScript, preenchendo automaticamente serviço e preço:
  > Olá! Quero agendar **[Serviço]** ([Preço]). Meu nome é ___ e prefiro [dia] às [hora].
- O botão do topo e a barra fixa usam uma mensagem genérica (sem serviço/preço), para quem quer combinar direto.
- `[dia]`, `[hora]` e `___` ficam como placeholders literais — o cliente edita antes de enviar no WhatsApp.

## Galeria — fotos e créditos

Fotos fornecidas pelo usuário (pasta `Downloads/salao`, formato `.avif`), convertidas para JPEG (1200×1500, qualidade 78, cover 4:5) com a biblioteca `sharp`, e embutidas como `data:image/jpeg;base64` diretamente no HTML. Distribuição:

| Foto original | Legenda na galeria |
|---|---|
| `764e97ca-...avif` | Corte masculino |
| `6e6ae9e7-...avif` | Corte feminino |
| `f6c2e6f6-...avif` | Coloração |
| `9893d08c-...avif` | Balayage |
| `bb0a9352-...avif` | Escova |
| `0a7eda87-...avif` | Penteado |

## Horário

| Dia | Horário |
|---|---|
| Segunda | Fechado |
| Terça a Sexta | 10:30 – 20:00 |
| Sábado | 10:30 – 19:00 |
| Domingo | Fechado |

**Endereço:** Rua dos Mártires da Liberdade, 336, Cedofeita, Porto.

## Visual

- Tema escuro premium com acento dourado único (`#c89b3c` no modo escuro / `#a1791f` no modo claro — a página se adapta ao tema do navegador/host).
- Tipografia: **Fraunces** (display/serifada, títulos), **Work Sans** (corpo/botões), **JetBrains Mono** (preços, horários, rótulos — estilo "menu de preços").
- Cards de serviço em formato "ticket", numerados, com divisórias finas.
- Totalmente responsivo: 3 colunas de serviços/galeria no desktop, 1–2 colunas no mobile, com barra de agendar fixa no rodapé em telas pequenas.

## Histórico de alterações

1. **Versão inicial** — estrutura completa (hero, 11 serviços, galeria com placeholders SVG gerados, "a casa", horário/localização, rodapé), todos os botões de WhatsApp funcionais e testados (14 links verificados, cada um com serviço/preço corretos), lógica de "dia de hoje" no horário, mobile e desktop testados no navegador.
2. **Correção**: espaço quebrado no rodapé ("SalãoLuiz" grudado) causado por `display:flex` colapsando espaço em branco entre texto e `<span>` — trocado por `text-align:center`.
3. **Correção**: botão do menu no mobile mostrava só "agora" (a palavra "Agendar" estava escondida por engano) — invertido para esconder " agora" e manter "Agendar" sempre visível.
4. **Galeria com fotos reais** — as 6 fotos placeholder foram substituídas pelas fotos reais do salão (fornecidas pelo usuário), convertidas de AVIF para JPEG e embutidas em base64 no próprio arquivo, mantendo o mesmo comportamento de lightbox.

## Como publicar

O arquivo é 100% autocontido — não precisa de build, servidor ou passos extras. Basta:
- Abrir `salao-luiz.html` direto no navegador, ou
- Subir o arquivo para qualquer hospedagem estática (GitHub Pages, Netlify, Vercel, FTP tradicional, etc.).
