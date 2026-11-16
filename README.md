# Previsão de notas com Machine Learning

Este projeto usa regressão linear para estimar a nota de um estudante a partir das horas de estudo, da frequência nas aulas, das horas de sono e do nível de motivação. A implementação está no notebook [`previsao-notas.ipynb`](previsao-notas.ipynb).

## Dados

O projeto usa 6.607 registros da base [Student Performance Factors](https://www.kaggle.com/datasets/lainguyn123/student-performance-factors), disponível no Kaggle.

| Coluna | Uso no projeto |
|---|---|
| `Hours_Studied` | Horas de estudo |
| `Attendance` | Frequência nas aulas |
| `Sleep_Hours` | Horas de sono |
| `Motivation_Level` | Nível de motivação |
| `Exam_Score` | Nota real que o modelo aprende a prever |

## Como o modelo foi avaliado

O nível de motivação foi convertido em colunas indicadoras para que pudesse ser usado na regressão. Os dados foram divididos em 5.285 registros de treino e 1.322 de teste.

A regressão linear foi comparada com uma regra simples que prevê a média das notas do treino para todos os estudantes. As duas abordagens foram avaliadas no mesmo conjunto de teste. A métrica usada foi o **erro absoluto médio (MAE)**, que mede, em pontos, a distância média entre as notas previstas e as notas reais.

| Abordagem | MAE no teste |
|---|---:|
| Regressão linear | **1,44 ponto** |
| Previsão pela média do treino | 2,82 pontos |

A regressão reduziu o erro absoluto médio em aproximadamente **49%** em relação à previsão pela média nesse conjunto de teste.

## Exemplo de previsão

Para um estudante fictício com 20 horas de estudo, 85 de frequência na escala da base, 7 horas de sono e motivação média, o modelo estimou uma nota de **68,27 pontos**.

## Como executar no Windows

1. Baixe ou clone o repositório e abra a pasta do projeto no VS Code.
2. Se o CSV não estiver incluído, baixe a base na página do Kaggle e salve o arquivo em `dados/estudantes.csv`. O notebook usa as cinco colunas listadas na seção **Dados**.
3. Abra o **Prompt de Comando** na pasta do projeto e execute os comandos abaixo para criar o ambiente virtual e instalar as dependências.

   ```cmd
   py -m venv .venv
   .venv\Scripts\activate
   python -m pip install -r requirements.txt
   ```

4. Com as extensões **Python** e **Jupyter** instaladas no VS Code, abra `previsao-notas.ipynb` e selecione o Python da `.venv` como kernel.
5. Clique em **Run All** para executar todas as células e reproduzir os resultados.