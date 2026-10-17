# Social Minishop Automation — Viral Sales ($0 Marketing)

## Cel
Zautomatyzować pozyskiwanie zamówień i konwersję z treści social media przy minimalnym budżecie, wykorzystując automatyczne przepływy: generowanie contentu, publikacja, direct response i integracja z Telegram Shop Bot.

## Formaty contentu
- Short-form video: 9:16 TikTok/IG Reels/YouTube Shorts, 15–45s, tempo 60–120 BPM bass music.
- Assets: 3D renders, mockupy, GIFs, produktowe close-ups, unboxingi.
- CTA: „DROP” or „PREORDER” as comment trigger; short link in bio to Telegram bot.

## Automation architecture
1. Content generation pipeline
   - Inputs: product images, 3D renders, copy templates
   - Tools: FFmpeg for templating, headless browser rendering for captions, simple AI-based caption variations (open-source LLM or templating)
2. Scheduler & Publisher
   - Scheduler triggers uploads to social platforms via their APIs (or to a human operator via a publishing queue when API access is limited)
3. Comment listener & DM flow
   - Monitor comments for trigger words ("DROP", "PREORDER")
   - Upon trigger: platform sends DM with unique purchase link (shortened) to Telegram Shop or mini-checkout flow
4. Telegram Shop Bot
   - Handles checkout (simple invoice link or payment gateway), order confirmation, and sends activation instructions (NFC/QR claim)

## Purchase flow (3 clicks)
1. User comments "DROP" under post
2. Automation sends DM with one-click link to Telegram Shop
3. In Telegram: bot shows product, collects minimal info (wallet or email) and provides payment links or invoice

## Anti-abuse and rate limiting
- Limit number of DMs per user per drop to 1
- Use short-lived unique links tied to user ID or phone handle
- Enforce CAPTCHA / human verification in cases of suspicious behavior

## Metrics and growth hacks
- Track conversion rate from comment -> DM -> purchase
- A/B test thumbnail + first 3 seconds of video
- Use scarcity messaging and countdowns for drops

## Operational notes
- Keep legal compliance: ensure promotional messages comply with platform rules
- Provide clear instructions about activation (NFC/QR) and delivery times for pre-orders

## Minimal tech stack (open-source friendly)
- FFmpeg, Node.js or Python automation scripts, Redis for rate-limiting, simple webhook receiver
- Telegram Bot built on python-telegram-bot or node-telegram-bot-api
