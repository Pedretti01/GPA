# 10_MODELO_DE_DADOS.md

# Modelo Conceitual de Dados

**Ferramenta Multiplataforma de Apoio à Alfabetização**  
**Versão:** 0.3.0

---

# 1. Introdução

Este documento apresenta o Modelo Conceitual de Dados da ferramenta.

Seu objetivo é definir quais informações serão armazenadas pelo sistema e como elas se relacionam.

Este documento descreve o domínio da aplicação e não define uma tecnologia específica de banco de dados.

---

# 2. Independência da Plataforma

O Modelo de Dados deverá permanecer independente da tecnologia utilizada para implementação.

Os mesmos dados deverão atender todas as plataformas suportadas:

- Desktop;
- Web;
- Tablet;
- Smartphone.

Nenhuma informação deverá depender de um dispositivo específico.

---

# 3. Objetivos

O Modelo de Dados deverá permitir:

- organização dos conteúdos pedagógicos;
- criação de Planos de Atividade;
- execução das atividades;
- registro das interações;
- geração dos indicadores;
- produção dos relatórios e Dashboards.

---

# 4. Entidades Principais

## 4.1 Professor

Representa o responsável pelo planejamento pedagógico.

## 4.2 Turma

Agrupa estudantes.

## 4.3 Estudante

Representa o participante das atividades.

## 4.4 Objeto Pedagógico

Representa um único conceito e suas representações:

- palavra;
- imagem;
- áudio.

## 4.5 Plano de Atividade

Define as configurações pedagógicas da atividade.

Exemplos:

- modo;
- mecânica;
- categoria;
- complexidade linguística;
- quantidade de cartas.

## 4.6 Atividade

Representa a aplicação de um Plano de Atividade em determinado contexto.

## 4.7 Execução

Representa a realização de uma Atividade por um estudante.

## 4.8 Interação

Representa cada ação realizada durante a Execução.

Exemplos:

- abrir carta;
- selecionar carta;
- erro;
- acerto.

## 4.9 Indicador

Representa os resultados calculados a partir das interações.

## 4.10 Relatório

Organiza indicadores para apresentação ao professor.

---

# 5. Fluxo Conceitual

```text
Professor
    ↓
Plano de Atividade
    ↓
Atividade
    ↓
Execução
    ↓
Interações
    ↓
Indicadores
    ↓
Evidências
    ↓
Relatórios e Dashboards
```

---

# 6. Relacionamentos

Relacionamentos principais:

- Professor possui Turmas;
- Turma possui Estudantes;
- Professor cria Planos de Atividade;
- Plano de Atividade utiliza Objetos Pedagógicos;
- Plano de Atividade gera Atividades;
- Estudante realiza Execuções;
- Execução possui Interações;
- Interações geram Indicadores;
- Indicadores alimentam Relatórios e Dashboards.

---

# 7. Histórico e Rastreabilidade

A ferramenta deverá preservar o histórico completo das execuções.

Nenhuma informação de execução deverá ser sobrescrita.

Essa decisão permitirá acompanhar a evolução do estudante ao longo do tempo.

---

# 8. Persistência

A arquitetura deverá permitir diferentes mecanismos de armazenamento, como:

- SQLite;
- PostgreSQL;
- Firebase;
- Supabase;
- Hive;
- outros mecanismos futuros.

A modelagem conceitual permanece a mesma.

---

# 9. Considerações Finais

O Modelo Conceitual de Dados representa a estrutura lógica da ferramenta.

Toda implementação deverá preservar os relacionamentos definidos neste documento, garantindo consistência, reutilização e possibilidade de evolução futura.
