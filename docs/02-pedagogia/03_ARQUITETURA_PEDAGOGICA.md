# 03_ARQUITETURA_PEDAGOGICA.md

# Arquitetura Pedagógica

**GPA – Gamificação Pedagógica de Aprendizagens**  
**Documento:** Arquitetura Pedagógica 
**Versão:** 0.2.0
**Área:** Pedagogia

---

# 1. Introdução

Este documento apresenta a arquitetura pedagógica que orienta o desenvolvimento da ferramenta.

Seu objetivo é definir como os conhecimentos serão organizados e de que maneira as atividades propostas contribuirão para o processo de alfabetização.

A arquitetura pedagógica constitui a base conceitual do projeto e deverá permanecer independente da tecnologia utilizada para implementação.

---

# 2. Princípio Central

A ferramenta parte de um princípio simples:

> Um mesmo conhecimento pode ser representado por diferentes formas de linguagem.

Uma criança não aprende apenas palavras. Ela aprende relações entre diferentes formas de representar um mesmo conceito.

Exemplo:

- a palavra **GATO**;
- a imagem de um gato;
- o som da palavra "gato".

Essas representações apontam para o mesmo conceito.

---

# 3. Representações do Conhecimento

Na primeira versão, cada conceito será representado por três modalidades:

- Representação Textual: palavra escrita;
- Representação Visual: imagem;
- Representação Auditiva: áudio.

---

# 4. Objeto Pedagógico

Cada unidade de conteúdo será organizada como um Objeto Pedagógico.

Um Objeto Pedagógico reúne as representações de um mesmo conceito.

Exemplo:

```text
Conceito: GATO

Representações:
- Palavra escrita: GATO
- Imagem: gato.png
- Áudio: gato.mp3
```

---

# 5. Associação Trimodal

O primeiro módulo utiliza a estratégia denominada Associação Trimodal.

A atividade consiste em estabelecer relações entre três modalidades distintas de representação.

Não se trata de procurar cartas iguais, mas de encontrar representações diferentes que possuem o mesmo significado.

---

# 6. Organização da Aprendizagem

A arquitetura pedagógica organiza-se em quatro níveis:

```text
Conceito
    ↓
Representações
    ↓
Atividade
    ↓
Indicadores
```

---

# 7. Papel do Professor

O professor atua como mediador do processo.

Compete ao professor:

- selecionar conteúdos;
- organizar atividades;
- interpretar indicadores;
- planejar intervenções pedagógicas.

---

# 8. Papel da Ferramenta

Compete à ferramenta:

- apresentar atividades;
- registrar interações;
- validar associações;
- gerar indicadores;
- organizar evidências.

A ferramenta não substitui a avaliação docente.

---

# 9. Evolução da Arquitetura

A arquitetura foi concebida para permitir crescimento futuro.

Novas modalidades poderão ser incorporadas sem alteração dos princípios pedagógicos, desde que permaneçam vinculadas ao mesmo conceito.

---

# 10. Considerações Finais

A Arquitetura Pedagógica representa o núcleo conceitual da ferramenta.

Todas as atividades, indicadores, relatórios e futuras expansões deverão respeitar os princípios definidos neste documento.
