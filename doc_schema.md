---
layout: default
---
# Schema
## Metadata

{% include metadata_table.html %}

{% assign parts = "definitions,properties" | split: ','%}

{% for part in parts %}

<br/>

## {{ part | capitalize }}

{% for object in site.data.workflow-definition-schema[part] %}

### {{ object.first | capitalize }} properties

{% if object.last.type == "object" %}
  {% include object_table.html %}
{% elsif object.last.type == "array"%}
  {% include array_table.html %}
{% elsif object.last.type == "string"%}
  {% include string_table.html %}
{% else %}
  {{ object.last.title }}
{% endif %}
{% endfor %}

{% endfor %}