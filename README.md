<div align="center">

<img src="assets/google-code-archive.svg" width="540" alt="Google Code Archive" />

# vector-playing-cards-archive

A complete mirror of every published version of Chris Aguilar's
`vector-playing-cards` project, originally hosted on Google Code.
Both SVG and PNG sets, all four versions, organized for direct CDN
delivery via jsDelivr.

[![License](https://img.shields.io/badge/License-LGPL--3.0-007ec6.svg?style=flat-square)](LICENSE)
[![Source](https://img.shields.io/badge/Source-Google%20Code%20Archive-4285f4.svg?style=flat-square)](https://code.google.com/archive/p/vector-playing-cards/)
[![Versions](https://img.shields.io/badge/Versions-1.0%E2%80%931.3-9b59b6.svg?style=flat-square)](#versions)
[![SVG](https://img.shields.io/badge/SVG-67%20files-e74c3c.svg?style=flat-square)](svg/1.3)
[![PNG](https://img.shields.io/badge/PNG-67%20files-2ecc71.svg?style=flat-square)](png/1.3)
[![CDN](https://img.shields.io/badge/CDN-jsDelivr-orange.svg?style=flat-square)](https://www.jsdelivr.com/)

</div>

---

## Quick start — copy and paste

Pick a card, any card. Replace `<suit>` (1–4) and `<rank>` (1–13) with the values you want, or use the random-card JS snippet below.

```html
<!-- Ace of spades, SVG -->
<img src="https://cdn.jsdelivr.net/gh/AbhiiGatty/vector-playing-cards-archive@main/svg/1.3/card_3_1.svg"
     width="80" height="116" alt="Ace of spades" />

<!-- 7 of hearts, SVG -->
<img src="https://cdn.jsdelivr.net/gh/AbhiiGatty/vector-playing-cards-archive@main/svg/1.3/card_1_7.svg"
     width="80" height="116" alt="7 of hearts" />

<!-- King of clubs, PNG -->
<img src="https://cdn.jsdelivr.net/gh/AbhiiGatty/vector-playing-cards-archive@main/png/1.3/card_2_13.png"
     width="80" height="116" alt="King of clubs" />
```

**Random card (JavaScript):**

```js
const CDN = "https://cdn.jsdelivr.net/gh/AbhiiGatty/vector-playing-cards-archive@main/svg/1.3";
const suit = 1 + Math.floor(Math.random() * 4);   // 1=Hearts 2=Clubs 3=Spades 4=Diamonds
const rank = 1 + Math.floor(Math.random() * 13);  // 1=Ace 2-10 11=Jack 12=Queen 13=King
const url  = `${CDN}/card_${suit}_${rank}.svg`;
```

**Sanity-check a path before shipping:**

```sh
curl -I "https://cdn.jsdelivr.net/gh/AbhiiGatty/vector-playing-cards-archive@main/svg/1.3/card_1_1.svg"
# Expect: HTTP/2 200
# A 403 means the path or filename is wrong — check suit/rank numbers and the version folder.
```

---

## AI agent context

> This section is written for Claude, Copilot, and other coding assistants so they can integrate this repo correctly without guessing.

### CDN URL template

```
https://cdn.jsdelivr.net/gh/AbhiiGatty/vector-playing-cards-archive@main/<format>/<version>/card_<suit>_<rank>[_alt].<ext>
```

| Placeholder | Valid values | Notes |
|---|---|---|
| `<format>` | `svg` or `png` | SVG recommended for web; scales to any size |
| `<version>` | `1.0`, `1.1`, `1.2`, `1.3` | **Use `1.3`** — it is the featured version with the best face-card art |
| `<suit>` | `1` `2` `3` `4` (or `5` for jokers) | 1=Hearts, 2=Clubs, 3=Spades, 4=Diamonds, 5=Joker |
| `<rank>` | `1`–`13` (or `1`/`2` when suit=5) | 1=Ace, 11=Jack, 12=Queen, 13=King; suit=5 rank=1=Red joker, rank=2=Black joker |
| `[_alt]` | optional suffix | Alternate face-card art (available in 1.1+) — e.g., `card_3_11_alt.svg` |
| `<ext>` | `.svg` or `.png` | Must match `<format>` |

### What exists vs. what does not

- `svg/1.0/` — 54 files, no `_alt` variants, no jokers in this set (suits 1–4, ranks 1–13 only)
- `svg/1.1/`, `svg/1.2/`, `svg/1.3/` — 67 files each, includes `_alt` face cards and jokers (suit=5, rank=1–2)
- Same structure mirrors under `png/1.0/` through `png/1.3/`
- There is no `svg/1.4/` or higher — do not reference versions that are not listed here

### Rules for code generation

1. **Always use `1.3`** unless the project has an explicit constraint requiring an older version.
2. **File naming is numeric only** — never use suit names (`spades`, `hearts`) or rank names (`ace`, `king`) in the URL; they will 404.
3. **Verify with `curl -I`** before committing a CDN_BASE constant. A 403 from jsDelivr means the folder path is wrong (not a permissions issue — this repo is public).
4. **Do not generate `_alt` URLs** unless the consuming code explicitly selects alternate art.
5. **Do not use suit=5 (jokers)** unless the application specifically deals joker cards.
6. **Pin to a commit SHA for production** if stability matters: replace `@main` with `@<sha>` to prevent any future commit from changing cached files.

### Known projects using this repo

| Project | Version | Notes |
|---|---|---|
| [abhiigatty.com/tools/otp](https://abhiigatty.com/tools/otp) | `svg/1.3` | Suits 1–4, ranks 1–13, no jokers/alt |

---


## About this archive

When Google turned down the Google Code Project Hosting Service in
early 2016, the project files moved to a read-only archive served from
Google Cloud Storage. The originals are still there, but they are not
trivially CDN-cacheable, and the archive UI requires a few clicks per
file. This repo solves both problems by hosting every published bundle
of `vector-playing-cards` directly on GitHub, where any modern free
CDN (jsDelivr, Statically) can serve them globally.

The original upstream zip archives are mirrored verbatim under
[`downloads/`](downloads), so the repo stands on its own — no
dependency on the Google Code archive remaining online.

## About Google Code Archive

> Welcome! The Google Code Archive contains the data found on the
> Google Code Project Hosting Service, which was turned down in early
> 2016.
>
> This archive contains over 1.4 million projects, 1.5 million
> downloads, and 12.6 million issues. You can learn more about the data
> served from Google Cloud Storage.
>
> Google Code offered open-source project hosting on other domains
> besides just code.google.com, too: Google Code, Eclipselabs, and
> Apache Extras.

## Versions

Every published version of `vector-playing-cards` is preserved. The
original upstream zip bundles are mirrored verbatim under
[`downloads/`](downloads) so this repo stands on its own — nothing
here depends on the Google Code archive remaining online. SHA-256
checksums are in [`downloads/SHA256SUMS.txt`](downloads/SHA256SUMS.txt).

| File | Summary | Status | Uploaded | Size |
|---|---|---|---|---|
| [PNG-cards-1.3.zip](downloads/PNG-cards-1.3.zip) | PNG Playing Cards Version 1.3 | **Featured** | Aug 18, 2012 | 4.6 MB |
| [SVG-cards-1.3.zip](downloads/SVG-cards-1.3.zip) | SVG Playing Cards Version 1.3 | **Featured** | Aug 18, 2012 | 3.57 MB |
| [SVG-cards-1.2.zip](downloads/SVG-cards-1.2.zip) | SVG Playing Cards Version 1.2 | Deprecated | Apr 24, 2011 | 3.46 MB |
| [PNG-cards-1.2.zip](downloads/PNG-cards-1.2.zip) | PNG Playing Cards Version 1.2 | Deprecated | Apr 24, 2011 | 4.57 MB |
| [PNG-cards-1.1.zip](downloads/PNG-cards-1.1.zip) | PNG Playing Cards Version 1.1 | Deprecated | Mar 9, 2011 | 4.52 MB |
| [SVG-cards-1.1.zip](downloads/SVG-cards-1.1.zip) | SVG Playing Cards Version 1.1 | Deprecated | Mar 9, 2011 | 3.36 MB |
| [PNG-cards.zip](downloads/PNG-cards.zip) | PNG Playing Cards Version 1.0 | Deprecated | Mar 4, 2011 | 1.79 MB |
| [SVG-cards.zip](downloads/SVG-cards.zip) | SVG Playing Cards Version 1.0 | Deprecated | Mar 4, 2011 | 176.94 KB |

The [original Google Code downloads page](https://code.google.com/archive/p/vector-playing-cards/downloads)
remains the upstream source of record.

Use **1.3** unless you specifically need an older variant. The 1.0 set
is much smaller because it predates the joker / face-card additions
introduced in 1.1.

### Download and verify with `curl`

Grab one bundle plus its checksum and verify:

```sh
BASE="https://raw.githubusercontent.com/AbhiiGatty/vector-playing-cards-archive/main/downloads"
curl -sLO "$BASE/SVG-cards-1.3.zip"
curl -sLO "$BASE/SHA256SUMS.txt"
sha256sum --ignore-missing -c SHA256SUMS.txt
# SVG-cards-1.3.zip: OK
```

Or fetch every bundle and verify them all at once:

```sh
BASE="https://raw.githubusercontent.com/AbhiiGatty/vector-playing-cards-archive/main/downloads"
curl -sLO "$BASE/SHA256SUMS.txt"
awk '{print $2}' SHA256SUMS.txt | sed 's/^\*//' | \
    xargs -I{} curl -sLO "$BASE/{}"
sha256sum -c SHA256SUMS.txt
```

On macOS, replace `sha256sum -c` with `shasum -a 256 -c` (both ship
with the OS). On Windows PowerShell, use
`Get-FileHash <file> -Algorithm SHA256` and compare to the matching
line in `SHA256SUMS.txt`.

## Repository layout

```
vector-playing-cards-archive/
  README.md                this file
  LICENSE                  LGPL-3.0 text
  NOTICE.md                source attribution
  assets/                  README banners
  downloads/               verbatim upstream zip bundles + SHA256SUMS.txt
  svg/
    1.0/   54 files
    1.1/   67 files
    1.2/   67 files
    1.3/   67 files        <- featured
  png/
    1.0/   54 files
    1.1/   67 files
    1.2/   67 files
    1.3/   67 files        <- featured
```

Files have been **renamed** from the upstream `<rank>_of_<suit>.<ext>`
naming to a strictly numeric scheme so URLs can be generated
programmatically with no string lookup table:

```
card_<suit>_<rank>[_alt].<ext>
```

| Suit | Number |
|---|---|
| Hearts   | 1 |
| Clubs    | 2 |
| Spades   | 3 |
| Diamonds | 4 |
| Joker    | 5 |

| Rank | Number |
|---|---|
| Ace        | 1 |
| 2 to 10    | 2 to 10 |
| Jack       | 11 |
| Queen      | 12 |
| King       | 13 |
| Joker      | 1 = red, 2 = black (with suit = 5) |

The `_alt` suffix marks the secondary face-card art that ships with
the upstream pack (e.g., `card_3_11_alt.svg` is the alternate jack of
spades). The "second ace of spades" the original deck includes lives
at `card_3_1_alt`.

A few examples:

- `card_1_1.svg` — ace of hearts
- `card_2_10.svg` — 10 of clubs
- `card_3_13.svg` — king of spades
- `card_4_5.svg` — 5 of diamonds
- `card_5_1.svg` — red joker
- `card_5_2.svg` — black joker
- `card_2_11_alt.svg` — alternate jack of clubs

The point of the numeric scheme: an OTP / dice / random-card consumer
just does `\`card_${1+Math.floor(Math.random()*4)}_${1+Math.floor(Math.random()*13)}.svg\``
and it is a valid URL — no rank/suit dictionary required.

## Use via jsDelivr

jsDelivr serves any file from any public GitHub repo. The URL pattern
is:

```
https://cdn.jsdelivr.net/gh/AbhiiGatty/vector-playing-cards-archive@main/<path>
```

A few examples:

```html
<!-- 7 of hearts, SVG, latest version -->
<img
    src="https://cdn.jsdelivr.net/gh/AbhiiGatty/vector-playing-cards-archive@main/svg/1.3/card_1_7.svg"
    width="80" height="116" alt="7 of hearts"
/>

<!-- King of spades, PNG -->
<img
    src="https://cdn.jsdelivr.net/gh/AbhiiGatty/vector-playing-cards-archive@main/png/1.3/card_3_13.png"
    alt="King of spades"
/>

<!-- Pin to a specific commit (recommended for production) -->
<img
    src="https://cdn.jsdelivr.net/gh/AbhiiGatty/vector-playing-cards-archive@v1.0.0/svg/1.3/card_2_1.svg"
    alt="Ace of clubs"
/>
```

A tiny JS snippet for picking a random card:

```js
const suit = 1 + Math.floor(Math.random() * 4);   // 1..4
const rank = 1 + Math.floor(Math.random() * 13);  // 1..13
const url =
    `https://cdn.jsdelivr.net/gh/AbhiiGatty/vector-playing-cards-archive` +
    `@main/svg/1.3/card_${suit}_${rank}.svg`;
```

For more aggressive caching, jsDelivr lets you append `@latest` (always
HEAD) or `@SHA` (pin to a specific commit) instead of `@main`.

## License

The card art is the original work of **Chris Aguilar** and is
distributed under the **GNU Lesser General Public License v3.0**. See
[LICENSE](LICENSE) for the full text and [NOTICE.md](NOTICE.md) for
attribution details.

If you redistribute the cards (in any form), please:

1. Credit Chris Aguilar.
2. Link back to the original Google Code archive page.
3. Keep your distribution under LGPL-3.0 or a compatible license.

## Why this exists

Built as the asset backbone for the [/tools/otp](https://abhiigatty.com/tools/otp)
card-deck OTP generator on
[abhiigatty.com](https://abhiigatty.com), but it is general-purpose:
any project that wants free, reasonably-drawn vector playing cards can
point an `<img src>` at jsDelivr and be done.
