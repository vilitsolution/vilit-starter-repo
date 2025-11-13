# Specialist Quick Reference

Use this guide to quickly identify which specialist you need for your task.

## 🎯 Which Specialist Do I Need?

### Working with Application Code?
→ **NestJS Specialist** (`chatmodes/nestjs.md`)
- Creating services, controllers, modules
- Implementing guards, pipes, interceptors
- Dependency injection
- NestJS configuration

### Working with Database?
→ **Prisma Specialist** (`chatmodes/prisma.md`)
- Creating or modifying schema
- Adding database relationships
- Creating migrations
- Database optimization

### Working with Containers?
→ **Docker Specialist** (`chatmodes/docker.md`)
- Writing Dockerfiles
- Docker Compose configuration
- Swarm stack setup
- Container deployment

### Designing APIs?
→ **API Specialist** (`chatmodes/api.md`)
- REST endpoint design
- OpenAPI/Swagger specs
- API versioning
- Request/response contracts

### Writing Documentation?
→ **Documentation Specialist** (`chatmodes/documentation.md`)
- README files
- Setup guides
- Architecture docs
- User tutorials

### Writing Tests?
→ **Testing Specialist** (`chatmodes/testing.md`)
- Test strategy
- Unit/Integration/E2E tests
- Test data management
- Coverage optimization

### Working with Workspace?
→ **Monorepo Specialist** (`chatmodes/monorepo.md`)
- Workspace structure
- pnpm configuration
- Turborepo setup
- Build optimization

### Setting up CI/CD?
→ **GitHub Actions Specialist** (`chatmodes/github-actions.md`)
- Workflow definitions
- Automated builds
- Test automation
- Deployment pipelines

## 🔄 Common Task Flows

### Adding a New Feature
1. **Prisma**: Define data models
2. **NestJS**: Implement service and controller
3. **API**: Document endpoints
4. **Testing**: Write tests
5. **Documentation**: Update README

### Setting Up Authentication
1. **Prisma**: Create User model
2. **NestJS**: Implement AuthService and Guards
3. **API**: Design auth endpoints
4. **Testing**: Write auth tests
5. **Docker**: Configure secrets

### Deploying to Production
1. **Docker**: Optimize Dockerfile and stack
2. **GitHub Actions**: Set up deployment workflow
3. **Documentation**: Update deployment guide

### Adding a New Package
1. **Monorepo**: Configure workspace
2. **[Relevant Specialist]**: Implement package
3. **GitHub Actions**: Add to CI pipeline
4. **Documentation**: Document package

## 💡 Pro Tips

- **Start with data**: If your feature needs database changes, start with Prisma
- **Think contracts**: Design API contracts before implementation
- **Test early**: Involve Testing specialist early in feature development
- **Document continuously**: Keep Documentation specialist updated
- **Automate**: Use GitHub Actions specialist to automate repetitive tasks

## 🚫 Anti-Patterns

- ❌ Asking NestJS specialist to modify Prisma schema
- ❌ Asking Docker specialist to implement application logic
- ❌ Asking API specialist to write controller code
- ❌ Skipping handoffs and trying to do everything in one specialist

## ✅ Best Practices

- ✅ Start with the right specialist for your primary task
- ✅ Follow handoff recommendations when boundaries are crossed
- ✅ Provide context when switching specialists
- ✅ Trust specialists' boundary recognition
- ✅ Read the global instructions for deeper understanding

## 📖 Learn More

- Read `instructions/global.md` for complete system rules
- Check each `chatmodes/*.md` file for specialist details
- Review `prompts/*-prompt.md` for operational context
- See `.github/README.md` for system overview
