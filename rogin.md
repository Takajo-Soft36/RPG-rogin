<html>
<head>
<meta http-equiv="content-type" content="text/html; charset=shift_jis">
<script>
function getkey(key,tmp1,tmp2,xx1,xx2,xx3){
tmp1=location.search.substring(1,location.search.length)+"&";
xx1=xx2=0;
len=tmp1.length;
while(xx1<len){
xx2=tmp1.indexOf("&",xx1);
tmp2=tmp1.substring(xx1,xx2);
xx3=tmp2.indexOf("=");
if (tmp2.substring(0,xx3)==key){
return(unescape(tmp2.substring(xx3 + 1, xx2 - xx1)));
}
xx1=xx2+1;
}
return("");
}
function start(){
txt=getkey("txt");
slt=getkey("slt");
chk=getkey("chk");
str="name："+txt+"<br>nennrei："+slt+"<br>petto："+chk;
text.innerHTML=str;
}
</script>
</head>
<body onload="start()">
<table>
<tr>
<td id="text"> </td>
</tr>
</table>
</body>
</html>
