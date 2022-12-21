### Programa de Pós-graduação em Engenharia Elétrica e de Computação

### Disciplina: Processamento Digital de Imagens

### Discente: Alan Marques da Rocha

### Trabalho 01: Realce no domínio espacial

---

O trabalho consiste no desenvolvimento de filtros passa-baixa, tem como objetivo realizar a suavização das imagens disponpiveis no dataset

Inicialmente projetou-se os filtros de média 3x3, 5x5 e 7x7 para aplicá-los ao conjunto de imagens.

Nesse projeto foram utilizadas as bibliotecas ```numpy``` e ```opencv``` conforme ilustrado a seguir:

![image](https://user-images.githubusercontent.com/13985581/195952831-a4073f72-d806-4816-86ca-7cf4e9daafa5.png)

As imagens do dataset foram renomeadas em ```img_1```, ```img_2```, ```img_3```, ```img_4``` e ```img_5``` e foram utilizas utilizando o método ```imread``` da biblioteca ```opencv```.

![image](https://user-images.githubusercontent.com/13985581/195952974-c814ff19-20f0-4489-a93d-851fd35f405c.png)

### Imagens utilizadas no projeto:

![image](https://user-images.githubusercontent.com/13985581/195953148-b744ea70-e6e9-4d30-acc1-58707f2bdbc3.png)

A implementação de filtro no OpenCV usa uma estrutura bem simples. Ele consiste em convolver uma matriz (kernel) pela imagem, as operações são executadas entre os valores do kernel e os pixels embaixo.
Normalmente os kernels são normalizados, isto é, cada valor é dividido pelo tamanho do kernel. Nesse caso 3×3=9, essa divisão é implementada para não distorcer as cores da imagem, assim a operação depende apenas de sua vizinhança.

O primeiro passo se deu na implementação dos filtros de 3x3, 5x5 e 7x7. Para realizar tal procedimento, utilizou-se a função ```cv2.blur``` que recebe a imagem e a dimensão da máscara que será aplicada a cada imagem, deve=se ter em mente que o blur é o filtro de média.

### Filtros implementados:

```python

# Montando os filtros para cada imagem do projeto através do método cv2.blur da biblioteca opencv:

blur_img_1 = cv2.blur(img_1, (3, 3))

blur_img_1 = cv2.blur(img_5, (5, 5))

blur_img_1 = cv2.blur(img_5, (7, 7))

```

Os filtros foram implementados e aplicados para cada imagem disponível no dataset.

### Resultado obtidido para a ```img_1``` nos três filtros citados anteriormente:

![image](https://user-images.githubusercontent.com/13985581/195953576-a797736f-4e6f-4ff9-a698-db4b9266da13.png)

### Resultado obtidido para a ```img_2``` nos três filtros citados anteriormente:

![image](https://user-images.githubusercontent.com/13985581/195953782-45a1dbb7-c946-463d-b6c4-b69a73858dad.png)

### Resultado obtidido para a ```img_3``` nos três filtros citados anteriormente:

![image](https://user-images.githubusercontent.com/13985581/195953879-2327c1e9-5dd0-4958-bb03-1c14b54414c5.png)

### Resultado obtidido para a ```img_4``` nos três filtros citados anteriormente:

![image](https://user-images.githubusercontent.com/13985581/195954047-d49ff925-51f8-48c6-948e-f5be15ab46f7.png)

### Resultado obtidido para a ```img_5``` nos três filtros citados anteriormente:

![image](https://user-images.githubusercontent.com/13985581/195954143-77313083-6e28-44c0-a72c-51b6a8cb9f42.png)

Observa-se que o filtro realiza o realce das imagens, principalmente nas dimensões (5x5), desfocando-as a partir de (7x7). Embora o filtro média seja eficaz, ainda é possível observar pontos indesejados nas imagens.

---

Como segundo passo, desenvolveu-se um filtro média, seguindo as seguintes características:

![image](https://user-images.githubusercontent.com/13985581/195954494-c030015b-a8db-4165-8083-94114095cb07.png)

Desenvolvimento do filtro através da biblioteca ```opencv```

![image](https://user-images.githubusercontent.com/13985581/195954635-c0b95e36-c597-4275-ad13-9093cbd65b0d.png)

Após a implementação o filtro foi aplicado às imagens do dataset. O resultado é mostrado a seguir:

### Resultado obtidido para a ```img_1``` do Filtro Média (3x3) 1/16:

![image](https://user-images.githubusercontent.com/13985581/195954929-96dd221b-5885-4346-92ac-53b6e53601de.png)

### Resultado obtidido para a ```img_2``` o Filtro Média (3x3) 1/16:

![image](https://user-images.githubusercontent.com/13985581/195954951-27157730-bcaa-4fa8-b6fa-3dfd612e7815.png)

### Resultado obtidido para a ```img_3``` o Filtro Média (3x3) 1/16:

![image](https://user-images.githubusercontent.com/13985581/195954974-cc8b5f3a-dc73-48fa-8957-daad63e58e96.png)

### Resultado obtidido para a ```img_4``` o Filtro Média (3x3) 1/16:

![image](https://user-images.githubusercontent.com/13985581/195954989-5f00a552-42f6-4b4f-98a1-5485c4ecfb81.png)

### Resultado obtidido para a ```img_5``` o Filtro Média (3x3) 1/16:

![image](https://user-images.githubusercontent.com/13985581/195955016-8bd3ce9b-5e0f-4029-a3de-4eaf002165f4.png)

Nota-se uma grande melhora na retirada dos pontos pretos e branco das imagens, melhorando sua resolução, se comparado com os filtros aplicados anteriormente.

---

Na última parte do projeto, realizou-se o desenvolvendo dos Filtros da Mediana para 3x3, 5x5 e 7x7:

A implementação se deu da seguinte maneira (Exemplificando para a ```img_1```:

```python

# Filtro da Mediana 3x3 para a img_1:
median_img_1 = cv2.medianBlur(img_1, 3)

# Filtro da Mediana 5x5 para a img_1:
median_img_1 = cv2.medianBlur(img_1, 5)

# Filtro da Mediana 7x7 para a img_1:
median_img_1 = cv2.medianBlur(img_1, 7))

```

Os resultados obtidos são mostrados a seguir:

### Resultado obtidido para a ```img_1``` nos três filtros citados anteriormente:

![image](https://user-images.githubusercontent.com/13985581/195955833-baa18513-a89b-40b9-bef8-d8c81cd90264.png)

### Resultado obtidido para a ```img_2``` nos três filtros citados anteriormente:

![image](https://user-images.githubusercontent.com/13985581/195955935-584b5590-9cf1-411e-b432-61f6a5b80aea.png)

### Resultado obtidido para a ```img_3``` nos três filtros citados anteriormente:

![image](https://user-images.githubusercontent.com/13985581/195956021-9cf86007-e643-481f-ac22-58a8bd9f5dd8.png)

### Resultado obtidido para a ```img_4``` nos três filtros citados anteriormente:

![image](https://user-images.githubusercontent.com/13985581/195956193-7049365b-77e9-4647-86dd-4315fb9ea5be.png)

### Resultado obtidido para a ```img_5``` nos três filtros citados anteriormente:

![image](https://user-images.githubusercontent.com/13985581/195956113-f95bf564-2417-4f4f-b1e9-dd02c1a7139b.png)

## Conclusões:

Através do projeto foi possível realizar a implementação dos filtros média e mediana para observaar a aplicabilidade dos mesmos em um conjunto de imagens com características de desfoque e pontos indesejados.

A documentação de OpenCV classifica esses filtros como filtros de alisamento ou desfoque (Smoothing). O resultado visual, é uma imagem desfocada, mais, na verdade, a operação remove os componentes de baixa frequência. Isso pode ser útil para remover detalhes e manter apenas a estrutura dos objetos.

---
