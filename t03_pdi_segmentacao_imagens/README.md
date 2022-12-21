<h3 align="center">Programa de Pós-graduação em Engenharia Elétrica e de Computação (PPGEEC) <br>
Disciplina: Processamento Digital de Imagens (BBP1026) </h3>

<h3 align="center">Trabalho 03: Segmentação de Imagens <br>
Discente: Alan Marques da Rocha - Matrícula: 543897 </h3>

---

## 1. Informações do trabalho proposto

Foi disponibilizada a base de imagens ``imagens-cor-segmentacao`` para que fossem implementados os seguintes algoritmos:

- ``Crescimento de Regiões``
- ``Watershed``
- ``K-means``
- ``Otsu``

Além disso, técnicas de pré-processamento foram utilizadas para realizar ajustes antes do processo de segmentação.

## 2. Base de images

As imagens disponibilizadas para a realização do trabalho proposto são apresentadas a seguir.

![image](https://user-images.githubusercontent.com/13985581/197046007-2bb58f60-5d01-4c43-bcd9-1ff82875c288.png)

---

## 3. Conceitos Introdutórios

A construção de objetos refere-se à segmentação de uma imagem em vários segmentos separados entre si, cujas características internas são relativamente homogêneas e diferem umas das outras. 

Em visão computacional (VC) o termo ``segmentação de imagens`` ou simplesmente ``segmentação``, refere-se a dividir a imagem em grupos de pixels com base em alguns critérios. Um algoritmo de segmentação recebe uma imagem como entrada e gera uma coleção de regiões (ou segmentos) que podem ser representadas como:

- Uma coleção de contornos;
- Uma máscara (em tons de cinza ou em cores ) em que cada segmento recebe um valor ou cor de tons de cinza exclusivo para identificá-lo.


<p align="center">
  <img  src="https://github.com/AlanMarquesRocha/t03_pdi_segmentacao_imagens/blob/main/imgs_readme/img_01_readme.png">
</p>

### 3.1 Métodos propostos

- Crescimento de Regiões:

Os métodos de segmentação baseados em região visam reunir num mesmo conjunto pixels adjacentes que atendem a um dado critério de heterogeneidade. Desta forma, regiões da imagem são agrupadas ou divididas dependendo de seus pixels terem ou não características semelhantes em termos de ``cor``, ``textura`` ou ``forma``. 

- Watershed:

``Watershed`` é um método de segmentação de imagens baseado em região que tem suas origens na morfologia matemática. O conceito geral foi introduzido por (Digabel e Lantuejoul, 1978). Na segmentação por watershed, uima imagem é considerada como uma paisagem topográfica com cristas e vales. Os valores de elevação da paisagem são tipicamente definidos pelos valores de cinza dos respectivos pixels ou pela magnitude do gradiente (Bernhard et. al.; 2014).

![image](https://user-images.githubusercontent.com/13985581/199824834-25324641-86b7-4422-94a1-3fc9e8da85bd.png)


- K-means:

``K-means`` é um tipo de segmentação de imagens tem tem como base o agrupamento, ou seja,  é um algoritmo de agrupamento de dados não-hierárquico que utiliza uma técnica iterativa para particionar um conjunto de dados.

Esse algoritmo busca minimizar a distância dos elementos de um conjunto de dados com k centros de forma iterativa. Considere um conjunto de dados $X = \{p_1, p_2, ..., p_n}\$, e uma distância $d:(.,.)$ nesse conjunto. O algoritmo k-means inicia-se com a escolha de $k$ centroides (centros) $c_1, c_2, ... , c_k$ para o agrupamento depois, associa cada ponto do conjunto $X$ ao seu centro mais próximo segundo a distância $d$ formando assim k grupos $X_i$. O próximo passo do algoritmo é atualizar os centroides. 


Um exemplo do resultado de implementação do algoritmo ``K-means`` é mostrado a seguir:

![image](https://user-images.githubusercontent.com/13985581/199827886-90168a58-2afb-460b-abe6-94fc208aa071.png)


- Otsu:

O método de Otsu (1979) propõe uma técnica não paramétrica, ou seja, não estima parâmetros do modelo e não supervisionada para a seleção automática do limiar visando a segmentação  da imagem.


![image](https://user-images.githubusercontent.com/13985581/199749016-7c550b3f-4fed-4d08-beb9-bc8dc6c81856.png)

onde

![image](https://user-images.githubusercontent.com/13985581/199749119-93b937d0-8e25-4425-a4e9-1512986a1fd5.png)

---

## 4. Pré-Processamento de Imagens

Técnias de pré-processamento foram utilizadas visando a retirada de ruídos e aumento da nitidez das imagens, além disso foi necessário realizar o threshold, ou seja, binarização do conjunto de imagens para a aplicação das técnias do método de ``otsu`` e ``watershed``.

Para a retirada dos ruídos das imagens, foi implementado a ``operação morfológica`` da ``erosão`` com um kernel de (3 x 3), utilizando a biblioteca ``OpenCV``. A documentação da função pode ser acessada no link: https://docs.opencv.org/4.x/db/df6/tutorial_erosion_dilatation.html

O resultado das imagens pré-processadas podem ser observadas na figura abaixo:

![image](https://user-images.githubusercontent.com/13985581/199813125-a1e52327-f5eb-4442-b3ad-5a9d68c5023e.png)

---

## 5. Processo de Segmentação

O processo de segmentação do conjunto de imagens deu-se inicialmente através da conversão das imagens de ``BGR`` para ``RGB`` utilizando a função ``cv2.cvtCOLOR`` e o parâmetro ``cv2.COLOR_BGR2RGB`` da biblioteca ``OpenCV``, tendo em vista que as imagens são geradas inicialmente com os canais B e R invertidos.

Após isso, foi necessário realizar a conversão das imagens para níveis de cinza, utilizando agora o parâmetro ``cv2.COLOR_RGB2_GRAY``

### 5.1 Método de Otsu

Para o método de Otsu, definiu-se inicialmente a função ``lim_otsu`` que recebia a imagem como parâmetro para a realização da binarização utilizando o limiar ideal calculado pela própria função.

Para isso, utilizou-se a função ``cv2.threshold`` e os parâmetros ``cv2.THRESH_BINARY`` e ``cv2.THRESH_OTSU`` para obtermos os resultados esperados.

```python

# Função que retorna o valor do limiar de otsu e realiza a conversão da imagem aplicando o threshold binary + otsu:
def lim_otsu(imagem):
    valor, otsu = cv2.threshold(imagem, 0, 255, cv2.THRESH_BINARY | cv2.THRESH_OTSU)
    print(valor)
    return otsu 
```

Os valores dos limiares para as Figuras da base de dados são mostrados a seguir.

![image](https://user-images.githubusercontent.com/13985581/199831658-8d94fc69-e2e0-40d2-bb91-26a92836b860.png)

### 5.2 Método Watershed

Para implementar o método de ``watershed`` foi necessário inicialmente realizar o processo de binarização inversa utilizando o método de ``Otsu``. Do passo implementado no método anterior, alterou-se apenas o parâmetro ``cv2.THRESH_BINARY`` para ``cv2.THRESH_BINARY_INV``. A função ``lim_inv`` é mostrada a seguir:

```python
# Função que retorna o valor do limiar de otsu_inv e realiza a conversão da imagem aplicando o threshold binary + otsu_inv:
def lim_inv(imagem):
    valor, otsu_inv = cv2.threshold(imagem, 0, 255, cv2.THRESH_BINARY_INV | cv2.THRESH_OTSU)
    print(valor)
    return otsu_inv
    
 ```
 
 A implemtanação do método ``watershed`` foi feita através da função ``img_watershed``, recebendo dois parâmetros, a saber: ``imagem`` e ``img_original``. O primeiro parâmetro recebe o resultado obtido através da função ``img_watershed``, já o segundo recebe a imagem original, para que em seguida seja feito a mesclagem de ambas as imagens, obtendo o resultado esperado. A função ``img_watershed`` é mostrada a seguir:
 
 ```python
 
 def img_watershed(imagem, img_original):
    
    otsu_inv = cv2.threshold(imagem, 0, 255, cv2.THRESH_BINARY_INV | cv2.THRESH_OTSU)[1]
    
    # realizando operações morfologicas:
    seg = cv2.erode(otsu_inv, np.ones((3,3), np.uint8), iterations = 3)
    
    # imagem de mapa da distância Euclidiana
    dist = ndi.distance_transform_edt(seg)
    
    local_max = peak_local_max(dist, indices = False, min_distance = 20, labels = seg)
    
    markers = ndi.label(local_max, structure=np.ones((3,3)))[0]
    
    
    labels = watershed(-dist, markers, mask = seg)
    
    cmap = plt.cm.jet

    # processo de normalização da escala de cores
    norm = plt.Normalize(vmin=labels.min(), vmax = labels.max())

    seg_watershed = cmap(norm(labels))

    seg_watershed = ((seg_watershed * 255).astype(np.uint8))

    # Transformando a imagem de RGB p/ BGR voltando ao original
    seg_watershed = cv2.cvtColor(seg_watershed, cv2.COLOR_RGB2BGR)
    
    
    # sobreposição da imagem segmentada sob a imagem original
    img_sobreposicao = cv2.addWeighted(seg_watershed, 0.5, img_original, 0.5, 0)

    return img_sobreposicao
```

### 5.3 Método K-means

O método ``K-means`` foi implementado utilizando os parâmetros ``cv2.TERM_CRITERIA_EPS``,  ``cv2.TERM_CRITERIA_MAX_ITER``e ``cv2.KMEANS_RANDOM_CENTERS``. Tomando a imagem como uma forma tridimensional [ $x$, $y$, $z$ ], foi necessário inicialmente reformulá-la para uma matriz bidimensional, através da biblioteca ``numpy``

A função ``kmedia`` recebe uma imagem de entrada, retornando a imagem segmentada após o final do processo. 

```python
def kmedia(imagem):
    # Reformulando a imagem para um array bidimensional
    new_pixels = imagem.reshape((-1,3))
 
    # Convert to float type
    new_pixels = np.float32(new_pixels)
    
    # a linha de código abaixo define os critérios para o algoritmo parar de funcionar,
    # o que acontecerá é que 100 iterações sejam executadas ou o epsilon (que é a precisão necessária)
    # torna-se 85%
    criterio = (cv2.TERM_CRITERIA_EPS + cv2.TERM_CRITERIA_MAX_ITER, 100, 0.70)
 
    # então realiza o agrupamento k-means com h número de agrupamentos definido como k = n
    # centros aleatórios são inicialmente escolhidos para o agrupamento
    k = 8
    retval, labels, centers = cv2.kmeans(new_pixels, k, None, criterio, 10, cv2.KMEANS_RANDOM_CENTERS)
 
    # converte dos dados para 8-bits
    centers = np.uint8(centers)
    seg_data = centers[labels.flatten()]
 
    # reformula os dados dentro das dimensões originais na imagem
    seg_image = seg_data.reshape((imagem.shape))
    
    return seg_image

```

---

## 6. Resultados Obtidos

### 6.1 Resultados Obtidos para a Figura 1:

![image](https://user-images.githubusercontent.com/13985581/199829555-ff4af786-592e-4193-bc75-9e841ba625ae.png)

### 6.2 Resultados Obtidos para a Figura 2

![image](https://user-images.githubusercontent.com/13985581/199829596-c9638709-0ea7-4a4c-a9b6-2feb3deccff2.png)

### 6.3 Resultados Obtidos para a Figura 3

![image](https://user-images.githubusercontent.com/13985581/199829641-40883f5a-7d0a-476a-b797-b0ea8d73737b.png)

### 6.4 Resultados Obtidos para a Figura 4

![image](https://user-images.githubusercontent.com/13985581/199829687-1d5ac179-c0c2-4446-b846-8f6a673484e9.png)

### 6.5 Resultados Obtidos para a Figura 5

![image](https://user-images.githubusercontent.com/13985581/199829730-7e11001e-5b58-4ae3-892c-f8c9c09cd40a.png)

### 6.6 Resultados Obtidos para a Figura 6

![image](https://user-images.githubusercontent.com/13985581/199829768-d9ba58be-a62e-4ec7-b2da-bdae3ea38797.png)

---

## 7. Referências

[Otsu, 1979] OTSU, N. A threshold selection method from grey-level histograms. IEEE Transactions on Systems, Man and Cybernetics. 1979, vol. 9, no. 1, pp. 41–47.

[Niblack, 1986] NIBLACK, W. An Introduction to Image Processing. Prentice Hall. 1986, pp 115–116.

[Bernhard Preim, Charl Botha], Chapter 4 - Image Analysis for Medical Visualization, Editor(s): Bernhard Preim, Charl Botha,
Visual Computing for Medicine (Second Edition), Morgan Kaufmann, 2014, Pages 111-175, ISBN 9780124158733, https://doi.org/10.1016/B978-0-12-415873-3.00004-3.


