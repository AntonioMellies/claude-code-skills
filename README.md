# claude-code-skills

Repositório central de skills customizadas para o [Claude Code](https://claude.ai/code). Cada skill fica em sua própria pasta com um arquivo `SKILL.md` — basta copiar esse arquivo para o ambiente desejado para ativá-la.

## Pré-requisitos

- [Claude Code](https://claude.ai/code) instalado
- Terminal com acesso a PowerShell (Windows) ou Bash (macOS/Linux)

---

## Skills disponíveis

| Skill | Pasta | Quando usar | Referência |
|---|---|---|---|
| Clean Architecture Expert | `skills/clean-architecture-expert/` | Projetar camadas, modelar DDD, avaliar Dependency Rule | *Arquitetura Limpa* — Robert C. Martin |
| Clean Code Expert | `skills/clean-code-expert/` | Revisar código, refatorar nomes/funções, definir padrões de implementação | *Código Limpo* — Robert C. Martin |
| Architecture Hard Parts Expert | `skills/architecture-hard-parts-expert/` | Decidir entre alternativas arquiteturais, documentar ADRs, analisar trade-offs | *Software Architecture: The Hard Parts* — Ford, Richards et al. |
| Production-Ready Microservices Expert | `skills/production-ready-microservices-expert/` | Avaliar prontidão para produção, projetar observabilidade, resiliência e deploy | *Microsserviços Prontos para a Produção* — Susan J. Fowler |

---

## Como instalar

### Passo 1 — Obter o repositório

```bash
git clone <url-do-repositorio>
cd claude-code-skills
```

### Passo 2 — Instalar as skills

Cada skill é instalada copiando seu `SKILL.md` para o diretório de skills do Claude Code, renomeado com o nome da skill.

**Uso global** (disponível em todas as sessões e projetos):

**Windows (PowerShell)**
```powershell
# Criar pasta global se não existir
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills"

# Instalar uma skill específica
Copy-Item "skills\clean-architecture-expert\SKILL.md" `
  "$env:USERPROFILE\.claude\skills\clean-architecture-expert.md"

# Instalar todas as skills de uma vez
Get-ChildItem "skills" -Directory | Where-Object { $_.Name -ne "_template" } | ForEach-Object {
  Copy-Item "$($_.FullName)\SKILL.md" `
    "$env:USERPROFILE\.claude\skills\$($_.Name).md"
}
```

**macOS / Linux**
```bash
# Criar pasta global se não existir
mkdir -p ~/.claude/skills

# Instalar uma skill específica
cp skills/clean-architecture-expert/SKILL.md \
   ~/.claude/skills/clean-architecture-expert.md

# Instalar todas as skills de uma vez
for dir in skills/*/; do
  name=$(basename "$dir")
  [[ "$name" == "_template" ]] && continue
  cp "$dir/SKILL.md" ~/.claude/skills/"$name".md
done
```

**Uso por projeto** (disponível apenas no projeto atual):

Copie o `SKILL.md` para `.claude/skills/` na raiz do projeto:

```
meu-projeto/
  .claude/
    skills/
      clean-architecture-expert.md
      clean-code-expert.md
```

### Passo 3 — Verificar a instalação

Abra o Claude Code, digite `/` no prompt e confirme que as skills aparecem na lista de sugestões.

---

## Como usar uma skill

Com a skill instalada, invoque pelo nome no prompt:

```
/clean-architecture-expert
```

O Claude assume o papel definido na skill e mantém esse comportamento durante toda a sessão.

---

## Estrutura de cada skill

```
skills/
  <nome-da-skill>/
    SKILL.md          ← arquivo que será copiado para o Claude Code
    examples/         ← exemplos e templates de apoio (não são skills)
      *.md
```

O arquivo `SKILL.md` contém frontmatter YAML com `name` e `description`, seguido das instruções da skill. Os arquivos em `examples/` são material de referência para copiar para o seu projeto.

---

## Como adicionar uma nova skill

1. Copie a pasta `skills/_template/` e renomeie para `skills/<nome-da-skill>/`
2. Edite `SKILL.md` preenchendo todas as seções obrigatórias
3. Crie a pasta `examples/` com pelo menos um arquivo de apoio
4. Adicione uma linha na tabela de skills acima
5. Se houver livro de referência, adicione o PDF em `references/books/` com o padrão `Título - Autor.pdf`

### Estrutura obrigatória do SKILL.md

```markdown
---
name: nome-da-skill
description: Atua como [papel]. [Foco principal em uma linha].
---

## Quando usar esta skill
## Mentalidade Principal
## [Seções específicas]
## Anti-Padrões
## Comportamento Esperado
## Regra Máxima
```

---

## Como desinstalar uma skill

```powershell
# Windows
Remove-Item "$env:USERPROFILE\.claude\skills\nome-da-skill.md"
```
```bash
# macOS / Linux
rm ~/.claude/skills/nome-da-skill.md
```

---

## Estrutura do repositório

```
skills/
  clean-architecture-expert/
    SKILL.md
    examples/
      hexagonal-structure.md
      use-case-example.md
  clean-code-expert/
    SKILL.md
    examples/
      before-after.md
  architecture-hard-parts-expert/
    SKILL.md
    examples/
      trade-off-table.md
      adr-template.md
  production-ready-microservices-expert/
    SKILL.md
    examples/
      production-checklist.md
      observability-setup.md
  _template/
    SKILL.md
references/
  books/
    Arquitetura Limpa - Robert C. Martin.pdf
    Código Limpo - Robert C. Martin.pdf
    Software Architecture The Hard Parts - Ford, Richards et al.pdf
    Microsserviços Prontos para a Produção - Susan J. Fowler.pdf
CLAUDE.md
README.md
```
