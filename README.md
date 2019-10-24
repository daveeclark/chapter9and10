# chapter9and10

Chapter 9: Constructors and Garbage Collection: Life and Death of an Object
(pg 261 online pdf, 235 in book)

The areas of memory in Java
  - The stack (where method invocations and local variables live)
  - The head (where ALL objects live)

Instance variables are decalared inside a class but not inside a method
Local variables are declared inside a method or method parameters

If the method foo() calls method bar(), bar() is stacked on top
  - the method on the top of the stack is always the currently executing method
  - the instance variable(s) of the method on top of the stack becomes the frame

If the local variable is a reference to an object, only the variable (the reference/remote control) goes on the stack (where method invocations and local variables live)

3 steps of object declaration and assignment
  - Declare a reference variable (Duck myDuck)
  - Create an object ( new Duck())
  - Link the object and the reference ( ... = ...)

The key feature of a constructor is that it runs before the object can be assigned to a reference (ability to step in and do things to get the object ready for use)

Use constructors to initialize the state of an object like making and assigning values to the object's instance variables (Public Duck() { size = 34; } )

If you write a constructor that takes arguments, and you still want a no-arg constructor (default constructor), you'll have to build the no-arg constructor yourself
If you have more than one constructor in a class, the constuctors must have different argument lists

Overloaded constructors means you have more than one constructor in your class, to compile each constructor you must have a different argument list

Four things to remember about constructors:
  - A constructor is the code that runs when somebody says new on a class type
        - Duck d = new Duck();
  - A constructor must have the same name as the class and a no return type
        - public Duck (int size) { }
  - If you don't put a constructor in your class, the compiler puts in a default constructor, a no-arg constructor
        - public Duck () { }
  - You can have more than one constructor in a class as long as the argument lists are different
        - public Duck() { }
        - public Duck(int size) { }
        - public Duck(String name) { }
        - public Duck(String name, int size) { }

The only way to call a super constructor is by calling (super()) from the parent class
The call to super() must be the first statement in each constructor of the child class

Hippo can inherit the getName() method but won't have the "name" instance variable unless "name" is passed into the super() method constructor like (super(name))

Will want whichever constructor is first invoked to call The Real Constructor and let The Real Constructor finish the job of construction

Imagine the keyword "this" is a reference to the current object

Use this() to call a constructor from another overloaded constructor in the same class
Every constructor can have a call to super() or this() but never both

public Mini() {
  this(Color.Red); //The no-arg constructor supplies a default Color and calls the overloaded Real Constructor (the one that calls super())
}

public Mini(Color c) {
  super("Mini");  //This is the Real Constructor that does the real work of initializing the object (including the call to super())
  color = c;
  // more initialization
}

A local variable lives only within the method that declared the variable (life of variable ends when method completes)

An instance variable lives as long as the object does (can only use when it is in scope)




Chapter 10: Numbers and statics: Numbers Matter
(pg. 299 online pdf, 273 in book)
