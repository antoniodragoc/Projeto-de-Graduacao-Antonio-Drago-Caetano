# Projeto-de-Graduacao-Antonio-Drago-Caetano

Neste repositório estão os códigos utilizados para o Projeto de Graduação no curso de Engenharia Elétrica do autor. 

O texto pode ser acessado no [link](adicionar).

<h2> Introdução </h2>
Com o propósito de ajudar a comunidade médica com o diagnóstico precoce de câncer de mama, imagens microscópicas de tecido da mama foram obtidas de diversas pacientes, tanto aquelas que possuíam câncer como aquelas que estavam livres da doença. A base de dados foi disponibilizada de forma gratuita, disponível no site da [ICIAR 2018](https://iciar2018-challenge.grand-challenge.org/), para o Grand Challenge on Breast Cancer Histology Images – BACH (ICIAR, 2018). 

O principal objetivo do desafio foi obter formas de classificação automática de imagens de microscopia celular para a detecção de câncer de mama. Ao todo, houve 677 registros para a participação do evento, porém, aconteceram apenas 64 envios para avaliação, o que obteve o melhor desempenho apresentou 87% de acurácia (ARESTA; ARAÚJO; KWOK; et al., 2019).

O conjunto de dados possui ao todo 400 imagens rotuladas em quatro classes divididas de forma igualitária entre 4 classes, logo, cada classe possui 100 exemplares de alta resolução com 2048 × 1536 pixels. As imagens foram rotuladas conforme o tipo de patologia podendo ser: normal, benigno (Benign), câncer não invasivo (In situ carcinoma) e câncer invasivo (Invasive carcinoma) (KONÉ; BOULMANE, 2018).

<h2> Metodologia </h2>
Para a Classificação das imagens foram utilizados métodos supervisionados: 
  - Redes Neurais Convolucionais: VGG-19 e ResNet-50
  - Modelos Clássicos: SVM e XGBoost
  
Importante ressaltar que a ResNet-50 como extrator de características para as entradas dos modelos clássicos.
  
As imagens diponibilizadas neste repositório já foram pré-processadas. Caso deseje-se utilizar imagens maiores será necessário o download do dataset no link do desafio.

Os dados foram salvos em pastas separadas pelos rótulos de treino, validação e teste, o primeiro conjunto tem 300 imagens (75%), o segundo possui 60 imagens (15%) e o terceiro tem 40 imagens (10%). A divisão foi feita por meio de pastas que foram divididas conforme a etapa em questão train, val e test e o rótulo dos dados podendo ser: benign, in situ, invasive e normal. 

As imagens originais eram de alta resolução com aproximadamente 13 MB de tamanho e resolução de 2048 × 1536 pixels. Por conta da elevada dimensionalidade e tamanho de cada exemplar, foi necessário modificar as dimensões das imagens, conforme feito no artigo que obteve a oitava colocação no desafio BACH de 2018 (KONÉ; BOULMANE, 2018). No primeiro momento foi feita a redução no tamanho para 399 × 299 pixels, com o objetivo de se manter o aspecto e evitar o achatamento da figura, evitando assim a distorção das características. Em seguida, foram cortadas em 50 pixels de cada uma das extremidades chegando ao resultado final de 299 × 299 pixels. O resultado final foi uma grande redução no tamanho total do conjunto de dados que no primeiro momento possuía mais de 13 GB e no segundo momento, o mesmo conjunto com 400 imagens passou a ocupar apenas 80 MB de espaço. 


<h2> Resultados </h2>
<h3> VGG-19 </h3>

<p align="center">
  <img src="https://user-images.githubusercontent.com/65796341/186297840-351bebab-76a4-4f2f-82f8-f0593d44f537.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/65796341/186297875-dc039022-da5f-4174-a38c-d4d823a0297d.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/65796341/186297895-5e557a99-68ae-4cb9-a4c9-6c8f6a490a54.png" />
</p>



<h3> ResNet-50 </h3>

<p align="center">
  <img src="https://user-images.githubusercontent.com/65796341/186298588-f77a8f4c-7f35-43ff-b29b-c4ef9b5bb6ad.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/65796341/186298616-0f19ac87-26c7-4f36-a643-66175bac083f.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/65796341/186298656-b28fe7da-dfea-475c-92b5-3efc8f704d53.png" />
</p>


<h3> ResNet-50 + SVM </h3>

<p align="center">
  <img src="https://user-images.githubusercontent.com/65796341/186298849-5a37129f-edd6-4d2d-bb24-dd7a52c9d7fe.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/65796341/186298874-63b167dc-0e1c-452a-8b33-8561693f7bf0.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/65796341/186298909-0a151629-094a-4799-8a46-b089228cf01a.png" />
</p>

<h3> ResNet-50 + XGBoost </h3>

<p align="center">
  <img src="https://user-images.githubusercontent.com/65796341/186298754-f6c0e9e6-73d5-4ae9-868b-8f2d0b0014af.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/65796341/186298784-f048038b-5627-4f05-9868-f5b79c8cb1ef.png" />
</p>

<p align="center">
  <img src="https://user-images.githubusercontent.com/65796341/186298802-ad6c36d0-51c0-4d81-9465-aca25a9ec40a.png" />
</p>


<h2> Conclusões </h2>
O presente trabalho teve como objetivo apresentar um estudo com ferramentas de aprendizado de máquina mesclando diferentes metodologias e ferramentas, além da reutilização de técnicas como forma de entrada de dados para outros modelos. Tal objetivo foi bem sucedido por meio da utilização da aplicação de diferentes técnicas de classificação combinadas ao uso de data augmentation para o treinamento dos modelos. 

As redes convolucionais obtiveram bons desempenhos, 80% e 85% para as redes VGG-19 e ResNet-50, respectivamente. Além disso, a utilização das redes neurais como extratores de características para o treinamento de classificadores clássicos se mostrou bem eficaz, resultando nas acurácias de 87,5% e 72,5% para os modelos SVM e XGBoost.
 
A rede ResNet-50 foi escolhida para a etapa de extração de características por conta da sua maior capacidade de generalização com o conjunto de dados reduzido. Para isso, algumas camadas foram ajustadas para o desafio proposto além de seus hiperparâmetros otimizados para o problema em questão. A etapa que tomou mais tempo de execução e de pesquisa foi de fine tunning dos modelos de redes convolucionais, já que o grande número de camadas das redes aumenta o tempo de treinamento.

Por fim, é também relevante se observar a matriz de confusão dos dados de teste para analisar o desempenho do modelo em cada classe e com isso observar a capacidade de generalização do modelo.

