# ilib-loctool-ghfm

Ilib loctool plugin to parse and localize github-flavored markdown

## Release Notes

### 1.4.0

- Add support for localizing links and link references.

By default, URLs are not localizable, as the majority are the same
in all languages. Sometimes, however you want to be able to give a
different URL for each locale. With this new features, you can turn
on link localization.

To localize a link in the text, put a localize-links directive around
it, which is an lint-style HTML comment. Example:

```markdown
There are
<!-- i18n-enable localize-links -->
[fifty](http://www.example.com/)
<!-- i18n-disable localize-links -->
of them for sale.
```

The text "fifty" is localized along with the rest of the sentence in the
string:

```
There are <c0>fifty</c0> of them for sale.
```

Note the c0 tags denote where the link goes. The directives, being HTML
comments, are not included in the string to translate.

The URL itself appears as a separate string to translate.

Localizing a link reference is very similar. Surround the reference
definition with a localize-links directive:

```markdown
There are [fifty][url] of them for sale.

<!-- i18n-enable localize-links -->
[url]: http://www.example.com/ "link title"
<!-- i18n-disable localize-links -->
```

The link title for link reference definitions is included as a separate string
to translate.

### 1.3.0

- The plugin now adds a translator comment/note for inline code so that the
  translator can know what the text of the self-closing components is.

### 1.2.6

- Add support for shortcut and full link references
    - Shortcut references are converted back to full so that the title of the
      reference can be translated to something different than the [possibly]
      English label of the shortcut.

### 1.2.5

- Handle valueless HTML attributes properly

### 1.2.4

- The previous fix where HTML comments were not recognized and skipped properly 
was only fixed for the parsing side of this plugin. Now it is fixed for the
localization side as well.

### 1.2.3

- Fixed a bug where HTML comments were not recognized and skipped properly 
if there was whitespace/indentation before them in the source file.

### 1.2.2

- Fixed reference link support. If there is text in a reference link, then it will
be included in the text to localize.

