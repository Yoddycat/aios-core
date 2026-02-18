# MCP Servers - Configuração AIOS

## Status da Configuração

✅ **Configurado em:** `~/.claude/mcp.json`

## MCP Servers Instalados

| Server | Status | Descrição | Comando |
|--------|--------|-----------|---------|
| **github** | ✅ Configurado | GitHub API integration | `@modelcontextprotocol/server-github` |
| **playwright** | ✅ Configurado | Browser automation | `@executeautomation/playwright-mcp-server` |
| **filesystem** | ✅ Configurado | File operations | `@modelcontextprotocol/server-filesystem` |

## Como Ativar

Os MCP servers são iniciados automaticamente pelo Claude Code quando você:
1. Reinicia o Claude Code CLI
2. Os servers são carregados na primeira vez que são necessários

## Testando os MCPs

Após reiniciar o Claude Code, teste com:

```bash
# No Claude Code, pergunte:
"Liste os repositórios da minha conta GitHub"  # Testa github MCP
"Tire um screenshot da página https://google.com"  # Testa playwright MCP
"Liste os arquivos em /Users/edilson/aios-core"  # Testa filesystem MCP
```

## Troubleshooting

### MCPs não carregam
1. Verifique se Node.js está instalado: `node --version`
2. Verifique se npx funciona: `npx --version`
3. Limpe o cache: `rm -rf ~/.npm/_npx`
4. Reinicie o Claude Code

### Playwright falha
- Primeira execução demora (baixa browsers)
- Requer ~1GB de espaço em disco
- Aguarde instalação completa

### GitHub MCP falha
- Verifique o token em `~/.claude/mcp.json`
- Token precisa ter permissões: `repo`, `read:org`
- Gere novo token em: https://github.com/settings/tokens

## Adicionar Mais MCPs (Futuro)

Para adicionar EXA (web search):
1. Obter API key: https://exa.ai
2. Adicionar em `~/.claude/mcp.json`:

```json
"exa": {
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-exa"],
  "env": {
    "EXA_API_KEY": "sua-chave-aqui"
  }
}
```

---

*Configurado automaticamente em: 2026-02-18*
