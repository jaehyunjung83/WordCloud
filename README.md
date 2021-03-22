# webpack이 v5로 업데이트되고 webpack-cli와 버전이 꼬이면서 발생한 문제
* 아래 사항 그대로 하면 이런 오류 발생
```
Error: Cannot find module 'webpack-cli/bin/config-yargs'
Require stack:
- /Users/jjh/Documents/ReactNative/ReactWordCloudWebApp-React/node_modules/webpack-dev-server/bin/webpack-dev-server.js
```

# package.json에서 webpack 버전 4로 바꾸고 npm install해야 함
* (최신 버전인 5버전으로 하면 webpack-cli@3.3.11 버전이랑 호환x고,
   4.0.0처럼 4중에 너무 낮은 버전으로 하면 css-loader@5.1.3 버전과 호환x)
* 일단 git clone https://github.com/ndb796/ReactWordCloudWebApp-React.git
한거에서 그대로 yarn add나 npm install 해서 다른 거 설정 하고

package.json을
```
  "devDependencies": {
    "webpack": "4.27.0",
    "webpack-cli": "3.3.11",
    "webpack-dev-server": "3.7.1"
    }
```
로 설정하고
```
npm i -g webpack-cli@3.3.11
```
```
npm cache clean (--force) // cache clean command
```
```
rm -rf node_modules // node_modules 폴더삭제
```
```
rm package-lock.json // package.json 파일삭제
```
```
npm install // 노드모듈 인스톨
```
```
npm start
```
하면 됨


---


# ReactWordCloudWebApp-React
* 프로젝트 환경을 구축할 수 있습니다.
```
git clone https://github.com/ndb796/ReactWordCloudWebApp-React.git
```
* Visual Studio Code로 루트 폴더를 엽니다.
* 종속성 모듈을 설치합니다.
```
yarn add --dev webpack webpack-dev-server
yarn add --dev babel-core babel-loader babel-preset-react-app
npm install --save-dev style-loader
npm install --save-dev css-loader
yarn add webpack-cli
```
* Firebase에 새로운 프로젝트를 생성해 테스트 모드로 Realtime DB를 생성합니다.
* 다음과 같이 규칙을 설정합니다.
```
{
  "rules": {
    ".read": true,
    ".write": true,
  	"words": {
      ".indexOn": ["word"]
    }
  }
}
```
* 소스코드에서 databaseURL 경로를 새로운 파이어베이스 경로로 변경합니다.
* 이후에 프로젝트를 시작합니다.
```
yarn start
```
* 프로젝트 정상 동작 확인 이후에는 파이어베이스에 배포합니다.
```
yarn add --dev copy-webpack-plugin
yarn add webpack-cli
npm install -g firebase-tools
firebase init
# 호스팅 서비스 설정: Deploy - Build 폴더 - No Single Page App
yarn build
firebase deploy
```
