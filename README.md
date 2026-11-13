# Email Manager for CS-Cart

**🛑 PREMIUM ADD-ON: This repository does not contain the open-source code. It serves as the official listing and documentation page for the WebGraphiq premium add-on.**

**Email Manager** is a B2B customer email exporter and list-quality add-on for CS-Cart and Multi-Vendor. It collects and exports addresses for email marketing, can sync them to your own **Listmonk** (Mailchimp replacement), and can filter dead or risky addresses before you mail an old customer list — without deleting shop users.

## [🛒 Buy & View Live Demo](https://www.webgraphiq.com/email-manager-v4.html)

One-time license. The current price and the live demo are on the product page.

## Why store owners use it

- Export contacts from orders, customers, subscribers, or selected mailing lists to CSV/TXT.
- Push the same filtered set to **Listmonk** (bulk import), or write a file and Listmonk together.
- Live sync: new customer accounts and contact-form emails can upsert into Listmonk when sync is enabled.
- **List quality** pipeline drops invalid domains before a campaign — protects sender reputation.
- Free local checks first (syntax, typos, disposable domains, MX/DNS); optional mailbox API in daily chunks.
- Shop signals on export: only active customers, must have logged in, must have an order in the last N years.
- Customer accounts are **never** deleted by this add-on.
- No CS-Cart core file edits.

## Export and files

- **Marketing → Email Manager**: choose period, source, format (CSV/TXT), headers, separator, enclosure, date format, and extra fields.
- Files land in `var/email_manager/` and are managed on the **Export files** tab (download / delete).
- Totals show distinct emails in orders, customers, and subscribers.
- Same-day from/to dates include the whole calendar day.

## Listmonk sync

- Enable under **Add-ons → Wg Email Manager → Listmonk**: base URL (no `/api/…`), API user, token, and list dropdown (save credentials first so lists load).
- Pre-confirm is on by default so Listmonk does not send a second opt-in when the shop already collected consent.
- Sync new customers and/or contact-form emails; profile-update sync stays off unless you enable it.
- When Listmonk is configured, native Mailchimp (CS-Cart Email marketing) is left unused. If Listmonk is down, local subscribers and file export still work.

## List quality

Filtering runs in layers (SMTP probing from the shop is **not** used):

1. Normalise and unique the address.
2. Syntax and obvious typos.
3. Disposable domains → invalid.
4. Role addresses (`info@`, `admin@`, …) → risky (optional skip).
5. MX / DNS — no exchanger or null MX → invalid.
6. Optional shop signals on export.
7. Optional mailbox API for remaining unknowns (daily quota + batch size).
8. Listmonk hard-bounce / blocklist cache → skip on the next export.

On Marketing → Email Manager you set skip-invalid (default on), skip-risky, skip-unverified, and shop-signal checkboxes. Each export reports kept vs skipped counts.

## Mailbox verification API (optional)

After local checks, leftover addresses can go to a third-party API (DPA with that vendor required):

- Free / primary providers (e.g. AbstractAPI, Mailboxlayer) with a daily limit.
- Optional paid fallback (Kickbox, ZeroBounce, NeverBounce, Emailable, …) — off by default so a large list cannot spend paid credits by accident.
- Cron examples on the Email validation tab (password + PHP CLI / wget / curl). Suggested: hourly or a few times per day.

## Requirements

- CS-Cart or Multi-Vendor **4.12.1** or newer, including **4.21**
- PHP **8.3** or a current 8.x release used by that shop
- Optional: self-hosted Listmonk; optional mailbox verification API keys

## This repository

<p align="center">
  <a href="https://www.webgraphiq.com/email-manager-v4.html">
    <img alt="Buy and view the live demo" src="https://img.shields.io/badge/CS--Cart-Buy%20%26%20View%20Live%20Demo-28a745?style=for-the-badge&labelColor=1A365D">
  </a>
</p>

<p align="center"><strong>One-time license · export, Listmonk sync, list quality</strong></p>

This is the public product listing. The add-on package, license checks, and source files are not published here. After purchase, the package is readable PHP under the WebGraphiq commercial license, installed from your WebGraphiq account.

Support: [webgraphiq.com](https://www.webgraphiq.com) · webgraphiq@gmail.com

© WebGraphiq. All rights reserved. [License](https://www.webgraphiq.com/license.html)

## Other Premium CS-Cart Add-ons by WebGraphiq

More CS-Cart and Multi-Vendor add-ons are listed on the [WebGraphiq GitHub profile](https://github.com/webgraphiq).
