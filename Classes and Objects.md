## Objects

In Ruby, an object is an entity that possesses state and behavior. This can be anything with physical or logical characteristics, like a chair, pen, table, keyboard, bike, etc. Each object is an instance of a class and occupies a unique space in memory.

Objects in Ruby interact by sending messages to one another. During this interaction, they don't need to be aware of each other's data or code specifics. The only requirements are the messages that the objects send and receive, focusing on what is being asked and what should be returned.

For instance, consider a dog as an object. It has states like color, name, breed, etc., and behaviors like wagging the tail, barking, and eating. The dog's actions are encapsulated within it, and it interacts with the external environment through well-defined interfaces.

## Classes 

A class in Ruby is more than just a template for objects; it's a fundamental concept that encapsulates behaviors and states. Classes define the structure and capabilities of objects, acting as blueprints for creating individual instances.

Each class in Ruby can create objects (instances), and each object is associated with a class. However, unlike some other languages, classes in Ruby are themselves objects, instances of the Class class. This gives Ruby a highly dynamic and flexible approach to OOP, allowing for modifications at runtime and a more fluid and less rigid structure.

Ruby classes encapsulate methods (for behavior) and attributes (for state), and they don't consume space until an object is instantiated from them.

### Advantages of OOP in Ruby over Procedure-Oriented Programming

- **Enhanced Maintainability**: OOP in Ruby promotes cleaner and more modular code, making it easier to manage, extend, and modify as the project grows, unlike in procedural programming where scaling the project can lead to complex and intertwined code.
- **Data Encapsulation and Protection**: Ruby provides mechanisms to control the level of access to the object's data, safeguarding it from unintended modification and ensuring interactions are conducted through well-defined interfaces.

```Ruby
class Dog
  attr_accessor :breed, :age, :color

  def initialize(breed, age, color)
    @breed = breed
    @age = age
    @color = color
  end

  def barking
    puts "#{@breed} is barking."
  end

  def hungry
    puts "#{@breed} is hungry."
  end

  def sleeping
    puts "#{@breed} is sleeping."
  end
end

```

The code above is a Ruby representation of a `Dog` class, illustrating how individual objects with specific attributes and behaviors are spawned from this class blueprint.

- We define the class `Dog` using the `class` keyword.

- The `attr_accessor` method is a Ruby shortcut that automatically creates getter and setter methods for the specified attributes (`:breed`, `:age`, `:color`).

- The `initialize` method is a special type of method in Ruby, called when a new instance of the class is created. It's analogous to a constructor in typescript.

- The instance methods `barking`, `hungry`, and `sleeping` are defined to represent the dog's behaviors. Inside these methods, we can access the instance variables (`@breed`, `@age`, `@color`) directly.

- In Ruby, explicit return statements are not required. The last evaluated expression in a method is automatically returned.