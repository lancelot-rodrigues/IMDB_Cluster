# Análise de Cluster para Recomendação de Filmes do IMDb

## Visão Geral do Projeto

Este projeto tem como objetivo desenvolver um sistema de recomendação de filmes a partir da lista "IMDb Top 250". Utilizando técnicas de *web scraping* para a coleta de dados e o algoritmo de clusterização *KMeans*, buscamos agrupar os filmes em clusters coesos. A ideia central é que filmes dentro do mesmo cluster possam ser recomendados a usuários que demonstraram interesse em um dos títulos daquele grupo.

Para atingir este objetivo, foram desenvolvidos dois notebooks com abordagens distintas:

1.  **Notebook 1:** Cria clusters utilizando apenas a **sinopse** dos filmes.
2.  **Notebook 2:** Expande a análise, utilizando **todas as features disponíveis** (sinopse, gênero, ano de lançamento e avaliação) e compara os resultados com a primeira abordagem.

## Comparação dos Modelos

A principal diferença entre os dois notebooks reside na riqueza dos dados utilizados para treinar o modelo de clusterização.

### Modelo 1: Clusterização Baseada Apenas na Sinopse

Este modelo utiliza o processamento de linguagem natural (NLP) para transformar o texto da sinopse de cada filme em um vetor numérico (usando TF-IDF). O KMeans então agrupa os filmes com base na similaridade temática de suas histórias.

* **Vantagens:**
    * Consegue identificar com sucesso os temas centrais dos filmes, agrupando-os por enredos similares (ex: um cluster para filmes de guerra, outro para dramas familiares, etc.).
    * Valida a hipótese de que a sinopse é uma feature poderosa para determinar a similaridade.

* **Desvantagens:**
    * **Visão unidimensional:** Ignora contextos cruciais como o gênero, a época (ano) e a recepção do público (avaliação).
    * **Agrupamentos muito amplos:** Pode colocar no mesmo cluster filmes com estilos e públicos completamente diferentes, como um suspense clássico dos anos 50 e um thriller de ação moderno, apenas porque ambos envolvem "investigação" e "crime".

### Modelo 2: Clusterização Multifatorial (Todas as Features)

Este modelo adota uma abordagem mais completa. Além da sinopse vetorizada, ele incorpora:
* **Gênero:** Convertido em features numéricas (*one-hot encoding*).
* **Ano de Lançamento:** Tratado como uma feature numérica (normalizada).
* **Avaliação (Rating):** Tratada como uma feature numérica (normalizada).

* **Vantagens:**
    * **Clusters ricos e específicos:** Os agrupamentos são muito mais detalhados. O modelo consegue distinguir, por exemplo, um "drama de crime aclamado pela crítica dos anos 70" de uma "animação de aventura para a família dos anos 2010".
    * **Maior relevância para o usuário:** A recomendação se torna mais precisa, pois leva em conta não apenas "o que" acontece no filme, mas também "como", "quando" e "o quão bom" ele é.
    * **Visão holística:** Trata cada filme como um produto completo, refletindo de forma mais fiel como os espectadores percebem e escolhem o que assistir.

---

## Justificativa da Escolha: Por que o Modelo 2 é Superior?

A escolha do **Modelo 2 (desenvolvido no Notebook 2) é inquestionavelmente a melhor opção** para o objetivo deste projeto.

> A inclusão de múltiplas features (sinopse, gênero, ano e avaliação) permite a criação de clusters significativamente mais inteligentes, coesos e úteis para um sistema de recomendação eficaz.

Os principais motivos são:

1.  **Precisão e Contexto:** O Modelo 2 captura nuances que o Modelo 1 ignora completamente. Gênero, ano e avaliação são fatores decisivos na escolha de um filme por um espectador. Ao incluir esses dados, os clusters passam a representar "perfis" de filmes muito mais alinhados com o gosto do público.

2.  **Segmentação de Mercado:** Os clusters do Modelo 2 representam segmentos de mercado reais. Um grupo de "ficção científica cult dos anos 80" é um nicho muito mais acionável para recomendação do que um grupo genérico de filmes "sobre o futuro".

3.  **Qualidade da Recomendação:** Em um cenário prático, recomendar filmes baseados nos clusters do Modelo 2 resultaria em uma experiência de usuário muito superior. As chances de um usuário gostar de outra sugestão do mesmo cluster são drasticamente maiores, pois os filmes compartilham não apenas um tema, mas também um estilo, uma época e um nível de aclamação semelhantes.

Em resumo, enquanto o Notebook 1 prova um conceito valioso sobre a análise textual, o **Notebook 2 entrega uma solução muito mais robusta, completa e pronta para aplicação real**, justificando plenamente sua superioridade.

----

## Links dos notebooks

1. Notebook 1: [https://colab.research.google.com/drive/1ti-KRq_HqCX1SY_ZM1V4YrnhpPCDXYOZ?usp=sharing](https://colab.research.google.com/drive/1Bt2B0h_rxvWi0WKCgquQOqzFZI_MP8Tk?usp=sharing)
2. Notebook 2: [https://colab.research.google.com/drive/1ti-KRq_HqCX1SY_ZM1V4YrnhpPCDXYOZ?usp=sharing](https://colab.research.google.com/drive/1ti-KRq_HqCX1SY_ZM1V4YrnhpPCDXYOZ?usp=sharing)
