# YOLOv8 이미지 수집, 라벨링, 학습, 모델변환, 플러터 앱 적용 방법
[![테스트영상 ](http://img.youtube.com/vi/dCNm0Gi_59Q/0.jpg)](https://youtu.be/dCNm0Gi_59Q)
## 1. 이미지 수집 방법

### 1-1) 크롬 확장 프로그램 이용: [Fatkun 일괄 다운로드 이미지 - Chrome 웹 스토어 (google.com)](https://google.com)
사용 방법:
- 크롬 설치, 확장 프로그램 다운로드한다.
- 원하는 이미지는 구글, 네이버 등에서 검색한다. 검색엔진 bing을 추천한다.
  ex) bing에서 딸기 검색한다.
- 검색 후 원하는 이미지를 클릭한다.
- 단축키: alt+z 시 화면이 나온다.
- 다운로드할 이미지를 골라서 일괄 다운로드 가능하다.
- Tip) 이미지 크기가 너무 작으면 안 되므로 다운로드할 폭과 신장 길이 걸러서 다운로드한다.
- Download 버튼을 누른 후 다운로드 폴더 안에 들어가면 다운로드한 이미지들이 폴더안에 들어있다.

**주의사항**: 다운로드할 이미지에 저작권이 있을 수 있으므로 저작권법에 위반 되지 않도록 사용한다.


### 1-2) AI-Hub 이용 
[AI-Hub](https://www.aihub.or.kr/index.do)

사용 방법:
1. AI Hub 회원가입
2. 로그인->마이페이지->회원정보에 휴대전화 인증
3. 원하는 데이터 신청 후 다운로드

**주의사항**: 본 AI 데이터는 인공지능 학습모델의 학습용으로만 사용할 수 있습니다.

 ## 이미지 라벨링 방법

### 로보플로우 이용
[Roboflow](https://roboflow.com/)

#### 1. 접속 후 회원가입

#### 2. Create New Project 클릭
> **주의**: 초기 Workspaces는 public으로 설정됩니다. public으로 생성하면 라벨링된 자료들이 roboflow universe에 공유됩니다. 공유를 원하지 않으면 private로 설정하세요.

#### 3. 프로젝트 설정
- License를 CC BY 4.0으로 설정합니다. 

#### 4. 이미지 업로드
- 라벨링할 사진을 업로드합니다.

#### 5. 업로드 세이브
- `save and continue`를 클릭하여 저장합니다.

#### 6. 라벨링 작업 할당
- 프로젝트 초대로 작업을 나눌 수 있습니다. (최대 5명)

#### 7. 라벨링 작업
- 라벨링 방식은 Box 또는 Segmentation 중 선택합니다.
> **주의**: 클래스명을 정확하게 지정해야 합니다.

#### 8. 라벨링을 데이터 세트에 추가
- `Add images to Dataset` 버튼을 클릭합니다.
- 라벨링된 이미지를 Train, Valid, Test로 분할합니다. (일반적으로 7:2:1 비율)

#### 9. Generate 클릭
- 이미지 처리, 리사이징, 분할 등의 작업을 진행할 수 있습니다.

#### 10. 데이터셋 파일 다운로드
- YOLOv8 등의 포맷으로 데이터셋을 다운로드합니다.

> **주의**: Public WorkSpace로 작업을 완료하면 Roboflow Universe에서 공개됩니다. 저작권 문제를 피하기 위해 주의가 필요합니다.

## 이미지 학습 모델 변환 방법

- 학습 및 tflite 변환에 대한 상세한 방법은 `yolov8_CupTrain&convert_tflite.ipynb` 파일을 참고하세요.

## 플러터 적용 방법

### 1. 플러터 설치

### 2. Git Code 다운로드
- 관련 문서 및 git 주소를 참고하여 코드를 다운로드합니다. (https://github.com/vladiH/flutter_vision)
- `example/android/build.gardle` 파일에서 Line 39의 `minSdkVersion`을 21로 수정합니다.

### 3. tflite 모델 및 라벨 정보 적용
- `assets` 폴더에 tflite 모델을 넣습니다.
- `labels.txt` 파일에서 라벨 정보를 수정합니다. `metadata.yaml` 파일의 순서를 따르며, 해당 순서에 맞게 명칭을 바꾸면 됩니다.
  
### 4. 의존성 업데이트
- `pubspec.yaml` 파일에서 `pub get` 명령어를 실행하여 의존성을 업데이트합니다.

### 5. tflite 모델 경로 수정
- `main.dart` 파일에서 tflite 모델의 경로를 수정합니다.

### 6. 앱 실행
- `main.dart` 파일을 실행하여 결과를 확인합니다.

