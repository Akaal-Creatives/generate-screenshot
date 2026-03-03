# generate-screenshot

A [Claude Code](https://claude.ai/claude-code) skill that generates screenshots of your web app across multiple viewports and colour modes using [Playwright](https://playwright.dev).

## Features

- **Auto-detects** running dev servers on common ports (3000, 5173, 8080, etc.)
- **Multi-viewport** — Desktop (1920×1080), Tablet (768×1024), Mobile (375×812)
- **Dark & Light mode** — Captures both `prefers-color-scheme` variants
- **Route scanning** — Auto-discovers routes from Next.js, Nuxt, SvelteKit, React Router, Vue Router, Angular, and Remix
- **Multiple routes** — Capture as many pages as you need in one command
- **Configurable** — Override viewports, colour modes, output directory, and base URL
- **Cookie banner dismissal** — Attempts to close common consent banners before capture

## Installation

### As a personal skill (recommended)

```bash
# Clone into your Claude skills directory
git clone https://github.com/Akaal-Creatives/generate-screenshot ~/.claude/skills/generate-screenshot

# Install dependencies
cd ~/.claude/skills/generate-screenshot && npm run setup
```

### As a project skill

```bash
# Clone into your project's .claude/skills directory
git clone https://github.com/Akaal-Creatives/generate-screenshot .claude/skills/generate-screenshot

# Install dependencies
cd .claude/skills/generate-screenshot && npm run setup
```

## Usage

### Basic — capture all routes

```
/generate-screenshot
```

Claude will auto-detect your dev server, scan your project for routes, and capture screenshots in all viewports and colour modes.

### Specific routes

```
/generate-screenshot /login /dashboard /settings
```

### Custom options

```
/generate-screenshot /home /about --viewports desktop,mobile --modes light --output ./my-screenshots
```

### With explicit URL

```
/generate-screenshot /home --url http://localhost:4000
```

## Output

Screenshots are saved to `screenshots/` by default with the naming convention:

```
{route}--{viewport}--{mode}.png
```

Examples:

```
screenshots/
├── home--desktop--light.png
├── home--desktop--dark.png
├── home--tablet--light.png
├── home--tablet--dark.png
├── home--mobile--light.png
├── home--mobile--dark.png
├── login--desktop--light.png
├── login--desktop--dark.png
└── ...
```

## Options

| Option | Default | Description |
|--------|---------|-------------|
| `--url` | Auto-detected | Base URL of the web app |
| `--viewports` | `desktop,tablet,mobile` | Comma-separated list of viewports |
| `--modes` | `light,dark` | Comma-separated list of colour modes |
| `--output` | `screenshots/` | Output directory for screenshots |

## Viewport Sizes

| Viewport | Width | Height |
|----------|-------|--------|
| Desktop | 1920 | 1080 |
| Tablet | 768 | 1024 |
| Mobile | 375 | 812 |

## Supported Frameworks (Route Scanning)

| Framework | Pattern |
|-----------|---------|
| Next.js (App Router) | `app/**/page.{tsx,jsx,ts,js}` |
| Next.js (Pages Router) | `pages/**/*.{tsx,jsx,ts,js}` |
| Nuxt | `pages/**/*.vue` |
| SvelteKit | `src/routes/**/+page.svelte` |
| Remix | `app/routes/**/*.{tsx,jsx,ts,js}` |
| React Router | `<Route path=...>` patterns |
| Vue Router | `path:` in router files |
| Angular | `path:` in routing modules |

## Requirements

- Node.js >= 18
- Claude Code CLI

## Licence

MIT

---

Developed by [Akaal Creatives](https://www.akaalcreatives.com)
