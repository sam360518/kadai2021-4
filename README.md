# kadai2021-4

自由にアプリを製作して提出してください。

<!DOCTYPE html>
<html>
<head>
	<meta charset="Shift_JIS">
	<link rel="stylesheet" href="mystyle.css">
	<script src="main.js"></script>
	<title>Sai</title>
</head>
<body>
	<p><input type="button" id="btn" value="サイコロを振る" onclick="saikoro()"></p>
	<div id="saikoro"></div>
</body>
</html>
/*
 * main.js サイコロを振るプログラム
 */
var count;	// 変化しているように見せる回数
var $id = function(id){ return document.getElementById(id); };

/*
 * サイコロを振る
 */
function shake(){
	var sai = Math.floor(Math.random() * 6) + 1;		// 1から6までの適当な数字
	sai = sai + ".png";							// 画像ファイル名生成
	$id("saikoro").innerHTML = "<img src='" + sai + "' width='64' height='64'>";
}

/*
 * サイコロを振るときのアニメーション
 */
function anime(){
	if(count > 20){	// 適当に20回ほど振る
		count = 0;
		$id("btn").disabled = "";	// ボタンを使える状態にする
		return 0;
	}
	shake();
	count++;
	setTimeout(anime, 50);	// 50ミリ秒間隔で表示切り替え
}

function saikoro(){
	count = 0;
	$id("btn").disabled = "true";	// ボタンを使用不可にする
	anime();						// サイコロアニメ開始
}

/*
 * 起動時の処理
 */
window.onload = function(){
	shake();		// 一回だけサイコロを振る
}