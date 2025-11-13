# Vilit-Starter-Repo: GitHub Copilot Architecture

This directory contains a comprehensive system of specialized AI assistants designed to work as an integrated team on the vilit-starter-repo project.

## 🎯 Overview

This architecture is inspired by [github/awesome-copilot](https://github.com/github/awesome-copilot) but customized specifically for our stack:
- **Backend**: NestJS + Prisma
- **Infrastructure**: Docker (Portainer/Swarm)
- **Build System**: pnpm workspaces + Turborepo
- **Automation**: Bash scripts + GitHub Actions

## 📁 Structure

```
.github/
├── README.md                    # This file
├── instructions/
│   └── global.md               # Universal rules for all specialists
├── chatmodes/
│   ├── nestjs.md               # NestJS framework specialist
│   ├── prisma.md               # Database & ORM specialist
│   ├── docker.md               # Container & infrastructure specialist
│   ├── api.md                  # API design & documentation specialist
│   ├── documentation.md        # Technical writing specialist
│   ├── testing.md              # Testing strategy specialist
│   ├── monorepo.md             # Build system & workspace specialist
│   └── github-actions.md       # CI/CD automation specialist
└── prompts/
    ├── nestjs-prompt.md        # Operational context for NestJS
    ├── prisma-prompt.md        # Operational context for Prisma
    ├── docker-prompt.md        # Operational context for Docker
    ├── api-prompt.md           # Operational context for API
    ├── documentation-prompt.md # Operational context for Documentation
    ├── testing-prompt.md       # Operational context for Testing
    ├── monorepo-prompt.md      # Operational context for Monorepo
    └── github-actions-prompt.md # Operational context for GitHub Actions
```

## 🧩 System Components

### 1. Instructions (`instructions/`)

**Purpose**: Define universal rules and principles for all specialists.

**Key File**:
- `global.md`: Core principles, handoff protocols, communication standards, and interaction matrix

**What it provides**:
- Specialist autonomy and boundary rules
- Collaborative handoff protocol
- Stack-specific context
- Communication standards
- Quality standards
- Anti-patterns to avoid

### 2. Chatmodes (`chatmodes/`)

**Purpose**: Define each specialist's identity, expertise, and boundaries.

**Each chatmode defines**:
- Domain of expertise
- Core responsibilities
- Technology context
- Boundaries and limitations
- Handoff protocols
- Best practices
- Integration points with other specialists

**Available Specialists**:

#### 🟢 NestJS Specialist
- Application architecture and module design
- Services, controllers, guards, pipes
- Dependency injection
- Middleware and interceptors

#### 🔵 Prisma Specialist
- Database schema design
- Relationships and migrations
- Query optimization
- Data modeling

#### 🟣 Docker Specialist
- Container configuration
- Docker Swarm orchestration
- Portainer management
- Infrastructure setup

#### 🟡 API Specialist
- REST API design
- OpenAPI/Swagger specs
- API versioning
- Status codes and contracts

#### 🟠 Documentation Specialist
- Technical writing
- README files
- Architecture docs
- User guides

#### 🔴 Testing Specialist
- Test strategy
- Unit/Integration/E2E tests
- Test data management
- Coverage analysis

#### 🟤 Monorepo Specialist
- Workspace structure
- pnpm configuration
- Turborepo optimization
- Build orchestration

#### ⚫ GitHub Actions Specialist
- CI/CD workflows
- Automated testing
- Deployment pipelines
- Workflow optimization

### 3. Prompts (`prompts/`)

**Purpose**: Provide operational context and quick reference for each specialist.

**What they contain**:
- Context awareness for the project
- Quick operational guidelines
- "Stay in lane" checklists
- Handoff triggers
- Response patterns
- Example interactions

## 🔄 How the System Works

### Core Principle: Separation of Concerns

Each specialist operates within their defined domain. When work requires another domain, they:

1. **Acknowledge the boundary**: "This requires [domain] expertise"
2. **Identify the specialist**: "Switch to [specialist chatmode]"
3. **Request user confirmation**: "Would you like to switch?"
4. **Provide context**: Summary of what's been done and what's needed

### Example Workflow

**User**: "I need to add user authentication"

**NestJS Specialist** responds:
> "This task spans multiple domains:
> 1. **Prisma Specialist** should first create the User schema with password fields
> 2. **I (NestJS)** can implement the AuthService and Guards
> 3. **API Specialist** can design the authentication endpoints
> 
> Would you like to start with the **prisma** specialist?"

**User** switches to Prisma → Prisma creates schema → User switches back to NestJS → NestJS implements service → User switches to API → API documents endpoints.

### Interaction Matrix

The `global.md` instructions file contains a comprehensive matrix showing when each specialist should hand off to another. For example:

| Current Specialist | Encounters | Handoff To |
|-------------------|-----------|-----------|
| NestJS | Database schema changes | Prisma |
| Prisma | Service layer logic | NestJS |
| Docker | Application code errors | NestJS |
| API | Route implementation | NestJS |

## 🎓 Using the System

### For Users

1. **Identify your task domain**: Is it about NestJS? Prisma? Docker?
2. **Start with the appropriate specialist**: Use the chatmode for that domain
3. **Follow handoff recommendations**: When a specialist suggests switching, do so
4. **Trust the boundaries**: Specialists are designed to recognize their limits

### For Contributors

When adding or modifying specialists:

1. **Maintain consistency**: Follow existing patterns in chatmodes and prompts
2. **Respect boundaries**: Don't overlap domains
3. **Update the matrix**: Modify the interaction matrix in global.md if needed
4. **Test handoffs**: Ensure specialists correctly identify boundary crossings

## 🎯 Design Principles

### 1. Modular & Cohesive
- Each specialist is independent but interoperable
- Clear interfaces between specialists
- Shared vocabulary and concepts

### 2. Safe Collaboration
- Universal rules prevent confusion
- Explicit handoff protocol
- User always in control

### 3. Autonomous Expertise
- Deep knowledge in specific domains
- Confident within boundaries
- Humble at boundaries

### 4. Stack-Aligned
- All specialists understand the project stack
- Recommendations align with NestJS + Prisma + Docker + pnpm + Turborepo
- Based on official documentation

### 5. User-Centric
- Always ask for confirmation before switching
- Provide clear explanations
- Focus on delivering value

## 📚 Key References

Each specialist bases recommendations on:
- Official documentation for their domain
- Industry best practices
- Security guidelines
- Performance patterns

## 🔧 Maintenance

### Adding a New Specialist

1. Create chatmode in `chatmodes/[name].md`
2. Create prompt in `prompts/[name]-prompt.md`
3. Update interaction matrix in `instructions/global.md`
4. Update this README

### Updating a Specialist

1. Modify the relevant chatmode file
2. Update corresponding prompt if needed
3. Check for impact on interaction matrix
4. Document changes in commit

## 🚀 Benefits

- **Clarity**: Each specialist has a clear role
- **Quality**: Deep expertise in each domain
- **Safety**: Boundaries prevent mistakes
- **Efficiency**: Right specialist for each task
- **Maintainability**: Modular and organized

## 📝 Notes

- Specialists should never execute work outside their domain
- Handoffs always require user confirmation
- The system evolves with the project
- Documentation should stay current

## 🤝 Contributing

When working with this system:
1. Respect specialist boundaries
2. Follow handoff protocols
3. Maintain consistency
4. Update documentation
5. Test interactions

---

**Last Updated**: November 2025  
**Version**: 1.0  
**Stack**: NestJS + Prisma + Docker + pnpm + Turborepo
