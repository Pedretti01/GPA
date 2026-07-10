# 14_DIAGRAMA_DE_CLASSES.md

# Diagrama de Classes

**GPA – Gamificação Pedagógica de Aprendizagens**  
**Documento:** Diagrama de Classes   
**Versão:** 1.3.3
**Área:** Engenharia
**Documento relacionado:** `13_MODELO_FISICO.md`

---

# 1. Objetivo do Documento

Este documento apresenta o **Diagrama de Classes** do GPA, representando a estrutura orientada a objetos do sistema.

O Diagrama de Classes atua como ponte entre o Modelo de Domínio, o Modelo Conceitual, o Modelo Lógico, o Modelo Físico e a futura implementação do backend, da aplicação Flutter e dos serviços de domínio.

---

# 2. Diagrama de Classes

<div align="center">

![Diagrama de Classes do GPA](../assets/diagrama/diagrama-de-classes-gpa.png)

**Figura 1 – Diagrama de Classes do GPA.**

</div>

---

# 3. Organização Geral das Classes

As classes do GPA estão organizadas em oito grandes grupos:

1. Usuários e Permissões;
2. Estrutura Organizacional;
3. Núcleo Pedagógico;
4. Objetos Pedagógicos e Mídias;
5. Atividades, Respostas e Progresso;
6. Gamificação;
7. Relatórios, Indicadores e Dashboards;
8. Sistema, Auditoria e Segurança.

---

# 4. Usuários e Permissões

## Classes principais

```text
Usuario
Perfil
Permissao
EscopoAcesso
PerfilPermissao
```

## Responsabilidade

Controlar autenticação, autorização, permissões e escopos de acesso.

## Métodos candidatos

```text
Usuario.autenticar()
Usuario.alterarSenha()
Usuario.obterEscopos()
Perfil.adicionarPermissao()
Perfil.possuiPermissao()
EscopoAcesso.validarAcesso()
```

---

# 5. Estrutura Organizacional

## Classes principais

```text
RedeEnsino
Regional
Escola
Turma
Sala
Professor
ProfessorTurma
Estudante
Responsavel
ResponsavelEstudante
```

## Responsabilidade

Representar a hierarquia institucional e os vínculos entre redes, regionais, escolas, turmas, salas, professores, estudantes e responsáveis.

---

# 6. Núcleo Pedagógico

## Classes principais

```text
Curriculo
EixoConhecimento
Competencia
Habilidade
ObjetivoAprendizagem
SequenciaDidatica
Atividade
Questao
```

## Responsabilidade

Organizar a estrutura curricular, as competências, habilidades, objetivos de aprendizagem, sequências didáticas, atividades e questões.

## Métodos candidatos

```text
Atividade.iniciar()
Atividade.finalizar()
Atividade.obterQuestoes()
Atividade.calcularResultado()
Questao.validarResposta()
```

---

# 7. Objetos Pedagógicos e Mídias

## Classes principais

```text
CategoriaObjeto
TemaObjeto
ObjetoPedagogico
MidiaObjeto
QuestaoObjeto
CartaPedagogica
```

## Responsabilidade

Representar os conteúdos pedagógicos permanentes, suas mídias associadas e sua utilização nas atividades.

## Regras

Cada Objeto Pedagógico deve possuir um identificador permanente, como:

```text
OP-000001
OP-000002
OP-000003
```

Um Objeto Pedagógico poderá possuir áudios dos tipos:

```text
PRONUNCIA_DIRETA
PRONUNCIA_FRAGMENTADA
```

## Métodos candidatos

```text
ObjetoPedagogico.adicionarMidia()
ObjetoPedagogico.obterMidiasPorTipo()
ObjetoPedagogico.obterAudioDireto()
ObjetoPedagogico.obterAudioFragmentado()
CartaPedagogica.tocar()
CartaPedagogica.alternarAudio()
CartaPedagogica.exibirImagem()
CartaPedagogica.exibirTexto()
```

---

# 8. Atividades, Respostas e Progresso

## Classes principais

```text
TentativaAtividade
Resposta
Resultado
ProgressoEstudante
```

## Responsabilidade

Registrar a execução das atividades, as respostas dos estudantes, os resultados obtidos e a evolução pedagógica.

## Métodos candidatos

```text
TentativaAtividade.iniciar()
TentativaAtividade.finalizar()
TentativaAtividade.registrarResposta()
Resposta.validar()
Resultado.calcularPontuacao()
ProgressoEstudante.atualizarDominio()
```

---

# 9. Gamificação

## Classes principais

```text
Avatar
Personagem
Nivel
Conquista
Recompensa
EstudanteConquista
EstudanteRecompensa
```

## Responsabilidade

Controlar elementos motivacionais vinculados ao percurso pedagógico do estudante.

## Métodos candidatos

```text
Avatar.ganharExperiencia()
Avatar.atualizarNivel()
Conquista.verificarCriterio()
Recompensa.atribuirAoEstudante()
```

---

# 10. Relatórios, Indicadores e Dashboards

## Classes principais

```text
Indicador
Dashboard
Relatorio
```

## Responsabilidade

Organizar evidências de aprendizagem em visões analíticas conforme perfil e escopo do usuário.

## Métodos candidatos

```text
Indicador.calcular()
Dashboard.carregarIndicadores()
Relatorio.gerar()
Relatorio.exportar()
```

---

# 11. Sistema, Auditoria e Segurança

## Classes principais

```text
LogSistema
Auditoria
```

## Responsabilidade

Registrar eventos técnicos, ações críticas, alterações, rastreabilidade e informações de auditoria.

## Métodos candidatos

```text
LogSistema.registrarEvento()
LogSistema.registrarErro()
Auditoria.registrarAcao()
Auditoria.obterAlteracoes()
```

---

# 12. Relação com os Demais Documentos

Este documento complementa:

- 10_MODELO_DE_DOMINIO.md
- 11_MODELO_CONCEITUAL.md
- 12_MODELO_LOGICO.md
- 13_MODELO_FISICO.md
- 15_DIAGRAMA_DE_CASOS_DE_USO.md

O Diagrama de Classes traduz os conceitos do domínio e da modelagem de dados em uma visão orientada a objetos, apoiando a futura implementação do sistema.

---

# 13. Considerações Finais

O Diagrama de Classes consolida a visão orientada a objetos do GPA, preservando a separação por domínios e mantendo alinhamento com a arquitetura pedagógica, a arquitetura de software e a modelagem de dados.

Este documento deverá evoluir conforme a implementação do backend, da aplicação Flutter e dos serviços de domínio forem consolidados.
