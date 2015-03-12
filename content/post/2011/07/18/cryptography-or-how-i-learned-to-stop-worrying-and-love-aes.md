---
author: Phillip Gawlowski
categories:
- Beginners
- Ruby
- Ruby Masters
date: 2011-07-18
layout: post
permalink: /2011/07/18/cryptography-or-how-i-learned-to-stop-worrying-and-love-aes/
tags:
- decryption
- encryption
- Phillip Gawlowski
- programming
- ruby programming
thesis_description:
- Phillip Gawlowski explains how to use encryption and decryption in Ruby.
thesis_keywords:
- Programming,Ruby programming, Phillip Gawlowski, decryption, encryption
title: 'Cryptography Or: How I Learned to Stop Worrying, and Love AES'
topsy_short_url:
- null
---

<div>
  <h3>
    Cryptography Or: How I Learned to Stop Worrying, and Love AES
  </h3>
  
  <p class="update">
    This guest post is by <strong>Phillip Gawlowski</strong>, who is living in the German wilderness of Oberberg near Cologne. Phillip spends his time writing Ruby as a hobby just for fun. He tries to make life a little easier for himself and for others when he is crazy enough to release his code as open source. He&#8217;s neither famous nor rich, but likes it that way (most of the time). He blogs his musings at <a href="http://phgaw.posterous.com/">his blog</a>.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/pg_mugshot.jpg" alt="Phillip Gawlowski" /> <span class="drop_cap">A</span> friend gave you the plans for Dr. Blofeld&#8217;s newest Doomsday Device. Over the engine noise of his Aston-Martin, he tells you: &#8220;Send this to offers@universal-exports.co.uk, and make sure it arrives there intact!&#8221;
  </p>
  
  <p>
    All you have is a laptop, wonky Internet access, and Ruby. What to do?
  </p>
  
  <h4>
    AES For Safety, SHA2 For Integrity
  </h4>
  
  <p>
    You now have two goals:
  </p>
  
  <ol>
    <li>
      Make the Doomsday Device plans unreadable, and
    </li>
    <li>
      Ensure that the data has arrived at its destination without error.
    </li>
  </ol>
  
  <p>
    Fortunately, Ruby provides an API to <a href="http://openssl.org/">OpenSSL</a>, a well-tested, widely used library and set of tools used for encryption of all kinds, and includes its own implementations of several cryptographic hashes.
  </p>
  
  <p>
    In this article we will use <a href="http://en.wikipedia.org/wiki/Advanced_Encryption_Standard">AES</a> for de- and encryption, and <a href="http://en.wikipedia.org/wiki/Secure_Hash_Algorithm">SHA</a>2 to hash data.
  </p>
  
  <h4>
    Using SHA2
  </h4>
  
  <p>
    Like many things, Ruby makes creating crypto-hashes easy:
  </p>
  
  <pre>require 'digest/sha2'
sha256 = Digest::SHA2.new(256)
sha256.digest("Bond, James Bond")</pre>
  
  <p>
    The <code>SHA2#new</code> call provides us with the bit length we want our hash to have. SHA2 exists in two variants: 256, also called SHA256, and 512, called SHA512. A longer key length takes longer to calculate, but is also more accurate, and much more difficult to attack with a rainbow table or other cryptanalysis.
  </p>
  
  <p>
    Once we have our SHA object, we pass a String of data into the <code>#digest</code> to have the hash of this data returned as a String.
  </p>
  
  <p>
    You can call the <code>#digest</code> method directly when you are working with MD5 or SHA1:
  </p>
  
  <pre>require 'digest/MD5'
Digest::MD5.digest "Bond, James Bond"</pre>
  
  <h4>
    The Advanced Encryption Standard
  </h4>
  
  <h5>
    Theory
  </h5>
  
  <p>
    As AES is a so-called symmetric-key block cipher, it operates on chunks of data, called blocks, and applies the provided key to this block to create de- and encrypted output. The use of the same key for encryption and decryption is what makes the cipher symmetric. Conversely, asymmetrical ciphers use different keys for decryption and encryption, usually a private key known only to the recipient to decrypt, and a public key known to anyone to encrypt. SSH, SSL/TLS and PGP are examples for this kind of cipher.
  </p>
  
  <p>
    The AES family has three modes of operation: 128 bit, 192 bit, and 256 bit. Just as with SHA2, you&#8217;ll find AES-128, or AES-256 being used to describe the particular block size that can be used.
  </p>
  
  <p>
    The downside to this approach is that the same key is used for each block of data, which weakens the encryption (the same data is encrypted in the same way!). The solution is to use a so called &#8220;mode of operation&#8221;, which scrambles the cipher so that it becomes indistinguishable from noise.
  </p>
  
  <p>
    A full discussion of methods of operation and their strengths and weaknesses would go well beyond the scope of this article, however.
  </p>
  
  <h5>
    &#8230;And Practice
  </h5>
  
  <p>
    Now let&#8217;s take a look at Ruby&#8217;s encryption API:
  </p>
  
  <pre>require 'openssl'
require 'digest/sha2'

payload = "Plans for Blofeld's newest Doomsday Device. This is top secret!"
sha256 = Digest::SHA2.new(256)
aes = OpenSSL::Cipher.new("AES-256-CFB")
iv = rand.to_s
key = sha256.digest("Bond, James Bond")

aes.encrypt
aes.key = key
aes.iv = iv
encrypted_data = aes.update(payload) + aes.final

puts encrypted_data</pre>
  
  <p>
    Since Ruby&#8217;s OpenSSL API is pretty straight forward (and so is the OpenSSL API, if you would like to use OpenSSL in C code), we will only discuss what&#8217;s really important.
  </p>
  
  <p>
    <code>OpenSSL::Cipher.new("AES-256-CFB")</code> sets up an AES object, with a block size of 256 bits and the CFB mode of operation. To find out which ciphers are supported, <code>OpenSSL::Cipher.ciphers</code> allows you to interrogate the class for which ciphers are understood.
  </p>
  
  <p>
    The <code>iv</code> variable stores our random Initialization Vector, random data to seed the mode of operation to ensure that each 256 bit block is encrypted uniquely, and thus (hopefully) indistinguishable from noise.
  </p>
  
  <p>
    We also take advantage of SHA2&#8217;s 256 bit variant to generate a 256 bit password from a simpler password. AES expects the encryption key to be as long as a block of data, and since creating a 256 bit password from hand is pretty difficult, we let the computer do the job. When used in production, you most likely want to add a salt to the hash, or use a user&#8217;s already hashed password.
  </p>
  
  <p>
    With the <code>#decrypt</code> and <code>#encrypt</code> methods, we put our AES object into the proper state. Behind the scenes, this initializes OpenSSL&#8217;s encryption engine. <em>These two method calls are required before any other method call!</em>
  </p>
  
  <p>
    Last but definitely not least, the <code>#update</code> and <code>#final</code> methods are where the encryption actually happens. The more data you have, the longer the chunks, and the more complex the cipher, the longer this will take. The <code>#final</code> method does the same as <code>#update</code>, but ads padding to a chunk to bring it up to the required block size.
  </p>
  
  <p>
    In case you make a mistake, or want to do another round of encryption or decryption, the <code>#reset</code> method can reset a Cipher object.
  </p>
  
  <p>
    Decryption works pretty much the same as encryption, except that we pass the encrypted data to the <code>#update</code>-method:
  </p>
  
  <pre>aes.decrypt
aes.key = key
aes.iv = iv
puts aes.update(encrypted) + aes.final</pre>
  
  <p>
    Note, however, that both the key and the IV must be the same, and thus have to be stored or transmitted to the recipient of the encrypted data!
  </p>
  
  <h4>
    Verifying Integrity
  </h4>
  
  <p>
    As we&#8217;ve already seen, a hashing algorithm can turn data of arbitrary length into a fixed length, unique stream of bytes. This can function as password storage, to generate securer keys for encryption, or, since the output of a hash algorithm is deterministic (it&#8217;s always the same for the same input) as an integrity check.
  </p>
  
  <p>
    If you&#8217;ve downloaded a Linux distribution or other software, you have already seen this, in the form of MD5 digests, with which you can verify that a download is complete and error free, like on <a href="http://www.ruby-lang.org/en/downloads">Ruby&#8217;s homepage</a>.
  </p>
  
  <p>
    We will do the same with our encrypted data, as a poor man&#8217;s <a href="http://en.wikipedia.org/wiki/Message_authentication_codes">message authentication code</a>&#8211;a technique in cryptography to ensure that a message has not been tampered with:
  </p>
  
  <pre>poor_mans_mac = sha2.digest(encrypted)</pre>
  
  <p>
    Now all that&#8217;s left is to send an email to James&#8217; employer with the Doomsday Device plans, and to give them a call to give them the IV and key.
  </p>
  
  <h4>
    Closing Remarks
  </h4>
  
  <h5>
    Think of the Future
  </h5>
  
  <p>
    Security is not a state, it is a process. You should write your security-aware code in such a way that you don&#8217;t depend on a particular cryptographic algorithm. Ruby&#8217;s API (and OpenSSL&#8217;s own API) wrap encryption abstractly, so that you can swap out the algorithm you use at any time. This is also necessary for hashing algorithms: While there are no feasible attacks against SHA2 yet, the <a href="http://en.wikipedia.org/wiki/Cryptanalysis">cryptanalysis</a> only gets better over time, as the histories of MD5 and DES show.
  </p>
  
  <h5>
    Schneier&#8217;s Law
  </h5>
  
  <p>
    <a href="http://www.schneier.com/blog/archives/2011/04/schneiers_law.html">Schneier&#8217;s Law</a> states that &#8220;any person can invent a security system so clever that she or he can&#8217;t think of how to break it.&#8221; This is why Ruby&#8217;s developers use OpenSSL to do encryption, a widely tested and certified (in some variants!) cryptographic library, instead of writing their own library.
  </p>
  
  <p>
    A mistake in your implementation can compromise your and your customer&#8217;s data, since so called &#8220;<a href="http://en.wikipedia.org/wiki/Side-channel_attack">side channel attack</a>&#8221; are used as a matter of course to attack cryptography.
  </p>
  
  <h5>
    Encryption Does Not Mean You Are Safe
  </h5>
  
  <p>
    It is important, and I cannot stress this enough, that you do not store encrypted data and the keys to access it on the same machine (ideally, you don&#8217;t store these things on the same network!), or do your encryption and decryption on the same machine that you store you encrypted data on. Whole libraries have been filled with books on how to design a secure system, from hardware to software. Above all, security is a <em>mindset</em>, and you have to be properly paranoid to secure your data <em>and</em> access to this data. Sooner or later, if you deploy, or are about to deploy, security relevant code have your code tested by outsiders. Penetration testing is worth your while.
  </p>
  
  <p>
    Asymmetric encryption has been invented to solve one problem with encryption: It is not necessary for such a cipher to transmit the key. However, they have their own set of trade offs (key trust, and computational efficiency, among others).
  </p>
  
  <h5>
    The Safest Data is No Data
  </h5>
  
  <p>
    Like the fastest code is no code at all, if you don&#8217;t store data you don&#8217;t absolutely, positively have to store, don&#8217;t even bother with it. What you don&#8217;t have can&#8217;t be compromised.
  </p>
  
  <h4>
    Conclusion
  </h4>
  
  <p>
    This article is nothing but a superficial introduction to encryption in Ruby. There are dozens of standards and regulations that govern this vast topic. However, I have tried my best to give you, fellow Rubyists, enough knowledge about this topic for you to know which questions you should ask, which is, in the end, much more important than the code itself. Now go forth, and hash an encrypt and decrypt, and, above all, have fun doing it!
  </p>
  
  <p class="alert">
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Phillip+Gawlowski" rel="tag"> Phillip Gawlowski</a>
