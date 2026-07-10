# 10. Modelo de Domínio

# Modelo de Domínio

**GPA – Gamificação Pedagógica de Aprendizagens**  
**Documento:** Modelo de Domínio   
**Versão:** 1.3.3
**Área:** Engenharia
**Documento relacionado:** `09_ARQUITETURA_DE_SOFTWARE.md`

---

## 1. Objetivo

Este documento descreve o **Modelo de Domínio** do GPA, ou seja, o vocabulário principal do sistema e os conceitos que orientam sua implementação.

O Modelo de Domínio não é um modelo de banco de dados e não representa tabelas, chaves primárias ou comandos SQL. Ele define os conceitos essenciais que devem ser compreendidos pela equipe pedagógica, técnica e de gestão.

Este documento serve como base para os documentos posteriores de modelagem, especialmente:

- `11_MODELO_CONCEITUAL.md`
- `12_MODELO_LOGICO.md`
- `13_MODELO_FISICO.md`
- `14_DIAGRAMA_DE_CLASSES.md`
- `15_DIAGRAMA_DE_CASOS_DE_USO.md`

---

## 2. Mapa Geral do Domínio

A Figura 1 apresenta uma visão conceitual do domínio do GPA, destacando os principais grupos de conceitos do sistema e suas relações em alto nível.

Este diagrama não representa arquitetura de software, banco de dados ou infraestrutura. Seu objetivo é apresentar o vocabulário central do domínio do projeto.

<div align="center">

![Diagrama Conceitual de Domínio do GPA](../assets/modelos/diagrama-modelo-dominio-gpa.png)

**Figura 1 – Diagrama conceitual de domínio do GPA.**

</div>

---

## 3. Domínios do Sistema

O GPA é organizado em oito grandes domínios:

```text
GPA
├── Usuários e permissões
├── Estrutura organizacional
├── Núcleo pedagógico
├── Objetos pedagógicos e mídias
├── Atividades, respostas e progresso
├── Gamificação pedagógica
├── Relatórios e indicadores
└── Sistema, auditoria e segurança
```

---

## 4. Usuários e Permissões

### Usuário

Representa qualquer pessoa que acessa o sistema.

Exemplos:

- administrador;
- gestor regional;
- diretor;
- coordenador pedagógico;
- professor;
- responsável;
- estudante.

### Perfil

Define o nível de responsabilidade do usuário.

Perfis previstos:

```text
Administrador
Nível 1 — Regional
Nível 2 — Setor / Escola
Nível 3 — Local / Professor
Nível 4 — Acompanhamento / Responsáveis
```

### Permissão

Define o que um usuário pode fazer.

Exemplos:

- cadastrar escola;
- cadastrar professor;
- cadastrar estudante;
- criar atividade;
- visualizar relatório;
- administrar objetos pedagógicos.

### Escopo de Acesso

Define quais dados o usuário pode acessar.

Exemplos:

```text
REDE
REGIONAL
ESCOLA
TURMA
SALA
ALUNO
```

### Regra central

```text
Perfil define o que o usuário pode fazer.
Escopo define quais dados o usuário pode acessar.
```

---

## 5. Estrutura Organizacional

### Rede de Ensino

Representa a instância maior de organização educacional.

### Regional

Representa uma unidade administrativa intermediária, como uma Diretoria Regional, Unidade Regional de Ensino ou Secretaria Municipal.

### Escola

Representa a unidade escolar.

### Turma

Representa o agrupamento pedagógico de estudantes em determinado ano, série ou etapa.

### Sala

Representa o espaço ou agrupamento operacional onde os estudantes realizam atividades.

### Professor

Usuário responsável pela aplicação das atividades, acompanhamento das turmas e análise dos indicadores.

### Estudante

Sujeito central do processo de aprendizagem no GPA.

### Responsável

Usuário vinculado a um ou mais estudantes, com acesso restrito aos relatórios dos estudantes sob sua responsabilidade.

---

## 6. Núcleo Pedagógico

### Currículo

Estrutura maior que organiza a aprendizagem prevista.

### Eixo de Conhecimento

Agrupa competências e habilidades por área ou dimensão pedagógica.

### Competência

Representa uma capacidade ampla a ser desenvolvida.

### Habilidade

Representa uma aprendizagem específica observável.

### Objetivo de Aprendizagem

Define uma intenção pedagógica concreta que orienta atividades e avaliações.

### Sequência Didática

Organiza atividades em uma progressão planejada.

### Atividade

Representa uma proposta pedagógica aplicada ao estudante.

---

## 7. Objetos Pedagógicos e Mídias

### Objeto Pedagógico

É uma unidade permanente de conteúdo pedagógico. Cada Objeto Pedagógico possui um identificador estável e rastreável.

Exemplo:

```text
OP-000001 → abacaxi
```

O código permanente não deve ser alterado, mesmo que o título, a imagem ou os arquivos associados sejam revisados.

### Mídia do Objeto

Representa uma manifestação do Objeto Pedagógico.

Tipos previstos:

```text
IMAGEM
TEXTO
AUDIO
VIDEO
ANIMACAO
OUTROS
```

Subtipos importantes para áudio:

```text
PRONUNCIA_DIRETA
PRONUNCIA_FRAGMENTADA
```

### Associação Trimodal

Princípio pedagógico que relaciona:

```text
Imagem + Texto + Áudio
```

Exemplo:

```text
Objeto: OP-000001 — abacaxi
Imagem: abacaxi.png
Texto: abacaxi
Áudio direto: abacaxi.mp3
Áudio fragmentado: a-ba-ca-xi.mp3
```

---

## 8. Carta Pedagógica

A Carta Pedagógica é uma representação interativa de um Objeto Pedagógico na interface.

Regra de interação com áudio:

```text
1º toque → pronúncia direta
2º toque → pronúncia fragmentada
3º toque → pronúncia direta
4º toque → pronúncia fragmentada
```

Essa regra pertence à camada de aplicação/interface, mas depende da correta associação entre Objeto Pedagógico e Mídias.

---

## 9. Atividades, Respostas e Progresso

### Tentativa de Atividade

Representa a execução de uma atividade por um estudante.

### Questão

Representa uma unidade avaliável dentro de uma atividade.

### Resposta

Registra a resposta do estudante a uma questão.

### Resultado

Registra se houve acerto, erro, pontuação e feedback.

### Progresso do Estudante

Representa a evolução do estudante por habilidade, objetivo ou domínio pedagógico.

---

## 10. Gamificação Pedagógica

### Avatar

Representação do estudante no ambiente gamificado.

### Personagem

Elemento narrativo ou visual associado à jornada do estudante.

### Nível

Representa avanço progressivo no percurso.

### Conquista

Representa reconhecimento por desempenho, participação ou evolução.

### Recompensa

Elemento motivacional concedido ao estudante.

A gamificação deve reforçar a aprendizagem e não substituir a avaliação pedagógica.

---

## 11. Relatórios, Dashboards e Indicadores

### Indicador

Representa uma métrica pedagógica calculada a partir das interações, respostas e resultados.

Exemplos:

- taxa de acerto;
- tempo de resposta;
- dificuldade por habilidade;
- evolução por estudante;
- desempenho por turma;
- erros recorrentes.

### Dashboard

Organiza indicadores em painéis visuais de acompanhamento para diferentes perfis de usuário.

### Relatório

Organiza indicadores em visões úteis para análise pedagógica, administrativa e institucional.

Tipos previstos:

```text
GERAL_REDE
GERAL_REGIONAL
GERAL_ESCOLA
GERAL_TURMA
GERAL_SALA
INDIVIDUAL_ALUNO
POR_ATIVIDADE
POR_QUESTAO
POR_HABILIDADE
POR_ACERTO
POR_ERRO
POR_EVOLUCAO
```

---

## 12. Sistema, Auditoria e Segurança

### Autenticação

Processo de identificação do usuário no sistema.

### Autorização

Processo que define quais ações o usuário pode executar.

### Log do Sistema

Registra eventos relevantes, como acesso, falhas, ações críticas e alterações.

### Auditoria

Registra alterações importantes em dados sensíveis ou estruturais.

### Segurança

Abrange autenticação, autorização, proteção de dados, privacidade e rastreabilidade.

---

## 13. Relação entre os Principais Conceitos

O domínio do GPA pode ser compreendido pela seguinte sequência conceitual:

```text
Usuário
   ↓
Perfil e Escopo de Acesso
   ↓
Estrutura Organizacional
   ↓
Núcleo Pedagógico
   ↓
Objeto Pedagógico
   ↓
Atividade
   ↓
Tentativa
   ↓
Resposta
   ↓
Resultado
   ↓
Indicadores
   ↓
Dashboards e Relatórios
```

---

## 14. Regras Gerais do Domínio

### Usuários e acesso

1. Todo usuário deve possuir perfil e escopo de acesso.
2. O perfil define o que o usuário pode fazer.
3. O escopo limita quais dados o usuário pode acessar.
4. Relatórios e dashboards respeitam perfil e escopo de acesso.

### Objetos pedagógicos

5. O Objeto Pedagógico deve possuir identificador permanente.
6. Um Objeto Pedagógico pode possuir múltiplas mídias.
7. Áudios podem ser diretos ou fragmentados.
8. A Carta Pedagógica representa um Objeto Pedagógico na interface.

### Atividades e aprendizagem

9. Atividades utilizam Objetos Pedagógicos.
10. Respostas geram resultados.
11. Resultados alimentam o progresso do estudante.
12. Indicadores são calculados a partir das evidências registradas.

### Gamificação, segurança e auditoria

13. A gamificação deve apoiar a aprendizagem.
14. Logs e auditorias garantem rastreabilidade.
15. Segurança e privacidade devem ser observadas em todos os domínios.

---

## 15. Relação com a Arquitetura

O Modelo de Domínio é a base conceitual da arquitetura do GPA.

```text
Modelo de Domínio
      ↓
Modelo Conceitual
      ↓
Modelo Lógico
      ↓
Modelo Físico
      ↓
Diagrama de Classes
      ↓
Casos de Uso
```

A arquitetura de software define como esses conceitos serão organizados tecnicamente, enquanto o Modelo de Domínio define o vocabulário e as relações conceituais do sistema.

---

## 16. Considerações Finais

O Modelo de Domínio funciona como vocabulário oficial do GPA. Ele deve ser utilizado como base para o Modelo Conceitual, Modelo Lógico, Modelo Físico, Diagrama de Classes, Casos de Uso e implementação futura.

Este documento deverá ser revisado sempre que novos módulos pedagógicos, novos perfis de usuário ou novos conceitos estruturais forem incorporados ao GPA.
