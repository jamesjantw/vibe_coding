# BMad Method - Agent Prompts Collection

This document collects commonly used prompt templates and instructions for various BMad Method Agents. These prompts can help you interact more effectively with AI agents in different scenarios.

## 📋 Document Structure

- **Universal Prompts** - Basic instructions applicable to all Agents
- **Role-Specific Prompts** - Dedicated instructions for each Agent
- **Task-Specific Prompts** - Prompt templates for specific tasks
- **Contextual Prompts** - Prompt examples for different development stages

## 🔧 Universal Prompts

### Basic Interaction Principles

```markdown
# Basic format
@agent_name [task description]

# Examples
@pm Create PRD for task management app
@architect Design system architecture
@dev Implement user authentication
```

### Quality Requirement Prompts

```markdown
# Request high-quality output
Please provide detailed, structured responses containing:
- Specific implementation steps
- Relevant code examples
- Potential risk considerations
- Testing suggestions
```

### Formatting Requirements

```markdown
# Request structured output
Please respond using the following format:
## Title
- Point 1
- Point 2

## Code Examples
```language
// Code content
```
```

### Mandatory Execution Rules (Mandatory Rules)

**All Agents must follow:**

#### 1. File Update Preparation
```markdown
# ⚠️ Important: Must execute before any file updates
Before performing any file updates, all Agents must:

1. **Read Latest Content**
    - Use read_file to read the latest content of files to be updated
    - Ensure understanding of the complete current state of files
    - Avoid updates based on outdated memory

2. **Confirm File Status**
    - Check if other Agents have simultaneous changes
    - Confirm current version and modification history of files
    - Ensure changes won't conflict with other ongoing work

# Example preparation steps
@agent First read latest content of [file name]
Confirm understanding of current file status ✓
Prepare for safe updates ✓
```

#### 2. Development Pre-Preparation
```markdown
# @dev Dedicated - Must read before development
@dev Before starting any development task, please first read docs/architecture/coding-standards.md and confirm understanding of all coding standards.

Confirm reading of coding standards ✓
```

#### 3. Work Session Completion Requirements
```markdown
# Must execute at end of each work session
After completion of each work session, all Agents must:

1. **Update Related Files**
    - Record processing procedures and completed items
    - Update task status and progress
    - Record encountered problems and solutions

2. **Update Change Log**
    - Record changes in CHANGELOG.md in project root directory
    - Include date, author, change content, impact scope

3. **Update File Status**
    - Update status of all related files in docs/ directory
    - Mark completed items, in-progress items, pending items
    - Update last modification time and responsible person

# Example update format
## [YYYY-MM-DD] - [Agent Name]
### Completed Items
- [Specific completed content]
- [Affected files/functions]

### Pending Items
- [Items needing follow-up processing]

### Problems and Solutions
- [Encountered problem]: [Solution]
```

## 👥 Role-Specific Prompts

### PM (Product Manager) Prompts

#### Create PRD
```markdown
@pm Create a comprehensive PRD for [product name] with the following features:
- [Feature 1]
- [Feature 2]
- [Feature 3]

Include: user stories, acceptance criteria, priority matrix, and success metrics.
```

#### Requirements Clarification
```markdown
@pm Help me clarify the requirements for [feature name].
Current understanding: [current understanding]
Questions to resolve: [questions needing clarification]
```

### Architect (Architect) Prompts

#### System Design
```markdown
@architect Design a scalable architecture for [system name] using:
- Frontend: [tech stack]
- Backend: [tech stack]
- Database: [database]
- Authentication: [auth method]

Consider: performance, security, maintainability, and scalability.
```

#### Technology Selection Recommendations
```markdown
@architect Recommend technology choices for [project type]:
- Current team skills: [team skills]
- Project constraints: [project constraints]
- Future scalability needs: [future scaling needs]
```

### Dev (Developer) Prompts

#### Feature Implementation
```markdown
@dev Implement [feature name] with the following requirements:
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

Include: error handling, input validation, and unit tests.

⚠️  Important: Read docs/architecture/coding-standards.md first
✅ Coding standards read and all norms followed
```

#### Code Refactoring
```markdown
@dev Refactor [file/function name] to improve:
- Readability
- Performance
- Maintainability

Current issues: [existing issues]

⚠️  Important: Read docs/architecture/coding-standards.md first
✅ Coding standards read and all norms followed
```

### QA (Test Architect) Prompts

#### Risk Assessment
```markdown
@qa *risk [story name]
Assess implementation risks and provide mitigation strategies.
```

#### Test Strategy Design
```markdown
@qa *design [story name]
Establish complete test scenarios including:
- Unit tests
- Integration tests
- End-to-end tests
- Edge cases
```

#### Quality Review
```markdown
@qa *review [story name]
Conduct comprehensive quality assessment and provide:
- Test coverage analysis
- Code quality feedback
- Security considerations
```

## 🎯 Task-Specific Prompts

### New Feature Development

```markdown
@dev Implement a new feature for [feature description]

Requirements:
- [Specific requirements]
- [Technical constraints]
- [Quality standards]

Please include:
- Implementation plan
- Code structure
- Error handling
- Unit tests
```

### Bug Fixes

```markdown
@dev Fix the bug in [feature/file name]

Problem description: [problem description]
Expected behavior: [expected behavior]
Current behavior: [current behavior]

Reproduction steps:
1. [Step 1]
2. [Step 2]
3. [Step 3]
```

### Code Reviews

```markdown
@qa Review the following code changes:

Files changed: [file list]
Key changes: [main changes]

Focus on:
- Code quality
- Security vulnerabilities
- Performance impact
- Test coverage
```

## 📝 Contextual Prompts

### Project Initiation Phase

```markdown
@pm We're starting a new project: [project description]

Initial requirements:
- [Requirement 1]
- [Requirement 2]

Please establish:
- High-level project vision
- Initial epic breakdown
- Technical recommendations
- Timeline estimates
```

### Mid-Development Check

```markdown
@sm Review our current progress on [story name]

Completed work: [completed items]
Remaining tasks: [remaining tasks]
Blockers: [blockers]

Next step suggestions: [suggested next steps]
```

### Project Closure Phase

```markdown
@po Prepare for project closure: [project name]

Deliverables checklist:
- [Deliverable 1]
- [Deliverable 2]

Documentation needed:
- [Document 1]
- [Document 2]

Deployment plan: [deployment plan]
```

## 🔄 Iterative Optimization Prompts

### Feedback Collection

```markdown
Based on the recently implemented [feature name], please analyze:

Well-performing aspects: [strengths]
Areas for improvement: [improvement points]
Lessons learned: [lessons learned]

Suggestions for future similar tasks: [future suggestions]
```

### Process Improvement

```markdown
@sm Review our development process for [project phase]

Current workflow: [current process]
Pain points identified: [pain points]
Proposed improvements: [improvement suggestions]

Please suggest process optimization solutions.
```

## 📚 Usage Tips

### Principles for Writing Effective Prompts

1. **Specific and Clear** - Clearly describe expected output
2. **Provide Context** - Include relevant background information
3. **Specify Format** - Indicate expected response format
4. **Set Limits** - Clearly state scope and constraints

### Mandatory Requirement Reminders

**⚠️ All Agents must remember:**

Every completion of a work session must immediately execute the following four items:

1. **📖 File Update Preparation**
    - Use read_file to read latest content
    - Ensure understanding of complete current file state
    - Avoid updates based on outdated memory

2. **📝 Update Related Files**
    - Record processing procedures and completed items
    - Update task status and progress tracking

3. **📋 Update Change Log**
    - Record changes in project root CHANGELOG.md
    - Include date, author, change content, and impact scope

4. **🔄 Update File Status**
    - Update status of all related files in docs/ directory
    - Mark completed items, in-progress items, pending items
    - Update last modification time and personnel information

### Best Practices

- **Progressive Questioning** - Start high-level, gradually refine
- **Reference Existing Documents** - Utilize existing project documents
- **Include Examples** - Provide examples of expected output
- **Specify Priorities** - Clearly state what aspects are most important
- **Follow Coding Standards** - @dev must read coding-standards.md first
- **Safe File Updates** - Always read latest content before updates
- **Complete Recording** - Update file status at end of every phase

### Common Patterns

- **Task Decomposition**: Break large tasks into small steps
- **Conditional Branching**: Provide different handling for different scenarios
- **Quality Checks**: Include verification and testing requirements
- **File Generation**: Specify output file formats and content
- **Status Tracking**: Record progress and problems for each step

---

*This document will be continuously updated, welcome contributions of new prompt templates and best practices.*