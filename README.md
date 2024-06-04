# SHOPIFY THEME SANDBOX

<a href="https://dawn-customized-sandbox.myshopify.com/">
    <img src="https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-logo.png" alt="Outdoor Gear logo" title="Outdoor Gear" align="right" height="60" />
</a>

:star: Star this on GitHub if you got any value out of this :smile:

Note:
This Shopify 2.0 theme, built and modified from Dawn, showcases extensive customizations and features to enhance user experience and functionality. It includes custom fonts, dynamic banners, metafields, checkout enhancements, and SEO optimizations, making it perfect for learning and demonstrating advanced Shopify theme development techniques.

This is not a production-ready theme but an ongoing learning sandbox. Certain areas would need refactoring, including significant CSS improvements, before pushing to production.

![dawn-customized](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-homepage.png)

## Customizations

- [Theme](#theme)
  - [Custom Fonts](#custom-fonts)
- [Home Page](#homepage)
  - [Announcement Bar](#announcement-bar)
  - [Transparent Header](#transparent-header)
  - [Custom Hero Banner](#custom-hero-banner)
  - [Animated Brand & Text Marquee](#animated-brand-and-text-marquee)
- [Product Page](#product-page)
  - [Dynamic vendor Link](#dynamic-vendor-link)
  - [Free Shipping Threshold](#free-shipping-threshold)
  - [Free Shipping Restriction](#free-shipping-restriction)
  - [Fragile Item Message](#fragile-item-message)
  - [Tabbed Product Descriptions](#tabbed-product-descriptions)
  - [Sale Badge](#sale-badge)
- [Collection Page](#collection-page)
- [Cart Drawer](#cart-drawer)
- [Checkout Branding API](#checkout-branding-api)
- [Checkout UI Extensions](#checkout-ui-extensions)
  - [Upsell Offer](#upsell-offer)
  - [Post Purchase Survey](#post-purchase-survey)
  - [Fragile Text Banner](#fragile-text-banner)
  - [Custom Data via Metafield](#custom-data-via-metafields)
- [Checkout Functions](#checkout-functions)
  - [Tiered Discounts](#tiered-discounts)
- [SEO & Metadata](#seo-and-metadata)
- [MetaFields & Objects](#metafields-and-objects)
- [Shopify Flow](#shopify-flow)
- [Visuals & STylings](#visuals-and-stylings)

## THEME

### Custom Fonts

Added 2 Custom Fonts - File: base.css

```bash
@font-face {
  font-family: CustomThin;
  src: url('https://cdn.shopify.com/s/files/1/0704/7482/5964/files/LEMONMILK-Regular.woff2?v=1715786814');
}

@font-face {
  font-family: CustomThick;
  src: url('https://cdn.shopify.com/s/files/1/0704/7482/5964/files/Akira_Expanded_Demo.woff2?v=1715786814');
}
```

<br><br>

## HOMEPAGE

### Announcement Bar

Allows the user to choose background color, font color, write multiple headlines with links and choose the timing intervals between each messages.

- File: custom-announcement-bar.liquid

Visuals:
![Announcement Bar](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-announcement-bar.png)
<br><br><br>

### Transparent header

Transparent header with opacity transition when scrolled

- File: custom-header.liquid

Visuals:
![Opacity Header](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-opacity-header.png)
<br><br><br>

### Custom Hero Banner

Allows merchants to add gradient headings, adjust size & color as well as complete control over position.

- File: custom-image-banner.liquid

Visuals:
![Gradients Banner](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-gradient-header.png)
<br><br><br>

### Animated brand and text marquee

Text, font color, background color, logos can be customized via the theme settings. Animation speed is hardcoded.

- Files: custom-marquee.liquid & custom-marquee-text.liquid

Visuals:
![Brand Logo Marquee](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-marquee.png)
<br><br><br>

### Video Banner

The video auto plays on a loop, the section allows the merchant to enter a header, subheading and a button link.

- File: custom-video-banner.liquid

Visuals
![Video Autoplay Banner](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-video-banner.png)
<br><br><br>

### Reassurance icons bar and Our Story

- Added via the Theme editor

Visuals:
![Brand Logo Marquee](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-reassurance.png)
<br><br><br>

## PRODUCT PAGE

### Dynamic vendor link

Vendor name appears over the product title and dynamically creates a link to the vendor collection.

- File: main.product.liquid

Visuals:
![Brand Logo Marquee](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-vendor-logo.png)

```bash
{%- when 'text' -%}
                {% if block.settings.text == product.vendor %}
                  {% assign vendor_collection_handle = product.vendor | handleize %}
                  {% assign vendor_collection = collections[vendor_collection_handle] %}

                  {% if vendor_collection and vendor_collection.image %}
                    <div class="vendor-collection-image">
                      <a
                        href="{{ shop.url }}/collections/{{ vendor_collection_handle }}"
                        style="text-decoration: none;"
                      >
                        {{ vendor_collection.image | image_url: width: 50 | image_tag }}
                      </a>
                    </div>
```

<br><br><br>

### Free Shipping Threshold

Added a Block which acts as a Free Shipping threshold and outputs and icon and message to display Free Shipping messaging dependent on price threshold.

- File: product-main.liquid

Visuals:
![Free Shipping Threshold](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-free-shipping.png)
<br><br><br>

### Free Shipping Restriction

Added a Block which acts as a conditional towards the Free Shipping block. It allows the merchant to enter a discount % threshold. Any products above this discount % wll not qualify for Free Shipping and will see a different icon and message displayed.

- File: product-main.liquid

Visuals:
![No Free Shipping - Discount](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-nofreeship.png)
<br><br><br>

### Fragile Item Message

Added a Block which outputs and icon and message to display a fragile product - local pick-up only messaging. The merchant can enter a tag value which will prompt this message. If the tag is present, this will overide the Free shipping msg, mentioned above.

- File: product-main.liquid

Visuals:
![Fragile Product Message](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-fragile-product.png)
<br><br><br>

### Tabbed product descriptions

Added a tabbed product description area which is triggered if conditionals are present in the product description such as "Description:", "Features", "Specs", "Reviews".

- File: main-product.liquid

Visuals:
![Tabbed Descriptions](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-tabbed.png)
<br><br><br>

### Sale Badge

Replaced the sale badge with % off amount appearing in the badge.

- File: price.liquid

```bash
{%- if show_badges and product.compare_at_price > product.price -%}
    {% assign numerator = product.compare_at_price | minus: product.price %}
    {% assign denominator = product.compare_at_price %}
    {% assign intermediate_result = numerator | times: 100 %}
    {% assign percentage = intermediate_result | divided_by: denominator %}
    {% assign rounded_percentage = percentage | round %}
    <span class="badge price__badge-sale color-{{ settings.sale_badge_color_scheme }}">
      -{{ rounded_percentage }}%
    </span>
  {%- endif -%}
```

<br><br><br>

## COLLECTION PAGE

Replaced the sale badge with % off amount + Added a custom banner with links input

- File: custom-collections-banner.liquid
  <br><br><br>

## CART DRAWER

Added a shipping progress bar which outputs various messaging depending on cart amount.

- File: cart-drawer-tracker.liquid Snippet & added some settings in settings_schema.json

Visuals:
![Shipping Progress Bar](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-ship-progress-bar.png)
<br><br><br>

## CHECKOUT BRANDING API - GraphQL

- Modified via a GraphQL mutation
- Added 2 custom Fonts
- Modified the input fields to only have a bottom border and be Transparent
- Modified button styling
- Increased heading sizes
- Added favicon

Visuals:
![Branding API](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-checkout-branding.png)
<br><br><br>

## CHECKOUT UI EXTENTIONS

### Upsell offer:

Added an upsell product offer on the checkout.

- Repo: shopify-checkout-upsell-extension

Visuals:
![Upsell Extension](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-extension-upsell.png)
<br><br><br>

### Post purchase survey:

Presents the user with one survey at the Thank You page and a reviews survey at the order page.

- Repo: shopify-checkout-survey-extension

Visuals:
![Upsell Extension](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-postpurchase-survey.png)
<br><br><br>

### Fragile text banner:

This component displays a warning banner if a product in the cart is of the product type "fragile".

- Repo: shopify-banner-checkout-extension

Visuals:
![Custom warning banner](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-warning-banner.png)
<br><br><br>

### Custom data via metafields:

This component displays custom text below the line item within the order summary. Currently its displaying a metafield of the product.

- Repo: shopify-metafield-extension

Visuals:
![Custom Text Extension](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-fragile-extension.png)
<br><br><br>

## CHECKOUT FUNCTIONS

### Tiered Discounts

Added a function that adds a tired discount on a specific product. 10% on 2, 15% on 3, 20% on 4.

- Repo: shopify-checkout-tiered-discounts

Visuals:
![Tiered Discount](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-tiered-discount.png)
<br><br><br>

### Delivery Customization Text

This function ads a UI for the merchant within the Settings > Delivery Customization area to enter a Province/State code along with a message to display when the region is present in the checkout.

- Repo: shopify-delivery-customization-function

Visuals:
![Delivery Customization](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-delivery-customization.png)
<br><br><br>

## SEO AND METADATA

Added a custom robots.txt file which excludes a specific product and excludes all products that contain the 'no-index' tag.

```bash
{% for product in collections.all.products %}
      {% if product.tags contains 'no-index' %}
        {{ 'Disallow: /products/' | append: product.handle }}
      {% endif %}
    {% endfor %}
```

Added logic on theme.liquid to add the no-index meta tag for a products with the specified tag.

```bash
{% if product.tags contains 'no-index' %}
      <meta name="robots" content="noindex, nofollow">
    {% endif %}
```

Added logic in theme.liquid to customize the meta description for product templates. If the template is a product, the meta description will include custom text and the vendor name. Otherwise, the default description will be used.

```bash
{% if template contains 'product' %}
      {% assign custom_page_description = 'Shop '
        | append: product.vendor
        | append: ' at Outdoor Gear - Best Prices Guaranteed!'
      %}
    {% else %}
      {% assign custom_page_description = page_description %}
    {% endif %}
```

<br><br><br>

## METAFIELDS AND OBJECTS

- Added a Brands Bio Meta Object that can be inserted on product pages via a MetaField. Allows the merchant to update data in 1 place and have the updates displayed across all products. The metaobject is inserted via dynamic fields in theme editor using an Image with Text prebuilt section.

Visuals:
![Metaobjects](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-metaobject.png)
<br><br><br>

## SHOPIFY FLOW

Added a flow that sums up the total of a customers orders and tags them if them with a "VIP" if the total is over $1000 - Note: Needed to filter the getOrderData objct with a query of: ''customer_id:{{order.customer.legacyResourceId}}'' to narrow the data to the specific customer.

Visuals:
![Shopify Flow](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-flow-vip.png)
<br><br><br>

## VISUALS AND STYLINGS

Added gradient blobs to Home Page background to add warmth to the page.

- File: base.css

Visuals:
![Gradient Blobs](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-gradient-blobs.png)

```bash
.section-template--17989368479980__featured_collection_gyHQhz-padding::before {
  content: '';
  position: absolute;
  top: 10%;
  left: 10%;
  width: 70%;
  height: 60%;
  background: radial-gradient(
      circle at 30% 30%,
      rgba(255, 139, 110, 0.35) 20%,
      transparent 50%
    ),
    radial-gradient(
      circle at 80% 80%,
      rgba(120, 128, 250, 0.35) 20%,
      transparent 50%
    );
  filter: blur(80px);
  z-index: -1;
}
```
