# Shopping Website in Java
import java.util.ArrayList;
import java.util.Scanner;

class Product {
    private String name;
    private double price;

    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public double getPrice() {
        return price;
    }
}

class ShoppingCart {
    private ArrayList<Product> items = new ArrayList<>();

    public void addToCart(Product product) {
        items.add(product);
    }

    public void displayCart() {
        System.out.println("Shopping Cart:");
        for (Product item : items) {
            System.out.println(item.getName() + " - $" + item.getPrice());
        }
        System.out.println("Total: $" + calculateTotal());
    }

    private double calculateTotal() {
        double total = 0;
        for (Product item : items) {
            total += item.getPrice();
        }
        return total;
    }
}

class Shop {
    private ArrayList<Product> products = new ArrayList<>();
    private ShoppingCart shoppingCart = new ShoppingCart();

    public void addProduct(Product product) {
        products.add(product);
    }

    public void displayProducts() {
        System.out.println("Available Products:");
        for (int i = 0; i < products.size(); i++) {
            System.out.println((i + 1) + ". " + products.get(i).getName() + " - $" + products.get(i).getPrice());
        }
    }

    public void addToCart(int productIndex) {
        if (productIndex >= 0 && productIndex < products.size()) {
            Product selectedProduct = products.get(productIndex);
            shoppingCart.addToCart(selectedProduct);
            System.out.println(selectedProduct.getName() + " added to the cart.");
        } else {
            System.out.println("Invalid product index.");
        }
    }

    public void checkout() {
        shoppingCart.displayCart();
        System.out.println("Thank you for shopping!");
        System.exit(0);
    }
}

public class ShoppingWebsite {
    public static void main(String[] args) {
        Shop shop = new Shop();

        // Add some sample products
        shop.addProduct(new Product("Laptop", 999.99));
        shop.addProduct(new Product("Smartphone", 499.99));
        shop.addProduct(new Product("Headphones", 79.99));

        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("\nShopping Website");
            System.out.println("1. Display Products");
            System.out.println("2. Add to Cart");
            System.out.println("3. View Cart");
            System.out.println("4. Checkout");
            System.out.println("5. Exit");

            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    shop.displayProducts();
                    break;
                case 2:
                    System.out.print("Enter the product index to add to cart: ");
                    int productIndex = scanner.nextInt();
                    shop.addToCart(productIndex - 1);
                    break;
                case 3:
                    shop.shoppingCart.displayCart();
                    break;
                case 4:
                    shop.checkout();
                    break;
                case 5:
                    System.out.println("Exiting the shopping website. Goodbye!");
                    System.exit(0);
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
}

 
