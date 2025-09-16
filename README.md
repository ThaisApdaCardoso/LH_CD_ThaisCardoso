# Estudo de Caso: Análise de Filmes para a PProductions

## Sobre o Projeto

Este projeto foi desenvolvido como um estudo de caso de Ciência de Dados para a empresa Indicium. O cenário proposto envolve uma consultoria para um estúdio de Hollywood fictício, a **PProductions**, que busca orientação baseada em dados para decidir qual tipo de filme deve ser sua próxima grande produção.

O objetivo é analisar um banco de dados cinematográfico para identificar fatores de sucesso, extrair insights e construir um modelo de previsão para estimar a nota do IMDB de um filme.

---

## Objetivo

Analisar detalhadamente uma base de dados de filmes, identificando fatores de sucesso dessas obras e criando um modelo de previsão para estimar a nota no IMDB de um filme através de algumas características, além de responder às seguintes questões do estúdio:

1.  **Recomendação Universal:** Qual filme seria a aposta mais segura para recomendar a um público geral?
2.  **Fatores de Sucesso Financeiro:** Quais são os principais fatores que se relacionam com um alto `Gross` (faturamento)?
3.  **Análise de Roteiros:** Que insights podem ser extraídos do `Overview` (resumo) dos filmes?
4.  **Previsão de Qualidade:** Como prever o `IMDB_Rating` (nota do público no IMDb) com base nas características de um filme?

---

## Análise e Insights

Após o processo de limpeza e pré-processamento dos dados, a análise exploratória revelou os seguintes insights:

* **Recomendação Universal:** O filme **"Parasita" (Gisaengchung)** foi selecionado como a recomendação ideal. A escolha se baseia em suas altíssimas notas tanto da crítica (`Meta_score`) quanto do público (`IMDB_Rating`), além de seu apelo global, comprovado por suas múltiplas vitórias no Oscar 2020, incluindo Melhor Filme.
* **Fatores de Sucesso Financeiro:**
    * O fator numérico que tem maior correlação com o `Gross` (faturamento) é o **`No_of_Votes`**, com um coeficiente de **0.57**. Isso sugere que o engajamento e a popularidade de um filme são cruciais para o sucesso de bilheteria.
    * Ao analisar os gêneros, ficou claro que as maiores médias de faturamento pertencem aos filmes que combinam **Ação, Aventura, Sci-Fi e Fantasia**, de preferência com um apelo **Familiar**.
* **Insights do `Overview`:** Através de uma Nuvem de Palavras-chave, foi identificado que os temas mais comuns em filmes de sucesso têm uma natureza extremamente humana, girando em torno de conceitos como **vida (`life`), família (`family`), homem (`man`), mulher (`woman`) e suas jornadas (`find`, `story`, `world`)**.
* **Descoberta através dos gráficos de dispersão:** foi confirmada uma forte correlação positiva entre a nota da crítica (`Meta_score`) e a nota do público (`IMDB_Rating`), validando a escolha dessas features para o modelo.

---

## Modelo Preditivo

Para prever a nota do IMDb, foi desenvolvido um modelo de Machine Learning.

* **Tipo de Problema:** **Regressão**, devido ao objetivo de prever a nota do IMDB, e se trata de um valor numérico.
* **Variáveis Utilizadas:** `Meta_score`, `No_of_Votes`, `Gross` e `Genre_Principal`. A variável de gênero foi simplificada para conter apenas o gênero principal de cada filme e foi transformada em variáveis numéricas através de One-Hot Encoding.
* **Modelo Escolhido:** Foi utilizado um modelo de **Regressão Linear** por sua simplicidade, rapidez e facilidade de interpretação.
* **Performance:** O modelo alcançou um **RMSE (Raiz do Erro Quadrático Médio) de 0.21**, indicando que, em média, suas previsões erram a nota do IMDb por apenas 0.21 pontos, o que demonstra uma alta precisão do modelo. Ao ser testado com o filme "The Shawshank Redemption", o modelo previu uma nota de **9.28**, muito próxima da nota real de 9.3. Além disso, o modelo alcançou um excelente R² (Coeficiente de Determinação) de 0.8143, indicando que o modelo é muito preciso (errando em média apenas 0.21 pontos) e também consegue explicar 81,4% da variação nas notas do IMDb com base nas features selecionadas.

---

## Como Executar o Projeto

1. **Clone o repositório:**
    ```bash
    git clone https://github.com/ThaisApdaCardoso/LH_CD_ThaisCardoso
    ```
2.  **Crie um ambiente virtual (recomendado):**
    ```bash
    python -m venv venv
    source venv/bin/activate (No Windows: venv\Scripts\activate)
    ```
3.  **Instale as dependências:**
    ```bash
    pip install -r requirements.txt
    ```
4.  **Execute o Notebook:** Abra e execute o arquivo `.ipynb` (`LH_CD_ThaisCardoso.ipynb`) em um ambiente Jupyter.

---

## Ferramentas Utilizadas

* **Linguagem:** Python 3
* **Bibliotecas Principais:**
    * `pandas` para manipulação e análise de dados.
    * `matplotlib` e `seaborn` para visualização de dados.
    * `wordcloud` para análise de texto.
    * `scikit-learn` para a construção do modelo de Machine Learning.
    * `joblib` para salvar o modelo treinado.
