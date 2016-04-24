# Usage

- [Setting Values](#mutator)
- [Basic Output](#output)
- [Presenter Output](#presenter)

<hr>

<a name="mutator"></a>
## Setting Values

You can set the markdown field type value with a string.

{{ code('php', '$entry->example = $html;') }}

<hr>

<a name="output"></a>
## Basic Output

The markdown field type always returns the storage file content.

{% code php %}
$entry->example; // Contents of storage::example/input/file.js
{% endcode %}

<hr>

<a name="presenter"></a>
## Presenter Output

When accessing the value from a decorated entry, like one in a view, the country field type presenter is returned instead.

#### Storage Path

The storage path is the hinted path string for the field type's storage file. The path hint is shown instead of the full system path.

{% code php %}
$entry->example->path(); // storage::example/input/file.js
{% endcode %}

#### Render

Return the storage file rendered through the view system. An optional argument of view payload data can also be passed.

{% code php %}
$entry->example->render();                          // The rendered content.
$entry->example->render(['products' => $products]); // The rendered content with extra data.
{% endcode %}

#### Parse

Return the storage file parsed through the view layer. Again, optional data payload can also be passed.

<div class="alert alert-primary">
<strong>Note:</strong> This is very different from loading the file as a view. For example, a JS storage file can be parsed but not loaded as a view.
</div>

{% code php %}
$entry->example->parse();                          // The rendered content.
$entry->example->parse(['products' => $products]); // The rendered content with extra data.
{% endcode %}

#### Content

Return the storage file contents. If there is newer information in the database, it will be synced first.

{% code php %}
$entry->example->content(); // The storage file content
{% endcode %}

#### Text

Return the text only contents. This method runs the HTML value through `strip_tags()`;

{% code php %}
$entry->example->text(); // The text only value
{% endcode %}

#### Excerpt

Return a substring of the text value. An optional length and ending string parameters can also be passed.

{% code php %}
$entry->example->excerpt();              // The text only value limited to 100 characters and ending in "..."
$entry->example->excerpt(160, '[more]'); // The text only value limited to 160 characters and ending in "[more]"
{% endcode %}
