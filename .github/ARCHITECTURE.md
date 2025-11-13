# System Architecture Visualization

## 🏗️ The Specialist Ecosystem

```
                           ┌─────────────────────────────┐
                           │   USER (Project Manager)    │
                           │  Coordinates Specialists     │
                           └─────────────┬───────────────┘
                                         │
                    ┌────────────────────┼────────────────────┐
                    │                    │                    │
         ┌──────────▼──────────┐  ┌─────▼──────┐  ┌────────▼─────────┐
         │  GLOBAL INSTRUCTIONS │  │  CHATMODES │  │     PROMPTS      │
         │  Universal Rules     │  │ Specialist │  │   Operational    │
         │  Handoff Protocol    │  │  Identity  │  │    Context       │
         └──────────────────────┘  └────────────┘  └──────────────────┘
                    │                    │                    │
                    └────────────────────┼────────────────────┘
                                         │
            ┌────────────────────────────┼────────────────────────────┐
            │                            │                            │
    ┌───────▼────────┐         ┌────────▼──────┐          ┌─────────▼────────┐
    │ APPLICATION    │         │  DATABASE      │          │ INFRASTRUCTURE   │
    │   LAYER        │         │    LAYER       │          │     LAYER        │
    ├────────────────┤         ├───────────────┤          ├──────────────────┤
    │ NestJS         │◄───────►│ Prisma        │◄────────►│ Docker           │
    │ Specialist     │         │ Specialist    │          │ Specialist       │
    └────────┬───────┘         └───────┬───────┘          └────────┬─────────┘
             │                         │                           │
             │                         │                           │
    ┌────────▼────────┐       ┌────────▼──────┐          ┌────────▼─────────┐
    │ API            │       │ Testing        │          │ GitHub Actions   │
    │ Specialist     │       │ Specialist     │          │ Specialist       │
    └────────┬───────┘       └────────┬───────┘          └────────┬─────────┘
             │                        │                            │
             │                        │                            │
    ┌────────▼────────┐      ┌────────▼──────┐                   │
    │ Documentation  │       │ Monorepo       │                   │
    │ Specialist     │◄──────┤ Specialist     │◄──────────────────┘
    └────────────────┘       └────────────────┘
```

## 🔄 Interaction Flow Example

### Scenario: Adding User Authentication

```
┌─────────┐
│  USER   │ "I need user authentication"
└────┬────┘
     │
     ▼
┌─────────────────┐
│ NestJS Specialist│ "This requires multiple specialists"
└────┬────────────┘
     │ Recommends: Prisma → NestJS → API
     │
     ▼
┌─────────────────┐
│ USER           │ Switches to Prisma
└────┬───────────┘
     │
     ▼
┌─────────────────┐
│ Prisma Specialist│ Creates User model with password field
└────┬────────────┘
     │ Handoff: "Schema ready, switch to NestJS"
     │
     ▼
┌─────────────────┐
│ USER           │ Switches to NestJS
└────┬───────────┘
     │
     ▼
┌─────────────────┐
│ NestJS Specialist│ Implements AuthService, Guards, JWT strategy
└────┬────────────┘
     │ Handoff: "Service ready, switch to API for documentation"
     │
     ▼
┌─────────────────┐
│ USER           │ Switches to API
└────┬───────────┘
     │
     ▼
┌─────────────────┐
│ API Specialist  │ Documents /auth/login and /auth/register endpoints
└────┬────────────┘
     │ Handoff: "API documented, switch to Testing"
     │
     ▼
┌─────────────────┐
│ USER           │ Switches to Testing
└────┬───────────┘
     │
     ▼
┌─────────────────┐
│ Testing Specialist│ Creates auth test suite
└────┬────────────┘
     │ Complete!
     ▼
┌─────────────────┐
│ USER           │ Feature complete
└─────────────────┘
```

## 🎯 Specialist Responsibility Matrix

| Specialist | Primary Focus | Creates | Consumes | Hands Off To |
|-----------|--------------|---------|----------|--------------|
| **NestJS** | Application logic | Services, Controllers, Modules | Prisma types, Config | Prisma, API, Testing |
| **Prisma** | Data models | Schema, Migrations | Database | NestJS, Documentation |
| **Docker** | Containers | Dockerfiles, Compose files | Build artifacts | NestJS, Monorepo, GitHub Actions |
| **API** | Contracts | OpenAPI specs, Docs | Service interfaces | NestJS, Documentation |
| **Documentation** | Knowledge | READMEs, Guides | Code examples | Any (for implementation) |
| **Testing** | Quality | Test suites | Application code | NestJS (for fixes) |
| **Monorepo** | Build system | Workspace configs | Package.json | NestJS, Docker |
| **GitHub Actions** | Automation | Workflows | All artifacts | Docker, Monorepo, Testing |

## 📊 Decision Tree: Which Specialist?

```
                        START: What do you need?
                                  │
                    ┌─────────────┼─────────────┐
                    │             │             │
              [Code Change]  [Infrastructure] [Documentation]
                    │             │             │
        ┌───────────┼───────┐     │        Documentation
        │           │       │     │         Specialist
    [Database]  [Service] [API]  │
        │           │       │     │
     Prisma      NestJS    API   │
    Specialist  Specialist Spec. │
                    │             │
                [Tests?]    [Container?]
                    │             │
                 Testing       Docker
                Specialist   Specialist
                                  │
                            [Automation?]
                                  │
                            GitHub Actions
                             Specialist
```

## 🔗 Integration Points

### NestJS ↔ Prisma
- **NestJS** injects PrismaService
- **Prisma** provides generated types
- Handoff: Schema changes require Prisma, usage requires NestJS

### NestJS ↔ Docker
- **Docker** containerizes NestJS apps
- **NestJS** exposes ports and health checks
- Handoff: Container config vs application config

### Docker ↔ GitHub Actions
- **GitHub Actions** builds and pushes Docker images
- **Docker** provides Dockerfiles and configs
- Handoff: Workflow automation vs container definition

### Monorepo ↔ All
- **Monorepo** structures workspace for all packages
- All specialists work within workspace structure
- Handoff: Workspace config vs package implementation

### API ↔ NestJS
- **API** defines contracts
- **NestJS** implements endpoints
- Handoff: Contract design vs implementation

### Testing ↔ All
- **Testing** validates all components
- All specialists may need fixes based on test results
- Handoff: Test design vs bug fixes

## 🛡️ Boundary Protection

Each specialist has built-in boundary detection:

```
┌─────────────────────────────────────────┐
│          Specialist Domain              │
│  ┌───────────────────────────────────┐ │
│  │                                   │ │
│  │     Safe Operation Zone           │ │
│  │   (Deep Expertise)                │ │
│  │                                   │ │
│  └───────────────┬───────────────────┘ │
│                  │ Boundary            │
│  ┌───────────────▼───────────────────┐ │
│  │  Handoff Zone                     │ │
│  │  (Recognition & Coordination)     │ │
│  └───────────────────────────────────┘ │
└─────────────────────────────────────────┘
```

When a specialist detects they're at a boundary:
1. ⚠️ **Recognize** - "This is outside my domain"
2. 🎯 **Identify** - "This needs [Specialist X]"
3. 📢 **Communicate** - "Switch to [specialist] because [reason]"
4. 🤝 **Context** - "Here's what I've done, here's what's needed"

## 💡 Key Principles Visualized

### Principle 1: Autonomy
```
┌──────────┐     ┌──────────┐     ┌──────────┐
│ NestJS   │     │ Prisma   │     │ Docker   │
│ ┌──────┐ │     │ ┌──────┐ │     │ ┌──────┐ │
│ │Expert│ │     │ │Expert│ │     │ │Expert│ │
│ └──────┘ │     │ └──────┘ │     │ └──────┘ │
└──────────┘     └──────────┘     └──────────┘
   Independent      Independent      Independent
```

### Principle 2: Collaboration
```
┌──────────┐        ┌──────────┐        ┌──────────┐
│ NestJS   │───────►│ Prisma   │◄───────│ Docker   │
│          │ Handoff│          │ Handoff│          │
└──────────┘        └──────────┘        └──────────┘
     ▲                                        │
     │                  Handoff              │
     └────────────────────────────────────────┘
```

### Principle 3: User Control
```
        ┌──────────────┐
        │     USER     │
        │  (Approves   │
        │   Handoffs)  │
        └──────┬───────┘
               │
    ┌──────────┼──────────┐
    ▼          ▼          ▼
[Specialist] [Specialist] [Specialist]
  (Suggests)  (Suggests)   (Suggests)
```

## 📈 Success Indicators

The system is working when you see:

✅ **Clear Boundaries**
- Specialists quickly recognize non-domain work
- Handoff recommendations are accurate

✅ **Smooth Handoffs**
- Context is preserved across specialists
- User understands why handoff is needed

✅ **Quality Work**
- Each specialist provides deep expertise
- Solutions follow best practices

✅ **Efficient Collaboration**
- Minimal back-and-forth
- Clear communication
- Predictable behavior

---

**Remember**: The specialists are a **team**, not a hierarchy. Each brings unique expertise, and together they cover the entire stack comprehensively.
