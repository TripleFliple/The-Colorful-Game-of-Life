# The Game of Life Pro

A highly advanced implementation of Conway's Game of Life with color evolution, moving cells, territorial battles, and intelligent pattern management organized by rule sets.

## Overview

The Game of Life Pro is an enhanced cellular automaton simulation that extends the classic Game of Life with multiple colors, evolution mechanics, moving cell spores, and territorial competition. Each color can spawn, survive, evolve, and compete for space on the canvas. Patterns are automatically organized by rule configurations for easy experimentation and discovery.

## Quick Start

1. Open `index.html` in any modern web browser
2. Click **▶ Play** to start the simulation
3. Click on the canvas to draw cells
4. Experiment with the color palette, drawing tools, and rule sliders
5. Use pattern management features to save and organize your discoveries

## Game Rules

### Core Mechanics

- **Birth**: Empty cells with exactly 3 neighbors of the same color are born as that color
  - Default range: 3-3 neighbors (adjustable from 0-8)
  - Example: An empty cell surrounded by 3 red cells becomes red

- **Evolution**: Cells with exactly 4 neighbors evolve to the next color in the hierarchy
  - Default range: 4-4 neighbors (adjustable from 0-8)
  - **IMPORTANT**: Evolution is checked BEFORE survival, meaning cells will evolve even if they would normally survive
  - This allows overlapping evolution and survival ranges for dynamic gameplay
  - Example: With Survival 2-6 and Evolution 4-5, cells with 4-5 neighbors evolve while 2-3 neighbors just survive

- **Survival**: Living cells survive if they have 2-3 neighbors
  - Default range: 2-3 neighbors (adjustable from 0-8)
  - Only applies if evolution doesn't trigger first
  - Cells with too few or too many neighbors will die

- **Death**: Cells die from isolation (<2 neighbors) or overpopulation (5+ neighbors)
  - Default: 5+ neighbors causes death (adjustable from 0-8)
  - Dead cells become empty (black) cells

### Color Hierarchy

```
White → Red → Orange → Yellow → Green → Cyan → Blue → Purple → Magenta → White (cycles)
```

### Special Mechanics

#### Magenta Special
Magenta is the final color in the evolution chain and has special behavior:
- With **Moving Cells ON**: Magenta cells in evolution range spawn a moving white spore and die
- With **Moving Cells OFF**: Magenta cells evolve back to white

#### Moving Cells (Toggleable)
When enabled, stagnant cells spawn moving cell spores:
- **Stagnation**: Cells with 3+ same-color neighbors that haven't changed for the Color Expansion Rate
- **Movement**: Moving cells travel outward (70% straight, 30% turn chance)
- **Passing**: Moving cells pass through other movers
- **Conversion**: After 4+ frames, movers stop on same color or convert entire groups of different colors
- Creates organic spreading and colonization patterns

#### Neighbors Fight (Toggleable)
When enabled, higher-tier colors can convert adjacent lower-tier neighbors:
- Stagnant cells of a higher color convert adjacent lower-colored neighbors
- Conversion occurs based on the Color Expansion Rate timing
- Creates territorial battles and color wars
- Example: Red cells can convert adjacent white cells to red

#### Color Expansion Rate
Controls the speed of advanced mechanics:
- Range: 1-300 generations
- Default: 100 generations
- Lower values = faster Moving Cells spawning and Neighbors Fight conversions
- Higher values = more stability before stagnation kicks in
- Affects both Moving Cells timing and Neighbors Fight timing

## Drawing Tools

### Color Selection
- Click any of the 9 color swatches to select a drawing color
- White, Red, Orange, Yellow, Green, Cyan, Blue, Purple, Magenta
- Selected color is highlighted with a white border
- Click or drag on canvas to draw cells in the selected color

### Tool Buttons

#### Eraser (🗑)
- Click to activate/deactivate: 25×25 → OFF
- Red circle cursor shows eraser size
- Circle fills in when actively erasing
- Click or drag to erase cells

#### Line Tool (╱)
1. Click to activate (button highlights)
2. Click canvas for start point
3. Move mouse to see red preview line
4. Click again for end point to draw straight line

#### Rectangle Tool (▢)
1. Click to activate (button highlights)
2. Click canvas for first corner
3. Move mouse to see red preview rectangle
4. Click again for opposite corner to draw rectangle outline

#### Oval Tool (⬭)
1. Click to activate (button highlights)
2. Click canvas for first corner
3. Move mouse to see red preview ellipse
4. Click again for opposite corner to draw oval outline

#### Random (🎲)
- Fills entire canvas with random cells in the currently selected color
- Great for creating chaotic starting conditions with specific colors

#### Select Tool (⬚)
1. Click to activate (button highlights)
2. Click two points on canvas to select a rectangular area
3. Selection is automatically copied
4. Click and drag anywhere within the selection box to move cells to a new position
5. Green save button (💾) appears in bottom-right corner (desktop only)
6. Click outside selection or deactivate tool to finalize placement

#### Paste Tool (📋)
1. First select and copy cells OR load a saved pattern
2. Click Paste button to activate paste mode
3. Click anywhere on canvas to place the pattern
4. Pattern centers on your click position
5. Click Paste again to deactivate

#### Load Pattern (📂) - Desktop Only
- Opens the saved patterns library organized by rule sets
- Displays all rule sets with their configurations
- Click rule set headers to expand/collapse pattern lists
- Click any pattern to load it for pasting
- Each rule set shows its complete configuration (including Neighbors Fight and Moving Cells)
- Patterns are stored in browser's local storage

## Pattern Management (Desktop Only)

### Rule Set Organization

Patterns are automatically organized into "rule sets" based on your current game configuration:
- Birth range (min-max)
- Survival range (min-max)
- Evolution range (min-max)
- Death threshold
- Color Expansion Rate
- **Neighbors Fight** (ON/OFF)
- **Moving Cells** (ON/OFF)

When you change ANY of these settings, saving a pattern will create a new rule set!

### Saving Patterns

**First Pattern with New Rules:**
1. Activate the Select Tool (⬚)
2. Click two points to select an area containing cells
3. Click the green save button (💾) in the bottom-right corner of the selection box
4. Prompted: "New Rule Set Detected" with current rules displayed
5. Enter a name for the rule set (e.g., "Rapid Evolution" or "Territory Wars")
6. Prompted: "Saving Pattern"
7. Enter a name for the pattern
8. Pattern saved to new rule set!

**Subsequent Patterns with Same Rules:**
1. Select cells with Select tool
2. Click Save button (💾)
3. Only prompted for pattern name
4. Automatically saved to matching rule set!

**Example Organization:**
```
📁 Classic Game of Life
   Birth: 3-3, Survival: 2-3, Evolution: 4-4, Death: 5+
   Neighbors Fight: ON, Moving Cells: ON
   [12 patterns]
   
📁 Rapid Color Change
   Birth: 2-4, Survival: 2-6, Evolution: 4-5, Death: 7+
   Neighbors Fight: ON, Moving Cells: ON
   [8 patterns]
   
📁 Stable Growth (No Fight)
   Birth: 3-3, Survival: 2-4, Evolution: 5-5, Death: 6+
   Neighbors Fight: OFF, Moving Cells: OFF
   [5 patterns]
```

### Loading Patterns

1. Click the Load Pattern button (📂) in the toolbar
2. Rule sets appear as collapsible sections
3. Click rule set header to expand/collapse
4. See full rule configuration for each set
5. Click any pattern to load it into paste mode
6. Click on canvas to place it wherever you want
7. Pattern automatically centers on your click position

### Export & Import

**Export Single Rule Set:**
- Click "Export" button next to any rule set
- Downloads as JSON file named after the rule set
- Share with others or backup individually

**Export All Rule Sets:**
- Click "Export All" button at bottom of Load Pattern dialog
- Downloads complete library as single JSON file
- Perfect for backing up your entire collection

**Import Rule Sets:**
- Click "Import" button at bottom of Load Pattern dialog
- Select a previously exported JSON file
- Automatically handles name collisions (adds numbers if needed)
- Success message appears, click Load Pattern to view imported data
- Works with both single rule set and "all rule sets" exports

### Managing Rule Sets

**Delete Individual Pattern:**
- Expand a rule set
- Click "Delete" button next to any pattern
- Confirm deletion
- If it's the last pattern, entire rule set is removed

**Delete Entire Rule Set:**
- Click "Delete" button next to rule set name
- Confirm deletion of rule set and ALL its patterns
- Permanently removes from storage

**View Pattern Details:**
- Each pattern shows: name, dimensions (width×height), cell count
- Rule sets show: complete configuration, pattern count

Note: Pattern save/load features are automatically hidden on mobile devices.

## Game Controls

### Main Controls

- **▶ Play/Pause**: Start or stop the simulation
- **Step**: Advance exactly one generation (great for studying patterns)
- **Clear**: Erase all cells from the canvas
- **Zoom**: Cycles through OFF → IN → OUT → OFF
  - IN mode: Click canvas to zoom in (up to 4x)
  - OUT mode: Click canvas to zoom out (down to 0.25x)
  - Automatically limited to prevent showing empty black space
  - Drag canvas while zoomed to pan the view

### Speed Control

- Slider adjusts simulation speed from 1 to 30 generations per second
- Lower values: Slower, easier to observe patterns
- Higher values: Faster, for long-term evolution observation

### Canvas Size

- Width dropdown: 50 to 500 cells
- Height dropdown: 50 to 500 cells
- Click "Apply Size" to rebuild the grid with new dimensions
- Warning: Changing size clears the current canvas
- Mobile devices automatically use 100×150 for performance

## Rule Customization

All rules are adjustable via slider controls below the canvas:

### Birth Range (Min-Max)
- Default: 3-3 neighbors
- Controls when empty cells become alive
- Lower minimum: More aggressive spawning
- Higher maximum: Allows births with more neighbors

### Evolution Range (Min-Max) ⭐ NEW BEHAVIOR
- Default: 4-4 neighbors
- **Evolution is checked FIRST** (before survival)
- Can now overlap with survival range!
- Example: Survival 2-6, Evolution 4-5 → Cells with 4-5 neighbors evolve, 2-3 just survive
- Wider range: More color changes and visual variety
- Narrow range: More stable color regions

### Survival Range (Min-Max)
- Default: 2-3 neighbors
- Controls which cells stay alive
- Only applies if evolution doesn't trigger
- Can now be wider without blocking evolution!
- Range 0-0: Almost everything dies (crystal growth patterns)
- Range 0-8: Almost nothing dies (very stable)

### Death Threshold (Minimum)
- Default: 5+ neighbors
- Cells with this many or more neighbors die from overpopulation
- Lower values: More aggressive culling
- Higher values: Denser populations survive

### Reset Rules to Default
- Click "Reset Rules to Default" button to restore:
  - Birth: 3-3
  - Survival: 2-3
  - Evolution: 4-4
  - Death: 5+
  - Color Expansion Rate: 100

## Advanced Features

### Moving Cells Toggle
- **ON** (default): Enables moving cell spores
  - Stagnant cells spawn mobile spores that colonize new areas
  - Creates organic, spreading patterns
  - Magenta cells spawn white spores instead of evolving
  - Included in rule set signature

- **OFF**: Disables moving cells
  - Pure cellular automaton behavior
  - Magenta evolves to white instead of spawning spores
  - More predictable, classic Game of Life behavior

### Neighbors Fight Toggle
- **ON** (default): Enables territorial color battles
  - Higher-tier colors convert adjacent lower-tier colors
  - Creates expanding territories and color wars
  - Based on Color Expansion Rate timing
  - Included in rule set signature

- **OFF**: Disables color conversion
  - Colors only change through evolution rules
  - More stable, less aggressive dynamics

### Save/Load Game State
- **Save Game**: Downloads complete game state as JSON file
  - Includes: grid, moving cells, rules, settings, generation count
  - Can be loaded later to resume exactly where you left off

- **Load Game**: Upload a previously saved JSON file
  - Restores everything: pattern, rules, zoom level, generation count
  - Great for sharing interesting configurations

## Tips & Tricks

### Creating Interesting Patterns

1. **Birth Minimum = 0 Warning**: Avoid setting birth minimum to 0 as it causes rapid, unpleasant blinking

2. **Wide Birth Range**: Open the birth range (e.g., 2-5) to create explosive, chaotic reactions

3. **Overlapping Evolution & Survival**: ⭐ NEW! Try Survival 2-6 with Evolution 4-5 for dynamic color shifting while maintaining stable regions

4. **Low Survival Minimum**: Set survival minimum to 0 or 1 to create beautiful crystal-like growth patterns

5. **Pattern Library Organization**: Save patterns with different rule combinations. Try:
   - High Chaos: Wide ranges with both toggles ON
   - Stable Growth: Narrow ranges with both toggles OFF
   - Territory Wars: Neighbors Fight ON, Moving Cells OFF
   - Spreading Colonies: Moving Cells ON, Neighbors Fight OFF

### Performance Tips

- Smaller canvas sizes (100×150 or less) run faster on mobile devices
- Lower simulation speed (1-10) for detailed observation
- Use Step button to advance frame-by-frame when studying complex interactions

### Experiment Ideas

- **Evolution Priority Testing**: Survival 1-7, Evolution 3-5 → Watch evolution dominate
- **Stable Patterns**: Find oscillators and still lifes by adjusting survival range
- **Color Wars**: Enable Neighbors Fight with high Color Expansion Rate for epic battles
- **Spreading Colonies**: Enable Moving Cells with low Color Expansion Rate for aggressive expansion
- **Custom Rules**: Try survival 1-1 with death 3+ for completely different dynamics
- **Pattern Combinations**: Save small patterns and combine them by pasting multiple times
- **Rule Set Comparison**: Create identical patterns in different rule sets to see how rules affect evolution

## Technical Details

### Browser Compatibility
- Works in all modern browsers (Chrome, Firefox, Safari, Edge)
- Requires JavaScript enabled
- Local storage required for pattern save/load features

### Mobile Support
- Touch controls supported for drawing and tool use
- Automatic canvas size adjustment (100×150)
- Pattern save/load features hidden on mobile
- Select and paste tools fully functional on mobile

### Storage
- Patterns organized by rule sets in browser's localStorage
- No server required, all data stored locally
- Patterns persist between sessions
- Clear browser data will remove saved patterns
- Rule sets include all configuration details

### Rule Set Signatures
Each rule set has a unique signature based on:
- Birth range (min-max)
- Survival range (min-max)  
- Evolution range (min-max)
- Death threshold
- Color Expansion Rate
- Neighbors Fight (ON/OFF)
- Moving Cells (ON/OFF)

Changing ANY of these creates a new rule set!

## Keyboard Shortcuts

Currently no keyboard shortcuts are implemented. All controls are accessible via mouse/touch interface.

## What's New

### Recent Updates

**Evolution Priority System:**
- Evolution now checked BEFORE survival
- Allows overlapping evolution and survival ranges
- Creates more dynamic color-shifting gameplay
- Opens up new strategic possibilities with wide survival ranges

**Enhanced Rule Set Organization:**
- Patterns automatically organized by complete rule configuration
- Includes Neighbors Fight and Moving Cells in signatures
- Collapsible rule set sections in Load Pattern dialog
- Full rule descriptions displayed for each set

**Import/Export Improvements:**
- Export individual rule sets or entire library
- Import handles name collisions automatically
- Success messages guide user to view imported data
- No page refresh needed after import

**Bug Fixes:**
- Load Pattern button now works immediately after saving
- Import no longer causes modal errors
- All dialogs properly restore modal structure

## Credits

An enhanced implementation of Conway's Game of Life featuring:
- Multi-color evolution system with priority mechanics
- Moving cell spores
- Territorial color battles
- Intelligent pattern organization by rule sets
- Comprehensive drawing tools
- Export/Import capabilities

## Version

Current Version: 1.1 (Evolution Priority + Rule Set Organization)

---

**Enjoy exploring the infinite possibilities of The Game of Life Pro!**

**Pro Tip**: Start with the defaults, then try Survival 2-6 with Evolution 4-4 to see how the new evolution priority system creates beautiful, dynamic color cascades!
