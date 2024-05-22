# (TEMPLATE) Discount Limitations in Different Collections

## Overview

This document discusses the limitations encountered when implementing discount codes in different Shopify collections. The primary issue involves the inability to apply multiple discounts simultaneously to products that belong to more than one collection.

## Problem

When attempting to apply different discount codes to products within various collections, Shopify's current discount system restricts the application of multiple discounts to a single product. This limitation complicates scenarios where a product needs to be part of multiple promotional campaigns simultaneously.

## Details

### Context

- **Discount Codes**: Discounts such as "1free", "2free", and "3free" need to be applied based on the number of items added to the cart from specific collections.
- **Collections**: Products belong to collections like "bogo-sale-collection" and "dip-powder-collection". Both collections may contain the same products.
- **Conflict**: Applying a discount code like "1free" to products in "bogo-sale-collection" affects those in "dip-powder-collection", causing conflicts since Shopify doesn't support applying multiple discounts to the same product.

### Example

1. If 2-3 products from the "bogo-sale-collection" are added to the cart, the "1free" discount code should be applied.
2. For 4-5 products, the "2free" code should be used, replacing the "1free" code.
3. Similarly, for 6-7 products, "3free" should replace "2free".

However, if the same product is also in the "dip-powder-collection", it cannot simultaneously benefit from a discount like "2jars" applied to that collection.

## Solution Attempt

### Suggested Approaches

1. **Single Discount Application**: Apply only one discount at a time, prioritizing the most beneficial discount for the customer.
2. **JavaScript Implementation**: Use JavaScript to dynamically apply and remove discount codes based on the template and product collection.
3. **Custom App**: Develop a custom Shopify app to manage and prioritize discounts for products in multiple collections.

### Challenges

- **Discount Code Field**: The Dawn theme's default discount field needs modification to handle custom logic.
- **Priority Handling**: Ensuring the correct discount is applied without conflicting with other promotional codes.

### Final Consideration

The final solution proposed includes duplicating products for different collections or using an app like Ninja Code to manage discount prioritization without additional development.

## Conclusion

Handling discount limitations in different collections requires careful planning and prioritization of discount logic. While Shopify's built-in discount system poses certain restrictions, implementing a combination of custom code and third-party apps can offer a viable workaround.

Powered by Byteex
