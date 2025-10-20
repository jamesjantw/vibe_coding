# BMAD-method vs Openspec

> **Version**: v1.0
> **Author**: Integrated revision by ChatGPT (GPT-5)
> **Purpose**: This document is for use by development teams on GitHub, technical presentations, or open source project folders.
> **Features**: Emphasizes development methodologies, AI collaboration architecture, and practical application guidance.

---

## 1. Method Overview

### 🧠 BMAD-method
BMAD (Behavioral Multi-Agent Development) is a method centered on "multi-agent collaboration" for AI agile development.
It simulates the interactions between complete software teams (PO, PM, Architect, Dev, QA, UI/UX) and automates advancement through context and task division.
Emphasizes **agent-based decision-making, context engineering, repeatable agile cycles**.

**Latest Version Features**:
- **Modular Architecture**: Supports expansion pack system, applicable to any domain like game development, creative writing
- **Dual Environment Support**: Optimized for Web UI (planning phase) and IDE (development phase)
- **Intelligent Configuration System**: core-config.yaml enables project structure flexibility
- **Quality Assurance Architecture**: Test Architect (Quinn) provides professional testing strategies and quality gate controls

**Applicable Scenarios**
- Complex cross-domain projects (ERP, Portal, AI Agent)
- Teams with clear division of labor requiring high traceability
- Development environments needing AI participation in strategic decisions
- Any domain projects: software development, game development, creative writing, business strategy, etc.
- New projects (Greenfield) and existing project enhancements (Brownfield)

### ⚙️ Openspec
OpenSpec is a development framework centered on "specification-driven development" ideology.
It incorporates "proposal → review → implementation → archiving" into automated cycles to ensure consistency between requirements, design, and code.
Emphasizes **auditable, traceable, reproducible** collaboration modes.

**Applicable Scenarios**
- SaaS / API platform development and operations
- Highly compliant and review-demanding scenarios (enterprise projects)
- Open source communities or multi-person collaborative projects

---

## 2. Core Philosophy Comparison

| Item | BMAD-method | Openspec |
|:--|:--|:--|
| **Design Philosophy** | Multi-agent simulation of human team collaboration | Specification-driven, ensuring consistency and traceability |
| **Development Process Core** | Agent collaboration + Context-based task division | Proposal → Review → Spec → Archive |
| **Emphasis** | Automated agile cycles, context recording, quality assurance architecture | Documentation, normalization, automatic alignment |
| **Main Deliverables** | Reproducible team decision records and code, professional testing strategies | Standardized development specifications and versioned documentation |
| **Typical Applications** | AI Agents, enterprise automation platforms, complex systems, game development, creative writing | SaaS platforms, open source projects, compliance products |
| **Environment Support** | Web UI + IDE dual environment optimization | Mainly for normalized development environments |
| **Extensibility** | Expansion pack system supports any domain | Focused on normalized development processes |

---

## 3. Advantages and Disadvantages Analysis

| Category | BMAD-method | Openspec |
|:--|:--|:--|
| **Advantages** | - Multi-agent automatic division and feedback<br>- Supports Scrum/Agile rhythms<br>- Helps establish context-based decision knowledge bases<br>- Quality assurance architecture (Test Architect)<br>- Expansion pack support for any domain | - Documentation and code consistency<br>- Development history auditable<br>- Suitable for version control and automatic documentation generation |
| **Disadvantages** | - High learning curve<br>- Context management requires experience<br>- Suitable for medium to large projects | - High upfront investment in specification writing<br>- Unfavorable for rapid prototyping or exploratory development<br>- Lacks team collaboration simulation |

---

## 4. Practical Process Examples

### BMAD-method Implementation Steps
1. **Planning Phase (Web UI)**: Use large context models like Gemini to establish PRD and architecture documents
2. **Environment Transition**: Copy documents to project's `docs/prd.md` and `docs/architecture.md`
3. **Document Sharding**: Use PO agent to shard large documents into manageable parts
4. **Development Cycle**: SM → Dev → QA sequential development flow, each story one complete cycle
5. **Quality Assurance**: Test Architect (Quinn) provides professional testing strategies and quality gate controls
📺 [YouTube Complete Tutorial Video](https://www.youtube.com/watch?v=5mhjgwTWAPA)

### Openspec Implementation Steps
1. Write feature proposal (Proposal Draft)
2. Review and iterate via Review/Alignment
3. AI generates code and tests based on specifications
4. Automatic archiving and version control
📺 [Openspec Concept Tutorial](https://www.youtube.com/watch?v=ANjiJQQIBo0)

---

## 5. Practical Application Recommendations

| Development Requirement Type | Recommended Method |
|:--|:--|
| Building AI automatic development teams, agent simulation projects | **BMAD-method** |
| Highly process-oriented, review or specification tracking required systems | **Openspec** |
| Teaching / experimental projects | **Openspec (easier to get started)** |
| Large enterprise-level projects or multi-role integrations | **BMAD-method (high extensibility)** |
| Game development, creative writing, business strategy, etc. non-technical domains | **BMAD-method (expansion pack support)** |
| Projects needing professional quality assurance and testing strategies | **BMAD-method (Test Architect)** |
| Brownfield project enhancements and refactoring | **BMAD-method (dedicated workflows)** |

---

## 6. Popular Audio-Visual & Tutorial Resources

### 🎥 BMAD-method Tutorial Highlights
- [Complete Guide to Building AI Agile Teams (YouTube)](https://www.youtube.com/watch?v=5mhjgwTWAPA)
- [Multi-Agent Practical Demonstration (YouTube)](https://www.youtube.com/watch?v=31wPd03ZOJ0)
- [Gemini Implementation of BMad Team Example](https://www.youtube.com/watch?v=Coo4tfJsL7k)

### 🎬 Openspec Tutorial Highlights
- [OpenSpec Development Specifications and Implementation Teaching (YouTube)](https://www.youtube.com/watch?v=ANjiJQQIBo0)
- [AI Coding Specification Revolution Tool (YouTube)](https://www.youtube.com/watch?v=NexwdkKrcUU)
- [Complete Flow from Spec to Code (YouTube)](https://www.youtube.com/watch?v=xTOY6ryjHSE)

---

## 7. References & Extensions

| Topic | Reference Resources |
|:--|:--|
| BMAD Official Documentation | [BMAD User Guide](docs/user-guide.md) |
| BMAD Core Architecture | [Core Architecture](docs/core-architecture.md) |
| BMAD Framework Analysis | [GMO Engineering Blog](https://recruit.gmo.jp/engineer/jisedai/blog/the-bmad-method-a-framework-for-spec-oriented-ai-driven-development/) |
| BMAD Community & Support | [Discord Community](https://discord.gg/gk8jAdXWmj) |
| Openspec Specification Interpretation | [CSDN Technical Article](https://blog.csdn.net/m0_71165399/article/details/153475459) |
| Specification-Driven Development Trends | [From Spec-Kit to OpenSpec Trend Analysis](https://www.53ai.com/news/LargeLanguageModel/2025101896725.html) |
| BMAD Expansion Pack Guide | [Expansion Packs Guide](docs/expansion-packs.md) |

---

## 8. Technology Trends & Outlook

- **BMAD-method**:
  Moving towards "multi-agent collaboration + automatic agile planning" mainstream framework, expected to integrate GitOps, LLM CodeOps, and Agentic Orchestration. Latest v4 version has implemented modular architecture, dual environment support, intelligent configuration system, and professional quality assurance architecture.

- **Openspec**:
  Will become the core mechanism for "AI development governance", future integration with Lint, CI/CD, API Schema automatic synchronization, a key tool for enterprise open source project governance.

---

> 💡 **Suggested Integration Strategy:**
> If the team needs quick start-up, adopt "OpenSpec for specification writing → BMAD method for automatic execution and management" hybrid mode, combining flexibility and rigor.
> For complex projects, prioritize using BMAD-method's planning phase to establish complete documentation, then utilize its quality assurance architecture to ensure development quality.

---

## 9. Implementation Examples & Quick Start Guide

### 🚀 BMAD-method Quick Start Guide

#### Step 1: Environment Preparation
```bash
# Install BMAD-method to your project
npx bmad-method install
```

#### Step 2: Choose Suitable Team
Select team based on project type and set up according to following steps:

**New Project Development (Recommended)**:
```bash
# Download team-fullstack.txt
curl -O https://raw.githubusercontent.com/bmadcode/bmad-method/main/dist/teams/team-fullstack.txt

# Create new Gem in Gemini
# 1. Go to https://gemini.google.com/app
# 2. Create new Gemini Gem
# 3. Upload team-fullstack.txt file
# 4. Set instruction: "Your critical operating instructions are attached, do not break character as directed"
```

**Backend Project**:
```bash
# Download team-no-ui.txt
curl -O https://raw.githubusercontent.com/bmadcode/bmad-method/main/dist/teams/team-no-ui.txt

# Create Custom GPT in ChatGPT
# 1. Go to https://chat.openai.com/gpts
# 2. Create new Custom GPT
# 3. Upload team-no-ui.txt as knowledge file
# 4. Set system prompt: "You are part of a BMAD-method development team focused on backend development"
```

**Full Functionality (Advanced Users)**:
```bash
# Download team-all.txt
curl -O https://raw.githubusercontent.com/bmadcode/bmad-method/main/dist/teams/team-all.txt

# Use in Claude
# 1. Go to https://claude.ai
# 2. Create new conversation
# 3. Copy paste content of team-all.txt
# 4. Start using /help command
```

**Team File Locations**: All team files can be found in project's `dist/teams/` directory, or download directly from GitHub.

#### Step 3: Start Planning (Web UI or IDE Phase)

**Option A: Web UI Planning (Recommended for Beginners, Cost-Effective)**
In Gemini or other Web UI:

**Initial Prompt Examples**:
```
I want to create a [project type, e.g.: task management application].

Project goal: [Brief description of your idea]
Main features: [List 3-5 core features]
Target users: [Describe target user group]
Tech preferences: [Mention preferred tech stack if any]

Please help me plan this project using BMAD-method team.
```

**Specific Planning Prompts**:
```
@pm I need to create a PRD for a task management application. This application should allow users to create, edit, and track tasks, support team collaboration, and have basic reporting functionality. Guide me through the PRD creation process.
```

```
@architect Based on this PRD, design a scalable system architecture. Considering users may grow to 10,000 people and need to support mobile applications.
```

**Option B: IDE Direct Planning (For Experienced Developers)**
In Kilo Code or other BMAD-supporting IDE:

**Install and Launch**:
```bash
# Install BMAD to project
npx bmad-method install

# Launch planning mode
@pm create-doc prd
```

**IDE Planning Prompt Examples**:
```
@pm I want to create a task management application. Help me create a complete PRD including user stories, functional requirements, and acceptance criteria.

Project background: A tool supporting team collaboration for task management
Main features:
- Task creation, editing, deletion
- Team member assignment
- Progress tracking and reporting
- Notification system

Guide me step by step through PRD creation.
```

```
@architect Now that PRD is complete, design the technical architecture for this task management system.

Technical requirements:
- Frontend: React or Vue
- Backend: Node.js or Python
- Database: PostgreSQL or MongoDB
- Support 1000+ concurrent users
- Need RESTful API

Create complete architecture documentation.
```

**IDE Planning Advantages**:
- Work directly in development environment
- Documents automatically saved to project structure
- Immediate transition to development phase possible
- No need to copy documents between different environments

#### Step 4: Development Phase (IDE Phase)
After switching to your IDE:

**Story Development Prompts**:
```
@sm Create the next development story for user authentication functionality. Reference security requirements in PRD and authentication design in architecture document.
```

```
@dev Implement this user login function. Remember to include password validation, session management, and error handling. Reference security design in architecture document.
```

```
@qa Check this login function implementation, ensure it complies with security standards and has appropriate test coverage.
```

### 📋 Openspec Quick Start Guide

#### Step 1: Establish Specification Structure
```yaml
# Establish specs/ directory structure
specs/
├── features/
│   ├── user-management/
│   └── task-management/
└── api/
    ├── v1/
    └── v2/
```

#### Step 2: Write First Feature Proposal
**Initial Prompt Examples**:
```
I need to establish specifications for user management system.

Functional requirements:
- User registration and login
- Password reset functionality
- Basic profile management

Please help me write specification proposal.
```

**Specification Proposal Template**:
```yaml
proposal:
  id: "user-registration-v1"
  title: "User Registration Function"
  version: "1.0"
  author: "Development Team"
  date: "2025-10-20"

  description: |
    Implement complete user registration flow, including validation and data storage

  requirements:
    functional:
      - Email verification
      - Password strength check
      - User data storage
    non-functional:
      - Response time < 2 seconds
      - Support 1000 concurrent users
      - GDPR compliance

  acceptance-criteria:
    - User can successfully register account
    - Receive verification email
    - Password meets security standards
```

#### Step 3: Review and Iteration
**Review Prompts**:
```
Review this user registration specification proposal. Check if it covers all necessary security considerations and ensure specifications are detailed enough for development.
```

#### Step 4: Generate Implementation Specifications
**Implementation Prompts**:
```
Based on approved user registration proposal, generate detailed API specifications and database design specifications.
```

### 💡 Practical Application Examples

#### Example 1: Simple Todo Application

**BMAD-method Approach**:
1. **Planning Phase**: `@pm Create PRD for simple todo application`
2. **Architecture Design**: `@architect Design frontend using React, backend using Node.js architecture`
3. **Development Phase**: `@sm Create first story - task creation functionality`
4. **Implementation**: `@dev Implement task CRUD operations`

**Openspec Approach**:
1. **Proposal**: Write task management specification proposal
2. **Review**: Team review function completeness
3. **Implementation**: Generate code and tests based on specifications

#### Example 2: Enterprise-Level User Management System

**BMAD-method Approach**:
- Use complete team (PM, Architect, Dev, QA, UX)
- Phased development: Authentication → User Management → Permission Control → Audit Logs
- Each phase has complete testing and quality checks

**Openspec Approach**:
- Establish complete security and compliance specifications first
- Specification-driven development, ensure every function meets enterprise standards
- Version control all specification changes

### 🔧 Common Questions & Solutions

#### BMAD-method Common Questions
**Q: Where should I start for first use?**
A: Start in Web UI, use `/help` command to understand available functions, then say `/pm I want to create a [your project idea]`.

**Q: How to switch between different environments?**
A: After completing planning in Web UI, copy generated documents to project's `docs/` folder, then continue development in IDE.

#### Openspec Common Questions
**Q: How detailed should specifications be?**
A: Specifications should be detailed enough for developers to directly write code based on them, but not over-designed. Include input output formats, error handling, and edge cases.

**Q: How to handle specification changes?**
A: All specification changes must go through review process, create new versions, and record change reasons.

### 📈 Advanced Techniques

#### BMAD-method Advanced Applications
- **Expansion Packs**: Explore `expansion-packs/` directory, find suitable ones for your domain
- **Customization**: Modify `core-config.yaml` to adapt to your project structure
- **Team Optimization**: Choose appropriate team size based on project scale

#### Openspec Advanced Applications
- **Automation**: Integrate into CI/CD processes for automatic specification consistency verification
- **Version Management**: Use semantic versioning for specification changes
- **Cross-Project Reuse**: Establish common specification libraries to improve development efficiency

---

**Document Update Record**
- 2025-10-20: v1.0 update - Added BMAD-method latest features, quality assurance architecture, expansion pack support, etc.
- 2025-10-20: Added implementation examples chapter, providing specific application templates for BMAD-method and Openspec

---

<div align="center">© 2025 Team Insight – AI Collaborative Development Framework</div>