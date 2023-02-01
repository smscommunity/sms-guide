---
layout: default
title: Editing Guide
permalink: /editor
nav_order: 11
---

# Editing Guide

This wiki setup is still **a draft**, so do bear in mind things that you find challenging and they'll come under the discussion of what wiki setup to use going forward.

First, make a GitHub account, then create a fork of the main repository. On this fork, you will have full editing powers and can try out stuff without it impacting the main site.
**Edit** the site [here](https://github.com/smscommunity/sms-guide/)  
**View** the site [here](https://smscommunity.github.io/sms-guide/)

If you want to instead edit the site using a tool like VS Code, you will need to clone the repository and set it up for local development. Follow the short guide in the README for more information.

## Edit Workflow
To edit the wiki:
1. Navigate to the page you want to edit on the edit website, and click the pencil.
![](https://cdn.discordapp.com/attachments/529145099003887618/963155220144214026/unknown.png)
2. Type in the "Edit File" tab, and see a preview in the "Preview" tab.
3. Save your changes by typing an edit summary and optional detailed summary, then with the "commit directly" bullet selected, click "Commit changes".
![](https://cdn.discordapp.com/attachments/529145099003887618/963155961336442990/unknown.png)
4. If you want to confirm your changes on the live (reading) website, wait ~3 mins for it to update.

**Iterative Work**  
You can make as many edits as you like, but the delay for the live site to rebuild is a downside of this setup. The preview tab is a reasonably accurate live view of the changes, but some stuff can get messed up and need formatting fixes down the line (which a more technical editor can take care of and might not be the main editor's responsibility).

# Syntax

There are two kinds of syntax used:
1. The basic Markdown syntax for day-to-day edits, which supports adding in snippets of HTML.
2. The extended Markdown that provides stuff like metadata for the page (title, menu order etc.), video embeds and such like.

The latter is there and shows up in the preview as broken, but renders correctly on the real thing. You can just safely ignore it, and if the real thing breaks, someone else can fix it :p. Examples of extended Markdown that's broken in preview but works on the real thing:

![](https://cdn.discordapp.com/attachments/529145099003887618/963158324155674644/unknown.png)

![](https://cdn.discordapp.com/attachments/529145099003887618/963158545140969532/unknown.png)

## Basic Markdown Guide
An important part of this setup is that basic Markdown is very simple, just an extension of Discord syntax. Here's a guide; edit this page to see the source code for these examples.

1\. A double newline will give a **paragraph break**. A single newline does nothing (except makes the Markdown itself easier to read). If you want a **line break**, add two spaces to the end of that line.  
*Like this.*

2\. **Bold** is given by `**bold**`, *Italic* by `*italic*`. I think <u>underline</u> requires HTML (unfort) – it's given by `<u>underline</u>`. Coloured text doesn't work; don't even try.

3\. Code blocks like the ones in the previous point are given by ``backticks``. Triple backtick gives multiline blocks.

```
This be a multiline block.
How *you* doin?
```

4\. Sections are structured by prepending # symbols – `# Title`, `## Section`, `### Subsection` etc.

5\. Lists can be created by starting lines with `*` or `-`, and numbered lists by `1.`, `2.` etc. The actual numbers typed don't make a difference; it auto-numbers them. But sometimes that breaks (like if there are many paragraphs in a list entry) and manually overriding numbering by typing `1\.`, `2\.` etc. does the trick. Examples:

- Bulleted
- List

1. Numbered
2. List

6\. URLs are given by `[link name](link address)`, like [this](https://cdn.discordapp.com/attachments/529145099003887618/947937236933042206/unknown.png). Images are embedded by `![alt text](image address)`, like:

![](https://cdn.discordapp.com/attachments/529145099003887618/947937236933042206/unknown.png)

Markdown by default renders large images that are left-aligned, but html can be used to refine that with a maximum width and centre-alignment, e.g.

```html
<p align="center"><img src="https://cdn.discordapp.com/attachments/529145099003887618/947937236933042206/unknown.png" width="400"></p>
```

<p align="center"><img src="https://cdn.discordapp.com/attachments/529145099003887618/947937236933042206/unknown.png" width="400"></p>

7\. Indentation of lines can only be done manually by pasting in special whitespace characters:  
    *This line is indented by 4 en-spaces.*

For the love of god, never indent anything by 4 or more normal spaces; it'll trigger a multiline code block and leave you confuse-o.

## Extended Markdown Guide
Basic Markdown is simple but scrappy, and doesn't support stuff like video embeds for example. You can copy examples to get those working if you fancy. There are 2 main things whose existence you should note, whether you try to use them or not:

### Macros (e.g. Video Embed)

The {% raw %}`{% %}`{% endraw %} stuff is macros for including bits of HTML (that, say, handle video embeds) in a clean way. This is the current setup for YouTube embeds:

{% raw %}`{% include yt.html id="Ksr-H9dgGjA" %}`{% endraw %}

{% include yt.html id="Ksr-H9dgGjA" %}

The `{: }` stuff is iirc custom features provided by the website theme, like tables of contents (`{:toc}`).

### Front-Matter (for Page Metadata)

The top of each page has `---` blocks, like:

```
---
layout: default
title: Events
permalink: /events
nav_order: 6
---
```

This doesn't render correctly in the preview so can take some patience to fiddle with and can be ignored by regular editors. But it basically gives pages titles, layout templates, positions in the menu, and urls.

## Folder Structure

For specific episode shines, the format should be:

`/shines/[world]/episode[x].md` for episodes.

Once we get to 100 coins and secret shines, we'll figure out a better system :)