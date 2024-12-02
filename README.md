<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>게시물 저장 예제</title>
</head>
<body>
    <h1>게시물 저장 예제</h1>
    <form id="calcForm">
        <select id="operator">
            <option value="+">덧셈 (+)</option>
            <option value="-">뺄셈 (-)</option>
            <option value="*">곱셈 (*)</option>
            <option value="/">나눗셈 (/)</option>
        </select>
        <input type="number" id="num1" placeholder="첫 번째 숫자">
        <input type="number" id="num2" placeholder="두 번째 숫자">
        <button type="button" onclick="calculate()">계산</button>
    </form>
    <p>결과: <span id="result"></span></p>

    <h2>게시물 작성</h2>
    <input type="text" id="postTitle" placeholder="제목">
    <textarea id="postContent" placeholder="내용"></textarea>
    <button type="button" onclick="savePost()">게시물 저장</button>

    <h2>저장된 게시물</h2>
    <ul id="postsList"></ul>

    <script>
        function calculate() {
            var operator = document.getElementById('operator').value;
            var num1 = parseFloat(document.getElementById('num1').value);
            var num2 = parseFloat(document.getElementById('num2').value);
            var result;

            switch (operator) {
                case '+':
                    result = num1 + num2;
                    break;
                case '-':
                    result = num1 - num2;
                    break;
                case '*':
                    result = num1 * num2;
                    break;
                case '/':
                    if (num2 !== 0) {
                        result = num1 / num2;
                    } else {
                        result = '오류: 0으로 나눌 수 없습니다.';
                    }
                    break;
                default:
                    result = '잘못된 연산자';
            }

            document.getElementById('result').innerText = result;
        }

        function savePost() {
            var title = document.getElementById('postTitle').value;
            var content = document.getElementById('postContent').value;
            var operator = document.getElementById('operator').value;
            var num1 = parseFloat(document.getElementById('num1').value);
            var num2 = parseFloat(document.getElementById('num2').value);
            var result = document.getElementById('result').innerText;

            if (!title || !content) {
                alert("제목과 내용을 입력해 주세요.");
                return;
            }

            var post = {
                id: Date.now(),
                title: title,
                content: content,
                operator: operator,
                num1: num1,
                num2: num2,
                result: result
            };

            var posts = JSON.parse(localStorage.getItem('posts')) || [];
            posts.push(post);
            localStorage.setItem('posts', JSON.stringify(posts));

            displayPosts();
        }

        function displayPosts() {
            var posts = JSON.parse(localStorage.getItem('posts')) || [];
            var postsList = document.getElementById('postsList');
            postsList.innerHTML = '';
            posts.forEach(function (post) {
                var li = document.createElement('li');
                li.innerHTML = `<a href="#" onclick="viewPost(${post.id})">${post.title}</a>`;
                postsList.appendChild(li);
            });
        }

     함수 보기Post(id) {
     var 게시물 = JSON.parse(localStorage.getItem('posts') || [];
     var post = posts.find(게시물 => post.id === ID);
     만약 (게시물) {
     varpostDetailWindow = window.open ("", "_blank");
     postDetailWindows.document.write(')
     <html lang="ko">
     <헤드>
     <meta Charset="UTF-8">
     <title>${post.title}/<title>
     </헤드>
     <바디>
     <h1>${post.title}</h1>
     <p><strong>내용://strong> ${post.content}/p>
     <p><strong>연산:/strong>${post.operator}, <strong>첫 번째 숫자:/strong>${post.num1}, <strong>두 번째 숫자:/strong>${post.num2}, <strong>결과:/strong>${post.result}/p>
     </바디>
     </html>
     `);
     }
     }

     window.onload = 디스플레이포스트;
    </script>
</바디>
</html>
