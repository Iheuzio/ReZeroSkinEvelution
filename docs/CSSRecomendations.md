# Evelution CSS Best Practices
This documents about how to style your Wiki using the Evelution Skin and making it working accross themes

## Putting code
All code related to the Evelution Skin should be placed inside ``MediaWiki:Evelution.css``. It is recommended to use the theming variables to make it work across themes like:
```css
.my-container {
  background-color:var(--canvas-secondary-background-color);
  color:var(--canvas-text-background-color);
}
```

You can also use ``MediaWiki:Common.css`` and scope the changes to this skin only like:
```css
body.skin-evelution .my-container {
  background-color:var(--canvas-secondary-background-color);
  color:var(--canvas-text-background-color);
}
```

If you decide that only your own color scheme/schemes should be used on your wiki, you can hide the visual colors dropdown by putting the above code to ``MediaWiki:Evelution.css``:
```css
.colors .cpe-floating-button.page-side-tool {
	display:none;
}
```

## Always check against contrast
When picking up custom colors, you should check them to have enough contrast. Below is a table with the list of Contrast Ratios used by Evelution Skin:

| Property 										 	    | Low Contrast  	        | High Contrast |
| ----------------------------------------------------- | ------------------------- | ------------- |
| Text       									   	    | 4.50+                     | 7.00+         |
| XL Text <br> Inactive Text <br> Active Elements       | 3.00+                     | 4.50+         |
| Neutral Color	<br> Inactive Elements			   	 	| 3.00-                     | 4.50-         |
| Document Canvas <br> Solid Background Image			| 0.00+                     | 0.00+         |


Contrast rations that end with ``+`` mean that a color is acceptable if contrast ratio of the color against another color like Canvas is equals or greater than the specified ratio (``--hyperlink-background-color`` for instance). Contrast rations that end with ``-`` mean that a color is acceptable if contrast ratio of the color against another color like Canvas is less than the specified ratio ( ``--canvas-secondary-background-color`` for instance).

Text in size over 20 pixels is considered to be **XL Text**, meaning it can have fewer contrast than small ones, which is the same as the non-notable Small ones. Buttons are considered to be **Active Elements**.

Using theming variables like ``var(--hyperink-background-color)`` as background color and ``var(--hyperlink-foreground-color)`` as foreground color is one of the best choices you can do as you will have forced-colors support out of the box.

If you need to use your own colors for background and foreground color, always pick the best. For instance, if you want your box to have a Lime background, always choose a legible forerground color such as Black or Dark Blue. Never pick a color such as White or Wheat as those colors don't play nice against a Lime background.

On no account will you expect contrast issues when using the theming variables properly as Evelution automatically adjusts offending themes (Those with low contrast) to be as great as possible. This means that creating a theme with all color variables set to the same color (Such as red) will not create an illegible theme. If you're still not satisfied with the color contrast, you can increase contrast level by using the Contrast Modes dropdown and either move the slider more to the right or pick one of the eight Contrast Mode presets (The first one is automatic to match your system preferences).

Evelution also provides Inactive Text, Hyperlink, Visited Hyperlink, Active Text, Highlight, Active Caption and Generic colors variables that can be paired either with the neutral color ( ``-*-secondary-background-color-*`` like ``active-text-secondary-background-color`` ), the Luna Lavccent color aka the Active Caption color ( ``-*-tertiary-background-color-*`` like ``hyperlink-tertiary-background-color`` ) or the Desktop color ( ``-*-quaternary-background-color-*`` like ``highlight-quaternary-background-color`` ) so as to have good color contrast although the Highlight and Active Caption Colors are not usually used as text color of small regular text.

Rememeber that you can increase up Contrast Level in Evelution by changing the contrast mode slider in the contrast modes dropdown if the current minumum contrast requires can't satisfy you although you cannot increase contrast of a specific color pair if the text color against the background color is black or white as the text color cannot be adjusted any further.

## Avoid destroying the layout
When styling the Evelution Skin with CSS, make sure that the layout will still be usable and will not cause any distorts. This is also the case for many other skins.

## Only hide the Global Nav links when required
By default, Global Nav upper links consist of Five (Six on Miraheze Wikis) links. While you can hide them using Sitewide CSS, it can result in important information being lost (Such as the Link to the Evelution Documentation). Those customizations are allowed, unlike in Fandom

## Never Customize other color schemes
Wikis should avoid customizing any color scheme beyond the ``standard`` ones as the rest of them contain color schemes for people who need accessible and different color schemes to suit their preference.

For DCM Modes, avoid customizing any DCM Modes beyond the ``custom_1``, ``custom_2``, ``custom_3`` and ``custom_4`` as the rest provide the base DCM Functionality

Here's a theming template you can use for getting custom theme(s) for your wiki:

## Enabled Color Management (Standard Color Scheme)

### CSS Way (Apply it to MediaWiki:Common.css or MediaWiki:Evelution.css)
```css
.theme-A.colorscheme-light.visualcolors-standard { /* Replace .theme-A with either .theme-B, .theme-C, .theme-D, .theme-E, .theme-F, .theme-G, .theme-H if you want to target the other 7 slots, otherwise don't replace .theme-A with anything. Replace .colorscheme-light with .colorscheme-dark if you want to target the dark color scheme, otherwise don't replace .colorscheme-light with anything */ 
--desktop-background-image:url("loadbg_dev.png"); /* <image> */
--desktop-background-image-filter:opacity(100%); /* <filter-function> */
--desktop-background-image-blend-mode:normal; /* <blend-mode> */
--desktop-background-color:#441177; /* auto | <color> */
--desktop-background-size:cover; /* cover | contain | stretched | full */
--desktop-background-horizontal-alignment:left; /* left | center | right */
--desktop-background-vertical-alignment:top; /* top | center | bottom */
--desktop-background-no-horizontal-tiling:false; /* <boolean> */
--desktop-background-no-vertical-tiling:false; /* <boolean> */
--desktop-text-background-color:auto; /* auto | <color> */
--canvas-background-color:#f1f2f3; /* auto | <color> */
--canvas-secondary-background-color:auto; /* auto | <color> */
--inactive-text-background-color:#aaabbb; /* auto | <color> */
--active-text-background-color:auto; /* auto | <color> */
--canvas-text-background-color:#222222; /* auto | <color> */
--canvas-text-secondary-background-color:auto; /* auto | <color> */
--highlight-background-color:#dd8300; /* <color> */
--highlight-text-background-color:auto; /* auto |<color> */
--hyperlink-background-color:#dd2300; /* <color> */
--visited-hyperlink-background-color:auto; /* auto | <color> */
--active-title-background-color:#b88300; /* auto | <color> */
--active-title-text-background-color:auto; /* auto |<color> */
--inactive-title-background-color:#b88300; /* auto | <color> */
--inactive-title-text-background-color:auto; /* auto |<color> */
--custom-sans-serif-font:""; /* <string> */
--custom-serif-font:""; /* <string> */
--custom-rounded-font:""; /* <string> */
--custom-monospace-font:""; /* <string> */
--border-radius:3px; /* <number> 0 to 15 */
--icon-filter:opacity(1); /* <filter-function> */
--icon-filter-hover:opacity(0.8); /* <filter-function> */
--icon-filter-duration:300ms; /* <duration> */
--icon-filter-delay:0; /* <duration> */
--system-acryllic-opacity:0.6; /* <number> 0.4 to 0.8 */
--system-generic-color-hue-shift:1; /* <number> -12 to 12 */
--system-generic-color-saturation:100%; /* <number> 20% to 100% */
--system-icon-style:rounded; /* rounded | outlined | sharp */
}
```

### PHP Way (Apply it to LocalSettings.php)
```php
$wgEvelutionThemeA = [/* Replace $wgEvelutionThemeA with either $wgEvelutionThemeB, $wgEvelutionThemeC, $wgEvelutionThemeD, $wgEvelutionThemeE, $wgEvelutionThemeF, $wgEvelutionThemeG, $wgEvelutionThemeH, $wgEvelutionThemeADark, $wgEvelutionThemeBDark, $wgEvelutionThemeCDark, $wgEvelutionThemeDDark, $wgEvelutionThemeEDark, $wgEvelutionThemeFDark, $wgEvelutionThemeGDark or $wgEvelutionThemeHDark if you want to target the other 7 slots or the dark color scheme, otherwise don't replace $wgEvelutionThemeA with anything */ 
'desktop-background-image' => 'url("loadbg_dev.png")', /* <image> */
'desktop-background-image-filter' => 'opacity(100%)', /* <filter-function> */
'desktop-background-image-blend-mode' => 'normal', /* <blend-mode> */
'desktop-background-color' => '#441177', /* auto | <color> */
'desktop-background-size' => 'cover', /* cover | contain | stretched | full */
'desktop-background-horizontal-alignment' => 'left', /* left | center | right */
'desktop-background-vertical-alignment' => 'top', /* top | center | bottom */
'desktop-background-no-horizontal-tiling' => 'false', /* <boolean> */
'desktop-background-no-vertical-tiling' => 'false', /* <boolean> */
'desktop-text-background-color' => 'auto', /* auto | <color> */
'canvas-background-color' => '#f1f2f3', /* auto | <color> */
'canvas-secondary-background-color' => 'auto', /* auto | <color> */
'inactive-text-background-color' => '#aaabbb', /* auto | <color> */
'active-text-background-color' => 'auto', /* auto | <color> */
'canvas-text-background-color' => '#222222', /* auto | <color> */
'canvas-text-secondary-background-color' => 'auto', /* auto | <color> */
'highlight-background-color' => '#dd8300', /* <color> */
'highlight-text-background-color' => 'auto', /* auto |<color> */
'hyperlink-background-color' => '#dd2300', /* <color> */
'visited-hyperlink-background-color' => 'auto', /* auto | <color> */
'active-title-background-color' => '#b88300', /* auto | <color> */
'active-title-text-background-color' => 'auto', /* auto |<color> */
'inactive-title-background-color' => '#b88300', /* auto | <color> */
'inactive-title-text-background-color' => 'auto', /* auto |<color> */
'custom-sans-serif-font' => '""', /* <string> */
'custom-serif-font' => '""', /* <string> */
'custom-rounded-font' => '""', /* <string> */
'custom-monospace-font' => '""', /* <string> */
'border-radius' => '3px', /* <number> 0 to 15 */
'icon-filter' => 'opacity(1)', /* <filter-function> */
'icon-filter-hover' => 'opacity(0.8)', /* <filter-function> */
'icon-filter-duration' => '300ms', /* <duration> */
'icon-filter-delay' => '0', /* <duration> */
'system-acryllic-opacity' => '0.6', /* <number> 0.4 to 0.8 */
'system-generic-color-hue-shift' => '1', /* <number> -12 to 12 */
'system-generic-color-saturation' => '100%', /* <number> 20% to 100% */
'system-icon-style' => 'rounded' /* rounded | outlined | sharp */
];

```

## Disabled Color Management (Custom DCM Modes)

### CSS Way (Apply it to MediaWiki:Common.css or MediaWiki:Evelution.css)
```css
.visualcolors-nocolormanagement.dcmmode-custom_1 { /* Replace .custom_1 with either .custom_2, .custom_3 or .custom_4 if you want to target the other 4 custom slots, otherwise don't replace .custom_1 with anything */ 
	--desktop-background-color:field; /* <system-color> */
	--desktop-text-background-color:fieldtext; /* <system-color> */
	--canvas-background-color:canvas; /* <system-color> */
	--canvas-secondary-background-color:buttonface; /* <system-color> */
	--hyperlink-background-color:linktext; /* <system-color> */
	--visited-hyperlink-background-color:visitedtext; /* <system-color> */
	--inactive-text-background-color:graytext; /* <system-color> */
	--active-text-background-color:activetext; /* <system-color> */
	--canvas-text-background-color:canvastext; /* <system-color> */
	--canvas-text-secondary-background-color:buttontext; /* <system-color> */
	--highlight-background-color:highlight; /* <system-color> */
	--highlight-text-background-color:highlighttext; /* <system-color> */
	--active-title-background-color:fieldtext; /* <system-color> */
	--active-title-text-background-color:field; /* <system-color> */
	--inactive-title-background-color:canvas; /* <system-color> */
	--inactive-title-text-background-color:graytext; /* <system-color> */
}
```

### PHP Way (Apply it to LocalSettings.php)
```php
$wgEvelutionCustomDCMMode1 = [ /* Replace $wgEvelutionCustomDCMMode1 with either $wgEvelutionCustomDCMMode2, $wgEvelutionCustomDCMMode3 or $wgEvelutionCustomDCMMode4 if you want to target the other 4 custom slots, otherwise don't replace $wgEvelutionCustomDCMMode1 with anything */ 
	'desktop-background-color' => 'field', /* <system-color> */
	'desktop-text-background-color' => 'fieldtext', /* <system-color> */
	'canvas-background-color' => 'canvas', /* <system-color> */
	'canvas-secondary-background-color' => 'buttonface', /* <system-color> */
	'hyperlink-background-color' => 'linktext', /* <system-color> */
	'visited-hyperlink-background-color' => 'visitedtext', /* <system-color> */
	'inactive-text-background-color' => 'graytext', /* <system-color> */
	'active-text-background-color' => 'activetext', /* <system-color> */
	'canvas-text-background-color' => 'canvastext', /* <system-color> */
	'canvas-text-secondary-background-color' => 'buttontext', /* <system-color> */
	'highlight-background-color' => 'highlight', /* <system-color> */
	'highlight-text-background-color' => 'highlighttext', /* <system-color> */
	'active-title-background-color' => 'fieldtext', /* <system-color> */
	'active-title-text-background-color' => 'field', /* <system-color> */
	'inactive-title-background-color' => 'canvas', /* <system-color> */
	'inactive-title-text-background-color' => 'graytext', /* <system-color> */
];
```
