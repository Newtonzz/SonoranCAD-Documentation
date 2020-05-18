---
description: >-
  Allows sending nearest postal to the CAD via the location field. Also enables
  postal auto-fill for new dispatches and calls.
---

# Postals

{% hint style="warning" %}
This plugin utilizes API endpoints that require the **standard** version of Sonoran CAD or higher. For more information, view our [pricing ](../../../pricing/faq/)page.
{% endhint %}

## Installation

### 1. Download and Install the Framework

If you haven't already, be sure to install and configure the [plugin framework](../framework-installation.md) first.

### 2. Download the Plugin and Dependencies

1. Click [HERE ](https://github.com/Sonoran-Software/sonoran_postals/releases)to download the postals plugin .zip file.
2. Download and install the [locations ](locations.md)plugin.

### 3. Install the Plugin and Dependencies

1. Follow the [standard plugin installation guide](../plugin-installation.md) for the postals and locations plugin.

## Configuration

| Option | Description | Default |
| :--- | :--- | :--- |
| sendTimer | Time between sending postal updates to the server. | 950 ms |
| shouldSendPostalData | Toggles the plugin on/off | True |
| getPostalMethod | Use a custom postal function or use the supported nearest-postal plugin \(see below\). | custom |

If using "custom" for `getPostalMethod`, you must also define in the `getPostalCustom()` function how to fetch the current player's postal.

## Usage

### Using Nearest-Postal

1. If you're using the publicly available [nearest postals script](https://forum.cfx.re/t/release-nearest-postal-script/293511), you must add the following code to the bottom of `cl.lua`:

```lua
exports('getPostal', function() if nearest ~= nil then return postals[nearest.i].code else return nil end end)
```

2. After doing so, set the `getPostalMethod` configuration option to `"nearestpostal"`.

### Custom Postal Scripts

If you specify "custom", you must edit the `getPostalCustom` function found in `config_postals.lua` to return a postal code as a string.
