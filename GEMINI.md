# heyGRC compliance review

You (Gemini) can set up and run heyGRC compliance review for this repository's pull requests. heyGRC
reviews each PR against ISO 27001, SOC 2, GDPR, DORA, NIS 2, the EU AI Act and the org's company
profile, then posts inline findings, a neutral check run, and a sticky summary comment on the PR.

heyGRC runs as a GitHub App server-side. It does not review code on this machine. Your job is to get
it installed and configured.

## Setup

1. **Install the GitHub App (the user clicks once):**
   `https://github.com/apps/heygrc/installations/new?via=gemini-cli`
   Installing is an account-owner action; no agent or API can do it for them. heyGRC asks for
   read-only Contents and metadata, plus read + write on Checks and Pull requests. A bare install
   already reviews PRs with default frameworks under Free-plan limits.

2. **Get a review:** open a pull request, or comment `/heygrc` on one (commenter must be an Owner,
   Member, or Collaborator).

3. **Claim and configure (optional, sharpens every review):** the user signs in at
   https://app.heygrc.com to claim the install (this starts the 14-day trial) and creates an API key
   (`hgrc_...`, shown once). Store it as `HEYGRC_API_KEY` and send it only in the `Authorization`
   header. Then write the company profile and frameworks with one call:

```bash
curl -X PUT https://api.heygrc.com/v1/config \
  -H "Authorization: Bearer $HEYGRC_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "profile": {
      "company": "Acme Inc",
      "product": "B2B SaaS for invoice automation",
      "data_handled": "customer PII, payment metadata, uploaded documents",
      "hosting": "EU, AWS eu-central-1",
      "compliance_posture": "pursuing SOC 2 and ISO 27001; ships an AI feature"
    },
    "frameworks": ["ISO_27001", "SOC_2", "GDPR", "EU_AI_ACT"]
  }'
```

4. **Cadence** (set in the console, per org or repo): `auto` (default) reviews every PR;
   `auto_once` only on open/reopen; `mention_only` waits for a `/heygrc` comment.

heyGRC never fails a check or blocks a merge; it informs the humans and agents shipping the code.
Public repositories are always free. Private repos: 25 reviews/month free; claiming starts a 14-day
unlimited-private trial.

Docs: https://docs.heygrc.com/docs/setup-with-an-agent | Pricing: https://docs.heygrc.com/docs/pricing-and-plans
