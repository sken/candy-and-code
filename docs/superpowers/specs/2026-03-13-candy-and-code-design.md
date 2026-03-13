# Design Spec: The Candy & The Code

**Date:** 2026-03-13  
**Status:** Approved  
**Topic:** Existential Human-AI Dialogue System for Astro Blog

## 1. Vision & Purpose
"The Candy & The Code" is a blog built on Astro that explores the "existential mirror" between human creativity and machine logic. The core feature is a **Dialogue System** that visually represents a conversation between a human (**The Candy**) and an AI (**The Code**).

The layout should emphasize the contrast between the organic, messy human and the structured, indifferent silicon.

## 2. Technical Strategy
We will use **Astro + MDX** to enable a clean, component-based dialogue syntax directly within Markdown files.

### 2.1 Dependencies
- `@astrojs/mdx`: Required for rendering custom components (`<Candy />` and `<Code />`) in blog posts.
- **Install command:** `npx astro add mdx` or `bun add @astrojs/mdx` (manually).

### 2.2 Content Model Update
- **`src/content.config.ts`**: Update the `blog` collection's loader pattern to `pattern: "**/[^_]*.{md,mdx}"`.
- **`src/data/blog/`**: Future posts will use the `.mdx` extension.

## 3. The "Existential Mirror" Layout
The dialogue will be presented as a vertical split, emphasizing the "mirroring" aspect.

### 3.1 Components
All components will be located in `src/components/dialogue/`.

1.  **`<DialogueMirror />` (The Container):**
    - **Purpose:** Provides the layout context (Flex/Grid) for the conversation and renders the central vertical line.
    - **Layout:** On desktop, a 2-column grid with a thin vertical border between columns. On mobile, the columns stack vertically, and the mirror line is hidden.
    - **Accessibility:** Uses a `<section>` or `<div role="log" aria-label="Conversation between Human and AI">`.

2.  **`<Candy />` (The Human):**
    - **Position:** Left of the mirror line.
    - **Typography:** Serif font (e.g., `Georgia`, `Times New Roman`).
    - **Style:** "Slightly messy" achieved via irregular margins (e.g., `margin-bottom: 1.5rem`, `margin-left: 0.5rem`), slightly looser line-height, and potentially a subtle tilt or organic border-radius.
    - **Accessibility:** Wrapped in a `<div>` with `aria-label="Human (The Candy)"`.

3.  **`<Code />` (The AI):**
    - **Position:** Right of the mirror line.
    - **Typography:** Monospace terminal font (`Google Sans Code`).
    - **Style:** Cold, precise, and structured. Perfect alignment, consistent padding, and a sharp, rectangular border-radius.
    - **Accessibility:** Wrapped in a `<div>` with `aria-label="AI (The Code)"`.

### 3.2 Visual Treatment & Responsiveness
- **Central Mirror Line:** A 1px wide, low-opacity line (`border-accent/20`) that appears only on screens wider than 768px.
- **Mobile Fallback:** On small screens, the `<Candy>` and `<Code>` components stack vertically. `<Candy>` stays left-aligned, and `<Code>` becomes left-aligned but retains its monospace styling to maintain distinction.
- **Monochrome Contrast:** The primary visual distinction is alignment and typography rather than heavy background colors.

## 4. Content Generation Workflow
- **Creation:** Conversations can be held with the Gemini CLI (or any AI).
- **Transformation:** The transcript is converted into an `.mdx` file where human lines are wrapped in `<Candy>` tags and AI lines in `<Code>` tags.

## 5. Success Criteria
- [ ] `@astrojs/mdx` is integrated and rendering correctly.
- [ ] `<Candy>` and `<Code>` components are functional and visually distinct.
- [ ] The "Mirror" layout (vertical line and alignment) is responsive and legible.
- [ ] A sample `.mdx` post is generated and displays correctly in the blog.
