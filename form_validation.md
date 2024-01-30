# <span style="color:#38e05b">Form Basic</span>

1. form

   - form은 사용자가 양식에서 사용 작용할 모든 입력을 묶고 있습니다.
   - form은 2개의 필수적인 속성을 받을수 있다.
     - action : form에게 처리할 데이터를 보낼 곳을 알려주는 URL값을 받음
     - method : 'GET', 'POST'

2. labels

   - label - for, input - id : <span style="color:skyblue">**id와 for은 일치해야한다.**</span>

3. **name**
   - submit할때 name : {data}로 저장시켜주기때문에 무조건 있어야하는 속성

<br/>
<br/>

# <span style="color:#38e05b">Form Validation</span>

<span style="color:skyblue">1. Required validation ( required )</span>

- 필수적으로 있어야되는 입력값이 필요한 경우(ex. 로그인)
- required 한 곳을 입력하지 않고 submit 할 경우 경고표시로 쓰라고 알려준다.

```html
<form action="#" method="get">
  <div>
    <label for="user_email">*Email :</label>
    <input type="email" id="user_email" name="user_email" required />
  </div>
  <div>
    <label for="user_password">*Password : </label>
    <input type="password" id="user_password" name="user_password" required />
  </div>
  <button type="submit">Login</button>
</form>
```

<br/>

<span style="color:skyblue">2. Text length validations ( minlength, maxlength )</span>

1.  Minimum length(minlength)

```html
<form action="#" method="get">
  <div>
    <textarea placeholder="What's happening?" minlength="3"></textarea>
  </div>
  <button type="submit">Tweet</button>
</form>
```

2.  Maximum length(maxlength)

```html
<form action="#" method="get">
  <div>
    <textarea placeholder="What's happening?" maxlength="20"></textarea>
  </div>
  <button type="submit">Tweet</button>
</form>
```

3. Combining validations
   - minlength와 maxlength를 같이 사용해서 원하는 글자 수로 지정할 수 있다.

<br/>

<span style="color:skyblue">3. Number range validations ( min, max )</span>

1.  Min validation (min)

    - `<input type="number" min=1 value=0>`

2.  Max validation
    - `<input type="number" max=10 value=0>`

- 참고사항: 숫자 외 다른 것도 range를 설정가능하다 -> [MDN'docu](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/max#syntax)

<br/>

<span style="color:skyblue">4. Pattern validations</span>

- 우편번호와 같이 특정한 패턴이 있는 형식은 그 형식에 맞게 사용해야하는데, 사용자가
  잘못 입력했을 경우 그것을 인지시켜줄 수 있는 속성(input 태그에서 사용한다.)

```html
<form action="#" method="get">
  <input
    type="text"
    id="zip_code"
    name="zip_code"
    pattern="(\d{5}([\-]\d{4})?)"
    title="Please enter a valid zip code, example: 65251"
    placeholder="65251"
    required
  />
</form>

위의 pattern에서 d(decimal)의 숫자크기를 지정해줌
```

- 추가적으로 자주 사용하는 pattern들은 미리 type속성으로 만들어져 있다.  
  `<input type="email"/>` `<input type="url"/>`

<br/>

<span style="color:skyblue">5. Styling validations</span>

- CSS에 :valid , :invalid 를 사용해 입력한 값이 적절한지 적절하지 않은지 사용자에게 알려줄 수 있다.

```html
<form action="#" method="get">
  <div>
    <label for="email">Email</label>
  </div>
  <input type="email" id="email" name="email" />

  <div>
    <label for="website">Website</label>
  </div>
  <input type="url" id="website" name="website" />

  <div>
    <button type="submit">Submit</button>
  </div>
</form>
```

```css
input {
  border: 2px solid #000;
  margin-bottom: 15px;
  padding: 5px;
  border-radius: 5px;
}

input:invalid {
  border-color: red;
}

input:valid {
  border-color: green;
}
```

<style>
input {
  border: 2px solid #000;
  margin-bottom: 15px;
  padding: 5px;
  border-radius: 5px;
}

input:invalid {
  border-color: red;
}

input:valid {
  border-color: green;
}
</style>
<form action="#" method="get">
  <div>
    <label for="email">Email</label>
    <input type="email" id="email" name="email">
    &nbsp;&emsp;&emsp;
    <label for="website">Website</label>
    <input type="url" id="website" name="website">
  </div>
</form>

## **읽어보면 좋은 사이트**

- [Regex](https://www.sitepoint.com/learn-regex/ "pattern 사용할 때 쓰는 문법")
