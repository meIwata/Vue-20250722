請用 Vue 3 Options API 寫一個 ToDo 新增表單元件。

點擊「新增」按鈕時，會 emit 一個 'add-todo' 事件，參數為 input 欄位的值
input 欄位使用 v-model.lazy.trim
按鈕 type 設為 submit，form 用 @submit.prevent 處理
程式碼請分成 template、script、style 三段