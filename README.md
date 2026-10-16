<!DOCTYPE html><html lang="ru"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<title>Номера</title>
<link href="https://fonts.googleapis.com/css2?family=Oswald:wght@500;700&family=Russo+One&family=Sora:wght@400;600;800&display=swap" rel="stylesheet">
<style>
*{box-sizing:border-box;margin:0}html,body{height:100%}
body{background:radial-gradient(90% 55% at 50% 38%,#4a2391,#170b34 62%,#07040f);color:#fff;font:14px Sora,sans-serif;display:flex;flex-direction:column;overflow:hidden;padding-top:env(safe-area-inset-top,0)}
.ru{font-family:"Russo One",sans-serif}.o{font-family:Oswald,sans-serif}
#top{display:flex;justify-content:space-between;padding:14px 16px 0}
.pill{display:flex;align-items:center;gap:8px;background:#0b0618bb;border:1px solid #ffffff2a;border-radius:22px;padding:5px 12px 5px 5px;font:600 15px Sora}
.coin{width:26px;height:26px;border-radius:50%;background:linear-gradient(#ffe08a,#e8a317);color:#5a3a00;display:flex;align-items:center;justify-content:center;font-size:14px}
#main{flex:1;overflow-y:auto;padding:10px 16px;display:flex;flex-direction:column;align-items:center}
.b3{border:0;border-radius:20px;font:400 20px "Russo One",sans-serif;letter-spacing:.05em;color:#fff;width:100%;height:60px;margin-top:14px}
.b3:disabled{opacity:.45}.gold{background:linear-gradient(#ffd76a,#f5a300);box-shadow:0 6px 0 #a35f00,0 12px 26px #f5a30066;color:#3a2200}
.vio{background:linear-gradient(#9d6bff,#6a35e6);box-shadow:0 6px 0 #3b1a9c;height:52px;font-size:16px}
.nav{display:flex;justify-content:space-around;background:#0b0618;border-top:1px solid #ffffff18;padding:8px 0 calc(10px + env(safe-area-inset-bottom,0))}
.ni{display:flex;flex-direction:column;align-items:center;font:600 11px Sora;color:#8a84a8;background:none;border:0}.ni i{font-style:normal;font-size:20px}.on{color:#ffd76a}.on i{filter:drop-shadow(0 0 8px #f5a300)}
.pl{display:flex;background:linear-gradient(#e2e4e8,#aeb1b6);border:3px solid #111;border-radius:10px;color:#000}
.rg{border-left:3px solid #111;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:0 .2em}
.rs{display:flex;gap:4px;align-items:center;font:700 .17em Sora}.fl{width:1.6em;height:1em;background:linear-gradient(#fff 33%,#1c4fb4 33% 66%,#d52b1e 66%);border:1px solid #444}
.main{display:flex;align-items:center;padding:.06em .22em}.rr{display:flex;font-size:.78em}
.r{display:inline-block;width:.64em;height:1.1em;overflow:hidden;font:700 1em/1.1em Oswald,sans-serif;text-align:center}.rr .r{width:.6em}.sp{width:.08em}
.r div{display:flex;flex-direction:column}.r b{height:1.1em;line-height:1.1em}
#win{position:relative;width:100%;max-width:350px;height:200px;border-radius:26px;border:3px solid #ffd76a;background:#0b0618d9;box-shadow:0 0 44px #a855f777,inset 0 0 34px #000;display:flex;align-items:center;justify-content:center;margin-top:12px}
#plate{font-size:min(13.5vw,54px);transition:box-shadow .6s;border-radius:10px;display:flex}
.card{width:100%;border-radius:20px;border:2px solid var(--c);background:linear-gradient(#1d1040,#110a28);box-shadow:0 0 22px var(--c);padding:12px;margin-bottom:12px;text-align:center}
#wh{width:290px;height:290px;border-radius:50%;border:8px solid #ffd76a;box-shadow:0 0 44px #f5a30088,inset 0 0 30px #0008;position:relative}
#wh span{position:absolute;left:50%;top:50%;width:70px;margin:-12px 0 0 -35px;text-align:center;font:400 17px "Russo One";text-shadow:0 2px 4px #000}
#md{position:fixed;inset:0;background:#000a;display:none;align-items:center;justify-content:center;padding:20px;z-index:9}
</style></head><body>
<div id="top"><div class="pill"><span class="coin">★</span><span id="s"></span></div><div class="pill"><span class="coin" style="background:linear-gradient(#b8f5c8,#2fb457);color:#073d1a">₽</span><span id="m"></span></div></div>
<div id="main"></div>
<div class="nav" id="nav"><button class="ni" onclick="go(0)"><i>◉</i>Рулетка</button><button class="ni" onclick="go(1)"><i>▤</i>Коллекция</button><button class="ni" onclick="go(2)"><i>♛</i>Топ</button><button class="ni" onclick="go(3)"><i>✦</i>Бонусы</button><button class="ni" onclick="go(4)"><i>◆</i>Магазин</button></div>
<div id="md"></div>
<script>
const $=id=>document.getElementById(id),rnd=s=>s[Math.random()*s.length|0],fmt=n=>Math.round(n).toLocaleString('ru-RU'),sleep=ms=>new Promise(r=>setTimeout(r,ms));
const D='0123456789',L='АВЕКМНОРСТУХ',KIND='ldddllrrr';
const REG=['77','78','50','52','61','63','74','86','102','116','124','150','152','154','161','163','174','177','178','190','197','199','716','750','761','763','774','777','797','799'];
const TOP=['77','777','97','99','177','197','199','277','797','799','78','178','50','150','190','750','774'];
const RAR=[['ОБЫЧНЫЙ','#9aa0a8',[2e4,15e4],.8],['РЕДКИЙ','#3b82f6',[15e4,6e5],1.2],['ЭПИЧЕСКИЙ','#a855f7',[6e5,2e6],2],['МИФИЧЕСКИЙ','#ef4444',[2e6,8e6],3],['ЛЕГЕНДАРНЫЙ','#f5b301',[8e6,3e7],4.5]];
let S={s:40,m:0,g:[],w:0},busy=0,T=0,cur=0,last=null;
try{Object.assign(S,JSON.parse(localStorage.getItem('np1')||'{}'))}catch(e){}
const save=()=>{try{localStorage.setItem('np1',JSON.stringify(S))}catch(e){}},bal=()=>{$('s').textContent=S.s;$('m').textContent=fmt(S.m)};
const pool=(k,i)=>k=='l'?L:k=='r'&&i==6?'1234567':D;
function rate(t){const d=t.slice(1,4);let q=0;if(d[0]==d[1]&&d[1]==d[2])q=d=='777'?4:3;else if(d[0]==d[1]||d[1]==d[2]||d[0]==d[2])q=1;
 if(q<3&&(d[0]==d[2]||(+d[1]==+d[0]+1&&+d[2]==+d[1]+1)))q=Math.max(q,2);if(TOP.includes(t.slice(6).trim()))q=Math.min(4,q+1);return q}
function make(p){let d=[0,1,2].map(()=>rnd(D));if(Math.random()<(p?.12:.04)){const a=rnd(D);d=[a,a,a]}const r=rnd(REG);return rnd(L)+d.join('')+rnd(L)+rnd(L)+(r.length==2?r+'\u00a0':r)}
function force(q){let t,n=0;do{t=make(1)}while(rate(t)<q&&++n<30000);return t}
const price=q=>{const [a,b]=RAR[q][2];return Math.round((a+Math.random()*(b-a))/1e3)*1e3};
const cell=c=>`<span class="r"><div><b>${c}</b></div></span>`;
const spl=(t,c)=>`<div class="pl" style="font-size:34px;box-shadow:0 0 16px ${c}"><div class="o" style="padding:0 .25em;font-weight:700;display:flex;align-items:center">${t.slice(0,6)}</div><div class="rg"><div class="o" style="font-size:.78em;font-weight:700">${t.slice(6).trim()}</div><div class="rs"><span>RUS</span><span class="fl"></span></div></div></div>`;
const md=h=>{$('md').innerHTML='<div class="card" style="--c:#ffd76a;max-width:320px">'+h+'<button class="b3 gold" onclick="$(\'md\').style.display=\'none\'">OK</button></div>';$('md').style.display='flex'};
function go(t){if(busy)return;T=t;[...$('nav').children].forEach((b,i)=>b.classList.toggle('on',i==t));[vr,vg,()=>soon('Топ игроков'),vb,()=>soon('Магазин')][t]()}
const soon=n=>$('main').innerHTML=`<div class="ru" style="margin-top:80px;font-size:22px">${n}</div><p style="color:#b9b0e0;margin-top:10px;text-align:center">Скоро. Нужен сервер бота.</p>`;
function vr(){$('main').innerHTML=`<div class="ru" id="rt" style="font-size:30px;margin-top:8px">КРУТИ НОМЕР</div><div id="win"><div id="plate"><div class="pl"><div class="main">${[...'К774'].map(cell).join('')}<span class="sp"></span>${[...'КС'].map(cell).join('')}</div><div class="rg"><div class="rr">${[...'774'].map(cell).join('')}</div><div class="rs"><span>RUS</span><span class="fl"></span></div></div></div></div></div>
<div id="pr" class="ru" style="font-size:36px;color:#ffe08a;height:46px;margin-top:10px;opacity:0;transition:opacity .6s">&nbsp;</div><div id="ac"></div>
<button class="b3 gold" id="b1" onclick="spin(0)">КРУТИТЬ</button><button class="b3 vio" id="b2" onclick="spin(1)">КРУТИТЬ ЗА 20 ★ · ШАНС ВЫШЕ</button>`}
const count=(el,to,ms,col)=>new Promise(r=>{const t0=performance.now();el.style.color=col;(function f(n){const p=Math.min((n-t0)/ms,1);el.textContent=fmt(to*(1-Math.pow(1-p,3)))+' ₽';p<1?requestAnimationFrame(f):r()})(t0)});
async function spin(p){if(busy)return;if(p){if(S.s<20)return md('Не хватает ★');S.s-=20}
 busy=1;$('b1').disabled=$('b2').disabled=true;$('ac').innerHTML='';$('pr').style.opacity=0;$('rt').textContent='КРУТИМ...';$('rt').style.color='#fff';$('plate').style.boxShadow='none';bal();
 const fin=make(p),q=rate(fin),[nm,c]=RAR[q],reels=[...document.querySelectorAll('.r')];let done=0;
 await new Promise(res=>reels.forEach((r,i)=>{const n=14+i*4,it=[fin[i]];for(let j=0;j<n;j++)it.push(rnd(pool(KIND[i],i)));const dv=r.firstElementChild;dv.innerHTML=it.map(x=>`<b>${x}</b>`).join('');
  dv.animate([{transform:`translateY(${-n*1.1}em)`},{transform:'translateY(0)'}],{duration:1600+i*380,easing:'cubic-bezier(.12,.75,.2,1)',fill:'forwards'}).onfinish=()=>{if(++done==reels.length)res()}}));
 $('rt').textContent=nm;$('rt').style.color=c;$('plate').style.boxShadow=`0 0 ${10+q*10}px ${c}`;
 if(q==4)await sleep(500);$('pr').style.opacity=1;const pc=price(q);await count($('pr'),pc,RAR[q][3]*1000,c);
 last={t:fin,p:pc,q};S.g.push(last);save();
 $('ac').innerHTML='<button class="b3 gold" style="height:44px;font-size:15px;margin-top:0" onclick="sellLast()">ПРОДАТЬ</button>';
 $('b1').disabled=$('b2').disabled=false;busy=0}
function sellLast(){const i=S.g.indexOf(last);if(i<0)return;S.g.splice(i,1);S.m+=last.p;last=null;save();bal();$('ac').innerHTML=''}
function vg(){const tot=S.g.reduce((a,c)=>a+c.p,0);$('main').innerHTML=`<div class="ru" style="font-size:26px;align-self:flex-start">КОЛЛЕКЦИЯ</div><div style="align-self:flex-start;color:#b9b0e0;margin:4px 0 12px">${S.g.length} номеров · ${fmt(tot)} ₽</div>`+S.g.map((c,i)=>({c,i})).reverse().map(({c,i})=>`<div class="card" style="--c:${RAR[c.q][1]}"><div style="display:flex;justify-content:space-between;margin-bottom:10px"><span class="ru" style="color:${RAR[c.q][1]}">${RAR[c.q][0]}</span><span class="ru" style="color:#ffe08a">${fmt(c.p)} ₽</span></div><div style="display:flex;justify-content:center">${spl(c.t,RAR[c.q][1])}</div><button class="b3 gold" style="height:38px;font-size:14px" onclick="sell(${i})">ПРОДАТЬ</button></div>`).join('')||'<p style="color:#b9b0e0;margin-top:60px">Пусто. Крути рулетку!</p>'}
function sell(i){const c=S.g.splice(i,1)[0];S.m+=c.p;save();bal();vg()}
const WL=['★5','МИФ','★10','ЛЕГ','★50'],WC=['#3b82f6','#ef4444','#8b5cf6','#f5b301','#10b981'],P=[50,14,30,3,3];
function vb(){const ok=Date.now()-S.w>=864e5,g=WC.concat(WC).map((c,i)=>`${c} ${i*36}deg ${i*36+36}deg`).join(',');
 $('main').innerHTML=`<div class="ru" style="font-size:28px;color:#ffe08a">КОЛЕСО УДАЧИ</div><div style="position:relative;margin:30px 0 8px"><div style="position:absolute;left:50%;top:-22px;margin-left:-16px;border-top:30px solid #ef4444;border-left:16px solid transparent;border-right:16px solid transparent;z-index:3"></div><div id="wh" style="background:conic-gradient(${g});transform:rotate(${cur}deg)">${Array.from({length:10},(_,k)=>`<span style="transform:rotate(${k*36+18}deg) translateY(-108px)">${WL[k%5]}</span>`).join('')}</div></div><button class="b3 gold" onclick="wheel()" ${ok?'':'disabled'}>${ok?'КРУТИТЬ КОЛЕСО':'ЗАВТРА'}</button><p style="color:#b9b0e0;margin-top:10px">Бесплатно раз в 24 часа</p>`}
async function wheel(){if(busy||Date.now()-S.w<864e5)return;busy=1;let x=Math.random()*100,t=0;for(;t<4;t++){x-=P[t];if(x<0)break}
 const k=t+5*(Math.random()*2|0);S.w=Date.now();save();cur=Math.ceil(cur/360)*360+1800-(k*36+18)+(Math.random()*20-10);
 const w=$('wh');w.style.transition='transform 5s cubic-bezier(.1,.7,.1,1)';w.style.transform=`rotate(${cur}deg)`;await sleep(5300);
 let h;if(t%2==0){const n=[5,0,10,0,50][t];S.s+=n;h=`<div class="ru" style="font-size:34px">★ +${n}</div>`}else{const q=t==1?3:4,tt=force(q),pc=price(q);S.g.push({t:tt,p:pc,q});h=`<div class="ru" style="color:${RAR[q][1]}">${RAR[q][0]}</div><div style="display:flex;justify-content:center;margin:10px 0">${spl(tt,RAR[q][1])}</div><div class="ru" style="color:#ffe08a">${fmt(pc)} ₽</div>`}
 save();bal();busy=0;vb();md(h)}
bal();go(0);
</script></body></html>

