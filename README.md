# Flutter App-Level Find-in-Page (`Cmd+F` / `Ctrl+F`) Showcase

- **🌐 Live Public WebAssembly Demo**: **[https://kevmoo.github.io/flutter_find_in_page_demo/](https://kevmoo.github.io/flutter_find_in_page_demo/)**
- **🔧 Prototype Pull Request**: [flutter/flutter#193186](https://github.com/flutter/flutter/pull/193186)
- **📌 Tracking Issue**: [flutter/flutter#65504](https://github.com/flutter/flutter/issues/65504) (*"Support 'find on page' navigation in text elements"*)

This repository hosts the interactive showcase for Flutter's pluggable app-level Find-in-Page (`FindInPageController`, `FindInPageScope`, `SelectableRegion.findOnly`, and `DefaultSelectionStyle` highlight colors).

## Try It Live in Your Browser

Open **[https://kevmoo.github.io/flutter_find_in_page_demo/](https://kevmoo.github.io/flutter_find_in_page_demo/)** (compiled with `flutter build web --wasm` against [flutter/flutter#193186](https://github.com/flutter/flutter/pull/193186)):

1. **Press `Cmd+F` (macOS) or `Ctrl+F` (Windows/Linux)** anywhere on the page.
2. **Toggle between modes** in the header controls:
   - **`Selection + Find`**: Standard `SelectionArea` wrapped in `FindInPageScope` — select single-line text and press `Cmd+F` to seed the Find bar anchored to that exact occurrence, and press `Escape` to hand the active match back to the OS selection.
   - **`Find-Only` (`SelectableRegion.findOnly`)**: Enables `Cmd+F` highlighting and 2D viewport auto-scrolling *without* pointer drag-selection or `SystemMouseCursors.text` overriding button/chip cursors.
   - **Built-in Floating FindBar vs. Custom AppBar Search UI**: Switch between `SelectableRegionFindBar` and a custom Material AppBar search control driven headlessly via `FindInPageController`.
3. **Explore the 4 layout tabs**:
   - **1. Mixed Document**: Headings, `Text.rich`, inline `WidgetSpan` badges, code blocks, and cards.
   - **2. 2D Scrollable DataTable**: Dual-axis (`horizontal` + `vertical`) auto-scrolling via `showRangeOnScreen`.
   - **3. Scrollable Feed (`ListView`)**: Off-screen vertical viewport auto-scrolling and live in-place `setState` text mutation while the Find bar is open.
   - **4. Architecture & Shortcuts**: Live state inspector (`query`, `activeMatchIndex`, `matchCount`, `caseSensitive`).

## Running Locally from Source

Because this showcase uses the new framework APIs in [flutter/flutter#193186](https://github.com/flutter/flutter/pull/193186), building from source requires checking out the `find-in-page` branch of `kevmoo/flutter`:

```bash
# 1. Switch your Flutter SDK checkout to the PR branch:
git -C /path/to/flutter fetch https://github.com/kevmoo/flutter.git find-in-page
git -C /path/to/flutter checkout FETCH_HEAD

# 2. Run the app (WebAssembly or Desktop):
/path/to/flutter/bin/flutter run -d chrome --wasm
```
