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

## About this archive

When Google turned down the Google Code Project Hosting Service in
early 2016, the project files moved to a read-only archive served from
Google Cloud Storage. The originals are still there, but they are not
trivially CDN-cacheable, and the archive UI requires a few clicks per
file. This repo solves both problems by hosting every published bundle
of `vector-playing-cards` directly on GitHub, where any modern free
CDN (jsDelivr, Statically) can serve them globally.

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

Every published version of `vector-playing-cards` is preserved. Below
is the original Downloads tab from the project, reproduced verbatim:

| File | Summary | Status | Uploaded | Size |
|---|---|---|---|---|
| [PNG-cards-1.3.zip](https://code.google.com/archive/p/vector-playing-cards/downloads) | PNG Playing Cards Version 1.3 | **Featured** | Aug 18, 2012 | 4.6 MB |
| [SVG-cards-1.3.zip](https://code.google.com/archive/p/vector-playing-cards/downloads) | SVG Playing Cards Version 1.3 | **Featured** | Aug 18, 2012 | 3.57 MB |
| [SVG-cards-1.2.zip](https://code.google.com/archive/p/vector-playing-cards/downloads) | SVG Playing Cards Version 1.2 | Deprecated | Apr 24, 2011 | 3.46 MB |
| [PNG-cards-1.2.zip](https://code.google.com/archive/p/vector-playing-cards/downloads) | PNG Playing Cards Version 1.2 | Deprecated | Apr 24, 2011 | 4.57 MB |
| [PNG-cards-1.1.zip](https://code.google.com/archive/p/vector-playing-cards/downloads) | PNG Playing Cards Version 1.1 | Deprecated | Mar 9, 2011 | 4.52 MB |
| [SVG-cards-1.1.zip](https://code.google.com/archive/p/vector-playing-cards/downloads) | SVG Playing Cards Version 1.1 | Deprecated | Mar 9, 2011 | 3.36 MB |
| [PNG-cards.zip](https://code.google.com/archive/p/vector-playing-cards/downloads) | PNG Playing Cards Version 1.0 | Deprecated | Mar 4, 2011 | 1.79 MB |
| [SVG-cards.zip](https://code.google.com/archive/p/vector-playing-cards/downloads) | SVG Playing Cards Version 1.0 | Deprecated | Mar 4, 2011 | 176.94 KB |

Use **1.3** unless you specifically need an older variant. The 1.0 set
is much smaller because it predates the joker / face-card additions
introduced in 1.1.

## Repository layout

```
vector-playing-cards-archive/
  README.md                this file
  LICENSE                  LGPL-3.0 text
  NOTICE.md                source attribution
  assets/                  README banners
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
