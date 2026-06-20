# cyy-writing

> A Codex/OpenClaw skill for turning reference articles into polished WeChat Official Account drafts.

`cyy-writing` is a lightweight writing workflow for creating 微信公众号文章. It guides an AI agent through style analysis, topic reconstruction, humanized rewriting, and WeChat-friendly inline HTML output.

## Highlights

- **5-stage writing workflow**: style deconstruction, topic rewrite, humanize pass, HTML layout, final packaging.
- **Reference-driven drafting**: starts from an article or source material and adapts its structure, voice, and audience fit.
- **A/B direction selection**: produces a conservative version and a more creative version before final drafting.
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

1. **Style deconstruction**  
   Analyze the reference article's structure, language texture, examples, emotional tone, and target audience.

2. **Topic reconstruction**  
   Produce two possible directions: one closer to the reference style, one with a fresher angle.

3. **Humanize pass**  
   Rewrite with more natural transitions, varied sentence length, conversational phrasing, and personal judgment.

4. **Inline HTML layout**  
   Convert the final markdown into WeChat-editor-friendly HTML with inline styles only.

5. **Final handoff**  
   Save markdown and HTML artifacts, then provide the final title, file location, and copy-paste guide.

## Best For

- WeChat Official Account articles
- Tech commentary and product launch posts
- Tutorial-style public-account drafts
- Reference-article rewriting and localization
- Chinese long-form content that needs a more human voice

## Notes

- The skill intentionally avoids external CSS and Tailwind-style classes because the WeChat editor may strip them.
- The bundled HTML file is a template, not a full publishing system.
- The original workflow references a Gemini sub-agent step from an OpenClaw setup. In Codex, adapt that step to whatever model or agent orchestration is available in your environment.

## License

No license has been declared yet. If you want others to reuse, modify, or redistribute this skill, add a license such as MIT or Apache-2.0.
