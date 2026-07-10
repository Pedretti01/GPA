# GPA

## Ferramenta Multiplataforma de Apoio aos Processos de Ensino e Aprendizagem

> Uma ferramenta multiplataforma destinada ao planejamento, organização, aplicação e acompanhamento de recursos pedagógicos digitais, fundamentada em Objetos Pedagógicos, Atividades Parametrizadas, Gamificação Pedagógica e Learning Analytics.

![Status](https://img.shields.io/badge/status-em%20concepção-red)
![Arquitetura](https://img.shields.io/badge/arquitetura-modular-yellow)
![MVP](https://img.shields.io/badge/MVP-Alfabetização-orange)
![Plataformas](https://img.shields.io/badge/plataformas-Web%20%7C%20Desktop%20%7C%20Tablet%20%7C%20Mobile-blue)

---

# Sobre a GPA

A **GPA** é uma ferramenta concebida para apoiar professores e instituições de ensino na criação, organização, aplicação e acompanhamento de recursos pedagógicos digitais voltados aos processos de ensino e aprendizagem.

Seu propósito é produzir **evidências pedagógicas** que auxiliem o professor na observação do percurso de aprendizagem dos estudantes, preservando sua autonomia profissional.

Embora seja apresentada como uma **ferramenta**, sua implementação utiliza uma **arquitetura de plataforma modular**, permitindo sua expansão para diferentes áreas do conhecimento sem alterar seus princípios fundamentais.

---

# O problema que buscamos resolver

O acompanhamento individual da aprendizagem exige do professor:

- observar o desempenho dos estudantes;
- registrar dificuldades;
- identificar progressos;
- planejar intervenções pedagógicas;
- acompanhar a evolução ao longo do tempo.

Grande parte desse processo ainda depende de observações e registros manuais.

A GPA foi concebida para apoiar esse trabalho, registrando automaticamente indicadores produzidos durante as atividades e transformando essas informações em evidências pedagógicas.

A GPA **não substitui o professor** e **não realiza diagnósticos automáticos**.

---

# Missão

Apoiar professores por meio de recursos pedagógicos digitais fundamentados em evidências, contribuindo para o planejamento, acompanhamento e avaliação do processo de aprendizagem.

---

# Visão

Consolidar uma ferramenta educacional modular, multiplataforma e evolutiva, capaz de apoiar diferentes domínios pedagógicos utilizando uma arquitetura tecnológica comum.

---

# Princípios

- Fundamentação pedagógica;
- Apoio ao professor;
- Aprendizagem centrada no estudante;
- Objetos Pedagógicos;
- Atividades Parametrizadas;
- Gamificação Pedagógica;
- Learning Analytics;
- Produção de Evidências Pedagógicas;
- Modularidade;
- Evolução incremental;
- Multiplataforma.

---

# Ferramenta × Plataforma

Para evitar ambiguidades, a GPA adota dois conceitos complementares:

- **Ferramenta**: forma como a GPA é apresentada aos seus usuários (professores, gestores e pesquisadores).
- **Plataforma**: arquitetura interna utilizada para organizar os componentes reutilizáveis da solução.

---

# Arquitetura Conceitual

```text
GPA (Ferramenta)
        │
Arquitetura de Plataforma
        │
      Core
        │
 ┌──────|───────────┐──────────┐
 │                  │          │
Alfabetização   Matemática  Ciências
```

O **Core** concentra componentes reutilizáveis:

- Objetos Pedagógicos;
- Atividades Parametrizadas;
- Gamificação Pedagógica;
- Learning Analytics;
- Indicadores;
- Relatórios;
- Dashboards.

---

# Domínios Pedagógicos

A arquitetura da GPA permite a criação de diferentes Domínios Pedagógicos.

O primeiro domínio será:

## Alfabetização

Destinado ao apoio ao processo de alfabetização e desenvolvimento da leitura e escrita.

---

# Primeiro Módulo

## Associação Trimodal

Primeira atividade da GPA.

Relaciona três representações de um mesmo Objeto Pedagógico:

- Palavra Escrita;
- Imagem;
- Áudio.

A atividade registra:

- tempo de execução;
- tentativas;
- acertos;
- erros;
- indicadores de desempenho.

---

# Fundamentação Pedagógica

A proposta foi construída considerando, entre outras referências:

- Base Nacional Comum Curricular (BNCC);
- RENABE;
- Práticas de Alfabetização;
- estudos sobre Consciência Fonológica;
- estudos sobre Fluência Leitora;
- pesquisas sobre aprendizagem da leitura e escrita.

---

# Organização do Repositório

```text
GPA/
├── README.md
├── LICENSE
├── CHANGELOG.md
├── docs/
├── core/
├── domains/
│   ├── alfabetizacao/
│   ├── matematica/
│   └── ...
├── software/
├── assets/
└── research/
```

---

# Organização da Documentação

A documentação da GPA está organizada em áreas temáticas, permitindo que aspectos pedagógicos, técnicos e de governança evoluam de forma independente, mantendo uma estrutura consistente e de fácil navegação.

```text
docs/

📘 01-fundamentos/
    Manifesto
    Visão do Projeto
    Fundamentação Pedagógica

🎓 02-pedagogia/
    Arquitetura Pedagógica
    Objetos Pedagógicos
    Associação Trimodal
    Gamificação
    Indicadores
    Relatórios

⚙ 03-engenharia/
    Arquitetura de Software
    Modelo de Dados
    Dashboards
    Experiência do Usuário (UX)

📑 04-governanca/
    Decisões
    Ideias
    Changelog

📚 05-referencias/
    Bibliografia
    Documentos Oficiais
    Referências Técnicas
    Roadmap
```

Cada grupo possui uma responsabilidade específica:

- **Fundamentos** reúne os documentos institucionais que definem a identidade, visão e princípios da GPA.

- **Pedagogia** concentra toda a fundamentação educacional, os conceitos pedagógicos, as atividades e os modelos de aprendizagem adotados pela ferramenta.

- **Engenharia** descreve a arquitetura técnica da solução, o modelo de dados, a experiência do usuário e os aspectos relacionados ao desenvolvimento do software.

- **Governança** registra as decisões arquiteturais, ideias, histórico de mudanças e demais documentos relacionados à evolução do projeto.

- **Referências** reúne a bibliografia utilizada, documentos oficiais e materiais que fundamentam teoricamente a GPA.

**Observação**

A documentação da GPA evolui de forma incremental. Novos documentos poderão ser incorporados às categorias existentes sem alterar a organização geral da documentação.

---

# Plataformas Suportadas

- 💻 Desktop
- 🌐 Web
- 📱 Smartphone
- 📲 Tablet

Todos compartilham o mesmo modelo de dados, regras de negócio e indicadores.

---

# Tecnologias Previstas

- Flutter
- Dart
- Python
- PostgreSQL
- SQLite

## Ferramentas de Desenvolvimento

- Git
- GitHub
- Visual Studio Code

---

# Estado Atual do Projeto

Atualmente a GPA encontra-se na fase de concepção arquitetural, consolidação da documentação e validação pedagógica.

Nesta etapa, o foco do projeto está na especificação funcional do domínio **Alfabetização**, utilizando a **Associação Trimodal** como primeiro módulo para validação da arquitetura pedagógica e tecnológica.

O desenvolvimento do software será iniciado após a consolidação da documentação.

---

# Roadmap

| Fase | Status |
|------|--------|
| Concepção | ✅ |
| Fundamentos | ✅ |
| Modelagem | ✅ |
| Engenharia | ✅ |
| Consolidação | ✅ |
| Desenvolvimento Core | ⏳ |
| MVP | ⏳ |

---

# Como Contribuir

São bem-vindas contribuições de:

- professores;
- pesquisadores;
- desenvolvedores;
- designers;
- especialistas em educação.

---

# Status do Projeto

🚧 Em fase de concepção arquitetural, documentação e validação pedagógica.

---

# Licença

*A definir.*

---

# Autor

**Rephael Pedretti da Silva**

Idealizador e mantenedor do projeto GPA.

---

Projeto desenvolvido com foco no apoio aos processos de ensino e aprendizagem por meio de recursos pedagógicos digitais fundamentados em evidências.

**GPA — Ferramenta Multiplataforma de Apoio aos Processos de Ensino e Aprendizagem**

**Versão:** v1.3.3
