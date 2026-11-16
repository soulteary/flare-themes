# Flare themes

Themes for [Flare](https://github.com/soulteary/flare), each as one file
that an instance can install.

The application links to this repository from its theme page and does
nothing else with it: it does not read the index, list themes or look for
newer versions. A theme gets onto an instance because its administrator
puts it there.

## What is here

| Path | Content |
| --- | --- |
| `themes/` | The themes: `<name>.yml` for a theme that is one file, `<name>.zip` for a theme with a stylesheet, images, fonts or templates |
| `index.json` | The list of the themes with the size and the SHA-256 of each file, written by the tool that checks them |
| `CONTRIBUTING.md` | How a theme is proposed and what it has to meet |

Themes need a release of Flare after 0.7.0 where they bring templates or
are installed from an address. A theme file names the first release it
works with under `requires`, and the index repeats it.

## Installing a theme

1. Pick a theme from `index.json`. Its entry names the file, its size and
   its SHA-256.
2. On the theme page of the instance, either upload the file, or enter its
   address under **Install a theme from an address**:

   ```text
   https://raw.githubusercontent.com/soulteary/flare-themes/main/themes/harbor.zip
   ```

3. The theme page shows the SHA-256 of what it fetched before it installs
   anything. Compare it with the one in `index.json`.
4. A theme with templates is shown with them only after templates are
   allowed for the site and those of the theme are confirmed on the theme
   page.

Being listed says that a theme met the rules of this repository when it was
added. It does not say more than that. A stylesheet can restyle and hide
anything on a page, and a template can write any text and any link, so look
at what a theme brings before using it on an instance other people visit.
The documentation of Flare describes
[what a stylesheet can do](https://github.com/soulteary/flare/blob/main/docs/theme-stylesheets.md)
and
[what the check of a template does not cover](https://github.com/soulteary/flare/blob/main/docs/theme-templates.md#what-the-check-does-not-cover).

## How the themes are checked

Every change runs `tools/themecheck` from the source of Flare on every file
in `themes/`, and writes the index again to compare it with the stored one.
The rules and the format of the index are described in
[the theme repository](https://github.com/soulteary/flare/blob/main/docs/theme-repository.md).

The tool is built from the commit of Flare that
`.github/workflows/check.yml` names, and a theme is checked as that source
reads it. To run the same check on a copy of this repository, with the
source of Flare beside it:

```bash
go -C ../flare run ./tools/themecheck "$PWD"/themes/*
```

```bash
go -C ../flare run ./tools/themecheck -index "$PWD"/themes/* | diff -u index.json -
```

The tool does not replace reading a theme. What a person looks at before a
theme is listed is in `CONTRIBUTING.md`.

## Licenses

Each theme has the license its theme file names, and an archive carries the
text of that license. The other files of this repository are under the
Apache License 2.0; see `LICENSE`.
