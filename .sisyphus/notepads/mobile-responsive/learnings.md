# Mobile Responsive - Learnings

## [2026-02-28] Task F1: Full Mobile QA

### Verified Behaviors
- Hamburger menu: opens/closes via click, Escape key, and tap outside overlay
- Swipe gestures: left=next, right=prev, 100px delta triggers navigation
- All 11 slides: no horizontal scroll at 390px, 480px, 768px
- Touch targets: all ≥44px after fixing nav-btn from 40px→44px

### Bug Found & Fixed
- `nav-btn` at `@media (max-width: 768px)` was 40x40px (below 44px minimum)
- `nav-btn` at `@media (max-width: 480px)` was 36x36px (below 44px minimum)
- Fixed both to 44x44px in Navigation.svelte
- CSS edit accidentally removed closing `}` for `.nav-btn` block — required second fix

### CSS Brace Counting Technique
When Svelte reports "Unexpected end of input" at `</style>`:
```bash
node -e "
const fs = require('fs');
const content = fs.readFileSync('src/components/Navigation.svelte', 'utf8');
const styleStart = content.indexOf('<style>');
const styleEnd = content.indexOf('</style>');
const styleContent = content.slice(styleStart + 7, styleEnd);
let open = 0, close = 0;
for (const ch of styleContent) { if (ch === '{') open++; if (ch === '}') close++; }
console.log('Open:', open, 'Close:', close, 'Diff:', open - close);
"
```

### Dev Server URL
- Base path: `/coding-agents-presentation` (configured in astro.config.mjs)
- Correct URL: `http://localhost:4323/coding-agents-presentation/`
- NOT: `http://localhost:4323/` (returns 404)

### Swipe Gesture Testing
Can simulate with TouchEvent API in browser console:
```js
const container = document.querySelector('.presentation-container');
const touchStart = new TouchEvent('touchstart', { bubbles: true, touches: [new Touch({ identifier: 1, target: container, clientX: 300, clientY: 400 })] });
// ... dispatch touchmove and touchend
```

### 1Password SSH Agent Issue
- Git commits fail with "1Password: failed to fill whole buffer"
- Requires 1Password to be unlocked and SSH agent active
- Cannot be bypassed programmatically

### Evidence Screenshots
- `.sisyphus/evidence/mobile-390px-hero.png`
- `.sisyphus/evidence/mobile-390px-slide5.png`
- `.sisyphus/evidence/mobile-480px-slide5.png`
- `.sisyphus/evidence/768px-slide5-agents.png`
- `.sisyphus/evidence/768px-slide6-hallucinations.png`
