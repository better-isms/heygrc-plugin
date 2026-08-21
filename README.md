# heyGRC for Claude Code

**GRC compliance review for your pull requests.** heyGRC reviews each PR against ISO 27001, SOC 2,
GDPR, the EU AI Act, DORA, NIS 2 and your own company profile, then posts inline findings, a neutral
check run, and a sticky summary comment. Public repositories are free.

By [Better ISMS](https://heygrc.com).

## Install

This repository is a self-hosted Claude Code plugin marketplace. Add it and install the plugin:

```
/plugin marketplace add better-isms/heygrc-plugin
/plugin install heygrc@heygrc
```

Then run the setup skill:

```
/heygrc:review
```

It walks you through installing the heyGRC GitHub App, configuring your company profile and
frameworks as code, and choosing how often reviews run. Full instructions are in [SETUP.md](./SETUP.md).

## What it does

heyGRC runs as a GitHub App, so reviews happen server-side, not on your machine. On each pull request
it posts:

- **Inline findings** on the exact lines that touch a compliance obligation, each with a control
  reference and a short reason.
- **A neutral check run.** heyGRC never fails a check or blocks a merge.
- **One sticky summary comment per PR**, updated in place.

## Pricing

- **Public repositories:** always free.
- **Private repositories:** free up to 25 reviews per month. Claiming your install starts a 14-day
  unlimited-private trial; after that, on-demand private reviews are $0.49 each.

See [pricing and plans](https://docs.heygrc.com/docs/pricing-and-plans).

## Links

- Website: https://heygrc.com
- Docs: https://docs.heygrc.com
- Setup with your agent: https://docs.heygrc.com/docs/setup-with-an-agent
- Privacy policy: https://trust.ismscopilot.com/en/privacy-policy
- Terms: https://trust.ismscopilot.com/en/terms
- Support: support@ismscopilot.com

## License

MIT. See [LICENSE](./LICENSE).
