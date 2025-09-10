# LineChart

## Overview

A responsive line chart component powered by Nivo’s `ResponsiveLine`. It renders one or more series with optional date-based X‑axis, custom tick rendering, background zones, dynamic dashed/solid segments, and visual markers for prediction start and planned target values. The component emphasizes visual clarity and design‑system consistency while remaining configurable for a variety of analytics dashboards.

## Key Features

- **Dual X‑axis modes:** point or time (date) scale with locale‑aware labels.
- **Smart ticks:** builds internal X ticks when explicit values are not provided and a desired tick count is set.
- **Custom layers:** background, zones, bottom domain line, dynamic line styling, prediction start markers, and planned value guides.
- **Per‑series curves:** curve selection per series (e.g., natural) mapped to the underlying Nivo curve types.
- **Precise axis rendering:** bespoke tick renderers for left and bottom axes (anchors, paddings, small guides).
- **Configurable visuals:** grid, axis, and label colors; dashed patterns; margins; stroke widths.
- **Interactive by default:** hover interaction enabled (points hidden to reduce noise).

## Usage Scenarios

- Time‑series performance charts with a clear separation between historical and predicted values.
- KPI dashboards that require a visual target (planned value) and contextual bands (zones).
- Multi‑series comparisons where each series may use a different curve style.
- Compact widgets where a clean, minimal axis presentation is preferred.

## Props Explanation

- **series** — Input data for one or more series. Each item may include id, color, data points, curve type, and (optionally) prediction metadata used by dynamic layers.
- **height** — Chart container height in pixels (defaults to 216).
- **className** — Extra CSS class for the outer wrapper.
- **yMin / yMax** — Y scale bounds (`number` or `"auto"`).
- **yTickValues** — Tick values/count for the Y axis. A `number` value enables “nice” rounding at that granularity.
- **xTickValues** — Explicit tick values for the X axis. If omitted/empty and a desired tick count is provided, the chart will build ticks internally.
- **xTickParams** — Config for X ticks: `{ type?: "date" | string; ticksCount?: number; withTime?: boolean; locale?: string }`. When `type: "date"`, X scale switches to a time scale.
- **axisLeftFormat(value, index)** — Formatter for Y tick labels.
- **axisBottomFormat(value, index)** — Formatter for X tick labels.
- **gridColor / axisColor** — Colors for grid and axis decorations (used by the theme and custom renderers).
- **bottomDomainColor** — Color of the bottom domain baseline.
- **dashedPattern** — SVG dash array pattern applied by the dynamic line layer (e.g., `"4 4"`).
- **zones** — Array of background zones to visually segment the plotting area.
- **margin** — Partial margin override: `{ top, right, bottom, left }`.
- **color** — Label/text color for custom tick renderers.
- **plannedValue** — Target value shown by the planned value layer (e.g., KPI goal).

## Accessibility

- Uses clear, high‑contrast tick labels and optional grid lines for readability.
- Interaction is hover‑based; pair with external controls (legend, toggles) to provide keyboard‑accessible alternatives.
- Ensure sufficient color contrast for series lines and backgrounds; reserve dashed patterns to distinguish predicted segments for color‑blind accessibility.

## Theming & Styling

- Visuals derive from a theme produced by `makeTheme({ gridColor, axisColor })` plus per‑prop colors (`color`, `bottomDomainColor`).
- Background and zone layers accept solid fills and can align with dark or light surfaces.
- Margins are configurable to fit dense layouts; labels use a consistent typography scale (12px) for harmony across widgets.

## Performance Considerations

- Rendering is **non‑animated** by default to avoid costly transitions in dashboards.
- Points are disabled to reduce DOM/SVG complexity; hover remains active over the line paths.
- Provide stable references for `series`, formatters, and props to minimize re‑renders; pre‑normalize data if possible.
- Prefer bounded tick counts and explicit `yMin/yMax` in highly dynamic views to prevent layout thrashing.
