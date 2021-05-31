# Image-Captioning-with-Transformer

## Transformer_Captioning_CS231N.ipynb
이전에 학습하고 구현했던 Transformer(Decoder) 를 이용하여 CS231N(2021) 에서 제공하는 dataset 과 utility 를 활용하여 image captioning.

## Image_Captioning_Attention_ViT.ipynb
ViT 는 patch 로 나누어 Transformer 을 적용하고 이 patch 들과 caption의 word들 에 attention 을 적용하여 시각화 하면 각 word 마다 attention 하는 patch 를 볼 수 있지 않을까 라는 궁금즘으로 시도해 보았다. 

MS COCO dataset 을 이용하여 전처리한 뒤, 이전에 학습하고 구현했던 Transformer(Decoder) 와 Vision Transformer(Encoder) 를 이용하여 image captioning 및 Attention 시각화.


## dataset

MS COCO 2014 : https://cocodataset.org/#download

## result
### Transformer_Captioning_CS231N.ipynb
![image](https://user-images.githubusercontent.com/68524289/120184846-6738a280-c24c-11eb-843b-d17749fd8ecc.png)
![image](https://user-images.githubusercontent.com/68524289/120184898-79b2dc00-c24c-11eb-9394-5bf3f67e3bdf.png)


### Image_Captioning_Attention_ViT.ipynb
GT : A person is in mid air on a snowboard.

![image](https://user-images.githubusercontent.com/68524289/120185536-491f7200-c24d-11eb-8897-49fb29b8cf12.png)

GN : (start) the person is (unk) skiing through the mountains . (end) 

Mean Attention
  
![image](https://user-images.githubusercontent.com/68524289/120185605-648a7d00-c24d-11eb-9c7f-3624728e8e94.png)

All Attention (4 heads)

  the

  ![image](https://user-images.githubusercontent.com/68524289/120185882-bc28e880-c24d-11eb-8cbc-347f58be0d04.png)

  person
  
  ![image](https://user-images.githubusercontent.com/68524289/120185962-d2cf3f80-c24d-11eb-8225-38311841806f.png)
    
  is
  
  ![image](https://user-images.githubusercontent.com/68524289/120190693-eb425880-c253-11eb-8c82-9588581c93a7.png)

  
  skiing
  
  ![image](https://user-images.githubusercontent.com/68524289/120190719-f4332a00-c253-11eb-8303-cf75b324f335.png)

  through
  
  ![image](https://user-images.githubusercontent.com/68524289/120190766-02814600-c254-11eb-8292-0f696a8fb1c3.png) 

  the
  
  ![image](https://user-images.githubusercontent.com/68524289/120190893-2a70a980-c254-11eb-850b-f461307a95ff.png)

  mountains
  
  ![image](https://user-images.githubusercontent.com/68524289/120190904-2e043080-c254-11eb-949c-7a99dcf6553a.png)
  
  GT : A woman that is on a tennis court with a racquet.
  
  GN(Gnerated Caption) : <start> woman that is on a tennis court with a racquet . <end>
  
  ![image](https://user-images.githubusercontent.com/68524289/120190963-43795a80-c254-11eb-9cbb-a3a182bd83dc.png)
  ![image](https://user-images.githubusercontent.com/68524289/120190985-4d9b5900-c254-11eb-8866-c781200003b0.png)

 

## Comment
data set 이 너무 크고 caption 이 너무 다양해서 val set 으로 나누지 않고 overfitting 시켜 관찰하였다. 
추후에 전체 학습 데이터를 학습시켜 overfitting 을 줄이고 일반화 된 것들을 관찰할 것.

Transformer_Captioning_CS231N.ipynb 의 경우 
  
CS231N 에서 제공하는 MS COCO dataset, utility, image feature 를 사용하였다. overfitting 되어, val set 에서는 낮은 정확도를 보인다.
  
Image_Captioning_Attention_ViT.ipynb 의 경우 

1. MS COCO dataset 을 download 하여 caption 을 preprocessing 하였다.
2. Pretrained ViT 로 image feature 를 patch 마다 생성하고
3. 생성한 patch 마다의 feature 들과 caption 을 attention 을 활용하여 학습하였다. (Transformer Decoder 이용)
4. caption 의 word 마다 어떠한 patch 를 attention 하는 지 시각화 하였다.

(현재 보인 attention 은 잘 된 케이스이고 일반화가 덜 되어있다. 추후에 개선.)


preprosessing 은 
1. https://www.tensorflow.org/tutorials/text/image_captioning
2. https://github.com/yunjey/pytorch-tutorial/tree/master/tutorials/03-advanced/image_captioning
를 참고하였다.

## TODO
전체 dataset 학습 및 일반화

attention 과 original image 를 결합한 시각화


