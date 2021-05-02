# Software citation

```{questions}
* How can software be cited?
* How can I make my software citeable?
```

```{objectives}
Learn about software citation.
```

## Software citation


```{discussion}
- Do you cite software that you use? How?
- If I wanted to cite your code/scripts, what would I need to do?
```

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
- https://www.force11.org/software-citation-principles

## Where to place your code

- https://github.com: public (unlimited) or private (up to 3 collaborators or unlimited educational) repositories
- https://gitlab.com: public or private repositories
- https://source.coderefinery.org: public or private repositories

**Making code public is not enough! Why? Get a DOI in addition.**


## FAIR principles

<img src="../img/turing-way/8-fair-principles.jpg" style="width: 70%;"/>

(c) [Scriberia](http://www.scriberia.co.uk) for [The Turing Way](https://the-turing-way.netlify.com), CC-BY.

For a discussion of FAIR in the context of software, see https://softdev4research.github.io/4OSS-lesson/.


```{discussion}
- Who owns the code that you write?
- Does your code/script have a license?
- Can you take your own code with you after the PhD?
- Are you using open source software in your work?
- What are your thoughts about sharing software with your colleagues or competitors?
```

```{keypoints}
- License your code **very early** in the project:
  ideally develop publicly accessible open source code **from day one**.
- Make it easy to cite your code ([Zenodo](https://zenodo.org))
- Do not forget to cite code you use.
```


```{callout} Further reading
- http://depth-first.com/articles/2006/12/29/dispelling-open-source-confusion-an-introduction-to-licenses/
- http://oss-watch.ac.uk/resources/ipr
- http://rkd.zgib.net/scicomp/open-science/open-science.html
- https://choosealicense.com (can send automatic pull request to your GitHub repo)
- https://hintjens.gitbooks.io/social-architecture/content/chapter2.html
- https://softdev4research.github.io/4OSS-lesson/
- https://softdev4research.github.io/recommendations/
- https://tldrlegal.com/
- https://users.aalto.fi/~darstr1/cheatsheets/ipr-cheatsheet.pdf
- https://www.software.ac.uk/choosing-open-source-licence
- http://www.oreilly.com/openbook/osfreesoft/
- http://www.rosenlaw.com/oslbook.htm
- http://lib.tkk.fi/Diss/2005/isbn9529187793/isbn9529187793.pdf
- https://www.software.ac.uk/resources/guides/adopting-open-source-licence
- https://jacobian.org/2009/sep/17/contributor-license-agreements/
- https://github.com/DEGoodmanWilson/Ethical-Resources
- https://opensource.google/docs/patching/#forbidden
- https://opensource.google/docs/
- https://opensource.guide/
```