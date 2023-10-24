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

Em todos os cenários, o "Coeficiente de aversão ao risco" foi igual a 5 (representa um alto grau de aversão ao risco)


| Carteira     | 10 Ativos      |20 Ativos      | 30 Ativos  |
| :---         |     :---:      |     :---:     |     :---:  |
| Carteira do investidor  | <img src="https://github.com/jtcearth/TCC/assets/105126373/f3b3fd9f-26db-473a-97d4-eb3bfedd4c3c" width="200"> | <img src="https://github.com/jtcearth/TCC/assets/105126373/bf8b0c3e-581b-4e26-b10f-b83184fa31ec" width="200">  | <img src="https://github.com/jtcearth/TCC/assets/105126373/02b056d4-7d39-4ea1-bc89-745dd7701a5c" width="200">  |
| Carteira CVM | <img src="https://github.com/jtcearth/TCC/assets/105126373/7ee8b23b-11a0-4335-a324-9549806b0555" width="200">       | <img src="https://github.com/jtcearth/TCC/assets/105126373/9519cc5c-9b9b-4fac-b99d-39193a8dd44b" width="200">  | <img src="https://github.com/jtcearth/TCC/assets/105126373/4b717808-ec87-4405-936f-14a075a9ede2" width="200">  | 
| Carteira PR    | <img src="https://github.com/jtcearth/TCC/assets/105126373/63e9f48c-8f5d-486a-b302-cee371e9402b" width="200">       | <img src="https://github.com/jtcearth/TCC/assets/105126373/356a2852-54e6-4d5d-a463-f28d4cb56fda" width="200">  | <img src="https://github.com/jtcearth/TCC/assets/105126373/b363d96a-b817-4bbf-aab8-c94b64c52a54" width="200">  |
|  Carteira Naïve     | <img src="https://github.com/jtcearth/TCC/assets/105126373/02e3b92e-cf0c-4aa4-bba8-675e1c8663b9" width="200">      | <img src="https://github.com/jtcearth/TCC/assets/105126373/4720f802-0ae4-467c-858b-97b4b506cb15" width="200">  | <img src="https://github.com/jtcearth/TCC/assets/105126373/9963b2a5-19f0-4e4d-bb2d-42e1d6377e68" width="200">  |
| teste  |
| Carteira     | 10 Ativos      |20 Ativos      | 30 Ativos  |
| :---         |     :---:      |     :---:     |     :---:  |




|  Retornos ano-a-ano    |

|  Retornos ano-a-ano    | <img src="https://github.com/jtcearth/TCC/assets/105126373/31735038-ff89-4fac-8bfc-4de60bbb6028">      | <img src="https://github.com/jtcearth/TCC/assets/105126373/791ce468-c399-4f1b-b906-73972385c7de">  | <img src="https://github.com/jtcearth/TCC/assets/105126373/4ebc3e5a-4edd-4865-a304-c4ac91f46770">  |
|  Retornos consolidados   | <img src="https://github.com/jtcearth/TCC/assets/105126373/d0f6c522-30c5-47df-866c-f470d4f3e3f9" width="200">      | <img src="https://github.com/jtcearth/TCC/assets/105126373/d59e2552-6f6f-4afd-a3f4-e1e277f1a188" width="200">  | <img src="https://github.com/jtcearth/TCC/assets/105126373/12e091e7-fb49-4648-8817-336cc54631d2" width="200">  |

![image](https://github.com/jtcearth/TCC/assets/105126373/ef33b3c5-cdb6-42e6-ae8b-9de984174b7c)

![image](https://github.com/jtcearth/TCC/assets/105126373/cf94a274-0b56-47c4-b99b-4b4185af0bef)

![image](https://github.com/jtcearth/TCC/assets/105126373/31735038-ff89-4fac-8bfc-4de60bbb6028)



#### 3.4 - Cenário com todos os ativos da planilha.

##### 3.4.1 - Retornos ano-a-ano:

![image](https://github.com/jtcearth/TCC/assets/105126373/d85aec0a-308d-4dd1-88d5-ca8c6287e3e6)

##### 3.4.2 - Retornos consolidados:

![image](https://github.com/jtcearth/TCC/assets/105126373/ff466ac7-6948-4810-9470-333c9a5dc57c)


### 4. Conclusões

A quantidade de ativos definida previamente influenciou no desempenho das carteiras geradas.

No cenário com 10 ativos, o destaque foi para a carteira Naïve que superou a CVM, a PR e a do Investidor. Ela também superou todos os bechmarks. A carteira PR, a segunda melhor carteira nesse cenário, foi superada pelo IBOV e pela carteira do investidor. A CVM foi a pior em comparação a todas as carteiras e a todos os benchmarks, apresentando retorno negativo.

Com 20 ativos, a Naïve foi novamente a carteira que predominou, apresentando um retorno ligeiramente superior ao cenário anterior. A PR permaneceu como a segunda melhor carteira gerada, mas foi superada novamente pela carteira do investidor e pelo IBOV. Além disso, a carteira PR teve uma considerável piora com relação ao cenário anterior. A carteira CVM, mesmo apresentando retorno positivo, foi, de novo, a pior dentre as carteiras geradas e os benchmarks.

Quando a restrição da carteira foi fixada em 30 ativos, houve uma mudança considerável de cenário com relação à carteira CVM, que passou a oferecer tanta rentabilidade quanto a Naïve. Ambas se revezaram no posto de melhor carteira gerada, superando as demais carteiras e os bechmarks. A carteira PR teve um desempenho melhor, mas foi superada novamente pela carteira do investidor e pelo IBOV.

No cenário em que todos os ativos da planilha foram utilizados para a montagem das carteiras, a Naïve e a CVM foram as mais rentáveis e a PR foi capaz de superar a carteira do investidor e o IBOV.

---

Matrícula: 212.100.341

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*


<table>
  <tr>
    <th rowspan=2>Carteira</th>
    <th colspan=3>Pesos</th>
  </tr>
  <tr>
    <th>10 Ativos</th>
    <th>20 Ativos</th>
    <th>30 Ativos</th>
  </tr>
  <tr>
    <td>Carteira do investidor</td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/f3b3fd9f-26db-473a-97d4-eb3bfedd4c3c" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/bf8b0c3e-581b-4e26-b10f-b83184fa31ec" width="200"></td>
	<td><img src="https://github.com/jtcearth/TCC/assets/105126373/02b056d4-7d39-4ea1-bc89-745dd7701a5c" width="200"></td>
  </tr>
  <tr>
    <td>Carteira CVM</td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/7ee8b23b-11a0-4335-a324-9549806b0555" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/9519cc5c-9b9b-4fac-b99d-39193a8dd44b" width="200"></td>
	<td><img src="https://github.com/jtcearth/TCC/assets/105126373/4b717808-ec87-4405-936f-14a075a9ede2" width="200"></td>
  </tr>
    <tr>
    <td>Carteira PR</td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/63e9f48c-8f5d-486a-b302-cee371e9402b" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/356a2852-54e6-4d5d-a463-f28d4cb56fda" width="200"></td>
	<td><img src="https://github.com/jtcearth/TCC/assets/105126373/b363d96a-b817-4bbf-aab8-c94b64c52a54" width="200"></td>
  </tr>
    <tr>
    <td>Carteira Naïve</td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/02e3b92e-cf0c-4aa4-bba8-675e1c8663b9" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/4720f802-0ae4-467c-858b-97b4b506cb15" width="200"></td>
	<td><img src="https://github.com/jtcearth/TCC/assets/105126373/9963b2a5-19f0-4e4d-bb2d-42e1d6377e68" width="200"> </td>
  </tr>
  <tr>
    <th colspan=4>Retornos ano-a-ano</th>
  </tr>
  <tr>
	<td>10 Ativos</td>
    <td colspan=3><img src="https://github.com/jtcearth/TCC/assets/105126373/ef33b3c5-cdb6-42e6-ae8b-9de984174b7c" width=300 height=100></td>
  </tr>
  <tr>
  	<td>20 Ativos</td>
    <td colspan=3><img src="https://github.com/jtcearth/TCC/assets/105126373/791ce468-c399-4f1b-b906-73972385c7de" width=300 height=100></td>
  </tr>
  <tr>
  	<td>30 Ativos</td>
    <td colspan=3><img src="https://github.com/jtcearth/TCC/assets/105126373/4ebc3e5a-4edd-4865-a304-c4ac91f46770" width=300 height=100></td>
  </tr>
  <tr>
    <th colspan=4>Retornos consolidados</th>
  </tr>
  <tr>
    <td>10 Ativos</td>
    <td colspan=3><img src="https://github.com/jtcearth/TCC/assets/105126373/d0f6c522-30c5-47df-866c-f470d4f3e3f9" width="200"></td>
  </tr>
  <tr>
    <td>20 Ativos</td>
    <td colspan=3><img src="https://github.com/jtcearth/TCC/assets/105126373/d59e2552-6f6f-4afd-a3f4-e1e277f1a188" width="200"></td>
  </tr>
  <tr>
    <td>30 Ativos</td>
    <td colspan=3><img src="https://github.com/jtcearth/TCC/assets/105126373/12e091e7-fb49-4648-8817-336cc54631d2" width="200"></td>
  </tr>
</table>
