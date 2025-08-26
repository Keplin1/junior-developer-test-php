# Changelog
1. In Product.vue file fixed the directory from `../assets/Product.json` to `./data/product.json`;
2. Fixed `@import "./assets/css/poppins.css"` in the `App.vue` file;
3. Split the page into two sections. Placed product images from the `product.json` file into the left side. Added styling - placed two images per row `(col-6)`, making them appear side by side. 
4. Added `product_offer_label` from `product.json` file to the right section. Added `border-left` to create a red pipe line next to it. 
5. Added prices (original/ now) from `product.json`. Placed them along with the discount into one parent `div` and applied styling. The styling for the discount is set to `col-md-6`, so that it appears on the far right side of the screen. 
6. Added a `calcDiscount` function, which calculates the discount based on the original vs current price. (This functionality could be potentially improved in case of no discounts and function reused in other parts of the project as a util).
7. Added the alternative colours. Wrapped them in a `<button>` tag, so that they can be selected. Looped through the images and filtered out ones that have broken urls by using `@error`. Added a dynamic class which adds a border around the selected image (`@click`), so that the user can see the colour they chose.
8. Added the choice of sizes from the `product.json` file. Created a `selectedSize` variable which keeps track of the selected size. Looped through the sizes and added dynamic styling which is triggered on click. 
9. Added an 'Add To Bag' button. When clicked it triggers the `addToBag` function. In turn, the function checks if the size was selected. If the size is not null, it triggers a toast-pop up. The toast pop-up appers with a message for the user, which reads as "You have selected size: {{ addedSize }}".
10. Added a description, with product bullet points and the product code from the `product.json` file Used a few font styles from the `poppings.css` file.

11. Hosted the page on netlify: https://regatta-tech-test.netlify.app/

# To be improved/ added:
- Carousel for the images
- Depending on desired behaviour, make the colour selector change to the URL on click
- Size select button layout on small screens
- Discount may not need to be displayed 
- Testing
