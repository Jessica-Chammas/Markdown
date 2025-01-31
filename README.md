---
icon: hand-wave
cover: .gitbook/assets/Screenshot 2025-01-27 at 10.08.37 AM.png
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# REVER's Size Suggestion Script - Integration Guide

This guide provides step-by-step instructions for integrating the Size Suggestion Script into PrestaShop websites. By following this guide, you can dynamically display size recommendations on your product pages to enhance the shopping experience for your customers.



<figure><img src=".gitbook/assets/Screenshot 2025-01-30 at 9.27.08 AM.png" alt=""><figcaption></figcaption></figure>

## 1. Introduction

The Size Suggestion Script fetches and displays size recommendations based on past returns and product reviews, specifically analyzing the reasons for returns related to sizing. Designed for seamless integration, this script ensures that size recommendations appear dynamically on your product pages with minimal setup, helping customers make better-informed decisions.

## 2. Integration Steps

#### **Step 1: Add the Size Recommendation Container**

1. Log in to your PrestaShop Admin Panel.
2. Navigate to: **Advanced Parameters > Templates > Edit Product Template**.
3.  Locate the product page template file:

    ```
    /themes/your-theme/templates/catalog/product.tpl
    ```
4.  Add the following code snippet to the product page template:

    ```html
    <div id="size-recommendation-container"></div>
    ```

**Placement Recommendation:**

* Place the container directly below the size selection dropdown and above any other product attributes (e.g., color options).

Example:

```html
{if isset($product.attributes)}
<select name="group[{attribute_group}]" id="group_{attribute_group}">
    <option value="">Choose an option</option>
    ...
</select>
{/if}
<div id="size-recommendation-container"></div>
```

5. Save your changes.
6. Clear the PrestaShop cache by navigating to **Advanced Parameters > Performance** and clicking **Clear Cache**.

#### **Step 2: Add the Size Suggestion Script**

1. Navigate to: **Design > Theme & Logo > Edit Code**.
2.  Locate the `header.tpl` file:

    ```
    /themes/your-theme/templates/_partials/header.tpl
    ```
3.  Add the following `<script>` tag within the `<head>` section:

    {% code fullWidth="true" %}
    ```html
    <script src="https://rever-static-files.s3.eu-west-3.amazonaws.com/pa-scripts/sizesuggestionscript.js"></script>
    ```
    {% endcode %}
4. Save your changes and clear the cache again.

## 3. Customization&#x20;

You can customize the size recommendation's appearance using CSS:

```css
#size-recommendation-container {
    background-color: #f8f9fa;
    padding: 10px;
    border-radius: 5px;
    margin-top: 10px;
}
.recommendation-message {
    font-size: 14px;
    color: #333;
}
.recommendation-message a.logo-container img {
    height: 20px;
    vertical-align: middle;
    margin-right: 5px;
}
```

## 4. Support:

If you encounter any issues or need further assistance, please contact our support team at **support@rever.com**

#### **Common Issues**

* **Size Recommendation Not Displayed:**
  * Verify the script is correctly added to `header.tpl`.
  * Ensure the `#size-recommendation-container` exists in the product template.
