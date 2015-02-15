---
title: Some Security Concerns While Programming In Ruby
author: Satish Talim
date: 2008-04-28
layout: post
permalink: /2008/04/28/some-security-concerns-while-programming-in-ruby/
categories:
  - Ruby
tags:
  - command injection attacks
  - programming
  - Ruby
  - ruby programming
  - security
---
<div>
  <p>
    Making critical information available across the Internet has arguably been one of the most profound business enablers in the history of technology. It has meant expanded markets, increased productivity, and streamlined processes. Unfortunately, it has also meant a profound increase in operational risk. Vulnerabilities like <a href="http://www.owasp.org/index.php/Command_Injection">command injection attacks</a> result from inadequately designed or written Ruby code, creating opportunities for attackers to threaten privacy and steal data. The only way to eliminate vulnerabilities is to get them where they live: in the source code itself.
  </p>
  
  <p>
    Let me show you two possible vulnerabilities:
  </p>
  
  <ol>
    <li>
      <strong>System Commands and Command Injection Attacks:</strong> The Ruby language supports the use of system commands. Generally, these calls are used to execute external functions outside of the program, including launching a different application or URL, sending an email, gaining access to files, or executing other commands from the operating system. The module <strong>Kernel</strong> provides the <strong>system</strong> method. From a security perspective, <strong>Kernel.system</strong> provides an opportunity for a user to bypass normal security measures by injecting malicious input into the application. If the parameter to the <strong>system</strong> command is not validated, an attacker can execute any command on the system for which the application has privileges. For example, if an attacker can terminate the intended command string using â€œ;â€ or â€œ&â€, they may be able to insert their own malicious commands such as â€œrm â€“rf /â€ or â€œdel /S /Q ?AS *â€. In general, there are no safe way to use <strong>system</strong>. If <strong>system</strong> must be called, then extreme care should be taken to ensure that input is properly validated prior to being used to execute a <strong>system</strong> command.
    </li>
    <li>
      <strong>Improper Exception Handling:</strong> Improper error messages can provide critical information about an application which may aid an attacker in exploiting the application. The most common problem occurs when detailed internal error messages such as stack traces, database dumps, and error codes are displayed to the user. Security analysts view logging and error handling as potential areas of risk. It is recommended that production applications should not use, for example, a <strong>puts e.backtrace.inspect</strong> call unless it is being directly committed into a log that is not viewable to the end user.
    </li>
  </ol>
  
  <p>
    By analyzing the code itself to identify these flaws and errors, organizations can drastically reduce their levels of risk and exposure.
  </p>
  
  <p>
    <strong><em>What other vulnerabilities in Ruby (not Rails) can you think of? I&#8217;d definitely like to hear and add them here.</em></strong>
  </p>
  
  <p>
    <strong><span style="color:red;">Hat Tip:</span></strong> The idea for this post came while reading <a href="http://www.ouncelabs.com/index.asp">Ounce Labsâ€™</a> solutions that enable organizations to identify, prioritize and eliminate business risk to the enterprise, caused by software security vulnerabilities.
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Security" rel="tag">Security</a>
