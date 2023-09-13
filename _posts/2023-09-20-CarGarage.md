---
title: 3 Car Garage
layout: default
description: Entering your Dream 3 Car Garage
courses: { csa: {week: 5} }
type: tangibles
---
<html>
<head>
    <title>User Data Table</title>
</head>
<body>
    <h1>User Data Table</h1>
    <table id="userDataTable" border="1">
        <tr>
            <th>Name</th>
            <th>Car 1</th>
            <th>Car 2</th>
            <th>Car 3</th>
        </tr>
    </table>
    <script>
        // Function to read and populate the table from the CSV file
        function populateTable() {
            fetch('https://raw.githubusercontent.com/EdwinKuttappi/CSABlog/main/_posts_/files/cargarage.csv')
                .then(response => response.text())
                .then(data => {
                    const rows = data.split('\n');
                    const table = document.getElementById('userDataTable');
                    //
                    for (let i = 1; i < rows.length; i++) {
                        const cells = rows[i].split(',');
                        if (cells.length === 4) {
                            const row = table.insertRow();
                            for (let j = 0; j < cells.length; j++) {
                                const cell = row.insertCell(j);
                                cell.innerHTML = cells[j];
                            }
                        }
                    }
                })
                .catch(error => console.error('Error:', error));
        }
        // Call the populateTable function when the page loads
        window.onload = populateTable;
    </script>
</body>
</html>
