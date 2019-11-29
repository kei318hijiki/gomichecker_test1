<!DOCTYPE html>
<html lang="ja">
<head>

<!--■■■■■①【タイトル】次の「越前市」部分をあなたのまち（自治体）に直してください。■■■■■-->
<title>函館市ゴミチェッカー</title>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, minimum-scale=1, maximum-scale=1">
<meta http-equiv="X-UA-Compatible" content="IE=10">

<link rel="stylesheet" href="https://code.jquery.com/mobile/1.3.2/jquery.mobile-1.3.2.min.css" />

<script src="https://code.jquery.com/jquery-1.9.1.min.js"></script>
<script src="https://code.jquery.com/mobile/1.3.2/jquery.mobile-1.3.2.min.js"></script>
<script type="text/javascript" src="js/jquery.gomi.js"></script>

<link rel="apple-touch-icon" href="image/gomi_icon.png"/>

<script type="text/javascript">

$(window).load(function(){
	myparseXml()
});
 
function myparseXml(xml){
	$.mobile.defaultPageTransition = 'none';
	scrollTo(0,0);
	$.getinfo({xml: "xml/gomi.xml", template: "text/gomichecker.txt"},
		function (obj, map) {
			$('#myList li').remove();
			$('#myContents div').remove();
			var mycategory = $('#mysel').val();
			var myList = "", myContents = "";
			var count = $.size("gomi");
			for (var n = 0; n < count; n++) {
				if(mycategory == "全て"){
					myList += $.convert("myList", n);
					myContents += $.convert("myContents", n);
				}
				else if($.convert("mySel", n).match(mycategory)){
					myList += $.convert("myList", n);
					myContents += $.convert("myContents", n);
				}
				else{
				}
			}
			$("#myList").append(myList).listview("refresh");
			$("#home").after(myContents).page();
			$("input[data-type='search']").val("");
		},
		function (msg) { alert(msg); }
	);
}

</script>
<!--以下はGoogleAnalytics用トラッキングコード-->
<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-49329627-2', 'auto');
  ga('send', 'pageview');

</script>
<style type="text/css">

#myfix {
    padding-top : 45px;
}

#myfix form {
    position : fixed;
    top      : 130px;
    left     : 15px;
    width    : 100%;
    z-index  : 2;
}

</style>


<!--■■■■■　google analytics　■■■■■-->


</head>


<body>


<div data-role="page" id="home">

<!--★★★★★★★★★★　ここからがヘッダー　★★★★★★★★★★-->
	<div data-role="header" data-position="fixed" align="center" data-tap-toggle="false" style="min-height:115px;">
		<div><image src="image/gomicheckerimage/1_1_blue.png" width="100%" height="22" alt=""></div>
		<span style="position: absolute; top: 1px; left: 18px;"><font size="3">このゴミ、燃えるゴミだっけ？</font></span>
		<image src="image/gomicheckerimage/1_2_gomichecker.png" width="200" alt="gomichecker" align="left">

<!--■■■■■②【あなたのまち（自治体）をゴミチェッカーのロゴの部分の吹き出しに表示】 　　　　　■■■■■-->
<!--■■■■■　・次の「越前市」の部分を直してください。 　　　　　　　　　　　　　　　　　　　　■■■■■-->
<!--■■■■■　・自治体の文字数とleft:@@@px値の対応を見て書き換えてください。 　　　　　　　　　■■■■■-->
<!--■■■■■　　　2文字＝113px,3文字＝105px,4文字＝99px,5文字＝91px,6文字＝85px,7文字＝77px　　■■■■■-->
		<span style="position: absolute; top: 36px; left: 105px;"><font size="2">函館市</font></span>
<!--■■■■■※ここまで■■■■■-->

<!--■■■■■③【他言語版の「ゴミチェッカー」へのリンク】もし他の言語版が無い場合は、次の※ここまで※を消去してください。■■■■■-->
		
<!--■■■■■※ここまで■■■■■-->


		<image src="image/gomicheckerimage/1_3_search.png" width="80" alt="50onsearch">

		<select id="mysel" name="mysel" data-inline="true" onchange="myparseXml()">
			<option value="全て">全て</option>
			<option value="あ">あ行</option>
			<option value="か">か行</option>
			<option value="さ">さ行</option>
			<option value="た">た行</option>
			<option value="な">な行</option>
			<option value="は">は行</option>
			<option value="ま">ま行</option>
			<option value="や">や行</option>
			<option value="ら">ら行</option>
			<option value="わ">わ行</option>
		</select>

	</div>



<!--★★★★★★★★★★　ここからがリスト　★★★★★★★★★★-->
	<div data-role="content" id="myListview">
		<div id="myfix">
			<ul data-role="listview" id="myList" data-filter="true" data-filter-placeholder="検索ワード...（ひらがな検索対応）"></ul>
		</div>
	</div>

<!--★★★★★★★★★★　ここからがフッター　★★★★★★★★★★-->
	<div data-role="footer" data-position="fixed" align="center" data-tap-toggle="false">
<!--■■■■■④【「ゴミかれんだー」へのリンク】もし「ゴミかれんだー」を使用しない場合は、次の※ここまで※を消去してください。■■■■■-->


<!--■■■■■※ここまで※■■■■■-->

<!--■■■■■⑤【各自治体のオープンデータのポータルサイトへのリンク】次の「越前市」の部分を直してください。もしない場合は、次の※ここまで※を消去してください。■■■■■-->

<!--■■■■■※ここまで■■■■■-->

<!--■■■■■⑥【著作権表示】次の「越前市ぷらぷらぼ」の部分を直してください。■■■■■-->
		<font size="2">&copy;函館市<br>
<a href="https://www.city.hakodate.hokkaido.jp/docs/2014012100458/" target="_blank">ごみ収集日カレンダー</a></font><br>
<!--■■■■■※ここまで■■■■■-->
		<!--<font size="2">&nbsp;<a href="http://www4.ttn.ne.jp/~flowerhana/gomiindex.html" target="_blank">オリジナル版ゴミチェッカー</a></font><br>-->

<!--■■■■■⑦【最終更新日】次の「日付」の部分を直してください。■■■■■-->
		<font size="2">Last updated[2015/02/13]</font>
<!--■■■■■※ここまで■■■■■-->

	</div>

</div>


</body>

</html>
