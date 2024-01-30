# Creating a Grid

### 1. Setting up a grid

- Grid container : child의 child는 grid설정이 안된다.

  ```html
  <div class="container">
    <div>Item 1</div>
    <div>
      Item 2
      <p>I'm not a grid item!</p>
    </div>
    <div>Item 3</div>
    <div>Item 4</div>
  </div>
  ```

  ```css
  .container {
    display: grid;
  }
  ```

- Columns and rows - gird-template-columns, grid-template-rows : 내가 원하는 column과 row를 지정해줄수 있는 속성

    <pre>
    <span style="color: skyblue">아래처럼 2열 2행으로 grid를 생성하였다. 여기에 추가적으로 넣고 싶다면 grid-template에 사이즈만 더 넣어주면 된다.</span>
    <code>
    예시1
    <div class="container" style="display: grid; grid-template-columns: 50px 50px; grid-template-rows: 50px 50px">
      <div>Item 1</div>
      <div>Item 2</div>
      <div>Item 3</div>
      <div>Item 4</div>
    </div>
    예시2
    <div class="container2" style="display: grid; grid-template-columns: 50px 50px 50px; grid-template-rows: 50px 50px">
      <div>Item 1</div>
      <div>Item 2</div>
      <div>Item 3</div>
      <div>Item 4</div>
    </div>
    </code>
    </pre>

- Shorthand 버전(grid-template : [rows] / [columns])

  ```html
  <div
    class="container"
    style="display: grid; grid-template: 50px 50px / 50px 50px"
  >
    <div>Item 1</div>
    <div>Item 2</div>
    <div>Item 3</div>
    <div>Item 4</div>
  </div>
  ```

  <pre>
  <code>
    <div
        class="container"
        style="display: grid; grid-template: 50px 50px / 50px 50px"
      >
        <div>Item 1</div>
        <div>Item 2</div>
        <div>Item 3</div>
        <div>Item 4</div>
      </div>
  </code>
  </pre>

- gap

<br/>

# Positioning Grid Elements

### 1. Lines

- Grid Line은 grid를 만들 때 내부적으로 생성되는데, 왼쪽 위의 기준으로 1로 시작한다.(가로 1,2,3,... 세로 1,2,3,...)

- Grid Line은 grid items을 위치시키는데 사용된다.

### 2. Positioning

```html
<!DOCTYPE html>
<html lang="en-US">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>My test page</title>
    <link href="./index.css" rel="stylesheet" />
  </head>
  <body>
    <div class="container">
      <div class="room" id="living-room">Living Room</div>
      <div class="room" id="kitchen">Kitchen</div>
      <div class="room" id="bedroom">Bedroom</div>
      <div class="room" id="bathroom">Bathroom</div>
      <div class="room" id="closet">Closet</div>
    </div>
  </body>
</html>
```

```css
.container {
  display: inline-grid;
  grid-template: 80px 80px 80px 80px 80px/ 80px 80px 80px 80px 80px;
  background-color: wheat;
}

.room {
  border: 1px solid;
  font-size: 50%;
  text-align: center;
}

#living-room {
  grid-column-start: 1;
  grid-column-end: 6;
  grid-row-start: 1;
  grid-row-end: 3;
}

#kitchen {
  grid-column: 4 / 6;
  grid-row: 3/6;
}

#bedroom {
  grid-column: 2/4;
  grid-row: 3/5;
}

#bathroom {
  grid-column: 1/2;
  grid-row: 3/6;
}

#closet {
  grid-column: 2/4;
  grid-row: 5/6;
}
```

<pre>
위의 css에서 grid-column과 grid-row를 이용해 방을 만들어 보았다.
<code>
<head><link href="./index.css" rel="stylesheet" /></head>
  <body>
    <div class="container">
      <div class="room" id="living-room">Living Room</div>
      <div class="room" id="kitchen">Kitchen</div>
      <div class="room" id="bedroom">Bedroom</div>
      <div class="room" id="bathroom">Bathroom</div>
      <div class="room" id="closet">Closet</div>
    </div>
  </body>
</html>
</code>
</pre>

### 3. grid-area

- grid-column과 grid-row를 합쳐 놓은 것이 grid-area이다
- grid-area : [grid-row-start] / [grid-column-start] / [grid-row-end] / [grid-column-end]

  ```css
  #living-room {
    grid-area: 1/1/3/6;
  }
  ```

- 이렇게도 사용할 수 있지만, string을 사용해 grid를 설정할 수 있다.

```css
.container {
  display: inline-grid;
  grid-template: 40px 40px 40px 40px 40px/40px 40px 40px 40px 40px;
  grid-template-areas: "a a a a a" "a a a a a" "b b c d d" "b b c d d" "e e c d d" ". . . . .";
}

.item-a {
  grid-area: a;
}
```

- 추가적으로 ' . ' 을 사용해서 빈 곳이라는 의미를 부여해줄 수 있다.

<br/>

# Advanced Grid Properties

### 1. Repeat

- repeat() : 각각의 트랙 사이즈를 지정해줄 필요 없이 우리가 원하는 매뉴얼로 편하게 생성해주기 위해 사용하는 함수.

```css
/* 예를 들어 원래는 이렇게 grid를 생성하였다면,*/
.grid-container {
  grid-template-rows: 150px 150px;
  grid-template-columns: 150px 150px 150px 150px 150px;
}

/* 반복적인 작업은 'repeat' 함수를 사용해서 아래와 같이 생성할 수 있다.*/

.grid-container {
  grid-template-rows: repeat(2, 150px);
  grid-template-columns: repeat(5, 150px);
}
```

<pre>
<code>
<div style="resize: both;
  overflow: auto;
  display: grid;
  gap: 4px;
  padding: 4px;
  border: 1px solid grey;
  background-color: skyblue;
  grid-template-rows: repeat(2, 150px);
  grid-template-columns: repeat(5, 150px);">
      <div class="grid-item">
        <p>Odin 1</p>
      </div>
      <div class="grid-item">
        <p>Odin 2</p>
      </div>
      <div class="grid-item">
        <p>Odin 3</p>
      </div>
      <div class="grid-item">
        <p>Odin 4</p>
      </div>
      <div class="grid-item">
        <p>Odin 5</p>
      </div>
      <div class="grid-item">
        <p>Odin 6</p>
      </div>
      <div class="grid-item">
        <p>Odin 7</p>
      </div>
      <div class="grid-item">
        <p>Odin 8</p>
      </div>
      <div class="grid-item">
        <p>Odin 9</p>
      </div>
      <div class="grid-item">
        <p>Odin 10</p>
      </div>
    </div>
</code>
</pre>

### 2. Fractional units(fr) - grid를 dynamic(flexible)하게 만들 수 있는 단위.

- fr은 grid에 남은 공간을 분배하는 방법이다. 예를 들어, 400px의 고정된 크기의 너비와 4열의 grid가 있을 경우, 1fr은 100px씩 나뉘어 질것이다.
- 이전 예에선 150px씩 고정적으로 나뉘었다면, 1fr을 사용했을 땐 <span style="font-weight:bold; color:skyblue;">1/전체너비</span> 로 나뉘어 진다.

<pre>
<code>
<div style="resize: both;
  overflow: auto;
  display: grid;
  gap: 4px;
  padding: 4px;
  border: 1px solid grey;
  background-color: skyblue;
  grid-template-rows: repeat(2, 1fr);
  grid-template-columns: repeat(5, 1fr);">
      <div class="grid-item">
        <p>Odin 1</p>
      </div>
      <div class="grid-item">
        <p>Odin 2</p>
      </div>
      <div class="grid-item">
        <p>Odin 3</p>
      </div>
      <div class="grid-item">
        <p>Odin 4</p>
      </div>
      <div class="grid-item">
        <p>Odin 5</p>
      </div>
      <div class="grid-item">
        <p>Odin 6</p>
      </div>
      <div class="grid-item">
        <p>Odin 7</p>
      </div>
      <div class="grid-item">
        <p>Odin 8</p>
      </div>
      <div class="grid-item">
        <p>Odin 9</p>
      </div>
      <div class="grid-item">
        <p>Odin 10</p>
      </div>
    </div>
</code>
</pre>

<br/>

- 위와 다르게 fr을 다르게 주어서 비균등하게 grid를 설정해줄수도 있다.

<pre>
<code>
<div style="resize: both;
  overflow: auto;
  display: grid;
  gap: 4px;
  padding: 4px;
  border: 1px solid grey;
  background-color: skyblue;
  grid-template-rows: repeat(2, 1fr);
  grid-template-columns: repeat(2, 2fr) repeat(3, 1fr);">
      <div class="grid-item">
        <p>Odin 1</p>
      </div>
      <div class="grid-item">
        <p>Odin 2</p>
      </div>
      <div class="grid-item">
        <p>Odin 3</p>
      </div>
      <div class="grid-item">
        <p>Odin 4</p>
      </div>
      <div class="grid-item">
        <p>Odin 5</p>
      </div>
      <div class="grid-item">
        <p>Odin 6</p>
      </div>
      <div class="grid-item">
        <p>Odin 7</p>
      </div>
      <div class="grid-item">
        <p>Odin 8</p>
      </div>
      <div class="grid-item">
        <p>Odin 9</p>
      </div>
      <div class="grid-item">
        <p>Odin 10</p>
      </div>
    </div>
</code>
</pre>

# Using Flexbox and Grid

### 1. Contetn first vs layout first design

- content first layout 은 layout이 역동적으로 변할 가능 성이 크다.
- layout first design 은 layout을 배치할 것을 먼저 생각하고 content를 기획하기 때문에 Grid의 사용이 큰 빛을 발한다.

### 2. Combining flexbox and grid

- 1차원 콘텐츠의 경우 flexbox, 2차원 콘텐츠의 경우 grid
