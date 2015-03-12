---
author: Satish Talim
categories:
- News
- Ruby
date: 2009-11-06
layout: post
permalink: /2009/11/06/rubyists-eu-stairway-to-the-european-ruby-community-integration/
tags:
- European Ruby Community
- Ruby
- Rubyists.EU
- The Ruby Programming Language
thesis_description:
- Rubyists.EU is a free of charge communications platform, which aims at encouraging
  better communications among Ruby communities and individual enthusiasts across Europe.
thesis_keywords:
- Ruby,The Ruby Programming Language,Rubyists.EU,European Ruby Community,Europe
title: 'Rubyists.EU: Stairway to the European Ruby Community Integration'
---

<div>
  <p>
    A Guest Post By <a href="http://twitter.com/dream_warrior">Mariela Dimitrova</a>, <a href="http://twitter.com/gusma">Gustavo Malamud</a> and <a href="http://twitter.com/monsieur_rock">Javier Cicchelli</a>.
  </p>
  
  <p class="block">
    <img class="alignright" title="European Ruby Community Integration" src="http://rubylearning.com/images/EULogo.png" alt="European Ruby Community Integration" />At the beginning of October 2009, a project, sweeping in both scope and ambition, was born. Begotten out of the current integration trends in an ever shrinking world with porous boundaries, this initiative is an attempt to fill in a paradoxical void. Indeed, whereas the Internet has dismantled the final barriers that prevent people from promoting their work, sharing their knowledge, and cooperating with one another, it still appears to be quite difficult to establish better communication and keep in touch with Rubyists in Europe.
  </p>
  
  <p>
    Driven by the idea that Ruby/Rails hackers and user groups in the Old Continent do have something to show and share, the <a href="http://rock-n-code.com/">Rock & Code</a> team came up with the concept of <a href="http://rubyists.eu/">Rubyists.EU</a>. In its essence, this initiative is a free of charge communications platform, which aims at encouraging better communications among communities and individual enthusiasts across Europe. Its brave mission is to promote awareness, enhance assistance, and further boost cooperation and collaboration among Ruby/Rails hackers and user groups in Europe. This initiative harbors the grand vision that in time, by forging long lasting bonds, European Rubyists could foster a sense of belonging to something bigger than their local communities. All the enthusiasts and, respectively, all the Ruby/Rails communities in Europe are invited and encouraged to join forces on the <a href="http://rubyists.eu/">Rubyists.EU</a> arena of action and interaction.
  </p>
  
  <p>
    This bold initiative has the potential to become a treasure trove for both Ruby/Rails developers and communities in Europe. Indeed, by partaking in <strong>Rubyists.EU</strong>, members can attach an extra layer of visibility to their groups and respectively, to themselves. Enthusiastic hackers have the opportunity to join new communities or even found their own. Rubyists can share delicious details about their regular group meetups, bring interesting events and conferences to the attention of others, announce special presentations, make their groundbreaking Ruby advancements public, or simply publish the pioneering Ruby projects they are working on. Hopefully, the <strong>Rubyists.EU</strong> initiative will grow into a living and breathing idea, which can precipitate the development of a robust Ruby community in Europe.
  </p>
  
  <p>
    The technical specification of the Rubyists.EU platform is essentially a result of the perfect mix of several Open Source technologies. Before elaborating on the whole constitution of this platform, it should be pointed out that the testings are carried out by a combination of <a href="http://rspec.info/">RSpec</a> + <a href="http://cukes.info/">Cucumber</a> to handle both functional and integration tests. Due to the Web nature of the project, both <a href="http://wiki.github.com/brynary/webrat">Webrat</a> and <a href="http://selenium.rubyforge.org/">Selenium</a> are used in order to manage simple Hypertext interactions and the significant amount of code written in Javascript.
  </p>
  
  <p>
    The Core of this platform is composed of <a href="http://www.sinatrarb.com/">Sinatra</a> + <a href="http://rack.rubyforge.org/">Rack</a>. <a href="http://www.sinatrarb.com/">Sinatra</a> is a light-weight DSL used for quickly creating web applications in Ruby. It keeps a minimal set of features for developers and it is an excellent tool for creating small to mid-sized web applications. It is based on <a href="http://rack.rubyforge.org/">Rack</a>, which as everyone probably knows, is a Ruby library that provides an interface between web servers supporting Ruby and Ruby web frameworks. Most of the underlying infrastructure is handled by <strong>Rack</strong>.
  </p>
  
  <p>
    The selected database is <a href="http://www.postgresql.org/">PostgreSQL</a>. This Open Source ORDBMS (Object-Relational Database Management System) was chosen because of its robustness, its features, and (mainly) because it is the default database system supported by <a href="http://www.heroku.com/">Heroku</a>.
  </p>
  
  <p>
    The connection and the operations between the Sinatra-powered core and the database are established by <a href="http://datamapper.org/">DataMapper</a>. This is an object-relational mapping library for Ruby. <strong>DataMapper</strong> has a number of excellent features. It is independent and it does not tie in with any particular framework. It is designed to be fast and efficient. One of its pros is that it often delays interaction with the data store and it initiates it only when it is required.
  </p>
  
  <p>
    The Rubyists.EU platform utilizes a user interface based on the <a href="http://code.google.com/apis/maps/">Google Maps platform</a>. Google provides HTML and Javascript APIs for their maps, which allow developers to easily transform a simple map into an interactive application. In addition, the <a href="http://jquery.com/">JQuery</a> library is used in order to simplify and simultaneously AJAXify the Javascript code on the client. The AJAX functionality uses <a href="http://json.org/">JSON</a> (JavaScript Object Notation) to marshall objects for both synchronous and asynchronous transport. The Google Maps standard UI is embedded in the generated HTML structure, defined and generated by <a href="http://haml-lang.com/">HAML</a>. <strong>HAML</strong> is both a simple markup language for templating HTML on a web page and a compiler of HAML-to-HTML and vice-versa. Following the same principle, the <a href="http://sass-lang.com/">SASS</a> defines and generates the CSS representation of the website. The main purpose of developing the front-end this way is to secure the unobstructed separation of the HTML structure, the CSS representation, and the Javascript functionality.
  </p>
  
  <p>
    As a direct consequence of the <strong>Sinatra</strong> core, this platform already provides a RESTful API that allows our platform to interact with any existent client or system. This would allow both developers and communities to integrate its functionality to their own websites, projects, applications, etc.
  </p>
  
  <p>
    Last, but not least, this framework is deployed in <strong>Heroku</strong>. For those who still have no clue about this service, it is a Ruby-specific cloud-computing platform that provides specialized Ruby hosting services for developers. It allows developers to almost instantly deploy web applications on the Internet. Heroku supports Rack-based web applications so deploying the code on Heroku is a piece of cake. While this service charges for hosting, it also provides a free basic tier account. It should be remarked that this platform requires the intensive use of <a href="http://git-scm.com/">Git</a>, a powerful decentralized SCM (Source Control Management) system, in order to deploy applications.
  </p>
  
  <p>
    Currently the Rubyists.EU platform is isolated from the rest of the available systems out there but soon, it will be integrated with the existing communications platforms such as <a href="http://twitter.com/">Twitter</a>, <a href="http://www.facebook.com/">Facebook</a>, <a href="http://www.linkedin.com/">LinkedIn</a>, <a href="http://freenode.net/">Freenode</a>, <a href="http://groups.google.com/">Google Groups</a>, <a href="http://wave.google.com/">Google Wave</a>, and <a href="http://github.com/">Github</a> in order to facilitate and ensure the transparent communications among Rubyists in Europe.
  </p>
  
  <p>
    This project is being built on tests. Whenever a functionality has to be written or existing Ruby libraries have to be inserted into the code, the BDD (Behavior Driven Development) approach is used to specify how the piece of code should work in the platform. For those of you who are still unfamiliar with the BBD, it is an approach that emphasizes on the domain language of the problem and the interactions occurring in the Software Development process. It implies outside-in development: it starts with the either the definition of a class, a module or a user interface and it ends with the creation of a functional piece of code. Therefore, you have to design scenarios for the functionalities or features you want to develop and then, you simply have to follow the BDD process.
  </p>
  
  <p>
    When a scenario is defined, the developer should write the tests and then write the necessary code to make sure that the code passes the tests. Then, the developer should focus on refactoring this code while verifying it still passes the written tests. Once you are done, you can move on to the next feature and so on. These scenarios guide developers throughout the entire development process. They force people to focus on writing down the tests and the required application code, and only then are developers allowed to move on to the next step. Developers are satisfied every time they pass a step successfully because they know for sure, which of the features they have been developed function properly.
  </p>
  
  <p>
    Since the Rubyists.EU is an initiative designed for the whole European Ruby/Rails community, everybody is welcome to join in and even collaborate with ideas, suggestions, comments, constructive criticism and code. Developers can get involved by following the <a href="http://github.com/rock-n-code/rubyists.eu">Github account</a> and even forking the source code. Some of the members of the Dutch <a href="http://amsterdam-rb.org/">Amsterdam.rb</a>, the Belgium <a href="http://wiki.rubyist.be/wiki/show/HomePage">BRUG</a>, the Greek <a href="http://rubyst.es/">Rubyst.es</a>, and the Estonian <a href="http://www.ruby.ee/">Ruby.ee</a> have already volunteered to collaborate on this project.
  </p>
  
  <p>
    Rubyists can get in touch and make comments, suggestions for new features or propositions to improve the existing ones by subscribing to the <a href="http://groups.google.com/group/rubyists-eu">mailing list</a>. In addition, hackers can follow the <a href="http://twitter.com/rubyists_eu">@rubyists_eu</a> on Twitter, join the <a href="http://www.facebook.com/pages/Europe/RubyistsEU/188196555796">Rubyists.EU Facebook page</a>, and the <a href="http://http://www.linkedin.com/groups?gid=2400973">Rubyists.EU group on LinkedIn</a>. Furthermore, developers and enthusiasts can also chat with other Rubyists on the IRC channel on Freenode: <a href="irc://irc.freenode.net/rubyists.eu">#rubyists.eu</a> or exchange enlightening information on the public <a href="https://wave.google.com/wave/?pli=1#restored:wave:googlewave.com!w%252Ba39S3saqF">Google Wave channel</a>.
  </p>
  
  <p>
    After all, the Rubyists.EU endeavor is a joint adventure that can become as exciting as hackers and communities in Europe want it to be. Hopefully, in the long run, this initiative could help eliminate the obstacles that prevent the smooth adoption of the Ruby language as a whole, and it would contribute to the development of a robust Ruby/Rails community in Europe.
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>, <a href="http://technorati.com/tag/Rubyists.EU" rel="tag">Rubyists.EU</a>, <a href="http://technorati.com/tag/European+Ruby+Community" rel="tag">European Ruby Community</a>
