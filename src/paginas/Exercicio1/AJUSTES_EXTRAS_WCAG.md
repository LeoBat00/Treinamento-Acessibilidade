# Ajustes extras de acessibilidade — Exercício 1

Correções adicionais aplicadas além das tarefas do `Tarefas.md`, baseadas em auditoria WCAG.

## 1. Remoção de IDs duplicados (WCAG 4.1.1 — Parsing)

- **Problema:** todos os cards tinham `id="card-registro"`, violando a regra de IDs únicos no DOM.
- **Correção:** atributo `id` removido dos `<article>`.

## 2. Subtítulo com semântica correta (WCAG 1.3.1 — Info and Relationships)

- **Problema:** o subtítulo da página usava `<span>`, que não carrega semântica de bloco de texto.
- **Correção:** `<span className="subtitulo-pagina">` → `<p className="subtitulo-pagina">`.

## 3. Contraste do título de seção no tema dark (WCAG 1.4.3 — Contrast Minimum)

- **Problema:** `.titulo-secao` tinha `color: #000000` fixo, sem override no dark. Sobre fundo `#333333` o contraste era ~2.7:1 (mínimo exigido: 4.5:1).
- **Correção:** adicionado `color: #e7edf6` em `body[data-theme='dark'] .pagina-exercicio-1 .titulo-secao`.

## 4. Tamanho do alvo de toque do botão de download (WCAG 2.5.8 — Target Size)

- **Problema:** `.botao-baixar` tinha 40×40px, abaixo do mínimo AAA de 44×44px.
- **Correção:** dimensões alteradas para 44×44px.

## 5. Remoção de código morto

- **Problema:** bloco comentado de `onKeyDown` no JSX, remanescente da `<div role="button">`.
- **Correção:** comentário removido, pois o `<button>` nativo já trata teclado nativamente.

## 6. Ícone do botão de download invisível no dark (WCAG 1.4.3 — Contrast Minimum)

- **Problema:** o `<button>` não tinha cor explícita; o user-agent renderizava o ícone em preto sobre fundo `#000000` do card no tema dark.
- **Correção:** adicionado `color: #fff333` no seletor dark do `.botao-baixar`, seguindo o padrão do projeto para clicáveis em alto contraste (~19:1 sobre preto).

## 7. Hover do botão de download invisível no dark (WCAG 1.4.11 — Non-text Contrast)

- **Problema:** o hover usava `rgba(19, 81, 180, 0.16)` (azul translúcido), praticamente invisível sobre fundo `#000000` no tema dark.
- **Correção:** adicionado hover específico no dark com `rgba(255, 243, 51, 0.2)` (halo amarelo), consistente com a cor `#fff333` do ícone.

## 8. Rótulos sem separador para leitores de tela (WCAG 1.3.1 — Info and Relationships)

- **Problema:** "Tipo Comprovante" e "Formato PDF (1.2 MB)" eram lidos corridos pelo leitor de tela, sem distinção clara entre rótulo e valor.
- **Correção:** adicionado `aria-label` nos `<p>` com texto estruturado (ex: `"Tipo: Comprovante"`, `"Formato: PDF, 1.2 MB"`).
