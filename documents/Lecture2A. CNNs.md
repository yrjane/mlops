# Lecture2. CNNs

## 1) Review of the convolution operation
### 1.1) What's a convolutional filter
- image 분석에 있어서 fully-connected filter를 사용하지 않는 이유
 1) 엄청난 연산량: tensor 연산량이 기하급수적으로 증가하는 문제
 2) overkill: 모든 picxel에 대해 동일하게 가중치를 계산하는데 실제 분류에 사용되는 부분은 일부분으로 과도하게 계산하는 문제
- convolutional filter: 일부 이미지 공간에 대해 합성곱을 진행하여 이미지의 공간정보를 유지한채 학습을 하게함
### 1.2) filter stacks and ConvNets
- multiple channels를 가진 image를 입력할 경우에도 각 채널마다 window size에 맞게 filter가 이동하며, 합성곱을 진행할 때 스칼라곱 혹은 행렬곱셈을 사용하는지에 따라 output 이 1개의 채널 혹은 여러 개의 채널을 가질지도록 만들 수 있음
- 이를 통해 convolutional layers 를 쌓아서 모델을 구성하는 것이 가능함
### 1.3) Strides & Padding
- stride: convolutional filter를 몇 칸씩 이동할지 정하는 것이 가능함
- padding: stride를 적용하여 filter를 이동할 경우 입력데이터보다 출력 데이터가 작아지게 되는데 이를 방지하고자 동일 사이즈를 갖도록 특정 값을 이미지 가장자리에 추가하는 padding 작업을 진행할 수 있음
### 1.4) filter math
- filter size(F), stride(S), padding(P)를 통해 output 크기를 계산 가능함
  W' = (W-F+2P)/S+1
  H' = (H-F+2P)/S+1
  각 filter마다 parameters F*F*D개 가지며 layer 내에 K*(F*F*D)개 파라미터 가짐 


## 2) Other important operations for ConvNets
## 2.1) Increasing the receptive field (dilated convolutions)
- receptive field: 출력 레이어의 뉴런 하나에 영향을 미치는 입력 뉴런들의 공간 크기
- convolution을 쌓으면 기존 receptive field 가 증가함 
- dilated Convolution: 기존 컨볼루션 필터가 수용하는 픽셀 사이에 간격을 둔 형태로 입력 픽셀 수는 동일하지만, 더 넓은 범위에 대한 입력을 수용할 수 있게 됨
## 2.2) decreasing the size of the tensor
- Pooling: feature map: Convolution을 거쳐서 나온 activation maps를 작게 resize함 (ex. 2x2 max pooling)
- 1x1-convolutions: 이미지의 채널 수("depth" dimension)를 줄이는 방법

## 3) Classic ConvNet architectures
- 가장 기본적인 CNN 아키텍처로 LeNet이 존재함

![image](https://user-images.githubusercontent.com/66201990/160846148-42b8a5e4-ea00-4744-aba7-61d2052d6487.png)




