# 16 — Arquitetura Multiplataforma

# Arquitetura Multiplataforma

**GPA – Gamificação Pedagógica de Aprendizagens**  
**Documento:** Arquitetura Multiplataforma   
**Versão:** 1.3.3
**Área:** Engenharia
**Documento relacionado:** `09_ARQUITETURA_DE_SOFTWARE.md`
                         - `14_DIAGRAMA_DE_CLASSES.md`
                         - `15_DIAGRAMA_DE_CASOS_DE_USO.md`

---

# 1. Objetivo

Este documento define a arquitetura multiplataforma do GPA, estabelecendo como os componentes do sistema se organizam para atender diferentes dispositivos utilizando uma única base tecnológica e um domínio pedagógico comum.

## Diagrama Geral da Arquitetura

![Arquitetura Geral do GPA](../assets/arquitetura/arquitetura_geral_gpa.png)

---

# 2. Decisão Técnica Principal

O GPA será desenvolvido com:

- **Frontend:** Flutter
- **Backend:** Python
- **Banco de Dados:** PostgreSQL

Plataformas suportadas:

- Web
- Android
- iOS
- Windows
- Linux
- macOS
- Tablets

---

# 3. Princípio Central

O GPA é composto por:

- Um domínio pedagógico único;
- Uma API única;
- Interfaces adaptadas para cada dispositivo.

---

# 4. Princípios Arquiteturais

- Single Source of Truth
- API First
- Arquitetura Multiplataforma
- Domínio Pedagógico Compartilhado
- Objetos Pedagógicos Reutilizáveis
- Segurança por Perfil e Escopo
- Observabilidade e Auditoria

---

# 5. Arquitetura em Camadas

![Arquitetura em Camadas](../assets/arquitetura/arquitetura_camadas.png)

---

# 6. Arquitetura do Frontend (Flutter)

![Arquitetura Flutter](../assets/arquitetura/arquitetura_flutter.png)

### Responsabilidades

- Interface gráfica
- Cartas pedagógicas
- Áudio
- Imagens
- Animações
- Dashboards
- Gamificação
- Experiência do usuário

Os módulos implementam os Casos de Uso descritos em `15_DIAGRAMA_DE_CASOS_DE_USO.md`.

---

# 7. Arquitetura do Backend (Python)

![Arquitetura Backend](../assets/arquitetura/arquitetura_backend.png)

### Responsabilidades

- API
- Autenticação
- Autorização
- Motor Pedagógico
- Motor de Gamificação
- Indicadores
- Relatórios
- IA
- Auditoria
- Persistência

As regras de negócio seguem o `14_DIAGRAMA_DE_CLASSES.md`.

---

# 8. Comunicação entre Componentes

![Fluxo de Comunicação](../assets/arquitetura/fluxo_comunicacao.png)

Este diagrama representa a comunicação entre Flutter, API, Backend Python e PostgreSQL.

---

# 9. Experiência por Dispositivo

### Desktop / Web

- Administrador
- Órgão Central
- Diretor
- Professor

### Tablet

- Professor
- Estudante

### Smartphone

- Pais / Responsáveis
- Estudante

---

# 10. Regras de Consistência

1. O progresso do estudante é único em qualquer dispositivo.
2. Os Objetos Pedagógicos são reutilizados em todas as plataformas.
3. Os relatórios respeitam perfil e escopo.
4. A Carta Pedagógica possui comportamento idêntico em qualquer plataforma.
5. O domínio pedagógico permanece único.

---

# 11. Arquitetura de Implantação

![Arquitetura de Implantação](../assets/arquitetura/arquitetura_deployment.png)

---

# 12. Fluxo Lógico de Implantação

Usuário → Flutter → HTTPS → API → Backend → PostgreSQL → API → Interface.

---

# 13. Escalabilidade

- Novos módulos.
- Novas plataformas.
- IA.
- Integrações.
- Escalabilidade horizontal.

---

# 14. Organização dos Arquivos

```text
docs/
└── assets/
    └── arquitetura/
        ├── arquitetura_geral_gpa.png
        ├── arquitetura_camadas.png
        ├── arquitetura_flutter.png
        ├── arquitetura_backend.png
        ├── fluxo_comunicacao.png
        └── arquitetura_deployment.png
```

---

# 15. Considerações Finais

A arquitetura multiplataforma do GPA separa claramente responsabilidades entre interface, serviços, domínio pedagógico e persistência de dados. Essa organização permite evolução da plataforma sem fragmentar as regras de negócio nem os Objetos Pedagógicos, garantindo escalabilidade, manutenção e reutilização do código, está alinhada à documentação da versão v1.3.3.
