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

* EU directives set only minimum requirements in some areas: Member States implement them differently and may add national rules not covered here. For example, some Member States let university researchers retain ownership of the programs they write instead of applying the employer rule in Art. 2(3).
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

Under copyright law worldwide, software without an explicit license defaults to All Rights Reserved: nobody else may run, copy, modify, distribute, or build on your code. A software license is how the copyright holder exercises their exclusive rights, granting others permission to reproduce, distribute, modify, and sometimes sublicense the work.

Note that author and copyright holder may differ: under Art. 2(3), an employer exercises the economic rights in code written by an employee on the job, unless a contract says otherwise. The employee is still the author; the employer is who licenses it. This matters in practice, because the person choosing the license for a research project is often not the person who wrote the code.

In this lesson, we focus on open-source licenses to define both how we grant permissions for software we develop (outbound licensing) and how we safely comply with terms attached to code written by others (inbound reuse).

Open-source licenses fall into three main families:

* **Permissive (e.g., MIT, Apache-2.0, 0BSD):** *Do whatever you want, just keep credit.* Grants maximum reuse freedom, allowing anyone to modify, embed, or re-license your code in open or closed projects.

* **Copyleft / Reciprocal (e.g., GPL-3.0, EUPL-1.2):** *Share alike.* Grants full freedom to run and modify, but requires that any distributed adaptation or combined work also be released under matching copyleft terms.

* **Weak copyleft (e.g., LGPL-3.0, MPL-2.0, EPL-2.0):** *Share alike, but only within a boundary.* Reciprocity applies to the file (MPL-2.0) or the library (LGPL), not to your whole project. Your surrounding code can usually stay permissive or even closed, while modifications to the covered files or library must stay open.

You will hear copyleft called *viral* or *infectious* in developer conversation. The slang is worth knowing, but it is misleading in two ways: nothing spreads by mere contact, so code merely sitting beside GPL code in a repository or a container image is unaffected, and the requirement only triggers when you **distribute**, not when you run modified code internally. Reciprocity reaches only across specific technical boundaries such as embedding snippets or static linking, and how far it reaches depends on which copyleft license you are dealing with. Choosing copyleft over permissive is a project-level decision, not a sign that a license is harmful.

Weak copyleft is worth a closer look, because it is widely used and its terms are more conditional than the label suggests. LGPL-3.0 §4 lets you ship a combined work under your own terms only if those terms do not restrict modification of the LGPL portions, or reverse engineering for debugging those modifications, and this condition applies whether you linked statically or dynamically. Since most proprietary end-user licenses forbid reverse engineering, the common shorthand that "dynamic linking is safe" is not the whole story. The practical lesson is that "does this dependency force my project open?" has no general answer: it depends on which copyleft license, and at which boundary.

The diagram below unifies these license choices and their downstream rights:

```{mermaid}
%%{init: {'themeVariables': { 'edgeLabelBackground': '#faf5ff' }}}%%

flowchart TB

  subgraph box["How License Selection Governs Code Reuse"]
    A["<b>Your Research Codebase</b><br/><i>(Source code, container recipes, prompt templates)</i>"] -->|"No License Attached<br/>(Statutory Default)"| B["<b>All Rights Reserved</b><br/>❌ Zero permissions: Cannot run, modify, or share"]

    A -->|"Attach License<br/>(Explicit Permission Grant)"| C{"Select License"}

    C -->|"Goal: Maximum adoption & unrestricted reuse"| D["<b>Permissive</b><br/><i>MIT, Apache-2.0, 0BSD</i>"]
    C -->|"Goal: Keep the library open, allow closed users"| W["<b>Weak Copyleft</b><br/><i>LGPL-3.0, MPL-2.0, EPL-2.0</i>"]
    C -->|"Goal: Ensure changes stay open-source (Reciprocity)"| E["<b>Copyleft</b><br/><i>GPL-3.0, EUPL-1.2</i>"]
    C -->|"Goal: Proprietary control & restricted access"| F["<b>Closed Source / Restricted</b><br/>🚫 <i>Not discussed in this lesson</i>"]

    D --> D1["Run & Modify? <b>Yes</b>"]
    D --> D2["Embed in closed product? <b>Yes</b>"]
    D --> D3["Must changes stay open? <b>No</b> (optional)"]

    W --> W1["Run & Modify? <b>Yes</b>"]
    W --> W2["Embed in closed product? <b>Yes, with conditions</b>"]
    W --> W3["Must changes stay open? <b>Only the covered file or library</b>"]

    E --> E1["Run & Modify? <b>Yes</b>"]
    E --> E2["Embed in closed product? <b>No</b>"]
    E --> E3["Must changes stay open? <b>Yes</b> (mandatory)"]
  end

  G["<b>Reciprocity only triggers on distribution</b><br/>Running modified code internally creates no obligation"]
  E -.-> G
  W -.-> G

   classDef green fill:#e6ffe6,stroke:#2b8a3e,stroke-width:2px,color:#1b4332;
   classDef red fill:#ffe3e3,stroke:#e03131,stroke-width:2px,color:#5c0000;
   classDef yellow fill:#fff9db,stroke:#f59f00,stroke-width:2px,color:#5c3c00;
   classDef amber fill:#fff3bf,stroke:#f08c00,stroke-width:2px,color:#5c3c00;
   classDef white fill:#f8f9fa,stroke:#adb5bd,stroke-width:2px,color:#212529;
   classDef dashed fill:#f8f9fa,stroke:#adb5bd,stroke-width:2px,stroke-dasharray: 5 5,color:#000000;
   classDef dashed_red fill:#ffe3e3,stroke:#adb5bd,stroke-width:2px,stroke-dasharray: 5 5,color:#000000;
   classDef note fill:#ffffff,stroke:#868e96,stroke-width:1px,stroke-dasharray: 3 3,color:#212529;
   classDef box_fill fill:#ffffff,stroke:#adb5bd,stroke-width:1px;

   class D1,D2,D3,W1,E1 green;
   class W2,W3 amber;
   class E2 red;
   class E3 green;
   class D yellow;
   class W amber;
   class E yellow;
   class F dashed;
   class B dashed_red;
   class A,C white;
   class G note;
   class box box_fill;
```

### Copyright Foundation: Expression vs. Ideas

Under Directive 2009/24/EC, software is protected by copyright as a **literary work** (Art. 1(1)). But copyright protects only the **expression**, not the ideas beneath it: Art. 1(2) explicitly excludes "ideas and principles which underlie any element of a computer program, including those which underlie its interfaces."

* **Protected**: your specific source code text, binaries, container recipes, prompt text, and preparatory design material.
* **Not protected**: mathematical algorithms, scientific models, programming logic, data structures, and interfaces.

The CJEU confirmed this line in *SAS Institute v World Programming* (C-406/10): a program's functionality, its programming language, and its data file formats are ideas, not expression, and are therefore outside copyright. Someone may reimplement your algorithm from scratch; they may not copy your code. This is exactly why licenses exist — they set the terms for the expression, which is the only part copyright lets you control.

### Scope of this Lesson: What Counts as *Software*?

Across international frameworks (17 U.S.C. § 101 and WIPO model provisions), software is broadly defined as a set of statements or instructions used directly or indirectly in a computer to bring about a certain result. Research software goes well beyond Python scripts, so this lesson covers six asset types — find the ones matching your own project, since the scenarios later map onto them:

* **Source Code** — original algorithms, or implementations of published methods.
* **Third-Party Integrations** — embedded snippets and linked libraries (static or dynamic).
* **Infrastructure as Code** — Ansible playbooks, Terraform configs, container recipes (`Dockerfile`, Apptainer `.def`).
* **Container Images** — built binary snapshots (`.sif` files, OCI registry images).
* **AI-Assisted Code** — generated or refactored with human oversight.
* **AI Prompt Templates** — engineered system prompts meeting the threshold of human authorship.

## Motivation: Debugging a License Compliance Failure

With the three license families in mind, examine what happens when they collide inside an automated CI/CD pipeline:

```{mermaid}
%%{init: {'themeVariables': { 'edgeLabelBackground': '#faf5ff' }}}%%
flowchart TB

    subgraph box["CI/CD License Compliance Debugging Pipeline"]
        A["Paste a snippet copied from somewhere"] --> A2["<b>Build Trigger:</b> Push to my-code-base"]
        A2 --> B["Run Compliance Scanner"]
        B --> C{"Check Inbound vs.<br/>Outbound Terms"}

        C -->|"Target license: Permissive<br/>Pasted snippet: Copyleft"| D["❌ <b>BUILD FAILURE</b><br/>Pasted copyleft snippet blocks MIT release"]

        D --> E{"Select Patch Option"}

        E -->|"A: Keep MIT, add comment '# Originally GPL'"| F["❌ <b>BUILD FAIL</b><br/>Comments do not override license terms"]
        E -->|"B: Re-license repo to GPL-3.0 / EUPL-1.2"| G["✅ <b>BUILD PASS</b><br/>Your license now matches the snippet"]
        E -->|"C: Reimplement the functionality yourself"| H["✅ <b>BUILD PASS</b><br/>Your own expression, your own license"]
        E -->|"D: Delete LICENSE file to silence the scanner"| I["⚠️ <b>SCANNER PASSES — LEGAL TRAP</b><br/>Still infringing, and your own code reverts to All Rights Reserved"]

        P["<b>Permissive</b><br/>MIT, Apache-2.0, 0BSD"]
        WC["<b>Weak Copyleft</b><br/>LGPL, MPL-2.0, EPL-2.0"]
        CL["<b>Copyleft</b><br/>GPL-3.0, EUPL-1.2"]
    end

    P -.->|"What I want for my repo"| C
    CL -.->|"What the pasted snippet uses"| C
    WC -.->|"Would often have been fine"| C

    classDef pass fill:#e6ffe6,stroke:#2b8a3e,stroke-width:2px,color:#1b4332;
    classDef copyleft fill:#fff9db,stroke:#f59f00,stroke-width:2px,color:#5c3c00;
    classDef amber fill:#fff3bf,stroke:#f08c00,stroke-width:2px,color:#5c3c00;
    classDef fail fill:#ffe3e3,stroke:#e03131,stroke-width:2px,color:#5c0000;
    classDef warning fill:#fff3bf,stroke:#f08c00,stroke-width:2px,color:#5c0000;
    classDef neutral fill:#f8f9fa,stroke:#495057,stroke-width:2px,color:#212529;
    classDef box_fill fill:#ffffff,stroke:#adb5bd,stroke-width:1px;

    class P,G,H pass;
    class CL copyleft;
    class WC amber;
    class D,F fail;
    class I warning;
    class A,A2,B,C,E neutral;
    class box box_fill;
```

* Option D is the one worth dwelling on: deleting the `LICENSE` file makes the scanner quiet without changing anything legally. You are still distributing someone else's copyleft code without honouring its terms, and you have now stripped your own users of any permission to use your work. A green pipeline is not a compliance result.

* Option C works only if you genuinely reimplement the functionality without copying the original expression. As the idea/expression split above establishes, the algorithm is free to reuse — the specific code is not. Reading the original closely and retyping a close paraphrase is still copying.


## Limitations of AI-Assisted Licensing Advice

Modern software developers and RSEs routinely rely on AI coding assistants 
(ChatGPT, Claude, GitHub Copilot) to generate boilerplate, refactor functions, 
and answer project setup questions. 


However, using these tools for legal or licensing guidance introduces a subtle risk of **AI legal bias**. AI models are overwhelmingly trained on US-centric web data and legal forum posts, so their outputs default almost universally to **US common law concepts** such as *Fair Use*, *Work Made for Hire*, and *Derivative Works*.

Developers working under EU statutory frameworks face a different legal reality around exceptions, ownership, and code adaptation. The clearest example is the term you will hear constantly:

* **US law (17 U.S.C. § 101)** formally defines *"derivative work"*, and AI assistants reach for it to describe almost any code modification.
* **EU law (Directive 2009/24/EC, Art. 4(1)(b))** does not use that term at all. It grants exclusive rights over "the translation, adaptation, arrangement and any other alteration of a computer program" — governed collectively as an **adaptation**.
* **Licenses use it anyway**: `GPL-3.0` and `EUPL-1.2` define "derivative work" inside their own text as a contractual term for international enforceability, even though EU statute treats the act as an adaptation.

So when an AI assistant tells you a snippet creates a "derivative work", treat that as a prompt to check the actual question under EU law: is this a statutory **adaptation**, or a **combined work** across a technical boundary? The rest of this lesson gives you that EU-aligned framework.

## Standardizing In-File Declarations: SPDX Identifiers

Selecting a license is only half the job. Automated scanners and CI/CD pipelines need a machine-readable way to verify compliance per file without parsing legal text.

Managed by the Linux Foundation, **SPDX identifiers** are standardized short tags (`MIT`, `Apache-2.0`, `GPL-3.0-only`, `EUPL-1.2`) placed at the top of every source file:

```python
# SPDX-License-Identifier: MIT
# Copyright (c) 2026 Author Name <author@institute.eu>
```

Every scenario below shows the SPDX tagging for its asset type — Python scripts, container recipes, and prompt templates each have their own conventions.

## License Selection Decision Matrix & Scenario Index

Our decision framework is grounded in the European Commission's **[Joinup Licensing Assistant (JLA)](https://interoperable-europe.ec.europa.eu/collection/eupl/solution/licensing-assistant/find-and-compare-software-licenses)**, which sorts licenses across six criteria: **Can** (permissions), **Must** (obligations), **Cannot** (restrictions), **Compatible** (interoperability), **Law** (jurisdiction), and **Support** (governance).

The scenarios below are independent. Find the row that matches what you are actually building, jump to it, and skip the rest.

| If you are... | Scenario | Typical Outcome | Example Licenses |
| :--- | :--- | :--- | :--- |
| Writing everything yourself | [**1. Own code**](#scenario-1) | 🟢 Free choice | `MIT`, `Apache-2.0`, `BSD-3-Clause` |
| Implementing a published algorithm | [**2. Algorithm implementation**](#scenario-2) | 🟢 Free choice — copyleft if you want reciprocity | `EUPL-1.2`, `GPL-3.0`, `AGPL-3.0` |
| Pasting in a permissive snippet | [**3. Embed permissive**](#scenario-3) | 🟢 Stay permissive, keep notices | `MIT`, `Apache-2.0`, `EUPL-1.2`, `GPL-3.0` |
| Pasting in a copyleft snippet | [**4. Embed copyleft**](#scenario-4) | 🟡 Strong copyleft likely required | `EUPL-1.2`, `GPL-3.0` |
| Importing or linking a library | [**5. Link a library**](#scenario-5) | 🟡 Depends on which copyleft — see below | `GPL-3.0`, `EUPL-1.2`, or permissive if weak copyleft |
| Writing a Dockerfile or `.def` | [**6. Container recipe**](#scenario-6) | 🟢 Free choice | `MIT`, `Apache-2.0`, `BSD-3-Clause` |
| Publishing a built image | [**7. Built image**](#scenario-7) | ⚠️ Multi-license bundle | Governed by each layer's own terms |
| Using Copilot, ChatGPT or Claude | [**8. AI-assisted code**](#scenario-8) | 🟢 Free choice, verify for memorization | `MIT`, `Apache-2.0`, `EUPL-1.2`, `GPL-3.0` |
| Shipping prompts, weights or datasets | [**9. AI workflows & assets**](#scenario-9) | 🟢 Dual-license code vs. assets | `MIT` + `CC-BY-4.0` |

This lesson covers nine scenarios, a typical session works through three or four. The rest are here for reference when your project changes

## Module 1: Clean Slate – Authoring Original Code & Algorithms

When writing original code or implementing published algorithms, no third-party license constrains your choice — but who owns the code depends on your employment contract and national rules, so check your institution's policy first.

(scenario-1)=
::::{exercise} Scenario 1: Authoring original code and algorithms
You wrote an original algorithm from scratch (in Python, C++, Rust, etc.). Your repository contains only your original source code and dependency specifications (`requirements.txt`, `CMakeLists.txt`, `Cargo.toml`).

* **Licensing Goal**: You want **maximum adoption** and zero friction for commercial or academic reuse.
* **Legal Reality**: External dependencies remain separate works. Because you have not bundled third-party code inside your repository, no inbound license terms constrain your choice.
* **JLA Selection Strategy**: To ensure downstream users must acknowledge your original authorship while granting them maximum flexibility to incorporate your code into both open and proprietary software, you require citation credit (`Incl. Copyright`) without imposing share-alike conditions (leaving `Copyleft/Share a.` unselected).

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute`, `Modify/merge`, and `Commercial use`
2. **Must Column**: Select `Incl. Copyright`
3. **Support Column**: Select `OSI approved`

* **Example JLA Matches**: `MIT`, `Apache-2.0`, `BSD-3-Clause`

* **Permissive vs. Public Domain (EU Civil Law Nuance)**: Public domain dedications (e.g., `CC0`, `Unlicense`) attempt to give away all rights. However, under EU civil law, authors cannot legally give up their moral rights (*droit moral*). Selecting an explicit permissive license like `MIT` or `Apache-2.0` grants broad permissions globally, remains legally valid under European copyright law, and guarantees academic citation credit.

* **Downstream Obligations**: Anyone who reuses, modifies, or integrates your code into their work must preserve your copyright notice and license text. They are not required to share their modifications or open-source their downstream projects.

* **Allowed Inbound Snippets**: If you want to include small third-party code snippets in your files, you can freely embed code licensed under **permissive terms** (e.g., MIT, BSD, Apache-2.0, 0BSD) or public domain waivers (CC0) without affecting your permissive license. However, embedding copyleft snippets (e.g., GPL, EUPL) might trigger reciprocal obligations requiring you to re-license. Whether it does depends on which copyleft: weak copyleft (LGPL, MPL-2.0) often lets your surrounding code stay permissive, while strong copyleft generally does not.

* **In-File Identification (SPDX)**: Apply standard machine-readable SPDX identifier comments directly at the top of your scripts:

```python
# SPDX-License-Identifier: MIT
# Copyright (c) 2026 Author Name <author@institute.eu>

import numpy as np
```
:::
::::

(scenario-2)=
::::{exercise} Scenario 2: Choosing reciprocity for your own implementation
You developed a custom solver implementing algorithms from academic literature. You want any downstream improvements, extensions, or modifications to remain open-source and be shared back with the scientific community.

* **Licensing Goal**: You want to enforce **reciprocity** (share-alike), preventing third parties from incorporating your implementation into proprietary software without sharing their modifications.
* **Legal Reality**: The published algorithm itself is an unprotected idea — anyone may implement it independently, as Scenario 1 and the *SAS* ruling establish. What copyright protects is *your* specific implementation. Nothing about implementing a published method forces a particular license; copyleft here is your deliberate choice to bind downstream distributors to matching terms.
* **JLA Selection Strategy**: To enforce reciprocal sharing, you must mandate that downstream distributors disclose their modified source code (`Disclose source`) and license their adaptations or combined works under matching terms (`Copyleft/Share a.`).

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute`, `Modify/merge`, and `Commercial use`
2. **Must Column**: Select `Incl. Copyright`, `Disclose source`, and `Copyleft/Share a.`
3. **Support Column**: Select `OSI approved`

* **Example JLA Matches**: `EUPL-1.2`, `GPL-3.0`, `AGPL-3.0`

* **Copyleft Mechanics (EUPL vs. GPL Nuance)**: `GPL-3.0` is the standard global copyleft license, but `EUPL-1.2` is specifically tailored for European institutions. EUPL-1.2 is officially published in 23 EU language versions (each with equal legal validity), includes built-in compatibility clauses with GPL, and explicitly defaults to EU Member State jurisdiction and courts.
* **A caution before choosing strong copyleft**: reciprocity also limits who can combine with your code. Strong copyleft licenses are frequently incompatible with each other, so a future collaborator on a differently-licensed copyleft project may be unable to use your work at all. Scenario 5 covers this.
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

Embedding third-party snippets or linking against external libraries introduces boundaries that can constrain your license choice. How far those boundaries reach depends on which license the inbound code carries.

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

* **Notice Preservation Nuance**: Permissive licenses are flexible, but they are not license-free. If you copy code from an Apache-2.0 or BSD-3-Clause project into your MIT-licensed repository, you must retain the original author's copyright statement and license identifier directly above the embedded code block. Your repository license covers *your* code. It does not relicense the embedded snippet — that code stays under its original license and its original copyright holder's terms. You are distributing one file containing two separately licensed contributions, which is why both notices must appear.

* **Downstream Obligations**: Downstream users receive your project under your primary permissive license (e.g., MIT), but they must preserve both your overall copyright notice and the specific third-party notices attached to embedded snippets.

* **Allowed Inbound Snippets**: In addition to the embedded permissive snippet, you can freely embed other permissively licensed code (MIT, BSD, Apache-2.0) or public domain waivers (CC0).Embedding **strong** copyleft code (GPL, EUPL) generally requires re-licensing your repository to match. Weak copyleft (LGPL, MPL-2.0) applies at a narrower boundary and often does not

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
You are building a software tool and copied a non-trivial code snippet from a third-party project licensed under a copyleft license (e.g., GPL-3.0 or EUPL-1.2) directly into one of your source files.

* **Licensing Goal**: Comply with legal requirements imposed by the inbound copyleft code while ensuring your overall repository remains legally compliant.
* **Legal Reality**: Copying a non-trivial copyleft snippet into your source files creates a single combined work, so copyleft licensing generally extends to your whole project. "Non-trivial" matters: a snippet too short or purely functional to qualify as the author's own intellectual creation (Art. 1(3)) may not carry copyright at all. There is no word count or line count that draws this line — if you are unsure, assume it is protected and either comply or reimplement.
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
You are developing a software application that imports or links against an external software library licensed under GPL-3.0 (e.g., importing a GPL Python package or linking a C/C++ static/shared library).

* **Licensing Goal**: Ensure legal compliance while using copyleft libraries as core dependencies in your software project.
* **Legal Reality**: Whether linking creates a combined work is genuinely unsettled, and often has to be decided case by case. The FSF's position is that linking a GPL library — statically or dynamically — creates a combined work; some legal scholars and Commission EUPL guidance disagree, particularly for dynamic linking through a stable API. Most Member States have no case law on this, so no firm general rule can be stated. The guidance below follows the conservative, widely-adopted reading.
* **JLA Selection Strategy**: Because linking to a GPL library requires your distributed project to be released under matching reciprocal terms, you must configure JLA to mandate source code disclosure (`Disclose source`) and reciprocal licensing (`Copyleft/Share a.`).

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute`, `Modify/merge`, and `Commercial use`
2. **Must Column**: Select `Incl. Copyright`, `Disclose source`, and `Copyleft/Share a.`
3. **Support Column**: Select `OSI approved`

* **Example JLA Matches**: `GPL-3.0`, `EUPL-1.2`

* **Linking Boundaries & License Selection (Legal Nuance)**: 
  * **Why GPL forces copyleft**: Linking against a standard `GPL-3.0` library extends copyleft to your entire project. Your repository must adopt a compatible copyleft license (`GPL-3.0` or `EUPL-1.2`, which explicitly lists GPL-3.0 in its compatibility appendix).
* **Copyleft licenses are not compatible with each other**: two strong copyleft licenses can each demand that the combined work use *their* terms, which makes the combination undistributable. The classic trap is `GPL-2.0-only`: without the "or later" clause you cannot upgrade to GPL-3.0 to resolve a conflict, so GPL-2.0-only code cannot be combined with GPL-3.0 or Apache-2.0 code at all. Always check the exact SPDX identifier — `GPL-2.0-only` and `GPL-2.0-or-later` behave very differently.
* **Downstream Obligations**: Anyone to whom you **distribute** the application must receive full access to your source code under `GPL-3.0` (or `EUPL-1.2`), along with upstream copyright notices and the build scripts needed to recompile it. Running the software internally, without distributing it, creates no such obligation — though note that `AGPL-3.0` extends this to network use.

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
* **Legal Reality**: Build recipes and configuration scripts are plain-text source code, separate from the software binaries they download at build time. The build instructions you write are your expression — but note that a very short recipe (a `FROM` line plus two `RUN` commands) may be too trivial to meet the Art. 1(3) originality threshold and may not attract copyright at all. Longer, non-obvious recipes clearly do.
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
* **Legal Reality**: A compiled container image is a **multi-license aggregate bundle**, not a single combined work. Distributing pre-built binaries makes you a distributor of every package inside, so source-availability obligations apply to the copyleft components (Linux base packages, coreutils, GPL libraries). But those packages sitting in the same filesystem as your application do not make your application a derivative of them — this is mere aggregation. Your own code keeps whatever license you chose; you simply also carry distributor obligations for the copyleft software you are shipping alongside it.
* **JLA Selection Strategy**: Because a container image combines multiple distinct software components, JLA is used to evaluate constituent component obligations. When distributing compiled binaries containing copyleft layers, source disclosure requirements (`Disclose source`) must be fulfilled for those specific layers.

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute` and `Commercial use`
2. **Must Column**: Select `Incl. Copyright` and `Disclose source`
3. **Support Column**: Select `OSI approved`

* **JLA Outcome**: No single license applies. Use JLA per component to check each one's obligations, then record the aggregate in your image metadata.

* **Multi-License Aggregation Nuance**: Applying a permissive license (like MIT) to your application code inside the container does not override or erase the GPL/LGPL obligations of base system packages installed in `/usr/lib` or `/usr/bin`. Distributing the built image binary makes you a distributor of all installed packages.

* **Downstream Obligations**: You must ensure downstream users can obtain the corresponding source for the copyleft components you shipped. Publishing your `Dockerfile` documents the build but does not by itself satisfy this — the GPL asks for the source of the binaries actually distributed. In practice, most research images rely on unmodified upstream distribution packages, where pointing to the distributor's public source archives (as GPLv3 §6(d) permits) is the normal approach. If you modify or rebuild a copyleft component yourself, you must provide that source directly.

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

* **Marking AI-generated code**: Some projects and AI tool terms require contributors to disclose AI involvement — via a commit trailer, a PR checkbox, or an in-file comment. Even where it is optional, marking AI-assisted sections is increasingly recommended practice: it records provenance, signals to reviewers where extra scrutiny is warranted, and makes later authorship or infringement questions much easier to resolve. Check the contribution guidelines of any project you submit to.
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
* **Legal Reality**: Standard software licenses (MIT, GPL) are written for source code and fit datasets and model parameters poorly. Datasets may attract the EU *sui generis* database right where there has been substantial investment in obtaining, verifying, or presenting their contents. Model weights are a harder case: they are neither code nor a database, and whether they attract any copyright protection in the EU is genuinely unsettled. Because of this uncertainty, applying an explicit license to weights is about setting clear terms for your users, not about relying on a settled legal right.
* **JLA Selection Strategy**: Use JLA to select an OSI-approved open-source license for the executable code component (`Incl. Copyright` selected), while using Creative Commons licenses (e.g., `CC-BY-4.0` or `CC0`) for the dataset and weight files.

:::{solution}
**What to select in the JLA interface:**

1. **Can Column**: Select `Distribute`, `Modify/merge`, and `Commercial use`
2. **Must Column**: Select `Incl. Copyright`
3. **Support Column**: Select `OSI approved`

* **Example JLA Matches**: `MIT`, `Apache-2.0` (for the code component)

* **Code vs. Data/Weights & OpenRAIL Nuance**: Avoid applying software licenses like GPL or MIT to raw datasets or model weights — their terms reference source code, object code, and linking, which leaves users guessing about what applies. Use **CC-BY-4.0** or **CC0** for non-code assets instead. Note also that behavioral licenses (such as OpenRAIL) impose usage restrictions (e.g., prohibiting specific harmful uses), so they do **not** qualify as OSI-approved open source and will not appear in standard JLA queries.

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

Once you have selected a license using the JLA, you must officially attach it to your repository so automated scanners, package registries, and downstream users can verify your terms.


### 1. Adding the Root `LICENSE` File

Always place the full text of your chosen license in a plain-text file named `LICENSE` or `LICENSE.txt` at the root of your repository.

* **Exact Legal Text**: Copy the standard text directly from [spdx.org/licenses](https://spdx.org/licenses/) or [choosealicense.com](https://choosealicense.com/).
* **Copyright Header**: Ensure you fill in the copyright year and copyright holder line at the top of the license text:
  ```text
  Copyright (c) 2026 [Author Name or Institution Name]
  ```
* **Do Not Edit Terms**: Never modify the legal wording of standard licenses (e.g., removing clauses from GPL or MIT). Edited texts are no longer the license they claim to be: compliance scanners cannot classify them, package registries may flag them, and downstream users have to get their own legal review before touching your code. If a standard license does not fit, pick a different standard license.

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
* **Handling Inbound Copyleft ([Scenario 4](#scenario-4) & [Scenario 5](#scenario-5))**: Copying a non-trivial copyleft snippet (e.g., CC BY-SA code from Stack Overflow, or a GPL fragment) creates a combined work. Linking against a copyleft library may do the same, depending on the license and the linking method. In both cases, selecting a compatible copyleft license upfront (`GPL-3.0` or `EUPL-1.2`) satisfies the reciprocal terms and lets the scanner pass — and checking the exact SPDX identifier first avoids the `GPL-2.0-only` incompatibility trap.
* **Packaging and Build Automation ([Scenario 6](#scenario-6) & [Scenario 7](#scenario-7))**: Keep plain-text build recipes (Dockerfiles) permissively licensed for maximum reuse, while annotating compiled container image binaries as multi-license aggregate bundles to satisfy embedded base-layer obligations.
* **AI Assets and Dual-Licensing ([Scenario 8](#scenario-8) & [Scenario 9](#scenario-9))**: Run code-similarity scanners to catch LLM training memorization before releasing AI-assisted code, and apply dual-licensing to separate executable software code (`MIT`) from non-code datasets and model weights (`CC-BY-4.0`).
* **Standardized Distribution**: Adding machine-readable **SPDX headers** across every script, Dockerfile, and prompt template lets `reuse lint` confirm that every asset has a declared, documented license. Note what this does and does not prove: the linter verifies that declarations exist and are well-formed, not that they are legally correct or mutually compatible. Automation makes your intent auditable — it does not replace the judgment calls in the scenarios above.
