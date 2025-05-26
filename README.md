menu={
    'Pizza':40,
    'Pasta':50,
    'Burger':60,
    'Salad':70,
    'Coffee':80,
}
#Greet 

print("Welcome to our Restaurant")
print("Pizza:40\nPasta:50\nBurger:60\nSalad:70\nCoffee:80\n")

#Creating a variable name to add total purchased by user

order_total=0

# Creating variables named item so user can input their orders

item_1 = input("Enter the name of item you want to order=")
if item_1 in menu:
    order_total+=menu[item_1] #0 base price + price of items will be added
    print(f"your item has beeen added to total")
else:
    print("Your item not availabale at the moment")

another_order=input("Do you want to add something else?")
if another_order=="yes":
    item_2 =input("Enter the name of the item ")
    if item_2 in menu:
        order_total+=menu[item_2]
        print("Item{item_2}has been added")
    else:
        print("item{item_2} is not available")    

print("The total amount of item to pay is{order_total}")



