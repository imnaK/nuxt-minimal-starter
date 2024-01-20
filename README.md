# nuxt-minimal-starter

Project for representing a potential bug in nuxt3.
I could not reproduce it in vue3 with a similar setup.

## Steps to reproduce:
- The parallax effect will break if the page rerenders some part. You can test this by editing "THIS" word in code. (`index.vue`)
- It will also break if you build the project and run it on preview or production server.
## Temporary fix:
- It will be fixed if you reload the page (only on dev server).
- It will also be fixed if you switch pages and come back.
## Real fix:
The actual fix is in the `index.vue` file commented out in line 15.

## Nuxt 3 Minimal Starter

Look at the [Nuxt 3 documentation](https://nuxt.com/docs/getting-started/introduction) to learn more.

### Setup

Make sure to install the dependencies:

```bash
# npm
npm install

# pnpm
pnpm install

# yarn
yarn install

# bun
bun install
```

### Development Server

Start the development server on `http://localhost:3000`:

```bash
# npm
npm run dev

# pnpm
pnpm run dev

# yarn
yarn dev

# bun
bun run dev
```

### Production

Build the application for production:

```bash
# npm
npm run build

# pnpm
pnpm run build

# yarn
yarn build

# bun
bun run build
```

Locally preview production build:

```bash
# npm
npm run preview

# pnpm
pnpm run preview

# yarn
yarn preview

# bun
bun run preview
```

Check out the [deployment documentation](https://nuxt.com/docs/getting-started/deployment) for more information.
