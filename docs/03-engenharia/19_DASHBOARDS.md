# 19_DASHBOARDS.md

# Dashboards

**GPA – Gamificação Pedagógica de Aprendizagens**  
**Documento:** Dashboards  
**Versão:** 1.3.3
**Área:** Engenharia
**Documento relacionado:** `07_INDICADORES.md`
                         - `08_RELATORIOS.md`
                         - `15_CASOS_DE_USO.md`
                         - `17_FLUXOS_DA_APLICACAO.md`
                         - `18_SEGURANCA_E_PRIVACIDADE.md`

---

# 1. Objetivo

Este documento descreve a arquitetura funcional dos dashboards do GPA, responsáveis por transformar indicadores e relatórios em painéis visuais para apoio à tomada de decisão pedagógica, administrativa e estratégica.

---

# 2. Relação entre Indicadores, Relatórios e Dashboards

```text
Respostas
    ↓
Resultados
    ↓
Indicadores
    ↓
Relatórios
    ↓
Dashboards
```

Relatórios possuem caráter documental e analítico.

Dashboards possuem caráter visual, exploratório, interativo e contínuo.

---

# 3. Arquitetura dos Dashboards

<div align="center">

![Arquitetura dos Dashboards](../assets/dashboards/arquitetura-dashboards-gpa.png)

**Figura 1 – Arquitetura dos Dashboards do GPA**

</div>

Os dashboards consomem indicadores produzidos pelo Backend, respeitando autenticação, autorização (RBAC + ABAC) e escopos institucionais.

---

# 4. Dashboards por Perfil

## Administrador
- Visão global da plataforma
- Indicadores consolidados
- Uso do sistema
- Auditoria e saúde operacional

## Órgão Central da Rede de Ensino
- Comparativo entre regionais
- Evolução da rede
- Habilidades críticas
- Indicadores estratégicos

## Diretor / Coordenador
- Desempenho da escola
- Comparação entre turmas
- Evolução por habilidade
- Estudantes em acompanhamento

## Professor
- Evolução da turma
- Desempenho individual
- Acertos e erros
- Tempo médio de resposta
- Atividades concluídas

## Pais / Responsáveis
- Evolução do estudante
- Conquistas
- Atividades realizadas
- Habilidades em desenvolvimento

---

# 5. Filtros Recomendados

Os dashboards deverão permitir filtros por:

```text
Período
Rede
Regional
Escola
Turma
Sala
Professor
Estudante
Atividade
Habilidade
Objeto Pedagógico
Questão
Acerto / Erro
```

---

# 6. Perguntas que os Dashboards Devem Responder

- Como está a aprendizagem da rede?
- Como está a aprendizagem da escola?
- Quais turmas precisam de atenção?
- Quais estudantes precisam de intervenção?
- Quais habilidades apresentam maior dificuldade?
- Quais Objetos Pedagógicos são mais eficazes?
- Como evoluiu cada estudante ao longo do tempo?

---

# 7. Segurança e Privacidade

Os dashboards devem respeitar:

- escopos de acesso;
- autenticação e autorização;
- anonimização quando necessário;
- conformidade com a LGPD;
- registro de auditoria.

---

# 8. Cuidados Pedagógicos

Os dashboards apoiam decisões pedagógicas e não devem ser utilizados para rotular estudantes.

As informações devem orientar intervenções, acompanhamento e melhoria contínua.

---

# 9. Relação com os Demais Documentos

Este documento complementa:

- 07_INDICADORES.md
- 08_RELATORIOS.md
- 15_CASOS_DE_USO.md
- 17_FLUXOS_DA_APLICACAO.md
- 18_SEGURANCA_E_PRIVACIDADE.md

---

# 10. Considerações Finais

Os dashboards do GPA representam a camada visual da inteligência pedagógica da plataforma, consolidando indicadores, relatórios e métricas em painéis interativos que apoiam professores, gestores e responsáveis na tomada de decisões baseadas em evidências.

