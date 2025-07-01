# Claude Next.js DevContainer Template

A Next.js starter template with a fully configured DevContainer environment optimized for Claude Code integration.

## Tech Stack (技術スタック)

Tech stack intended for building with this template:

このテンプレートを使用して構築することを想定している技術スタック：

- **Frontend**
  - Next.js 14+ (React framework with App Router)
  - TypeScript for type safety
  - Tailwind CSS for styling
  - shadcn/ui component library
- **Backend**
  - Next.js API Routes
  - Supabase integration ready
- **Infrastructure**
  - Docker DevContainer environment
  - Claude Code optimized development setup

## Quick Start (クイックスタート)

### Using Docker (Recommended)

```bash
# Clone the template
git clone <your-repo-url> my-nextjs-app
cd my-nextjs-app

# Start development environment
docker compose up -d

# Enter the container
docker compose exec nextjs-dev zsh

# After setting up your Next.js application:
# npm install
# npm run dev
```

### Using Claude Code

This template is optimized for Claude Code development:

```bash
# Inside the container
claude
```

## Project Structure (プロジェクト構造)

```
claude-nextjs-devcontainer-template/
├── .devcontainer/          # DevContainer configuration
├── .gitignore             # Git ignore rules
├── CLAUDE.md              # Claude Code project guidance
├── README.md              # Project documentation
├── compose.yml            # Docker Compose configuration
└── package.json           # Node.js project configuration
```

This template provides the foundation for a Next.js project. After setup, you'll typically create:

```
├── app/                   # Next.js App Router (to be created)
├── components/            # React components (to be created)
├── lib/                   # Utilities and configurations (to be created)
└── public/                # Static assets (to be created)
```

## Claude Code Integration (Claude Code統合)

This template includes:

- **CLAUDE.md** with comprehensive project guidance
- **DevContainer** configuration for consistent development
- **Docker environment** with persistent volumes

**DevContainer Reference:**
This DevContainer configuration is based on: https://github.com/kenfdev/claude-code-todo-app/tree/main/.devcontainer

**Note:** The reference URL takes priority for the latest configuration updates.

**Main Differences:**
- **DevContainer Setup**: Reference uses dockerComposeFile (docker-compose.yml), this template uses build.dockerfile
- **Compose File Name**: Reference uses docker-compose.yml, this template uses compose.yml
- **Compose Configuration**: This template extends the reference with Next.js-focused features (port 3000, SSH access, node_modules cache, etc.)
- **Playwright (E2E Testing)**: Reference includes browser testing capabilities
- **Claude CLI**: This template focuses on Claude Code integration
- **Firewall Configuration**: Network control features (unique to this template)

**Claude Code Best Practices:**
https://www.anthropic.com/engineering/claude-code-best-practices

## License (ライセンス)

MIT License - see [LICENSE](LICENSE) file for details.