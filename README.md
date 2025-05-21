
# 📚 Flask 기반 주소록 프로그램

간단한 **Flask 웹 애플리케이션**을 통해 이름과 전화번호를 입력받고, 이를 `addbook.txt` 파일에 저장하는 주소록 프로그램입니다.

<br>

## 🛠 개발 환경 준비 (conda 기준)

1. 새 폴더 생성  
2. 터미널에서 가상환경 만들기  
    ```bash
    conda create -n addrBook python=3.11
    ```
3. 가상환경 활성화  
    ```bash
    conda activate addrBook
    ```
4. Visual Studio Code에서 인터프리터 선택 (Ctrl + Shift + P → Python: 인터프리터 선택 → `addrBook` 선택)  
5. Flask 설치  
    ```bash
    pip install flask
    ```

<br>

## 📁 디렉토리 구조

```
addrBook
│
├── addbook.txt              # 연락처가 저장되는 파일
├── app.py                   # Flask 애플리케이션 메인 파일
├── templates/
│   └── index.html           # 사용자 입력 폼
└── static/
    └── styles.css           # 선택적 CSS 스타일
```

<br>

## 💡 주요 기능

- 이름과 전화번호 입력 폼 제공
- 입력값을 `addbook.txt`에 CSV 형식으로 저장
- 심플한 UI와 CSS 적용

<br>

## 🚀 실행 방법

```bash
python app.py
```

성공적으로 실행되면 아래 주소로 접속할 수 있습니다:

```
http://127.0.0.1:5000
```

> ⚠️ `WARNING: This is a development server...` 메시지는 무시해도 괜찮습니다.

<br>

## 🌐 사용 예시

1. 웹 브라우저에서 실행 주소(`http://127.0.0.1:5000`) 접속  
2. 이름과 전화번호를 입력  
3. `연락처 추가하기` 버튼 클릭  
4. `addbook.txt` 파일에 입력 내용이 저장됨

<br>

## 🖼️ 실행 화면

| 실행 화면 | 터미널 실행 결과 |
|--------------|------------------|
| ![입력 화면](https://github.com/user-attachments/assets/73024b97-91ee-4d3e-b847-d107fd2184ff) | ![터미널](https://github.com/user-attachments/assets/c0e541a1-6b1c-41e0-a98f-60135cb60517) |

<br>

## 🎨 선택사항: CSS 디자인

`static/styles.css` 파일을 통해 폼 스타일링이 가능합니다.  
CSS는 필수가 아니며, 깔끔한 UI를 위한 선택적 요소입니다.

<br>

## 📄 라이선스

MIT License
