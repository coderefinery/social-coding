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
- No. Because nothing prevents me from deleting my GitHub repository and we have no guarantee that
  GitHub will still be around in 10 years.
- **Get a persistent identifier (PID) such as DOI in addition.**


## Papers with focus on scientific software

Where can I publish papers which are primarily focused on my scientific software?

Great list/summary: ["In which journals should I publish my software?" (Neil P. Chue Hong)](https://www.software.ac.uk/resources/guides/which-journals-should-i-publish-my-software)


## How to make your software citable

```{discussion} Discussion (Citation-1): Explain how you currently cite software
- Do you cite software that you use? How?
- If I wanted to cite your code/scripts, what would I need to do?
```

**Checklist for making a release of your software citable**:
- Assigned an appropriate license
- Described the software using an appropriate metadata format
- Clear version number
- Authors credited
- Procured a persistent identifier
- Added a recommended citation to the software documentation

This checklist is adapted from: N. P. Chue Hong, A. Allen, A. Gonzalez-Beltran,
et al., Software Citation Checklist for Developers (Version 0.9.0). Zenodo.
2019b. ([DOI](https://doi.org/10.5281/zenodo.3482769))

**Our practical recommendations**:
- Get a [DOI](https://en.wikipedia.org/wiki/Digital_object_identifier) using [Zenodo](https://zenodo.org) or similar services.
- Open source license can't demand citation, but it is required by science ethics anyway.
- Make it as easy as possible! Clearly say what you want cited.
- Make it easy for scripts and tools, use the [Citation File Format](https://citation-file-format.github.io).
- [GitHub now supports CITATION.cff files](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-citation-files)

This is an example of a simple `CITATION.cff` file:
```yaml
cff-version: 1.2.0
message: "If you use this software, please cite it as below."
authors:
  - family-names: Druskat
    given-names: Stephan
    orcid: https://orcid.org/0000-0003-4925-7248
title: "My Research Software"
version: 2.0.4
doi: 10.5281/zenodo.1234
date-released: 2021-08-11
```


## How to cite software

Great resources:
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

Recommended format for software citation is to ensure the following information
is provided as part of the reference [Katz, Chue Hong, Clark, 2021](https://doi.org/10.12688/f1000research.26932.2):
- Creator
- Title
- Publication venue
- Date
- Identifier
- Version
- Type

For software citation examples please see [Katz, Chue Hong, Clark, 2021](https://doi.org/10.12688/f1000research.26932.2).
