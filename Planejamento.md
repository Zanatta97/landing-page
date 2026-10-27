# Planejamento

Site vitrine do serviço de páginas simples para negócios locais, com páginas-exemplo de negócios
fictícios. O link vai circular principalmente por WhatsApp, então o público abre no celular.

URL pública prevista: https://zanatta97.github.io/landing-page/ (GitHub Pages, servindo a raiz da
branch como está).

## Stack

- **HTML + CSS + JS vanilla.** Sem build, sem `package.json`, sem npm.
- **Google Fonts via `<link>`** é a única dependência externa permitida.
- Nenhuma outra biblioteca (ícones, animação, CSS framework) sem autorização.
- `.nojekyll` na raiz para o GitHub Pages servir os arquivos sem processar.

## Estrutura

```
index.html                       vitrine (usa assets/css/style.css)
assets/
  css/style.css                  estilos da vitrine (não é usado pelos exemplos)
  favicon.svg
  og-image.png                   prévia de link da vitrine (1200x630)
  img/exemplos/<pasta>.png       capturas de celular dos exemplos (390x844 @1.5x)
exemplos/<pasta>/
  index.html                     página-exemplo com CSS próprio em <style>
  og.png                         prévia de link do exemplo (1200x630)
Planejamento.md
.nojekyll
```

Pastas dos exemplos: `restaurante`, `salao-de-beleza`, `oficina-mecanica`, `padaria`, `pet-shop`,
`clinica-odontologica`.

## Convenções

- **Idioma:** textos de interface e comentários em português; classes, ids e nomes de arquivo de
  código em inglês. Nomes de pasta dos exemplos e âncoras (`#cardapio`, `#visite`) em português,
  porque aparecem na URL.
- **Links internos sempre relativos** (`exemplos/padaria/index.html`, `../../index.html`): o site
  roda na subpasta `/landing-page/`.
- **`og:url` e `og:image` absolutos**, com a URL pública.
- **Cada exemplo é autocontido:** CSS próprio dentro do `<style>`, favicon em data URI, sem
  depender de nada da vitrine. Assim qualquer exemplo pode ser copiado e virar a página de um
  cliente real.
- **Sem fotos externas.** Visual em CSS e tipografia. Os espaços de foto ficam sinalizados como
  "Foto do seu estabelecimento".
- **Mapa ilustrado em CSS** + botão "Abrir no mapa" (link de busca do Google Maps). Sem iframe.
- **Botões de WhatsApp dos exemplos levam ao WhatsApp do dono do site**, com mensagem pronta
  ("Vi o exemplo de ... e quero uma página assim"). Em cliente real, trocar pelo número do cliente.
- **Clínica odontológica não divulga preço nem forma de pagamento** e mostra responsável técnico
  com CRO: são exigências do Código de Ética Odontológica para publicidade.
- **Acessibilidade:** contraste AA, `:focus-visible` em todos os interativos, link "Pular para o
  conteúdo", HTML semântico, `prefers-reduced-motion` respeitado, sem scroll horizontal em 375px.
- **Sem travessão** (em dash / en dash) em texto de interface. Use hífen, vírgula ou ponto.

## Imagens geradas

`og.png`, `og-image.png` e as capturas em `assets/img/exemplos/` são capturas de tela das próprias
páginas (navegador headless, viewport 1200x630 para OG e 390x844 a 1.5x para celular, com
`prefers-reduced-motion: reduce` e tema claro). **Regere depois de mudar o visual de uma página** ou
o nome no cabeçalho da vitrine, senão a prévia fica desatualizada.

## Design system

Cada página tem identidade própria de propósito: o cliente precisa ver variedade, não um template
trocando cor. Abaixo, os tokens de cada uma.

### Vitrine (`index.html`)

- **Leitura:** landing de serviço local para donos de pequeno comércio que chegam pelo WhatsApp,
  linguagem direta e próxima. Dials 7 / 5 / 4 (variação / movimento / densidade).
- **Tema:** claro e escuro automáticos (`prefers-color-scheme`), via variáveis CSS.
- **Cores (claro):** fundo `#f4f5f7`, superfície `#ffffff`, texto `#15171c`, texto secundário
  `#50555f`, acento azul-cobalto `#2443c9` (texto branco sobre ele).
- **Cores (escuro):** fundo `#111318`, superfície `#1a1d24`, texto `#eceef2`, secundário `#a3a9b5`,
  acento `#8ea2ff` (texto `#111318` sobre ele).
- **Tipografia:** Bricolage Grotesque 600/700 (títulos), Geist 400/500/600 (texto).
- **Forma:** botões em pílula; blocos 20px; celulares 34px de borda arredondada.
- **Movimento:** entrada do hero; revelação ao rolar com `animation-timeline: view()` (só onde há
  suporte e sem redução de movimento).
- **Visual:** capturas reais dos exemplos dentro de molduras de celular; prévia de link do WhatsApp
  montada como componente real com a `og.png`.

### Restaurante: Tempero da Vila

- **Leitura:** restaurante caseiro de almoço, apetitoso e acolhedor, estilo lousa. Dials 6 / 4 / 5.
- **Tema:** escuro fixo (identidade da marca).
- **Cores:** fundo `#1c2420`, superfície `#242e29`, texto `#f1ece2`, secundário `#b9c2b8`, acento
  tomate `#f0714f` com texto `#161b18`.
- **Tipografia:** Caprasimo (títulos), Figtree (texto). **Raio:** 14px, botões em pílula.
- **Padrões:** prato do dia em trilho horizontal com destaque automático do dia; cardápio com linha
  pontilhada até o preço; botão de WhatsApp fixo no celular.

### Salão de beleza: Maré Studio

- **Leitura:** estúdio de beleza editorial, moderno. Dials 8 / 5 / 3.
- **Tema:** claro fixo.
- **Cores:** fundo `#fafaf7`, texto `#1c1a22`, secundário `#5d5866`, acento magenta `#b0186a` com
  texto `#fafaf7`.
- **Tipografia:** Syne 600/800 (títulos), DM Sans (texto).
- **Forma:** botões em pílula, fotos em arco, superfícies retas com linhas finas.
- **Padrões:** serviços em abas acessíveis (setas, Home, End; sem JS mostra tudo); equipe com foto em
  arco.

### Oficina mecânica: Bertolini Auto Mecânica

- **Leitura:** oficina de confiança, industrial e direta. Dials 5 / 3 / 6.
- **Tema:** claro fixo (concreto).
- **Cores:** fundo `#efefec`, superfície `#fafaf8`, texto `#151515`, secundário `#55554f`, acento
  amarelo de sinalização `#f5b700` **só como fundo**, sempre com texto `#151515`.
- **Tipografia:** Archivo com largura condensada (68%) em caixa alta nos títulos, IBM Plex Mono
  para preços e horários.
- **Forma:** cantos retos em tudo, bordas de 2px, sombra sólida deslocada nos botões.
- **Padrões:** grade de serviços com destaque para revisão completa; faixa zebrada de sinalização.

### Padaria: Padaria Bairro Alto

- **Leitura:** padaria de tradição portuguesa, azulejo azul e branco. Dials 6 / 4 / 4.
- **Tema:** claro fixo.
- **Cores:** fundo `#f7f8fb`, superfície `#ffffff`, texto `#14204a`, secundário `#4a4f63`, acento
  cobalto `#1f3fa8` com texto `#f7f8fb`, azulejo claro `#e6ebf8`.
- **Tipografia:** Playfair Display 700/900 com itálico (títulos; serifa justificada pela herança),
  Work Sans (texto). **Raio:** 6px em tudo.
- **Padrões:** azulejo feito só com gradientes; linha do tempo das fornadas com a próxima marcada
  automaticamente.

### Pet shop: Lambeijo

- **Leitura:** pet shop alegre e próximo. Dials 7 / 6 / 4.
- **Tema:** claro fixo.
- **Cores:** fundo `#eef7f2`, superfície `#ffffff`, menta `#cfe9dc`, pêssego `#ffd9c4`, texto
  `#123b33`, secundário `#3f6158`, acento tangerina `#ff8a52` com texto `#123b33`.
- **Tipografia:** Fredoka (títulos), Nunito (texto).
- **Forma:** botões em pílula, blocos 28px, foto em formato orgânico.
- **Padrões:** tabela de preços por porte (tabela de verdade, com `caption` e `scope`); mosaico de
  serviços com fundos variados.

### Clínica odontológica: Aurora Odontologia

- **Leitura:** clínica de confiança, calma e clara. Dials 4 / 3 / 5.
- **Tema:** claro fixo.
- **Cores:** fundo `#f5f8fa`, superfície `#ffffff`, tinta `#e3f0f1`, texto `#0f2a3a`, secundário
  `#4b5d68`, acento azul-petróleo `#0d6f78` com texto branco.
- **Tipografia:** Manrope em tudo. **Raio:** 12px em superfícies, 10px em botões.
- **Padrões:** tratamentos em acordeão (`details`); primeira consulta em etapas numeradas; sem
  preços (ver Convenções).
