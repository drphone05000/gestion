# gestion
programe gestion
import java.util.HashMap;

public class StockManager {
    private HashMap<String, Integer> stock;

    public StockManager() {
        stock = new HashMap<String, Integer>();
    }

    public void addItem(String itemName, int quantity) {
        if (stock.containsKey(itemName)) {
            int currentQuantity = stock.get(itemName);
            stock.put(itemName, currentQuantity + quantity);
        } else {
            stock.put(itemName, quantity);
        }
    }

    public void removeItem(String itemName, int quantity) {
        if (stock.containsKey(itemName)) {
            int currentQuantity = stock.get(itemName);
            if (currentQuantity - quantity < 0) {
                System.out.println("Error: Not enough items in stock.");
            } else {
                stock.put(itemName, currentQuantity - quantity);
            }
        } else {
            System.out.println("Error: Item not found in stock.");
        }
    }

    public int getQuantity(String itemName) {
        if (stock.containsKey(itemName)) {
            return stock.get(itemName);
        } else {
            return 0;
        }
    }

    public void printStock() {
        for (String itemName : stock.keySet()) {
            System.out.println(itemName + ": " + stock.get(itemName));
        }
    }

    public static void main(String[] args) {
        StockManager sm = new StockManager();
        sm.addItem("item1", 10);
        sm.addItem("item2", 5);
        sm.removeItem("item1", 2);
        sm.printStock();
