# Mobile Store PK (production candidate — see 'Not yet built')

## Roman Urdu Setup Guide
1. **GitHub:** github.com par new repository banayein, phir is folder ko upload karein (`.env` kabhi upload na karein).
2. **Database:** neon.tech par free PostgreSQL banayein, `DATABASE_URL` copy karein.
3. **Vercel:** vercel.com > Add New Project > apni GitHub repo import karein.
4. **Environment variables** (Vercel > Settings > Environment Variables), `.env.example` dekhein:
   DATABASE_URL, GMAIL_USER, GMAIL_APP_PASSWORD, NOTIFY_EMAIL, DELIVERY_FEE, SITE_URL, AUTH_SECRET, ADMIN_PASSWORD, BLOB_READ_WRITE_TOKEN.
5. **Gmail:** Google Account > Security > 2-Step Verification ON > App Passwords se 16-digit password banayein > GMAIL_APP_PASSWORD mein daalein.
6. **Images:** Vercel > Storage > Blob banayein; token BLOB_READ_WRITE_TOKEN mein aa jata hai.
7. **Tables banane ke liye (sirf aik dafa, apne computer par):** `npm install`, DATABASE_URL set karke `npx prisma db push`, phir `npm run seed`.
8. **Admin:** `/admin/login` par ADMIN_PASSWORD se login. AUTH_SECRET lamba random text rakhein.
9. **Pehla phone:** Admin > + New Product > form bharein > Save & Publish. Demo phones Products list se delete karein.
10. **Test:** Admin > Send Test Email dabayein, phir aik test order dein aur email check karein.

## Changes in this version
Multi-item cart, OrderItem table, atomic stock decrement inside a transaction, stock restored on cancel, login rate limit (5 tries / 15 min), Next 14.2.35, Nodemailer 10, Prisma 5.22, security headers.
**Schema changed:** run `npx prisma db push` on a fresh database (Phase 1/2 order tables are not compatible; there are no migration files).

## Not yet built / not tested
Product variants with own price/stock, categories, banners, blog, shipping/SEO settings pages, /latest-mobiles, /mobile-deals, /best-selling-mobiles.
Not run: prisma generate, full next build, database, checkout concurrency, image upload, Gmail (sandbox cannot download Prisma engines or reach Gmail).
