### 1.	fetching in javascript 
```bash
fetch('complete.php', {
        method: 'POST', // HTTP method
        headers: {
            'Content-Type': 'application/json', // Specify the content type
        },
        body: JSON.stringify({
            key1: 'value1',
            key2: 'value2'
        }) // Data to send
    })
    .then(response => {
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        return response.json(); // Parse JSON response
    })
    .then(data => {
        console.log('Success:', data);
    })
    .catch(error => {
        console.error('Error:', error);
    });

```

### 2. Received in php
```bash
<?php
$rawData = file_get_contents("php://input");

$data = json_decode($rawData, true);

$key1 = $data['key1'] ?? null;
$key2 = $data['key2'] ?? null;

header('Content-Type: application/json');
echo json_encode([
    'status' => 'success',
    'receivedKey1' => $key1,
    'receivedKey2' => $key2
]);
?>

```
