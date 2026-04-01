# Claude Code 2.1.88 Source Restored

Restored source tree for `@anthropic-ai/claude-code@2.1.88`, reconstructed from the published `cli.js.map` `sourcesContent`.

## Copyright And Usage Notice

- Copyright and other applicable rights in Anthropic first-party source code remain with Anthropic, PBC.
- This repository is an unofficial restored reference copy provided only for study, research, and archival learning purposes.
- This repository is not affiliated with, endorsed by, or maintained by Anthropic.
- Do not use this repository or its contents for commercial purposes.
- Third-party code included in the restored output remains subject to the rights and licenses of its respective authors.

## What This Repository Contains

- `raw/package/cli.js`: bundled CLI from the published npm package
- `raw/package/cli.js.map`: source map shipped with the published npm package
- `raw/package/package.json`: package metadata from the published npm package
- `restored/`: files reconstructed from `cli.js.map`
- `restore-manifest.json`: mapping from source-map entries to restored output paths

## Restore Method

Minimal restore flow:

```bash
npm pack @anthropic-ai/claude-code@2.1.88
tar xzf anthropic-ai-claude-code-2.1.88.tgz
node -e "
const fs = require('fs');
const path = require('path');
const map = JSON.parse(fs.readFileSync('package/cli.js.map', 'utf8'));
const outDir = './restored';
for (let i = 0; i < map.sources.length; i++) {
  const content = map.sourcesContent?.[i];
  if (typeof content !== 'string') continue;
  let rel = map.sources[i];
  while (rel.startsWith('../')) rel = rel.slice(3);
  while (rel.startsWith('./')) rel = rel.slice(2);
  const outPath = path.join(outDir, rel);
  fs.mkdirSync(path.dirname(outPath), { recursive: true });
  fs.writeFileSync(outPath, content, 'utf8');
}
"
```

## Verification

- `cli.js` matches the published npm package for `@anthropic-ai/claude-code@2.1.88`
- `cli.js.map` matches the published npm package for `@anthropic-ai/claude-code@2.1.88`
- The source map contains `4756` source entries
- `sourcesContent` is present for all `4756` entries
- The restored output writes `4756` files

## Repository Layout

```text
.
├── raw/
│   └── package/
│       ├── cli.js
│       ├── cli.js.map
│       └── package.json
├── restored/
│   ├── src/
│   ├── vendor/
│   └── node_modules/
└── restore-manifest.json
```

Useful restored entry points:

- `restored/src/entrypoints/cli.tsx`
- `restored/src/main.tsx`
- `restored/src/commands.ts`
- `restored/src/tools.ts`

## Comparison With `Stephaneguisard/claude--`

This repository was compared against:

- [`Stephaneguisard/claude--`](https://github.com/Stephaneguisard/claude--)

Results:

- `claude-code-extracted/package/cli.js` is identical to `raw/package/cli.js`
- `claude-code-extracted/package/cli.js.map` is identical to `raw/package/cli.js.map`
- All `1902` shared files in `restored/src` and `claude-code-source/src` match exactly by hash
- The compared repository contains `28` additional scaffolding or supplemental files not present in this pure source-map reconstruction

In short: the core restored source content matches, but this repository keeps a more direct "published package + restored output" layout.

## Known Limitations

- This repository reflects what was embedded in the published source map
- It may not contain every original build-time file, generated file, or repository-only artifact
- Some files are large, especially `raw/package/cli.js.map`
- The restored tree includes third-party code present in `sourcesContent`, not just first-party source files
