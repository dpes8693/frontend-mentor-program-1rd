# 第6周

- 教學
  - 本周
    - 複習 js 長時間任務，短時間任務
    - 學習 call api ?
      - 學習 `postman` 這個開發工具(認識一堆名詞)
  - 下周
    - 會有分組做教學(後端工程師進場)
    - 看一下 freeCodeCamp 學習狀況
- 公布新作業
  - 作業
    - 寫出一個網頁 call api 取資料，將JSON資訊渲染出UI (可以試著找你感興趣的API)
      - 學習 js `fetch`
        - https://ithelp.ithome.com.tw/articles/10252941
    - ex:
      - https://randomuser.me/
      - https://pokeapi.co/docs/v2#pokemon-section
      - https://cataas.com/
  - 繳交方式和之前一樣
    - 並詢問問題

## 範例程式碼

### 同步,非同步 demo code

#### setTimeout

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

#### fetch

```js
// call api 拿資料
function getUsers() {
  return fetch("https://randomuser.me/api/")
    .then((response) => {
      //console.log(response);
      return response.json();
    })
    .then((data) => {
      //console.log(data);
      return data.results;
    })
    .catch((error) => {
      console.log(`Error: ${error}`);
    });
}
async function main() {
  const response = await getUsers();
  console.log(response);
}
main();
```

## 其他資源

https://www.shubo.io/javascript-promise/

http://liubin.org/promises-book/#not-throw-use-reject