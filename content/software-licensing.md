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

## Motivation

```{mermaid}
%%{init: {'themeVariables': { 'edgeLabelBackground': '#faf5ff' }}}%%
flowchart TB

    subgraph box["CI/CD License Compliance Debugging Pipeline"]
        A["<b>Build Trigger:</b> Push to my-analysis-tool"] --> B["Run Compliance Scanner"]
        B --> C{"Check Inbound vs.<br/>Outbound Terms"}
        
        C -->|"Your Target License: MIT (Permissive)<br/>Pasted Snippet: GPL-3.0 (Copyleft)"| D["❌ <b>BUILD FAILURE</b><br/>Pasted copyleft snippet restricts MIT release"]
        
        D --> E{"Select Patch Option"}
        
        E -->|"Option A: Keep MIT & add comment '# Originally GPL'"| F["❌ <b>BUILD FAIL</b><br/>Comments do not override copyleft terms"]
        E -->|"Option B: Re-license repo to GPL-3.0 / EUPL-1.2"| G["✅ <b>BUILD PASS</b><br/>Your license matches the pasted copyleft snippet"]
        E -->|"Option C: Rewrite code from scratch to replace snippet"| H["✅ <b>BUILD PASS</b><br/>New code expression frees your target license"]
        E -->|"Option D: Delete LICENSE file to bypass scanner"| I["⚠️ <b>PASSED SCANNER (TRAP!)</b><br/>No license = Default 'All Rights Reserved'<br/>Nobody can legally run, modify, or reuse your tool"]

        P["<b>Permissive</b><br/>(MIT, Apache-2.0, 0BSD)<br/><i>'Do whatever you want, just keep credit'</i>"]
        CL["<b>Copyleft / Reciprocal</b><br/>(GPL-3.0, EUPL-1.2)<br/><i>'Must share changes under same terms'</i>"]
    end

    P -.->|"I want to use"| C
    CL -.->|"Pasted code snippet uses"| C

    classDef pass fill:#e6ffe6,stroke:#2b8a3e,stroke-width:2px,color:#1b4332;
    classDef copyleft fill:#fff9db,stroke:#f59f00,stroke-width:2px,color:#5c3c00;
    classDef fail fill:#ffe3e3,stroke:#e03131,stroke-width:2px,color:#5c0000;
    classDef warning fill:#fff3bf,stroke:#f08c00,stroke-width:2px,color:#5c3c00;
    classDef neutral fill:#f8f9fa,stroke:#495057,stroke-width:2px,color:#212529;
    classDef box_fill fill:#ffffff,stroke:#adb5bd,stroke-width:1px;

    class P,G,H pass;
    class CL copyleft;
    class D,F fail;
    class I warning;
    class A,B,C,E neutral;
    class box box_fill; 

```


## Introduction: What is a Software License?

In {bdg-warning}`Option D` of our debugging pipeline, deleting the `LICENSE` file tricked the automated scanner into passing, but created a major distribution trap. Under copyright law worldwide, software without a license automatically defaults to **"All Rights Reserved"**: meaning nobody else has the legal right to run, modify, or cite your code.

A **software license** is an explicit permission grant that overrides this statutory default, defining exactly how downstream researchers can reuse your work.

```{mermaid}
%%{init: {'themeVariables': { 'edgeLabelBackground': '#faf5ff' }}}%%
flowchart TD
    A["<b>Your Research Codebase</b><br/><i>(Source code, container definition files, prompt templates)</i>"] -->|"Option D: No License Attached<br/>(Statutory Default)"| B["<b>All Rights Reserved</b><br/>❌ Zero permissions: Nobody can legally run, modify, or share"]
    
    A -->|"Attach Software License<br/>(Explicit Permission Grant)"| C{"Select License Flavor"}
    
    C -->|"Permissive<br/>(MIT, Apache-2.0, 0BSD)"| D["<b>Maximum Reuse Freedom</b><br/>✅ Anyone can run, modify, embed in commercial tools, or re-license"]
    C -->|"Copyleft / Reciprocal<br/>(GPL-3.0, EUPL-1.2)"| E["<b>Reciprocal Protection</b><br/>✅ Free to run & modify, but distributed changes <i>must</i> stay open source"]
    C -->|"Proprietary / Closed Source<br/>(Commercial EULA)"| F["<b>Closed Source / Restricted</b><br/>🚫 <i>Flavour not discussed in this lesson</i>"]

    classDef defaultState fill:#ffe3e3,stroke:#e03131,stroke-width:2px,color:#5c0000;
    classDef openState fill:#e6ffe6,stroke:#2b8a3e,stroke-width:2px,color:#1b4332;
    classDef copyleftState fill:#fff9db,stroke:#f59f00,stroke-width:2px,color:#5c3c00;
    classDef closedState fill:#f8f9fa,stroke:#adb5bd,stroke-width:2px,stroke-dasharray: 5 5,color:#6c757d;
    classDef codeState fill:#f8f9fa,stroke:#495057,stroke-width:2px,color:#212529;

    class B defaultState;
    class D openState;
    class E copyleftState;
    class F closedState;
    class A,C codeState;

```


### Copyright Foundation: Expression vs. Ideas

To understand why licenses are required, you must understand how copyright law treats software. Under EU statutory law (Directive 2009/24/EC) and international treaties, software is protected under copyright as a **literary work**. 

However, copyright law draws a sharp, fundamental distinction between what is protected and what is free for anyone to use:

* **Protected (Code Expression)**: The specific source code text, variable names, binaries, container build recipes, prompt engineering text, and preparatory design documents.
* **Not Protected (Underlying Ideas)**: Mathematical algorithms, scientific models, programming logic, data structures, and interface principles.

Because copyright restricts only the *creative human expression* and not the underlying *ideas or algorithms*, developers use open-source licenses to define the exact terms under which that expression can be legally shared and modified.

### Scope of this Lesson: What Counts as "Software"?

Across international legal frameworks (such as 17 U.S.C. § 101 and WIPO model provisions), software is broadly defined as a set of instructions to be used directly or indirectly in a computer to bring about a certain result. 

Because modern research software extends beyond simple Python scripts, this lesson applies copyright and licensing principles across six core research software assets:

* **Source Code**: Original algorithms written from scratch or implemented from scientific papers.
* **Third-Party Integrations**: Embedded permissive or copyleft code snippets and dynamically/statically linked libraries.
* **Infrastructure as Code**: Ansible playbooks,Terraform configurations,container Recipes  (`Dockerfile`, Apptainer `.def`).
* **Container Images**: Bundled binary filesystem snapshots (`.sif` files, OCI registry images).
* **AI-Assisted Code**: Code generated, refactored, or assembled with human creative oversight.
* **AI Prompt Templates**: Complex, engineered system prompts and structured frameworks meeting the threshold of human creative authorship.

## Global Context: Software Engineering Across Legal Borders

Software development is an inherently cosmopolitan business. Research software engineers routinely collaborate across continents, fetch dependencies from global registries, and commit code to international repositories. 

However, modern developers face a subtle trap: **AI legal bias**. Coding assistants (ChatGPT, Claude, GitHub Copilot) are overwhelmingly trained on US-centric web data and legal texts. Consequently, when asked about software ownership or licensing, AI outputs almost universally default to **US common law concepts** (*"Fair Use"*, *"Work Made for Hire"*, *"Derivative Works"*). Relying blindly on AI advice can create legal blind spots when operating in the EU or collaborating globally.

:::{dropdown} Deep Dive: Comparative Legal Mechanisms (US vs. EU vs. Asia)
:color: info

* **Code Adaptation / Refactoring**
  * **US Concept:** **Derivative Work** (broadly interpreted judicial doctrine).
  * **EU Concept:** **Adaptation**, translation, arrangement, or alteration (Directive 2009/24/EC Art. 4(1)(b)).
  * **Practical Impact:** EU law avoids the vague term "derivative work." Any code modification is classified as a specific statutory act of adaptation or translation.

* **User Rights & Interoperability** (Run, debug, reverse engineer)
  * **US Concept:** **Fair Use** (flexible balancing test evaluated case-by-case in court).
  * **EU Concept:** **Statutory Exceptions** (Directive 2009/24/EC Articles 5 & 6).
  * **Practical Impact:** EU law splits user rights into **non-waivable statutory rights** (backup copies under Art. 5(2), studying/testing under Art. 5(3), and decompilation for interoperability under Art. 6, which cannot be overridden by contract under Art. 8) and **contract-overridable default rules** (error correction under Art. 5(1), which applies unless an employment or vendor contract specifies otherwise).

* **Code Ownership** (Employee authorship)
  * **US Concept:** **Work Made for Hire** (the employer is legally recognized as the primary author).
  * **EU Concept:** **Employer Economic Rights** (Directive 2009/24/EC Art. 2(3)).
  * **Practical Impact:** The individual developer remains the legal author, but all economic exploitation rights automatically transfer to the employer for code created during employment duties.

* **Waiving Rights & Public Domain** (Giving up control)
  * **US Concept:** **Public Domain Dedication** (authors can fully surrender both economic and moral rights).
  * **EU & Asian Civil Law Concept:** **Economic Rights Transfer / Non-Waivable Moral Rights**.
  * **Practical Impact:** Civil law traditions (EU, China, Japan, South Korea) do not allow complete waivers of moral rights (e.g., the author's right to attribution). Always use permissive open-source licenses (MIT, 0BSD) rather than informal public domain claims.

* **Collaborating with Asian Ecosystems & Chinese AI Tools**
  * **Civil Law Alignment:** Legal frameworks in China, Japan, and South Korea mirror EU civil law rather than US common law, strictly protecting moral rights and requiring formal contract grants.
  * **OSI-Approved Chinese Licenses:** Chinese open-source projects frequently use **MulanPSL-2.0** (Mulan Permissive Software License), an OSI-approved bilingual license designed to align with Chinese contract law while maintaining global compatibility with MIT/Apache-2.0.
  * **Using Chinese AI Models (e.g., DeepSeek, Qwen):** While code generated using Chinese LLMs follows standard copyright rules (human creative oversight determines ownership), always review the **Model Weights License** (e.g., OpenRAIL or specific commercial restrictions) attached to the model itself, as some open-weight licenses restrict specific commercial downstream uses.
:::

## Classification of licenses

```{mermaid}
   flowchart LR
     subgraph box[ ]
       A["Copyright Law Foundation<br/>(EU Directive 2009/24/EC)"] --> B["Permissive<br/>(MIT, BSD, Apache-2.0)"]
       A --> C["Copyleft / Reciprocal<br/>(EUPL, GPL, LGPL)"]
       A --> D["All Rights Reserved / Proprietary"]
   
       B --> B1["Run & Modify?<br/><b>Yes!</b>"]
       B --> B2["Sell copies as-is?<br/><b>Yes!</b>"]
       B --> B3["Embed in closed product & sell?<br/><b>Yes!</b>"]
       B --> B4["Must changes stay open?<br/><b>No</b> (Optional)"]
   
       C --> C1["Run & Modify?<br/><b>Yes!</b>"]
       C --> C2["Sell copies as-is?<br/><b>Yes!</b>"]
       C --> C3["Embed in closed product & sell?<br/><b>No!</b>"]
       C --> C4["Must changes stay open?<br/><b>Yes!</b> (Mandatory)"]
   
       D --> D1["Run & Modify?<br/><b>No!</b> (Zero permission)"]
       D --> D2["Sell copies as-is?<br/><b>No!</b>"]
       D --> D3["Embed in closed product & sell?<br/><b>No!</b>"]
       D --> D4["Can I change code?<br/><b>No</b> (Closed source)"]
       subgraph osi["OSI compatible"]
           B["Permissive<br/>(MIT, BSD, Apache-2.0)"]
           C["Copyleft / Reciprocal<br/>(EUPL, GPL, LGPL)"]
         end
     end
       classDef permissive fill:#e6ffe6,stroke:#2b8a3e,stroke-width:2px,color:#1b4332;
       classDef copyleft fill:#fff9db,stroke:#f59f00,stroke-width:2px,color:#5c3c00;
       classDef proprietary fill:#ffe3e3,stroke:#e03131,stroke-width:2px,color:#5c0000;
       classDef header fill:#f8f9fa,stroke:#495057,stroke-width:2px,color:#212529;
       classDef mains fill:#fafadc,stroke:#495057,stroke-width:2px,color:#212529;
       classDef osiBox fill:#f8f9fa,stroke:#0275d8,stroke-width:2px,stroke-dasharray: 5 5,color:#0275d8;
       classDef box fill:#ffffff;
       class B1,B2,B3,B4,C1,C2 permissive;
       class C3,C4,D1,D2,D3,D4 proprietary;
       class box box; 
       class A,B,C,D mains;
       class osi osiBox;

```

## Selecting Compliant Licenses

When using the European Commission's [Joinup Licensing Assistant (JLA)](https://interoperable-europe.ec.europa.eu/collection/eupl/solution/licensing-assistant/find-and-compare-software-licenses), license selection depends on your RSE workflow. The JLA groups criteria into four categories: **🟢 Can** (Permissions), **⚪ Must** (Obligations), **🔵 Compatible** (Domain), and **🟡 Support** (OSI Approval).

### JLA Decision Matrix at a Glance

| Scenario Module | Key JLA Toggle (⚪ Must) | Resulting Category | Target Licenses |
| :--- | :--- | :--- | :--- |
| **1. Own Code** | `Incl. Copyright` | 🟢 Permissive | `MIT`, `Apache-2.0`, `BSD-3-Clause` |
| **2. Math Implementation** | `Copyleft/Share a.` + `Disclose Source` | 🟡 Copyleft | `EUPL-1.2`, `GPL-3.0`, `AGPL-3.0` |
| **3. Embed Permissive** | `Incl. Copyright` | 🟢 Flexible (Any) | `MIT` or `EUPL-1.2` / `GPL-3.0` |
| **4. Embed Copyleft** | `Copyleft/Share a.` *(Mandatory)* | 🟡 Copyleft | `EUPL-1.2`, `GPL-3.0` |
| **5. Link GPL Library** | `Copyleft/Share a.` *(Mandatory)* | 🟡 Copyleft | `GPL-3.0`, `EUPL-1.2` |
| **6. AI-Assisted Code** | `Incl. Copyright` | 🟢 Author Choice | `MIT`, `Apache-2.0` (or Copyleft) |
| **7. Container Recipe** | `Incl. Copyright` | 🟢 Permissive | `MIT`, `Apache-2.0` |
| **8. Built Image** | Overlapping Component Terms | ⚠️ Multi-License | Governed by individual image layers |
| **9. Prompt Template** | `Incl. Copyright` | 🟢 Permissive | `MIT`, `Apache-2.0` |

---

### Module 1: Clean Slate – Authoring Original Code & Algorithms

When writing original code or implementing published mathematical logic, you control 100% of your copyright.

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
:::
::::

::::{exercise} Scenario 2: Implementing an algorithm from a paper
You read a published scientific paper, understand the underlying mathematical algorithm, and write your own original software implementation from scratch.

* **Licensing Goal**: You want **reciprocal protection**—anyone can use your code, but downstream modifications distributed by others must remain open source.
*  **JLA Filter Focus**: Add ⚪ **Must** toggles: `Copyleft/Share a.` + `Disclose source`.

:::{solution}
**Legal Reality**: Under EU Directive 2009/24/EC Art. 1(2), copyright protects specific source code *expression*, not underlying mathematical algorithms or scientific principles. Writing a fresh implementation creates a brand-new copyright.

* **Outcome**: **Fully Permissible.** You own 100% of the copyright for your software implementation.
* **Selected Category**: **Copyleft / Reciprocal** (driven by your goal of community protection).
* **JLA Matches**: `EUPL-1.2`, `GPL-3.0`, `AGPL-3.0`
* **User Obligation**: Users who redistribute your software or their modified versions must provide source code access under matching copyleft terms.
:::
::::

---

### Module 2: The Dependency Minefield – Inbound Code & Linking

Embedding third-party source code snippets or linking against strong copyleft libraries introduces legal boundaries that restrict your repository choices.

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

::::{exercise} Scenario 4: Directly embedding third-party Copyleft source code
You copy and paste a utility function licensed under a **Copyleft / Reciprocal license** (e.g., GPL-3.0 or EUPL-1.2) directly into your repository files.

* **Licensing Goal**: Fulfill legal obligations imposed by incorporating inbound copyleft code into your codebase.
*  **JLA Filter Focus**: ⚪ **Must** clause `Copyleft/Share a.` is **mandated** by inbound code.

:::{solution}
**Legal Reality**: Pasting third-party copyleft source code directly into your repository creates a single combined (derivative) work. You do not hold exclusive copyright over the overall codebase.

* **Outcome**: **Restricted Choice (Mandatory Copyleft).** You cannot choose a permissive license (MIT) or keep the repository proprietary.
* **Selected Category**: **Copyleft / Reciprocal**
* **JLA Matches**: `EUPL-1.2`, `GPL-3.0`
* **User Obligation**: Anyone distributing your project must provide access to the full source code under matching copyleft terms.
:::
::::

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

::::{exercise} Scenario 7: Distributing a Container Build Recipe (Dockerfile or Apptainer .def)
You write a container build recipe (`Dockerfile` or Apptainer `.def` file) containing text commands that pull base images and install packages.

* **Licensing Goal**: Maximum adoption for your build instructions with zero restrictions.
*  **JLA Filter Focus**: Treat as original source code 🟢 `Commercial use` + ⚪ `Incl. Copyright`.

:::{solution}
**Legal Reality**: A container recipe is a text file containing build instructions (Infrastructure as Code). Referencing external base images or packages in commands does not transfer third-party copyright onto your text file.

* **Outcome**: **Fully Permissible.** You own the copyright to the build instructions and can choose any license for your recipe file.
* **JLA Matches**: `MIT`, `Apache-2.0`, `BSD-3-Clause`
* **User Obligation**: Users downloading your recipe file must preserve your copyright notice.
:::
::::

::::{exercise} Scenario 8: Distributing a Built Container Image (Docker Hub or Apptainer .sif)
You build and publish a complete container runtime image (`.sif` or Docker Hub image) bundling a base Linux OS, system libraries, dependencies, and your application code.

* **Licensing Goal**: Comply with legal obligations when distributing a bundled binary filesystem image.
*  **JLA Filter Focus**: N/A (Cannot apply a single JLA license filter to a multi-work binary bundle).

:::{solution}
**Legal Reality**: Unlike a text recipe file, a compiled container image is a **bundle of separate third-party software works**. You do not hold exclusive copyright over the entire image filesystem.

* **Outcome**: **Mandatory Multi-License Compliance.** Distribution is governed by the overlapping terms of all installed base layers, packages, and linked binaries inside.
* **Key Rule**: If your application links against a GPL library inside the container, image distribution triggers GPL source disclosure obligations for your app. If GPL tools in the container are standalone system utilities, "mere aggregation" applies.
* **User Obligation**: Ensure compliance with all third-party licenses bundled inside the container layers.
:::
::::

---

### Module 4: Modern AI Workflows – Assisted Code & Prompt Engineering

AI tools introduce distinct licensing considerations depending on whether you integrate AI-generated code snippets or author complex system prompt templates.

::::{exercise} Scenario 6: Generating or assisting code using AI tools
You write software using AI coding assistants (ChatGPT, Copilot) to generate functions, boilerplate, or refactor algorithms.

* **Licensing Goal**: Determine if using AI coding tools restricts your open-source license choices.
*  **JLA Filter Focus**: Driven by human author intent (e.g., 🟢 `Commercial use` + ⚪ `Incl. Copyright`).

:::{solution}
**Legal Reality**: Pure AI outputs lacking human authorship are ineligible for copyright. However, when you guide, refine, and integrate AI code into a project through creative human effort, you hold copyright over the resulting human-authored work.

* **Outcome**: **Fully Permissible.** Using AI tools does not force a specific open-source license onto your repository.
* **JLA Matches**: `MIT`, `Apache-2.0`, `EUPL-1.2`, `GPL-3.0` (Author choice).
* **User Obligation**: Standard obligations apply based on the license you choose for your human-authored codebase.
:::
::::

::::{exercise} Scenario 9: Including AI prompt templates in LLM applications
Your repository contains Python scripts alongside complex, 500-word structured prompt templates (system prompts, XML schemas, reasoning frameworks).

* **Licensing Goal**: Ensure prompt templates are legally covered under the same open-source license as your code.
*  **JLA Filter Focus**: Treat engineered prompts as code assets: 🟢 `Commercial use` + ⚪ `Incl. Copyright`.

:::{solution}
**Legal Reality**: Short functional prompts carry no copyright. However, complex, highly structured prompt templates meet the threshold of creative human expression and are legally protected as literary text assets.

* **Outcome**: **Fully Coverable.** Engineered prompt templates checked into your repository are covered under your overall repository license.
* **JLA Matches**: `MIT`, `Apache-2.0`, `BSD-3-Clause`
* **User Obligation**: Downstream users who copy your prompt files must preserve your copyright notice and file headers (`# SPDX-License-Identifier: MIT`).
:::
::::

### Best Practice: 

#### In-File Identification using SPDX

Once you select a license, apply it to individual source files and build recipes using **SPDX identifiers** (Software Package Data Exchange). Managed by the Linux Foundation, an SPDX identifier is a standardized, machine-readable short tag (e.g., `MIT`, `Apache-2.0`, `GPL-3.0-only`, `0BSD`) recognized by automated compliance scanners, package managers, and CI/CD build pipelines.

Instead of pasting long legal texts at the top of every file, add a single-line comment at the very first line of your script or recipe:
 - In a container recipe

```dockerfile
# SPDX-License-Identifier: MIT
FROM ubuntu:24.04
```
 - In a python script 
```python
# SPDX-License-Identifier: 0BSD
import numpy as np
```

#### How to include a license file
