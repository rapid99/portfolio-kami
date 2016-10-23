---
layout: post
title: Progress Bars
---

Recently I was asked to create some progress bars. This task needed to be completed with using Javascript and without. I thought I'd share my code in case any one out there was wondering how to accomplish this. 

**With Javascript (and colors):**

```
<!DOCTYPE html>
<html>
<head>
  <meta name="description" content="Colored progress bar powered by Javascript">
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
  <style type="text/css">

  	.frame {
  		position: relative;
  		width: 100%;
  		height: 50px;
  		background-color: grey;
	}

	.bar {
 	 	position: absolute;
  		width: 1%;
  		height: 100%;
  		background-color: red;
	}

	button {
  		position: relative;
  		width: 100px;
  		height: 25px;
	}

	.label {
  		text-align: center;
  		line-height: 50px;
  		color: white;
	}
  </style>
</head>
<body>
  <div class="frame">
    <div class="bar">
      <div class="label">0%</div><br />
      <button onclick="moveBar()">Click Me!</button>
    </div
  </div>
  <script>
  	function moveBar(){
  		var bar = document.getElementById("bar");
  		var width = 1;
  		var interval = setInterval(fill, 30);
  
  		function fill(){
    		if (width >= 100){
      		clearInterval(interval);
    	} else {
      		width++;
      		bar.style.width = width + '%';
      		document.getElementById("label").innerHTML = width + '%';
    	}
    	if (width <= 16.66){
      		document.getElementById('bar').style.backgroundColor = "red";
    	} else if (width <= 33.32){
      		document.getElementById('bar').style.backgroundColor = "orange";
    	} else if (width <= 49.98){
      		document.getElementById('bar').style.backgroundColor = "yellow";
    	} else if (width <= 66.64){
      		document.getElementById('bar').style.backgroundColor = "green";
    	} else if (width <= 83.3){
      		document.getElementById('bar').style.backgroundColor = "blue";
    	} else if (width <= 99.96){
      		document.getElementById('bar').style.backgroundColor = "purple";
    	} else {
      		document.getElementById('bar').style.backgroundColor = "black";
    		}
  		}	
	}
  </script>
</body>
</html>
```

The advantages of using JavaScript for making progress bars are that you can fire them whenever you need them to and you have a lot more functionality available to you. However, load times will be slightly longer than a pure CSS progress bar (but there shouldn't be too much of a difference between the two).

**Only CSS:**

```
<!DOCTYPE html>
<html>
<head>
<meta name="description" content="Progress Bar Powered By CSS">
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
  <style type="text/css">

	body {
    	background-color: grey;
    	padding: 10px;
	}

	.progressbar {
    	width: 100%;
    	height: 15px;
    	background-color: white;
    	padding: 2px;
    	margin: 1em 0;
    	border: 1px black solid;
    	clear: both;
	}

	/* used http://shouldiprefix.com/#animations to detirmine prefixes */

	.fill {
    	background: green;
    	height: 15px;
    	width: 0%;
    	max-width: 100%;
    	float: left;
        -webkit-animation: move 3s 1 forwards;
    	animation: move 3s 1 forwards;
	}

	@-webkit-keyframes move { 
    	from { width: 0% }

    	to { width: 100% }
	}


	@keyframes move { 
    	from {width: 0% }

    	to { width: 100% }
	}
  </style>
</head>
<body>
  <div class="progressbar">
    <div class="fill"></div>
  </div>
</body>
</html>
```

Pure CSS progress bars are simpler than JavaScript powered progress bars. They will load quicker but have a glaring disadvantage of only firing when the page loads. Without JavaScript (or any other scripting language), you won't be able to change this. 