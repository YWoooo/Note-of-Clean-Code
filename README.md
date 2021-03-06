# Note-of-Clean-Code

# TLDR
1. Clean code means readable code. If we must choose, readability and maintainability are more important than efficacy, since we spend much more time reading old code than writing new code.
2. There are rules to clean code. Read the list of rules below or jump to the conclusion.
3. No one can write clean code at once, but we can rewrite code to make it cleaner whenever we read. Even just a little bit would be helpful.

# Intro
I take this note to remind me of the rules mentioned in this book, which I think every software engineer should understand. They may not always be correct. But most of the time, they make our works easier, at least for me.  

I divide this book into four parts. I will try to conclude these parts, then add some afterthoughts.

# Why Clean Code?
In the first chapter, the author explains what clean code is and why we need it. He thinks, if my understanding is not wrong, clean code is the code that is easy to read and easy to change.  

We code for requirements, and requirements change, a lot. So in most of the time, instead of writing a whole new piece of code, we are always spending our time maintaining old code. Therefore, if we can save more time maintaining, like reading and changing, old code, our works will be more efficient. That is why code should be easy to write and easy to change.  

I love this saying so much, not only because it works, but also it is so calculative and crafty inside. I think this makes us engineers.  

## Readability & Maintainability > Efficacy
By this saying, another engineer once told me that: if there are two kinds of code in the world,  
* Code A runs faster but is hard to maintain, which means it cost better engineers;
* Code B runs slower but is easy to maintain, which means it costs better hardware.

In 21 century, hardware is so much cheaper than engineers. So a rational businessperson, like our boss, if we are lucky, would choose Code B to minimize the costs, which just fit our interset, since we are a good lazy engineer.  

Of course, the best engineer can do both. But let us face that: we are not the best, at least not for now, or you will not be reading a shabby pathetic tiny little blog of an Asian yellow code monkey. So most of the time we have to choose. And for the interest of many people, a code with readability and maintainability is a good choice, even if it sacrifices efficacy.  

## The Boy Scout Rule
Yet no one can write clean code at once. Since it is hard, and code can always be cleaner. But at least we can make it cleaner than cleaner every time we read it, like the boy scouts "Leave the campground cleaner than you found it." Then the code will keep cleaning, evolving, and become a clean code eventually.  

# How To Clean Code
From chapter 1, the author tells us why clean code. And from chapter 2 to chapter 13, the author tells us the principles and patterns to write clean code. And since for a young front-end engineer likes me,  systems, emergence, and concurrency are not daily routines, I will leave them out from this article for now.  

> ## Before We Start
> I used to be a law school student. In law school, there are theories and articles (I am in a civil law country). However, even if only articles are obligatory, we did not spend much time on them. Instead, we spend time on theories, since articles are from theories.  
> 
> I think this situation also happens in clean code. I mean, sure, there are principles, patterns, and practices of clean code, but they are many, and there is only one rule, one goal behind: make our code easy to read and easy to change. If we remember this, theoretically, we should be able to derive these principles and patterns all by ourselves.  

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

```js
function checkoutShirt() {
  const shirt = findTheShirt()
  payByCard(shirt)
  deliverToCustomer(shirt)
}
```

The wording of the story and the function is almost the same. We can easily read and picture what this function is doing like a story. Maybe I am flattering myself, but I think they are both vivid, and I think that is the spirit of a good story and a good function.  

## Comments
The author thinks comments are necessary evils at best. Since if we have time to write a good comment, we should have time to clear the code, like rename variables or break down functions. That is why the best comment is no comment. So we only write comments like:  
* Some information that is hard to convey in names, such as intentions, explanations, or TODOs.
* For public usages, such as Javadocs or README.md.

I think this is right for masters like the author. And again, we, or at least me, are not masters. Masters only need time to clear the code, but for us, besides time, we also need ability. Sometimes changing code risks. And sometimes we cannot change it for other reasons, like political issues. Most of the time, comments are not the best solution, but they are the best things we can do for now, and they work for a while, which is enough, just for now.

And even worse, this "the best comment is no comment" thinking becomes a cult. People use it as an excuse not to write any comments, even if their codes are not clean enough for others to understand. They will say that you are not smart enough to understand my "clean code." That would be a nightmare for other engineers.

For those two reasons, I would say we should try to write no comment. We also need to know our ability and when our code isn't clean enough without comments.

## Formatting
A well-formatted code should make the reading speed faster. People could spend less time and get more code information from it. Therefore:  
* Both the words and lines should be short. Under a size of a screen is the best.
* Files should be small. Like functions, small but many is better.
* Important things first, like the newspaper. I think that may be one of the reasons why JavaScript has hoisting.
* Tear down codes by brackets and spaces. Avoid omit brackets like the arrow function.
* One team, one formatting rule. Use linter.  

Actually, in Chapter 17, the author says:

>*This means that each team member must be mature enough to realize that it doesn???t matter a whit where you put your braces so long as you all agree on where to put them.*

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

Honestly, this might be the part I agree with the most in this book. Reducing the amount of if-else statements improves the coding experience and readability significantly. And I think this tip is an example of the "*Functions should do one thing.*" rule.  

## Boundaries

Boundaries are codes we write to connect with other codes, like a third-party code or an unknown, none-exist-yet code. We should not trust other codes too much. Therefore, instead of using other codes directly, we should write codes to connect, to pack, to encapsulate them. These codes are boundaries.  

And I think the key to boundaries is the interface. We do not care about the implementation of other codes. Instead, we just have to validate the output of these codes is what we need. And the way of validation is testing. That is what learning tests are about.  

However, the author says we should try writing tests instead of only reading documents while learning the third-party code. From this saying, I can understand why someone would say TDD is a cult, yet as a nobody, I would not say TDD or learning tests are wrong. Anyway, a clear boundary to keep our code from other codes is needed.  

And none-exist-code can be tread like third-party codes. I mean, if we do not care about the implementation, what is the difference between existing or not? We just mock the output. That is the beauty of a clear boundary: theoretically, it makes our code work no matter how the other codes are changed. It adapts.  

> You may see I stop listing and keep murmuring in this part. Since I think this chapter is quite, well, a masterpiece.

## Unit Tests
So here comes the famous TDD. TDD asks us to write unit tests before we write codes. According to this book, there are three laws of TDD:
* You may not write production code until you have written a failing unit test.
* You may not write more of a unit test than is sufficient to fail, and not compiling is failing.
* You may not write more production code than is sufficient to pass the currently failing test.

I quote these laws directly since I think no matter what we thought about TDD, we better understand it, at least, well, give them some respect.

In my personal experiences, TDD is like talking manners with packs of apes inside a jungle. It is a good thing, a good thing in the wrong place and wrong beings. Perhaps many Americans or European companies are good enough to understand TDD, yet it is hard to do it if the requirements keep changing and changing. It is not impossible, but it cost a lot, since how do you write tests if you do not know what the output should be? And perhaps no one knows. Not the engineers, not the PMs, even not the bosses, not the investors. 

I guess this is life, no one fucking knows what things should be, yet somehow it keeps going.

Back to this book, I am not saying TDD is wrong. Who am I anyway? I will try to understand TDD and practice it in some other projects. But I think it would not harm if we write tests after the production codes.  

And there are other tips about testing:
* Tests should be clean, yet clean as production codes are unnecessary.
* By clean, which means tests also follow principles above, like nicely named, small, do one thing only, .etc.
* Tests should be easy to run. Use CLI, IDE, or other tools to run tests in one or even zero keys. Do not run them manually.
* Tests should be fast, or we will be lazy to run them.
* Check the coverage. Again, use tools.  
* If codes are not easy to test, refactor codes. It is one of the purposes of writing tests.  

We may not want to follow any of the above. But by all means, tests are necessary. Codes without tests are not clean.  

## Classes
Classes and functions are both should be small. Small here mean two things:
* A class should have only one reason to change, aka SRP.
* Classes should be cohesive, which means they should have fewer variables and methods, but these variables and methods should use each other more. Small but compact.  

Like the author said: "No, we???re not going to repeat the exact same text from the Functions chapter." So basically, principles and patterns about functions still work here.  

## Other Chapters
As mentioned, I am going to skip systems, emergence, and concurrency. And the third part of the book is some case studies. There are exercises in cleaning up some code. Since this is a note about principles, patterns, and practices of clean code for me, who do not use Java, I also skip this part. I think these studies are more valuable for back-end engineers and Java users. So here is the conclusion.

# Conclusion
Chapter 17 is the final of this book. It is a list of smells and heuristics, aka the sign of dirty, unclean codes. And I think it can be the examination or overview of how a clean code should or should not be. The list is long. I select some I think is handy and helpful:

**Comments**  
* Obsolete comment
* Redundant Comment
* Poorly Written Comment,
* Commented-Out Code

**Environment**  
* Build and Tests Require More Than One Step

**Functions**  
* Too Many Arguments
* Dead Function

**General**  
* Obvious Behavior Is Unimplemented
* Duplication
* Code at Wrong Level of Abstraction
* Too Much Information
* Dead Code
* Inconsistency
* Clutter
* Misplaced Responsibility
* Use Explanatory Variables
* Function Names Should Say What They Do
* Follow Standard Conventions
* Replace Magic Numbers with Named Constants
* Be Precise
* Encapsulate Conditionals
* Function Should Do One Thing
* Functions Should Descend Only One Level of Abstraction
*
**Names**
* Choose Descriptive Names
* Use Standard Nomenclature Where Possible

**Tests**
* Insufficient Tests
* Use a Coverage Tool
* Do not Skip Trivial Tests
* Test Boundary Conditions
* Test Should Be Fast

Besides these, I also have my little list about unclean codes:  

## God Classes
God classes are classes that can do many things like an omnipotent god. They usually contain too many variables and methods so that they can be thousands of lines, literally. The number of codes already makes it hard to maintain, and the number of reasons for changing class makes it worse. Yet the worst thing is whoever writes these classes usually has a god complex. They think their creations are perfect and refuse to change or even only break them down.  

## Poor English
It may sound like a cultural hegemony or orientalism, spoken from an Asian specifically, but I think a good programmer should at least not be weak at English. Like it or not, most codes are in English, so poor English usually leads to poor namings or poor comments, reduce readability and maintainability.  

## Lack of Craftsmanship
I love how James O. Coplien mentioned the Japanese and their philosophy like 5S, much as I hate how some of my coworkers treat their code without only a little respect. While the path may be different, the heart of keeping code clean should be the same. So it is easy to sense someone does not care about the shit about clean code and only wants to get rid of the work. That is how the code starts to rot, or other coworkers, like me, pay their debts.  

That is why I am going to use this part as the ending. We maybe disagree with this article or this book. But we as programmers, no matter in the interest of others or ourselves, should always try to make codes cleaner and better.
