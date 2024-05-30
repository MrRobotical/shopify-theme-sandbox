# SHOPIFY THEME SANDBOX

<a href="https://dawn-customized-sandbox.myshopify.com/">
    <img src="https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-logo.png" alt="Outdoor Gear logo" title="Outdoor Gear" align="right" height="60" />
</a>

:star: Star this on GitHub if you got any value out of this :smile:

A Shopify 2.0 theme learning sandbox, built and modified from Dawn, showcasing extensive customizations and features to enhance user experience and functionality. Explore custom fonts, dynamic banners, metafields, checkout enhancements, and SEO optimizations. Perfect for learning and demonstrating advanced Shopify theme development techniques.

![dawn-customized](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-homepage.png)

## Customizations

- [Theme](#theme)
  - [Custom Fonts](#custom-fonts)
- [Home Page](#homepage)
  - [Announcement Bar](#announcement-bar)
  - [Transparent Header](#transparent-header)
  - [Custom Hero Banner](#custom-hero-banner)
  - [Animated Brand & Text Marquee](#animated-brand-and-text-marquee)
  - [Home Page](#homepage)
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

## HOMEPAGE

### Announcement Bar

Allows the user to choose background color, font color, write multiple headlines with links and choose the timing intervals between each messages - File: custom-announcement-bar.liquid

### Transparent header

Transparent header with opacity transition when scrolled - File: header.liquid
![Opacity Header](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-opacity-header.png)

### Custom Hero Banner

Allows merchants to add gradient headings, adjust size & color as well as complete control over position. File: custom-image-banner.liquid
![Gradients Banner](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-gradient-header.png)

- File: custom-image-banner.liquid

### Animated brand and text marquee

Text, font color, background color, logos can be customized via the theme settings. Animation speed is hardcoded.
![Brand Logo Marquee](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-marquee.png)

- Files: custom-marquee.liquid & custom-marquee-text.liquid

### Video Banner

The video auto plays on a loop, the section allows the merchant to enter a header, subheading and a button link.

- File: custom-video-banner.liquid

### Reassurance icons bar

- Added via the Theme editor

### Our Story

- Added via the Theme editor

## PRODUCT PAGE

### Dynamic vendor link

Vendor name appears over the product title and dynamically creates a link to the vendor collcetion.

- File: main.product.liquid

### Free Shipping Threshold

Added a Block which acts as a Free Shipping threshold and outputs and icon and message to display Free Shipping messaging dependent on price threshold. - File: product-main.liquid
![Free Shipping Threshold](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-free-shipping.png)

### Free Shipping Restriction

Added a Block which acts as a conditional towards the Free Shipping block. It allows the merchant to enter a discount % threshold. Any products above this discount % wll not qualify for Free Shipping and will see a different icon and message displayed. - File: product-main.liquid
![No Free Shipping - Discount](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-nofreeship.png)

### Fragile Item Message

Added a Block which outputs and icon and message to display a fragile product - local pick-up only messaging. The merchant can enter a tag value which will prompt this message. If the tag is present, this will overide the Free shipping msg, mentioned above - File: product-main.liquid
![Fragile Product Message](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-fragile-product.png)

### Tabbed product descriptions

Added a tabbed product description area which is triggered if conditionals are present in the product description such as "Description:", "Features", "Specs", "Reviews". File: main-product.liquid
![Tabbed Descriptions](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-tabbed.png)

### Sale Badge

Replaced the sale badge with % off amount

## COLLECTION PAGE

Replaced the sale badge with % off amount + Added a custom banner with links input
![Shipping Progress Bar](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-ship-progress-bar.png)

- File: custom-collections-banner.liquid

## CART DRAWER

Added a shipping progress bar which outputs various messaging depending on cart amount.

- File: cart-drawer-tracker & added some settings in settings_schema.json

## CHECKOUT BRANDING API

- Added 2 custom Fonts
- Modified the input fields to only have a bottom border and be Transparent
- Modified button styling
- Increased heading sizes
- Added favicon

## CHECKOUT UI EXTENTIONS

### Upsell offer:

- Added an upsell product offer on the checkout

### Post purchase survey:

- Presents the user with one survey at the Thank You page.
- Presents the user with a reviews survey at the order page.

### Fragile text banner:

- This component displays a warning banner if a product in the cart is of the product type "fragile"

### Custom data via metafields:

- Added a component that outputs the products metadata on the order line if the product is fragile

## CHECKOUT FUNCTIONS

### Tiered Discounts

Added a function that adds a tired discount on a specific product. 10% on 2, 15% on 3, 20% on 4.

## SEO AND METADATA

- Added a custom robots.txt which excludes a specific product and excludes all products that contain the 'no-index' tag.

- Added logic on theme.liquid to add the no-index meta tag for a products with the specified tag.

- Added logic in theme.liquid to customize the meta description for product templates. If the template is a product, the meta description will include custom text and the vendor name. Otherwise, the default description will be used.

## METAFIELDS AND OBJECTS

- Added a Brands Bio Meta Object that can be inserted on product pages via a MetaField. Allows the merchant to update data in 1 place and have the updates displayed across all products.

## SHOPIFY FLOW

- Added a flow that sums up the total of a customers orders and tags them if them with a "VIP" if the total is over $1000 - Note: Needed to filter the getOrderData objct with a query of: ''customer_id:{{order.customer.legacyResourceId}}'' to narrow the data to the specific customer.

## VISUALS AND STYLINGS

- Added gradient blobs to Home Page background
