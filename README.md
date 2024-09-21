class Product:
    def __init__(self, name, price, quantity):
        self.name = name
        self.price = price
        self.quantity = quantity

    def __str__(self):
        return f"{self.name} - {self.price} грн (Наявність: {self.quantity})"


class Cart:
    def __init__(self):
        self.items = {}

    def add_product(self, product, quantity):
        """Додає товар до кошика. Якщо товар уже є, збільшує кількість."""
        if product.name in self.items:
            self.items[product.name]['quantity'] += quantity
        else:
            self.items[product.name] = {'product': product, 'quantity': quantity}
        product.quantity -= quantity

    def remove_product(self, product, quantity):
        """Видаляє товар з кошика або зменшує його кількість."""
        if product.name in self.items:
            if self.items[product.name]['quantity'] <= quantity:
                product.quantity += self.items[product.name]['quantity']
                del self.items[product.name]
            else:
                self.items[product.name]['quantity'] -= quantity
                product.quantity += quantity

    def total_price(self):
        """Підраховує загальну вартість товарів у кошику."""
        total = sum(item['product'].price * item['quantity'] for item in self.items.values())
        return total

    def show_cart(self):
        """Виводить усі товари, які є в кошику."""
        if not self.items:
            return "Ваш кошик порожній."
        result = []
        for item in self.items.values():
            product = item['product']
            quantity = item['quantity']
            result.append(f"{product.name} - {quantity} шт. - {product.price * quantity} грн")
        return "\n".join(result)


product1 = Product("Ноутбук", 20000, 5)
product2 = Product("Смартфон", 15000, 10)
product3 = Product("Навушники", 2000, 20)

cart = Cart()

cart.add_product(product1, 1)
cart.add_product(product2, 2)
cart.add_product(product3, 3)
print("Товари в кошику:")
print(cart.show_cart())
