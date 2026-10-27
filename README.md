<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Kick the Buddy: Gussa Edition</title>
<style>
:root{--bg:#f6efe9;--ink:#2a1a17;--card:#fff;--track:#e6d8d0;--on:#ffd9cf;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#1b1210;--ink:#f7e9e2;--card:#2a1c19;--track:#3b2a26;--on:#6a2a22}}
html,body{height:100%;margin:0}
body{background:var(--bg);color:var(--ink);font-family:"Baloo 2","Trebuchet MS",system-ui,sans-serif;display:flex;justify-content:center;touch-action:manipulation;-webkit-user-select:none;user-select:none}
.app{width:100%;max-width:440px;padding:10px 12px 14px;display:flex;flex-direction:column;gap:10px}
.meter{background:var(--card);border-radius:14px;padding:8px 12px}
.row{display:flex;justify-content:space-between;font-weight:700;font-size:15px;margin-bottom:5px}
.track{height:16px;background:var(--track);border-radius:8px;overflow:hidden}
#fill{height:100%;width:0;border-radius:8px}
.stage{position:relative;height:440px;border-radius:18px;overflow:hidden;background:linear-gradient(#f3d9b4 0 78%,#a67847 78%);touch-action:manipulation;cursor:crosshair}
.stage.shake{animation:sk .5s}
@keyframes sk{0%,100%{transform:none}20%{transform:translate(-10px,6px)}40%{transform:translate(9px,-8px)}60%{transform:translate(-6px,5px)}80%{transform:translate(4px,-3px)}}
#bud{position:absolute;left:50%;bottom:14px;width:200px;height:300px;margin-left:-100px;transform-origin:50% 100%;pointer-events:none}
#bud div{position:absolute}
.leg{width:24px;height:86px;top:214px;background:#2f4a7a;border-radius:10px 10px 12px 12px}
.torso{left:55px;top:106px;width:90px;height:114px;background:#e8453c;border-radius:30px 30px 18px 18px;overflow:hidden}
.arm{width:18px;height:94px;top:116px;background:#e8453c;border-radius:9px;transform-origin:50% 8px}
.arm::after{content:"";position:absolute;bottom:-6px;left:-1px;width:20px;height:20px;border-radius:50%;background:#e0b08c}
.torso,.arm,.leg{background-image:linear-gradient(rgba(15,10,8,var(--s,0)),rgba(15,10,8,var(--s,0)))}
#head{left:42px;top:0;width:116px;height:116px;border-radius:50%;overflow:hidden;border:4px solid #e0b08c;box-sizing:border-box;transform-origin:50% 100%;background:#444}
#head img{width:100%;height:100%;object-fit:cover;display:block}
#red{position:absolute;inset:0;background:radial-gradient(circle at 50% 55%,rgba(255,30,20,.9),rgba(200,0,0,.6));mix-blend-mode:multiply;opacity:0}
#soot{position:absolute;inset:0;background:radial-gradient(circle at 50% 50%,rgba(20,15,10,.82),rgba(20,15,10,.7));opacity:0}
.cloud{position:absolute;left:50%;top:12px;transform:translateX(-50%);width:76%;background:#fff;color:#222;border-radius:44px;padding:12px 18px;text-align:center;font-weight:800;font-size:17px;line-height:1.15;box-shadow:0 3px 0 rgba(0,0,0,.12)}
.cloud::before,.cloud::after{content:"";position:absolute;background:#fff;border-radius:50%;z-index:-1}
.cloud::before{width:56px;height:56px;top:-18px;left:22px}
.cloud::after{width:68px;height:68px;top:-24px;right:30px}
.dot{position:absolute;background:#fff;border-radius:50%;left:50%;box-shadow:0 2px 0 rgba(0,0,0,.1)}
#cemo{display:block;font-size:34px}
.fx{position:absolute;pointer-events:none;margin:-30px}
.fist{font-size:70px;animation:punch .38s ease-out forwards}
@keyframes punch{0%{transform:scale(2.4) rotate(-20deg);opacity:1}60%{transform:scale(.9);opacity:1}100%{transform:scale(.7);opacity:0}}
.pow{font-weight:900;font-size:26px;color:#ffe14a;-webkit-text-stroke:1.5px #7a1010;animation:pow .5s forwards}
@keyframes pow{to{transform:translateY(-40px) scale(1.3);opacity:0}}
.knife{font-size:46px;margin:-23px;transition:transform .16s ease-in,opacity .4s}
.bomb{font-size:54px;animation:fuse .3s infinite alternate}
@keyframes fuse{to{transform:scale(1.25) rotate(8deg)}}
.boom{font-size:190px;margin:-95px;animation:boom .6s ease-out forwards}
@keyframes boom{0%{transform:scale(.2);opacity:1}60%{transform:scale(1.1);opacity:1}100%{transform:scale(1.3);opacity:0}}
.flash{position:absolute;inset:0;background:#fff;opacity:.9;pointer-events:none;animation:fl .35s forwards}
@keyframes fl{to{opacity:0}}
.tools{display:grid;grid-template-columns:repeat(4,1fr);gap:6px}
button{font:inherit;font-weight:800;border:3px solid transparent;border-radius:14px;padding:6px 4px;background:var(--card);color:var(--ink);cursor:pointer;font-size:13px;line-height:1.1}
button span{display:block;font-size:26px}
#snd{padding:0 8px;border-radius:8px;font-size:16px;border-width:2px;margin-left:6px}
.tear{position:absolute;background:#e0b08c;transition:opacity 1.2s}
.band{position:absolute;width:28px;height:11px;background:#f1cfa6;border-radius:6px;border:1px solid #c79a6a;transition:opacity 1.2s}
.band::after{content:"";position:absolute;left:10px;top:2px;width:6px;height:5px;background:#d9a877;border-radius:2px}
button[aria-pressed="true"]{background:var(--on);border-color:#e8453c}
button:focus-visible{outline:3px solid #e8453c}
@media (prefers-reduced-motion:reduce){.stage.shake,.fist,.pow,.boom,.bomb{animation-duration:.01s}}
</style>
</head>
<body>
<div class="app">
  <div class="meter">
    <div class="row"><span id="mood">Shaant 😇</span><span><span id="pct">0%</span><button id="snd" aria-label="Sound on or off">🔊</button></span></div>
    <div class="track"><div id="fill"></div></div>
  </div>
  <div class="stage" id="stage">
    <div class="cloud"><span id="cemo">😌</span><span id="ctxt">Maaro mujhe…</span></div>
    <div class="dot" style="top:84px;width:18px;height:18px;margin-left:-6px"></div>
    <div class="dot" style="top:106px;width:11px;height:11px;margin-left:-14px"></div>
    <div id="bud">
      <div class="leg" style="left:66px"></div><div class="leg" style="left:110px"></div>
      <div class="arm" id="armL" style="left:32px"></div><div class="arm" id="armR" style="left:150px"></div>
      <div class="torso" id="torso"></div>
      <div id="head"><img alt="" src="data:image/jpeg;base64,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"><div id="red"></div><div id="soot"></div></div>
    </div>
  </div>
  <div class="tools" role="group" aria-label="Weapons">
    <button data-w="punch" aria-pressed="true"><span>👊</span>Punch</button>
    <button data-w="knife" aria-pressed="false"><span>🔪</span>Knife</button>
    <button data-w="bomb" aria-pressed="false"><span>💣</span>Bomb</button>
    <button data-w="jump" aria-pressed="false"><span>🦘</span>Jump</button>
  </div>
</div>
<script>
(function(){
  var $=function(i){return document.getElementById(i)};
  var stage=$('stage'),bud=$('bud'),head=$('head'),armL=$('armL'),armR=$('armR'),
      redEl=$('red'),sootEl=$('soot'),cemo=$('cemo'),ctxt=$('ctxt'),
      fill=$('fill'),pct=$('pct'),mood=$('mood');
  function Sp(k,d){return{x:0,v:0,k:k,d:d}}
  var rot=Sp(60,5),hd=Sp(90,4),arm=Sp(70,3),ox=Sp(80,6),oy=Sp(120,8);
  function step(s,dt){s.v+=(-s.k*s.x-s.d*s.v)*dt;s.x+=s.v*dt}
  var weapon='punch',gussa=0,redness=0,soot=0,sayUntil=0,idleSet=true,last=performance.now(),lie=0,lieDir=1,fallUntil=0,punches=0,wasAir=false,lastLand=0,muted=false,AC=null;
  function ac(){if(!AC){try{AC=new (window.AudioContext||window.webkitAudioContext)()}catch(_){}}if(AC&&AC.state==='suspended')AC.resume();return AC}
  function tone(f1,f2,dur,type,vol){if(muted)return;var a=ac();if(!a)return;var o=a.createOscillator(),g=a.createGain(),n=a.currentTime;o.type=type||'sine';o.frequency.setValueAtTime(f1,n);o.frequency.exponentialRampToValueAtTime(Math.max(1,f2),n+dur);g.gain.setValueAtTime(vol||.3,n);g.gain.exponentialRampToValueAtTime(.001,n+dur);o.connect(g);g.connect(a.destination);o.start();o.stop(n+dur)}
  function noise(dur,vol,freq,type){if(muted)return;var a=ac();if(!a)return;var n=Math.floor(a.sampleRate*dur),b=a.createBuffer(1,n,a.sampleRate),d=b.getChannelData(0);for(var i=0;i<n;i++)d[i]=Math.random()*2-1;var s=a.createBufferSource();s.buffer=b;var f=a.createBiquadFilter();f.type=type;f.frequency.value=freq;var g=a.createGain();g.gain.setValueAtTime(vol,a.currentTime);g.gain.exponentialRampToValueAtTime(.001,a.currentTime+dur);s.connect(f);f.connect(g);g.connect(a.destination);s.start()}
  var sfx={
    punch:function(){noise(.12,.6,900,'lowpass');tone(160,40,.15,'sine',.7)},
    knife:function(){noise(.18,.35,3500,'highpass');setTimeout(function(){tone(300,120,.08,'square',.25)},150)},
    tick:function(){tone(900,900,.05,'square',.15)},
    boom:function(){noise(.9,.9,500,'lowpass');tone(110,25,.8,'sawtooth',.6)},
    jump:function(){tone(250,700,.25,'sine',.35)},
    thud:function(){tone(90,30,.2,'sine',.8);noise(.1,.4,400,'lowpass')},
    ouch:function(){var f=500+Math.random()*400;tone(f,f*.5,.18,'triangle',.3)}
  };
  $('snd').addEventListener('click',function(e){muted=!muted;e.target.textContent=muted?'🔇':'🔊';if(!muted){ac();sfx.ouch()}});
  function expire(d,life){setTimeout(function(){d.style.opacity='0'},life);setTimeout(function(){d.remove()},life+1200)}
  var SH={s:'polygon(0 45%,18% 0,32% 40%,52% 8%,70% 45%,100% 15%,88% 70%,100% 100%,58% 82%,38% 100%,18% 72%)',k:'polygon(0 10%,8% 0,100% 85%,92% 100%)'};
  function tear(p,type){var d=document.createElement('div'),k=type==='k',w=k?46:20+Math.random()*14,h=k?40:16+Math.random()*10;d.className='tear';d.style.cssText='left:'+(Math.random()*(84-w)+3)+'px;top:'+(10+Math.random()*(90-h))+'px;width:'+w+'px;height:'+h+'px;clip-path:'+SH[type]+';-webkit-clip-path:'+SH[type];if(p.children.length>10)p.removeChild(p.firstChild);p.appendChild(d);expire(d,12000)}
  function sleeves(){[armL,armR].forEach(function(a){var d=document.createElement('div'),s='polygon(0 18%,25% 0,50% 15%,75% 0,100% 20%,100% 100%,0 100%)';d.className='tear';d.style.cssText='left:0;top:38px;width:18px;height:56px;clip-path:'+s+';-webkit-clip-path:'+s;a.appendChild(d);expire(d,12000)})}
  function band(){var d=document.createElement('div'),h=Math.random()<.5;d.className='band';d.style.left=(h?55+Math.random()*50:62+Math.random()*50)+'px';d.style.top=(h?18+Math.random()*60:130+Math.random()*60)+'px';d.style.transform='rotate('+(Math.random()*80-40)+'deg)';bud.appendChild(d);expire(d,10000)}
  function fall(ms,dir){lieDir=dir||1;fallUntil=performance.now()+ms;setTimeout(sfx.thud,260)}
  function damage(kind,dir){
    var t=$('torso');
    if(kind==='punch'){oy.v=-420;punches++;if(punches%6===0)fall(1300,dir);if(Math.random()<.3)tear(t,'s')}
    else if(kind==='knife'){fall(1100,dir);tear(t,'k');band()}
    else{soot=1;tear(t,'s');tear(t,'s');tear(t,'s');tear(t,'k');sleeves()}
  }
  var W={
    punch:{p:40,g:8,r:.06,e:['😖','😣','😫'],t:['Aah!','Ouch!','Maaf kar do!','Ruko yaar!','Bas bas!']},
    knife:{p:25,g:12,r:.05,e:['😱','😨'],t:['Arey knife?!','Yeh kya kar rahi ho!','Sorry baby!','Dar lag raha hai!']},
    bomb:{p:90,g:35,r:.3,e:['😵','🤯'],t:['BOOM! Mera chehra!','Main kala ho gaya!','Ye kya tha?!']}
  };
  function rnd(a){return a[Math.floor(Math.random()*a.length)]}
  function say(e,t,ms){cemo.textContent=e;ctxt.textContent=t;sayUntil=performance.now()+(ms||1800);idleSet=false}
  function fx(cls,txt,x,y){var d=document.createElement('div');d.className='fx '+cls;d.textContent=txt;d.style.left=x+'px';d.style.top=y+'px';stage.appendChild(d);setTimeout(function(){d.remove()},650);return d}
  function inBuddy(cx,cy){var b=bud.getBoundingClientRect();return cx>b.left+20&&cx<b.right-20&&cy>b.top&&cy<b.bottom}
  function hurt(kind,cx){
    var w=W[kind],b=bud.getBoundingClientRect(),dir=cx>b.left+b.width/2?-1:1;
    rot.v+=dir*w.p*5;hd.v+=dir*w.p*8;arm.v+=dir*w.p*6;ox.v+=dir*w.p*4;
    gussa=Math.min(100,gussa+w.g);redness=Math.min(1,redness+w.r);
    say(rnd(w.e),rnd(w.t));sfx.ouch();damage(kind,dir);
    if(navigator.vibrate){try{navigator.vibrate(kind==='bomb'?120:25)}catch(_){}}
  }
  function explode(el,x,y,r){
    el.remove();
    fx('boom','💥',x,y);sfx.boom();
    var f=document.createElement('div');f.className='flash';stage.appendChild(f);setTimeout(function(){f.remove()},400);
    stage.classList.remove('shake');void stage.offsetWidth;stage.classList.add('shake');
    var b=bud.getBoundingClientRect(),dx=(r.left+x)-(b.left+b.width/2),dy=(r.top+y)-(b.top+b.height/2);
    if(Math.sqrt(dx*dx+dy*dy)<230){
      hurt('bomb',r.left+x);soot=1;oy.v=-1500;rot.v+=(dx>0?-1:1)*650;fall(1800,dx>0?-1:1);
    }else say('😜','Bomb galat jagah gira!');
  }
  stage.addEventListener('pointerdown',function(e){
    e.preventDefault();ac();
    var r=stage.getBoundingClientRect(),x=e.clientX-r.left,y=e.clientY-r.top,hit=inBuddy(e.clientX,e.clientY);
    if(weapon==='jump'){oy.v=-1400;arm.v+=450*(Math.random()<.5?1:-1);sfx.jump();say('🤸',rnd(['Wooo!','Uchhal gaya!','Main ud raha hoon!']),1200);return}
    if(weapon==='punch'){
      fx('fist','👊',x,y);fx('pow','POW!',x,y-30);
      sfx.punch();if(hit)hurt('punch',e.clientX);else say('😜','Miss ho gaya!',1000);
    }else if(weapon==='knife'){
      var k=document.createElement('div'),parent=hit?bud:stage,b=bud.getBoundingClientRect();
      k.className='fx knife';k.textContent='🔪';
      k.style.left=(hit?e.clientX-b.left:x)+'px';k.style.top=(hit?e.clientY-b.top:y)+'px';
      k.style.transform='translate(60px,-170px) rotate(200deg) scale(1.7)';k.style.opacity='.5';
      parent.appendChild(k);
      requestAnimationFrame(function(){requestAnimationFrame(function(){k.style.transform='rotate('+(Math.random()*50-25)+'deg)';k.style.opacity='1'})});
      sfx.knife();setTimeout(function(){if(hit)hurt('knife',e.clientX);else say('😜','Knife deewar mein laga!',1000)},170);
      setTimeout(function(){k.style.opacity='0'},2800);setTimeout(function(){k.remove()},3300);
    }else{
      var bm=fx('bomb','💣',x,y);say('😨','Yeh bomb kya hai?!',1300);[0,350,700,1000,1200].forEach(function(d){setTimeout(sfx.tick,d)});
      setTimeout(function(){explode(bm,x,y,r)},1300);
    }
  });
  var btns=document.querySelectorAll('.tools button');
  btns.forEach(function(b){b.addEventListener('click',function(){
    weapon=b.dataset.w;btns.forEach(function(o){o.setAttribute('aria-pressed',o===b?'true':'false')});
  })});
  var moods=[[0,'Shaant 😇'],[15,'Thoda gussa 😒'],[35,'Gussa 😠'],[60,'Bahut gussa 😡'],[85,'MAX GUSSA 🤬🔥']];
  function tick(t){
    var dt=Math.min(.033,(t-last)/1000);last=t;
    for(var i=0;i<2;i++){[rot,hd,arm,ox,oy].forEach(function(s){step(s,dt/2)})}
    gussa=Math.max(0,gussa-dt*20);          /* empties in 5 seconds */
    redness=Math.max(0,redness-dt*.035);
    soot=Math.max(0,soot-dt*.06);
    lie+=((t<fallUntil?1:0)-lie)*Math.min(1,dt*7);
    var air=oy.x<-12;if(wasAir&&!air&&oy.v>0&&t-lastLand>300){lastLand=t;sfx.thud()}wasAir=air;
    if(fallUntil&&t>fallUntil){fallUntil=0;say('😅','Uth gaya! Ab bas karo!',1500)}
    bud.style.transform='translate('+ox.x+'px,'+Math.min(0,oy.x)+'px) rotate('+(rot.x+lieDir*lie*84)+'deg)';
    head.style.transform='rotate('+hd.x+'deg)';
    armL.style.transform='rotate('+arm.x+'deg)';armR.style.transform='rotate('+(-arm.x*.8)+'deg)';
    redEl.style.opacity=Math.min(1,redness*1.15);sootEl.style.opacity=soot;
    bud.style.setProperty('--s',(soot*.85).toFixed(2));
    fill.style.width=gussa+'%';fill.style.background='hsl('+(120-gussa*1.2)+' 85% 45%)';
    pct.textContent=Math.round(gussa)+'%';
    var m=moods[0][1];moods.forEach(function(a){if(gussa>=a[0])m=a[1]});mood.textContent=m;
    if(t>sayUntil&&!idleSet){
      idleSet=true;
      if(soot>.3)say('🥴','Dekho, kala ho gaya hoon…',99999);
      else if(redness>.15)say('🥺','Ho gaya na? Ab maaf kar do!',99999);
      else say('😌','Maaro mujhe…',99999);
      idleSet=true;
    }
    requestAnimationFrame(tick);
  }
  requestAnimationFrame(tick);
})();
</script>
</body>
</html>
