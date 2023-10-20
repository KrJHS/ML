# YOLO v8n
##-YOLOv8 이미지 수집, 라벨링, 학습, 모델변환, 플러터 앱 적용 방법-

###1.	이미지 수집 방법
1-1) 크롬 확장 프로그램 이용: Fatkun 일괄 다운로드 이미지 - Chrome 웹 스토어 (google.com) (하이퍼 링크 이용 시 Ctrl+마우스 좌 클릭)
사용 방법
1.	크롬 설치, 확장 프로그램 다운로드한다.
2.	원하는 이미지는 구글, 네이버 등에서 검색한다. 검색엔진 bing을 추천한다.
ex) bing에서 딸기 검색한다.

검색 후 원하는 이미지를 클릭한다.
 
클릭한 이미지와 유사한 이미지들이 나온다.
3.	단축키: alt+z 시 화면이 나온다.
 
	   다운로드할 이미지를 골라서 일괄 다운로드 가능하다.
Tip) 이미지 크기가 너무 작으면 안 되므로 다운로드할 폭과 신장 길이 걸러서 다운로드한다.
4.	Download 버튼을 누른 후 다운로드 폴더 안에 들어가면 다운로드한 이미지들이 폴더안에 들어있다.
 
*주의사항: 다운로드할 이미지에 저작권이 있을 수 있으므로 저작권법에 위반 되지 않도록 사용한다.
1-2) AI-Hub 이용 https://www.aihub.or.kr/index.do
 
사용 방법
1.	AI Hub 회원가입
2.	로그인->마이페이지->회원정보에 휴대전화 인증
3.	원하는 데이터 신청 후 다운로드
*주의사항: 본 AI 데이터는 인공지능 학습모델의 학습용으로만 사용할 수 있습니다. 다만 기존의 데이터셋을 활용하시어 만들어진 2차 저작물(훈련으로 만들어진 지능형 제품・서비스, 챗봇 등) 은 영리적・비영리적 활용이 가능합니다. 사이트 업로드, 무
단 배포 등 금지

###2.	이미지 라벨링 방법
1)	로보플로우 이용: https://roboflow.com/
사용방법
1.	접속 후 회원가입
 
2.	가운데 Create New Project 클릭한다.
*초기 Workspaces는 public으로 되어있다. public으로 생성 시 라벨링 한 자료들이 roboflow universe에 공유가 되므로 공유를 원하지 않는다면 private로 생성하여 라벨링 작업을 해야 한다. Public, Private 업로드 가능한 이미지 수 1000장 유료 계정 이용 시 업로드 가능한 이미지 수 증가
3.	프로젝트 설정
 
License는 CC BY 4.0으로 설정하고 나머지는 아무렇게 써도 상관없다.
4.	이미지 업로드
프로젝트 생성 후에는 이제 라벨링 작업을 진행할 사진을 프로젝트에 업로드 해 주어야 한다. 자료를 선택하거나 파일에서 드래그해서 업로드한다.. 

5.	업로드 세이브
업로드가 다 되었으면 save and continue 초록색 버튼을 눌러 저장을 해준다.
 
6.	라벨링 작업 할당
 
프로젝트에 초대를 하면 작업을 나누어서 작업할 수 있다. (5명까지 가능)
Assign images-> Start Annotating
7.	라벨링 작업
 
라벨링 작업시 보는 화면이다.
라벨링 작업의 2가지 방법
1.	Box
2.	Segmentation 
  
상황에 맞는 라벨링 방식을 선택해 주면 된다. 
 
영역을 지정한 후 Class 이름을 지정하는 Annotation Editor가 나오면 이름을 적어주고 Save 한다.
*클래스를 정확하게 구분하여 작업해야 한다. 구분이 잘못되었으면 모델에 영향을 준다. Ex) 딸기 이미지에 사과 클래스 (x)

8.	라벨링을 데이터 세트에 추가하기
작업을 다해주었으면 Add images to Dataset 버튼을 눌러준다. 
 
Train, Valid, Test 데이터로 라벨링 된 이미지를 비율대로 나눌 수 있다.
보통 7:2:1로 나눈다. 
Dataset에 들어가면 7:2:1 비율로 라벨링 데이터가 들어가 있다.

9.	Generate 클릭
 
마지막으로 Generate 버튼을 눌러준다. 여기서 이미지 증식 Preprocessing, 이미지 resize, Split 등 작업을 할 수 있다.
10.	데이터셋 파일 다운로드
 
Generate 버튼을 누른 후에 이런 위에 와 같은 화면이 나온다. 사이트에서 직접 학습이 가능하기도 하지만 유료 버전이라 Custom Train에 YOLOv8을 선택해 주고 Get Snippet을 눌러준다. 
 
그러면 zip 파일로 다운로드할 것인지 다운로드 Code로 받을 것인지 선택할 수 있다. Select a Format을 YOLOv8, download zip to computer을 선택해 주고 Continue 버튼을 눌러준다.
그러면 zip 폴더 안에 Train, Valid, Test 폴더와 data.yaml 파일이 들어 있을 것이다.
data.yaml 파일로 라벨링 구성 정보들을 볼 수 있다.
*WorkSpace를 Public으로 하여 여기까지 작업을 완료하였으면 Roboflow Universe에 작업한 데이터 세트를 누구든지 볼 수 있고 다운로드할 수 있다. 그러므로 저작권 있는 이미지는 조심해야 한다. 자신의 Universe 링크는 Universe Page 가운데 링크가 있다.
###3.	이미지 학습 모델변환 방법
학습 및 tflite 변환은 yolov8_CupTrain&convert_tflite.ipynb에 나와있다.

###4.	플러터 적용 방법
1.	플러터 설치
2.	Git Code 다운로드 관련 문서, git
example/android/build.gardle 파일 Line 39 코드 수정 minSdkVersion 21 
3.	assets 폴더 안에 tflite 모델 넣기, labels.txt 라벨 정보 수정해주기
metadata.yaml파일 순서대로 되어있으므로 순서에 맞게 명칭을 바꿔주면 된다.

Ex)
 
 
4.	pubspec.yaml - pubget
5.	main.dart에 tflite 모델 경로 수정해 주기
6.	main.dart 실행
결과화면
 
 
