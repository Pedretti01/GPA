# 12_MODELO_LOGICO.md

# Modelo Lógico de Dados

**GPA – Gamificação Pedagógica de Aprendizagens**  
**Documento:** Modelo Lógico de Dados   
**Versão:** 1.3.3
**Área:** Engenharia
**Documento relacionado:** `11_MODELO_CONCEITUAL.md`

---

# 1. Objetivo do Documento

Este documento apresenta o **Modelo Lógico de Dados** do GPA, derivado do **11_MODELO_CONCEITUAL.md**.

Seu objetivo é transformar as entidades conceituais em uma estrutura lógica de tabelas, chaves primárias, chaves estrangeiras e relacionamentos, ainda sem definir detalhes específicos da implementação física no PostgreSQL.

Este documento serve de base para:

- 13_MODELO_FISICO.md
- 14_DIAGRAMA_DE_CLASSES.md

---

# 2. Diagrama do Modelo Lógico

<div align="center">

![Modelo Lógico do GPA](../assets/modelos/modelo-logico-gpa.png)

**Figura 1 – Modelo Lógico do GPA.**

</div>

---

# 3. Convenções Utilizadas

| Convenção | Significado |
|---|---|
| `TB_` | Prefixo para tabela |
| `PK` | Chave primária |
| `FK` | Chave estrangeira |
| `UNIQUE` | Valor único |
| `id_` | Identificador interno |
| `codigo_` | Identificador funcional |
| `json` | Estrutura flexível |

---

# 4. Domínio de Usuários, Perfis e Acesso

Mantém as entidades:

- TB_USUARIO
- TB_PERFIL
- TB_PERMISSAO
- TB_PERFIL_PERMISSAO
- TB_ESCOPO_ACESSO

Regra lógica:

```text
Perfil define o que o usuário pode fazer.
Escopo define quais dados o usuário pode acessar.
```

---

# 5. Domínio da Estrutura Organizacional

Entidades:

- TB_REDE_ENSINO
- TB_REGIONAL
- TB_ESCOLA
- TB_TURMA
- TB_SALA
- TB_ESTUDANTE
- TB_PROFESSOR
- TB_PROFESSOR_TURMA
- TB_RESPONSAVEL
- TB_RESPONSAVEL_ESTUDANTE

Mantêm-se os relacionamentos apresentados no modelo conceitual.

---

# 6. Domínio Pedagógico

Hierarquia lógica:

```text
TB_CURRICULO
    └── TB_EIXO_CONHECIMENTO
        └── TB_COMPETENCIA
            └── TB_HABILIDADE
                └── TB_OBJETIVO_APRENDIZAGEM
                    └── TB_SEQUENCIA_DIDATICA
                        └── TB_ATIVIDADE
                            └── TB_QUESTAO
```

---

# 7. Objetos Pedagógicos e Mídias

Principais entidades:

- TB_OBJETO_PEDAGOGICO
- TB_MIDIA_OBJETO
- TB_QUESTAO_OBJETO
- TB_CARTA_PEDAGOGICA

Mantém-se a regra do identificador permanente dos Objetos Pedagógicos e da associação entre mídias e questões.

---

# 8. Avaliação e Progresso

Entidades:

- TB_TENTATIVA_ATIVIDADE
- TB_RESPOSTA
- TB_PROGRESSO_HABILIDADE

Os indicadores de progresso permanecem derivados das respostas registradas pelo estudante.

---

# 9. Gamificação

Entidades:

- TB_AVATAR
- TB_RECOMPENSA
- TB_CONQUISTA
- TB_ESTUDANTE_RECOMPENSA
- TB_ESTUDANTE_CONQUISTA

A gamificação permanece vinculada ao progresso pedagógico.

---

# 10. Relatórios, Indicadores e Auditoria

Entidades:

- TB_INDICADOR
- TB_RELATORIO
- TB_AUDITORIA
- TB_LOG_SISTEMA

Os relatórios armazenam parâmetros de geração, preservando a rastreabilidade das consultas.

---

# 11. Relacionamentos Principais

Mantêm-se todos os relacionamentos apresentados no Modelo Conceitual, refinados em tabelas, chaves primárias e chaves estrangeiras.

---

# 12. Diretrizes para o Modelo Físico

O Modelo Físico deverá definir:

- tipos PostgreSQL;
- índices;
- constraints;
- foreign keys;
- estratégias de exclusão;
- views;
- funções;
- triggers;
- auditoria;
- versionamento dos Objetos Pedagógicos.

---

# 13. Relação com os Demais Documentos

Este documento complementa:

- 11_MODELO_CONCEITUAL.md
- 13_MODELO_FISICO.md
- 14_DIAGRAMA_DE_CLASSES.md

---

# 14. Considerações Finais

O Modelo Lógico consolida a estrutura lógica do GPA, servindo como ponte entre o Modelo Conceitual e o Modelo Físico. Ele preserva a coerência da arquitetura documental estabelecida para a versão **1.3.3**, garantindo rastreabilidade e consistência para a implementação futura.
