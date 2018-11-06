<body>
<form action="#" method="post">
	<p>ID：<br>
	<input type="text" name="name" size="15"></p>
	<p>PassWard：<br>
	<input type="text" name="address" size="30"></p>
</form>
</body>
[ログイン](https://takajo-soft36.github.io/RPG-rogin/rog.md)
<!DOCTYPE HTML>
<html lang="en-US">
    <head>
        <meta charset="UTF-8">
        <title></title>
    </head>
    <body>
        <form action="">
            <textarea name="" id="input" cols="30" rows="10"></textarea>

            <textarea name="" id="a" cols="30" rows="10"></textarea>
            <textarea name="" id="b" cols="30" rows="10"></textarea>
            <textarea name="" id="c" cols="30" rows="10"></textarea>
        </form>
        <script src="https://code.jquery.com/jquery-2.1.4.min.js"></script>
        <script type="text/javascript">
            $(function () {
                $("#input").on("keyup change", function () {
                    $("#a,#b,#c").val($(this).val());
                });
            });
        </script>
    </body>
</html>
