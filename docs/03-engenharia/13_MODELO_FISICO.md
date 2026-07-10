# 13. Modelo Físico de Dados

# Modelo Físico de Dados

**GPA – Gamificação Pedagógica de Aprendizagens**  
**Documento:** Modelo Físico de Dados   
**Versão:** 1.3.3
**Área:** Engenharia
**Banco recomendado:** PostgreSQL
**Documento relacionado:** `12_MODELO_LOGICO.md`

---

## 1. Objetivo do documento

Este documento apresenta a primeira versão do **Modelo Físico de Dados** do GPA, derivado do Modelo Lógico.

Diferentemente do modelo lógico, este documento já considera decisões específicas de implementação em banco de dados, como:

- schemas;
- tipos de dados PostgreSQL;
- chaves primárias;
- chaves estrangeiras;
- constraints;
- índices;
- campos `JSONB`;
- campos de auditoria;
- estratégia para identificadores permanentes.

---

## 2. Diagrama do Modelo Físico

<div align="center">

![Modelo Físico do GPA](../assets/modelos/modelo-fisico-gpa.png)

**Figura 1 – Modelo Físico de Dados do GPA.**

</div>

---

## 3. Convenções físicas

| Convenção | Uso |
|---|---|
| `BIGSERIAL` | Chaves primárias internas |
| `VARCHAR` | Textos curtos com limite definido |
| `TEXT` | Textos longos |
| `JSONB` | Configurações, respostas flexíveis e critérios |
| `TIMESTAMPTZ` | Datas com fuso horário |
| `created_at` | Data de criação do registro |
| `updated_at` | Data de atualização do registro |
| `codigo_permanente` | Identificador fixo do Objeto Pedagógico, como `OP-000001` |

---

## 4. Extensões recomendadas

```sql
CREATE EXTENSION IF NOT EXISTS citext;
```

A extensão `citext` permite tratar e-mails sem diferenciação entre letras maiúsculas e minúsculas.

---

## 5. Organização por schemas

```sql
CREATE SCHEMA IF NOT EXISTS core_acesso;
CREATE SCHEMA IF NOT EXISTS educacional;
CREATE SCHEMA IF NOT EXISTS pedagogico;
CREATE SCHEMA IF NOT EXISTS objetos;
CREATE SCHEMA IF NOT EXISTS avaliacao;
CREATE SCHEMA IF NOT EXISTS gamificacao;
CREATE SCHEMA IF NOT EXISTS observabilidade;
```

---

## 6. Schema `core_acesso`

Responsável por usuários, perfis, permissões e escopos de acesso.

```sql
CREATE TABLE core_acesso.perfil (
    id BIGSERIAL PRIMARY KEY,
    nome VARCHAR(80) NOT NULL UNIQUE,
    nivel SMALLINT NOT NULL UNIQUE,
    descricao TEXT
);

CREATE TABLE core_acesso.permissao (
    id BIGSERIAL PRIMARY KEY,
    chave VARCHAR(100) NOT NULL UNIQUE,
    descricao TEXT
);

CREATE TABLE core_acesso.perfil_permissao (
    perfil_id BIGINT NOT NULL REFERENCES core_acesso.perfil(id) ON DELETE CASCADE,
    permissao_id BIGINT NOT NULL REFERENCES core_acesso.permissao(id) ON DELETE CASCADE,
    PRIMARY KEY (perfil_id, permissao_id)
);

CREATE TABLE core_acesso.usuario (
    id BIGSERIAL PRIMARY KEY,
    perfil_id BIGINT NOT NULL REFERENCES core_acesso.perfil(id),
    codigo VARCHAR(30) NOT NULL UNIQUE,
    nome VARCHAR(150) NOT NULL,
    email CITEXT NOT NULL UNIQUE,
    senha_hash TEXT NOT NULL,
    status VARCHAR(20) NOT NULL DEFAULT 'ativo',
    created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    updated_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    CONSTRAINT ck_usuario_status CHECK (status IN ('ativo', 'inativo', 'bloqueado'))
);

CREATE TABLE core_acesso.escopo_acesso (
    id BIGSERIAL PRIMARY KEY,
    usuario_id BIGINT NOT NULL REFERENCES core_acesso.usuario(id) ON DELETE CASCADE,
    tipo_escopo VARCHAR(30) NOT NULL,
    referencia_id BIGINT NOT NULL,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    CONSTRAINT ck_tipo_escopo CHECK (
        tipo_escopo IN ('sistema', 'rede', 'regional', 'escola', 'turma', 'sala', 'estudante')
    ),
    CONSTRAINT uq_escopo_usuario UNIQUE (usuario_id, tipo_escopo, referencia_id)
);
```

---

## 7. Schema `educacional`

Responsável pela estrutura organizacional: rede, regional, escola, turma, sala, estudantes, professores e responsáveis.

```sql
CREATE TABLE educacional.rede_ensino (
    id BIGSERIAL PRIMARY KEY,
    nome VARCHAR(150) NOT NULL,
    municipio VARCHAR(100),
    uf CHAR(2),
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE educacional.regional (
    id BIGSERIAL PRIMARY KEY,
    rede_id BIGINT NOT NULL REFERENCES educacional.rede_ensino(id),
    nome VARCHAR(150) NOT NULL,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE educacional.escola (
    id BIGSERIAL PRIMARY KEY,
    regional_id BIGINT NOT NULL REFERENCES educacional.regional(id),
    nome VARCHAR(180) NOT NULL,
    inep VARCHAR(20) UNIQUE,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE educacional.turma (
    id BIGSERIAL PRIMARY KEY,
    escola_id BIGINT NOT NULL REFERENCES educacional.escola(id),
    ano_letivo SMALLINT NOT NULL,
    nome VARCHAR(80) NOT NULL,
    etapa VARCHAR(60),
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE educacional.sala (
    id BIGSERIAL PRIMARY KEY,
    turma_id BIGINT NOT NULL REFERENCES educacional.turma(id),
    nome VARCHAR(80) NOT NULL,
    turno VARCHAR(20),
    created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    CONSTRAINT ck_sala_turno CHECK (turno IS NULL OR turno IN ('manha', 'tarde', 'noite', 'integral'))
);

CREATE TABLE educacional.estudante (
    id BIGSERIAL PRIMARY KEY,
    sala_id BIGINT NOT NULL REFERENCES educacional.sala(id),
    nome VARCHAR(150) NOT NULL,
    data_nascimento DATE,
    matricula VARCHAR(50) UNIQUE,
    status VARCHAR(20) NOT NULL DEFAULT 'ativo',
    created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    updated_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    CONSTRAINT ck_estudante_status CHECK (status IN ('ativo', 'inativo', 'transferido'))
);

CREATE TABLE educacional.professor (
    id BIGSERIAL PRIMARY KEY,
    usuario_id BIGINT NOT NULL UNIQUE REFERENCES core_acesso.usuario(id),
    nome VARCHAR(150) NOT NULL,
    registro VARCHAR(50),
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE educacional.professor_turma (
    professor_id BIGINT NOT NULL REFERENCES educacional.professor(id) ON DELETE CASCADE,
    turma_id BIGINT NOT NULL REFERENCES educacional.turma(id) ON DELETE CASCADE,
    ativo BOOLEAN NOT NULL DEFAULT true,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    PRIMARY KEY (professor_id, turma_id)
);

CREATE TABLE educacional.responsavel (
    id BIGSERIAL PRIMARY KEY,
    usuario_id BIGINT NOT NULL UNIQUE REFERENCES core_acesso.usuario(id),
    nome VARCHAR(150) NOT NULL,
    parentesco VARCHAR(50),
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE educacional.responsavel_estudante (
    responsavel_id BIGINT NOT NULL REFERENCES educacional.responsavel(id) ON DELETE CASCADE,
    estudante_id BIGINT NOT NULL REFERENCES educacional.estudante(id) ON DELETE CASCADE,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    PRIMARY KEY (responsavel_id, estudante_id)
);
```

---

## 8. Schema `pedagogico`

Responsável por currículo, competências, habilidades, objetivos, sequências, atividades e questões.

```sql
CREATE TABLE pedagogico.curriculo (
    id BIGSERIAL PRIMARY KEY,
    nome VARCHAR(150) NOT NULL,
    versao VARCHAR(40),
    ano_base SMALLINT,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE pedagogico.eixo_conhecimento (
    id BIGSERIAL PRIMARY KEY,
    curriculo_id BIGINT NOT NULL REFERENCES pedagogico.curriculo(id),
    nome VARCHAR(150) NOT NULL,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE pedagogico.competencia (
    id BIGSERIAL PRIMARY KEY,
    eixo_id BIGINT NOT NULL REFERENCES pedagogico.eixo_conhecimento(id),
    codigo VARCHAR(40) NOT NULL UNIQUE,
    descricao TEXT NOT NULL,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE pedagogico.habilidade (
    id BIGSERIAL PRIMARY KEY,
    competencia_id BIGINT NOT NULL REFERENCES pedagogico.competencia(id),
    codigo VARCHAR(40) NOT NULL UNIQUE,
    descricao TEXT NOT NULL,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE pedagogico.objetivo_aprendizagem (
    id BIGSERIAL PRIMARY KEY,
    habilidade_id BIGINT NOT NULL REFERENCES pedagogico.habilidade(id),
    descricao TEXT NOT NULL,
    nivel SMALLINT,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE pedagogico.sequencia_didatica (
    id BIGSERIAL PRIMARY KEY,
    objetivo_id BIGINT NOT NULL REFERENCES pedagogico.objetivo_aprendizagem(id),
    titulo VARCHAR(180) NOT NULL,
    descricao TEXT,
    ordem SMALLINT DEFAULT 1,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE pedagogico.atividade (
    id BIGSERIAL PRIMARY KEY,
    sequencia_id BIGINT NOT NULL REFERENCES pedagogico.sequencia_didatica(id),
    titulo VARCHAR(180) NOT NULL,
    tipo VARCHAR(50) NOT NULL,
    nivel SMALLINT,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE pedagogico.questao (
    id BIGSERIAL PRIMARY KEY,
    atividade_id BIGINT NOT NULL REFERENCES pedagogico.atividade(id) ON DELETE CASCADE,
    enunciado TEXT,
    tipo VARCHAR(50) NOT NULL,
    ordem SMALLINT DEFAULT 1,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);
```

---

## 9. Schema `objetos`

Responsável por Objetos Pedagógicos, mídias e cartas pedagógicas.

```sql
CREATE TABLE objetos.objeto_pedagogico (
    id BIGSERIAL PRIMARY KEY,
    codigo_permanente VARCHAR(20) NOT NULL UNIQUE,
    tipo VARCHAR(50) NOT NULL,
    titulo VARCHAR(180) NOT NULL,
    descricao TEXT,
    status VARCHAR(20) NOT NULL DEFAULT 'ativo',
    created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    updated_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    CONSTRAINT ck_objeto_codigo CHECK (codigo_permanente ~ '^OP-[0-9]{6}$'),
    CONSTRAINT ck_objeto_status CHECK (status IN ('ativo', 'inativo', 'revisao'))
);

CREATE TABLE objetos.midia_objeto (
    id BIGSERIAL PRIMARY KEY,
    objeto_id BIGINT NOT NULL REFERENCES objetos.objeto_pedagogico(id) ON DELETE CASCADE,
    tipo_midia VARCHAR(30) NOT NULL,
    subtipo VARCHAR(60) NOT NULL,
    arquivo_url TEXT,
    texto_referencia TEXT,
    ordem SMALLINT DEFAULT 1,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    CONSTRAINT ck_tipo_midia CHECK (tipo_midia IN ('texto', 'imagem', 'audio', 'video', 'animacao')),
    CONSTRAINT ck_subtipo_audio CHECK (
        tipo_midia <> 'audio'
        OR subtipo IN ('pronuncia_direta', 'pronuncia_fragmentada', 'efeito_sonoro', 'narracao')
    ),
    CONSTRAINT uq_midia_objeto_subtipo UNIQUE (objeto_id, tipo_midia, subtipo)
);

CREATE TABLE objetos.carta_pedagogica (
    id BIGSERIAL PRIMARY KEY,
    objeto_id BIGINT NOT NULL REFERENCES objetos.objeto_pedagogico(id),
    titulo VARCHAR(150) NOT NULL,
    config_interacao JSONB NOT NULL DEFAULT '{"alternancia_audio": true}'::jsonb,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE objetos.questao_objeto (
    questao_id BIGINT NOT NULL REFERENCES pedagogico.questao(id) ON DELETE CASCADE,
    objeto_id BIGINT NOT NULL REFERENCES objetos.objeto_pedagogico(id),
    papel VARCHAR(50) NOT NULL,
    ordem SMALLINT DEFAULT 1,
    PRIMARY KEY (questao_id, objeto_id, papel)
);
```

### Observação sobre áudio direto e fragmentado

Para cada Objeto Pedagógico do tipo palavra, recomenda-se cadastrar pelo menos dois registros na tabela `objetos.midia_objeto`:

```text
subtipo = pronuncia_direta
subtipo = pronuncia_fragmentada
```

Exemplo:

```sql
INSERT INTO objetos.objeto_pedagogico
(codigo_permanente, tipo, titulo, descricao)
VALUES
('OP-000001', 'palavra', 'abacaxi', 'Objeto pedagógico da palavra abacaxi');

INSERT INTO objetos.midia_objeto
(objeto_id, tipo_midia, subtipo, arquivo_url, texto_referencia, ordem)
VALUES
(1, 'imagem', 'ilustracao', '/imagens/abacaxi.png', 'abacaxi', 1),
(1, 'texto', 'palavra', NULL, 'abacaxi', 2),
(1, 'texto', 'silabacao', NULL, 'a-ba-ca-xi', 3),
(1, 'audio', 'pronuncia_direta', '/audios/abacaxi.mp3', 'abacaxi', 4),
(1, 'audio', 'pronuncia_fragmentada', '/audios/a-ba-ca-xi.mp3', 'a ba ca xi', 5);
```

---

## 10. Schema `avaliacao`

Responsável por tentativas, respostas e progresso por habilidade.

```sql
CREATE TABLE avaliacao.tentativa_atividade (
    id BIGSERIAL PRIMARY KEY,
    estudante_id BIGINT NOT NULL REFERENCES educacional.estudante(id),
    atividade_id BIGINT NOT NULL REFERENCES pedagogico.atividade(id),
    iniciada_em TIMESTAMPTZ NOT NULL DEFAULT now(),
    finalizada_em TIMESTAMPTZ,
    status VARCHAR(20) NOT NULL DEFAULT 'em_andamento',
    CONSTRAINT ck_tentativa_status CHECK (status IN ('em_andamento', 'concluida', 'cancelada'))
);

CREATE TABLE avaliacao.resposta (
    id BIGSERIAL PRIMARY KEY,
    tentativa_id BIGINT NOT NULL REFERENCES avaliacao.tentativa_atividade(id) ON DELETE CASCADE,
    questao_id BIGINT NOT NULL REFERENCES pedagogico.questao(id),
    resposta_dada JSONB,
    correta BOOLEAN,
    tempo_ms INTEGER,
    tentativas SMALLINT NOT NULL DEFAULT 1,
    respondida_em TIMESTAMPTZ NOT NULL DEFAULT now(),
    CONSTRAINT ck_tempo_ms CHECK (tempo_ms IS NULL OR tempo_ms >= 0),
    CONSTRAINT ck_tentativas CHECK (tentativas >= 1)
);

CREATE TABLE avaliacao.progresso_habilidade (
    estudante_id BIGINT NOT NULL REFERENCES educacional.estudante(id) ON DELETE CASCADE,
    habilidade_id BIGINT NOT NULL REFERENCES pedagogico.habilidade(id),
    percentual_dominio NUMERIC(5,2) NOT NULL DEFAULT 0,
    acertos INTEGER NOT NULL DEFAULT 0,
    erros INTEGER NOT NULL DEFAULT 0,
    atualizado_em TIMESTAMPTZ NOT NULL DEFAULT now(),
    PRIMARY KEY (estudante_id, habilidade_id),
    CONSTRAINT ck_percentual_dominio CHECK (percentual_dominio BETWEEN 0 AND 100),
    CONSTRAINT ck_acertos_erros CHECK (acertos >= 0 AND erros >= 0)
);
```

---

## 11. Schema `gamificacao`

Responsável por avatar, conquistas e recompensas.

```sql
CREATE TABLE gamificacao.avatar (
    id BIGSERIAL PRIMARY KEY,
    estudante_id BIGINT NOT NULL UNIQUE REFERENCES educacional.estudante(id) ON DELETE CASCADE,
    nome VARCHAR(100),
    nivel_atual INTEGER NOT NULL DEFAULT 1,
    experiencia INTEGER NOT NULL DEFAULT 0,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    updated_at TIMESTAMPTZ NOT NULL DEFAULT now(),
    CONSTRAINT ck_avatar_nivel CHECK (nivel_atual >= 1),
    CONSTRAINT ck_avatar_xp CHECK (experiencia >= 0)
);

CREATE TABLE gamificacao.recompensa (
    id BIGSERIAL PRIMARY KEY,
    nome VARCHAR(120) NOT NULL,
    tipo VARCHAR(50) NOT NULL,
    criterio JSONB,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE gamificacao.conquista (
    id BIGSERIAL PRIMARY KEY,
    nome VARCHAR(120) NOT NULL,
    descricao TEXT,
    criterio JSONB,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE gamificacao.estudante_recompensa (
    estudante_id BIGINT NOT NULL REFERENCES educacional.estudante(id) ON DELETE CASCADE,
    recompensa_id BIGINT NOT NULL REFERENCES gamificacao.recompensa(id),
    recebida_em TIMESTAMPTZ NOT NULL DEFAULT now(),
    PRIMARY KEY (estudante_id, recompensa_id)
);

CREATE TABLE gamificacao.estudante_conquista (
    estudante_id BIGINT NOT NULL REFERENCES educacional.estudante(id) ON DELETE CASCADE,
    conquista_id BIGINT NOT NULL REFERENCES gamificacao.conquista(id),
    obtida_em TIMESTAMPTZ NOT NULL DEFAULT now(),
    PRIMARY KEY (estudante_id, conquista_id)
);
```

---

## 12. Schema `observabilidade`

Responsável por indicadores, relatórios, logs e auditoria.

```sql
CREATE TABLE observabilidade.indicador (
    id BIGSERIAL PRIMARY KEY,
    nome VARCHAR(120) NOT NULL,
    tipo VARCHAR(50) NOT NULL,
    formula TEXT,
    created_at TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE observabilidade.relatorio (
    id BIGSERIAL PRIMARY KEY,
    usuario_gerador_id BIGINT NOT NULL REFERENCES core_acesso.usuario(id),
    tipo VARCHAR(80) NOT NULL,
    parametros JSONB,
    gerado_em TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE observabilidade.auditoria (
    id BIGSERIAL PRIMARY KEY,
    usuario_id BIGINT REFERENCES core_acesso.usuario(id),
    acao VARCHAR(100) NOT NULL,
    entidade VARCHAR(100) NOT NULL,
    entidade_id BIGINT,
    dados JSONB,
    data_hora TIMESTAMPTZ NOT NULL DEFAULT now()
);

CREATE TABLE observabilidade.log_sistema (
    id BIGSERIAL PRIMARY KEY,
    nivel VARCHAR(20) NOT NULL,
    mensagem TEXT NOT NULL,
    contexto JSONB,
    criado_em TIMESTAMPTZ NOT NULL DEFAULT now(),
    CONSTRAINT ck_log_nivel CHECK (nivel IN ('debug', 'info', 'warning', 'error', 'critical'))
);
```

---

## 13. Índices recomendados

```sql
CREATE INDEX idx_usuario_perfil ON core_acesso.usuario(perfil_id);
CREATE INDEX idx_escopo_usuario ON core_acesso.escopo_acesso(usuario_id);
CREATE INDEX idx_escopo_tipo_ref ON core_acesso.escopo_acesso(tipo_escopo, referencia_id);

CREATE INDEX idx_regional_rede ON educacional.regional(rede_id);
CREATE INDEX idx_escola_regional ON educacional.escola(regional_id);
CREATE INDEX idx_turma_escola ON educacional.turma(escola_id);
CREATE INDEX idx_sala_turma ON educacional.sala(turma_id);
CREATE INDEX idx_estudante_sala ON educacional.estudante(sala_id);

CREATE INDEX idx_habilidade_competencia ON pedagogico.habilidade(competencia_id);
CREATE INDEX idx_atividade_sequencia ON pedagogico.atividade(sequencia_id);
CREATE INDEX idx_questao_atividade ON pedagogico.questao(atividade_id);

CREATE INDEX idx_objeto_codigo ON objetos.objeto_pedagogico(codigo_permanente);
CREATE INDEX idx_midia_objeto ON objetos.midia_objeto(objeto_id);
CREATE INDEX idx_midia_audio ON objetos.midia_objeto(objeto_id, subtipo) WHERE tipo_midia = 'audio';

CREATE INDEX idx_tentativa_estudante ON avaliacao.tentativa_atividade(estudante_id);
CREATE INDEX idx_tentativa_atividade ON avaliacao.tentativa_atividade(atividade_id);
CREATE INDEX idx_resposta_tentativa ON avaliacao.resposta(tentativa_id);
CREATE INDEX idx_resposta_questao ON avaliacao.resposta(questao_id);

CREATE INDEX idx_relatorio_usuario ON observabilidade.relatorio(usuario_gerador_id);
CREATE INDEX idx_auditoria_usuario ON observabilidade.auditoria(usuario_id);
CREATE INDEX idx_auditoria_entidade ON observabilidade.auditoria(entidade, entidade_id);
CREATE INDEX idx_log_criado_em ON observabilidade.log_sistema(criado_em);
```

---

## 14. Considerações sobre LGPD e segurança

O modelo físico deverá ser evoluído considerando:

- criptografia de dados sensíveis quando necessário;
- controle rigoroso por perfil e escopo;
- auditoria de alterações relevantes;
- logs sem exposição indevida de dados pessoais;
- políticas de retenção de dados;
- anonimização ou pseudonimização para análises agregadas.

---

## 15. Decisões físicas iniciais

1. O banco principal do GPA será relacional, preferencialmente **PostgreSQL**.
2. O identificador permanente do Objeto Pedagógico seguirá o padrão `OP-000001`.
3. Áudios de pronúncia direta e fragmentada serão registros separados em `objetos.midia_objeto`.
4. Campos flexíveis e critérios de regras serão armazenados em `JSONB`.
5. Relatórios devem armazenar parâmetros de geração, não cópias completas de dados analíticos.
6. Auditoria e logs ficarão separados dos dados pedagógicos.

---

## 16. Próximos passos

Após validação deste modelo físico, os próximos passos são:

1. revisar nomes finais das tabelas e schemas;
2. validar constraints com as regras pedagógicas;
3. criar scripts de migração;
4. definir seeds iniciais de perfis e permissões;
5. definir views para relatórios e dashboards;
6. revisar requisitos de segurança e LGPD.


---

## 15. Relação com os Demais Documentos

Este documento complementa:

- 12_MODELO_LOGICO.md
- 14_DIAGRAMA_DE_CLASSES.md
- 09_ARQUITETURA_DE_SOFTWARE.md

Representa a implementação física do Modelo Lógico em PostgreSQL.

---

## 16. Considerações Finais

O Modelo Físico consolida as decisões de implementação do banco de dados do GPA, preservando a coerência arquitetural da versão **1.3.3** e servindo de base para migrações, criação do banco e desenvolvimento do backend.
