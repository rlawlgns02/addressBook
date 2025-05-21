# addressBook (주소록 프로그램)
# Flask를 이용해서 주소록 프로그램 만들기
1. 새 폴더 만들기
2. 터미널에서 가상환경 만들기 (conda기준으로 설명)
```bash
conda create -n addrBook python=3.11
```
3. 가상환경이 만들어 졌다면 가상 환경 활성화 하기
```bash
conda activate addrBook
```
VSC기준으로 파이썬 인터프리터 선택 메뉴(Ctrl + Shift + P )에서 생성한 가상환경으로 설정하기

4. Flask 설치하기
```bash
pip install flask
```
# 디렉토리 구조
```
addrBook
│
├── addbook.txt
├── app.py
├── templates\
│   └── index.html
└── static\
    └── styles.css
```
# 코드 작성
### app.py (메인파일) 만들고 코드 작성하기

app.py 코드
```python 
from flask import Flask, render_template, request, redirect
import csv

app = Flask(__name__)

# Route for the home page
@app.route('/')
def index():
    return render_template('index.html')

# Route to handle form submission
@app.route('/add', methods=['POST'])
def add_contact():
    name = request.form['pyname']
    phone = request.form['pyphone']

    # Save to addbook.txt in CSV format
    with open('addbook.txt', 'a', newline='', encoding='utf-8') as file:
        writer = csv.writer(file)
        writer.writerow([name, phone])

    return redirect('/')

if __name__ == '__main__':
    app.run(debug=True)
```
### index.html 코드 작성하기

index.html 코드

```HTML
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>주소록</title>
    <link rel="stylesheet" href="/static/styles.css">
</head>
<body>
    <div class="container">
        <h1>주소록</h1>
        <form action="/add" method="post">
            <div class="form-group">
                <label for="name">이름</label>
                <input type="text" id="name" name="pyname" placeholder="이름을 입력하세요" required>
            </div>
            
            <div class="form-group">
                <label for="phone">전화번호</label>
                <input type="tel" id="phone" name="pyphone" placeholder="전화번호를 입력하세요" required>
            </div>
            
            <button type="submit">
                연락처 추가하기
            </button>
        </form>
    </div>
</body>
</html>
```

### style.css 코드 작성하기 (필수 아님 디자인요소)
css의 경우 기능적인 요소는 없고 디자인요소기 때문에 필수 조건은 아님

```CSS
:root {
  --primary-color: #4361ee;
  --primary-hover: #3a56d4;
  --text-color: #333;
  --background-color: #f8f9fa;
  --card-bg: #ffffff;
  --border-radius: 8px;
  --box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
  --transition: all 0.3s ease;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Pretendard', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

body {
  background-color: var(--background-color);
  color: var(--text-color);
  line-height: 1.6;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  padding: 2rem;
}

.container {
  width: 100%;
  max-width: 480px;
  background-color: var(--card-bg);
  border-radius: var(--border-radius);
  box-shadow: var(--box-shadow);
  padding: 2.5rem;
  margin: 0 auto;
}

h1 {
  font-size: 2rem;
  margin-bottom: 1.5rem;
  color: var(--primary-color);
  text-align: center;
  position: relative;
}

h1::after {
  content: '';
  display: block;
  width: 50px;
  height: 3px;
  background-color: var(--primary-color);
  margin: 10px auto 0;
  border-radius: 2px;
}

.form-group {
  margin-bottom: 1.5rem;
}

label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: 500;
  font-size: 0.9rem;
  color: #555;
}

input {
  width: 100%;
  padding: 0.8rem 1rem;
  border: 1px solid #ddd;
  border-radius: var(--border-radius);
  font-size: 1rem;
  transition: var(--transition);
}

input:hover{
  outline: none;
  border-color: #b1bdf1;
  transform: translateY(-2px);
}
input:focus {
  outline: none;
  border-color: var(--primary-color);
  box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.15);
}

button {
  width: 100%;
  padding: 0.9rem;
  background-color: var(--primary-color);
  color: white;
  border: none;
  border-radius: var(--border-radius);
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: var(--transition);
  margin-top: 0.5rem;
}

button:hover {
  background-color: var(--primary-hover);
  transform: translateY(-2px);
}

button:active {
  transform: translateY(0);
}

.icon {
  margin-right: 6px;
}

@media (max-width: 520px) {
  .container {
      padding: 1.5rem;
  }
}
```
