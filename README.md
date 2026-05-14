# Humanize PPT

**Humanize PPT** is an AST-based outline director for human-centered AI presentation workflows.

It does not try to be another slide template. It turns raw material into an audience-aware, presentation-ready deck brief before handing it to downstream PPT / HTML slide skills.

中文定位：**基于 AST 理论的人感 PPT 大纲导演 Skill**。

## Core idea

> PPT is not an information container. PPT is an audience state-transfer artifact.

Humanize PPT first answers:

- **Audience**: Who is this for?
- **State**: What state are they in before and after the deck?
- **Transfer**: How should each slide move them from one state to the next?

Only after that should the deck be rendered by tools such as guizang, Zara-style HTML templates, HyperFrames, presenter shells, or deployment adapters.

## V0.1 public preview

V0.1 is intentionally narrow. It validates this pipeline:

```text
Raw material
→ Humanize PPT / AST Outline Director
→ Style exploration HTML deck
→ Presenter Adapter shell
→ Static deploy package
```

V0.1 includes:

- `SKILL.md` — agent skill entrypoint
- `docs/AST-theory.md` — AST theory
- `docs/OPC-workflow.md` — Outline / Produce / Complete workflow
- `contracts/` — output contract templates
- `scripts/humanize_ppt_v1.py` — deterministic local demo runner
- `examples/01-ai-tool-update/source.md` — safe sample input

## Quick start

```bash
python3 scripts/humanize_ppt_v1.py \
  --source examples/01-ai-tool-update/source.md \
  --out .humanize-ppt-runs/ai-tool-update \
  --title "AI 工具更新，不只是功能清单"

open .humanize-ppt-runs/ai-tool-update/styles/index.html
open .humanize-ppt-runs/ai-tool-update/presenter/index.html
```

The runner produces:

```text
out/
  deck_brief.md
  ast_outline.md
  slide_plan.json
  speaker_intent.md
  asset_manifest.md
  video_slots.json
  styles/
    index.html
    guizang-stable.html
    zara-editorial.html
    zara-contrast.html
  presenter/
    index.html
    notes.json
  deploy/
    index.html
    presenter.html
```

## What it is not

- Not a generic PPT generator.
- Not a fixed bundle of several HTML PPT skills.
- Not a normal text humanizer.
- Not a template converter between guizang and Zara.

## License

MIT
