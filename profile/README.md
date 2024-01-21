# NiceAdvice App

## Foreword  
**<span style="color: red">Please read the materials below carefully before you begin.</span>**
### A bit of terminology to make it easier to understand what's going on:  
1. **T3 Stack** - combination of JS libs that provide you an opportunity to write 100% typed apps.  
2. **client-app** - main application with all interractions.  
3. **landing** - marketing plafrorm with blog.  
4. **admin** - admin panel for modaration and user deleteon 

## Installation. Use it for development purposes.

- clone target repo Example: `git clone git@github.com:NiceAdvice/client-app.git`
- `cd ./client-app`
- `pnpm i && npx prisma generate && pnpm dev`
- create .env files based on .env.example. Fill it with values. @madashindeinai can give you actual ones.

## Work flow:

_Commit example: NA-22 feat: {enter your commit message}_

1. _For each task, we make a separate branch from master (main)._
2. _Name the branch by the task name in Github Projects (for example NA-22)._
3. _Change card status in Github Project to the "in progress"._
4. _At the end of the task, open PR into master branch, assign Sergei and ask for review._
5. _Merge PR. Change card status to 'done'._

### **Makefile**:

For your convenience we have alias for popular terminal commands in Makefile. 'Make' util available by default macOS users. Can be installed by another os users. Ask for makefiles @madashindeinai


## Tech Stack:
1. T3 Stack - https://create.t3.gg/
  - NextJS - https://nextjs.org/
  - React 18+ - https://reactjs.org/
  - Prisma - https://www.prisma.io/
  - tRPC - https://trpc.io/
  - Tailwind CSS - https://tailwindcss.com/
2. TypeScript - https://www.typescriptlang.org/
3. PostgreSQL - https://www.postgresql.org/
4. Clerk - https://clerk.com/
## Libraries:

- React Query (tRPC version) - https://react-query-v3.tanstack.com/overview
- next-i18next - https://github.com/i18next/next-i18next
- zod - https://github.com/colinhacks/zod
- dayjs - https://day.js.org/
- shadcn-ui - https://ui.shadcn.com/  
#### Linters:

- Prettier
- Eslint  

## Update DB (do not do it without @madashindeinai approval)
1. `npx prisma migrate dev` will run a migration according new schema.prisma. **Remember to sync all 3 apps and resolve issues if they occure**  To do this, replace all inner files in prisma folder and run `npx prisma generate`

## Auth with Clerk:  
1. We are using pre-defined components.
2. We are saving all user's PP and T&C consents in our db on SignUp form submit.
3. After succesful "user.create" on Clerk side we are creating user in our db with webhook
4. We are using Clerk userId as id of user in our db.

## GTM and Cookie Consent:  
1. For each app we have configured Cookie consent with managing data about it with GTM (and GA).
2. For each app in GTM we have created container with a tag. Each tag linked by Meajurement ID with separate data stream that confugured on GA side.
3. [Very helpful article about that things. Probably will be needed to configure tags for PROD apps.](https://javascript.plainenglish.io/manage-cookie-consent-in-next-js-with-google-tag-manager-4d58818266ea)
4. GTM NEXT GUIDE: https://morganfeeney.com/guides/how-to-integrate-google-tag-manager-with-nextjs

## General info:

0. All files and folders use only lowercase naming. If name consists from 2 words - devide them with "-".  
1. Use only **PNPM** package manager for this project to avoid potential problems!
2. Use a linter while coding!
3. Deployments: [Landing](https://niceadvice.pl/), [app](app.niceadvice.pl), AdminApp - ask @madashindeinai
4. Use named export everywhere is possible.
5. next-i18next library is used for translations/text editing by customer. Use this syntax for common cases:

```
<h3>{t('Description')}</h3>

in json :

"Description": "Lorem ipsum: Lorem ipsum dolor sit amet",
```


Use this syntax if you need to show different text depending of props:
```
<h3>
  {t('DescriptionWithProp', { customProp: isCondition? t('ipsum') : t('test') })}
</h3>

in json:

"DescriptionWithProp": "Lorem {{customProp}}: Lorem ipsum dolor sit amet",
```

6. The src/components folder stores simple UI components that can be reused throughout the application.

7. The src/modules folder stores components that are individual, complex block of code, which is divided to simples subcomponents.

8. The src/utils folder stores some repeatedly used functions that are commonly used in the project and inputs validation.

9. The src/appConstants folder stores all constants variable used throughout the application.

10. Things related for app but not for partucular page or module can be stored in src/features (not used for now).

11. The src/screens folder stores jsx that should be represented on a page.  

12. All app text should be styled with custom classes defined in Tailwind (body,body-bold, body-sm etc.).
13. As Tailwind uses mobile-first approach we are using same in our app.
14. All text should be stored in json files in public folder.
15. Project ruler length - `"editor.rulers": [80]`. 
15. PostgreSQL stored on Supabase. CI/CD process provided by Vercel. 
16. Prisma require separate space for [shadow DBs](https://www.prisma.io/docs/concepts/components/prisma-migrate/shadow-database#cloud-hosted-shadow-databases-must-be-created-manually), supabase require to use [different ports](https://supabase.com/docs/guides/integrations/prisma#connection-pooling-with-supabase) for migrations and actual work with db
17. [Supabase -> Prisma integration guide](https://supabase.com/partners/integrations/prisma)


## Create T3 App Template basic description.

This is a [T3 Stack](https://create.t3.gg/) project bootstrapped with `create-t3-app`.

## What's next? How do I make an app with this?

We try to keep this project as simple as possible, so you can start with just the scaffolding we set up for you, and add additional things later when they become necessary.

If you are not familiar with the different technologies used in this project, please refer to the respective docs. If you still are in the wind, please join our [Discord](https://t3.gg/discord) and ask for help.

- [Next.js](https://nextjs.org)
- [Prisma](https://prisma.io)
- [Tailwind CSS](https://tailwindcss.com)
- [tRPC](https://trpc.io)

## Learn More

To learn more about the [T3 Stack](https://create.t3.gg/), take a look at the following resources:

- [Documentation](https://create.t3.gg/)
- [Learn the T3 Stack](https://create.t3.gg/en/faq#what-learning-resources-are-currently-available) — Check out these awesome tutorials

You can check out the [create-t3-app GitHub repository](https://github.com/t3-oss/create-t3-app) — your feedback and contributions are welcome!

## How do I deploy this?

Follow our deployment guides for [Vercel](https://create.t3.gg/en/deployment/vercel), [Netlify](https://create.t3.gg/en/deployment/netlify) and [Docker](https://create.t3.gg/en/deployment/docker) for more information.  

## Init Fly.io (Postgres) !!!Legacy knowledges. Supabase used for now.
1. Install fly CLI on your machine: `brew install flyctl`  
2. Login to fly via CLI: `fly auth login`
3. [Add credit card](https://fly.io/dashboard/madashindeinai/billing)
4. [Create postgres in Fly](https://fly.io/docs/postgres/getting-started/create-pg-cluster/): `fly postgres create`  
**ATTENTION!!!!! It will give you creds for DB that will be shown only once. Save them in secure place!**      

<img width="660" alt="Screenshot 2023-03-07 at 16 10 41" src="https://user-images.githubusercontent.com/50995397/223463416-de1792b5-c58a-4797-9d0d-04fdf0d8b0c5.png">  

5. [Share app for external use (outside of Fly)](https://fly.io/docs/postgres/connecting/connecting-external/):  

<img width="589" alt="Screenshot 2023-03-07 at 16 22 11" src="https://user-images.githubusercontent.com/50995397/223470174-4b8c9f51-00f7-4dca-b183-b2715c5b8cda.png">  

<img width="639" alt="Screenshot 2023-03-07 at 16 22 37" src="https://user-images.githubusercontent.com/50995397/223470275-4cab3346-3daf-45a1-9f28-fc97abcd3584.png">  

<img width="1108" alt="Screenshot 2023-03-07 at 16 27 53" src="https://user-images.githubusercontent.com/50995397/223470388-e7d7b239-5131-4945-9e3a-e991d015345d.png">
