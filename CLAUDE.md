# CLAUDE.md

Guidance for Claude Code when working in this repository.

## Development

No build step. Open `index.html` directly or serve with `npx serve .` / `python3 -m http.server 8080`. Tailwind CSS and Inter load via CDN.

## Architecture

Single-page static site for **Instituto ByteCoração** (bytecoracao.ong.br). Only page: `index.html`. All assets in `assets/`. See `DESIGN.md` for component patterns.

## Nav

Links: **O que fazemos | Voluntários | Seja voluntário**. Active anchor link: `text-[#7c4084] font-medium`. Inactive: `text-[#111111] hover:opacity-50 transition-opacity hidden md:block`. CTA button: `bg-[#7c4084]` hover `#5a2d60`.

## Footer

Setbox logo + address block only. No columns. `© 2026 Setbox Serviços Digitais`, `Rua João Bettega, 649 - Sala 3A, Curitiba / PR`.

## Content Rules

- Language: Brazilian Portuguese
- No trailing period on any title or subtitle (h1-h6)
- Never use em dash anywhere - use hyphen (-) or comma
- Volunteer CTA: `mailto:voluntario@bytecoracao.ong.br`
- Contact: `mailto:contato@bytecoracao.ong.br`

## Image Rules

- All `<img>` must have `width`, `height`, and `loading="lazy"` - except nav/footer logos (above fold)

## SEO

Every page needs: `meta[description]`, `link[canonical]`, Open Graph tags (`og:type/site_name/locale/url/title/description/image`), Twitter card. OG image: `assets/og-image.png` (1200x630). Tailwind CDN: add `<link rel="preload" as="script">` before the `<script>` tag.
