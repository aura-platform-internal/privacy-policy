# Aura Privacy Policy Site Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build and publish a self-contained, responsive Portuguese privacy policy page for Aura that accurately describes the current product and gives users a clear LGPD and data-deletion channel.

**Architecture:** The site is a single semantic `index.html` with embedded CSS and no JavaScript, external assets, cookies, analytics, or runtime dependencies. Repository documentation explains GitHub Pages and the optional custom domain, while `.nojekyll` ensures direct static serving.

**Tech Stack:** HTML5, embedded CSS, GitHub Pages, Git/GitHub CLI, browser accessibility and responsive inspection.

**Spec:** `docs/superpowers/specs/2026-09-23-aura-privacy-policy-site-design.md`

## Global Constraints

- The controller name is exactly `Filmaro Corp`.
- The privacy contact is exactly `wudarski@filmaro.com.br`.
- Initial content language is Brazilian Portuguese.
- The page must reflect the actual Aura integrations: Meta/Instagram, Groq, Mercado Pago, Resend, Locaweb, and GitHub Pages.
- Do not load external fonts, scripts, styles, images, pixels, analytics, or other third-party resources.
- Do not promise fixed retention periods or absolute security guarantees that the product does not implement.
- Provide a stable `#exclusao-de-dados` fragment for Meta data-deletion instructions.
- Do not create `CNAME` until the custom domain and DNS are ready.
- Treat the page as an operational policy that should receive professional legal review before becoming a final contractual document.

## Review Focus

- A narrow viewport down to 320 CSS pixels must not cause horizontal overflow or clipped navigation.
- Long URLs and the contact email must wrap without breaking the layout.
- Keyboard users must see focus states and be able to reach every table-of-contents link.
- `#exclusao-de-dados` must land on a visible heading that contains complete request and Meta-revocation instructions.
- The generated page must make zero external network requests during normal rendering.

---

### Task 1: Build the privacy policy page

**Files:**
- Create: `index.html`

**Interfaces:**
- Consumes: controller/contact values and product data flows from the approved spec.
- Produces: a standalone document served at `/` and a deletion-instructions target served at `/#exclusao-de-dados`.

- [ ] **Step 1: Create the semantic document shell**

Create `index.html` with `lang="pt-BR"`, UTF-8 encoding, responsive viewport, description metadata, color-scheme metadata, canonical heading hierarchy, and these stable section IDs:

```html
<main id="conteudo">
  <section id="visao-geral"></section>
  <section id="dados-coletados"></section>
  <section id="como-usamos"></section>
  <section id="inteligencia-artificial"></section>
  <section id="compartilhamento"></section>
  <section id="armazenamento"></section>
  <section id="seguranca"></section>
  <section id="seus-direitos"></section>
  <section id="exclusao-de-dados"></section>
  <section id="criancas-adolescentes"></section>
  <section id="alteracoes"></section>
  <section id="contato"></section>
</main>
```

Add a skip link before the header, a table of contents linking to every section, and a footer containing `Filmaro Corp`, `wudarski@filmaro.com.br`, and the policy effective date `23 de setembro de 2026`.

- [ ] **Step 2: Write the complete policy content**

Write plain-language Portuguese copy that covers:

1. controller identity and scope;
2. Instagram account/profile data, authorized posts, comments, public commenter names, engagement metrics, and access tokens;
3. Aura account data, verified email, session/authentication data, plans, subscriptions, and analysis history;
4. purposes and contextual LGPD legal bases;
5. Groq-based automated sentiment classification, possible inaccuracies, and the absence of consequential legal, credit, employment, or financial decisions;
6. Meta/Instagram, Groq, Mercado Pago, Resend, Locaweb, and GitHub Pages with each provider's purpose;
7. possible international processing by providers;
8. purpose-based retention, lawful retention exceptions, and security categories;
9. LGPD rights and the free contact channel;
10. the following deletion flow under `id="exclusao-de-dados"`:

```text
Envie a solicitação para wudarski@filmaro.com.br com o assunto
“Exclusão de dados — Aura”. Informe o nome de usuário do Instagram e o
e-mail associado à conta Aura. Não envie senha, código de acesso ou token.
Podemos pedir informações adicionais estritamente necessárias para confirmar
a identidade do solicitante. Para interromper novos acessos pela integração,
o usuário também deve remover o Aura na área de Aplicativos e sites das
configurações da Meta/Instagram.
```

State that deletion or anonymization follows verification and may preserve records required by law or needed to exercise rights. Add sections for minors, policy updates, and contact.

- [ ] **Step 3: Add the responsive visual system**

Embed all CSS in `<style>` inside `index.html`. Define design tokens in `:root`, a restrained violet/blue Aura accent, system font stack, readable line length, cards, table/list presentation, visible `:focus-visible`, and responsive rules.

The layout must use one column by default and switch to a content-plus-navigation grid only at `min-width: 960px`. At widths below 640px, reduce padding and card radius. Add:

```css
html { scroll-behavior: smooth; }
body { overflow-wrap: anywhere; }
:focus-visible { outline: 3px solid var(--focus); outline-offset: 3px; }
@media (prefers-reduced-motion: reduce) {
  html { scroll-behavior: auto; }
  *, *::before, *::after { animation-duration: .01ms !important; transition-duration: .01ms !important; }
}
```

Ensure the sticky navigation is enabled only in the desktop grid and does not cover anchored headings by setting `scroll-margin-top` on sections.

- [ ] **Step 4: Inspect the rendered page manually**

Open `index.html` in a browser and inspect at 320, 375, 768, and 1440 CSS pixels. Confirm there is no horizontal scroll; long strings wrap; the navigation, email link, skip link, and deletion anchor work; headings remain visible; and the browser Network panel shows no external requests.

- [ ] **Step 5: Commit the page**

```bash
git add index.html
git commit -m "feat: add Aura privacy policy page"
```

### Task 2: Document and prepare GitHub Pages hosting

**Files:**
- Create: `README.md`
- Create: `.nojekyll`

**Interfaces:**
- Consumes: the root `index.html` from Task 1.
- Produces: repository instructions and direct GitHub Pages static serving.

- [ ] **Step 1: Create the Pages marker**

Create an empty `.nojekyll` file so GitHub Pages serves the repository as plain static content.

- [ ] **Step 2: Write repository documentation**

Create `README.md` with:

- the purpose of the repository;
- local preview command `python -m http.server 8080` and URL `http://localhost:8080`;
- GitHub Pages activation: repository **Settings → Pages → Build and deployment → Deploy from a branch → main / root**;
- expected initial URL `https://aura-platform-internal.github.io/privacy-policy/`;
- recommended custom domain `privacidade.aura-platform.filmaro.com.br`;
- DNS instruction to add a CNAME record pointing to `aura-platform-internal.github.io` before creating the repository `CNAME` file;
- production URLs `https://privacidade.aura-platform.filmaro.com.br/` and `https://privacidade.aura-platform.filmaro.com.br/#exclusao-de-dados` after DNS and Pages HTTPS are active;
- a maintenance checklist requiring policy review when data, purposes, providers, retention, or contact information changes.

- [ ] **Step 3: Commit hosting documentation**

```bash
git add README.md .nojekyll
git commit -m "docs: add GitHub Pages publishing guide"
```

### Task 3: Validate and publish the repository

**Files:**
- Verify: `index.html`
- Verify: `README.md`
- Verify: `.nojekyll`

**Interfaces:**
- Consumes: all artifacts from Tasks 1 and 2.
- Produces: a pushed `main` branch ready for GitHub Pages activation.

- [ ] **Step 1: Run repository integrity checks**

Run:

```bash
git diff --check
git status --short
```

Expected: no whitespace errors; only intended files are present before their commits, and a clean tree after commits.

- [ ] **Step 2: Validate required HTML content and links**

Use PowerShell to check required anchors, identity, email, metadata, and the absence of remote asset URLs:

```powershell
$html = Get-Content -Raw index.html
$required = @(
  'lang="pt-BR"', 'name="viewport"', 'Filmaro Corp',
  'wudarski@filmaro.com.br', 'id="exclusao-de-dados"',
  'Meta/Instagram', 'Groq', 'Mercado Pago', 'Resend', 'Locaweb'
)
$missing = $required | Where-Object { -not $html.Contains($_) }
if ($missing) { throw "Conteúdo obrigatório ausente: $($missing -join ', ')" }
if ($html -match '<(script|img|link)[^>]+https?://') {
  throw 'A página contém recurso externo não permitido'
}
```

Expected: command exits without error.

- [ ] **Step 3: Perform final browser review**

Serve the repository locally with `python -m http.server 8080`, open `/` and `/#exclusao-de-dados`, and verify desktop and mobile rendering, keyboard navigation, email link, anchor positioning, and zero external requests. Stop the server after review.

- [ ] **Step 4: Push the initial main branch**

```bash
git push -u origin main
```

Expected: the GitHub repository shows `index.html`, `.nojekyll`, `README.md`, the spec, and this plan on `main`.

- [ ] **Step 5: Configure GitHub Pages**

Use the repository Pages settings or GitHub API to configure Pages from `main` at `/`. Wait for the Pages deployment workflow to finish, then open the returned public URL and verify that both `/` and `/#exclusao-de-dados` load successfully over HTTPS.

- [ ] **Step 6: Record the public URL**

Update the repository description or README only if the actual Pages URL differs from the expected organization URL. Do not add `CNAME` until the DNS record exists and GitHub Pages accepts the custom domain.
