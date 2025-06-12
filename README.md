# 🍮 소스 코드 
### Frontend
<br></br>
### Backend
- `src/main/java/fooding/foodingback/Auth` : Kakao 로그인, 서버 배포 관련 코드
- `src/main/java/fooding/foodingback/User` : 회원 관련 코드
- `src/main/java/fooding/foodingback/Ingredient` : 식재료 관련 기능 코드
- `src/main/java/fooding/foodingback/global/config` : Kakao 로그인, 서버 배포 관련 코드
- `src/main/java/fooding/foodingback/global/util` : jwt 관련 코드
- `src/main/java/fooding/foodingback/FoodingBackApplication.java` : SpringBoot 프로젝트 Main 클래스
<br></br>
### AI
- `OCR/`              : 영수증 OCR → 텍스트 추출 코드  
- `YOLO_train_test/`  : YOLOv8 모델 학습/테스트 코드  
- `YOLO_result/`      : 학습된 모델 결과 
- `filtering/`        : 식재료 이미지 정제  
- `menu_recomm/`      : 보유 재고 기준 메뉴 추천 모듈  
- `ingredient_recomm/`: 주간 소비 분석 → 식재료 조언 모듈  
- `purchase_prediction.ipynb`: 구매 주기 및 수량 예측 실험 코드
- `web_crawling/`     : 식재료 이미지 크롤링 스크립트

<br></br>
# 🍮 Build 방법 
### Frontend Repository
<br></br>
### Backend Repository
① git clone https://github.com/EWHA-CAPSTONE-FOODING/FOODING-back 으로 프로젝트 폴더를 local 환경에 다운로드합니다.

② 다운로드 받은 폴더의 build.gradle 파일을 코드 편집기에서 연 후, build 버튼을 클릭하여 필요한 라이브러리들을 다운로드합니다.

③ 필요한 정보들을 application.yml 파일에 작성해줍니다.

④ run을 클릭하여 local 환경에서 프로젝트를 실행합니다.
<br></br>
### AI Repository
1. **OCR (영수증 텍스트 추출)**
- 별도 빌드 필요 없음
- API Key, 이미지 파일, 경로를 코드 상에서 직접 지정 필요

2. **YOLOv8 (식재료 이미지 인식)**
- YOLOv8 모델 학습에는 커스텀 데이터셋(data.yaml 기반)과 ultralytics 라이브러리를 사용
- 학습된 weight는 best.pt로 저장

3. **OpenAI 기반 GPT4o (메뉴 추천 / 식재료 조언)**
- GPT 모델은 OpenAI API(gpt-4o)를 통해 사용
- 사용자의 보유 식재료 또는 식단 소비 기록 데이터를 기반으로 프롬프트를 구성하고 GPT에게 JSON/CSV 형식으로 직접 응답을 요청

4. **구매 주기 예측**
<br>: 별도 빌드 없이 코드 실행

5. **AI 모델 서버 배포 (Flask)**
- 학습된 모델은 joblib 형식으로 저장되며, Flask 서버에 로드되어 배포
- API는 프론트엔드에서 JSON 요청을 통해 출력 결과를 받을 수 있도록 구성
