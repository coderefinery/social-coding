# Sharing data


## Services for sharing and collaborating on research data

To find a research data repository for your data, you can search on the
[Registry of Research Data Repositories (re3data)](https://www.re3data.org/)
platform and filter by country, content type, discipline, etc.

**International:**
- [Zenodo](https://zenodo.org/): A general-purpose open access repository
  created by OpenAIRE and CERN. Integration with GitHub, allows
  researchers to upload files up to 50 GB.
- [Figshare](https://figshare.com/): Online digital repository where researchers
  can preserve and share their research outputs (figures, datasets, images and videos).
  Users can make all of their research outputs available in a citable,
  shareable and discoverable manner.
- [EUDAT](https://eudat.eu): European platform for researchers and practitioners from any research discipline to preserve, find, access, and process data in a trusted environment.
- [Dryad](https://datadryad.org/): A general-purpose home for a wide diversity of datatypes,
  governed by a nonprofit membership organization.
  A curated resource that makes the data underlying scientific publications discoverable,
  freely reusable, and citable.
- [The Open Science Framework](https://osf.io/): Gives free accounts for collaboration
  around files and other research artifacts. Each account can have up to 5 GB of files
  without any problem, and it remains private until you make it public.

**Sweden:**
- [ICOS for climate data](http://www.icos-sweden.se/)
- [Bolin center climate / geodata](https://bolin.su.se/data/)
- [NBIS for life science, sequence, omics data](https://nbis.se/services/data-sharing)

**Norway:**
- [NIRD archive is widely used by some communities](https://archive.norstore.no/)
- [NSD - Norwegian Center for Research Data, for any kind of data](https://nsd.no/nsd/english/index.html)
- [Dataverse.no - Dataverse network, based at University of Tromsø but open for other institutions](https://dataverse.no/)
- [ELIXIR Norway for life science, sequence, omics data](https://elixir.no/)

**Denmark:**
- [Datavejviser](https://datavejviser.dk/) – metadata catalogue aggregating from research organisations and National Archives
- [GEUS Dataverse](https://www.dataverse.geus.dk/) – data from the Geological Survey of Denmark and Greenland
- [DTU Data](https://data.dtu.dk/) – repository of the Technical University of Denmark
- [DeiC Dataverse for University of Copenhagen](https://dataverse.deic.dk/dataverse/ucph)

**Finland:**
- [IDA, for general data](https://ida.fairdata.fi/login)
- [FSD for social data](https://www.fsd.uta.fi/en/)
- [more information on Finnish resources for open data](https://www.fairdata.fi/en/)

**Portugal:**
- [DMPortal - Dataverse network for any research data](https://dmportal.biodata.pt/)

---

## Resources for data management

- [DataLad](https://www.datalad.org/)
- [Data Stewardship Wizard](https://ds-wizard.org/)

---

## Licensing of datasets and databases

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
[Zenodo](https://zenodo.org) or [Figshare](https://figshare.com) or [OSF](https://osf.io/) other services.

---


## Licensing and machine learning/ AI

This section is maybe more relevant to **developers of AI models / AI systems** rather than **users of AI models / AI systems**.

**Is it data? Is it software?**
It depends. We need to consider the AI system as a whole, the training data, the production data, the AI output, and how it is put on service. **AI models** are like the engine of the car: they cannot do anything without the rest of the car infrastructure. **AI systems** are the whole car with the AI model and all the software and hardware to actually use it. 

Depending on what you are going to share, there might be things to consider beyond the license.

For example **large language models** are often shared with open source software licenses, on **HuggingFace** which is like a GitHub/GitLab for AI models (see for example the [OLMO model](https://huggingface.co/allenai/OLMo-7B)). Many so-called *open-source* models are actually just *open-weights* models: only the trained neural network weights are shared, while the training data, training code, and full documentation are often kept private. This lack of transparency raises concerns about reproducibility and accountability and this phenomenon is sometimes called **"open washing"** ([ref](https://dl.acm.org/doi/abs/10.1145/3630106.3659005)). Models are also shared with a **model card** which is a documentation tool for transparency that provide a comprehensive snapshot of a model’s characteristics and ethical considerations (see [Ch.8 Glerean 2025](https://www.edpb.europa.eu/our-work-tools/our-documents/support-pool-experts-projects/fundamentals-secure-ai-systems-personal_en)).

**What about ethics? What about liability?**

As AI models (e.g. the deep network weights) and AI systems (the model with all the software and infrastructure to query it) are becoming more available, there can be legal (and ethical!) requirements on the developer of the AI model/system by the [EU AI Act](https://artificialintelligenceact.eu/). In general researchers do not need to worry, but ethically one should consider that if the research-purpose AI model/system could be used for something harmful, ethically (if not legally) one should consider if such model/system should be implemented at all.

**What about the training data inside the model?**
Large models can memorize and unintentionally reveal parts of their training data. This raises concerns about copyright, trade secrets, and personal data. News publishers and artists are suing AI companies for unauthorized use of their content in training. It is still unclear how traditional data licenses can apply to data that has been transformed into model weights.


**More resources**
- [RAIL initiative: "Responsible AI licenses"](https://www.licenses.ai)
- [The Turing Way: Machine Learning Model Licenses](https://the-turing-way.netlify.app/reproducible-research/licensing/licensing-ml.html)
- ["Expert Q&A on Artificial Intelligence (AI) Licensing"](https://www.mayerbrown.com/-/media/files/news/2019/01/expert-qanda-on-artificial-intelligence-ai-licensing-w0219801.pdf)


---

## Further reading

- [The Turing way](https://github.com/alan-turing-institute/the-turing-way/)
- [Illustrations from the Turing Way book dashes](https://zenodo.org/record/3332808)
- [Reproduciblity syllabus](http://lorenabarba.com/blog/barbagroup-reproducibility-syllabus/)
- The [reproducible research data analysis platform](http://www.reana.io/)
- Good talks on open reproducible research can be found [here](http://inundata.org/talks/index.html).
- ["FAIR is not fair enough"](https://danielskatzblog.wordpress.com/2017/06/22/fair-is-not-fair-enough/)
- ["A FAIRer future"](https://www.nature.com/articles/s41567-019-0624-3)
- ["Top 10 FAIR Data & Software Things"](https://librarycarpentry.org/Top-10-FAIR/) are brief guides that can be used by the research community to understand how they can make their research (data and software) more FAIR.
- [Five recommendations for fair software](https://fair-software.eu/)
- [Publishing research software](https://libguides.mit.edu/software) A MIT libraries webpage on why to publish software, where to publish software, and how to make software citable.
- [Software Quality Checklist](https://technical-reference.readthedocs.io/en/latest/quality/software-checklist.html)
- [MolSSI Best Practice Guides](http://molssi.org/education/best-practices/)
- [Five recommendations for fair software](https://fair-software.eu/)
- [Awesome Research Software Registries](https://github.com/NLeSC/awesome-research-software-registries)
