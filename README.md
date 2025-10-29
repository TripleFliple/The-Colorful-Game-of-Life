# 🌈 The Colorful Game of Life

A mesmerizing cellular automaton based on Conway's Game of Life, enhanced with 9-color evolution, territorial color wars, and moving spore mechanics that create emergent warfare patterns.

## 🎮 What Is This?

This is Conway's Game of Life reimagined with colors and propagation. Cells don't just live and die, they can evolve through a rainbow hierarchy. When they become stagnant they can invade neighboring colors and/or spawn moving cells in an attempt to continue their growth and development.

Watch simple patterns explode into complex, ever-changing color wars. It's hypnotic, chaotic, and endlessly fascinating.

## ✨ Key Features

### Core Mechanics
- **9-Color Evolution System**: White → Red → Orange → Yellow → Green → Cyan → Blue → Purple → Magenta → (back to White spore)
- **Moving Cells**: Stagnant cells spawn mobile "spores" that travel across the grid, convert enemy colors, and create dynamic warfare
- **Neighbors Fight**: Colored cells convert adjacent lower-tier colors, creating territorial expansion and color dominance battles
- **Color Expansion Rate**: Adjustable stagnation threshold (1-300 generations) that controls how quickly moving cells spawn and color conversion happens

### Drawing Tools
- **9 Color Palette**: Click any color swatch to paint cells on the canvas
- **Multi-Size Eraser**: Cycles through 5x5 → 25x25 → 51x51 → OFF with visual red circle indicator (fills when actively erasing)
- **Line Tool**: Draw straight lines between two points
- **Rectangle Tool**: Draw hollow rectangles
- **Oval Tool**: Draw hollow ovals/ellipses
- **Zoom Controls**: Zoom in/out to see intricate details or get a bird's-eye view

### Customization
- **Adjustable Rules**: Modify birth, survival, evolution, and death neighbor counts
- **Canvas Sizing**: Choose from preset sizes or create custom dimensions (50-500 cells)
- **Speed Control**: Adjust simulation speed from 1-30 generations per second
- **Toggle Features**: Turn Moving Cells and Neighbors Fight on/off independently

## 🕹️ How to Use

### Getting Started
1. **Open the HTML file** in any modern web browser (Chrome, Firefox, Safari, Edge)
2. **Click a color swatch** from the palette to select your drawing color
3. **Click or drag on the canvas** to place cells
4. **Press Play (▶)** to watch the simulation run
5. **Experiment!** Try different patterns, colors, and settings

### Controls Overview

#### Playback Controls
- **Play/Pause**: Start or stop the simulation
- **Step**: Advance one generation at a time
- **Clear**: Erase the entire canvas
- **Random**: Fill canvas with random white cells
- **Speed Slider**: Control how fast generations advance (1-30)

#### Drawing Tools
- **Color Swatches**: Select from 9 colors in the palette above the controls
- **Eraser Tool**: Click to cycle through sizes (5x5 → 25x25 → 51x51 → OFF)
  - Red outline shows eraser size
  - Fills red when actively erasing (mouse/touch down)
  - Click through all sizes to turn off
- **Line Tool**: Click start point, then end point
- **Rectangle Tool**: Click one corner, then opposite corner
- **Oval Tool**: Click one corner, then opposite corner
- **Zoom**: Cycle through OFF → Zoom In → Zoom Out modes

#### Advanced Settings
- **Birth Range**: How many neighbors needed for a cell to be born (default: 3-3)
- **Survival Range**: How many neighbors needed for a cell to survive (default: 2-3)
- **Evolution Range**: How many neighbors needed for a cell to evolve colors (default: 4-4)
- **Death Threshold**: How many neighbors cause death by overpopulation (default: 5+)
- **Color Expansion Rate**: Stagnation timer for spawning movers and color fights (default: 100)

## 🎯 Pro Tips

### For Beginners
1. **Start Simple**: Draw a small cluster of one color and press Play
2. **Try Classic Patterns**: Draw a glider, blinker, or block from classic Game of Life
3. **Use the Eraser**: Multi-size eraser with visual feedback makes editing easy
4. **Watch the Generation Counter**: See how fast your patterns evolve

### For Experimentation
1. **Fast Chaos**: Set Color Expansion Rate to 50 for rapid moving cell spawns and quick color wars
2. **Slow Evolution**: Set Color Expansion Rate to 200 for stable, gradual changes
3. **Color Battles**: Turn on BOTH Moving Cells + Neighbors Fight for epic warfare
4. **Pure Life**: Turn OFF both features for classic Conway's Life behavior (with colors)
5. **Mobile Friendly**: Canvas automatically adjusts to 100x150 on mobile devices

### Cool Patterns to Try
- **Rainbow Collision**: Draw lines of different colors pointing at each other
- **Color Flower**: Use the Oval tool to create concentric circles of different colors
- **Spore Storm**: Create a dense cluster of high-tier colors (purple/magenta) and watch them spawn armies
- **Territorial Wars**: Paint large blocks of different colors and turn on Neighbors Fight

## 🧬 Understanding the Rules

### Classic Game of Life Rules
The foundation follows Conway's original rules:
- **Birth**: Dead cells with exactly 3 living neighbors become alive
- **Survival**: Living cells with 2-3 neighbors survive
- **Death**: Living cells with <2 neighbors die (isolation) or 5+ die (overpopulation)

### Color Evolution Rules
When cells have exactly 4 neighbors, they evolve:
- White → Red → Orange → Yellow → Green → Cyan → Blue → Purple → Magenta
- **Magenta Special**: Instead of evolving to the next color, magenta cells spawn a moving white spore (if Moving Cells ON) or become white (if Moving Cells OFF)

### Moving Cells Behavior
When a cell is stagnant (unchanged for Color Expansion Rate generations) with 3+ same-color neighbors:
1. Spawns a moving cell in an empty adjacent space
2. Moving cell travels in a direction (70% straight, 30% random turn)
3. Passes through other moving cells without interaction
4. After aging 4+ generations, can:
   - Stop when encountering same color
   - Convert entire connected groups of different colors to its color

### Neighbors Fight
When enabled, stagnant colored cells (Red through Magenta):
- Convert adjacent lower-tier color neighbors to match their color
- Creates territorial expansion and color dominance
- Only affects stationary cells, not moving cells

## 📱 Mobile Support

The game works great on mobile devices!
- **Touch Controls**: Tap and drag to draw
- **Auto-Detection**: Canvas automatically sizes to 100x150 on mobile
- **Responsive**: All controls work with touch input
- **Eraser Feedback**: Red filled circle appears when actively erasing with touch
- **Zoom**: Use zoom to see details on small screens

## 🐛 Troubleshooting

**Game runs too fast/slow:**
- Adjust the Speed slider (1-30)
- Higher values = faster generations

**Want classic Conway's Life:**
- Turn OFF Moving Cells
- Turn OFF Neighbors Fight
- Reset Rules to Default

**Canvas too small/large:**
- Mobile devices auto-detect and use 100x150
- Desktop: set custom size with Width/Height dropdowns
- Click "Apply Size" after changes

**Eraser not working:**
- Click the Eraser button to activate (it should highlight)
- Look for the red circle that follows your mouse/finger
- Circle fills red when actively erasing
- Click through all sizes (5x5 → 25x25 → 51x51) to turn off

**Moving cells not spawning:**
- Check that "Moving Cells: ON" is active
- Increase stagnant cell clusters (they need 3+ same-color neighbors)
- Lower Color Expansion Rate for faster spawning (try 50)

## 🎨 Technical Details

- **Pure HTML/CSS/JavaScript**: No dependencies, runs entirely in the browser
- **Canvas API**: Used for rendering the grid
- **Cell States**: 10 states (0=empty, 1-9=colors)
- **Moving Cells**: Tracked separately with position, direction, color, and age
- **Stagnation Timer**: Tracks how long each cell has been unchanged
- **Touch Events**: Full mobile support with touch handling
- **Responsive Design**: Color palette adapts for mobile screens

## 📜 Credits

- I designed and organized this program in 3 days using Claude Sonnet 4.5

Inspired by:
- **John Conway's Game of Life** (1970) - The original cellular automaton
- **Rainbow War** - Rainbow War 1986 ‧ Comedy/Fantasy ‧ (20 min film)

## 📄 License

This is a fun educational project. Feel free to:
- Share it with friends
- Modify it for learning
- Use it in educational contexts
- Experiment and create variations

Just keep the spirit of discovery and wonder alive! 🌟

---

## 🚀 Quick Start Guide

1. **Open the HTML file** in your browser
2. **Click a color swatch** from the palette
3. **Draw some cells** on the canvas
4. **Press Play ▶**
5. **Watch the magic happen** ✨

Enjoy exploring the emergent beauty of cellular automata! 🎮🌈
