# generate-screenshot

A [Claude Code](https://claude.ai/claude-code) skill that captures web app screenshots across desktop, tablet, and mobile viewports in both light and dark mode using [Playwright](https://playwright.dev).

## Installation

Requires **Node.js >= 18** and **Claude Code CLI**.

```bash
# Clone into your Claude skills directory
git clone https://github.com/AkaalCreatives/generate-screenshot ~/.claude/skills/generate-screenshot

# Install dependencies
cd ~/.claude/skills/generate-screenshot && npm run setup
```

For project-level use, clone into `.claude/skills/generate-screenshot` instead.

## Usage

```
/generate-screenshot                                          # Auto-detect server & routes
/generate-screenshot /login /dashboard /settings              # Specific routes
/generate-screenshot / --viewports desktop --modes dark       # Desktop dark mode only
/generate-screenshot / --url http://localhost:4000             # Explicit URL
/generate-screenshot / --output ./my-screenshots              # Custom output directory
```

If no dev server or routes are found, you'll be prompted.

## Defaults

| Setting | Default |
|---------|---------|
| Viewports | Desktop (1920x1080), Tablet (768x1024), Mobile (375x812) |
| Colour modes | Light, Dark |
| Output | `screenshots/` |
| Naming | `{route}--{viewport}--{mode}.png` |

Route scanning supports Next.js, Nuxt, SvelteKit, Remix, React Router, Vue Router, and Angular.

## Licence

MIT

---

Developed by [Akaal Creatives](https://www.akaalcreatives.com)
