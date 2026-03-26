# Ajustes extras de acessibilidade — Exercício 2

Correções adicionais aplicadas além das tarefas do `Tarefas.md`, baseadas em auditoria WCAG.

## 1. Subtítulo com semântica correta (WCAG 1.3.1)

- **Problema:** subtítulo usava `<span>`, sem semântica de bloco de texto.
- **Correção:** `<span>` → `<p>`.

## 2. aria-controls referenciando elemento inexistente (WCAG 4.1.2)

- **Problema:** quando o dropdown estava fechado, o submenu era removido do DOM (`return null`), mas o `aria-controls` do botão ainda referenciava o ID inexistente.
- **Correção:** submenu permanece no DOM com atributo `hidden` quando fechado, garantindo que o `aria-controls` sempre aponte para um elemento válido.

## 3. Sem indicação acessível do item ativo (WCAG 4.1.2)

- **Problema:** ao selecionar um item, não havia comunicação para tecnologias assistivas sobre qual item estava ativo.
- **Correção:** adicionado `aria-current="true"` no link do item selecionado (tanto itens sem submenu quanto subitens).

## 4. Fragment desnecessário removido

- **Problema:** `<>...</>` dentro de `<article>` sem necessidade.
- **Correção:** conteúdo movido diretamente para dentro do `<article>`.
