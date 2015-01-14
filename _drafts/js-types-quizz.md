---
layout: post
category : script
tagline: "An up to date review of the Gang of Four classic"
tags : [perl, script]
---

https://github.com/motherjones/newsquiz

{% include JB/setup %}

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