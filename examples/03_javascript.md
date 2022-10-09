# Beispiel 3 - JavaScript Beispiel»

```html
<!DOCTYPE html>
<html>

<head>
	<title>JavaScript Beispiel</title>
	<script>
		function updateName() {
			let name = document.getElementById('name').value;
			let paragraph = document.getElementById('mytext');
			paragraph.innerText = `Hallo ${name}!`;
		}
	</script>
</head>

<body>
    <p id="mytext">Hallo!</p>
    <input type="text" placeholder="Dein Name" id="name" />
    <button onclick="updateName()">Klick mich!</button>
</body>

</html>
```

<a href="./03_javascript_result.html" target="_blank">Ergebnis in neuem Tab öffnen</a>

<iframe src="./03_javascript_result.html" width="100%"></iframe>
