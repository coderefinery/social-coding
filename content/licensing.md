# Licensing

```{questions}
- What is intellectual property/copyright/derivative work?
- What is free software?
- What types of licenses exist?
```

```{objectives}
- Get familiar with terminology around licensing
- Discuss what is and is not derivative work
```


## Intellectual property

```{figure} img/tate.jpg
:alt: Photo of somebody taking a photo of an artwork that contains the text "WHO OWNS WHAT?"
```

- **Trademark**: Protects a name/brand from impersonation.
- **Patent**: Protects a novel, non-obvious, technical invention.
- **Copyright**: Protects **creative expression**: software, writing, graphics, photos, certain datasets, this presentation.


## Copyright

- Protects creative expression
- Automatically created
- **Derivative works** usually inherit copyright of the thing derived
- Time frame: essentially forever (lifetime + X years)

When can you use:
- When there is a **license** saying you can
- Limited other cases (private use, fair use: context dependent)
- In practice: people do many things, but then can't share their
  output if license does not allow it or is not clarified

**When we write or use software then copyright, licenses, and derivative works are important concepts**


## Derivative work: Changing, remixing, covering

```{figure} img/rubik.jpg
:alt: Images of Bob Marley and Mona Lisa made out of Rubik cubes

Is this derivative work? ["Distillery District 26"](https://www.flickr.com/photos/dgriebeling/3851273590) CC-BY.
```


### If you build on something, you form a derivative work

- The original creator may have rights to what you make
- The whole point of this talk is to make sure that **you can make and publish derivative works**
  and **others can make and publish derivative works from you**


```{instructor-note}
This question 4 below can be used as a starting point and copied to the collaborative
document or form input for an online poll:
```

```markdown
## Question 4: Which of these are derivative works?

- A. Download some code from a website and add on to it
- B. Download some code and use one of the functions in your code
- C. Changing code you got from somewhere
- D. Extending code you got from somewhere
- E. Completely rewriting code you got from somewhere
- F. Rewriting code to a different programming language
- G. Linking to libraries (static or dynamic), plug-ins, and drivers
- H. Clean room design (somebody explains you the code but you have never seen it)
- I. You read a paper, understand algorithm, write own code

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
```

```{solution}
- Derivative work: A-F
- Not derivative work: G-I
- E and F: This depends on how you do it, see clean room design.
```


### Why could allowing derivative work be good for you as researcher?

- **Quality** control: groups depending on your code will find bugs.
- More applications.
- Globally probably more papers (**more impact**).
- If you make your code citeable, you can measure this impact and use this
  in grant applications.
- Long-term probably also **more papers** for you: new collaborations and projects.
- Groups depending on your code will not want your code to disappear: they might **support you**,
  send improvements, and share maintenance load.


## What is free software?

### Software freedom is the freedom to ...

- ... run the software for **any purpose**: new applications
- ... **study** how the software works and to adapt it to your needs: new applications, less reinventing wheels
- ... **redistribute** copies of the software: more users, more citations
- ... **improve** the software and distribute your improvements to the public: fix bugs, new science

### Typical confusion

- Free software does not mean that software is for free
- Open source license does not mean you need to share everything immediately (share main branch, put unpublished code on a fork)
- Open source does not mean public domain: software in the public domain has no owner
- Open source does not mean non-commercial: plenty of companies produce and support it


## Taxonomy of software licenses

**1. Custom/closed/proprietary**

- Derivative work typically not possible

**2. Permissive (MIT, BSD, Apache)**

- Derivative work does not have to be shared

```{figure} img/MIT.png
:alt: Permissions, conditions, and limitations of the MIT license

Example: Permissions, conditions, and limitations of the MIT license. Unchanged from <https://choosealicense.com/>.
```

**3. Weak copyleft share-alike (LGPL, MPL)**

- Derivative work is free software but is limited to the component

```{figure} img/GNU_LGPL_v3.png
:alt: Permissions, conditions, and limitations of the LGPL license

Example: Permissions, conditions, and limitations of the LGPL license. Unchanged from <https://choosealicense.com/>.
```

**4. Strong copyleft share-alike (GPL, AGPL)**

- Derivative work is free software and derivative work extends to the combined project

```{figure} img/GNU_GPL_v3.png
:alt: Permissions, conditions, and limitations of the GPL license

Example: Permissions, conditions, and limitations of the GPL license. Unchanged from <https://choosealicense.com/>.
```

If you would like to learn more about licenses, check out our slide deck ["Software licensing
and open source explained with
cakes"](https://cicero.xyz/v3/remark/0.14.0/github.com/coderefinery/social-coding/main/licensing-and-cakes.md/).


## Licencing and ownership

**Who can decide about or change a license?**
- The copyright holder

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


## Practical recommendations for licenses

- **You cannot ignore licensing**: default is "no one can make copies or
  derivative works".
- License your code **very early** in the project:
  ideally develop publicly accessible open source code **from day one**.
  Start with a `README.md` and a `LICENSE`. Use GitHub recommendation or/and
  [Choose an open source license](https://choosealicense.com/).
- Add also the files `CONTRIBUTING.md` and `CODE_OF_CONDUCT.md`. See [Mozilla
  Introduction to Contributor
  Guidelines](https://mozilla.github.io/open-leadership-training-series/articles/building-communities-of-contributors/write-contributor-guidelines/).
  Good example: <https://github.com/KirstieJane/STEMMRoleModels>
- Emphasize the open source nature of the code output in your research proposal.
- Take an [OSI](https://opensource.org/licenses)-approved license: makes it easier to evaluate
  [compatibility](https://en.wikipedia.org/wiki/License_compatibility).
- **Do not design your own custom licenses** for open source/ open use: compatibility not clear.
- Open source your code to make sure you are not locked out of your own code if you don't own it
  once you change affiliation.

```{note}
## How about datasets and databases?

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

Services for sharing and collaborating on research data:
<https://coderefinery.org/reproducible-research/sharing/#services-for-sharing-and-collaborating-on-research-data>
```

## Exercises: licensing

```{challenge} Licensing-2: Consider some common licensing situations
1. What is the StackOverflow license for code you copy and paste?
2. A journal requests that you release your software during publication. You have
   copied a portion of the code from another package, which you have forgotten.
   Can you satisfy the journal's request?
3. You want to fix a bug in a project someone else has released, but there is no license. What risks are there?
4. How would you ask someone to add a license?
5. You incorporate MIT, GPL, and BSD3 licensed code into your project. What possible licenses can you pick for your project?
6. You do the same as above but add in another license that looks viral. What possible licenses can you use now?
7. Do licenses apply if you don't distribute your code? Why or why not?
8. Which licenses are most/least attractive for companies with proprietary software?
```
```{solution} Solution
1. As indicated [here](https://stackoverflow.com/help/licensing), all publicly accessible user contributions are licensed under [Creative Commons Attribution-ShareAlike](https://creativecommons.org/licenses/by-sa/4.0/) license. See Stackoverflow [Terms of service](https://stackoverflow.com/legal/terms-of-service/public#licensing) for more detailed information.
2. "Standard" licensing rules apply. So in this case, you would need to remove the portion of code you have copied from another package before being able to release your software.
3. By default you are no authorized to use the content of a repository when there is no license. And derivative work is also not possible by default. Other risks: it may not be clear whether you can use and distribute (publish) the bugfixed code. For the repo owners it may not be clear whether they can use and distributed the bugfixed code. However, the authors may have forgotten to add a license so we suggest you to contact the authors (e.g. make an issue) and ask whether they are willing to add a license.
4. As mentionned in 3., the easiest is to fill an issue and explain the reasons why you would like to use this software (or update it).
5. Combining software with different licenses can be tricky and it is important to understand compatibilities (or lack of compatibilities) of the various licenses. GPL license is the most protective (BSD and MIT are quite permissive) so for the resulting combined software you could use a GPL license. However, re-licensing may not be necessary.
6. Derivative work would need to be shared under this viral license (e.g. AGPL or GPL), unless the components are only plugins or libraries.
7. If you keep your code for yourself, you may think you do not need a license. However, remember that in most companies/universities, your employer is "owning" your work and when you leave you may not be allowed to "distribute your code to your future self". So the best is always to add a license!
8. The least attractive licenses for companies with proprietary software are licenses where you would need to keep an open license when creating derivative work. For instance GPL and and AGPL. The most attractive licenses are permissive licenses where they can reuse, modify and relicense with no conditions. For instance MIT, BSD and Apache License.
```

```{keypoints}
- Always add a license

```


## Notes that were previously in the README

These will be incorporated into above text/lesson:
- https://choosealicense.com/
- https://opensource.guide/legal/#which-open-source-license-is-appropriate-for-my-project
- Permissive: gives the public permission to use, modify, and share, without any condition for downstream licensing
- If the licenses of dependencies are permissive, one may use any open license they want.
- If the licenses of dependencies are strong copyleft, one must use the same license.
