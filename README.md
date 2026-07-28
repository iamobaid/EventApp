# Evently

A full-stack event management platform built with Next.js 14. Users can browse and search events, create and manage their own events, and purchase tickets through a Stripe-powered checkout.

## Features

- **Authentication** — user sign-up, sign-in, and profile management via Clerk, synced to the app database through Clerk webhooks.
- **Event management (CRUD)** — create, view, update, and delete events with title, description, date, location, price, and category.
- **Image upload** — event banner images uploaded via UploadThing, with drag-and-drop support.
- **Categories** — events are organized into categories, with new categories creatable on the fly from the event form.
- **Search & filter** — full-text search by event title plus category filtering on the events listing.
- **Related events** — events in the same category are surfaced on an event's detail page.
- **Organizer profile** — a profile page listing the events a user has created and the tickets they've purchased.
- **Ticket checkout** — Stripe Checkout integration for paid events, with free events supported directly.
- **Order management** — order history for buyers, plus a searchable list of orders per event for organizers, backed by a Stripe webhook that records completed purchases.
- **Pagination** — paginated event listings and order lists.

## Tech stack

| Layer | Technology |
|---|---|
| Framework | Next.js 14 (App Router) |
| Language | TypeScript |
| Auth | Clerk |
| Database / ODM | MongoDB + Mongoose |
| Payments | Stripe Checkout |
| File uploads | UploadThing |
| Styling | Tailwind CSS, shadcn/ui |
| Forms | React Hook Form, Zod |

## Screenshots

_Add screenshots of the events listing, event detail page, and checkout flow here._

## Local setup

**Prerequisites:** Node.js, a MongoDB database, a Clerk account, a Stripe account, and an UploadThing account.

1. Clone the repo and install dependencies:

   ```bash
   git clone https://github.com/iamobaid/EventApp.git
   cd EventApp
   npm install
   ```

2. Create a `.env` file in the project root with:

   ```env
   # Next.js
   NEXT_PUBLIC_SERVER_URL=http://localhost:3000

   # Clerk
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
   CLERK_SECRET_KEY=
   WEBHOOK_SECRET=

   NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
   NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
   NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/
   NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/

   # MongoDB
   MONGODB_URI=

   # UploadThing
   UPLOADTHING_SECRET=
   UPLOADTHING_APP_ID=

   # Stripe
   STRIPE_SECRET_KEY=
   STRIPE_WEBHOOK_SECRET=
   NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=
   ```

3. Start the dev server:

   ```bash
   npm run dev
   ```

   The app runs at [http://localhost:3000](http://localhost:3000).

## Project structure

```
app/
  (auth)/                  # Sign-in / sign-up routes (Clerk)
  (root)/
    events/                 # Event detail and event creation/update pages
    orders/                 # Order search page for organizers
    profile/                # User's created events and purchased tickets
  api/
    webhook/clerk/          # Clerk user sync webhook
    webhook/stripe/         # Stripe checkout completion webhook
    uploadthing/             # UploadThing route config
components/
  shared/                    # Event cards, forms, checkout, search, filters, nav
  ui/                        # shadcn/ui components
lib/
  actions/                   # Server actions: events, orders, categories, users
  database/models/           # Mongoose models: Event, Order, User, Category
  validator.ts                # Zod schemas
constants/                   # Static app constants
types/                        # Shared TypeScript types
```

## Credits

This project was built as a learning exercise following a publicly available
full-stack tutorial, then extended and maintained here. Credit for the original
course material and project structure goes to its respective authors.

The upstream project this was built from is published without a license, so no
license is asserted here either. The repository is shared for portfolio and
reference purposes.