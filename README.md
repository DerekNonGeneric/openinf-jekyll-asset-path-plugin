<!-- markdownlint-disable-next-line line-length -->
<a href="##"><img src="https://raw.githubusercontent.com/OpenINF/openinf.github.io/live/assets/img/svg/logogram-color.svg?sanitize=true" alt="OpenINF logo" title="OpenINF" align="right" height="96" width="96" /></a>

<div align="left">

## Jekyll Asset Path Tag (OpenINF Adaptation)

> A liquid tag to output a relative URL for assets related to a post or page;
> enabling the organizing of their associated materials into respective
> subdirectories (as opposed to potential, absolute chaos).

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/OpenINF/openinf-jekyll-asset-path-plugin/)

=====================

<img src="https://raw.githubusercontent.com/samrayner/jekyll-asset-path-plugin/master/icon.png" width="150" alt="Jekyll Asset Path Plugin" />


Syntax:
```
{% asset_path filename %}
{% asset_path filename post_id %}
{% asset_path "filename with whitespace" post_id %}
{% asset_path filename /collection_label/post_id %}
```

## Installation
Copy asset_path_tag.rb into */_plugins* ([Jekyll][j]) or */plugins* ([Octopress][o])

## Examples

### Asset of this post

```
{% asset_path my-image.png %}
```
in post 2013-01-01-post-title would output:
```
/assets/posts/post-title/my-image.png
```
in page my-first-page would output:
```
/assets/my-first-page/my-image.png
```

### Asset of another post

```
{% asset_path document.pdf /2012/05/25/another-post-title %}
```
would output:
```
/assets/posts/another-post-title/document.pdf
```

### Asset of document in a collection

```
{% asset_path image.jpg /my_collection/document_in_collection %}
```
would output:
```
/assets/my_collection/document_in_collection/image.jpg
```

## Uses

Useful for images and links in Markdown or HTML:
```
[Download script]({% asset_path my-script.js %})
<img src="{% asset_path my-image.png %}" alt="My Image" />
```

Given file _data/image.csv contains:
```csv
file
image_one.png
image_two.png
```
and post 2015-03-21-another-post-title contains:
```liquid
{% for image in site.data.images %}
  {% asset_path {{ image.file }} %}
{% endfor %}
```
then the tag will output:
```text
/assets/posts/another-post-title/image_one.png
/assets/posts/another-post-title/image_two.png
```

When used with `post_id` parameter, the tag is useful for showing asset from each page. Given the site contains pages:
```
post-title
another-post-title
```
then
```
{% for post in site.posts %}{% asset_path cover.jpg {{post.id}} %}{% endfor %}
```
on index.html will output:
```
/assets/posts/post-title/cover.jpg
/assets/posts/another-post-title/cover.jpg
```

[j]: http://jekyllrb.com/
[o]: http://octopress.org/

## Testing
The plugin can be tested by using the Jekyll test site in `test_site` directory. Generate the site with
```
bundle exec jekyll serve
```
then check the test results by browsing to [http://localhost:4000][test_site].

[test_site]: http://localhost:4000
