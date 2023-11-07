# Configuration Documentation

This documentation provides details about the JSON configuration for your application.

## Table of Contents

1. [oneSignal](#onesignal)
2. [currency](#currency)
3. [imageDimension](#imagedimension)
4. [imageQualityFactors](#imagequalityfactors)
5. [privacyId](#privacyid)
6. [spinner](#spinner)
7. [quickActions](#quickactions)
8. [features](#features)
9. [layouts](#layouts)
10. [language](#language)
11. [homeSections](#homesections)
12. [infoData](#infodata)
13. [colorsPallet](#colorspallet)
14. [rImages](#rimages)
15. [zCountriesOTP](#zcountriesotp)
16. [zImagesQuality](#zimagesquality)

## `oneSignal`

The `oneSignal` key is used to specify the OneSignal App ID, which is essential for enabling push notifications and other features provided by the OneSignal service.

### Value

-   **OneSignal App ID**: Replace this with your OneSignal App ID.

Example Usage:

```json
"oneSignal": "your-onesignal-app-id"
```

## `currency`

The `currency` key is used to specify the initial currency code for the application. This currency code is typically used as the default currency for displaying prices and performing currency-related operations.

### Value

-   **Initial Currency Code**: Replace this with the desired initial currency code, such as "SAR" (Saudi Riyal).

Example Usage:

```json
"currency": "SAR"
```

## `imageDimension`

The `imageDimension` key is used to specify the global header for image dimensions within the Majtrah API. It determines the default dimensions that should be applied to images retrieved from the API.

### Value

-   **Global Header for Image Dimensions**: Replace this with the desired image dimension format. The default value is "600x600."

Example Usage:

```json
"imageDimension": "600x600"
```

## `imageQualityFactors`

The `imageQualityFactors` key allows you to control the quality of images used in various parts of the application. The value for each factor can be adjusted to control image quality. The scale for these factors represents the level of quality, where 1.0 represents normal image quality. Values above 1.0 increase quality, and values below 1.0 decrease quality.

Please note that these quality factors are primarily related to Matjrah API requests and are specifically applicable when the platform is set to "matjrah."

### Factors

- **`cart`**: A factor affecting the image quality for cart-related images.
- **`banners`**: A factor affecting the image quality for banners.
- **`brands`**: A factor affecting the image quality for brand-related images.
- **`categories`**: A factor affecting the image quality for category-related images.
- **`productCard`**: A factor affecting the image quality for product card images.
- **`productDetails`**: A factor affecting the image quality for product details images.
- **`featuredCategories`**: A factor affecting the image quality for featured category images.

### Example Usage

```json
"imageQualityFactors": {
    "cart": 2.0, // 100% extra quality
    "banners": 1.0, // Normal quality
    "brands": 0.5, // 50% less quality
    "categories": 1.5, // 50% extra quality
    "productCard": 1.0, // Normal quality
    "productDetails": 1.2, // 20% extra quality
    "featuredCategories": 1.0 // Normal quality
}
```

## `privacyId`

The `privacyId` key is used to specify the privacy page ID that will be displayed on the signup screen. Users are typically required to read and agree to the privacy policy or terms of service before submitting the signup form.

### Value

-   **Privacy Page ID**: Replace this with the desired privacy page ID. The default value for Majtrah is 5.

Example Usage:

```json
"privacyId": 5
```

## `spinner`

The `spinner` key is used to specify the type of spinner that should be displayed within the application. A spinner is a visual indicator used to convey that a process is underway. This key allows you to choose the style of the spinner to be used.

### Possible Values

The `spinner` key can take one of the following values:

-   `false` (default spinner): The default spinner is used.
-   `"CircleFlip"`
-   `"Bounce"`
-   `"Wave"`
-   `"WanderingCubes"`
-   `"Pulse"`
-   `"ChasingDots"`
-   `"ThreeBounce"`
-   `"Circle"`
-   `"9CubeGrid"`
-   `"FadingCircle"`
-   `"FadingCircleAlt"`

Example Usage:

```json
"spinner": "Wave"
```

## `quickActions`

The `quickActions` key is an array that allows you to define quick actions within the application. These quick actions are typically accessible when a user holds down on the app icon.

### Sub-Elements (Object Structure)

Each object within the `quickActions` array has the following sub-elements:

-   **`type`**: Specifies the type of quick action, which determines its behavior. It can take one of the following values:

    -   `home`: Opens the home screen.
    -   `search`: Opens the search screen.
    -   `orders`: Opens the orders screen.
    -   `cart`: Opens the shopping cart.
    -   `product:9044`: Opens the product screen and attempts to load the product with the specified ID (replace `9044` with the actual product identifier).
    -   `query:{}`: Opens the products listing screen and performs a product search based on the provided query object (if applicable).

-   **`icon`**: The icon associated with the quick action. It should be one of the following enum values:

    -   `home`
    -   `orders`
    -   `cart`
    -   `search`
    -   `product`
    -   `query`

- **`titleStringKey`**: A string identifier for the title of the quick action. This string identifier can be set in the `language.variableStrings` object for different languages, allowing you to customize the title text based on the selected language.

- **`subtitleStringKey`**: A string identifier for the subtitle of the quick action. Similar to the `titleStringKey`, this string identifier can be set in the `language.variableStrings` object for different languages, enabling you to customize the subtitle text based on the selected language.


### Example Usage

```json
"quickActions": [
  {
    "type": "orders",
    "icon": "orders",
    "titleStringKey": "myOrders",
    "subtitleStringKey": "ordersSub"
  },
  {
    "type": "home",
    "icon": "home",
    "titleStringKey": "homeTitle",
    "subtitleStringKey": "homeSub"
  },
  {
    "type": "product:9044",
    "icon": "product",
    "titleStringKey": "productTitle",
    "subtitleStringKey": "productSub"
  },
  // Additional quick action objects...
]
```

## `features`

The `features` key is an object containing boolean values that control various features and functionalities of the application. Each sub-element corresponds to a specific feature, and the boolean value indicates whether the feature is enabled (`true`) or disabled (`false`).

### Sub-Elements

-   **`showHomeLoading`**: Determines whether the home screen displays a loading indicator during data retrieval.
-   **`productCardCarousel`**: Controls the use of a carousel for displaying product cards.
-   **`flashSale`**: Enables or disables the display of flash sale items.
-   **`addressLocation`**: Allows the use of address-based location services.
-   **`showBrandsTab`**: Controls the visibility of a "Brands" tab.
-   **`showBrandSearch`**: Enables or disables the brand search functionality.
-   **`showCategoriesTab`**: Determines whether the "Categories" tab is visible.
-   **`wishlist`**: Controls the availability of a wishlist feature.
-   **`barcode`**: Enables or disables barcode scanning functionality.
-   **`search`**: Determines whether the search feature is available.
-   **`confirmCOD`**: Controls the confirmation of cash-on-delivery (COD) orders.
-   **`coupon`**: Enables or disables the use of coupons in the application.
-   **`rewards`**: Determines whether the rewards feature is enabled.

Each sub-element can be set to `true` to enable the corresponding feature or `false` to disable it.

Example Usage:

```json
"features": {
  "showHomeLoading": true,
  "productCardCarousel": true,
  "flashSale": true,
  "addressLocation": true,
  "showBrandsTab": true,
  "showBrandSearch": true,
  "showCategoriesTab": true,
  "wishlist": true,
  "barcode": true,
  "search": true,
  "confirmCOD": true,
  "coupon": true,
  "rewards": true
}
```

## `layouts`

The `layouts` key contains configuration settings for various layout elements within the application. These settings allow you to customize the appearance and behavior of different UI components.

### Sub-Elements

#### `header`

The `header` layout configuration controls the header section of the application.

-   **`logoWidthFactor`**: Determines the logo's width as a factor of the header's width.
-   **`logoResizeMode`**: Specifies how the logo should be resized within the header.
-   **`logoPositionInContainer`**: Defines the logo's position within the header container (options: `center`, `start`, `end`).
-   **`sideAligned`**: Specifies whether the header should be side-aligned.

#### `intro`

The `intro` layout configuration controls the introductory section of the application.

-   **`animation`**: Defines the introductory animation style (options: `none`, `pulse`, `in_out`, `scaleout`).
-   **`width`**: Specifies the width of the introductory section as a percentage of the screen width.
-   **`height`**: Specifies the height of the introductory section as a percentage of the screen height.
-   **`bg_color`**: Sets the background color for the introductory section.

#### `home`

The `home` layout configuration controls the home screen.

-   **`tabPaddingH`**: Sets the horizontal padding for tabs.
-   **`tabPaddingV`**: Sets the vertical padding for tabs.
-   **`showSwiperIndex`**: Determines whether the Swiper index is displayed.

#### `productCard`

The `productCard` layout configuration controls the appearance of product cards.

-   **`style`**: Specifies the style of product cards (options: `sharp`, `simple`, `rounded`, `soft`).
-   **`homeSize`**: Defines the size of product cards on the home screen (options: `xsmall`, `small`, `default`, `large`).
-   **`listSize`**: Defines the size of product cards in lists (options: `xsmall`, `small`, `default`, `large`).
-   **`resizeMode`**: Specifies how product card images are resized (e.g., `cover`).
-   **`imageRatio`**: Sets the image aspect ratio.
-   **`border`**: Enables or disables borders on product cards.
-   **`addToCart`**: Determines whether an "Add to Cart" button is displayed on product cards.
-   **`quantityPicker`**: Specifies whether a quantity picker is available.

#### `categories`

The `categories` layout configuration controls the presentation of product categories.

-   **`imageRatio`**: Sets the image aspect ratio for category images.
-   **`showSubcategories`**: Determines whether subcategories are displayed.
-   **`showParentImage`**: Specifies when to show the parent category image (options: `always`, `selection`, `never`).
-   **`subcategoriesColumns`**: Defines the number of columns for subcategories (options: `1`, `2`, `3`).
-   **`titlePosition`**: Sets the position of the category title (options: `none`, `below`, `black`, `white`).

#### `brands`

The `brands` layout configuration controls the presentation of brands.

-   **`alpha`**: Specifies whether brands are displayed alphabetically.
-   **`showTitle`**: Determines whether brand titles are shown.
-   **`imageRatio`**: Sets the image aspect ratio for brand images.
-   **`columns`**: Defines the number of columns for brands (only applicable if `alpha` is `false`, options: `1`, `2`, `3`).

#### `productDetails`

The `productDetails` layout configuration controls the product details view.

-   **`optionPrice`**: Determines whether option prices are displayed.
-   **`actionBar`**: Specifies whether the action bar is shown.
-   **`showRelated`**: Controls the visibility of related products.
-   **`resizeMode`**: Specifies how product images are resized.
-   **`relatedSection`**: Configuration for the related products section.
    -   **`stringKey`**: A unique string identifier.
    -   **`iconKey`**: The icon associated with the section.
    -   **`style`**: Sets the style of the section.
    -   **`colors`**: Configuration for section colors.
        -   **`primary`**: The primary color.
        -   **`secondary`**: The secondary color.
-   **`ctaIcon`**: Determines whether a call-to-action (CTA) icon is displayed.
-   **`ctaType`**: Specifies the type of CTA (options: `cart`, `quantity`, `null`).

#### `tabBar`

The `tabBar` layout configuration controls the tab bar.

-   **`style`**: Defines the style of the tab bar (options: `simple`, `rounded`, `top`, `sharp`).
-   **`titleShown`**: Specifies when tab titles are shown (options: `always`, `never`, `unselected`).

#### `account`

The `account` layout configuration controls the account section.

-   **`buttons`**: Specifies the positioning of account buttons (options: `out`, `in`, `mid`).

These layout settings allow you to customize the appearance and behavior of various UI components within the application, providing flexibility to tailor the user experience according to your requirements.

## `language`

The `language` key allows you to configure language-related settings and provides language-specific strings for the application.

### Configuration Settings

- **`default`**: Specifies the default language for the application. It can be set to either:
  - `ar`: Arabic
  - `en`: English

- **`changeable`**: A boolean value that determines whether users can change the application's language. When set to `true`, users can switch between the configured languages. When set to `false`, the application remains in the default language.

- **`variableStrings`**: An object that holds language-specific strings for different parts of the application.

> Note: Any object within the configuration, regardless of its location, that includes a `stringKey` key and values, should have corresponding values in the `language.variableStrings` object. For example, if a configuration object has a `titleStringKey` with a value of "latest," ensure that both `language.variableStrings.en.latest` and `language.variableStrings.ar.latest` contain the corresponding string values. This allows the application to read the string values from the `variableStrings` based on the selected language.

### Example Usage

```json
"language": {
  "default": "ar", // ar | en
  "changeable": true,
  "variableStrings": {
    "ar": {
      "announceMessage": "عروض حصرية بمناسبة فوز منتخبنا الوطني على الأرجنتين في كأس العالم قطر ٢٠٢٢",
      "fcategories": "الاقسام المميزة",
      "lastPiece": "آخر قطعة",
      "latest": "آخر ما ورد إلينا"
    },
    "en": {
      "announceMessage": "Exclusive offers celebrating our national team's victory over Argentina in the 2022 FIFA World Cup Qatar",
      "fcategories": "Featured Categories",
      "lastPiece": "Last Piece",
      "latest": "Latest New products"
    }
  }
}
```


## `homeSections`

The `homeSections` key represents an array of tabbed sections on the home screen, each with its own title and content sections.

- Each tab is defined as an object with the following properties:

  - **`stringKey`**: A string identifier for the tab's title. You can set the value for different languages using the `language.variableStrings` object.

  - **`sections`**: An array of elements that make up the content of the tab. These elements can include various section types, each with its own configuration.

### Example Usage

```json
"homeSections": [
  {
    "stringKey": "tabTitleStringKey1",
    "sections": [
      // Sections for the first tab
    ]
  },
  {
    "stringKey": "tabTitleStringKey2",
    "sections": [
      // Sections for the second tab
    ]
  }
]
```

### Separator Section

The "Separator" section is used to add a visual separator within a tab of the home screen.

- **`type`**: The type of section, which is "separator"

- **`stringKey`**: A string identifier for the separator section's title. You can set the value for different languages using the `language.variableStrings` object.

- **`iconKey`**: A string identifier for the icon used in the separator section. You can reference icons from the `rImages` object.

- **`style`**: The style of the separator. You can customize its alignment, and the available options are "basic," "top," "start," or "center."

- **`colors`**: A set of colors for the separator. Customize the primary and secondary colors, using either named colors or hash values.

Example Usage:

```json
{
  "type": "separator",
  "stringKey": "separatorTitleStringKey",
  "iconKey": "separatorIcon",
  "style": "center",
  "colors": {
    "primary": "blue", // or "#0000FF"
    "secondary": "green" // or "#008000"
  }
}
```

### Featured Categories Section

The "Featured Categories" section is used to display a set of featured categories within a tab on the home screen.

- **`type`**: The type of section, which is "featured_categories"

- **`style`**: The style of the featured categories. You can choose from different styles, including "square," "circle," "rectlight," or "rectdark."

- **`direction`**: The direction in which the featured categories are displayed. You can set it as "column" or "row" to control the layout.

- **Data Source**: Choose one of the following options to define the source of featured categories:

  - **`parent`**: Use the `parent` property to show the children of a specific parent category identified by its ID.

  - **`ids`**: Provide an array of category IDs to specify which categories should be displayed as featured.

  - **`level`**: Set the `level` property to determine the level of categories to be shown as featured.

Examples Usage:

```json
{
  "type": "featured_categories",
  "style": "rectdark",
  "direction": "row",
  "parent": 103
}
// OR
{
  "type": "featured_categories",
  "style": "circle",
  "direction": "column",
  "ids": [23, 123, 421]
}
// OR
{
  "type": "featured_categories",
  "style": "rectlight",
  "direction": "row",
  "level": 1
}
```

### Popup Section

The "Popup" section is used to display a popup image in a modal when the app starts up, and a specific tab on the home screen is selected. This popup can be linked to various actions or content.

- **`type`**: The type of section, which is "popup"

- **`id`**: An identifier used in preventing the display of the same popup locally. This value helps ensure that the same popup is not shown repeatedly to users.

- **`hours`**: The number of hours to hide the popup for after it is shown. Users will not see the popup again within this time frame.

- **`imageHeightRatio`**: The height ratio of the popup image. A value of 1 indicates a square image. Adjust this value to control the image's aspect ratio.

- **`image`**: The URL of the popup image that will be displayed in the modal.

- **`link_type`**: The type of action or content that the popup is linked to. Possible values include:
  - "home": To load a custom screen (link value expected to be a full home configuration).
  - "manufacturer": To load the manufacturer products screen (link value expected to be the `manufacturer_id`).
  - "product": To load the product screen (link value expected to be the `product_id`).
  - "list": To load a product listing screen (link value expected to be a query object).
  - "category": To load products listing in subcategories (link value expected to be `categoryId`).
  - "internal": To load an in-app web view (link value expected to be a URL).
  - "external": To load a browser (link value expected to be a URL).
  - "copy": To copy something to the clipboard (e.g., "coupon text").

- **`link_value`**: The specific value or identifier associated with the `link_type`, depending on the selected type.

Example Usage:

```json
{
  "type": "popup",
  "id": 234,
  "hours": 24,
  "imageHeightRatio": 0.75,
  "image": "https://assets.matjrah.store/images/1339/image/cache/catalog/1677055847-mBNlFGQZaRhXmQKGJHFHfWMAa7TWhOrvnBN6KmbN-max-828.jpg",
  "link_type": "product",
  "link_value": 9029
}
```

### Timer Section

The "Timer" section is used to display a countdown timer for a sale event. Users are encouraged to take action before the timer expires.

- **`type`**: The type of section, which is "timer"

- **`datetime`**: The date and time when the timer should end, in the format "YYYY-MM-DD HH:mm." Users are encouraged to take action before this time expires.

- **`titleStringKey`**: A string identifier for the title of the timer. This string identifier can be used to retrieve the localized text for the timer's title. It ensures that the text is displayed in the user's preferred language.

- **`navTitleStringKey`**: A string identifier for the navigation title related to the timer. Like the titleStringKey, this identifier is used to retrieve localized text.

- **`image`**: The URL of the image associated with the timer. This image is typically used to visually represent the sale event.

- **`imageWidthRatio`**: The width ratio of the timer image, allowing you to control the image's aspect ratio.

- **`imageHeightRatio`**: The height ratio of the timer image, enabling you to control the image's aspect ratio.

- **`colors`**: Define the color scheme for the timer, including background colors, text colors, and more.

- **`link_type`**: The type of action or content that the timer is linked to. Possible values include:
  - "home": To load a custom screen (link value expected to be a full home configuration).
  - "manufacturer": To load the manufacturer products screen (link value expected to be the `manufacturer_id`).
  - "product": To load the product screen (link value expected to be the `product_id`).
  - "list": To load a product listing screen (link value expected to be a query object).
  - "category": To load products listing in subcategories (link value expected to be `categoryId`).
  - "internal": To load an in-app web view (link value expected to be a URL).
  - "external": To load a browser (link value expected to be a URL).
  - "copy": To copy something to the clipboard (e.g., "coupon text").

- **`link_value`**: The specific value or identifier associated with the `link_type`, depending on the selected type.

Example Usage:

```json
{
  "type": "timer",
  "datetime": "2023-08-25 23:25",
  "titleStringKey": "ramadanOffer",
  "navTitleStringKey": "ramadanOfferTitle",
  "image": "https://rahatystore.matjrah.store/images/1419/image/catalog/2023/web%20banners/1672664683-1.gif",
  "imageWidthRatio": 0.9,
  "imageHeightRatio": 0.5,
  "colors": {
    "background": "#451458",
    "time_text": "#00207c",
    "title": {
      "text": "#00207c",
      "background": "#451458"
    },
    "subtitle": {
      "text": "#00207c",
      "background": "#451458"
    }
  },
  "link_type": "home",
  "link_value": []
}
```

### Home Announcer Section

The "Home Announcer" section is used to display an announcement message on the home screen, providing important information or updates to users.

- **`type`**: The type of section, which is "announce."

- **`stringKey`**: A string representing the key for the associated text content. This key should have corresponding values in the `language.variableStrings` object for language localization.

- **`iconKey`**: A unique key that represents the icon associated with the announcement. You can use this key to fetch the icon's URL from the "rImages" object.

- **`colors`**: Define the color scheme for the announcer, including background colors, text colors, and icon tint.

- **`title`**: The title of the screen, web view, or product listing that is navigated to when the user interacts with the announcer.

- **`link_type`**: The type of action or content that the announcer is linked to. Specify one of the following values:
  - "home": To load a custom screen (link value expected to be a full home configuration).
  - "manufacturer": To load the manufacturer products screen (link value expected to be the `manufacturer_id`).
  - "product": To load the product screen (link value expected to be the `product_id`).
  - "list": To load a product listing screen (link value expected to be a query object).
  - "category": To load products listing in subcategories (link value expected to be `categoryId`).
  - "internal": To load an in-app web view (link value expected to be a URL).
  - "external": To load a browser (link value expected to be a URL).
  - "copy": To copy something to the clipboard (e.g., "coupon text").

- **`link_value`**: The specific value or identifier associated with the `link_type`, depending on the selected type.

Example Usage:

```json
{
  "type": "announce",
  "stringKey": "announceMessage",
  "iconKey": "heart",
  "colors": {
    "background": "green",
    "text": "cyan",
    "iconTint": "blue"
  },
  "title": "123",
  "link_type": "home",
  "link_value": []
}
```

### Product Section

The "Product Section" is a versatile section designed to showcase a collection of products based on customizable criteria.

- **`stringKey`**: A string representing the key for the associated text content. This key should have corresponding values in the `language.variableStrings` object for language localization.

- **`iconKey`**: A unique key that represents the icon associated with the product section. You can use this key to fetch the icon's URL from the "rImages" object.

- **`style`**: The style of the product section, which can be one of the following:
  - "basic": A basic style.
  - "top": A top-aligned style.
  - "start": A start-aligned style.
  - "center": A center-aligned style.

- **`colors`**: Define the color scheme for the product section, including primary and secondary colors.

- **`isGrid`**: A boolean value to determine whether the product display is in a grid format (true) or not (false).

- **`limit`**: The maximum number of products to display in the section.

- **`query`**: A query object used to customize the criteria for product selection. The `query` object can include filters, sorting options, and other parameters.

Example Usage:

```json
{
  "stringKey": "lastPiece",
  "iconKey": "star",
  "style": "center",
  "colors": {
    "primary": "purple",
    "secondary": "purple"
  },
  "isGrid": true,
  "limit": 10,
  "query": {
    // Customize the query object to filter, sort, and select products as needed.
  }
}
```

### Banner Section

The "Banner Section" is designed to display a collection of banners, which can be used for various promotional purposes.

- **`banner_id`**: A unique identifier for the banner section.

- **`displayAs`**: The display style of the banners, which can be one of the following:
  - "carousel": Banners are displayed in a carousel.
  - "row": Banners are displayed in a row.
  - "scroll": Banners are displayed with horizontal scrolling.

- **`data`**: Contains an array of banner objects with details for each banner. Each banner includes the following properties:
  - **`title`**: The title of the banner.
  - **`link_type`**: The type of link associated with the banner (e.g., "product," "category," "external," etc.).
  - **`link_value`**: The value associated with the link type (e.g., product ID, category ID, URL, etc.).
  - **`image`**: The URL of the banner image.

- **`showSwiperIndex`**: A boolean value indicating whether to display the index of the current banner in a swiper component.

- **`ratio`**: The height ratio of the banner. A value of 1 represents a square banner, while other values adjust the banner's height accordingly.

- **`resizeMode`**: The image resizing mode, which can be one of the following:
  - "cover": The image covers the entire banner area, possibly cropping parts.
  - "contain": The image fits within the banner area without cropping.

- **`justifyContent`**: The horizontal alignment of the banner within its container. It can be set to "center" to center-align the banner horizontally.

- **`widthRatio`**: The width ratio of the banner, which determines the width of the banner as a percentage of the screen width.

- **`marginVertical`**: The vertical margin or spacing around the banner.

Example Usage:

```json
{
  "banner_id": "static",
  "displayAs": "row",
  "data": {
    "banners": [
      {
        "title": "",
        "link_type": "",
        "link_value": "",
        "image": "https://matjrah-app.store/images/1233/image/cache/catalog/1667402811-BA09956D-5A25-4167-90ED-856D1932EF5C-max-375.jpeg"
      },
      // Additional banners here...
    ],
    "showSwiperIndex": true,
    "ratio": 1,
  },
  "resizeMode": "contain",
  "justifyContent": "center",
  "widthRatio": 0.95,
  "marginVertical": 12
}
```

### Story Section

The "story" section is used to define a collection of images or videos presented in a story format within your app. This section is commonly used for promotional content, announcements, or engaging multimedia presentations.

#### Structure

- **type**: Specifies that this is a "story" section.
- **data**: An array of story items, each representing a separate story.
  - **id**: A unique identifier for the story.
  - **image**: The cover image for the story, typically displayed as a thumbnail or introductory image.
  - **name**: A name or title for the story, which may provide context or a brief description.
  - **duration**: The default duration (in seconds) for all stories inside this section. This duration determines how long each image or video is displayed in the story.
  - **is_special**: Indicates if the story is special or featured. Special stories might be highlighted or treated differently within the app.
  - **images**: An array of images or videos within the story, creating a sequence of content.
    - **image**: URL for an image in the story, which is typically a static image.
    - **video**: URL for a video in the story, allowing the inclusion of multimedia elements.
    - **duration**: Custom duration (in seconds) for the individual media item. This can override the default duration for specific images or videos.
    - **link_type**: Specifies the type of link for the image or video, such as "product," "internal," "external," or "copy."
    - **link_value**: Provides the value associated with the link type, which might be a product ID, a URL, or other relevant information.

Example Usage:

```json
{
  "type": "story",
  "data": [
    {
      "id": 1,
      "image": "https://example.com/story1_cover.jpg",
      "name": "Story 1",
      "duration": 10,
      "is_special": true,
      "images": [
        {
          "image": "https://example.com/story1_image1.jpg",
          "duration": 15,
          "link_type": "product",
          "link_value": 9029
        },
        {
          "video": "https://example.com/story1_video1.mp4",
          "duration": 30,
          "link_type": "internal",
          "link_value": "https://example.com/internal-page"
        },
        {
          "image": "https://example.com/story1_image2.jpg",
          "duration": 8,
          "link_type": "external",
          "link_value": "https://example.com/external-link"
        }
      ]
    },
    {
      "id": 2,
      "image": "https://example.com/story2_cover.jpg",
      "name": "Story 2",
      "duration": 12,
      "images": [
        {
          "image": "https://example.com/story2_image1.jpg",
          "link_type": "product",
          "link_value": 9030
        },
        {
          "image": "https://example.com/story2_image2.jpg",
          "link_type": "copy",
          "link_value": "ABC123"
        }
      ]
    }
  ]
}

```


## `infoData`

The `infoData` key is an array of objects that are used to define various informational elements within the application. These elements can include buttons, internal URL paths, external URLs, predefined action buttons, and separators.

### Array Structure

Each object within the `infoData` array has the following possible properties:

- **`stringKey`**: A string representing the key for the associated text content. This key should have corresponding values in the `language.variableStrings` object for language localization.

- **`iconKey`**: A string indicating the key for the associated icon. This key is typically used to reference icons from the `rImages` object.

- **`id`**: An identifier for the information page that should be loaded when the user presses the element. This `id` corresponds to a specific information page.

- **`path`**: Specifies the internal URL path. When used, it opens the specified path in a WebView, typically constructed as `baseURL/path`.

- **`url`**: Specifies an external URL. When used, it opens the provided URL in an external browser.

- **`onPress`**: A predefined action for the button. Possible values include "share" or "social," indicating specific actions to be performed when the button is pressed.

- **`hideArrow`**: A boolean value that determines whether to hide an arrow or indicator associated with the element.

- **`type`**: For separators, it specifies the type as "separator."

### Example Usage

```json
"infoData": [
  {
    "stringKey": "aboutApp",
    "iconKey": "wave",
    "id": 9
  },
  {
    "stringKey": "aboutApp",
    "iconKey": "wave",
    "path": "about_us"
  },
  {
    "stringKey": "aboutApp",
    "iconKey": "wave",
    "url": "https://facebook.com"
  },
  {
    "stringKey": "shareApp",
    "iconKey": "share",
    "onPress": "share",
    "hideArrow": true
  },
  {
    "type": "separator",
    "stringKey": "lastPiece"
  }
]
```

## `colorsPallet`

The `colorsPallet` key defines a complex object that specifies the colors used throughout the application. This object is generated by a complex logic and allows customization of color values while preserving the predefined keys.

### Characteristics

-   **Keys**: The keys within the `colorsPallet` object are predefined and should not be modified. They represent specific color attributes and elements used within the app.

-   **Values**: The values associated with the predefined keys can be edited to customize the color scheme of the application. You have the flexibility to change color values while maintaining the key structure.

### Example Usage

```json
"colorsPallet": {
  "primaryColor": "#FF5733", // Editable
  "secondaryColor": "#6699FF", // Editable
  "textColor": "#333333", // Editable
  "background": "#FFFFFF", // Editable
  // Additional predefined keys...
}
```

## `rImages`

The `rImages` key is an object that holds a collection of remote images and icons for use within the application. Each key within this object should be unique, and the corresponding value should be a valid URL pointing to a PNG, JPG, or GIF image.

### Key Structure

-   **Keys**: Each key within the `rImages` object should be unique and serves as a reference to a specific image or icon within the collection.

-   **Values**: The values associated with the keys should be valid URLs pointing to PNG, JPG, or GIF image files.

### Example Usage

```json
"rImages": {
  "iconKey1": "https://example.com/icon1.png",
  "iconKey2": "https://example.com/icon2.jpg",
  "backgroundImage": "https://example.com/background.jpg",
  "logoImage": "https://example.com/logo.png",
  // Additional image and icon references...
}
```

## `zCountriesOTP`

The `zCountriesOTP` key is an array of countries that are allowed for use within the application for sending OTP (One-Time Password) and validating mobile numbers. Each entry in the array represents a specific country and its associated attributes.

This object is used when the platform is set to `Zid`.

### Sub-Elements (Object Structure)

Each object within the `zCountriesOTP` array has the following sub-elements:

-   **`country_id`**: A unique identifier for the country. This ID is used for selection purposes.

-   **`phone_prefix`**: The phone prefix or country code for the respective country.

-   **`phone_length`**: The expected length of mobile phone numbers in that country.

-   **`flag`**: The URL pointing to the flag image of the country.

### Example Usage

```json
"zCountriesOTP": [
  {
    "country_id": 1,
    "phone_prefix": "966",
    "phone_length": 9,
    "flag": "https://example.com/flags/sar.png"
  },
  {
    "country_id": 2,
    "phone_prefix": "1",
    "phone_length": 10,
    "flag": "https://example.com/flags/us.png"
  },
  // Additional country entries...
]
```

## `zImagesQuality`

The `zImagesQuality` key defines image quality settings specific to the `Zid` platform. This configuration allows you to specify the quality of images used in various parts of the application.

### Characteristics

- **Platform**: The `zImagesQuality` object is intended for use when the platform is set to `Zid`.

- **Values**: Each key within the `zImagesQuality` object corresponds to a specific area of the application, and its value indicates the desired image quality for that area. The available options for image quality include:

### Available Options

- `productCard`: Specifies the image quality for product card images. This key can take one of the following values:
  - `full_size`
  - `large`
  - `medium`
  - `thumbnail`
  - `small`

- `productDetails`: Specifies the image quality for product details images. This key can take one of the following values:
  - `full_size`
  - `large`
  - `medium`
  - `thumbnail`
  - `small`

- `cart`: Specifies the image quality for cart-related images. This key can take one of the following values:
  - `fullSize`
  - `large`
  - `medium`
  - `thumbnail`
  - `small`

- `orderDetails`: Specifies the image quality for order details-related images. This key can take one of the following values:
  - `fullSize`
  - `large`
  - `medium`
  - `thumbnail`
  - `small`

### Example Usage

```json
"zImagesQuality": {
  "productCard": "small", // small
  "productDetails": "full_size", // full_size
  "cart": "fullSize", // fullSize
  "orderDetails": "medium", // medium
}
```
```json
"zImagesQuality": {
  "productCard": "small", // fullSize | large | medium | thumbnail | small
  "productDetails": "full_size", // fullSize | large | medium | thumbnail | small
  "cart": "fullSize", // fullSize | large | medium | thumbnail | small
  "orderDetails": "fullSize" // fullSize | large | medium | thumbnail | small
}
```
