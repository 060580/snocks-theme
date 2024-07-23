# Preorder sold out products in Shopify Theme Dawn

##Demo links
###Sold out Preorder Product:
https://060580-development.myshopify.com/products/socke

###Product with Variants:
https://060580-development.myshopify.com/products/unterhose

* S: available
* M: sold out
* L: Preorder available

## Changed Files 
layout/theme.liquid
snippets/buy-buttons.liquid
snippets/product-variant-picker.liquid
assets/product-form.js
assets/product-info.js
locales/en.default.json
locales/de.json

## Changes 

### layout/theme.liquid

Added translation string in `window.variantStrings` to make them accessiable for javascript.

### snippets/buy-buttons.liquid

Added a check if a product is able to preorder on intial pageload if the current variant is available and the quantity is lower than 1. 
Added hidden inputfield to store preorder information on line items in cart and checkout. 
Added case for preorder at add to cart button. 
Added paragraph for preorder information text. 

### snippets/product-variant-picker.liquid

Added additional information `inventory_quantity` and `inventory_policiy` to make a check for preorder in javascript possible. 

### assets/product-form.js

Extended `toggleSubmitButton` for preorder case. 

### assets/product-info.js

Added functions to get data from the template about inventory policy and inventory quantity. 
Added function to toggle preorder not below add to cart button. 
Adjusted `handleUpdateProductInfo` function: 
* call the functions to get quantity and inventory policy.
* setting variable `isPreoder` with default of `false`. 
* setting variable `variantPreorderInputValue` for the hidden input field. 
* check if current variant is able to preorder in case quantity is lower than 1 and inventory policy is set to continue.  
* if check above is true set `isPreoder` to `true` and `variantPreorderInputValue` to the preoder note text. 
* passing `isPreorder` to the `toggleSubmitButton` function. 
Added function to update hidden input field for preorder information. 

### locales/en.default.json & locales/de.json
Added needed translations. 
`products.product.preorder`
`products.product.preorder_note`

## Future possible improvements
* Setting a flexbile preorder date, which is stored at `variant.next_incoming_date`. Adjustment of translation strings and javascript needed. 
* Optimized visualisation of preorder not below Add to Cart Button. Set individual class name in preperation. 
