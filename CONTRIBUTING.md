# Proposing a theme

A theme is proposed as a pull request that adds or changes one file in
`themes/` and the entry for it in `index.json`.

## Before the pull request

1. Go through the list
   [before passing a theme on](https://github.com/soulteary/flare/blob/main/docs/theme-template-guide.md#before-passing-a-theme-on)
   in the documentation of Flare. It holds for a theme without templates as
   well.
2. Take the file from the instance the theme was made on: a theme that is
   one file as `<name>.yml`, a theme that is a directory as the archive the
   theme page hands out, `<name>.zip`. An archive made by hand is accepted
   too, if it holds the files of the theme and nothing else.
3. Put the text of the license into an archive as `LICENSE.txt` beside
   `theme.yml`, and the licenses of fonts and images it brings likewise.
4. Run the tool and correct what it names; see the
   [README](README.md#how-the-themes-are-checked) for the command.
5. Write the index again with `-index` and commit it with the theme.

## What the pull request holds

- The file in `themes/`. One theme per pull request.
- `index.json`, written by the tool. It is not edited by hand: the check
  writes it again and fails where the two differ.
- In the description: what the theme looks like, a screenshot of the home
  page in the light and the dark mode, and for a theme with templates what
  each template changes.

A screenshot belongs in the description of the pull request, not in the
archive and not in `themes/`: an archive with an entry that is not a file
of a theme is refused.

## What a theme has to meet

The tool checks these, and the check of the pull request fails without
them:

| Rule | What it means |
| --- | --- |
| The application takes it in | The theme passes every check of an upload and is in use afterwards, with each of its templates accepted |
| It is written for this format | No key, token or layout option the application does not use |
| An archive holds the theme and nothing else | No entry an import would leave out |
| It is described | The theme file gives a `name`, a `version` and an `author` |
| It has a license that lets it be passed on | `license` is one of `0BSD`, `Apache-2.0`, `BSD-2-Clause`, `BSD-3-Clause`, `CC-BY-4.0`, `CC0-1.0`, `ISC`, `MIT`, `Unlicense` |
| It is installed by itself | It stands on its own or is based on a theme that comes with Flare, not on another theme of this repository |
| Its name is a theme name | Lower-case letters, digits and single hyphens, up to 32 characters, and not the name of a theme that comes with Flare |
| It is listed once | Not both `<name>.yml` and `<name>.zip` |

A person looks at these before a theme is merged:

| Rule | What is looked at |
| --- | --- |
| It presents and does nothing else | The theme changes how the pages look. It does not hide the settings or the help, and it does not present content of its own as part of the site |
| Templates are read | Every template is read, and read again when it changes. A template can write any text and any link |
| The focus stays visible | The keyboard reaches every link and the search field, and it can be seen where the focus is |
| The name and the images are the author's to give | No name or image that belongs to someone else |
| The license is true | The author has the right to give the license the theme file names, also for the fonts and images the theme brings |

## Changing a theme

A change to a theme is a pull request like the first one. Raise `version`
in the theme file, so that the index tells the two files apart by more than
their SHA-256. The address of the file stays the same; an instance that has
the theme keeps what it installed and is not told of the change.

## Removing a theme

A theme is removed when it no longer meets the rules, or when its author
asks for it. Removing it here does not remove it from any instance.
