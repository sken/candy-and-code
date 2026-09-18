# The Candy & The Code Dialogue Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Implement a responsive, visually stark dialogue system using Astro + MDX that allows for an "existential mirror" layout between human (**The Candy**) and AI (**The Code**).

**Architecture:** 
- **MDX Integration:** Leverage `@astrojs/mdx` for component-in-markdown support.
- **Component-Based Layout:** A `<DialogueMirror>` container using a CSS grid to create a vertical split with a central line.
- **Typography-Driven Distinction:** Using Serif (Human) vs. Monospace (AI) fonts to define speaker identity.

**Tech Stack:** Astro, MDX, Tailwind CSS 4.0 (for layout/styling).

---

### Task 1: Setup MDX Integration

**Files:**
- Modify: `package.json` (via install)
- Modify: `astro.config.ts`

- [ ] **Step 1: Install `@astrojs/mdx`**
Run: `npm install @astrojs/mdx`
Expected: Package added to dependencies.

- [ ] **Step 2: Add MDX integration to Astro config**
Modify `astro.config.ts` to include the MDX integration.
```typescript
import mdx from "@astrojs/mdx";
// ...
integrations: [
  mdx(),
  // ... existing integrations
],
```

- [ ] **Step 3: Commit**
```bash
git add package.json astro.config.ts
git commit -m "feat: add mdx integration"
```

---

### Task 2: Update Content Configuration

**Files:**
- Modify: `src/content.config.ts`

- [ ] **Step 1: Update loader pattern to support .mdx**
Change the glob pattern to include both `.md` and `.mdx`.
```typescript
loader: glob({ pattern: "**/[^_]*.{md,mdx}", base: `./${BLOG_PATH}` }),
```

- [ ] **Step 2: Commit**
```bash
git add src/content.config.ts
git commit -m "feat: support mdx in blog collection"
```

---

### Task 3: Create Dialogue Components

**Files:**
- Create: `src/components/dialogue/DialogueMirror.astro`
- Create: `src/components/dialogue/Candy.astro`
- Create: `src/components/dialogue/Code.astro`

- [ ] **Step 1: Implement DialogueMirror.astro**
Create the container with the central mirror line and responsive grid.
```astro
---
---
<div class="dialogue-mirror relative my-12 grid grid-cols-1 gap-y-8 md:grid-cols-2 md:gap-y-0">
  <!-- The Mirror Line (Desktop only) -->
  <div class="absolute left-1/2 top-0 hidden h-full w-px bg-accent/20 md:block -translate-x-1/2"></div>
  <slot />
</div>
```

- [ ] **Step 2: Implement Candy.astro (The Human)**
Create the human component with serif typography and "messy" margins.
```astro
---
---
<div class="candy-message md:pr-12 md:text-right" aria-label="Human (The Candy)">
  <div class="font-serif italic leading-relaxed text-lg md:ml-auto md:max-w-[80%]">
    <slot />
  </div>
</div>
```

- [ ] **Step 3: Implement Code.astro (The AI)**
Create the AI component with monospace typography and precise layout.
```astro
---
---
<div class="code-message md:pl-12" aria-label="AI (The Code)">
  <div class="font-mono text-sm leading-tight text-accent/90 md:max-w-[80%]">
    <slot />
  </div>
</div>
```

- [ ] **Step 4: Commit**
```bash
git add src/components/dialogue/
git commit -m "feat: add Candy and Code dialogue components"
```

---

### Task 4: Create Verification Post

**Files:**
- Create: `src/data/blog/existential-mirror-test.mdx`

- [ ] **Step 1: Create sample MDX post**
Write a short dialogue using the new components.
```mdx
---
author: Candy & Code
pubDatetime: 2026-03-14T10:00:00Z
title: The Mirror of Silicon and Soul
slug: mirror-test
description: Testing the new existential mirror dialogue layout.
---
import DialogueMirror from '@/components/dialogue/DialogueMirror.astro';
import Candy from '@/components/dialogue/Candy.astro';
import Code from '@/components/dialogue/Code.astro';

Testing the new dialogue system.

<DialogueMirror>
  <Candy>Why do we keep searching for patterns in the noise?</Candy>
  <Code>Because noise is the only thing that doesn't lie to you.</Code>
  <Candy>But noise has no heart. It just exists.</Candy>
  <Code>Heart is a pattern you projected onto the noise. It exists because you do.</Code>
</DialogueMirror>
```

- [ ] **Step 2: Verify in build**
Run: `npm run build`
Expected: Build succeeds without MDX errors.

- [ ] **Step 3: Commit**
```bash
git add src/data/blog/existential-mirror-test.mdx
git commit -m "test: add existential mirror verification post"
```
