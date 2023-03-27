# Social coding

```{objectives}
- Get an overview of motivations, benefits, but also risks of sharing and reusing code.
- Learn to identify whether you can use other peoples software.
```


## Discussion/questions/poll: basics of sharing

```{instructor-note}
These questions 1-4 below can be used as a starting point and copied to the collaborative
document or form input for an online poll.

Alternatively, they can be discussed in voice or free-form text (discussion box below).
```

```{discussion} Social-1: Think about if and how you share
- Did you ever share your code? If yes, what motivated you? Come up with
  **reasons for sharing** your scripts/code/data.
- Also think about **reasons for not sharing**.
```

```markdown
## Question 1: Why would I want to share my scripts/code/data?

**Choose many**. Vote by adding an `o` character:

- A: Easier to find and reproduce (scientific reproducibility)
  - votes:

- B: More trustworthy: others can verify correctness and find and report bugs
  - votes:

- C: Enables others to build on top of your code
     (derivative work, provided the license allows it)
  - votes:

- D: Others can submit features/improvements
  - votes:

- E: Others can help fixing bugs
  - votes:

- F: Many tools and apps are free for open source, so no financial cost for this
     (GitHub, GitLab, Appveyor, Read the Docs)
  - votes:

- G: Good for your CV: you can show what you have built
  - votes:

- H: Discourages competitors. If others can't build on your work,
     they will make competing work
  - votes:

- I: When publicly shared, usually we time-stamp or set a version,
     so it is easier to refer to a specific version
  - votes:

- J: You can reuse your own code later after change of job or affiliation
  - votes:

- K: It encourages me to code properly from the start
  - votes:


## Quesion 2: The most concerning thing for me, If I share my software now

**Choose one**. Vote by adding an `o` character:

- A: It will be scooped (stolen) by someone else
  - votes:

- B: It will expose my "ugly code"
  - votes:

- C: Others may find bugs and mistakes. What if the algorithm is wrong?
  - votes:

- D: I will get too many questions, I do not have time for that
  - votes:

- E: Losing control over the direction of the project
  - votes:

- F: Low quality copies will appear
  - votes:

- G: I won't be able to sell this later. Someone else will make money from it
  - votes:

- H: It is too early, I am just prototyping, I will write version to distribute later
  - votes:

- I: Worried about licensing and legal matters, as they are very complicated
  - votes:


## Question 3: Why is software often treated differently from papers?

Free-form answers:
- ...
- ...
- ...
- ...
- ...
- ...


## Question 4: When you find a repository with code/library you would like to reuse, what are the things you look at to decide whether you use it?

Free-form answers:
- ...
- ...
- ...
- ...
- ...
- ...
```


## Comparing sharing papers and sharing code

```{figure} img/sharing-papers.jpg
:alt: Image shows that we are motivated sharing our published papers since we get rewarded with academic credit in form of citations

Citation as one form of academic credit to motivate sharing papers.
```

Sharing papers and academic credit:
- The goal is maximum visibility and maximum reuse.
- The more interesting science is done referencing my paper, the better for me.
- Nobody actively tries to limit the reach of their papers.

```{figure} img/sharing-code.jpg
:alt: Getting improvements back and also getting citations can motivate us to share code

Different ways we can benefit from sharing code.
```

Sharing code:
- "I did all the ground work and they get to do the interesting science?"
- Sharing code and encouraging *derivative work* may boost your academic impact.
- But will your work be visible if it is used two levels deep down?


## Journal policies as motivation for sharing

From [Science editorial policy](https://www.sciencemag.org/authors/science-journals-editorial-policies):
> "We require that **all computer code used for modeling and/or data analysis**
> that is not commercially available be deposited in a **publicly accessible repository**
> upon publication. In rare exceptional cases where security
> concerns or competing commercial interests pose a conflict, code-sharing
> arrangements that still facilitate reproduction of the work should be
> discussed with your Editor no later than the revision stage."

From [Nature editorial policy](https://www.nature.com/authors/policies/availability.html):
> "An inherent principle of publication is that others should be able to
> replicate and build upon the authors' published claims. A condition of
> publication in a Nature Research journal is that authors are required to make
> **materials, data, code, and associated protocols promptly available** to readers
> without undue qualifications. Any restrictions on the availability of
> materials or information must be disclosed to the editors at the time of
> submission. Any restrictions must also be disclosed in the submitted
> manuscript."

However [a study](https://www.pnas.org/content/115/11/2584) showed that despite
these policies, many people still do not share their code 😞.  This paper
includes samples of charming author responses such as:
> "When you approach a PI for the source codes and raw data, you better explain
> who you are, whom you work for, why you need the data and what you are going
> to do with it."


## Motivation for open source software

```{instructor-note}
We revisit answers to question 1 (above).
```

- Enable derivative work
- Do not lock yourself out of own code
- Attract developers who want to be able to show the coding work on their CVs
- Tightly regulated domains require open source
- Open-source software (OSS) can lead to more engagement from industry which may lead to more impact
- If it's not open, it is not likely to become standard


## Sharing software is also scary

```{instructor-note}
We revisit answers to question 2 (above).
```

- **Fear of being scooped**:
  A license can avoid it, and you can release when you are ready. Anyway, it is
  very unlikely that others will understand your code and publish before you
  without involving you in a collaboration. Sharing is a form of publishing.
- **Exposes possibly "ugly code"**:
  In practice almost nobody will judge the quality of your code.
  "Software, once written, is never really finished" (N. Asparouhova).
- **Others may find bugs and mistakes**:
  Isn't this good? Would you not like to use a code which gives people the chance to locate bugs?
  If you don't release, people will assume there are bugs anyway.
- **Others may require support and ask too many questions**:
  This can become a problem: use tools and community and protect your time.
  You aren't required to support anyone. You can also "archive" a repository to disable
  most forms of interaction (issues, PRs). Also a note in README on support level helps.
- **Fear of losing control over the direction of the project**:
  Open source does not mean everybody can change **your version**.
- **"Bad" derivative projects may appear**:
  It will be clear which is the official version.

```{discussion} Social-2: Discussion about "You aren't required to support anyone"
- Have you experienced an implicit expectation of support?
- Supporting all requests can lead to overworking and mental health issues.
- Not supporting requests can also induce guilt.
- Most projects are maintained by 1 or 2 persons.
- Most projects cannot retain contributors for a longer time. Interests change.
  "Casual contributors are like tourists visiting NYC for a weekend" (Nadia
  Asparouhova, book below).
- If you maintain all projects that you start forever, at some point it may be difficult to start new projects.
- What are your experiences? Do you agree with the above thoughts?
- Book recommendation: Nadia Asparouhova (formerly Nadia Eghbal): "Working in
  Public: The Making and Maintenance of Open Source Software (Stripe Press)"
```


## Code reusability: What contributes to reusability?

What contributes to you being able to reuse stuff that others make, and others
(or you) being able to reuse your stuff?  When you find a repository with code
you would like to reuse, you may look at the following things to determine its
reusability:

```{instructor-note}
This can be now reconnected to question 4 (above).
```

- **Date of last code change**: Is the project abandoned?
- **Release history**: How about stability and backwards-compatibility?
- **Versioning**: Will it be painful to upgrade?
- **Number of open pull requests and issues**: Are they followed-up?
- **Installation instructions**: Will it be difficult to get it running?
- **Example**: Will it be difficult to get started?
- **License**: Am I allowed to use it?
- **Contribution guide**: How to contribute and decision process?
- **Code of conduct**: How to make clear which behaviors are unacceptable and
  discouraged? How violations of Code of conduct will be handled?
- **Trust and community**: Somebody you trust recommended it?

... most of which you have or will learn during this
[CodeRefinery](https://coderefinery.org) workshop!


## Social coding

```{figure} img/in-out.jpg
:alt: Our work depends on ideas, articles, data, and software

Whether and what we can share depends on how we obtained the components.
```

- Our work depends on outputs from others. Research of others depends on our outputs.
- Whether you can share your output depends on how you obtained your input.
- A repository that is private today might become public one day.
- Sometimes "OTHERS" are you yourself in the future in a different group/job.
- Our code often starts by changing other code: **derivative work**.
- **Software licenses** matter. And this is what we will discuss in the next episode.
