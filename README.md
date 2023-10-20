# Otimização de carteiras de investimentos

#### Aluno: [Jefferson Terra da Conceição](https://github.com/jtcearth)
#### Orientador: [Felipe Borges](https://github.com/FelipeBorgesC)

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

- [Link para o código](https://github.com/jtcearth/TCC).

---

### Resumo

Esse trabalho baseia-se em ativos negociados no mercado financeiro brasileiro (ações, fundos de invesimento imobiliário e títulos públicos) para propor um processo de otimização que objetiva selecionar o melhor conjunto de ativos e a melhor estratégia para sua diversificação.

### Abstract

This work is based on assets traded in the Brazilian financial market (shares, real estate investment funds and public bonds) to propose an optimization process that aims to select the best set of assets
and the best strategy for its diversification.

### 1. Introdução

Montar um portfólio de investimentos é um processo que pode demandar tempo e esforço consideráveis. A grande variedade de ativos disponíveis no mercado financeiro, somando-se às características inerentes a cada um deles, pode levar um investidor desprecavido a um cenário, no mínimo, desafiador. 

Ao selecionar ativos para investir, é necessário avaliar não apenas o retorno que podem oferecer, mas também considerar todo o risco identificável a que se submetem por fatores políticos, geopolíticos, econômicos, ambientais e, até mesmo, emocionais.

De maneira geral, o risco tomado de forma calculada pode representar ótimas oportunidades aos investidores mais tolerantes a cenários arriscados. Essas circunstâncias permitem ganhos interessantes, mesmo com ativos considerados menos arriscados, como observado historicamente com a renda fixa no Brasil. 

É preciso reconhecer que, independentemente se o investidor é pessoa física ou institucional, nem sempre é possível identificar todo risco na escolha de um ativo para realizar um investimento.
Desse modo, seja qual for o objetivo almejado com o investimento, o investidor precisa adotar algumas medidas para a mitigação de riscos, por exemplo: 
*	Identificar o seu grau de tolerância ao risco; e
*	Definir uma estratégia de diversificação.
	
O conhecimento da sua tolerância ao risco possibilita que o investidor defina em que tipos de ativo deve, ou não, realizar os seus aportes. 
A diversificação, ao longo dos anos, demonstrou ser primordial para a área de investimentos, sendo um preceito já estabelecido pela maioria dos investidores. Para que alcance o seu propósito é necessário o estabelecimento de uma maneira de diversificar, ou melhor, que seja definida uma estratégia capaz de permitir uma boa rentabilidade, em períodos de mercado aquecido, e apresente resiliência, em períodos de mercado em baixa. Abaixo estão relacionadas as três estratégias que serão adotadas nesse trabalho:
1.	Ingênua (Naïve)
	*	Ativos na carteira de investimentos possuem pesos na proporção 1/n, sendo “n” a quantidade de ativos.

2.	CVM (Carteira de Variância Mínima)
	*	Baseado na teoria do portfólio de Markowitz, consiste na montagem de um portfólio que garanta uma variância mínima global.

3.	PR (Paridade de Risco)
	*	A equalização dos pesos de cada ativo no portfólio ocorre de acordo com a contribuição ao risco de cada um dos ativos. 

A partir desses princípios, a solução que será apresentada nesse trabalho se propõe a auxiliar o investidor na escolha dos ativos e da estratégia mais apropriados para atingir o resultado desejado, de acordo com o risco a que o investidor se predispõe a assumir.



### 2. Modelagem

O processo se inicia a partir do upload do arquivo Excel “Planilha_Ativos.xlsx” que contém as abas:
1.	Ações
	*	Contém amostras de ações/ETFs negociados na bolsa de valores brasileira.
2.	FII
	*	Contém amostras de fundos de investimento imobiliário negociados na bolsa de valores brasileira.
3.	Renda Fixa
	*	Contém amostras de títulos públicos do governo federal.
4.	Restrições
	*	São definidos a quantidade de ativos das carteiras de investimentos geradas e o coeficiente de aversão de risco do investidor.
5.	Carteira de um investidor
	*	Uma carteira sugerida por um investidor para confrontar as carteiras geradas pelo processo de otimização.

Um período é definido para delimitar a faixa de tempo para a obtenção dos retornos dos ativos (Ações/ETFs, FIIs e Renda Fixa) e dos índices financeiros (IBOVESPA, IPCA, SELIC e Dólar).
A partir do período informado, a solução utiliza os dados disponíveis nas planilhas para obter essas informações e as disponibiliza, de forma anualizada, em arquivos que serão salvos na pasta do Drive previamente indicada.

Foi adotado o critério de desprezar os ativos em que a média de valores não-declarados supere o percentual de 10%.

Os primeiros cinco anos de retornos dos ativos selecionados serão utilizados no processo de otimização das carteiras que seguem as estratégias de diversificação CVM, PR e Ingênua.

As restrições “Quantidade de ativos” e “Coeficiente de Aversão ao Risco”, definidas na planilha, serão utilizados na otimização das três carteiras. A primeira restrição impõe que as carteiras geradas ao término do processo possuam o número de ativos informado nesse local da planilha. A segunda restrição determina o quão averso ao risco é o investidor. Esse valor varia de 1 (mais propenso ao risco) a 5 (menos propenso ao risco). O coeficiente de aversão ao risco é um dos elementos integrantes da fórmula para calcular a “utilidade ao investidor”.

Após o término da etapa de otimização, são obtidas as três carteiras com as estratégias distintas de diversificação. Cada uma das carteiras resultantes foi a que obteve os melhores retornos e utilidade para o investidor dentro de cada estratégia proposta.

O próximo passo é averiguar como essas carteiras performam em um período subsequente ao utilizado para o processo de otimização, em comparação com a carteira elaborada por um investidor e aos índices selecionados para benchmark (IPCA, IBOV, Dólar e Taxa SELIC). 


A solução é subdivida nos arquivos abaixo:
1.	Apresentacao.ipynb: 
	*	Notebook principal.
	*	É definida a pasta onde deverão estar localizados todos os arquivos citados para a execução da solução.

2.	OtimizadorCVM.ipynb:
	*	Otimização de carteiras com a estratégia CVM.
	*	Utiliza o framework DEAP.

3.	OtimizadorNaive.ipynb:
	*	Otimização de carteiras com a estratégia Naïve.
	*	Utiliza o framework DEAP.

4.	OtimizadorPR.ipynb:
	*	Otimização de carteiras com a estratégia PR.
	*	Utiliza o framework DEAP.

5.	Estrategia_Alocacao.ipynb: 
	*	Implementações dos métodos para geração das estratégias CVM, Naïve e PR.
	*	Utiliza a biblioteca SciPy.

6.	Funcoes_Apoio.py: 
	*	Concentra funções de uso genérico.

7.	Dados_Planilha_Ativos.ipynb: 
	*	Importação dos dados do arquivo “Planilha_Ativos.xlsx”.

8.	Dados_Ativos_Renda_Variavel.ipynb: 
	*	Importação dos dados de ativos de renda variável.
	*	Utiliza o framework yfinance.

9.	Dados_benchmark.ipynb:
	*	Importação de dados de referências de benchmark (SELIC, IPCA, IBOVESPA e Dólar).
	*	Utiliza o framework yfinance.
	*	Utiliza APIs do Banco Central do Brasil e do IBGE.




10.	Dados_Titulos_Publicos.ipynb: 
	*	Importação de dados de títulos públicos.
	*	Utiliza a API Tesouro Transparente.





### 3. Resultados

O período definido para a etapa de otimização compreendeu os anos 2011, 2012, 2013, 2014 e 2015. 

Foram utilizadas como retrições:
* Quantidade de ativos igual a 30
* Coeficiente de aversão ao risco igual a 5 (representa um alto grau de aversão ao risco)

Em uma das execuções, as carteiras CVM, Naïve e PR obtidas ao término da otimização tem, respectivamente, as seguintes composições:

![30 ativos](https://github.com/jtcearth/TCC/assets/105126373/515c4634-7b90-4211-ba58-d70aba9f0bcb)



Comparando as carteiras geradas com a carteira elaborada por um especialista e os índices de benchmark, no período subsequente, de 2016 a 2020, observou-se:

![30 ativos_2](https://github.com/jtcearth/TCC/assets/105126373/24085a7e-4624-4e12-9633-921b76411b63)

E consolidado igual a:

![30 ativos_3](https://github.com/jtcearth/TCC/assets/105126373/37250a78-94f0-4b93-bf24-367f1998651b)



### 4. Conclusões

Com relação ao desempenho das carteiras geradas, verificou-se que a otimização utilizando um quantitativo de 30 ativos ocasiona uma performance melhor ora para a carteira CVM ora para a Naïve. Nas execuções relaizadas, a carteira PR sempre ocupou a terceira posição na comparação entre elas.

Quanto a comparação das carteiras geradas com a carteira do investidor e com os índices de benchmark, a CVM e a Naïve, eventualmente, performam pior do que a carteira do Investidor. Esta carteira teve uma rentabilidade melhor do que a PR em todas as execuções. Em comparação com os índices IBOV, Dólar, SELIC e IPCA, as carteiras CVM e Naïve geradas conseguiram batê-los. A carteira PR superou o IBOV em algumas oportunidades e em outras não.

A quantidade de ativos 

---

Matrícula: 212.100.341

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
