ToDoForm.vue
```
新增 ToDoForm.vue
template
需要一個帶有 <label> 的 <form> 、一個 <input> ，以及一個 <button>

script
data 要有輸入資料 ， 輸入資料要跟 input 做雙向綁定， v-model 加上 lazy,trim
當按下新增的時候，會送出事件 資料新增 ,還有文字格式的輸入資料，接著清空輸入框
有資料輸入才會送出事件
```


ToDoItemEditForm.vue
```
新增一個 ToDoItemEditForm.vue
建立一個表單，裡面有一個 <input> 欄位，用來編輯待辦事項的名稱。
有一個「儲存」按鈕和一個「取消」按鈕

當點擊「儲存」按鈕時，元件會送出 清單編輯 事件，新的代辦事項名稱。
當點擊「取消」按鈕時，元件會送出 取消編輯 事件。
```


TodoItem.vue
```
新增一個 TodoItem.vue
template 
有 DIV 包括 checkbox input 跟 文字 Label， input id 跟 checked 與 Data 做單向綁定
Label for 跟 ID 做單向綁定， label 用於顯示 label 參數

新增「編輯」和「刪除」按鈕
當點擊「編輯」按鈕時，會切換顯示 ToDoItemEditForm 元件。
當點擊「刪除」按鈕時。發出一個 清單刪除 事件，以便更新列表。

使用 ToDoItemEditForm  
當在編輯中，不顯示 div ，改成顯示 ToDoItemEditForm

script
會有三個輸入的 props 參數， Label ， Label 必填的， done 是 boolean ，id 文字必填
Data 包括 isDone 跟 props 的 done 一樣
當 checkbox 有改變，會送出 checkbox變更 的事件，還有元件的 id 字串

ToDoItemEditForm 元件 會聽事件 清單編輯 事件，送出 清單編輯 事件，同時傳遞新的代辦事項名稱，不顯示 ToDoItemEditForm 
ToDoItemEditForm 元件 會聽事件 取消編輯 事件，不顯示 ToDoItemEditForm 

```


app.vue
```
Data 屬性新增 ToDoItems 欄位，裡面幫我新增四筆代辦事項，id 前面有前綴字 "todo-" 加上 nanoid
使用 ToDoItem 元件，並且顯示 Data 裡面的 ToDoItems
使用 ToDoForm 元件，會聽事件 資料新增 並呼叫 將資料新增到清單的方法
在 ToDoForm 下面，顯示清單完成狀況
使用 computed 屬性，會計算已完成的清單數量，與清單總數
ToDoItem 元件，會聽事件 資料改變 ，並呼叫 更新完成清單 的方法

ToDoItem 元件，會聽事件 清單完成編輯 ，並呼叫 編輯清單 的方法
ToDoItem 元件，會聽事件 清單刪除 ，並呼叫 刪除清單 的方法
```