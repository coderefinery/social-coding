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

    * **Permissive (e.g., MIT, Apache-2.0, 0BSD):** *Do whatever you want, just keep credit*. 
      Grants maximum reuse freedom, allowing anyone to modify, embed, or re-license your code 
      in open or closed projects.

    * **Copyleft/Reciprocal (e.g., GPL-3.0, EUPL-1.2):** *Share alike.* Grants full freedom 
      to run and modify, but mandates that any distributed adaptations or combined work must 
      also be released under matching copyleft terms. Often informally referred to as *viral* 
      or *infectious* because its open-source requirements propagate across code boundaries 
      (such as embedding snippets or static linking) into downstream projects. The diagram 
      below unifies these license choices and their downstream rights:

```{mermaid}
%%{init: {'themeVariables': { 'edgeLabelBackground': '#faf5ff' }}}%%

flowchart TB

  subgraph box["How License Selection Governs Code Reuse"]
    A["<b>Your Research Codebase </b></><i>(Source code, container recipes, prompt templates)</i>"] -->|"No License Attached</>(Statutory Default)"| B["<b>All Rights Reserved</b></>❌ Zero permissions: Cannot run, modify, or share"]

    A -->|"Attach License</>(Explicit Permission Grant)"| C{"Select License"}

    C -->|"Goal: Maximum adoption & unrestricted reuse"| D["<b>Permissive License</b>"]
    C -->|"Goal: Ensure changes stay open-source (Reciprocity)"| E["<b>Copyleft License</b>"]
    C -->|"Goal: Proprietary control & restricted access"| F["<b>Closed Source / Restricted</b></>🚫 <i>Flavour not discussed in this lesson</i>"]

    D --> D1["Run & Modify? <b>Yes!</b>"]
    D --> D2["Embed in closed product? <b>Yes!</b>"]
    D --> D3["Must changes stay open? <b>No</b> (Optional)"]

    E --> E1["Run & Modify? <b>Yes!</b>"]
    E --> E2["Embed in closed product? <b>No!</b>"]
    E --> E3["Must changes stay open? <b>Yes!</b> (Mandatory)"]
  end  
   classDef green fill:#e6ffe6,stroke:#2b8a3e,stroke-width:2px,color:#1b4332;
   classDef red fill:#ffe3e3,stroke:#e03131,stroke-width:2px,color:#5c0000;
   classDef yellow fill:#fff9db,stroke:#f59f00,stroke-width:2px,color:#5c3c00;
   classDef white fill:#f8f9fa,stroke:#adb
   classDef dashed fill:#f8f9fa,stroke:#adb5bd,stroke-width:2px,stroke-dasharray: 5 5,color:#000000;
   classDef dashed_red fill:#ffe3e3,stroke:#adb5bd,stroke-width:2px,stroke-dasharray: 5 5,color:#000000;
   classDef defaultState fill:#ffe3e3,stroke:#e03131,stroke-width:2px,color:#5c0000;
   classDef box_fill fill:#ffffff,stroke:#adb5bd,stroke-width:1px;
    
   class D1,D2,D3,E1,E3 green;
   class E2 red;
   class D,E yellow;
   class F dashed;
   class B dashed_red;
   class A,C white;
   class box box_fill;
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
*ideas or algorithms*, developers could use open-source licenses to define the exact terms under 
which that expression can be legally shared and modified.

### Scope of this Lesson: What Counts as *Software*?

Across international legal frameworks (such as 17 U.S.C. § 101 and WIPO-World Intellectual Property Organization
model provisions), software is broadly defined as a set of instructions to be used directly or indirectly in 
a computer to bring about a certain result. 

Because modern research software extends beyond simple Python scripts, this lesson applies 
copyright and licensing principles across six core research software assets:

* **Source Code**: Original algorithms written from scratch or implemented from scientific papers.
* **Third-Party Integrations**: Embedded permissive or copyleft code snippets and linked libraries (dynamically/statically).
* **Infrastructure as Code**: Ansible playbooks,Terraform configurations,container Recipes  (`Dockerfile`, Apptainer `.def`).
* **Container Images**: Bundled binary filesystem snapshots (`.sif` files, OCI registry images).
* **AI-Assisted Code**: Code generated, refactored, or assembled with human creative oversight.
* **AI Prompt Templates**: Complex, engineered system prompts and structured frameworks meeting the threshold of human creative authorship.


## Motivation: Debugging a License Compliance Failure

With the understanding of the difference between Permissive and Copyleft licenses, 
examine what happens when they collide inside an automated CI/CD pipeline:

```{mermaid}
%%{init: {'themeVariables': { 'edgeLabelBackground': '#faf5ff' }}}%%
flowchart TB

    subgraph box["CI/CD License Compliance Debugging Pipeline"]
        A[Paste snippet copyied from somewhere ] --> A2["<b>Build Trigger:</b>Push to my-code-base"]
        A2["<b>Build Trigger:</b> Push to my-code-base"] --> B["Run Compliance Scanner"]
        B --> C{"Check Inbound vs.</>Outbound Terms"}
        
        C -->|"Target License:Permissive</> but pasted snippet:Copyleft"| D["❌ <b>BUILD FAILURE</b><br/>Pasted copyleft snippet restricts MIT release"]
        
        D --> E{"Select Patch Option"}
        
        E -->|"Option A: Keep MIT & add comment '# Originally GPL'"| F["❌ <b>BUILD FAIL</b><br/>Comments do not override copyleft terms"]
        E -->|"Option B: Re-license repo to GPL-3.0 / EUPL-1.2"| G["✅ <b>BUILD PASS</b><br/>Your license matches the pasted copyleft snippet"]
        E -->|"Option C: Rewrite code from scratch to replace snippet"| H["✅ <b>BUILD PASS</b><br/>New code expression frees your target license"]
        E -->|"Option D: Delete LICENSE file to bypass scanner"| I["⚠️ <b>PASSED SCANNER (LEGAL TRAP!)</b><br/>Infringes third-party copyright & locks own code to All Rights Reserved"]

        P["<b>Permissive</b><br/>(MIT, Apache-2.0, 0BSD)</><i>'Do whatever you want, just keep credit'</i>"]
        CL["<b>Copyleft / Reciprocal</b><br/>(GPL-3.0, EUPL-1.2)</><i>'Must share changes under same terms'</i>"]
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
and answer project setup questions. 

However, using these tools for legal or licensing guidance introduces a subtle 
risk of **AI legal bias** as AI models are overwhelmingly trained on US-centric 
web data and legal forum posts, their outputs default almost universally 
to **US common law concepts** such as *Fair Use*, *Work Made for Hire*, and 
*Derivative Works*.

In contrast, developers operating under EU statutory frameworks (such as Directive 2009/24/EC) 
face a different legal reality related to exceptions, author ownership, and code adaptations. 
Relying blindly on AI legal advice creates significant compliance blind spots, 
which is why this lesson equips you with a direct, EU-aligned framework for software licensing.



## Standardizing In-File Declarations: SPDX Identifiers

Selecting a license is only half the battle; automated scanners and CI/CD pipelines need a machine-readable way to verify license compliance per file without parsing long legal texts.

Managed by the Linux Foundation, **SPDX identifiers** (Software Package Data Exchange) provide standardized short tags (e.g., `MIT`, `Apache-2.0`, `GPL-3.0-only`, `EUPL-1.2`) placed at the very top line of every source file:

```python
# SPDX-License-Identifier: MIT
# Copyright (c) 2026 Author Name <author@institute.eu>
```

Throughout the exercise scenarios below, look for the **In-File Identification (SPDX)** callouts to see how these tags apply directly to Python scripts, container recipes, and engineered prompt templates.


## License Selection Decision Matrix & Scenario Index

To help you navigate open-source compliance, the matrix below serves as an upfront 
quick-reference summary and interactive index for the core licensing scenarios 
encountered in research software engineering. 


### [Joinup Licensing Assistant (JLA)](https://interoperable-europe.ec.europa.eu/collection/eupl/solution/licensing-assistant/find-and-compare-software-licenses)
  *  Our decision framework is grounded in the European Commission's **JLA**, which evaluates software 
     assets across six criteria categories: 
       * Can (Permissions)
       * Must (Obligations)
       * Cannot (Restrictions)
       * Compatible** (Interoperability)
       * Law (Jurisdiction)
       * Support(Governance)

Use this index to preview the demonstrated path for each scenario, or click any module link to jump 
directly to its detailed exercise, legal analysis, and JLA selection instructions.

| Scenario Module | Demonstrated Path / Focus | Compliant Target Licenses |
| :--- | :--- | :--- |
| [**1. Own Code**](#scenario-1) | 🟢 Permissive *(Default Choice)* | `MIT`, `Apache-2.0`, `BSD-3-Clause` |
| [**2. Implement an algorithm**](#scenario-2) | 🟡 Copyleft / Reciprocal | `EUPL-1.2`, `GPL-3.0`, `AGPL-3.0` |
| [**3. Embed Permissive**](#scenario-3) | 🟢 Permissive Focus *(Copyleft Flexible)* | `MIT`, `Apache-2.0`, `EUPL-1.2`, `GPL-3.0` |
| [**4. Embed Copyleft**](#scenario-4) | 🟡 Mandatory Copyleft | `EUPL-1.2`, `GPL-3.0` |
| [**5. Link GPL Library**](#scenario-5) | 🟡 Mandatory Copyleft | `GPL-3.0`, `EUPL-1.2` |
| [**6. Container Recipe**](#scenario-6) | 🟢 Permissive Focus | `MIT`, `Apache-2.0`, `BSD-3-Clause` |
| [**7. Built Image**](#scenario-7) | ⚠️ Multi-License Bundle | Governed by individual layer/binary terms |
| [**8. AI-Assisted Code**](#scenario-8) | 🟢 Permissive Focus *(Author Choice)* | `MIT`, `Apache-2.0`, `EUPL-1.2`, `GPL-3.0` |
| [**9. Prompt Chaining Architecture**](#scenario-9) | 🟢 Permissive Focus | `MIT`, `Apache-2.0` |

### Module 1: Clean Slate – Authoring Original Code & Algorithms

When writing original code or implementing published mathematical logic, you control 100% of your copyright.

(scenario-1)=
::::{exercise} Scenario 1: Authoring original code and algorithms
You wrote an original algorithm from scratch (in Python, C++, Rust, etc.). Your repository contains only your original source code and dependency specifications (`requirements.txt`, `CMakeLists.txt`, `Cargo.toml`).

* **Licensing Goal**: You want **maximum adoption** and zero friction for commercial or academic reuse.
* **Legal Reality**: External dependencies remain separate works. Because you have not bundled third-party code inside your repository, you hold full copyright over your original codebase.
* **JLA Selection Strategy**: To ensure downstream users must acknowledge your original authorship while granting them maximum flexibility to incorporate your code into both open and proprietary software, you require citation credit (`Incl. Copyright`) without imposing share-alike conditions (leaving `Copyleft/Share a.` unselected).

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute`, `Modify/merge`, and `Commercial use`
2. **Must Column**: Select `Incl. Copyright`
3. **Support Column**: Select `OSI approved`

* **Example JLA Matches**: `MIT`, `Apache-2.0`, `BSD-3-Clause`

* **Permissive vs. Public Domain (EU Civil Law Nuance)**: Public domain dedications (e.g., `CC0`, `Unlicense`) attempt to give away all rights. However, under EU civil law, authors cannot legally give up their moral rights (*droit moral*). Selecting an explicit permissive license like `MIT` or `Apache-2.0` grants broad permissions globally, remains legally valid under European copyright law, and guarantees academic citation credit.

* **Downstream Obligations**: Anyone who reuses, modifies, or integrates your code into their work must preserve your copyright notice and license text. They are not required to share their modifications or open-source their downstream projects.

* **Allowed Inbound Snippets**: If you want to include small third-party code snippets in your files, you can freely embed code licensed under **permissive terms** (e.g., MIT, BSD, Apache-2.0, 0BSD) or public domain waivers (CC0) without affecting your permissive license. However, embedding copyleft snippets (e.g., GPL, EUPL) will trigger reciprocal obligations, forcing your entire repository to be re-licensed under those copyleft terms.

* **In-File Identification (SPDX)**: Apply standard machine-readable SPDX identifier comments directly at the top of your scripts:

```python
# SPDX-License-Identifier: MIT
# Copyright (c) 2026 Author Name <author@institute.eu>

import numpy as np
```
:::
::::

(scenario-2)=
::::{exercise} Scenario 2: Implementing mathematical models with copyleft obligations
You developed a custom mathematical solver implementing algorithms from academic literature. You want to ensure that any downstream improvements, extensions, or modifications made by others remain open-source and are shared back with the scientific community.

* **Licensing Goal**: You want to enforce **reciprocity** (share-alike), preventing third parties from incorporating your algorithm into proprietary, closed-source software without sharing their modifications.
* **Legal Reality**: Mathematical concepts and formulas themselves are not copyrightable, but your specific code implementation is fully protected by copyright. Applying a copyleft license legally binds anyone who distributes modified versions of your implementation to release their source code under matching reciprocal terms.
* **JLA Selection Strategy**: To enforce reciprocal sharing, you must mandate that downstream distributors disclose their modified source code (`Disclose source`) and license their adaptations or combined worrks under matching terms (`Copyleft/Share a.`).

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute`, `Modify/merge`, and `Commercial use`
2. **Must Column**: Select `Incl. Copyright`, `Disclose source`, and `Copyleft/Share a.`
3. **Support Column**: Select `OSI approved`

* **Example JLA Matches**: `EUPL-1.2`, `GPL-3.0`, `AGPL-3.0`

* **Copyleft Mechanics (EUPL vs. GPL Nuance)**: `GPL-3.0` is the standard global copyleft license, but `EUPL-1.2` is specifically tailored for European institutions. EUPL-1.2 is officially published in 23 EU language versions (each with equal legal validity), includes built-in compatibility clauses with GPL, and explicitly defaults to EU Member State jurisdiction and courts.

* **Downstream Obligations**: Anyone who distributes your code or a modified version of it must provide complete access to the corresponding source code under the same copyleft license and preserve your original copyright notices.

* **Allowed Inbound Snippets**: You can freely embed code snippets licensed under **permissive terms** (e.g., MIT, Apache-2.0, BSD) or public domain waivers (CC0). You may also embed snippets from compatible copyleft code (e.g., EUPL, GPL). However, you cannot embed closed-source or proprietary code snippets.

* **In-File Identification (SPDX)**: Apply standard machine-readable SPDX identifier comments directly at the top of your scripts:

```python
# SPDX-License-Identifier: EUPL-1.2
# Copyright (c) 2026 Author Name <author@institute.eu>

import numpy as np
```
:::
::::

## Module 2: The Dependency Minefield – Inbound Code & Linking

Embedding third-party source code snippets or linking against strong copyleft libraries 
introduces legal boundaries that restrict your repository choices.

(scenario-3)=
::::{exercise} Scenario 3: Embedding permissively licensed third-party code
You are building an RSE tool and copied a helper function or utility snippet from a third-party project licensed under a permissive license (e.g., MIT or Apache-2.0) directly into one of your source files.

* **Licensing Goal**: You want to maintain a **permissive default** for your project while properly acknowledging and legally respecting the embedded third-party code.
* **Legal Reality**: Permissive licenses explicitly grant you permission to copy, modify, and embed their code into your repository. However, embedding permissive code does not make the original third-party copyright disappear, you must preserve the original copyright attribution and license terms for that specific snippet.
* **JLA Selection Strategy**: Because inbound permissive code gives you maximum licensing flexibility, your overall repository can remain permissively licensed. To reflect this, select citation obligations (`Incl. Copyright`) without imposing reciprocal sharing constraints (leaving `Copyleft/Share a.` unselected).

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute`, `Modify/merge`, and `Commercial use`
2. **Must Column**: Select `Incl. Copyright`
3. **Support Column**: Select `OSI approved`

* **Example JLA Matches**: `MIT`, `Apache-2.0`, `BSD-3-Clause`

* **Notice Preservation Nuance**: Permissive licenses are flexible, but they are not license-free. If you copy code from an Apache-2.0 or BSD-3-Clause project into your MIT-licensed repository, you must retain the original author's copyright statement and license identifier directly above the embedded code block.

* **Downstream Obligations**: Downstream users receive your project under your primary permissive license (e.g., MIT), but they must preserve both your overall copyright notice and the specific third-party notices attached to embedded snippets.

* **Allowed Inbound Snippets**: In addition to the embedded permissive snippet, you can freely embed other permissively licensed code (MIT, BSD, Apache-2.0) or public domain waivers (CC0). You cannot embed copyleft code (e.g., GPL, EUPL) without upgrading your entire repository's license to match that copyleft license.

* **In-File Identification (SPDX)**: Mark both your overall file license and the specific embedded snippet using SPDX comments:

```python
# SPDX-License-Identifier: MIT
# Copyright (c) 2026 Author Name <author@institute.eu>

# --- Embedded Third-Party Snippet ---
# SPDX-License-Identifier: Apache-2.0
# Copyright (c) 2024 External Contributor <dev@external-lib.org>
def fast_matrix_solver(matrix):
    # Embedded algorithm implementation
    return np.linalg.solve(matrix, np.eye(len(matrix)))
# --- End Embedded Snippet ---

def main():
    pass
```
:::
::::

(scenario-4)=
::::{exercise} Scenario 4: Embedding copyleft third-party code
You are building an software tool and copied a non-trivial code snippet from a third-party project licensed under a copyleft license (e.g., GPL-3.0 or EUPL-1.2) directly into one of your source files.

* **Licensing Goal**: Comply with legal requirements imposed by the inbound copyleft code while ensuring your overall repository remains legally compliant.
* **Legal Reality**: Copyleft licenses require that any work containing copyleft code must be shared under a compatible copyleft license as a whole. Embedding copyleft code directly into your repository creates a single combined work, making copyleft licensing mandatory for your entire project.
* **JLA Selection Strategy**: Because the inbound copyleft code forces your repository to adopt reciprocal sharing terms, you must configure JLA to require source code disclosure (`Disclose source`) and reciprocal licensing (`Copyleft/Share a.`).

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute`, `Modify/merge`, and `Commercial use`
2. **Must Column**: Select `Incl. Copyright`, `Disclose source`, and `Copyleft/Share a.`
3. **Support Column**: Select `OSI approved`

* **Example JLA Matches**: `GPL-3.0`, `EUPL-1.2`

* **Copyleft Scope & EUPL Compatibility (Legal Nuance)**: Directly copying copyleft code into your source files extends the copyleft obligation to your entire codebase. If the embedded snippet is `EUPL-1.2`, its built-in compatibility provisions allow you to license your combined project under `GPL-3.0` if your project ecosystem requires it, resolving license conflicts without violating EUPL terms.

* **Downstream Obligations**: Anyone who receives, modifies, or distributes your repository must receive full access to the source code under the same copyleft license terms (`GPL-3.0` or `EUPL-1.2`) and preserve all copyright notices.

* **Allowed Inbound Snippets**: Because your overall repository is now governed by a copyleft license, you can safely embed code from **permissive sources** (MIT, BSD, Apache-2.0, CC0) as well as **compatible copyleft sources**. You cannot embed proprietary, closed-source code or snippets from incompatible copyleft licenses.

* **In-File Identification (SPDX)**: Mark your overall file license and clearly cite the embedded copyleft snippet using SPDX comments:

```python
# SPDX-License-Identifier: GPL-3.0-or-later
# Copyright (c) 2026 Author Name <author@institute.eu>

# --- Embedded Copyleft Snippet ---
# SPDX-License-Identifier: GPL-3.0-or-later
# Copyright (c) 2023 External Researcher <researcher@university.org>
def optimized_fft_filter(data_signal):
    # Embedded copyleft algorithm implementation
    return np.fft.fft(data_signal)
# --- End Embedded Snippet ---

def main():
    pass
```
:::
::::

## Module 3: Dependency Linking & Packaging

When software incorporates external dependencies, whether by dynamic linking, static compiling, or bundling binaries into container images licensing obligations expand beyond your own written source code. This module covers how dependency boundaries, build automation scripts, and packaged container artifacts affect legal compliance under the Joinup Licensing Assistant (JLA) framework.

(scenario-5)=
::::{exercise} Scenario 5: Linking against a GPL-licensed library
You are developing an software application that imports or links against an external software library licensed under GPL-3.0 (e.g., importing a GPL Python package or linking a C/C++ static/shared library).

* **Licensing Goal**: Ensure legal compliance while using copyleft libraries as core dependencies in your software project.
* **Legal Reality**: Under mainstream copyright interpretation and the text of GPL-3.0, linking your code directly against a GPL library (whether statically or dynamically) creates a combined work. Consequently, the copyleft obligations of the external library extend to your entire repository.
* **JLA Selection Strategy**: Because linking to a GPL library requires your distributed project to be released under matching reciprocal terms, you must configure JLA to mandate source code disclosure (`Disclose source`) and reciprocal licensing (`Copyleft/Share a.`).

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute`, `Modify/merge`, and `Commercial use`
2. **Must Column**: Select `Incl. Copyright`, `Disclose source`, and `Copyleft/Share a.`
3. **Support Column**: Select `OSI approved`

* **Example JLA Matches**: `GPL-3.0`, `EUPL-1.2`

* **Linking Boundaries & License Selection (Legal Nuance)**: 
  * **Why GPL forces copyleft**: Linking against a standard `GPL-3.0` library extends copyleft to your entire project. Your repository must adopt a compatible copyleft license (`GPL-3.0` or `EUPL-1.2`, which explicitly lists GPL-3.0 in its compatibility appendix).
  * **Why LGPL or EUPL-1.2 libraries allow permissive licenses**: If the external library is licensed under `LGPL` (which includes an explicit linking exception) or `EUPL-1.2` (where European Commission guidance takes the position that dynamically linking an EUPL work through its API does not by itself create a adaptation work), copyleft does not extend to your application. In these dynamic linking scenarios, your own project can stay **permissively licensed** (e.g., MIT, Apache-2.0, BSD). However, note that this EUPL stance reflects Commission guidance rather than settled CJEU case law, and static linking or direct code incorporation continues to trigger EUPL copyleft obligations.

* **Downstream Obligations**: Downstream users who receive or run your application must receive full access to your source code under `GPL-3.0` (or `EUPL-1.2`), along with all upstream copyright notices and build scripts required to recompile the project.

* **Allowed Inbound Code & Dependencies**: Your project can import or include other **permissively licensed** packages (MIT, BSD, Apache-2.0) and public domain waivers (CC0). However, all code linked together in the final executable or runtime environment must satisfy GPL compatibility.

* **In-File Identification (SPDX)**: Apply standard machine-readable SPDX identifier comments directly at the top of your main scripts:

```python
# SPDX-License-Identifier: GPL-3.0-or-later
# Copyright (c) 2026 Author Name <author@institute.eu>

import gpl_licensed_solver  # External GPL dependency forces GPL/EUPL compliance

def solve_system(data):
    return gpl_licensed_solver.compute(data)
```
:::
::::


(scenario-6)=
::::{exercise} Scenario 6: Authoring container recipes and environment specifications
You are creating a `Dockerfile`, Conda `environment.yml`, or build recipe to automate the setup of your research environment. The recipe itself contains setup instructions, shell commands, and package lists.

* **Licensing Goal**: You want **maximum adoption** and reuse of your build automation script so other researchers can freely adapt and build upon your workflow.
* **Legal Reality**: Build recipes and configuration scripts are plain-text source code separate from the software binaries they download at execution time. You hold copyright over the unique build instructions you write in the Dockerfile.
* **JLA Selection Strategy**: To allow anyone to reuse or adapt your container recipe without restrictions, you require citation credit (`Incl. Copyright`) while leaving reciprocal requirements (`Copyleft/Share a.`) unselected.

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute`, `Modify/merge`, and `Commercial use`
2. **Must Column**: Select `Incl. Copyright`
3. **Support Column**: Select `OSI approved`

* **Example JLA Matches**: `MIT`, `Apache-2.0`, `BSD-3-Clause`

* **Recipe vs. Image Nuance**: The license applied to a `Dockerfile` covers only the recipe instructions, not the software packages installed inside the container when `docker build` runs. A permissively licensed Dockerfile can install both permissive and copyleft packages without legal conflict.

* **Downstream Obligations**: Anyone who reuses or adapts your build recipe must preserve your original copyright notice in the header of the recipe file.

* **Allowed Inbound Snippets**: You can freely include build commands and code snippets from permissively licensed build scripts or public domain code. 

* **In-File Identification (SPDX)**: Place SPDX identifier comments at the top of your Dockerfile or recipe file:

```dockerfile
# SPDX-License-Identifier: MIT
# Copyright (c) 2026 Author Name <author@institute.eu>

FROM ubuntu:24.04
RUN apt-get update && apt-get install -y python3 python3-pip
COPY solver.py /app/solver.py
```
:::
::::

---

(scenario-7)=
::::{exercise} Scenario 7: Distributing pre-built container images
You compiled and published a pre-built container image (e.g., pushing a compiled Docker image to Docker Hub, GitHub Container Registry, or an institutional registry) containing an OS layer, runtime binaries, dependencies, and your application code.

* **Licensing Goal**: Safely distribute compiled container images without violating the license terms of any software layer or binary included inside the image.
* **Legal Reality**: A compiled container image is a **multi-license aggregate bundle**. Distributing pre-built binaries triggers source-code distribution obligations for any copyleft software (e.g., Linux base packages, coreutils, GPL libraries) pre-installed inside the image layers.
* **JLA Selection Strategy**: Because a container image combines multiple distinct software components, JLA is used to evaluate constituent component obligations. When distributing compiled binaries containing copyleft layers, source disclosure requirements (`Disclose source`) must be fulfilled for those specific layers.

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute` and `Commercial use`
2. **Must Column**: Select `Incl. Copyright` and `Disclose source`
3. **Support Column**: Select `OSI approved`

* **Example JLA Matches**: `Multi-License Bundle` (Governed by constituent package terms)

* **Multi-License Aggregation Nuance**: Applying a permissive license (like MIT) to your application code inside the container does not override or erase the GPL/LGPL obligations of base system packages installed in `/usr/lib` or `/usr/bin`. Distributing the built image binary makes you a distributor of all installed packages.

* **Downstream Obligations**: You must ensure that downstream users can obtain the source code for copyleft components shipped inside the image, typically by publishing the `Dockerfile` and build steps used to generate the image from public upstream sources.

* **Allowed Inbound Packages**: Before publishing an image binary, run automated compliance scanning tools (e.g., Syft, Trivy) to generate a Software Bill of Materials (SBOM) and verify that no non-redistributable or proprietary software is packaged inside.

* **In-File Identification (Metadata Annotations)**: Document the multi-license nature of the aggregate bundle using standard OCI (Open Container Initiative) image labels inside your Dockerfile:

```dockerfile
# SPDX-License-Identifier: MIT
# Copyright (c) 2026 Author Name <author@institute.eu>

FROM ubuntu:24.04
LABEL org.opencontainers.image.authors="author@institute.eu"
# OCI Standard Image Annotations for Docker Hub Compliance
LABEL org.opencontainers.image.title="My Research Pipeline"
LABEL org.opencontainers.image.licenses="MIT AND GPL-3.0-or-later"
LABEL org.opencontainers.image.vendor="My Institute Name"
LABEL org.opencontainers.image.description="Includes Ubuntu 24.04 base layers (GPL/LGPL) and custom solver (MIT)"

COPY solver.py /app/solver.py
```
:::
::::

## Module 4: Emerging Workflows & AI

AI-assisted development tools and machine learning models introduce unique legal challenges regarding copyright ownership, training data memorization, and behavioral restrictions. This module addresses how to license projects built with AI code generation tools and how to package research software that bundles AI models, weights, and datasets alongside source code.

---

(scenario-8)=
::::{exercise} Scenario 8: AI-assisted code generation
You used AI tools (e.g., GitHub Copilot, ChatGPT, Claude) to write functions, unit tests, or documentation for your research software repository.

* **Licensing Goal**: Retain clear ownership and apply a **permissive license** (`MIT` or `Apache-2.0`) to your repository without incurring hidden copyright infringement or copyleft obligations from code embedded during model training.
* **Legal Reality**: Unmodified AI-generated outputs lack human authorship and are generally not eligible for copyright protection under current EU and international legal standards. However, if an LLM reproduces a substantial copyrighted code snippet verbatim from its training data (memorization), that output snippet retains its original copyright and license obligations.
* **JLA Selection Strategy**: To ensure maximum adoption and academic reuse for your overall codebase, require citation credit (`Incl. Copyright`) while avoiding share-alike constraints (leaving `Copyleft/Share a.` unselected), supported by automated compliance checks.

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute`, `Modify/merge`, and `Commercial use`
2. **Must Column**: Select `Incl. Copyright`
3. **Support Column**: Select `OSI approved`

* **Example JLA Matches**: `MIT`, `Apache-2.0`, `BSD-3-Clause`

* **AI Code Generation & Verification Nuance**: Because non-human AI output cannot hold copyright, your copyright applies to the overall project structure, human-written logic, and creative choices. To protect your repository against accidental copyright infringement or copyleft contamination from AI memorization, turn on public code matching filters in your AI tools and run automated code-similarity scanners before releasing your repository.

* **Downstream Obligations**: Downstream users must preserve your copyright notice for the repository. They are free to reuse, modify, and integrate your code into commercial or open-source projects.

* **Allowed Inbound Snippets**: You can include permissively licensed code, public domain code (CC0), and AI-generated snippets that have been verified against verbatim training data duplication.

* **In-File Identification (SPDX)**: Apply standard machine-readable SPDX identifier comments directly at the top of your scripts:

```python
# SPDX-License-Identifier: MIT
# Copyright (c) 2026 Author Name <author@institute.eu>

def filter_sensor_data(raw_readings: list[float]) -> list[float]:
    """Cleans raw sensor data (written with AI assistance and human review)."""
    return [reading for reading in raw_readings if reading > 0.0]
```
:::
::::

---

(scenario-9)=
::::{exercise} Scenario 9: Packaging AI workflows, datasets, and model weights
You are developing research software that includes source code alongside trained machine learning model weights (`.pt`, `.safetensors`) and benchmark datasets.

* **Licensing Goal**: Apply a clear **dual-licensing strategy** that makes both the software source code and the non-code assets (data, weights) open and reusable under appropriate legal frameworks.
* **Legal Reality**: Standard open-source software licenses (MIT, GPL) are written specifically for source code and are legally ill-suited for datasets or neural network parameters. Under EU legal frameworks, datasets and model weights are governed by database rights (*sui generis* database protection) rather than traditional code copyright.
* **JLA Selection Strategy**: Use JLA to select an OSI-approved open-source license for the executable code component (`Incl. Copyright` selected), while using Creative Commons licenses (e.g., `CC-BY-4.0` or `CC0`) for the dataset and weight files.

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute`, `Modify/merge`, and `Commercial use`
2. **Must Column**: Select `Incl. Copyright`
3. **Support Column**: Select `OSI approved`

* **Example JLA Matches**: `MIT`, `Apache-2.0` (for the code component)

* **Code vs. Data/Weights & OpenRAIL Nuance**: Never apply software licenses like GPL or MIT to raw datasets or model weights. Use **CC-BY-4.0** or **CC0** for non-code assets. Additionally, behavioral licenses (such as OpenRAIL) impose usage restrictions (e.g., prohibiting specific harmful uses), which means they do **not** qualify as OSI-approved open-source software and cannot be filtered via standard JLA open-source queries.

* **Downstream Obligations**: Downstream users must cite your repository for the code (under your chosen software license) and give credit for the model weights and data under the corresponding Creative Commons license.

* **Allowed Inbound Assets**: You may combine permissively licensed python code with CC-BY-4.0 datasets or open-weight models, provided the attribution files clearly separate code licenses from data/weight licenses.

* **In-File Identification (SPDX / Dual-Licensing Structure)**: Document the dual-licensing scheme in your root repository structure and script headers:

```python
# SPDX-License-Identifier: MIT
# Copyright (c) 2026 Author Name <author@institute.eu>
#
# Note: Source code is licensed under MIT.
# Model weights in /models/ and datasets in /data/ are licensed under CC-BY-4.0.

import torch

def load_pipeline():
    model = torch.load("models/climate_weights.safetensors")
    return model
```
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


### 2. Documenting License Status in `README.md`

Add a dedicated **License** section near the bottom of your repository's `README.md` file, along with a machine-readable badge:

```markdown
## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
```


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

When developing research software, license compliance is not an afterthought to debug at the end of a project, it is a proactive design choice. By using the **Joinup Licensing Assistant (JLA)** framework to align your repository license with your inbound dependencies from day one, your CI/CD pipeline passes cleanly on the first run.

The diagram below illustrates how selecting a compatible license upfront ensures your code passes automated compliance checks and results in a legally sound release:

```{mermaid}

%%{init: {'themeVariables': { 'edgeLabelBackground': '#faf5ff' }}}%%
flowchart TB

    subgraph local["1. Local Authoring & Standardization"]
        A["<b>Inbound Reuse Trigger:</b><br/>User copies copyleft snippet <i>(Scenario 4)</i><br/>or links GPL library <i>(Scenario 5)</i>"] --> B["<b>JLA Selection Strategy:</b><br/>Select compatible copyleft license<br/><i>(GPL-3.0 / EUPL-1.2)</i>"]
        
        B --> C["<b>Standardize Local Codebase:</b><br/>1. Add <b>SPDX Headers</b> to all files <i>(Scenarios 1-9)</i><br/>2. Add root <code>LICENSE</code> file & README badge"]
    end

    subgraph cicd["2. Automated CI/CD & Verification"]
        C -->|"<b>Git Push</b> to Repository"| D["<b>Build Trigger: Run Compliance Scanner</b><br/><i>(Executes <code>reuse lint</code> in CI/CD)</i>"]
        
        D --> E{"<b>Verify Inbound vs.<br/>Outbound Terms</b>"}
        
        E -->|"SPDX Headers & License Match Confirmed!"| F["✅ <b>BUILD PASSES</b><br/>Compliance verified automatically"]
        
        F --> SUCCESS["🎉 <b>COMPLIANT OPEN-SOURCE RELEASE</b><br/>Legally sound, reproducible & ready for scientific reuse"]
    end

    classDef pass fill:#e6ffe6,stroke:#2b8a3e,stroke-width:2px,color:#1b4332;
    classDef neutral fill:#f8f9fa,stroke:#495057,stroke-width:2px,color:#212529;
    classDef box_fill fill:#ffffff,stroke:#adb5bd,stroke-width:1px;

    class F,SUCCESS pass;
    class A,B,C,D,E neutral;
    class local,cicd box_fill;
```


### Scenario Mapping Across the Pipeline

* **Handling Inbound Copyleft ([Scenario 4](#scenario-4) & [Scenario 5](#scenario-5))**: When you copy non-trivial copyleft code snippets (e.g., CC BY-SA from Stack Overflow or GPL snippets) or link directly against a GPL library, your overall project becomes a combined work. Selecting a compatible copyleft license upfront (`GPL-3.0` or `EUPL-1.2`) satisfies the reciprocal sharing terms and allows the pipeline scanner to pass without conflict.
* **Maintaining Permissive Defaults ([Scenario 1](#scenario-1) & [Scenario 3](#scenario-3))**: If you write original code or embed only permissively licensed snippets (MIT, Apache-2.0, BSD), selecting a permissive license (`MIT` or `Apache-2.0`) grants downstream users maximum adoption freedom while preserving your citation credit.
* **Packaging and Build Automation ([Scenario 6](#scenario-6) & [Scenario 7](#scenario-7))**: Keep plain-text build recipes (Dockerfiles) permissively licensed for maximum reuse, while annotating compiled container image binaries as multi-license aggregate bundles to satisfy embedded base-layer obligations.
* **AI Assets and Dual-Licensing ([Scenario 8](#scenario-8) & [Scenario 9](#scenario-9))**: Run code-similarity scanners to catch LLM training memorization before releasing AI-assisted code, and apply dual-licensing to separate executable software code (`MIT`) from non-code datasets and model weights (`CC-BY-4.0`).
* **Standardized Distribution**: By adding machine-readable **SPDX headers** across every script, Dockerfile, and prompt template, running `reuse lint` in your pipeline confirms 100% legal clarity for the entire scientific community.<S-Del>
