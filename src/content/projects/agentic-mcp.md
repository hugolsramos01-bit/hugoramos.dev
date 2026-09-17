---
title: "Agentic MCP"
summary: "Servidor MCP open source para conectar agentes de IA a repositórios locais com edição estruturada, Git, shell controlado e navegação semântica."
order: 1
status: "Open source"
period: "2026 — atual"
role: "Criador e mantenedor"
stack: ["TypeScript", "Node.js", "Model Context Protocol", "Git", "AST"]
externalUrl: "https://github.com/hugolsramos01-bit/mcp-agentic-server"
featured: true
public: true
---

O **Agentic MCP** nasceu de uma necessidade prática: permitir que agentes de desenvolvimento trabalhem sobre repositórios locais com mais contexto, previsibilidade e controle do que um fluxo baseado apenas em leitura e escrita de arquivos.

O projeto implementa um servidor **Model Context Protocol (MCP)** com ferramentas para inspeção e edição estruturada de código, execução controlada de comandos, operações Git, worktrees isoladas, checkpoints e navegação semântica.

## O problema

Agentes de código precisam fazer mais do que gerar trechos isolados. Em tarefas reais, eles precisam entender a estrutura do projeto, localizar referências, modificar arquivos com segurança, executar verificações e deixar um caminho claro de revisão e reversão.

O Agentic MCP concentra essas capacidades em uma interface única, mantendo o repositório local como fonte de verdade.

## Decisões de engenharia

- ferramentas especializadas para leitura, busca, edição, Git e execução;
- edição estruturada com pré-condições para reduzir alterações sobre versões desatualizadas;
- suporte a **Git worktrees** para trabalho isolado e paralelo;
- navegação semântica e mapas estruturais para reduzir leitura desnecessária de arquivos;
- checkpoints e mecanismos de revisão antes de mudanças de maior impacto;
- políticas de segurança proporcionais ao tipo de operação.

## Tecnologias

O servidor é desenvolvido em **TypeScript e Node.js** e utiliza o Model Context Protocol como camada de integração com clientes e agentes compatíveis.

O projeto é público, distribuído como pacote e mantido como uma ferramenta de desenvolvimento de propósito geral.
