# DECISOES.md

# Decisões Arquiteturais do Projeto

**GPA – Ferramenta Multiplataforma de Apoio aos Processos de Ensino e Aprendizagem**

**Versão:** 0.3.0

---

# DECISÃO 001 — Primeiro módulo

**Status:** Aprovado

O primeiro módulo da ferramenta será a **Associação Trimodal**.

Justificativa: permite validar a arquitetura pedagógica e tecnológica utilizando uma única mecânica de atividade.

---

# DECISÃO 002 — Três modalidades iniciais

**Status:** Aprovado

As representações iniciais serão:

- Palavra Escrita;
- Imagem;
- Áudio.

---

# DECISÃO 003 — Sem diagnóstico automático

**Status:** Aprovado

A ferramenta não realizará diagnóstico automático dos níveis de alfabetização.

Os indicadores produzidos apoiarão o professor, mas não substituirão sua avaliação pedagógica.

---

# DECISÃO 004 — Desenvolvimento incremental

**Status:** Aprovado

O projeto será desenvolvido em pequenas etapas.

Nenhuma nova funcionalidade será incorporada antes da consolidação da etapa anterior.

---

# DECISÃO 005 — Ferramenta Multiplataforma

**Status:** Aprovado

A GPA será concebida como uma ferramenta multiplataforma, disponível para Desktop, Web, Tablet e Smartphone.

Independentemente do dispositivo utilizado, todos os ambientes compartilharão o mesmo modelo de dados, as mesmas regras de negócio e os mesmos Domínios Pedagógicos, diferenciando-se apenas pela adaptação da interface ao contexto de uso.

---

# DECISÃO 006 — Atividades parametrizadas

**Status:** Aprovado

A Associação Trimodal será estruturada como atividade parametrizada, permitindo variações de modo, mecânica, tema, categoria, quantidade de cartas e complexidade linguística.

---

# DECISÃO 007 — Identidade da GPA

**Status:** Aprovado

A GPA passa a ser reconhecida oficialmente como uma **ferramenta multiplataforma de apoio aos processos de ensino e aprendizagem**.

O termo "plataforma" será utilizado exclusivamente para descrever sua arquitetura interna de software.

Justificativa:

Esta decisão diferencia a forma como a solução é apresentada aos usuários (ferramenta) da forma como é estruturada tecnicamente (arquitetura de plataforma modular), evitando ambiguidades na documentação.

---

# DECISÃO 008 — Arquitetura Modular

**Status:** Aprovado

A arquitetura da GPA será organizada em um núcleo compartilhado (Core) e por Domínios Pedagógicos independentes.

O Core concentrará funcionalidades reutilizáveis por todos os domínios, enquanto cada domínio implementará suas próprias regras pedagógicas, atividades e conteúdos.

Justificativa:

Essa organização favorece reutilização, escalabilidade e evolução sustentável da ferramenta.

---

# DECISÃO 009 — Primeiro Domínio Pedagógico

**Status:** Aprovado

Embora a GPA tenha sido concebida para suportar diferentes Domínios Pedagógicos, a primeira versão contemplará exclusivamente o domínio **Alfabetização**.

Justificativa:

A validação do domínio Alfabetização permitirá consolidar a arquitetura pedagógica e tecnológica antes da expansão para outras áreas do conhecimento.

---

# DECISÃO 010 — Controle de Escopo

**Status:** Aprovado

Novas ideias, funcionalidades ou Domínios Pedagógicos deverão ser registradas no documento IDEIAS.md e somente poderão integrar o projeto após avaliação e aprovação.

O desenvolvimento deverá permanecer concentrado no escopo definido para o MVP.

Justificativa:

Garantir evolução incremental, reduzir complexidade e preservar o foco na entrega da primeira versão da ferramenta.

---


