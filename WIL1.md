딥 러닝 component: 
1. Data: Task에 따라 다른 형태
2. Model: 쉽게 말해 프로그램
        ㄴ Data에서 특정 feature를 뽑아내서 우리가 원하는 output으로 만들어줌
            ex> AlexNet, ResNet...
3. Loss function: 학습 중 알고리즘이 내놓은 예측이 정답과 다른 정도에 대한 지표.
    우리의 Model은 Neural Network로 이루어져 있음
    Neural Network
    ㄴ여러 Layer가 있음
    ㄴ각 Layer에 weight와 bias가 있음
    ㄴ이러한 것들(?) 은 pharameter
    Loss function을 이용해 알고리즘이 내놓은 예측과 정답을 비교해 pharameter를 업데이트함->이 것을 통해 우리가 원하는 정답에 가까운 output을 뽑아내는 것이 딥러닝
    ex1> 회귀 문제: MSE
    ex2> 분류 문제: Cross Entropy
    ex3> 확률적 문제: MLE
4. Optimizaion
    optimization: 경사하강법
    Regularization: 학습을 방해해 일반화 성능 높임
        ㄴ ex> Dropout, Early Stopping...

Neural Network
행렬곱, 비선형 연산으로 만들어짐

Nonlinear Function
ㄴ 대부분 활성함수
ㄴ 비선형 함수
ㄴㄴ 선형인 경우 의미가 없음
ㄴ ex> ReLU, Sigmoid, Hyperbolic Tangent.

multi-layer perceptron
ㄴperceptron 으로 이루어져 있고, perceptron을 여러 겹으로 쌓은 것
ㄴㄴperceptron: 가중치*input + bias 
ㄴ input x가 행렬곱셈과 비선형 연산을 거쳐 히든 벡터인 h가 되고 h에서 다시 행렬곱셈과 비선형 연산을 거쳐서 output이 된다.
ㄴㄴ 이러한 반복을 많이 했을 때 multi-layer perceptron 이 된다.

Loss function의 모순
ㄴ 학습데이터에 noise 가 낀 outlier들이 많을 경우 Loss function을 줄이려고 outlier들에 맞추려다가 뉴럴 네트워크가 전반적으로 망가질 수 있다.
ㄴㄴ Loss function을 강박적으로 줄이는 게 항상 target-data를 찾는 데 도움이 되는 것은 아니다.

Generalization
ㄴ 학습에 사용하지 않은 data: test data
ㄴ test data의 에러 test error
ㄴ 학습을 반복할 수록, training error는 줄어드나, test error는 같이 줄어들다가 어느 순간 증가한다.

under fitting: 모든 data에서 잘 동작하지 않음: 뉴럴 네트워크 너무 간단
over fitting: train data에서 잘 동작하나, test data에서 잘 동작하지 않음: 뉴럴 네트워크 너무 복잡

under fitting, over fitting 중간이 가장 최적의 상태

cross-validation: train data 중 일부를 모델이 잘 학습됐는지 확인하는 valid data로 이용

ensemble: 데이터를 나눠서 학습시키는 방법

regularization:
ㄴ 학습을 방해해 과적합 방지
ㄴ Early stopping
ㄴ parameter norm penalty: network parameter가 작으면 작을 수록 좋으므로 작게하는 방법
ㄴ data augmentation: 데이터를 수정해서 학습 데이터를 다양하게 가져가는 방법
                    ㄴ 단 task에 따라서 다르게 데이터를 수정해야 함
    Noise robustness: 
    ㄴ robustness한 모델은 noise 가 꼇거나 이상치가 들어와도 크게 흔들리지 않는다.
    ㄴ 그리고 범용적인 데이터에도 잘 작동한다.
ㄴ Dropout: train 중 일정 확률로 임의의 노드를 drop 하는 것
ㄴㄴ 더 robust한 모델을 만드는 방법론
ㄴ 라벨 스무딩
ㄴㄴ 모델이 너무 확신을 가지지 않도록 하는 것

Convolutional Neural Network
ㄴ 이미지의 공간정보를 유지하는 것이 핵심
ㄴ 1*n 으로 집어넣을 시 공간 정보 소실, 보완하는 것이 CNN

FNN
ㄴ 인접 픽셀간 상관관계 유실: 1*n
ㄴ CNN이 해결

CNN
input에서 convolution 연산, pooling 반복적으로 거쳐 feature map 추출 후 fully connected layer 통과하여 output

convolution 연산
ㄴn*n크기의 filter 가  input을 하나 하나 스탬프질 해서 output 한칸한칸 채워나감
ㄴinput의 depth와 filter 의 depth 는 동일해야 함
ㄴoutput의 채널 수 만큼의 filter 가 필요함

input 은 다음을 차레로 거친다.
1. convolution 연산
2. 활성화함수
3. pooling
4. 1~3 몇번 반복
5. fully connected layer 통과.

pooling
ㄴ 공간정보 유지하며, 사이즈 줄이기.
ㄴ ex> max pooling, avaerage pooling

1x1 convolution
ㄴ n 깊이의 data depth로 조절 가능하게 해주는 1x1xn filter를 이용한 연산
ㄴ depth 조절 가능 하면 parameter 수가 줄어들고, parameter 수가 줄어들면 뉴럴네트워크를 깊게 쌓을 수 있다.


human error rate: 5.1%

alex net:
1. 네트워크 두개로 나눔
2. ReLU 사용: 그래디언트 소실 막음
3. data augmentation 사용

VGG Net
3x3 convolution filer 를 써서 파라미터를 매우 줄임

GoogleNet
1x1 convolution filter 사용하여 뉴럴 네트워크를 매우 깊게 쌓았고, 파라미터 절약함

Resnet
Skip connection 사용하여 gradient vanishing problem 해결





