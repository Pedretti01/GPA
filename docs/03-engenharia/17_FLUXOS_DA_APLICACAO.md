# 17. Fluxos da Aplicação

# Fluxos da Aplicação

**GPA – Gamificação Pedagógica de Aprendizagens**  
**Documento:** Fluxos da Aplicação   
**Versão:** 1.3.3
**Área:** Engenharia
**Documento relacionado:** `09_ARQUITETURA_DE_SOFTWARE.md`
                         - `14_DIAGRAMA_DE_CLASSES.md`
                         - `15_DIAGRAMA_DE_CASOS_DE_USO.md`
                         - `16_ARQUITETURA_MULTIPLATAFORMA.md`

---

# 1. Objetivo

Este documento descreve os principais fluxos operacionais do GPA, servindo como referência para a navegação da aplicação, construção das telas, definição das rotas, implementação dos casos de uso e testes de usabilidade.

---

## 2. Fluxo Geral de Acesso

Representa o fluxo macro de autenticação, identificação do perfil, definição do escopo de acesso e direcionamento para os módulos da plataforma.

![Fluxo Geral](../assets/fluxos/fluxo_geral_acesso.png)

---

## 3. Fluxo do Administrador

Representa as operações administrativas da plataforma, incluindo gestão de usuários, permissões, estrutura institucional, objetos pedagógicos e auditoria.

![Administrador](../assets/fluxos/fluxo_administrador.png)

---

## 4. Fluxo Órgão Central Rede de Ensino (Municipal ou Estadual)

Representa o acompanhamento da rede, currículo, indicadores e gestão pedagógica em nível central.

![Órgão Central](../assets/fluxos/fluxo_orgao_central.png)

---

## 5. Fluxo do Diretor / Coordenador

Representa o gerenciamento da unidade escolar, professores, turmas, estudantes e acompanhamento pedagógico.

![Diretor](../assets/fluxos/fluxo_diretor_coordenador.png)

---

## 6. Fluxo do Professor

Representa o planejamento, aplicação e acompanhamento das atividades pedagógicas.

![Professor](../assets/fluxos/fluxo_professor.png)

---

## 7. Fluxo do Estudante

Representa a execução das atividades, interação com os Objetos Pedagógicos e evolução na gamificação.

![Estudante](../assets/fluxos/fluxo_estudante.png)

---

## 8. Fluxo do Responsável

Representa o acompanhamento da evolução do estudante, consulta a relatórios e recebimento de comunicados.

![Responsável](../assets/fluxos/fluxo_responsavel.png)

---

## 9. Fluxo dos Objetos Pedagógicos

Representa o acesso, utilização e associação dos Objetos Pedagógicos às atividades e questões.

![Objetos Pedagógicos](../assets/fluxos/fluxo_carta_pedagogica.png)

---

## 10. Fluxo do Motor Pedagógico

Representa o processamento das regras pedagógicas, avaliação, feedback e atualização do progresso.

![Motor](../assets/fluxos/fluxo_motor_pedagogico.png)

---

## 11. Fluxo dos indicadores

Representa a consolidação dos dados educacionais para geração de indicadores.

![Indicadores](../assets/fluxos/fluxo_indicadores.png)

---

## 12. Fluxo dos Dashboards

Representa a construção das visões analíticas para cada perfil de usuário.

![Dashboards](../assets/fluxos/fluxo_dashboards.png)

---

# 13. Legenda dos Fluxos

- **Início/Fim** — início ou término do processo.
- **Processo** — execução de uma ação.
- **Decisão** — ponto de escolha ou validação.
- **Conector** — continuidade do fluxo.

---

# 14. Organização dos Arquivos

```text
docs/
└── assets/
    └── fluxos/
        ├── fluxo-gpa-01-geral.png
        ├── fluxo-gpa-02-administrador.png
        ├── fluxo-gpa-03-orgao-central.png
        ├── fluxo-gpa-04-diretor-coordenador.png
        ├── fluxo-gpa-05-professor.png
        ├── fluxo-gpa-06-estudante.png
        ├── fluxo-gpa-07-responsavel.png
        ├── fluxo-gpa-08-objetos-pedagogicos.png
        ├── fluxo-gpa-09-motor-pedagogico.png
        ├── fluxo-gpa-10-indicadores.png
        └── fluxo-gpa-11-dashboards.png
```

---

# 15. Integração entre Fluxos

Os fluxos apresentados complementam os Casos de Uso, o Diagrama de Classes e a Arquitetura Multiplataforma, permitindo rastrear cada processo operacional desde a arquitetura até a implementação.

---

# 16. Considerações Finais

Os fluxos documentados representam a sequência operacional da plataforma GPA e orientam a implementação das interfaces, APIs, regras de negócio e experiência do usuário, mantendo alinhamento com a documentação consolidada da versão **v1.3.3**.
