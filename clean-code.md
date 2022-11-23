# Clean Code

By Temba Mateke written in November of 2022 (unless I updated it later and forgot to update this caption)

# Introduction

This is a collection of my thoughts on what clean code is and how to write clean code. Think of clean code as the opposite of “but it works” code. “But it works” code is code that that makes no sense, is extremely hard to edit, and is very sensitive to small changes. Clean code makes perfect sense, is easy to edit and easy to fix when something goes wrong. Clean code saves everyone time and heartache.

**Notes**

1. While this writing and most of the ideas it contains are my own, a lot of it is based on ideas other people have had and shared with me personally or otherwise.
2. I reserve the right to change my mind about any and all of the opinions expressed in this document
3. This is document written _prescriptively_ ****\*****to myself****\*****. If you are not me, take it as a description of my opinions on these matters.
4. If you disagree with anything, or have any suggestion, please include them as comments on this document
5. This is a living document. It is intentionally, perpetually unfinished. That said, if you notice anything weird in the document, feel free to let me know.

# Readability

It is critical that code is easy to understand. Code that is easy to understand is easy to debug, improve, refactor, and fix. Code that is hard to understand is hard to debug, improve, refactor, and fix. This means code that is hard to understand or “thick” code is code that comes with a tax. That is, everyone who works with the thick code has to pay a time tax to first understand how the code works. In most situations, this time tax also translates directly into a monetary tax. This tax can be avoided altogether if the code is written for readability from the start.

The following sections explain how to do this.

## Writing for Readability

Making code easy to understand is similar to making any form of writing easy to understand.

### Clarity

The first step is having a clear idea of what it is you are trying to communicate, or in the case of code, what it is your code is supposed to be doing. If you are not absolutely sure about what your code is supposed to be doing, you cannot possibly write your code in a way that is easy to understand.

If what you are coding is a task that was given to you and you are not clear on what exactly the task is, ask questions to the person who gave you the task. If it is something that you came up with yourself, ask yourself those questions. You should be able to explain in a few words what it is you’re trying to do and why.

### Modularity / Fragmentation

The next step, is breaking down the main idea into a few smaller chunks. In the case of writing these chunks may be anything from chapters to sentences. In the case of coding it could be anything from packages and modules to individual lines of code.

At any given level of abstraction, there shouldn’t be too much or too little fragmentation. Too little and splitting up the code actually makes it harder to understand, too much and things become hard to find. Practically, this means a given folder generally shouldn’t contain just 1 file or over 100 loose files, a given file shouldn’t contain just 1 function or over 100 functions, a given function shouldn’t contain just 1 line or over 100 lines.

There are exceptions for all the examples above, but the general idea is that if something gets too big, break it into smaller pieces by grouping subcomponents. This makes code easier to understand because the reader can read through five lines of code at a high level and get a summary of everything that is going on. If they don’t understand what any particular subcomponent is doing, they can “step into” that component and see how it is defined.

### Simplicity

When trying to communicate efficiently, we use no more words than we need to and we avoid uncommon words and grammar.

Similarly, when writing code for readability, it should be written in no more lines / characters than necessary while avoiding techniques that are difficult to understand. This means simplifying an shortening everything so long as the process does not make the code harder to understand.

There are some situations in which performance must be prioritized over readability. In these situations you may want to include comments to explain in a few words what the code is doing and why it is being done this way.

### How many lines?

The number of lines of code in a file, function, class, etc. are dictated by the basic principles of modularity and simplicity and are ultimately up to the developer. That said, files with thousands of lines are best avoided because of the sheer amount of time spent scrolling and searching.

A related issue is that of the number of characters per line. A commonly used standard is no more than 80 characters per line of code. Limiting the number of characters per line reduces the need for horizontal scrolling and makes viewing two files side-by-side easier. There is no harm in just adopting this standard limit, but equally no harm in going with a limit of 100 or 120. In the end, there should be some limit as very long lines of code are difficult to work with. Enforcing this standard is best done with a code formatter.

## Naming

### Consistency

Similar things should have similar names.

- Variables that store similar data should have similar names. A function with a `location` parameter should not be passed a variable called `coords`. Two variables that both store contact information should not be named `employeeContactInfo` and `contactInfoForCustomer`. They should be named in the same way `employeeContactInfo` and `customerContactInfo`. Giving similar variables similar names makes code easier to understand.
- Stick to one case per language per project. That case could be `snake_case`, `camelCase`, `kebab-case`, or something else, whatever it is, use it consistently. Otherwise you will face issues like naming a property `num_segments` in one file and wondering why accessing that property with `numSegments` in another file is not working.

### Conformity

If a good name already exists, use it. Examples:

- Classes in Python and Java are typically defined using `UpperCamelCase`. Sticking to this convention, makes code easier for newcomers to understand your code.
- If a repository uses the name `pts` to refer to an array of points, stick to that convention rather than introducing a new name like `points` or `pnts`. Alternatively if the names currently in use in a project are causing issues, suggest alternatives to your team. Whatever is ultimately agreed upon should be used ****\*\*\*\*****consistently****\*\*\*\***** across the project.
- If a documentation for a package contains examples, try to name your variables similar to what is used in the examples

### Compactness

Shorter names take up less space, and are easier to read and type. Examples:

- If you’re dealing with `points` in a certain file, you can instead use the abbreviation `pts` for `points` and `pt` for a single `point`.
- An extreme version of this can be implemented if you have a short function with one parameter that does a simple manipulation on the input. In this case, you can use just the first letter of the parameter. For instance, instead of `degToRad(theta)` you can use `degToRad(t)`. Instead of `handleEvent(event)` you can have `handleEvent(e)`. In simple functions like this, there is no ambiguity about the single-letter variables.
- This also means variables names should never start with “a”, “the”, ”an” etc. as these words add nothing to the meaning and just take up space. Similarly, adding the data type to a variable should be avoided as much as possible. Instead of `wordList` try `words`. Instead of `firstNameString` try use `firstName`. Only include the data type if doing so makes the code easier to understand.
- Use common coding abbreviations like `avg`, `max`, `arr`, `props`, `conn`, `fig`, `img`, `num`, rather than spelling out the full word. These stand for average, maximum, array, properties, connection, figure, image, and number. If a common unambiguous abbreviation exists, use it.

Exceptions:

- Some names just have to be long, but even so, no variable name should be more than five words or so
- If you’re reading data from an external source (data file, api, package), you may have no control over what names were used to define the data. Just read the data in using whatever names the other party used, the immediately rename the variables if the names they chose are not suitable for your project.

## Formatting

Formatting code is changing how code is presented without changing any of the functionality. There are various rules for formatting code in various languages in a way that is clean and easy to read and manipulate. For almost every single one of those languages and frameworks, there exists a [formatter extension for VS Code](https://marketplace.visualstudio.com/search?target=VSCode&category=Formatters&sortBy=Installs) that will automatically format the code for you. If you do not use VS Code, consider using it. Otherwise, there are likely code formatter extensions that work with your IDE.

# Building from Scratch

## Test Everything

Never write code, assume it will do what you want it to do, and move on. Every line of code you write must be tested at least once. Failing to do this will result in the frequent issue of debugging your code for hours only to find that one little function was defined wrong from the start and was just never tested.

For very large projects being worked on by large teams, this testing can be automated to save time. Automated tests can be used to check that new changes to a codebase do not break code that used to work.

## Work Top-Down

Thoughts are translated into code in a top-down fashion. The developer first thinks of what it is they are trying to do, they then break down that task into subtasks, and break the subtasks down further until they know how to translate a subtask directly into a line of code.

The trap to avoid is drilling down to that first line of code before listing out the high-level subtasks.

### Example 1

You are trying to create a tool that analyzes your bank transactions and presents the results on a chart

1. You realize that the first thing you will have to do is find a way to access your bank’s API. So you write some code that does that. Then you decide the next step is formatting that data so that it is easier to work with. Then you write code that analyzes the data, say grouping transactions by spending category and so on. At the end of this process, your code may work, but it will likely be messy.
2. You identify that the main three subtasks are `getData`, `processData`, and `plotData`. You could even write placeholder functions with these names. After identifying these, you dive into the first function and identify the next three subtasks as `accessBankApi`, `downloadData`, `formatData`. You then create placeholder functions for these.

Working top-down creates modular code with hardly any effort. It also forces you to think about what your code is doing at a high level, as well as the interfaces between modules. Notice that in the second case, you are forced to think about what kind of data is being passed between `getData`, `processData`, and `plotData`, before those functions are even written. Whereas, in the first case, it is all too easy to just take whatever data is available at the start and manipulate it into whatever format suits the immediate next step.

## E****************\*\*****************xpand and Contract****************\*\*****************

Coding is best done in cycles of expansion and contraction.

### Expansion - Creating the new

During expansion, we are adding new code to a project. This is a creative and inherently messy process where we experiment and adjust until we get the desired results. This is analogous to creating a draft of a piece of writing.

### Contraction - Cleaning the old

During contraction, we are improving functional code in a project. This is a careful logical process where we take functional code and improve readability, performance, and neatness. The resulting code often takes up less space than it did at the start, hence the name contraction. This is analogous to editing a draft.

### Duration

The whole cycle can be as short as a few minutes when working on a function at a time, or as long as a few days, when working on larger components. Expanding for more than a few days is dangerous as lots of new code is being introduced without it being properly cleaned, tested, and finally committed. Long cycles also make contraction harder since you may forget how certain functions work.

### Benefits

Most developers will find that they already use cycles of expansion and contraction while developing code. For those who have not explicitly recognized it, understanding the concept and having a name for it allows them to leverage these tools better.

Those who do not develop with cycles of expansion and contraction are either never contracting, or always contracting. Never contracting means messy code is never cleaned up. Always contracting means wasting time perfecting each line of code, before knowing if that code will even be used or work. Neither is ideal. The analogs in draft editing would be never editing your drafts (never contracting) and toiling over every word in the first few sentences before completing a draft (always contracting).

## Shorten the Feedback Loop

- If it takes 1 second for you to know if your code works or not, you can code a little, test, fix, test, code a little, test and so on. When you’re done you will have tested almost every line of code and will know that it does what you expect (at least under normal conditions).
- If it takes you 15 seconds for you to know if your code works or not, you won’t want to test it after every line or every few lines because you’ll get bored waiting 15 seconds. You’ll test less frequently and ultimately have more issues to debug which will slow you down
- Basically, reducing the amount of time between wanting to know if your code works and knowing if your code works is almost always worth the time put into it.

# Version Control

## Commits

### Size

Commits are the units of change in Git. As a developer, you get to decide how big or small those units are. Generally speaking, very large commits can be problematic as they can be hard to understand and dangerous to revert. Small commits are preferable for this reason.

### Messages

Commit messages are one of those things that you don’t need to think too much about. If your team doesn’t have their own conventions, find some conventions online and stick to them. here is an example: [https://www.gitkraken.com/learn/git/best-practices/git-commit-message](https://www.gitkraken.com/learn/git/best-practices/git-commit-message). This is sort of a “solved problem”, you just need to pick a solution that works for you.

## Branches

Branches are great for isolating copies of the same code such that they do not interfere with one another. This is most helpful when collaborating on a project. This document is not a git tutorial so I will limit my notes to saying only that you should be using branches if you are working on a team.

There are also several neat things you can do with branches like triggering notifications (email, Slack, phone) when certain things happen on certain branches, or using pushes to certain branches to trigger automatic deployments using GitHub actions.

## GitHub

- Include a ReadMe for every project no matter how small
- make sure you gitignore package folders like `node_modules` or `.venv`.
- store secret keys, passwords, api keys, etc in GitHub secrets and insert them dynamically using github actions
- autodeploy everything that you can
- use pull requests to document big changes
- use issues to track issues (could use a personal to do list, but github issues are built for just this sort of thing)

- …
- speeding up code:
  - Write good code, but don’t spend time optimizing code before it is in use. Having something run 10x faster is not really helpful it it was running in a few milliseconds before the optimization. Write reasonably good code, and speed it up if you notice parts of it that seems slow.
  - Use profilers to see which parts of your code are slowest
  -

# Choosing Tools

When writing code we use various tools including coding languages, frameworks, integrated development environments (IDEs), packages, etc. How do we go about choosing the best tools for the task at hand?

## Popularity

A great place to start is with popularity. Popular tools tend to offer the following advantages over unpopular tools:

- There will likely be lots of **online support** for the issues you face i.e. almost all issues you face will be one Google away from a solution
- There will likely be **fewer bugs**, since the large number of users means higher bug detection rates and more demand for issues to be resolved
- There will likely be ****************\*\*\*\*****************good documentation****************\*\*\*\***************** for the tool since lots of people want to know how to use it, and many are able to contribute to the docs
- There will likely be **more tutorials** explaining exactly how to get started with the tool and achieve specific outcomes with it
- It will likely be **highly optimized** since small “inconveniences” will be felt by a large number of users, some of whom will be compelled to optimize the issues away.

The list goes on.

### Issues with Popularity

One critical way in which the popularity metric can fail is with legacy tools. That is, if a lot of people \***\*used\*\*** _to use_ a certain tool, there there will be lots of documentation and tutorials, but it may be outdated. There won’t necessarily be good online support or fewer bugs either. For this reason it is helpful to distinguish between tools that \***\*are\*\*** popular and tools that ****\*\*****used to be****\*\***** popular.

Another thing to look out for is tools that are popular for something other than your desired use case. For instance, you may find that Python is the most popular programming language and then proceed to create a computationally intensive package in Python. What you would have missed is that Python is popular for being flexible and easy to learn, not fast.

### Measuring Popularity

There are various ways to measure popularity of a tool. Here are a few:

- Using [Google Trends](https://trends.google.com/)
- By GitHub Stars
- Number of weekly downloads
- Googling “most popular [tools]”
- Just googling the kind of tool you want and seeing what comes up first e.g. “http request package python”

## Other Factors

Other things to consider when selecting tools include:

- What tools your team is already using
  - If everyone is already using a certain tool, sticking to that tool makes it easier for everyone else to understand what you are doing
- What tools you have used before
  - If you’ve used a certain tool in the past and it worked well … use it again!
- What tools

# Other Tidbits

- avoid magic numbers. magic numbers are numbers that exist without variable names. All numbers should be defined as variables so that we know what they stand for. One exception is very simple calculations such as halving some variable with `x/2`. You don’t need a variable name for `2`. On the other hand if this was `x/160`, then the intention is less clear, and it would be good to extract `160` as a variable.
- Comments - comments should be used sparingly to explain code that doesn’t explain itself. If the code doesn’t explain itself, try to write it in a way that it does without sacrificing performance or taking up too much space. If that is not possible, add a small comment.
  - Avoid commenting out code. Good version control will allow you to retrieve that code if you ever need it (you probably won’t). There are exceptions to this, but prefer deleting to commenting out.
- sorting functions / imports
  - If there are more than 5 or so imports, they should be sorted. Best to put built-in packages at the top, third-party packages int he middle, and custom imports at the bottom. Then sort alphabetically.
  - If Function A is used in Function B, and they are both in the same file, put Function A first, with Function B below it. Sometimes this is required, when it is not, it is still good to stick to this pattern. This makes finding high and low level functions easier.
