[![Orange banner indicating a preview software component][release-level-banner--unstable]](##)

<br />

<!-- markdownlint-disable-next-line line-length -->
<a href="##"><img src="https://open.inf.is/assets/img/svg/logogram-color.svg" alt="OpenINF logo" title="OpenINF" align="right" height="96" width="96" /></a>

<div align="left">

## `@openinf/jekyll-asset-path-tag`

> A Liquid tag to output a relative URL for assets related to a post or page;
> enabling the organizing of their associated materials into respective
> subdirectories (as opposed to potential, absolute chaos).

<br />

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#https://github.com/OpenINF/openinf-jekyll-asset-path-plugin/)

</div>

<img src="https://raw.githubusercontent.com/samrayner/jekyll-asset-path-plugin/master/icon.png" width="150" alt="Jekyll Asset Path Plugin" />


Syntax:

```liquid
{% asset_path filename %}
{% asset_path filename post_id %}
{% asset_path "filename with whitespace" post_id %}
{% asset_path filename /collection_label/post_id %}
```

### Installation

Copy asset_path_tag.rb into */_plugins* ([Jekyll][j]) or */plugins* ([Octopress][o])

### Examples

#### Asset of this post

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

#### Asset of another post

```
{% asset_path document.pdf /2012/05/25/another-post-title %}
```

would output:

```
/assets/posts/another-post-title/document.pdf
```

#### Asset of document in a collection

```liquid
{% asset_path image.jpg /my_collection/document_in_collection %}
```

would output:

```markdown
/assets/my_collection/document_in_collection/image.jpg
```

### Usage

Useful for images and links in Markdown or HTML:

```markdown
[Download script]({% asset_path my-script.js %})
<img src="{% asset_path my-image.png %}" alt="My Image" />
```

Given file `_data/image.csv` contains:

```csv
file
image_one.png
image_two.png
```

and post `2015-03-21-another-post-title` contains:

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

```text
post-title
another-post-title
```

then

```liquid
{% for post in site.posts %}{% asset_path cover.jpg {{post.id}} %}{% endfor %}
```

on `index.html` will output:

```markdown
/assets/posts/post-title/cover.jpg
/assets/posts/another-post-title/cover.jpg
```

[j]: http://jekyllrb.com/
[o]: http://octopress.org/

### Testing

The plugin can be tested by using the Jekyll test site in `test_site` directory. Generate the site with

```shell
bundle exec jekyll serve
```

then check the test results by browsing to [http://localhost:4000][test_site].

[test_site]: http://localhost:4000

<br /><br />

---

<br /><br />

<div align="center">

<a title="The OpenINF website" href="https://open.inf.is" rel="author">
  <img alt="The OpenINF logo" height="32px" width="32px" src="https://open.inf.is/assets/img/svg/logogram-color.svg" />
</a>

</div>

<br /><br />

[![Orange banner indicating a preview software component][release-level-banner--unstable]](##)
  
<!-- LINK LABEL DEFINITIONS - START -->

[release-level-banner--unstable]: https://open.inf.is/assets/img/svg/release-level-banner--unstable.svg 'Banner for Release Level: Unstable'

<!-- LINK LABEL DEFINITIONS - END -->
