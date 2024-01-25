### Polymorphism in Ruby

Polymorphism is the capability of a method or object to take on multiple forms. It's a pivotal concept in Ruby's approach to Object-Oriented Programming, facilitating flexibility and extendibility in code structure. In Ruby, polymorphism typically manifests in two main ways:

1. **Method Overriding**: This form of polymorphism occurs when a subclass provides a specific implementation of a method already defined in its superclass. It allows instances of the subclass to respond differently to the same method call compared to instances of the superclass.
    
2. **Duck Typing**: Ruby is often said to use "duck typing" (if it quacks like a duck and walks like a duck, it must be a duck). This means that Ruby is less concerned with the class of an object and more concerned with the methods that object responds to. An object's suitability for use is determined by the presence of certain methods and properties, rather than the actual type of the object.
    

Here’s how polymorphism can be understood in Ruby:

- **Inherent Polymorphism**: Thanks to inheritance, objects in Ruby can be treated as instances of their parent class as well as their actual class. This allows for a flexible code structure where methods can interact with a broader set of objects.
    
- **Universal Ancestry**: Similar to Java, all Ruby objects are somewhat polymorphic. This is because every class in Ruby is a descendant of the `Object` class (except for the `BasicObject` class). Therefore, every object in Ruby passes the IS-A check for their own type and for `Object`.

### Method Flexibility in Ruby

In Ruby, while you can't strictly overload methods (having multiple methods with the same name but different parameters), you can design methods to accept various numbers of arguments. This is achieved using splat operators, default parameters, or keyword arguments, making the methods more flexible and versatile. Here’s how you can handle situations that would traditionally require method overloading in Java:

- **Splat Operator**: Allows a method to receive an arbitrary number of arguments as an array.
```Ruby
def sum(*numbers)
  numbers.reduce(0, :+)
end

puts sum(1, 2)          # => 3
puts sum(1, 2, 3)       # => 6
puts sum(1, 2, 3, 4, 5) # => 15

```

- **Default Parameters**: Enable methods to have default values if no specific value is provided for an argument.
```Ruby
def greet(name, message="Hello")
  puts "#{message}, #{name}!"
end

greet("Alice")          # => Hello, Alice!
greet("Bob", "Welcome") # => Welcome, Bob!

```

- **Keyword Arguments**: Improve the readability of method calls with multiple parameters and allow the omission of some arguments if defaults are set.
```Ruby
def create_person(name:, age:, profession: "Unknown")
  puts "Name: #{name}, Age: #{age}, Profession: #{profession}"
end

create_person(name: "John", age: 30, profession: "Developer")
create_person(name: "Jane", age: 25) # Profession defaults to "Unknown"

```

- **Handling Different Data Types**: Ruby is a dynamically typed language, so you don't need to specify data types for parameters. You can handle different types within the method based on the type of the argument passed.
```Ruby
def display(item)
  if item.is_a?(String)
    puts "It's a string: #{item}"
  elsif item.is_a?(Integer)
    puts "It's an integer: #{item}"
  else
    puts "It's something else: #{item}"
  end
end

display("Hello")
display(100)
display([1, 2, 3])

```

These techniques provide the means to create methods that can handle different sets of arguments, enhancing the readability and flexibility of your program. They allow you to mimic the behavior of method overloading by defining a single method that can handle a variety of argument lists.

### Handling Different Numbers of Arguments in Ruby

In Ruby, you can define a method that accepts a variable number of arguments using the splat operator (`*`). This allows you to handle different numbers of arguments within the same method:

```Ruby
class Adder
  def self.add(*args)
    args.sum
  end
end

# Testing the method with different numbers of arguments
puts Adder.add(11, 11)        # Output: 22
puts Adder.add(11, 11, 11)    # Output: 33

```

In this Ruby version:

- The `add` method is defined as a class method (using `self.`), similar to how the static methods are defined in the Java example.
- The `add` method takes a variable number of arguments (`*args`). The splat operator (`*`) allows the method to accept any number of arguments as an array.
- Inside the method, `args.sum` calculates the sum of all arguments provided, regardless of the number of arguments.

This approach allows the `add` method to handle any number of arguments gracefully, providing functionality similar to method overloading in Java but with a single, flexible Ruby method.

### Handling Different Data Types in Ruby

In Ruby, a method can handle arguments of different data types without needing separate method definitions. Ruby relies on dynamic typing, so you don't need to specify the data type of the arguments. Here's how you can rewrite the Java example in Ruby:

```Ruby
class Adder
  def self.add(a, b)
    a + b
  end
end

# Testing the method with different types of arguments
puts Adder.add(11, 11)        # Output: 22
puts Adder.add(12.3, 12.6)    # Output: 24.9

```

In this Ruby version:

- The `add` method is defined as a class method (using `self.`), allowing you to call it directly on the class without creating an instance.
- The `add` method can handle arguments of different data types. The `+` operator in Ruby is versatile and will perform the correct operation based on the types of `a` and `b` (integer addition, floating-point addition, etc.).

This approach demonstrates Ruby's flexibility in handling arguments of different types within the same method, obviating the need for separate method definitions for different argument types.

### Method Flexibility and Method Overriding in Ruby

#### Method Flexibility (Similar to Method Overloading in Java):

- While Ruby doesn't support method overloading in the same way as Java, it offers flexibility in method definitions. A single method in Ruby can handle various numbers of arguments and types, thanks to features like default parameters, splat operators, and keyword arguments.
- This flexibility in method definitions enhances the readability and adaptability of Ruby programs, allowing a single method to behave differently based on the provided arguments.
- Ruby's approach to handling methods with varying arguments can be seen as a form of compile-time polymorphism, although it's not method overloading in the traditional sense.

#### Method Overriding:

- Method overriding in Ruby is used to provide a specific implementation of a method in a subclass that's already defined in its superclass. This allows subclasses to modify or extend the behavior of methods inherited from the superclass.
- Method overriding occurs in classes that have an inheritance relationship, adhering to the IS-A principle.
- In the case of method overriding, the method signature (name and parameters) in the subclass must match the method signature in the superclass. However, the implementation of the method in the subclass is specific to that subclass.
- Method overriding is a form of runtime polymorphism in Ruby, where the method that gets called is determined at runtime based on the object's class.
- The return type in method overriding in Ruby doesn't have to be the same as in the superclass method.

Here's a Ruby example illustrating method overriding:

```Ruby
class Animal
  def make_sound
    puts "Some generic sound"
  end
end

class Dog < Animal
  def make_sound
    puts "Barking"
  end
end

# Testing method overriding
generic_animal = Animal.new
generic_animal.make_sound  # Output: Some generic sound

pet_dog = Dog.new
pet_dog.make_sound  # Output: Barking

```

In this example, the `Dog` class overrides the `make_sound` method of the `Animal` class, providing a specific implementation that's suitable for a `Dog`.

### Sample Exercise: Bank Interest Rates

#### Scenario

Consider a scenario where `Bank` is a class that provides functionality to get the rate of interest. However, the rate of interest varies according to different types of banks. For example, let's consider three banks: `CommunityBank`, `CityBank`, and `NationalBank`, which offer different interest rates.

#### Task

Implement the scenario in Ruby, ensuring that each specific bank class provides its own interest rate.

1. **Define the Base Class (Bank):**
```Ruby 
class Bank
  def rate_of_interest
    raise NotImplementedError, "This method should be overridden by subclasses"
  end
end

```

2. **Define Subclasses for Each Bank:**

```Ruby
class CommunityBank < Bank
  def rate_of_interest
    8
  end
end

class CityBank < Bank
  def rate_of_interest
    7
  end
end

class NationalBank < Bank
  def rate_of_interest
    9
  end
end

```

3. **Demonstrate Usage:**

```Ruby
# Instantiate bank objects
community_bank = CommunityBank.new
city_bank = CityBank.new
national_bank = NationalBank.new

# Output interest rates for each bank
puts "Community Bank offers a rate of interest of #{community_bank.rate_of_interest}%"
puts "City Bank offers a rate of interest of #{city_bank.rate_of_interest}%"
puts "National Bank offers a rate of interest of #{national_bank.rate_of_interest}%"

# Output: 

"Community Bank offers a rate of interest of 8%"
"City Bank offers a rate of interest of 7%"
"National Bank offers a rate of interest of 9%"


```
