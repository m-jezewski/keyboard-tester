## Keyboard Tester
vibe-coded browser-based keyboard testing tool with double key registration (chattering) detection.

<img width="1324" height="890" alt="image" src="https://github.com/user-attachments/assets/620d765b-fb97-4c02-937f-8958ef4189db" />

### What it does

- Visual keyboard layout
- Typing area
- Key press history — a log of every keypress showing the key name, event code, time since the previous press, and time since the last press *of the same key*.
- Double press detection — if the same key fires again within 150ms (configurable via `DEBOUNCE_THRESHOLD`), the entry is highlighted in red. This catches chattering/ghosting issues where a single physical keypress registers twice.

This tool helps you **identify which keys are affected** and **measure the timing gap** between ghost presses. Unlike simple debounce testers that only catch sub-millisecond doubles, this tool tracks per-key timing independently, so it catches ghost presses even when other keys are typed in between (e.g., typing "git" but getting "giti" because "i" registered twice with a 100ms gap).

### Usage
Open `src/index.html` in any modern browser.

### Configuration

The debounce detection threshold is set at the top of the script:

```js
const DEBOUNCE_THRESHOLD = 150; // ms
```

Adjust this value based on your keyboard's behavior. Lower values catch only very fast ghost presses, higher values may produce false positives during intentional rapid key repeats.
