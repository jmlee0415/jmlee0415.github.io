## JWT(JSON Web Token)
<수정 요구> 보다 강력한 보안을 위해 JWT 사용
<br>
```javascript

//routes 폴더에서 index.js에서 jsonwebtoken을 가져와서 사용하고 싶을때 사용한다
var jwt = require('jsonwebtoken');

//쿠키에서 accessToken 라는 쿠키이름을 가져와서 token 변수에 저장한다
const token = req.cookies['accessToken'];

//토큰과 jwtSecret을 통해 검증
tokenResult = jwt.verify(token, jwtSecret)

//get으로 index 페이지를 불러올 때 사용한다
router.get("/mymap", (req, res, rows) => {               
  res.render("index", { title: "Express" });
});

// 쿠키를 출력해서 확인해보고 싶을때 사용한다
console.log(req.cookies);
// 쿠키이름이 accessToken인 값을 token 변수에 넣고 jwt_decode를 통해 토큰을 디코딩한다
var token = req.cookies['accessToken'];
var decoded = jwt_decode(token);

//헤더에 있는 쿠키값을 가져와서 jwtSecret 비밀키와 검증을 해서 인증을 한다 ? 
const token = req.headers.cookies.user
const tokenResult = jwt.verify(token, jwtSecret)
console.log(tokenResult)

// 헤더에 있는 토큰을 디코딩해서 출력한다 ?
var decodedHeader = jwt_decode(token, { header: true });
console.log(decodedHeader); 

//토큰을 디코딩해서 값을 확인한다
var token = "eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX251bSI6MSwidXNlcl9pZCI6ImVlIiwibmFtZSI6ImVlIn0.HEURm4BIXp6YogTzNPIAKu5tcHrFB9hQVhKKV157xnw";
var decoded = jwt-decode(token);
console.log(decoded);



```




