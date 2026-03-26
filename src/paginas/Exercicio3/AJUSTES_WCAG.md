# Ajustes de acessibilidade — Exercício 3

Correções baseadas em auditoria WCAG.

## 1. aria-labelledby apontando para ID inexistente (WCAG 4.1.2)

- **Problema:** `<section aria-labelledby="titulo-painel-cadastro">` referenciava um ID que não existia.
- **Correção:** o banner "Alterar cadastro" agora é um `<h3 id="titulo-painel-cadastro">`, resolvendo a referência.

## 2. Subtítulo com semântica correta (WCAG 1.3.1)

- **Problema:** subtítulo usava `<span>`.
- **Correção:** `<span>` → `<p>`.

## 3. Banner sem semântica e com estilos inline (WCAG 1.3.1)

- **Problema:** `<div>` com estilos inline e `<span>` sem significado semântico.
- **Correção:** substituído por `<div role="banner">` com `<h3>` e estilos movidos para CSS. Adicionado suporte ao tema dark.

## 4. Labels em dados estáticos sem associação (WCAG 1.3.1)

- **Problema:** `<label>` usado para rotular texto estático (CPF, Nome, etc.) sem `htmlFor` e sem campo associado.
- **Correção:** substituído por `<dl>/<dt>/<dd>` — semanticamente correto para pares rótulo-valor.

## 5. DTPInput ignorando prop type (WCAG 1.3.5 — Identify Input Purpose)

- **Problema:** o componente DTPInput tinha `type="text"` hardcoded em todos os `<input>`, ignorando `type="email"` e `type="tel"` passados via props.
- **Correção:** adicionado `type` na interface e desestruturação, com default `"text"`. Todos os `<input>` agora usam `type={type}`.

## 6. Label sem htmlFor no DTPInput (icon + inline) (WCAG 4.1.2)

- **Problema:** no branch `icon + inline` do DTPInput, o `<label>` não tinha `htmlFor`.
- **Correção:** adicionado `htmlFor={id}`.
