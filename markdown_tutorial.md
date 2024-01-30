# Mark Down(MD) 사용법

md preview 보는 방법 : ctrl + shift + v

1. Header (=,-)

# this is h1

## this is h2 "-----------"

2. '#'

# this is h1

## this is h2

### this is h3

#### this is h4

##### this is h5

###### this is h6

---

3. '>' blockquote

> hi
>
> > hi
> >
> > > hi

---

4. 목록
   1. 순서있는건 (1. 2. 3.)
   2. 순서 없는 건(\*, + , -)
      - 빨강
        - 노랑
          - 초록

---

5. 코드

   1. pre code /code /pre : #TODO <> 이걸 붙여야하는데 쓰면 지워져서 나중에 방법확인
   <pre>
   <code>
       <p>p hi</p>
       <div>div hi</div>
       <input type="text"/ placeholder="input">
       <button>hi</button>
   </code>
   </pre>

   2. ( ``` ) : 시작 백틱에 사용 언어를 쓰면 그 언어에 맞는 강조 표시를 넣어준다.

   ```cpp
    int a = 1;
    int b = 2;
    int c = a + b;
   ```

---

6. 수평선 ()

```
    * * *
    ***
    *****
    - - -
    -----
```

---

---

---

---

---

7. 링크

외부링크

[Google](https://google.com)

[Google](https://google.com "구글")

---

참조링크

[고글][구글]

이 [구글]을 사용하세요.

이 [구글2]도 사용해보세요

[구글]: https://google.com
[구글2]: https://google.com "구글로오세요"

---

자동 연결

외부링크 : <https://google.com>

이메일링크 : <test@googld.com>

8. 강조

   ```
    *  *  : 이탤릭
    _  _

    ** **  : 굵게
    __ __

    ~~ ~~  : 취소선
   ```

   안녕

   _안녕_

   _안녕_

   **안녕**

   **안녕**

   ~~안녕~~

9. 이미지

```
 ![Alt text](/path/to/img.jpg)
 ![Alt text](/path/to/img.jpg "optional title)
```

![Space](./space.jpg "space")

size 조절
<img src="./space.jpg" width="450px" height="300px" title="픽셀 조정" alt="우주"></img>

10. 줄바꿈(마지막 문장에서 띄어쓰기 3번 후 엔터)

3번 안띄우면
이렇게됩니다

3번 띄우고 줄을 바꿉니다.  
이렇게
