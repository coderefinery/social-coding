# Licensing

```{objectives}
- Knowing about what derivative work is and whether we can share it.
- Get familiar with terminology around licensing.
- Practical advice for software licensing.
```


## Copyright

```{figure} img/tate.jpg
:alt: Photo of somebody taking a photo of an artwork that contains the text "WHO OWNS WHAT?"
:width: 50%
```

- **Trademark**: Protects a name/brand from impersonation.
- **Patent**: Protects a novel, non-obvious, technical invention.
- **Copyright**: Protects **creative expression**: software, writing, graphics, photos, certain datasets, this presentation.
  Practically "forever" (lifetime of author + 70 years).

Copyright controls whether and how we can distribute the original work or the **derivative work**.


## Derivative work: Sampling/remixing

```{figure} img/ai/record-player.png
:alt: Generated image of a monk operating a record player
:width: 50%
```
[Midjourney, CC-BY-NC 4.0]

```{figure} img/ai/turntable.png
:alt: Generated image of a monk operating two record players
:width: 50%
```
[Midjourney, CC-BY-NC 4.0]

- Changing and distributing software is similar to changing and distributing
  music
- You can do almost anything if you don't distribute it

**Often we don't have the choice**:
- We are expected to publish software
- Sharing can be good insurance against being locked out


### Exercise: derivative work

````{discussion} Licensing-1: What constitutes derivative work?
This question 5 below can be used as a starting point and copied to the collaborative
document or form input for an online poll:

```markdown
## Question 5: Which of these are derivative works?

**Choose many**. Vote by adding an `o` character:

- A. Download some code from a website and add on to it
  - votes:

- B. Download some code and use one of the functions in your code
  - votes:

- C. Changing code you got from somewhere
  - votes:

- D. Extending code you got from somewhere
  - votes:

- E. Completely rewriting code you got from somewhere
  - votes:

- F. Rewriting code to a different programming language
  - votes:

- G. Linking to libraries (static or dynamic), plug-ins, and drivers
  - votes:

- H. Clean room design (somebody explains you the code but you have never seen it)
  - votes:

- I. You read a paper, understand algorithm, write own code
  - votes:
```

```{solution}
- Derivative work: A-F
- Not derivative work: G-I
- E and F: This depends on how you do it, see clean room design.
```
````


### Derivative work and containers

(I haven't found a discussion/paper on this so only speculating; please suggest changes/improvements)

- Distribution of container recipes: it's like distributing source code
- Distribution of container images: it's like distributing binary form

---

## Taxonomy of software licenses

```{figure} img/license-models.png
:alt: "European Union Public Licence (EUPL): guidelines July 2021"

European Commission, Directorate-General for Informatics, Schmitz, P., European Union Public Licence (EUPL): guidelines July 2021, Publications Office, 2021, <https://data.europa.eu/doi/10.2799/77160>
```

Comments:
- Arrows represent compatibility (A -> B: B can reuse A)
- Proprietary/custom: Derivative work typically not possible (no arrow goes from proprietary to open)
- Permissive: Derivative work does not have to be shared
- Copyleft/reciprocal: Derivative work must be made available under the same license terms
- NC (non-commercial) and ND (non-derivative) exist for data licenses but not really for software licenses

**Great resource for comparing software licenses**: [Joinup Licensing Assistant](https://joinup.ec.europa.eu/collection/eupl/solution/joinup-licensing-assistant/jla-find-and-compare-software-licenses)
- Provides comments on licenses
- Easy to compare licenses ([example](https://joinup.ec.europa.eu/licence/compare/BSD-3-Clause;Apache-2.0))
- Not biased by some company agenda

If you would like to learn more about licenses, check out our slide deck ["Software licensing
and open source explained with
cakes"](https://cicero.xyz/v3/remark/0.14.0/github.com/coderefinery/social-coding/main/licensing-and-cakes.md/).


## Exercise: licensing situations

````{exercise} Licensing-2: Consider some common licensing situations
1. What is the StackOverflow license for code you copy and paste?
2. A journal requests that you release your software during publication. You have
   copied a portion of the code from another package, which you have forgotten.
   Can you satisfy the journal's request?
3. You want to fix a bug in a project someone else has released, but there is no license. What risks are there?
4. How would you ask someone to add a license?
5. You incorporate MIT, GPL, and BSD3 licensed code into your project. What possible licenses can you pick for your project?
6. You do the same as above but add in another license that looks strong copyleft. What possible licenses can you use now?
7. Do licenses apply if you don't distribute your code? Why or why not?
8. Which licenses are most/least attractive for companies with proprietary software?

```{solution}
1. As indicated [here](https://stackoverflow.com/help/licensing), all publicly accessible user contributions are licensed under [Creative Commons Attribution-ShareAlike](https://creativecommons.org/licenses/by-sa/4.0/) license. See Stackoverflow [Terms of service](https://stackoverflow.com/legal/terms-of-service/public#licensing) for more detailed information.
2. "Standard" licensing rules apply. So in this case, you would need to remove the portion of code you have copied from another package before being able to release your software.
3. By default you are no authorized to use the content of a repository when there is no license. And derivative work is also not possible by default. Other risks: it may not be clear whether you can use and distribute (publish) the bugfixed code. For the repo owners it may not be clear whether they can use and distributed the bugfixed code. However, the authors may have forgotten to add a license so we suggest you to contact the authors (e.g. make an issue) and ask whether they are willing to add a license.
4. As mentionned in 3., the easiest is to fill an issue and explain the reasons why you would like to use this software (or update it).
5. Combining software with different licenses can be tricky and it is important to understand compatibilities (or lack of compatibilities) of the various licenses. GPL license is the most protective (BSD and MIT are quite permissive) so for the resulting combined software you could use a GPL license. However, re-licensing may not be necessary.
6. Derivative work would need to be shared under this strong copyleft license (e.g. AGPL or GPL), unless the components are only plugins or libraries.
7. If you keep your code for yourself, you may think you do not need a license. However, remember that in most companies/universities, your employer is "owning" your work and when you leave you may not be allowed to "distribute your code to your future self". So the best is always to add a license!
8. The least attractive licenses for companies with proprietary software are licenses where you would need to keep an open license when creating derivative work. For instance GPL and and AGPL. The most attractive licenses are permissive licenses where they can reuse, modify and relicense with no conditions. For instance MIT, BSD and Apache License.
```
````


## Licensing and ownership

**Who can decide about or change a license?**
- The copyright holder if a separate "Contributor License Agreement" is signed. Otherwise
  copyright holder provided they secure express consent from all the contributors.

**Who owns the copyright for software you write?**
- **Intellectual property depends on the country and the employer!**
- So-called works made for hire.

**If you own your software:**
- You can change the license.
- You can dual-license (e.g. GPL for anyone, but you can pay for commercial non-GPL).

**If you do not own your software, you can:**
- Request open-sourcing directly (preserves your rights!).
- Request a transfer of ownership (check with your university).

**If you accept contributions (pull requests), you may not be the only owner anymore!**
- Clarify licensing strategy **before** - otherwise you won't have
  all rights to your code.


## Guidelines/recommendations from various universities

- [Aalto university](https://www.aalto.fi/en/open-science-and-research/opening-your-software-at-aalto-university)
    - Summary: yes, you can open software and data and you need to ask only
      minimal permission (confirm your supervisor agrees).
- [UiT](https://en.uit.no/research/innovation/art?p_document_id=754152)
    - "Work results of a copyright nature belong to the author"
- [NTNU](https://i.ntnu.no/wiki/-/wiki/English/Guidelines+for+policy+for+Open+Science)
    - "Where no overriding guidelines exist, NTNU-produced software must be
      licensed under the European Union Public Licence."
- [UiB](https://www.uib.no/en/ub/106619/copyright-own-scientific-work)
    - "As a rule authors have copyright to their own work"
    - Encourage the use of CC-BY
- [UiO](https://www.uio.no/english/for-employees/support/research/funding/units/hf/imv/data-ethics/ipr.html)
    - "If the University chooses not to take steps to secure copyright
      protection and exploit the findings, the employees must be entitled to
      have these rights reassigned to them."


## Practical recommendations

- **You cannot ignore licensing**: default is "no one can make copies or
  derivative works".
- License your code **very early** in the project:
  ideally develop publicly accessible open source code **from day one**.
- Start with a `README.md` and a `LICENSE` file.
- Use the [Joinup Licensing Assistant](https://joinup.ec.europa.eu/collection/eupl/solution/joinup-licensing-assistant/jla-find-and-compare-software-licenses)
- Follow the checklist from <https://reuse.software> (good information about so-called SPDX identifiers).
- A great resource on what to include in a `README.md`
  are the [JOSS paper review criteria](https://joss.readthedocs.io/en/latest/review_criteria.html).
- Add also the files `CONTRIBUTING.md` and `CODE_OF_CONDUCT.md` (see [Mozilla
  Introduction to Contributor
  Guidelines](https://mozilla.github.io/open-leadership-training-series/articles/building-communities-of-contributors/write-contributor-guidelines/),
  good example: <https://github.com/KirstieJane/STEMMRoleModels>).
- Emphasize the open source nature of the code output in your research proposal.
- **Do not design your own custom licenses** for open source/ open use: compatibility not clear.
  Take an [OSI](https://opensource.org/licenses)-approved license: makes it easier to evaluate
  [compatibility](https://en.wikipedia.org/wiki/License_compatibility).
- Open source your code to make sure you are not locked out of your own code if you don't own it
  once you change affiliation. For this, both permissive and copy-left licenses are good for this.
- **Work as if the repo is public even though it is still private**:
  This is to avoid surprises about code in the history with incompatible
  license years later when we decide to open the project (thanks to E.
  Glerean for this great suggestion).
- Example for a [license file in a derivative project](https://opensource.stackexchange.com/a/5488).


## Licensing of dataset and databases

- The EU has a [database directive](https://en.wikipedia.org/wiki/Database_Directive) which restricts data mining on
  databases.
- Has a somewhat similar effect to copyright, because copyright would
  not apply to data mining.
- A good license also gives rights to data mine. So not a major concern.

When you can use datasets:
- The license allows
- Your country has exceptions for research
- The data doesn't come from the EU

License text, slides, images, and supporting information under a
[Creative Commons license](https://creativecommons.org/licenses/), and get a DOI using
[Zenodo](https://zenodo.org) or [Figshare](https://figshare.com) or other services.


## Licensing and machine learning/ AI

**Is it data? Is it software?**
We need to consider the AI solution, the training data, the production data,
the AI output, and AI evolutions.


**How about ethics? How about liability?**
- [EU AI Act](https://artificialintelligenceact.eu/)
- Models can be reverse-engineered and training data can be extracted
- What if the model generates an outcome that is dangerous?
.cite[Thanks to E. Glerean for pointing these issues out to us]


**Some resources**
- [RAIL initiative: "Responsible AI licenses"](https://www.licenses.ai)
- [The Turing Way: Machine Learning Model Licenses](https://the-turing-way.netlify.app/reproducible-research/licensing/licensing-ml.html)
- ["Expert Q&A on Artificial Intelligence (AI) Licensing"](https://www.mayerbrown.com/-/media/files/news/2019/01/expert-qanda-on-artificial-intelligence-ai-licensing-w0219801.pdf)


## Further reading

- [Joinup Licensing Assistant](https://joinup.ec.europa.eu/collection/eupl/solution/joinup-licensing-assistant/jla-find-and-compare-software-licenses)
- [Choosing an open-source licence](https://www.software.ac.uk/resources/guides/choosing-open-source-licence)
- [Understanding Open Source and Free Software Licensing](http://www.oreilly.com/openbook/osfreesoft/)
- [Software Licenses in Plain English](https://tldrlegal.com)
- [Don's Bibliography of Ethical Source Reading and Resources](https://github.com/DEGoodmanWilson/Ethical-Resources)
- [Mikko Välimäki: The Rise of Open Source Licensing](http://lib.tkk.fi/Diss/2005/isbn9529187793/isbn9529187793.pdf)
- [Lawrence Rosen: Open Source Licensing](http://www.rosenlaw.com/oslbook.htm)
- [Aalto IPR Cheatsheet](https://users.aalto.fi/~darstr1/cheatsheets/ipr-cheatsheet.pdf)
- [Contributor License Agreements](https://jacobian.org/2009/sep/17/contributor-license-agreements/)
- [4OSS recommendations](https://softdev4research.github.io/recommendations/)
- [4OSS lesson](https://softdev4research.github.io/4OSS-lesson/)
- [Intellectual Property Rights (IPR), Licensing And Patents](http://oss-watch.ac.uk/resources/ipr)
- [Dispelling Open Source Confusion: An Introduction to Licenses](http://depth-first.com/articles/2006/12/29/dispelling-open-source-confusion-an-introduction-to-licenses/)
- <https://choosealicense.com> (can send automatic pull request to your GitHub repo)
- <https://hintjens.gitbooks.io/social-architecture/content/chapter2.html>
- <http://rkd.zgib.net/scicomp/open-science/open-science.html>
- Nadia Asparouhova (formerly Nadia Eghbal): "Working in Public: The Making and Maintenance of Open Source Software" (Stripe Press)
- [Open Source Guides](https://opensource.guide/)
- [The Architecture of Open Source Applications](http://aosabook.org)
- Christopher M. Kelty: ["Two Bits: The Cultural Significance of Free Software"](https://twobits.net/) (Duke University Press, 2008)
- [Open Source (Almost) Everything](http://tom.preston-werner.com/2011/11/22/open-source-everything.html)
- [99 ways to ruin an open source project](http://opensoul.org/99ways/)
- [Open Source Casebook](https://google.github.io/opencasebook/)
