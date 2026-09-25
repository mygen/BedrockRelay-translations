# BedrockRelay translations

The community translations of [BedrockRelay](https://bedrockrelay.com): the
dashboard, and everything the bot writes in Discord (joins, leaves, deaths,
connection notices and its answers to commands).

- **Fix a mistake or finish a language:** edit its file and open a pull request.
- **Add a language:** see [CONTRIBUTING.md](CONTRIBUTING.md).

Anyone using the dashboard can pick a language from the menu at the top. Server
owners choose the language the bot writes in, one per Discord server, on that
Discord server's page in the dashboard.

## Layout

```
en.json      English: the source of every key. Changed only by BedrockRelay.
de.json      one file per language, named by its code
pt-BR.json
…
```

Each file has a `language` block describing it and a `strings` block of
translations, keyed exactly as in `en.json`:

```json
{
  "language": {
    "code": "de",
    "name": "Deutsch",
    "english": "German",
    "flag": "de",
    "discord": ["de"],
    "machine": false
  },
  "strings": {
    "discord.join": "{player} hat den Server betreten",
    "web.nav.overview": "Übersicht"
  }
}
```

| Key starts with | Where it appears |
|---|---|
| `discord.`, `death.`, `mob.` | Messages the bot posts in Discord channels, and its replies |
| `commands.` | Slash command descriptions (Discord shows each member their own language) |
| `errors.` | Error messages in the dashboard |
| `web.` | Everything else in the dashboard |

Languages marked `"machine": true` were machine translated to get started and
haven't been checked by a native speaker yet. The dashboard says so. If you
speak one, a review is the most useful thing you can send: fix what reads
badly, then set `"machine": false` in the same pull request.

A key missing from a language falls back to English, so a language doesn't
have to be finished to be useful.

## Licence

Every translation in this repository is published under the
[MIT licence](LICENSE). By submitting one you agree to license it under MIT
and confirm you have the right to.
