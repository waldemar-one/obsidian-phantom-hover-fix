# Obsidian Phantom Hover Fix

Fix for the phantom hover highlight bug in Obsidian when scrolling with the mouse wheel.

## Problem

After scrolling with the mouse wheel, the hover state gets stuck on navigation elements and does not disappear — a phantom highlight remains. Reproduces on any theme.

The cause is a long-standing Chromium bug (reported in 2014). When scrolling with the mouse wheel, the browser does not fire the `mouseleave` event because the cursor did not physically move, so the hover state just freezes. Since Obsidian is built on Electron (Chromium), the bug is present here as well.

## Solution

`transform: translateZ(0)` forces GPU compositing layer recreation and clears the stuck hover state. Side effect — the keyboard icon in the hotkey search field shifts down due to a transform conflict, fixed with a separate rule.

## Installation

1. Download `fix-hover.css`
2. Place the file in the `.obsidian/snippets` folder inside your vault
3. Open Obsidian, go to `Settings` → `Appearance` → `CSS snippets`
4. Enable `fix-hover`

## Compatibility

Works with any theme. Tested on many themes: Minimal, Primary, Things, and others.

## Feedback

If you notice any broken elements after installing — open an Issue.
