# QuickCommerce Web Frontend Demo

A standalone React + TypeScript + Vite recreation of the customer-facing workflow from the supplied QuickCommerce alpha repository.

## Workflow included
1. Phone authentication screen (mock OTP, matching the supplied alpha).
2. Product discovery with search and category filters.
3. Product cards with stock state and quantity controls.
4. Cart drawer with subtotal and free delivery.
5. Checkout review flow.
6. Successful order confirmation.
7. `409 OUT_OF_STOCK` demo path using the seeded Free-Range Eggs product.
8. Retry flow that visually demonstrates the same idempotency-key concept used by the backend.

## Run

Requirements: Node.js 18+.

```bash
npm install
npm run dev
```

Open the localhost URL printed by Vite.

## Connect the real backend

This demo is intentionally frontend-only and uses local mock state so it runs immediately. To wire it to the supplied NestJS API, replace the mock handlers in `src/main.tsx` with calls to:

- `POST /api/v1/auth/login`
- `GET /api/v1/products?cursor=&limit=`
- `POST /api/v1/orders` with `Authorization: Bearer <token>` and an `Idempotency-Key` header

The UI states are already aligned with the backend's documented success and error envelopes.
