# 11_MODELO_CONCEITUAL.md

# Modelo Conceitual do Sistema

**GPA – Gamificação Pedagógica de Aprendizagens**  
**Documento:** Modelo Conceitual do Sistema   
**Versão:** 1.3.3
**Área:** Engenharia
**Documento relacionado:** `10_MODELO_DE_DOMINIO.md`

---

# 1. Objetivo do Documento

Este documento apresenta o **Modelo Conceitual** do GPA, descrevendo as principais entidades do sistema, seus relacionamentos e cardinalidades em alto nível.

Seu objetivo é representar a estrutura conceitual do sistema antes da elaboração do Modelo Lógico, Modelo Físico e implementação em software.

Este documento é derivado do **10_MODELO_DE_DOMINIO.md** e serve de base para:

- 12_MODELO_LOGICO.md
- 13_MODELO_FISICO.md
- 14_DIAGRAMA_DE_CLASSES.md

---

# 2. Diagrama do Modelo Conceitual

<div align="center">

![Modelo Conceitual do GPA](../assets/modelos/modelo-conceitual-gpa.png)

**Figura 1 – Modelo Conceitual do GPA.**

</div>

---

# 3. Visão Geral do Modelo

O Modelo Conceitual está organizado em oito grandes domínios:

1. Usuários, Perfis e Escopos;
2. Estrutura Organizacional;
3. Núcleo Pedagógico;
4. Objetos Pedagógicos e Mídias;
5. Avaliação, Respostas e Progresso;
6. Gamificação;
7. Relatórios, Indicadores e Dashboards;
8. Sistema, Auditoria e Segurança.

Cada domínio representa um conjunto de entidades e relacionamentos que serão refinados nos modelos subsequentes.

---

# 4. Usuários, Perfis e Escopos

O controle de acesso do GPA baseia-se em Perfil e Escopo de Acesso.

- **Perfil** define o que o usuário pode fazer.
- **Escopo** define quais dados pode acessar.

Exemplos de escopo:

- Rede;
- Regional;
- Escola;
- Turma;
- Sala;
- Estudante.

---

# 5. Estrutura Organizacional

Hierarquia conceitual:

```text
Rede de Ensino
    └── Regional
        └── Escola
            └── Turma
                └── Sala
                    └── Estudante
```

Professores podem atuar em múltiplas turmas e responsáveis podem acompanhar múltiplos estudantes.

---

# 6. Núcleo Pedagógico

```text
Currículo
    └── Eixo de Conhecimento
        └── Competência
            └── Habilidade
                └── Objetivo de Aprendizagem
                    └── Sequência Didática
                        └── Atividade
                            └── Questão
```

---

# 7. Objetos Pedagógicos e Mídias

Os Objetos Pedagógicos possuem identificador permanente (ex.: OP-000001) e podem reunir múltiplas mídias (imagem, texto, áudio, vídeo e animação), incluindo os subtipos de áudio **pronuncia_direta** e **pronuncia_fragmentada**.

---

# 8. Carta Pedagógica

A Carta Pedagógica representa visualmente um Objeto Pedagógico na interface e implementa a alternância entre áudio direto e fragmentado durante a interação do estudante.

---

# 9. Avaliação, Respostas e Progresso

Fluxo conceitual:

```text
Estudante
    ↓
Tentativa de Atividade
    ↓
Resposta
    ↓
Resultado
    ↓
Progresso do Estudante
```

---

# 10. Gamificação

Entidades principais:

- Avatar;
- Personagem;
- Nível;
- Conquista;
- Recompensa.

A gamificação deve apoiar o processo de aprendizagem.

---

# 11. Relatórios, Indicadores e Dashboards

Os indicadores alimentam dashboards e relatórios específicos para cada perfil de usuário, respeitando perfil e escopo de acesso.

---

# 12. Sistema, Auditoria e Segurança

Abrange autenticação, autorização, logs e auditoria, garantindo rastreabilidade das operações e conformidade com a arquitetura do GPA.

---

# 13. Relação com os Demais Documentos

Este documento complementa:

- 10_MODELO_DE_DOMINIO.md
- 12_MODELO_LOGICO.md
- 13_MODELO_FISICO.md
- 14_DIAGRAMA_DE_CLASSES.md

---

# 14. Considerações Finais

O Modelo Conceitual representa a transição entre o Modelo de Domínio e o Modelo Lógico. Ele consolida as entidades e seus relacionamentos em alto nível, preservando a coerência entre a arquitetura pedagógica e a arquitetura de software do GPA.

