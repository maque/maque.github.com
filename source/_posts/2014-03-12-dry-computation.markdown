---
layout: post
title: "DRY Computation"
date: 2014-03-12 18:09:13 +0100
comments: false
categories: PrinciplesRevisited
---
There is this one nice & simple principle: don’t repeat yourself. Basically you shouldn’t repeat your code if you can create more generic method, after all it’s good for code maintainability.

But being to DRY on your side can easily cause strange behavior. Recently I’ve noticed really weird behavior of SQL Management Studio. If you will open lots of tabs and close them, you will see what i mean – whole SQL MS window is jumping like a tiger from Winnie the pooh.

Let’s imagine for a moment how this could happen because of following DRY principle .

We’re starting with something simple. We create a function for closing one tab:

``` c#
	private void DisposeTab(Tab tab){
	  //release allocated memory
	  //a lot of different stuff that is needed in this place
	  AllTabs.Remove(tab);
	}

	private void CloseTab(Tab tab){
	   DisposeTab(tab);
	   RedrawWindow();
	}
```

It’s nice, it’s simple and int works. Now we need second function for closing all tabs at once. And we now that already we have function for closing one Tab. We wanted to stay DRY and created something like this:

```
	private void ClosseAllTabs(){
	  foreach(Tab tab in AllTabs){
		  CloseTab(tab);
	  }
	}
```

And I’m like 100% sure that it is what is happening in SQL MS. Window is jumping because it’s refresh itself for each closed tab instead of waiting for closing them all and then re-draw window. Code look like DRY but actually it is unnecessary repeated in loop. We should not only avoid code repeating but also avoid repeating computation.

Maybe you remember about that when you are dealing with getting all rows from database, maybe you remember about that with advanced computation – compute them once and put into table. But as MS SQL example shows it is easy to forgot when dealing with simpler things.

I found it’s very useful to start opposite way – writing function for dealing with list or array of items instead of one item. For this example it would be something like that:

```
private void DisposeTab(Tab tab){
  //release allocated memory
  //a lot of different stuff that is needed in this place
  AllTabs.Remove(tab);
}
private void CloseTabs(List<Tab> tabs){
  foreach(Tab tab in tabs){
	  DisposeTab(tab);
  }
  RedrawWindow();
}

private void CloseTab(Tab tab){
  CloseTabs(new List<Tab>{tab});
}

private void ClosseAllTabs(){
  CloseTabs(AllTabs);
}
```

After all you will always end up with writing method for dealing with all items (adding, removing, changing) and starting with this point can let you avoid a lot of problems in future. Also very quick it made you to rewrite your methods and optimize all code.