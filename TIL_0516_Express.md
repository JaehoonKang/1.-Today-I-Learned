# TIL 0516 Express and Web Form


### What did I learn?

- with `get` and `post` method, I can exchange data back and forth from a client and to a server.

- 

```js
!DOCTYPE html>
<html>
  <head>
    <title>Todos</title>
    <link rel="stylesheet" href="/static/index.css">
  </head>
  <body>
    <div class="main">
      <form action="/edit/<%= id %>" method="post">
        <label>제목</label>
        <input type="text" name="title" value ="<%= title %>">
        <label>내용</label>
        <textarea name="body"><%= body %></textarea>
        <button type="submit">
          전송
        </button>
        <button type="reset">
          초기화
        </button>
      </form>                            
    </div>
  </body>
</html>
```

