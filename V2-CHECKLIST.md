# janineisaacs.com v2: review, switch-over and visibility checklist

Status: built, not published. The live site (janineisaacsdraft on Netlify, custom domain janineisaacs.com, deployed from GitHub `martinvarley100-ship-it/janineisaacs-site`, branch `main`) is untouched.

## 1. What v2 is

A single-page site built exactly to the approved design (Design.pdf, 3 September 2026), plus two retained inner pages. Copy is verbatim from the design. Nothing has been added or reworded.

Files:

- `index.html`: the full page (hero, sections 01 to 04, dark band, about with portrait, professionals, three quotes, closing and contact).
- `discovery-call.html`: the enquiry form from v1, restyled. Reached at `/discovery-call`.
- `thank-you.html`: form confirmation, restyled, `noindex`.
- `style.css`: mobile-first stylesheet. Palette sampled from the PDF (page #f7f4ef, band #3d2f2c, heading ink #42312f). Cormorant Garamond for headings, Inter for body, via Google Fonts, with system fallbacks.
- `assets/janine-portrait.jpg` (1254px) and `-800.jpg`: extracted from the PDF as a stand-in until the high-res image arrives. `assets/og-image.jpg` (1200x630) for link previews.
- `_redirects`, `netlify.toml`, `robots.txt`, `sitemap.xml`, `llms.txt`, `llms-full.txt`.
- `admin/` and `data/`: carried over unchanged from v1 (Decap CMS with Netlify Identity and Git Gateway).

Verified: renders without horizontal scroll at 390px and 1280px; JSON-LD parses; every internal link resolves; both Netlify forms present with the original names and field names.

## 2. Nothing lost from Netlify

What the live site actually has on Netlify (checked through your logged-in dashboard):

- Forms: `contact` (8 submissions), `discovery-call` (3), `newsletter` (3). All submissions stay in Netlify's Forms tab regardless of what is deployed.
- Form notifications (the "auto responses"): `contact` emails janinealisonisaacs@gmail.com (subject "Contact Request") and martin.varley@mac.com (subject "response to J9 Contact"); `discovery-call` emails janinealisonisaacs@gmail.com (subject "Discovery Call Request"). These are keyed to the form name, so they keep firing as long as the names stay the same. v2 keeps `contact` and `discovery-call` byte-for-byte on the field names.
- Functions: none deployed. Blobs: no stores exist on this site. So there was no function or Blob code to carry across; the "blobs" you had in mind are almost certainly the form submissions, which are safe.
- Netlify Identity and Git Gateway: enabled, used by `/admin`. Kept.
- Pretty URLs: on. v2 links use extensionless paths and `_redirects` maps every v1 URL (`/about`, `/philosophy`, `/this-is-for-you`, `/the-woman-behind-the-work`, `/work-with-me`, `/testimonials`, `/contact`, `/reflections`) to the matching section, as 301s, so bookmarks and search results keep working.

One deliberate omission: the `newsletter` form is not on the v2 page because the design has no newsletter. It had no notification attached. The three existing subscriber emails remain in Netlify. If you want it back, say so and I will add it to the closing section.

## 3. Before switch-over (things only you or Janine can settle)

- [x] Phone number: +44 7747 897113 (confirmed by Martin, 14 September). On the page, in the JSON-LD and in the llms files.
- [ ] Email. The design uses hello@janineisaacs.com. Confirm that mailbox exists and forwards. (v1 had no public email; notifications go to Janine's Gmail.)
- [ ] High-res portrait. Drop it in as `assets/janine-portrait.jpg` (square crop, 1254px or larger) and regenerate `-800.jpg` and `og-image.jpg`, or send it to me and I will.
- [ ] Decap CMS. The v1 admin edits pages that no longer exist (testimonials list, blog posts, page copy). Options: leave it as is (harmless, Janine just will not use it), retarget it at v2 (I can wire the three quotes and the section copy into `data/` so she can edit them), or remove `admin/` and switch Identity off. Say which.
- [ ] LinkedIn URL. JSON-LD and llms.txt reuse linkedin.com/in/janineisaacs from v1. Confirm it is right.
- [ ] Section numbering 01 to 04 follows the design. If Janine would rather they were not numbered, it is a one-line change.

## 4. Switch-over (when you say go)

Option A, branch preview first (recommended):

1. In the repo, create branch `v2`, replace the contents with the `v2/` folder from the zip, push.
2. Netlify: Project configuration > Build & deploy > Branches and deploy contexts > add `v2` as a branch deploy. You get `https://v2--janineisaacsdraft.netlify.app` with working forms (submissions land in the same Forms tab, notifications fire).
3. Test both forms once from the branch URL and check the emails arrive.
4. Merge `v2` into `main`. Netlify publishes it. DNS does not change.

Option B, direct: replace the contents of `main` with the `v2/` folder and push. Netlify publishes within about ten seconds.

After publishing:

5. Netlify > Forms: confirm `contact` and `discovery-call` still show, with the notifications attached (Forms > form > Notifications).
6. Open `https://janineisaacs.com/about` and `https://janineisaacs.com/contact` to confirm the redirects.
7. Google Search Console: submit `https://janineisaacs.com/sitemap.xml` and request indexing of the home page.
8. Bing Webmaster Tools: same (Bing feeds ChatGPT search and Copilot).
9. Paste the home URL into the Rich Results Test (search.google.com/test/rich-results) and validator.schema.org; both should show Person, ProfessionalService, WebSite, WebPage with no errors.
10. Share the URL in a LinkedIn post preview or opengraph.xyz to check the link card shows the portrait and title.

## 5. LLM and search visibility: what is in place and what raises it further

In the build:

- JSON-LD graph in `<head>`: Person (credentials, knowsAbout, three work locations), ProfessionalService (what it is, what it is not, where it applies, two audiences, areas served), WebSite, WebPage. All wording is taken from the design.
- `/llms.txt` (short, structured summary with links) and `/llms-full.txt` (full page text), the emerging convention answer engines and agents read first. Linked from the page head with `rel="alternate"`.
- `robots.txt` explicitly allows GPTBot, OAI-SearchBot, ChatGPT-User, ClaudeBot, Claude-SearchBot, Claude-User, anthropic-ai, PerplexityBot, Perplexity-User, Google-Extended, Googlebot, Bingbot, Applebot, CCBot, meta-externalagent, DuckAssistBot, Amazonbot. `/admin/` and `/thank-you` are disallowed.
- Semantic HTML: one `h1`, `h2` per section, `blockquote` for the quotes, `mailto:` and `tel:` links, `lang="en-GB"`, canonical, Open Graph and Twitter cards, image sitemap entry, descriptive alt text.
- Fast and light: no JavaScript beyond the form toggle and the Identity widget, fonts with `display=swap`, portrait lazy-loaded with `srcset`, long cache on `/assets/`.

Outside the build (in rough order of impact):

- [ ] Consistent entity across the web. The same name, description and the three cities on LinkedIn, and anywhere else Janine is listed, so models can reconcile the entity. The LinkedIn headline matters more than most people expect.
- [ ] Google Business Profile is worth it only if she wants to appear for "near me" style searches in Manchester or London. If so, use the exact same wording as the site.
- [ ] Links from professional referrers. A mention on one or two solicitor or family-office sites (even a "we sometimes introduce clients to...") does more for both Google and LLM retrieval than anything on-page.
- [ ] Wikipedia-adjacent sources. A Crunchbase, Chambers or Legal 500 alumni listing, or a professional directory entry, gives models a second source to corroborate the biography.
- [ ] One or two long-form pieces. LLM search surfaces pages that answer a question directly. Two pages of 800 to 1200 words, each on one of the "Where this applies" situations, written in Janine's voice, would give the site something to be retrieved for beyond her name. Only when she is ready to write them; I will not draft copy for the site without instruction.
- [ ] Keep `llms.txt` and the JSON-LD in step with any copy change. If a section is edited, those two files need the same edit.
- [ ] Measure. Bing Webmaster Tools and Google Search Console both now report AI-referred impressions; Netlify Analytics (paid add-on) shows referrers, including chatgpt.com and perplexity.ai, which is the only direct signal you will get.
