<title>Главная</title>
<head><a href='http://localhost:63342/main.php/main.php/'>Главная страница</a></head>
<body>
<form method="POST">
    <p>Новый текст</p>
    <p><input type="submit" name="SaveAs" value="Сохранить текст в новый файл"></p>
    <p>Существующий текст</p>
    <p>Пароль: <input type="password" maxlength="25" size="40" name="password"></p>
    <p><input type="submit" name="Open" value="Открыть"></p>
    <p><input type="submit" name="Save" value="Сохранить текст в существующий файл"></p>


<?php
$Text = NULL;
    if (isset($_POST['Open'])) {
        $id = htmlspecialchars($_GET["id"]);
        echo "Текст будет доступен по ссылке: <a href='http://localhost:63342/main.php/main.php/?id=$id'>'http://localhost:63342/main.php/main.php/?id=$id'</a>";
        $Password1 = $_POST['password'];
        $Password2 = file_get_contents("passwords/$id.txt");
        if ($Password1 == $Password2) {
            $Text = file_get_contents("texts/$id.txt");
            $_POST['Text'] = $Text;
        }
        else
        {
            $Text = 'Неверный пароль';
            $_POST['Text'] = $Text;
        }

    }

if (isset($_POST['SaveAs'])) {
    $Text = $_POST['Text'];
    $Password = $_POST['password'];
    $permitted_chars = '0123456789abcdefghijklmnopqrstuvwxyz';
    $id = substr(str_shuffle($permitted_chars), 0, 6);
    file_put_contents ( "texts/$id.txt" , $Text , FILE_USE_INCLUDE_PATH);
    file_put_contents ( "passwords/$id.txt" , $Password , FILE_USE_INCLUDE_PATH);
    echo "Текст будет доступен по ссылке: <a href='http://localhost:63342/main.php/main.php/?id=$id'>'http://localhost:63342/main.php/main.php/?id=$id'</a>" ;
}

if (isset($_POST['Save'])) {
    $Text = $_POST['Text'];
    $id = htmlspecialchars($_GET["id"]);
    file_put_contents ( "texts/$id.txt" , $Text , FILE_USE_INCLUDE_PATH);
}

?>
    <br><textarea style="width: 90%; height: 30%;" name='Text'><?php echo $Text ?></textarea></form>
</body>
