# Modelagem Dimensional (Star Schema)Esquema estrela pro projeto DIO

Projeto desenvolvido para o desafio **Criando um Star Schema para Cenários de Universidade com Power BI** do bootcamp de Engenharia de Dados (DIO & NTT Data).

## Objetivo
Transformar um modelo relacional de ambiente universitário em um **modelo dimensional (Star Schema)** voltado para a análise de dados dos **professores** (disciplinas ministradas, cursos, departamentos 
e períodos de oferta), desconsiderando entidades fora do escopo como alunos e matrículas.

## Estrutura do Modelo

### Tabela Fato
* **`Fato_Professor`**: Centraliza os identificadores das dimensões (`idProfessor`, `idDepartamento`, `idCurso`, `idDisciplina`, `idData`) e as métricas quantitativas de análise (`Carga_Horaria` e
`Qtd_Disciplinas`).

### Tabelas Dimensão
* **`Dim_Professor`**: Atributos descritivos dos docentes (`idProfessor`, `Nome_Professor`, `Titulacao`).
* **`Dim_Departamento`**: Informações organizacionais (`idDepartamento`, `Nome_Departamento`, `Campus`, `idProfessor_coordenador`).
* **`Dim_Curso`**: Dados dos cursos vinculados (`idCurso`, `Nome_Curso`, `idDepartamento`).
* **`Dim_Disciplina`**: Detalhes das matérias ofertadas (`idDisciplina`, `Nome_Disciplina`, `Pre_Requisitos`).
* **`Dim_Data`**: Dimensão temporal criada para suportar análises por período de oferta (`idData`, `Data_Oferta`, `Ano`, `Semestre`, `Mes`).

## Relacionamentos
* Todas as 5 tabelas dimensão conectam-se diretamente à `Fato_Professor` com cardinalidade **Um para Muitos (`1:*`)**, evitando relacionamentos entre dimensões (*Snowflake*) e otimizando a performance
de filtros no Power BI.
