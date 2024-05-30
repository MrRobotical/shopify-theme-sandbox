<a href="https://dawn-customized-sandbox.myshopify.com/">
    <img src="https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-logo.png" alt="Outdoor Gear logo" title="Outdoor Gear" align="right" height="60" />
</a>

:star: Star this on GitHub if you got any value out of this :smile:

A Shopify 2.0 theme learning sandbox, built and modified from Dawn, showcasing extensive customizations and features to enhance user experience and functionality. Explore custom fonts, dynamic banners, metafields, checkout enhancements, and SEO optimizations. Perfect for learning and demonstrating advanced Shopify theme development techniques.

![dawn-customized](https://github.com/MrRobotical/shopify-theme-sandbox/blob/main/assets/readme-homepage.png)

## Theme

- 2 Custom Fonts added - File: base.css

## HomePage

- Announcement bar. Allows the user to choose background color, font color, write multiple headlines with links and choose the timing intervals between each messages - File: custom-announcement-bar.liquid

- Custome Hero Banner. Allows merchant to add gradient headings, adjust size & color as well as complete control over position. File: custom-image-banner

- Imported a custom CSS file from the assets folder - {{ 'custom-image-banner.css' | asset_url | stylesheet_tag }}

- Transparent header with color transition when scrolled - File: header.liquid

- Animated brand marquee - File: custom-marquee.liquid

- Animated text marquee - File: custom-marquee-text.liquid

- Video Banner with text overlay - File: custom-video-banner.liquid

- Reassurance icons bar - Theme editor

- Our Story - Theme editor

## Product Page

- Added dynamic vendor link above product title - File: main.product.liquid

- Added a Block which acts as a Free Shipping threshold and outputs and icon and message to display Free Shipping messaging dependent on price threshold. - File: product-main.liquid

- Added a Block which acts as a conditional towards the Free Shipping block. It allows the merchant to enter a discount % threshold. Any products above this discount % wll not qualify for Free Shipping and will see a different icon and message displayed. - File: product-main.liquid

- Added a Block which outputs and icon and message to display a fragile product - local pick-up only messaging. The merchant can enter a tag value which will prompt this message. If the tag is present, this will overide the Free shipping msg, mentioned above - File: product-main.liquid

- Added a tabbed product description which is triggered from conditionals present in the product description such as "Description:", "Features", "Specs", "Reviews". File: main-product.liquid

- Replaced the sale badge with % off amount

## Cart Drawer

- Added a shipping progress bar - File: cart-drawer-tracker & added some settings in settings_schema.json

## Collection Page

- Replaced the sale badge with % off amount
- Added a custom banner with links input - File: custom-collections-banner.liquid

## Meta Objects & Metafields

- Added a Brands Bio Meta Object that can be inserted on product pages via a MetaField. Allows the merchant to update data in 1 place and have the updates displayed across all products.

## Checkout Branding API via GraphQL

- Added 2 custom Fonts
- Modified the input fields to only have a bottom border and be Transparent
- Modified button styling
- Increased heading sizes
- Added favicon

## Checkout UI Extensions - Upsell offer:

- Added an upsell product offer on the checkout

## Checkout UI Extensions - Post purchase survey:

- Presents the user with one survey at the Thank You page.
- Presents the user with a reviews survey at the order page.

## Checkout UI Extensions - Fragile Product banner:

- This component displays a warning banner if a product in the cart is of the product type "fragile"

## Checkout UI Extensions - Custom data via metafields:

- Added a component that outputs the products metadata on the order line if the product is fragile

## Checkout Function - Discounts

- Added a function that adds a tired discount on a specific product. 10% on 2, 15% on 3, 20% on 4

## Visuals & styling

- Added gradient blobs to Home Page background

##SEO - robots.text

- Added a custom robots.txt which excludes a specific product and excludes all products that contain the 'no-index' tag.
- Added logic on theme.liquid to add the no-index meta tag for a products with the specified tag.

##SEO - metadata

- Added logic in theme.liquid to customize the meta description for product templates. If the template is a product, the meta description will include custom text and the vendor name. Otherwise, the default description will be used.

##Shopify Flow

- Added a flow that sums up the total of a customers orders and tags them if them with a "VIP" if the total is over $1000 - Note: Needed to filter the getOrderData objct with a query of: ''customer_id:{{order.customer.legacyResourceId}}'' to narrow the data to the specific customer.