# Color Picker Component

## Overview

The Color Picker component is a reusable frontend element that allows users to select colors within a Shopify store. It is designed to enhance the user experience by providing an intuitive and interactive way to choose colors for products, themes, or any customizable options.

## Theme

This component is designed to be used with the "Dawn" theme, but it can be adapted for use with other Shopify themes with minimal modifications.

## Code

### HTML

```html
<div class="color-picker">
  <input type="color" id="color-input" name="color" value="#ff0000">
  <label for="color-input">Choose your color</label>
</div>
```

### CSS

```css
.color-picker {
  display: flex;
  align-items: center;
  margin: 10px 0;
}

#color-input {
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  height: 40px;
  width: 40px;
  cursor: pointer;
}

label {
  font-size: 16px;
  font-weight: bold;
}
```

### JavaScript

```javascript
document.getElementById('color-input').addEventListener('input', function(event) {
  const selectedColor = event.target.value;
  console.log(`Selected color: ${selectedColor}`);
  // Additional logic to apply the selected color
});
```

## Use Cases

1. **Product Customization**: Allow customers to select colors for customizable products such as t-shirts, mugs, or phone cases.
2. **Theme Customization**: Enable store owners to choose colors for various theme elements like backgrounds, headers, and buttons.
3. **Interactive Demos**: Use the color picker in interactive product demos to showcase different color options in real-time.

## How to Integrate

### Step 1: Add HTML to Your Theme

Insert the HTML code for the color picker component into the appropriate section of your theme. For product customization, add it to the product template file.

```html
<! –– Include this code in your product template (e.g., product.liquid) ––>


<div class="product-customization">
  <h3>Customize Your Product</h3>
  <div class="color-picker">
    <input type="color" id="color-input" name="color" value="#ff0000">
    <label for="color-input">Choose your color</label>
  </div>
</div>
```

### Step 2: Include CSS in Your Stylesheet

Add the CSS code to your theme's stylesheet (e.g., theme.css).

```css
/* Add this CSS to your theme's stylesheet */
.color-picker {
  display: flex;
  align-items: center;
  margin: 10px 0;
}

#color-input {
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  height: 40px;
  width: 40px;
  cursor: pointer;
}

label {
  font-size: 16px;
  font-weight: bold;
}
```

### Step 3: Add JavaScript

Include the JavaScript code in your theme's main JavaScript file (e.g., theme.js).

```javascript
// Add this JavaScript to your theme's main JavaScript file
document.getElementById('color-input').addEventListener('input', function(event) {
  const selectedColor = event.target.value;
  console.log(`Selected color: ${selectedColor}`);
  // Additional logic to apply the selected color
});
```

## How to Make Changes

### Changing the Default Color

To change the default color of the color picker, update the `value` attribute in the HTML code.

```html
<input type="color" id="color-input" name="color" value="#00ff00"> <!-- Default color set to green -->
```

### Modifying the Appearance

Adjust the CSS styles to change the appearance of the color picker.

```css
#color-input {
  margin-right: 10px;
  border: 2px solid #000; /* Change border color to black */
  border-radius: 10px;    /* Increase border radius */
  height: 50px;           /* Increase height */
  width: 50px;            /* Increase width */
}
```

### Adding Additional Functionality

To add more functionality, such as updating the product image based on the selected color, modify the JavaScript code.

```javascript
document.getElementById('color-input').addEventListener('input', function(event) {
  const selectedColor = event.target.value;
  console.log(`Selected color: ${selectedColor}`);
  
  // Example: Change the product image based on selected color
  const productImage = document.getElementById('product-image');
  productImage.style.backgroundColor = selectedColor; // Apply selected color to product image background
});
```
Powered by Byteex
