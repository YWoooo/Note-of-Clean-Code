# Note-of-Clean-Code

wip...

# TLDR
1. Clean code means readable code. If we have to choose, readability and maintainability are more important than efficacy, since we spend much more time reading old code than writing new code.
2. No one can write clean code at once, but we can rewrite code to make it cleaner whenever we read. Even just a little bit would be helpful.

# Intro
I take this note to remind me of the principles and patterns mentioned in this book, which I think every software engineer should understand. They may not always be correct, but most of the time, they make our works easier, at least for me.

I divide this book into four parts. I will try to conclude these parts, then add some afterthoughts.

# Why Clean Code?
In the first chapter, the author explains what clean code is and why we need it. He thinks, if my understanding isn't wrong, clean code is the code that is easy to read and easy to change.

We code for requirements, and requirements change, a lot. So in most of the time, instead of writing a whole new piece of code, we are always spending our time maintaining old code. Therefore, if we can save more time maintaining, like reading and changing, old code, our works will be more efficient. That is why code should be easy to write and easy to change.

I love this saying so much, not only because it works, but also it's calculative and crafty inside. I think this makes us engineers.

## Readability & Maintainability > Efficacy
By this saying, another engineer once told me that: if there are two kinds of code in the world,
* Code A runs faster but is hard to maintain, which means it cost better engineers;
* Code B runs slower but is easy to maintain, which means it costs better hardware.

In 21 century, hardware is so much cheaper than engineers. So a rational businessperson, like our boss, if we are lucky, would choose Code B to minimize the costs, which just fit our interset, since we are a good lazy engineer.

Of course, the best engineer can do both. But let's face that: we are not the best, at least not for now, or you won't be reading a shabby pathetic tiny little blog of an Asian yellow code monkey. So most of the time we have to choose. And for the interest of many people, a code with readability and maintainability is a good choice, even if it sacrifices efficacy.

## The Boy Scout Rule
Yet no one can write clean code at once, since it is hard, and code can always be cleaner. But at least we can make it cleaner than cleaner every time we read it, like the boy scouts "Leave the campground cleaner than you found it." Then the code will keep cleaning, evolving, and become a clean code eventually.

# How To Clean Code
From chapter 1, the author tells us why clean code. And from chapter 2 to chapter 13, the author tells us the principles and patterns to write clean code. And since for a young front-end engineer likes me, classes, systems, emergence, and concurrency are not daily routines, I will leave them out from this article for now.

> ## Before We Start
> I used to be a law school student. In law school, there are theories and articles (I am in a civil law country). However, even if only articles are obligatory, we didn't spend much time on them. Instead, we spend time on theories, since articles are from theories.  
> 
> I think this situation also happens in clean code. I mean, sure, there are principles, patterns, and practices of clean code, but they are many, and there is only one rule, one goal behind: make your code easy to read and easy to change. If we remember this, theoretically, we should be able to derive these principles and patterns all by ourselves.

## Names
Names should be easy to understand. Others should understand what this name is about immediately just by a glance, which means:
* Names should be meaningful.
* Names should declare what they store or what their input and output are.
* A long but meaningful name is better than a short but less informative name, even if it can be quite long like 'getBindingStatusOfDigitalCurrencyWallet'
* Names should be as short as possible if the requirements above are satisfied.
* Names should not have unrelative things.

## Functions
Functions should do one thing. Only one thing. Which means:
* Functions should be small. A clean code should have many small functions, instead of few large ones.
* Since they should be small, functions should have zero arguments ideally. If three or more arguments are needed, wrap as an object instead.
* Functions should be subdivided level by level. It should sound like: "To do A, we have to do a and b. And to do a, we have to do I, II, and III. And to do I, we have to do 1, 2, and 3."
* When handling errors, functions should throw exceptions instead of return error codes.
* Keep trying to abstract every duplicate logic into a single function. *Don't repeat yourself.*

I think functions should read like a story. Let's say I want to buy a shirt, then the story would be like: I find a shirt in the store, pay money by card, and get my shirt. And if I want to write a checkout function of a shirt-buying-process, it would be like:

```
function checkoutShirt() {
  const shirt = findTheShirt()
  payByCard(shirt)
  deliverToCustomer(shirt)
}
```

The wording of the story and the function is almost the same. We can easily read and picture what this function is doing like a story. Maybe I am flattering myself, but I think they are both vivid, and I think that is the spirit of a good story and a good function.

## Comments
The author thinks comments are necessary evils at best. Since if we have time to write a good comment, we should have time to clear the code, like rename variables or break down functions. That's why the best comment is no comment. So we only write comments like:
* Some information that is hard to convey in names, such as intentions, explanations, or TODOs.
* For public usages, such as Javadocs or README.md.

I think this is right for masters like the author. And again, we, or at least me, are not masters. Masters only need time to clear the code, but for us, besides time, we also need ability. Sometimes changing code risks. And sometimes we cannot change it for other reasons, like political issues. Most of the time, comments are not the best solution, but they are the best things we can do for now, and they work for a while, which is enough, just for now.

And even worse, this "the best comment is no comment" thinking becomes a cult. People use it as an excuse not to write any comments, even if their codes are not clean enough for others to understand. They will say that you are not smart enough to understand my "clean code." That would be a nightmare for other engineers.

For those two reasons, I would say we should try to write no comment. We also need to know our ability and when our code isn't clean enough without comments.

## Formatting
A well-formatted code should make the reading speed faster, which means people could spend less time and get more code information from it. Therefore:
* Both the words and lines should be short. Under a size of a screen is the best.
* Files should be small. Like functions, small but many is better.
* Important things first, like the newspaper. I think that may be one of the reasons why JavaScript has hoisting.
* Tear down codes by brackets and spaces. Avoid omit brackets like the arrow function.
* One team, one formatting rule. Use linter.  

Actually, in Chapter 17, the author says:

>*This means that each team member must be mature enough to realize that it doesn’t matter a whit where you put your braces so long as you all agree on where to put them.*

I love how he uses the word mature here. There are lots of jokes and memes about some little formatting things like spaces or braces. And yes, theoretically, the best practice about formatting does exist, but it does not bring much profit. However, the same formatting rule will make other team members spend way more time reading and writing. Save time means profits. I love profits. So when in a team, I don't argue about coding styles.  

## Object and Data Structures
It is a short chapter. And honestly, as a young front-end engineer, I work on the application layer most of the time. So I am going to throw the conclusion now:
* Objects expose behavior and hide data, while data structures expose data and have no significant behavior.
* Therefore, for an object, changing behavior is hard, but add new data is easy. For a data structure, things are otherwise.
* Do not hybrid. Choose.  

I might edit this part later.

## Error Handling
In the function section, we said functions should throw exceptions instead of return error codes. The reason is that the return of code forces the caller to handle the error immediately, which usually causes lots of if statements. That is how the code becomes ugly, hard to read.

On the other hand, thanks to the try-catch statement, the caller can handle the error at the catch block if the function throws errors as exceptions. Therefore, the concerns are separated, the error handling logic can be abstract into a single function, and the code becomes cleaner.

There are several other tips about throwing exceptions:
* List out all possible exceptions is unnecessary. In general, a few universal handlers would be plenty.
* For the same reason of not return error codes, try not to return or pass null, nor other falsy values.
* Use error messages.  

...  
...  
wip...  
wip...  
wip...  
