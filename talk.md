class: center, middle

# Social coding and open software

Text is free to share and remix under [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/)

Radovan Bast, Richard Darst, Sabry Razick, Jyry Suvilehto

Thanks for great suggestions/corrections: Anne Fouilloux, Oxana Smirnova, Lucy Whalley

---

## Target audience

- Someone writing their own relatively small material
- Someone who wants to incorporate other code/libraries into their own projects
- Group leader who wants to decide how to balance openness and long-term strategy

### Plan

- Social coding
- Licensing
- Openness
- Software citation

---

class: center, middle

## Part 1/4: Social coding

---

## Sharing papers and academic credit

<img src="img/sharing-papers.jpg" style="width: 80%;"/>

- We want maximum visibility and maximum reuse.
- The more interesting science is done referencing my paper, the better for me.

---

## Group work before we go on

Discuss in pairs or groups (5-10 minutes):

- Come up with .emph[reasons for sharing] your scripts/code/data
- Also think about .emph[reasons for not sharing]
- Why is software often treated differently from papers

We will discuss our findings as a class.

---

## What are the benefits of sharing software?

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

## Sharing is scary (1/2)

- Fear of being scooped
> .remark[Very unlikely that others will understand your code and publish before you without involving you in a collaboration. Sharing is a form of publishing.]
- Exposes possibly "ugly code"
> .remark[In practice almost nobody will judge the quality of your code.]
- Others may find bugs
> .remark[Isn't this good? Would you not like to use a code which gives people the chance to locate bugs?]

---

## Sharing is scary (2/2)

- Others may require support and ask too many questions
> .remark[This can become a problem: use tools and community and protect your time.]
- Fear of losing control over the direction of the project
> .remark[Open source does not mean everybody can change **your version**.]
- "Bad" derivative projects may appear
> .remark[It will be clear which is the official version.]

---

## Sharing code

<img src="img/sharing-code.jpg" style="width: 80%;"/>

.quote["I did all the ground work and they get to do the interesting science?"]

- Sharing code and encouraging .emph[derivative work] may boost your academic impact.

---

## Social coding

<img src="img/in-out.jpg" style="width: 100%;"/>

- Whether you can share your output depends on how you obtained your input.
- .emph[Software licenses] matter.
- Sometimes "OTHERS" are you yourself in the future in a different group/job.

---

## Code reuse

Should you reuse things that others have done?

Types of things that can be reused:
- Main libraries (e.g. numpy, scipy)
- Special scientific libs
- Random code from website
- Copying from Stack Overflow

Do you want others to reuse what you make?

How do you turn your own small project into the next numpy? Do you want to?

---

## What contributes to reuse?

What contributes to you being able to reuse stuff that others make, and others (or you) being able to reuse your stuff?

As a .emph[developer] or .emph[user] what are you looking at when discovering a new package?

Discuss in groups ...

---

### As a .emph[developer] or .emph[user] what are you looking at when discovering a new package?

These are common things to check:

- Date of last code change .remark[... is the project abandoned?]
- Release history .remark[... how about stability and backwards-compatibility?]
- Versioning .remark[... will it be painful to upgrade?]
- Number of open pull requests and issues - are they followed-up?
- Installation instructions .remark[... will it be difficult to get it running?]
- Example .remark[... will it be difficult to get started?]
- License .remark[... am I allowed to use it?]
- Contribution guide .remark[... how to contribute and decision process?]

### This is what we teach in [CodeRefinery](https://coderefinery.org):

- Version control including project management
- Testing
- Documentation
- Reproducibility
- Code citations
- Being findable
- License

---

## FAIR principles

The FAIR Guiding Principles for scientific **data** management and stewardship (https://www.nature.com/articles/sdata201618):

- To be .emph[**F**indable]
- To be .emph[**A**ccessible]
- To be .emph[**I**nteroperable]
- To be .emph[**R**eusable]

For a discussion of FAIR in the context of software, see https://softdev4research.github.io/4OSS-lesson/.

Software development should consider .emph[FAIR principles, ideally from the start].

- .remark[Have you written a data management plan?]
- .remark[How about a software management plan?]

---

class: center, middle

## Part 2/4: Licensing

---

## Exercises

1. What is the StackOverflow license for code you copy and paste?

2. Name some software or work you have created that should be
   non-open, licensed permissively, and licensed virally.

3. What can you do with CodeRefinery lessons?  present
   them?  copy them?  modify them and present them?  send changes back
   to us?  find them in 20 years?  present them and call them a
   CodeRefinery workshop?

4. (advanced) Find the package "Omnet++" and study its license.  Compare to the
   GPL.  What do you think?

---

## Practical recommendations for licenses

- .emph[You cannot ignore licensing]: default is "no one can make copies or
  derivative works".
- License your code .emph[very early] in the project:
  ideally develop publicly accessible open source code .emph[from day one].
- Take an [OSI](https://opensource.org/licenses)-approved license: makes it easier to evaluate
  [compatibility](https://en.wikipedia.org/wiki/License_compatibility).
- Add a `LICENSE` file to your repository.
- .emph[Do not design your own custom licenses] for open source/ open use: compatibility not clear.
- Open source your code to make sure you are not locked out of your own code
  once you change affiliation.

---

## Derivative work

- If you build on something, you form a **derivative work**
- Then, the original creator may have rights to what you make
- The whole point of this talk is to make sure that .emph[you can make derivative works] and .emph[others can make derivative works from you]

---

## Derivative work examples

### Is a derivative work

- Download some code from a website and add on to it
- Download some code and use a function in your code
- Changing the code
- Extending the code
- Completely rewriting the code
- Rewriting the code to a different programming language

### Typically not derivative work

- Linking to libraries (static or dynamic), plug-ins, and drivers
- Clean room design
- You read a paper, understand algorithm, write own code

---

## Why could allowing derivative work be good for you as researcher?

- .emph[Quality] control: groups depending on your code will find bugs.
- More applications.
- Globally probably more papers (.emph[more impact]).
- If you make your code citeable, you can measure this impact and use this
  in grant applications.
- Long-term probably also .emph[more papers] for you: new collaborations and projects.
- Groups depending on your code will not want your code to disappear: they might .emph[support you],
  send improvements, and share maintenance load.

---

## Types of intellectual property (IP)

- Created automatically in certain circumstances (copyright)
- Registered after the fact in other cases (patents)
- Does not allow you to do something: allows you to prevent others
  from doing something.
- Understanding IP is important for social coding.

Next slides: **Types of IP** and **When can you use it?**

---

## Copyright

What:

- Protects creative expression
- Automatically created
- **Derivative works** usually inherits copyright of the thing derived
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

- Protects a *novel, non-obvious, technical invention*.
- Must be registered *before revealed*.  Registration involves full
  disclosure.
- Can an algorithm be patented?  Software?
- Patents are a minefield and often used to troll ("patent troll").

When you can use:
- Get expert advice.

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

.emph[Are not be protected by IP]: you can always use them.

Example: You read a paper, understand the algorithm, and write your
own software to do it.

---

## Exercises

1. Contrast Matlab vs Octave from a derivative work, intellectual
   property, and open science standpoint.

3. Do you form derivative works of your groupmates' work?  Colleagues
   who came before you?  What have you done that isn't a derivative
   work?

2. Try to trace and think of the derivative work history of this
   lesson.  How many inputs are there?  What happens if you think of
   more than copyright?

---

## Software licensing: What is free software?

### Free as in beer or free as in speech?

<img src="img/beer.png" style="width: 15%;"/>
<img src="img/speaker.png" style="width: 15%;"/>

(Emoji icons provided free by [EmojiOne](https://www.emojione.com))

### Software freedom

Is the freedom to ...

- ... run the software for .emph[any purpose]
- ... .emph[study] how the software works and to adapt it to your needs
- ... .emph[redistribute] copies of the software
- ... .emph[improve] the software and distribute your improvements to the public

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

---

## What outcomes did we have?

### 1. Custom/closed

- **Derivative work typically not possible**: others have to reimplement the wheel

### 2. Permissive

- You may lose access to **derivative work**
- Attractive for companies with proprietary software

### 3. Share-alike

- You can reuse **derivative work**
- Compatible with proprietary software

### 4. Viral

- .emph[You always have access if someone improves and re-shares]
- Not attractive for companies with proprietary software

---

## Who owns the copyright for software you write? (1/2)

- You? Your university?
- .emph[Intellectual property depends on the country and the employer!]
- So-called works made for hire.

### If you own your software:

- You can change the license.
- You can dual-license (e.g. GPL for anyone, but you can pay for commercial non-GPL).

---

## Who owns the copyright for software you write? (2/2)

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
- License text, slides, images, and supporting information under a
  [Creative Commons license](https://creativecommons.org/licenses/), and get a DOI using
  [Zenodo](https://zenodo.org) or [Figshare](https://figshare.com).

---

class: center, middle

## Part 3/4: Openness

---

class: center, middle

## Part 4/4: Software citation

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

- License your code .emph[very early] in the project:
  ideally develop publicly accessible open source code .emph[from day one].
- Make it easy to cite your code ([Zenodo](https://zenodo.org))
- Please help us to improve this material: https://github.com/coderefinery/social-coding

### Where to place your code

- https://github.com: public (unlimited) or private (up to 3 collaborators or unlimited educational) repositories
- https://gitlab.com: public or private repositories
- https://source.coderefinery.org: public or private repositories

---

## Great resources

- http://blog.milkingthegnu.org/2008/03/10-answers-for.html
- http://depth-first.com/articles/2006/12/29/dispelling-open-source-confusion-an-introduction-to-licenses/
- http://oss-watch.ac.uk/resources/ipr
- http://rkd.zgib.net/scicomp/open-science/open-science.html
- https://choosealicense.com (can send automatic pull request to your GitHub repo)
- https://github.com/coderefinery/software-licensing
- https://hintjens.gitbooks.io/social-architecture/content/chapter2.html
- https://softdev4research.github.io/4OSS-lesson/
- https://softdev4research.github.io/recommendations/
- https://tldrlegal.com/
- https://users.aalto.fi/~darstr1/cheatsheets/ipr-cheatsheet.pdf
- https://www.software.ac.uk/choosing-open-source-licence
- http://www.oreilly.com/openbook/osfreesoft/
- http://www.rosenlaw.com/oslbook.htm
