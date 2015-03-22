---
draft: true
title: How Does One Use Design Patterns In Ruby?
date: 2010-11-02
author: Chee Yeo
categories:
- Beginners
- Ruby
- Ruby Masters
layout: post
permalink: /2010/11/02/how-does-one-use-design-patterns-in-ruby/
tags:
- Design Patterns
- programming
- ruby programming
---
### How Does One Use Design Patterns In Ruby?

This guest post is by **Chee Yeo**, a 32-year-old Ruby Rails sometimes
IPhone programmer from Glasgow, Scotland. He enjoys hacking around Ruby
and exploring other new technologies in his day job as a developer. In
his free time he enjoys traveling and exploring the beautiful sights of
the British Isles. You can reach him at
[http://29steps.co.uk](http://29steps.co.uk/) and
[http://github.com/cheeyeo](http://github.com/cheeyeo). He is currently
seeking for contract work and interesting projects to work on.

![Chee Yeo](http://rubylearning.com/images/chee-yeo.jpg "Chee Yeo") As
software develops through requirements and scope changes, it tends to
become ‘bloated’ through its increased complexity. The key idea behind
object-oriented languages is to create flexible systems capable of
handling new changes with minimal side-effects through software reuse.
This is where design patterns come in and can help to create such
extensible systems.

The term was coined by the reknowned ‘Gang Of Four’ (GOF) back in the
nineties when the book ‘Designing Patterns: Elements of Reusable
Software’ was published. The four guiding principles of creating
reusable software can be summarized as follows:

### 1. Generate loose coupling between objects

Design systems whereby the parts that change often are isolated from the
parts that stay consistent. That way, if changes are to occur, you will
not have to go through all the systems code.

### 2. Program to an interface

Reduce your objects to the most general type possible. For example, in
Ruby we could have a Car class instantiated like so:

    new_car = Car.new
    new_care.drive(10)

The above will work as long as there is only one type of transport –
cars. If other types of transport with a drive method were to be
introduced, the above code will not be adequate since it couples the
`drive` method to the Car class.

We can make this system more flexible by creating a more generic type
e.g. create a `Vehicle` class where other classes like a `Car` can subclass
from. That way, other types of transport such as a boat or a plane can
subclass `Vehicle` and implement their own functionality.

An improved version of the above could be something like this:

### 3. Composition over inheritance

One of the strengths of OO languages is the use of inheritance or
subclassing whereby we create our own specialized classes from abstract
or parent classes to incorporate more advanced functionality by
overriding the methods of the super class it inherits from.

If we look at the Vehicle example before, we see that it works for any
type of transport which has an engine. But how do you deal with new
types of vehicles which may not have an engine? If we were to continue
to use the Vehicle superclass, we would still inherit the start and stop
engine methods for vehicles without any engines. Although you could
override them to return nil it is still not the best practice.

This is the subtle point of having an inheritance hierarchy – the
subclasses are tied to the parent class which means changes made to the
parent will be rippled through to the subclasses.

A more rational way would be to break out the engine functionality into
a new class of its own and include it within the subclasses that need it
such as a Car. This is known as composition whereby you build up the
functionality of a class through other classes.

A revised code of the Car class can be as follows:

### 4. Delegation

The improved Car class code from the previous example also has a subtle
improvement.

The work of starting and stopping the engine is now a functionality of
the Engine class. This makes more sense since the Engine class should
know more and be responsible for the engine rather than the
encapsulating class, Car.

By passing on functionality (delegate) to more specialized classes to
handle, you make the system more extensible without the side effects of
inheritance as mentioned before.

It is also possible to create more specialized classes of Engine and
swap them in and out of the Car class above without any further changes
to the core classes involved.

With the above four principles in mind, lets explore some commonly used
design patterns and how they can be applied in Ruby.\
There are 23 design patterns in total as described by the GOF. In this
article I will discuss three of them which I feel are useful in you
daily development work.

### TEMPLATE METHOD PATTERN

You may have come across certain functionality in your own code which is
dependent on certain conditions being met.

A real life example of this could be a report generator which needs to
produce report outputs of various formats i.e. HTML, text files etc.

A first implementation might be to put all the functionality into a core
Parent class call Report and let it handle the output formats itself
like so:

The problem with the approach above is that within the ‘output\_report’
method there is a big ‘if-else’ conditional which outputs the data based
on the format it receives. While this might work for a fixed number of
formats, it will not be possible to make it generic to fit any other
data formats in the long run.

The Template pattern can help to solve this by making the Report class
above an abstract class and defines the ‘output\_report’ method to be
the ‘template’ or core method which handles the core functionality. The
‘output\_report’ method would then call upon the more specialized
methods of its subclasses to complete the rest of the task.

In other words, the base or Parent class has a single method which is
responsible for the overall processing performed by the application and
delegates its functionality to other abstract methods which are defined
in its subclasses.

The new implementation is like so:

The implementation of the format subclasses can be defined as follows:

By delegating the various stages involved in the report processing to
its subclasses, we have managed to decoupled the formatting steps for
each format type into its own subclass, making the overall system more
flexible. Adding a new format type is as easy as making a new subclass
of Report and implementing the abstract methods.

### SINGLETON PATTERN

The singleton pattern defines a class that can only have one instance of
itself and provides global access to that one instance, which means it
can be accessed in all parts of your system.

The rationale behind this pattern is that there may be only one unique
object of a class in your application space, for instance as a GUI
window or a database connection manager and it does not make sense to
instantiate new instances of that class every time you need access to
it.

Ruby has a built-in `Singleton` module in the standard library which
allows you to create a singleton from a given class just by including
it.

For example:

The above can also be achieved using class variables but I find it
easier to understand by using Ruby’s built in modules.

An example of a practical usage of the singleton pattern is to create a
logger class and the code sample can be found at this link:

### THE ADAPTER PATTERN

The Adapter pattern is useful when you have classes with ‘incompatible
interfaces to work together’ which is otherwise impossible to do so.
This is achieved by converting the interface of the incompatible classes
into a suitable interface that the receiving clients expect.

For example, we might have a Renderer class which displays text. The
implementation of the Renderer class might look something like this:

The render method above takes a text\_object which would need to be
implemented like this:

What happens if you have a similar text object as above but with
different attributes like so:

The render method of the Renderer class will not accept the new text
object as its interface is different from that of the TextObject
declared before.

We can create an intermediate class using the Adapter pattern to let the
DifferentTextObject class conform to the interface the render method in
the Renderer class is expecting to receive.

As can be seen above, the adapter object exposes the same interface as
the renderer object expects it to do within its render method but
underneath, it is referring to another type of text object.

The adapter pattern can also be achieved without the use of an extra
adapter class. Recall that in Ruby all classes are open – we can use
some meta programming techniques to achieve the same functionality as
above.

For example:

The ‘class \<\< diff\_text\_obj’ grabs the singleton class of
DifferentTextObject and adds in those additional methods to only the
instance of diff\_text\_obj. Ruby creates an anonymous class as a
superclass of diff\_text\_obj and wraps those new methods without
chaning the DifferentTextObject class.

Any methods defined on a singleton class override that of its original
class which is why the above will still work.

While using the singleton method above makes it easier than creating an
additional adapter class, such approaches work well when the changes to
be made to the existing class are straightforward. For more complex
interfaces, it is still better to create an additional adapter class
until such time you understand how it works.

### ACKNOWLEDGEMENTS

Some of the examples in this article are adapted from the book ‘Design
Patterns In Ruby’ by Russ Olsen and it is recommended reading to really
understand design patterns and its usage in Ruby in detail.

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*

***Do also read* these awesome Guest Posts:**

-   [Do you know what’s new in Ruby
    1.9?](http://rubylearning.com/blog/2010/10/26/do-you-know-whats-new-in-ruby-1-9/)
-   [The value of a personal bug
    log](http://rubylearning.com/blog/2010/10/25/the-value-of-a-personal-bug-log/)
-   [Do You Enjoy Your Code
    Quality?](http://rubylearning.com/blog/2010/10/18/do-you-enjoy-your-code-quality/)

