# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static memorial webpage recreating a nostalgic classroom experience at Zhongnan University of Economics and Law (中南财经政法大学). The project commemorates a return visit to classroom Wenbo 208 on May 6, 2023.

**Live URL**: http://zhaoyanyun.com/zuel_classroom/

## Architecture

### Static HTML Website
- No build process, package manager, or build tools
- Pure HTML/CSS/JavaScript deployed as static files
- Based on HTML5 Boilerplate v8.0.0
- Uses Vue.js (v2) for the real-time clock component

### Key Files Structure
- `index.html` - Main page with embedded Vue.js clock and CSS
- `css/main.css` - Styles (includes HTML5 Boilerplate base + custom styles)
- `css/normalize.css` - CSS normalization
- `js/vue.js` - Vue.js library (v2.x)
- `js/plugins.js` - Console error prevention for older browsers
- `js/main.js` - Currently empty (intended for custom JavaScript)
- `font/` - Chinese font files including DinkieBitmap-9px and HanyiSentyMeadow
- `img/` - Classroom background and animated character images
- `audio/` - Autoplaying university song (南山南财大.mp3)

### Font Optimization
- Uses `.font-spider/` cache directory for font subsetting
- Git history shows fonts were optimized using font-spider tool
- Key fonts: DinkieBitmap-9px (clock display), HanyiSentyMeadow (blackboard text)

## Development Notes

### No Build/Deploy Commands
This is a static site with no build process. To test locally:
```bash
# Use any static file server
python -m http.server 8000
# or
npx serve .
# or
open index.html  # directly in browser
```

### Making Changes
- Edit `index.html` directly for structure/content changes
- CSS styles are embedded in `<style>` tags within `index.html`
- Clock functionality is in inline `<script>` at bottom of `index.html`
- Static assets (images, fonts, audio) go in respective directories

### Font Updates
If adding new Chinese text that requires font subsetting:
1. Update text in HTML
2. Run font-spider: `font-spider index.html`
3. This will create optimized font files in `.font-spider/` cache

### Key Interactive Elements
- **Clock** (`#clock`): Shows real-time date/time in Chinese format
- **Blackboard** (`#blackboard`): Displays poetry, hides on hover
- **Walking character** (`#person`): CSS animation across screen, scales on hover
- All UI elements hide when hovered (opacity: 0)

### Browser Considerations
- Audio autoplays on page load (may be blocked by browser policies)
- Uses WebKit-specific CSS animations (`-webkit-animation`)
- Includes console error prevention for older browsers without console object
