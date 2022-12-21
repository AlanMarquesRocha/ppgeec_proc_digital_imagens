### Programa de Pós-graduação em Engenharia Elétrica e de Computação

### Disciplina: Processamento Digital de Imagens

### Discente: Alan Marques da Rocha

### Trabalho 02: Morfologia Matemática

---

O trabalho consiste no desenvolvimento dos operadores morfológicos para realizar a etapas de ```erosão, dilatação, abertura e fechamento``` em dois conjuntos de dados ```imgs_pb``` que caracteriza as imagens binarizadas e ```imgs_cinza``` que caracteriza as imagens em níveis de cinza do dataset.

Nesse projeto foram utilizadas as bibliotecas ```numpy``` e ```opencv``` conforme ilustrado a seguir:

![image](https://user-images.githubusercontent.com/13985581/195952831-a4073f72-d806-4816-86ca-7cf4e9daafa5.png)

Para que o projeto não ficasse muito extenso (em termos de código), optou-se por realizar os processos solicitados em dois códigos distindos (duas partes), ou seja, os procedimentos de **erosão, dilatação, abertura e fechamento** foram aplicados no conjunto de dados ```imgs_cinza``` cujo o código está disponível [**nesse link.**](https://github.com/AlanMarquesRocha/t02_morfologia_matematica/blob/master/part_1_t02_morfologia_matematica_grey_scale.ipynb) e a aplicação dos métodos propostos no conjunto de dados ```imgs_pb``` está disponível [**aqui.**](https://github.com/AlanMarquesRocha/t02_morfologia_matematica/blob/master/part_2_t02_morfologia_matematica_pb.ipynb)

### Breve introdução:

Um conceito importante na morfologia matemática é a definição de elemento estruturante. O elemento estruturante é um conjunto definido e conhecido (forma e tamanho), que é usado em uma operação com o conjunto da imagem para salientar determinado aspecto. Ele pode assumir várias formas dependendo do efeito a ser obtido e sua origem pode ser definida em qualquer ponto.

Neste trabalho, foram utilizados três elementos estruturantes, também chamados de kernels, a saber: quadrado, linha e cículo (Substituído por um elemento em forma de elipse).

![image](https://user-images.githubusercontent.com/13985581/195958276-aaa9d7af-3c5a-4247-b712-38ad05dda585.png)

---

As imagens do conjunto de dados foram abertas e rotuladas como segue:

![image](https://user-images.githubusercontent.com/13985581/195957908-5f2660a4-1fee-4343-9adc-5db7a47cf1f2.png)

Os operadores morfológicos foram definidos e implementados com três dimensões distintas, conforme mostrado a seguir:

### Operador morfológico quadrático:

![image](https://user-images.githubusercontent.com/13985581/195958104-6340e2fa-2fdd-4048-a604-66605329af45.png)

### Operador morfológico linear:

![image](https://user-images.githubusercontent.com/13985581/195958335-856c54a8-e7f5-4094-8e6c-b20c23c6768b.png)

### Operador morfológico circular:

![image](https://user-images.githubusercontent.com/13985581/195958358-227b6cd5-9d00-4602-834b-3b37e13fd044.png)

Para melhorar os processos solicitados no projeto, foram realizadas cinco interações para cada tipo de operador morfológico.

### Exemplos de resultados obtidos após a implementação dos algotirmos.

### Dilatação - Operador circular (3x3) com 05 interações da ```img_1``` do conjunto de imagens ```imgs_pb```:

![image](https://user-images.githubusercontent.com/13985581/195958603-54684c5d-72c5-4db1-abe8-43a1ec5349ed.png)

### Abertura - Operador Circular (3x3) nas imagens: ```img_1```,```img_2``` e ```img_3```

![image](https://user-images.githubusercontent.com/13985581/195958729-ee2b206a-5a2e-4c81-a0c0-437990db53fa.png)


### Dilatação - Operador circular (3 x 3) com 05 interações da ```img_1``` do conjunto de imagens ```imgs_cinza```

![image](https://user-images.githubusercontent.com/13985581/195958999-29d4ee24-ae8d-4b79-b8f1-65e6b4cfc067.png)

---
