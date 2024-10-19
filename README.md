# vite-vanilla-ts

This repo is a minimal reproduction of the malfunctioning `npm create-vite@latest` scaffolding with 
the `vanilla-ts` template. Steps to recreate this repo are the following:

1. Initialize a new project with `npm create-vite@latest`. Choose any name,  `vanilla` template, and `TypeScript` as a language. Follow the instructions of the setup utility.
```
~/Development/Projects via Node v22.10.0
❯ npm create vite@latest
✔ Project name: … vite-vanilla-ts
✔ Select a framework: › Vanilla
✔ Select a variant: › TypeScript

Scaffolding project in /Users/anton/Development/Projects/vite-vanilla-ts...

Done. Now run:

  cd vite-vanilla-ts
  npm install
  npm run dev

~/Development/Projects via Node v22.10.0 took 8s
❯ cd vite-vanilla-ts

Development/Projects/vite-vanilla-ts via Node v22.10.0
❯ npm install

added 12 packages, and audited 13 packages in 2s

3 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

2. Run `npm run dev`
```
❯ npm run dev

> vite-vanilla-ts@0.0.0 dev
> vite


  VITE v5.4.9  ready in 360 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h + enter to show help
undefined:1


[Failed to load PostCSS config: Failed to load PostCSS config (searchPath: /Users/anton/Development/Projects/vite-vanilla-ts): [SyntaxError] Unexpected end of JSON input
SyntaxError: Unexpected end of JSON input
    at JSON.parse (<anonymous>)
    at jsonLoader (file:///Users/anton/Development/Projects/vite-vanilla-ts/node_modules/vite/dist/node/chunks/dep-Cyk9bIUq.js:25733:41)
    at Object.search (file:///Users/anton/Development/Projects/vite-vanilla-ts/node_modules/vite/dist/node/chunks/dep-Cyk9bIUq.js:25894:25)]
```

3. Add default config. I got the same results by adding either a `.ts` or `.js` config.
```
❯ npm run dev

> vite-vanilla-ts@0.0.0 dev
> vite

✘ [ERROR] Unexpected end of file in JSON

    ../package.json:1:0:
      1 │ 
        ╵ ^

failed to load config from /Users/anton/Development/Projects/vite-vanilla-ts/vite.config.js
error when starting dev server:
Error: Build failed with 1 error:
../package.json:1:0: ERROR: Unexpected end of file in JSON
    at failureErrorWithLog (/Users/anton/Development/Projects/vite-vanilla-ts/node_modules/esbuild/lib/main.js:1472:15)
    at /Users/anton/Development/Projects/vite-vanilla-ts/node_modules/esbuild/lib/main.js:945:25
    at runOnEndCallbacks (/Users/anton/Development/Projects/vite-vanilla-ts/node_modules/esbuild/lib/main.js:1315:45)
    at buildResponseToResult (/Users/anton/Development/Projects/vite-vanilla-ts/node_modules/esbuild/lib/main.js:943:7)
    at /Users/anton/Development/Projects/vite-vanilla-ts/node_modules/esbuild/lib/main.js:970:16
    at responseCallbacks.<computed> (/Users/anton/Development/Projects/vite-vanilla-ts/node_modules/esbuild/lib/main.js:622:9)
    at handleIncomingPacket (/Users/anton/Development/Projects/vite-vanilla-ts/node_modules/esbuild/lib/main.js:677:12)
    at Socket.readFromStdout (/Users/anton/Development/Projects/vite-vanilla-ts/node_modules/esbuild/lib/main.js:600:7)
    at Socket.emit (node:events:518:28)
    at addChunk (node:internal/streams/readable:561:12)
```

Notice that:

1. None of the files were edited after scaffolding.
2. In both cases of getting an error (steps 2 and 3) the error message has something to do with the JSON parsing, although the files are different:
```
Unexpected end of file in JSON
```
