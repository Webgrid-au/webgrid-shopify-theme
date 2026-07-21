# Webgrid Shopify Starter

A [Dawn](https://github.com/Shopify/dawn) fork shaped into Webgrid's reusable
starter theme. Dawn's commerce logic (cart, variants, search, checkout hooks)
is kept intact; presentation is replaced over time with self-contained
`custom-` sections styled by Webgrid brand tokens.

Working rules for humans and AI assistants live in [CLAUDE.md](CLAUDE.md) —
read it before changing anything.

## Starting a client project

1. Duplicate this repo (don't fork the client off Shopify/dawn — this repo is
   the base). Keep this starter generic: no client assets or copy committed here.
2. Point the CLI at the client's store and start the preview:
   ```sh
   shopify theme dev --store <client-store>.myshopify.com
   ```
   The prompt asks for the *storefront* password (Online Store → Preferences),
   not the account login.
3. Rebrand the tokens in `config/settings_data.json` (color schemes, fonts,
   radii) and `config/settings_schema.json` if new global tokens are needed.
4. Swap in the client's logo, menus, and content through the theme editor.
5. Record in the client repo which starter version it was cut from (see tags).

## Custom sections

Custom sections are prefixed `custom-` and copy the reference pattern in
`sections/custom-hero.liquid`: every setting has a default and a preset,
CSS is self-contained in the section file, and every output is escaped or
carries a `{% # ... %}` comment saying why not.

Current roster: `custom-hero`, `custom-image-with-text`, `custom-multicolumn`,
`custom-image-banner`, `custom-slideshow`. The homepage
(`templates/index.json`) demos all of them.

Dawn's originals are never modified in place — replacements are swapped in via
template JSON so upstream merges stay clean.

## Staying up to date with Dawn

The `upstream` remote points at Shopify/dawn. Every few months:

```sh
git fetch upstream
git merge upstream/main
```

Conflicts should be rare because Dawn files aren't edited in place.

## Checks

```sh
shopify theme check
```

Baseline: 8 warnings in stock Dawn files are accepted (fixing them would dirty
upstream merges). Only new offenses in `custom-` code need fixing.

## License

Based on Dawn, copyright (c) 2021-present Shopify Inc.
See [LICENSE](/LICENSE.md) for further details.
