# Change log
###Index page
+ remove google font
+ minify print.css and add print media 
``` 
<link rel=stylesheet type=text/css href=css/print.min.css media=print> 
```
+ instead of using style.css, I already use inline css
+ use pizzeria-index.jpg (compressed )instead of pizzeria.jpg image size reduce 2 mb to 2.8kb.
+ add async to javaScript
```
<script src=js/perfmatters.js async></script>
```
+ reform Script code into 
```
(function(w,g){w['GoogleAnalyticsObject']=g;
      w[g]=w[g]||function(){(w[g].q=w[g].q||[]).push(arguments)};w[g].l=1*new Date();})(window,'ga');
      ga('create', 'UA-XXXX-Y');
      ga('send', 'pageview') 
``` 
+ minify index.html and perfmatters.js files

### pizza.html
+ reform  function changePizzaSizes(size) into and pizza slider become fast:
```
  function changePizzaSizes(size) {
    switch(size) {
        case "1":
          newwidth = 25;
          break;
        case "2":
          newwidth = 33.3;
          break;
        case "3":
          newwidth = 50;
          break;
        default:
          console.log("bug in sizeSwitcher");
      }
    
    var randomPizzas = document.querySelectorAll(".randomPizzaContainer");
    for (var i = 0; i < randomPizzas.length; i++) {
      randomPizzas[i].style.width = newwidth+"%";
    }
  }
```
+  Reform function updatePositions() by let scrollTop outside of for loop :
```
function updatePositions() {
  frame++;
  window.performance.mark("mark_start_frame");
  var items = document.querySelectorAll('.mover');
  // document.body.scrollTop is no longer supported in Chrome.
  var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;
  for (var i = 0; i < items.length; i++) {
    var phase = Math.sin((scrollTop / 1250) + (i % 5));
    items[i].style.left = items[i].basicLeft + 100 * phase + 'px';
  }  
```  
+  Add will change into mover class inside style.css 
```
.mover {
  position: fixed;
  width: 256px;
  z-index: -1;
  will-change: transform;
} 
``` 


 