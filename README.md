<!DOCTYPE html>
<html>
<head>
	<title>Self Network | search.selfnetwork/</title>
	<style>
		body {
			margin: 0;
			padding: 0;
			text-align: left;
		}

		form {
			display: inline-block;
			margin-top: 20px;
			margin-bottom: 20px;
			text-align: left;
		}

		h1 {
			text-align: left;
		}

		h2 {
			text-align: left;
		}

		label {
			display: block;
			margin-bottom: 10px;
		}

		input[type="text"] {
			display: block;
			margin-bottom: 10px;
			padding: 5px;
			border-radius: 5px;
			border: 1px solid #ccc;
			width: 200px;
		}

		button[type="submit"] {
			display: block;
			padding: 5px 10px;
			border-radius: 5px;
			border: none;
			background-color: #0077cc;
			color: #fff;
			cursor: pointer;
		}

		#output {
			margin-top: 20px;
			padding: 10px;
			border: 1px solid #ccc;
			border-radius: 5px;
			width: 400px;
			min-height: 100px;
			background-color: #f0f0f0;
			font-family: monospace;
			white-space: pre-wrap;
			word-wrap: break-word;
		}
	</style>
</head>

<body>
	<script async src="https://cse.google.com/cse.js?cx=b667ff28003398517"></script>

	<form id="input-form">
		<label for="business-name">Business Name:</label>
		<input type="text" id="business-name" name="business-name"><br>

		<label for="niche">Niche or Topic:</label>
		<input type="text" id="niche" name="niche"><br>

		<button type="submit">Generate Insights</button>
	</form>

	<h2>Insights:</h2>
	<div id="output"></div>

	<script src="https://cdn.openai.com/sdk/js/latest.js"></script>
	<script>
		const openai = new OpenAI(Your-API-Key);

		document.getElementById("input-form").addEventListener("submit", function(event) {
			event.preventDefault();

			const businessName = document.getElementById("business-name").value;
			const niche = document.getElementById("niche").value;

			openai.complete({
				engine: 'text-davinci-002',
				prompt: `Generate insights for ${businessName} in the ${niche} niche.`,
				maxTokens: 150,
				n: 1,
				stop: '\n'
			}).then(function(response) {
				const output = response.choices[0].text;
				document.getElementById("output").innerHTML = output;
			});
		});
	</script>
</body>
</html>






