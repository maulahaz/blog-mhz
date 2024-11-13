# AstroPaper 📄

![AstroPaper](public/astropaper-og.jpg)
[![Figma](https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white)](https://www.figma.com/community/file/1356898632249991861)
![Typescript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![GitHub](https://img.shields.io/github/license/satnaing/astro-paper?color=%232F3741&style=for-the-badge)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-%23FE5196?logo=conventionalcommits&logoColor=white&style=for-the-badge)](https://conventionalcommits.org)
[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg?style=for-the-badge)](http://commitizen.github.io/cz-cli/)

AstroPaper is a minimal, responsive, accessible and SEO-friendly Astro blog theme. This theme is designed and crafted based on [my personal blog](https://satnaing.dev/blog).

This theme follows best practices and provides accessibility out of the box. Light and dark mode are supported by default. Moreover, additional color schemes can also be configured.

This theme is self-documented \_ which means articles/posts in this theme can also be considered as documentations. Read [the blog posts](https://astro-paper.pages.dev/posts/) or check [the README Documentation Section](#-documentation) for more info.

## 🔥 Features

- [x] type-safe markdown
- [x] super fast performance
- [x] accessible (Keyboard/VoiceOver)
- [x] responsive (mobile ~ desktops)
- [x] SEO-friendly
- [x] light & dark mode
- [x] fuzzy search
- [x] draft posts & pagination
- [x] sitemap & rss feed
- [x] followed best practices
- [x] highly customizable
- [x] dynamic OG image generation for blog posts [#15](https://github.com/satnaing/astro-paper/pull/15) ([Blog Post](https://astro-paper.pages.dev/posts/dynamic-og-image-generation-in-astropaper-blog-posts/))

_Note: I've tested screen-reader accessibility of AstroPaper using **VoiceOver** on Mac and **TalkBack** on Android. I couldn't test all other screen-readers out there. However, accessibility enhancements in AstroPaper should be working fine on others as well._

## ✅ Lighthouse Score

<p align="center">
  <a href="https://pagespeed.web.dev/report?url=https%3A%2F%2Fastro-paper.pages.dev%2F&form_factor=desktop">
    <img width="710" alt="AstroPaper Lighthouse Score" src="AstroPaper-lighthouse-score.svg">
  <a>
</p>

## 🚀 Project Structure

Inside of AstroPaper, you'll see the following folders and files:

```bash
/
├── public/
│   ├── assets/
│   │   └── logo.svg
│   │   └── logo.png
│   └── favicon.svg
│   └── astropaper-og.jpg
│   └── robots.txt
│   └── toggle-theme.js
├── src/
│   ├── assets/
│   │   └── socialIcons.ts
│   ├── components/
│   ├── content/
│   │   |  blog/
│   │   |    └── some-blog-posts.md
│   │   └── config.ts
│   ├── layouts/
│   └── pages/
│   └── styles/
│   └── utils/
│   └── config.ts
│   └── types.ts
└── package.json
```

Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

Any static assets, like images, can be placed in the `public/` directory.

All blog posts are stored in `src/content/blog` directory.

## 📖 Documentation

Documentation can be read in two formats\_ _markdown_ & _blog post_.

- Configuration - [markdown](src/content/blog/how-to-configure-astropaper-theme.md) | [blog post](https://astro-paper.pages.dev/posts/how-to-configure-astropaper-theme/)
- Add Posts - [markdown](src/content/blog/adding-new-post.md) | [blog post](https://astro-paper.pages.dev/posts/adding-new-posts-in-astropaper-theme/)
- Customize Color Schemes - [markdown](src/content/blog/customizing-astropaper-theme-color-schemes.md) | [blog post](https://astro-paper.pages.dev/posts/customizing-astropaper-theme-color-schemes/)
- Predefined Color Schemes - [markdown](src/content/blog/predefined-color-schemes.md) | [blog post](https://astro-paper.pages.dev/posts/predefined-color-schemes/)

> For AstroPaper v1, check out [this branch](https://github.com/satnaing/astro-paper/tree/astro-paper-v1) and this [live URL](https://astro-paper-v1.astro-paper.pages.dev/)

## 💻 Tech Stack

**Main Framework** - [Astro](https://astro.build/)  
**Type Checking** - [TypeScript](https://www.typescriptlang.org/)  
**Component Framework** - [ReactJS](https://reactjs.org/)  
**Styling** - [TailwindCSS](https://tailwindcss.com/)  
**UI/UX** - [Figma Design File](https://www.figma.com/community/file/1356898632249991861)  
**Fuzzy Search** - [FuseJS](https://fusejs.io/)  
**Icons** - [Boxicons](https://boxicons.com/) | [Tablers](https://tabler-icons.io/)  
**Code Formatting** - [Prettier](https://prettier.io/)  
**Deployment** - [Cloudflare Pages](https://pages.cloudflare.com/)  
**Illustration in About Page** - [https://freesvgillustration.com](https://freesvgillustration.com/)  
**Linting** - [ESLint](https://eslint.org)

## 👨🏻‍💻 Running Locally

You can start using this project locally by running the following command in your desired directory:

```bash
# npm 6.x
npm create astro@latest --template satnaing/astro-paper

# npm 7+, extra double-dash is needed:
npm create astro@latest -- --template satnaing/astro-paper

# yarn
yarn create astro --template satnaing/astro-paper

# pnpm
pnpm dlx create-astro --template satnaing/astro-paper
```

> **_Warning!_** If you're using `yarn 1`, you might need to [install `sharp`](https://sharp.pixelplumbing.com/install) as a dependency.

Then start the project by running the following commands:

```bash
# install dependencies
npm run install

# start running the project
npm run dev
```

As an alternative approach, if you have Docker installed, you can use Docker to run this project locally. Here's how:

```bash
# Build the Docker image
docker build -t astropaper .

# Run the Docker container
docker run -p 4321:80 astropaper
```

## Google Site Verification (optional)

You can easily add your [Google Site Verification HTML tag](https://support.google.com/webmasters/answer/9008080#meta_tag_verification&zippy=%2Chtml-tag) in AstroPaper using an environment variable. This step is optional. If you don't add the following environment variable, the google-site-verification tag won't appear in the HTML `<head>` section.

```bash
# in your environment variable file (.env)
PUBLIC_GOOGLE_SITE_VERIFICATION=your-google-site-verification-value
```

> See [this discussion](https://github.com/satnaing/astro-paper/discussions/334#discussioncomment-10139247) for adding AstroPaper to the Google Search Console.

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

> **_Note!_** For `Docker` commands we must have it [installed](https://docs.docker.com/engine/install/) in your machine.

| Command                              | Action                                                                                                                           |
| :----------------------------------- | :------------------------------------------------------------------------------------------------------------------------------- |
| `npm install`                        | Installs dependencies                                                                                                            |
| `npm run dev`                        | Starts local dev server at `localhost:4321`                                                                                      |
| `npm run build`                      | Build your production site to `./dist/`                                                                                          |
| `npm run preview`                    | Preview your build locally, before deploying                                                                                     |
| `npm run format:check`               | Check code format with Prettier                                                                                                  |
| `npm run format`                     | Format codes with Prettier                                                                                                       |
| `npm run sync`                       | Generates TypeScript types for all Astro modules. [Learn more](https://docs.astro.build/en/reference/cli-reference/#astro-sync). |
| `npm run lint`                       | Lint with ESLint                                                                                                                 |
| `docker compose up -d`               | Run AstroPaper on docker, You can access with the same hostname and port informed on `dev` command.                              |
| `docker compose run app npm install` | You can run any command above into the docker container.                                                                         |
| `docker build -t astropaper .`       | Build Docker image for AstroPaper.                                                                                               |
| `docker run -p 4321:80 astropaper`   | Run AstroPaper on Docker. The website will be accessible at `http://localhost:4321`.                                             |

> **_Warning!_** Windows PowerShell users may need to install the [concurrently package](https://www.npmjs.com/package/concurrently) if they want to [run diagnostics](https://docs.astro.build/en/reference/cli-reference/#astro-check) during development (`astro check --watch & astro dev`). For more info, see [this issue](https://github.com/satnaing/astro-paper/issues/113).

## ✨ Feedback & Suggestions

If you have any suggestions/feedback, you can contact me via [my email](mailto:contact@satnaing.dev). Alternatively, feel free to open an issue if you find bugs or want to request new features.

## 📜 License

Licensed under the MIT License, Copyright © 2023

---

Made with 🤍 by [Sat Naing](https://satnaing.dev) 👨🏻‍💻 and [contributors](https://github.com/satnaing/astro-paper/graphs/contributors).


======

"Safety First, Bismillah First"

You know, every company these days starts their meetings with the same old slogan: "Safety first." And you know what? They're absolutely right. Safety should be the top priority for any organization - or really, for all of us in our daily lives.

But did you know that as Muslims, we've got our own version of "safety first"? It's called saying "Bismillah" - which means "In the name of Allah" in Arabic. Now, I know what you're thinking: "What's the connection between safety and saying some Arabic phrase?" Well, let me tell you, there's a strong link there.

When we say "Bismillah" before starting any task or activity, we're essentially asking Allah, the Almighty, to watch over us and keep us safe. We're acknowledging that He is in control of everything in this universe, and that we need His protection and guidance. It's like the company's "safety first" slogan, but on a deeper, spiritual level.

But it's not just about safety, my friends. When we say "Bismillah," we're also reminding ourselves to be mindful and do things the right way. We know that if we act carelessly or ignore safety protocols, we won't just be putting ourselves at risk - we might also incur the displeasure of Allah. And trust me, you don't want that.


===
### Safety First: A Muslim’s Perspective with "Bismillah"

You’ve probably heard the slogan "Safety First" in workplaces, meetings, or even just in everyday life. It’s a simple idea but a powerful one. Before you start any task, make sure safety is your top priority. It's all about protecting yourself and others. But what if I told you that as a Muslim, we have something very similar, something even deeper, that ties safety to our faith?

It’s the simple yet powerful phrase "Bismillah" – "In the name of Allah."

* * *

### What Does "Bismillah" Have to Do with Safety?

For Muslims, saying “Bismillah” before any task is like putting on a seatbelt before driving. It’s a way of asking Allah for protection and guidance. You might say it before a big meeting, while you’re heading to work, or even before you start something as simple as a meal or a workout.

Saying “Bismillah” is more than just a routine – it’s a conscious request for divine protection. We believe that by saying it, we're acknowledging that Allah is in control of everything, and we’re asking for His help to keep us safe in all that we do.

* * *

### Why It Matters: Protection, Accountability, and Rewards

1.  Protection  
    Saying “Bismillah” is like a shield. It’s a reminder that we are not alone in whatever we do, whether it's driving to the office or fixing a leaky pipe at home. It’s an active step in ensuring our safety by putting our trust in Allah.
    
2.  Mindfulness and Accountability  
    But it’s not just about safety; saying “Bismillah” is a way to make us more mindful of how we approach things. It’s about doing things the right way, with care. When you say "Bismillah," you’re also reminding yourself to take things seriously, follow the right procedures, and not cut corners. This is where safety and faith go hand-in-hand.
    
3.  Rewards and Consequences  
    The beauty of saying "Bismillah" is that it reminds us that our actions matter. When we do things the right way – safely, responsibly – we’re not only avoiding harm, but we’re also earning rewards from Allah. On the flip side, if we bypass safety, act carelessly, or ignore rules, we’re at risk of harm, both physically and spiritually. So, it’s a win-win: by prioritizing safety, we’re doing what's right for us and earning rewards in the process.
    

* * *

### More Than Just Personal Safety

It’s easy to think that saying “Bismillah” is just for your own protection. But in Islam, it’s not just about you. Saying "Bismillah" before any task is also a way to ensure the safety of your family and environment. Your actions ripple outward – from how you drive your car to how you treat your coworkers – and the goal is to make sure everyone around you stays safe, too. By invoking Allah’s name, you’re ensuring that your environment remains peaceful, secure, and protected.

So, next time you’re about to start something important, whether it’s a work project, driving home, or even just cooking dinner, take a moment to say “Bismillah.” It’s not just a habit – it’s a powerful, meaningful way to ensure you stay protected and do things right.

Remember, safety isn’t just about rules and regulations – it’s about being mindful, responsible, and trusting in Allah. By saying “Bismillah,” you’re aligning both your faith and your actions with safety and success. It’s a simple step, but it makes all the difference.
