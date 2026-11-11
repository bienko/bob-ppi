**IBM BOB PREMIUM PACKAGE FOR i**
# **INTRODUCTION**

---

## **i. IBM i modernization is indispensable to enterprise IT**

!!! success "RECOMMENDED: *CLIMBING THE AI MATURITY CURVE* (LEVEL 3)"
    This course assumes you have completed the <a href="https://ibm.github.io/bob-l3/" target="_blank">**Climbing the AI Maturity Curve with IBM Bob**</a> Level 3 curriculum and that its concepts are familiar ground: the Agentic Sidebar and its modes, the plan-first delegation discipline, Bob Rules and custom configuration, and the context window and its economics. The material ahead builds on those foundations and refers to them throughout. As in that course, Bob does the building and the developer stays in control.

For more than three decades, IBM i (formerly known as AS/400, iSeries and System i) has run some of the most critical business systems in the world. It is common in wholesale distribution, manufacturing, banking, insurance, healthcare and logistics, in enterprises that value reliability, an integrated database and applications that stay in service for decades. Most IBM i shops hold a large body of **RPG**, **CL** and **DDS** code. Some of it was written decades ago, and a great deal of it is still in production.

!!! quote ""
    **Typical IBM i workloads include:**

    - Order entry, inventory and distribution systems
    - Manufacturing and ERP applications
    - Airline and travel reservation systems
    - Banking core systems and payment processing
    - Insurance policy administration
    - Retail point-of-sale and back-office operations
    - Government and public-sector recordkeeping

!!! failure ""
    **Despite their stability, many of these applications now face modernization challenges:**

    - Fixed-format OPM RPG that predates modern language features
    - DDS-defined databases that limit SQL performance and portability
    - Green-screen 5250 interfaces that constrain the user experience
    - Sparse or outdated documentation
    - A shrinking pool of RPG and CL expertise
    - Growing demand for REST APIs, web and mobile front ends and cloud integration

As a result, IBM i organizations increasingly seek ways to modernize their applications while preserving the business logic that has been trusted and refined for years. That is the challenge IBM Bob was designed to address.

---

## **ii. What is IBM Bob?**

***IBM Bob* is an AI-powered modernization and software engineering partner that supports the entire software development lifecycle.** Where a traditional code-completion tool is anchored to the moment of writing code, Bob is designed to support the lifecycle around it. Bob plans, executes, validates and governs multi-step tasks on a developer's behalf, which lets teams:

- Understand existing applications and analyze their business logic
- Generate technical documentation and architectural artifacts
- Modernize legacy systems and build new features
- Create automated tests and accelerate development workflows in general

Enterprises are entering a phase of AI-driven development in which tools do more than suggest or autocomplete code: they operate and coordinate across systems. Four requirements follow from that shift and each is built into how clients work with IBM Bob:

!!! note ""
    - **Support across the SDLC**, from planning through development. The value appears when AI operates inside the existing delivery pipeline
    - **Understanding of entire applications.** Safe orchestration requires application-wide context, which file-level reasoning cannot provide
    - **Governance, security and human oversight by design**, so that policy and accountability are enforced as the work happens
    - **Execution of multi-step workflows.** Outcomes require orchestration, iteration and validation, and a single prompt rarely supplies all three

Bob operates directly within the IBM Bob IDE (VS Code-based). When connected to an IBM i partition, Bob inherits your **library list, OS version, CCSID and home directory**, so every conversation is grounded in the real state of your system. Throughout this lab, Bob will help you understand, modernize, optimize, test and operate a real IBM i application in place. You (the developer) remain in the decision seat for every consequential step along the way.

---

## **iii. What the Premium Package for i adds**

***IBM Bob Premium Package for i (`PPi`)* adds deep IBM i expertise to Bob, so that RPG, CL, DDS and Db2 for i applications can be modernized accurately and efficiently.** It is an extension for the Bob IDE that bundles the **Code for IBM i** extension (source editing, the Object Browser and the IFS Browser) and layers IBM i-specific modes, workflows, skills, tools and slash commands on top of the capabilities already present within Bob. With the package installed, Bob can:

- Read, write and search source members in QSYS and stream files in the IFS
- Run CL commands, SQL statements and PASE commands against the connected system
- Ground its answers in a semantic search over the official IBM i documentation
- Scan an application library into a metadata database and reason from the dependency graph it produces

What sets the Premium Package apart from a general-purpose coding assistant is the set of concrete mechanisms through which that expertise is delivered. Each of them is exercised somewhere in this lab:

| MECHANISM | WHAT IT DOES | LAB SECTION |
| --- | --- | --- |
| **Specialized modes** | Purpose-built AI personas for IBM i work. **IBM i Developer** explains, generates, compiles and tests RPG, CL and DDS; **IBM i Database** generates, modernizes, tunes and reviews Db2 for i SQL. Their presence in the mode selector is the visible proof that your entitlement is live | Modules 1, 2, 4, 5 and 6 run in IBM i Developer; Module 3 runs in IBM i Database |
| **`/init` and the AGENTS member** | A slash command that scans the current library and writes a persistent `AGENTS` member to `QBOBSRC`. Every later task reads it first, so Bob starts with the source layout, compile conventions and project-specific pitfalls already in context | Module 1 |
| **Understand** | A code intelligence component that scans the compiled objects of an application library into a metadata library and maps every dependency between them. The *Understand Dashboard* presents the inventory, and Bob queries the scan data rather than re-reading source members | Module 1, and the *Understand* permission thereafter |
| **Workflows** | Guided multi-step analyses with built-in prompts: *Business Rules Extraction*, *RPG Modernization*, *SQL Index Strategy Advisor*, *RPGUnit Test Plan Creation* and *RPGUnit Test Suite Implementation* | Modules 1, 2, 3 and 4 |
| **Slash commands** | Reusable prompts for repetitive IBM i tasks. `/erd` draws a Mermaid entity relationship diagram from the live catalog; `/review` checks a Db2 for i SQL statement for correctness, security and performance | Modules 1 and 3 |
| **Custom instructions** | Standing rules added to a mode's configuration, so that Bob follows them in every task without being reminded in chat | Module 2 |
| **Skills** | Reusable instructions that Bob activates automatically when a task matches them, such as *understand-app-overview*, *dds-primer-basics* and *rpg-primer-basics*. You can also author your own | Modules 1 and 6 |
| **Tools** | The actions Bob can take on the LPAR: `execute_sql_statement`, `execute_cl_command`, `read_member`, `search_qsys`, `write_stream_file`, `execute_pase_command` and more. Destructive operations require explicit approval | Every module |

!!! info "WHY METADATA MATTERS ON IBM i"
    An IBM i application is a graph of programs, files, logical views, display files, menus and service programs. They reference one another through calls, file opens, bindings, triggers and foreign keys. A model that must rediscover that graph by reading source members on every question is slow, expensive in Bobcoins and prone to guessing about the parts it did not read. **Understand** captures the graph once, from the compiled objects, and stores it in a Db2 library that the whole team can share. From that point on, Bob answers questions such as *"what breaks if I change this file?"* from deterministic scan data and opens a source member only when you ask it to. The `AGENTS` member written by `/init` plays the complementary role for conventions: compile commands, naming patterns and the non-default compile parameters that are easy to miss.

---

## **iv. The environment: the FLIGHT400 application**

The application used throughout this lab is **FLIGHT400**, a classic IBM i flight reservation and booking system originally compiled in the late 1990s and still representative of the applications many IBM i shops run in production.

FLIGHT400 is a complete, self-contained IBM i application delivered as a save file and restored into a library (`FLGHT400`). It contains dozens of programs, display files and database files that together implement a menu-driven flight reservation system. Key components include:

| COMPONENT | RESPONSIBILITY |
| --- | --- |
| `FRSMAIN` | Main application menu and entry point |
| `FRS000` | Flight reservation logon program, compiled in 1997 |
| `FRS001` / `FRS001DF` | Create Order screen and program |
| `FRS021` / `FRS021DF` | Flight Maintenance screen and program |
| `FRS401` | Agent Selection Window, a mid-sized ILE RPG subprogram |
| `FRS409` | Order Modification Confirmation window (OPM RPG) |
| `FLIGHTS`, `ORDERS`, `CUSTOMERS`, `AGENTS` | DDS-described physical files |
| `FLIGHTSZ` and the other `*Z` logical files | Renamed field views over the physical files |
| `CUSTCHK` | A small SQLRPGLE service module that you create in Module 4 as the subject of an RPGUnit test suite |

Together, these components demonstrate the IBM i development patterns found in most enterprise codebases:

- Fixed-format **OPM RPG** with subroutines, indicators and workstation data structures
- **DDS-described** physical and logical files with `RENAME` mappings
- **DDS display files** driving 5250 subfile and window layouts
- Program-to-program `CALL` with parameter passing
- Menu-driven navigation via `*MENU` objects
- **Embedded key handling** (F3, F12, Enter) using `DOUEQ` / `CASEQ` dispatch
- Field naming conventions such as the `S`-prefix used for screen fields

Although FLIGHT400 is intentionally focused, it contains many of the same patterns found in real IBM i systems running today in airlines, distribution, manufacturing and financial services. Because the lab uses one application from start to finish, you see Bob work the way it would in a client's modernization project.

!!! info "WHAT IS IBM i?"
    **IBM i** is the integrated operating system of IBM Power servers. Programs and files live as objects inside **libraries** (`FLGHT400` is one), and a job finds objects by searching its **library list** in order. Source code is stored as **members** of source physical files such as `QRPGSRC` and `QDDSSRCF`, while the **IFS** (Integrated File System) holds stream files in Unix-style directories. **DDS** (Data Description Specifications) describes database files and 5250 display files in fixed columns; **RPG** comes in the older fixed-format **OPM** flavor and the modern **ILE** free-format flavor; **CL** is the control language. **Db2 for i** is the integrated database, and **PASE** is the AIX-compatible runtime in which open-source tools such as Node.js run. Each of these terms comes up in the modules that follow.

---

## **v. Lab objectives**

!!! note "TO EFFECTIVELY MODERNIZE, YOU MUST FIRST UNDERSTAND A CLIENT'S ESTATE"

    IBM i modernization projects frequently involve hundreds of programs, thousands of DDS members and decades of accumulated business logic. Rewriting that code is seldom the hardest part of the initiative. The far greater difficulty lies in understanding:

    - What each program actually does
    - Which fields, files and programs are affected by a change
    - Which business rules must be preserved unchanged
    - How the DDS, RPG, CL and SQL layers fit together
    - How changes can be introduced safely without breaking production

    As more of the code is generated by an agent, this understanding grows more important still. The developer's work moves toward directing, constraining, verifying and correcting what the agent produces, and sound judgment at each of those steps becomes the skill that matters most. That is why the lab starts with understanding. Module 1 maps the application and its dependencies before any code is changed, and Module 2 traces an existing field through every layer before a new one is added.

    IBM Bob, enhanced with the Premium Package for i, accelerates each of these activities: application understanding and architecture discovery, code transformation, database optimization, automated testing and operations. All the while, the developer stays in control of the process.

This lab follows a realistic IBM i modernization workflow. You will use the Premium Package for i to perform the same activities that IBM i teams undertake during modernization initiatives, organized across six modules that progress from analysis to change to operations. The five required modules take roughly **two and a half hours** of hands-on time once the environment is in place; the optional sixth adds about 30 minutes.

| CHAPTER | TOPIC | WHAT YOU'LL TAKE AWAY |
|---------|-------|------------------------|
| [**Setup**](setup.md){:target="_blank"} | Request the Premium Package for i entitlement, install the extension and the IBM i Development Pack, reserve an IBM i 7.6 partition from IBM Technology Zone, connect Bob to it, enable the 5250 terminal and restore the FLIGHT400 save file | A Bob IDE with the *IBM i Developer* and *IBM i Database* modes live, connected to an LPAR with `FLGHT400` on the library list |
| [**1. Analyze**](1-1.md){:target="_blank"} | Browse the library, write the `AGENTS` member with `/init`, scan the application with the *Understand Dashboard*, extract the business rules of `FRS401`, generate an architecture overview and append an entity relationship diagram with `/erd` | Living documentation produced in minutes, plus a persistent dependency graph that every later module draws on |
| [**2. Modernize**](2-1.md){:target="_blank"} | Explain and modernize the OPM RPG program `FRS409` with the *RPG Modernization* workflow; then add standing rules to the *IBM i Developer* mode and extend a *Total Flight Hours* field end to end across `FLIGHTS`, `FLIGHTSZ`, `FRS021` and `FRS021DF` | Free-format ILE RPG produced from fixed-format source, and a cross-stack change delivered as reviewed, insert-only diffs |
| [**3. Optimize**](3-1.md){:target="_blank"} | Review a junior developer's SQL query with `/review` in *IBM i Database* mode, then run the *SQL Index Strategy Advisor* workflow and create the index it recommends | A corrected query and a permanent index chosen from plan cache evidence |
| [**4. Test**](4-1.md){:target="_blank"} | Install RPGUnit, create the `CUSTCHK` service module and have the *RPGUnit Test Plan Creation* and *Test Suite Implementation* workflows plan, write and run its tests | A passing RPGUnit suite produced from a test plan, without writing test boilerplate by hand |
| [**5. Operate**](5-1.md){:target="_blank"} | Ask Bob about active jobs and CPU consumption, investigate the top-ranked job and list the programs in `FLGHT400` that have not been recompiled in years | An operational health check and a modernization backlog, each from a single natural-language prompt. The accreditation instructions close this module |
| [**6. Extend**](6-1.md){:target="_blank"} | **OPTIONAL.** Author a helper skill for React and Vite on IBM i PASE, then have Bob generate a React application styled with IBM Carbon from a screenshot of the 5250 *Create Order* screen and run it on the LPAR | A modern web front end for a green-screen transaction, served from the IBM i itself |

---

## **vi. Lab prerequisites**

The hands-on work ahead assumes you have completed the core curriculum of the *Climbing the AI Maturity Curve* L3 course, or that you hold equivalent familiarity with the Bob IDE and the Agentic Sidebar as well as Rules and AGENTS.md. No prior IBM i experience is required: the *Setup* chapter provisions the partition for you, and the modules explain each IBM i concept where it first appears.

---

What you ***do*** need:

!!! success "REQUIREMENTS"
    - **IBM Bob** installed and authenticated on your local machine
    - Your **IBMid** credentials are at hand (IBM regular employees sign in with their w3id)
    - **IBM regular employees:** access to the **<a href="https://w3.ibm.com/w3publisher/bob/addons" target="_blank">w3 add-ons portal</a>** to request the Premium Package for i entitlement
    - **Business Partners:** access to **IBM Technology Zone** to request the Premium Package for i entitlement
    - Access to **IBM Technology Zone** to reserve an *IBM i 7.6* virtual machine from the *Certified PowerVS Base VMs* collection, which takes 30 to 60 minutes to provision
    - The two Flight400 distribution files, **`FLGHT400.FILE`** and **`Install-Flight400.sql`**, downloaded from the links in the *Setup* chapter
    - A local folder is available to serve as your Bob project workspace, and an SSH client is installed (macOS, Linux and Windows 10 or later include one)

!!! warning "A WORD ON WORKING WITH *GENERATIVE AI*"

    IBM Bob is powered by generative AI and LLMs, and a defining trait of these systems is that they are *non-deterministic* — unlike the *deterministic* tools most IBM i developers are accustomed to. In practice, that means the same prompt can produce different code, DDS or SQL from one run to the next. This is both a strength and a quirk of the technology, and it is something to work *with* rather than against.

    **Precision is what tips the odds in your favor.** The more clearly you describe what you want — the exact library, source file, member, field name and constraints — the more closely Bob's output will mirror your intent. The smallest change in wording can meaningfully change the generated code. Throughout this lab, your results may differ from the examples shown — and that is expected, not a defect. Whenever an output diverges, you have three good options: refine the prompt and try again, edit the generated source by hand, or simply proceed if the variation still compiles and runs correctly on your LPAR. Human review remains essential at every step, and never more so than while you are still learning the tool.

!!! info "MANAGING CONSUMPTION OF *BOBCOINS*"
    The Premium Package requires agentic AI capabilities, which consume Bob Resource Units (Bobcoins). The architecture overview in Module 1 and the RPG modernization in Module 2 are the most expensive prompts in this lab. The `AGENTS` member and the Understand scan exist to lower that cost: once they are in place, Bob answers structural questions from metadata instead of re-reading source members. Finish each module's prompts before you experiment with the optional variations.

---

## **vii. Next steps**

In the chapter ahead, you will obtain the Premium Package for i entitlement in accordance with your job role, install the extension and reserve the IBM i partition that the rest of the lab runs against:

!!! quote ""
    - **IBM regular employees** request the entitlement through the w3 add-ons portal
    - **Business Partners** request the entitlement through IBM Technology Zone

All participants then connect Bob to the partition, enable the 5250 terminal and restore the FLIGHT400 save file into the `FLGHT400` library. The first module begins by analyzing that library: Bob writes its own context file, scans the application into the Understand Dashboard, extracts the business rules of one program and documents the architecture of the whole application. Every later module draws on that understanding. Continue to **[Registration and Setup](setup.md){:target="_blank"}**.

---
