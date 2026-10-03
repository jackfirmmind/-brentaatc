# Right-Hire Blueprint

A free hiring tool for employers, built for AccessAbility Talent Connect as a lead magnet.

An employer answers 18 questions in about 4 minutes. They see a one-line teaser of their result with the rest blurred, enter their name and email to unlock it, and get a personalised hiring blueprint. At the end, one button opens an email to Brent with their brief already filled in.

- `index.html`: the whole tool in one self-contained file (no build step, no server).
- `MESSAGES.md`: the message to Brent, the email he sends to leads, a short LinkedIn/WhatsApp version and a follow-up.

## The 3 employer pain points it's built around

| Pain point | What the employer is thinking | How the tool helps |
|---|---|---|
| **The fuzzy brief** | "We're not 100% sure who we need." | Part 1 makes them commit to one core outcome, check whether decision-makers agree, and pick three non-negotiables. It returns a *Brief clarity* score and a written ideal-candidate profile. |
| **The costly mis-hire** | "What if we hire the wrong person?" | Part 2 brings out mismatches (level vs. priority, management style vs. seniority, what went wrong with the last hire, a narrow talent pool). It returns a *Mis-hire risk* score, watch-outs with fixes, and a tailored interview cheat-sheet. |
| **The empty seat** | "We can't afford for this to drag on." | Part 3 measures timeline, team strain and their own time. It returns a *Vacancy pressure* score, what the vacancy costs in Rands, and a hiring plan with the steps the agency can take off their plate. |

## What the results include

- A hiring profile (one of 15), with its edge and its trap
- A hire readiness score and three risk meters
- Advice on the specific worry they chose
- An ideal-candidate profile written in plain language
- Cost of the vacancy, cost of a mis-hire, and cost of a 2-month delay (based on their budget band)
- Watch-outs ranked by severity, each with a fix (22 rules)
- An interview cheat-sheet built from their non-negotiables and core outcome
- A job ad opener they can copy
- A hiring plan for their timeline (10-day, 4-week, 6-week, or ongoing)
- An inclusion section (adjustment costs, research, EE/B-BBEE)
- "Send my blueprint to Brent", which opens an email in their mail app, Gmail or Outlook. They can also copy the summary or save the blueprint as a PDF.

There are well over 500,000 possible results. In a test of 1.5 million random answer sets, 1.47 million produced different blueprints.

## Before going live: edit the `CONFIG` block

At the top of the `<script>` in `index.html`:

```js
agencyName:  'AccessAbility Talent Connect',
contactName: 'Brent',
agencyEmail: 'brent@accessabilitytalentconnect.com', // ← confirm this
region:      'ZA',   // '' hides the EE / B-BBEE notes
currency:    'R',
budgets:     [...],  // salary bands and the midpoints used for the cost estimates
leadWebhook: ''      // optional, see below
```

Brand colours live in the `:root` CSS variables at the top of the file.

## Optional: capture every lead automatically

Out of the box, nothing leaves the visitor's browser until they choose to email their blueprint. To capture every unlock (name, email, company, role, scores and the full summary) as well, create a webhook in Zapier, Make, n8n, Formspree or a Google Apps Script and paste its URL into `leadWebhook`. Each unlock, send and copy is then posted to it as a form. The privacy wording on the page updates automatically.

## Hosting (any of these work)

1. **Netlify Drop** (quickest): go to app.netlify.com/drop and drag in a folder containing `index.html`. You get a live link in seconds.
2. **Brent's own site**: upload `index.html` as a page, e.g. `accessabilitytalentconnect.com/hiring-blueprint`.
3. **GitHub Pages / Vercel**: serve this repo as a static site.

## Accessibility

Built to WCAG 2.2 AA principles, which matters for an accessibility-focused agency: real form controls with labels, full keyboard support, visible focus, focus moved to each new question for screen readers, no auto-advance for keyboard users, AA contrast, respects reduced-motion settings, and supports Windows high-contrast mode.
