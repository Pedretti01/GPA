# 01_VISAO_DO_PROJETO.md

# Visão do Projeto

**Ferramenta Multiplataforma de Apoio à Alfabetização**  
**Versão:** 0.3.0

---

# 1. Introdução

A Ferramenta Multiplataforma de Apoio à Alfabetização é um projeto voltado ao desenvolvimento de recursos digitais capazes de apoiar o processo de alfabetização por meio de atividades gamificadas, indicadores objetivos e evidências pedagógicas.

A proposta inicial utiliza diferentes formas de representação de um mesmo conceito para estimular a associação entre linguagem escrita, linguagem oral e representação visual.

O projeto será desenvolvido de forma incremental, iniciando com um único módulo de aprendizagem: **Associação Trimodal**.

---

# 2. Problema

O processo de alfabetização exige acompanhamento constante por parte do professor.

Embora existam diversos jogos educativos disponíveis, poucos fornecem informações objetivas que auxiliem o professor a compreender quais conteúdos apresentam maior facilidade ou dificuldade para cada estudante.

A ferramenta pretende contribuir com esse acompanhamento, registrando dados como:

- tempo de resposta;
- quantidade de tentativas;
- quantidade de erros;
- quantidade de acertos;
- evolução do estudante;
- conteúdos com maior dificuldade.

---

# 3. Objetivo Geral

Desenvolver uma ferramenta multiplataforma de gamificação pedagógica capaz de apoiar o processo de alfabetização por meio de atividades digitais que produzam indicadores objetivos da aprendizagem.

---

# 4. Plataforma Multiplataforma

A ferramenta foi concebida como uma solução educacional multiplataforma.

Seu objetivo é permitir que professores e estudantes utilizem os mesmos recursos pedagógicos em diferentes dispositivos, respeitando as características de cada ambiente.

Os ambientes previstos são:

- Desktop;
- Web;
- Tablet;
- Smartphone.

Independentemente do dispositivo utilizado, todos compartilharão:

- Objetos Pedagógicos;
- Planos de Atividade;
- Execuções da Atividade;
- Indicadores;
- Dashboards;
- Relatórios;
- Histórico das atividades.

A interface poderá adaptar-se às características de cada dispositivo, preservando sempre a coerência funcional e pedagógica da ferramenta.

---

# 5. Objetivos Específicos

São objetivos da primeira versão:

- desenvolver o módulo Associação Trimodal;
- estimular a associação entre palavra, imagem e áudio;
- registrar indicadores de desempenho durante a atividade;
- gerar relatórios destinados ao professor;
- permitir acompanhamento da evolução do estudante;
- preservar uma arquitetura preparada para uso em Desktop, Web, Tablet e Smartphone.

---

# 6. Público-Alvo

## 6.1 Professor

Responsável por:

- cadastrar estudantes;
- organizar turmas;
- cadastrar Objetos Pedagógicos;
- configurar Planos de Atividade;
- acompanhar indicadores;
- analisar Dashboards;
- emitir Relatórios;
- planejar intervenções pedagógicas.

## 6.2 Estudante

Responsável pela realização das atividades propostas pela ferramenta.

O estudante utilizará apenas os recursos necessários para execução das atividades.

---

# 7. Escopo da Primeira Versão

A primeira versão contempla exclusivamente o desenvolvimento do módulo **Associação Trimodal**.

Esse módulo consiste em uma atividade de associação entre três formas distintas de representação de um mesmo conceito:

- Palavra Escrita;
- Imagem;
- Áudio.

Não fazem parte da primeira versão outros jogos ou estratégias de aprendizagem.

---

# 8. Benefícios Esperados

## 8.1 Para o estudante

- desenvolvimento da associação entre diferentes formas de representação;
- estímulo à leitura;
- estímulo à percepção auditiva;
- estímulo ao reconhecimento visual;
- aprendizagem por meio da gamificação pedagógica.

## 8.2 Para o professor

- acompanhamento objetivo do desempenho;
- identificação de conteúdos com maior dificuldade;
- identificação de conteúdos com maior facilidade;
- histórico de evolução;
- apoio ao planejamento pedagógico.

---

# 9. Indicadores Produzidos

A ferramenta registrará automaticamente informações como:

- tempo de execução;
- tempo por associação;
- quantidade de tentativas;
- quantidade de acertos;
- quantidade de erros.

Esses indicadores serão utilizados na construção dos relatórios pedagógicos.

---

# 10. Relatórios e Dashboards

Os relatórios terão como finalidade apoiar o professor por meio da organização das evidências produzidas durante as atividades.

Os Dashboards permitirão acompanhamento visual e interativo dos indicadores.

A ferramenta não realiza diagnóstico automático do nível de alfabetização do estudante.

Os relatórios e Dashboards representam evidências quantitativas que poderão auxiliar a avaliação pedagógica conduzida pelo professor.

---

# 11. Limites do Projeto

A primeira versão não contempla:

- diagnóstico automático da hipótese de escrita;
- inteligência artificial;
- reconhecimento de voz;
- novos jogos pedagógicos;
- atividades de produção textual;
- atividades matemáticas.

Esses recursos poderão ser estudados futuramente, porém não fazem parte do escopo atual.

---

# 12. Expansão da Ferramenta

A arquitetura foi concebida para permitir crescimento modular.

Novos recursos poderão ser incorporados futuramente sem comprometer a estrutura existente.

Entretanto, toda expansão deverá ocorrer somente após a consolidação do módulo Associação Trimodal.

As possibilidades futuras serão registradas no documento:

```text
docs/04-governanca/IDEIAS.md
```

---

# 13. Critérios de Sucesso

A primeira versão será considerada concluída quando permitir:

- cadastro dos Objetos Pedagógicos;
- execução dos três modos da Associação Trimodal;
- registro dos indicadores definidos;
- geração de relatórios básicos para o professor;
- funcionamento estável da ferramenta nos ambientes previstos.

---

# 14. Considerações Finais

A ferramenta foi concebida para crescer de forma gradual.

A primeira versão concentra esforços na construção de um único módulo de aprendizagem, permitindo validar tanto os aspectos pedagógicos quanto os tecnológicos antes da expansão para novos recursos.

Essa abordagem busca garantir simplicidade, qualidade e consistência durante todo o desenvolvimento do projeto.
