# 20. Experiência do Usuário

# Experiência do Usuário

**GPA – Gamificação Pedagógica de Aprendizagens**  
**Documento:** Experiência do Usuário (UX)  
**Versão:** 1.3.3
**Área:** Engenharia
**Documento relacionado:** `15_CASOS_DE_USO.md`
                         - `16_ARQUITETURA_MULTIPLATAFORMA.md`
                         - `17_FLUXOS_DA_APLICACAO.md`
                         - `19_DASHBOARDS.md`

---

# 1. Objetivo

Este documento estabelece as diretrizes de Experiência do Usuário (UX) do GPA, garantindo uma interface simples, acessível, lúdica e coerente com os objetivos pedagógicos da alfabetização.

---

# 2. Princípios de UX

O GPA deverá priorizar:

- Simplicidade
- Clareza visual
- Acessibilidade
- Feedback imediato
- Navegação intuitiva
- Consistência entre plataformas
- Foco pedagógico
- Ludicidade sem distrações

---

# 3. Arquitetura da Experiência do Usuário

**Diagrama de referência**

```text
../assets/ux/arquitetura-experiencia-usuario-gpa.png
```

O diagrama representa a jornada dos perfis, interfaces, feedbacks, gamificação, dashboards e fluxo geral da experiência.

---

# 4. Perfis de Usuário

- Administrador
- Órgão Central da Rede de Ensino
- Diretor / Coordenador Pedagógico
- Professor
- Estudante
- Pais / Responsáveis

Cada perfil possui interfaces, permissões e jornadas específicas.

---

# 5. Workspace do Professor

- Dashboard
- Turmas
- Planejamento
- Sequências Didáticas
- Objetos Pedagógicos
- Atividades
- Indicadores
- Relatórios
- Configurações

---

# 6. Workspace do Estudante

- Atividade atual
- Cartas Pedagógicas
- Imagem
- Texto
- Áudio
- Feedback
- Progresso
- Avatar
- Níveis
- Conquistas
- Recompensas

---

# 7. Carta Pedagógica

Elementos:

- imagem principal
- palavra
- botão/área de toque
- feedback visual
- áudio direto
- áudio fragmentado

Regra de interação:

```text
1º toque → áudio direto
2º toque → áudio fragmentado
3º toque → áudio direto
4º toque → áudio fragmentado
```

---

# 8. Acessibilidade

O sistema deverá oferecer:

- alto contraste
- tipografia legível
- botões grandes
- áreas adequadas ao toque
- áudio de qualidade
- navegação por teclado
- compatibilidade com leitores de tela quando aplicável
- linguagem simples

---

# 9. Responsividade

A interface adapta-se automaticamente para:

- Desktop
- Web
- Tablet
- Smartphone

Mantendo consistência visual e funcional.

---

# 10. Feedback ao Estudante

O feedback deve ser:

- imediato
- positivo
- pedagógico
- claro
- não punitivo

Exemplos:

```text
"Muito bem! Vamos tentar outra palavra."
"Quase! Ouça novamente e tente outra vez."
```

---

# 11. Gamificação na Experiência

Elementos:

- Avatar
- Personagens
- Níveis
- Conquistas
- Recompensas
- Sons
- Animações leves

A gamificação deve reforçar o aprendizado, nunca competir com ele.

---

# 12. Design System

O GPA utilizará componentes reutilizáveis, identidade visual padronizada, tipografia consistente, ícones unificados, espaçamentos regulares e feedback visual uniforme em todas as plataformas.

---

# 13. Relação com os Demais Documentos

Este documento complementa:

- 15_CASOS_DE_USO.md
- 16_ARQUITETURA_MULTIPLATAFORMA.md
- 17_FLUXOS_DA_APLICACAO.md
- 19_DASHBOARDS.md

---

# 14. Considerações Finais

A experiência do usuário constitui um dos pilares do GPA. Todas as decisões de interface devem favorecer a aprendizagem, a acessibilidade, o engajamento e a simplicidade de uso, preservando o foco pedagógico em todas as plataformas.
