---
layout: page
title: Markdown quick reference
order: 10
permalink: markdown
family: syntax
---

Both the [Octopus blog](https://github.com/OctopusDeploy/blog) and the [Octopus documentation](https://github.com/OctopusDeploy/docs) are written in Markdown and rendered using [markdig](https://github.com/lunet-io/markdig). Markdig supports [GitHub Flavored Markdown](https://help.github.com/articles/github-flavored-markdown) as well as some extra syntax. 

- [Filenames](#filenames)
- [Files and directories](#files-and-directories)
- [YAML headers](#yaml-headers)
  - [YAML header (blog)](#yaml-header-blog)
  - [YAML header (docs)](#yaml-header-docs)
- [Headings](#headings)
- [Formatting text](#formatting-text)
- [Images](#images)
- [Lists](#lists)
- [Tables](#tables)
- [Links](#links)
- [Documentation](#documentation)
- [Blog](#blog)
  - [Anchor links](#anchor-links)
- [Navigation paths](#navigation-paths)
- [Code samples](#code-samples)
- [Call-outs](#call-outs)
- [Reuse text](#reuse-text)
  - [Referencing Docker images](#referencing-docker-images)
    - [Example 1 - with tags](#example-1---with-tags)
    - [Example 2 - without tags](#example-2---without-tags)
- [Link to the Octopus Guides](#link-to-the-octopus-guides)
- [Redirects](#redirects)
- [Docs redirects](#docs-redirects)

## Filenames

Markdown filenames are lowercase and end with `.md` or `.mdx` for pages with includes. Use hyphens to separate words:

- `installation.md`
- `backup-and-restore.md`

## Files and directories

Directories must have an index file: `index.md`.

- directory/index.md
- directory/another-file.md

## YAML headers

The Markdown files in the blog and docs have a YAML header:

### YAML header (blog)

```md
---
title: Runbooks best practices <!-- post title -->
description: This post provides a step by step template you can use to generate high quality runbooks in Octopus
author: email@octopus.com <!-- use your email address -->
visibility: public <!-- options are public or private -->
published: 2020-03-09 <!-- The date the post will be published  -->
metaImage: runbooks-best-practices.png
bannerImage: runbooks-best-practices.png
tags: <!-- see blog/tags.txt for a comprehensive list of tags -->
 - Product
 - Runbooks
---
```

### YAML header (docs)

```md
---
layout: src/layouts/Default.astro
pubDate: 2023-01-01 <!-- The date first published, don't update this -->
modDate: 2023-01-01 <!-- Change this date to singal an update to search engines -->
title: Getting started
subtitle: An overview of Octopus Deploy concepts <!-- Optional: Shown below the title -->
navTitle: Overview <!-- Optional: A shorter title for use in the navigation -->
navSection: Getting started <!-- Optional: For pages with children, the section name -->
description: <!-- Used for list pages, meta tags, and open graph -->
navOrder: 5
---
```

## Headings

Use `##` to create h2 headers and `###` to create h3 headers.

The first header you include on a page must be a h2 header. The h1 title of the page comes from the title in the YAML block.

## Formatting text

Bold text with `**` on both sides of the text to create `**bold text**`: **bold text**.

Italicize text with `*` on both sides of text to create `*emphasized text*`: *emphasized text*.

## Images

Image filenames must be all lowercase. 

Add images to an `images/` directory in the same directory as the file that references the image.

Images are added to documents with the following syntax:

	![](images/image-name.png)

Images should include alt text for accessibility:

	![A brief description of the image](images/image-name.png)

Control the size of the image in pixels by adding: `width=500`:

	![A brief description of the image](images/image-name.png "width=500")
  
Add a caption below the image by appending the caption text:

  	![A brief description of the image](images/image-name.png "width=500")*This is a caption*
  

## Lists

Bullet lists are written with a hyphen at the beginning of the line:

```md
- Item 1
- Item 2
```

Which is rendered as:

- Item 1
- Item 2

Numbered lists are written with a number at the beginning of the line. The numbers do not need to increment as this will happen automatically:

```md
1. Item 1
1. Item 2
```

Which is rendered as:

1. Item 1
2. Item 2

You can nest lists by adding three spaces before the nested list items.

```md
1. Item 1
   1. Item 1.1
   1. Item 1.2
1. Item 2
```

Which is rendered as:

1. Item 1
   1. Item 1.1
   1. Item 1.2
1. Item 2

If you include an interruption between list items, you need to resume the list with the number the list should restart from:

```md
1. Item 1
1. Item 2

A break in the list.

3. Item 3
3. Item 4

```

Which is rendered as:

<ol>
<li>Item 1</li>
<li>Item 2</li>

A break in the list.

<li>Item 3</li>
<li>Item 4</li>
</ol>

## Tables

Tables are written in the following following way:

```
|  Header 1 | Header 2 | Header 3 | Header 4 | Header 4 |
|---|---|---|---|---|
| Row 1 Cell 1 | Cell 2 | Cell 3 | Cell 4 | Cell 4 |
| Row 2 Cell 1 | Cell 2 | Cell 3 | Cell 4 | Cell 4 |
```

There are generators online you can use to make this process a bit easier, for instance, [Table generator](https://www.tablesgenerator.com/markdown_tables).

## Links

Links are written with the following syntax: 

`[Link text](http://www.octopus.com/docs/installation/index.md)`

## Documentation 

To link to other pages within the **documentation**, use the following syntax (include the full filename and extension):

For more information, see the `[installation page](/docs/installation/index.md)` and review the `[installation requirements](/docs/installation/requirements.md)`.

This will link to https://www.octopus.com/docs/installation and https://www.octopus.com/docs/installation/requirements.

## Blog

To link to other posts within the **blog**, use the following syntax (include the full filename and extension):

This is part one in a series of posts, read `[part two](blog/2020-03/blog-title-part-two.md)`.

This links to https://www.octopus.com/blog/blog-title-part-two.

Note, blog posts are organized in the repo into year-month folders, and you need to include this in your link.

### Anchor links

To link to a specific section within a document, add the section heading as an anchor and replace the spaces with hyphens:

Octopus can be installed on these versions of `[Windows Server](docs/installation/requirements.md#windows-server)`.

This will link to https://octopus.com/docs/installation/requirements#windows-server

If you'd like to control the anchor text (to ensure it doesn't change even if the title does), use the following syntax:

~~~
## Windows Server {#windows-server}
~~~

Special characters will break the anchor text, so don't include special characters in the anchor.

## Navigation paths

When instructing users to navigate through multiple options in the UI, use the following syntax:

    {% raw %}{{ infrastructure,Deployment Targets }}{% endraw %}

Which will be rendered:

**Infrastructure ➜ Deployment Targets**

## Code samples

Use GitHub-style fenced code blocks. For example:

    ​```ps
    Write-Host "Hello"
    ​```

If your example uses multiple languages or files, you can combine them together to add tab headings:

    ​```ps PowerShell
    Write-Host "Hello"
    ​```
    ​```cs C#
    Console.WriteLine("Hello");
    ​```

Snippets are highlighted by Highlight.js

* [Documentation](https://highlightjs.readthedocs.io/)
* [Language List](https://github.com/highlightjs/highlight.js/blob/master/SUPPORTED_LANGUAGES.md)

| language     | key            |
| ------------ | -------------- |
| c#           | cs          |
| xml          | xml          |
| no format    | no-highlight |
| command line | bash         |
| powershell   | ps           |
| json         | json         |
| sql          | sql         |
| f#           | fsharp       |
| python       | python       |
| text         | text           |

If no language is defined, highlightjs will guess the language, and it regularly gets it wrong.

## Call-outs

To create a call-out that draws the reader's attention, use the following syntax:

```md
:::warning
This release includes the following breaking changes...
:::
```

This will be converted to the following HTML:

```html
<div class="alert alert-warning">
<p>This release includes the following breaking changes...</p>
</div>
```

There are several keys, each of which map to a different colored alert:

| Key       | Color  |
| --------- | ------ |
| `success` | green  |
| `hint`    | blue   |
| `warning` | yellow |
| `problem` | red    |

Call-outs are added through bootstrap alerts [https://getbootstrap.com/components/#alerts](https://getbootstrap.com/components/#alerts).

## Reuse text

To create reusable text that is automatically added to any document that references it, add the text to a new file and save the file with a key followed by `.include.md`. For instance, `latest-version.include.md`, and save the file to the `docs/shared-content/` or `blog/shared-content/` directory respectively:

```md
The latest version of Octopus Deploy is 2020.1
```

If the complete filename is `latest-version.include.md`, to include the text in other documents, use the following everywhere you want to include the text:

`!include <latest-version>`

When you use an include file in this way, you only need to update the text in one file and the updated text will be included anywhere it is referenced.

### Referencing Docker images

**Deprecated** this is no longer available for docs.

When referencing docker images, use the syntax:

`!docker-image <org/image:tag>`

This will be replaced with the most recently published version of the image.

#### Example 1 - with tags

`!docker-image <octopusdeploy/octo:alpine>`

Will be replaced with:

`octopusdeploy/octo:6.17.3-alpine`

#### Example 2 - without tags

`!docker-image <octopusdeploy/octo>`

Will be replaced with:

`octopusdeploy/octo:6.17.3`

## Link to the Octopus Guides

The [Octopus Guides](https://octopus.com/docs/guides) combine content to allow users to specify their entire CI/CD pipeline and access a guide for their specific pipeline. It is sometimes helpful to link to the guides with specific options pre-defined rather than the default options.

You create the links to specific guides by adding query parameters to the URL for the guide `https://www.octopus.com/docs/guides`:

- Application: add `?application=PHP`:

    [https://www.octopus.com/docs/guides?application=PHP](https://www.octopus.com/docs/guides?application=PHP)
- Build server: add `?build-server=jenkins`:

    [https://www.octopus.com/docs/guides?buildServer=Jenkins](https://www.octopus.com/docs/guides?buildServer=Jenkins)
- Source control: `sourceControl=TFVC`:

    [https://octopus.com/docs/guides?sourceControl=TFVC](https://octopus.com/docs/guides?sourceControl=TFVC)
- Package repository: `?packageRepository=Artifactory`:

    [https://octopus.com/docs/guides?packageRepository=Artifactory](https://octopus.com/docs/guides?packageRepository=Artifactory)
- Destination: `?destination=NGINX`:

    [https://octopus.com/docs/guides?destination=NGINX](https://octopus.com/docs/guides?destination=NGINX)

If you'd like to pre-fill more than one option, add multiple queries parameters to the URL:

https://octopus.com/docs/guides?application=PHP&buildServer=TeamCity&destination=NGINX

## Redirects

If you delete or rename a file in either the docs or blog repos, you must add a redirect for that file otherwise publishing will fail.

Blog redirects are added to `blog/redirects.txt`:

The redirects.txt file looks like this:
```
from-file-path -> to-file-path                 #DO NOT DELETE THIS LINE
blog/page1.md -> blog/page2.md
```
In the above example, `/blog/page1` is redirected to `/blog/page2`.

Add your redirect to the end of the file, after the redirect is added, the original file (`page1`) needs to be deleted from the repo.

## Docs redirects

Please use the Redirect layout and set the new destination page. The entire contents of a redirct file is the following YAML frontmatter:

```
---
layout: src/layouts/Redirect.astro
title: Redirect
redirect: https://octopus.com/docs/security/fips-and-octopus-deploy
pubDate:  2023-01-01
navSearch: false
navSitemap: false
navMenu: false
---
```

