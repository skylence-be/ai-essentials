# AI Essentials

Meta-package with essential AI agent tooling for Laravel projects. One install, everything you need.

## Installation

```bash
composer require skylence/ai-essentials
```

## What's Included

| Package | What it does |
|---------|-------------|
| [laravel/ai](https://github.com/laravel/ai) | Laravel AI SDK — text generation, tool-calling agents, embeddings |
| [laravel/boost](https://github.com/laravel/boost) | MCP server helping AI agents discover and interact with your Laravel app |
| [nunomaduro/pao](https://github.com/nunomaduro/pao) | Agent-optimized output for PHPUnit, Pest, Paratest, PHPStan |
| [skylence/laravel-artisan-agent-output](https://github.com/skylence-be/laravel-artisan-agent-output) | Agent-optimized output for Laravel Artisan commands |
| [skylence/laravel-model-inspector-mcp](https://github.com/skylence-be/laravel-model-inspector-mcp) | MCP server for Eloquent model inspection |
| [skylence/laravel-optimize-mcp](https://github.com/skylence-be/laravel-optimize-mcp) | MCP server for Laravel optimization insights |
| [skylence/laravel-telescope-mcp](https://github.com/skylence-be/laravel-telescope-mcp) | MCP server for Laravel Telescope data |

Zero config. Install and all tools automatically optimize their output when an AI agent is detected.

## MCP Server Setup

The MCP servers ship as dev dependencies — run `composer install` (not `--no-dev`) to get them.

### Laravel Boost

Laravel Boost provides AI guidelines, skills, and an MCP server for your project.

**Install the package:**

```bash
composer require laravel/boost --dev
```

**Run the installer** (auto-detects Claude Code, Cursor, VS Code, PhpStorm):

```bash
php artisan boost:install
```

This configures AI guidelines, agent skills, and the MCP server in one step.

**Manual MCP setup** (if you skip the installer):

Add to `.mcp.json` in the project root:

```json
{
    "mcpServers": {
        "boost": {
            "command": "php",
            "args": ["artisan", "boost:mcp"]
        }
    }
}
```

### Model Inspector MCP

Gives AI assistants deep introspection into Eloquent models, relationships, and schema.

**Install the package:**

```bash
composer require skylence/laravel-model-inspector-mcp --dev
```

**Run the installer** (auto-detects your editor):

```bash
php artisan model-inspector:install
```

**Manual MCP setup:**

```json
{
    "mcpServers": {
        "laravel-model-inspector-mcp": {
            "command": "php",
            "args": ["artisan", "model-inspector:mcp"]
        }
    }
}
```

Using Laravel Sail? Replace `php` with `./vendor/bin/sail`.

### Optimize MCP

Analyzes your Laravel config, structure, and database for performance and security insights.

**Install the package:**

```bash
composer require skylence/laravel-optimize-mcp --dev
```

**Run the installer** (auto-detects your editor, optionally configures HTTP access for staging/production):

```bash
php artisan optimize-mcp:install
```

### Telescope MCP

Real-time monitoring, performance analysis, and debugging through Laravel Telescope.

Requires [Laravel Telescope](https://laravel.com/docs/telescope) to be installed first.

**Install the package:**

```bash
composer require skylence/laravel-telescope-mcp --dev
```

**Manual MCP setup** (add to `.mcp.json`):

```json
{
    "mcpServers": {
        "telescope": {
            "type": "stdio",
            "command": "php",
            "args": ["artisan", "mcp:start", "telescope"]
        }
    }
}
```

Restart your editor/AI tool after updating `.mcp.json`.

## License

MIT
