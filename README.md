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
        System.out.println("Total: $" + calcul

