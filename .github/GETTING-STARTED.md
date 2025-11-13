# Getting Started with the Specialist System

This guide will help you understand and effectively use the vilit-starter-repo specialist system.

## 🚀 Quick Start

### 1. Understand Your Task

Before choosing a specialist, identify what you're trying to do:

- 🟢 **Building features?** → Start with NestJS
- 🔵 **Changing database structure?** → Start with Prisma
- 🟣 **Deploying or containerizing?** → Start with Docker
- 🟡 **Designing API contracts?** → Start with API
- 🟠 **Writing docs?** → Start with Documentation
- 🔴 **Writing tests?** → Start with Testing
- 🟤 **Configuring workspace?** → Start with Monorepo
- ⚫ **Setting up CI/CD?** → Start with GitHub Actions

### 2. Read the Specialist's Profile

Each specialist has a detailed profile in `.github/chatmodes/`:

```bash
# Read specialist profiles
cat .github/chatmodes/nestjs.md
cat .github/chatmodes/prisma.md
# ... etc
```

### 3. Start Working

Begin with your chosen specialist and follow their guidance. When they recommend a handoff, trust their judgment and switch specialists.

## 📖 Your First Feature: User CRUD

Let's walk through a complete feature implementation to see how specialists work together.

### Goal
Create a complete user management system with database, API, and tests.

### Step 1: Design the Data Model (Prisma Specialist)

**You ask**: "I need a User entity with email, name, and timestamps"

**Prisma Specialist provides**:
```prisma
model User {
  id        String   @id @default(uuid())
  email     String   @unique
  name      String
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  
  @@index([email])
}
```

**Prisma says**: "Schema is ready. Run `prisma migrate dev --name create-users`. Now switch to **nestjs** specialist to implement the service layer."

### Step 2: Implement Service Layer (NestJS Specialist)

**You ask**: "Implement UserService with CRUD operations"

**NestJS Specialist provides**:
- UserService with create, findAll, findOne, update, delete methods
- UserController with corresponding endpoints
- CreateUserDto and UpdateUserDto with validation
- UserModule configuration

**NestJS says**: "Service layer complete. Switch to **api** specialist to document the endpoints."

### Step 3: Document API (API Specialist)

**You ask**: "Document the User API endpoints"

**API Specialist provides**:
- OpenAPI/Swagger decorators for each endpoint
- Request/response schema documentation
- Status code specifications
- Error response formats

**API says**: "API documented. Switch to **testing** specialist to add test coverage."

### Step 4: Add Tests (Testing Specialist)

**You ask**: "Create tests for User CRUD operations"

**Testing Specialist provides**:
- Unit tests for UserService
- Integration tests for UserController
- E2E tests for the complete flow
- Test data factories

**Testing says**: "Tests complete. Switch to **documentation** specialist to update the README."

### Step 5: Update Documentation (Documentation Specialist)

**You ask**: "Document the User feature in the README"

**Documentation Specialist provides**:
- Feature description in README
- Usage examples
- Setup instructions
- API reference link

**Documentation says**: "Documentation complete. Your feature is ready!"

## 🎯 Understanding Handoffs

### What is a Handoff?

A handoff is when a specialist recognizes that work needs to move to another domain. They will:

1. **Acknowledge the boundary**: "This requires [domain] expertise"
2. **Name the specialist**: "Switch to the **[specialist]** chatmode"
3. **Explain why**: Clear reasoning for the handoff
4. **Provide context**: What's been done and what's needed

### Example Handoff

```
User: "I need to add a createdBy field to track who created each post"

NestJS Specialist responds:
"Adding a field to the database schema requires the Prisma specialist's 
expertise. I recommend:

1. Switch to **prisma** chatmode
2. Add the createdBy field with a relation to User model
3. Generate the migration
4. Return to **nestjs** chatmode
5. I'll help you update the service to set createdBy on post creation

Would you like to switch to the prisma specialist now?"
```

### How to Handle Handoffs

When you receive a handoff recommendation:

1. ✅ **Accept it** - The specialist knows their boundaries
2. 📝 **Note the context** - Remember what needs to be done
3. 🔄 **Switch specialists** - Move to the recommended specialist
4. 📢 **Provide context** - Tell the new specialist what you need
5. 🔙 **Return when ready** - Come back to continue the work

## 🔍 Recognizing Patterns

### Pattern 1: Data-First Features

When a feature needs new data:
```
Prisma (schema) → NestJS (logic) → API (docs) → Testing (tests)
```

### Pattern 2: Infrastructure Changes

When deployment needs change:
```
Docker (container) → GitHub Actions (automation) → Documentation (guide)
```

### Pattern 3: API Redesign

When API needs evolution:
```
API (design) → NestJS (implementation) → Testing (validation) → Documentation (update)
```

### Pattern 4: New Package

When adding a workspace package:
```
Monorepo (structure) → [Domain Specialist] (implementation) → GitHub Actions (CI) → Documentation (guide)
```

## 💬 Communication Tips

### With Specialists

**Be specific**:
- ✅ "Add email validation to User model"
- ❌ "Fix the user thing"

**Provide context**:
- ✅ "The UserService needs to hash passwords before saving to the database"
- ❌ "Hash passwords"

**Trust boundaries**:
- ✅ Accept handoff recommendations
- ❌ Ask specialist to work outside their domain

### Asking Questions

**Good questions**:
- "What's the best way to structure authentication in NestJS?"
- "How should I model a many-to-many relationship in Prisma?"
- "What's the optimal Docker setup for development?"

**Questions that trigger handoffs**:
- "How do I add a database field?" (NestJS → Prisma)
- "How do I deploy this?" (NestJS → Docker)
- "How do I document this API?" (NestJS → API)

## 🛠️ Troubleshooting

### Specialist seems confused about domain

**Solution**: Clarify your question with more specific details about what you're trying to achieve.

### Not sure which specialist to start with

**Solution**: Consult `.github/SPECIALISTS.md` for a decision tree, or start with the specialist for your primary task.

### Handoff seems unnecessary

**Solution**: Trust the specialist's judgment. Specialists are designed to recognize boundaries for safety and quality.

### Need multiple changes across domains

**Solution**: Work with specialists sequentially. Start with the foundational changes (usually Prisma), then move up the stack.

## 📚 Learning Resources

### Understanding the System

1. **Start here**: `.github/README.md` - System overview
2. **Quick reference**: `.github/SPECIALISTS.md` - Which specialist to use
3. **Visual guide**: `.github/ARCHITECTURE.md` - How it all works
4. **Deep dive**: `.github/instructions/global.md` - Complete rules

### Understanding Each Specialist

Each specialist has two files:

1. **Chatmode** (`.github/chatmodes/[name].md`) - Full profile and expertise
2. **Prompt** (`.github/prompts/[name]-prompt.md`) - Quick operational guide

### Best Practices

Read the "Best Practices" section in each specialist's chatmode file to understand:
- Recommended patterns
- Common anti-patterns
- Integration points
- Quality standards

## 🎓 Advanced Usage

### Working on Complex Features

For features spanning multiple domains:

1. **Plan the flow**: Identify all specialists needed
2. **Start with data**: Usually begins with Prisma
3. **Build up**: Move through the stack systematically
4. **Test continuously**: Involve Testing specialist early
5. **Document as you go**: Keep Documentation specialist updated

### Optimizing Workflow

- **Batch similar work**: Do all Prisma schema changes together
- **Follow natural flow**: Data → Logic → API → Tests → Docs
- **Keep context**: Take notes during handoffs
- **Validate frequently**: Test after each specialist's work

### Handling Emergencies

When debugging urgent issues:

1. **Identify the domain**: Where is the problem?
2. **Start with that specialist**: Go directly to the expert
3. **Follow diagnosis**: Let specialist identify root cause
4. **Hand off if needed**: Problem might be in another domain

## ✅ Success Checklist

You're using the system effectively when:

- [ ] You consistently start with the right specialist
- [ ] You follow handoff recommendations without hesitation
- [ ] You provide clear context when switching specialists
- [ ] You understand why handoffs are happening
- [ ] Your code follows domain-specific best practices
- [ ] You complete features using multiple specialists smoothly
- [ ] You document your work with Documentation specialist
- [ ] You add tests with Testing specialist

## 🤝 Contributing

If you notice:
- A specialist overstepping boundaries
- Missing handoff recommendations
- Inconsistent advice
- Unclear documentation

Please:
1. Document the issue
2. Suggest improvements
3. Update relevant files
4. Test the changes

## 🎯 Remember

- **Specialists are experts**: Trust their deep knowledge
- **Boundaries are features**: They ensure quality and safety
- **Handoffs are normal**: They're part of professional collaboration
- **You're in control**: All handoffs require your approval
- **The system evolves**: It improves with use and feedback

---

**Need help?** Start with `.github/SPECIALISTS.md` for a quick reference on which specialist to consult!

**Ready to start?** Pick your first task and choose your specialist. The system will guide you from there.

**Have feedback?** The specialists welcome improvements to better serve your needs!
