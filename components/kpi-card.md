# KPI Card

## Overview

The **KPI Card** is a highlight tile designed to surface a key metric with context and actionable follow‑ups. It presents a prominent value (plus optional unit), a short description, and a bold takeaway summary. On hover, the card expands to reveal suggested questions that can trigger deeper exploration or assistant actions.

## Key Features

- **Prominent KPI display:** large numeric value with optional unit for quick scanning.
- **Context & takeaway:** concise description and bold summary to frame the metric.
- **Expandable follow‑ups:** hover‑to‑expand list of suggested questions for next steps.
- **Clickable card action:** the whole card acts as a call‑to‑action (CTA) for drill‑down.
- **Subtle animations:** smooth height/opacity transitions for the expanded section.
- **Color themes:** preset background/text palettes to convey status or category (gray, brown, green).

## Usage Scenarios

- Management dashboards showcasing daily/weekly KPIs with one‑click drill‑down.
- Assistant‑augmented analytics where suggested questions kick off guided analysis.
- Landing blocks for reports where each card links to a detailed view or filter preset.

## Props Explanation

- **tag** — Short uppercase label/category for the metric (e.g., “REVENUE”, “RETENTION”).
- **value** — Primary numeric/text KPI value displayed in large typography.
- **unit** — Optional unit label (e.g., “%”, “K”, “hrs”) shown beside the value.
- **description** — One‑sentence context or explanation of the KPI.
- **summary** — Bold takeaway or insight emphasizing what matters about the KPI.
- **questions** — Array of follow‑up questions shown in the expanded area.
- **color** — Visual theme of the card; one of: `gray`, `brown`, `green`.
- **onClickCard()** — Handler invoked when the card body is clicked (e.g., open detail page).
- **onClickQuestion(question)** — Handler invoked when a suggested question is clicked.

## Accessibility

- The card uses `role="button"`; add keyboard support (Enter/Space) and visible focus styles for full accessibility.
- Ensure color contrast for each theme meets WCAG recommendations, especially for text and icons.
- Provide descriptive labels/aria text for icons where needed; make the question text itself the accessible name.

## Theming & Styling

- Three presets (`gray`, `brown`, `green`) define background, text, and hover shadow glow.
- Typography hierarchy: large KPI value, optional unit, body description, bold summary, and compact questions list.
- Hover state expands the questions area; consider adding focus‑based expansion for keyboard users in app logic.
- Iconography (e.g., ArrowRightTop) appears on hover to signal interactivity in the questions list.

## Performance Considerations

- Expansion uses lightweight height/opacity animations; avoid rendering very long question lists.
- Interaction state is local (hover/expand); prefer stable props to minimize reflows.
- If many cards render simultaneously, consider virtualization in parent layouts to keep scrolling smooth.
