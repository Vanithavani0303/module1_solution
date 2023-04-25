<!DOCTYPE html>
<html ng-app>
<head>
	<title>Check If Too Much</title>
	<style type="text/css">
		body {
			font-family: Arial, sans-serif;
		}
		form {
			margin: 20px auto;
			width: 400px;
		}
		input[type="text"] {
			width: 100%;
			padding: 10px;
			box-sizing: border-box;
			margin-bottom: 10px;
			border: 1px solid #ccc;
			border-radius: 5px;
			font-size: 16px;
		}
		input[type="submit"] {
			background-color: #4CAF50;
			color: white;
			padding: 10px 20px;
			border: none;
			border-radius: 5px;
			cursor: pointer;
			font-size: 16px;
		}
		input[type="submit"]:hover {
			background-color: #3e8e41;
		}
		.message {
			color: red;
			font-weight: bold;
		}
	</style>
	<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.8.2/angular.min.js"></script>
	<script type="text/javascript">
		function CheckIfTooMuch() {
			var items = document.getElementById("lunch-items").value;
			if (items.trim() === "") {
				document.getElementById("message").innerHTML = "Please enter data first";
			} else {
				var itemsArray = items.split(",");
				var numItems = itemsArray.filter(function(item) { return item.trim() !== ""; }).length;
				if (numItems <= 3) {
					document.getElementById("message").innerHTML = "Enjoy!";
				} else {
					document.getElementById("message").innerHTML = "Too much!";
				}
			}
		}
	</script>
</head>
<body>
	<form>
		<label for="lunch-items">Enter comma-separated lunch items:</label>
		<input type="text" id="lunch-items" name="lunch-items" placeholder="e.g. sandwich, apple, yogurt" ng-model="lunchItems">
		<input type="button" value="Check If Too Much" ng-click="CheckIfTooMuch()">
		<p class="message" id="message"></p>
	</form>
</body>
</html>
