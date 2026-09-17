---
title: "Arquitetura de um servidor MCP para agentes de desenvolvimento"
description: "Como organizei ferramentas, contexto, Git e segurança no Agentic MCP para trabalhar com repositórios locais sem transformar o agente em um shell irrestrito."
publishedAt: 2026-09-17
tags: ["MCP", "Agentes de IA", "TypeScript", "Engenharia de Software"]
draft: false
---

Quando comecei a trabalhar com agentes de código sobre projetos reais, ficou claro que gerar código era apenas uma parte do problema. O agente também precisava **entender o repositório, localizar referências, editar com precisão, executar verificações e deixar mudanças revisáveis**.

Foi a partir dessa necessidade que desenvolvi o **Agentic MCP**, um servidor Model Context Protocol voltado ao trabalho com repositórios locais.

## Ferramentas especializadas em vez de uma única interface genérica

Uma decisão importante foi separar operações por intenção. Ler um arquivo, localizar um símbolo, mostrar um diff e executar um comando têm riscos e necessidades de contexto diferentes.

Em vez de tratar tudo como shell, o servidor expõe ferramentas específicas para tarefas recorrentes. Isso permite respostas estruturadas e reduz a quantidade de texto que o agente precisa interpretar.

## Contexto é um recurso limitado

Outro problema aparece rapidamente em bases de código maiores: ler arquivos demais não torna o agente necessariamente mais capaz. Muitas vezes acontece o contrário.

Por isso, parte da arquitetura passou a priorizar **busca delimitada, mapas estruturais, leitura comprimida e pacotes semânticos de contexto**. A ideia é fornecer o contexto necessário para a decisão atual, e não tentar colocar o repositório inteiro dentro da conversa.

## Git como mecanismo de segurança e revisão

Git não serve apenas para versionamento. Em fluxos com agentes, ele também funciona como uma camada operacional de controle.

O Agentic MCP utiliza status, diff, checkpoints e worktrees para separar alterações, tornar mudanças inspecionáveis e preservar caminhos de reversão. Tarefas paralelas podem acontecer em worktrees diferentes sem exigir que o agente misture estados do projeto principal.

## Segurança proporcional à operação

Nem toda ação merece o mesmo nível de restrição. Uma busca textual tem um risco muito diferente de um comando que altera infraestrutura ou dados.

A arquitetura procura refletir essa diferença com políticas por tipo de operação, limites e pré-condições de edição. Isso evita dois extremos: tornar a ferramenta inutilizável por excesso de bloqueios ou transformar o agente em uma execução irrestrita sobre a máquina.

## O aprendizado principal

O ponto mais importante não foi adicionar mais ferramentas ao agente. Foi estruturar um ambiente em que **contexto, alteração, execução e revisão fazem parte do mesmo fluxo**.

Para mim, esse passou a ser um dos principais critérios para avaliar ferramentas de desenvolvimento assistido por IA: não apenas o que o modelo consegue gerar, mas quão bem o sistema ao redor dele permite entender, verificar e evoluir software real.
