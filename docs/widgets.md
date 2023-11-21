# Widgets


We provide widgets for easy integration of OpenWindMap stations on your website.


## Code


#### 1) Add one or more widgets on your page
```html
<!-- display only live wind for Windbird n°1399 -->
<div class="owm-widget" data-id="WB1399"></div>

<!-- display live wind and 2 h history graph for Pioupiou n°641 -->
<div class="owm-widget" data-id="PP641" data-show-live="yes" data-show-2h="yes" data-show-24h="no"></div>

<!-- display live wind and 24 h history graph for MeteoWind n°800 -->
<div class="owm-widget" data-id="MW800" data-show-live="no" data-show-2h="no" data-show-24h="yes"></div>
```

#### 2) Add this script to the bottom of the page
just before the `</body>` tag.
```html
<script src="https://www.openwindmap.org/js/widget-v1.js"></script>
```

## Options

Name | Description | .
-----|----------- |---
{data-id} | ID of the station | ex: WB1300, PP123, MW800, A900 (Required)
{data-show-live} | Display the live wind | yes / no / 0 / 1 / true / false (Optional)
{data-show-2h} | Display the 2 hours history graph | (Optional)
{data-show-24h} | Display the 24 hours history graph |(Optional)

If no `data-show-...` option is passed, the widget will display live wind

<div class="owm-widget" data-id="WB1399"></div>
<script src="https://www.openwindmap.org/js/widget-v1.js"></script>
