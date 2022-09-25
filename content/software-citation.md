# Software citation

```{questions}
- How can software be cited?
- How can I make my software citeable?
```

```{discussion} Citation-1: Explain how you currently cite software
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
- <https://www.force11.org/software-citation-principles>

## Where to place your code

- <https://github.com>: public or private repositories
- <https://gitlab.com>: public or private repositories
- <https://source.coderefinery.org>: public or private repositories

**Making code public is not enough! Why? Get a DOI in addition.**


## FAIR principles

<img src="../img/turing-way/8-fair-principles.jpg" style="width: 70%;"/>

(c) [Scriberia](http://www.scriberia.co.uk) for [The Turing Way](https://the-turing-way.netlify.com), CC-BY.

For a discussion of FAIR in the context of software, see <https://softdev4research.github.io/4OSS-lesson/>.
