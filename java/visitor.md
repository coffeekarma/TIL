# Visitor pattern

A Visitor is useful if you have to perform a number of unrelated operations across the classes.

### Example
```Java
//Element interface
public interface Visitable{
  public void accept(Visitor visitor);
}
``` 
```Java
//concrete element
public class Book implements Visitable{
  private double price;
  private double weight;
  //accept the visitor
  public void accept(Visitor vistor) {
    visitor.visit(this);
  }
  public double getPrice() {
    return price;
  }
  public double getWeight() {
    return weight;
  }
}
``` 
```Java
public interface Visitor{
  public void visit(Book book);
  
  //visit other concrete items
  public void visit(CD cd);
  public void visit(DVD dvd);
}
``` 
```Java
public class PostageVisitor implements Visitor {
  private double totalPostageForCart;
  //collect data about the book
  public void visit(Book book) {
    //assume we have a calculation here related to weight and price
    //free postage for a book over 10 
    if(book.getPrice() < 10.0) {
      totalPostageForCart += book.getWeight() * 2;
    }
  }
  //add other visitors here
  public void visit(CD cd) {...}
  public void visit(DVD dvd) {...}
  //return the internal state
  public double getTotalPostage() {
    return totalPostageForCart;
  }
}
``` 
