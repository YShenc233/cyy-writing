# cyy-writing

> A Codex/OpenClaw skill for turning reference articles into polished WeChat Official Account drafts.

`cyy-writing` creates CYY 小陈风格的微信公众号文章 for readers who use AI for coding and everyday work. It helps readers decide whether a tool is worth trying and how to start, with verified sources, concrete examples, local images and GIFs, and inline HTML output.

## Highlights

- **Direct first delivery**: full article in chat plus a matching Markdown document with available images.
- **Reference-driven drafting**: starts from an article or source material and adapts its structure, voice, and audience fit.
- **Official-source research**: verifies new-model announcements, capabilities, pricing and access on the vendor's website; collects useful benchmark and pricing screenshots.
- **X case research**: checks original posts for coding and office-work demos, user experiences and failures, then embeds relevant images or GIF excerpts in the article.
- **Practical decisions**: explains what a result is suitable for, what needs checking, and a first task the reader can try.
- **WeChat-safe HTML template**: uses inline styles that survive the WeChat editor better than external CSS or class-based styling.
- **Humanized Chinese copy**: nudges the draft away from stiff AI prose and toward a conversational public-account voice.

## Repository Structure

```text
.
├── README.md
└── cyy-writing/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    ├── assets/
    │   └── wechat-template.html
    └── references/
        └── workflow-examples.md
```

## Install

### Codex

Copy the skill folder into your Codex skills directory:

```powershell
Copy-Item -Recurse .\cyy-writing "$env:USERPROFILE\.codex\skills\cyy-writing"
```

Restart Codex, then invoke it naturally:

```text
Use $cyy-writing to turn this reference article into a WeChat Official Account article.
```

### OpenClaw

Copy the skill folder into your OpenClaw workspace skills directory:

```powershell
Copy-Item -Recurse .\cyy-writing "$env:USERPROFILE\.openclaw\workspace\skills\cyy-writing"
```

## Workflow

1. **Direct draft delivery**
   Research official sources and case materials, analyze the reference, and deliver the full CYY-style article in chat with a matching Markdown document.

2. **Revise and finalize**
   Apply feedback to the article and the same Markdown file.

3. **Confirm the save location**
   Use local directory history to determine the final output location.

4. **Organize final files**
   Save final Markdown and local media in an article directory without accumulating intermediate drafts.

5. **Inline HTML layout and handoff**
   Generate WeChat-editor-friendly HTML with inline styles, and provide file locations and a copy-paste guide.

## Best For

- WeChat Official Account articles
- Tech commentary and product launch posts
- Tutorial-style public-account drafts
- Reference-article rewriting and localization
- Chinese long-form content that needs a more human voice

## Notes

- The skill intentionally avoids external CSS and Tailwind-style classes because the WeChat editor may strip them.
- The bundled HTML file is a template, not a full publishing system.
- Website and X research use the tools available in the host environment. The skill does not include a publishing service or a media downloader.
- Personal save-directory history lives in `memory/save-roots.json` under the installed skill directory and is excluded from this repository.
- Keep the HTML file beside its `images/` folder when moving it. Images or GIFs that the WeChat editor does not import on paste need to be uploaded separately.

## License

No license has been declared yet. If you want others to reuse, modify, or redistribute this skill, add a license such as MIT or Apache-2.0.
