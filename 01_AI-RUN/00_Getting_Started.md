# Getting Started: AI-Assisted Development Workflow

## Introduction

Welcome to the AI-Assisted Development Workflow! This document will guide you through the complete process of taking your project from initial idea to implementation using a structured, AI-driven approach.

The workflow consists of ten sequential phases, each with its own prompt file that instructs the AI agent on how to assist you. By following this process, you'll create a comprehensive set of documents that build upon each other, culminating in a detailed implementation plan, a tested product, and a successful deployment.

## Complete Workflow Overview

```mermaid
flowchart TD
    A0[Getting Started] -->|Initialize workflow| A
    A[Idea] -->|Human pre-writing, optional AI brainstorming| B
    B[Market Research] -->|Human analysis, AI assists with rapid research via chat| C
    C[Concept Definition] -->|Human finalizes, AI proposes UVP, refines Personas| D
    D[PRD Generation] -->|AI generates and decomposes according to template, Human iteratively validates| E
    E[Task Manager Initialization] -->|AI instructs Roo Orchestrator with PRD features| F
    F[Task Refinement] -->|Roo Orchestrator with Roo Code decomposes complex features into sub-tasks| G
    G[Builder] -->|AI executes tasks, codes via MCPs, Human reviews/validates code & features| H
    H[Testing 08_Testing.md] -->|AI tests features, sets up preview, Human validates| I
    I[Deployment 09_Deployment.md] -->|AI executes deployment plan, Human verifies| J
    J[Iteration] -->|Collects feedback, Human decides next cycle| A
```

## File Naming Conventions

The workflow uses consistent file naming for inputs and outputs. Note that prompt files mentioned here refer to their logical sequence (e.g., `01_Idea.md` is the first conceptual prompt for defining the idea, `05_Specs_Docs.md` handles technical documentation). You will need to ensure your actual prompt filenames in `01_AI-RUN/` are aligned or that [`01_AutoPilot.md`](01_AI-RUN/01_AutoPilot.md:1) correctly references your specific filenames.

| Phase | Logical Prompt File | Primary Output / Location | Nature of Output |
|-------|-----------------------|---------------------------|------------------|
| Idea | 01_Idea.md | idea_document.md | Creation |
| Market Research | 02_Market_Research.md | market_research.md | Creation |
| Core Concept | 03_Core_Concept.md | core_concept.md | Creation |
| PRD Generation | 04_PRD_Generation.md | project_prd.md | Creation |
| Specs & Docs | 05_Specs_Docs.md | `02_AI-DOCS/` & `03_SPECS/` | **Creation** of project-specific files from templates (templates remain untouched) & Reference/Annotation of Best Practices |
| Task Manager | (See [`../02_AI-DOCS/TaskManagement/Roo_Task_Workflow.md`](../02_AI-DOCS/TaskManagement/Roo_Task_Workflow.md:1)) | [`tasks/tasks.json`](tasks/tasks.json:1) (Structure: [`../02_AI-DOCS/TaskManagement/Tasks_JSON_Structure.md`](../02_AI-DOCS/TaskManagement/Tasks_JSON_Structure.md:1)) | Creation |
| Start Building | 07_Start_Building.md | Implementation code | N/A (code) |
| Testing | 08_Testing.md | Tested features, Preview Environment | Validation |
| Deployment | 09_Deployment.md | Deployed Application | Execution |
 
## AI Agent Initial Onboarding (Important!)
 
**AI Agent Directive:** Before starting the workflow (e.g., when processing [`01_AutoPilot.md`](01_AI-RUN/01_AutoPilot.md:1) or the first manual step), you MUST perform the following initial analysis:
1.  **Analyze File Structure:** Carefully examine the list of files provided in the initial `environment_details`. Understand the purpose of the main directories:
    *   `01_AI-RUN/`: Contains the prompt files guiding the workflow stages.
    *   `02_AI-DOCS/`: Contains project documentation templates (architecture, conventions, etc.) and core AI guidance (`Documentation/`). **Crucially, during the 'Specs & Docs' phase, project-specific documents (e.g., `architecture.md`, `coding_conventions.md`) will be CREATED in these subdirectories based on the templates.**
    *   `03_SPECS/`: Contains specification templates (features, bugs). **Similarly, project-specific specification files (e.g., `features/feature_spec_FEAT-XXX.md`) will be CREATED here during the 'Specs & Docs' phase.**
    *   `tasks/`: Will contain the generated task breakdown (`tasks.json`).
2.  **In-Depth Codebase Understanding (Pre-computation & Analysis):**
    *   Beyond just the file structure, you MUST strive to understand the *content and interconnections* of all relevant files within the project workspace.
    *   This means proactively reading key files (e.g., `logic.md`, `project_session_state.json`, existing `.md` files in `01_AI-RUN/`, templates in `02_AI-DOCS/` and `03_SPECS/`, and any core application code if present) to build a mental model of the project's current state, its logic, and how different components are intended to interact.
    *   This deep analysis is foundational for accurately executing the subsequent workflow phases.
3.  **Identify Key Reference Documents:** Recognize that the primary sources of truth for the project, once generated or established, will be:
    *   `project_prd.md` (Generated in Phase 4).
    *   Project-specific technical documents **created** in `02_AI-DOCS/` (e.g., `02_AI-DOCS/Architecture/architecture.md`, `02_AI-DOCS/Conventions/coding_conventions.md`, `02_AI-DOCS/Conventions/design_conventions.md`).
    *   Project-specific specification documents **created** in `03_SPECS/` (e.g., `03_SPECS/features/feature_spec_FEAT-XXX.md`).
    *   Task management guidelines: [`../02_AI-DOCS/TaskManagement/Roo_Task_Workflow.md`](../02_AI-DOCS/TaskManagement/Roo_Task_Workflow.md:1) and [`../02_AI-DOCS/TaskManagement/Tasks_JSON_Structure.md`](../02_AI-DOCS/TaskManagement/Tasks_JSON_Structure.md:1).
    *   AI Agent Optimization Guides: [`../02_AI-DOCS/Documentation/AI_Coding_Agent_Optimization.md`](../02_AI-DOCS/Documentation/AI_Coding_Agent_Optimization.md:1), [`../02_AI-DOCS/Documentation/AI_Design_Agent_Optimization.md`](../02_AI-DOCS/Documentation/AI_Design_Agent_Optimization.md:1).
    *   Overall AI Task Management Vision: [`../02_AI-DOCS/Documentation/AI_Task_Management_Optimization.md`](../02_AI-DOCS/Documentation/AI_Task_Management_Optimization.md:1).
4.  **Prioritize Generated Documents & Adhere to Specs:** When performing subsequent tasks (especially Task Management and Building), you MUST prioritize referencing these **generated, project-specific documents** over the original templates. The templates serve only as a starting structure.
5.  **Spec-Driven Execution:** For any development task (frontend, backend, database, design, etc.), you MUST actively locate, read, and strictly adhere to the relevant detailed specification documents (feature specs, design mockups/guidelines, API contracts, coding conventions, etc.) found within `02_AI-DOCS/` and `03_SPECS/`, or linked within the task `details` in [`tasks/tasks.json`](tasks/tasks.json:1).
 
## How to Use This Workflow

### Step 1: Initialize Your Project

1. Review this Getting Started guide
2. Create a project directory if you haven't already
3. Ensure all prompt files (logically `01_Idea.md` through `09_Deployment.md`) are present in your `01_AI-RUN/` directory, correctly named and sequenced for the [`01_AutoPilot.md`](01_AI-RUN/01_AutoPilot.md:1) or manual execution.

### Step 2: Complete Each Phase in Sequence

For each phase of the workflow:

1. Open the corresponding prompt file (e.g., the file serving as `01_Idea.md` for the Idea phase)
2. Share the prompt with your AI agent
3. Follow the instructions in the prompt to complete the phase
4. Save the output in the designated location using the naming convention
5. Move to the next phase once the current phase is complete

### Step 3: Transition Between Phases

Each prompt file includes a "Next Steps" section at the end that explains:
- How to save the current phase's output
- Which prompt file to use next
- What inputs the next phase requires

## Quick Start Guide

### Option 1: Fully Automated Workflow (Recommended)

1. **Start with AutoPilot**: Open [`01_AutoPilot.md`](01_AI-RUN/01_AutoPilot.md:1) and share it with your AI agent. Ensure [`01_AutoPilot.md`](01_AI-RUN/01_AutoPilot.md:1) correctly references your actual prompt filenames.
2. **Provide your initial idea**: Give a brief description of your project idea (1-3 sentences)
3. **Answer clarifying questions**: The AI will ask 5-7 targeted questions to gather essential information
4. **Minimal intervention**: The AI will guide itself through all phases, only pausing for essential validation

### Option 2: Step-by-Step Workflow

1. **Start with the Idea phase**: Open the prompt file corresponding to `01_Idea.md` and share it with your AI agent
2. **Fill in the template**: Provide your initial project concept
3. **Save the output**: Store as `idea_document.md` in your project directory
4. **Continue to Market Research**: Open the prompt file corresponding to `02_Market_Research.md` and proceed
5. **Follow through each phase**: Complete all ten phases in sequence

## Troubleshooting

If at any point the AI agent seems confused or lacks context:

1. Ensure you've completed all previous phases
2. Verify that output files are named correctly and stored in the expected locations
3. Explicitly reference the relevant output files from previous phases
4. If needed, provide the AI with links to specific sections of previous outputs

## Workflow Stages and Responsibilities (Logical Sequence)

### 1. Idea (using `01_Idea.md` logic)
- **Human Role**: Pre-writing, initial concept formulation
- **AI Role**: Optional brainstorming assistance
- **Output**: Initial project concept (`idea_document.md`)

### 2. Market Research (using `02_Market_Research.md` logic)
- **Human Role**: Analysis and evaluation of research findings
- **AI Role**: Assistance with rapid research via direct interaction/chat
- **Output**: Market validation, competitor analysis, opportunity assessment (`market_research.md`)

### 3. Concept Definition (using `03_Core_Concept.md` logic)
- **Human Role**: Finalizing the core concept
- **AI Role**: Proposing Unique Value Propositions, refining personas
- **Output**: Clearly defined project concept with target users (`core_concept.md`)

### 4. PRD Generation (using `04_PRD_Generation.md` logic)
- **Human Role**: Iterative validation of PRD sections
- **AI Role**: Generating and decomposing PRD according to template
- **Output**: Comprehensive Product Requirements Document (`project_prd.md`)

### 5. Specs & Docs (using `05_Specs_Docs.md` logic)
- **Human Role**: Review of generated documentation
- **AI Role**: **Creating** project-specific files in `02_AI-DOCS/` and `03_SPECS/` by copying and populating templates based on the PRD and gathered technical information.
- **Output**: **Created** project-specific technical documentation and specifications within `02_AI-DOCS/` and `03_SPECS/`.
 
### 6. Task Manager Initialization (Workflow: [`../02_AI-DOCS/TaskManagement/Roo_Task_Workflow.md`](../02_AI-DOCS/TaskManagement/Roo_Task_Workflow.md:1))
- **Human Role**: Review of task structure (as defined in [`../02_AI-DOCS/TaskManagement/Tasks_JSON_Structure.md`](../02_AI-DOCS/TaskManagement/Tasks_JSON_Structure.md:1))
- **AI Role**: Instructing Roo Orchestrator with PRD features, as per [`../02_AI-DOCS/TaskManagement/Roo_Task_Workflow.md`](../02_AI-DOCS/TaskManagement/Roo_Task_Workflow.md:1)
- **Output**: Initial task hierarchy ([`tasks/tasks.json`](tasks/tasks.json:1) adhering to [`../02_AI-DOCS/TaskManagement/Tasks_JSON_Structure.md`](../02_AI-DOCS/TaskManagement/Tasks_JSON_Structure.md:1))

### 7. Builder (using `07_Start_Building.md` logic)
- **Human Role**: Reviewing and validating code and features
- **AI Role**: Executing tasks, coding, utilizing MCPs
- **Output**: Functional code implementation

### 8. Testing (using `08_Testing.md` logic)
- **Human Role**: Final validation of features and preview environment.
- **AI Role**: Executing tests, setting up preview, addressing issues.
- **Output**: Fully tested application, accessible preview, (optional) test reports.

### 9. Deployment (using `09_Deployment.md` logic)
- **Human Role**: Final review of deployed application, go/no-go for public release if applicable.
- **AI Role**: Executing deployment plan, performing post-deployment checks.
- **Output**: Successfully deployed application to the target environment.

### 10. Iteration
- **Human Role**: Making decisions about the next development cycle based on feedback and strategic goals.
- **AI Role**: Assisting with feedback collection analysis, planning for the next iteration.
- **Output**: Plan for the next development cycle or new feature set.

## Key Benefits

- **Human-AI Collaboration**: Leverages strengths of both human creativity and AI capabilities
- **Structured Process**: Clear workflow with defined responsibilities
- **Efficiency**: Automation of repetitive tasks while maintaining quality
- **Flexibility**: Adaptable to various project types and scales
- **Continuous Improvement**: Built-in feedback loops for ongoing refinement

## Best Practices

1. **Complete phases sequentially**: Each phase builds on the outputs of previous phases
2. **Save all outputs**: Keep all generated documents for reference
3. **Validate key decisions**: Review and approve important decisions before proceeding
4. **Provide feedback**: Refine outputs before moving to the next phase
5. **Track changes**: Maintain version control for all documents

---

You are now ready to start the AI-assisted development workflow!

**Recommended Option**: Open the [`01_AutoPilot.md`](01_AI-RUN/01_AutoPilot.md:1) file and share it with your AI agent for a fully automated experience with minimal intervention. Ensure [`01_AutoPilot.md`](01_AI-RUN/01_AutoPilot.md:1) is configured to use the correct prompt filenames from your `01_AI-RUN/` directory.

Alternatively, you can follow the step-by-step process by starting with opening the prompt file corresponding to `01_Idea.md` and sharing it with your AI agent.
