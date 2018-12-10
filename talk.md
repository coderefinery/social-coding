name: inverse
layout: true
class: middle, inverse

---

# Social science and open software

## [Radovan Bast](https://bast.fr) (NeIC, UiT-The Arctic University of Norway)

Text is free to share and remix under
[CC-BY-SA-4.0](https://creativecommons.org/licenses/by-sa/4.0/).

Based on material with contributions by:
- Richard Darst
- Sabry Razick
- Oxana Smirnova
- Jyry Suvilehto

---

layout: false

.left-column[
# Plan for this talk

<img src="img/in-out.svg" style="width: 50%;"/>

- Things .emph[go in], things .emph[come out].  You can't survive
  without both.

]

.right-column[
## - Why software and what you make matters
## - When can you take from others?
## - How can you give to others?
## - How to grow a community around your code

... and how does this relate to CodeRefinery?
]

<!-- Tell an anecdote: we were working on this talk, and wondered this
talk was originally about software licensing, but why do you care?  Do
you use software you find online regardless of license status?  The
answer is that you yourself can effectively do whatever you
want... but if you want to build on others, you have to care.  If you
want others to build on you, you have to care. If others can't build
on you, you won't get followers to give you citations. -->

---

## Why software matters in research

.emph[**Data** is part of research output]

- Funding agencies often ask for a data management plan

.emph[**Software** is part of research output]

- Simulations which generate data
- Control software for instruments
- Post-processing of measurements
- Data processing
- Portals and apps
- Spreadsheets
- Scripts and tools which produce graphs and compute statistics

Curiosity: Not too many projects consider a software management plan **yet**.

Data/software should make science completely **shareable** and
**reproducible**... .emph[but is it?]

---

## Sharing is caring

### What are the benefits of sharing software?

- Easier to find and reproduce (.emph[scientific reproducibility])
- More trustworthy: others can verify correctness and find and report bugs
- Enables others to build on top of your code (derivative work, .emph[provided the license allows it])
- Others can submit features/improvements
- Others can fix bugs
- Many tools and apps are free for open source
  ([GitHub](https://github.com), [Travis CI](https://travis-ci.org),
  [Appveyor](https://www.appveyor.com), [Read the Docs](https://readthedocs.org))
- Good for your CV: you can show what you have built

---

## Sharing is scary

### Why do some researchers prefer not to share?

- Fear of being scooped
- Exposes possibly "ugly code"
- Others may find bugs
- Others may require support and ask too many questions
- Fear of losing control over the direction of the project
- "Bad" derivative projects may appear - fear that this will harm the reputation

... we will discuss these in this talk and during this week.

---

## Sharing is caring

### What are the benefits of sharing software?

- Easier to find and reproduce (.emph[scientific reproducibility])
- More trustworthy: others can verify correctness and find and report bugs
- Enables others to build on top of your code (derivative work, .emph[provided the license allows it])
- Others can submit features/improvements
- Others can fix bugs
- Many tools and apps are free for open source
  ([GitHub](https://github.com), [Travis CI](https://travis-ci.org),
  [Appveyor](https://www.appveyor.com), [Read the Docs](https://readthedocs.org))
- Good for your CV: you can show what you have built

---

## Sharing is scary

### Why do some researchers prefer not to share?

- Fear of being scooped
- Exposes possibly "ugly code"
- Others may find bugs
- Others may require support and ask too many questions
- Fear of losing control over the direction of the project
- "Bad" derivative projects may appear - fear that this will harm the reputation

---

- Fear of being scooped
> .remark[Very unlikely that others will understand your code and publish before you without involving you in a collaboration.]
- Exposes possibly "ugly code"
> .remark[In practice almost nobody will care/judge.]
- Others may find bugs
> .remark[Isn't this good? Would you not like to use a code which gives people the chance to locate bugs?]
- Others may require support and ask too many questions
> .remark[More about this later.]
- Fear of losing control over the direction of the project
> .remark[Open source does not mean everybody can change **your version**.]
- "Bad" derivative projects may appear
> .remark[It will be clear which is the official version.]

---

## Derivative works

- If you build on something, you form a **derivative work**
- Then, the original creator may have rights to what you make
- .emph[The whole point of this talk is to make sure that *you can
  make derivative works* and *others can make derivative works from
  you*]

### Is derivative work

- Changing the code
- Extending the code
- Completely rewriting the code
- Rewriting the code to a different programming language

### Typically not derivative work

- Linking to libraries (static or dynamic), plug-ins, and drivers
- Clean room design

Exercise: what *is* and *is not* a derivative work of the presentation
you are seeing now?

---

## Why is allowing derivative work good for you as researcher?

- .emph[Quality] control: groups depending on your code will find bugs.
- More applications.
- Globally probably more papers (.emph[more impact]).
- If you make your code citeable, you can measure this impact and use this
  in grant applications.
- Long-term probably also .emph[more papers] for you: new collaborations and projects.
- Groups depending on your code will not want your code to disappear: they might .emph[support you],
  send improvements, and share maintenance load.

---

## Derivative work examples

Is a derivative work:
- Download some code from a website and add on to it
- Download some code from a website and use a function in your code

Not a derivative work:
- You read a paper, understand algorithm, write own code.


---

## Types of intellectual property (IP)

- Created automatically in certain circumstances (copyright)
- Registered after the fact in other cases (patents)
- Does not allow you to do something: allows you to prevent others
  from doing something.
- Understanding IP is important for social science.

Next slides: **Types of IP** and **When can you use it?**

---

## Copyright

What:

- Protects creative expression
- Automatically created
- **Derivative works** usually inherits copyright of the thing derived
  (next slide)
- Time frame: essentially forever (lifetime + X years)

When can you use:

- When there is a license saying you can
- Limited other cases (private use, fair use: context dependent)
- In practice: people do many things, but then can't share their
  output if copyright

Applicable to: software, writing, graphics, photos, certain datasets,
this presentation. *Very broad.*

---

## Patents

- Protects a *novel, non-obvious, technical invention*
- Must be registered *before revealed*.  Registration involves full
  disclosure.
- Can an algorithm be patented?  Software?
- Patents are a minefield and often used to troll ("patent troll").

When you can use:
- Get expert advice

Examples: RSA cryptography (possibly good), Amazon 1-click (probably bad).

---

## Trademarks

What:
- Protects a name/brand from impersonation.

When you can use:
- To factually refer to something.
- In general, just don't use an existing name in order to deceive.

Examples: "Mozilla Firefox", "Apple", "Linux".

---

## Datasets

What:
- The EU has a database directive which restricts data mining on
  databases.
- Has a somewhat similar effect to copyright, because copyright would
  not apply to data mining.
- A good license also gives rights to data mine.  So not a major concern.

When you can use datasets:
- The license allows
- Your country has exceptions for research
- The data doesn't come from the EU

---

## Ideas

What:
- An idea
- **is not be protected** by IP: you can always use

Example: You read a paper, understand the algorithm, and write your
own software to do it.

---

## Social science: what is relevant to scientists?

- You come up with .emph[ideas]
- Ideas are published in .emph[papers]
  - Papers might have limited access, but .emph[anyone can use the ideas] in them
  - Your goal is to get citations for your paper by people using or improving your ideas
- Your .emph[software] may implement an idea in your paper
  - For your ideas to be used, software should be usable
  - If people can use or .emph[improve your software] they can more easily use your ideas
  - If people cannot reuse and extend your software, .emph[its impact will be limited]

The middle part of this talk is about how to allow others to use your
.emph[copyright (and data)]

<!---
Maybe scientists aren't the only audience, but may be useful to start here anyway.

- Emphasize that trying to protect your code usually doesn't do you
  that much good: your ideas are purposely put out there when you
  publish.
- If your code isn't free software, people might take your code and
  run it, but not reuse it.  Following up on your work becomes much
  harder, since they have to re-create everything.

Copyright protects a certain expression.  If you publish a paper on
your idea, someone can always read that paper and re-create your
method.  Don't think that copyright gives you magic protection.
-->

---

## Exercises (1/2)

1. Contrast Matlab vs Octave from a derivative work, intellectual
   property, and open science standpoint.

3. Do you form derivative works of your groupmates' work?  Colleagues
   who came before you?  What have you done that isn't a derivative
   work?

2. Try to trace and think of the derivative work history of this
   lesson.  How many inputs are there?  What happens if you think of
   more than copyright?

---

## Software licensing

---

## What is free software?

### Free as in beer or free as in speech?

<img src="img/beer.png" style="width: 15%;"/>
<img src="img/speaker.png" style="width: 15%;"/>

(Emoji icons provided free by [EmojiOne](https://www.emojione.com))

### Software freedom

Is the freedom to ...

- ... run the software for any purpose
- ... study how the software works and to adapt it to your needs
- ... redistribute copies of the software
- ... improve the software and distribute your improvements to the public

---

## What is free software?

### Software freedom and research

Is the freedom to ...

- ... run the software for any purpose: .emph[new applications]
- ... study how the software works and to adapt it to your needs: .emph[new applications, less reinventing wheels]
- ... redistribute copies of the software: .emph[more users, more citations]
- ... improve the software and distribute your improvements to the public: .emph[fix bugs, new science]

### Typical confusion

- Free software does not mean that software is for free
- Open source license does not mean you need to share everything immediately
- Open source does not mean public domain: software in the public domain has no owner
- Open source does not mean non-commercial: plenty of companies produce and support it

<!---
Example: Ubuntu is free software.  It is supported by a company called
Canonical.  Many people make free software.  Canonical packages it up as
Ubuntu.  Because the software guarantees freedom, Canonical can't make Ubuntu
closed-source.  Canonical doesn't make money out of the software itself - only
their actual value-added services which they offer to companies.

Example: you come up with a formula and a piece of software to improve a
chemical process.

Relate this to the value of what people have and want - much software is so
small it isn't/can't be sold, but through a proper license others can help it
make an impact.
-->

---

## In practice you need to choose a license

- Code without license is not useful for reuse or derivative work.
- Example why choice of license matters, X vs. SunView: https://lwn.net/Articles/26608/


## Software licensing and open source explained with cakes

<img src="img/cake-1.svg" style="width: 15%;"/>

- Imagine you compose a recipe for a really tasty cake (a great idea).
- In regular intervals you distribute cakes (release binaries).
- Your family and friends love it.
- But you can only bake so many.

(cake emoji licensed under CC-BY-SA-4.0, attribution: [EmojiOne](https://www.emojione.com))

<!--- Perhaps may be worth saying that this is a metaphor - the
ingredients list and basic instructions simply facts, so not
protectable.  However, your description *is* protectable. -->

---

## Possible outcomes 0/4: closed

### Closed source (recipe never released)

- Your cake is celebrated by The New Yorker magazine.
- People will have difficulties to reproduce your celebrated recipe.
- Nobody else will improve your recipe.
- Bad copycats might appear, you don't get any credit.
- Fewer tasty cakes will get consumed.

---

## A friend tells you: why not distribute the recipe?

- Put your recipe on GitHub.
- Start the OpenCake organization.
- Get feedback / start a mailing list.
- More people will be able to enjoy the cake (increase impact).
- Maybe somebody will find ways to improve the recipe.
- Everyone will know that it was your idea even though somebody else bakes it.

---

## Mrs. X (running a famous restaurant) finds your cake recipe on GitHub

<img src="img/cake-1.svg" style="width: 15%;"/>

- The chef tries it and it is great.
- The chef suggests improvements (derivative work):

<img src="img/cake-2.svg" style="width: 15%;"/>

- It becomes part of the restaurant menu.
- Or does it? .emph[Depends on your license!]

<!--- What is most important is *how are the changes handled*.  Since
you are giving the recipe out yourself, people can use it "personally"
however they want.  But if they want to improve/reuse/redistribute it,
then what?  -->

---

## Possible outcomes 1/4: custom

### No license or custom license

- No restaurant chef will touch it: too much hassle to employ a lawyer to be sure
  that the cake can be served to customers.
- But maybe they will bake it and eat it and not distribute it and that is OK
  ("fair use" provision permits the making of copies for own use).

<!--- The restaurant industry is infamous for copying recipes and there are
very few published court cases. Let's skim over this fact and stay in the
fictitious example though. -->

---

## Possible outcomes 2/4: permissive

### License: MIT or Apache or BSD-2

- It is OK to use the recipe and sell the cake.
- It is OK to not share the improved recipe.
- If somebody becomes sick, it is not the fault of the OpenCake organization (limit of liability).
- You may not get the improvements back to use yourself.

### License: BSD-3

- In addition to the above it is understood that the updated recipe are not endorsed by the OpenCake organization.

---

## Possible outcomes 3/4: share-alike

### License: GNU Lesser GPL (LGPL)

- The famous restaurant has to share only the improved cake recipe but can keep the rest of the menu closed.
- The restaurant guests have to be able to exchange the cake from the menu by improved cakes from other restaurants (dynamic relinking).

### License: Mozilla Public License v2.0

- Like LGPL but do not require that the modified cake can be exchanged by the restaurant guest.

---

## Possible outcomes 4/4: viral

### License: GNU GPL or GNU Affero GPL

- If the cake is a part of the menu, the famous restaurant has to
  .emph[share the recipes of the entire menu].
- You can use their improved recipe and improve it further:

<img src="img/cake-2.svg" style="width: 15%;"/>
<img src="img/cake-3.svg" style="width: 15%;"/>

- Other restaurants can then reuse and improve the full menu and the hope is that we will all eat better food.
- You support open restaurants. You can use everything they do, too.

<!--- Example of benefits of virality in software: Linksys routers and
GPL's kernel image. Some company used linux, didn't distribute source.
They were fourced to distribute it, and that has directly led to
a huge community of firmware modders.  -->

---

## What outcomes did we have?

### 1. Custom/closed

- Others have to reimplement the wheel, **no derivative work possible**

### 2. Permissive

- Attractive for commercial software companies
- No guaranteed access to **derivative work**, but typically not a problem in practice
- .emph[You still have access, even if someone else buys your business.]

### 3. Share-alike

- Compatible with proprietary software
- You can reuse **derivative work**

### 4. Viral

- You have to share the **derivative work** and cannot restrict access
- Not attractive for commercial software companies.
- .emph[You always have access if someone improves and re-shares.]

---

## Who owns the copyright for software you write?

- You? Your university?
- .emph[Intellectual property depends on the country and the employer!]
- So-called works made for hire.

### If you own your software:

- You can change the license.
- You can dual-license (e.g. GPL for anyone, but you can pay for commercial non-GPL).

### If you accept contributions (pull requests), you may not be the only owner anymore!

- Clarify licensing strategy .emph[before] - otherwise you won't have
  all rights to your code.

### If you do not own your software, you can:

- Request open-sourcing directly (preserves your rights!).
- Request a transfer of ownership (check with your university).

<!--- Fun story: I once had a friend who worked at IBM.  In their
division, they always tried to open-source what they worked on,
because if they didn't some other division could come and take it away
from them to put in some product.  By open sourcing, they ensure even
their internal rights to do their work! -->



---

## Practical recommendations

### Starting and contributing to a project

- .emph[You cannot ignore licensing]: default is "no one can make copies or
  derivative works".
- License your code .emph[very early] in the project:
  ideally develop publicly accessible open source code .emph[from day one].
- Take an [OSI](https://opensource.org/licenses)-approved license: makes it easier to evaluate
  [compatibility](https://en.wikipedia.org/wiki/License_compatibility).
- .emph[Do not use custom licenses] for open source: compatibility not clear.
- Open source your code to make sure you are not locked out of your own code
  once you change affiliation.


### Licensing

- Add a `LICENSE` file to your repository (GitHub understands it):
  - Use GitHub web to add file named `LICENSE` and it helps you select!
  - You should check that GitHub can automatically detect the license.
- License your supporting information (images) under
  creative commons (use [Zenodo](https://zenodo.org) or [Figshare](https://figshare.com)).

---

## Social science

- Licensing is one thing... but will anyone ever use it?
- Too much use is rarely a problem.  What if you want people to use
  your work and .emph[make you the leader?]

The second half of CodeRefinery can be considered to be strategies to
make your software more usable by others (and you six months from
now!).

Here we summarize what is to come...

---

## Version control

- Minimum requirement to share software with others
- The basis of everything everything else

Somewhat related: project management/issue system:

- Included as part of Gitlab/Github/etc.
- Allows communication, issue tracking, and community.

CodeRefinery lessons: Introduction to version control, Collaborative
distributed version control, etc.

---

## Reproducibility and build systems

- Can someone duplicate your results easily?
- Can someone actually install your software and use it?
- If they can't, there is a high barrier to use

CodeRefinery lesson: Reproducible Research

---

## Software testing

- How can someone modify your software and make sure they don't break
  it?
- Software tests are verification that your software works the right
  way before and after.
- Software tests allow others to modify and improve software with
  confidence.
  - .emph[And you!]

CodeRefinery lessons: Software testing

---

## Documentation

- Code alone is not
- Is there a more modern solution than README files?
- Are there clear contributor instructions?  How to get started, how
  to submit first pull request, how to test, etc?

CodeRefinery lessons: Documentation

---

## Does this look like a serious project?

### As a .emph[developer] or .emph[user] what are you looking at when discovering a new package?

These are common things to check:

- Date of last code change .remark[... is the project abandoned?]
- Release history
- Versioning .remark[... will it be painful to upgrade?]
- Number of open pull requests and issues - are they followed-up?
- Installation instructions
- Example .remark[... will it be difficult to get started?]
- License .remark[... am I allowed to use it?]

---

## Communication and atmosphere

- Do you welcome people to your project?
- Do you give credit?
- Do you respond to issues and pull requests?
- Do you have a Code of Conduct? https://www.contributor-covenant.org
- Openness and transparency
- Document whether/how/where you want to be asked questions
- Chat or mailing list
- If the project grows, agree on a decision process for controversial changes

---

## Software citation

- Get a [DOI](https://en.wikipedia.org/wiki/Digital_object_identifier) using [Zenodo](https://zenodo.org).
- Open source license can't demand citation, but it is required by science ethics anyway.
- Make it as easy as possible! Clearly say what you want cited.
- Make it easy for scripts and tools, use the [Citation file format](https://citation-file-format.github.io):

```
cff-version: 1.0.3
message: If you use numgrid, please cite it as below.
authors:
  - family-names: Bast
    given-names: Radovan
title: numgrid
version: 1.0.2
doi: 10.5281/zenodo.1470277
date-released: 2018-10-24
```

### Publishing papers about software

- [The Journal of Open Source Software](https://joss.theoj.org/about)
- [In which journals should I publish my software?](https://www.software.ac.uk/resources/guides/which-journals-should-i-publish-my-software)


---

## Conclusions and discussion

- Track code using version control, learn Git
- Use code review: review each other's code changes
- Make it easy to reproduce your computational results
- Open source your code and make it accessible (GitHub, GitLab, Bitbucket)
- Make it easy to cite your code ([Zenodo](https://zenodo.org))

### Where to place your code

- https://github.com: public repositories
- https://gitlab.com: public or private repositories
- https://source.coderefinery.org: public or private repositories

### Great resources

- http://rkd.zgib.net/scicomp/open-science/open-science.html
- https://softdev4research.github.io/4OSS-lesson/
- https://softdev4research.github.io/recommendations/


---

## Exercises (2/2)


1. What is the StackOverflow license for code you copy and paste?

2. Name some software or work you have created that should be
   non-open, licensed permissively, and licensed virally.

3. (advanced) Find the package "Omnet++" and study its license.  Compare to the
   GPL.  What do you think?

---

## Good resources for software licensing

- https://www.software.ac.uk/choosing-open-source-licence
- https://choosealicense.com
- http://oss-watch.ac.uk/resources/ipr
- http://www.rosenlaw.com/oslbook.htm
- http://depth-first.com/articles/2006/12/29/dispelling-open-source-confusion-an-introduction-to-licenses/
- http://blog.milkingthegnu.org/2008/03/10-answers-for.html
- http://www.oreilly.com/openbook/osfreesoft/
- https://tldrlegal.com/
- https://hintjens.gitbooks.io/social-architecture/content/chapter2.html
- https://users.aalto.fi/~darstr1/cheatsheets/ipr-cheatsheet.pdf

