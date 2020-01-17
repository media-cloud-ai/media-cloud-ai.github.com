---
layout: default
---
# Schema
## Metadata

 <table style="width:100%">
  <tr>
    <th>Keyword</th>
    <th>Value</th>
  </tr>
  <tr>
    <td>ID</td>
    <td>
        <a href= "{{ site.data.workflow-definition-schema['$id'] }}">
            {{ site.data.workflow-definition-schema['$id'] }}</a>
    </td>
  </tr>
  <tr>
    <td>Json draft</td>
    <td>
        <a href="{{ site.data.workflow-definition-schema['$schema'] }}">
            {{ site.data.workflow-definition-schema['$schema'] }}</a>
    </td>
  </tr>
</table> 

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