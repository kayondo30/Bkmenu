# Simu Works website - project prompt (v9, 2026-11-02)
NEXT TASK (kept on the first line; update it in every version): upload simuworks-v9.zip (no database change), check the video plays on my phone, delete test booking SW-7WU7E in admin, then share the site and the video with my first real businesses.

VERSION RULE (like FHG): one whole number for everything, counting 1, 2, 3, 4, 5... Every change Claude delivers is the next number, and the prompt file and the site zip carry the SAME number (simu-works-website-prompt-v10.md + simuworks-v10.zip). No decimals. The build steps below are called Stages, not versions, so they never get mixed up. The site footer shows the version (config.js "version").

ONE PROMPT HABIT: upload this file at the start of every new chat and update it at every version (Claude gives me the new file each time). Claude teaches me as we build: every step says what it does and why, in plain words. I am learning, so no step is skipped or assumed.

## LOCKED DECISIONS
- Business name: SIMU WORKS (chosen 2026-11-01; "simu" = phone in Swahili; phone-first apps made simply). Before printing anything, I check the name on the URSB name search and on Google. The same name may become my URSB company for the Play Store organisation account (see the FHG prompt).
- Tagline (in use; change in config.js if wanted): "Phone-first menus and apps for Ugandan businesses."
- Address: https://simuworks.pages.dev (free Cloudflare Pages, project name simuworks, LIVE). Own domain (.com or .co.ug, about UGX 45,000 to 110,000 a year) later, once the first clients pay.
- Hosting: Cloudflare Pages (direct upload) + Supabase, the same way as the BK menu. Site zip = only the site files at top level; never upload the GitHub project zip to Cloudflare.
- SUPABASE: Simu Works has its OWN Supabase account, on kayondobaker3@gmail.com (not kayondo30). Project simuworks, URL https://srlksusvcvqrgdgrcasd.supabase.co, publishable key in config.js (safe in the site). The database password, secret key and service_role key are NEVER shared, never put in the site, never sent to Claude.
- Look: calm teal/sage look based on the FHG "Calm" look, with light/dark toggle. Fonts Bricolage Grotesque (headings) + Figtree (text). Works well on a phone first.
- Admin: only me, at https://simuworks.pages.dev/admin. Login kayondo30@gmail.com (a Supabase Auth user in the Simu Works project, user id 192ce38e-cc7d-4d54-8a4a-1c0caf4baba8; the database only accepts this id as admin) + Action PIN (4-8 digits, stored scrambled with pgcrypto; 5 wrong = locked 15 minutes; remembered 5 minutes on screen; always asked to delete). Customers never log in. Passwords and PINs are never sent to Claude.
- CONTACTS (all in config.js):
  - Main WhatsApp + calls: +256 785 104 465 (big WhatsApp buttons; https://wa.me/256785104465)
  - Second WhatsApp + calls: +256 705 814 221 (contact section; https://wa.me/256705814221)
  - Email: kayondo30@gmail.com
- WhatsApp Business (set up 2026-11-01): categories Web Designer + Software Company; no physical location, area Kampala/Uganda; website simuworks.pages.dev; description, greeting message, away message, quick replies /site and /pay. Catalog postponed until there are good screenshots (4 items: Basic, Standard, Premium, Monthly care).
- Currency UGX. Language English (more later if needed).
- Never hard-code wording that may change: business name, phone, prices and texts go in one config.js (same rule as the BK menu template).

## THE SITE
1. Home: tagline, intro, WhatsApp + See prices buttons, a small phone showing a menu price changing by itself; three benefits.
2. Work: BK menu as a DEMO (I built BK myself as my first practice project; not a paying client; always called a demo). FHG FX Signals as "Our own app, in progress" with NO link while under construction (add link + button in config.js when ready; no profit or results claims, ever). Real client menus added later, with their permission.
3. Prices: three packages + monthly care + launch offer; Standard marked "Recommended"; each card has a "Book <package>" button.
4. How it works: 4 steps (chat, 50% to start, build and check, 50% when live).
5. Book a call (#book): package, name, business name, phone, optional note. Saves the request and shows a booking code (SW-XXXXX), a WhatsApp button that sends me the code, and Copy code.
5b. See how booking works (#video, just above Book a call): the how-to video media/how-to-book.mp4 (about 70 s, 6.5 MB, captions, no sound, made by Claude from the real site with a pretend database) with poster media/how-to-book-poster.jpg; preload none so it only uses data when tapped.
6. Check a booking (#check): code + same phone shows business, package, status track (Received, Quoted, In progress, Live, or closed if cancelled) and my note.
7. Contact: 2 WhatsApp, 2 call, email. Floating WhatsApp button. Nav: Prices, Book, Contact.
8. Admin (Stage 3, me only): every booking in a list, change its status, add a short note the client can see.

## PRICE LIST (saved 2026-11-01; a starting point, adjust after the first 2 or 3 clients; not financial advice)
One-time setup, UGX:
- BASIC 600,000: their menu and logo, one language, staff page to change prices, QR code.
- STANDARD 1,000,000: BK level, plus two languages, specials and messages, celebrations, dollar switch.
- PREMIUM 1,500,000: plus photos of their items, their own web address, designed QR table cards, staff training.
- MONTHLY CARE (optional, recommended): 50,000 a month or 500,000 a year (changes on request, keeping it running, fixes).
Rules: first 3 clients 30% off in return for a review and permission to show their menu; 50% before starting, 50% when live, by mobile money, with a short written agreement; each client opens their own free Supabase and Cloudflare accounts in their name and I set them up. Selling line: "Change a price in 10 seconds from your phone. Never reprint a menu."

## BUILD PLAN (one stage at a time; a stage can take several version numbers; I test on my phone before the next)
- STAGE 1 PUBLIC SITE (done, live).
- STAGE 2 BOOKINGS (built in v6): Supabase bookings table, Book a call, booking codes, Check a booking.
- STAGE 3 ADMIN (built in v8): admin.html + admin.js. Log in, create PIN the first time, bookings with filters (Open, Received, Quoted, In progress, Live, Closed, All), each with name, phone, note, WhatsApp and Call buttons, status + client note (Save, PIN), Delete (PIN).
- LATER (ideas, not promised): a message to me when a booking arrives (for now the client taps "Send it to us on WhatsApp"), smaller floating WhatsApp button, one-page price sheet for WhatsApp, written client agreement template, own domain, WhatsApp catalog.

## FILES
- Site zip: index.html, styles.css, config.js (all wording and settings), app.js (fills the page), bookings.js (talks to Supabase), admin.html + admin.js (my admin page, not linked from the site, noindex), manifest.webmanifest (app name, colours, icons), sw.js (service worker: makes it installable; stores nothing, so updates show at once), icons/ folder (icon-192, icon-512, icon-maskable-512, apple-touch-icon), media/ folder (how-to video + poster). Folders must stay folders inside the zip.
- Database: simuworks-v6-database.sql (Stage 2, already run 2026-11-01) and simuworks-v8-database.sql (Stage 3: admin_settings table, admin doors). Only .sql files go into the Supabase SQL Editor; the prompt .md file never does.

## DATABASE RULES
- Table bookings: code (SW- + 5 letters/numbers, no 0 O 1 I L), package, name, business, phone (digits, 256...), note, status (received, quoted, in_progress, live, cancelled), client_note, created_at, updated_at.
- Row Level Security ON with no policies: the website can never read the table directly. Only two public doors: create_booking (adds one, returns the code) and check_booking (code + same phone; returns business, package, status, client_note, dates; never name, phone or note).
- Spam limits: 3 requests per phone per day, 30 per hour in total.
- Admin doors (logged-in user must be MY user id): admin_has_pin, admin_set_pin, admin_list_bookings (no PIN), admin_update_booking (PIN), admin_delete_booking (PIN). The public (anon) cannot call them.
- Free Supabase projects pause after about a week with no activity: if bookings stop working, open the Supabase dashboard and restore the project.
- Bookings hold names and phone numbers of real people: keep them private, collect only what is needed.

## OPEN QUESTIONS ONLY I CAN ANSWER (ask once, when it matters)
- Logo: simple text logo for now (current: teal phone shape + "Simu Works") or my own.

## RELATED PROJECTS (separate chats and prompt files; do not mix the code)
- BK menu: BK-menu-project-prompt (v5.5) - my own practice project, shown as the demo, and the template for every menu client. Tested as a guest (Secure Folder): no staff bar.
- FHG FX Signals: fhg-fx-signals-prompt (v508) - my trading app, under construction; Pages project fhgfx, never touch it from this project.

## VERSION LOG
- v1 (was v0.1), 2026-11-01: project started; name Simu Works; six-part site and build plan agreed.
- v2 (was v0.2): simuworks.pages.dev confirmed; contacts saved; WhatsApp Business categories chosen.
- v3 (was v0.3 + site v1): Stage 1 site built and LIVE. WhatsApp Business fully set up.
- v4 (was site v1.1): version shown in footer; BK shown as a demo; "Recommended" instead of "Most chosen"; whole-number versions like FHG.
- v5: FHG added to Work as "Our own app, in progress", no link.
- v6: Stage 2 bookings: bookings.js, Book a call, Check a booking, Book buttons on price cards, nav Prices/Book/Contact, database SQL. Separate Supabase account for Simu Works.
- v7: installable as an app: manifest, service worker, app icons (teal phone with menu lines, one highlighted). Database SQL unchanged (still simuworks-v6-database.sql).
- v7 tested 2026-11-01: installed on my phone; test booking SW-7WU7E made, WhatsApp message and Check a booking both worked (phone typed without 0 still matched).
- v8, 2026-11-02: Stage 3 admin page (/admin) + simuworks-v8-database.sql.
- v8 tested 2026-11-02: admin login, PIN, status changes and client note all work; client side shows the updates.
- Teaching video: Claude Doc "Simu Works teaching video" (script for recording my own voiced version) + simuworks-how-to-book.mp4 made by Claude (captions, no voice).
- v9, 2026-11-02: how-to video added to the website (#video section). No database change.
