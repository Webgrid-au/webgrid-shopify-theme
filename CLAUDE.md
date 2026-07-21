# Shopify Starter — Working Rules

## What this is

A Dawn fork being shaped into a reusable starter theme. Dawn's commerce
logic (cart, variants, search, checkout hooks) is load-bearing: restyle
it, wrap it, but do not rewrite it without being asked.

## Stack

- Shopify Online Store 2.0 theme, Liquid + JSON templates
- Shopify CLI: `shopify theme dev` for local preview, `shopify theme check` before any commit
- No build framework unless asked; Dawn's vanilla JS/CSS approach stands

## Structure

- `sections/` — one file per section, schema at the bottom of the file
- `snippets/` — reusable partials, prefix custom ones `custom-`
- `templates/*.json` — page composition; prefer editing these over hardcoding sections
- `config/settings_schema.json` — global tokens only (colour, type, spacing)
- Custom sections we add are prefixed `custom-` and self-contained:
  their CSS lives in the section file or a same-named asset, not in base CSS

## Conventions

- Every user-facing string through `| escape` unless it is deliberately rich text
- All merchant-editable values via schema settings — no hardcoded copy in Liquid
- Schema: every setting gets a sensible default and a preset so the section
  is usable the moment it's added in the editor
- Translations: strings in locales/en.default.json, referenced with `| t`
- Run `shopify theme check` and report results after changes

## Don'ts

- Don't touch checkout — it's not themeable at this level
- Don't add npm build tooling, external CDNs, or JS frameworks
- Don't modify Dawn core sections in place; copy to a `custom-` version
  and swap it in the template JSON, so upstream merges stay clean
