# Debugging 

Debugging is a complicated skill. It's a mix of experience ("I've seen this before ..."), strategies ("I'll try back-tracing this time"), specific knowledge ("This pandas method modifies the data in-place"), patience ("Breath in, breath out, try again") and good habits ("If only I'd written tests!"). You will never know everything about debugging because every project is different. But if you practice good habits, you will be ready to fix new bugs when you find them.

Much of your time as a computer programmer will likely be spent debugging. This phenomenon is best described by a quotation from one of the first computer pioneers, Maurice Wilkes:

As soon as we started programming, we found to our surprise that it wasn’t as easy to get programs right as we had thought. We had to discover debugging. I can remember the exact instant when I realized that a large part of my life from then on was going to be spent in finding mistakes in my own programs.

— Maurice Wilkes, 1949

In order to be better prepared to undertake the more complex future debugging that you will be doing, we aim to give you here both a sense of the philosophy of debugging as well as to teach you how to use some of the practical tips that make testing and debugging easier. The Philosophy of Debugging

Debugging is one of the most creative and intellectually challenging aspects of programming. It can also be one of the most frustrating. To a large extent, the problems that people face debugging programs are not so much technical as they are psychological. To become successful debuggers, you must learn to think in a different way. There is no cookbook approach to debugging, although Nick Parlante’s 11 Truths of Debugging (given below) will probably help. What you need is insight, creativity, logic, and determination. As computer scientists, it is important to remember that the programming process leads you through a series of tasks and roles:

Design - Architect 
Coding - Engineer
Testing - Vandal
Debugging - Detective

-[Stanford university paper on debugging](https://web.stanford.edu/class/archive/cs/cs106a/cs106a.1184//handouts/9%20-%20Debugging.pdf)
- [Stanford university paper on debugging](https://cs.stanford.edu/people/nick/compdocs/Debugging.pdf)

## Using a IDE Debugger 
- Using Breakpoints:
  - You can add and remove breakpoints, before and while you are debugging a program.
  - You can enable and disable breakpoints without removing them.
- Debugger Buttons:
  -  Skip Ahead: You can skip ahead to the next breakpoint or the end of the program.
  - Step Over: You can step over a function call to ignore its implementation.
  - Step In: You can step into a function call to debug it's implementation.
  - Step Out: You can step out of a function call to resume debugging the main program.
  - Restart: You can restart your debugger at the beginning of the program.
  - Exiting: You can exit the debugger at any point of execution.
- Reading State
  - At each point in a program's execution, you can find the value of any declared variable in the Variables pane.
- The Call Stack
  - You understand the relationship to between the callstack pane, local variables and function calls.
  - You can view the local variables for each level of the callstack by clicking on it.
- Tracing Recursion: 
  - You can debug a recursive algorithm by tracing through it's callstack in the debugger.
- Variable Categories: 
  - You can explain the difference between Locals, Globals, Function Variables, Class Variables, and Special Variables
- Watch Expressions: 
  - You can create helpful watch expressions and use them to track information about your program that is not explicitly declared in the code.

## Debugging Mindset and Strategies
- [Rubber Duck Debugging](https://rubberduckdebugging.com/)
- [Someone else will always use your program](https://www.youtube.com/watch?v=CfCiW4UhqLo)
- You can study a program skeptically, always asking "how can I break this program?".
- Pair programming with someone you trust.
- You can predict a program's behavior while stepping through in the debugger:
  - Which line will execute next?
  - What will change in memory (callstack and variables)?
- You can identify steps of execution that surprise you. This will help understand the gap between what a program does do, and what it should do.
- You can recognize these four types of bug: overt vs. covert, and persistent vs. intermittent.
- You can clearly describe a bug by answering these questions:
  - what should the program do? Name specific test cases and lines of code!
  - What does the program do? Name specific test cases and lines of code!
-  You can trace a program backwards from a surprising step to understand how it happened (either mentally or on paper, VSCode's debugger only goes forward).

## Avoiding bugs in the first place

Debugging is twice as hard as writing the code in the first place. Therefore, if you write the code as cleverly as possible, you are, by definition, not smart enough to debug it.

- [Hackers Law](https://github.com/dwmkerr/hacker-laws#kernighans-law)
- Pair programming with someone you trust.
- Always use the simplest and most understandable solution. (KISS)
- Develop your code one small step at a time, writing and running tests for each change before moving on.
- Have others read and review your code, they will find mistakes you missed and think of improvements you wouldn't.
- Write less code. Keep your end goal in mind and avoid writing any code that is not absolutely necessary to reach your goal.
- Keep a Bug Log; Write down bugs you've encountered and how you fixed them. This log will help you avoid making the same mistakes, and double as inspiration for how to fix new bugs.

## 11 Truths about Debugging 
- Intuition and hunches are great—you just have to test them out. When a hunch and a fact collide, the fact wins. That's life in the city.
- Don’t look for complex explanations. Even the simplest omission or typo can lead to very weird behavior. Everyone is capable producing extremely simple and obvious errors from time to time. Look at code critically—don’t just sweep your eye over that series of simple statements assuming that they are too simple to be wrong.
- The clue to what is wrong in your code is in the values of your variables and the flow of control. Try to see what the facts are pointing to. The computer is not trying to mislead you. Work from the facts.
- Be systematic and persistent. Don’t panic. The bug is not moving around in your code, trying to trick or evade you. It is just sitting in one place, doing the wrong thing in the same way every time.
- If you code was working a minute ago, but now it doesn’t—what was the last thing you changed? This incredibly reliable rule of thumb is the reason your section leader told you to test your code as you go rather than all at once.
- Do not change your code haphazardly trying to track down a bug. This is sort of like a scientist who changes more than one variable in an experiment at a time. It makes the observed behavior much more difficult to interpret, and you tend to introduce new bugs.
- If you find some wrong code that does not seem to be related to the bug you were tracking, fix the wrong code anyway. Many times the wrong code was related to or obscured the bug in a way you had not imagined.
- You should be able to explain in Sherlock Holmes style the series of facts, tests, and deductions that led you to find a bug. Alternately, if you have a bug but can’t pinpoint it, then you should be able to give an argument to a critical third party detailing why each one of your functions cannot contain the bug. One of these arguments will contain a flaw since one of your functions does in fact contain a bug. Trying to construct the arguments may help you to see the flaw.
- Be critical of your beliefs about your code. It’s almost impossible to see a bug in a function when your instinct is that the function is innocent. Only when the facts have proven without question that the function is not the source of the problem should you assume it to be correct.
- Although you need to be systematic, there is still an enormous amount of room for beliefs, hunches, guesses, etc. Use your intuition about where the bug probably is to direct the order that you check things in your systematic search. Check the functions you suspect the most first. Good instincts will come with experience.
- Debugging depends on an objective and reasoned approach. It depends on overall perspective and understanding of the workings of your code. Debugging code is more mentally demanding than writing code. The longer you try to track down a bug without success, the less perspective you tend to have. Realize when you have lost the perspective on your code to debug. Take a break. Get some sleep. You cannot debug when you are not seeing things clearly. Many times a programmer can spend hours late at night hunting for a bug only to finally give up at 4:00A.M. The next day, they find the bug in 10 minutes. What allowed them to find the bug the next day so quickly? Maybe they just needed some sleep and time for perspective. Or maybe their subconscious figured it out while they were asleep. In any case, the “go do something else for a while, come back, and find the bug immediately” scenario happens too often to be an accident.