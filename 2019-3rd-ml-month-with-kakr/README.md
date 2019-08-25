
https://www.kaggle.com/c/2019-3rd-ml-month-with-kakr/overview

# 2019 3rd ML month with KaKR
### 자동차 이미지 데이터셋을 이용한 자동차 차종 분류

안녕하세요. Titanic으로 kaggle에 입문하자마자 무작정 3차 대회에 뛰어든 캐글 초보자입니다.
우선 제가 이렇게 Notebook을 올리는 이유는 다른 고수분들의 Notebook과 비교하면 부끄러운 수준이지만 제 스스로 대회 기간동안
고민하면서 공부한 과정들을 복기하기 위함이고 뒤늦게나마 대회를 시작하는 초보자분들께 조금이나마 도움이 됐으면 하는 바람으로 올리게 되었습니다.


저는 이번 대회를 시작하기 전에는 딥러닝에 대한 지식이 전무하다시피 했었습니다.
따라서 개인적으로 사놓은 딥러닝 책과 구글링을 통한 자료들, 그리고 대회 Notebook들을 동시에 참고하면서 공부했습니다. 
초반에는 이해가 안되는 부분도 많았고 캐글 사용법도 잘 몰랐던 저로써는 많이 어려웠지만 꾸준한 필사와 함께 Discussion을 보고 또 보면서
많은 도움을 받았고 차근차근 단계를 밟으면서 공부하다보니 재미와 함께 성취감을 느낄 수 있었습니다.


캐글은 서로 공유하면서 같이 공부하자라는 취지로 인해 저 같은 초보자들이 공부하기에 너무 좋은 환경인 것을 이번 대회를 통해 많이 느꼈습니다.
저 뿐만 아니라 다른 초보자분들도 이러한 감정을 많이 느낄 수 있었으면 좋겠고 이번 3차 대회를 준비해주시고 운영해주신 운영자분들과 제게 많은 도움을 주신 고수분들께 감사드립니다.

<br>

## Reference
- Image Segmentation Crop (Steve Jang님 notebook)
  https://www.kaggle.com/cruiserx/3rd-ml-month-car-image-segmentation-crop
- Keras / Xception (vh1981님 notebook)
  https://www.kaggle.com/vh1981/kakr-3rd-keras-xception 
- Pretrained Model (Daehun Gwak님 notebook)
  https://www.kaggle.com/daehungwak/keras-how-to-use-pretrained-model

Reference를 큰 줄기로 간추리기 위해 3개 정도만 작성했는데 위에서 언급했다시피 다른 분들께서 올려주신 Notebook, Discussion들을 전부 봤다고해도 과언이 아닐 정도로 꾸준히 참고하면서 많은 도움을 받았습니다. 
Notebooks을 공유해주신 모든 분들께 감사드리고 특히 제게 가장 많은 도움을 주신 vh1981님께 다시 한 번 감사드립니다.


<br>


# Process

### 1. 필사적으로 필사하기.
 - 태진님께서 올려주신 Baseline을 기반으로 필사하면서 안에 담긴 이론들과 Keras를 공부했습니다.
 - Jang님께서 올려주신 Xception 모델을 사용한 Notebook을 필사하면서 Pre-Trained Model, Transfer Learning을 공부했습니다.
 - 동시에 Daehun Gwak님께서 올려주신 How to use pretrained model Notebook도 많이 참고했습니다.

### 2. 나만의 Baseline을 만들기.
 - 여태까지 필사하면서 공부한 자료로 Xception 모델을 사용한 Baseline을 만들었습니다.
 - 그 때의 Public Score는 0.90003이었고 점수를 올리기 위해 앙상블 기법을 사용해야겠다고 생각했습니다.
 - 또한 Private Score를 잘 받기 위해서는 Overfitting을 막기 위한 일반화가 필수라는 것을 배웠습니다.
 
### 3. 최종 Modeling
 - 저는 Stratified KFold를 사용해서 5개의 fold를 만들었고 이를 각각의 커널로 불러와서 가중치를 만드는 법을 배웠습니다.
 - 또한 Steve Jang님의 Segmentation crop방법을 이용한 dataset을 사용했습니다.
 - 위에서 만든 Segmentation dataset과 5개의 fold file들, weight들을 하나의 커널로 불러왔고 Stacking을 통한 앙상블 기법 중 하나로 weight average model을 사용했습니다.
 - 이 때, vh1981님의 Notebook을 많이 참고했고 질문도 많이 했었는데 그 때마다 친절히 답변해주셨습니다. 


<br>


저는 Private LB 기준으로 0.937의 Score를 받아서 61등으로 대회를 마쳤습니다.
Steve Jang님의 Solution Notebook을 보시면 Segmentation crop Dataset을 사용했을때 점수가 오히려 안나왔다고 말씀해주셨는데요.
이를 보고 저도 Dataset을 허태명님께서 올려주신 Bounding box로 crop한 dataset을 사용해서 다시 시도해봤더니 0.937에서 0.949로 오른 것을 확인할 수 있었습니다.
Segmentation crop한 점수가 왜 더 낮은지는 저도 의문이네요...

