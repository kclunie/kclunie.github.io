---
layout: post
title:      "Like it or Not"
date:       2020-07-21 00:35:36 +0000
permalink:  like_it_or_not
---


Like it or not, everyone likes to "like". So how do we get that much loved button up and running?

1) Create your button and add some pizzazz to it using your HTML and CSS skills.

```
<!DOCTYPE html>
<html>
<head>
<style type="text/css">
#button{
     color: black;
     font-size: 16px;
}
</style>
</head>

<body>
<p>Click on the button to like or dislike:</p>
<p type="text" id="show"></p>
<button id="button">Like</button>
</body>
</html>
```

2) Add some JavaScript for functionality. Let's show off our popularity by attaching our liking count to our p tag.

```
<script type="text/javascript">
var likes=0;
function like(){
     document.getElementById("show").innerHTML=likes;
     likes=likes+1;
}
</script>
```

3) Handle the Event. We need to get this potion in motion and actually call the function when we click the button. Once the button is clicked, like() is called.

`<button id="button" onclick="like()">Like</button>`

4) All together now. We click our button and the magic is made. It's quite likely we can like now. :)

```
<!DOCTYPE html>
<html>
<head>
<script type="text/javascript">
var likes=0;
function like(){
     document.getElementById("show").innerHTML=likes;
     likes=likes+1;
}
</script>

<style type="text/css">
#button{
     color: red;
     font-size: 26px;
}
</style>
</head>

<body>
<p>Click on the button to like or dislike:</p>
<p type="text" id="show"></p>
<button id="button" onclick="like()">Like</button>
</body>
</html>
```
