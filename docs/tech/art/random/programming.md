# Programming

## Piet

Hello World in [Piet](https://www.dangermouse.net/esoteric/piet/samples.html) with the matching pixel art by Kelly Boothby.

![piet-hello-world](_piet-hello-world.png)

Another great work of art is [Matthias Ernst](https://lutter.cc) [piet programm](https://lutter.cc/piet/) which inteprets [brainfuck](https://en.wikipedia.org/wiki/Brainfuck).

![piet-brainfuck](_piet-brainfuck.gif)

There are also attempts to write a piet program and a piet like art work.

One last great example for a piet program which I like a lot is by Richard Mitton. This program calculates an approximation of pi by dividing a circular area by the radius twice. A more accurate value can be obtained by using a bigger program and therewith circle :)

![piet_pi](_piet_pi.png)

## AllRGB

The objective of [allRGB](https://allrgb.com/) is simple: To create images with one pixel for every RGB color (16,777,216); not one color missing, and not one color twice.

[This picture](https://allrgb.com/recursive) from [yashe](https://allrgb.com/yashe) includes it's own code.

![allrgb-recursive](_allrgb-recursive.png)

## Donut

Code in the shape of a donut creating a rotating donut :)

Source:

- Original: <https://www.a1k0n.net/2006/09/15/obfuscated-c-donut.html>
- Update 1: <https://www.a1k0n.net/2006/09/20/obfuscated-c-donut-2.html>
- Update 2: <https://www.a1k0n.net/2011/07/20/donut-math.html>
- Update 3: <https://www.a1k0n.net/2021/01/13/optimizing-donut.html>

C code:

``` c
             i,j,k,x,y,o,N;
         main(){float z[1760],a
      #define R(t,x,y) f=x;x-=t*y\
   ;y+=t*f;f=(3-x*x-y*y)/2;x*=f;y*=f;
   =0,e=1,c=1,d=0,f,g,h,G,H,A,t,D;char
 b[1760];for(;;){memset(b,32,1760);g=0,
h=1;memset(z,0,7040);for(j=0;j<90;j++){
G=0,H=1;for(i=0;i<314;i++){A=h+2,D=1/(G*
A*a+g*e+5);t=G*A        *e-g*a;x=40+30*D
*(H*A*d-t*c);y=          12+15*D*(H*A*c+
t*d);o=x+80*y;N          =8*((g*a-G*h*e)
*d-G*h*a-g*e-H*h        *c);if(22>y&&y>
 0&&x>0&&80>x&&D>z[o]){z[o]=D;b[o]=(N>0
  ?N:0)[".,-~:;=!*#$@"];}R(.02,H,G);}R(
  .07,h,g);}for(k=0;1761>k;k++)putchar
   (k%80?b[k]:10);R(.04,e,a);R(.02,d,
     c);usleep(15000);printf('\n'+(
        " donut.c! \x1b[23A"));}}
          /*no math lib needed
             .@a1k0n 2021.*/
```

javascript version:

``` js
(function() {
var _onload = function() {
  var pretag = document.getElementById('d');
  var canvastag = document.getElementById('canvasdonut');
  var tmr1 = undefined, tmr2 = undefined;
  var cA=1, sA=0, cB=0, sB=1;

  var R=function(tanangle, x, y) {
    var tmp=x;
    x -= tanangle*y;
    y += tanangle*tmp;
    tmp = (3-x*x-y*y)/2;
    x *= tmp;
    y *= tmp;
    return [x, y];
  }

  var asciiframe=function() {
    var b=[];
    var z=[];
    var xy = R(.04, cA, sA);
    cA = xy[0]; sA = xy[1];
    xy = R(.02, cB, sB);
    cB = xy[0]; sB = xy[1];
    for(var k=0;k<1760;k++) {
      b[k]=k%80 == 79 ? "\n" : " ";
      z[k]=0;
    }
    var sj = 0, cj = 1;
    for(var j = 0; j < 90; j++) {
      var si = 0, ci = 1;
      for(var i = 0; i < 314; i++) {
        var h=cj + 2,
          D=1/(si*h*sA+sj*cA+5),
          t=si*h*cA-sj*sA;

        var x=0|(40+30*D*(ci*h*cB-t*sB)),
            y=0|(12+15*D*(ci*h*sB+t*cB)),
            o=x+80*y,
            N=0|(8*((sj*sA-si*cj*cA)*cB-si*cj*sA-sj*cA-ci*cj*sB));
        if(y<22 && y>=0 && x>=0 && x<79 && D>z[o]) {
          z[o]=D;
          b[o]=".,-~:;=!*#$@"[N>0?N:0];
        }
        xy = R(.02, ci, si);
        ci = xy[0]; si = xy[1];
      }
      xy = R(.07, cj, sj);
      cj = xy[0]; sj = xy[1];
    }
    pretag.innerHTML = b.join("");
  };

  window.anim1 = function() {
    if(tmr1 === undefined) {
      tmr1 = setInterval(asciiframe, 50);
    } else {
      clearInterval(tmr1);
      tmr1 = undefined;
    }
  };

  asciiframe();
}

if(document.all)
  window.attachEvent('onload',_onload);
else
  window.addEventListener("load",_onload,false);
})();
```

This is how it looks like:

![donut](_donut.gif)
