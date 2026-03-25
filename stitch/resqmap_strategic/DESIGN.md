# Design System Specification: High-Response Editorial

## 1. Overview & Creative North Star
**The Creative North Star: "The Sentinel Archive"**

In an emergency, clarity isn't just a preference—it’s a requirement. This design system rejects the "cluttered dashboard" trope in favor of an **Editorial Authority** aesthetic. By combining high-contrast functionalism with sophisticated tonal layering, we move beyond a standard map utility into a premium, calm, and decisive command center.

The "Sentinel Archive" approach uses **intentional asymmetry** and **breathing room** to reduce cognitive load. We break the rigid grid by using overlapping "information sheets" and varied typography scales that guide the eye to the most critical data first. It feels less like a generic app and more like a high-end, digital field manual.

---

## 2. Colors & Surface Philosophy
The palette is rooted in high-visibility functionality, using Material Design tokens to create a "Tactile Glass" experience.

### The "No-Line" Rule
**Explicit Instruction:** Designers are prohibited from using 1px solid borders for sectioning. Boundaries must be defined solely through background color shifts or subtle tonal transitions. For example, a map sidebar should use `surface_container_low` sitting against a `surface` background.

### Surface Hierarchy & Nesting
Treat the UI as a series of stacked, physical layers. 
- **Base Level:** `surface` (#faf8ff) for the widest layout areas.
- **Mid Level:** `surface_container` (#ededf7) for primary content blocks.
- **Top Level:** `surface_container_highest` (#e1e2ec) for active interaction states or critical overlays.
This "nested depth" creates a natural hierarchy without the visual noise of dividers.

### The "Glass & Gradient" Rule
Floating panels and navigation bars should utilize **Glassmorphism**. Apply `surface_container_low` at 80% opacity with a `backdrop-blur` of 20px. This allows map data to bleed through subtly, maintaining environmental context. 

### Signature Textures
Main Action buttons (CTAs) should not be flat. Use a subtle linear gradient from `primary` (#00478d) to `primary_container` (#005eb8) at a 135-degree angle to provide "visual soul" and a tactile, pressed-ink feel.

---

## 3. Typography
We utilize a dual-sans-serif pairing to balance high-end editorial aesthetics with rapid-response legibility.

- **Display & Headlines (Public Sans):** A sturdy, geometric sans-serif that commands authority. Use `display-lg` (3.5rem) for critical status updates and `headline-md` (1.75rem) for location headers.
- **Body & Labels (Inter):** Chosen for its exceptional x-height and legibility under stress. 
- **The Hierarchy of Urgency:** Use `title-lg` (1.375rem) in `secondary` (#b6171e) for active alerts. Use `label-md` (0.75rem) with `on_surface_variant` (#424752) for metadata to ensure secondary info stays secondary.

---

## 4. Elevation & Depth
Depth is achieved through **Tonal Layering** rather than traditional structural lines.

- **The Layering Principle:** Place a `surface_container_lowest` (#ffffff) card on a `surface_container_low` (#f2f3fd) section. This creates a soft, natural lift that mimics fine paper.
- **Ambient Shadows:** For floating map markers or emergency modals, use a "Sentinel Shadow": `blur: 32px`, `spread: -4px`, and `color: rgba(25, 27, 34, 0.08)`. The shadow must be a tinted version of the `on_surface` color to feel integrated with the atmosphere.
- **The "Ghost Border" Fallback:** If a container requires further definition (e.g., in high-glare outdoor use), use the `outline_variant` token at **15% opacity**. 100% opaque borders are strictly forbidden.

---

## 5. Components

### Buttons
- **Primary (Emergency Action):** Gradient fill (`primary` to `primary_container`), `rounded-md` (0.375rem). Text in `on_primary`.
- **Secondary (Safe Zone/Resource):** `tertiary_container` (#1d6e25) fill with `on_tertiary_container` text.
- **Tactile State:** On hover, shift the gradient 180 degrees. On press, scale the component to 98% to simulate physical feedback.

### Resource Cards & Lists
- **The No-Divider Rule:** Forbid the use of horizontal lines. Separate list items using `spacing-4` (0.9rem) of vertical white space or by alternating background tones between `surface_container_low` and `surface_container`.
- **Typography as Separator:** Use `label-sm` in all-caps with 0.05em letter spacing to categorize list sections.

### Status Chips
- **Urgent:** `secondary_container` (#da3433) background with `on_secondary_fixed` (#410003) text.
- **Stable:** `tertiary_fixed` (#a3f69c) background with `on_tertiary_fixed` (#002204) text.
- **Shape:** Use `rounded-full` (9999px) for chips to contrast against the more architectural `rounded-md` cards.

### Map Markers (Context Specific)
Markers should use a "Pin-Drop" shape with a `surface_container_lowest` core and a 2px "Ghost Border" of the category color (`primary`, `secondary`, or `tertiary`).

---

## 6. Do’s and Don’ts

### Do
- **Do** use `spacing-12` and `spacing-16` for hero sections to create an "Editorial" feel.
- **Do** use `inverse_surface` for "Dark Mode" emergency overlays to maximize contrast.
- **Do** ensure all interactive elements have a minimum touch target of 44x44px, even if the visual asset is smaller.

### Don’t
- **Don’t** use pure black (#000000). Use `on_background` (#191b22) to keep the look premium and avoid "ink bleed" on OLED screens.
- **Don’t** use traditional "Drop Shadows" with high opacity. They muddy the interface.
- **Don’t** use more than two levels of nesting. If a third level is needed, use a `surface_tint` (#005db6) at 5% opacity to differentiate.

---

## 7. Accessibility Note
This system is designed for WCAG AAA compliance in critical paths. The contrast ratio between `on_primary` and `primary` exceeds 7:1. When using Glassmorphism, ensure the `backdrop-filter: blur` is high enough to maintain text legibility regardless of the map content beneath.