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

### 2.2 Content Model Update
- **`src/content.config.ts`**: Update the `blog` collection's loader to support `.mdx` files.
- **`src/data/blog/`**: Future posts will use the `.mdx` extension.

## 3. The "Existential Mirror" Layout
The dialogue will be presented as a vertical split, emphasizing the "mirroring" aspect.

### 3.1 Components
1.  **`<Candy />` (The Human):**
    - **Position:** Left-aligned, positioned to the left of a central vertical mirror line.
    - **Typography:** Serif font (e.g., `Georgia`, `Times New Roman`).
    - **Style:** Warm, literary, and slightly "messy."
2.  **`<Code />` (The AI):**
    - **Position:** Right-aligned, positioned to the right of the central vertical mirror line.
    - **Typography:** Monospace terminal font (e.g., `Google Sans Code`).
    - **Style:** Cold, precise, and structured.

### 3.2 Visual Treatment
- **Central Mirror Line:** A light, vertical line running down the center of the dialogue section to divide the human and machine perspectives.
- **Monochrome Contrast:** The primary visual distinction is alignment and typography rather than heavy background colors.

## 4. Content Generation Workflow
- **Creation:** Conversations can be held with the Gemini CLI (or any AI).
- **Transformation:** The transcript is converted into an `.mdx` file where human lines are wrapped in `<Candy>` tags and AI lines in `<Code>` tags.

## 5. Success Criteria
- [ ] `@astrojs/mdx` is integrated and rendering correctly.
- [ ] `<Candy>` and `<Code>` components are functional and visually distinct.
- [ ] The "Mirror" layout (vertical line and alignment) is responsive and legible.
- [ ] A sample `.mdx` post is generated and displays correctly in the blog.
