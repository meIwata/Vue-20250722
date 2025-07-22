新增一個 TodoItem.vue
template
有 DIV 包括 checkbox input 跟 文字 Label， input id 跟 checked 與 Data 做單向綁定
Label for 跟 ID 做單向綁定， label 用於顯示 label 參數

script
會有三個輸入的 props 參數， Label ， Label 必填的， done 是 boolean ，id 文字必填
Data 包括 isDone 跟 props 的 done 一樣