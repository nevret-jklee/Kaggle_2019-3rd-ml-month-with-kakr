
https://www.kaggle.com/c/2019-3rd-ml-month-with-kakr/overview

# 2019 3rd ML month with KaKR
### 자동차 이미지 데이터셋을 이용한 자동차 차종 분류

## Introduction

안녕하세요. Titanic으로 kaggle에 입문하자마자 무작정 3차 대회에 뛰어든 캐글 초보자입니다. <br>
제가 이렇게 Notebook을 올리는 이유는 다른 잘하시는분들의 Notebook과 비교하면 부끄러운 수준이지만 제 스스로 대회 기간동안 고민하면서 공부한 과정들을 
복기하기 위함입니다. 또한 딥러닝 지식이 전무하다시피 했던 저의 경험을 공유하면서 추후에 대회를 시작하는 초보자분들께 조금이나마 도움이 됐으면 하는 바람입니다.


<br>


## Reference
- Image Segmentation Crop (Steve Jang님 notebook) <br>
  https://www.kaggle.com/cruiserx/3rd-ml-month-car-image-segmentation-crop
  
- Keras / Xception (vh1981님 notebook) <br>
  https://www.kaggle.com/vh1981/kakr-3rd-keras-xception 
  
- Pretrained Model (Daehun Gwak님 notebook) <br>
  https://www.kaggle.com/daehungwak/keras-how-to-use-pretrained-model
  
- Xception (Jang님 notebook) <br>
  https://www.kaggle.com/janged/3rd-ml-month-car-model-classification-xception


Reference Notebook을 간단하게 4개로 추려서 올렸지만 다른 분들께서 올려주신 Notebook, Discussion들을 전부 봤다고해도 과언이 아닐 정도로 꾸준히 참고하면서 많은 도움을 받았습니다. 공유해주신 모든 분들께 감사드립니다!


<br>


## Process

제가 대회를 준비하면서 겪은 과정들입니다.

### 1. 필사하기.
 - 태진님께서 올려주신 Baseline을 기반으로 필사하면서 안에 담긴 이론들과 Keras를 공부했습니다.
 - Jang님께서 올려주신 Xception 모델을 사용한 Notebook을 필사하면서 Pre-Trained Model, Transfer Learning을 공부했습니다.
 - 동시에 Daehun Gwak님께서 올려주신 How to use pretrained model Notebook도 많이 참고했습니다.

### 2. 나만의 Baseline을 만들기.
 - 여태까지 필사하면서 공부한 자료로 Xception 모델을 사용한 Baseline을 만들었습니다.
 - 그 때의 Public Score는 0.90003이었고 점수를 올리기 위해 Stratified KFold, 앙상블 기법을 사용해야겠다고 생각했습니다.
 - 또한 Private Score를 잘 받기 위해서는 Overfitting을 막기 위한 일반화가 필수라는 것을 배웠습니다.
 
### 3. 최종 Modeling
 - Stratified KFold를 사용해서 5개의 fold를 만들었고 이를 각각의 Notebook으로 불러와서 model을 만드는 법을 배웠습니다.
 - 또한 Steve Jang님의 Segmentation crop방법을 이용한 dataset을 사용했습니다. (bounding box로 crop한 dataset보다 더 좋은 성능이 나올 것이라고 예상했습니다.)
 - vh1981님의 https://www.kaggle.com/vh1981/kakr-3rd-keras-xception 을 기반으로 만들었습니다.
 - 위에서 만든 Segmentation dataset과 5개의 fold file, model들을 하나의 커널로 불러왔고 Stacking을 통한 앙상블 기법 중 하나로 weight average model을 사용했습니다.


<br>


## Result

저는 Private LB 기준으로 0.93668의 Score를 받아 61등으로 대회를 마쳤는데요, 개인적으로는 공부만 하다보니 제출을 많이 못했던 점이 아쉬웠습니다. <br>
Steve Jang님의 Solution Notebook을 보시면 Segmentation crop Dataset을 사용했을때 점수가 오히려 안나왔다고 말씀해주셨는데요. <br>
이를 보고 저도 Dataset을 허태명님께서 올려주신 Bounding box로 crop한 dataset을 사용해서 다시 시도해봤더니 0.93668에서 0.94930로 오른 것을 확인할 수 있었습니다. 이 점도 아쉽긴 하지만 좋은 접근이었다고 생각합니다.

