# EBEC Challenge Zagreb 2018 website (archived edition)

Static archive of the EBEC Challenge Zagreb 2018 site: WordPress 4.9 with the Twenty Seventeen theme and Polylang, 8 pages in Croatian and the same 8 in English (under `en/`), published between 2018-01-09 and 2018-03-07. It was rebuilt from the backup a former maintainer left on the server in July 2018 (a MySQL data directory and the web root, found during the 2026 server retirement), not from a live site, and it is complete: every page the database listed as published is here. Every page is plain HTML; there is no database, no PHP and nothing to keep patched.

Home: **https://2018.ebec.best.hr/** (the site ran at **best.hr/ebec-challenge**)

- 16 published pages, 86 files, 4.9 MB
- Verified: every page and asset requested over HTTP, 98 URLs, **0 failures**, at the root and under a sub-path
- Verified: every page rendered in a browser, **0 broken images**
- Verified: after the deliberate changes below, the visible text and image list of every page match the 2018 install running in a container

## Looking at it locally

    python3 -m http.server 8000

Then open <http://127.0.0.1:8000/>. Any static file server works.

## How it was made

The 2018 database was started in a MySQL 5.7 container and the 2018 web root in a WordPress 4.9 container with PHP 7.2, the site's address rewritten to the container. The page list came from the database, not from what a crawler happened to find; the site was mirrored with `wget`, every page refetched raw, relinked to relative paths, and compared page by page with the container. Everything that would ask a server for something was stripped: feed, oEmbed, REST, RSD, shortlink and manifest links, the embed and comment-reply scripts, the comment forms. Google Analytics, Google Fonts, YouTube embeds and the other third-party loads the original pages made are kept. The tooling and the logs live in the migration notes alongside this archive.

## What deliberately differs from the 2018 pages

### Personal contact details

4 occurrences of one jury member's university e-mail address were replaced with **board@best.hr**. No phone numbers were on the site. This archive is public and outlives the students named in it.

### Repairs and limits

The Polylang language switch is two plain links (the flags), so both language trees work as static files; every page carries `hreflang` links to its counterpart.

## Editions

EBEC Zagreb editions on the web: 2018 (this repository), 2021 onward at [ebec.best.hr](https://ebec.best.hr/) ([EBEC-Web](https://github.com/BEST-Zagreb/EBEC-Web)); the EBEC Final 2022 in Zagreb at [ebecfinal.best.hr](https://ebecfinal.best.hr/).

## Hosting

Live at <https://2018.ebec.best.hr/>, served by Cloudflare Workers as static files straight from this repository. Every push to `main` is deployed by Workers Builds within a minute or two. Every page carries an archive notice and a `noindex` header, added at the edge by `banner.js`, so search engines keep sending people to the current site; the archived files themselves are untouched.

## Wayback Machine

This edition ran at <http://best.hr/ebec-challenge/>; the Internet Archive's calendar for it is <https://web.archive.org/web/*/best.hr/ebec-challenge*>, with captures from the period of this edition where the crawler reached them. This repository is the complete copy; the archive is a partial, independent second copy.

## Licence

The content, images and copy belong to BEST Zagreb. Third-party theme and plugin assets under `wp-content/` remain under their own licences and are included only because the pages need them to render as they originally did.
