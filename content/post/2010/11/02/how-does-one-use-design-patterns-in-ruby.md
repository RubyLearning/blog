---
author: Chee Yeo
categories:
- Beginners
- Ruby
- Ruby Masters
date: 2010-11-02
layout: post
permalink: /2010/11/02/how-does-one-use-design-patterns-in-ruby/
tags:
- Design Patterns
- programming
- ruby programming
thesis_description:
- Chee Yeo introduces you to Design Patterns in Ruby and how to use them in your own
  Ruby code. A guest blog post on RubyLearning.
thesis_keywords:
- Design Patterns,Programming,Ruby programming
title: How Does One Use Design Patterns In Ruby?
topsy_short_url:
- null
---

<div>
  <h3>
    How Does One Use Design Patterns In Ruby?
  </h3>
  
  <p class="update">
    This guest post is by <strong>Chee Yeo</strong>, a 32-year-old Ruby Rails sometimes IPhone programmer from Glasgow, Scotland. He enjoys hacking around Ruby and exploring other new technologies in his day job as a developer. In his free time he enjoys traveling and exploring the beautiful sights of the British Isles. You can reach him at <a href="http://29steps.co.uk/">http://29steps.co.uk</a> and <a href="http://github.com/cheeyeo">http://github.com/cheeyeo</a>. He is currently seeking for contract work and interesting projects to work on.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/chee-yeo.jpg" alt="Chee Yeo" title="Chee Yeo" width="125" height="125" /> <span class="drop_cap">A</span>s software develops through requirements and scope changes, it tends to become &#8216;bloated&#8217; through its increased complexity. The key idea behind object-oriented languages is to create flexible systems capable of handling new changes with minimal side-effects through software reuse. This is where design patterns come in and can help to create such extensible systems.
  </p>
  
  <p>
    The term was coined by the reknowned &#8216;Gang Of Four&#8217; (GOF) back in the nineties when the book &#8216;Designing Patterns: Elements of Reusable Software&#8217; was published. The four guiding principles of creating reusable software can be summarized as follows:
  </p>
  
  <h3>
    1. Generate loose coupling between objects
  </h3>
  
  <p>
    Design systems whereby the parts that change often are isolated from the parts that stay consistent. That way, if changes are to occur, you will not have to go through all the systems code.
  </p>
  
  <h3>
    2. Program to an interface
  </h3>
  
  <p>
    Reduce your objects to the most general type possible. For example, in Ruby we could have a Car class instantiated like so:
  </p>
  
  <pre>new_car = Car.new
new_care.drive(10)
</pre>
  
  <p>
    The above will work as long as there is only one type of transport – cars. If other types of transport with a drive method were to be introduced, the above code will not be adequate since it couples the &#8216;drive&#8217; method to the Car class.
  </p>
  
  <p>
    We can make this system more flexible by creating a more generic type e.g. create a Vehicle class where other classes like a Car can subclass from. That way, other types of transport such as a boat or a plane can subclass Vehicle and implement their own functionality.
  </p>
  
  <p>
    An improved version of the above could be something like this:
  </p>
  
  <p>
  </p>
  
  <h3>
    3. Composition over inheritance
  </h3>
  
  <p>
    One of the strengths of OO languages is the use of inheritance or subclassing whereby we create our own specialized classes from abstract or parent classes to incorporate more advanced functionality by overriding the methods of the super class it inherits from.
  </p>
  
  <p>
    If we look at the Vehicle example before, we see that it works for any type of transport which has an engine. But how do you deal with new types of vehicles which may not have an engine? If we were to continue to use the Vehicle superclass, we would still inherit the start and stop engine methods for vehicles without any engines. Although you could override them to return nil it is still not the best practice.
  </p>
  
  <p>
    This is the subtle point of having an inheritance hierarchy – the subclasses are tied to the parent class which means changes made to the parent will be rippled through to the subclasses.
  </p>
  
  <p>
    A more rational way would be to break out the engine functionality into a new class of its own and include it within the subclasses that need it such as a Car. This is known as composition whereby you build up the functionality of a class through other classes.
  </p>
  
  <p>
    A revised code of the Car class can be as follows:
  </p>
  
  <p>
  </p>
  
  <h3>
    4. Delegation
  </h3>
  
  <p>
    The improved Car class code from the previous example also has a subtle improvement.
  </p>
  
  <p>
    The work of starting and stopping the engine is now a functionality of the Engine class. This makes more sense since the Engine class should know more and be responsible for the engine rather than the encapsulating class, Car.
  </p>
  
  <p>
    By passing on functionality (delegate) to more specialized classes to handle, you make the system more extensible without the side effects of inheritance as mentioned before.
  </p>
  
  <p>
    It is also possible to create more specialized classes of Engine and swap them in and out of the Car class above without any further changes to the core classes involved.
  </p>
  
  <p class="note">
    With the above four principles in mind, lets explore some commonly used design patterns and how they can be applied in Ruby.<br />There are 23 design patterns in total as described by the GOF. In this article I will discuss three of them which I feel are useful in you daily development work.
  </p>
  
  <h3>
    TEMPLATE METHOD PATTERN
  </h3>
  
  <p>
    You may have come across certain functionality in your own code which is dependent on certain conditions being met.
  </p>
  
  <p>
    A real life example of this could be a report generator which needs to produce report outputs of various formats i.e. HTML, text files etc.
  </p>
  
  <p>
    A first implementation might be to put all the functionality into a core Parent class call Report and let it handle the output formats itself like so:
  </p>
  
  <p>
  </p>
  
  <p>
    The problem with the approach above is that within the &#8216;output_report&#8217; method there is a big &#8216;if-else&#8217; conditional which outputs the data based on the format it receives. While this might work for a fixed number of formats, it will not be possible to make it generic to fit any other data formats in the long run.
  </p>
  
  <p>
    The Template pattern can help to solve this by making the Report class above an abstract class and defines the &#8216;output_report&#8217; method to be the &#8216;template&#8217; or core method which handles the core functionality. The &#8216;output_report&#8217; method would then call upon the more specialized methods of its subclasses to complete the rest of the task.
  </p>
  
  <p>
    In other words, the base or Parent class has a single method which is responsible for the overall processing performed by the application and delegates its functionality to other abstract methods which are defined in its subclasses.
  </p>
  
  <p>
    The new implementation is like so:
  </p>
  
  <p>
  </p>
  
  <p>
    The implementation of the format subclasses can be defined as follows:
  </p>
  
  <p>
  </p>
  
  <p>
    By delegating the various stages involved in the report processing to its subclasses, we have managed to decoupled the formatting steps for each format type into its own subclass, making the overall system more flexible. Adding a new format type is as easy as making a new subclass of Report and implementing the abstract methods.
  </p>
  
  <h3>
    SINGLETON PATTERN
  </h3>
  
  <p>
    The singleton pattern defines a class that can only have one instance of itself and provides global access to that one instance, which means it can be accessed in all parts of your system.
  </p>
  
  <p>
    The rationale behind this pattern is that there may be only one unique object of a class in your application space, for instance as a GUI window or a database connection manager and it does not make sense to instantiate new instances of that class every time you need access to it.
  </p>
  
  <p>
    Ruby has a built-in <code>Singleton</code> module in the standard library which allows you to create a singleton from a given class just by including it.
  </p>
  
  <p>
    For example:
  </p>
  
  <p>
  </p>
  
  <p>
    The above can also be achieved using class variables but I find it easier to understand by using Ruby’s built in modules.
  </p>
  
  <p>
    An example of a practical usage of the singleton pattern is to create a logger class and the code sample can be found at this link:
  </p>
  
  <p>
  </p>
  
  <h3>
    THE ADAPTER PATTERN
  </h3>
  
  <p>
    The Adapter pattern is useful when you have classes with &#8216;incompatible interfaces to work together&#8217; which is otherwise impossible to do so. This is achieved by converting the interface of the incompatible classes into a suitable interface that the receiving clients expect.
  </p>
  
  <p>
    For example, we might have a Renderer class which displays text. The implementation of the Renderer class might look something like this:
  </p>
  
  <p>
  </p>
  
  <p>
    The render method above takes a text_object which would need to be implemented like this:
  </p>
  
  <p>
  </p>
  
  <p>
    What happens if you have a similar text object as above but with different attributes like so:
  </p>
  
  <p>
  </p>
  
  <p>
    The render method of the Renderer class will not accept the new text object as its interface is different from that of the TextObject declared before.
  </p>
  
  <p>
    We can create an intermediate class using the Adapter pattern to let the DifferentTextObject class conform to the interface the render method in the Renderer class is expecting to receive.
  </p>
  
  <p>
  </p>
  
  <p>
    As can be seen above, the adapter object exposes the same interface as the renderer object expects it to do within its render method but underneath, it is referring to another type of text object.
  </p>
  
  <p>
    The adapter pattern can also be achieved without the use of an extra adapter class. Recall that in Ruby all classes are open – we can use some meta programming techniques to achieve the same functionality as above.
  </p>
  
  <p>
    For example:
  </p>
  
  <p>
  </p>
  
  <p>
    The &#8216;class << diff_text_obj&#8217; grabs the singleton class of DifferentTextObject and adds in those additional methods to only the instance of diff_text_obj. Ruby creates an anonymous class as a superclass of diff_text_obj and wraps those new methods without chaning the DifferentTextObject class.
  </p>
  
  <p>
    Any methods defined on a singleton class override that of its original class which is why the above will still work.
  </p>
  
  <p>
    While using the singleton method above makes it easier than creating an additional adapter class, such approaches work well when the changes to be made to the existing class are straightforward. For more complex interfaces, it is still better to create an additional adapter class until such time you understand how it works.
  </p>
  
  <h3>
    ACKNOWLEDGEMENTS
  </h3>
  
  <p>
    Some of the examples in this article are adapted from the book &#8216;Design Patterns In Ruby&#8217; by Russ Olsen and it is recommended reading to really understand design patterns and its usage in Ruby in detail.
  </p>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <strong><em>Do also read</em> these awesome Guest Posts:</strong>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/26/do-you-know-whats-new-in-ruby-1-9/">Do you know what’s new in Ruby 1.9?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/25/the-value-of-a-personal-bug-log/">The value of a personal bug log</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/18/do-you-enjoy-your-code-quality/">Do You Enjoy Your Code Quality?</a>
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Design+Patterns" rel="tag">Design Patterns</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>
