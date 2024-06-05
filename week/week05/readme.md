# 第5周

- 教學
  - 本周
    - 教材要看
      - freeCodeCamp 刷題
      - 監督機制 & 學習狀況回顧
    - json 處理
       - 什麼是JSON格式? 有哪些型別?
       - 實戰 List
         - 使用 JSON 將 html UI 渲染出來
  - 下周
    - JavaScript 怎麼 call API
  - 練習量不夠
    - 課堂上持續打程式
    - SOP:
      - 先自己嘗試 5 分鐘，把題目拆解打在編輯器裡
      - 真的不行再開始 google
- 公布新作業
  - 作業
    - [筆記] 學習 js 如何處理等待
      - `非同步事件(長時間任務)` `同步事件(短時間任務)` 差異
      - `Promise` `then` 怎麼用
      - `async` `await` 怎麼用
      - 注意事項
        - 🔺建議跳過 Event Loop (事件循環)🔺
  - 繳交方式和之前一樣
    - 並詢問問題

## 範例程式碼

### 使用 json 渲染 DOM

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>JSON 渲染</title>
    <style>
      ul li {
        border: black 1px solid;
        margin: 5px;
        padding: 5px;
        list-style-type: none;
        width: 50%;
        text-align: center;
      }
    </style>
  </head>
  <body>
    <h1>給一個輸入框 裡面填上 JSON 怎麼渲染出 html?</h1>
    <textarea name="" id="myTextarea" rows="10" cols="50">
[
    {
        "id": 1,
        "name": "妳好"
    },
    {
        "id": 2,
        "name": "Hi"
    }
]
    </textarea>
    <button id="parseBtn">渲染JSON</button>

    <hr />

    <ul id="cardListWrapper"></ul>
  </body>
  <script>
    // 這個範例就不使用 document.getElementById~因為主要是 demo JSON 轉換
    const parseJson = (jsonString) => {
      try {
        return JSON.parse(jsonString);
      } catch (error) {
        console.log(error);
      }
    };

    parseBtn.addEventListener("click", () => {
      // 1. 把JSON轉成 js 陣列[]
      const cardList = parseJson(myTextarea.value);
      if (!cardList) {
        // 失敗
        alert("json有問題");
      }
      console.log(cardList);
      // 2. 先找到 cardListWrapper，跑 for 生成再一口氣取代
      const arrayOfNewChildren = [];
      cardList.forEach((element) => {
        const cardText = `${element.id}-${element.name}`;
        // 生成 DOM
        const li = document.createElement("li");
        li.textContent = cardText;
        arrayOfNewChildren.push(li);
      });
      // 取代 DOM
      cardListWrapper.replaceChildren(...arrayOfNewChildren);
    });
  </script>
</html>

```


### 新作業 demo code

Promise, async, await

```js

function sleep(ms) {
  return new Promise( (resolve, reject) => {
    setTimeout(resolve, ms);
  });
}

// 使用範例
async function example() {
  console.time();
  console.log('Start');
  await sleep(2000); // 暫停2秒
  console.log('End');
  console.timeEnd();
}

example();

```

## 其他資源

https://dpes8693.notion.site/Vue-82668a88c89c440fbe743a19e0643c96?pvs=4