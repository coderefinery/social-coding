# Social coding

```{objectives}
Get an overview of motivations, benefits, but also risks of sharing and reusing code.
```


## Discussion/questions/poll: basics of sharing

```{instructor-note}
These questions 1-3 below can be used as a starting point and copied to the collaborative
document or form input for an online poll.

Alternatively, they can be discussed in voice or free-form text (discussion box below).
```

```{discussion} Social-1: Think about if and how you share
- Did you ever share your code? If yes, what motivated you? Come up with
  **reasons for sharing** your scripts/code/data
- Also think about **reasons for not sharing**
```

```markdown
## Question 1: Why would I want to share my scripts/code/data?

- A: Easier to find and reproduce (scientific reproducibility)
- B: More trustworthy: others can verify correctness and find and report bugs
- C: Enables others to build on top of your code
     (derivative work, provided the license allows it)
- D: Others can submit features/improvements
- E: Others can help fixing bugs
- F: Many tools and apps are free for open source, so no financial cost for this
     (GitHub, GitLab, Appveyor, Read the Docs)
- G: Good for your CV: you can show what you have built
- H: Discourages competitors. If others can't build on your work,
     they will make competing work
- I: When publicly shared, usually we timestamp or set a version,
     so it is easier to refer to a specific version
- J: You can reuse your own code later after change of job or affiliation

**Choose many**. Vote by adding an `o` character:
- A:
- B:
- C:
- D:
- E:
- F:
- G:
- H:
- I:
- J:


## Quesion 2: The most concerning thing for me, If I share my software now

-A: It will be scooped (stolen) by someone else
-B: It will expose my "ugly code"
-C: Others may find bugs and mistakes. What if the algorithm is wrong?
-D: I will get too many questions, I do not have time for that
-E: Losing control over the direction of the project
-F: Low quality copies will appear
-G: I won't be able to sell this later. Someone else will make money from it
-H: It is too early, I am just prototyping, I will write version to distribute later
-I: Worried about licensing and legal matters, as they are very complicated

**Choose one**. Vote by adding an `o` character:
- A:
- B:
- C:
- D:
- E:
- F:
- G:
- H:
- I:


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






## Sharing papers and academic credit

```{figure} img/sharing-papers.jpg
:alt: Image shows that we are motivated sharing our published papers since we get rewarded with academic credit in form of citations

Citation as one form of academic credit to motivate sharing papers.
```

- The goal is maximum visibility and maximum reuse.
- The more interesting science is done referencing my paper, the better for me.

## Sharing software

### Benefits

- Easier to find and reproduce (**scientific reproducibility**)
- More trustworthy: others can verify correctness and find and report bugs
- Enables others to build on top of your code (derivative work, **provided the license allows it**)
- Others can submit features/improvements
- Others can fix bugs
- Many tools and apps are free for open source
  ([GitHub](https://github.com), [Travis CI](https://travis-ci.org),
  [Appveyor](https://www.appveyor.com), [Read the Docs](https://readthedocs.org))
- Good for your CV: you can show what you have built.  Shows that you
  have useful skills.
- Discourages competitors. If others can't build on your work, they will make competing work

### Sharing is scary

- Fear of being scooped
> A license can avoid it, and you can release when you are ready. Anyway, it is very unlikely that others will understand your code and publish before you without involving you in a collaboration. Sharing is a form of publishing.
- Exposes possibly "ugly code"
> In practice almost nobody will judge the quality of your code.
- Others may find bugs
> Isn't this good? Would you not like to use a code which gives people the chance to locate bugs?
>
> If you don't release, people will assume there are bugs anyway.

- Others may require support and ask too many questions
> This can become a problem: use tools and community and protect your time.
>
> You aren't required to support anyone.


- Fear of losing control over the direction of the project
> Open source does not mean everybody can change **your version**.
- "Bad" derivative projects may appear
> It will be clear which is the official version.

## Sharing is caring

```{figure} img/sharing-code.jpg
:alt: Getting improvements back and also getting citations can motivate us to share code

Different ways we can benefit from sharing code.
```

> "I did all the ground work and they get to do the interesting science?"

- Sharing code and encouraging *derivative work* may boost your academic impact.


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


## Social coding

```{figure} img/in-out.jpg
:alt: Our work depends on ideas, articles, data, and software

Whether and what we can share depends on how we obtained the components.
```

- Whether you can share your output depends on how you obtained your input.
- **Software licenses** matter.
- Sometimes "OTHERS" are you yourself in the future in a different group/job.

## Motivation for open source software

- Enable derivative work
- Do not lock yourself out of own code
- Attract developers who want to be able to show the coding work on their CVs
- Tightly regulated domains require open source
- Open-source software (OSS) can lead to more engagement from industry which may lead to more impact
- If it's not open, it is not likely to become standard

## Code reusability

Should you reuse things that others have done?

Types of things that can be reused:
- Main libraries (e.g. numpy, scipy)
- Special scientific libs
- Random code from website
- Copying from Stack Overflow

Do you want others to reuse what you make?

How do you turn your own small project into the next numpy? Do you want to?

### What contributes to reusability?

What contributes to you being able to reuse stuff that others make, and others (or you) being able to reuse your stuff?

When you find a repository with code you would like to reuse, you may look at the following things to determine its reusability:

- Date of last code change
> ... is the project abandoned?
- Release history
> ... how about stability and backwards-compatibility?
- Versioning
> ... will it be painful to upgrade?
- Number of open pull requests and issues
> ... are they followed-up?
- Installation instructions
> ... will it be difficult to get it running?
- Example
> ... will it be difficult to get started?
- License
> ... am I allowed to use it?
- Contribution guide
> ... how to contribute and decision process?
- Code of Conduct
> ... how to make clear which behaviors are unacceptable and discouraged? How violations of Code of Conduct will be handled?
- Trust and community
> ... somebody you trust recommended it?


... most of which you have or will learn during this [CodeRefinery](https://coderefinery.org) workshop!

```{exercise} Social-2: Discuss what our "recipe" repository needs to be shareable (15 min)
Let's go back to the repository `recipe` we have created at the beginning of this CodeRefinery workshop. This repository contains a guacamole recipe and we would like you to think about what you could add in your repository to improve its reusability and encourage external contributions. Using the list given above, pick the items (one or two) you think are the most important.

If you have not created this repository, you can fork the coderefinery [recipe](https://github.com/coderefinery/recipe).

When online, this exercise is done in breakout rooms where we encourage learners to take 2-3 minutes at the end (before returning to the main room) to exchange on their choices and have a look at your colleagues' repositories. Did you all pick the same items?
```
````{solution} Solution
- Add a license: it is usually advisable to add a license at the creation of your repository but if you haven't, [https://choosealicense.com/](https://choosealicense.com/) can guide you through the process. You may add the license by copying the license text into a LICENSE file in your repository or use the Suggest this license section on choosealicense.com by entering the link to your repository on the website.
- Add a Code of Conduct: it is often complex to define your own code of conduct but you usually can reuse (or at least get inspired) by existing code of conduct; for instance, the [CodeRefinery Code of Conduct](https://coderefinery.org/about/code-of-conduct/). One important aspect of the code of conduct, is how you plan to deal with incidents.
- Add installation instructions and examples, etc. See for instance [CodeRefinery installation instructions](https://coderefinery.github.io/installation/).
````

```{keypoints}
- Share your software, if you can
- Learn to identify whether you can use other peoples software
```
