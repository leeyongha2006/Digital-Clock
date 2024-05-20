# Digital-Clock
JavaScript를 사용하여 현대식 시계 만들기

![image](https://github.com/leeyongha2006/Digital-Clock/assets/126844590/3d423bf6-5d5d-46f8-a5ad-d9f27611bc66)
### 현재 시간을 불러와 구현하는 프로그램이다

## index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta http-equiv="X-UA-Compatible" content="IE=edge">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<link rel="stylesheet" href="css/style.css">
	<link rel="shortcut icon" href="assets/favicon.png" type="image/x-icon">
	<script src="main.js"></script>
	<title>Random Password Generator</title>
</head>
<body>
  <div class="container">
	<h2>Random Password Generator</h2>
	<div class="inputBox">
    	<input type="text" name="" placeholder="Create Password" id="password" readonly="">
    	<input type="number" id="length" min="8" max="32" value="16" placeholder="Enter Number of Characters">
    	<label><input type="checkbox" id="includeLowercase" checked> Lowercase(a-z)</label>
    	<label><input type="checkbox" id="includeUppercase" checked> Uppercase(A-Z)</label>
    	<label><input type="checkbox" id="includeSymbols" checked> Symbols(@-*)</label>
    	<label><input type="checkbox" id="includeNumbers" checked> Numbers(0-9)</label>
   	 
	</div>
	<div id="btn" onclick="getPassword();">Generate Password</div>
  </div>

</body>
</html>
```

## css
```css
* {
    padding: 0;
    margin: 0;
    font-family: "sans";
    user-select: none;
  }
  
  @font-face {
    src: url("font/sans.ttf");
    font-family: "sans";
  }
  
  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    background: #19172e;
  }
  
  h2 {
    color: white;
    font-size: 2rem;
    text-align: center;
    margin-bottom: 20px;
  }
  
  .inputBox {
    width: 400px;
    background: rgba(255, 255, 255, 0.05);
    box-shadow: 0 15px 25px rgba(0, 0, 0, 0.1);
    z-index: 1000;
    border-radius: 20px;
    backdrop-filter: blur(20px);
    padding: 20px;
  }
  
  .inputBox input[type="text"],
  .inputBox input[type="number"],
  .inputBox input[type="checkbox"] {
    width: calc(100% - 20px);
    height: 40px;
    margin-bottom: 10px;
    padding: 5px;
    font-size: 1rem;
    border-radius: 5px;
    border: none;
    background: rgba(255, 255, 255, 0.1);
    color: white;
    outline: none;
  }
  .inputBox input[type="number"]::-webkit-inner-spin-button,
  .inputBox input[type="number"]::-webkit-outer-spin-button {
    appearance: none;
    margin: 0;
  }
  
  
  .inputBox label {
    color: white;
    font-size: 1rem;
    display: block;
    margin-bottom: 5px;
  }
  
  .inputBox input[type="checkbox"] {
    display: inline-block;
    width: auto;
    margin: 0 5px 0 0;
    vertical-align: middle;
  }
  
  #btn {
    cursor: pointer;
    color: #fff;
    background: #333;
    font-size: 1rem;
    padding: 10px 20px;
    border-radius: 5px;
    transition: background 0.3s ease;
    text-align: center;
    margin-top: 20px;
  }
  
  #btn:hover {
    background: #1e8e3e;
  }
  
  .name {
    text-decoration: none;
    color: white;
  }
  
  .ProjectName {
    color: white;
    text-decoration: none;
  }
```

## script
``` javascript
const words = ['seat', 'pen', 'broad', 'vapor', 'ocean',
	'red', 'plate', 'late', 'that', 'ring', 'swim', 'shown',
	'path', 'law', 'list', 'hard', 'plate', 'block', 'two',
	'pupil', 'were', 'lot', 'pay', 'would', 'tired', 'dull',
	'mud', 'sky', 'grew', 'hard', 'ill', 'frame',
	'sport', 'did', 'many', 'been', 'page', 'year', 'trail',
	'earth', 'are', 'while', 'off', 'town', 'doing', 'size',
	'steel', 'sale', 'swam', 'put', 'zero', 'week', 'mill',
	'past', 'aside', 'her', 'cent', 'box', 'fuel', 'block',
	'those', 'late', 'sun', 'map', 'silk', 'lady', 'meant',
	'still', 'shine', 'range', 'loud', 'fox', 'gate', 'slide',
	'each', 'nails', 'flag', 'exist', 'door', 'luck', 'down',
	'poem', 'depth', 'press', 'crowd', 'herd', 'drink', 'worry',
	'dried', 'dig', 'new', 'rest', 'play', 'win', 'strong'];

  function getPassword() {
  // 1. 비밀번호 길이 설정
  let length = document.getElementById('length').value;
  if (length === '') {
	length = 8;  // 기본 길이 8로 설정
  }

  // 2. 옵션 설정 (문자 포함 여부)
  const includeLowercase = document.getElementById('includeLowercase').checked;
  const includeUppercase = documentgetElementById('includeUppercase').checked;
  const includeSymbols = document.getElementById('includeSymbols').checked;
  const includeNumbers = document.getElementById('includeNumbers').checked;

  // 3. 사용 가능한 문자열 생성
  let chars = '';
  if (includeLowercase) chars += 'abcdefghijklmnopqrstuvwxyz';
  if (includeUppercase) chars += 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
  if (includeSymbols) chars += '!@#$%&';
  if (includeNumbers) chars += '0123456789';

  // 4. 비밀번호 생성
  let password = '';
  for (let i = 0; i < length; i++) {
	password += chars.charAt(Math.floor(Math.random() * chars.length));
  }

  // 5. 생성된 비밀번호 표시
  document.getElementById('password').value = password;
}
```
