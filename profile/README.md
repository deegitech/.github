# DEEGITECH

**A small studio in Türkiye building games and developer tools.**

We make games, and we open-source the tools we build to ship them: careful command-line tools for small teams that
release apps, post video, run ads and publish code without a platform team behind them.

*Türkiye'den küçük bir stüdyoyuz. Oyun yapıyoruz; oyunlarımızı çıkarırken yazdığımız araçları da açık kaynak olarak paylaşıyoruz.*

## Tools

| Tool | What it saves you |
| --- | --- |
| [**ig-publish**](https://github.com/deegitech/ig-publish) | Hosting media and babysitting the Instagram Graph API: Stories and Reels go out from local files, in order, and never twice. |
| [**asc-release-kit**](https://github.com/deegitech/asc-release-kit) | Clicking through App Store Connect, and a Ruby toolchain: versions, builds, What's New and store text in many languages, every change read back. |
| [**adops-guard**](https://github.com/deegitech/adops-guard) | Accidental ad spend on Google Ads and Meta: every change is a dry run until `--apply`, held to your spend ceiling and read back. |
| [**social-video-qa**](https://github.com/deegitech/social-video-qa) | Rejected and quietly mangled uploads: checks videos against Instagram, TikTok, YouTube Shorts, Meta ads and App Store preview specs, then fixes them offline. |
| [**prepublish-audit**](https://github.com/deegitech/prepublish-audit) | Leaking secrets and internal details when you open-source a repo, publish a site or share a bundle: checks contents, metadata and git history against built-in patterns and your private denylist. |

All five are Python 3.10+ command-line tools under the MIT License. Install any of them with
`pipx install git+https://github.com/deegitech/<tool>`. Each README has a quickstart, a security model and an
honest list of limits.

### How we build them

- **Plan first.** Anything that changes a live account is a dry run until you add `--apply`, and a change only counts
  as done once it has been read back.
- **Secrets stay out of sight.** Tokens and keys come from environment variables, a `0600` file, the macOS Keychain
  or AWS SSM. They are never taken on the command line and are redacted from output, logs and journals.
  social-video-qa and prepublish-audit need no credentials and never open a network connection.
- **Safe to run twice.** Writes are journaled and idempotent, so a run that stopped halfway can be repeated without
  doing anything twice.
- **Honest about the platforms.** Behaviour we only saw in practice is labelled as observed, with a date, and never
  passed off as a documented rule.
- **Small supply chain.** No required third-party Python packages on Python 3.11+. Tests run offline against local
  mocks instead of live accounts, and CI adds CodeQL and a gitleaks secret scan.

## Libraries

- [**zadeh-net**](https://github.com/deegitech/zadeh-net): Lightweight Mamdani fuzzy inference engine for .NET 8+.

## Our games

- **Wide Molly Hooked**: a one-touch rope-swing climbing game for iPhone and iPad. Hold to grab, let go to fly, and
  don't let the dark catch you. [App Store](https://apps.apple.com/app/id6813081261) <!-- prepublish-audit:allow leak.numeric-id -->

## Contributing and security

Issues and pull requests are welcome; each project has a `CONTRIBUTING.md`.

**Found a vulnerability?** Please report it privately through GitHub's private vulnerability reporting on the
affected repository (its **Security** tab, then **Report a vulnerability**), not in a public issue.

<sub>Instagram, Meta, Google Ads, YouTube, TikTok, App Store and App Store Connect are trademarks of their owners. Our
tools are not affiliated with or endorsed by them.</sub>
