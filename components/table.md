# Table (filtering, color-coding, smart grouping)

## Overview

A flexible, data-driven table component built on top of TanStack React Table. It supports selectable rows, sortable columns, custom header/body/footer rendering, column resizing, and row hover reporting. The component is fully controlled via props and exposes fine-grained styling and behavior hooks through column metadata.

## Key Features

- Optional checkbox column for row selection (with “select all” and indeterminate states).
- Client-side sorting with visual sort indicators and single-direction toggling (no sort removal).
- Column resizing with live (“onChange”) feedback and per-column size constraints.
- Customizable header, cell, footer, and row attributes via `meta` callbacks.
- Row hover callback for external highlighting/preview logic.
- Works with any row shape (`<T>`), preserving strong typing.
- Sticky, accessible header section and structured footer groups.

## Usage Scenarios

- Data grids where users need to select multiple rows for bulk actions.
- Lists with sortable columns and custom cell rendering (badges, chips, status blocks).
- Dashboards where hovering a row should highlight related content on a map, chart, or side panel.
- Reporting tables with grouped footers and precise column widths.

## Props Explanation (conceptual)

- **data**: The array of row objects.
- **columns**: Column definitions enhanced with optional `meta` for header/cell/footer/row customization.
- **withCheckbox**: Enables a leading selection column with header “select all.”
- **onRowHover**: Reports hovered row (or `undefined` on leave) for external UI reactions.
- **hoveredRowIndex**: Allows externally controlling which row is visually treated as hovered.
- **columSizes**: Default size constraints for all columns (size, min, max) applied as the table’s default column config.
- **onSelectionChange**: Receives the array of currently selected row originals whenever selection changes.
- **allRowsSelected**: Initializes selection state with all rows marked selected.
- **className**: Extends the table root with additional styles.
- **isSortable**: Enables column sorting behavior and interactive header controls.
- **onSortingChange**: Notifies consumer about sorting state changes.

## Accessibility

- Checkbox controls provide clear labels for screen readers (“Select all rows”, “Select row”).
- Sticky header improves navigation in long tables.
- Hover interactions are side-effects only; selection and sorting remain accessible via focusable header and checkbox controls.
- Ensure sufficient color contrast and visible focus indicators in the consuming theme.

## Theming & Styling

- The root table accepts custom classes; internal elements use utility classes designed to be theme-friendly.
- Apply brand tokens (colors, spacing, borders) through your utility framework or CSS variables.
- `meta` prop callbacks are the primary extension point to inject per-cell/per-header styles without modifying core logic.

## Performance Considerations

- Leverages TanStack’s core row model for efficient rendering.
- Delegates complex logic (sorting, selection) to TanStack to minimize re-renders.
- Prefer memoized column definitions and stable callbacks in consumers for large datasets.
