# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Claude Next.js DevContainer Template** is a Next.js starter template with a fully configured DevContainer environment optimized for Claude Code integration.

## Development Environment

### Container-Based Development (Recommended)
This project uses Docker Compose with DevContainer configuration:

```bash
# Start development environment
docker compose up -d

# Enter the container
docker compose exec nextjs-dev zsh

# Stop environment
docker compose down
```

- **Application URL**: http://localhost:3000 (after Next.js setup)
- **Container**: `nextjs-dev` (Node.js 20 base)
- **Working Directory**: `/workspace`
- **User**: `node` (non-root)
- **Timezone**: Asia/Tokyo

### Development Tools Pre-configured
- **Shell**: zsh with powerline10k theme
- **Git tools**: GitLens extension available
- **VS Code Extensions**: ESLint, Prettier, GitLens (configured in devcontainer.json)

## Tech Stack (Template Ready For)

This template is prepared for setting up:

### Frontend Stack
- **Next.js**: React-based framework with App Router
- **TypeScript**: Type-safe development
- **Tailwind CSS**: Utility-first styling
- **shadcn/ui**: Component library built on Radix UI

### Backend Integration
- **API Routes**: Next.js API routes structure
- **Database**: Ready for Supabase PostgreSQL integration
- **Authentication**: Ready for Supabase Auth
- **File Storage**: Ready for Supabase Storage

### Deployment
- **Hosting**: Prepared for Vercel deployment
- **Database**: Ready for Supabase cloud infrastructure

## Current Project Structure

```
claude-nextjs-devcontainer-template/
├── .devcontainer/          # DevContainer configuration
│   ├── .devcontainer.json  # VS Code DevContainer settings
│   └── Dockerfile          # Container build configuration
├── .gitignore             # Git ignore rules
├── CLAUDE.md              # Claude Code project guidance
├── README.md              # Project documentation
├── compose.yml            # Docker Compose configuration
└── package.json           # Node.js project configuration (with Next.js scripts)
```

## Container Architecture

### Volume Management
- `claude-code-bashhistory`: Persistent command history
- `claude-code-config`: Claude configuration storage
- `node_modules_cache`: Node.js dependencies caching
- `gh-config`: GitHub CLI configuration

### Container Environment Variables
- `NODE_OPTIONS`: `--max-old-space-size=4096` for memory optimization
- `CLAUDE_CONFIG_DIR`: `/home/node/.claude`
- `TZ`: Asia/Tokyo

### Network Configuration
- Port 3000 exposed for Next.js development server
- Network capabilities (NET_ADMIN, NET_RAW) available

## Development Workflow

1. **Project Setup**: Use Docker Compose for consistent development environment
2. **Next.js Setup**: Install Next.js and configure your application structure
3. **Code Organization**: Follow Next.js 13+ App Router conventions (when implemented)
4. **Development**: Use Claude Code within the container environment

## Git Configuration

### .gitignore
The project includes a comprehensive `.gitignore` file that excludes:
- Node.js dependencies (`node_modules/`)
- Next.js build outputs (`.next/`, `/out/`)
- Environment files (`.env*.local`)
- IDE configurations (`.vscode/`, `.idea/`)
- Claude Code configuration (`.claude/`)
- Build artifacts, logs, and temporary files

## Troubleshooting

### Permission Errors with node_modules (node_modulesの権限エラー)

**Problem**: `EACCES: permission denied, mkdir '/workspace/node_modules'`

**Solution**:
```bash
# コンテナを停止してボリュームを削除
docker compose down
docker volume rm claude-nextjs-devcontainer-template-fin_node_modules_cache

# コンテナを再起動
docker compose up -d
docker compose exec nextjs-dev zsh
npm install
```

**Note**: Dockerコマンドはホストマシンで実行してください。コンテナ内では実行できません。

## Git Workflow

### Branch Strategy
- **main**: Production-ready code
- **feature branches**: Named descriptively (e.g., `feature/user-auth`, `feature/api-integration`)

### Commit Guidelines
- Use conventional commits format: `type(scope): description`
- Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`
- **Bilingual commit messages**: Use both English and Japanese with bullet points
- Format structure:
  ```
  type: brief description
  
  - English bullet point 1
  - English bullet point 2
  - English bullet point 3
  
  - 日本語の箇条書き 1
  - 日本語の箇条書き 2
  - 日本語の箇条書き 3
  
  🤖 Generated with [Claude Code](https://claude.ai/code)
  Co-Authored-By: Claude <noreply@anthropic.com>
  ```
- Examples:
  - `feat(auth): add user registration flow`
  - `fix(ui): resolve mobile layout issues`
  - `docs: update API documentation`

### Pre-commit Workflow
**IMPORTANT**: Always follow this procedure before committing. Always run `git pull origin main` first to get the latest changes from the main branch:
```bash
# 1. MANDATORY: Pull latest changes from remote first
git pull origin main

# 2. Run code quality checks (after setting up Next.js)
# npm run lint
# npm run type-check
# npm run test

# 3. Stage and commit changes
git add .
git commit -m "your commit message"

# 4. Push to remote
git push origin your-branch
```

Note: Code quality commands will be available after Next.js application setup.