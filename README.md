# python-challenge-1: Order from a food menu
## Problem Statement
As a customer of Variety Food Truck I want to order items from Variety Food Truck's menu. I want to be able to order multiple items of any quantity. Once I finish ordering I want to see a summary of my order containing the items I ordered, their respective price and the quantity of each item ordered. I also want to see the total cost of my order.

It is done when
* I can pick as many items from a menu in any quantity
* Once I complete my order, I am presented with the items I ordered, their prices and the quantity I ordered for each item.
* I am presented with the total cost of my order. 

## Solution
### Decomposition
Tasks:
1. Display a food menu to the customer
2. Enable the customer to select items from the menu.
3. Display the customer's order.
4. Display the total cost of the customer's order.

### Pattern recognition
1. The menu is given as a nested dictionary.

   Menu items are grouped into the following categories:
   * Snacks,
   * Meals,
   * Drinks, and
   * Sodas.

   Some menu items have different varieties, such as "Pizza" ("Cheese", "Vegetarian", and "Pepperoni").

   Each menu item has a price. Prices vary by variety of menu item.
  
2. The customer is able to order as many items in any quantity as they want.
3. The order summary displays a list of items ordered with price and quantity for each item.
4. The total cost of the order is the sum of the price of each item multiplied by the quantity ordered.

### Abstraction
1. The customer cannot order items that are not on the menu.

### Sequence
**Event 1:** Find out whether the customer wants to order.

<ins>Pseudocode:</ins>[^1]
```
Loop: while(true)
        Ask whether customer is ready to order
        Conditional: if 'yes'
                        break out of the loop and proceed with taking the order in Event 2
                     else if 'no'
                        exit the program
                     else
                        Invalid input. Continue in this loop.
```

**Event 2:** Display available menu items and allow customer to place an order and store it.

<ins>Pseudocode:</ins>
```
Loop: while (the customer wants to place an order)
        set a counter variable to 1
        Loop: for (each menu category)
                retrieve the menu category name from the menu
                display counter and menu category name
                increase counter variable by 1
        ask for a number corresponding to a menu category
        Conditional: if (chosen menu category is valid)
                        Set a counter variable to 1
                        Loop: for (each menu item in menu category)
                            Conditional: if (menu item has varieties)
                                retrieve menu item name, variety name and price from the menu
                                concatenate menu item name and variety name into compound menu item name
                            else
                                retrieve menu item name and price
                            display counter variable, (compound) menu item name, and price
                            ask for a number corresponding to a menu item
                            Conditional: if (chosen menu item is valid)
                                            ask for quantity
                                            store (compound) menu item name, price, and quantity
                                            as a dictionary in an "order" list 
                                         else
                                            set quantity to 1.
                                            tell the customer that his choice was invalid and
                                            that quantity was set to 1. If customer wants more
                                            they need to pick the menu item again.
                            increase counter variable by 1.
                     else
                        tell the customer that they picked an invalid menu category and
                        prompt them to pick a valid menu category
        Loop: while (True)
                Ask whether the customer wants to order more items
                Conditional: if (yes)
                                break out of this loop and allow the customer to enter the next
                                menu item to their order
                             else if (no)
                                break out of this loop and discontinue taking the order
                            else
                                tell the customer that their input is invalid and continue to
                                ask whether the customer wants to continue ordering.
```

**Event 3:** Display the customer's order.

Once the customer has completed their order, display what they ordered with price and quantity to them.

<ins>Pseudocode:</ins>
```
Loop: for (each item in order)
         List the item_name, its price, and the quantity ordered
```

**Event 4:** Display the total cost of the order.

<ins>Pseudocode:</ins>
```
Loop: for (each menu item in order)
    calculate the total cost of the order by summing over the product of the menu item price and
    the menu item quantity.
```
---
## Footnotes
[^1]: I learnd how to underline text in Markdown from Matt Cone Project (2024). *Hacks - Workarounds for things not officially supported by Markdown*, Markdown Guide. https://www.markdownguide.org/hacks/#:~:text=If%20your%20Markdown%20processor%20supports,these%20words%20will%20be%20underlined%20, accessed on 2/26/2024.