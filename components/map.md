# Map with Overlays and Drill-downs

## Overview
A versatile mapping component pattern that combines a base map container with support for overlays (polygons, markers, zones) and drill-down navigation. It allows users to start from a broad geographic overview and progressively reveal more detailed layers, enabling interactive exploration of spatial data.

## Key Features
- **Base map layer:** standardized React-Leaflet wrapper with tile style switching, resize handling, and smooth viewport transitions.  
- **Custom overlays:** support for polygons, clustered cells, pivot graphics, and markers with configurable styling.  
- **Drill-down navigation:** zooms and centers on the selected geometry, enabling a shift from overview to detail.  
- **Layer ordering:** named panes with z-index for predictable stacking of shapes, icons, and labels.  
- **User interactions:** hover to highlight, click to select or drill into deeper levels.  
- **Dynamic modes:** switch between visualization strategies (e.g., clusters vs. pivots, aggregated vs. detailed).  

## Usage Scenarios
- Interactive dashboards where users move from a high-level map of regions into detailed entity overlays.  
- Monitoring tools where zones or cells need to be visualized differently based on the selected mode.  
- QA or analytics flows where list/table selections sync with highlighted map areas.  
- Multi-layer decision support systems with contextual overlays (boundaries, markers, heatmaps).  

## Props Explanation
- **centerCoords / mapZoom** — Control the viewport; auto-update on drill-down to focus on selected entities.  
- **tileLayerType** — Switch between predefined base tiles (e.g., light or default OSM).  
- **selectedMode** — Chooses which overlay strategy to render (e.g., “clusters”, “pivot”, “zones”).  
- **onHover(id)** — Fired when the user hovers an overlay element, useful for syncing external UI highlights.  
- **onClick(id)** — Invoked on overlay click to enable drill-down or selection.  
- **hoveredId / selectedId** — Identifiers used to visually distinguish active elements.  
- **children** — Any React-Leaflet layers; allows composition beyond predefined overlays.  

## Accessibility
- Use contrasting colors and opacity rules for hover/selection states.  
- Provide keyboard-accessible controls (lists, filters) to replicate map interactions.  
- Ensure tile attributions and legends are present for compliance and context.  

## Theming & Styling
- Overlays inherit brand colors and tokens for consistency across dashboards.  
- Layer styles (stroke width, opacity, fill) adapt to emphasize selection.  
- Panes manage z-index so shapes and markers never visually conflict.  
- Base tiles can be chosen to align with dark/light themes.  

## Performance Considerations
- Memoize geometry transformations to prevent recalculation on every render.  
- Throttle hover and resize events for smoother interactivity.  
- For large datasets, simplify polygons and cluster markers to reduce DOM complexity.  
- Keep IDs and props stable to avoid unnecessary viewport resets.  
