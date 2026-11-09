# 🧩 Claude Skills Library
> 📌 **Overview:** Curated Notion-style collection of **90 Claude skills** (598 files) organized across official/community `examples/`, domain & workflow `plugins/`, and Anthropic `public/` document/UI skills.
> 🔗 **Ecosystem Role:** Referenced automatically alongside [`KARTHIKEYASHARMA672/skills`](https://github.com/KARTHIKEYASHARMA672/skills) and [`KARTHIKEYASHARMA672/new-skills`](https://github.com/KARTHIKEYASHARMA672/new-skills) in Antigravity global instructions (`GEMINI.md` Sections 4 & 17).
---
## 📋 Repository Properties
| Property | Value |
| :--- | :--- |
| **Owner** | Karthikeya Sharma (`KARTHIKEYASHARMA672`) |
| **Visibility** | **Public** |
| **Default Branch** | `main` |
| **Skill Count** | `90` skills (`35` examples · `47` plugins · `8` public) |
| **Total Skill Files** | `598` files (~`11.6 MB`, including bundled fonts, XML schemas, scripts, references) |
| **Companion Repos** | `KARTHIKEYASHARMA672/skills` (core) · `KARTHIKEYASHARMA672/new-skills` (521 curated) · `KARTHIKEYASHARMA672/memory` (private) |
| **Last Synced** | `2026-11-09` |

---
## 📑 Table of Contents
- [🗂️ Folder Architecture](#-folder-architecture)
- [📘 Examples Skills (35)](#-examples-skills-35)
- [🔌 Plugins Skills (47)](#-plugins-skills-47)
- [🌐 Public Skills (8)](#-public-skills-8)
- [🔄 Ecosystem & Maintenance Rules](#-ecosystem--maintenance-rules)

---
## 🗂️ Folder Architecture
| Directory | Skills | Files | Focus Area |
| :--- | :---: | :---: | :--- |
| [`examples/`](./examples/) | `35` | `217` | Creative canvas/art, browser/computer-use, research, doc co-authoring, MCP builder, personal ops, theme factory, web artifacts. |
| [`plugins/`](./plugins/) | `47` | `189` | Data analytics pack (`10`), Apollo GraphQL (`14`), B2B GTM/Outreach (`12`), Cowork plugin tools (`2`), custom media/ad/quant skills (`ad-creator-sop`, `gemini-omni-prompter`, `ig-nikil-video-skill`, `image-prompt-skill`, `instagram-agent`, `kronos`, `humanizer`, `brag`, `frontend-design`). |
| [`public/`](./public/) | `8` | `192` | Core `.docx`, `.pptx`, `.xlsx`, `.pdf` creation/inspection, file reading, frontend design, and Anthropic product self-knowledge. |

---
## 📘 Examples Skills (35)
> 💡 **Scope:** Creative workflows, research, browser automation, Google Workspace, MCP authoring, and interactive artifact builders.

| Skill | Directory | Files | Description |
| :--- | :--- | :---: | :--- |
| `algorithmic-art` | [`algorithmic-art`](./examples/algorithmic-art/) | `4` | Creating algorithmic art using p5.js with seeded randomness and interactive parameter exploration. Use this when users request creating art using code,... |
| `artifact-emulator` | [`artifact-emulator`](./examples/artifact-emulator/) | `7` | See a page, slide deck or design canvas artifact you made, close to how a person will see it: open its files in the real artifact viewer inside this cloud... |
| `benepass-reimbursement` | [`benepass-reimbursement`](./examples/benepass-reimbursement/) | `2` | Submit expense reimbursements through Benepass (app.getbenepass.com). For users whose employer uses Benepass as their benefits platform. Handles login,... |
| `brand-guidelines` | [`brand-guidelines`](./examples/brand-guidelines/) | `2` | Applies Anthropic's official brand colors and typography to any sort of artifact that may benefit from having Anthropic's look-and-feel. Use it when brand... |
| `built-in-browser` | [`built-in-browser`](./examples/built-in-browser/) | `2` | Read this skill before the first step that uses the built-in browser, the browser pane inside the Claude desktop app (also called the in-app browser, the... |
| `call-to-book` | [`call-to-book`](./examples/call-to-book/) | `2` | Make a phone call to book an appointment or reservation. Checks calendar first, gets explicit consent before dialing, discloses AI identity on the call, and... |
| `cancel-unsubscribe` | [`cancel-unsubscribe`](./examples/cancel-unsubscribe/) | `2` | Cancel a subscription or unsubscribe from a service. Works from a description, a pasted charge line, a URL, or a photo/screenshot. Can also audit a full... |
| `canvas-design` | [`canvas-design`](./examples/canvas-design/) | `83` | Create beautiful visual art in .png and .pdf documents using design philosophy. You should use this skill when the user asks to create a poster, piece of... |
| `chrome-browser` | [`chrome-browser`](./examples/chrome-browser/) | `2` | Read this skill before the first step that uses Claude in Chrome, the browser extension whose tools are named mcp__claude-in-chrome__* (also called Chrome,... |
| `computer-use` | [`computer-use`](./examples/computer-use/) | `2` | Read this skill before the first step of any request to do something in an app on the person's own computer (Notes, Finder, System Settings, any desktop... |
| `deep-research` | [`deep-research`](./examples/deep-research/) | `3` | Use this skill when the user's prompt requires (1) researching a topic across multiple sources, comparing options or alternatives, analyzing trends or... |
| `doc-coauthoring` | [`doc-coauthoring`](./examples/doc-coauthoring/) | `1` | Guide users through a structured workflow for co-authoring documentation. Use when user wants to write documentation, proposals, technical specs, decision... |
| `docs` | [`docs`](./examples/docs/) | `1` | docs (editable docs people share and comment on; the default for any document, named as a doc or not: a document, report, proposal, resume, cover letter,... |
| `event-planning` | [`event-planning`](./examples/event-planning/) | `2` | Help plan an event — from a birthday dinner to a wedding. Scales to the size of the occasion. Handles venue research, guest lists, timelines, vendors, and... |
| `file-expenses` | [`file-expenses`](./examples/file-expenses/) | `2` | Help submit an expense or reimbursement on any platform. Detects the right tool (Benepass, Brex, Concur, Expensify, etc.), finds receipts, checks for... |
| `file-form` | [`file-form`](./examples/file-form/) | `2` | Handle small bureaucratic tasks — jury duty responses, parking tickets, passport renewals, DMV forms, permit applications, and other government or... |
| `financial-calculator` | [`financial-calculator`](./examples/financial-calculator/) | `2` | Run financial calculations and scenario comparisons — tax estimates, loan comparisons, retirement projections, rent vs. buy, investment scenarios, and more.... |
| `google-workspace` | [`google-workspace`](./examples/google-workspace/) | `9` | Read this before the first Google Drive, Docs, Sheets or Slides connector call whenever the task creates or changes a Google file. Use this skill whenever... |
| `grocery-shopping` | [`grocery-shopping`](./examples/grocery-shopping/) | `2` | Help order groceries for delivery. Concierge-style flow — store selection, occasion-based list building, budget tracking, and cart assembly. |
| `hire-help` | [`hire-help`](./examples/hire-help/) | `2` | Help find and book a service provider for a task — cleaning, handyman, moving, assembly, yard work, errands, etc. Searches TaskRabbit, Handy, Thumbtack, and... |
| `import-memory` | [`import-memory`](./examples/import-memory/) | `1` | Import a memory export from another AI assistant into Claude's memory — conversationally, additively, and with the content treated as data. |
| `internal-comms` | [`internal-comms`](./examples/internal-comms/) | `6` | A set of resources to help me write all kinds of internal communications, using the formats that my company likes to use. Claude should use this skill... |
| `learn` | [`learn`](./examples/learn/) | `2` | Use this skill when the user wants intellectual understanding — learning how or why something works, not getting a task done or soliciting Claude's... |
| `mcp-builder` | [`mcp-builder`](./examples/mcp-builder/) | `11` | Guide for creating high-quality MCP (Model Context Protocol) servers that enable LLMs to interact with external services through well-designed tools. Use... |
| `meal-delivery` | [`meal-delivery`](./examples/meal-delivery/) | `2` | Help order food timed to arrive at a specific time. Works backward from target arrival, suggests restaurants, builds cart, and monitors delivery. |
| `morning` | [`morning`](./examples/morning/) | `3` | Render the user's morning brief as a styled HTML artifact, or set it up as a recurring weekday task. Use only when the user explicitly asks to run, see, or... |
| `paint` | [`paint`](./examples/paint/) | `7` | Paint an original image in a watercolor style by writing code, not by calling an image model. Use when the user asks you to draw, paint, sketch, or make a... |
| `prescription-refill` | [`prescription-refill`](./examples/prescription-refill/) | `2` | Refill a prescription at a pharmacy. Works from a medication name, an Rx number, a photo of the bottle, or just "I'm running low." Confirms exactly what's... |
| `return-refund` | [`return-refund`](./examples/return-refund/) | `2` | Help return an item or request a refund from any retailer. Identifies the item, finds the return policy, navigates the process, and handles shipping labels... |
| `setup-writing-style` | [`setup-writing-style`](./examples/setup-writing-style/) | `2` | Learns how the user writes from their own sent messages and docs, and builds a voice profile so future drafts sound like them instead of generic AI. The... |
| `skill-creator` | [`skill-creator`](./examples/skill-creator/) | `18` | Create new skills, modify and improve existing skills, and measure skill performance. Use when users want to create a skill from scratch, edit, or optimize... |
| `slack-gif-creator` | [`slack-gif-creator`](./examples/slack-gif-creator/) | `7` | Knowledge and utilities for creating animated GIFs optimized for Slack. Provides constraints, validation tools, and animation concepts. Use when users... |
| `theme-factory` | [`theme-factory`](./examples/theme-factory/) | `13` | Toolkit for styling artifacts with a theme. These artifacts can be slides, docs, reportings, HTML landing pages, etc. There are 10 pre-set themes with... |
| `video-making` | [`video-making`](./examples/video-making/) | `2` | Use this skill before making a new video. Not for editing a video file the user supplied. |
| `web-artifacts-builder` | [`web-artifacts-builder`](./examples/web-artifacts-builder/) | `5` | Suite of tools for creating elaborate, multi-component claude.ai HTML artifacts using modern frontend web technologies (React, Tailwind CSS, shadcn/ui). Use... |

---
## 🔌 Plugins Skills (47)
> 💡 **Scope:** Domain packs for SQL/Analytics, Apollo GraphQL & Rust, B2B sales/outreach, Cowork plugin management, Kronos forecasting, AI ad/video prompting, and Instagram growth.

| Skill | Directory | Files | Description |
| :--- | :--- | :---: | :--- |
| `analyze` | [`2529b2d1-9426-48a5-a8ad-2ebc77af2815__analyze`](./plugins/2529b2d1-9426-48a5-a8ad-2ebc77af2815__analyze/) | `1` | Answer data questions -- from quick lookups to full analyses. Use when looking up a single metric, investigating what's driving a trend or drop, comparing... |
| `build-dashboard` | [`2529b2d1-9426-48a5-a8ad-2ebc77af2815__build-dashboard`](./plugins/2529b2d1-9426-48a5-a8ad-2ebc77af2815__build-dashboard/) | `1` | Build an interactive HTML dashboard with charts, filters, and tables. Use when creating an executive overview with KPI cards, turning query results into a... |
| `create-viz` | [`2529b2d1-9426-48a5-a8ad-2ebc77af2815__create-viz`](./plugins/2529b2d1-9426-48a5-a8ad-2ebc77af2815__create-viz/) | `1` | Create publication-quality visualizations with Python. Use when turning query results or a DataFrame into a chart, selecting the right chart type for a... |
| `data-context-extractor` | [`2529b2d1-9426-48a5-a8ad-2ebc77af2815__data-context-extractor`](./plugins/2529b2d1-9426-48a5-a8ad-2ebc77af2815__data-context-extractor/) | `6` | Generate or improve a company-specific data analysis skill by extracting tribal knowledge from analysts. BOOTSTRAP MODE - Triggers: "Create a data context... |
| `data-visualization` | [`2529b2d1-9426-48a5-a8ad-2ebc77af2815__data-visualization`](./plugins/2529b2d1-9426-48a5-a8ad-2ebc77af2815__data-visualization/) | `1` | Create effective data visualizations with Python (matplotlib, seaborn, plotly). Use when building charts, choosing the right chart type for a dataset,... |
| `explore-data` | [`2529b2d1-9426-48a5-a8ad-2ebc77af2815__explore-data`](./plugins/2529b2d1-9426-48a5-a8ad-2ebc77af2815__explore-data/) | `1` | Profile and explore a dataset to understand its shape, quality, and patterns. Use when encountering a new table or file, checking null rates and column... |
| `sql-queries` | [`2529b2d1-9426-48a5-a8ad-2ebc77af2815__sql-queries`](./plugins/2529b2d1-9426-48a5-a8ad-2ebc77af2815__sql-queries/) | `1` | Write correct, performant SQL across all major data warehouse dialects (Snowflake, BigQuery, Databricks, PostgreSQL, etc.). Use when writing queries,... |
| `statistical-analysis` | [`2529b2d1-9426-48a5-a8ad-2ebc77af2815__statistical-analysis`](./plugins/2529b2d1-9426-48a5-a8ad-2ebc77af2815__statistical-analysis/) | `1` | Apply statistical methods including descriptive stats, trend analysis, outlier detection, and hypothesis testing. Use when analyzing distributions, testing... |
| `validate-data` | [`2529b2d1-9426-48a5-a8ad-2ebc77af2815__validate-data`](./plugins/2529b2d1-9426-48a5-a8ad-2ebc77af2815__validate-data/) | `1` | QA an analysis before sharing -- methodology, accuracy, and bias checks. Use when reviewing an analysis before a stakeholder presentation, spot-checking... |
| `write-query` | [`2529b2d1-9426-48a5-a8ad-2ebc77af2815__write-query`](./plugins/2529b2d1-9426-48a5-a8ad-2ebc77af2815__write-query/) | `1` | Write optimized SQL for your dialect with best practices. Use when translating a natural-language data need into SQL, building a multi-CTE query with joins... |
| `apollo-client` | [`5527d1c3-ad07-4523-b29e-96df73208f04__apollo-client`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__apollo-client/) | `14` | Guide for building React applications with Apollo Client 4.x. Use this skill when: (1) setting up Apollo Client in a React project, (2) writing GraphQL... |
| `apollo-connectors` | [`5527d1c3-ad07-4523-b29e-96df73208f04__apollo-connectors`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__apollo-connectors/) | `7` | Guide for integrating REST APIs into GraphQL supergraphs using Apollo Connectors with @source and @connect directives. Use this skill when the user: (1)... |
| `apollo-federation` | [`5527d1c3-ad07-4523-b29e-96df73208f04__apollo-federation`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__apollo-federation/) | `4` | Guide for authoring Apollo Federation subgraph schemas. Use this skill when: (1) creating new subgraph schemas for a federated supergraph, (2) defining or... |
| `apollo-ios` | [`5527d1c3-ad07-4523-b29e-96df73208f04__apollo-ios`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__apollo-ios/) | `10` | Guide for building Apple-platform applications with Apollo iOS, the strongly-typed GraphQL client for Swift. Use this skill when: (1) adding Apollo iOS to a... |
| `apollo-kotlin` | [`5527d1c3-ad07-4523-b29e-96df73208f04__apollo-kotlin`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__apollo-kotlin/) | `7` | Guide for building applications with Apollo Kotlin, the GraphQL client library for Android and Kotlin. Use this skill when: (1) setting up Apollo Kotlin in... |
| `apollo-mcp-server` | [`5527d1c3-ad07-4523-b29e-96df73208f04__apollo-mcp-server`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__apollo-mcp-server/) | `4` | Guide for using Apollo MCP Server to connect AI agents with GraphQL APIs. Use this skill when: (1) setting up or configuring Apollo MCP Server, (2) defining... |
| `apollo-router` | [`5527d1c3-ad07-4523-b29e-96df73208f04__apollo-router`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__apollo-router/) | `28` | Version-aware guide for configuring and running Apollo Router for federated GraphQL supergraphs. Generates correct YAML for both Router v1.x and v2.x. Use... |
| `apollo-router-plugin-creator` | [`5527d1c3-ad07-4523-b29e-96df73208f04__apollo-router-plugin-creator`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__apollo-router-plugin-creator/) | `4` | Guide for writing Apollo Router native Rust plugins. Use this skill when: (1) users want to create a new router plugin, (2) users want to add service hooks... |
| `apollo-server` | [`5527d1c3-ad07-4523-b29e-96df73208f04__apollo-server`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__apollo-server/) | `7` | Guide for building GraphQL servers with Apollo Server 5.x. Use this skill when: (1) setting up a new Apollo Server project, (2) writing resolvers or... |
| `graphql-operations` | [`5527d1c3-ad07-4523-b29e-96df73208f04__graphql-operations`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__graphql-operations/) | `6` | Guide for writing GraphQL operations (queries, mutations, fragments) following best practices. Use this skill when: (1) writing GraphQL queries or... |
| `graphql-schema` | [`5527d1c3-ad07-4523-b29e-96df73208f04__graphql-schema`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__graphql-schema/) | `6` | Guide for designing GraphQL schemas following industry best practices. Use this skill when: (1) designing a new GraphQL schema or API, (2) reviewing... |
| `rover` | [`5527d1c3-ad07-4523-b29e-96df73208f04__rover`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__rover/) | `7` | Guide for using Apollo Rover CLI to manage GraphQL schemas and federation. Use this skill when: (1) publishing or fetching subgraph/graph schemas, (2)... |
| `rust-best-practices` | [`5527d1c3-ad07-4523-b29e-96df73208f04__rust-best-practices`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__rust-best-practices/) | `10` | Guide for writing idiomatic Rust code based on Apollo GraphQL's best practices handbook. Use this skill when: (1) writing new Rust code or functions, (2)... |
| `skill-creator` | [`5527d1c3-ad07-4523-b29e-96df73208f04__skill-creator`](./plugins/5527d1c3-ad07-4523-b29e-96df73208f04__skill-creator/) | `2` | Guide for creating effective skills for Apollo GraphQL and GraphQL development. Use this skill when: (1) users want to create a new skill, (2) users want to... |
| `ad-creator-sop` | [`ad-creator-sop`](./plugins/ad-creator-sop/) | `1` | Full AI video ad creation pipeline for product ads (chocolates, perfumes, FMCG, any product). Trigger when user names a brand and asks for an ad, says... |
| `enrich-lead` | [`apollo__enrich-lead`](./plugins/apollo__enrich-lead/) | `1` | Instant lead enrichment. Drop a name, company, LinkedIn URL, or email and get the full contact card with email, phone, title, company intel, and next actions. |
| `prospect` | [`apollo__prospect`](./plugins/apollo__prospect/) | `1` | Full ICP-to-leads pipeline. Describe your ideal customer in plain English and get a ranked table of enriched decision-maker leads with emails and phone numbers. |
| `sequence-load` | [`apollo__sequence-load`](./plugins/apollo__sequence-load/) | `1` | Find leads matching criteria and bulk-add them to an Apollo outreach sequence. Handles enrichment, contact creation, deduplication, and enrollment in one flow. |
| `full-crm` | [`b6f58603-f016-40c1-9c15-fcd22e418efe__full-crm`](./plugins/b6f58603-f016-40c1-9c15-fcd22e418efe__full-crm/) | `1` | Use when the user wants to move already enriched contacts into a CRM and has a separate CRM MCP connected. Orchestrates that separately connected CRM MCP:... |
| `full-csv` | [`b6f58603-f016-40c1-9c15-fcd22e418efe__full-csv`](./plugins/b6f58603-f016-40c1-9c15-fcd22e418efe__full-csv/) | `1` | Use when the user uploads a CSV file containing contacts (LinkedIn URLs, names + companies, or any combination) and wants to enrich them with verified... |
| `full-lookalike` | [`b6f58603-f016-40c1-9c15-fcd22e418efe__full-lookalike`](./plugins/b6f58603-f016-40c1-9c15-fcd22e418efe__full-lookalike/) | `1` | Use when the user has a LinkedIn profile and wants to find similar people — same type of role, seniority, industry, and company size. Acts as a Sales Ops /... |
| `full-meeting` | [`b6f58603-f016-40c1-9c15-fcd22e418efe__full-meeting`](./plugins/b6f58603-f016-40c1-9c15-fcd22e418efe__full-meeting/) | `1` | Use when the user has an upcoming meeting and wants a comprehensive brief on the person they're meeting. Acts as a senior meeting strategist: pulls rich... |
| `full-org` | [`b6f58603-f016-40c1-9c15-fcd22e418efe__full-org`](./plugins/b6f58603-f016-40c1-9c15-fcd22e418efe__full-org/) | `1` | Use when the user wants to map a company's team structure, visualize the org chart, and identify the right people to contact. Acts as a sales intelligence... |
| `full-outreach` | [`b6f58603-f016-40c1-9c15-fcd22e418efe__full-outreach`](./plugins/b6f58603-f016-40c1-9c15-fcd22e418efe__full-outreach/) | `1` | Use when the user wants to craft hyper-personalized outreach messages for B2B contacts. Acts as a senior outreach strategist: captures the user's voice and... |
| `full-prospecting` | [`b6f58603-f016-40c1-9c15-fcd22e418efe__full-prospecting`](./plugins/b6f58603-f016-40c1-9c15-fcd22e418efe__full-prospecting/) | `1` | Use when the user wants to find and enrich B2B contacts matching an ICP. Triggers on: "find me contacts", "build a prospect list", "search for people",... |
| `full-sequence` | [`b6f58603-f016-40c1-9c15-fcd22e418efe__full-sequence`](./plugins/b6f58603-f016-40c1-9c15-fcd22e418efe__full-sequence/) | `1` | Use when the user wants to design and deploy a multi-touch outreach sequence. Acts as a senior outbound strategist: designs the sequence architecture... |
| `full-talent` | [`b6f58603-f016-40c1-9c15-fcd22e418efe__full-talent`](./plugins/b6f58603-f016-40c1-9c15-fcd22e418efe__full-talent/) | `1` | Use when the user wants to source candidates for a role. Acts as a senior talent acquisition partner and headhunter: runs a deep conversational intake to... |
| `brag` | [`brag`](./plugins/brag/) | `1` | Turn a project directory or a website URL into a short, shareable launch video with music, motion, and share copy, built entirely by the model with the... |
| `cowork-plugin-customizer` | [`cowork-plugin-management__cowork-plugin-customizer`](./plugins/cowork-plugin-management__cowork-plugin-customizer/) | `5` | Customize a Claude Code plugin for a specific organization's tools and workflows. Use when: customize plugin, set up plugin, configure plugin, tailor... |
| `create-cowork-plugin` | [`cowork-plugin-management__create-cowork-plugin`](./plugins/cowork-plugin-management__create-cowork-plugin/) | `3` | Guide users through creating a new plugin from scratch in a cowork session. Use when users want to create a plugin, build a plugin, make a new plugin,... |
| `frontend-design` | [`frontend-design`](./plugins/frontend-design/) | `1` | Create distinctive, production-grade frontend interfaces with high design quality. Use this skill when the user asks to build web components, pages, or... |
| `gemini-omni-prompter` | [`gemini-omni-prompter`](./plugins/gemini-omni-prompter/) | `1` | Generate optimized prompts for Google DeepMind's Gemini Omni model. Use when the user asks for a "Gemini Omni prompt", "Omni-optimized prompt", or wants to... |
| `humanizer` | [`humanizer`](./plugins/humanizer/) | `4` | Remove signs of AI-generated writing from text. Use when editing or reviewing text to make it sound more natural and human-written. Based on Wikipedia's... |
| `ig-nikil-video-skill` | [`ig-nikil-video-skill`](./plugins/ig-nikil-video-skill/) | `1` | Replicates Nikil's signature AI product-ad prompt-writing style (used with tools like Google Flow/Omni Flash, Higgsfield, etc.) for turning a product image... |
| `image-prompt-skill` | [`image-prompt-skill`](./plugins/image-prompt-skill/) | `1` | Turns any idea, word, or brief into a ready-to-paste AI image generation prompt using the CRAFT formula, tuned for Midjourney, Flux, DALL-E/GPT Image,... |
| `instagram-agent` | [`instagram-agent`](./plugins/instagram-agent/) | `25` | Run an Instagram account end to end - write Reels from a raw idea (hooks scored against 26 formulas, script, on-screen text, timed beat sheet), captions... |
| `kronos` | [`kronos`](./plugins/kronos/) | `3` | Expert guide for working with the Kronos financial time-series prediction model (by NeoQuasar). Use this skill whenever the user mentions Kronos,... |

---
## 🌐 Public Skills (8)
> 💡 **Scope:** Foundational document engineering (`docx`, `pptx`, `xlsx`, `pdf`), safe file/PDF inspection, frontend craft, and Anthropic product facts.

| Skill | Directory | Files | Description |
| :--- | :--- | :---: | :--- |
| `docx` | [`docx`](./public/docx/) | `61` | Use this skill whenever the user wants to create, read, edit, or manipulate Word documents (.docx) or Word templates (.dotx). Triggers include: any mention... |
| `file-reading` | [`file-reading`](./public/file-reading/) | `2` | Use this skill when a file has been uploaded but its content is NOT in your context — only its path at /mnt/user-data/uploads/ is listed in an... |
| `frontend-design` | [`frontend-design`](./public/frontend-design/) | `2` | Guidance for distinctive, intentional visual design when building new UI or reshaping an existing one. Helps with aesthetic direction, typography, and... |
| `pdf` | [`pdf`](./public/pdf/) | `12` | Use this skill whenever the user wants to do anything with PDF files. This includes reading or extracting text/tables from PDFs, combining or merging... |
| `pdf-reading` | [`pdf-reading`](./public/pdf-reading/) | `3` | Use this skill when you need to read, inspect, or extract content from PDF files — especially when file content is NOT in your context and you need to read... |
| `pptx` | [`pptx`](./public/pptx/) | `58` | Use this skill any time a .pptx or .potx file is involved in any way — as input, output, or both. This includes: creating slide decks, pitch decks, or... |
| `product-self-knowledge` | [`product-self-knowledge`](./public/product-self-knowledge/) | `1` | Stop and consult this skill whenever your response would include specific facts about Anthropic's products. Covers: Claude Code (how to install, Node.js... |
| `xlsx` | [`xlsx`](./public/xlsx/) | `53` | Use this skill any time a spreadsheet file is the primary input or output. This means any task where the user wants to: open, read, edit, or fix an existing... |

---
## 🔄 Ecosystem & Maintenance Rules
- [x] Keep every skill self-contained under `examples/`, `plugins/`, or `public/` with its `SKILL.md` and bundled assets intact.
- [x] Format all repository documentation (`README.md`, notes) in **Notion-style Markdown**.
- [x] Never commit `.env` files, API tokens, Personal Access Tokens (PATs), or private credentials.
- [x] Update `KARTHIKEYASHARMA672/memory` whenever adding, removing, or refactoring skills in this repository.
