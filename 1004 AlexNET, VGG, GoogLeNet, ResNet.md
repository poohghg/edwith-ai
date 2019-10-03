참고자료

# <http://taewan.kim/post/cnn/>



## 4가지 CNN 살펴보기: AlexNET, VGG, GoogLeNet, ResNet**

레이어가 많으면 성능이 좋아질 확률이 높아진다.

딥하게  레이어를 쌓는것도 중요하지만 무조건 레이어를 깊게 쌓다고 성능이 좋아지지 않는다.

레이어를 쌓을때마다 필요로 하는 기술이 있다.

# AlexNET

![1570127041906](C:\Users\user\AppData\Roaming\Typora\typora-user-images\1570127041906.png)



- 하이퍼파라메터를 구하는게 중요하다
- 입력채널 * 필터사이즈 * 출력채널 로 구하면된다.
- 입력데이터에 적용한 필터의 개수는 출력 데이터인 Feature Map의 채널이 됩니다.



### RELU

![1570127392663](C:\Users\user\AppData\Roaming\Typora\typora-user-images\1570127392663.png)



### LRN

- 컨볼류션 피처맵의 일정부분만 높은값을 가지고 나머지는 낮은값을 가진다.



### Data augumentation

일반적으로 데이터를 늘려서 사용했다.

- Flip -> 좌우반전
- crop + Flip aufmentation
- ![1570127703668](C:\Users\user\AppData\Roaming\Typora\typora-user-images\1570127703668.png)
- ![1570127869406](C:\Users\user\AppData\Roaming\Typora\typora-user-images\1570127869406.png)
- RGB 채널에 특정값을 더한다. 학습데이터에서 얼마나 정보가 변화되었는지 본 다음에 그에 맞게 노이즈를 더한다.

### Dropout

아웃풋에 0.5를 곱해서 사용했다.

# VGG

컨볼류셜은 은 3x3  stride는 1를 준다.

![1570128285885](C:\Users\user\AppData\Roaming\Typora\typora-user-images\1570128285885.png)

# GoogLenet

### Inception module

![1570128444265](C:\Users\user\AppData\Roaming\Typora\typora-user-images\1570128444265.png)



- one by one 컨볼류선을 추가했다.
- 채널의 수를 한번 줄였을때 파라메터 수가 줄어든다.
- 1 바이 1로 줄였을때 전체 파라메터가 줄어들었다.
- 갈림길이 생김으로써 최종입력 이미지에서 취합된 정보가 달라질 수 있다.
- 이를 통해 더 다양한 결과가 나올수 있다.
- ![1570128496966](C:\Users\user\AppData\Roaming\Typora\typora-user-images\1570128496966.png)
- ![1570128633799](C:\Users\user\AppData\Roaming\Typora\typora-user-images\1570128633799.png)

# ResNet

- residual networks
- ![1570129900742](C:\Users\user\AppData\Roaming\Typora\typora-user-images\1570129900742.png)
- 기존 딥러닝은 레이어가 깊어 질수록 백프로게이션을 통해 얻어진 그래디언트값이 0 또는 1에 극단적으로 수렴할 확률이 높았다.
- 이를 좋은 초기화 방법/배치 정규화/ ReLU의 발달로 해결하려 했다.
- overfiting을 확인하는 방법은 train acc가 높아지지만 test acc가 떨이지는 상태일때 발생한다.
- ![1570130114669](C:\Users\user\AppData\Roaming\Typora\typora-user-images\1570130114669.png)
- Degradation -> 레이어를 더 깊게 쌓아는데도 성능이 떨어지는 현상
- ![1570130412170](C:\Users\user\AppData\Roaming\Typora\typora-user-images\1570130412170.png)
- 입렵 및 출력 데이터를 더한 후 입력데이터의 값을 뺀다. 그후 나머지 값만을 학습한다.
- 타켓과 입력사이의 값만 학습하는 기법이다.

- ![1570130656965](C:\Users\user\AppData\Roaming\Typora\typora-user-images\1570130656965.png)
- 입력과 아웃풋 채널을 맞춰주기위해서 1바이1 필터를 한번 더 사용했다.