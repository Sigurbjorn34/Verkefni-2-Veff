<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=no">
<title>pusl</title>
<style>body{margin:0;background:#e0f7fa;touch-action:none}svg{width:100vw;height:100vh}.t{fill:none;stroke:#999;stroke-width:3;stroke-dasharray:5}</style>
</head>
<body>
<svg id="g" viewBox="0 0 800 600">
<circle class="t" cx="600" cy="150" r="50"/><rect class="t" x="550" y="250" width="100" height="100"/><polygon class="t" points="600,450 550,550 650,550"/>
<circle id="c" cx="150" cy="150" r="45" fill="red"/><rect id="s" x="100" y="250" width="90" height="90" fill="blue"/><polygon id="t" points="150,450 110,540 190,540" fill="green"/>
<path id="st" d="M20,0 L25,15 L40,15 L28,25 L32,40 L20,30 L8,40 L12,25 L0,15 L15,15 Z" fill="gold" transform="translate(100,50)" opacity="0"/>
<path id="o" fill="none" stroke="purple" stroke-width="4" d="" opacity="0"/><g id="ts"></g>
</svg>
<script src="https://cdn.jsdelivr.net/npm/animejs@4.5.0/dist/bundles/anime.umd.min.js"></script>
<script>
const{animate,createTimeline}=anime;let d=null,sx,sy,ps={},f=0,lt=null,c=0,ti={};
function init(){ps.c={el:document.getElementById('c'),tx:600,ty:150,ok:0};ps.s={el:document.getElementById('s'),tx:600,ty:300,ok:0};ps.t={el:document.getElementById('t'),tx:600,ty:500,ok:0};
let o=document.getElementById('o');o.setAttribute('d','M550,100 A50,50 0 1,1 650,100 A50,50 0 1,1 550,100 M550,250 h100 v100 h-100 z M550,450 L600,400 L650,450 L600,500 Z');animate(o,{strokeDashoffset:[1000,0],duration:2000,opacity:[0,1]});
let g=document.getElementById('g');g.addEventListener('pointerdown',dn);g.addEventListener('pointermove',mv);g.addEventListener('pointerup',up);g.addEventListener('pointercancel',up)}
function dn(e){e.preventDefault();f++;let i=document.createElementNS('http://www.w3.org/2000/svg','circle');i.setAttribute('r','20');i.setAttribute('cx',e.clientX);i.setAttribute('cy',e.clientY);i.setAttribute('fill','yellow');i.setAttribute('opacity','0.6');document.getElementById('ts').appendChild(i);ti[e.pointerId]=i;animate(i,{r:[10,30,10],duration:500,loop:true});
if(lt)clearTimeout(lt);lt=setTimeout(()=>{if(f>0){reset();alert('reset')}},2000);let p=pt(e);for(let id in ps){let q=ps[id];let b=q.el.getBBox();if(p.x>b.x&&p.x<b.x+b.width&&p.y>b.y&&p.y<b.y+b.height&&!q.ok){d=q;sx=p.x-(q.el.cx?q.el.cx.baseVal.value:q.el.x.baseVal.value);sy=p.y-(q.el.cy?q.el.cy.baseVal.value:q.el.y.baseVal.value);animate(q.el,{scale:1.2,duration:200});break}}if(f==2&&d)animate(d.el,{rotate:'+=45',duration:300})}
function mv(e){if(!d)return;let p=pt(e);if(d.el.tagName=='circle'){d.el.setAttribute('cx',p.x-sx+45);d.el.setAttribute('cy',p.y-sy+45)}else if(d.el.tagName=='rect'){d.el.setAttribute('x',p.x-sx);d.el.setAttribute('y',p.y-sy)}else d.el.setAttribute('transform',`translate(${p.x-sx-150},${p.y-sy-450})`);if(ti[e.pointerId]){ti[e.pointerId].setAttribute('cx',e.clientX);ti[e.pointerId].setAttribute('cy',e.clientY)}}
function up(e){f=Math.max(0,f-1);if(lt)clearTimeout(lt);if(ti[e.pointerId]){animate(ti[e.pointerId],{r:0,opacity:0,duration:300,complete:()=>ti[e.pointerId].remove()});delete ti[e.pointerId]}if(d){let cx=d.el.cx?d.el.cx.baseVal.value:(d.el.x?d.el.x.baseVal.value+45:600);let cy=d.el.cy?d.el.cy.baseVal.value:(d.el.y?d.el.y.baseVal.value+45:300);if(Math.hypot(cx-d.tx,cy-d.ty)<80){if(d.el.tagName=='circle')animate(d.el,{cx:d.tx,cy:d.ty,scale:1,duration:400});else if(d.el.tagName=='rect')animate(d.el,{x:d.tx-50,y:d.ty-50,scale:1,duration:400});else animate(d.el,{translateX:d.tx-150,translateY:d.ty-450,duration:400});d.ok=1;c++;animate(d.el,{fill:'#0f0',duration:200,direction:'alternate',loop:2});if(c>=2)win()}else{let tl=createTimeline();tl.add(d.el,{translateX:[0,10,-10,0],duration:100}).add(d.el,{rotate:[0,5,-5,0],duration:150});animate(d.el,{scale:1,duration:200})}d=null}}
function pt(e){let s=document.getElementById('g');let p=s.createSVGPoint();p.x=e.clientX;p.y=e.clientY;return p.matrixTransform(s.getScreenCTM().inverse())}
function reset(){c=0;document.getElementById('c').setAttribute('cx',150);document.getElementById('c').setAttribute('cy',150);document.getElementById('s').setAttribute('x',100);document.getElementById('s').setAttribute('y',250);document.getElementById('t').setAttribute('transform','');for(let id in ps)ps[id].ok=0;animate('#st',{opacity:0})}
function win(){let st=document.getElementById('st');st.setAttribute('opacity',1);let tl=createTimeline();tl.add(st,{translateX:[100,400,700],translateY:[50,200,50],rotate:'1turn',duration:2000}).add(st,{opacity:0,duration:500});animate(st,{d:'M20,0 L30,10 L40,0 L30,20 L40,30 L20,25 L0,30 L10,20 L0,10 L10,0 Z',duration:1000})}
init();
</script>
</body>
</html>
