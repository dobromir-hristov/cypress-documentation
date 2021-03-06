# Tags

The Cypress documentation uses [Hexo](https://hexo.io) to convert [Markdown](https://daringfireball.net/projects/markdown/syntax) documents to static HTML.

Hexo ships with lots of [tags](https://hexo.io/docs/tag-plugins.html) that extend Markdown with extra features.

Here's documentation for all the custom tags that we've created.

- [Common Hexo tags](#common-hexo-tags)
  - [`img`](#img)
- [Cypress custom tags](#cypress-custom-tags)
  - [`assertions`](#assertions)
  - [`fa`](#fa)
  - [`helper_icon`](#helper_icon)
  - [`issue`](#issue)
  - [`note`](#note)
  - [`open_an_issue`](#open_an_issue)
  - [`partial`](#partial)
  - [`requirements`](#requirements)
  - [`timeouts`](#timeouts)
  - [`url`](#url)
  - [`urlHash`](#urlHash)
  - [`usage_options`](#usage_options)
  - [`user`](#user)
  - [`video`](#video)
  - [`yields`](#yields)

## Common Hexo tags

> We didn't create the tags in this section&mdash;they ship with Hexo&mdash;but they're used _all over the docs_ so here's the lowdown.

### `img`

Insert the markup for an inline image.

```md
{% img /img/examples/name-of-file.jpg "alt text describing img" %}
```
```html
<img src="/img/examples/name-of-file.jpg" alt="alt text describing img">
```

## Custom Cypress tags

We've created plenty of custom tags that Hexo loads from the [libs/tags](libs/tags) folder. Use 'em 'cos they give the docs a consistent look and feel.

### `assertions`

* [lib/tags/assertions.js](lib/tags/assertions.js)

Describe what assertions can be chained off a command.

```md
{% assertions none cy.clearCookie %}
```
```html
<ul>
  <li><p><code>cy.clearCookie()</code> cannot have any assertions chained.</p></li>
</ul>
```

The following assertions are supported:

* `actions`
* `existence`
* `its`
* `none`
* `once`
* `retry`
* `utility`
* `wait`

### `fa`

* [lib/tags/icons.js](lib/tags/icons.js)

Insert a specific [Font Awesome](https://fontawesome.com/) icon by name.

```md
{% fa fa-check-circle green %}
```

Use these icons to highlight important statements.

```md
**{% fa fa-check-circle green %} Correct Usage**

**{% fa fa-exclamation-triangle red %} Incorrect Usage**

**{% fa fa-angle-right %} value** ***(String)***
```

### `helper_icon`

* [lib/tags/icons.js](lib/tags/icons.js)

Insert a commonly used icon by name.

```md
{% helper_icon yields %}
```

The following icons are supported:

* `assertions`
* `requirements`
* `timeout`
* `yields`

### `issue`

* [lib/tags/issues.js](lib/tags/issues.js)

Link to an issue on Cypress's GitHub repository.

```md
{% issue 74 "not currently supported" %}
```

### `note`

* [lib/tags/note.js](lib/tags/note.js)

Display a block of content that visually stands out from the body of the text.

Most often used to call out warnings, useful info, and tips.

```md
{% note warning 'Anti-Pattern' %}
We do not recommend starting a web server using `cy.task()`. Read about {% url 'best practices' best-practices#Web-Servers %} here.
{% endnote %}
```

The first argument is required: it's used to style the block and add an appropriate icon. Use one of the following values:

* `info`
* `warning`
* `success`
* `danger`
* `bolt`

The second argument is optional: if present it's used as the title of the block.

### `open_an_issue`

* [lib/tags/issues.js](lib/tags/issues.js)

Link to the issue creation page on Cypress's GitHub repository.

```md
{% open_an_issue %}
```

Typically used to make it easier for users to open issues.

```md
At the moment, `mouseover` and `mouseout` events are *not* fired. {% open_an_issue %} if you need this to be fixed.
```

### `partial`

* [lib/tags/partial.js](lib/tags/partial.js)

Include the content of another file inline.

```md
{% partial then_should_difference %}
```

### `requirements`

* [lib/tags/requirements.js](lib/tags/requirements.js)

Describe a command's requirements.

```md
{% requirements parent cy.clearCookie %}
```
```html
<ul>
  <li><p><code>cy.clearCookie()</code> requires being chained off of <code>cy</code>.</p></li>
</ul>
```

The following requirements are supported:

* `none`
* `parent`
* `child`
* `dom`
* `dual`
* `dual_existence`
* `dual_existence_single_dom`
* `clearability`
* `blurability`
* `clearability`
* `focusability`
* `checkability`
* `selectability`
* `scrollability`
* `submitability`
* `spread`
* `exec`
* `task`
* `read_file`
* `write_file`
* `page`
* `tick`
* `request`

### `timeouts`

* [lib/tags/timeouts.js](lib/tags/timeouts.js)

Describe a timeout.

```md
{% timeouts existence cy.get %}
```
```html
<ul>
  <li><p><code>cy.get()</code> can time out waiting for the element(s) to <a href="/guides/core-concepts/introduction-to-cypress.html#Default-Assertions">exist in the DOM</a>.</p></li>
</ul>
```

Typically used inside the _Timeouts_ section when documenting a command. 

```md
## Timeouts {% helper_icon timeout %}

{% timeouts existence cy.get %}
```

The following timeouts are supported:

* `assertions`
* `actions`
* `existence`
* `automation`
* `its`
* `exec`
* `task`
* `none`
* `page`
* `request`
* `wait`
* `promises`
* `timeouts`

### `url`

* [lib/tags/url.js](lib/tags/url.js)

Generate a link.

```md
{% url `.and()` and %}
{% url `.should()` should#Notes %}
{% url 'Read about why' why-cypress %}
{% url http://foo.com %}
```

### `urlHash`

* [lib/tags/url.js](lib/tags/url.js)

Generate a link to an anchor.

```md
{% urlHash 'Standard Output' Standard-Output %}
```
```html
<a href="#Standard-Output">Standard Output</a>
```

### `usage_options`

* [lib/tags/usage.js](lib/tags/usage.js)

Describe the usage of a command option.

Typically used when documenting the `options` object inside the _Arguments_ section.

```md
## Arguments

**{% fa fa-angle-right %} options**  ***(Object)***

Pass in an options object to change the default behavior of `.blur`.

Option | Default | Description
--- | --- | ---
`log` | `true` | {% usage_options log %}
`timeout` | {% url `defaultCommandTimeout` configuration#Timeouts %} | {% usage_options timeout .blur %}
```

The following usages are supported:

* `log`
* `force`
* `multiple`
* `timeout`

### `user`

* [lib/tags/issues.js](lib/tags/issues.js)

Link to a GitHub profile.

Typically used to give attribution to someone who has contributed to Cypress.

```md
Contributed by {% user brian-mann %}.
```

### `video`

* [lib/tags/video.js](lib/tags/video.js)

Embed a video.

```md
{% video vimeo 240554515 %}
```
```md
{% video youtube 5XQOK0v_YRE %}
```
```md
{% video local /img/snippets/selector-playground.mp4 %}
```

### `yields`

* [lib/tags/yields.js](lib/tags/yields.js)

Describe what a command yields.

```md
{% yields sets_subject cy.readFile 'yields the contents of the file' %}
```
```html
<ul>
  <li><p><code>cy.readFile()</code> yields the contents of the file</p></li>
</ul>
```

Typically used inside the _Yields_ section when documenting a command. 

```md
## Yields {% helper_icon yields %}

{% yields sets_subject cy.readFile 'yields the contents of the file' %}
```

The following yields are supported:

* `same_subject`
* `changes_subject`
* `maybe_changes_subject`
* `changes_dom_subject`
* `changes_dom_subject_or_subjects`
* `sets_dom_subject`
* `sets_subject`
* `null`
* `null_alias`
* `assertion_indeterminate`
