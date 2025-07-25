```html
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>page10_signup.html</title>
        <style>
            table,
            tr,
            td {
                border: none;
            }
            .title {
                text-align: right;
                background-color: #FDF6B0;
            }
            .info {
                background-color: #5CC1F1;
                width: 50%;
                font-weight: bold;
            }
            .dscr {
                color: blue;
                font-size: x-small;
                text-align: justify;
            }
            #address2 {
                width: 95%;
            }
            #phone {
                color: purple;
                font-size: x-small;
            }
            div {
                text-align: center;
            }
        </style>
    </head>
    <body>
        <form action="join.jsp">
        <table>
            <tr>
                <td class="info" colspan="3">👉 아이디(ID) 정보</td>
            </tr>
            <tr>
                <td class="title" rowspan="2">* 아이디</td>
                <td colspan="2">
                    <input name="id" id="id" type="text" required/>&nbsp;
                    <button type="button" onclick="alert('사용 가능한 아이디입니다.')">중복검사</button>
                </td>
            </tr>
            <tr>
                <td class="dscr" colspan="2"><p>(4~12자 영자/숫자 가능, 한글, 특수문자 ID는 사용할 수 없습니다.)</p></td>
            </tr>
            <tr>
                <td class="title">* 비밀번호</td>
                <td colspan="2" class="dscr">
                    <input name="pwd" id="pwd" type="password" required />&nbsp;(4~8자 이내로 만들어 주세요)
                </td>
            </tr>
            <tr>
                <td class="title">* 비밀번호 확인</td>
                <td colspan="2" class="dscr">
                    <input name="pwd2" id="pwd2" type="password" required/>&nbsp;(위 번호와 같이 입력해 주세요)
                </td>
            </tr>
            <tr>
                <td class="info" colspan="3">👉 개인정보</td>
            </tr>
            <tr>
                <td class="title">* 이름(한글)</td>
                <td colspan="2" class="dscr">
                    <input name="usrName" id="userName" type="text" required />&nbsp;(예: 박정현)
                </td>
            </tr>
            <tr>
                <td class="title">생년월일</td>
                <td colspan="2">
                    <input name="birth" id="birth" type="date" /><input type="radio" />
                </td>
            </tr>
            <tr>
                <td class="title" rowspan="2">* 주소</td>
                <td colspan="2">
                    <input name="address1" id="address1" type="text" required/>&nbsp;
                    <button type="button" onclick="alert('우편번호 찾기')">우편번호 찾기</button>
                </td>
            </tr>
            <tr>
                <td colspan="2"><input name="address2" id="address2" type="text" required /></td>
            </tr>
            <tr>
                <td class="title">* 전화번호</td>
                <td>
                    <a id="phone">&nbsp;핸드폰&nbsp;</a>
                    <input type="tel" name="tel" id="tel" required />
                    <label for="carrier1"><input type="radio" name="carrier" id="carrier1" value="skt" checked />SKT</label>
                    <label for="carrier2"><input type="radio" name="carrier" id="carrier2" value="kt" />KT</label>
                    <label for="carrier3"><input type="radio" name="carrier" id="carrier3" value="lgt" />LGT</label>
                </td>
            </tr>
            <tr>
                <td class="title">이메일</td>
                <td colspan="2"><input type="email" name="email" id="email" /></td>
            </tr>
            <tr>
                <td class="title">가입인사</td>
                <td colspan="2"><textarea name="hello" id="hello" rows="5" cols="50"></textarea></td>
            </tr>
        </table>
    </body>
    <br>
    <div>
        <input
            type="submit"
            value="&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;확인&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"
        />
        <input type="reset" value="&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;다시입력&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;" />
    </div>
    </form>
</html>

```
<!DOCTYPE html>
<html lang="ko">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>page10_signup.html</title>
        <style>
            table,
            tr,
            td {
                border: none;
            }
            .title {
                text-align: right;
                background-color: #FDF6B0;
            }
            .info {
                background-color: #5CC1F1;
                width: 50%;
                font-weight: bold;
            }
            .dscr {
                color: blue;
                font-size: x-small;
                text-align: justify;
            }
            #address2 {
                width: 95%;
            }
            #phone {
                color: purple;
                font-size: x-small;
            }
            div {
                text-align: center;
            }
        </style>
    </head>
    <body>
        <form action="join.jsp">
        <table>
            <tr>
                <td class="info" colspan="3">👉 아이디(ID) 정보</td>
            </tr>
            <tr>
                <td class="title" rowspan="2">* 아이디</td>
                <td colspan="2">
                    <input name="id" id="id" type="text" required/>&nbsp;
                    <button type="button" onclick="alert('사용 가능한 아이디입니다.')">중복검사</button>
                </td>
            </tr>
            <tr>
                <td class="dscr" colspan="2"><p>(4~12자 영자/숫자 가능, 한글, 특수문자 ID는 사용할 수 없습니다.)</p></td>
            </tr>
            <tr>
                <td class="title">* 비밀번호</td>
                <td colspan="2" class="dscr">
                    <input name="pwd" id="pwd" type="password" required />&nbsp;(4~8자 이내로 만들어 주세요)
                </td>
            </tr>
            <tr>
                <td class="title">* 비밀번호 확인</td>
                <td colspan="2" class="dscr">
                    <input name="pwd2" id="pwd2" type="password" required/>&nbsp;(위 번호와 같이 입력해 주세요)
                </td>
            </tr>
            <tr>
                <td class="info" colspan="3">👉 개인정보</td>
            </tr>
            <tr>
                <td class="title">* 이름(한글)</td>
                <td colspan="2" class="dscr">
                    <input name="usrName" id="userName" type="text" required />&nbsp;(예: 박정현)
                </td>
            </tr>
            <tr>
                <td class="title">생년월일</td>
                <td colspan="2">
                    <input name="birth" id="birth" type="date" /><input type="radio" />
                </td>
            </tr>
            <tr>
                <td class="title" rowspan="2">* 주소</td>
                <td colspan="2">
                    <input name="address1" id="address1" type="text" required/>&nbsp;
                    <button type="button" onclick="alert('우편번호 찾기')">우편번호 찾기</button>
                </td>
            </tr>
            <tr>
                <td colspan="2"><input name="address2" id="address2" type="text" required /></td>
            </tr>
            <tr>
                <td class="title">* 전화번호</td>
                <td>
                    <a id="phone">&nbsp;핸드폰&nbsp;</a>
                    <input type="tel" name="tel" id="tel" required />
                    <label for="carrier1"><input type="radio" name="carrier" id="carrier1" value="skt" checked />SKT</label>
                    <label for="carrier2"><input type="radio" name="carrier" id="carrier2" value="kt" />KT</label>
                    <label for="carrier3"><input type="radio" name="carrier" id="carrier3" value="lgt" />LGT</label>
                </td>
            </tr>
            <tr>
                <td class="title">이메일</td>
                <td colspan="2"><input type="email" name="email" id="email" /></td>
            </tr>
            <tr>
                <td class="title">가입인사</td>
                <td colspan="2"><textarea name="hello" id="hello" rows="5" cols="50"></textarea></td>
            </tr>
        </table>
    </body>
    <br>
    <div>
        <input
            type="submit"
            value="&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;확인&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"
        />
        <input type="reset" value="&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;다시입력&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;" />
    </div>
    </form>
</html>
