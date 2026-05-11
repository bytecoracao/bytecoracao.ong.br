# Design Reference - Instituto ByteCoração

Análise visual adaptada da identidade ByteCoração: editorial minimalista com paleta roxa/rosa.

---

## Identidade Visual

**Filosofia:** Editorial minimalista. Swiss/International typographic style. Quase zero ornamento, todo o trabalho estético é feito por tipografia, espaçamento e uso cirúrgico da cor de destaque.

**Paleta:**

| Token | Valor | Uso |
|---|---|---|
| `bg` | `#FAFAFA` | Fundo de todas as seções |
| `bg-alt` | `#F7F7F7` | Fundo de seções alternadas |
| `bg-purple-lt` | `#f5eaf7` | Fundo de pillars, ícones de card, badges |
| `text` | `#111111` | Texto primário |
| `text-muted` | `#555555-#888888` | Texto secundário, subtítulos |
| `border` | `#E5E5E5` | Divisores, bordas de card |
| `accent` | `#7c4084` | Roxo: labels, nav ativo, bullets, botão principal |
| `accent-hover` | `#5a2d60` | Hover do botão roxo |
| `accent-pink` | `#e05a7b` | Rosa: ícone coração, botão CTA final |
| `accent-pink-hover` | `#c0365a` | Hover do botão rosa |
| `accent-dark` | `#3d1a42` | Roxo escuro: fundo da seção CTA final |
| `neutral-lt` | `#dbbde0` | Borda de badge, texto sobre fundo escuro |

---

## Tipografia

**Font stack:** Inter via Google Fonts (optical size 14..32, pesos 300-800). Sem serifa em todos os elementos.

### Escala

| Nível | Tamanho | Peso | Uso |
|---|---|---|---|
| Display | 48-52px | 800 | H1 hero |
| H2 | 26-38px | 700 | Títulos de seção |
| H3 | 16-22px | 600 | Subtítulos, cabeçalhos de card |
| Body | 15-17px | 400 | Parágrafos, descrições |
| Small / Meta | 13px | 400-500 | Labels, bullets, células de tabela |
| Nav | 14px | 400 | Links de navegação |
| Caption | 12px | 400 | Footer, legendas, copyright |
| Label | 11px | 600 | Labels de seção (uppercase, tracking-wide) |

### Labels de seção

```html
<p class="text-[11px] font-semibold tracking-wide uppercase mb-3" style="color:#7c4084;">Label</p>
```

---

## Layout e Grid

**Max width:** `max-w-5xl` (~1024px) para navbar e footer. `.container-inner` (`max-width:1024px; margin:0 auto; padding:0 32px`) para seções.

**Alinhamento:** Hero e seção WHAT WE DO: grid 2 colunas (`1fr 1fr`, gap 64px). Cards 3 colunas: `repeat(3,1fr)`, gap 16px. CTAs centrados: `text-align:center`.

**Responsivo:** Classes utilitárias `.two-col`, `.three-col`, `.stats-grid` colapsar para 1 coluna em mobile via CSS inline (não Tailwind breakpoints) - padrão herdado.

---

## Espaçamento Vertical

| Contexto | Valor |
|---|---|
| Hero | `padding-top:96px; padding-bottom:96px` |
| Seções principais | `padding-top:80px; padding-bottom:80px` |
| Pillars (compacto) | `padding-top:56px; padding-bottom:56px` |
| CTA final | `padding-top:96px; padding-bottom:96px` |
| Label -> H2 | `mb-3` -> `mb-5` |
| H1 -> parágrafo | `mb-6` |
| Parágrafo -> CTA | `mb-8` |

---

## Componentes

### Navbar

```
[Logo ByteCoração]    O que fazemos  Voluntários  [Seja voluntário ▶]
```

- Sticky top, `bg-[#FAFAFA]`, `border-b border-[#E5E5E5]`, `h-14`, `z-50`
- Logo: SVG coração `fill:#e05a7b` + `Byte` preto + `Coração` em `#7c4084`
- Links: `text-sm text-[#111111] hover:opacity-50 transition-opacity hidden md:block`
- Link ativo: `text-[#7c4084] font-medium`
- Botão "Seja voluntário": `bg-[#7c4084] text-white px-4 py-1.5 rounded-[6px]`, hover `#5a2d60`
- Mobile: hambúrguer toggle, menu dropdown com links e CTA

### Botão Primário (roxo)

```html
<a href="mailto:voluntario@bytecoracao.ong.br"
   class="inline-block text-[14px] text-white px-6 py-3 rounded-[6px] font-semibold transition-colors"
   style="background:#7c4084;"
   onmouseover="this.style.background='#5a2d60'"
   onmouseout="this.style.background='#7c4084'">CTA →</a>
```

### Botão CTA Final (rosa, sobre fundo escuro)

```html
<a href="mailto:voluntario@bytecoracao.ong.br"
   class="inline-block text-[14px] font-semibold px-6 py-3 rounded-[6px] transition-colors text-white"
   style="background:#e05a7b;"
   onmouseover="this.style.background='#c0365a'"
   onmouseout="this.style.background='#e05a7b'">CTA →</a>
```

### Botão Secundário

```html
<a href="#ancora" class="inline-block text-[14px] text-[#111111] px-6 py-3 rounded-[6px] border border-[#E5E5E5] hover:bg-[#F7F7F7] transition-colors font-medium">Texto</a>
```

### Card

```html
<div class="border border-[#E5E5E5] rounded-xl bg-white p-6">...</div>
```

### Card com ícone de seção

```html
<div class="border border-[#E5E5E5] rounded-xl bg-white p-6">
  <div style="width:32px;height:32px;border-radius:8px;background:#f5eaf7;display:flex;align-items:center;justify-content:center;margin-bottom:16px;">
    <svg width="18" height="18" ... stroke="#7c4084" ...></svg>
  </div>
  <h3 class="text-[16px] font-semibold tracking-tight text-[#111111] mb-2">Título</h3>
  <p class="text-[14px] leading-[1.7] text-[#555555]">Descrição.</p>
</div>
```

### Badge de status (ATIVO)

```html
<span class="text-[11px] font-semibold ml-auto flex-shrink-0"
      style="letter-spacing:0.04em;padding:3px 8px;border-radius:9999px;background:#f5eaf7;border:1px solid #dbbde0;color:#7c4084;">ATIVO</span>
```

### Bullets com seta roxa

```html
<ul class="space-y-4">
  <li class="flex gap-3 text-[14px] text-[#444444]">
    <span class="font-bold flex-shrink-0 mt-0.5" style="color:#7c4084;">→</span>
    <span>Texto do item</span>
  </li>
</ul>
```

### Seção CTA Final

Fundo `#3d1a42`, texto branco, subtítulo `#dbbde0`, botão rosa.

### Divisor de Seção

`border-b border-[#E5E5E5]` na seção. Sem elemento `<hr>` separado.

### Footer

Setbox logo + endereço, sem colunas.

```
[Logo Setbox]
© 2026 Setbox Serviços Digitais
Rua João Bettega, 649 - Sala 3A
Curitiba / PR
```

- Fonte: 12px, `text-[#BBBBBB]`
- Separador topo: `border-t border-[#E5E5E5]`
- Padding: `py-10 md:py-14`

---

## Tom Visual Geral

- **Zero decoração:** sem gradientes, sem shadows, sem ilustrações, sem stock photos
- **Hierarquia por tamanho e peso:** cor de destaque usada com parcimônia (labels, bullets, CTAs)
- **Densidade baixa:** uma ideia por bloco, muito espaço entre seções
- **Confiança editorial:** conteúdo fala sozinho, design não grita
