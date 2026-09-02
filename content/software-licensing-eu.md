# Software licensing

```{objectives}
 - Objective 1
```

```{discussion} Limitations and context of this lesson 

This lesson is designed as practical educational material for researchers and research software engineers, not formal legal advice.

* Regional Focus: Guidance is grounded in European Union directives and Nordic institutional frameworks.
* Institutional Context: Employment contracts, grant agreements, and university policies heavily influence software ownership and licensing choices.
* Scope: This lesson covers general principles of open-source reuse, copyright scope, and software adaptation. 

If you need formal guidance reference below could be used:

* [Directive 2009/24/EC of the European Parliament and of the Council](https://eur-lex.europa.eu/eli/dir/2009/24)
* [Joinup Licensing Assistant,JLA](https://joinup.ec.europa.eu/collection/eupl/solution/joinup-licensing-assistant/jla-find-and-compare-software-licenses)
* [FSFE REUSE Initiative](https://reuse.software/)
* [Research Software Alliance Policy Directory](https://www.researchsoft.org/software-policies/)
```

## Introduction 

- What parts of computer programs are protected by copyright
    - Protected: Specific text and expression of a program in any form, including preparatory design work
    - Not protected: Underlying ideas, mathematical algorithms, logic, and interface principles.

## Difference in terminology in the US regulative text and EU regulation 2009/24/EC
 
### 1. Modified Code & Works
* **US Concept**: **Derivative Work** (broadly defined in the US Copyright Act).
* **EU Concept**: **Adaptation**, translation, arrangement, or alteration (Directive 2009/24/EC Art. 4(1)(b)).
* **Practical Impact**: EU law avoids the term "derivative work." Any code modifications are classified as specific statutory acts of adaptation or translation.

### 2. User Rights & Exceptions
* **US Concept**: **Fair Use** (flexible judicial doctrine evaluated case-by-case in court).
* **EU Concept**: **Statutory Exceptions** (strictly codified rights, such as error correction under Art. 5(1) or decompilation for interoperability under Art. 6).
* **Practical Impact**: EU user rights are fixed by statute and cannot be overridden by contract, avoiding reliance on judicial interpretation.

### 3. Waiver of Rights
* **US Concept**: **Public Domain Dedication** (authors can fully surrender economic and moral rights).
* **EU Concept**: **Economic Rights Transfer / Non-Waivable Moral Rights**.
* **Practical Impact**: European legal traditions do not allow full waiver of moral rights (e.g., right to attribution), requiring permissive open licenses rather than pure public domain dedications.

### 4. Work Ownership in Employment
* **US Concept**: **Work Made for Hire** (the employer is legally recognized as the primary author).
* **EU Concept**: **Employer Economic Rights** (Directive 2009/24/EC Art. 2(3)).
* **Practical Impact**: The individual developer remains the author, but all economic rights automatically transfer to the employer for code created during employment duties.

### 5. Non-Protectable Elements
* **US Concept**: **Idea-Expression Dichotomy** (established primarily through court case law).
* **EU Concept**: **Expression vs. Ideas, Principles, & Interfaces** (explicitly codified under Directive 2009/24/EC Art. 1(2)).
* **Practical Impact**: EU statutory law explicitly excludes algorithms, programming languages, logic, and interface principles from copyright protection. 


## Claisfication of licenses related to software

```{mermaid}
   flowchart TB
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
       subgraph osi["Open Source Initiative (OSI)"]
           osi_H["👉 Some exceptions exists"]
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
       class osi_H,osi osiBox;

```

::::{exercise} Scenario 1: Own algorithm with external dependencies
You wrote an original algorithm from scratch (in Python, C++, Rust, etc.). Your repository contains only your original source code and dependency specifications (`requirements.txt`, `CMakeLists.txt`, `Cargo.toml`, or dynamic linking flags).

* **Licensing Goal**: You want **maximum adoption** and zero friction for commercial or academic reuse.

[Licensing Assistant](https://interoperable-europe.ec.europa.eu/collection/eupl/solution/licensing-assistant/find-and-compare-software-licenses) selection guide:

| 🟢 **Can** | ⚪ **Must** | 🟡 **Support** |
| :--- | :--- | :--- |
| ☑ Commercial use | ☑ Incl. Copyright | ☑ OSI approved |
| ☑ Modify/merge | | |
| ☑ Distribute | | |

:::{solution}
**Legal Reality**: External dependencies remain separate works. Because you have not bundled third-party code inside your repository, you hold full copyright over your original codebase.

* **Outcome**: **Fully Permissible.** You own the code and can choose any open-source license.
* **Selected Category**: **Permissive** (driven by your goal of maximum adoption).
* **JLA Expected Matches**: `MIT`, `Apache-2.0`, `BSD-3-Clause`
* **Why**: Filters select licenses granting maximum reuse while requiring only basic copyright attribution.
* **User Obligation**: Downstream users must comply with individual external package licenses when fetching, compiling, or running them.
* **Mixing & Redistribution**: Anyone can freely mix, embed, or redistribute your source code. If a user compiles and distributes a combined binary that dynamically links to a copyleft shared library (e.g., GPL `.so`), their *distributed binary* must comply with copyleft obligations, but your upstream source repository remains unaffected under your chosen permissive license.
:::
::::

::::{exercise} Scenario 2: Implementing an algorithm from a paper
You read a published scientific paper or technical specification, understand the underlying mathematical algorithm, and write your own original software implementation from scratch.

* **Licensing Goal**: You want **reciprocal protection** anyone can use your implementation, but any downstream modifications distributed by others must remain open source.

[Licensing Assistant](https://interoperable-europe.ec.europa.eu/collection/eupl/solution/licensing-assistant/find-and-compare-software-licenses) selection guide:

| 🟢 **Can** | ⚪ **Must** | 🔵 **Compatible** |
| :--- | :--- | :--- |
| ☑ Commercial use | ☑ Copyleft/Share a. | ☑ For software |
| ☑ Modify/merge | ☑ Disclose source | |
| ☑ Distribute | | |

:::{solution}
**Legal Reality**: Under EU Directive 2009/24/EC Art. 1(2), copyright protects specific source code *expression*, not underlying mathematical algorithms or scientific principles. Writing a fresh implementation creates a brand-new, independent copyright.

* **Outcome**: **Fully Permissible.** You own 100% of the copyright for your software implementation and can choose any open-source license.
* **Selected Category**: **Copyleft / Reciprocal** (driven by your goal of community protection).
* **JLA Expected Matches**: `EUPL-1.2`, `GPL-3.0`, `AGPL-3.0`
* **Why**: Selecting **"Copyleft/Share a."** and **"Disclose source"** filters out permissive licenses to isolate reciprocal terms.
* **User Obligation**: Users who redistribute your software or their modified versions must provide source code access under the same copyleft terms.
* **Mixing & Redistribution**: Anyone can use and modify your code. However, if a third party integrates your copyleft implementation into their software and distributes the combined product, their whole application must be released under a compatible open-source copyleft license.
:::
::::
