# Create Cloud Visualizations

## Built-in clouds

The default CB theme has two cloud visualizations pre-configured: subjects and locations. 
These can be easily controlled using variables in the `theme.yml`.

```
# Subject page
subjects-page: true # true / false, turns off subject generation 
subjects-fields: subject;creator # set of fields separated by ; to be featured in the cloud
subjects-min: 1 # min size for subject cloud, too many terms = slow load time!
subjects-stopwords: # set of subjects separated by ; that will be removed from display, e.g. boxers;boxing

# Locations page
locations-page: false # true/false
locations-fields: location # set of fields separated by ; to be featured in the cloud
locations-min: 1 # min size for subject cloud, too many terms = slow load time!
locations-stopwords: # set of subjects separated by ; that will be removed from display, e.g. boxers;boxing
```

These theme configuration options drive pre-made pages (with layout `subjects` and `locations` respectively), and use the layout value to add an _include via `foot.html` (which allows the theme values to be used).
Modifying the config settings can easily transform these two pages into clouds based on any metadata field.

## Cloud Layout and Front matter

Custom cloud pages can be easily created using the cloud layout and page front matter.
To the page front matter add: 

- `cloud-fields:`, with a value of a set of fields separated by `;` to be featured in the cloud.
- `cloud-min:` (optional), with a integer value such as `2`.
- `cloud-stopwords:` (optional), with a set of subjects separated by `;` that will be removed from display

For example, to create an Authors cloud page, create a file named `authors.md` in the "pages" folder. 
Edit the `authors.md` with this content:

```
---
title: Authors
layout: cloud
permalink: /authors.html
cloud-fields: creator
cloud-min: 
cloud-stopwords:
---

## Browse Authors

Example custom cloud page.
```

## Cloud include 

Clouds can also be added to any page using the `_include/js/cloud-js.html` include in the page stub content, with the variable `fields`, and optional variables `min` and `stopwords`. 
Cloud-js include assumes a div with `id="cloud"` exists on the page for the cloud to fill.
So putting them together, you can add a cloud anywhere in a page.
For example:

```
<div id="cloud" class="text-center my-4 bg-light border rounded p-2"></div>
{% include js/cloud-js.html fields="creator;publisher" min="2" stopwords="example;another" %}
```
