# Galleria bilingual portfolio — setup

This is a deployable bilingual (Arabic/English) portfolio with a Supabase-powered online CMS.
It is a starter package: it becomes a shared live website after you connect your own Supabase project and deploy it to a hosting provider.

## 1) Create Supabase backend
1. Create a free project at https://supabase.com/
2. Open SQL Editor and run all contents of `supabase-setup.sql`.
3. In Storage, create a bucket named `product-images` and set it to **Public**.
4. Open Project Settings → API. Copy Project URL and anon/public key into `config.js`.
   Never put a `service_role` key in browser code.

## 2) Create your admin login
1. In Supabase → Authentication → Users, add a user with your email and a strong password.
2. Copy that user's UUID.
3. In SQL Editor run (replace UUID):
   `insert into public.admin_users(user_id) values ('YOUR-USER-UUID');`
4. Disable public sign-ups in Authentication settings if you do not need them.

## 3) Deploy the website
1. Create a GitHub repository and upload `index.html`, `app.js`, and `config.js`.
2. Import the repository into https://vercel.com/ and deploy with the default static settings.
3. Your public address will be a free `*.vercel.app` URL. You can connect a custom domain later if you buy one.
4. Open `your-site.vercel.app/#admin` to manage the website.

## Features
- Arabic / English language switch.
- Public gallery with category filters, search, sorting, lazy-loaded images and product detail modal.
- Admin sign-in via Supabase Auth.
- Online editing for brand name, tagline, About in both languages, email, phone and Instagram.
- Add, edit and delete products, with image upload to Supabase Storage.

## Notes
- Do not share your Supabase password or service-role key.
- The admin route is not protected by a client-side password; it uses Supabase Auth and database/storage row-level security.
- This package does not publish itself. Supabase project setup and Vercel deployment are required.
