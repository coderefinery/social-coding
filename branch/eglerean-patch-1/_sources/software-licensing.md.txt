# Software licensing

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


### Exercise: Derivative work

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
- [Joinup Licensing Assistant - Compatibility Checker](https://joinup.ec.europa.eu/collection/eupl/solution/joinup-licensing-assistant/jla-compatibility-checker)
- Not biased by some company agenda

If you would like to learn more about licenses, check out our slide deck: ["Software licensing
and open source explained with
cakes"](https://cicero.xyz/v3/remark/0.14.0/github.com/coderefinery/social-coding/main/licensing-and-cakes.md/).


## Exercise: Licensing situations

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


## When should I add a license?

**Choose a license early in the project, even before you publish it**. Later in
the project it may become complicated to change it.  Agreeing on a software
license does not mean that you have to make it open immediately.  You can also
follow the **"open core" approach**: You don't have to open source all your
work. Core can be open and on a public branch. Unpublished code can be on a
private repository.

However, we recommend to **work as if the code is public even though it still
may be private** (thanks to E.  Glerean for this great suggestion): This is to
avoid surprises about code in the history with incompatible license years later
when you decide to open the project.


## How to add a license if your work is derivative work

Your code is derivative work if you have started from an existing code and
made changes to it or if you incorporated an existing code into your code.

If your code is derivative work, then **you need to check the license of the
original code**. Depending on the license, your choices might be limited. In
this case we recommend to use these two resources:
- [Joinup Licensing Assistant - Find and compare software licenses](https://joinup.ec.europa.eu/collection/eupl/solution/joinup-licensing-assistant/jla-find-and-compare-software-licenses)
- [Joinup Licensing Assistant - Compatibility Checker](https://joinup.ec.europa.eu/collection/eupl/solution/joinup-licensing-assistant/jla-compatibility-checker)

If the original code does not have a license, you may not be able to distribute your
derivative code. You can try to contact the authors and ask them to clarify
the license of their code.

Practical steps for **incorporating something small into your own project** with a license
that allows you to do so (as
an example incorporating a function or two from another project):
- Create a `LICENSES/` folder in your project and "put the unmodified license text
  (i.e., the license text template without any copyright notices) in your
  `LICENSES/` folder" (<https://reuse.software/faq/#license-templates>). This
  way if you reuse code from multiple projects, you can keep there multiple
  license files.
- **Put the code that you incorporate into a separate file or separate files**. This makes
  it later easier to see what was incorporated, and what was written from scratch.
  On top of the file(s) which you have incorporated into your project add (and
  adapt) the following header ([more examples](https://reuse.software/faq/)):
  ```python
  # SPDX-FileCopyrightText: 2023 Jane Doe <jane@example.com>
  #
  # SPDX-License-Identifier: MIT
  ```
  The [REUSE](https://reuse.software/) initiative was started by the [Free
  Software Foundation Europe](https://fsfe.org/) to make licensing of software
  projects easier.  It is OK if you prefer to not follow this strict format but
  the advantage of following it is that the
  [reuse-tool](https://github.com/fsfe/reuse-tool) makes it then easy to verify
  and update license headers if you have many files from different sources.
- If it does not make sense to have several files in your project (e.g. when incorporating
  something into a notebook), then add a note/comment
  about the license and where the code came from on top of the function.
- Although it is not dictated by the license but it can still be nice to
  acknowledge the incorporated functions/code in your README/documentation and to cite
  their work if you publish a paper about your code.
- Some licenses are more permissive (you can keep your changes private) but some licenses
  require you to publish the changes (share-alike).

Practical steps for making **changes to an existing project** with a license
that allows you to do so:
- If the project is on GitHub or GitLab or similar, first fork the project
  (copy it into your user space where you can make changes).
- For the BSD and MIT licenses you are not obliged to state your changes but it can
  still be helpful for others if you do. You can state your changes in the
  header of the files you have modified. It can be helpful to state
  bigger-picture changes in the README file of the project.
- Some licenses are more permissive (you can keep your changes private) but some licenses
  require you to publish the changes (share-alike).


### If your work is not derivative work

If you have started "from scratch", and not used any existing code, or
incorporated existing code into your code, then you may consider your code to
be not derivative work.

Before you may choose a license, clarify the following points with, for
example, your supervisor, collaborators, or principal investigator:
- Does your work contract, grant, or collaboration agreement dictate a
  specific license?
- Is there an intent to commercialize the code?
- When there is unknown or mixed ownership: If there are multiple persons or
  organizations as owners of the code, all must agree to the license.

**Do not invent your own license**. Choose one of the standard licenses, otherwise
compatibility is not clear:
  - [Joinup Licensing Assistant - Find and compare software licenses](https://joinup.ec.europa.eu/collection/eupl/solution/joinup-licensing-assistant/jla-find-and-compare-software-licenses)
  - [Joinup Licensing Assistant - Compatibility Checker](https://joinup.ec.europa.eu/collection/eupl/solution/joinup-licensing-assistant/jla-compatibility-checker)

Practical steps:
- Create a `LICENSES/` folder ([example](https://github.com/bast/runtest/tree/main/LICENSES)).
- Put the unmodified license text
  (i.e., the license text template without any copyright notices) in plain
  text format into the folder  ([example](https://github.com/bast/runtest/tree/main/LICENSES)).  Here are
  the two above licenses in plain text:
  [EUPL](https://joinup.ec.europa.eu/sites/default/files/custom-page/attachment/2020-03/EUPL-1.2%20EN.txt)
  and [MIT](https://en.wikipedia.org/wiki/MIT_License#License_terms) (but the
  latter contains a copyright notice which we rather want to have on top of
  files).
- Add copyright and license information to each file following
  <https://reuse.software/tutorial/> which uses a standard format with
  so-called [SPDX identifiers](https://spdx.org/licenses/). Example below
  ([example](https://github.com/bast/runtest/blob/3b210d2e9bdbdc1903a1dab9da32e161d390092d/runtest/tuple_comparison.py#L1-L3)):
  ```python
  # SPDX-FileCopyrightText: 2023 Jane Doe <jane@example.com>
  #
  # SPDX-License-Identifier: EUPL-1.2
  ```
  The [REUSE](https://reuse.software/) initiative was started by the [Free
  Software Foundation Europe](https://fsfe.org/) to make licensing of software
  projects easier.  It is OK if you prefer to not follow this strict format but
  the advantage of following it is that the
  [reuse-tool](https://github.com/fsfe/reuse-tool) makes it then easy to verify
  and update license headers if you have many files from different sources.
- For really small projects with one or two files the above may seem excessive
  and some projects choose to not have copyright information on top of their
  files and they only have one `LICENSE` file and that is
  OK for really small projects.

---


## Great resources

- [Research institution policies to support research software (compiled by the Research Software Alliance)](https://www.researchsoft.org/software-policies/)
- Guide from the Aalto University in Finland: ["Opening your Software at Aalto University"](https://www.aalto.fi/en/open-science-and-research/opening-your-software-at-aalto-university)
- [Draft: Research software licensing guide](https://research-software.uit.no/blog/2023-software-licensing-guide/)
- [Joinup Licensing Assistant - Find and compare software licenses](https://joinup.ec.europa.eu/collection/eupl/solution/joinup-licensing-assistant/jla-find-and-compare-software-licenses)
- [Joinup Licensing Assistant - Compatibility Checker](https://joinup.ec.europa.eu/collection/eupl/solution/joinup-licensing-assistant/jla-compatibility-checker)
- [Social coding lesson material](https://coderefinery.github.io/social-coding/) by [CodeRefinery](https://coderefinery.org/)
- [Citation File Format (CFF)](https://citation-file-format.github.io/)
- [License Selector](https://ufal.github.io/public-license-selector/)
- [GitHub licensing guide](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository)
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

```{keypoints}
- **You cannot ignore licensing**: default is "no one can make copies or
  derivative works".
```
