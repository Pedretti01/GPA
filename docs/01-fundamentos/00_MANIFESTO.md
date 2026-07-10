# 00_MANIFESTO.md

# Manifesto Arquitetural e Pedagógico

**Ferramenta Multiplataforma de Apoio à Aprendizagens**
**Documento:** Manifesto    
**Versão:** 0.3.0  
**Status:** Documento Fundador
**Área:** Fundamentos

---

# 1. Declaração do Projeto

A Plataforma de Gamificação Pedagógica para Aprendizagens é uma **ferramenta multiplataforma de apoio ao processo de aprendizagens**, fundamentada em **Objetos Pedagógicos**, **Atividades Parametrizadas**, **Gamificação Pedagógica** e **Learning Analytics**.

Seu objetivo é produzir evidências que apoiem o trabalho do professor, respeitando o percurso de aprendizagem de cada estudante.

---

# 2. Missão

Apoiar professores no acompanhamento do processo de aprendizagens por meio de atividades gamificadas, indicadores objetivos e evidências pedagógicas.

---

# 3. Visão

Construir uma ferramenta educacional multiplataforma, modular e evolutiva, capaz de apoiar o processo de aprendizagens em diferentes contextos de uso.

---

# 4. Objetivo Inicial

O primeiro objetivo da ferramenta é desenvolver e validar o módulo **Associação Trimodal**.

Esse módulo permitirá associar três formas de representação de um mesmo conceito:

- palavra escrita;
- imagem;
- áudio.

A expansão para novos módulos ocorrerá somente após a consolidação deste primeiro módulo.

---

# 5. Filosofia do Projeto

A ferramenta foi concebida para:

- apoiar o trabalho do professor;
- respeitar a autonomia docente;
- produzir evidências de aprendizagem;
- favorecer o acompanhamento pedagógico;
- utilizar gamificação como estratégia de aprendizagem;
- evitar diagnósticos automáticos não validados;
- crescer de forma incremental e controlada.

A tecnologia não substitui o professor. A tecnologia amplia a capacidade de observar, registrar e compreender o processo de aprendizagem.

---

# 6. Princípios Fundamentais

## 6.1 Evolução Controlada

A ferramenta será desenvolvida em pequenas etapas. Cada etapa deverá ser validada antes da inclusão de novos recursos.

Ideias futuras deverão ser registradas, discutidas e avaliadas antes de se tornarem requisitos oficiais.

## 6.2 Simplicidade

A simplicidade é um princípio permanente. Toda solução deverá priorizar clareza, facilidade de uso e manutenção.

## 6.3 Modularidade

A ferramenta será organizada em módulos independentes. Cada módulo deverá possuir responsabilidade própria e poderá evoluir sem comprometer os demais.

## 6.4 Multiplataforma

A ferramenta será concebida desde sua origem para funcionar em diferentes ambientes:

- Desktop;
- Web;
- Tablet;
- Smartphone.

Todos os ambientes deverão compartilhar:

- o mesmo núcleo pedagógico;
- o mesmo modelo de dados;
- as mesmas regras de negócio;
- os mesmos Objetos Pedagógicos;
- os mesmos Indicadores;
- os mesmos Relatórios.

Cada dispositivo poderá possuir uma interface adaptada ao seu contexto de uso.

## 6.5 Objetos Pedagógicos

O conteúdo central da ferramenta será organizado por meio de Objetos Pedagógicos.

Cada Objeto Pedagógico representa um conceito e suas diferentes formas de representação. Na primeira versão:

- palavra escrita;
- imagem;
- áudio.

## 6.6 Atividades Parametrizadas

As atividades serão configuráveis. Uma atividade poderá variar conforme:

- modo;
- mecânica;
- quantidade de cartas;
- categoria;
- tema;
- complexidade linguística.

Essa parametrização permitirá ajustar a atividade às necessidades pedagógicas sem criar novos jogos desnecessariamente.

## 6.7 Gamificação Pedagógica

A gamificação será utilizada para favorecer motivação, engajamento e permanência na atividade.

A gamificação não terá caráter competitivo. O foco será:

- aprendizagem;
- feedback;
- progresso;
- acolhimento;
- tentativa;
- superação.

## 6.8 Learning Analytics

A ferramenta utilizará dados produzidos durante as atividades para gerar indicadores e evidências pedagógicas.

Essas evidências deverão apoiar o professor na análise do processo de aprendizagem.

O sistema não realizará diagnóstico automático do nível de alfabetização.

## 6.9 Documentação Viva

A documentação faz parte do projeto. Toda decisão importante deverá ser registrada antes da implementação.

A documentação deverá acompanhar a evolução da ferramenta.

## 6.10 Fundamentação Pedagógica

As decisões pedagógicas deverão estar fundamentadas em documentos oficiais, pesquisas científicas e literatura especializada.

Referências iniciais:

- BNCC;
- Práticas de Alfabetização;
- RENABE;
- estudos sobre alfabetização, consciência fonológica, leitura e escrita.

---

# 7. Escopo Inicial

A primeira versão contempla:

- cadastro de Objetos Pedagógicos;
- módulo Associação Trimodal;
- registro de indicadores;
- relatórios básicos para o professor;
- funcionamento multiplataforma.

Não fazem parte do escopo inicial:

- novos jogos;
- inteligência artificial;
- diagnóstico automático;
- reconhecimento de voz;
- produção textual;
- atividades matemáticas.

---

# 8. Compromisso Pedagógico

A ferramenta não classifica automaticamente estudantes como:

- pré-silábico;
- silábico;
- silábico com valor sonoro;
- silábico-alfabético;
- alfabético.

Essas avaliações permanecem sob responsabilidade do professor.

A ferramenta apenas organiza evidências que podem apoiar essa avaliação.

---

# 9. Organização da Documentação

A documentação oficial da ferramenta está organizada por áreas de conhecimento.

```text
docs/

├── 01-fundamentos/
│   ├── 00_MANIFESTO.md
│   ├── 01_VISAO_DO_PROJETO.md
│   └── 02_FUNDAMENTACAO_PEDAGOGICA.md
│
├── 02-pedagogia/
│   ├── 03_ARQUITETURA_PEDAGOGICA.md
│   ├── 04_OBJETOS_PEDAGOGICOS.md
│   ├── 05_ASSOCIACAO_TRIMODAL.md
│   ├── 06_GAMIFICACAO_PEDAGOGICA.md
│   ├── 07_INDICADORES.md
│   └── 08_RELATORIOS.md
│
├── 03-engenharia/
│   ├── 09_ARQUITETURA_DE_SOFTWARE.md
│   ├── 10_MODELO_DE_DOMINIO.md
│   ├── 11_MODELO_CONCEITUAL.md
│   ├── 12_MODELO_LOGICO.md
│   ├── 13_MODELO_FISICO.md
│   ├── 14_DIAGRAMA_DE_CLASSES.md
│   ├── 15_DIAGRAMA_DE_CASOS_DE_USO.md
│   ├── 16_ARQUITETURA_MULTIPLATAFORMA.md
│   ├── 17_FLUXOS_DA_APLICACAO.md
│   ├── 18_SEGURANCA_E_PRIVACIDADE.md
│   ├── 19_DASHBOARDS.md
│   └── 20_EXPERIENCIA_DO_USUARIO.md
│
├── 04-governanca/
│   ├── CHANGELOG.md
│   ├── DECISOES.md
│   └── IDEIAS.md
│
└── 05-referencias/
    ├── 21_REFERENCIAS.md
    └── 22_ROADMAP.md
```

Cada documento possui uma responsabilidade específica e complementa os demais, formando a especificação funcional e arquitetural oficial do projeto.

---

# 10. Considerações Finais

Este Manifesto representa o documento fundador da ferramenta.

Todas as decisões futuras deverão respeitar os princípios aqui definidos.

A evolução da ferramenta deverá preservar:

- simplicidade;
- modularidade;
- fundamentação pedagógica;
- apoio ao professor;
- respeito ao estudante;
- produção de evidências;
- arquitetura multiplataforma.

A finalidade do projeto não é criar apenas um jogo digital.

A finalidade é construir uma ferramenta educacional de apoio à aprendizagens, capaz de crescer de forma organizada, fundamentada e pedagogicamente responsável.
