
# HTML Tags extension for MediaWiki.

This extension defines a tag function, `<htmltag>`, that allows users to place
HTML tags on the page that may not be otherwise allowed by the MediaWiki
parser.  This repository contains minor additions to that original extension,
needed for use in the Lurch project, [as described below](#lurch).

For more information,
[see the extension homepage](https://www.mediawiki.org/wiki/Extension:HTML_Tags).

## Overview

`<htmltag>` can only display tags and attributes that are allowed for that wiki.
Tags and attributes are allowed through the use of the global variable
`$wgHTMLTagsAttributes` in `LocalSetting.php`. To allow the use of the `<a>` tag,
for instance, with the attributes `href` and `class`, you would add the
following to LocalSettings.php:

```php
$wgHTMLTagsAttributes['a'] = array( 'href', 'class' );
```

A user could then display an `<a>` tag on the wiki, with those attributes, with
text like the following:

```html
<htmltag tagname="a" href="http://example.com" class="link">See here</htmltag>
```

Calling `<htmltag>` with a tag name that is not allowed will result in an error
message; calling it with an attribute that is not allowed will simply lead to
the attribute being ignored.

## License

HTML Tags is available under the GNU Public License.
 
## Authors

HTML Tags was written by Yaron Koren.

The small extensions in this repository were added by Nathan Carter.

## Lurch

[The Lurch Project](https://github.com/lurchmath/lurch) will run on a web
server that also runs an instance of MediaWiki.  The main Lurch application
will be able to export files to the wiki as pages, as a means of publishing
them.  It will also be able to import pages from the wiki for editing.

To facilitate this, a wide variety of tag names needed to be supported, and
HTMLTags was nearly perfect.  It needed only the small tweaks recorded in the
commits of this fork for it to suit the needs of the Lurch project.

