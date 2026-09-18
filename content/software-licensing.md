# Software licensing focusing on open source

```{objectives}
- Principles of open source licensing
- Difference between permissive and copyleft licenses
- Regulations for AI-generated and AI-assisted code
- Determine the software license for your project following EU regulation
- Navigate the Joinup Licensing Assistant to select a compliant license
- Understand the licensing distinction between container recipes and container images
```

```{discussion} Limitations and context of this lesson 

This lesson is designed as practical educational material for researchers and research software engineers, **not formal legal advice**

* Regional Focus: Guidance is grounded in EU statutory directives, European institutional frameworks and developers based in Europe with a global focus.
* Institutional Context: Employment contracts, grant agreements, and university policies heavily influence software ownership and licensing choices.
* This lesson covers only the general principles of open-source reuse, copyright scope, and software adaptation. 

If you need formal guidance references below and legal experts, especially if you have legal services at your host institute,  could be of help:

* [EUR Directive 2009/24/EC](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32009L0024)
* [Compendium of U.S. Copyright Office Practices (3rd Ed.) – Chapter 700, Section 721: Computer Programs](https://www.copyright.gov/comp3/)
* [Chinese Regulations on Computer Software Protection,(search:"计算机软件保护条例")](https://xzfg.moj.gov.cn/)
* [Joinup Licensing Assistant,JLA](https://interoperable-europe.ec.europa.eu/collection/eupl/solution/licensing-assistant/find-and-compare-software-licenses)
* [FSFE REUSE Initiative](https://reuse.software/)
* [Research Software Alliance Policy Directory](https://www.researchsoft.org/software-policies/)
```

## Introduction: What is a Software License?

Under copyright law worldwide, software without an explicit license automatically
defaults to *All Rights Reserved*: meaning nobody else has the legal right to run,
modify, embed, or cite your code. A software license is a legal permission grant
created by the author that overrides this statutory default, defining how 
downstream researchers can reuse your work.

In this lesson, we focus on open-source licenses to define both how we grant 
permissions for software we develop (outbound licensing) and how we safely 
comply with terms attached to code written by others (inbound reuse).

* Open-source licenses fall into two main families:

    * **Permissive (e.g., MIT, Apache-2.0, 0BSD):** *Do whatever you want, just keep crediti*. 
      Grants maximum reuse freedom, allowing anyone to modify, embed, or re-license your code 
      in open or closed projects.

    * **Copyleft/Reciprocal (e.g., GPL-3.0, EUPL-1.2):** *Share alike.* Grants full freedom 
      to run and modify, but mandates that any distributed derivative or combined work must 
      also be released under matching copyleft terms. Often informally referred to as *viral* 
      or *infectious* because its open-source requirements propagate across code boundaries 
      (such as embedding snippets or static linking) into downstream projects. The diagram 
      below unifies these license choices and their downstream rights:

```{mermaid}
%%{init: {'themeVariables': { 'edgeLabelBackground': '#faf5ff' }}}%%

flowchart TB
    A["<b>Your Research Codebase</b></><i>(Source code, container recipes, prompt templates)</i>"] -->|"No License Attached</>(Statutory Default)"| B["<b>All Rights Reserved</b></>❌ Zero permissions: Cannot run, modify, or share"]

    A -->|"Attach Open-Source License</>(Explicit Permission Grant)"| C{"Select License Flavor"}

    C -->|"Permissive</>(MIT, Apache-2.0, 0BSD)"| D["<b>Permissive License</b>"]
    C -->|"Copyleft / Reciprocal</>(GPL-3.0, EUPL-1.2)"| E["<b>Copyleft License</b>"]
    C -->|"Proprietary / Closed Source"| F["<b>Closed Source / Restricted</b></>🚫 <i>Flavour not discussed in this lesson</i>"]

    D --> D1["Run & Modify? <b>Yes!</b>"]
    D --> D2["Embed in closed product? <b>Yes!</b>"]
    D --> D3["Must changes stay open? <b>No</b> (Optional)"]

    E --> E1["Run & Modify? <b>Yes!</b>"]
    E --> E2["Embed in closed product? <b>No!</b>"]
    E --> E3["Must changes stay open? <b>Yes!</b> (Mandatory)"]
    classDef green fill:#e6ffe6,stroke:#2b8a3e,stroke-width:2px,color:#1b4332;
   classDef red fill:#ffe3e3,stroke:#e03131,stroke-width:2px,color:#5c0000;
   classDef yellow fill:#fff9db,stroke:#f59f00,stroke-width:2px,color:#5c3c00;
   classDef white fill:#f8f9fa,stroke:#adb
   classDef dashed fill:#f8f9fa,stroke:#adb5bd,stroke-width:2px,stroke-dasharray: 5 5,color:#000000;
   classDef dashed_red fill:#ffe3e3,stroke:#adb5bd,stroke-width:2px,stroke-dasharray: 5 5,color:#000000;
    classDef defaultState fill:#ffe3e3,stroke:#e03131,stroke-width:2px,color:#5c0000;
    
   class D1,D2,D3,E1,E3 green;
   class E2 red;
   class D,E yellow;
   class F dashed;
   class B dashed_red;
   class A,C white;
```

### Copyright Foundation: Expression vs. Ideas

To understand why licenses are required, you must understand how copyright law treats software.
Under EU statutory law (Directive 2009/24/EC) and international treaties, software is protected 
under copyright as a **literary work**. 

However, copyright law draws a sharp, fundamental distinction between what is protected and what 
is free for anyone to use:

* **Protected (Code Expression)**: The specific source code text, variable names, binaries, 
  container build recipes, prompt engineering text, and preparatory design documents.
* **Not Protected (Underlying Ideas)**: Mathematical algorithms, scientific models, 
  programming logic, data structures, and interface principles.

Because copyright restricts only the *creative human expression* and not the underlying 
*ideas or algorithms*, developers use open-source licenses to define the exact terms under 
which that expression can be legally shared and modified.

### Scope of this Lesson: What Counts as *Software*?

Across international legal frameworks (such as 17 U.S.C. § 101 and WIPO model provisions), 
software is broadly defined as a set of instructions to be used directly or indirectly in 
a computer to bring about a certain result. 

Because modern research software extends beyond simple Python scripts, this lesson applies 
copyright and licensing principles across six core research software assets:

* **Source Code**: Original algorithms written from scratch or implemented from scientific papers.
* **Third-Party Integrations**: Embedded permissive or copyleft code snippets and dynamically/statically linked libraries.
* **Infrastructure as Code**: Ansible playbooks,Terraform configurations,container Recipes  (`Dockerfile`, Apptainer `.def`).
* **Container Images**: Bundled binary filesystem snapshots (`.sif` files, OCI registry images).
* **AI-Assisted Code**: Code generated, refactored, or assembled with human creative oversight.
* **AI Prompt Templates**: Complex, engineered system prompts and structured frameworks meeting the threshold of human creative authorship.


## Motivation: Debugging a License Compliance Failure

With the understanding of the difference between Permissive (MIT) and Copyleft (GPL-3.0) licenses, 
examine what happens when they collide inside an automated CI/CD pipeline:

```{mermaid}
%%{init: {'themeVariables': { 'edgeLabelBackground': '#faf5ff' }}}%%
flowchart TB

    subgraph box["CI/CD License Compliance Debugging Pipeline"]
        A[<b>Update</b></>Paste snippet copyied from somewhere ] --> A2["<b>Build Trigger:</b>Push to my-code-base"]
        A2["<b>Build Trigger:</b> Push to my-code-base"] --> B["Run Compliance Scanner"]
        B --> C{"Check Inbound vs.</>Outbound Terms"}
        
        C -->|"Your Target License: MIT (Permissive)</>Pasted Snippet: GPL-3.0 (Copyleft)"| D["❌ <b>BUILD FAILURE</b></>Pasted copyleft snippet restricts MIT release"]
        
        D --> E{"Select Patch Option"}
        
        E -->|"Option A: Keep MIT & add comment '# Originally GPL'"| F["❌ <b>BUILD FAIL</b></>Comments do not override copyleft terms"]
        E -->|"Option B: Re-license repo to GPL-3.0 / EUPL-1.2"| G["✅ <b>BUILD PASS</b></>Your license matches the pasted copyleft snippet"]
        E -->|"Option C: Rewrite code from scratch to replace snippet"| H["✅ <b>BUILD PASS</b></>New code expression frees your target license"]
        E -->|"Option D: Delete LICENSE file to bypass scanner"| I["⚠️ <b>PASSED SCANNER (TRAP!)</b></>No license = Default 'All Rights Reserved'</>Nobody can legally run, modify, or reuse your tool"]

        P["<b>Permissive</b></>(MIT, Apache-2.0, 0BSD)</><i>'Do whatever you want, just keep credit'</i>"]
        CL["<b>Copyleft / Reciprocal</b></>(GPL-3.0, EUPL-1.2)</><i>'Must share changes under same terms'</i>"]
    end

    P -.->|"I want to use"| C
    CL -.->|"Pasted code snippet uses"| C

    classDef pass fill:#e6ffe6,stroke:#2b8a3e,stroke-width:2px,color:#1b4332;
    classDef copyleft fill:#fff9db,stroke:#f59f00,stroke-width:2px,color:#5c3c00;
    classDef fail fill:#ffe3e3,stroke:#e03131,stroke-width:2px,color:#5c0000;
    classDef warning fill:#fff3bf,stroke:#f08c00,stroke-width:2px,color:#5c0000;
    classDef neutral fill:#f8f9fa,stroke:#495057,stroke-width:2px,color:#212529;
    classDef box_fill fill:#ffffff,stroke:#adb5bd,stroke-width:1px;

    class P,G,H pass;
    class CL copyleft;
    class D,F fail;
    class I warning;
    class A,B,C,E neutral;
    class box box_fill;
```

## Limitations of AI-Assisted Licensing Advice

Modern software developers and RSEs routinely rely on AI coding assistants 
(ChatGPT, Claude, GitHub Copilot) to generate boilerplate, refactor functions, 
and answer project setup questions. However, using these tools for legal or 
licensing guidance introduces a subtle risk: **AI legal bias**.

Because AI models are overwhelmingly trained on US-centric web data and legal 
forum posts, their outputs default almost universally to **US common law concepts**
such as *Fair Use*, *Work Made for Hire*, and *Derivative Works*.

In contrast, developers operating under EU statutory frameworks 
(such as Directive 2009/24/EC) face a different legal reality regarding statutory 
exceptions, author ownership, and code adaptations. Relying blindly on AI legal 
advice creates significant compliance blind spots, which is why this lesson equips 
you with a direct, EU-aligned framework for software licensing.



### Standardizing In-File Declarations: SPDX Identifiers

Selecting a license is only half the battle; automated scanners and CI/CD pipelines need a machine-readable way to verify license compliance per file without parsing long legal texts.

Managed by the Linux Foundation, **SPDX identifiers** (Software Package Data Exchange) provide standardized short tags (e.g., `MIT`, `Apache-2.0`, `GPL-3.0-only`, `EUPL-1.2`) placed at the very top line of every source file:

```python
# SPDX-License-Identifier: MIT
# Copyright (c) 2026 Author Name <author@institute.eu>
```

```dockerfile
# SPDX-License-Identifier: Apache-2.0
FROM ubuntu:24.04
```

Throughout the exercise scenarios below, look for the **In-File Identification (SPDX)** callouts to see how these tags apply directly to Python scripts, container recipes, and engineered prompt templates.

### JLA Decision Matrix at a Glance

When using the European Commission's Joinup Licensing Assistant (JLA),
license selection depends on your RSE workflow. The JLA groups 
criteria into four categories: 
🟢 Can (Permissions), ⚪ Must (Obligations), 🔵 Compatible (Domain), 
and 🟡 Support (OSI Approval).

| Scenario Module | Key JLA Toggle (⚪ Must) | Resulting Category | Target Licenses |
| :--- | :--- | :--- | :--- |
| [**1. Own Code**](#scenario-1) | `Incl. Copyright` | 🟢 Permissive | `MIT`, `Apache-2.0`, `BSD-3-Clause` |
| [**2. Math Implementation**](#scenario-2) | `Copyleft/Share a.` + `Disclose Source` | 🟡 Copyleft | `EUPL-1.2`, `GPL-3.0`, `AGPL-3.0` |
| [**3. Embed Permissive**](#scenario-3) | `Incl. Copyright` | 🟢 Flexible (Any) | `MIT` or `EUPL-1.2` / `GPL-3.0` |
| [**4. Embed Copyleft**](#scenario-4) | `Copyleft/Share a.` *(Mandatory)* | 🟡 Copyleft | `EUPL-1.2`, `GPL-3.0` |
| [**5. Link GPL Library**](#scenario-5) | `Copyleft/Share a.` *(Mandatory)* | 🟡 Copyleft | `GPL-3.0`, `EUPL-1.2` |
| [**6. Container Recipe**](#scenario-6) | `Incl. Copyright` | 🟢 Permissive | `MIT`, `Apache-2.0` |
| [**7. Built Image**](#scenario-7) | Overlapping Component Terms | ⚠️ Multi-License | Governed by individual image layers |
| [**8. AI-Assisted Code**](#scenario-8) | `Incl. Copyright` | 🟢 Author Choice | `MIT`, `Apache-2.0` (or Copyleft) |
| [**9. Prompt Template**](#scenario-9) | `Incl. Copyright` | 🟢 Permissive | `MIT`, `Apache-2.0` |

### Module 1: Clean Slate – Authoring Original Code & Algorithms

When writing original code or implementing published mathematical logic, you control 100% of your copyright.

(scenario-1)=
::::{exercise} Scenario 1: Own algorithm with external dependencies
You wrote an original algorithm from scratch (in Python, C++, Rust, etc.). Your repository contains only your original source code and dependency specifications (`requirements.txt`, `CMakeLists.txt`, `Cargo.toml`).

* **Licensing Goal**: You want **maximum adoption** and zero friction for commercial or academic reuse.
*  **JLA Filter Focus**: Select 🟢 `Commercial use`, `Modify`, `Distribute` + ⚪ `Incl. Copyright` + 🟡 `OSI approved`.

:::{solution}
**Legal Reality**: External dependencies remain separate works. Because you have not bundled third-party code inside your repository, you hold full copyright over your original codebase.

* **Outcome**: **Fully Permissible.** You own the code and can choose any open-source license.
* **Selected Category**: **Permissive** (driven by your goal of maximum adoption).
* **JLA Matches**: `MIT`, `Apache-2.0`, `BSD-3-Clause`
* **User Obligation**: Downstream users must comply with individual external package licenses when fetching or running dependencies.
* **In-File Identification (SPDX)**: Apply standard machine-readable SPDX identifier comments directly at the top of your scripts:

```python
# SPDX-License-Identifier: MIT
# Copyright (c) 2026 Author Name <author@institute.eu>

import numpy as np
```
* Public Domain vs. Permissive Licenses: Civil law jurisdictions (EU, China, Japan,
South Korea) do not recognize total waivers of moral rights (e.g., your right 
to attribution as an author). Avoid informal *Public Domain* claims; 
always use standard permissive open-source licenses (MIT, 0BSD, Apache-2.0) to 
grant legal permissions safely worldwide.
:::
::::

(scenario-2)=
::::{exercise} Scenario 2: Implementing an algorithm from a paper
You read a published scientific paper, understand the underlying mathematical algorithm, and write your own original software implementation from scratch.

* **Licensing Goal**: You want **reciprocal protection**—anyone can use your code, but downstream modifications distributed by others must remain open source.
* **JLA Filter Focus**: Add ⚪ **Must** toggles: `Copyleft/Share a.` + `Disclose source`.

:::{solution}
**Legal Reality**: Under EU Directive 2009/24/EC Art. 1(2), copyright protects specific source code *expression*, not underlying mathematical algorithms or scientific principles. Writing a fresh implementation creates a brand-new copyright.

* **Outcome**: **Fully Permissible.** You own 100% of the copyright for your software implementation.
* **Selected Category**: **Copyleft / Reciprocal** (driven by your goal of community protection).
* **JLA Matches**: `EUPL-1.2`, `GPL-3.0`, `AGPL-3.0`
* **User Obligation**: Users who redistribute your software or their modified versions must provide source code access under matching copyleft terms.
:::
::::

### Module 2: The Dependency Minefield – Inbound Code & Linking

Embedding third-party source code snippets or linking against strong copyleft libraries introduces legal boundaries that restrict your repository choices.

(scenario-3)=
::::{exercise} Scenario 3: Directly embedding third-party Permissive source code
You copy and paste a helper module licensed under a **Permissive license** (e.g., MIT or BSD-3-Clause) directly into your repository.

* **Licensing Goal**: Know if including permissive third-party code limits your overall repository license choices.
*  **JLA Filter Focus**: Baseline 🟢 `Commercial use` + ⚪ `Incl. Copyright` (Permissive code leaves all target options open).

:::{solution}
**Legal Reality**: Permissive licenses grant broad rights to combine, modify, and re-license derivative works, provided you preserve the original author's copyright notice.

* **Outcome**: **Full Flexibility.** Embedding Permissive code does not force a specific license on your project. You can choose Permissive *or* Copyleft.
* **JLA Matches**: `EUPL-1.2`, `GPL-3.0`, `MIT`, `Apache-2.0`
* **User Obligation**: Retain the original copyright notice and MIT/BSD license text within the specific files where the copied code resides.
:::
::::

(scenario-4)=
::::{exercise} Scenario 4: Directly embedding third-party Copyleft source code
You copy and paste a utility function licensed under a **Copyleft / Reciprocal license** (e.g., GPL-3.0 or EUPL-1.2) directly into your repository files.

* **Licensing Goal**: Fulfill legal obligations imposed by incorporating inbound copyleft code into your codebase.
*  **JLA Filter Focus**: ⚪ **Must** clause `Copyleft/Share a.` is **mandated** by inbound code.

:::{solution}
**Legal Reality**: Pasting third-party copyleft source code directly into your repository creates a single combined work. You do not hold exclusive copyright over the overall codebase.

* **EU vs. US Legal Concepts (Adaptation vs. Derivative Work)**: Coding AI tools often refer to this under the US common-law doctrine of *Derivative Works*. In the EU (Directive 2009/24/EC Art. 4(1)(b)), modifying or refactoring code is classified as a statutory act of **Adaptation, Translation, or Alteration**. Regardless of terminology, modifying copyleft code triggers mandatory reciprocal sharing obligations.
* **Outcome**: **Restricted Choice (Mandatory Copyleft).** You cannot choose a permissive license (MIT) or keep the repository proprietary.
* **Selected Category**: **Copyleft / Reciprocal**
* **JLA Matches**: `EUPL-1.2`, `GPL-3.0`
* **User Obligation**: Anyone distributing your project must provide access to the full source code under matching copyleft terms.
:::
::::

(scenario-5)=
::::{exercise} Scenario 5: Linking against a Strong Copyleft library (e.g., GSL or FFTW)
You write your code from scratch, but your program links (statically or dynamically) against a scientific library licensed under **GPL-3.0**.

* **Licensing Goal**: Select a license compliant with the inbound linking requirements of the GPL library.
*  **JLA Filter Focus**: ⚪ **Must** clause `Copyleft/Share a.` + `Disclose source` (Required across linking boundaries).

:::{solution}
**Legal Reality**: Linking your code with a Strong Copyleft library like GPL creates a combined software work upon compilation and distribution.

* **Outcome**: **Mandatory Copyleft.** To distribute the compiled application or repository, your code must be licensed under a GPL-compatible copyleft license.
* **JLA Matches**: `GPL-3.0`, `AGPL-3.0`, `EUPL-1.2`
* **User Obligation**: Anyone distributing compiled binaries must provide the full application source code under GPL-compatible copyleft terms.
:::
::::

---

### Module 3: Reproducible Infrastructure – Build Recipes vs. Binary Bundles

A major trap for RSEs is confusing **Infrastructure as Code text files** (recipes) with **compiled binary filesystems** (container images).

(scenario-6)=
::::{exercise} Scenario 6: Distributing a Container Build Recipe (Dockerfile or Apptainer .def)
You write a container build recipe (`Dockerfile` or Apptainer `.def` file) containing text commands that pull base images and install packages.

* **Licensing Goal**: Maximum adoption for your build instructions with zero restrictions.
*  **JLA Filter Focus**: Treat as original source code 🟢 `Commercial use` + ⚪ `Incl. Copyright`.

:::{solution}
**Legal Reality**: A container recipe is a text file containing build instructions (Infrastructure as Code). Referencing external base images or packages in commands does not transfer third-party copyright onto your text file.

* **Outcome**: **Fully Permissible.** You own the copyright to the build instructions and can choose any license for your recipe file.
* **JLA Matches**: `MIT`, `Apache-2.0`, `BSD-3-Clause`
* **In-File Identification (SPDX)**: Add an SPDX header comment to the first line of your Dockerfile:

```dockerfile
# SPDX-License-Identifier: MIT
# Copyright (c) 2026 Research Group

FROM ubuntu:24.04
RUN apt-get update && apt-get install -y python3
```

* **User Obligation**: Users downloading your recipe file must preserve your copyright notice.
:::
::::

(scenario-7)=
::::{exercise} Scenario 7: Distributing a Built Container Image (Docker Hub or Apptainer .sif)
You build and publish a complete container runtime image (`.sif` or Docker Hub image) bundling a base Linux OS, system libraries, dependencies, and your application code.

* **Licensing Goal**: Comply with legal obligations when distributing a bundled binary filesystem image.
*  **JLA Filter Focus**: N/A (Cannot apply a single JLA license filter to a multi-work binary bundle).

:::{solution}
**Legal Reality**: Unlike a text recipe file, a compiled container image is a **bundle of separate third-party software works**. You do not hold exclusive copyright over the entire image filesystem.

* **Outcome**: **Mandatory Multi-License Compliance.** Distribution is governed by the overlapping terms of all installed base layers, packages, and linked binaries inside.
* **Key Rule**: If your application links against a GPL library inside the container, image distribution triggers GPL source disclosure obligations for your app. If GPL tools in the container are standalone system utilities, *mere aggregation* applies.
* **User Obligation**: Ensure compliance with all third-party licenses bundled inside the container layers.
:::
::::

---

### Module 4: Modern AI Workflows – Assisted Code & Prompt Engineering

AI tools introduce distinct licensing considerations depending on whether you integrate AI-generated code snippets or author complex system prompt templates.

(scenario-8)=
::::{exercise} Scenario 8: Generating or assisting code using AI tools
You write software using AI coding assistants (ChatGPT, Copilot, DeepSeek) to generate functions, boilerplate, or refactor algorithms.

* **Licensing Goal**: Determine if using AI coding tools restricts your open-source license choices.
*  **JLA Filter Focus**: Driven by human author intent (e.g., 🟢 `Commercial use` + ⚪ `Incl. Copyright`).

:::{solution}
**Legal Reality**: Pure AI outputs lacking human authorship are generally ineligible for copyright. However, when you guide, refine, and integrate AI code into a project through creative human effort, you hold copyright over the resulting human-authored work.

* **Global & Asian AI Tools (e.g., DeepSeek, Qwen)**: Code generated using open-weight models follows standard copyright rules (human creative oversight determines code ownership). However, distinguish between **generated code** and **model weights**: always review the **Model Weights License** (e.g., OpenRAIL or specific commercial restrictions) attached to the LLM itself. When collaborating internationally or using Asian open-source software, you may also encounter **MulanPSL-2.0** (an OSI-approved Chinese permissive license compatible with MIT/Apache-2.0).
* **Outcome**: **Fully Permissible.** Using AI tools does not force a specific open-source license onto your repository.
* **JLA Matches**: `MIT`, `Apache-2.0`, `EUPL-1.2`, `GPL-3.0` (Author choice).
* **User Obligation**: Standard obligations apply based on the license you choose for your human-authored codebase.
:::
::::

(scenario-9)=
::::{exercise} Scenario 9: Including AI prompt templates in LLM applications
Your repository contains Python scripts alongside complex, 500-word structured prompt templates (system prompts, XML schemas, reasoning frameworks).

* **Licensing Goal**: Ensure prompt templates are legally covered under the same open-source license as your code.
*  **JLA Filter Focus**: Treat engineered prompts as code assets: 🟢 `Commercial use` + ⚪ `Incl. Copyright`.

:::{solution}
**Legal Reality**: Short functional prompts carry no copyright. However, complex, highly structured prompt templates meet the threshold of creative human expression and are legally protected as literary text assets.

* **Outcome**: **Fully Coverable.** Engineered prompt templates checked into your repository are covered under your overall repository license.
* **JLA Matches**: `MIT`, `Apache-2.0`, `BSD-3-Clause`
* **In-File Identification (SPDX)**: Place SPDX comments at the top of structured prompt files:

```yaml
# SPDX-License-Identifier: MIT
# System Prompt: Structured Research Summarizer Framework
```

* **User Obligation**: Downstream users who copy your prompt files must preserve your copyright notice and file headers (`# SPDX-License-Identifier: MIT`).
:::
::::

## Best Practices: Attaching a License to Your Repository

Once you have selected a license using the JLA, you must officially attach it to your repository so automated scanners, package registries, and downstream researchers can verify your terms.


### 1. Adding the Root `LICENSE` File

Always place the full text of your chosen license in a plain-text file named `LICENSE` or `LICENSE.txt` at the root of your repository.

* **Exact Legal Text**: Copy the standard text directly from [spdx.org/licenses](https://spdx.org/licenses/) or [choosealicense.com](https://choosealicense.com/).
* **Copyright Header**: Ensure you fill in the copyright year and copyright holder line at the top of the license text:
  ```text
  Copyright (c) 2026 [Author Name or Institution Name]
  ```
* **Do Not Edit Terms**: Never modify the legal wording of standard licenses (e.g., removing clauses from GPL or MIT). Custom license edits create *non-standard* legal texts that compliance scanners cannot parse, defaulting your repository back to restricted status.

---

### 2. Documenting License Status in `README.md`

Add a dedicated **License** section near the bottom of your repository's `README.md` file, along with a machine-readable badge:

```markdown
## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
```

---

### 3. Automated Compliance with the REUSE Standard

For multi-asset research repositories containing code, data, container build recipes, and prompt templates, follow the [FSFE REUSE Initiative](https://reuse.software/) standard:

1. **Include License Texts**: Place full license files inside a `LICENSES/` directory (e.g., `LICENSES/MIT.txt`, `LICENSES/GPL-3.0-or-later.txt`).
2. **Add In-File SPDX Headers**: Label every source file, build script, and prompt file with SPDX tags.
3. **Verify Compliance**: Run the automated REUSE linter in your CI/CD pipeline:

```bash
# Install and run REUSE compliance check
pip install reuse
reuse lint
```

When `reuse lint` passes, downstream researchers can automatically verify the 
legal status of every single asset in your codebase.

## Summary: Resolving the Compliance Pipeline

At the start of this lesson, our project hit a **❌ BUILD FAILURE** because a pasted copyleft snippet conflicted with our target `MIT` license. 

By applying the legal concepts and technical tools covered in this module, we can trace how our learned skills directly resolve the original pipeline crash:

```{mermaid}
%%{init: {'themeVariables': { 'edgeLabelBackground': '#faf5ff' }}}%%
flowchart TB

    subgraph box["Resolved CI/CD License Compliance Pipeline"]
        A["<b>Build Trigger: Push code with inbound dependency/snippet"] --> B["Run Compliance Scanner"]
        B --> C{"Check Inbound vs Outbound Terms"}
        
        C -->|"Apply JLA Decision Matrix &</>Copyright Principles"| E{"Select Compliant Strategy"}
        
        E -->|"<b>Strategy 1: Align Project License<b><i>(Module 2)</i>Re-license repo to GPL-3.0 / EUPL-1.2"| G["✅ <b>BUILD PASS</b>Project license matches inbound copyleft terms"]
        
        E -->|"<b>Strategy 2: Clean Implementation</b></><i>(Module 1)</i></>Rewrite code expression from scratch"| H["✅ <b>BUILD PASS</b></>Fresh expression frees original MIT license"]
        
        G --> V["<b>Standardize & Verify Repository</b></>1. Tag files with <b>SPDX Identifiers</b> (<code># SPDX-License-Identifier</code>)</>2. Add root <code>LICENSE</code> file & README badge</>3. Execute <b>REUSE Linter</b> (<code>reuse lint</code>)"]
        H --> V
        
        V --> SUCCESS["🎉 <b>COMPLIANT OPEN-SOURCE RELEASE</b></>Legally safe, reproducible & ready for research reuse"]
    end

    classDef pass fill:#e6ffe6,stroke:#2b8a3e,stroke-width:2px,color:#1b4332;
    classDef neutral fill:#f8f9fa,stroke:#495057,stroke-width:2px,color:#212529;
    classDef box_fill fill:#ffffff,stroke:#adb5bd,stroke-width:1px;

    class G,H,V,SUCCESS pass;
    class A,B,C,E neutral;
    class box box_fill;
```

### What Resolved the Issue:

1. **Applied Copyright Expression vs. Idea (Option C)**: You learned that copyright protects code *expression*, not underlying algorithms. Rewriting the logic creates a fresh copyright, freeing you to maintain an `MIT` permissive license.
2. **Applied the JLA Decision Matrix (Option B)**: You learned how to navigate inbound copyleft obligations. Re-licensing the repository to `GPL-3.0` or `EUPL-1.2` satisfies reciprocal terms while keeping your work open source.
3. **Bypassed Legal Traps (Options A & D)**: You recognized that code comments cannot waive statutory licenses and that deleting a license triggers the default *"All Rights Reserved"* trap.
4. **Standardized Distribution**: You embedded **SPDX headers** across code, recipes, and prompts, verifying full repository compliance via `reuse lint`.
