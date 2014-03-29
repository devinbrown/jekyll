# Jekyll

>Jekyll is, at its core, a text transformation engine. The concept behind the system is this: you give it text written in your favorite markup language, be that Markdown, Textile, or just plain HTML, and it churns that through a layout or series of layout files. Throughout that process you can tweak how you want the site URLs to look, what data gets displayed in the layout, and more. This is all done through editing text files, and the static web site is the final product.

## Drafts

Drafts are stored in `drafts/` and following the format: `title.MARKUP`.

## Includes

This includes the partials that may be mixed and matched by the layouts.

## Layouts

These are the templats that wrap posts. Layouts are chosen on a post-by-post basis in the YAML front matter. The liquid tag `{{ content }}` is used to inject content into the web page.

## Posts

The dynamic content, so to speak. The naming convention of these files is important and must follow the format: `YEAR-MONTH-DAY-title.MARKUP`. The permalinks can be customized for each post, but the date and markup language are determined soley by the filename.

## Data

Well-formatted site data should be placed here. They jekyll engine will autoload all yaml files in this directory.

If there is a `members.yml` under the directory, then you can access contents of the file through `site.data.members`.

## Site

This is where the generated site will be placed (by default) once Jekyll is done transforming it. It's probably a good idea to add this to your `.gitignore` file.

## Index

The `index.html` file provides a YAML Front Matter section, it will be transformed by Jekyll.