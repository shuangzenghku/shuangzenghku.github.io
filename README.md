<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>可操作表格</title>
    <style>
        body {
            display: flex;
            justify-content: space-around;
            align-items: flex-start;
            margin: 20px;
        }
        table {
            border-collapse: collapse;
            width: 200px;
            margin: 10px;
        }
        th, td {
            border: 1px solid #000;
            padding: 8px;
            text-align: center;
            cursor: pointer;
        }
        th {
            background-color: #f2f2f2;
        }
    </style>
</head>
<body>

    <table id="table1">
        <thead>
            <tr><th>表格1</th></tr>
        </thead>
        <tbody>
            <tr><td>行1</td></tr>
            <tr><td>行2</td></tr>
            <tr><td>行3</td></tr>
        </tbody>
    </table>

    <div>
        <button onclick="moveRow('table1', 'table2')">→</button>
        <button onclick="moveRow('table2', 'table1')">←</button>
    </div>

    <table id="table2">
        <thead>
            <tr><th>表格2</th></tr>
        </thead>
        <tbody>
            <tr><td>行A</td></tr>
            <tr><td>行B</td></tr>
        </tbody>
    </table>

    <script>
        function moveRow(fromTableId, toTableId) {
            const fromTable = document.getElementById(fromTableId);
            const toTable = document.getElementById(toTableId);
            const selectedRow = getSelectedRow(fromTable);

            if (selectedRow) {
                toTable.querySelector("tbody").appendChild(selectedRow);
            }
        }

        function getSelectedRow(table) {
            const rows = table.querySelectorAll("tbody tr");
            for (const row of rows) {
                if (row.style.backgroundColor === "yellow") {
                    row.style.backgroundColor = ""; // Reset background color
                    return row;
                }
            }
            return null;
        }

        document.querySelectorAll("table tbody tr").forEach(row => {
            row.onclick = function() {
                const isSelected = this.style.backgroundColor === "yellow";
                this.style.backgroundColor = isSelected ? "" : "yellow";
            };
        });
    </script>

</body>
</html>
