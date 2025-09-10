# Geo-data Timelapse

## Overview
The **Geo-data Timelapse** component provides an interactive control panel for exploring geospatial data over time. It combines a date range selector, timeline navigation, and playback controls to let users step through or animate historical and forecast data points.

## Key Features
- **Date range picker:** choose the period of interest using a calendar interface.  
- **Timeline navigation:** scrollable horizontal list of available dates with quick jump arrows.  
- **Playback controls:** play/pause toggle to animate through the timeline automatically.  
- **Manual stepping:** navigate to the previous/next date with arrows.  
- **Highlighting:** currently selected date is visually emphasized for clarity.  
- **Export option:** download timelapse data in XLS format.  
- **Smooth transitions:** animated presence and fade-in/out for controls.  

## Usage Scenarios
- Visualizing satellite or sensor data over a time period (e.g., vegetation, soil moisture, temperature).  
- Reviewing infrastructure changes or environmental events across selected dates.  
- Running animated playback for presentations or monitoring dashboards.  
- Exporting the selected timeline data for offline analysis.  

## Props Explanation
This component does not accept external props directly; it manages its own internal state. Key internal states include:  
- **selectedTimelapse** — currently selected date in the timeline.  
- **selected** — the active date range.  
- **playing** — boolean flag indicating if playback mode is active.  

## Accessibility
- All interactive elements (play/pause, arrows, date buttons, export) are accessible via keyboard.  
- Labels such as “XLS” and clear date formats ensure understandable context for screen readers.  
- High-contrast highlighting (active date chips) makes selection states visually distinct.  

## Theming & Styling
- Minimalist white container with rounded corners and subtle shadow for elevation.  
- Selected date styled with strong accent background (`#92986C`) and white text.  
- Icons adapt based on state (play/pause, enabled/disabled arrows).  
- Scrollbar hidden for timeline chips to maintain clean design.  

## Performance Considerations
- Dates array is memoized to avoid recalculation on each render.  
- Scroll operations are smooth and targeted to the active element.  
- Animations use Framer Motion (`AnimatePresence`) for optimized rendering.  
- Keep large timelapse ranges manageable; long datasets may require virtualized rendering.  
