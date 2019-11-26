<h2>AJAX ASP/PHP 请求实例</h2>
<h3>请在下面的输入框中键入字母（A - Z）：</h3>
<form action="">
    姓氏：<input type="text" id="txt1" onkeyup="showHint(this.value)" />
</form>
<p>建议：<span id="txtHint"></span></p>
<script>
    var xmlhttp;
    function loadXMLDoc(url,cfunc) {
        if(window.XMLHttpRequest){
            xmlhttp=new XMLHttpRequest();
        }else{
            xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
        }
        xmlhttp.onreadystatechange=cfunc;
        xmlhttp.open("GET",url,true);
        xmlhttp.send();
    }
    
    function showHint(str) {
        if (str.length==0)
        {
            document.getElementById("txtHint").innerHTML="暂无推荐";
            return;
        }
        loadXMLDoc("getuser.php",function () {
            if (xmlhttp.readyState==4 && xmlhttp.status==200)
            {
                console.log(xmlhttp.responseText);
                document.getElementById("txtHint").innerHTML=xmlhttp.responseText;
            }
        });
    }
</script>