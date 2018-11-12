<html>
<head>
<script type="text/javascript">
<!--
function init() {
var arr=Array();

var ss = "";
var querys=location.search;
if(querys) {
var q = querys.replace(/^\?/,'').split('&');
for(i=0 ; i<q.length ; i++){
var pair=q[i].split('=');
// arr[pair[0]]=pair[1];
ss += pair[0] + " = " + pair[1] + "\n";
}
}
alert(ss);
}

window.onload= init;

//--></script>
</head>
<body>
</body>
</html>
