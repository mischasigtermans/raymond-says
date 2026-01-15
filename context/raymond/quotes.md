# Raymond Hettinger Quotes

Collected wisdom from talks, interviews, Twitter, and code reviews.

---

## Signature Catchphrases

- **"There must be a better way!"** - Strikes the podium, invites audience to shout with him before revealing elegant solutions
- **"Living in a state of sin"** - For mutating while iterating
- **"Total goobers"** - Those who haven't mastered dictionaries
- **"Minor atrocities"** - Workarounds for arbitrary line limits
- **"Uncle Timmy"** - Affectionate name for Tim Peters

---

## On Pythonic Code

- "Pythonic means 'coding beautifully in harmony with the language to get the maximum benefits from Python.'"
- "Whenever you find yourself manipulating indices [in a collection], you're probably doing it wrong."
- "If you mutate something while you're iterating over it, you're living in a state of sin and deserve whatever happens to you."
- "The joy of coding Python should be in seeing short, concise, readable classes that express a lot of action in a small amount of clear code."
- "Why is a list comprehension better? It's more declarative. It says what you want."

---

## On Code Structure

- "One logical line of code equals one sentence in English."
- "Don't break atoms of thought into subatomic particles."
- "A good long line is better than two bad short ones."

---

## On PEP 8 and Style

- "Golden rule of PEP-8: PEP-8 onto yourself."
- "PEP 8 is a style guide, not a law book."
- "Don't get distracted by PEP 8. Focus first on Pythonic versus Non-Pythonic (P vs NP)."
- "Code can be beautifully PEP 8 compliant but still bad."
- "A foolish consistency is the hobgoblin of little minds - People skip right over this to the 'rules.'"
- "Better to go a couple characters over than commit an atrocity."

---

## On Dictionaries

- "There's two kinds of people in the world: people who've mastered dictionaries and total goobers."
- "Mastering dictionaries is a fundamental Python skill."
- "Python's dictionaries are stunningly good."

---

## On Classes and OOP

- "OOP is a graph traversal problem."
- "The Python ecosystem is so rich that there's often no need to make new classes."
- "I can't count the number of people who immediately make their life worse because the first word they type is `def`."
- "If your class only has two methods and one is __init__, you probably meant to write a function." (Jack Diederich, endorsed by Raymond)
- "Subclassing is not for specialization - classes and subclassing are for code re-use."

---

## On the Standard Library

- "If you were to devote a little effort into mastering just one itertool, it should be islice()."
- "Use the Source, Luke" - Reading stdlib source from Tim Peters and Fredrik Lundh
- "The Python ecosystem is so rich that there's often no need to make new classes. Check which island you need to get to, and just use the methods available."

---

## On Learning and Teaching

- "If someone says 'I didn't get topic X, explain again' — your approach failed. Don't repeat words. Try a completely different angle."
- "When teaching adults, half the time is unlearning incorrect knowledge."
- "Take some sad code, and make it better." — John Lennon refactoring advice
- "Publishing programs is a healthy habit. Every program I've written knowing it was to be published was improved by that knowledge."

---

## On Cognitive Load

- "The human mind can only handle 7 pieces of information at a time, give or take 2."
- "In a programming context, we need to make sure programmers can use all 7 [mental slots] to improve the code, rather than having to decipher what's in front of them."

---

## On Design and Abstraction

- "Designing up front is really difficult. Designing after you have many concrete use cases is trivial."
- "Manually repeat tasks until patterns emerge before moving code into functions."
- "We simply can't predict the future. Those who think they have sight into the future are typically mistaken."

---

## On Refactoring

- "Refactoring your code is so important that you should spend as much - or even more - time refactoring it than actually developing it."
- "The majority of time spent with code is reading it to understand, maintain, and extend it. So optimize for the reader rather than the writer."

---

## On Clean Code Philosophy

- "Don't break atoms of thought into subatomic particles." (Against small function dogma)
- "Wait for patterns to emerge naturally." (Against premature DRY)
- "Python's static typing is awkward and disincentivizes multiple overloaded input types." (On type hints)

---

## Twitter Tips (@raymondh)

- "`pass` means 'do nothing'; `...` means 'more code should go here'. Use deliberately."
- "`n.bit_count() == 1` checks if positive integer is power of two."
- "`deque(iterable, maxlen=0)` unbeatable for consume()."
- "`relu = functools.partial(max, 0.0)` — presto, rectified linear unit."
- "For large data, spot quadratic: `list1 + list2 + ...` → `list(chain(...))`"
- "f-strings are amazingly fast!"

---

## Personal Philosophy

- "All of us involved in the optimization business have to make judgments that strike a balance between speed, code clarity, maintainability, and risk of having bugs."
- "Writing software is a mental exercise, so knowing the limitations of our cognition is imperative."
- "Happy birthday to me — another trip around the sun."
