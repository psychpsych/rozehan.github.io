# Converting from LESS to SCSS

Global search and replace regex:

```bash
# Convert mixins
search:
  ^(\s+)\.(.*\(.*\);)
replace:
  $1@include $2

# Convert variables from config.less file
search:
  @(link-color|link-hover-color|base-font-family|base-font-size|base-line-height|h1|h2|h3|h4|h5|h6|icon-normal|icon-medium|icon-large|input-border-radius|pagination-color|pager-padding|button-text|button-hover|button-active|button-primary-hover|button-primary-active|button-info-hover|button-info-active|button-success-hover|button-success-active|button-danger-hover|button-danger-active|button-warning-hover|button-warning-active|button-inverse-hover|button-inverse-active|navbar-link-space|navbar-sublink-space|dropdown-background|progress-height|switch-border-radius|switch-width|turquoise|green-sea|emerald|nephritis|peter-river|belize-hole|amethyst|wisteria|wet-asphalt|midnight-blue|sun-flower|orange|carrot|pumpkin|alizarin|pomegranate|clouds|silver|concrete|asbestos|base|firm|gray|lightgray|inverse|success|danger|warning|info)
replace:
  \$$1

# Replace ~
search:
  ~
replace:
  [leave blank]
```

Manually go through each file and look for...

* Classes meant to be used as mixins
  * Look for ()
  * Replace with @include or @extend
* Variables at the top of files that need replacing
* Variable variables $#{#{$VAR}}
  * SCSS does not support variable variables
  * Rewrite code as needed
