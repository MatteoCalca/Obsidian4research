---
title: "{{title}}"
authors: {{authors}}{{directors}}
tags:
  - type/paper
linked_project: 
year: {{date | format("YYYY")}}
read_status: {%- if markdownNotes %} Yes {%- else %} No {%- endif %}
aliases:  
  - {{title}}  
  - {{citekey}}  
  - {% set authlist = authors %} {%- if creators.length>2 %} {%- set authlist = creators[0].lastName+' et al.'-%} {% endif -%} {%- if creators.length == 1 %} {%- set authlist = creators[0].lastName-%} {% endif -%} {%- if creators.length == 2 %} {%- set authlist = creators[0].lastName+' & '+creators[1].lastName-%} {% endif -%}{{authlist}} {{date | format("YYYY")}}
---
*Zotero link*: {{pdfZoteroLink}}

{{bibliography}}

> [!example] Abstract
> {{abstractNote}}

```ad-note
{{markdownNotes}}
```


{%-
    set zoteroColors = {
        "#e56eee": "magenta",
        "#2ea8e5": "blue",
        "#5fb236": "green",
        "#a28ae5": "purple",
        "#ff6666": "red",
        "#f19837": "orange",
        "#aaaaaa": "grey",
        "#ffd400": "yellow"
    }
-%}

{%-
   set colorHeading = {
         "magenta": "Main point",
        "red": "Problematic",
        "blue": "Definitions",
        "green": "Generic",
        "purple": "Generic",
        "orange": "Generic",
        "grey": "Generic",
        "yellow": "Generic"
  }
-%}

{%- macro calloutHeader(type) -%}
    {%- switch type -%}
        {%- case "highlight" -%}
        H
        {%- case "image" -%}
        Img
        {%- default -%}
        Note
    {%- endswitch -%}
{%- endmacro %}

{%- set newAnnot = [] -%}
{%- set newAnnotations = [] -%}
{%- set annotations = annotations | filterby("date", "dateafter", lastImportDate) %}

{%- for annot in annotations -%}
    {%- if annot.color in zoteroColors -%}
        {%- set customColor = zoteroColors[annot.color] -%}
    {%- elif annot.colorCategory|lower in colorHeading -%}
        {%- set customColor = annot.colorCategory|lower -%}
    {%- else -%}
        {%- set customColor = "other" -%}
    {%- endif -%}
    {%- set newAnnotations = (newAnnotations.push({"annotation": annot, "customColor": customColor}), newAnnotations) -%}
{%- endfor -%}

{%- for color, heading in colorHeading -%}
{%- for entry in newAnnotations | filterby ("customColor", "startswith", color) -%}
{%- set annot = entry.annotation -%}
 

{%- if entry and loop.first %}
### {{colorHeading[color]}} %% fold %%
{%- endif %}

{{calloutHeader(annot.type)}} ([Page {{annot.page}}]({{annot.desktopURI}}))  {%- if annot.annotatedText %}  {{annot.annotatedText}} {% if annot.hashTags %}{{annot.hashTags}}{% endif -%}{%- endif %}

{%- if annot.imageRelativePath %}
![[{{annot.imageRelativePath}}]]
{%- endif %}

{%- if annot.ocrText %}
{{annot.ocrText}}
{%- endif %}
 
{%- if annot.comment %}
- **{{annot.comment}}**
{%- endif -%}
 

{%- endfor -%}

{%- endfor -%}