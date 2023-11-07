# Configuration Documentation

This documentation provides details about the JSON configuration for your application.

## Table of Contents

1. [oneSignal](##onesignal)
2. [currency](##currency)
3. [imageDimension](##imagedimension)
4. [imageQualityFactors](##imagequalityfactors)
5. [privacyId](##privacyid)
6. [spinner](##spinner)
7. [quickActions](##quickactions)
8. [features](##features)
9. [layouts](##layouts)
10. [language](##language)
11. [homeSections](##homesections)
12. [infoData](##infodata)
13. [colorsPallet](##colorspallet)
14. [rImages](##rimages)
15. [zCountriesOTP](##zcountriesotp)
16. [zImagesQuality](##zimagesquality)

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

The `imageQualityFactors` key is used to adjust the requested image quality from the Majtrah API for different types of images in the application. These factors allow you to control the level of image quality for specific image categories by multiplying them with the requested image dimensions.

### Sub-Elements

-   **`cart`**: Quality factor for cart-related images.
-   **`banners`**: Quality factor for banner images.
-   **`brands`**: Quality factor for brand-related images.
-   **`categories`**: Quality factor for category images.
-   **`productCard`**: Quality factor for product card images.
-   **`productDetails`**: Quality factor for product details images.
-   **`featuredCategories`**: Quality factor for featured category images.

The quality factor values range from 0 to 1, with 1 representing the highest image quality. Increasing these values will result in higher image quality when requesting images from the Majtrah API.

Example Usage:

```json
"imageQualityFactors": {
  "cart": 1,
  "banners": 1,
  "brands": 1,
  "categories": 1,
  "productCard": 1,
  "productDetails": 1,
  "featuredCategories": 1
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

-   **`titleStringKey`**: A string identifier for the title of the quick action.
-   **`subtitleStringKey`**: A string identifier for the subtitle of the quick action.

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

<!-- Explanation for the homeSections key -->

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
