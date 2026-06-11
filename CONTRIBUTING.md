# Contributing to vector-playing-cards-archive

This repo is an archive of Chris Aguilar's `vector-playing-cards` project, mirrored from the Google Code Archive for reliable CDN delivery. Contributions are narrow in scope by design.

## What belongs here

| Type | Welcome? |
|---|---|
| New upstream version (if Chris releases one) | Yes |
| Bug fix to a renamed file that breaks a CDN URL | Yes |
| Changes to the card artwork itself | No — this is a mirror, not a fork |
| New card designs unrelated to the upstream | No |
| Tooling, scripts, or web apps that consume the cards | No — keep those in your own repo |

## Adding a new upstream version

1. Download the zip from the [Google Code Archive](https://code.google.com/archive/p/vector-playing-cards/downloads) and verify its SHA-256 against the upstream listing.
2. Place the zip verbatim under `downloads/` and update `downloads/SHA256SUMS.txt`.
3. Extract the files and rename them to match the `card_<suit>_<rank>[_alt].<ext>` scheme used by all other versions (see the **File naming** table in `README.md`).
4. Place SVG files under `svg/<version>/` and PNG files under `png/<version>/`.
5. Verify at least one card loads from jsDelivr before opening a PR:
   ```sh
   curl -I "https://cdn.jsdelivr.net/gh/AbhiiGatty/vector-playing-cards-archive@main/svg/<version>/card_1_1.svg"
   # Expect: HTTP/2 200
   ```
   > jsDelivr may take a few minutes to index a newly pushed folder. If you get a 403, wait 5 minutes and retry before assuming a path error.
6. Update the **Versions** table and **Repository layout** section in `README.md`.

## Fixing a renamed file

If a file was committed with the wrong name (wrong suit/rank number, missing `_alt`, wrong extension), open a PR with the corrected filename and update `README.md` examples if they reference the old name.

## Pull request checklist

- [ ] New zip is in `downloads/` and its SHA-256 is added to `SHA256SUMS.txt`
- [ ] Files follow `card_<suit>_<rank>[_alt].<ext>` naming
- [ ] CDN smoke-test passes (`curl -I ...` returns 200)
- [ ] `README.md` version table updated
- [ ] No changes to card artwork content

## Commit style

Short imperative subject line, 72 chars max:

```
add: svg/1.4 and png/1.4 from upstream v1.4 release
fix: rename card_3_1_alt in svg/1.1 (was card_3_0_alt)
docs: add v1.4 to README versions table
```

## License

By contributing you agree that your changes are licensed under the same [LGPL-3.0](LICENSE) terms as the rest of the repository.
