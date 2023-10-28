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

Em todos os cenários, o "Coeficiente de aversão ao risco" foi igual a 5 (representa um alto grau de aversão ao risco).

Foram geradas carteiras CVM, PR e Naïve com 10, 20, 30 e 40 ativos.

São apresentados na tabela abaixo, as carteiras geradas e como se comportam nos anos subsequentes (2016, 2017, 2018, 2019 e 2020) em comparação com a carteira do investidor e os índices de benchmark:

<table>
  <tr>
    <th rowspan=2>Carteira</th>
    <th colspan=4>Pesos</th>
  </tr>
  <tr>
    <th>10 Ativos</th>
    <th>20 Ativos</th>
    <th>30 Ativos</th>
    <th>40 Ativos</th>
  </tr>
  <tr>
    <td>Carteira do investidor</td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/f3b3fd9f-26db-473a-97d4-eb3bfedd4c3c" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/bf8b0c3e-581b-4e26-b10f-b83184fa31ec" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/02b056d4-7d39-4ea1-bc89-745dd7701a5c" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/72897b32-6b6d-480b-a869-c69f820d4493" width="200"></td>
  </tr>
  <tr>
    <td>Carteira CVM</td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/bb276fb8-c37d-44a1-b3d0-70d647782507" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/a467697f-ebe5-4025-909a-14b2f2b9556f" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/39ef58e6-1ce5-42d7-9f06-c6388ef75cdb" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/47585854-c50d-4802-a8a3-6634504cd6d9" width="200"></td>
  </tr>
    <tr>
    <td>Carteira PR</td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/95fff8cf-ffd0-450e-9edb-5653544aace7" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/565023b2-a190-4053-929d-99044fc22dbe" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/4e8a248b-cf46-4aff-8efa-75cf19114ded" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/673b6933-5f1c-4e88-8c53-80fd01da3b51" width="200"></td>
  </tr>
    <tr>
    <td>Carteira Naïve</td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/fa7abec3-956c-4787-a84e-3ba46ff369a4" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/a462215f-9425-4a2a-9516-110cafa1bbf2" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/940f3c89-1f77-44a6-aeb1-843e825e349c" width="200"></td>
    <td><img src="https://github.com/jtcearth/TCC/assets/105126373/00b64c01-531e-4d1a-8d7c-c8a3fed07ff2" width="200"></td>
  </tr>
  <tr>
    <th colspan=5>Retornos ano-a-ano (2016 - 2020)</th>
  </tr>
  <tr>
    <td>10 Ativos</td>
    <td colspan=4 align="center"><img src="https://github.com/jtcearth/TCC/assets/105126373/d832a0ca-9402-4336-90c4-6fb685f86ecf" width=600 height=200></td>
  </tr>
  <tr>
    <td>20 Ativos</td>
    <td colspan=4 align="center"><img src="https://github.com/jtcearth/TCC/assets/105126373/3d8052b4-e2e5-4399-8fda-089548352b73" width=600 height=200></td>
  </tr>
  <tr>
    <td>30 Ativos</td>
    <td colspan=4 align="center"><img src="https://github.com/jtcearth/TCC/assets/105126373/16f5cc1c-3fd4-463f-8f8c-b366d0fdbfe5" width=600 height=200></td>
  </tr>
  <tr>
    <td>40 Ativos</td>
    <td colspan=4 align="center"><img src="https://github.com/jtcearth/TCC/assets/105126373/4c9096fd-8a20-4723-865b-373a2a85e645" width=600 height=200></td>
  </tr>
  <tr>
    <th colspan=5>Retornos consolidados (2016 - 2020)</th>
  </tr>
  <tr>
    <td>10 Ativos</td>
    <td colspan=4 align="center"><img src="https://github.com/jtcearth/TCC/assets/105126373/1f6cc592-5acd-4ff7-9d65-ad2be2ac7347" width="200"></td>
  </tr>
  <tr>
    <td>20 Ativos</td>
    <td colspan=4 align="center"><img src="https://github.com/jtcearth/TCC/assets/105126373/29f1704c-f930-4774-a2f3-52dbb7dc4fc8" width="200"></td>
  </tr>
  <tr>
    <td>30 Ativos</td>
    <td colspan=4 align="center"><img src="https://github.com/jtcearth/TCC/assets/105126373/29bd72f0-c47c-4869-9dce-61ec34278a77" width="200"></td>
  </tr>
  <tr>
    <td>40 Ativos</td>
    <td colspan=4 align="center"><img src="https://github.com/jtcearth/TCC/assets/105126373/1edd1cf1-0023-46e6-a0f3-5d3904893c7a" width="200"></td>
  </tr>
</table>


### 4. Conclusões

A quantidade de ativos definida previamente influenciou no desempenho das carteiras geradas.

No cenário com 10 ativos, o destaque foi para a carteira Naïve que superou a CVM, a PR e a do Investidor. Ela também superou todos os bechmarks. A carteira PR, a segunda melhor carteira nesse cenário, foi superada pelo IBOV e pela carteira do investidor. A CVM foi a pior em comparação a todas as carteiras e a todos os benchmarks, apresentando retorno negativo.

Com 20 ativos, a Naïve foi novamente a carteira que predominou, apresentando um retorno ligeiramente superior ao cenário anterior. A PR permaneceu como a segunda melhor carteira gerada, mas foi superada novamente pela carteira do investidor e pelo IBOV. Além disso, a carteira PR teve uma considerável piora com relação ao cenário anterior. A carteira CVM, mesmo apresentando retorno positivo, foi, de novo, a pior dentre as carteiras geradas e os benchmarks.

Quando a restrição da carteira foi fixada em 30 ativos, houve uma mudança considerável de cenário com relação à carteira CVM, que passou a oferecer tanta rentabilidade quanto a Naïve. Ambas se revezaram no posto de melhor carteira gerada nas execuções realizadas, superando as demais carteiras e os bechmarks. A carteira PR teve um desempenho melhor, mas foi superada novamente pela carteira do investidor e pelo IBOV.

No cenário com 40 ativos, a Naïve e a CVM foram as mais rentáveis e a PR foi capaz de superar a carteira do investidor e o IBOV pela primeira vez.

---

Matrícula: 212.100.341

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*


