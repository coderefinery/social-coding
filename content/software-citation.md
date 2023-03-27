# Software citation

```{questions}
- Is putting software on GitHub/GitLab/... publishing?
- Where to publish software?
- How can software be cited?
- How can I make my software citeable?
```


## Is putting software on GitHub/GitLab/... publishing?

```{figure} img/turing-way/8-fair-principles.jpg
:alt: FAIR principles
:width: 70%

FAIR principles. (c) [Scriberia](http://www.scriberia.co.uk) for [The Turing Way](https://the-turing-way.netlify.com), CC-BY.
```

Is it enough to make the code public for the code to remain **findable and accessible**?
- No. Because nothing prevents me from deleting my GitHub repository or
  rewriting the Git history and we have no guarantee that GitHub will still be around in 10 years.
- **Get a persistent identifier (PID) such as DOI in addition** using
  [Zenodo](https://zenodo.org) or [Dataverse](https://dataverse.no/) or similar services
  (see our lesson about [reproducible research](https://coderefinery.github.io/reproducible-research/) on how to do that).


## Papers with focus on scientific software

Where can I publish papers which are primarily focused on my scientific
software?  Great list/summary is provided in this blog post: ["In which
journals should I publish my software?" (Neil P. Chue
Hong)](https://www.software.ac.uk/resources/guides/which-journals-should-i-publish-my-software)


## How to make your software citable

```{discussion} Discussion (Citation-1): Explain how you currently cite software
- Do you cite software that you use? How?
- If I wanted to cite your code/scripts, what would I need to do?
```

**Checklist for making a release of your software citable**:

- {octicon}`check` Assigned an appropriate license
- {octicon}`check` Described the software using an appropriate metadata format
- {octicon}`check` Clear version number
- {octicon}`check` Authors credited
- {octicon}`check` Procured a persistent identifier
- {octicon}`check` Added a recommended citation to the software documentation

This checklist is adapted from: N. P. Chue Hong, A. Allen, A. Gonzalez-Beltran,
et al., Software Citation Checklist for Developers (Version 0.9.0). Zenodo.
2019b. ([DOI](https://doi.org/10.5281/zenodo.3482769))

**Our practical recommendations**:
- Get a [DOI](https://en.wikipedia.org/wiki/Digital_object_identifier) using
  [Zenodo](https://zenodo.org) or [Dataverse](https://dataverse.no/) or similar services.
- Open source license can't demand citation, but it is required by science ethics anyway.
- Make it as easy as possible: clearly say what you want cited.
- Make it easy for scripts and tools: use the [Citation File Format](https://citation-file-format.github.io).
- [GitHub now supports CITATION.cff files](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-citation-files)
- [Web form to create, edit, and validate CITATION.cff files](https://citation-file-format.github.io/cff-initializer-javascript/)
- [Video: "How to create a CITATION.cff using cffinit"](https://www.youtube.com/watch?v=zcgLIT5Qd4M)

This is an example of a simple `CITATION.cff` file:
```yaml
cff-version: 1.2.0
message: "If you use this software, please cite it as below."
authors:
  - family-names: Druskat
    given-names: Stephan
    orcid: https://orcid.org/1234-5678-9101-1121
title: "My Research Software"
version: 2.0.4
doi: 10.5281/zenodo.1234
date-released: 2021-08-11
```


## How to cite software

```{admonition} Great resources
- A. M. Smith, D. S. Katz, K. E. Niemeyer, and FORCE11 Software Citation
  Working Group, "Software citation principles," PeerJ Comput. Sci., vol. 2,
  no. e86, 2016 ([DOI](https://doi.org/10.7717/peerj-cs.86))
- D. S. Katz, N. P. Chue Hong, T. Clark, et al., Recognizing the value of
  software: a software citation guide [version 2; peer review: 2 approved].
  F1000Research 2021, 9:1257 ([DOI](https://doi.org/10.12688/f1000research.26932.2))
- N. P. Chue Hong, A. Allen, A. Gonzalez-Beltran, et al., Software Citation
  Checklist for Authors (Version 0.9.0). Zenodo. 2019a. ([DOI](https://doi.org/10.5281/zenodo.3479199))
- N. P. Chue Hong, A. Allen, A. Gonzalez-Beltran, et al., Software Citation
  Checklist for Developers (Version 0.9.0). Zenodo. 2019b. ([DOI](https://doi.org/10.5281/zenodo.3482769))
```

Recommended format for software citation is to ensure the following information
is provided as part of the reference (from [Katz, Chue Hong, Clark,
2021](https://doi.org/10.12688/f1000research.26932.2) which also contains
software citation examples):
- Creator
- Title
- Publication venue
- Date
- Identifier
- Version
- Type
