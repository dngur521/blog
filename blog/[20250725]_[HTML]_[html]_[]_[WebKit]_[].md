# page01.html
```html
<!DOCTYPE html>
<!-- HTML 문서임을 선언하는 선언문 -->
<html>
    <head>
        <title>웹 문서 만들기</title>
    </head>
    <body>
        <h1>웹 개발 기초</h1>
        <p>HTML : 문서의 구조를 만든다.</p>
        <p>CSS : 문서에 디자인을 입힌다.</p>
        <p>Javascript : 이벤트 등 동작을 처리한다.</p>
    </body>
</html>

```

# page02.html
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8" />
        <meta name="description" content="html sw fullstack" />
        <!-- 검색엔진에 제공할 키워드나 설명을 설정 -->
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <!-- 화면의 폭을 기기 화면 폭에 맞게 설정. 초기 화면 배율은 100%를 유지하도록 -->
        <!-- <meta http-equiv="refresh" content="3;url=http://www.google.com" /> -->

        <title>page02.html</title>
    </head>
    <br>
        <h1>meta 태그를 이용해봅시다</h1>
        <h2><del>3초 뒤에 구글로 이동합니다.</del></h2>
        1. 여기는 몸체입니다. </br> 2. 여기도 몸체입니다. </br> 3. 여기는 몸체입니다. </br> 4. 여기도 몸체입니다.
        <p>문단을 나누고자 할 때는 p 태그를 이용합니다. p태그는 br을 2번 준 효과</p>
        <p>두 번째 문단입니다.</p>
    </body>
</html>

```

# page03_text.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <title>page03_text.html</title>
    </head>
    <br>
        <!-- block 요소 -->
        <h1>Heading 1</h1>
        <h2>Heading 2</h2>
        <h3>Heading 3</h3>
        <h4>Heading 4</h4>
        <h5>Heading 5</h5>
        <h6>Heading 6</h6>

        <!-- inline 요소 -->
        normal text입니다 <br />

        <i>italic</i> text 입니다.<br />
        <em>em text 입니다.</em> <br />
        <strong>strong text 입니다.</strong> <br />
        <b>bold text 입니다.</b> <br />
        <ins>밑줄 그은 문자 ins text</ins> 입니다. <br />
        <del>취소선 del text</del> 입니다.<br />
        <strike>strike 태그</strike> <br />
        <sup>윗첨자</sup>를 만들어요. <sub>아랫첨자</sub>를 만들어요. </br>
        <h1>2<sup>3</sup> = 8<sub>cm</sub></h1>
        <address>dngur521@naver.com</address> 
        <!-- 이메일, 웹사이트 주소, 연락처 등을 의미적으로 표시 -->
        <p>마감일은 <time datetime="2025-07-30T12:00">2025-07-30 12:00:00</time></p>
        <hr color="red"/>
        <blockquote>
            <p>
                홍길동이 말했습니다. 
                <q>삶은 스스로 만들어 가는 거야</q> <br />
                <abbr title="Hyper Text Markup Language">HTML</abbr>을 이용해서 웹문서를 만들어요
            </p>
        </blockquote>
        <hr color="blue">
        <h1>엔티티 문자</h1>
        <h1>h1태그 출력</h1>
        &lt;h1&gt; &quot;쌍따옴표입니다.
        &amp;
        &copy;<br>
        띄어&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;쓰기
    </body>
</html>

```

# page04_img.html
```html
<!DOCTYPE html>
<html>
    <head>
        <title>page04_img.html</title>
    </head>
    <body>
        <h1>이미지 태그 - img (inline 요소)</h1>
        <img src="images/bird.jpg" width="300rem" alt="새 이미지" />
        <!-- 상대 경로: 실행중인 html 파일이 있는 경로를 기준으로 퍼알을 찾는 방식 -->
        <img src="./images/dog.jpg" width="250rem" alt="강아지 이미지" />
        <!-- . : 현재 디렉토리 | .. : 상위 디렉토리 | ../../ : 2단계 상위 디렉토리 -->
        <img src="http://127.0.0.1:5500/Web_0724/images/cat.jpg" width="200rem" alt="고양이 이미지" />
        <img
            src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Google_2015_logo.svg/640px-Google_2015_logo.svg.png"
            alt="구글 로고"
            width="300rem"
        />
        <!-- 절대 경로 : 서버의 루트 디렉토리에서 시작하여 파일의 경로를 전체적으로 지정하는 방식 -->
        <hr color="red" />

        <img src="/Web_0724/images/chicken.jpg" width="250rem" alt="치킨 이미지" />
        <br />
        <figure>
            <img src="/Web_0724/images/coffee.jpg" width="200rem" />
            <figcaption>커피 사진</figcaption>
        </figure>
    </body>
</html>

```

# page05_link.html
```html
<!DOCTYPE html>
<html>
    <head>
        <title>page05_link.html</title>
    </head>
    <body>
        <h1>링크 - a 태그 (inline 요소)</h1>
        <a href="https://www.naver.com">네이버</a>
        <a href="https://www.google.com">구글</a>
        <a href="https://www.daum.net" target="_blank">다음</a>
        <!-- target="_blank" : 새로운 탭을 계속 열음 -->
        <!-- target="blank"  : 새로운 탭을 계속 하나만 열음(이미 열린 탭이 있을 시 더이상 생성 X) -->
        <hr color="red" />
        <a href="./page01.html" title="page01 웹페이지">내가 만든 문서 - page01.html</a> <br />
        <a href="./sample/test.html">내가 만든 문서 - test.html</a> <br />
        <a href="/Web_0724/page01.html" target="blank"><img src="./images/subak1.png" width="50rem" /> </a>
        <hr />
        <p id="Ch01">
            <h2>Chapter 01. HTML이란?</h2> <br />
            어쩌구 저쩌구 <br />
            [<a href="#Ch02">chapter 2장으로 이동</a>] <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
            
        </p>
        <hr />
        <p id="Ch02">
            <h2>Chapter 02. CSS란?</h2><br />
            어쩌구 저쩌구 <br />
            [<a href="#Ch01">chapter 1장으로 이동</a>] <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
            [<a href="#">Top으로 이동</a>] <br />
        </p>
    </body>
</html>

```

# page06_list.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>page06_list</title>
    </head>
    <body>
        <h1>ol태그 - 순서있는 목록태그 (block요소)</h1>
        <!-- ol태그 속성:
        [1] type  : 1 (default), A, a, I, i
        [2] start : 시작값을 지정(숫자) -->
        <ol type="i" start="3">
            <li>Facebook</li>
            <li>Instagram</li>
            <li>Linked In</li>
        </ol>

        <hr color="red" />
        <h1>ul태그 - 순서없는 목록태그 (block요소)</h1>
        <!-- ul태그 속성
        [1] type : disc(default), circle, square -->
        <ul type="square">
            <li>Facebook</li>
            <li>Instagram</li>
            <li>Linked In</li>
        </ul>

        <hr color="blue" />
        <h1>dl>dt+dd</h1>
        <h2>상품 구성</h2>
        <dl>
            <dt>선물용 사과 3kg</dt>
            <dd>소과 13 ~ 16과</dd>
            <dd>중과 10 ~ 12과</dd>

            <dt>선물용 사과 5kg</dt>
            <dd>중과 6~8과</dd>
        </dl>

        <hr color="orange" />
        <h1>중첩 리스트 (목록 안에 목록)</h1>
        <ul>
            <li>Coffee</li>
            <li>
                Tea
                <ul type="square">
                    <li>Black Tea</li>
                    <li>Green Tea</li>
                </ul>
            </li>
            <li>Milk</li>
        </ul>
    </body>
</html>

```

# page07_iframe.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>page07_iframe class="html"</title>
    </head>
    <body>
        <h1>iframe - Internal Frame (내부 프레임, block요소)</h1>
        <iframe src="sample/test.html" width="80%" height="300"></iframe>
        <hr />
        <p>외부 페이지나 동영상 등을 내장할 때 사용함</p>
        <hr color="red" />
        <iframe
            width="560"
            height="315"
            src="https://www.youtube.com/embed/TYP1gI4b-FM?si=CL--199LXduXkRlr"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            referrerpolicy="strict-origin-when-cross-origin"
            allowfullscreen
        ></iframe>
    </body>
</html>

```

# page08_table.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>page08_title.html</title>
    </head>
    <body>
        <h1>table 태그</h1>
        <!-- 3행 2열 테이블 -->
        <table border="1px" width="400px" height="150px">
            <caption>
                월별 저축액
            </caption>
            <tr>
                <th>Month</th>
                <th>Savings</th>
            </tr>
            <tr>
                <td>Jan</td>
                <td>100000원</td>
            </tr>
            <tr>
                <td>Feb</td>
                <td>200000원</td>
            </tr>
        </table>
        <hr color="red" />
        <!-- 3행 4열 테이블 -->
        <h2>친구 연락처</h2>
        <table
            border="1px"
            bordercolor="red"
            cellspacing="10px"
            cellpadding="20px"
            width="80%"
            height="200px"
            align="center"
            bgcolor="#cccccc"
            background="images/dog.jpg"
        >
            <thead>
                <tr bgcolor="cccccc" style="color: #f61111">
                    <th>번호</th>
                    <th>이름</th>
                    <th>연락처</th>
                    <th>주소</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td bgcolor="orange">1</td>
                    <td bgcolor="lightblue">홍길동</td>
                    <td background="images/bird.jpg">010-1234-5678</td>
                    <td>조선</td>
                </tr>
                <tr>
                    <td>2</td>
                    <td>김철수</td>
                    <td>010-8765-4321</td>
                    <td>구미</td>
                </tr>
                <tr>
                    <td>3</td>
                    <td>김영희</td>
                    <td>010-4321-5678</td>
                    <td>대구</td>
                </tr>
            </tbody>
        </table>
        <hr color="green" />
        <h2>col, colgroup 활용</h2>
        <table border="1px" width="400px">
            <!-- thead, tbody보다 먼저 colgroup을 기술 -->
            <colgroup>
                <col span="1" width="20%" style="background-color: lavender" />
                <!-- <col span="1" style="background-color: rgb(255, 10, 123)" /> -->
                <col span="2" width="30%" style="background-color: skyblue" />
            </colgroup>
            <thead>
                <tr>
                    <th>이름</th>
                    <th>나이</th>
                    <th>도시</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>홍길동</td>
                    <td>22</td>
                    <td>서울</td>
                </tr>
                <tr>
                    <td>김철수</td>
                    <td>23</td>
                    <td>안동</td>
                </tr>
            </tbody>
        </table>
        <br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
    </body>
</html>

```

# page09_tableSpan.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>page09_tableSpan.html</title>
    </head>
    <body>
        <h1>열병합(colspan), 행병합(rowspan)</h1>
        <h2>Left, Top 에서 span을 지정한다.</h2>
    </body>
    <!-- 3행 4열 -->
    <table border="1px" width="400px">
        <tr>
            <td colspan="3">1</td>
            <td rowspan="3">4</td>
        </tr>
        <tr>
            <td>5</td>
            <td rowspan="2">6</td>
            <td>7</td>
        </tr>
        <tr>
            <td>9</td>
            <td>11</td>
        </tr>
    </table>
    <hr color="red" />
    <iframe src="table1.html" height="300px"></iframe>
</html>

```

# page10_profile.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <title>page10_profile.html</title>
        <style>
            table {
                width: 100%;
                border-collapse: collapse;
            }
            h1 {
                text-align: center;
                text-decoration: underline;
            }
            td {
                border: 2px solid black;
                padding: 0.4rem 3rem 0.4rem 0.1rem;
            }
        </style>
    </head>
    <body>
        <h1>이&nbsp;&nbsp;&nbsp;&nbsp;력&nbsp;&nbsp;&nbsp;&nbsp;서</h1>
        <table>
            <tr>
                <td rowspan="3">1, 1</td>
                <td rowspan="2">성명</td>
                <td rowspan="2">김우혁</td>
                <td colspan="2">주민등록번호</td>
            </tr>
            <tr>
                <td colspan="2">010101-3******</td>
            </tr>
            <tr>
                <td colspan="4">생년월일 1101년 01월 01일생 (만01세)</td>
            </tr>
            <tr>
                <td>주소</td>
                <td colspan="4">경북 구미시 금오공대</td>
            </tr>
            <tr>
                <td rowspan="2">연락처</td>
                <td>집</td>
                <td>없음</td>
                <td rowspan="2">전자우편</td>
                <td rowspan="2">ddaass@naver.com</td>
            </tr>
            <tr>
                <td>핸드폰</td>
                <td>010-1234-5678</td>
            </tr>
            <tr>
                <td>호적관계</td>
                <td>호주와의 관계</td>
                <td>부</td>
                <td>호주성명</td>
                <td>김철수</td>
            </tr>
        </table>
    </body>
</html>

```

# page11_audio.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>page11_audio.html</title>
    </head>
    <body>
        <h1>멀티미디어</h1>
        <h2>오디오 재생 - audio 태그</h2>
        <audio src="assets/I_Have_A_Dream.mp3" controls="controls"></audio>
        <br />
        <audio controls loop="2" preload="metadata">
            <source src="assets/Ob-La-Di Ob-La-Da.ogg" type="audio/ogg"/>
            <source src="assets/Ob-La-Di Ob-La-Da.mp3" type="audio/mpeg"/>
            <source src="assets/Ob-La-Di Ob-La-Da.wav" type="audio/wav"/>
        </audio>
        <hr color="red" />


        <h2>object, embed 태그</h2>
        <xmp>
웹에서 PDF는 <object> <embed> <iframe> 태그를 이용
미디어는 <video></video> <audio></audio> 태그를 이용한다
        </xmp>
        <!-- <object width="600" height="400" data="assets/1_3. 웹 퍼블리싱 (BootStrap).pdf" /> -->
        <embed width="600" height="300" src="assets/1_3. 웹 퍼블리싱 (BootStrap).pdf" />
    </body>
</html>

```

# page12_video.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>page12_video.html</title>
    </head>
    <body>
        <h1>비디오 재생 - video 태그</h1>
        <video width="300px" controls preload="none" poster="./assets/animal.jpg" autoplay muted>
            <source src="assets/wildlife.mp4" type="video.mp4" />
            비디오가 지원되지 않는 브라우저 입니다.
        </video>
    </body>
</html>

```

# page13_form.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>page13_form.html</title>
    </head>
    <body>
        <h1>입력양식 form 태그</h1>
        <p>
            form태그는 사용자가 입력한 값들을 웹서버(WAS)에 전달하고자 할 때 사용한다.
            <br />
            form 태그 안에는 다양한 입력양식 (form controls => input, select, textarea, button...)
        </p>
        <hr color="red" />
        <div style="border: 1px solid red">
            <h2>게시판</h2>
            <form action="write.jsp" method="post">
                <!-- method 방식 (get 방식 => 디폴트, post 방식)
                get 방식 : URL부분에 사용자가 입력한 데이터를 포함시켜서 서베에 보낸다(?name=Tom&title=Hello)
                post 방식: URL에 노출되지 않고 데이터를 요청 데이터의 body 부분에 포함시켜(감춰서) 보낸다 -->
                <!-- write.jsp에서는 사용자가 입력한 값들을 받아서 DB에 insert하는 로직 수행 -->
                <label>작성자</label>
                <input type="text" name="name" size="60" /> <br /><br />

                <label>제 목</label>
                <input type="text" name="title" size="80" /><br /><br />

                <label>글내용</label>
                <textarea name="content" rows="7" cols="100">여기에 글내용을 작성해요</textarea> <br /><br />

                <input type="submit" value="글 쓰 기" />
                <input type="reset" value="다시쓰기" />
            </form>
        </div>
    </body>
</html>

```

# page14_formControl.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>page14_formControl.html</title>
    </head>
    <body>
        <div>
            <h1>다양한 입력 폼</h1>

            <form name="frm1" id="frm1" action="join.jsp">
                <!-- method="post" enctype="multipart/form-data" ==> 파일 업로드 시 -->
                <label for="uname">이름</label>
                <input type="text" name="userName" id="uname" /><br /><br />

                <label>사진</label>
                <input type="file" name="photo" id="photo" /><br /><br />
                <!-- 파일 업로드시에는 form의 method는 post로 지정해야 하고
                enctype속성 값을 multipart/form-data로 주어야 파일 데이터가 함께 전송된다 -->

                성별 :
                <label for="gender1"> <input type="radio" name="gender" id="gender1" value="M" checked />남자 </label>
                <label for="gender2"> <input type="radio" name="gender" id="gender2" value="F" />여자 </label>
                <br /><br />
                취미 (다중선택)
                <label for="reading"><input type="checkbox" name="hobby" id="reading" value="reading" />독서</label>
                <label for="music"
                    ><input type="checkbox" name="hobby" id="music" value="music" checked />음악감상</label
                >
                <label for="movie"><input type="checkbox" name="hobby" id="movie" value="movie" />영화감상</label>
                <br /><br />
                드롭다운 리스트 (콤보박스):
                <select name="job" id="job">
                    <option value="">::직업을 선택하세요::</option>
                    <option value="system" selected>시스템엔지니어</option>
                    <option value="frontend">프론트엔드 개발자</option>
                    <option value="backend">백엔드 개발자</option>
                </select>
                <br /><br />

                <!-- select => 단일선택. multiple 속성을 주게되면 다중선택이 되며 펼친 목록형태가 된다 -->
                사용 가능한 언어:
                <select name="lang" id="lang" multiple size="5">
                    <option value="Python">Python</option>
                    <option value="Java">Java</option>
                    <option value="HTML">HTML</option>
                    <option value="C">C</option>
                </select>
                <br /><br />
                히든필드
                <input type="hidden" name="secret" value="TopSecret" id="" />
                <!-- 사용자에게는 보이지 않고 서버에 데이터를 전달하고자 할 떄 hidden필드 이용함 -->
                <br /><br />
                <input type="submit" value="회원가입" />
                <!-- 전송버튼 -->
                <input type="reset" value="다시쓰기" />
                <!-- 리셋버튼 -->
                <input type="button" value="일반버튼" onclick="alert('안녕하세요')" />
                <!-- 일반버튼 -->
            </form>
            <hr color="red" />
            <form name="frm2" id="frm2" action="login.jsp" method="post">
                <label for="">아이디</label>
                <input type="text" name="userId" id="id" />
                <label for="passwd">비밀번호</label>
                <input type="password" name="userPwd" id="passwd" />
                <button>로그인</button>
                <!-- default는 submit타입임 -->
                <button type="reset">다시쓰기</button>
                <button type="button" onclick="location.href='http://www.naver.com'">일반버튼-네이버로 이동</button>
            </form>
        </div>
    </body>
</html>

```

# page15_fomControl.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>page15_formControl.html</title>
    </head>
    <body>
        <h1>HTML5에 추가된 입력 양식</h1>
        <form action="join.jsp" method="get">
            <fieldset>
                <legend>:::회원가입:::</legend>
                <label for="email">이메일</label>
                <input type="email" name="email" id="email" multiple placeholder="이메일 양식에 맞게 입력하세요" />
                <!-- multiple 속성을 추가하면 콤마(,) 이용해서 여러 이메일 입력 가능 -->
                <br /><br />

                홈페이지:
                <input type="url" name="homepage" id="homapage" placeholder="URL 형식" />
                <br /><br />
                연락처:
                <input type="tel" name="tel" id="tel" />
                <!-- 연락처 형태가 아니여도 에러출력은 하지 않는다
                다만 모바일 기기에서 tel타입으로 지정하면 숫자패드가 나타남 -->
                <br /><br />
                생년월일:
                <input type="date" name="birth" id="birth" />

                시분초
                <input type="time" name="birthtime" id="birthtime" />
                <br /><br />
                나이:
                <input type="number" name="age" id="age" min="1" max="150" />
                <br /><br />
                검색어:
                <input type="search" name="keyword" id="keyword" />
                <br /><br />
                RGB범위
                <input type="range" name="rgb" id="rgb" min="0" max="255" value="30" />
                <input type="color" name="cr" id="cr" value="#1144aa" />
                <br /><br />
                포장여부:
                <input type="text" name="item" id="item" list="pack" />
                <datalist id="pack">
                    <option value="package">선물 포장</option>
                    <option value="no_package">선물 포장 안함</option>
                </datalist>
                <br /><br />
                <button>회원가입</button>
                <input type="image" src="images/cat.jpg" style="width: 100px" />
                <!-- image타입 버튼은 submit 기능을 갖는다 -->
                <img src="images/bird.jpg" onclick="alert('바이바이')" />
            </fieldset>
        </form>
    </body>
</html>

```

# page16_div_span.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>page16_div_span.html</title>
        <style type="text/css">
            /* css 주석 */
            div {
                background-color: antiquewhite;
                border: 1px solid hotpink;
                width: 300px;
                height: 100px;
                margin: 5px;
            }
            span {
                display: inline-block;
                background-color: aquamarine;
                border: 1px solid navy;
                width: 200px;
                height: 80px;
                margin: 5px;
            }
        </style>
    </head>
    <body>
        <h1>공간 분할 태그(div, span)</h1>
        <h2>div : block요소</h2>
        <div>하늘</div>
        <div>땅</div>
        <div>바다</div>

        <hr color="red" />
        <h2>span: inline 요소</h2>
        <span>봄</span><span>여름</span><span>가을</span><span>겨울</span>
    </body>
</html>

```

# page17_semantic.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>page17_semantic.html</title>
        <style type="text/css">
            div {
                width: 90%;
                margin: auto;
                height: 95vh; /* viewport height : 상대적 단위 */
                border: 3px solid black;
            }
            header {
                background-color: #ddd;
                height: 10vh;
            }
            nav {
                background-color: lightblue;
                height: 7vh;
            }
            main {
                background-color: bisque;
                width: 70%;
                height: 70vh;
                float: left;
            }
            aside {
                background-color: chartreuse;
                width: 30%;
                height: 70vh;
                float: right;
            }
            footer {
                /* float를 해제 */
                clear: both;
                background-color: #ddd;
                height: 10vh;
            }
        </style>
    </head>
    <body>
        <div id="container">
            <header>Header 영역</header>
            <nav>Navigation Menu</nav>
            <main>
                <section>
                    <article>제목1</article>
                    <article>제목2</article>
                    <article>제목3</article>
                    <article>제목4</article>
                </section>
            </main>
            <aside>사이드 메뉴</aside>
            <footer>Footer 영역</footer>
        </div>
    </body>
</html>

```

# table1.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <title>Table 태그 실습 문제 1</title>
        <style>
            table,
            td,
            tr {
                border: 1px solid black;
            }
            td {
                font-weight: bold;
                text-align: center;
                padding: 5px 15px;
            }

            #one {
                background-color: pink;
            }

            #seven {
                background-color: green;
            }

            #thirteen {
                background-color: blue;
            }

            #sixteen {
                background-color: skyblue;
            }
        </style>
    </head>
    <body>
        <h1>테이블 실습</h1>
        <table>
            <tr>
                <td id="one" rowspan="2">1</td>
                <td>2</td>
                <td>3</td>
                <td>4</td>
                <td>5</td>
            </tr>
            <tr>
                <!-- <td>6</td> -->
                <td id="seven" rowspan="2">7</td>
                <td>8</td>
                <td>9</td>
                <td>10</td>
            </tr>
            <tr>
                <td>11</td>
                <!--<td>12</td>-->
                <td id="thirteen" colspan="3">13</td>
                <!--<td>14</td>
                    <td>15</td>-->
            </tr>
            <tr>
                <td id="sixteen" colspan="5">16</td>
                <!--<td>17</td>
                    <td>18</td>
                    <td>19</td>
                    <td>20</td>-->
            </tr>
        </table>
    </body>
</html>

```

# htmlSite
## index.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>TASTY COFFEE</title>
        <style>
            h1,
            div {
                text-align: center;
            }
            img {
                width: 350px;
            }
        </style>
    </head>
    <body>
        <h1>Tasty Coffee</h1>
        <div>
            <a href="index.html">Home</a> | <a href="story.html">Tasty Story</a> | <a href="menu.html">메뉴 소개</a> |
            <a href="news.html">매장 소식</a>
            <a href="map.html">카페 오는 길</a> |
            <a href="center.html">고객 센터</a>
        </div>
        <br />
        <hr color="red" width="500" size="5" />
        <br />
        <div><img src="coffee.jpg" /></div>
        <br />
        <hr color="green" width="500" size="5" />
        <br />
        <div>회사이름: 주식회사 Tasty</div>
        <div>주 소 : 서울 강남구 강남대로</div>
        <div>연락처: 02&#41;2222-3333</div>
        <div>이메일: tasty&#64;a.b.c</div>
    </body>
</html>

```
## story.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>DAILY STORY</title>
        <style>
            h1,
            h3,
            div {
                text-align: center;
            }
            img {
                width: 350px;
            }
        </style>
    </head>
    <body>
        <h1>Tasty Coffee</h1>
        <div>
            <a href="index.html">Home</a> | <a href="story.html">Tasty Story</a> | <a href="menu.html">메뉴 소개</a> |
            <a href="news.html">매장 소식</a>
            <a href="map.html">카페 오는 길</a> |
            <a href="center.html">고객 센터</a>
        </div>
        <br />
        <hr color="red" width="500" size="5" />
        <h1>DAILY STORY</h1>
        <h3>하루 한잔! 나만의 커피</h3>
        <div>
            <iframe
                width="560"
                height="315"
                src="https://www.youtube.com/embed/PIFsgs0Bilk?si=yrtnpjyE7vUSohRo"
                title="YouTube video player"
                frameborder="0"
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
                referrerpolicy="strict-origin-when-cross-origin"
                allowfullscreen
            ></iframe>
        </div>
        <br />
        <hr color="green" width="500" size="5" />
        <br />
        <div>회사이름: 주식회사 Tasty</div>
        <div>주 소 : 서울 강남구 강남대로</div>
        <div>연락처: 02&#41;2222-3333</div>
        <div>이메일: tasty&#64;a.b.c</div>
    </body>
</html>

```
## news.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>NEWS</title>
        <style>
            h1,
            h2,
            div,
            table {
                text-align: center;
            }
            table,
            tr,
            td,
            th {
                border: 1px solid black;
            }
            tr,
            td,
            th {
                padding: 1rem;
            }
            table {
                margin: 0 auto;
            }
            th {
                background-color: skyblue;
            }
        </style>
    </head>
    <body>
        <h1>Tasty Coffee</h1>
        <div>
            <a href="index.html">Home</a> | <a href="story.html">Tasty Story</a> | <a href="menu.html">메뉴 소개</a> |
            <a href="news.html">매장 소식</a>
            <a href="map.html">카페 오는 길</a> |
            <a href="center.html">고객 센터</a>
        </div>
        <br />
        <hr color="red" width="500" size="5" />
        <br />

        <div>
            <table>
                <tr>
                    <th>번호</th>
                    <th>제목</th>
                    <th>날짜</th>
                    <th>조회수</th>
                </tr>
                <tr>
                    <td>15</td>
                    <td>1호점 신메뉴 출시</td>
                    <td>2025-01-13</td>
                    <td>1100</td>
                </tr>
                <tr>
                    <td>14</td>
                    <td>2호점 블랙라벨 시럽 안내</td>
                    <td>2025-01-01</td>
                    <td>5000</td>
                </tr>
                <tr>
                    <td>13</td>
                    <td>3호점 휴점일 안내</td>
                    <td>2024-12-30</td>
                    <td>2532</td>
                </tr>
            </table>
        </div>
        <br />
        <hr color="green" width="500" size="5" />
        <br />
        <div>회사이름: 주식회사 Tasty</div>
        <div>주 소 : 서울 강남구 강남대로</div>
        <div>연락처: 02&#41;2222-3333</div>
        <div>이메일: tasty&#64;a.b.c</div>
    </body>
</html>

```
## map.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>MAP</title>
        <style>
            h1,
            div {
                text-align: center;
            }
            img {
                width: 350px;
            }
        </style>
    </head>
    <body>
        <h1>Tasty Coffee</h1>
        <div>
            <a href="index.html">Home</a> | <a href="story.html">Tasty Story</a> | <a href="menu.html">메뉴 소개</a> |
            <a href="news.html">매장 소식</a>
            <a href="map.html">카페 오는 길</a> |
            <a href="center.html">고객 센터</a>
        </div>
        <br />
        <hr color="red" width="500" size="5" />
        <div><img src="coffee2.jpg" /></div>
        <div>카페 오는 길 : 지하철 강남역 1번 출구 직진 300m H몰 옆 건물</div>
        <br />
        <hr color="green" width="500" size="5" />
        <br />
        <div>회사이름: 주식회사 Tasty</div>
        <div>주 소 : 서울 강남구 강남대로</div>
        <div>연락처: 02&#41;2222-3333</div>
        <div>이메일: tasty&#64;a.b.c</div>
    </body>
</html>

```
## center.html
```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>CENTER</title>
        <style>
            h1,
            div {
                text-align: center;
            }
            table {
                text-align: left;
                margin: 0 auto;
            }
            fieldset {
                width: 430px;
                margin: 0 auto;
                border: 1px solid #ccc;
                padding: 20px;
            }

            legend {
                text-align: left;
                padding: 0 10px;
            }
        </style>
    </head>
    <body>
        <h1>Tasty Coffee</h1>
        <div>
            <a href="index.html">Home</a> | <a href="story.html">Tasty Story</a> | <a href="menu.html">메뉴 소개</a> |
            <a href="news.html">매장 소식</a>
            <a href="map.html">카페 오는 길</a> |
            <a href="center.html">고객 센터</a>
        </div>
        <br />
        <hr color="red" width="500" size="5" />
        <div>
            <fieldset>
                <legend>고객의 소리</legend>
                <form action="">
                    <table>
                        <tr>
                            <td>성명</td>
                            <td><input type="text" /></td>
                        </tr>
                        <tr>
                            <td>연락처</td>
                            <td><input type="text" /></td>
                        </tr>
                        <tr>
                            <td>내용</td>
                            <td><textarea rows="6" cols="50"></textarea></td>
                        </tr>
                    </table>
                    <input type="submit" value="등록하기" />
                </form>
            </fieldset>
        </div>

        <br />
        <hr color="green" width="500" size="5" />
        <br />
        <div>회사이름: 주식회사 Tasty</div>
        <div>주 소 : 서울 강남구 강남대로</div>
        <div>연락처: 02&#41;2222-3333</div>
        <div>이메일: tasty&#64;a.b.c</div>
    </body>
</html>

```
