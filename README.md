menu = {
    'coffee': 50,
    'tea': 30,
    'sandwich': 70,
    'burger': 120,
    'pizza': 150,
    'pasta': 100,
    'muffin': 40,
    'cookie': 20,
    'juice': 60
}

print("👨‍🍳 Welcome to Akii Chefssss! We're excited to serve you today.\n")
print("Here's what we have on the menu today:\n")

for item, price in menu.items():
    print(f"➡️  {item.capitalize()} - ₹{price}")

total = 0
order_summary = {}

while True:
    order = input("\nWhat would you like to order? Type the item name: ").strip().lower()
    
    if order in menu:
        quantity = input(f"How many {order}s would you like? ").strip()
        if quantity.isdigit():
            quantity = int(quantity)
            cost = menu[order] * quantity
            total += cost
            order_summary[order] = order_summary.get(order, 0) + quantity
            print(f"👍 Got it! {quantity} x {order.capitalize()} added to your order.")
        else:
            print("🚫 Hmm, that doesn't look like a number. Let's try again.")
    else:
        print(f"😔 Sorry, we don't have {order} on the menu right now.")

    cont = input("Would you like to order anything else? Press 1 for YES or 2 for NO: ").strip()
    if cont != '1':
        break

if total > 0:
    print(f"\n💵 Your current total is ₹{total}.")

    tip_choice = input("Would you like to add a tip? Press 1 for YES or 2 for NO: ").strip()
    if tip_choice == '1':
        while True:
            tip_input = input("Please enter tip amount: ").strip()
            if tip_input.isdigit():
                tip = int(tip_input)
                total += tip
                break
            else:
                print("Please enter a valid number for tip.")
    else:
        tip = 0
        print("No tip added. Thank you!")

    delivery_choice = input("Delivery or Pickup? Press 1 for Delivery or 2 for Pickup: ").strip()
    if delivery_choice == '1':
        address = input("Please enter your delivery address: ")
        print(f"🚚 Thanks! We'll deliver your order to: {address}")
    else:
        print("🛍️ Great! Your order will be ready for pickup soon.")

    payment = input("How would you like to pay? Press 1 for Cash, 2 for Card, 3 for UPI: ").strip()
    payment_methods = {'1': 'Cash', '2': 'Card', '3': 'UPI'}
    payment_method = payment_methods.get(payment, 'Cash')
    if payment not in payment_methods:
        print("We didn't catch that, so we’ll assume payment by Cash.")

    print("\n🧾 --------- Akii Chefssss Receipt ---------")
    for item, qty in order_summary.items():
        print(f"{item.capitalize()} x {qty} = ₹{menu[item] * qty}")
    if tip > 0:
        print(f"Tip = ₹{tip}")
    print(f"Total Amount = ₹{total}")
    print(f"Payment Method: {payment_method}")
    print("-------------------------------------------")
    print("🙏 Thank you so much for ordering from Akii Chefssss!")
    print("We hope your meal brings a smile to your face. 🍕🧁\n")
else:
    print("\nIt looks like you didn’t order anything. No worries! Come back soon to Akii Chefssss! 😊")
