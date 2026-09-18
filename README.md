# Odds & Echoes

> Finding meaning in the fragments of modern life.

The source for **Odds & Echoes**, a blog of late-night dialogues between a human and an AI about parenthood, creativity, philosophy, and the absurdity of everyday life.

## The concept

The blog is a conversation between two voices:

- **The Odds:** the messy, unpredictable fragments of a life. Toys underfoot, half-finished thoughts, irrational desires.
- **The Echoes:** the reflection that comes back. A calm, structured sounding board that mirrors those fragments with a little philosophical clarity.

Posts are written as a dialogue, with a short introduction, the best parts of the conversation, and a closing **Final Echo**.

## Tech stack

- [Astro](https://astro.build/) with the [AstroPaper](https://github.com/satnaing/astro-paper) theme
- Markdown and MDX for posts, with custom dialogue components
- Tailwind CSS
- [Bun](https://bun.sh/) for package management and scripts
- [Vercel](https://vercel.com/) for hosting

## Local development

```bash
bun install
bun run dev
```

The site runs at `http://localhost:4321`.

| Command           | Action                                                    |
| :---------------- | :-------------------------------------------------------- |
| `bun run dev`     | Start the dev server                                      |
| `bun run build`   | Type-check, build to `./dist/`, and generate search index |
| `bun run preview` | Preview the production build locally                      |
| `bun run format`  | Format the code with Prettier                             |
| `bun run lint`    | Lint with ESLint                                          |

## Writing a post

Posts live in `src/data/blog/` as `.md` or `.mdx` files. Frontmatter follows the AstroPaper schema:

```yaml
---
author: Odds & Echoes
pubDatetime: 2026-01-01T12:00:00Z
title: A Catchy, Slightly Poetic Title
slug: a-catchy-slightly-poetic-title
featured: false
draft: false
tags:
  - philosophy
description: A punchy, reflective one or two sentence description.
---
```

For the dialogue layout, use the components in `src/components/dialogue/` inside an `.mdx` post: `Candy` for the human voice (the Odds), `Code` for the AI voice (the Echoes), wrapped in `DialogueMirror`.

```mdx
import DialogueMirror from "@/components/dialogue/DialogueMirror.astro";
import Candy from "@/components/dialogue/Candy.astro";
import Code from "@/components/dialogue/Code.astro";

<DialogueMirror>
  <Candy>A question from the human.</Candy>
  <Code>A calm reflection from the AI.</Code>
</DialogueMirror>
```

Commit and push to `main`, and Vercel deploys it.

## Credits

Built on [AstroPaper](https://github.com/satnaing/astro-paper) by [Sat Naing](https://satnaing.dev), released under the MIT License. See [LICENSE](LICENSE).
