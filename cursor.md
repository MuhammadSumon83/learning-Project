# Cursor

This folder is a Node.js workspace. Keep examples small, runnable, and easy to change.

## Runtime

- Use the current Node.js LTS.
- Start new apps with `package.json` and `"type": "module"`.
- Put the entry file at `src/index.js` unless the task needs another layout.
- Add `start` and `dev` scripts in `package.json`.

## Modules

- Use ECMAScript modules and `import` / `export`.
- Include the `.js` extension in local import paths.
- Prefer Node.js built-in modules, imported from `node:`, before adding a package.

## Async and errors

- Use `async` / `await`.
- Handle errors where the program can respond, and attach the original error as `cause` when rethrowing.

```js
import { readFile } from 'node:fs/promises';

export async function loadJson(path) {
  try {
    const raw = await readFile(path, 'utf8');
    return JSON.parse(raw);
  } catch (error) {
    throw new Error(`Unable to load JSON at ${path}`, { cause: error });
  }
}
```

## Style

- Prefer `const`. Use `let` only when the binding changes.
- Name functions for what they do.
- Check input at the edge: CLI args, HTTP handlers, and file reads.
- Add a dependency or framework only when the example needs it.
