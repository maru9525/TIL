# Epoch vs Batch Size vs Iteration

## Epoch

>  신경망에서 사용되는 역전파 알고리즘은 파라미터를 사용하여 입력부터 출력까지의 각 계층의 weight를 계산하는 과정을 거치는 순방향 패스(forward pass), forward pass를 반대로 거슬러 올라가며 다시 한번 계산 과정을 거처 기존의 weight를 수정하는 역방향 패스(backward pass)로 나뉜다. 이 전체 데이터 셋에 대해 해당 과정이 완료되면 한번의 Epoch가 진행됐다고 볼 수 있다.(수학 시험지를 푼 횟수, 5)

epochs = 40 이라면 전체 데이터를 40번 사용해서 학습을 거치는 것이다.

적절한 epoch 값을 설정해야만 underfitting과 overfitting을 방지할 수 있다.

## Batch Size

> 한번에 학습할 데이터의 수 (=한번체 채점 + 복습하는 문제의 수, 20)



## Iteration

> 한 epoch에서 batch를 학습하는 횟수 (=200문제 / 20문제, 10)



### 정리

전체 2000개의 데이터가 있고, epochs = 20, batch_size = 500이라고 가정합니다. 그렇다면 1 epoch는 각 데이터의 size가 500인 batch가 들어간 네 번의 iteration으로 나누어집니다. 그리고 전체 데이터셋에 대해서는 20번의 학습이 이루어졌으며, iteration 기준으로 보자면 총 80번의 학습이 이루어진 것입니다.