# SHOPIFY THEME SANDBOX

<a href="https://dawn-customized-sandbox.myshopify.com/">
    <img src="https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-logo.png" alt="Outdoor Gear logo" title="Outdoor Gear" align="right" height="60" />
</a>

:star: Star this on GitHub if you got any value out of this :smile:

This Shopify 2.0 theme, built and modified from Dawn, showcases extensive customizations and features to enhance user experience and functionality. It includes custom fonts, dynamic banners, metafields, checkout enhancements, and SEO optimizations, making it perfect for learning and demonstrating advanced Shopify theme development techniques.

This is not a production-ready theme but an ongoing learning sandbox. Certain areas would need refactoring, including significant CSS improvements, before pushing to production.

View theme here: <br>
https://dawn-customized-sandbox.myshopify.com/

![dawn-customized](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-homepage.png)

## Customizations

- [Theme](#theme)
  - [Custom Fonts](#custom-fonts)
- [Home Page](#homepage)
  - [Announcement Bar](#announcement-bar)
  - [Transparent Header](#transparent-header)
  - [Mega-Menu Header](#mega-menu-header)
  - [Custom Hero Banner](#custom-hero-banner)
  - [Animated Brand & Text Marquee](#animated-brand-and-text-marquee)
  - [Gradient Background Blocs](#gradient-background-blobs)
- [Product Page](#product-page)
  - [Dynamic vendor Link](#dynamic-vendor-link)
  - [Free Shipping Threshold](#free-shipping-threshold)
  - [Free Shipping Restriction](#free-shipping-restriction)
  - [Fragile Item Message](#fragile-item-message)
  - [Tabbed Product Descriptions](#tabbed-product-descriptions)
- [Collection Page](#collection-page)
- [Cart Drawer](#cart-drawer)
- [Checkout Branding API - GraphQL](#checkout-branding-api-graphql)
- [QR Code App - Remix](#qr-code-app-remix)
- [Checkout UI Extensions](#checkout-ui-extensions)
  - [Upsell Offer](#upsell-offer)
  - [Post Purchase Survey](#post-purchase-survey)
  - [Fragile Text Banner](#fragile-text-banner)
  - [Custom Data via Metafield](#custom-data-via-metafields)
- [Checkout Functions](#checkout-functions)
  - [ Order Discount with Conditions](#order-discount-with-conditions)
  - [Delivery Customization](#delivery-customization-text)
    Delivery customization text
- [SEO & Metadata](#seo-and-metadata)
- [MetaFields & Objects](#metafields-and-objects)
- [Shopify Flow](#shopify-flow)
- [Translation](#translation)
- [Swatches via Taxonomy](#custom-color-swatches-via-metafields-and-product-taxonomy)
  <br><br><br>

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

### Announcement bar

Allows the user to choose background color, font color, write multiple headlines with links and choose the timing intervals between each message.

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

### Mega Menu Header

Custom Mega-menu header with extra large CTA search bar. Also mobile responsive.

- File: custom-mega-menu.liquid

Visuals:
![Mega-menu Desktop](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/mega-menu-desktop.png)
![Mega-menu Mobile](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/mega-menu-mobile.png)
<br><br><br>

### Custom hero banner

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

## Gradient background blobs

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

### Video banner

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

Vendor logo with link appears over the product title if image is present. Otherwise the vendor name is dynamically displayed.

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

### Free shipping threshold

Added a Block which acts as a Free Shipping threshold and outputs and icon and message to display Free Shipping messaging dependent on price threshold.

- File: product-main.liquid

Visuals:
![Free Shipping Threshold](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-free-shipping.png)
<br><br><br>

### Free shipping restriction

Added a Block which acts as a conditional towards the Free Shipping block. It allows the merchant to enter a discount % threshold. Any products above this discount % wll not qualify for Free Shipping and will see a different icon and message displayed.

- File: product-main.liquid

Visuals:
![No Free Shipping - Discount](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-nofreeship.png)
<br><br><br>

### Fragile item message

Added a Block which outputs and icon and message to display a fragile product - local pick-up only messaging. The merchant can enter a tag value which will prompt this message. If the tag is present, this will overide the Free shipping msg, mentioned above.

- File: product-main.liquid

Visuals:
![Fragile Product Message](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-fragile-product.png)
<br><br><br>

### Tabbed product descriptions

Added a tabbed product description area which is triggered if conditionals are present in the product description such as "Description:", "Features", "Specs", "Reviews".

- File: main-product.liquid

Visuals:
<br>
![Tabbed Descriptions](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-tabbed.png)
<br><br><br>

## COLLECTION PAGE

Replaced the sale badge with % off amount + Added a custom banner with links input

- File: card.product.liquid - snippet

Visuals: <br>
![Tabbed Descriptions](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-percentage-off.png)
<br><br><br>

## CART DRAWER

Added a shipping progress bar which outputs various messaging depending on cart amount.

- File: cart-drawer-tracker.liquid Snippet & added some settings in settings_schema.json

Visuals:
![Shipping Progress Bar](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-ship-progress-bar.png)
<br><br><br>

## CHECKOUT BRANDING API GraphQL

- Modified via a GraphQL mutation
- Added 2 custom Fonts
- Modified the input fields to only have a bottom border and be Transparent
- Modified button styling
- Increased heading sizes
- Added favicon

```bash
{
  "checkoutProfileId": "gid://shopify/CheckoutProfile/26214457",
  "checkoutBrandingInput": {
    "designSystem": {
      "colors": {
        "schemes": {
          "scheme1": {
            "base": {
              "text": "#ff3cae"
            },
            "primaryButton": {
              "background": "#8158fc",
              "text": "#000000",
              "hover": {
                "background": "#588afc",
                "text": "#000000"
              }
            }
          }
        }
      },


      "typography": {
        "secondary": {
          "customFontGroup": {
            "base": {
            "genericFileId": "gid://shopify/GenericFile/25779526172729",
             "weight":400
            },
            "bold":{
                  "genericFileId": "gid://shopify/GenericFile/25779526172729",
             "weight":400
            },
            "loadingStrategy": "SWAP"
          }
        }
      }
    },
    "customizations": {
      "favicon": {
        "mediaImageId": "gid://shopify/MediaImage/25779692339257"
      },
      "headingLevel2": {
        "typography": {
         "size": "BASE"
        }
      },
      "primaryButton": {
        "typography": {
          "font": "SECONDARY"
        },
        "background": "NONE",
        "border": "FULL",
        "cornerRadius": "NONE"
      },
      "control": {
        "color": "TRANSPARENT",
        "cornerRadius": "NONE"
      },
      "textField": {
        "border": "BLOCK_END"
      },
      "select": {
        "border": "BLOCK_END"
      }
    }

  }
}
```

Visuals:
![Branding API](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-checkout-branding.png)
<br><br><br>

## QR CODE APP REMIX

Made an app that creates a QR code for the product. You can choose if you want the landing page to be the product within the checkout or simply the product page. Followed the tutprial on Shopidy.dev - A little confusing.

- Repo: shopify-app-remix-qrcodes

Visuals:
![QR App](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-qr-app1.png)
![QR App](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-qr-app2.png)
<br><br><br>

## CHECKOUT UI EXTENSIONS

### Upsell offer:

Added an upsell product offer on the checkout.

- Repo: shopify-checkout-upsell-extension

Visuals:
![Upsell Extension](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-extension-upsell.png)
<br><br><br>

### Rental Product Date Picker:

This extensions presents the customer with a date-picker component when a product defined as rental is prensent in the cart. The date then gets saved as an order metafield and can be viewed within the order's details.

- Repo: shopify-date-picker-extension

Visuals:
![Datepicker](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-datepicker.png)
![Date Metafield](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-date-metafield.png)
<br><br><br>

### Post purchase survey:

Presents the user with one survey at the Thank You page and a reviews survey at the order page.

- Repo: shopify-checkout-survey-extension

Visuals:
![Upsell Extension](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-postpurchase-survey.png)
<br><br><br>

### Fragile text banner:

This component displays a warning banner if a product in the cart is of the product type "fragile". The text is configered within the Settings > Checkout Customizer.

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

### Order discount with conditions

This order discount function applies a $50 discount on orders once the cart reaches $500 and meets the conditions of being part of 3 defined product types and these products must not be discounted.

- GraphQL query:

```bash
query RunInput {
  cart {
    lines {
      quantity
      cost {
        totalAmount {
          amount
        }
      }
      merchandise {
        __typename
        ... on ProductVariant {
          id
          product {
            productType
            inAnyCollection(ids: ["gid://shopify/Collection/427822514412"])
          }
        }
      }
    }
  }
}
```

- Repo: shopify-order-discount-function

Visuals: <br>
![Order Discount in Cart](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-order-discount-cart.png)
<br><br><br>

### Delivery customization text

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

## TRANSLATION

Added the Shopify Translate & Adapt app to harness Shopify's Translation API. Didnt go overboard in translating the entire store, but here is an example of utilization a translation's key within a custom sectio's schema settings. This then allows the merchant to translate these fields with the app via the Theme editor. The syntax for adding a translations key is the following

```bash
"t:<section>.<part>.<sub-part>.<key>"
```

```bash
"blocks": [
    {
      "type": "announcement",
      "name": "t:sections.announcement_bar.blocks.announcement.name",
      "settings": [
        {
          "type": "text",
          "id": "text",
          "label": "t:sections.announcement_bar.blocks.announcement.settings.text.label",
          "default": "t:sections.announcement_bar.blocks.announcement.settings.text.default"
        },
        {
          "type": "url",
          "id": "link",
          "label": "t:sections.announcement_bar.blocks.announcement.settings.link.label"
        }
      ]
    }
  ],
```

## CUSTOM COLOR SWATCHES VIA METAFIELDS AND PRODUCT TAXONOMY

Shopify Summer Editions 2024 release. Allows to use product Taxonomy to attach product category specific metafields. Here is an example of creating custom colors available only for the Snowboards categry.

Visuals:
![Swatch - Taxonomy ](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/swatch-taxonomy1.png)

![Swatch - Taxonomy ](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/swatch-taxonomy2.png)

lets create a shopify section which will be a top nagivation bar.

We will want the merchant to be able to insert manu/nav links. Utilize a mega menu, Choose to keep the header sticky. Add the store logo.
