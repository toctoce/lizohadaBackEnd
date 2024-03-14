# 일조하다 백엔드 개발

## 인프라 배포 방법

현재 CICD를 완전히 구축하진 못한 상황이다. 하지만, 앞으로 CICD를 구축하기 위해 지속적인 노력을 할 것이며 일단은 AWS 콘솔을 이용해야한다.

### 람다를 배포하는 방법

루트 디렉토리에는 `index.mjs` or `index.js` 가 존재해야함.
AWS Lambda 는 `index.mjs`를 실행시키는 것.

사용자가 작성한 모듈은 `common` 디렉토리에 저장, 라이브러리 같은 의존성은 `node_modules`에 저장

프로젝트 압축 라이브러리 설치
aws에서 만든 압축 라이브러리 `npm install aws-xray-sdk --save` 를 통해 설치

이 라이브러리는  `index.mjs` 와 그 하위 모듈은 `common` 디렉토리에 있는 모듈들이 의존하는 의존성까지 포함해서 zip 으로 압축

압축 실시!
 `zip -r my_deployment_package.zip . `

 `zip -r [압축 파일 이름].zip [index.mjs가 존재하는 위치]`

람다에 넣으면 `index.mjs`를 실행 가능!

### EC2를 배포하는 방법

`CodePipeLine` 과 `CodeDeploy`를 이용해서 배포할 수 있는데 아직 구축하진 못했다. (주말 간 만들 예정)
다만, `cloudFormation`을 이용해서 EC2 인프라 자체는 생성할 수 있다.

1. `/lizohada/Infrastructure/default-ec2.yaml`의 코드 수정
2. aws cloudformation 콘솔로 이동
3. 해당 파일을 통해 LizohadaStack을 업데이트 

## 프로젝트 주요 기능

### 블로그 글 스크랩핑 (Blog Scrape) 

### 키워드 추출 (Keyword Extraction)

### 모델 학습 (Keyword Learning)

### 유저 취향 추론 (Preference Inference)