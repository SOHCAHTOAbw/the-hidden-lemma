# Deploy The Hidden Lemma to Cloudflare Pages

## Recommended: Git integration
1. Extract this project and push its contents to a GitHub repository named `the-hidden-lemma`.
2. Cloudflare dashboard → Workers & Pages → Create → Pages → Connect to Git.
3. Select the repository and use:
   - Production branch: `main`
   - Build command: `npm run build`
   - Build output directory: `dist`
   - Root directory: `/`
4. Save and deploy.
5. Pages will provide `<project>.pages.dev`.

## Custom domain
1. Pages project → Custom domains → Set up a domain.
2. Add `thehiddenlemma.com` first and allow Cloudflare to create its DNS record.
3. Add `www.thehiddenlemma.com` second.
4. Do not type `https://` in a CNAME target. Use only the exact `<project>.pages.dev` hostname.
5. The included `public/_redirects` sends `www` traffic to the apex domain.

## Direct upload alternative
Run locally:
```bash
npm install
npm run build
npx wrangler pages deploy dist --project-name the-hidden-lemma
```
Upload only the generated `dist/` directory, not the Astro source directory.
