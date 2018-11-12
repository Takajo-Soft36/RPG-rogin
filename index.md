
<html>
<head>
<meta http-equiv="content-type" content="text/html; charset=shift_jis">
<script>
function check(){
var obj=document.forms[0];
if(obj.txt.value==""){
alert("名前を入力してください。");
}else{
str1="txt="+escape(obj.txt.value);
str2="&slt="+escape(obj.slt.value);
str3="&chk=";
if(obj.chk[0].checked){str3+=escape(obj.chk[0].value);}
if(obj.chk[1].checked){str3+=escape(","+obj.chk[1].value);}
location.href="https://takajo-soft36.github.io/RPG-rogin/rog.md?"+str1+str2+str3;
}
}
</script>
</head>
<body>
<form>
名　前：
<input type="text" name="txt" value="" /><br><br>
年　齢：
<select name="slt">
<option value="10歳以下">10歳以下
<option value="10歳以下">20歳以下
</select><br><br>
ペット：
<input type="checkbox" name="chk" value="犬" checked/>犬
<input type="checkbox" name="chk" value="猫" />猫<br><br>
<input type="button" value="送信" onclick="check()"/>
</form>
</body>
</html>
