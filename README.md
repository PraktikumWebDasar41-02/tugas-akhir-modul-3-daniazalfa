# tugas-akhir-modul-3-daniazalfa
tugas-akhir-modul-3-daniazalfa created by GitHub Classroom
<?php
session_start();
if(isset($_SESSION["username"]) && isset($_SESSION["password"])) {
}
?>
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>
		<form action="koneksi.php" method="POST" enctype="multipart/form-data">
			<table>
				<tr>
			<h4><img src="picture/4.png" height="50" width="50"><br>DANIA ZALFA </h4><br><br>
				<tr>
					<img alt="" src="picture/1.jpg" height="200" width="210" />
					<img alt="" src="picture/2.jpg" height="200" width="210" />
					<img alt="" src="picture/3.jpg" height="200" width="210" /><br>
					<img alt="" src="picture/2.jpg" height="200" width="210" />
					<img alt="" src="picture/1.jpg" height="200" width="210" />
					<img alt="" src="picture/3.jpg" height="200" width="210" />
				</tr>
						<tr><br>

								<input type="file" name="fileToUpload" id="fileToUpload">
                <input type="submit" value="Upload Image" name="submit">
						</tr>
					</table>
					<a href="logout.php">Logout</a>
		</body>
</html>
</form>
---------------------------------------------------
<?php
 $host = "localhost";
 $user = "root";
 $pass = "";
 $db = "ta3";
 $conn = mysqli_connect($host,$user,$pass, $db);
 ord("koneksi gagal") ;
 try{
 	$pdo = new PDO("mysql:host={$host}; dbname={$db};", $user,$pass);
 	$pdo -> setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
 }
 catch (PDOException $e){
 	print "koneksi atau query bermasalah : " . $e -> getMessage() . "<br>";
 	die();
 }
 	if (isset($POST['submit'])) {
 		$username = $_POST['username'];
 		$password = $_POST['password'];
 		$foto = $_FILES['gambar']['name'];
 		$tmp_name = $_FILES['gambar']['tmp_name'];
 		$dir_foto = "picture/";
 		$target_foto = $dir_foto . $foto;

	 	$query = $pdo -> prepare("INSERT INTO galery VALUES ('$username' , '$password',  '$foto')");
	 	$query -> execute();

 	}
?>
--------------------------------------------
<!DOCTYPE html>
<html>
<head>
	<title></title>
</head>
<body>
	<form action="form.php" method="POST">
	<table>
		<tr>
			<td>Username</td>
			<td>:</td>
			<td><input type="text" name="username"></td>
		</tr>
		<tr>
			<td>Password</td>
			<td>:</td>
			<td><input type="password" name="password"></td>
		</tr>
		<tr>
			<td></td>
			<td><input type="submit" name="login" value="Login" class="form.php"> <input type="reset" value="Batal"></td>
		</tr>
	</table>
</form>
--------------------------------------------
<?php 
session_start();
session_destroy();
header("Location: login.php");
?>
