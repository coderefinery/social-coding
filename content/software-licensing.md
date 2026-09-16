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
defaults to "All Rights Reserved": meaning nobody else has the legal right to run,
modify, embed, or cite your code. A software license is a legal permission grant
created by the author that overrides this statutory default, defining how 
downstream researchers can reuse your work.

* Open-source licenses fall into two main families:

    * **Permissive (e.g., MIT, Apache-2.0, 0BSD):** "Do whatever you want, just keep credit." Grants maximum reuse freedom, allowing anyone to modify, embed, or re-license your code in open or closed projects.

    * **Copyleft / Reciprocal (e.g., GPL-3.0, EUPL-1.2):** "Share alike." Grants full freedom to run and modify, but mandates that any distributed derivative work must also be released under the same open-source copyleft terms.

The diagram below unifies these license choices and their downstream rights:

```{mermaid}
%%{init: {'themeVariables': { 'edgeLabelBackground': '#faf5ff' }}}%%

flowchart TB
    A["<b>Your Research Codebase</b><br/><i>(Source code, container recipes, prompt templates)</i>"] -->|"No License Attached<br/>(Statutory Default)"| B["<b>All Rights Reserved</b><br/>❌ Zero permissions: Cannot run, modify, or share"]

    A -->|"Attach Open-Source License<br/>(Explicit Permission Grant)"| C{"Select License Flavor"}

    C -->|"Permissive<br/>(MIT, Apache-2.0, 0BSD)"| D["<b>Permissive License</b>"]
    C -->|"Copyleft / Reciprocal<br/>(GPL-3.0, EUPL-1.2)"| E["<b>Copyleft License</b>"]
    C -->|"Proprietary / Closed Source"| F["<b>Closed Source / Restricted</b><br/>🚫 <i>Flavour not discussed in this lesson</i>"]

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
        A[<b>Update</b><br/>Paste snippet copyied from somewhere ] --> A2["<b>Build Trigger:</b>Push to my-code-base"]
        A2["<b>Build Trigger:</b> Push to my-code-base"] --> B["Run Compliance Scanner"]
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

Global Context & AI Legal Bias

Software development is inherently cosmopolitan: research software engineers
routinely collaborate across legal borders, fetch dependencies from global
registries, and commit code to international repositories.

However, modern developers face a subtle trap: AI legal bias. Coding assistants
(ChatGPT, Claude, GitHub Copilot) are overwhelmingly trained on US-centric
web data and legal texts. Consequently, when asked about software ownership
or licensing, AI outputs almost universally default to US common law concepts
("Fair Use", "Work Made for Hire", "Derivative Works"). Relying blindly on
AI advice can create legal blind spots when operating under EU statutory
frameworks or collaborating globally.Selecting Compliant Licenses

When using the European Commission's Joinup Licensing Assistant (JLA),
license selection depends on your RSE workflow. The JLA groups 
criteria into four categories: 
🟢 Can (Permissions), ⚪ Must (Obligations), 🔵 Compatible (Domain), 
and 🟡 Support (OSI Approval).
### JLA Decision Matrix at a Glance

| Scenario Module | Key JLA Toggle (⚪ Must) | Resulting Category | Target Licenses |
| :--- | :--- | :--- | :--- |
| **1. Own Code** | `Incl. Copyright` | 🟢 Permissive | `MIT`, `Apache-2.0`, `BSD-3-Clause` |
| **2. Math Implementation** | `Copyleft/Share a.` + `Disclose Source` | 🟡 Copyleft | `EUPL-1.2`, `GPL-3.0`, `AGPL-3.0` |
| **3. Embed Permissive** | `Incl. Copyright` | 🟢 Flexible (Any) | `MIT` or `EUPL-1.2` / `GPL-3.0` |
| **4. Embed Copyleft** | `Copyleft/Share a.` *(Mandatory)* | 🟡 Copyleft | `EUPL-1.2`, `GPL-3.0` |
| **5. Link GPL Library** | `Copyleft/Share a.` *(Mandatory)* | 🟡 Copyleft | `GPL-3.0`, `EUPL-1.2` |
| **6. Container Recipe** | `Incl. Copyright` | 🟢 Permissive | `MIT`, `Apache-2.0` |
| **7. Built Image** | Overlapping Component Terms | ⚠️ Multi-License | Governed by individual image layers |
| **8. AI-Assisted Code** | `Incl. Copyright` | 🟢 Author Choice | `MIT`, `Apache-2.0` (or Copyleft) |
| **9. Prompt Template** | `Incl. Copyright` | 🟢 Permissive | `MIT`, `Apache-2.0` |

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

