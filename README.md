# Professional Puerto Rican Spanish

A Claude skill that translates work text into the Spanish people actually write in Puerto Rican offices.

## Why this exists

Puerto Rican Spanish at work mixes in a lot of English, especially for tech, media, marketing, and office terms. Nobody in a San Juan office says "archivo fuente" or "ordenador portátil". They say "source file" and "laptop".

LLMs usually get this wrong in one of two ways:

1. **Too textbook.** They translate every term into "proper" Spanish, so the text sounds stiff or like it came from Spain or Mexico.
2. **Too Boricua.** Ask for "Puerto Rican Spanish" and they throw in slang like "wepa" or "pana", which doesn't belong in a work email.

This skill aims for the middle: clean, professional Spanish that keeps the English terms a bilingual professional in Puerto Rico would actually use.

## Example

**English:**

> Our media team is kindly requesting both the jpeg file and source file to ensure proper placement in the program. Let me know how else I can help.

**Typical LLM translation:**

> Nuestro equipo de medios le solicita amablemente tanto el archivo JPEG como el archivo fuente para asegurar la colocación correcta en el programa. Déjeme saber en qué más le puedo ayudar.

**With this skill:**

> Nuestro media team le solicita amablemente tanto el archivo JPEG como el source file para asegurar el placement correcto en el programa. Déjeme saber en qué más le puedo ayudar.
>
> Términos en inglés: media team, source file, placement

After each translation, it lists the English terms it kept, so you can swap any you don't want.

## What it does

- Keeps common work terms in English (link, laptop, deadline, feedback, source file, layout, and more)
- Uses Puerto Rican word choices over other regions (computadora, carro, celular, adiestramiento, planilla)
- Never adds slang
- Matches the tone of the original and uses usted for clients and external contacts
- Follows PR conventions: US-style numbers and dollars, "Déjeme saber", "Hola:" greetings
- Goes more formal for government and legal documents, where Spanish terms are the norm

## It only runs when you call it

This is a manual skill. Claude won't use it on its own for every Spanish request. You call it by name and give it the text.

## Install

### Claude app (web, desktop, mobile)

1. Download `professional-pr-spanish.zip` from the [latest release](../../releases/latest).
2. Make sure code execution is on. On Free, Pro, and Max plans it's under **Settings > Capabilities > Code execution and file creation**. On Team and Enterprise, an admin turns on skills in organization settings.
3. Go to **Customize > Skills**, click **+**, then **Create skill > Upload a skill**, and pick the zip.
4. Make sure the skill is toggled on.

Don't unzip it first. Claude expects the zip with the `professional-pr-spanish` folder inside.

### Claude Code

Personal install, for all your projects:

```bash
git clone https://github.com/Sacarianos/professional-pr-spanish.git
mkdir -p ~/.claude/skills
cp -r professional-pr-spanish/professional-pr-spanish ~/.claude/skills/
```

To use it in one project only, copy it to `.claude/skills/` inside that project instead.

**Optional, Claude Code only:** to make sure Claude can never use it on its own, add this line to the frontmatter at the top of `SKILL.md`, under `description`:

```yaml
disable-model-invocation: true
```

Don't add that line to the version you upload to the Claude app. The app doesn't support it and may reject the upload.

## How to use it

**Claude app:** name the skill and paste your text.

```
Use the professional-pr-spanish skill to translate this:

Hi Ana, attached is the updated flyer. Can you send me your feedback before Friday's deadline?
```

**Claude Code:** type the slash command, then the text.

```
/professional-pr-spanish Hi Ana, attached is the updated flyer. Can you send me your feedback before Friday's deadline?
```

If you call it without any text, it will ask you for some.

## Customize it

Everything lives in one file: [`professional-pr-spanish/SKILL.md`](professional-pr-spanish/SKILL.md). It's plain text, so you can edit it directly:

- **Add or remove English terms** in the "Usually keep in English" section to match your field.
- **Add word swaps** to the regional table.
- **Add examples** from your own work. Examples from different kinds of messages help it the most.

After editing, re-zip the `professional-pr-spanish` folder and upload it again in the Claude app.

## Contributing

The term lists are a starting point, not a final word. If it keeps a word in English that people in PR would say in Spanish, or the other way around, open an issue or a pull request with the word and a sentence showing how it's used.

## License

[MIT](LICENSE)
