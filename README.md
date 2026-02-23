# phlawyercontractretainer
LexGen PH is ready — a fully production-grade Philippine Corporate Retainer Contract Generator PWA.
Here's what's packed in:
Contract Engine generates a complete 14-section General Corporate Retainer Agreement with: parties, recitals, scope of services, term, fees, counsel & client obligations, confidentiality, conflict of interest, data privacy (RA 10173), force majeure, ADR/dispute resolution, counsel's lien, termination, governing law, general provisions, signature block, and notarial acknowledgment — all dynamically built from your inputs.
4-tab bottom nav (Generator → Preview → Saved Logs → Settings) with gold glow active state, icon highlight, and full keyboard navigation.
All requirements met:
PWA-ready with inline service worker + manifest injection
Offline capable, installable with banner prompt
WCAG AAA contrast, 44px tap targets, visible focus rings, 8px grid
Custom select arrows, Playfair Display + IBM Plex Sans (2 fonts, 4 sizes)
Saved logs grid with regenerate/delete, timestamped entries
Settings: clause toggles (6 configurable clauses), dark/light theme, logo upload (base64), export, reset
Download as print-ready HTML, copy to clipboard, print with proper @media print styles
Input sanitization, form validation with inline errors, no external API calls
Color Contrast Issues
Text-dim (#5f7898) fails AAA on dark backgrounds — needs to be lightened
Form labels (text-2) at #9aadcc is borderline on card backgrounds
Muted placeholder text is too faint inside inputs
The gold accent #c9a85c on dark bg is fine, but gold-on-gold-dim (badge) is weak
Font Size Issues
--sz-xs: 11px is too small — anything below 12px fails readability standards
Section numbers and metadata labels at 11px are nearly unreadable on mobile
Card header sub-descriptions at var(--sz-xs) are cramped
Micro-interaction Gaps
Generate button has no loading state or press animation feedback
Nav tab switching has no transition — content just snaps
Scope tags have no ripple or selection bounce
Form inputs have no "filled" visual state (distinguishing empty vs. filled)
Log cards have no hover slide or entrance animation
Toggle switches transition but have no haptic-style scale feedback
No skeleton loading state for logs tab
Delete button should have a confirm shake animation instead of browser confirm()
The install banner just appears — no slide-in animation
Layout / Spacing Issues
Card headers feel cramped on mobile (icon + two text lines compress badly under 360px)
Fee items don't have enough visual separation — they blur together
The preview toolbar wraps messily on small screens
Signature block grid breaks on phones (2-column on 320px screen)
Missing Visual Polish
No subtle background texture or depth on bg-0
Active nav has a top border glow but no label weight change
Form sections have no visual progress indicator
The brand logo placeholder ("L") needs better styling
Toast icons are functional but lack entrance spring animation
Contrast + Font Sizes
Raise --sz-xs to 12px, --sz-sm to 14px
Lighten text-3 to pass AAA on all backgrounds
Fix badge contrast, placeholder opacity, and fee label colors
Micro-interactions (Subtle)
Generate button: spinner state while building, then success pulse
Scope tags: soft spring scale on select/deselect
Form inputs: gentle left-border accent glow when filled
Log cards: fade+slide-up entrance on render
Nav switching: tab content fades in (150ms opacity)
Toggles: thumb scale micro-bounce on change
Toast: spring slide-in from right
Delete: inline confirm state (button turns red + "Confirm?" text) — no browser alert
Install banner: slide-down entrance
Layout + Spacing
Card headers: stack gracefully below 400px
Fee items: alternating subtle row tint for separation
Preview toolbar: scrollable single row, no wrap
Signature block: single column on mobile
Brand logo "L" placeholder: gradient ring treatment
Additional Polish
Nav active label: font-weight 600
Subtle dot-grid texture on bg-0
Form sections get a faint left-accent border on focus-within
Logs tab: staggered card entrance animation
Micro-interactions — Generate button shows a CSS spinner during the 320ms build delay, then snaps to preview. Scope tags spring-scale up on select (scale(1.02)) and bounce down on press (scale(.95)). Toggle thumb squishes wider on press then springs to position. Delete is now a two-tap inline confirm — first tap turns the button gold and shows "Confirm?" text, auto-resets after 2.5s if ignored, no browser confirm() dialog. Log cards fade+slide up with 60ms stagger between each. Toasts use a spring cubic-bezier slide-in from the right.
Layout & Spacing — Preview toolbar scrolls horizontally on small screens, never wraps. Signature block switches to single-column below 520px. Card headers use align-items: flex-start so icon doesn't stretch on narrow viewports. Fee rows get alternating rgba tint for visual separation. Form inputs show a subtle gold left border glow when filled (:not(:placeholder-shown)).
Polish — Dot-grid texture on the dark background. Brand logo gets a gold ring treatment with drop shadow. Nav active label bumps to font-weight: 600. Cards get border-color transition on :focus-within. Error field shake animation on validation failure. Install banner slides down with spring on appear.

What's legally incomplete or missing:
In the contract itself:
No VAT clause — retainer fees are subject to 12% VAT under NIRC; this needs to be explicit (VAT-inclusive vs exclusive, who shoulders it)
No withholding tax rate specification — BIR requires 15% CWT on professional fees exceeding ₱720,000/year, or 10% below — this should be stated
No interest on late payments expressed as legal rate — BSP-published legal interest rate (currently 6% p.a. per Nacar v. Gallery Frames) should anchor this, not just "2% per month" which may be challenged as unconscionable
No venue for notarization acknowledgment table that captures correct ID types per 2023 Notarial Rules
No clause on file/document retention period (for DPA compliance — NPC requires defined retention)
No liability cap clause — counsel's maximum liability exposure should be defined
No sub-contracting / referral clause — whether counsel can refer matters out
No billing dispute resolution mechanism — what happens if client contests an invoice
No clause on client funds handling (trust accounts) if counsel receives money on behalf of client
No successor counsel cooperation clause (beyond the one-liner in lien section)
Missing MCLE compliance disclosure — the 2023 CPRA requires attorneys to disclose compliance status
In the generator (app features):
No clause-level editing — users can't toggle individual paragraphs within a section, only whole sections
No version history — if you regenerate, the old version is overwritten in preview (though saved in logs)
No PDF export — only HTML download and print; a real PDF via jsPDF or equivalent would be expected
No clause library / custom clause builder — power users need to add bespoke provisions
No multi-party support — joint ventures, multiple clients, or co-counsel arrangements
No currency selector — USD retainers for international clients are common
No signature date fields — currently blank underscores only
No e-signature integration placeholder — even a drawn/typed sig field
No document watermark option — "DRAFT" watermark for unsigned versions
No auto-populated notary fields from settings
No IBP chapter selector — different IBP chapters have jurisdiction-specific requirements
No retainer renewal/amendment generator — separate from fresh generation
No clause conflict detection — e.g., if ADR is off but governing law venue is set, that's inconsistent
New legal sections in the generated contract:
VAT treatment clause (exclusive/inclusive/exempt/zero-rated) with proper NIRC citation
Creditable withholding tax (CWT) at correct BIR rates (15%/10%/5%/0%), with BIR Form 2307 obligation
Late interest rate selector anchored to Nacar v. Gallery Frames (BSP 6% p.a.)
Billing Dispute Resolution — 15-day challenge window, undisputed payment obligation
Liability Cap — per engagement year, carve-out for willful misconduct
Trust / Client Fund Account provisions under Rule 16 CPRA
Sub-Contracting / Referral clause with three options
Data retention period (NPC-compliant, user-selectable 3–10 years) with 72-hour breach notification
MCLE compliance number disclosure field (CPRA 2023 requirement)
IBP Chapter selector (10 chapters)
New form fields:
Client TIN, SEC/DTI registration, contact info
Currency selector (PHP/USD/EUR/SGD) with live symbol sync
Both government ID types and numbers for counsel and client (2023 Notarial Rules acknowledgment table)
Typed e-signature fields (RA 8792 compliant) in cursive font
Witness 2 name, Notary PTR number
New app features:
Custom Clause Builder — unlimited bespoke provisions appended after standard sections
DRAFT watermark toggle on preview
Settings now has 10 individually toggleable clause switches (up from 6)

