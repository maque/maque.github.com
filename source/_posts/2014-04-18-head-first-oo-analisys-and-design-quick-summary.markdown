---
layout: post
title: "Head First OO Analysis &amp; Design - Quick Summary"
date: 2014-04-18 18:09:30 +0100
comments: false
categories: Books Summary
---
{% img right /images/post/hfooad_cover.gif 180 208 'image' 'images' %}

I really love Head First books series. After all of this boring stuff you have to go through as developer, finally someone discover that picture is worth a 1k words.

I must admit that 2/3 of book is pretty interesting. Reminding things you already know but in a little
different form is always refreshing, also is always good to systematize your knowledge. Bellow is summary which helped me squeeze book into few paragraphs and bullet points.

##Great software is 3 easy steps:

1. Make sure your software does what the customer wants it to do.
	* **Don't create problems to solve problems.**
	* **You need to understand how your software is going to be used.**
	* **Plan for things going wrong.**  

	
	This is so obvious yet everyone seems to forgetting about this part. At the basic level it's just providing working, free of bugs software. So remember, it doesn't mean "provide whatever before deadline" or "make something which looks like working software and then quickly switch to different project".

	More sophisticated approach to this step is to provide software on which client can rely on as well as that software will behave as client is expecting, not the way which is easier for developers.
	Each time I see **"pending changes" in TFS** for unchanged files I'm dreaming about sending this book to the Redmond office.

2. Apply basic OO principles to add flexibility

	* Create encapsulation for duplicated parts of code
	* Encapsulate what varies
	* Apply SRP (and other SOLID stuff). CRC cards are good!
	* Code to an interface rather than to an implementation
  
  
  
  3. Strive for a maintainable reusable design.

	* Use delegation, composition and aggregation to achieve flexible and easy to maintain software 
	* Create abstraction for common behaviour
	* Write cohesive classes
		* how many classes you need to **add** to add new feature?
		* how many classes you need to  **change** to add new feature?
		
##Solving really big problems

This one I made a little bit different than in book

1. Describe system by:

	* commonality (what is the system like)
	* variability (what is the system not like)
	* from this point you can start writing features list
	* Defer details - see big picture first

2. Describe how system will be used by different actors
	
	I really don't like UML notation, personally I think it's to artificial. So I would use:
	* Mocks to show main parts of system
	* BDD to deeper analyse features and requirements
	* Define actors of system. Actor is not necessary a human or client
	* Define main actions that can be taken by actors.
	
3. Gather features from customer and figure out requirements (several requirements are part of one feature)
5. Write use cases with: 

	* clear value to the system
	* start and stop
	* external initiator (don't confuse with actor)
	
4. Prepare domain analysis (map use cases to objects in software)

6. Prepare implementation plan

7. Split features and functionalities into smaller modules. 

8. Iterate breaking big pieces into small ones.

8. Focus on significant functions first.

	* Is it part of the **essence** of the system?
	* Does this part introduce **risk**?
	* Start in place where you can reduce **risk**
	* Focus on one feature at a time

10. Build on what you've already got done whenever possible.

	Again some of those rules seems obvious yet it is so easy to just jump around trying to finish everything at first time.
	
11. Iterate through scenario until you cover:

	* all features
	* all use cases
	* all use cases scenario (happy path, alternative path)
	




