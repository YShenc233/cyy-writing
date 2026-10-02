# cyy-writing

> A Codex/OpenClaw skill for researching topics or rewriting templates into editable WeChat articles with images and GIFs.

`cyy-writing` creates CYY 小陈风格的微信公众号文章 for readers who use AI for coding and everyday work. It helps readers decide whether a tool is worth trying and how to start, with verified sources, concrete examples, local images and GIFs, and inline HTML output.

## Highlights

- **Direct first delivery**: full article in chat plus a matching Markdown document with available images.
- **Two drafting routes**: research a topic from reliable sources, or rewrite an uploaded template in CYY 小陈 style.
- **Markdown first**: deliver the article with local images/GIFs and a portable ZIP, then wait for user edits before generating HTML.
- **Notion archive**: store editable article content, media and stage-specific attachments under an authorized parent page; later update the same page.
- **Official-source research**: verifies new-model announcements, capabilities, pricing and access on the vendor's website; collects useful benchmark and pricing screenshots.
- **X case research and visible results**: required for both AI drafting routes; checks original posts, embeds actual results or GIF excerpts in relevant sections, explains what to observe, and labels uncertain model identities and missing evidence before delivery.
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
        ├── workflow-examples.md
        ├── x-case-workflow.md
        └── notion-archive.md
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

1. **Choose the route**: research a topic, or read and adapt the uploaded template and its media.
2. **Deliver illustrated Markdown**: write the full article, insert verified images/GIFs, check local references and animation frames, and provide Markdown plus a ZIP preserving `images/`.
3. **Save the current stage**: use the authorized local root and Notion destination. Name new article folders/pages `YYYY.MM.DD-公众号标题`; keep the original date for older articles. Saving alone does not trigger HTML.
4. **Wait for edits**: update the same Markdown. If the user edits in Notion, read the current page and media before layout.
5. **Generate HTML after finalization**: render the latest approved text and media with inline styles, verify the result, then update attachments and the same Notion page.

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
- Personal save-directory and Notion destination records live in `memory/` under the installed skill directory and are excluded from this repository. Page IDs, local paths, article files and upload credentials are not distributed with the skill.
- Notion integration depends on the host connection and its current upload tools; local Markdown/media remain available if the connection fails.
- Markdown needs its `images/` folder. Local HTML preferably embeds media for offline reading; when relative paths are used, preserve the folder structure. Images/GIFs that the WeChat editor does not import on paste need to be uploaded separately.

## License

No license has been declared yet. If you want others to reuse, modify, or redistribute this skill, add a license such as MIT or Apache-2.0.
