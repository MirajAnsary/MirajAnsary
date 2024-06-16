<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<meta name="viewport" content="width=device-width, initial-scale=1">
	<title> crete password</title>
	<style type="text/css">
		*{
			font-family: verdana;

		}
		body {
    background-color: #3498db;
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}
.container {
    background-color: #ffffff;
    border-radius: 5px;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3);
    padding: 20px;
    text-align: center;
}
		form {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 10px;
}

.form-group {
    margin: 10px 0;
    width: 100%;
}

		
		
		label {
    font-weight: bold;
    margin-bottom: 5px;
    display: block;
    text-align: left;
}
		input {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 16px;
    transition: border-color 0.3s ease;
}
input:focus {
    border-color: #3498db;
    outline: none;
}
div{
	height: 600px;
	width: 600px;
	margin: 2px;
	border: 5px solid black;
	}
	</style>

</head>
<body>
	<div id="container">
	<form action=# method="post"  onsubmit="return validate()">
		<p>
			<h1 style="font-style: 30px;text-align: center;">
				Register Your Account
			<br/>
			Registion form</h1>
		</p>
		<p>
			<label for="username">Username</label>
			<input  id ="username" placeholder="username" type="text" name="username">
		</p>
		<p>
			<label for="password"> Password</label>
			<input  id ="password" placeholder="password" type="password" name="password">

		</p>
		<p>
		     <label for="corfirm-password"> Confirm Password</label>
			<input  id ="password" placeholder="password" type="password" name="password" onkeyup="check(this)">
			<error id="alert"></error>	
		</p>
		<p>

			<input id="submit" type="submit" name="submit" value="SUBMIT" style="background: green;">
		</p>

	</form>
</div>
</body>
<script type="text/javascript">
	
	var password = document.getElementById('password');
var flag = 1;

function check(elem) {
    if (elem.value.length > 0) {
        if (elem.value != password.value) {
            document.getElementById('alert').innerText = "Confirm password does not match";
            flag = 0;
        } else {
            document.getElementById('alert').innerText = "";
            flag = 1;
        }
    } else {
        document.getElementById('alert').innerText = "Please enter your confirm password";
        flag = 0;
    }
}

function validate() {
    return flag === 1;
}

</script>
</html>
