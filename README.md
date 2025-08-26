# junior-developer-test-php

### Task 1 Part-1 order_upload 
1. Added a loop that filters out the orders that have already been uploaded (`$order['uploaded_at'] === null`), and only returns orders with the status `'ready_to_ship'` or `'cancelled'`.
2. Updated the foreach loop by changing the `billing_address` to `shipping_address` to make it consistent with the headers in the file. 
3. Swapped `uploaded_at` and `created_at` to make it consistent with the headers in the file. Also set the `uploaded_at` to the current date, in case it's not already set, so that it is consistent. 

### Task 2 Part-2 product_feed 
1. Moved the if condition, which checks for the product to be inactive (`if ($header['status'] !== 'active'`) to the top inside the loop, so that they can get skipped before the rest of the logic is applied. 
2. Updated the if statement that checks whether the product has been updated today. Now it compares whether the current date matches the `'updated_at'` date and skips the item if they match. 


