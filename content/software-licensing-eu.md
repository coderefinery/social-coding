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

| 🟢 **Can** | ⚪ **Must** | 🔵 **Compatible** | 🟡 **Support** |
| :--- | :--- | :--- | :--- |
| ☑ Commercial use | ☑ Incl. Copyright | ☑ For software | ☑ OSI approved |
| ☑ Modify/merge | | | |
| ☑ Distribute | | | |

:::{solution}
**Legal Reality**: External dependencies remain separate works. Because you have not bundled third-party code inside your repository, you hold full copyright over your original codebase.

* **Outcome**: **Fully Permissible.** You own the code and can choose any open-source license.
* **Selected Category**: **Permissive** (driven by our goal of maximum adoption).
* **JLA Expected Matches**: `MIT`, `Apache-2.0`, `BSD-3-Clause`
* **Why**: The filters select licenses granting maximum reuse while requiring only basic copyright attribution (`Incl. Copyright`).
* **User Obligation**: Downstream users must comply with individual external package licenses when fetching, compiling, or running them.
* **Mixing & Redistribution**: Anyone can freely mix, embed, or redistribute your source code. If a user compiles and distributes a combined **binary** that dynamically links to a copyleft shared library (e.g., GPL `.so`), their *distributed binary* must comply with copyleft obligations, but your upstream source repository remains unaffected under your chosen permissive license.
:::
::::

::::{exercise} Scenario 2: Implementing an algorithm from a paper
You read a published scientific paper or technical specification, understand the underlying mathematical algorithm, and write your own original software implementation from scratch.

* **Licensing Goal**: You want **reciprocal protection** anyone can use your implementation, but any downstream modifications distributed by others must remain open source.

[Licensing Assistant](https://interoperable-europe.ec.europa.eu/collection/eupl/solution/licensing-assistant/find-and-compare-software-licenses) selection guide:

| 🟢 **Can** | ⚪ **Must** | 🔵 **Compatible** | 🟡 **Support** |
| :--- | :--- | :--- | :--- |
| ☑ Commercial use | ☑ Copyleft/Share a. | ☑ For software | ☑ OSI approved |
| ☑ Modify/merge | ☑ Disclose source | | |
| ☑ Distribute | | | |

:::{solution}
**Legal Reality**: Under EU Directive 2009/24/EC Art. 1(2), copyright protects specific source code *expression*, not underlying mathematical algorithms or scientific principles. Writing a fresh implementation creates a brand-new, independent copyright.

* **Outcome**: **Fully Permissible.** You own 100% of the copyright for your software implementation and can choose any open-source license.
* **Selected Category**: **Copyleft / Reciprocal** (driven by your goal of community protection).
* **JLA Expected Matches**: `EUPL-1.2`, `GPL-3.0`, `AGPL-3.0`
* **Why**: Adding **`Copyleft/Share a.`** and **`Disclose source`** under the **Must** column isolates reciprocal terms while leaving all other baseline criteria identical.
* **User Obligation**: Users who redistribute your software or their modified versions must provide source code access under the same copyleft terms.
* **Mixing & Redistribution**: Anyone can use and modify your code. However, if a third party integrates your copyleft implementation into their software and distributes the combined product, their whole application must be released under a compatible open-source copyleft license.
:::
::::

::::{exercise} Scenario 3: Directly embedding third-party Copyleft source code
You find a useful utility function or module online licensed under a **Copyleft / Reciprocal license** (e.g., GPL-3.0 or EUPL-1.2). You copy and paste this source code directly into your repository files and extend it to fit your project.

* **Licensing Goal**: Fulfill legal obligations imposed by incorporating inbound copyleft code into your codebase.

[Licensing Assistant](https://interoperable-europe.ec.europa.eu/collection/eupl/solution/licensing-assistant/find-and-compare-software-licenses) selection guide:

| 🟢 **Can** | ⚪ **Must** | 🔵 **Compatible** | 🟡 **Support** |
| :--- | :--- | :--- | :--- |
| ☑ Commercial use | ☑ Copyleft/Share a. | ☑ For software | ☑ OSI approved |
| ☑ Modify/merge | ☑ Disclose source | | |
| ☑ Distribute | | | |

:::{solution}
**Legal Reality**: Unlike referencing external dependencies or writing code from scratch, pasting third-party source code directly into your repository creates a single combined (derivative) work. You do not hold exclusive copyright over the entire codebase.

* **Outcome**: **Restricted Choice (Mandatory Copyleft).** You cannot choose a permissive license (e.g., MIT) or keep the repository proprietary. You must choose a copyleft license compatible with the inbound code.
* **Selected Category**: **Copyleft / Reciprocal** (mandated by the inbound license's copyleft clause).
* **JLA Expected Matches**: `EUPL-1.2`, `GPL-3.0`
* **Why**: Inbound copyleft terms mandate that any derivative work distributed as a whole must inherit reciprocal sharing obligations (`Copyleft/Share a.` and `Disclose source`).
* **User Obligation**: Anyone distributing your project must provide access to the full source code (including your modifications) under the matching copyleft terms.
* **Mixing & Redistribution**: Downstream users receive full copyleft freedoms. You cannot re-license your combined repository under a permissive license later unless you completely strip out or rewrite the third-party copyleft code from scratch.
:::
::::

::::{exercise} Scenario 4: Generating or assisting code using AI tools
You write software using AI coding assistants (e.g., GitHub Copilot, ChatGPT) to generate functions, boilerplate, or refactor algorithms. Your repository consists of a mix of human-authored code and AI-generated outputs.

* **Licensing Goal**: You want **maximum adoption** (or any open-source model) and need to know if using AI tools restricts your choice of open-source license.

[Licensing Assistant](https://interoperable-europe.ec.europa.eu/collection/eupl/solution/licensing-assistant/find-and-compare-software-licenses) selection guide (example using Permissive selection):

| 🟢 **Can** | ⚪ **Must** | 🔵 **Compatible** | 🟡 **Support** |
| :--- | :--- | :--- | :--- |
| ☑ Commercial use | ☑ Incl. Copyright | ☑ For software | ☑ OSI approved |
| ☑ Modify/merge | | | |
| ☑ Distribute | | | |

:::{solution}
**Legal Reality**: Under EU copyright law and international consensus, **pure AI-generated outputs lacking human authorship** and are generally **ineligible** for copyright protection. However, when you assemble, refine, and integrate AI code into an overarching software project through creative human effort, you hold copyright over the resulting human-authored work (provided the AI tool did not reproduce substantial copyrighted third-party snippets verbatim).

* **How Much AI Assistance Is Allowed**: There is no fixed percentage threshold. If a legal dispute arises, courts evaluate **Human Authorship and Creative Control**. Using AI as a boilerplate code generator, advanced autocomplete, or research assistant where you actively guide, review, modify, and structure the code preserves your copyright ownership. Conversely, simply pressing a button to generate an entire project without human creative intervention yields uncopyrightable output.
* **How to Check for Copyrighted Material**: Combine manual codebase searches (e.g., GitHub Code Search), built-in AI tool filters (such as *Block suggestions matching public code* in GitHub Copilot), and automated open-source license scanners (like FOSSology or Snyk).
* **Outcome**: **Fully Permissible.** The use of AI tools does not force a specific open-source license onto your repository. You retain the choice between Permissive or Copyleft based on your strategic goals.
* **Selected Category**: **Permissive** (or Copyleft, determined by author intent rather than the AI tool).
* **JLA Expected Matches**: `MIT`, `Apache-2.0`, `BSD-3-Clause` (or `EUPL-1.2`, `GPL-3.0` if your intent is Copyleft).
* **User Obligation**: Standard obligations apply based on the license you choose to attach to your human-authored codebase.
* **Mixing & Redistribution**: Anyone can use, modify, or redistribute your repository under your chosen license. Downstream users are bound by your overall repository license terms, while the standalone, raw unedited AI snippets themselves remain ineligible for copyright protection.
:::
::::
::::{exercise} Scenario 5: Directly embedding third-party Permissive source code
You find a useful helper module online licensed under a **Permissive license** (e.g., MIT or BSD-3-Clause). You copy and paste this code directly into your repository to build upon it.

* **Licensing Goal**: You want to know if including permissive third-party code limits your overall repository license choices (e.g., if you prefer a Copyleft license like EUPL-1.2 or GPL-3.0).

[Licensing Assistant](https://interoperable-europe.ec.europa.eu/collection/eupl/solution/licensing-assistant/find-and-compare-software-licenses) selection guide (example selecting Copyleft):

| 🟢 **Can** | ⚪ **Must** | 🔵 **Compatible** | 🟡 **Support** |
| :--- | :--- | :--- | :--- |
| ☑ Commercial use | ☑ Copyleft/Share a. | ☑ For software | ☑ OSI approved |
| ☑ Modify/merge | ☑ Disclose source | | |
| ☑ Distribute | | | |

:::{solution}
**Legal Reality**: Permissive licenses (MIT, BSD) grant broad rights to combine, modify, and re-license derivative works under different terms, provided you preserve the original author's copyright notice and license text in the copied files.

* **Outcome**: **Full Flexibility.** Unlike inbound Copyleft (Scenario 3), embedding Permissive code does not force a specific license on your project. You can license your combined repository as Permissive *or* Copyleft.
* **Selected Category**: **Copyleft** (or Permissive, depending on your intent).
* **JLA Expected Matches**: `EUPL-1.2`, `GPL-3.0` (or `MIT`, `Apache-2.0` if Permissive goal).
* **Why**: Permissive inbound code is compatible with almost all OSI-approved software licenses.
* **User Obligation**: You must retain the original copyright notice and MIT/BSD license text within the specific files or NOTICE file where the copied code resides.
* **Mixing & Redistribution**: Downstream users follow your repository's overall license terms, but the original permissive author's attribution notice must remain intact inside the codebase.
:::
::::

::::{exercise} Scenario 6: Linking against a Strong Copyleft library (e.g., GSL or FFTW)
You write your own original code from scratch, but your program includes or links against a third-party scientific library licensed under a **Strong Copyleft license** (such as GPL-3.0).

* **Licensing Goal**: You want to publish your repository and need to select a license that complies with the inbound linking requirements of the GPL library.

[Licensing Assistant](https://interoperable-europe.ec.europa.eu/collection/eupl/solution/licensing-assistant/find-and-compare-software-licenses) selection guide:

| 🟢 **Can** | ⚪ **Must** | 🔵 **Compatible** | 🟡 **Support** |
| :--- | :--- | :--- | :--- |
| ☑ Commercial use | ☑ Copyleft/Share a. | ☑ For software | ☑ OSI approved |
| ☑ Modify/merge | ☑ Disclose source | | |
| ☑ Distribute | | | |

:::{solution}
**Legal Reality**: Linking your code (statically or dynamically) with a Strong Copyleft library like GPL creates a combined software work upon compilation and distribution. The strong copyleft obligation extends across the linking boundary.

* **Outcome**: **Mandatory Copyleft.** To distribute the compiled application or repository, your code must be licensed under a GPL-compatible copyleft license. You cannot license the overall project under a Permissive license (like MIT).
* **Selected Category**: **Copyleft / Reciprocal** (required by the linked GPL library).
* **JLA Expected Matches**: `GPL-3.0`, `AGPL-3.0`, `EUPL-1.2`
* **Why**: The linked library's reciprocal license mandates that any distributed program depending on it must also provide source code access under compatible copyleft terms (`Copyleft/Share a.` and `Disclose source`).
* **User Obligation**: Users who distribute binaries or modified packages of your project must provide the full source code under the GPL-compatible copyleft license.
* **Mixing & Redistribution**: Anyone using or building upon your work must maintain the GPL-compatible copyleft license. If you want to avoid copyleft restrictions for your codebase, you must replace the GPL library dependency with a permissively licensed alternative (e.g., an MIT or BSD library).
:::
::::

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

