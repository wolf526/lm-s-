<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Xuất Danh Sách Số</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            padding: 20px;
        }
        input, button {
            margin: 5px;
            padding: 10px;
            font-size: 16px;
        }
        textarea {
            width: 80%;
            height: 200px;
            margin-top: 10px;
            font-size: 16px;
            padding: 10px;
        }
    </style>
</head>
<body>
    <h1>Xuất Danh Sách Số</h1>
    <label>Nhập số bắt đầu: <input type="number" id="start"></label><br>
    <label>Nhập số kết thúc: <input type="number" id="end"></label><br>
    <label>Nhập từ muốn viết: <input type="text" id="word"></label><br>
    <button onclick="generateList()">Tạo Danh Sách</button>
    <br>
    <textarea id="output" readonly placeholder="Danh sách sẽ hiển thị ở đây..."></textarea>
    <br>
    <button onclick="copyToClipboard()">Copy</button>
    <script>
        function generateList() {
            let start = parseInt(document.getElementById('start').value);
            let end = parseInt(document.getElementById('end').value);
            let word = document.getElementById('word').value;
            let output = document.getElementById('output');
            
            if (isNaN(start) || isNaN(end) || word.trim() === "") {
                alert("Vui lòng nhập đầy đủ thông tin!");
                return;
            }
            
            if (end - start > 1000) {
                alert("Khoảng cách giữa số bắt đầu và kết thúc không được vượt quá 1000 để tránh quá tải!");
                return;
            }
            
            let content = "";
            for (let i = start; i <= end; i++) {
                content += `${i}. ${word}\n`;
            }
            output.value = content;
        }
        
        function copyToClipboard() {
            let output = document.getElementById('output');
            output.select();
            document.execCommand("copy");
            alert("Đã copy danh sách!");
        }
    </script>
</body>
</html>
