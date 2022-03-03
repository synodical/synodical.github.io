- 홍익대학교 기숙사 층장의 업무 자동화를 위해 점호 시스템을 만드는 과정
- ‘zerocho(조현영)님의 Node.js 교과서’를 참고하여 공부하면서 만들었음

- [ ]  ‘비동기/동기'와 async/await, promise 이해하기
- [ ]  [https://elvanov.com/2597](https://elvanov.com/2597) 이거 따라치면 위에가 될지도


*//const { DataTypes } = require("sequelize/types");*

*//const { sequelize } = require(".");*

# 에러

## User.findOne is not a function

[https://stackoverflow.com/questions/44248753/ssequelizejs-mysql-and-passportjs-user-findone-not-a-function](https://stackoverflow.com/questions/44248753/ssequelizejs-mysql-and-passportjs-user-findone-not-a-function)

[https://stackoverflow.com/questions/41924961/user-findone-is-not-a-function](https://stackoverflow.com/questions/41924961/user-findone-is-not-a-function)

첫번째 링크로 해결하였음. 

```jsx
const User = require('../models/user'); //에서
const User = require('../models').User; //로 수정
```

> This is like this because of the way the models are dynamically exported. You can have a look at your files, models/index.js. There you will find how each model is exported in a single object. So you basically always require the models/index.js and there specify which key you want to access, in this case "User”
> 

## EJS don't escape html

**[Print raw html strings on EJS](https://stackoverflow.com/questions/8124583/print-raw-html-strings-on-ejs)**

[https://www.digitalocean.com/community/tutorials/how-to-use-ejs-to-template-your-node-application](https://www.digitalocean.com/community/tutorials/how-to-use-ejs-to-template-your-node-application)

[https://burning-camp.tistory.com/4](https://burning-camp.tistory.com/4)

# 시작

## NoSQL

`mongoDB` 세팅하고 `mongoose` 연결한 후 postman으로 JSON형식의 data를 보내 register(회원가입)이 잘 동작하는지 mongoDB compass로 확인하였음. 

user, resident schema 만들고 ObjectId 추가하여 JOIN 비슷하게 했음. 

- [ ]  (NoSQL을 MySQL에 비해 제대로 공부를 하지 않아서 그게 조인이랑 어떤 차이가 있는지 알고 넘어갔어야 함)

그런데 [https://rollbar.com/blog/javascript-typeerror-cannot-read-property-of-undefined/](https://rollbar.com/blog/javascript-typeerror-cannot-read-property-of-undefined/)

에러로 더 이상 진행하지 못함. 이미 스키마 만들고 passport 설정해서 authentication까지 구현한 상태인데도..왜냐?

1. 돌아가는지 중간중간 test를 건너뜀... 책을 보고하는 거니까 괜찮을 줄 알았음(너무 부끄럽다 이런 거 블로그에 적어도 되는지...............)
2. 내가 공부한 책이 조금 구판이라서 현재의 버전에서 돌아가지 않았음

### 교훈

<aside>
💡 
1. test를 성실히 하자. 나의 코드를 너무 믿지 말자. Test 코드 작성법을 알고 적용해보자
2. 개발 공부용 책은 되도록 전자책으로, 신판으로 사자
3. 버전 관리를 섬세히 하자.

</aside>

그래서 해당 디렉토리에 sequelize 설치해서 MySQL쓰려고 했더니, 이젠 `Cannot find module err`로 꼬여버림.

package.json이랑 기타 코드들 빼고 node_modules랑 package-lock.json 삭제하고 `npm install`하여 재설치 진행했는데도 `Cannot find module` 에러에서 벗어날 수 없었음... 경로가 단단히 꼬인 듯함 (단단씌!! 박선생!)

그냥 RDB를 사용하기로 결정함. 

1. 층장-사생 간의 관계를 나타내기에 RDB가 적합할 것 같기도 했고,
2. Sequelize를 사용해보고 싶기도 했음

sequelize 장점 링크해야지... 쿼리성능이 raw보단 떨어지지만 쿼리를 튜닝하는 수준에 못 미치는 초보자로써는 일정 성능을 낼 수 있는 sequelize가 더 낫다고 블로그에서 읽었음.

## MySQL

위의 결심을 단단히 먹고 새출발하는 마음으로 새출발을 함. 새 디렉토리에 전부 다시 설치하고 app.js랑 기본적인 코드만 작성하였음.

![두번째 first commit... 마치 마지막 첫사랑](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/424b399a-7c17-4d8f-96e6-c0fd73447dac/Untitled.png)

두번째 first commit... 마치 마지막 첫사랑

그런데도 `cannot read property`와 함께 안됨. 막막한 심정으로 강사님의 깃헙에 들어가서 app.js만 복사해서 옴. 책 신판엔 nunjucks도 포함하신듯 하여 그것도 설치함. 

띠요옹~? 잘 돌아감. 역시 **버전 체크는 매우매우 중요하다.**

*~~와 진짜 언니 없으니까 개강 전인데도 공부 너무 열심히한다. 하나도 기쁘지 않고 서글플 뿐임...~~*

# 과정

## Semantic URL

의미론적 URL이라는 뜻

쿼리스트링과 semantic URL을 비교한 글: [https://sourceflower.tistory.com/17](https://sourceflower.tistory.com/17)

semantic url을 라우팅하는 방법 : **/: 기호 + key**
semantic url의 값에 접근하는 방법 : req객체의 query객체 대신 **params객체** 사용

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c7d3c5d3-e151-4bac-93a7-f6eacb5c828e/Untitled.png)

- [ ]  나도 URL이 의미하는 바가 잘 드러나도록 설계하기 위해 URL의 동작을 정리한 표를 짜야겠다!

- `/user/:id` 가 가능하게끔 함
    
    routes/page.js
    

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d95a0651-6bee-4586-b27d-0f92a69a752f/Untitled.png)

`<a id="my-profile" href="/user/{{[user.id](http://user.id/)}}" class="btn">내 프로필</a>` 

`{{}}` 를 사용해서 layout.html를 바꿈

- [ ]  그런데 왜 `href="/user/<%= user.id %>"` 는 안됐을까??
    - EJS cannot escape ... 로 찾아보자
    
    [https://www.npmjs.com/package/ejs/v/3.1.5](https://www.npmjs.com/package/ejs/v/3.1.5) 일단 얘를 읽어보자...