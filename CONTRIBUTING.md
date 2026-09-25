# Contributing a translation

Open a pull request that changes one language file. Small fixes are as
welcome as whole languages.

**Licence:** everything in this repository is published under the
[MIT licence](LICENSE). By opening a pull request you agree that your
contribution is licensed under MIT, and you confirm that you wrote it or
otherwise have the right to license it that way.

## Adding a language

1. Copy `en.json` to `<code>.json`. The code is the language's BCP 47 tag:
   `it`, `nl`, `tr`, `ko`, `pt-PT`, `zh-TW`.
2. Fill in the `language` block:
   - `code`: the same as the file name.
   - `name`: the language's name in itself, as the menu shows it (`Italiano`).
   - `english`: its name in English, for reviewers (`Italian`).
   - `flag`: a two-letter country code for the menu's flag (`it`). We add the
     flag image when we merge.
   - `discord`: the [Discord locale codes](https://discord.com/developers/docs/reference#locales)
     that mean this language (`["it"]`). This is how BedrockRelay picks it
     automatically for a Discord server set to that language.
   - `machine`: `false`, since you translated it yourself.
3. Translate the values under `strings`. Leave the keys alone. You can delete a
   key you're not sure about, and English is used for it.

## Rules every string must follow

A check runs on every language file. A string that breaks a rule is left out,
and the English one is used in its place.

- **Keep every `{placeholder}`** exactly as it is in `en.json`: `{player}`,
  `{server}`, `{count}`. Move them wherever your grammar needs them; don't
  translate or remove them, and don't add new ones.
- **Plurals:** where `en.json` has an object like
  `{ "one": "…", "other": "…" }`, give the forms your language uses:
  `zero`, `one`, `two`, `few`, `many`, `other` (the
  [CLDR plural rules](https://www.unicode.org/cldr/charts/latest/supplemental/language_plural_rules.html)).
  `other` is always required. Languages without plurals, like Japanese, use
  just `other`.
- **No mentions:** nothing that pings anyone in Discord (`@everyone`, `@here`,
  `<@…>`, `<#…>`).
- **Keep `code`, commands and file names as they are:** `/relay link`,
  `player:<your name>`, `server.properties`, `enable-lan-visibility`. Text
  inside backticks is something people type or see exactly.
- **Keep it short** where it is short in English. Buttons and Discord labels
  have little room: a Discord modal title fits 45 characters.

## Style

Write the way the English is written: plain, friendly, and direct, speaking
to the reader as "you". Use the informal "you" where your language has one
(du, tu, ты). Use Minecraft's own names for mobs, as the game does in your
language. Keep "BedrockRelay", "Discord" and "Minecraft" as they are.

## Checking your file

With the BedrockRelay code checked out, `npm run test:i18n` in `gateway/`
checks every language file and lists anything a rule would leave out.
Otherwise, we check it when you open the pull request.
