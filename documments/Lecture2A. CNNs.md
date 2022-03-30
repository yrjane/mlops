# Lecture1. Deep Learning Fundamentals

## 1) Neural Networks
- 인간의 뉴런구조에서 영감을 받아 수학적인 해석을 통해 neural network 컨셉이 탄생함
- activation function의 경우 sigmoid function, hyperbolic tangent, rectified linear unit(Relu)등이 일반적으로 사용됨
- neural network는 각각 weight, bias를 가진 퍼셉트론들이 layer의 형태로 구성되어있고 이 각 layer 끼리 연결되어 있는 구조로 function y를 나타낼 수 있음
## 2) Universality
- universal function approximation theorem 은 충분한 hidden unit를 가진 1개의 hidden layer로 구성된 neural network 를 이용하여 어떤 함수든 근사시킬 수 있다는 이론 (활성 함수는 비선형함수여야함)
## 3) Learning problems
- learning problem 타입에 따라 지도학습, 비지도학습, 강화학습으로 나눌 수 있음
- 비지도학습: 라벨링되지 않은 X데이터를 활용, 비지도학습 모델을 통해 fake데이터 생성 및 인사이트 도출 등
Ex1) predict next character(charRNN): 문자 단위의 RNN으로 다음에 올 문자를 예측하는 모델. 
ex2) predict nearby words(word2vec): 어떤 단어와 어떤 단어가 비슷한지 사람이 알려주지 않아도 word2vec은 비슷한 단어들을 찾아낼 수 있음
ex3) predict next pixel(pixelCNN): 이미지를 생성할 수 있는 generative model인데 현재까지 생성한 픽셀 정보를 바탕으로 다음 픽셀을 예측하는 과정을 하나의 이미지 생성을 완성할 때 까지 반복하는 과정으로 구성
ex4) predict X that is indistinguishable from real X (GAN): 실제에 가까운 이미지나 사람이 쓴 것과 같은 글 등 여러 가짜 데이터들을 생성하는 모델
- 지도학습: 라벨링된 데이터를 활용하여 학습된 모델을 통해 X를 기반으로 Y를 예측함 
- 강화학습: 어떠한 환경에서 어떠한 행동을 했을 때 그것이 잘 된 행동인지 잘못된 행동인지를 나중에 판단하고 보상(또는 벌칙)을 줌으로써 반복을 통해 스스로 학습
## 4) Empirical risk minimization / Loss functions
- linear regression: 데이터에서 squared error를 최소화하는 선형관계를 찾음
- 데이터를 토대로 산출한 모델의 예측 값과 실제 값과의 차이를 표현하는 지표를 손실 함수라고 하며 이를 최소화하는 것이 모델 학습의 목적임
- neural net Regression의 경우 MSE등의 loss function을, Classification의 경우 cross-entropy loss function 을 활용함
## 5) Gradient Descent
- Gradient Descent Algorithm 비용함수(Cost Function)를 최소화하는 θ를 찾기 위한 알고리즘으로 기울기에 따라 θ를 반복적으로 갱신하면서 비용을 최소화시키는 θ에 도달
- 경사하강법을 보다 더 잘 적용하기 위해서는 데이터의 well-conditioned(equal variance, zero mean)이 필요하며 이를 위해 weight initialization, normalization 등의 방법을 적용함
- 또한 gradient descent 계산시 데이터 샘플링을 통해 더 빠른 계산이 가능함
## 6) Backpropagation / Automatic differentiation
- 최적의 weight와 bais를 찾기 위해 loss function를 최소화하기 위한 학습을 하였는데 이를 gradient descent로 가능하였는데 그럼 gradient를 계산하는 효율적인 방법은 무엇일까? Backpropagation! 
## 7) Architectural Considerations (deep / conv / rnn)
- 가장 간단한 방법으로 fully connected layer를 쌓는 모델 구조
- 데이터 효율성
- optimization landscape / conditioning
- computational / parameter efficiency
## 8) CUDA / Cores of Compute
- CUDA란 그래픽 처리 장치(GPU)에서 수행하는 (병렬 처리) 알고리즘을 C 프로그래밍 언어를 비롯한 산업 표준 언어를 사용하여 작성할 수 있도록 하는 GPGPU 기술
