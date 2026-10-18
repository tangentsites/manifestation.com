# tangentsites/manifestation.com

**Repo:** https://github.com/tangentsites/manifestation.com
**Imported:** 2020-12-05 (single commit "import of manifestation.com (circa 1999)")
**What it is:** Archive import of Michal's late-90s self-improvement site **manifestation.com** —
"manifest station: change your mind". Tagline: "Self-improvement news, articles, books, and software."
**Stack:** PHP3 (run as php5-script per `.htaccess`), Perl 5 CGI, MySQL, a Perl
DB_File search index. Inert snapshot — no commits since import.

## Sitemap

### Root pages
- `index.php3` — Home page ("manifest station: change your mind"). Layout: about-the-site
  table ("I believe people can change in an instant..."), guru artwork sidebar
  (`images/art/guru_3d.jpg`), search box, "interact" links (submit a story, mindlist
  mailing list, alt.psychology.nlp), neurotoys links, and a random quote pulled from
  the `msdc_quote` MySQL table.
- `archive.php3` — Weblog archive: SQL-driven View over `mas_content`/`hive_content`
  (the "hive" CMS), newest first, page size 1000.
- `msdcrdf.php3` — RDF 0.9 feed ("manifest station") of the same hive content.
- `search.php3` + `search.pl` — Site search. PHP page shells out to a Perl 5 script
  that queries a DB_File B-tree index (`/usr/www/users/sabren/idx/msdc.idx`).
- `404.html`, `404.php3` — 404 pages (PHP one includes search form).
- `talkback` — Comment router; parses contentID from the URL and includes
  `hive/talkback.php3` (lives outside this repo).
- `station.css` — Site stylesheet.
- `test.bin` — gzip of `mmm.el` (Emacs Lisp file, dated 1999-05-14) — looks like an
  accidental leftover, likely his Emacs MMM-mode config.

### `/neurotoys/` — interactive toys
- `eliza.php3` — **Eliza, Computer Therapist** (classic Eliza chatbot).
- `bitcoin.js` — BitcoinPlus browser-miner embed; miner ID is a rot13-obfuscated
  email (`zvpuny.jnyynpr@tznvy.pbz` = michal.wallace@gmail.com) — his public email,
  not a secret.
- `.htaccess` also redirects several no-longer-present neurotoys pages
  (`calibrate`, `swish`, `nlpvac`, `lucid`/`vrlucid`, `nlpintro`, `eprime.pl`,
  `learnfast/`, `nlpdreams`) to `/resources/`.

### `/resources/` — knowledge base
- `index.php3` — Resources home: "Local Favorites" list (neurotoys, NLP/hypnosis
  articles, dreamwork articles), resource category tree (marked "coming soon..").
- `viewnode.php3` — Knowledge-base node viewer (SQL-driven tree).

### `.htaccess` redirects (archaeology of the full site)
Old sections referenced but not present in the import: `/buddha/` email newsletter
(21 issues, `htb00001`–`htb00021`), `/store` bookstore, `/projects/`, `/source`
(ftp), `/metalog`, plus redirects to sabren.com (`/rants`, `/sabren`, `/specs`).

### Missing / external dependencies
The app code references `../lib/station.inc`, `lib/view.inc`, `hive/talkback.php3`,
and the `msdc_*`/`hive_*` MySQL tables — none of that shared library code is in
this repo, so the site is not runnable from the import alone.

## Secrets scan (2026-10-18)
**No secrets found.** Searched for passwords, API keys, tokens, DB credentials,
connection strings, AWS/SMTP creds, `.env`/config files — none present. The only
obfuscated string is the rot13 email in `neurotoys/bitcoin.js` (public address,
not a credential). No scrub PR was needed. Note: `git log` shows only the import
commit, so history contains nothing new.
