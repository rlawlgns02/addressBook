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
# 코드 작성
## app.py (메인파일) 만들고 코드 작성하기

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
6. index.html 코드 작성하기
