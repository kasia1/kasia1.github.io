---
title: Exclude browser from Google Analytics
---
Script below should add a Google Analytics variable called 'exclude' to your cookies, which allows hits 
from this browser to be excluded from actual traffic.

<script type="text/javascript">
setTimeout(function (){var s=function(v){
try{_gaq._getAsyncTracker()._setVar(v)}catch(e){
try{__utmSetVar(v)}catch(e){
try{pageTracker._setVar(v)}catch(e){
setTimeout(function(){s(v)},500)}}}
};s('exclude')}, 500);
</script>
