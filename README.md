# SSR issue with C3 astro blog
Trying out the astro blog template with cloudlare pages results in this error the first time you browse to a blog post

```
TypeError
An error occurred.
post.render is not a function
```

### Repro steps
1. npm create cloudflare
1. choose the **astro** **framework** starter, then choose the **blog** template
1. run `npm run dev` and browse to any blog post like http://localhost:4321/blog/markdown-style-guide/

This repo is the result of steps 1-3. Terminal output below.
See related discussion on the [astro discord](https://discord.com/channels/830184174198718474/1276586107869466726/1276586107869466726)

```
~/cloudflare$ pnpm create cloudflare
.../1926df13d59-4074                     |   +1 +
.../1926df13d59-4074                     | Progress: resolved 1, reused 1, downloaded 0, added 1, done

────────────────────────────────────────────────────────────
👋 Welcome to create-cloudflare v2.29.2!
🧡 Let's get started.
────────────────────────────────────────────────────────────

╭ Create an application with Cloudflare Step 1 of 3
│ 
├ In which directory do you want to create your application?
│ dir ./pages-astro-oct-8
│
├ What would you like to start with?
│ category Framework Starter
│
├ Which development framework do you want to use?
│ framework Astro
│
├ Continue with Astro via `pnpm dlx create-astro@4.8.0 pages-astro-oct-8 --no-install`
│

Packages: +39
+++++++++++++++++++++++++++++++++++++++
Progress: resolved 39, reused 39, downloaded 0, added 39, done

 astro   Launch sequence initiated.

      ◼  dir Using pages-astro-oct-8 as project directory

  tmpl   How would you like to start your new project?
         Use blog template

    ts   Do you plan to write TypeScript?
         Yes

   use   How strict should TypeScript be?
         Strict
      ◼  No problem! Remember to install dependencies after setup.

   git   Initialize a new git repository?
         Yes

      ✔  Project initialized!
         ■ Template copied
         ■ TypeScript customized
         ■ Git initialized

  next   Liftoff confirmed. Explore your project!

         Enter your project directory using cd ./pages-astro-oct-8 
         Run pnpm dev to start the dev server. CTRL+C to stop.
         Add frameworks like react or tailwind using astro add.

         Stuck? Join us at https://astro.build/chat

╭─────╮  Houston:
│ ◠ ◡ ◠  Good luck out there, astronaut! 🚀
╰──🦴─╯

├ Copying template files 
│ files copied to project directory
│ 
├ Installing dependencies 
│ installed via `pnpm install`
│ 
╰ Application created 

╭ Configuring your application for Cloudflare Step 2 of 3
│ 
├ Installing wrangler A command line tool for building Cloudflare Workers 
│ installed via `pnpm install wrangler --save-dev`
│ 
├ Installing @cloudflare/workers-types 
│ installed via pnpm
│ 
├ Adding latest types to `tsconfig.json` 
│ added @cloudflare/workers-types/2023-07-01
│ 
├ Retrieving current workerd compatibility date 
│ compatibility date 2024-10-04
│ 
├ Installing adapter 
│ installed via `pnpm astro add cloudflare`
│ 
├ Updating configuration in astro.config.mjs
│
├ Adding type declarations in src/env.d.ts
│
├ Adding Wrangler files to the .gitignore file 
│ updated .gitignore file
│ 
├ Updating `package.json` scripts 
│ updated `package.json`
│ 
├ Committing new files 
│ git commit
│ 
╰ Application configured 

╭ Deploy with Cloudflare Step 3 of 3
│ 
├ Do you want to deploy your application?
│ no deploy via `pnpm run deploy`
│
╰ Done 

────────────────────────────────────────────────────────────
🎉  SUCCESS  Application created successfully!

💻 Continue Developing
Change directories: cd pages-astro-oct-8
Start dev server: pnpm run dev
Deploy: pnpm run deploy

📖 Explore Documentation
https://developers.cloudflare.com/pages

💬 Join our Community
https://discord.cloudflare.com
────────────────────────────────────────────────────────────


~/cloudflare$ cd pages-astro-oct-8/
jurgen@jldec.me main ~/cloudflare/pages-astro-oct-8$ pnpm dev

> pages-astro-oct-8@0.0.1 dev /Users/jldec/cloudflare/pages-astro-oct-8
> astro dev

22:05:13 [WARN] The currently selected adapter `@astrojs/cloudflare` is not compatible with the image service "Sharp".
22:05:13 [WARN] [config] The adapter @astrojs/cloudflare provides experimental support for "astro:env getSecret". You may experience issues or breaking changes until this feature is fully supported by the adapter.
22:05:13 [types] Generated 1ms

 astro  v4.15.12 ready in 2232 ms

┃ Local    http://localhost:4321/
┃ Network  use --host to expose

22:05:15 watching for file changes...
o
22:05:35 [200] / 107ms
22:05:35 [200] / 47ms
22:05:42 [WARN] [router] getStaticPaths() ignored in dynamic page /src/pages/blog/[...slug].astro. Add `export const prerender = true;` to prerender the page as static HTML during the build process.
22:05:42 [200] /blog 28ms
22:05:46 [ERROR] post.render is not a function
  Stack trace:
    at /Users/jldec/cloudflare/pages-astro-oct-8/src/pages/blog/[...slug].astro:15:32
    [...] See full stack trace in the browser, or rerun with --verbose.
22:05:57 [ERROR] post.render is not a function
  Stack trace:
    at /Users/jldec/cloudflare/pages-astro-oct-8/src/pages/blog/[...slug].astro:15:32
    [...] See full stack trace in the browser, or rerun with --verbose.
```

![Screenshot 2024-10-08 at 22 33 08](https://github.com/user-attachments/assets/2d6797a0-a799-4f2d-a52c-fbd14903d14a)
