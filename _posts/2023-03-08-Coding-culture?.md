---
layout: post
title: Coding culture?
---

I have been working as software developer in multiple organizations, both open as well as closed source, and professional-grade projects as well as random, hacky projects.
Personally, i am always interested in the most idiomatic way to write your code, which of course is depending of the language you are writing in, for multiple reasons:
- Writing idiomatic code in a language will help others familiar with that language to understand your code easier. If i try to apply patterns common in Rust or Haskell like `Maybe` to a Python codebase, less people familiar with Python will easily understand it.
- Writing idiomatic code will help to reduce bugs. This is the same argument that is used for design patterns, and idiomatic code is most often nothing else[^1].
Also: Not using language-specific tricks (some consider Python's comprehension methods there) to help persons not familiar with Python understand what is happening is totally acceptable, and an idiom by itself.

These and way more things are part of what is considered coding culture, and is often enforced by styleguides.
Recently, i wondered about another topic in this field: What measures are taken to prevent bugs, and when bugs occur, what measures are taken to resolve them, and also to prevent further bugs that are similar.
Here, i noticed i am used to two different main approaches:
- In one approach, every code is peer-reviewed during merge request, and even simple things like how a ternary operator is structured are discussed.
In the codebase where this happens, there aren't that many automated tests - for one, because there was just no way to executed such tests until recently, for the other, cause it was somewhat of a living codebase.
Development happens to some degree on the product, and the repository is more of a tracking system.
During reviews, it often happens that small logical bugs are found, e.g. unintended shortcutting in conditions or alike.
- In the other approach, there are no peer-reviews, but the ratio of automated tests is way higher, especially, features are only considered implemented once a test covers a requirement that specifies the feature.
This results in a shorter period of time between feature implementation until it is considered implemented (read: deployed) compared with the first approach, and therefore faster development.

So what is this all about?
My aversion against the second approach continues to increase day by day.
While this is surely personal, i find that i have more trouble reading my colleagues code that isn't peer-reviewed compared to the code that is reviewed by one or more people before being merged.
In another subjective metric, the amount of bugs being found afterwards seems to be about equal with both approaches.
What is different tho is the subjective severity: With peer reviews, bugs tend to be less severe, and are easier to fix, whereas the bugs that slipped through all of the automatic testing are all of harder to locate, more complicated to understand, tougher to fix without breaking something else.
Of course, all of this is rather project specific, and the projects at hand are of very different nature, but this is not a scientific study, but rather a blog post of my personal observations.

The final question that came upon me today:
If the former approach feels like it leads to worse bugs that require more complicated fixes, then does this get even worse over time, when every patch is one step closer to a patchwork?

[^1]: If you haven't read [Design Patterns](https://en.wikipedia.org/wiki/Design_Patterns) by the Gang of Four, you should consider doing so.
