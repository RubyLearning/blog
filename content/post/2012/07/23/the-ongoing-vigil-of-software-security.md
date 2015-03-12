---
author: James Schorr
categories:
- Ruby
- Security
date: 2012-07-23
layout: post
permalink: /2012/07/23/the-ongoing-vigil-of-software-security/
tags:
- James M. Schorr
- Software Security
thesis_description:
- James Schorr gives us some examples of how we can improve the security of our software
  projects to proactively work towards producing quality, stable software.
thesis_keywords:
- James M. Schorr, Software Security
title: The Ongoing Vigil of Software Security
topsy_short_url:
- null
---

<div>
  <h3>
    The Ongoing Vigil of Software Security
  </h3>
  
  <p class="update">
    This guest post is by <strong>James Schorr</strong>, who has been developing software since 1999. He is the owner of an IT consulting company, <a href="https://enspirenconsulting.com">Enspiren IT Consulting, LLC</a>.  He lives with his lovely wife, Tara, and their children in Kansas City, Missouri. James spends a lot of time writing code in many languages, doing IT security audits, and has a passion for Ruby on Rails in particular. He also loves spending time with his family, playing chess, going to the shooting range, hiking, fishing, and investing. His professional profile is on <a href="http://www.linkedin.com/in/jamesschorr">LinkedIn</a>.
  </p>
  
  <p class="block">
    <img class="alignright" alt="James M. Schorr" src="http://rubylearning.com/images/James_Schorr.png" width="125" height="125" /> <span class="drop_cap">T</span>he news is often filled with stories about exploits affecting large corporations and widely used software (LinkedIn, Yahoo, Windows, Linux, OS X, *BSD, Oracle, MySQL, Java, Flash, etc…). However, a tremendous amount of successful hacks and exploits take place on a daily basis on smaller-profile systems that we never hear about.
  </p>
  
  <p>
    Some of the reasons that we keep seeing these types of exploits are that the &#8220;bad guys&#8221; are much smarter and more determined than we give them credit for, we're much lazier and more ignorant than we take responsibility for, and security is difficult to manage properly. As we become more and more reliant upon software, it is imperative that security be taken more seriously.
  </p>
  
  <h3>
    What's the big deal?
  </h3>
  
  <p>
    Consider this somewhat over-the-top thought exercise:
  </p>
  
  <blockquote>
    <p>
      <em>Think of your systems, databases, and code as a ship floating in the middle of the Atlantic. The ship was fairly hastily constructed as the management team pushed the various craftsmen to get done in time for the journey.</em>
    </p>
    
    <p>
      <em>It's the middle of the hurricane season. The waves are getting higher, sharks are circling your boat, and aboard are quite a few passengers. Most of the passengers are of a fairly decent ilk, but some are not. This latter group, partially due to the insufferable boredom that accompanies their long journey, have taken delight in drilling holes in the side of the boat (with the tools that were discarded during construction). Other troublemakers spend their time throwing chum overboard to the encircling sharks and even, when no one is watching, throwing each other overboard. A few of the cleverer sort spend their time impersonating the crew and using their new privileges to look for ways to take over the ship. Sadly, even some of the crew members have been persuaded into joining their mutinous ranks.</em>
    </p>
    
    <p>
      <em>As time goes by, the remaining crew loses its ability to prevent damage to the craft and protect those on board, as a result of sheer exhaustion, the tenacity of the passengers, and the natural wear and tear of the elements.</em>
    </p>
  </blockquote>
  
  <p>
    What's the point of this mental exercise? We need to realize that unrelenting attacks abound, both from within and without the system. If not properly addressed, they only escalate over time.
  </p>
  
  <p>
    Security is a word that has a long, storied past. According to most dictionaries, one of the definitions of security includes, &#8220;free from danger&#8221;. Of course, stating that a system, code base, network, etc. is secure is quite naïve at best, dangerous at worst. Recognizing the threats is the first step toward positively addressing them.
  </p>
  
  <p>
    Ask any IT team member that is charged with &#8220;securing&#8221; anything and you'll quickly find out that it is an extremely difficult, often thankless task. Even in a tightly controlled environment, it can be pretty tough, especially during times of extreme change, turnover, growth, etc.
  </p>
  
  <h3>
    Why should we care?
  </h3>
  
  <p>
    We need to care because our applications, databases, and systems:
  </p>
  
  <ul>
    <li>
      are <em>regularly</em> being threatened from the inside and the outside, often without us even being aware of it.
    </li>
    <li>
      are depended upon by users who have invested some degree of their money, trust, time, or work into using them.
    </li>
    <li>
      haven't &#8220;arrived&#8221;. There is <em>always</em> a way to circumvent the &#8220;system&#8221;.
    </li>
    <li>
      typically depend upon the &#8220;happy path&#8221; scenarios (e.g. when all goes well).
    </li>
  </ul>
  
  <h3>
    What can we do?
  </h3>
  
  <p>
    Thankfully, there are quite a few things that can be proactively done to help mitigate the risks and stave off the threats. For brevity's sake, I'm going to give a high level overview of what can be done to help prevent exploits:
  </p>
  
  <h4>
    Team Security Measures
  </h4>
  
  <ol>
    <li>
      <em>Who should be in charge of our project's security?</em> Involve the right people, taking the time to get to know their character and mindset. Not everyone is cut out to think with the type of mindset needed to properly manage security. Unless someone is <em>really</em> into security, is trustworthy, is assertive, and unafraid of conflict, they simply aren't the right person for this task.
    </li>
    <li>
      <em>Who has need-to-know?</em> Need-to-know is an essential principle in projects. Data leakage often inadvertently occurs by team members that probably didn't need the information to begin with. Those that realize the &#8220;big-picture&#8221; usage of the data and need access to it for their tasks typically realize the need to keep the data private.
    </li>
    <li>
      <em>Separation of duties with each area managed by a small core team.</em> While not always possible, it is helpful to have one main realm of responsibility per team. Also, the core team of each area/realm needs to remain just that &#8211; the core team. In other words, the more people added, the tougher it is to keep things secure.
    </li>
    <li>
      <em>How, when and to whom do we communicate?</em> The procedures for securely communicating need-to-know information are critical to establish. Various methods need to be implemented to allow team members to exchange information in as secure a fashion as possible. An example might be the usage of an encrypted volume in a shared drive (retaining the control of the encryption details).
    </li>
    <li>
      <em>Knowledge Transfer</em>: when someone leaves the team, great care should be taken to transfer the knowledge to the new member in a secure fashion. Additionally, all relevant credentials should be changed immediately, <em>no matter how trusted that individual or group was</em>. A simple exit checklist – that is followed – can greatly help with this.
    </li>
  </ol>
  
  <h4>
    Technological Security Measures
  </h4>
  
  <ol>
    <li>
      <em>Testing is critical</em>: we are testing, right? In dev-speak, <code>tested_code != secure_code</code> but <code>tested_code.class == SecurityMindset</code>. In other words, it is possible to write insecure, tested code, but proper testing does seem to inherit qualities from a security mindset and to encourage more thoughtful programming. In my opinion, testing generally falls into two main types: <ol>
        <li>
          Code-based Testing: I'll let others bore you with a long list of what's available out there but do want to point out that real-world progress can be made towards better securing code with the usage of tools/methods such as: Rspec and friends, TDD, BDD, etc.
        </li>
        <li>
          Human Testing: sometimes nothing beats enlisting the help of others to pound away on our beloved projects. You'd be surprised at how many issues are found by this approach, often leading to cries of, &#8220;But users aren't supposed to do that!&#8221; <ol>
            <li>
              Non-technical users: enlist someone who can has a hard time finding the / key. This type of person will usually do all sorts of unexpected things. The unexpected behavior can quickly reveal the hidden weaknesses in the UI, workflow, and security.
            </li>
            <li>
              Enlist the upcoming geeks: you know those kids who are always jail-breaking phones? After issuing a few half-hearted reprimands, ask them to &#8220;conquer&#8221; your app. Offering a prize can't hurt.
            </li>
            <li>
              Enlist an expert to audit your code, procedures, and projects.
            </li>
          </ol>
        </li>
      </ol>
    </li>
    
    <li>
      <em>Logging:</em> <ol>
        <li>
          What to log: in general, the more information about transactional details (transactional referring to any actions that involve change), the better. Note that anything related to attempted security breaches needs to be logged. Admin alerts should also be automatically sent out; these alerts need to be designed with great care to not transmit anything that would harm the system if intercepted in transit.
        </li>
        <li>
          What to <em>never, ever</em>log: <ol>
            <li>
              Credentials: passwords, API keys (abstract before logging: e.g. if Bob does X with an API key, put a different identifier in the log file, not the key).
            </li>
            <li>
              Credit card numbers, PINs, debit card numbers, anything banking related unless we are doing so in compliance with <strong>PCI standards</strong>.
            </li>
            <li>
              Medical information (see <strong>HIPPA</strong> &#8211; Health Insurance Portability and Accountability Act or your country's corresponding laws).
            </li>
            <li>
              Anything that can be used to compromise the systems or it's users.
            </li>
          </ol>
        </li>
        
        <li>
          How to log: I personally prefer a two-pronged approach: 1) writing to log files which are automatically transferred offsite, 2) an audit trail via a NoSQL database (using a fire-and-forget type of approach; in other words send the insert but keep on moving, a failure to log to the audit trail should alert admins but not slow down or impact the user's use of the application at all).
        </li>
        <li>
          When to log: as close to the event as possible, to minimize the chance of data loss. <ol>
            <li>
              Log Alterability: Think, &#8220;if I was a hacker and compromised this system, I'd want to clean up after my activities&#8221;. How do I make my logs non-alterable, even by support staff?
            </li>
          </ol>
        </li>
      </ol>
    </li>
    
    <li>
      <em>Access Levels</em>: these typically fall into the following: <ol>
        <li>
          Users <ol>
            <li>
              What can they access and why
            </li>
            <li>
              Who can change their level (e.g. can the user manage their own level via subscriptions)?
            </li>
          </ol>
        </li>
        
        <li>
          Support Staff <ol>
            <li>
              Level 1 CSR
            </li>
            <li>
              Level 2 CSR
            </li>
            <li>
              Level 3 Admins
            </li>
            <li>
              Dictators (can do anything with no recourse)&#8230; careful with these types.
            </li>
          </ol>
        </li>
      </ol>
    </li>
    
    <li>
      <em>Crucial Elements</em>: <ol>
        <li>
          Account Lockouts <ol>
            <li>
              Users are locked out for some period of time when they fail to login after X attempts or try via different IPs, etc.
            </li>
            <li>
              Users are locked out and admins alerted when they try to get around the system (these types of lockouts do not expire with time but rather require a Support Staff person to unlock them based on their discretion).
            </li>
            <li>
              Ability for Support Staff to lock and unlock users very quickly <em>after</em> following a procedure to record why they're doing so. A permanent record needs to be kept as to who unlocked whom and why.
            </li>
          </ol>
        </li>
        
        <li>
          Account Password Policies: password strength, requirements to change the password every X days, password history (can't reuse old passwords), etc.
        </li>
        <li>
          Other: click-limits, IP address binding, geographic-binding, usage of Oauth 2, etc.
        </li>
      </ol>
    </li>
    
    <li>
      <em>Frameworks and Software Libraries</em>: it's fairly common to have security vulnerabilities &#8220;appear&#8221; due to the integration of code from other sources. Of course, no one has time to re-invent the wheel, so to speak; nor should they. It is a good practice to always read through the source code and reported issues of 3rd party software prior to implementation. <ol>
        <li>
          Take the time to search for some of its common exploits and best-practice methods of usage. Have we taken the time to test what X library (framework, gem, plugin, etc.) would mean for our application's speed, stability, and security?
        </li>
        <li>
          Refrain from handling some things ourselves. A good example is credit-card processing. Why handle it yourself when a 3rd party, tested service will likely do so in a more secure manner? Look for a project that has been around for a while and has a good track-record of quickly closing vulnerabilities.
        </li>
      </ol>
    </li>
    
    <li>
      <em>Servers and Hosting</em>: it may save some money to host on a shared host or cousin Bill's server, but will the data be secure? It's best to strive for meeting all three of the CIA principles (Confidentiality, Integrity, and Availability) when choosing a host, striving for at least a medium-level for each principal. <ol>
        <li>
          Keep the servers up-to-date.
        </li>
        <li>
          Use intrusion detection applications (e.g. psad, fwsnort) to alert admins of attempts to break in the system.
        </li>
        <li>
          Use a properly configured firewall that is easy to adjust quickly.
        </li>
        <li>
          Send the logs offsite (e.g. not on the same &#8220;box&#8221;) to a secured server on a frequent basis.
        </li>
        <li>
          Backups: ideally, these should occur nightly of the entire codebase, logs, and database dumps; these backups should be kept offsite in the same manner as logs.
        </li>
        <li>
          Imaging: frequent images of servers can be helpful for forensics in the event of an exploit and for data recovery.
        </li>
        <li>
          Server-side miscellaneous applications (Apache, Nginx, SSH, OpenSSL, etc.): disable unused modules, limit connections, use non-default ports, etc. (see Resources for more ideas).
        </li>
        <li>
          Schedule checks for rootkits and malware on a daily basis; be sure to alert admins if any is found.
        </li>
      </ol>
    </li>
    
    <li>
      <em>Database(s)</em>: Familiarity with the database(s) is key to keeping them secure. For instance, if a development team is very familiar with MySQL and decides to add in a secondary technology alongside (maybe some MongoDB databases), it would be wisest to evaluate the architecture and security implications prior to implementation.
    </li>
    <li>
      Credentials: <ol>
        <li>
          Where and how should we store the credentials that our app needs (e.g. api keys, database credentials, etc.)? A good thing to ask ourselves is, &#8220;if someone did get into our server (as non-root, as if they did as root, it's game-over anyhow), what could they get and who would it hurt?&#8221;
        </li>
        <li>
          Are we deploying our credentials to GitHub or other VCS? If so, we're blindly trusting that 3rd party to be and stay secure.
        </li>
        <li>
          Changes should be planned for and completed whenever there is a change in personnel and on a periodic basis. This can become a real hassle unless thought is given along the lines of, &#8220;How do we quickly change these credentials?&#8221;
        </li>
      </ol>
    </li>
  </ol>
  
  <p class="alert">
    <em>I hope that this article has given you at least a few ideas of how to better improve your software project's security. If so, I'll consider it a success. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <h3>
    Resources
  </h3>
  
  <p>
    Below are some resources that may be helpful (those that I have found extremely helpful over the years are denoted with a <strong>*</strong> next to them):
  </p>
  
  <ul>
    <li>
      <a href="http://xianshield.org/guides/apache2.0guide.html">Apache 2 Hardening Guide</a>
    </li>
    <li>
      <a href="https://github.com/binarylogic/authlogic">Authlogic</a>
    </li>
    <li>
      <a href="http://areyouahuman.com/">Are You a Human Anti-Captcha*</a>
    </li>
    <li>
      <a href="https://github.com/binarylogic/authlogic">Brakeman*</a>
    </li>
    <li>
      <a href="http://www.clamav.net/">ClamAV</a>
    </li>
    <li>
      <a href="https://github.com/plataformatec/devise">Devise*</a>
    </li>
    <li>
      <a href="http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/security.html">FreeBSD Security</a>
    </li>
    <li>
      <a href="http://cipherdyne.org/fwsnort/">Fwsnort</a>
    </li>
    <li>
      <a href="http://www.linuxsecurity.com/">Linux Security</a>
    </li>
    <li>
      <a href="http://www.greensql.com/articles/mysql-security-best-practices">MySQL Quick Security Guide</a>
    </li>
    <li>
      <a href="https://calomel.org/nginx.html">Nginx Security*</a>
    </li>
    <li>
      <a href="http://cipherdyne.org/psad/">PSAD*</a>
    </li>
    <li>
      <a href="http://www.postgresql.org/support/security/">PostgreSQL Security Notices</a>
    </li>
    <li>
      <a href="http://guides.rubyonrails.org/security.html">Rails Security Guide*</a>
    </li>
    <li>
      <a href="https://github.com/relevance/rcov">Rcov*</a>
    </li>
    <li>
      <a href="http://www.rootkit.nl/projects/rootkit_hunter.html/">RkHunter*</a>
    </li>
    <li>
      <a href="https://github.com/rspec/rspec">Rspec*</a>
    </li>
    <li>
      <a href="http://www.ruby-lang.org/en/security/">Ruby Security Notices</a>
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/James+M.+Schorr" rel="tag">James M. Schorr</a>, <a href="http://technorati.com/tag/Software+Security" rel="tag"> Software Security</a>
