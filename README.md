# A09 — Venue Explorer: Data Fetching

Next.js app continuing A08, with venue information fetched from the assignment backend.

## Run locally

```bash
npm install
npm run dev
```

Open http://localhost:3000/venue to browse the three venues. Select a card to see its image, address, district, province, postal code, telephone number, and daily rental rate.

## Implementation

- `src/libs/getVenues.tsx` fetches the catalog as `Promise<VenueJson>`.
- `src/components/VenueCatalog.tsx` awaits that promise and renders cards without ratings.
- `src/libs/getVenue.tsx` fetches one venue using its backend ID.
- `/venue/[vid]` renders the fetched details with asynchronous route parameters.
- Ratings remain available to A08 components that pass `onRatingChange`.
- Requests run on the server with `cache: "no-store"`. Backend availability is required at runtime, not during the production build.
- `next.config.ts` permits the backend's Google Drive pictures through Next.js Image optimization. Server-side API fetches do not require frontend CORS headers.

## Validate

```bash
npm test -- --runInBand
npx eslint src interface.ts next.config.ts
npm run build
npm run start
```

The supplied grading files use `var` and `any`, so the starter's repository-wide `npm run lint` reports errors in those unchanged tests.

## Submission

Deployment URL: not deployed yet.

Before submitting:

1. Push the completed project to the assignment repository and your personal GitHub repository.
2. Import the personal repository into Vercel as a Next.js project and deploy.
3. Verify `/venue`, each venue detail page, and venue images on the deployed site.
4. Replace the deployment status above with the actual Vercel URL in both repositories.

The manual grading point requires the deployed `/venue` page to fetch and display real backend data.
