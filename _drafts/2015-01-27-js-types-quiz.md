---
layout: post
category : script
tagline: "Test your JavaScript knowledge"
tags : [JavaScript, Quiz]
---

{% include JB/setup %}
<link href="/assets/css/quiz-style.css" rel="stylesheet" media="screen" type="text/css">
<div class="container-fluid">
    <div id="quiz"></div>
</div>
<script src="/assets/js/jquery.js" type="text/javascript"></script>
<script src="/assets/js/tabletop.js" type="text/javascript"></script>
<script src="/assets/js/script.js" type="text/javascript"></script>
<script type="text/javascript">
    var quiz = jQuery('#quiz').quiz('https://docs.google.com/spreadsheet/pub?key=0AnlYNFav-vA9dGVJdnJLZERsV1h3ZzJsNVpnellWS3c&output=html'); //your published spreadsheet key or URL goes here
</script>
