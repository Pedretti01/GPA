# 01_VISAO_DO_PROJETO.md

# Visão do Projeto

**GPA – Gamificação Pedagógica de Aprendizagens**  
**Documento:** Visão do Projeto  
**Versão:** 1.3.3
**Área:** Fundamentos

---

# 1. Introdução

O **GPA – Gamificação Pedagógica de Aprendizagens** é uma plataforma multiplataforma desenvolvida para apoiar o processos de aprendizaegns, entre eles a  alfabetização por meio da integração entre tecnologia, gamificação e acompanhamento pedagógico baseado em evidências.

O projeto propõe um ambiente capaz de disponibilizar atividades pedagógicas digitais, registrar indicadores objetivos de aprendizagem e fornecer informações que auxiliem professores, gestores e instituições educacionais na tomada de decisões pedagógicas.

Sua arquitetura foi concebida para ser modular, escalável e independente de plataforma, permitindo a evolução contínua da solução conforme novas estratégias pedagógicas forem incorporadas.

A primeira implementação concentra-se no módulo **Associação Trimodal**, utilizado como base para validação da arquitetura pedagógica e tecnológica do sistema.

---

# 2. Visão Geral da Plataforma

A Figura 1 apresenta uma visão conceitual do GPA, evidenciando seus principais pilares e a forma como a plataforma integra os aspectos pedagógicos, tecnológicos e de governança.

O diagrama não representa a arquitetura de software nem o modelo de dados do sistema. Seu objetivo é fornecer uma visão estratégica da plataforma e demonstrar como seus componentes se relacionam para apoiar o processo de alfabetização.

<div align="center">

![Visão Geral do GPA](../assets/diagramas/visao-geral-gpa.svg)

**Figura 1 – Visão conceitual da plataforma GPA.**

</div>

---

# 3. Problema

O processo de alfabetização exige acompanhamento contínuo, intervenções pedagógicas oportunas e evidências que permitam compreender a evolução de cada estudante.

Embora existam diversas aplicações educacionais voltadas à alfabetização, poucas oferecem mecanismos consistentes para registrar indicadores de aprendizagem e transformá-los em informações úteis ao planejamento pedagógico.

O GPA busca preencher essa lacuna por meio da coleta estruturada de dados durante a execução das atividades, permitindo acompanhar aspectos como:

- tempo de resposta;
- quantidade de tentativas;
- quantidade de acertos;
- quantidade de erros;
- evolução individual;
- evolução da turma;
- conteúdos com maior facilidade;
- conteúdos com maior dificuldade.

Essas informações constituem evidências objetivas que apoiam, mas não substituem, a avaliação realizada pelo professor.

---

# 4. Objetivo Geral

Desenvolver uma plataforma multiplataforma de gamificação pedagógica de aprendizagens, entre elas a alfabetização, capaz de integrar atividades educacionais digitais, objetos pedagógicos, indicadores de aprendizagem, dashboards e relatórios, apoiando professores e gestores no acompanhamento do processo de ensino e aprendizagem.

---

# 5. Princípios do Projeto

O GPA foi concebido com base nos seguintes princípios:

- foco no processo pedagógico;
- aprendizagem baseada em evidências;
- arquitetura modular;
- independência tecnológica;
- escalabilidade;
- reutilização de objetos pedagógicos;
- interoperabilidade entre módulos;
- experiência de uso consistente em diferentes plataformas.

Esses princípios orientam tanto a arquitetura pedagógica quanto a arquitetura de software do projeto.

---

# 6. Sistema Multiplataforma

O GPA foi concebido como uma solução educacional multiplataforma.

A mesma base de dados, regras de negócio e objetos pedagógicos poderá ser utilizada em diferentes ambientes computacionais, garantindo consistência funcional e pedagógica.

Os ambientes previstos são:

- Desktop;
- Web;
- Tablet;
- Smartphone.

Independentemente da plataforma utilizada, serão compartilhados:

- Objetos Pedagógicos;
- Planos de Atividade;
- Execuções das Atividades;
- Indicadores;
- Dashboards;
- Relatórios;
- Histórico de aprendizagem.

Cada interface poderá adaptar-se às características do dispositivo, preservando a mesma experiência pedagógica.

---

# 7. Objetivos Específicos

Entre os objetivos da versão inicial destacam-se:

- implementar o módulo Associação Trimodal;
- disponibilizar objetos pedagógicos reutilizáveis;
- registrar indicadores objetivos durante a execução das atividades;
- gerar relatórios pedagógicos;
- disponibilizar dashboards de acompanhamento;
- apoiar o planejamento pedagógico;
- validar a arquitetura modular da plataforma.

---

# 8. Público-Alvo

O GPA foi concebido para atender diferentes perfis de usuários.

## Professor

Responsável pelo planejamento das atividades pedagógicas, acompanhamento da aprendizagem e análise dos indicadores produzidos pelo sistema.

## Coordenador Pedagógico

Responsável pelo acompanhamento pedagógico das turmas e apoio aos professores.

## Diretor Escolar

Responsável pelo acompanhamento institucional dos indicadores educacionais.

## Gestores Educacionais

Responsáveis pela análise consolidada das informações produzidas pelas unidades escolares.

## Responsáveis

Acompanham o desenvolvimento do estudante por meio das informações disponibilizadas pela instituição.

## Estudante

Realiza as atividades pedagógicas propostas, interagindo exclusivamente com os recursos necessários ao processo de aprendizagem.

---

# 9. Escopo da Primeira Versão

A primeira versão do GPA concentra-se na implementação do módulo **Associação Trimodal**.

Esse módulo utiliza três formas complementares de representação de um mesmo conceito:

- Palavra Escrita;
- Imagem;
- Áudio.

Além da atividade pedagógica, a primeira versão contempla:

- cadastro de Objetos Pedagógicos;
- cadastro de Planos de Atividade;
- execução das atividades;
- registro de indicadores;
- dashboards básicos;
- relatórios pedagógicos.

---

# 10. Benefícios Esperados

## Para o estudante

- aprendizagem mediada por gamificação;
- fortalecimento das associações entre linguagem escrita, visual e oral;
- maior engajamento nas atividades;
- acompanhamento contínuo da evolução.

## Para professores e gestores

- evidências objetivas da aprendizagem;
- acompanhamento individual e coletivo;
- apoio ao planejamento pedagógico;
- identificação de dificuldades de aprendizagem;
- suporte à tomada de decisão.

---

# 11. Indicadores Pedagógicos

Durante a execução das atividades, o GPA registrará automaticamente informações como:

- tempo de execução;
- tempo por associação;
- número de tentativas;
- quantidade de acertos;
- quantidade de erros;
- evolução individual;
- evolução por turma.

Esses indicadores constituem a base para geração de relatórios e dashboards.

---

# 12. Relatórios e Dashboards

Os relatórios e dashboards têm como objetivo transformar os dados coletados em informações úteis ao acompanhamento pedagógico.

O GPA fornece evidências quantitativas de aprendizagem, preservando ao professor a responsabilidade pela interpretação pedagógica dos resultados.

O sistema não realiza diagnóstico automático do nível de alfabetização.

---

# 13. Limites da Versão Inicial

Não fazem parte da versão inicial:

- inteligência artificial;
- reconhecimento de voz;
- diagnóstico automático da hipótese de escrita;
- atividades matemáticas;
- produção textual;
- novos módulos pedagógicos além da Associação Trimodal.

Esses recursos poderão ser incorporados futuramente de forma modular.

---

# 14. Evolução da Plataforma

A arquitetura do GPA foi concebida para permitir crescimento incremental.

Novos módulos pedagógicos poderão ser incorporados sem comprometer a estrutura existente, preservando os princípios de modularidade, reutilização e escalabilidade.

As propostas de evolução são registradas na documentação de governança do projeto.

---

# 15. Critérios de Sucesso

A primeira etapa da plataforma será considerada consolidada quando permitir:

- gerenciamento de Objetos Pedagógicos;
- execução do módulo Associação Trimodal;
- registro consistente dos indicadores definidos;
- geração de dashboards;
- emissão de relatórios pedagógicos;
- funcionamento estável em diferentes plataformas.

---

# 16. Relação com os Demais Documentos

Este documento apresenta a visão estratégica do GPA.

Sua leitura é complementada pelos seguintes documentos:

- Arquitetura Pedagógica
- Arquitetura de Software
- Modelo de Domínio
- Arquitetura Multiplataforma
- Fluxos da Aplicação

---

# 17. Considerações Finais

O GPA foi concebido para evoluir de forma incremental, preservando o alinhamento entre arquitetura pedagógica, arquitetura de software e objetivos educacionais.

A consolidação do módulo Associação Trimodal representa a primeira etapa dessa evolução, estabelecendo uma base sólida para futuras expansões da plataforma e para a incorporação de novos recursos pedagógicos.