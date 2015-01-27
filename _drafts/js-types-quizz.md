---
layout: post
category : script
tagline: "An up to date review of the Gang of Four classic"
tags : [perl, script]
---

{% include JB/setup %}

<link href="http://maxcdn.bootstrapcdn.com/bootstrap/3.3.1/css/bootstrap.min.css" rel="stylesheet" media="screen" type="text/css">
<link href="css/style.css" rel="stylesheet" media="screen" type="text/css">
        <div class="container-fluid">
            <div id="quiz"></div>
        </div>
            <script src="js/jquery.js" type="text/javascript"></script>
            <script src="js/tabletop.js" type="text/javascript"></script>
            <script src="js/script.js" type="text/javascript"></script>

            <script type="text/javascript">
                var quiz = jQuery('#quiz').quiz('YOUR SPREADSHEET KEY GOES HERE'); //your published spreadsheet key or URL goes here
            </script>

    </body>

https://github.com/motherjones/newsquiz


    false == false
    false == 0
    false == ""
    false == "   "
    false == "0"
    false == "  0  "
    false == []
    false == [0] 
    false == [""]
    false == ["   "]
    false == ["   0   "]
    false == [[]]
    false == [[""]]
    false == [["   "]]
    false == [[0]]
    false == [["0"]]
    false == [["   0   "]]
    false != [false]
    
    false == new String()
    false == new Number()
    false == new Array()
    false == new Boolean()
    false != new Object()
    false != new Date()
    false != new RegExp()
    
    (new Boolean()).toString() == "false"
    new Boolean(false) == false
    new Boolean("") == false
    new Boolean(0) == false
    new Boolean(null) == false
    new Boolean(undefined) == false
    new Boolean("0") != false
    new Boolean([]) != false
    new Boolean("  ") != false
    new Boolean(new Boolean()) != false
    new Boolean(new Boolean(false)) != false
    
    (new Boolean(false) && 'WTF') == 'WTF'
    if (new Boolean(false)) { 'WTF' } => 'WTF'
    
    return 
    {
        a: 2,
        b: 3
    }
    You just returned nothing instead of an object.
    
    var foo = "bar";
    return
       foo;