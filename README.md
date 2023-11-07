# JavaScript---9---API-Call-using-fetch-
```

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Population Data</title>
</head>
<body>

<table border="1">
  <thead>
    <tr>
      <th>ID Nation</th>
      <th>Nation</th>
      <th>ID Year</th>
      <th>Population</th>
    </tr>
  </thead>
  <tbody id="populationData"></tbody>
</table>

<script>
  document.addEventListener('DOMContentLoaded', function() {

    fetch('https://api.datausa.io/api/data?drilldowns=Nation&measures=Population')
      .then(response => response.json())
      .then(data => {

        const populationData = data.data.map(entry => ({
          idNation: entry['ID Nation'],
          nation: entry['Nation'],
          idYear: entry['ID Year'],
          population: entry['Population']
        }));


        const tableBody = document.getElementById('populationData');
        populationData.forEach(entry => {
          const row = tableBody.insertRow();
          row.insertCell(0).innerText = entry.idNation;
          row.insertCell(1).innerText = entry.nation;
          row.insertCell(2).innerText = entry.idYear;
          row.insertCell(3).innerText = entry.population;
        });
      })
      .catch(error => console.error('Error fetching data:', error));
  });
</script>

</body>
</html>
```
# output
![WhatsApp Image 2023-11-07 at 11 38 57 AM (1)](https://github.com/dhinesh102004/JavaScript---10--API-Call-using-fetch-/assets/142372008/af01ca28-fe83-4f8b-a824-dbd2dbb73d0d)
