# PRD — Campanha Dia das Mães
## Promoção Interativa com Roleta de Prêmios
**Ótica | Versão 1.0 | 2025**

---

## 1. Visão Geral do Projeto

Este documento descreve os requisitos para o desenvolvimento de um site promocional interativo para a campanha de Dia das Mães da ótica. A campanha tem como objetivo atrair clientes via anúncios patrocinados e convertê-los em compradores através de uma experiência gamificada e divertida.

> 🎯 **Objetivo Principal:** Transformar cliques em anúncios em visitas presenciais à loja, utilizando frases icônicas de mãe + roleta de prêmios para criar engajamento emocional e urgência de compra.

### 1.1 Escopo
- Página 1 — Landing Page (Escolha de Frase)
- Página 2 — Roleta de Prêmios
- Página 3 — Tela de Prêmio Ganho + Redirecionamento para WhatsApp

### 1.2 Fora do Escopo
- Sistema de cadastro ou banco de dados de participantes
- Painel administrativo
- Integração com sistema de estoque

---

## 2. Fluxo Completo do Usuário

O usuário percorre exatamente 3 etapas desde o clique no anúncio até a chegada na loja:

| Etapa | Descrição | Ação do Usuário |
|-------|-----------|-----------------|
| 01 | Clica no anúncio (Instagram / Facebook / TikTok) e é redirecionado para a Landing Page | Visualiza a página com as frases de mãe |
| 02 | Lê as frases e identifica a favorita da sua mãe | Clica em uma das frases |
| 03 | É redirecionado para a Página da Roleta com a frase escolhida salva | Visualiza a roleta animada |
| 04 | Gira a roleta e aguarda o resultado | Clica no botão "Girar" |
| 05 | Vê o prêmio ganho com a mensagem personalizada | Lê o prêmio e a frase escolhida juntos |
| 06 | Clica em "Garantir Meu Prêmio" | É redirecionado para o WhatsApp da loja com mensagem pré-preenchida |

---

## 3. Página 1 — Landing Page (Frases de Mãe)

### 3.1 Objetivo
Criar conexão emocional imediata. O usuário se identifica com as frases e sente que o presente é feito especialmente para a mãe dele.

### 3.2 Conteúdo

**Título sugerido:**
> "Qual frase a sua mãe mais fala?" — Escolha uma e ganhe um presente especial para ela!

**Lista de Frases (Cards Clicáveis):**

| # | Frase |
|---|-------|
| 01 | Você não é todo mundo… |
| 02 | Se eu for aí e achar… |
| 03 | Não vai, eu já disse… |
| 04 | Me avisa quando chegar… |
| 05 | Eu te amo filho(a) |
| 06 | Não corre não que a pisa é maior… |
| 07 | Enquanto morar debaixo do meu teto… |
| 08 | Na volta a gente compra… |
| 09 | Tenho orgulho de você… |
| 10 | Eu só quero seu bem… |
| 11 | Eu avisei, mais não me escuta… |
| 12 | Se eu contar até três… |
| 13 | Sai de perto dessa TV que estraga as vista… |
| 14 | Só vive na rua, parece que não tem casa… |
| 15 | Quando chegar em casa a gente conversa… |
| 16 | Vai com Deus, Deus te proteja… |

### 3.3 Comportamento dos Cards
- **Hover:** card muda de cor / cresce levemente (efeito `scale`)
- **Click:** salva a frase no `sessionStorage` e redireciona para a Página 2
- **Responsivo:** 2 colunas no mobile, 3–4 colunas no desktop

### 3.4 Identidade Visual
- Tema: Dia das Mães — **preto, dourado e branco**
- Fonte: moderna e legível (ex: Poppins ou Nunito)
- Emojis podem reforçar emoção nos cards (ex: 💛 🌷 ❤️)
- Nome/logo da ótica visível no topo

---

## 4. Página 2 — Roleta de Prêmios

### 4.1 Objetivo
Gerar antecipação e urgência através da gamificação. O usuário sente que "ganhou" algo valioso e fica motivado a ir até a loja.

### 4.2 Elementos da Página
- Frase escolhida na Página 1 exibida no topo (ex: *"Você escolheu: Vai com Deus, Deus te proteja…"*)
- Roleta animada em destaque centralizado
- Botão **"GIRAR A ROLETA"** — grande, colorido e chamativo
- Texto motivador: *"Todo mundo ganha! Gire e descubra seu prêmio 🎁"*

### 4.3 Prêmios da Roleta

| Prêmio | Descrição | Peso Sugerido |
|--------|-----------|---------------|
| R$ 50 de desconto | Desconto em óculos solar | Alta (30%) |
| R$ 100 de desconto | Desconto em óculos solar | Alta (25%) |
| R$ 150 de desconto | Desconto em óculos solar | Média (20%) |
| R$ 200 de desconto | Desconto em óculos solar | Média (15%) |
| R$ 250 de desconto | Desconto em óculos solar | Baixa (7%) |
| R$ 300 de desconto | Desconto em óculos solar | Baixa (3%) |
| Óculos Solar + R$ 100 | Óculos solar completo + desconto adicional | Extra (0%) |

> ⚙️ **Nota Técnica:** Os pesos controlam a probabilidade de cada prêmio ser sorteado e podem ser ajustados no código (array de pesos da roleta). O prêmio "Óculos + R$100" pode ter peso 0 para não aparecer normalmente, sendo ativado pontualmente.

### 4.4 Comportamento da Roleta
- Ao clicar em "Girar", a roleta anima por 3–5 segundos com desaceleração gradual
- O botão fica **desabilitado** durante a animação (evita cliques duplos)
- Ao parar, exibe o prêmio em destaque com animação de confete
- Após 1,5 segundos, redireciona automaticamente para a Página 3
- A roleta só pode ser girada **UMA vez** por sessão (`sessionStorage`)

---

## 5. Página 3 — Tela do Prêmio Ganho

### 5.1 Objetivo
Confirmar o prêmio com entusiasmo, exibir a frase personalizada da mãe e converter o usuário em visita/venda via WhatsApp.

### 5.2 Elementos da Página
- 🎉 Animação de celebração (confete, estrelas ou corações)
- Título: **"Parabéns! Você ganhou!"**
- Prêmio em destaque: ex — *"R$ 150 de desconto em óculos solar"*
- Frase da mãe escolhida em destaque: ex — *"Vai com Deus, Deus te proteja" 💛*
- Texto: *"Mostre essa tela na loja e resgate seu prêmio. Válido até [DATA]."*
- Botão principal: **"CLIQUE PARA GARANTIR SEU PRÊMIO"**

### 5.3 Mensagem WhatsApp (Pré-preenchida)

> Olá! Participei da promoção Dia das Mães da Ótica e ganhei: **[PRÊMIO]**. Minha frase favorita foi: *"[FRASE ESCOLHIDA]"*. Quero garantir meu prêmio! 🎁

O link é gerado dinamicamente no formato:

```
https://wa.me/55XXXXXXXXXX?text=[MENSAGEM_CODIFICADA]
```

---

## 6. Requisitos Técnicos

### 6.1 Stack Recomendada
- **Frontend:** HTML5 + CSS3 + JavaScript Vanilla (ou React)
- **Hospedagem:** Vercel, Netlify ou GitHub Pages (gratuito)
- **Sem backend** — tudo no cliente com `sessionStorage`
- **Domínio:** subdomínio gratuito ou domínio próprio

### 6.2 Responsividade
- **Mobile First** — a maioria do tráfego virá de celular (anúncios no Instagram/Facebook)
- Breakpoints: `375px` (mobile), `768px` (tablet), `1280px` (desktop)
- Testar em iOS Safari e Android Chrome

### 6.3 Performance
- Carregamento inicial < 3 segundos em 4G
- Imagens otimizadas (WebP, máx. 200kb)
- Animações via CSS (evitar bibliotecas pesadas)

### 6.4 Armazenamento entre Páginas

```javascript
// Salvar na Página 1
sessionStorage.setItem('frase', fraseSelecionada)

// Salvar na Página 2
sessionStorage.setItem('premio', premioSorteado)

// Ler na Página 3
const frase = sessionStorage.getItem('frase')
const premio = sessionStorage.getItem('premio')
```

---

## 7. Identidade Visual e UX

### 7.1 Tom e Linguagem
- Descontraído, emocional e divertido
- Usar emojis com moderação para reforçar o clima festivo
- Verbos de ação: *"Escolha", "Gire", "Ganhe", "Garanta"*

### 7.2 Paleta de Cores

| Cor | Hex | Uso |
|-----|-----|-----|
| ⬛ Preto | `#1A1A1A` | Fundo principal, textos em fundo branco |
| 🟡 Dourado | `#C9A84C` | Destaques, botões, bordas, títulos |
| ⬜ Branco | `#FFFFFF` | Fundo de cards, textos em fundo preto |

### 7.3 Tipografia Sugerida
- **Títulos:** Poppins Bold ou Nunito ExtraBold (Google Fonts, gratuito)
- **Corpo:** Poppins Regular ou Open Sans
- **Frases de mãe:** estilo itálico ou manuscrito para efeito emocional

### 7.4 Animações
- Cards das frases: hover com `scale(1.05)` e sombra dourada
- Roleta: animação CSS com `cubic-bezier` para desaceleração realista
- Prêmio: confete (biblioteca `canvas-confetti`, ~3kb)

---

## 8. Rastreamento e Analytics

| Evento | O que mede |
|--------|------------|
| `page_view` — Página 1 | Total de visitantes que chegaram pelo anúncio |
| `frase_selecionada` | Qual frase foi mais escolhida |
| `roleta_girada` | Quantos usuários jogaram a roleta |
| `premio_revelado` | Qual prêmio foi mais sorteado |
| `whatsapp_clicado` | Taxa de conversão final |

> 📊 **Ferramentas recomendadas:** Google Analytics 4 (gratuito) + Meta Pixel (para otimizar anúncios no Instagram/Facebook).

---

## 9. Cronograma Sugerido

| Fase | Atividade | Prazo |
|------|-----------|-------|
| 1 | Aprovação do PRD e definição dos prêmios finais | 1 dia |
| 2 | Desenvolvimento da Landing Page (Página 1) | 2 dias |
| 3 | Desenvolvimento da Roleta (Página 2) | 2 dias |
| 4 | Tela do prêmio + integração WhatsApp (Página 3) | 1 dia |
| 5 | Testes em mobile e ajustes | 1 dia |
| 6 | Publicação + configuração de Analytics e Meta Pixel | 1 dia |
| 7 | Lançamento e início dos anúncios | Dia das Mães |

---

## 10. Pontos a Definir Antes do Desenvolvimento

Os itens abaixo precisam ser confirmados para iniciar o desenvolvimento:

- [ ] Número do WhatsApp da loja (com DDD)
- [ ] Data de validade dos prêmios (ex: *"Válido até 11/05/2025"*)
- [ ] Prêmios finais e seus respectivos pesos/probabilidades
- [ ] Logo da ótica em formato PNG (fundo transparente)
- [ ] Domínio ou URL onde o site será publicado
- [ ] Quais redes sociais terão anúncios (Instagram, Facebook, TikTok?)
- [ ] Existe limite de participantes? (Se sim, implementar contador)

---

*PRD — Campanha Dia das Mães | Ótica | v1.0*
