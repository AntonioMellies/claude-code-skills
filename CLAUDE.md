# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Este repositório é uma **biblioteca de skills** para Claude Code. Não usa skills — distribui skills para outros projetos e usuários instalarem. Cada skill vive em `skills/<nome>/SKILL.md`.

## Estrutura

```
skills/
  <nome-da-skill>/
    SKILL.md        ← arquivo instalável pelo usuário
    examples/       ← material de apoio (não é skill)
  _template/
    SKILL.md        ← ponto de partida para novas skills
references/
  books/            ← PDFs de referência, padrão: Título - Autor.pdf
```

## Skills disponíveis

```
skills/clean-architecture-expert/          ← Clean Arch, DDD, Hexagonal
skills/clean-code-expert/                  ← Clean Code, legibilidade
skills/architecture-hard-parts-expert/     ← Trade-offs, ADRs, sistemas distribuídos
skills/production-ready-microservices-expert/ ← Operação em produção
skills/_template/                          ← template para novas skills
```

## Formato obrigatório do SKILL.md

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

## Ao adicionar uma nova skill

1. Copiar `skills/_template/SKILL.md` para `skills/<nome>/SKILL.md`
2. Criar `skills/<nome>/examples/` com pelo menos um arquivo de apoio
3. Adicionar linha na tabela do `README.md`
4. Adicionar PDF de referência em `references/books/` com padrão `Título - Autor.pdf`
