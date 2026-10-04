<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>DECK — PS5 Game Discovery</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;700&family=Inter:wght@400;500;700&display=swap" rel="stylesheet">
<style>
:root{
  --bg:#07080c; --card:#0d0f16; --ink:#f2f1ec; --sub:#a3a8b8;
  --accent:#7dffb3; --accent2:#ff5f7e; --gold:#ffc857;
  --font-display:'Space Grotesk',sans-serif; --font-body:'Inter',sans-serif;
  --r-lg:20px; --r-md:14px; --r-sm:10px;
  --shadow-soft:0 8px 24px rgba(0,0,0,.35);
  box-sizing:border-box;
  padding-top:env(safe-area-inset-top,0px); padding-bottom:env(safe-area-inset-bottom,0px);
}
*{box-sizing:border-box;}
html,body{height:100%;margin:0;background:var(--bg);color:var(--ink);font-family:var(--font-body);overflow:hidden;}
#feed{height:100%;overflow-y:scroll;scroll-snap-type:y mandatory;-webkit-overflow-scrolling:touch;}
.card{
  position:relative;height:100%;width:100%;scroll-snap-align:start;scroll-snap-stop:always;
  display:flex;flex-direction:column;justify-content:flex-end;overflow:hidden;
}
.bg{position:absolute;inset:0;z-index:0;background-size:cover;transition:transform 6s ease;}
.card.active .bg{transform:scale(1.08);animation:drift 15s ease-in-out infinite alternate;}
@keyframes drift{from{background-position:50% 42%;}to{background-position:44% 58%;}}
.scan{position:absolute;inset:0;z-index:1;background:repeating-linear-gradient(180deg,rgba(255,255,255,.03) 0px,rgba(255,255,255,.03) 1px,transparent 1px,transparent 3px);pointer-events:none;mix-blend-mode:overlay;}
.grad{position:absolute;inset:0;z-index:1;background:linear-gradient(180deg,rgba(7,8,12,.15) 0%,rgba(7,8,12,.1) 45%,rgba(7,8,12,.96) 92%);}
.rail{position:absolute;right:12px;bottom:150px;z-index:3;display:flex;flex-direction:column;align-items:center;gap:20px;}
.rbtn{width:52px;height:52px;border-radius:50%;background:rgba(20,22,30,.55);backdrop-filter:blur(6px);border:1px solid rgba(255,255,255,.12);display:flex;align-items:center;justify-content:center;color:var(--ink);font-size:22px;cursor:pointer;transition:transform .15s,box-shadow .2s;-webkit-tap-highlight-color:transparent;text-decoration:none;box-shadow:0 4px 14px rgba(0,0,0,.35);}
.rbtn:active{transform:scale(.88);}
.rbtn.liked{color:var(--accent2);border-color:var(--accent2);box-shadow:0 0 16px rgba(255,95,126,.35);}
.rbtn.saved{color:var(--gold);border-color:var(--gold);box-shadow:0 0 16px rgba(255,200,87,.3);}
.pub{width:46px;height:46px;border-radius:14px;background:linear-gradient(135deg,#1c2030,#0d0f16);border:1px solid rgba(255,255,255,.15);display:flex;align-items:center;justify-content:center;font-family:var(--font-display);font-weight:700;font-size:15px;color:var(--accent);box-shadow:0 4px 14px rgba(0,0,0,.35);}
.fund{width:52px;padding:9px 0;border-radius:16px;background:linear-gradient(135deg,var(--accent),#43e39a);color:#04140b;border:none;font-family:var(--font-display);font-weight:700;font-size:9px;letter-spacing:.02em;cursor:pointer;text-align:center;line-height:1.15;box-shadow:0 4px 14px rgba(125,255,179,.25);}
.info{position:relative;z-index:2;padding:0 84px 34px 20px;}
.badge-row{display:flex;align-items:center;gap:8px;margin-bottom:8px;}
.rating{background:linear-gradient(135deg,rgba(255,200,87,.22),rgba(255,200,87,.08));border:1px solid var(--gold);color:var(--gold);font-family:var(--font-display);font-size:12px;font-weight:700;padding:3px 9px;border-radius:20px;}
.studio{color:var(--sub);font-size:12px;}
.chip{font-size:11px;color:var(--sub);background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.14);padding:3px 9px;border-radius:20px;}
.chip.psplus{color:#6fc8ff;border-color:rgba(111,200,255,.5);background:rgba(111,200,255,.1);}
.meta-row{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:14px;}
.title{font-family:var(--font-display);font-weight:700;font-size:26px;line-height:1.05;margin:0 0 8px;text-shadow:0 2px 18px rgba(0,0,0,.5);}
.hype{font-size:13.5px;color:#d4d6de;line-height:1.45;margin:0 0 10px;max-width:34ch;}
.tags{display:flex;gap:6px;flex-wrap:wrap;}
.tag{font-size:11px;color:var(--accent);border:1px solid rgba(125,255,179,.35);background:rgba(125,255,179,.06);padding:3px 9px;border-radius:20px;}
.brand{position:absolute;top:0;left:0;right:0;z-index:3;padding:14px 18px;display:flex;justify-content:space-between;align-items:center;padding-top:calc(14px + env(safe-area-inset-top,0px));pointer-events:none;background:linear-gradient(180deg,rgba(7,8,12,.55) 0%,rgba(7,8,12,0) 100%);}
.brand b{font-family:var(--font-display);font-size:16px;letter-spacing:.01em;background:linear-gradient(135deg,var(--ink),var(--accent));-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent;}
.brand span{font-size:11px;color:var(--sub);font-variant-numeric:tabular-nums;}
::-webkit-scrollbar{width:0px;background:transparent;}
.view,#feed{scrollbar-width:none;}

.sheet-wrap{position:fixed;inset:0;z-index:10;display:none;align-items:flex-end;background:rgba(0,0,0,.6);backdrop-filter:blur(2px);}
.sheet-wrap.open{display:flex;}
.sheet{width:100%;background:linear-gradient(180deg,#12141c,var(--card));border-radius:22px 22px 0 0;padding:22px 22px calc(28px + env(safe-area-inset-bottom,0px));border-top:1px solid rgba(255,255,255,.12);animation:up .25s ease;max-height:85vh;overflow-y:auto;box-shadow:0 -12px 40px rgba(0,0,0,.5);position:relative;}
.sheet::before{content:'';position:sticky;top:-22px;display:block;width:36px;height:4px;border-radius:3px;background:rgba(255,255,255,.18);margin:0 auto 14px;}
.prof-h{font-size:11px;color:var(--sub);text-transform:uppercase;letter-spacing:.06em;margin-bottom:4px;}
.prof-title{font-family:var(--font-display);font-weight:700;font-size:20px;margin-bottom:6px;}
.prof-stats{font-size:12.5px;color:var(--sub);margin-bottom:4px;}
.prof-sec{font-family:var(--font-display);font-weight:700;font-size:13px;margin:18px 0 7px;color:var(--accent);}
.vibe-list{display:flex;flex-direction:column;gap:7px;}
.vibe-row{display:flex;justify-content:space-between;font-size:12.5px;color:#d4d6de;}
.vibe-lvl{color:var(--gold);font-family:var(--font-display);font-weight:700;font-size:11px;}
.trailer-link{display:block;text-align:center;text-decoration:none;margin:12px 0 4px;}
@keyframes up{from{transform:translateY(30px);opacity:0;}to{transform:translateY(0);opacity:1;}}
.sheet h3{font-family:var(--font-display);margin:0 0 2px;font-size:20px;background:linear-gradient(135deg,var(--ink),var(--accent));-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent;}
.sheet .sub{color:var(--sub);font-size:12.5px;margin-bottom:16px;}
.bar-bg{height:8px;border-radius:6px;background:#20232f;overflow:hidden;margin-bottom:6px;}
.bar-fill{height:100%;background:linear-gradient(90deg,var(--accent),#43e39a);border-radius:6px;transition:width .4s ease;}
.goal-row{display:flex;justify-content:space-between;font-size:12px;color:var(--sub);margin-bottom:18px;}
.goal-row b{color:var(--ink);font-family:var(--font-display);}
.pledges{display:flex;gap:10px;margin-bottom:10px;}
.pledge{flex:1;padding:12px 0;border-radius:12px;background:#171a24;border:1px solid rgba(255,255,255,.1);color:var(--ink);font-family:var(--font-display);font-weight:700;font-size:14px;cursor:pointer;}
.pledge:active{background:var(--accent);color:#04140b;}
.close-sheet{display:block;width:100%;text-align:center;color:var(--sub);font-size:13px;padding:12px 0 0;background:none;border:none;letter-spacing:.02em;}
.close-sheet:active{color:var(--ink);}
.confirm{font-size:12px;color:var(--accent);text-align:center;height:16px;margin-top:6px;}
.info{cursor:pointer;}
.tap-hint{font-size:10.5px;color:var(--sub);margin-top:2px;}
.rev-p{font-size:13.5px;color:#d4d6de;line-height:1.5;margin:0 0 12px;}
.rev-sec .rev-p:last-child,.rev-sec .rev-list{margin-bottom:0;}
.cat-row{display:flex;align-items:center;gap:10px;margin-bottom:9px;}
.cat-row .cname{width:60px;font-size:12px;color:var(--sub);flex-shrink:0;}
.cat-row .bar-bg{flex:1;margin-bottom:0;}
.cat-row .cval{width:28px;text-align:right;font-family:var(--font-display);font-size:12px;flex-shrink:0;}
.brand-right{display:flex;align-items:center;gap:10px;pointer-events:auto;}
.icon-btn{width:36px;height:36px;border-radius:50%;background:rgba(20,22,30,.65);backdrop-filter:blur(6px);border:1px solid rgba(255,255,255,.15);display:flex;align-items:center;justify-content:center;font-size:15px;cursor:pointer;transition:transform .15s;box-shadow:0 3px 10px rgba(0,0,0,.3);}
.icon-btn:active{transform:scale(.9);}
.search-input,.company-select{width:100%;padding:13px 14px;border-radius:var(--r-sm);background:#171a24;border:1px solid rgba(255,255,255,.12);color:var(--ink);font-size:14px;margin-bottom:16px;font-family:var(--font-body);transition:border-color .15s;}
.search-input:focus,.company-select:focus{outline:none;border-color:var(--accent);}
.filter-label{font-size:11px;color:var(--sub);text-transform:uppercase;letter-spacing:.05em;margin-bottom:8px;}
.chip-row{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:18px;}
.chip-toggle{font-size:12px;color:var(--ink);background:#171a24;border:1px solid rgba(255,255,255,.14);padding:7px 13px;border-radius:20px;cursor:pointer;transition:background .15s,box-shadow .15s;}
.chip-toggle.active{background:var(--accent);color:#04140b;border-color:var(--accent);box-shadow:0 0 10px rgba(125,255,179,.35);font-weight:700;}
.tut-row{display:flex;align-items:center;gap:12px;font-size:13px;color:#d4d6de;margin-bottom:13px;padding:8px 10px;border-radius:var(--r-sm);background:rgba(255,255,255,.03);}
.tut-ic{font-size:18px;width:28px;text-align:center;flex-shrink:0;}
.primary-btn{width:100%;background:linear-gradient(135deg,var(--accent),#43e39a);color:#04140b;border:none;border-radius:var(--r-sm);padding:14px;font-family:var(--font-display);font-weight:700;font-size:14px;cursor:pointer;margin-top:4px;box-shadow:0 6px 18px rgba(125,255,179,.25);transition:transform .1s;}
.primary-btn:active{transform:scale(.98);}
input[type=range]{width:100%;accent-color:var(--accent);margin-bottom:4px;}
.sheet-scroll{max-height:82vh;overflow-y:auto;}
.stat-row{display:flex;flex-wrap:wrap;gap:8px;margin:12px 0 16px;font-size:12.5px;}
.stat-row span{background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.12);padding:6px 12px;border-radius:var(--r-sm);font-weight:500;}
.rev-sec{margin-bottom:12px;background:rgba(255,255,255,.03);border:1px solid rgba(255,255,255,.06);border-radius:var(--r-md);padding:13px 14px;}
.rev-h{font-family:var(--font-display);font-weight:700;font-size:13px;margin-bottom:8px;display:flex;align-items:center;justify-content:space-between;color:var(--ink);}
.ai-intro{font-size:13px;color:#d4d6de;margin-bottom:10px;line-height:1.45;}
.ai-why{font-size:12px;color:#b8bccb;line-height:1.4;margin-top:3px;}
.ai-miss{font-size:12px;color:#8b8fa0;margin:8px 0 2px;}
#aiGo:disabled{opacity:.5;}
.cover-wrap{width:64%;max-width:240px;margin:2px auto 14px;border-radius:10px;overflow:hidden;box-shadow:0 10px 28px rgba(0,0,0,.55);}
.sim-cv{width:42px;flex:none;border-radius:5px;overflow:hidden;box-shadow:0 2px 8px rgba(0,0,0,.5);}
.beat{font-size:12.5px;color:#c9ccda;margin-top:9px;padding-top:8px;border-top:1px solid rgba(255,255,255,.08);}
.sim-hint{font-size:11px;color:#8b8fa0;margin-bottom:6px;}
.sim-row{display:flex;align-items:center;gap:10px;padding:9px 10px;margin-bottom:6px;background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.07);border-radius:10px;cursor:pointer;}
.sim-row:active{background:rgba(255,255,255,.09);}
.sim-t{flex:1;min-width:0;display:flex;flex-direction:column;gap:2px;}
.sim-t b{font-size:13.5px;color:#fff;}
.sim-t span{font-size:11.5px;color:#9a9eb0;}
.sim-go{font-size:20px;color:#9a9eb0;}
.rev-list{list-style:none;padding:0;margin:0;}
.rev-list li{font-size:13px;color:#d4d6de;padding:2px 0 2px 14px;position:relative;}
.rev-list li::before{content:'•';color:var(--accent);position:absolute;left:0;}
.vibe-row{display:flex;justify-content:space-between;font-size:12.5px;color:#d4d6de;padding:5px 0;border-bottom:1px solid rgba(255,255,255,.07);}
.vibe-row:last-child{border-bottom:none;}
.vibe-row b{color:var(--accent);font-family:var(--font-display);}
.stars{color:var(--gold);font-size:12px;margin-left:6px;}
@keyframes viewIn{from{opacity:0;transform:translateY(8px);}to{opacity:1;transform:translateY(0);}}
.view{position:fixed;inset:0;z-index:4;background:radial-gradient(ellipse at top,rgba(125,255,179,.05),transparent 55%),var(--bg);display:none;overflow-y:auto;padding:calc(20px + env(safe-area-inset-top,0px)) 18px calc(84px + env(safe-area-inset-bottom,0px));animation:viewIn .22s ease;}
.view-header{font-family:var(--font-display);font-weight:700;font-size:23px;margin-bottom:6px;}
.view-sub{font-size:11px;color:var(--sub);text-transform:uppercase;letter-spacing:.05em;margin:18px 0 8px;}
.lib-row{display:flex;gap:12px;align-items:center;padding:11px 10px;border-radius:var(--r-md);margin-bottom:4px;background:rgba(255,255,255,.03);border:1px solid rgba(255,255,255,.06);cursor:pointer;transition:background .15s;}
.lib-row:active{background:rgba(255,255,255,.07);}
.lib-swatch{width:46px;height:46px;border-radius:10px;flex-shrink:0;box-shadow:0 3px 10px rgba(0,0,0,.35);}
.lib-title{font-family:var(--font-display);font-weight:700;font-size:14px;}
.lib-sub{font-size:12px;color:var(--sub);}
.lib-empty{color:var(--sub);font-size:13px;padding:14px 10px;background:rgba(255,255,255,.02);border:1px dashed rgba(255,255,255,.1);border-radius:var(--r-md);text-align:center;}
.tabbar{position:fixed;left:0;right:0;bottom:0;z-index:5;display:flex;background:rgba(10,11,16,.82);backdrop-filter:blur(14px);border-top:1px solid rgba(255,255,255,.08);padding-bottom:env(safe-area-inset-bottom,0px);}
.tab{flex:1;display:flex;flex-direction:column;align-items:center;gap:2px;padding:8px 0 5px;color:var(--sub);font-size:8px;cursor:pointer;position:relative;transition:color .15s;}
.tab-ic{font-size:16px;transition:transform .15s;}
.tab.active{color:var(--accent);}
.tab.active .tab-ic{transform:translateY(-1px) scale(1.08);}
.tab.active::before{content:'';position:absolute;top:0;left:50%;transform:translateX(-50%);width:22px;height:2px;border-radius:2px;background:var(--accent);box-shadow:0 0 8px var(--accent);}
.tab:active .tab-ic{transform:scale(.85);}
.strat-map{margin-bottom:18px;border-left:2px solid var(--accent);padding-left:12px;}
.strat-map h4{font-family:var(--font-display);font-size:14px;margin:0 0 6px;color:var(--accent);}
.strat-note{margin:16px 0 4px;font-size:12px;color:var(--sub);line-height:1.5;padding-top:12px;border-top:1px solid rgba(255,255,255,.08);}
.site-grid{display:flex;flex-direction:column;gap:6px;margin:8px 0;}
.site-floor-lbl{font-size:10px;text-transform:uppercase;letter-spacing:.05em;color:var(--sub);margin-top:6px;}
.site-btn{display:block;width:100%;text-align:left;background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.12);color:inherit;border-radius:8px;padding:9px 11px;font-size:12.5px;font-family:inherit;}
.site-btn:active{background:rgba(255,255,255,.12);}
.site-panel{font-size:12px;color:var(--sub);line-height:1.5;padding:8px 11px 2px;}
.coach-wrap{border:1px solid rgba(125,255,179,.25);border-radius:var(--r-md);padding:13px 14px 14px;margin:12px 0 14px;background:linear-gradient(160deg,rgba(125,255,179,.06),rgba(255,255,255,.02));}
.coach-select-row{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:10px;}
.coach-select-row select{flex:1 1 30%;min-width:0;padding:8px 6px;border-radius:8px;background:#171a24;border:1px solid rgba(255,255,255,.14);color:var(--ink);font-size:11.5px;font-family:inherit;}
.coach-chat{max-height:260px;overflow-y:auto;margin-bottom:10px;}
.coach-chat:empty{display:none;}
.coach-msg{padding:9px 12px;border-radius:12px;margin-bottom:8px;font-size:12.5px;line-height:1.5;white-space:pre-wrap;}
.coach-msg.user{background:rgba(125,255,179,.14);margin-left:18%;}
.coach-msg.assistant{background:rgba(255,255,255,.05);margin-right:18%;border:1px solid rgba(255,255,255,.06);}
.coach-input-row{display:flex;gap:8px;}
.coach-input-row input{flex:1;min-width:0;padding:11px 12px;border-radius:var(--r-sm);background:#171a24;border:1px solid rgba(255,255,255,.14);color:var(--ink);font-size:13px;font-family:inherit;}
.coach-input-row button{background:linear-gradient(135deg,var(--accent),#43e39a);color:#04140b;border:none;border-radius:var(--r-sm);padding:0 16px;font-family:var(--font-display);font-weight:700;font-size:13px;}
.coach-input-row button:disabled{opacity:.5;}
.coach-hint{font-size:10.5px;color:var(--sub);margin-top:7px;}
.quiz-ctx{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:10px;font-size:11px;}
.quiz-ctx span{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.14);padding:3px 9px;border-radius:8px;}
.quiz-q{font-size:14px;font-weight:600;margin-bottom:12px;line-height:1.4;}
.quiz-opt{display:block;width:100%;text-align:left;padding:11px 13px;margin-bottom:8px;border-radius:10px;background:#171a24;border:1px solid rgba(255,255,255,.14);color:var(--ink);font-size:13px;font-family:inherit;}
.quiz-opt.correct{background:rgba(125,255,179,.18);border-color:var(--accent);}
.quiz-opt.wrong{background:rgba(255,95,126,.15);border-color:var(--accent2);}
.quiz-opt:disabled{opacity:.65;}
.quiz-why{font-size:12.5px;color:#d4d6de;background:rgba(255,255,255,.04);border-radius:10px;padding:11px 13px;margin:8px 0 12px;line-height:1.5;border-left:2px solid var(--accent);}
.quiz-progress{font-size:11px;color:var(--sub);margin-bottom:10px;}
.quiz-next-btn,.quiz-restart-btn{background:linear-gradient(135deg,var(--accent),#43e39a);color:#04140b;border:none;border-radius:var(--r-sm);padding:11px;font-family:var(--font-display);font-weight:700;font-size:13px;width:100%;}
.quiz-score{font-size:17px;font-weight:700;text-align:center;margin:14px 0 4px;font-family:var(--font-display);}
.quiz-score-sub{font-size:12px;color:var(--sub);text-align:center;margin-bottom:14px;}
.strat-nav{position:sticky;top:0;z-index:2;display:flex;gap:6px;overflow-x:auto;padding:8px 0 10px;margin:0 0 4px;background:var(--bg);-ms-overflow-style:none;scrollbar-width:none;}
.strat-nav::-webkit-scrollbar{display:none;}
.strat-nav button{flex:0 0 auto;padding:7px 13px;border-radius:999px;border:1px solid rgba(255,255,255,.15);background:rgba(255,255,255,.07);color:inherit;font-size:12px;font-family:inherit;white-space:nowrap;}
.strat-nav button.active{background:var(--accent);color:#0a0a0a;border-color:var(--accent);font-weight:700;}
.strat-section{border:1px solid rgba(255,255,255,.09);border-radius:14px;margin-bottom:12px;overflow:hidden;background:rgba(255,255,255,.025);}
.strat-section>summary{list-style:none;cursor:pointer;display:flex;align-items:center;gap:8px;padding:13px 14px;font-family:var(--font-display);font-weight:700;font-size:15px;}
.strat-section>summary::-webkit-details-marker{display:none;}
.strat-section>summary .chev{margin-left:auto;color:var(--sub);font-size:11px;transition:transform .15s;}
.strat-section[open]>summary .chev{transform:rotate(180deg);}
.strat-section-count{font-size:11px;color:var(--sub);font-weight:400;}
.strat-section-body{padding:2px 14px 14px;}
.strat-subhead{font-size:11px;text-transform:uppercase;letter-spacing:.05em;color:var(--accent);margin:14px 0 6px;}
.strat-subhead:first-child{margin-top:2px;}
.op-row{display:flex;flex-wrap:wrap;column-gap:6px;align-items:baseline;padding:8px 6px;border-bottom:1px solid rgba(255,255,255,.06);font-size:12.5px;line-height:1.5;border-radius:6px;}
.op-row:nth-child(even){background:rgba(255,255,255,.02);}
.op-row:last-child{border-bottom:none;}
.op-dot{width:6px;height:6px;border-radius:50%;flex:0 0 auto;margin-right:2px;align-self:center;}
.op-atk .op-dot{background:#ff9466;}
.op-def .op-dot{background:#5cc8ff;}
.glos-row{padding:7px 6px;border-bottom:1px solid rgba(255,255,255,.06);font-size:12.5px;line-height:1.5;border-radius:6px;}
.glos-row:nth-child(even){background:rgba(255,255,255,.02);}
.glos-row:last-child{border-bottom:none;}
.badge{display:inline-block;font-size:9.5px;font-weight:700;text-transform:uppercase;letter-spacing:.03em;padding:2px 7px;border-radius:5px;margin-right:5px;vertical-align:middle;}
.badge-ranked{background:rgba(92,200,255,.16);color:#7fd4ff;}
.badge-pro{background:rgba(255,148,102,.18);color:#ffab7f;}
.role-tag{font-size:9.5px;color:var(--sub);font-weight:600;text-transform:uppercase;letter-spacing:.03em;margin-right:6px;flex:0 0 auto;}
.map-jump-grid{display:flex;flex-wrap:wrap;gap:6px;margin:4px 0 16px;}
.map-jump-grid button{font-size:11px;padding:6px 10px;border-radius:8px;border:1px solid rgba(255,255,255,.12);background:rgba(255,255,255,.05);color:inherit;font-family:inherit;}
.op-filter-row{display:flex;gap:6px;margin:2px 0 10px;}
.op-filter-row button{flex:1;font-size:11.5px;padding:7px 0;border-radius:8px;border:1px solid rgba(255,255,255,.12);background:rgba(255,255,255,.05);color:inherit;font-family:inherit;}
.op-filter-row button.active{background:var(--accent);color:#0a0a0a;border-color:var(--accent);font-weight:700;}

/* ---------- polish pass ---------- */
*{-webkit-tap-highlight-color:transparent;}
html{-webkit-font-smoothing:antialiased;-webkit-text-size-adjust:100%;text-rendering:optimizeLegibility;}
a,button,.rbtn,.icon-btn,.tab,.sim-row,.lib-row,.chip-toggle,.primary-btn,.close-sheet{touch-action:manipulation;}
#feed::-webkit-scrollbar,.sheet::-webkit-scrollbar,.view::-webkit-scrollbar{display:none;}
.sheet,.view,#rBody{overscroll-behavior:contain;-webkit-overflow-scrolling:touch;}
:focus-visible{outline:2px solid var(--accent);outline-offset:2px;border-radius:8px;}
.sheet-wrap.open{animation:fadeIn .2s ease-out;}
.sheet-wrap.open .sheet{animation:sheetUp .32s cubic-bezier(.2,.85,.25,1);}
@keyframes fadeIn{from{opacity:0}to{opacity:1}}
@keyframes sheetUp{from{transform:translateY(36px);opacity:.4}to{transform:none;opacity:1}}
.rbtn,.icon-btn,.chip-toggle,.primary-btn,.sim-row,.lib-row{transition:transform .12s ease,background .15s ease,border-color .15s ease,box-shadow .2s ease,filter .15s ease;}
.rbtn.liked,.rbtn.saved{animation:popIn .38s cubic-bezier(.3,1.6,.5,1);}
@keyframes popIn{0%{transform:scale(.7)}60%{transform:scale(1.22)}100%{transform:scale(1)}}
.primary-btn:active{filter:brightness(.94);}
.info{text-shadow:0 1px 14px rgba(0,0,0,.75);}
.info .rating,.info .badge-row span{text-shadow:none;}
.sub{color:#b4b9c9;}
.sim-row{box-shadow:0 1px 0 rgba(255,255,255,.03) inset;}
.sim-row:active{transform:scale(.985);}
.rev-sec{box-shadow:0 6px 18px rgba(0,0,0,.18);}
#toast{position:fixed;left:50%;bottom:calc(86px + env(safe-area-inset-bottom,0px));transform:translate(-50%,16px);background:rgba(18,20,28,.94);color:#f2f1ec;border:1px solid rgba(255,255,255,.14);padding:10px 16px;border-radius:999px;font-size:13px;font-weight:500;z-index:30;opacity:0;pointer-events:none;transition:opacity .2s ease,transform .25s ease;box-shadow:0 8px 24px rgba(0,0,0,.45);white-space:nowrap;}
#toast.show{opacity:1;transform:translate(-50%,0);}
#swipeHint{position:fixed;left:50%;bottom:calc(96px + env(safe-area-inset-bottom,0px));transform:translateX(-50%);z-index:6;color:#f2f1ec;font-size:12px;letter-spacing:1px;text-transform:uppercase;text-align:center;pointer-events:none;opacity:0;animation:hintIn .5s ease .8s forwards;text-shadow:0 1px 8px rgba(0,0,0,.8);}
#swipeHint b{display:block;font-size:18px;animation:bob 1.2s ease-in-out infinite;}
#swipeHint.gone{animation:none;opacity:0;transition:opacity .3s ease;}
@keyframes hintIn{to{opacity:.85}}
@keyframes bob{0%,100%{transform:translateY(0)}50%{transform:translateY(-6px)}}
@media (prefers-reduced-motion:reduce){
  .card.active .bg{animation:none;transform:none;}
  *,*::before,*::after{animation-duration:.01ms!important;animation-iteration-count:1!important;transition-duration:.01ms!important;}
}
</style>
</head>
<body>
<div class="brand"><b>DECK</b><div class="brand-right"><span id="counter">Loading…</span><div class="icon-btn" id="openAI" style="display:none" title="AI game finder">✨</div><div class="icon-btn" id="openFilter">🔍</div></div></div>
<div id="feed"></div>

<div class="sheet-wrap" id="filterWrap">
  <div class="sheet">
    <h3>Search &amp; Filter</h3>
    <div class="sub">Narrow the feed, or clear to go back to your For You mix</div>
    <input type="text" id="searchInput" class="search-input" placeholder="Search title or studio…">
    <div class="filter-label">Genre (tap to combine — e.g. Strategy + Shooter)</div>
    <div class="chip-row" id="genreChips"></div>
    <div class="filter-label">Company</div>
    <select id="companySelect" class="company-select"><option value="">All Companies</option></select>
    <div class="filter-label">Story length (games with a known length)</div>
    <select id="lengthSelect" class="company-select"><option value="">Any length</option><option value="short">Short — under 10 hours</option><option value="medium">Medium — 10 to 25 hours</option><option value="long">Long — over 25 hours</option><option value="none">No story campaign (multiplayer / arcade)</option></select>
    <div class="filter-label">Min Price: <span id="minPriceVal">$0</span></div>
    <input type="range" id="minPriceInput" min="0" max="70" step="5" value="0">
    <div class="filter-label" style="margin-top:14px;">Max Price: <span id="maxPriceVal">$70+</span></div>
    <input type="range" id="maxPriceInput" min="0" max="70" step="5" value="70">
    <button class="primary-btn" id="clearFilters" style="background:#171a24;color:var(--ink);border:1px solid rgba(255,255,255,.14);margin-top:20px;margin-bottom:8px;">Clear Filters</button>
    <button class="close-sheet" id="closeFilter">Close</button>
  </div>
</div>

<div class="sheet-wrap" id="tutorialWrap">
  <div class="sheet">
    <h3>Welcome to DECK</h3>
    <div class="sub" style="margin-bottom:18px;">A 10-second guide before you dive in</div>
    <div class="tut-row"><span class="tut-ic">⬆️</span>Swipe or scroll to browse games</div>
    <div class="tut-row"><span class="tut-ic">♡</span>Heart to like — the feed learns your taste</div>
    <div class="tut-row"><span class="tut-ic">☆</span>Star to save it to your collection</div>
    <div class="tut-row"><span class="tut-ic">📦</span>Each card shows how many copies have sold</div>
    <div class="tut-row"><span class="tut-ic">ℹ️</span>Tap the title or blurb for a full review</div>
    <div class="tut-row"><span class="tut-ic">🔍</span>Use the top-right icon to search or filter</div>
    <button class="primary-btn" id="closeTutorial">Got it</button>
  </div>
</div>

<div class="sheet-wrap" id="aiWrap">
  <div class="sheet sheet-scroll">
    <h3>✨ AI Game Finder</h3>
    <div class="sub">Describe what you want, or name a game you love — e.g. “a game like Call of Duty: Modern Warfare III”</div>
    <textarea id="aiInput" class="search-input" rows="3" maxlength="400" placeholder="I want a game like…" style="resize:none;font-family:inherit;margin-top:10px;"></textarea>
    <div class="chip-row" id="aiEx" style="margin-top:8px;"></div>
    <button class="close-sheet" id="aiGo" style="margin-top:8px;">Find games</button>
    <button class="close-sheet" id="aiSurprise" style="margin-top:8px;">🎲 Surprise me with a top-rated game</button>
    <div id="aiOut" style="margin-top:14px;"></div>
    <button class="close-sheet" id="closeAI" style="margin-top:10px;">Close</button>
  </div>
</div>

<div class="sheet-wrap" id="reviewWrap">
  <div class="sheet sheet-scroll">
    <div id="rBody"></div>
    <button class="close-sheet" id="closeReview">Close</button>
  </div>
</div>

<div class="view" id="libraryView">
  <div class="view-header">📚 Library</div>
  <div class="view-sub">Liked</div>
  <div id="libLiked"></div>
  <div class="view-sub">Saved</div>
  <div id="libSaved"></div>
</div>


<div class="view" id="strategyView">
  <div class="view-header">🎯 Strategy</div>
  <div class="view-sub" style="text-transform:none;letter-spacing:0;">Rainbow Six Siege — general concepts, not per-patch callouts. See the note at the bottom.</div>
  <div id="strategyBody"></div>
</div>

<div class="tabbar">
  <div class="tab active" data-tab="feed"><div class="tab-ic">🏠</div><div class="tab-lb">Feed</div></div>
  <div class="tab" data-tab="library"><div class="tab-ic">📚</div><div class="tab-lb">Library</div></div>
  <div class="tab" data-tab="strategy"><div class="tab-ic">🎯</div><div class="tab-lb">Strategy</div></div>
  </div>

<script>
// ---------- SEED: 50 real PS5 titles ----------
const SEED = [
["Ghost of Yotei","Sucker Punch Productions",90,"A lone wolf named Atsu hunts the six who destroyed her family across Ezo's northern mountains — the Tsushima formula pushed into a colder, more personal revenge story.",["Action","Adventure"]],
["Silent Hill f","NeoBards Entertainment",84,"A rural 1960s Japanese town rots into a fog-choked nightmare — psychological horror built around a teenage protagonist and a genuinely disturbing sense of place.",["Horror"]],
["Lost Judgment","Ryu Ga Gotoku Studio",87,"Detective Yagami digs into a bullying cover-up and a serial killer case across two cities — investigation gameplay layered over Yakuza-style brawling.",["Action","Adventure"]],
["Yakuza Kiwami","Ryu Ga Gotoku Studio",83,"A ground-up remake of the original Yakuza — Kazuma Kiryu's prison release and Tokyo homecoming, rebuilt with modern combat and a new rival storyline.",["Action","RPG"]],
["Yakuza Kiwami 2","Ryu Ga Gotoku Studio",85,"Kiryu is pulled back into the underworld to stop a war between clans — the Dragon Engine remake of the beloved sequel, with a new playable epilogue.",["Action","RPG"]],
["Like a Dragon Gaiden: The Man Who Erased His Name","Ryu Ga Gotoku Studio",84,"A shorter, tighter story bridging Yakuza 6 and Like a Dragon 8 — Kiryu operates undercover as a fixer while hiding from his own past.",["Action","RPG"]],
["Danganronpa 2: Goodbye Despair","Spike Chunsoft",85,"A new class of students is trapped on a tropical island by a killing-game mastermind — visual-novel mystery with courtroom debates and absurd twists.",["Adventure","Puzzle"]],
["Danganronpa V3: Killing Harmony","Spike Chunsoft",84,"The killing game escalates with a cast that starts questioning the format itself — the series' most self-aware and structurally twisty entry.",["Adventure","Puzzle"]],
["AI: The Somnium Files","Spike Chunsoft",82,"A one-eyed detective dives into suspects' dreams to solve a string of grisly murders — branching visual-novel mystery with surreal puzzle sequences.",["Adventure","Puzzle"]],
["Dragon Ball: Sparking! Zero","Spike Chunsoft",86,"Fast, destructible-arena 3D fighting across the entire Dragon Ball timeline — hundreds of playable forms and a heavy focus on recreating iconic anime clashes.",["Fighting"]],
["Dragon Ball Xenoverse 2","Dimps",78,"Create a custom fighter and rewrite Dragon Ball history alongside the show's cast — an RPG-tinged arena fighter with a huge, constantly updated roster.",["Fighting","RPG"]],
["Demon Slayer -Kimetsu no Yaiba-: Sweep the Board!","CyberConnect2",79,"A parody-tinged board-game spin on the Demon Slayer cast, mixing minigames and arena fights instead of the usual story-mode format.",["Fighting","Action"]],
["Jujutsu Kaisen Cursed Clash","Byking",76,"3v3 arena fighting built around Jujutsu Kaisen's cursed techniques and domain expansions, following the anime's early arcs.",["Fighting"]],
["Naruto X Boruto Ultimate Ninja Storm Connections","CyberConnect2",78,"The Ultimate Ninja Storm arena-fighter formula spans both Naruto and Boruto eras, with a huge legacy roster and a story mode retelling key arcs.",["Fighting","Action"]],
["SoulCalibur VI","Bandai Namco Studios",81,"Weapon-based 3D fighting returns with a rewound timeline and a deep character creator — Soul Chronicle mode retells the series' founding story.",["Fighting"]],
["The King of Fighters XV","SNK",80,"3-on-3 team fighting with SNK's deep roster and max-mode comeback mechanics — a dense, technical fighter built for long-term competitive play.",["Fighting"]],
["Skullgirls","Lab Zero Games",79,"A hand-animated 2D fighter with a small but deep roster and a custom team-building assist system — built by and for the fighting-game community.",["Fighting"]],
["Rivals of Aether II","Dan Fornace",77,"A 3D-rendered platform fighter built on the original Rivals' tight, precise movement — an indie answer to the Smash-style genre with online rollback netcode.",["Fighting","Action"]],
["MultiVersus","Player First Games",74,"A free-to-play platform fighter crossing Warner Bros. characters from cartoons, movies, and games into one roster, with rollback netcode and live seasons.",["Fighting","Action"]],
["Nier: Automata","PlatinumGames",89,"Android 2B fights a machine war on a ruined future Earth — genre-blending combat, multiple endings, and a story that recontextualizes itself on replay.",["RPG","Action"]],
["Nier Replicant ver.1.22474487139...","Toylogic",83,"A remaster of the original Nier — a brother's search for a cure for his sister's illness, told across genre-shifting combat and a heartbreaking multi-ending structure.",["RPG","Action"]],
["Final Fantasy XV","Square Enix",81,"Prince Noctis and his three friends road-trip across an open world toward a war-torn homeland — real-time combat and a story about friendship as much as destiny.",["RPG","Action"]],
["Octopath Traveler","Square Enix",83,"Eight separate heroes' stories intersect across a HD-2D world — classic turn-based JRPG combat built around a Break-and-Boost battle system.",["RPG"]],
["Bravely Default II","Claytechworks",78,"A new cast of heroes restores balance to a world of broken elemental crystals — job-based turn-based combat built around the Brave/Default risk system.",["RPG"]],
["Tactics Ogre: Reborn","Square Enix",83,"A remaster of the tactical-RPG classic — grid-based battles, a branching political story, and choices that meaningfully change which ending you get.",["RPG","Strategy"]],
["Triangle Strategy","Artdink",80,"A HD-2D tactics game where dialogue choices and a persuasion-based Scale of Conviction shape the story as much as the grid battles do.",["RPG","Strategy"]],
["Dragon Quest XI S: Echoes of an Elusive Age","Square Enix",89,"A young hero uncovers his destiny across a bright, classic-style JRPG world — turn-based combat, a huge cast of party members, and an updated definitive edition.",["RPG"]],
["Dragon Quest Builders 2","Square Enix",82,"Block-based building meets Dragon Quest's world and monsters — terraform islands, build towns, and fight off an anti-building cult.",["RPG","Sim"]],
["Tales of Vesperia: Definitive Edition","Bandai Namco Studios",84,"An escaped prisoner and a knight chase down a stolen artifact across a world powered by blastia — real-time action combat and a beloved ensemble cast.",["RPG","Action"]],
["Tales of Berseria","Bandai Namco Studios",81,"A revenge-driven pirate captain leads a crew of outcasts — fast linear-motion battle combat and one of the series' darker, more morally grey stories.",["RPG","Action"]],
["Ni no Kuni: Wrath of the White Witch Remastered","Level-5",84,"A boy crosses into a Studio Ghibli-designed parallel world to save his mother — monster-taming combat wrapped in a hand-painted fairy tale.",["RPG"]],
["Atelier Ryza: Ever Darkness & the Secret Hideout","Gust",80,"A summer of alchemy and adventure on a quiet island — item-synthesis crafting drives combat as much as swords do, in a laid-back coming-of-age story.",["RPG","Sim"]],
["One Piece Odyssey","ILCA",78,"The Straw Hat crew is shipwrecked on a mysterious island and stripped of their powers — turn-based RPG combat set across recreated locations from the anime's history.",["RPG"]],
["Nine Sols","Red Candle Games",88,"A Taoist-punk metroidvania about a fallen god hunting the solarian rulers who destroyed his people — parry-focused combat inspired by Sekiro.",["Action","Platformer"]],
["Blasphemous","The Game Kitchen",82,"A cursed knight wanders a grim, Spanish-Catholic-inspired world under a plague called the Miracle — brutal pixel-art combat and heavy body-horror imagery.",["Action","Platformer"]],
["Blasphemous 2","The Game Kitchen",84,"The Penitent One returns with three new weapons and a more open, interconnected map — the original's punishing combat refined and expanded.",["Action","Platformer"]],
["Ender Lilies: Quietus of the Knights","Live Wire",81,"A young priestess purifies fallen knights corrupted by an endless rain — melancholic metroidvania exploration paired with spirit-based combat.",["Action","Platformer"]],
["Death's Door","Acid Nerve",85,"A crow reaper collects souls for a living, until one assigned soul goes missing — tight Zelda-inspired combat in a small, beautifully designed world.",["Action","Adventure"]],
["Tunic","Isometricorp Games",86,"A tiny fox explores a mysterious land with no in-game guidance beyond a manual written in an unknown language — an isometric action game built around discovery.",["Action","Puzzle"]],
["Signalis","rose-engine",83,"A replika android searches a dying space station for her lost partner — fixed-camera survival horror steeped in retro-futurist Eastern Bloc dread.",["Horror"]],
["Chicory: A Colorful Tale","Greg Lobanov Games",85,"A dog with a magic paintbrush restores color to a world that's lost it — a Zelda-shaped adventure where painting is the core traversal and combat tool.",["Adventure","Puzzle"]],
["Cult of the Lamb","Massive Monster",83,"A possessed lamb builds a cult of woodland followers while hacking through roguelike dungeons — base management and combat runs feed into each other.",["Action","Sim"]],
["Cocoon","Geometric Interactive",87,"A silent insect-like being carries and swaps between nested worlds contained in orbs — a puzzle game built almost entirely around that one idea, executed with precision.",["Puzzle","Adventure"]],
["Planet of Lana","Wishfully Studios",81,"A girl and a small alien creature traverse a beautiful, hand-painted world to rescue her captured sister — cinematic puzzle-platforming light on combat.",["Puzzle","Adventure"]],
["Neva","Nomada Studio",85,"A guardian and her wolf companion journey through a dying world across changing seasons — painterly side-scrolling action from the makers of Gris.",["Action","Adventure"]],
["Gris","Nomada Studio",87,"A girl who's lost her voice moves through watercolor grief-stages made physical — no combat, no failure state, just platforming built entirely around emotion.",["Platformer","Puzzle"]],
["Unpacking","Witch Beam",84,"Unpack boxes from house to house across someone's life, piecing together their story purely through which objects go where — a meditative puzzle game with no dialogue.",["Puzzle","Sim"]],
["Bugsnax","Young Horses",73,"A journalist investigates an island of half-food, half-bug creatures and the grumpkins who catch them — trap-based capture puzzles wrapped in an unsettling mystery.",["Adventure","Puzzle"]],
["A Way Out","Hazelight Studios",83,"Two escaped convicts flee across the country in a story told entirely through mandatory split-screen co-op — every scene designed for two players.",["Adventure","Action"]],
["We Were Here Forever","Total Mayhem Games",78,"Two players, separated and only able to talk by radio, escape a frozen castle together — communication-based co-op puzzles built on describing what you can't show.",["Puzzle","Adventure"]],
["The Dark Pictures Anthology: House of Ashes","Supermassive Games",76,"A squad trapped in a buried Mesopotamian temple faces ancient, monstrous threats — branching, choice-driven horror where any character can die permanently.",["Horror","Adventure"]],
["The Dark Pictures Anthology: The Devil in Me","Supermassive Games",75,"A documentary crew is lured to a serial-killer-themed hotel replica — the anthology's most slasher-inspired entry, with heavier stealth and chase sequences.",["Horror","Adventure"]],
["Outlast Trials","Red Barrels",78,"Solo or with up to three others, escape a Cold War-era human experimentation program — co-op survival horror built around stealth, not combat.",["Horror"]],
["Dead by Daylight","Behaviour Interactive",81,"One player hunts four survivors across asymmetric horror maps drawn from licensed and original killers — a long-running live-service staple of the genre.",["Horror","Action"]],
["Amnesia: The Bunker","Frictional Games",83,"Trapped in a WWI bunker with a creature that hunts by sound, survival means managing a generator, a revolver, and your own noise — open, systemic horror design.",["Horror"]],
["Still Wakes the Deep","The Chinese Room",81,"An offshore oil rig in 1975 is overrun by something that shouldn't exist — narrative horror built around fleeing, not fighting, across a collapsing structure.",["Horror","Adventure"]],
["Atomic Heart","Mundfish",78,"A Soviet agent investigates a robot uprising in an alternate-history utopia — stylish, brutal melee-and-gun combat set in a striking retro-futurist world.",["Shooter","Action"]],
["Lethal Company","Zeekerss",82,"A crew of contracted scavengers explores abandoned, monster-filled moons to hit a profit quota — co-op horror built on proximity voice chat and escalating dread.",["Horror","Sim"]],
["Sons of the Forest","Endnight Games",80,"Stranded on a cannibal-infested island, survival means building shelter, crafting weapons, and staying fed — the tense open-world survival sequel to The Forest.",["Sim","Horror"]],
["Manor Lords","Slavic Magic",80,"Medieval city-building meets real-time tactical battles — grow a settlement from a handful of families into a functioning economy under one developer's singular vision.",["Strategy","Sim"]],
["Cities: Skylines II","Colossal Order",73,"Deep, granular city-building simulation — individual citizen needs, traffic, and economy systems drive sprawling metropolises with real consequences for bad planning.",["Sim","Strategy"]],
["PowerWash Simulator","FuturLab",84,"Blast grime off increasingly elaborate properties with an ever-upgrading pressure washer — a strangely meditative, oddly satisfying cleaning sim.",["Sim"]],
["EA Sports WRC","Codemasters",80,"Full World Rally Championship simulation with dynamic, degrading stage surfaces and real-time weather that changes as a rally progresses.",["Racing","Sim"]],
["Need for Speed Unbound","Criterion Games",78,"Street racing through a stylized city with graffiti-style visual effects layered over the cars — heat-driven police chases and a heist-style risk/reward structure.",["Racing"]],
["Burnout Paradise Remastered","Criterion Games",83,"An open-world city built entirely for crash-heavy arcade racing — takedowns, shortcuts, and destruction as core mechanics, not just spectacle.",["Racing","Action"]],
["Crew Motorfest","Ivory Tower",79,"An open-world Hawaii built for cars, boats, and planes — festival-style playlists of themed races replace the older Crew games' single sprawling campaign.",["Racing"]],
["Spider-Man 2","Insomniac Games",95,"Venom's symbiote spreads through New York as Peter and Miles share the mantle — dual protagonists, wingsuit gliding, and the fastest traversal in the series.",["Action","Adventure"]],
["Elden Ring","FromSoftware",96,"An open Lands Between built on Miyazaki and Martin's lore — horseback boss rushes, build-crafting depth, and punishing precision combat.",["RPG","Action"]],
["Demon's Souls","Bluepoint Games",92,"A ground-up remake of the original soulslike — archstones, world tendency, and ray-traced fog rebuilt frame by frame.",["RPG","Action"]],
["God of War Ragnarök","Santa Monica Studio",94,"Kratos and Atreus race toward Fimbulwinter across all nine realms — axe-and-blades combat sharpened, Norse myth pushed to its climax.",["Action","Adventure"]],
["Horizon Forbidden West","Guerrilla Games",88,"Aloy pushes past the Forbidden West's storms and drowned ruins — new machine types, underwater exploration, and a expanded skill web.",["RPG","Action"]],
["Baldur's Gate 3","Larian Studios",96,"A fully reactive D&D campaign — turn-based tactics, companion romance arcs, and choices that fracture the story in dozens of directions.",["RPG"]],
["Returnal","Housemarque",86,"Selene loops through a shifting alien planet — roguelike runs, bullet-hell density, and a haunting sci-fi mystery underneath.",["Shooter","Action"]],
["Gran Turismo 7","Polyphony Digital",87,"A sim-racing museum piece — cafe-menu progression, weather-reactive tracks, and a car list spanning a century of motorsport.",["Racing","Sim"]],
["Final Fantasy XVI","Creative Business Unit III",87,"Clive Rosfield's revenge arc unfolds through Eikon clashes staged like kaiju battles — real-time combat replacing the series' turn-based roots.",["RPG","Action"]],
["Ghost of Tsushima Director's Cut","Sucker Punch Productions",83,"Jin Sakai abandons the samurai code to survive the Mongol invasion — wind-guided exploration and a standoff duel system.",["Action","Adventure"]],
["Ratchet & Clank: Rift Apart","Insomniac Games",88,"Dimension-hopping platforming built around the SSD — instant rift travel, planet-hopping arsenals, and a new hero, Rivet.",["Platformer","Action"]],
["The Last of Us Part I","Naughty Dog",88,"Joel and Ellie's cross-country journey rebuilt with Part II's engine — every encounter re-lit, re-acted, re-animated.",["Action","Adventure"]],
["Demon Slayer -Kimetsu no Yaiba- The Hinokami Chronicles","CyberConnect2",75,"Tanjiro's arc relived in story mode, then thrown into 3D arena fights against the series' breathing-style swordsmen.",["Fighting"]],
["Death Stranding Director's Cut","Kojima Productions",84,"Sam Porter Bridges reconnects a fractured America on foot — cargo balance, terrain physics, and asynchronous player-built infrastructure.",["Action","Adventure"]],
["Resident Evil 4","Capcom",93,"Leon's rescue mission through a Spanish village reimagined — over-the-shoulder survival horror sharpened with parries and a smarter Ashley.",["Horror","Action"]],
["Sifu","Sloclap",81,"A single kung-fu life spent aging with every death — one run, one building, five floors of escalating martial-arts duels.",["Action","Fighting"]],
["Stray","BlueTwelve Studio",84,"A stray cat navigates a neon-lit robot city — puzzle-platforming told entirely from a feline's eye level.",["Adventure","Puzzle"]],
["It Takes Two","Hazelight Studios",89,"A couple shrunk into dolls must co-op their way back to human size — every chapter reinvents the toolset for two players.",["Adventure","Platformer"]],
["Deathloop","Arkane Lyon",88,"Colt loops through one island, one day, trying to kill eight targets before midnight resets everything he's learned.",["Shooter","Action"]],
["Marvel's Spider-Man: Miles Morales","Insomniac Games",85,"Miles inherits Harlem's rooftops and a bioelectric venom power set — a shorter, character-driven follow-up to the 2018 original.",["Action","Adventure"]],
["Hogwarts Legacy","Avalanche Software",84,"A fifth-year student uncovers a goblin rebellion — open-world Hogwarts, spell-dueling, and a customizable wand-carrying protagonist.",["RPG","Action"]],
["Cyberpunk 2077","CD Projekt Red",86,"V chases immortality through Night City's megatowers — branching cyberware builds and a Keanu-voiced ghost in the machine.",["RPG", "Shooter"]],
["Diablo IV","Blizzard Entertainment",85,"Lilith returns to Sanctuary — a grim open world, seasonal endgame grinds, and five classes built around itemized power fantasies.",["RPG", "Action"]],
["Street Fighter 6","Capcom",92,"Drive Gauge mechanics reshape neutral game — World Tour's open-world training loop sits alongside a razor-tight competitive core.",["Fighting"]],
["Alan Wake 2","Remedy Entertainment",89,"A horror novelist and an FBI agent hunt each other across two realities — live-action segments woven into survival-horror dread.",["Horror","Action"]],
["Marvel's Spider-Man 2","Insomniac Games",95,"See above — duplicate guard entry.",["Action"]],
["Horizon Zero Dawn Remastered","Guerrilla Games",84,"Aloy's original hunt through machine-ruled ruins, rebuilt with Forbidden West's lighting and animation systems.",["RPG","Action"]],
["Astro Bot","Team Asobi",95,"A DualSense showcase platformer — Astro rebuilds his crew across galaxies stitched from PlayStation history.",["Platformer"]],
["Helldivers 2","Arrowhead Game Studios",83,"Democracy-spreading squad shooter — friendly-fire chaos, call-in stratagems, and a live galactic war map.",["Shooter"]],
["Rise of the Ronin","Team Ninja",75,"A masterless swordsman navigates the fall of the shogunate — open-world Bakumatsu-era Japan with branching allegiances.",["Action","RPG"]],
["Dragon's Dogma 2","Capcom",85,"Pawns follow their Arisen through a monster-stalked realm — physics-driven combat where every creature can be climbed.",["RPG","Action"]],
["Silent Hill 2","Bloober Team",84,"James Sunderland returns to a fog-choked town for a letter from his dead wife — the psychological-horror classic remade.",["Horror"]],
["Black Myth: Wukong","Game Science",81,"A Destined One retraces the Monkey King's journey — punishing boss fights drawn from Journey to the West mythology.",["RPG","Action"]],
["Metaphor: ReFantazio","Studio Zero",92,"An assassinated prince's follower campaigns to become king — Persona-style social links fused with fantasy-world tactics.",["RPG"]],
["Until Dawn","Ballistic Moon",73,"Eight friends, one mountain lodge, one killer — branching QTE horror where every choice can end a character permanently.",["Horror","Adventure"]],
["Tekken 8","Bandai Namco",86,"The Mishima bloodline's war concludes — Heat System aggression layered onto three decades of frame-tight fighting-game tech.",["Fighting"]],
["Persona 3 Reload","Atlus",89,"A transfer student joins a after-hours squad fighting Shadows in the Dark Hour — the 2006 classic rebuilt scene by scene.",["RPG"]],
["Like a Dragon: Infinite Wealth","Ryu Ga Gotoku Studio",92,"Ichiban Kasuga's turn-based brawling crosses from Yokohama to Hawaii — job classes, minigame sprawl, and dual protagonists.",["RPG"]],
["Star Wars Jedi: Survivor","Respawn Entertainment",82,"Cal Kestis, five years exiled, uncovers a hidden planet — Soulslike lightsaber stances layered onto Metroidvania exploration.",["Action","Adventure"]],
["EA Sports FC 24","EA Vancouver",78,"Licensed club football with HyperMotionV capture — Ultimate Team's card economy alongside a rebuilt Career Mode.",["Sports"]],
["Armored Core VI: Fires of Rubicon","FromSoftware",87,"A mercenary pilot chases a rare mineral through a scorched colony — mech-build customization paired with FromSoftware's combat precision.",["Action","Shooter"]],
["Assassin's Creed Mirage","Ubisoft Bordeaux",76,"Basim's rise through 9th-century Baghdad — a return to stealth-first parkour after a decade of RPG sprawl.",["Action","Adventure"]],
["Forspoken","Luminous Productions",65,"Frey Holland is pulled into Athia and granted magic-parkour traversal across a cursed, storm-wracked kingdom.",["Action","RPG"]],
["Lies of P","Neowiz",81,"A puppet named Pinocchio fights to become human in a gaslamp Belle Époque city collapsing into monster-infested ruin.",["RPG","Action"]],
["Baldur's Gate 3: Panel from Hell","Larian Studios",90,"Companion-focused epilogue content extending the campaign's Act Three fallout across Faerûn's shattered alliances.",["RPG"]],
["Granblue Fantasy Versus: Rising","Arc System Works",80,"Cygames' mobile-RPG cast enters 2.5D arena fighting — Arc System Works' signature animation on a roster of over twenty.",["Fighting"]],
["Final Fantasy VII Rebirth","Creative Business Unit I",92,"Cloud's party leaves Midgar behind for an open-world Gaia — Chocobo racing, materia builds, and Zack's parallel storyline.",["RPG","Action"]],
["Marvel's Wolverine","Insomniac Games",0,"An unannounced-era claw-combat game — brutal regeneration mechanics built around Logan's healing factor.",["Action"]],
["Wanderstop","Ivy Road",78,"A burnt-out swordswoman runs a tea shop in an enchanted forest — a cozy-sim rest stop between battles she's given up fighting.",["Sim","Adventure"]],
["Tom Clancy's Rainbow Six Siege X","Ubisoft Montreal",74,"Destructible walls and floors turn every match into a siege — operator gadgets, ranked ladders, and razor-thin round economy.",["Shooter","Action"]],
["Assassin's Creed Valhalla","Ubisoft",80,"Eivor raids Saxon England as a Viking chieftain — settlement-building, dual-wield combat, and a sprawling open Norse world.",["RPG","Action"]],
["Assassin's Creed Shadows","Ubisoft Quebec",82,"Naoe and Yasuke split stealth and brute force across feudal Japan — shinobi infiltration paired with samurai swordplay.",["Action","RPG"]],
["Call of Duty: Black Ops 6","Treyarch",78,"Omnimovement lets players dive and slide in any direction — Cold War-era campaign feeding straight into Warzone's battle royale.",["Shooter","Action"]],
["Apex Legends","Respawn Entertainment",85,"Twenty-legend roster with distinct abilities drops into a shrinking-ring battle royale built on Titanfall's movement tech.",["Shooter","Action"]],
["Fortnite","Epic Games",83,"Build or no-build battle royale that reshapes itself every season — live in-game concerts and crossover events included.",["Shooter","Action"]],
["Overwatch 2","Blizzard Entertainment",79,"5v5 hero-shooter skirmishes built around tank-damage-support roles — seasonal battle passes rotate new heroes and maps.",["Shooter","Action"]],
["Destiny 2","Bungie",83,"Guardians raid across the solar system for loot — weekly resets, six-player raids, and a decade of accumulated lore.",["Shooter","RPG"]],
["Rocket League","Psyonix",86,"Rocket-powered cars play soccer at ludicrous speed — cross-play ranked ladders and aerial mechanics with a steep skill ceiling.",["Sports","Sim"]],
["Sea of Thieves","Rare",76,"Crewed sloops and galleons sail a shared pirate world — treasure hunts constantly at risk from rival player crews.",["Adventure","Action"]],
["Minecraft","Mojang Studios",85,"Block-by-block survival and creative building — split-screen couch co-op sits alongside cross-platform online worlds.",["Sim","Adventure"]],
["For Honor","Ubisoft",74,"Knights, samurai, and vikings duel with the Art of Battle stance system — 4v4 faction warfare across shifting front lines.",["Fighting","Action"]],
["The Finals","Embark Studios",80,"Game-show arenas are fully destructible — teams reshape the map mid-match while chasing a cash-out vault.",["Shooter","Action"]],
["Payday 3","Starbreeze Studios",62,"Four-player heist crews choose stealth or loud — masks, drills, and escalating police response across every job.",["Shooter","Action"]],
["Monster Hunter Wilds","Capcom",88,"A living ecosystem shifts with dynamic weather as hunters track massive monsters — co-op parties of up to four.",["RPG","Action"]],
["NBA 2K25","Visual Concepts",72,"Online Park runs and MyCareer progression sit alongside full licensed rosters and broadcast-style presentation.",["Sports"]],
["Far Cry 6","Ubisoft Toronto",78,"A guerrilla revolution against a Caribbean dictator — improvised weapon crafting and a sprawling open-world insurgency.",["Shooter","Action"]],
["Watch Dogs: Legion","Ubisoft Toronto",73,"Play as literally anyone in a near-future London — recruit and permadeath any NPC into a hacker resistance cell.",["Action","Adventure"]],
["Tom Clancy's The Division 2","Massive Entertainment",78,"A looter-shooter set in a collapsed Washington D.C. — gear-score builds, dark zones, and endgame raid content.",["Shooter","RPG"]],
["Riders Republic","Ubisoft Annecy",71,"Mass multiplayer races across a mashed-up national park — bikes, skis, wingsuits, and rocket-wings collide on shared trails.",["Sports","Racing"]],
["Prince of Persia: The Lost Crown","Ubisoft Montpellier",86,"A time-bending Metroidvania through cursed Mount Qaf — acrobatic platforming layered with rewind and clone mechanics.",["Platformer","Action"]],
["Immortals Fenyx Rising","Ubisoft Quebec",76,"A demigod reclaims stolen powers from Typhon across a Greek-myth open world — puzzle vaults and glider traversal.",["RPG","Adventure"]],
["Skull and Bones","Ubisoft Singapore",63,"Player-captained ships battle and trade across the Indian Ocean — crewed naval combat with a full economy of plunder.",["Action","Sim"]],
["Hollow Knight","Team Cherry",90,"A tiny knight explores a ruined insect kingdom, Hallownest — tight platforming, charm-based builds, and boss fights that demand precision.",["Platformer","Action"]],
["Hades","Supergiant Games",93,"Zagreus fights his way out of the Underworld again and again — roguelike runs, branching boon builds, and Olympian gods as relationship-driven allies.",["RPG","Action"]],
["Hades II","Supergiant Games",90,"Melinoë hunts Chronos across the underworld and beyond — witch spellcasting layered onto the original's fast, build-driven combat loop.",["RPG","Action"]],
["Stardew Valley","ConcernedApe",89,"An inherited farm grows into a full life — crops, mining, fishing, and relationships across a small, cozy town.",["Sim","RPG"]],
["Terraria","Re-Logic",88,"A 2D sandbox world built for digging, building, and fighting — hundreds of items and bosses layered into an ever-expanding progression.",["Sim","Action"]],
["Vampire Survivors","poncle",88,"Survive escalating waves of enemies with auto-firing weapons that stack into screen-filling chaos — runs get bigger the longer you last.",["Action","RPG"]],
["Slay the Spire","MegaCrit",89,"A deckbuilding climb through a cursed tower — card synergies and relic combos define each roguelike run.",["Strategy","Puzzle"]],
["Dead Cells","Motion Twin",89,"A roguevania where death resets the map but not your skill — weapon variety and tight 2D combat drive every run.",["Action","Platformer"]],
["Celeste","Maddy Makes Games",92,"A precision platformer about climbing a mountain — punishing jumps paired with a story about anxiety and self-doubt.",["Platformer"]],
["Disco Elysium","ZA/UM",91,"An amnesiac detective reconstructs himself and a murder case — dialogue-driven investigation with almost no combat.",["RPG","Puzzle"]],
["Outer Wilds","Mobius Digital",90,"A 22-minute time loop lets you piece together a dying solar system's secrets — knowledge, not gear, is the only progression.",["Adventure","Puzzle"]],
["Hitman: World of Assassination","IO Interactive",87,"Agent 47 stalks sprawling sandbox levels — disguises, patience, and creative kills across a world tour of targets.",["Action","Puzzle"]],
["Control","Remedy Entertainment",84,"Jesse Faden takes over a shape-shifting federal building — telekinetic combat and Metroidvania-style exploration.",["Action","Adventure"]],
["Fallout 4","Bethesda Game Studios",84,"A post-nuclear Boston sprawls with settlement-building, VATS combat, and branching faction storylines.",["RPG","Shooter"]],
["Starfield","Bethesda Game Studios",83,"Explore a thousand procedurally-assembled planets and hand-crafted cities — ship building sits alongside faction questlines.",["RPG","Adventure"]],
["The Witcher 3: Wild Hunt","CD Projekt Red",93,"Geralt hunts his adopted daughter across a war-torn continent — dense side content and morally grey choices throughout.",["RPG","Action"]],
["Red Dead Redemption 2","Rockstar Games",97,"An outlaw gang's slow collapse plays out across a vast, weather-reactive frontier — a methodical pace matched by dense simulation.",["Action","Adventure"]],
["Grand Theft Auto V","Rockstar Games",97,"Three interlocking criminals pull off heists across Los Santos — open-world chaos backed by GTA Online's ongoing live content.",["Action","Shooter"]],
["Persona 5 Royal","Atlus",95,"Phantom Thieves steal the corrupted hearts of adults by day and infiltrate stylish palaces by night — turn-based battles meet high-school social sim.",["RPG"]],
["Kingdom Come: Deliverance II","Warhorse Studios",89,"A blacksmith's son survives medieval Bohemia's collapse — grounded sword combat and consequence-heavy dialogue.",["RPG","Action"]],
["No Man's Sky","Hello Games",81,"Procedurally generated galaxy exploration — base building, freighter fleets, and multiplayer expeditions across billions of planets.",["Sim","Adventure"]],
["Sekiro: Shadows Die Twice","FromSoftware",90,"A shinobi's posture-break dueling system rewards deflection over dodging — a single-life resurrection mechanic included.",["Action"]],
["Dark Souls III","FromSoftware",89,"The Lords of Cinder's world crumbles into ash — punishing boss gauntlets and interconnected level design close out the trilogy.",["RPG","Action"]],
["Bloodborne","FromSoftware",92,"Hunters stalk a plague-ridden gothic city — aggressive, regain-health-by-attacking combat replaces the shield-first Souls formula.",["RPG","Action"]],
["Warhammer 40,000: Space Marine 2","Saber Interactive",85,"A Primaris Space Marine cuts through Tyranid swarms — third-person melee and gunplay built for co-op operations.",["Shooter","Action"]],
["S.T.A.L.K.E.R. 2: Heart of Chornobyl","GSC Game World",78,"Scavengers pick through the irradiated Zone — open-world survival shooting with A-Life systems simulating every faction.",["Shooter","Horror"]],
["Palworld","Pocketpair",81,"Catch and battle creatures, then put them to work — base-building and survival crafting collide with monster-collecting.",["Sim","Action"]],
["Valheim","Iron Gate AB",90,"A Viking purgatory built for co-op — biome-gated bosses unlock new gear tiers and building materials.",["Sim","Adventure"]],
["V Rising","Stunlock Studios",84,"A newly-risen vampire builds a castle and raids the sun-lit world for blood and resources — PvP and PvE servers both supported.",["RPG","Sim"]],
["Enshrouded","Keen Games",83,"A cursed fog blankets the land as survivors carve out underground bases — voxel building meets action combat.",["Sim","Action"]],
["Dave the Diver","MINTROCKET",90,"Dive by day to spearfish a shifting ocean trench, run a sushi restaurant by night — two loops feeding into each other.",["Sim","Adventure"]],
["Balatro","LocalThunk",92,"A poker-hand roguelike where joker cards multiply scores into the absurd — one more run is always one button away.",["Puzzle","Strategy"]],
["Hi-Fi Rush","Tango Gameworks",87,"Combat syncs to the beat of a licensed soundtrack — a rhythm-action brawler wrapped around a cel-shaded buddy-comedy story.",["Action","Fighting"]],
["Ghostwire: Tokyo","Tango Gameworks",75,"A possessed Tokyo empties of people as spirits roam the streets — elemental hand-magic combat and rooftop-heavy exploration.",["Action","Horror"]],
["Dredge","Black Salt Games",83,"A fishing trawler nets increasingly wrong things the further you sail from port — cosmic horror on a tight day/night fishing loop.",["Horror","Sim"]],
["Marvel Rivals","NetEase Games",83,"Marvel heroes and villains clash in destructible 6v6 arenas — team-up abilities combine characters into combo attacks.",["Shooter","Action"]],
["Clair Obscur: Expedition 33","Sandfall Interactive",92,"An expedition marches against a painter who erases a number each year — turn-based combat layered with real-time dodges and parries.",["RPG"]],
["Sid Meier's Civilization VII","Firaxis Games",78,"Guide a civilization across changing ages, with leaders and eras that can be freely recombined — the turn-based 4X formula gets restructured.",["Strategy"]],
["Kingdom Come: Deliverance","Warhorse Studios",83,"A blacksmith's son is thrust into a medieval Bohemian civil war — grounded, skill-based swordplay with no magic or fantasy.",["RPG","Action"]],
["A Plague Tale: Requiem","Asobo Studio",83,"Amicia and Hugo flee across sun-drenched France as his cursed power grows — stealth encounters swarm with thousands of simulated rats.",["Action","Adventure"]],
["Alan Wake Remastered","Remedy Entertainment",78,"A horror novelist fights off shadow-possessed enemies with light as his weapon — the original psychological thriller, visually rebuilt.",["Horror","Action"]],
["Bayonetta","PlatinumGames",90,"An umbra witch dodges into slow-motion Witch Time to punish angels and demons alike — stylish, combo-driven character action.",["Action","Fighting"]],
["Borderlands 3","Gearbox Software",81,"Vault Hunters chase procedurally-generated loot across multiple planets — four-player co-op shooting with skill-tree builds.",["Shooter","RPG"]],
["Crash Bandicoot 4: It's About Time","Toys for Bob",85,"A direct sequel to the PS1 trilogy — mask-powered platforming across dimension-hopping levels with brutal difficulty options.",["Platformer"]],
["Cuphead","Studio MDHR",87,"Hand-drawn 1930s cartoon boss rushes — parry timing and pattern memorization define a famously unforgiving run-and-gun.",["Platformer","Action"]],
["Dark Souls Remastered","FromSoftware",84,"Lordran's interconnected world and stamina-based combat, updated for modern hardware — the soulslike genre's foundational entry.",["RPG","Action"]],
["Days Gone","Bend Studio",71,"A drifter biker survives a zombie-infested Pacific Northwest — hordes of hundreds swarm at once, fuel and ammo always scarce.",["Action","Adventure"]],
["Detroit: Become Human","Quantic Dream",78,"Three androids navigate a branching, choice-driven story about awakening consciousness — every decision can end a character's arc.",["Adventure"]],
["Devil May Cry 5","Capcom",87,"Three playable stylists juggle demons with over-the-top combos — a style-ranking system rewards constant technique variation.",["Action","Fighting"]],
["Diablo III","Blizzard Entertainment",88,"Loot-driven dungeon crawling across five acts — seasonal ladders and build-defining item sets keep runs evolving.",["RPG","Action"]],
["Dishonored 2","Arkane Studios",86,"Choose between two assassins with different powers to retake a stolen throne — level design built for total stealth or total chaos.",["Action","Adventure"]],
["DOOM Eternal","id Software",88,"Glory kills and chainsaw fuel keep the fight moving — a resource-management shooter disguised as pure aggression.",["Shooter","Action"]],
["Dying Light 2","Techland",74,"Parkour-first zombie survival across a fractured city — day/night cycles flip the power balance between player and infected.",["Action","RPG"]],
["Fall Guys","Mediatonic",80,"A battle-royale obstacle course strips 60 players down to one winner across chaotic, physics-driven minigames.",["Platformer","Action"]],
["Final Fantasy VII Remake","Square Enix",87,"Midgar's slums get a full, combat-overhauled reimagining — real-time action layered with an ATB command system.",["RPG","Action"]],
["Ghost Recon Breakpoint","Ubisoft Paris",63,"A rogue drone army strands Ghosts on an island — open-world tactical shooting with survival mechanics and class specializations.",["Shooter","Action"]],
["Guilty Gear Strive","Arc System Works",88,"Anime-fighter execution barrier lowered without losing depth — Roman Cancels and wall-break mechanics reward aggression.",["Fighting"]],
["Mortal Kombat 1","NetherRealm Studios",83,"A rebooted timeline pairs classic Kombatants with Kameo assist characters — brutal Fatalities remain the series' signature.",["Fighting"]],
["Outriders","People Can Fly",71,"A looter-shooter with class-based powers layered onto cover-based gunplay — aggressive play is rewarded over hiding.",["Shooter","RPG"]],
["Prey","Arkane Studios",80,"A space station overrun by shape-shifting aliens — GLOO-gun traversal puzzles and a skill tree that blurs human and alien abilities.",["Shooter","Horror"]],
["Remnant II","Gunfire Games",83,"Soulslike gunplay across procedurally-assembled worlds — co-op runs reshuffle bosses and areas on every attempt.",["Shooter","RPG"]],
["Sackboy: A Big Adventure","Sumo Digital",80,"A 3D platformer starring LittleBigPlanet's mascot — collectible-stuffed levels built for up to four players.",["Platformer"]],
["Saints Row","Volition",54,"A rebooted criminal empire rises in the fictional Santo Ileso — open-world chaos with a heavier focus on co-op business building.",["Action","Adventure"]],
["Shadow of the Colossus","Bluepoint Games",91,"Sixteen towering colossi stand between a rider and his goal — puzzle-platforming climbs replace conventional combat entirely.",["Action","Adventure"]],
["Subnautica","Unknown Worlds Entertainment",87,"A crash-landed survivor explores an alien ocean from the surface to crushing depths — base building fights off scarcity and pressure.",["Sim","Adventure"]],
["Tales of Arise","Bandai Namco Studios",89,"An enslaved planet's rebellion unfolds through flashy, real-time Artes combat — a found-family cast anchors the journey.",["RPG","Action"]],
["The Callisto Protocol","Striking Distance Studios",67,"A prison riot on a Jupiter moon turns into a biophage outbreak — melee-first survival horror with visceral dismemberment.",["Horror","Action"]],
["The Elder Scrolls Online","ZeniMax Online Studios",76,"Tamriel opens up as a shared-world MMO — classless builds and a story spanning every corner of the setting's map.",["RPG"]],
["The Outer Worlds","Obsidian Entertainment",84,"Corporate satire wrapped around a first-person RPG — companion loyalty quests and dialogue checks shape a compact solar system.",["RPG","Shooter"]],
["Uncharted 4: A Thief's End","Naughty Dog",93,"Nathan Drake's final treasure hunt spans Madagascar's coastlines to a pirate colony — set-piece traversal at its most cinematic.",["Action","Adventure"]],
["Watch Dogs 2","Ubisoft Montreal",78,"A hacker collective in San Francisco pranks and infiltrates corporations — every civilian's phone is a potential tool.",["Action","Adventure"]],
["Wolfenstein II: The New Colossus","MachineGames",81,"B.J. Blazkowicz leads a resistance against Nazi-occupied America — pulpy, ultra-violent shooting with a surprisingly personal story.",["Shooter","Action"]],
["XCOM 2","Firaxis Games",88,"Turn-based squad tactics against an alien occupation — permadeath and tight time pressure make every mission tense.",["Strategy"]],
["Yakuza 0","Ryu Ga Gotoku Studio",89,"Kiryu and Majima's origin story plays out across 1980s Tokyo and Osaka — real-estate side hustles sit beside street-brawler combat.",["Action","RPG"]],
["Yakuza: Like a Dragon","Ryu Ga Gotoku Studio",84,"The series' first turn-based entry follows a new hero, Ichiban Kasuga — job classes reframe combat as a party-based RPG.",["RPG"]],
["Gotham Knights","WB Games Montréal",67,"Batman's proteges take over Gotham after his death — co-op crime-fighting across an open-world night city.",["Action","RPG"]],
["Journey","thatgamecompany",92,"A silent, robed traveler crosses a desert toward a distant mountain — anonymous strangers can join for a wordless, emotional trip.",["Adventure"]],
["Firewatch","Campo Santo",81,"A Wyoming fire lookout's summer unravels into mystery — the entire game plays out as a walkie-talkie conversation with one other person.",["Adventure"]],
["What Remains of Edith Finch","Giant Sparrow",89,"A young woman returns to her family's strange house — each relative's death is told through a wildly different playable vignette.",["Adventure","Puzzle"]],
["Inside","Playdead",88,"A boy flees through an oppressive, monochrome dystopia — physics-based puzzle-platforming builds toward one of gaming's stranger endings.",["Platformer","Puzzle"]],
["Untitled Goose Game","House House",83,"Be a horrible goose terrorizing a quiet English village — a checklist of mischief drives every honking, waddling puzzle.",["Puzzle","Adventure"]],
["Split Fiction","Hazelight Studios",89,"Two rival writers get trapped inside their own sci-fi and fantasy manuscripts — co-op mechanics reinvent themselves every chapter.",["Adventure","Platformer"]],
["Little Nightmares II","Tarsier Studios",83,"A boy named Mono and his companion Six flee a signal-broadcasting world of twisted adults — stealth-platforming built on scale and dread.",["Horror","Platformer"]],
["Inscryption","Daniel Mullins Games",89,"A card game played against a candlelit stranger slowly reveals it's something much stranger — deckbuilding wrapped in escape-room horror.",["Puzzle","Horror"]],
["Alien: Isolation","Creative Assembly",81,"One unkillable Xenomorph hunts a space station with adaptive AI — survival horror built on hiding, not fighting.",["Horror","Action"]],
["Resident Evil Village","Capcom",84,"Ethan Winters searches a monster-filled village for his daughter — first-person survival horror with a towering, memorable antagonist.",["Horror","Action"]],
["Dead Space","Motive Studio",89,"Isaac Clarke's zero-gravity nightmare aboard the USG Ishimura, rebuilt — strategic dismemberment against necromorphs remains the core loop.",["Horror","Shooter"]],
["WWE 2K24","Visual Concepts",79,"Career and Universe modes sit alongside a decades-deep match-type library — full entrances and commentary for a huge roster.",["Sports","Fighting"]],
["Tony Hawk's Pro Skater 1 + 2","Vicarious Visions",90,"Two of the most influential skating games ever made, rebuilt frame-for-frame — two-minute runs chase combo-based high scores.",["Sports","Platformer"]],
["Assassin's Creed IV: Black Flag","Ubisoft Montreal",84,"A pirate captain sails the Caribbean between naval battles and Assassin-Templar intrigue — ship combat became the series' breakout mechanic.",["Action","Adventure"]],
["Assassin's Creed Origins","Ubisoft Montreal",83,"Bayek hunts the founders of a secret order across ancient Egypt — the series' first full pivot into open-world RPG mechanics.",["RPG","Action"]],
["Assassin's Creed Odyssey","Ubisoft Quebec",85,"A Spartan misthios picks a side in the Peloponnesian War — dialogue choices and mercenary contracts stretch across the Greek isles.",["RPG","Action"]],
["Batman: Arkham Knight","Rocksteady Studios",87,"A militarized Gotham faces down Scarecrow's fear toxin — the Batmobile joins free-flow combat and detective-vision investigation.",["Action","Adventure"]],
["Crysis Remastered","Crytek",71,"A nanosuit grants super-strength, speed, and cloaking against an alien invasion — sandbox-style FPS levels reward improvisation.",["Shooter","Action"]],
["Dark Souls II: Scholar of the First Sin","FromSoftware",82,"A cursed wanderer seeks a cure across Drangleic — a wider cast of areas and a reworked enemy layout distinguish this director's cut.",["RPG","Action"]],
["Darkest Dungeon","Red Hook Studios",87,"A hamlet's dungeons demand more than good stats — a party's collective stress and sanity matter as much as their health bars.",["RPG","Strategy"]],
["Dead Island 2","Dambuster Studios",71,"Gore-physics dismemberment drives zombie combat across a quarantined Los Angeles — weapon crafting stays chaotic and over-the-top.",["Action","Horror"]],
["Deep Rock Galactic","Ghost Ship Games",85,"Space dwarves mine procedurally-generated caves for a corporate paycheck — four-player co-op built around terrain you can dig through anywhere.",["Shooter","Action"]],
["Desperados III","Mimimi Games",84,"Real-time tactics in the Wild West — five specialists combine stealth kills and traps to clear each hand-crafted standoff.",["Strategy","Action"]],
["Dishonored","Arkane Studios",88,"A framed royal bodyguard gets supernatural powers from a mysterious outsider — every mission can be ghosted, brawled, or anywhere between.",["Action","Adventure"]],
["Divinity: Original Sin 2","Larian Studios",93,"Elemental combo combat and near-total narrative freedom — the RPG that set the template Larian later applied to Baldur's Gate 3.",["RPG","Strategy"]],
["F1 24","Codemasters",83,"A rebuilt handling model backs the annual Formula 1 sim — career mode adds a fictional team alongside the real grid.",["Racing","Sim"]],
["Fallout 76","Bethesda Game Studios",52,"A shared-world take on post-nuclear West Virginia — human NPCs eventually arrived, alongside base building and PvP nuke launches.",["RPG","Shooter"]],
["Ghost Recon Wildlands","Ubisoft Paris",71,"A four-player squad dismantles a cartel across an open-world Bolivia — missions can be tackled in any order, any way.",["Shooter","Action"]],
["Grounded","Obsidian Entertainment",83,"Shrunk to insect size in a suburban backyard — survival crafting against spiders the size of cars, built for co-op.",["Sim","Action"]],
["Hell Let Loose","Black Matter",78,"50-player WWII battles hinge on logistics as much as gunfights — capturing supply points matters more than individual kills.",["Shooter"]],
["Hunt: Showdown","Crytek",81,"Bounty-hunting teams track monstrous targets through a Louisiana bayou — permadeath and sound-based tension define every extraction.",["Shooter","Horror"]],
["Injustice 2","NetherRealm Studios",84,"DC heroes and villains fight for control of a fractured Earth — gear-based loot customizes movesets on top of NetherRealm's fighting engine.",["Fighting"]],
["Kena: Bridge of Spirits","Ember Lab",78,"A young spirit guide clears corrupted forests alongside an army of tiny Rot companions — Pixar-quality visuals meet soulslike combat.",["Action","Adventure"]],
["Killzone Shadow Fall","Guerrilla Games",70,"A wall-divided city splits Helghast and Vektan survivors — a drone companion adds hacking and support options to corridor shooting.",["Shooter","Action"]],
["LEGO Star Wars: The Skywalker Saga","Traveller's Tales",85,"All nine saga films rebuilt in LEGO form — blaster combat, lightsabers, and space dogfights across a galaxy-spanning open hub.",["Action","Adventure"]],
["Little Nightmares","Tarsier Studios",81,"A small girl named Six escapes a ship of grotesque, oversized adults — atmospheric stealth-platforming built on scale and vulnerability.",["Horror","Platformer"]],
["Mafia: Definitive Edition","Hangar 13",81,"A cab driver's slow descent into 1930s organized crime — a full remake of the original's cinematic, mission-driven structure.",["Action","Adventure"]],
["Mass Effect Legendary Edition","BioWare",86,"Commander Shepard's trilogy against the Reapers, remastered — squad-based RPG combat and choices that carry across all three games.",["RPG","Shooter"]],
["Metro Exodus","4A Games",84,"Survivors leave Moscow's tunnels behind for an open, irradiated Russia — stealth-shooting gear degrades and must be maintained by hand.",["Shooter","Horror"]],
["Mount & Blade II: Bannerlord","TaleWorlds Entertainment",80,"Build a kingdom through large-scale medieval battles and trade — every soldier on the field is simulated individually.",["Strategy","RPG"]],
["Octopath Traveler II","Square Enix",89,"Eight travelers' stories interweave across a HD-2D world — turn-based Break-and-Boost combat rewards exploiting elemental weaknesses.",["RPG"]],
["Overcooked! All You Can Eat","Ghost Town Games",78,"Chaotic co-op kitchens demand split-second coordination — increasingly absurd stage gimmicks test communication under pressure.",["Sim","Puzzle"]],
["Persona 4 Golden","Atlus",89,"A transfer student investigates murders tied to a mysterious TV world — turn-based Shadow battles wrapped in a beloved small-town mystery.",["RPG"]],
["Psychonauts 2","Double Fine Productions",89,"A psychic summer camp dropout dives literally into co-workers' minds — each level is a wildly different platforming showcase.",["Platformer","Adventure"]],
["Rayman Legends","Ubisoft Montpellier",89,"Hand-drawn platforming built around rhythm and precision — Murfy-assisted co-op stages sit beside music-synced set pieces.",["Platformer"]],
["Red Dead Redemption","Rockstar San Diego",95,"A reformed outlaw is blackmailed into hunting his former gang across a dying Old West — the open-world foundation the sequel built on.",["Action","Adventure"]],
["Remnant: From the Ashes","Gunfire Games",78,"Soulslike gunplay against a world overrun by an otherworldly root — co-op runs shuffle bosses and dungeons on every playthrough.",["Shooter","RPG"]],
["Resident Evil 2","Capcom",91,"Leon and Claire survive Raccoon City's outbreak in a fully rebuilt remake — tense ammo conservation against a relentless stalking enemy.",["Horror","Action"]],
["Resident Evil 3","Capcom",79,"Jill Valentine flees the pursuing Nemesis through a collapsing city — a shorter, more action-focused companion to the RE2 remake.",["Horror","Action"]],
["Resident Evil 7: Biohazard","Capcom",84,"A first-person return to claustrophobic horror — a derelict Louisiana plantation hides a family that won't stay dead.",["Horror","Action"]],
["Rogue Legacy 2","Cellar Door Games",87,"Each death passes the castle-storming quest to a randomly-generated descendant — permanent upgrades stack across generations of runs.",["Platformer","RPG"]],
["Satisfactory","Coffee Stain Studios",90,"Automate an alien planet's resources into sprawling factory chains — conveyor-belt logistics scale from simple smelters to megafactories.",["Sim"]],
["Shin Megami Tensei V: Vengeance","Atlus",84,"A demon-fusing protagonist navigates a post-apocalyptic Tokyo — recruiting and merging demons defines both combat and story branches.",["RPG"]],
["Slime Rancher","Monomi Park",83,"Ranch colorful slimes on a distant planet, feeding and breeding them for profit — a cheerful, low-stakes farming-sim loop.",["Sim","Adventure"]],
["Sniper Elite 5","Rebellion Developments",76,"X-ray kill cams punctuate long-range WWII sniping — expansive levels support stealth, sabotage, or open combat approaches.",["Shooter","Action"]],
["Soul Hackers 2","Atlus",70,"A digital being fights to prevent an apocalypse by recruiting demons in modern Tokyo — Atlus's demon-fusion RPG systems in a sleeker package.",["RPG"]],
["Star Wars Jedi: Fallen Order","Respawn Entertainment",84,"A Jedi Padawan hides from the Empire while piecing together his training — Metroidvania exploration paired with lightsaber dueling.",["Action","Adventure"]],
["State of Decay 2","Undead Labs",70,"A community of survivors manages a home base amid a zombie outbreak — permadeath makes every scavenging run genuinely risky.",["Action","Sim"]],
["Teenage Mutant Ninja Turtles: Shredder's Revenge","Tribute Games",87,"A love letter to 90s beat-'em-ups — four-player co-op brawling with a soundtrack from the genre's original composer.",["Fighting","Action"]],
["The Forest","Endnight Games",88,"A plane-crash survivor builds shelter against a forest of cannibalistic mutants — base defense meets open survival crafting.",["Horror","Sim"]],
["The Quarry","Supermassive Games",73,"Nine camp counselors' last night spirals into horror-movie chaos — branching QTE choices decide who survives until morning.",["Horror","Adventure"]],
["Trine 4: The Nightmare Prince","Frozenbyte",78,"Three heroes' magic abilities combine to solve physics puzzles — co-op puzzle-platforming with a storybook art style.",["Puzzle","Platformer"]],
["Two Point Hospital","Two Point Studios",83,"Design and staff absurdist hospitals treating equally absurd illnesses — a spiritual successor to the classic tycoon-sim genre.",["Sim","Strategy"]],
["Vampyr","DONTNOD Entertainment",68,"A doctor-turned-vampire in 1918 London must feed to grow stronger — every NPC killed for blood permanently changes the city around them.",["RPG","Action"]],
["Warframe","Digital Extremes",79,"Space ninjas called Tenno pilot customizable Warframes through fast, acrobatic combat — a free-to-play looter with years of added story.",["Shooter","RPG"]],
["Wasteland 3","inXile Entertainment",83,"Rangers rebuild law and order in a frozen post-apocalyptic Colorado — turn-based squad tactics with heavy consequence-driven writing.",["RPG","Strategy"]],
["Worms W.M.D","Team17",79,"Turn-based artillery warfare between teams of armed worms — classic weapons return alongside new craftable gadgets.",["Strategy","Puzzle"]],
["XCOM: Chimera Squad","Firaxis Games",75,"A mixed human-alien police squad handles turn-based missions in a divided city — a faster, more tactical spin-off of the mainline series.",["Strategy"]],
["Yooka-Laylee","Playtonic Games",68,"A chameleon-bat duo collect Pagies across expansive 3D worlds — a spiritual successor built by veterans of the collect-a-thon genre.",["Platformer","Adventure"]],
["Hellblade: Senua's Sacrifice","Ninja Theory",83,"A Celtic warrior battles her own psychosis on a journey into Norse hell — binaural audio simulates the voices in her head.",["Action","Horror"]],
["Hellblade II: Senua's Saga","Ninja Theory",80,"Senua's fight against inner and outer darkness continues with photorealistic, performance-captured visuals and one-take cinematography.",["Action","Adventure"]],
["Dragon's Dogma: Dark Arisen","Capcom",84,"Pawns follow their Arisen through monster-filled Gransys — the original open-world action-RPG that Dragon's Dogma 2 later expanded on.",["RPG","Action"]],
["Kingdom Hearts III","Square Enix",83,"Sora reunites with Disney and Pixar worlds to close out the Xehanort saga — Keyblade combat blends with theme-park-scale set pieces.",["RPG","Action"]],
["Brothers: A Tale of Two Sons","Starbreeze Studios",86,"Two brothers are controlled simultaneously, one per analog stick, on a quest to save their father — told without any spoken dialogue.",["Adventure","Puzzle"]],
["Undertale","tobyfox",92,"Every enemy encounter can be fought or spared — a bullet-hell RPG about the consequences of violence, remembered by the world itself.",["RPG","Puzzle"]],
["The Stanley Parable: Ultra Deluxe","Crows Crows Crows",86,"A narrator describes what Stanley will do next — defying him unravels one of gaming's most self-aware, branching non-stories.",["Adventure","Puzzle"]],
["The Talos Principle","Croteam",84,"A puzzle-solving AI questions its own existence across ancient ruins wired with sci-fi tech — philosophy delivered through environmental logic puzzles.",["Puzzle"]],
["The Talos Principle 2","Croteam",87,"A new-generation android joins a post-human city rebuilding civilization — larger, more elaborate puzzle chambers with a deeper philosophical throughline.",["Puzzle"]],
["Superhot","SUPERHOT Team",81,"Time moves only when you do — a red-enemy shooter that turns every room into a slow-motion puzzle of bullets and improvised weapons.",["Shooter","Puzzle"]],
["Spelunky 2","Mossmouth",83,"Procedurally-generated caves punish every misstep with permadeath — a legendarily tight, physics-driven platformer built for mastery.",["Platformer","Action"]],
["Astroneer","System Era Softworks",81,"Terraform alien planets by literally reshaping terrain — co-op base building and resource gathering with a soft, low-stakes tone.",["Sim","Adventure"]],
["The Long Dark","Hinterland Studio",81,"A survival trek through the frozen Canadian wilderness — no zombies, no monsters, just cold, hunger, and the elements.",["Sim","Adventure"]],
["Fallout: New Vegas","Obsidian Entertainment",84,"The Mojave Wasteland's factions vie for control of the Hoover Dam — reactive writing lets nearly every quest be solved multiple ways.",["RPG","Shooter"]],
["Titanfall 2","Respawn Entertainment",89,"Wall-running pilots and towering mechs share the same fast, vertical shooter — a single-player campaign built on a different gimmick every level.",["Shooter","Action"]],
["Mad Max","Avalanche Studios",71,"A wasteland drifter builds up the ultimate war car — open-world vehicular combat across dune seas and scrapyard strongholds.",["Action","Racing"]],
["Judgment","Ryu Ga Gotoku Studio",81,"A disbarred lawyer turned private detective investigates a serial killer in Kamurocho — Yakuza's brawling engine repurposed for noir mystery.",["Action","RPG"]],
["Danganronpa: Trigger Happy Havoc","Spike Chunsoft",82,"Trapped students must find a killer among themselves or be executed — courtroom debates play out as rhythm-timed argument battles.",["Puzzle","Adventure"]],
["Catherine: Full Body","Atlus",78,"A man torn between two women survives nightmares by climbing block-puzzle towers — surreal horror wrapped around a dating-sim structure.",["Puzzle","Horror"]],
["Ace Attorney Trilogy","Capcom",86,"Defense attorney Phoenix Wright cross-examines witnesses and objects loudly in court — visual-novel courtroom drama with absurdist mystery plots.",["Adventure","Puzzle"]],
["The Great Ace Attorney Chronicles","Capcom",85,"A young Ryunosuke Naruhodo practices law in Meiji-era Japan and Victorian London — the courtroom formula gets a period-piece makeover.",["Adventure","Puzzle"]],
["Wo Long: Fallen Dynasty","Team Ninja",78,"A deflection-focused soulslike set during the fall of the Han dynasty — a Morale system rewards aggression over caution.",["Action","RPG"]],
["Granblue Fantasy: Relink","Cygames",81,"Cygames' mobile RPG cast gets a full action-RPG adaptation — co-op boss raids reward flashy, combo-driven skychild teamwork.",["RPG","Action"]],
["Dragon Ball FighterZ","Arc System Works",87,"3v3 tag-team fighting built on Arc System Works' signature 2.5D animation — accessible combos hide deep, high-level tech.",["Fighting"]],
["Star Wars: Knights of the Old Republic","BioWare",93,"A branching light side/dark side RPG set millennia before the films — a genuinely famous mid-game twist reframes everything before it.",["RPG"]],
["Tomb Raider I-III Remastered","Aspyr",78,"Lara Croft's original PS1-era trilogy, rebuilt with modern controls and a visual overhaul — tank controls remain optional.",["Action","Adventure"]],
["The Wonderful 101: Remastered","PlatinumGames",76,"A hundred tiny heroes merge into giant weapons drawn on-screen with the right stick — sentai chaos from the director of Bayonetta.",["Action"]],
["Dungeons & Dragons: Dark Alliance","Tuque Games",56,"Four Icewind Dale heroes hack through co-op dungeon crawls — real-time action built directly on D&D's Forgotten Realms lore.",["RPG","Action"]],
["DayZ","Bohemia Interactive",68,"An open-world zombie survival sandbox where other players are the real threat — permadeath and scarce loot breed constant tension.",["Shooter","Sim"]],
["Monster Hunter Rise","Capcom",88,"Wirebug grappling hooks add vertical mobility to monster hunts — village quests scale from solo play to four-player raids.",["RPG","Action"]],
["Godfall","Counterplay Games",51,"Looter-slasher melee combat in ornate, glowing armor sets — a launch-window PS5 title built around flashy valorplate abilities.",["Action","RPG"]],
["SteamWorld Dig 2","Thunderful Development",87,"A robot miner digs deeper into a procedurally-shaped underground — Metroidvania upgrades open new paths as the mine collapses around her.",["Platformer","Puzzle"]],
["Sea of Stars","Sabotage Studio",89,"Two Solstice Warriors combine sun and moon magic in timed, turn-based combat — a loving throwback to 16-bit-era RPGs.",["RPG"]],
["Eastward","Pixpil",81,"A gruff miner and a mysterious girl travel a post-apocalyptic underground world — pixel-art adventure mixing combat, puzzles, and cooking.",["Adventure","Puzzle"]],
["Eiyuden Chronicle: Hundred Heroes","Rabbit & Bear Studios",76,"Recruit a roster of a hundred playable characters into a growing castle stronghold — a spiritual successor to the Suikoden series.",["RPG"]],
["Metal: Hellsinger","The Outsiders",81,"Gunplay locks to the beat of a licensed metal soundtrack — combo multipliers reward staying perfectly on rhythm while demon-hunting.",["Shooter","Action"]],
["Foamstars","Square Enix",57,"Foam-splatting team shooter with a K-pop-adjacent aesthetic — territory-coverage objectives replace straightforward elimination.",["Shooter","Action"]],
["Far Cry 3","Ubisoft Montreal",88,"A vacationing tourist is stranded on a pirate-controlled island — the open-world formula the rest of the series would repeat for a decade.",["Shooter","Action"]],
["Far Cry 4","Ubisoft Montreal",82,"A Himalayan kingdom's civil war plays out around elephant-mounted assaults and outpost liberation — Far Cry 3's systems, bigger and stranger.",["Shooter","Action"]],
["Far Cry 5","Ubisoft Montreal",79,"A doomsday cult seizes rural Montana county by county — a fly-anything, drive-anything sandbox with a surprisingly dark undertone.",["Shooter","Action"]],
["Frostpunk: Console Edition","11 bit studios",81,"A city-survival strategy game where the last furnace keeps everyone alive — every law passed trades efficiency against your people's humanity.",["Strategy","Sim"]],
["Titan Quest","Iron Lore Entertainment",83,"A Diablo-style action-RPG built around Greek, Egyptian, and Chinese mythology — dual-class mastery combos define each build.",["RPG","Action"]],
["Dead Space 2","Visceral Games",89,"Isaac Clarke wakes up on a space station three years after the original outbreak — tighter pacing and bigger set pieces than the first.",["Horror","Shooter"]],
["Dead Space 3","Visceral Games",78,"A snowbound planet hides the origin of the necromorph outbreak — optional co-op adds a parallel storyline for a second player.",["Horror","Shooter"]],
["BioShock Infinite","Irrational Games",94,"A floating city in the clouds hides a fractured America — Elizabeth's reality-tearing powers turn every fight into a shifting battlefield.",["Shooter","Action"]],
["BioShock Remastered","Irrational Games",96,"Rapture's underwater art-deco ruins hide Little Sisters, Big Daddies, and a genre-defining twist — the original, remastered for modern hardware.",["Shooter","Action"]],
["Beyond: Two Souls","Quantic Dream",71,"A woman bonded to a mysterious entity since childhood lives a fractured, nonlinear life story — told through motion-captured performance.",["Adventure"]],
["Uncharted: Drake's Fortune","Naughty Dog",84,"Nathan Drake's first treasure hunt sets the template — cover-based shootouts between cinematic platforming and ancient ruins.",["Action","Adventure"]],
["Uncharted 2: Among Thieves","Naughty Dog",96,"A train collapsing down a mountainside remains one of the medium's iconic set pieces — the series' cinematic ambitions fully arrive.",["Action","Adventure"]],
["Uncharted 3: Drake's Deception","Naughty Dog",92,"A sinking ship and a desert mirage push the series' spectacle further — Drake's past with mentor Sully finally gets explored.",["Action","Adventure"]],
["Infamous Second Son","Sucker Punch Productions",80,"A neon-powered drifter chooses heroism or villainy across an open Seattle — smoke, neon, and video powers each play distinctly.",["Action","Adventure"]],
["God of War","Santa Monica Studio",94,"Kratos leaves Greek myth behind for Norse wilds with his son Atreus — a single unbroken camera take and a reinvented, more grounded combat style.",["Action","Adventure"]],
["Uncharted: The Lost Legacy","Naughty Dog",85,"Chloe Frazer and Nadine Ross hunt a Ganesh tusk across India's Western Ghats — a standalone story with the series' biggest open area yet.",["Action","Adventure"]],
["The Last of Us Part II","Naughty Dog",93,"Ellie's revenge spirals into a story that keeps swapping whose side you're on — brutal, grounded combat backs one of the medium's most divisive narratives.",["Action","Horror"]],
["Marvel's Guardians of the Galaxy","Eidos-Montréal",83,"A cash-strapped Star-Lord leads a bickering, dysfunctional team through cosmic chaos — combat pauses for genuinely funny team banter.",["Action","Adventure"]],
["Suicide Squad: Kill the Justice League","Rocksteady Studios",54,"A brainwashed Justice League must be put down by Task Force X — looter-shooter combat replaces the Arkham series' melee-focused combat.",["Shooter","Action"]],
["Star Wars Outlaws","Massive Entertainment",68,"A scoundrel navigates the criminal underworld's rival syndicates — the first open-world Star Wars game, blaster combat and starship travel included.",["Action","Adventure"]],
["Onimusha: Way of the Sword","Capcom",80,"A samurai wielding a demon-slaying gauntlet fights through feudal Japan — Capcom revives its parry-focused, Souls-adjacent action series.",["Action"]],
["Tekken 7","Bandai Namco Studios",83,"The Mishima family saga concludes across Rage Art comebacks and cinematic story mode — the long-running 3D fighter's most accessible entry to date.",["Fighting"]],
["A Plague Tale: Innocence","Asobo Studio",84,"A medieval survival adventure following two siblings evading soldiers and a plague of rats sweeping through 14th-century France.",["Adventure","Action"]],
["Ghostrunner","One More Level",78,"A first-person cyberpunk parkour game built around one-hit deaths, wall-runs, and split-second sword kills up a mega-tower.",["Action"]],
["Ghostrunner 2","One More Level",80,"The sequel adds a motorcycle chase sequence and a longer campaign to the same lethal, rhythm-like first-person slashing.",["Action"]],
["Metro 2033 Redux","4A Games",81,"A remastered survival shooter set in Moscow's irradiated subway tunnels, mixing scarce ammo with mutant-infested darkness.",["Shooter","Horror"]],
["Metro Last Light Redux","4A Games",82,"The remastered sequel continues Artyom's story through the metro and the ruined surface of post-apocalyptic Moscow.",["Shooter","Horror"]],
["South Park: The Stick of Truth","Obsidian Entertainment",85,"A turn-based RPG written in the show's own voice, casting the New Kid into a backyard fantasy war between Stan's and Cartman's factions.",["RPG"]],
["South Park: The Fractured but Whole","Ubisoft San Francisco",78,"A superhero-themed sequel RPG that swaps fantasy factions for rival superhero teams, still fully voiced by the show's cast.",["RPG"]],
["Middle-earth: Shadow of Mordor","Monolith Productions",84,"An open-world action game built around the Nemesis System, where orc captains remember and adapt to your past fights.",["Action","RPG"]],
["Middle-earth: Shadow of War","Monolith Productions",81,"Expands the Nemesis System across a larger map, letting players recruit rival orc captains into their own army.",["Action","RPG"]],
["Just Cause 3","Avalanche Studios",76,"An open-world sandbox built around a grappling hook, wingsuit, and unlimited explosives for toppling a Mediterranean dictatorship.",["Action"]],
["Just Cause 4","Avalanche Studios",67,"Continues the destruction-sandbox formula with extreme weather systems layered on top of the grapple-and-glide traversal.",["Action"]],
["Sleeping Dogs: Definitive Edition","United Front Games",78,"An open-world crime game following an undercover cop infiltrating Hong Kong's triads through martial-arts combat and car chases.",["Action"]],
["Saints Row IV: Re-Elected","Volition",70,"A superpowered, tongue-in-cheek open-world game where the player, now president, fights an alien simulation with super-speed and psychic blasts.",["Action"]],
["Mafia II: Definitive Edition","Hangar 13",68,"A remastered mob drama following an Italian immigrant's rise through 1940s-50s organized crime in a fictional American city.",["Action"]],
["Mafia III: Definitive Edition","Hangar 13",65,"A revenge story set in 1968 New Orleans, where a Vietnam veteran dismantles the mafia family that betrayed him district by district.",["Action"]],
["L.A. Noire","Team Bondi",81,"A detective game set in 1940s Los Angeles, built around interrogations where reading a suspect's face matters as much as the evidence.",["Adventure"]],
["Max Payne 3","Rockstar Studios",87,"A slow-motion shootout thriller following a burnt-out ex-cop turned bodyguard through corruption in São Paulo.",["Shooter"]],
["Kingdoms of Amalur: Re-Reckoning","Big Huge Games",71,"A remastered action RPG with a flexible class system, letting a resurrected hero fight through a large fantasy world however they choose.",["RPG"]],
["Two Point Campus","Two Point Studios",78,"A management sim about building and running an absurdist university, from courses in Knight School to Spy Academy.",["Sim","Strategy"]],
["Planet Coaster: Console Edition","Frontier Developments",76,"A deep theme-park builder letting players design custom coasters and rides piece by piece, then watch guests react to them.",["Sim"]],
["This War of Mine: Final Cut","11 bit studios",76,"A survival game about civilians, not soldiers, trying to get through a city under siege by scavenging and rationing what little they find.",["Strategy","Adventure"]],
["Return to Monkey Island","Terrible Toybox",83,"A direct sequel to the classic pirate comedy adventure, bringing back Guybrush Threepwood for one more round of absurd puzzle logic.",["Adventure","Puzzle"]],
["Oxenfree","Night School Studio",80,"A supernatural teen mystery told through overlapping, interruptible dialogue as a group of friends accidentally open a ghostly rift.",["Adventure"]],
["Oxenfree II: Lost Signals","Night School Studio",76,"A standalone sequel following a new protagonist investigating strange radio signals on the same haunted coastline.",["Adventure"]],
["Night in the Woods","Infinite Fall",83,"A narrative adventure about a college dropout returning to her decaying hometown and reconnecting with old friends as something strange stirs beneath it.",["Adventure"]],
["Ori and the Blind Forest: Definitive Edition","Moon Studios",88,"A hand-painted platformer following a small forest spirit restoring life to a dying woodland through precise, emotional platforming.",["Platformer"]],
["Ori and the Will of the Wisps","Moon Studios",88,"The sequel expands Ori's abilities and world with denser combat and some of the genre's most demanding movement sequences.",["Platformer"]],
["Salt and Sanctuary","Ska Studios",80,"A 2D side-scrolling take on Soulslike combat, mixing grim hand-drawn art with methodical, punishing swordplay.",["Action","RPG"]],
["Salt and Sacrifice","Ska Studios",71,"The sequel adds mage-hunting boss chases across a larger 2D world, still built on the same brutal Soulslike foundation.",["Action","RPG"]],
["Bloodstained: Ritual of the Night","ArtPlay",81,"A spiritual successor to classic Castlevania, sending an alchemically-scarred heroine through a sprawling, interconnected demon castle.",["Platformer","RPG"]],
["Axiom Verge","Thomas Happ Games",83,"A retro-styled Metroidvania built almost entirely by one developer, full of glitch-based weapons and a hostile alien world.",["Platformer"]],
["Axiom Verge 2","Thomas Happ Games",76,"A stranger, more open sequel that swaps the original's glitch weapons for a mix of exploration and light platforming puzzles.",["Platformer"]],
["Rain World","Videocult",77,"A survival platformer where the player is prey, not predator, and must learn a living ecosystem's rules just to find the next meal and shelter.",["Platformer","Action"]],
["Katana Zero","Askiisoft",84,"A neon one-hit-kill action game told in a single dash between rooms, replaying and rewinding fights until every enemy falls at once.",["Action"]],
["Mega Man 11","Capcom",81,"A modern return for the classic blue robot, introducing a Double Gear mechanic on top of the series' precise run-and-gun platforming.",["Platformer"]],
["Streets of Rage 4","Dotemu",83,"A hand-drawn revival of the classic beat-'em-up, sending old and new fighters punching through the same corrupt city once more.",["Action"]],
["River City Girls","WayForward",74,"A beat-'em-up spin-off starring two Riverdale high schoolers fighting their way through the Kunio-kun universe to rescue their boyfriends.",["Action"]],
["River City Girls 2","WayForward",74,"A sequel with a larger roster and updated combat, keeping the same colorful, over-the-top brawling through River City.",["Action"]],
["Yakuza 3 Remastered","Ryu Ga Gotoku Studio",73,"Kazuma Kiryu leaves the underworld to run an orphanage in Okinawa, only to be pulled back into gang politics anyway.",["Action","RPG"]],
["Yakuza 4 Remastered","Ryu Ga Gotoku Studio",75,"Four playable protagonists, including a loan shark and an ex-con, converge on a single conspiracy tearing through Kamurocho.",["Action","RPG"]],
["Yakuza 5 Remastered","Ryu Ga Gotoku Studio",75,"An ambitious five-protagonist entry spanning multiple cities, including a storyline built around a taxi driver and one about an idol.",["Action","RPG"]],
["Yakuza 6: The Song of Life","Ryu Ga Gotoku Studio",78,"Kazuma Kiryu's story arc closes with a search for the truth behind a hit-and-run and the daughter he's sworn to protect.",["Action","RPG"]],
["Nioh","Team Ninja",84,"A punishing Soulslike set in a supernatural Sengoku-era Japan, layering deep stance-based swordplay onto a Western samurai's story.",["Action","RPG"]],
["Nioh 2","Team Ninja",87,"A prequel with a custom protagonist and a Yokai-transformation mechanic added on top of the original's demanding stance combat.",["Action","RPG"]],
["Code Vein","Bandai Namco Studios",71,"An anime-styled Soulslike about vampiric Revenants fighting through a ruined world, playable solo or alongside an AI partner.",["Action","RPG"]],
["The Surge","Deck13",68,"A sci-fi Soulslike where targeting specific limbs lets players harvest an enemy's own armor and weapons mid-fight.",["Action","RPG"]],
["The Surge 2","Deck13",75,"The sequel widens its dystopian city into a more open map, keeping the limb-targeting combat that defined the original.",["Action","RPG"]],
["Mortal Shell","Cold Symmetry",73,"A stripped-down Soulslike where the player possesses different fallen warriors' bodies, each with its own stats and playstyle.",["Action","RPG"]],
["Thymesia","OverBorder Studio",70,"A fast, plague-ridden Soulslike built around parrying and stealing enemy abilities to use against them.",["Action","RPG"]],
["Lords of the Fallen","Hexworks",73,"A dark fantasy Soulslike where the player can peer into and fight through a parallel spirit realm layered over the physical world.",["Action","RPG"]],
["Star Ocean: Divine Force","tri-Ace",71,"A space-fantasy action RPG mixing real-time combat with a private spaceship for exploring the game's star system between planets.",["RPG"]],
["Star Ocean The Second Story R","Gemdrops",81,"A remake of the fan-favorite second entry, rebuilding its branching, multi-ending story with modern real-time combat.",["RPG"]],
["Trials of Mana","Square Enix",76,"A 3D remake of a classic action RPG, letting players pick three of six heroes whose choice reshapes the story and its villains.",["RPG"]],
["Live A Live","Square Enix",83,"A remake of a cult SNES RPG told as seven unconnected historical vignettes that eventually converge into one story.",["RPG"]],
["Dragon Quest Treasures","Square Enix",73,"A spin-off sending two young Dragon Quest siblings treasure-hunting across floating islands with a crew of monster allies.",["RPG","Adventure"]],
["Ys VIII: Lacrimosa of Dana","Nihon Falcom",80,"A shipwreck-survival action RPG where Adol builds a castaway village while uncovering the secrets of a cursed, ancient island.",["RPG"]],
["Ys IX: Monstrum Nox","Nihon Falcom",78,"Adol is imprisoned in a cursed walled city and granted supernatural powers to fight through it from the inside.",["RPG"]],
["Ys X: Nordics","Nihon Falcom",79,"A seafaring entry pairing Adol with a young pirate captain, adding ship-to-ship naval combat to the series' fast action.",["RPG"]],
["The Legend of Heroes: Trails through Daybreak","Nihon Falcom",82,"A new arc in the long-running Trails series, following a freelance problem-solver through a politically fractured nation.",["RPG"]],
["Watch Dogs","Ubisoft Montreal",78,"The original open-world hacking game, sending a vigilante hacker through Chicago using a smartphone that controls the whole city.",["Action"]],
["Street Fighter V","Capcom",71,"A reset for the long-running fighting series, built around V-Triggers and a rotating cast of guest and returning fighters.",["Fighting"]],
["The King of Fighters XIV","SNK",75,"A roster of over fifty fighters across three-on-three team battles, continuing SNK's long-running crossover tournament story.",["Fighting"]],
["Under Night In-Birth II Sys:Celes","French Bread",78,"A 2D anime fighter with a day/night mechanic that shifts each character's move set depending on which side of the story they're on.",["Fighting"]],
["Melty Blood: Type Lumina","French Bread",76,"A fast, technical 2D fighter set in the Tsukihime universe, built around a moon-phase power system tied to each match.",["Fighting"]],
["BlazBlue: Cross Tag Battle","Arc System Works",70,"A tag-team crossover fighter mixing characters from BlazBlue, Persona, Under Night In-Birth, and RWBY into two-on-two battles.",["Fighting"]],
["Them's Fightin' Herds","Mane6",77,"A 2D fighter starring a cast of magical farm animals, built on the same engine as the Skullgirls team but with its own combo system.",["Fighting"]],
["Dragon Ball Z: Kakarot","CyberConnect2",78,"An action RPG retelling of the Dragon Ball Z story, letting players fly, fish, and grind alongside the series' biggest fights.",["RPG","Action"]],
["My Hero One's Justice 2","Byking",70,"An arena fighter built around My Hero Academia's cast, with destructible stages and each character's signature Quirk powers.",["Fighting"]],
["Persona 4 Arena Ultimax","Arc System Works",78,"A 2D fighter spinning the Persona 4 cast into a tournament story, built on Arc System Works' Guilty Gear-style engine.",["Fighting"]],
["Age of Wonders 4","Triumph Studios",80,"A fantasy 4X strategy game where players design their own custom race and lead it through empire-building and tactical battles.",["Strategy"]],
["Crusader Kings III","Paradox Development Studio",91,"A medieval dynasty simulator where the player manages generations of a noble house through marriage, intrigue, and war.",["Strategy"]],
["Stellaris: Console Edition","Paradox Development Studio",80,"A grand strategy game about guiding a spacefaring civilization from first contact through galaxy-spanning politics and war.",["Strategy"]],
["Northgard","Shiro Games",78,"A Viking-themed strategy game blending city-building and resource management with clan rivalries and encroaching winters.",["Strategy"]],
["NBA 2K24","Visual Concepts",71,"The long-running basketball sim with its yearly roster and presentation refresh, alongside its MyCareer and MyTeam modes.",["Sim"]],
["WWE 2K25","Visual Concepts",78,"A wrestling sim with a deep create-a-wrestler suite and career mode, alongside its usual roster of current and legendary Superstars.",["Sim","Fighting"]],
["EA Sports UFC 5","EA Vancouver",76,"A mixed martial arts sim built on a new damage and injury system that makes fights look and feel rougher the longer they go.",["Fighting","Sim"]],
["Madden NFL 25","EA Tiburon",74,"The annual NFL sim, with a rebuilt physics-driven tackling system underneath its usual franchise and Ultimate Team modes.",["Sim"]],
["Skate.","Full Circle",75,"A free-to-play relaunch of the skateboarding sandbox series, dropping players into a shared city to build lines and tricks their own way.",["Sim"]],
["Ride 5","Milestone",73,"A motorcycle racing sim with an unusually large roster of licensed bikes, built for players who care about tuning over arcade thrills.",["Racing"]],
["MXGP 24","Milestone",73,"The official motocross championship sim, rebuilding its terrain deformation system so tracks actually rut and change as a race goes on.",["Racing"]],
["Test Drive Unlimited Solar Crown","KT Racing",63,"An open-world racing MMO set across a recreated Hong Kong island, mixing car culture and social hubs with street racing.",["Racing"]],
["Visage","SadSquare Studio",78,"A slow-burn haunted house horror game told across several families' tragedies, all tied to the same cursed home.",["Horror"]],
["The Evil Within","Tango Gameworks",75,"A survival horror game from Resident Evil's original director, throwing a detective into a shifting, monster-filled nightmare.",["Horror","Shooter"]],
["The Evil Within 2","Tango Gameworks",81,"A more open-ended sequel sending the same detective into a simulated town collapsing in on itself.",["Horror","Shooter"]],
["SOMA","Frictional Games",83,"A sci-fi horror game about identity and consciousness, set in an underwater research station slowly falling apart.",["Horror","Adventure"]],
["Martha Is Dead","LKA",63,"A psychological horror game set in World War II Italy, following a woman investigating her twin sister's death by a lake.",["Horror","Adventure"]],
["Layers of Fear","Bloober Team",73,"A 2023 remake and expansion of the studio's psychological horror games, exploring a painter's and an actress's unraveling minds.",["Horror"]],
["The Medium","Bloober Team",71,"A psychic investigator explores both the real and spirit versions of a derelict hotel simultaneously, split across the screen.",["Horror","Adventure"]],
["Scorn","Ebb Software",68,"A body-horror puzzle game built around H.R. Giger-inspired biomechanical environments, with almost no dialogue or hand-holding.",["Horror","Puzzle"]],
["Choo-Choo Charles","Two Star Games",73,"A survival horror game where the player builds up their own armed train to fight a giant spider-train stalking an open island.",["Horror","Action"]],
["Song of Horror","Protocol Games",78,"An episodic survival horror game with permanent character death, following a group investigating a missing author's house.",["Horror"]],
["Loop Hero","Four Quarters",81,"A card-placement roguelike where the player builds the very world their hero walks through, one tile at a time, each loop.",["Strategy","RPG"]],
["Neon White","Angel Matrix",84,"A first-person speedrunning game where cards are both weapons and movement tools, built for shaving seconds off every level.",["Action","Platformer"]],
["Cassette Beasts","Bytten Studio",84,"A monster-taming RPG where the player themselves transforms into creatures on a strange island stuck in a cassette-tape aesthetic.",["RPG"]],
["Chained Echoes","Deck13/Matthias Linda",84,"A turn-based JRPG built in a deliberately 16-bit style, with a heat-based combat system and a large continent to explore by mech.",["RPG"]],
["Tinykin","Splashteam",78,"A tiny astronaut explores an oversized suburban house with an army of ant-like Tinykin, in a puzzle-platformer inspired by Pikmin.",["Platformer","Puzzle"]],
["Botany Manor","Balloon Studios",76,"A gentle puzzle game about a retired botanist piecing together the growing conditions for a collection of fictional plants.",["Puzzle","Adventure"]],
["Animal Well","Billy Basso",89,"A tiny, atmospheric Metroidvania built almost entirely by one developer, full of strange tools and secrets buried in a dark, wet world.",["Platformer","Puzzle"]],
["Pizza Tower","Tour De Pizza",87,"A manic, high-speed platformer in a hand-drawn cartoon style, built around never stopping and chaining combos through each level.",["Platformer"]],
["Blue Prince","Dogubomb",87,"A puzzle exploration game where the player redraws the rooms of a mysterious mansion each day, trying to reach a locked attic.",["Puzzle","Adventure"]],
["Citizen Sleeper","Jump Over the Age",83,"A dice-driven tabletop-style RPG about a synthetic worker fighting to buy their own freedom on a decaying space station.",["RPG"]],
["Norco","Geography of Robots",83,"A surreal point-and-click adventure set in a near-future Louisiana, following a woman searching for her missing brother.",["Adventure"]],
["Ni no Kuni II: Revenant Kingdom","Level-5",78,"A young king rebuilds his kingdom from scratch while exploring a colorful, Ghibli-inspired action RPG world.",["RPG"]],
["Wild Hearts","Omega Force",71,"A monster-hunting action RPG where players build makeshift structures like catapults and trampolines mid-fight to turn the tide.",["RPG","Action"]],
["Eiyuden Chronicle: Rising","Rabbit & Bear Studios",68,"A side-story action RPG set before Hundred Heroes, following a treasure hunter helping rebuild a struggling mining town.",["RPG"]],
["Dragon Age: Inquisition","BioWare",85,"A large-scale fantasy RPG where the player leads a rebuilt order closing rifts torn into the sky above a war-torn continent.",["RPG"]],
["Dragon Age: The Veilguard","BioWare",80,"The next chapter in the Dragon Age saga, assembling a new companion cast to stop an ancient elven threat unleashed on the world.",["RPG"]],
["Death Stranding 2: On the Beach","Kojima Productions",86,"Sam Porter Bridges returns for a stranger, more combat-focused delivery journey across a new, disconnected landscape.",["Action","Adventure"]],
["Indiana Jones and the Great Circle","MachineGames",85,"A first-person adventure following Indiana Jones through 1930s dig sites and temples, built on the same engine as recent Wolfenstein games.",["Adventure","Action"]],
["Grand Theft Auto: The Trilogy – The Definitive Edition","Grove Street Games",58,"Remastered versions of GTA III, Vice City, and San Andreas with updated lighting and controls, built on one shared engine.",["Action"]],
["Sonic Frontiers","Sonic Team",72,"An open-zone Sonic game letting the hedgehog run, grind, and combo across large, puzzle-filled islands instead of linear stages.",["Platformer","Action"]],
["Persona 5 Tactica","Atlus",77,"A tactical spin-off sending the Phantom Thieves into cover-based, grid-strategy battles in a new fairy-tale-styled kingdom.",["Strategy","RPG"]],
["Ghostbusters: Spirits Unleashed","IllFonic",67,"An asymmetrical multiplayer game where a team of Ghostbusters traps a single player-controlled ghost haunting a location.",["Action"]],
["EA Sports College Football 25","EA Orlando",81,"The revived college football sim, rebuilt around campus atmosphere, mascots, and a dynasty mode spanning years of recruiting.",["Sim"]],
["Kunitsu-Gami: Path of the Goddess","Capcom",78,"A day-night defense game where players purify a corrupted village by day and fend off demon hordes with villagers by night.",["Strategy","Action"]],
["Battlefield 2042","DICE",68,"A large-scale multiplayer shooter built around massive player counts, dynamic weather events, and specialist soldiers instead of set classes.",["Shooter"]],
["Battlefield V","DICE",78,"A World War II shooter with large-scale Grand Operations battles and a destructible, ever-changing battlefield.",["Shooter"]],
["Rainbow Six Extraction","Ubisoft",71,"A co-op spin-off sending Rainbow Six operators against an alien parasite threat, built around escalating three-player missions.",["Shooter"]],
["Insurgency: Sandstorm","New World Interactive",81,"A tactical, punishing multiplayer shooter built around realistic gunplay, limited ammo, and no on-screen HUD clutter.",["Shooter"]],
["World War Z","Saber Interactive",71,"A four-player co-op shooter against massive, swarming zombie hordes that climb over each other to reach the player.",["Shooter","Action"]],
["Klonoa Phantasy Reverie Series","Bandai Namco Studios",78,"A remaster collecting two classic 2.5D platformers starring the dream-traveling Klonoa, rebuilt with modern visuals.",["Platformer"]],
["The Witness","Thekla, Inc.",87,"A first-person puzzle game set on a mysterious island covered in hundreds of interlocking line-maze puzzles.",["Puzzle"]],
["Baba Is You","Hempuli Oy",87,"A puzzle game where the rules of each level are physical blocks the player can push around to rewrite how the game itself works.",["Puzzle"]],
["Human: Fall Flat","No Brakes Games",73,"A physics-based puzzle-platformer starring a wobbly, floppy character solving surreal dreamscape puzzles, solo or in co-op.",["Puzzle","Platformer"]],
["Tropico 6","Limbic Entertainment",76,"A tongue-in-cheek dictator sim where the player runs a Caribbean island nation across eras, balancing rebels, allies, and tourists.",["Sim","Strategy"]],
["Conan Exiles","Funcom",73,"An open-world survival game set in the brutal Conan the Barbarian universe, built around building strongholds and fighting to survive the desert.",["Sim","Action"]],
["Green Hell","Creepy Jar",78,"A survival game set deep in the Amazon rainforest, with an unusually detailed health system tracking parasites, wounds, and mental state.",["Sim","Adventure"]],
["7 Days to Die","The Fun Pimps",68,"A zombie survival game mixing base-building and RPG progression with a recurring, escalating horde that attacks every seventh night.",["Sim","Horror"]],
["Raft","Redbeet Interactive",81,"A survival game that starts the player on a tiny raft in open ocean, growing it plank by plank while fending off sharks and scavenging debris.",["Sim","Adventure"]],
["13 Sentinels: Aegis Rim","Vanillaware",89,"A hand-drawn visual novel and mech-battle hybrid weaving together thirteen teenagers' storylines into one time-bending mystery.",["RPG","Adventure"]],
["One Piece: Pirate Warriors 4","Omega Force",76,"A hack-and-slash retelling of the One Piece story, letting players cut through hundreds of enemies as Luffy's crew and beyond.",["Action"]],
["Fist of the North Star: Lost Paradise","Ryu Ga Gotoku Studio",75,"An open-world brawler from the Yakuza team, retelling the post-apocalyptic manga's story with the same engine's side content and humor.",["Action","RPG"]],
["Final Fantasy X/X-2 HD Remaster","Square Enix",84,"A remastered double pack of the PS2-era classics, following Tidus and Yuna's pilgrimage across the world of Spira.",["RPG"]],
["Kingdom Hearts HD 1.5 + 2.5 ReMIX","Square Enix",83,"A remastered collection gathering the series' earliest entries, mixing Disney worlds with Square Enix's original story and characters.",["RPG","Action"]],
["Kingdom Hearts Melody of Memory","Square Enix",65,"A rhythm-game spin-off replaying the series' story beats through music from across every prior Kingdom Hearts game.",["RPG"]],
["Dragon's Crown Pro","Vanillaware",80,"A hand-drawn co-op brawler where a party of fantasy adventurers fights through dungeons for loot in lavishly animated 2D combat.",["Action","RPG"]],
["Odin Sphere Leifthrasir","Vanillaware",86,"A remaster of the studio's hand-painted fantasy epic, following five interconnected characters through a war between kingdoms.",["Action","RPG"]],
["Unicorn Overlord","Vanillaware",87,"A tactical RPG about reclaiming a fractured kingdom, mixing unit-formation strategy with the studio's signature hand-drawn art.",["Strategy","RPG"]],
["Ender Magnolia: Bloom in the Mist","Adglobe/Binary Haze Interactive",84,"A Metroidvania sequel following a new heroine through a similarly decaying, machine-haunted world.",["Platformer","RPG"]],
["Grime","Clover Bite",74,"A Soulslike Metroidvania where the player's black-hole hand absorbs enemies to steal their abilities in a surreal, alien world.",["Action","RPG"]],
["Islets","Kyle Thompson",80,"A tightly-designed Metroidvania set across a cluster of floating islands, built around a small, focused map and satisfying movement.",["Platformer"]],
["Prodeus","Bounding Box Software",83,"A retro-styled boomer shooter built on modern lighting, combining classic Doom-like speed with contemporary visuals.",["Shooter"]],
["Turbo Overkill","Trigger Happy Interactive",81,"A cyberpunk boomer shooter starring a cyborg with a chainsaw leg, built for fast, bloody, relentless momentum.",["Shooter","Action"]],
["DUSK","New Blood Interactive",88,"A deliberately retro horror shooter styled after '90s classics, with low-poly visuals and unrelenting old-school pacing.",["Shooter","Horror"]],
["Amid Evil","Indefatigable",81,"A fantasy-themed retro shooter, swapping the usual sci-fi boomer-shooter aesthetic for magic staffs and mythic realms.",["Shooter"]],
["Sniper Elite: Resistance","Rebellion Developments",75,"A World War II sniper campaign set in occupied France, continuing the series' signature slow-motion bullet-cam kills.",["Shooter"]],
["Diablo II: Resurrected","Vicarious Visions",85,"A faithful remaster of the genre-defining dungeon crawler, rebuilding its visuals while keeping the original's loot and combat intact.",["RPG","Action"]],
["Path of Exile","Grinding Gear Games",84,"A free-to-play action RPG with an enormous, player-driven passive skill tree and famously deep build customization.",["RPG","Action"]],
["Path of Exile 2","Grinding Gear Games",84,"A standalone successor with reworked combat and a fresh campaign, built alongside the original game's live economy.",["RPG","Action"]],
["Grim Dawn","Crate Entertainment",83,"A grim, industrial-fantasy action RPG with a dual-class system that lets players combine two skill trees into one build.",["RPG","Action"]],
["Hot Wheels Unleashed","Milestone",78,"An arcade racer built around real Hot Wheels toy cars and tracks, racing across oversized household environments.",["Racing"]],
["Hot Wheels Unleashed 2: Turbocharged","Milestone",76,"A sequel expanding the toy-car arcade racer with new environments, weather effects, and an even bigger track editor.",["Racing"]],
["Trackmania","Nadeo",78,"A precision arcade racer built around tight, replayable tracks and community-made courses, focused on shaving fractions of a second.",["Racing"]],
["Wartales","Shiro Games",79,"A mercenary-band RPG where a growing company of hired swords survives through banditry, contracts, and open-world exploration.",["RPG","Strategy"]],
["Journey to the Savage Planet","Typhoon Studios",76,"A colorful first-person exploration game about cataloguing the bizarre wildlife of an alien planet for a budget space agency.",["Adventure","Action"]],
["Superliminal","Pillow Castle",80,"A first-person puzzle game built around forced perspective, where an object's size changes based on how close or far it looks.",["Puzzle"]],
["Viewfinder","Sad Owl Studios",81,"A puzzle game where placing photographs into the world turns them into real, walkable environments.",["Puzzle"]],
["Humanity","tha ltd.",78,"A puzzle game where the player directs vast crowds of people like a flock, guiding them safely through increasingly strange levels.",["Puzzle"]],
["Sable","Shedworks",76,"A quiet, painterly open-world game about a teenager's coming-of-age desert journey on a hoverbike, with almost no combat at all.",["Adventure"]],
["In Other Waters","Jump Over the Age",79,"A minimalist sci-fi exploration game told entirely through an AI's sonar interface, guiding a scientist through an alien ocean.",["Adventure","Puzzle"]],
["A Short Hike","adamgryu",89,"A brief, cozy exploration game about climbing a mountain at your own pace, talking to the island's odd cast along the way.",["Adventure"]],
["Röki","Polygon Treehouse",76,"A Nordic folklore adventure following a girl through a fairy-tale forest, solving puzzles tied to Scandinavian myth.",["Adventure","Puzzle"]],
["Bramble: The Mountain King","Dimfrost Studio",75,"A dark fairy-tale adventure pulling from Scandinavian folklore, following a young boy through genuinely unsettling forest creatures.",["Adventure","Horror"]],
["Fuga: Melodies of Steel","CyberConnect2",78,"A tactical RPG about a group of children piloting a living tank-fortress to escape an invading empire.",["Strategy","RPG"]],
["Fuga: Melodies of Steel 2","CyberConnect2",77,"The story continues with a new crew and tank, deepening the original's mix of child-crew management and turn-based battles.",["Strategy","RPG"]],
["Trails of Cold Steel III","Nihon Falcom",80,"A new class and story arc in the long-running Trails series, following students at a military academy amid rising political tension.",["RPG"]],
["Trails of Cold Steel IV","Nihon Falcom",82,"The arc's climax, uniting nearly every playable character from the series so far into one final, sprawling turn-based campaign.",["RPG"]],
["Trails into Reverie","Nihon Falcom",83,"A crossover finale weaving together three different protagonists' storylines from across the Cold Steel and Crossbell arcs.",["RPG"]],
["Death end re;Quest 2","Compile Heart",68,"A dark JRPG mixing dungeon-crawling combat with a horror-tinged visual novel story about a cursed virtual world.",["RPG"]],
["Naruto Shippuden: Ultimate Ninja Storm 4","CyberConnect2",83,"An arena fighter retelling the Fourth Great Ninja War, with cinematic set-piece battles built around Naruto's biggest story moments.",["Fighting"]],
["Naruto to Boruto: Shinobi Striker","Soleil",65,"A team-based ninja shooter-brawler hybrid, mixing ranged jutsu and melee combat across four-on-four online matches.",["Fighting","Action"]],
["Jump Force","Spike Chunsoft",64,"A crossover arena fighter pulling characters from Dragon Ball, Naruto, One Piece, and other Shonen Jump series into one roster.",["Fighting"]],
["Attack on Titan 2","Omega Force",76,"A Titan-slaying action game with an original character woven into the anime's story, built around fast aerial grappling combat.",["Action"]],
["SD Gundam Battle Alliance","B.B. Studio",68,"A chibi-styled Gundam action RPG letting players pilot dozens of mobile suits across missions pulled from the franchise's history.",["Action","RPG"]],
["Dynasty Warriors 9","Omega Force",65,"An open-world take on the long-running hack-and-slash series, letting players roam ancient China between massive historical battles.",["Action"]],
["Samurai Warriors 5","Omega Force",73,"A stylized retelling of the Sengoku period, cutting through armies of soldiers as legendary samurai and warlords.",["Action"]],
["Devil May Cry HD Collection","Capcom",78,"A remastered trio of the original Devil May Cry trilogy, bringing Dante's earliest stylish demon-slaying to modern hardware.",["Action"]],
["Onimusha: Warlords","Capcom",73,"A remaster of the original samurai-horror action game, mixing fixed camera angles with demon-slaying swordplay in feudal Japan.",["Action","Horror"]],
["Mega Man Legacy Collection","Capcom",81,"A collection gathering the original six classic Mega Man games with save states and rewind, built for both nostalgia and newcomers.",["Platformer"]],
["Mega Man X Legacy Collection","Capcom",80,"A collection of the X sub-series' earliest entries, following the Maverick Hunter through faster, more mobile platforming action.",["Platformer"]],
["Shenmue I & II","Sega",71,"A remaster of the influential open-world adventure duo, following Ryo Hazuki's slow-burn revenge story through 1980s Japan.",["Adventure","RPG"]],
["Persona 3 Portable","Atlus",79,"The original handheld version of Persona 3, with a playable female protagonist option and streamlined social-link dungeon crawling.",["RPG"]],
["Hyper Light Drifter","Heart Machine",85,"A neon-drenched action-adventure about a wanderer dying from a mysterious illness, exploring a ruined, wordless world for a cure.",["Action","Adventure"]],
["Hyper Light Breaker","Heart Machine",73,"A 3D roguelike spin-off set in the same world as Hyper Light Drifter, built around procedurally shifting biomes and boss runs.",["Action","RPG"]],
["Return of the Obra Dinn","Lucas Pope",86,"A first-person mystery game where the player reconstructs the fate of a ship's entire crew using a device that replays moments of death.",["Puzzle","Adventure"]],
["Monster Train","Shiny Shoe",87,"A deckbuilding roguelike where the player defends a burning train's multiple floors at once, stacking monster clans together.",["Strategy"]],
["Griftlands","Klei Entertainment",83,"A narrative deckbuilder where every conversation is also a card battle, following outlaws navigating a web of double-crosses.",["Strategy","RPG"]],
["Brotato","Blobfish",83,"A frantic top-down survival roguelike starring a potato with up to six weapons equipped at once, fighting waves for thirty seconds at a time.",["Action","Strategy"]],
["Have a Nice Death","Magic Design Studios",78,"A hand-drawn roguelike where the player controls Death himself, cutting through their own overworked corporate afterlife staff.",["Action","Platformer"]],
["Lovers in a Dangerous Spacetime","Asteroid Base",76,"A co-op game where two players run every station of one small spaceship together, from guns to shields to the engine.",["Action"]],
["Moving Out","SMG Studio",76,"A chaotic couch co-op moving simulator where furniture removal turns into physics-based, time-pressured mayhem.",["Puzzle","Sim"]],
["Chivalry 2","Torn Banner Studios",80,"A large-scale medieval melee brawler built around massive battlefield chaos, siege objectives, and satisfyingly weighty sword swings.",["Action"]],
["GTFO","10 Chambers",73,"A brutal four-player co-op horror shooter where sound discipline matters as much as gunplay in a dark, hostile underground complex.",["Horror","Shooter"]],
["Phasmophobia","Kinetic Games",81,"A co-op ghost-hunting game where players use real investigative tools to identify a haunting before it turns deadly.",["Horror"]],
["Cities: Skylines","Colossal Order",85,"The original city-building sim that let players design traffic flow, zoning, and services for sprawling, living cities.",["Sim","Strategy"]],
["Going Under","Aggro Crab",78,"A satirical dungeon-crawling roguelike set inside failed startups, where office supplies double as improvised weapons.",["Action","RPG"]],
["Farming Simulator 22","Giants Software",76,"A detailed farming sim with licensed real-world equipment, letting players manage crops, livestock, and machinery across the seasons.",["Sim"]],
["My Time at Portia","Pathea Games",77,"A crafting and life sim set in a post-apocalyptic workshop town, mixing farming, dungeon-delving, and friendship with the locals.",["RPG","Sim"]],
["My Time at Sandrock","Pathea Games",78,"A desert-set sequel expanding the builder-workshop life sim with a bigger town, deeper crafting, and a new cast of neighbors.",["RPG","Sim"]],
["Disney Dreamlight Valley","Gameloft",73,"A life sim blending Stardew Valley-style farming with Disney and Pixar characters rebuilding a magical, curse-touched valley.",["Sim","Adventure"]],
["Story of Seasons: A Wonderful Life","Marvelous",76,"A remake of a beloved farming-life sim spanning an entire in-game lifetime, from a young farmer's first season to old age.",["Sim","RPG"]],
["AI: The Somnium Files - nirvanA Initiative","Spike Chunsoft",79,"A sequel visual-novel mystery jumping between two timelines and detectives, using the same dream-diving Somnium investigations.",["Adventure"]],
["Coffee Talk","Toge Productions",81,"A cozy narrative game about brewing drinks and listening to a cast of fantasy-creature regulars vent about their lives, one night at a time.",["Adventure","Sim"]],
["Coffee Talk Episode 2: Hibiscus & Butterfly","Toge Productions",79,"A sequel bringing new regulars and drink recipes to the same late-night café, with stories that continue where the first left off.",["Adventure","Sim"]],
["Warhammer 40,000: Boltgun","Auroch Digital",81,"A deliberately retro boomer shooter set in the Warhammer 40K universe, built around chainswords, boltguns, and relentless heretic hordes.",["Shooter"]],
["Killer Frequency","Team17",76,"An '80s-styled horror mystery told through a late-night radio show, where the host must guide callers away from a masked killer live on air.",["Horror","Adventure"]],
["The Case of the Golden Idol","Color Gray Games",84,"A deduction game where each scene is a frozen crime, and the player pieces together names, motives, and events with almost no dialogue.",["Puzzle","Adventure"]],
["Chants of Sennaar","Rundisc",83,"A puzzle-adventure about deciphering the written languages of five isolated civilizations stacked inside a mysterious tower.",["Puzzle","Adventure"]],
["Post Trauma","Red Soul Games",73,"A fixed-camera survival horror game in the classic Silent Hill mold, following a man trapped in a nightmarish, decaying subway system.",["Horror"]],
["Crow Country","SFB Games",81,"A PS1-styled survival horror game set in an abandoned theme park, leaning into tank controls and puzzle-heavy exploration on purpose.",["Horror","Puzzle"]],
["Paranormasight: The Seven Mysteries of Honjo","Square Enix",78,"A horror visual novel following multiple characters racing to complete urban-legend curses for a chance to resurrect the dead.",["Horror","Adventure"]],
["World's End Club","Too Kyo Games",73,"A side-scrolling adventure from the writers of Danganronpa and Zero Escape, following stranded kids surviving a strange, flooded Japan.",["Adventure","Platformer"]],
["Master Detective Archives: Rain Code","Too Kyo Games",78,"A rain-soaked detective adventure from the Danganronpa team, mixing open investigation with surreal deduction trials.",["Adventure","Puzzle"]],
["Slitterhead","Bokeh Game Studio",70,"A body-hopping horror action game from Silent Hill's original director, letting players possess bystanders to hunt flesh-warping monsters.",["Horror","Action"]],
["Zenless Zone Zero","HoYoverse",77,"An urban action RPG with fast, flashy combat and a roster of stylish agents fighting corrupted monsters inside unstable dimensional rifts.",["RPG","Action"]],
["Honkai: Star Rail","HoYoverse",83,"A turn-based sci-fi RPG following the Astral Express crew across a galaxy of distinct, story-driven worlds.",["RPG"]],
["Genshin Impact","HoYoverse",81,"An open-world action RPG built around elemental combos, letting players swap between characters to chain reactions across a vast fantasy world.",["RPG","Action"]],
["Tower of Fantasy","Hotta Studio",68,"An open-world sci-fantasy action RPG with MMO-style co-op exploration and a large roster of collectible, weapon-based characters.",["RPG","Action"]],
["Wuthering Waves","Kuro Games",73,"An open-world action RPG with fast, parry-heavy combat, set on a ruined future Earth reshaped by mysterious cataclysms.",["RPG","Action"]],
["Katamari Damacy Reroll","Bandai Namco Studios",80,"A remaster of the surreal rolling-ball game where a tiny prince grows a sticky ball from thumbtacks to buildings to rebuild the stars.",["Puzzle","Action"]],
["We Love Katamari REROLL+ Royal Reverie","Bandai Namco Studios",81,"A remaster of the beloved sequel, adding new themed levels to the same joyfully absurd rolling-and-collecting formula.",["Puzzle","Action"]],
["LocoRoco 2 Remastered","Japan Studio",79,"A tilt-the-world platformer starring blobby, singing creatures, remastered from the original PSP sequel.",["Platformer","Puzzle"]],
["Patapon 2 Remastered","Japan Studio",80,"A rhythm-strategy game where drumbeats command a tribe of tiny warriors through march, attack, and defense commands.",["Strategy","Sim"]],
["Grand Theft Auto IV","Rockstar North",90,"A darker, grounded entry in the GTA series following an immigrant war veteran chasing the American dream through Liberty City, playable on PS5 via the PS Plus Premium classics catalog.",["Action"]],
["Call of Duty: Modern Warfare II","Infinity Ward",73,"A 2022 reboot-continuation following Task Force 141 through a modern, gadget-heavy campaign alongside its massive multiplayer suite.",["Shooter"]],
["Call of Duty: Modern Warfare III","Sledgehammer Games",56,"A direct sequel bringing back an open-combat mission structure and a returning roster of classic multiplayer maps.",["Shooter"]],
["Call of Duty: Warzone","Infinity Ward",80,"The series' free-to-play battle royale, dropping over a hundred players into a massive, constantly rotating map.",["Shooter"]],
["Call of Duty: Black Ops Cold War","Treyarch",73,"A Cold War-era conspiracy campaign built around a mysterious operative named Perseus, alongside the series' Zombies mode.",["Shooter"]],
["Call of Duty: Vanguard","Sledgehammer Games",63,"A World War II entry following a multinational special forces squad across several of the war's major fronts.",["Shooter"]],
["FIFA 23","EA Vancouver",81,"The final FIFA-branded entry before the EA Sports FC rebrand, with cross-play and both men's and women's club football.",["Sim"]],
["Among Us","Innersloth",71,"A social deduction game where a crew of colorful astronauts tries to root out disguised impostors before their ship falls apart.",["Puzzle"]],
["PUBG: Battlegrounds","Krafton",70,"The battle royale that helped define the genre, dropping a hundred players onto a shrinking island armed with whatever they can scavenge.",["Shooter"]],
["The Sims 4","Maxis",70,"The long-running life simulator letting players build homes and guide simulated people through careers, relationships, and daily chaos.",["Sim"]],
["Rust","Facepunch Studios",73,"A brutal open-world survival game where players build bases, craft weapons, and constantly watch their backs against other players.",["Sim","Action"]],
["ARK: Survival Evolved","Studio Wildcard",70,"A dinosaur-filled survival game where players tame prehistoric creatures, build bases, and fight to survive a hostile island.",["Sim","Action"]],
["ARK: Survival Ascended","Studio Wildcard",64,"A remastered rebuild of the original ARK on modern tech, with overhauled visuals and updated creature and building systems.",["Sim","Action"]],
["EA Sports PGA Tour","EA Tiburon",75,"A golf sim built around real courses and a career mode following a pro's rise from amateur qualifiers to the majors.",["Sim"]],
["Ratchet & Clank","Insomniac Games",85,"A remake of the original PS2 classic, sending the Lombax and his robot sidekick across colorful planets armed with absurd weaponry.",["Platformer","Action"]],
["Marvel's Avengers","Crystal Dynamics",68,"A superhero action game reassembling Earth's Mightiest Heroes after a disaster, mixing single-player story with co-op missions.",["Action","RPG"]],
["Star Wars Battlefront II","DICE",67,"A large-scale Star Wars shooter spanning the prequel, original, and sequel trilogies, with a single-player campaign from the Empire's side.",["Shooter"]],
["Star Wars Battlefront","DICE",73,"A Star Wars shooter recreating iconic original-trilogy battles with an emphasis on atmosphere and cinematic large-scale combat.",["Shooter"]],
["Mortal Kombat 11","NetherRealm Studios",83,"A time-travel story pitting past and present versions of the roster against each other, alongside the series' signature Fatalities.",["Fighting"]],
["Injustice: Gods Among Us","NetherRealm Studios",81,"A DC Comics fighting game set in a world where Superman has become an authoritarian ruler after a personal tragedy.",["Fighting"]],
["Batman: Arkham City","Rocksteady Studios",91,"A sprawling sequel turning a walled-off section of Gotham into Batman's open playground, hunting down a rogues' gallery of villains.",["Action"]],
["Batman: Arkham Asylum","Rocksteady Studios",92,"The game that reinvented superhero games, trapping Batman inside Arkham Asylum as the Joker takes over the facility.",["Action"]],
["Just Dance 2024","Ubisoft Paris",70,"The yearly dance-along party game with a fresh setlist of pop songs, playable with just a phone as the controller.",["Sim"]],
["Heavy Rain","Quantic Dream",87,"A branching, choice-driven thriller following four characters investigating a serial killer, where any of them can permanently die.",["Adventure"]],
["LittleBigPlanet 3","Sumo Digital",78,"A physics-based platformer starring Sackboy, built as much around its massive level-creation toolset as its own campaign.",["Platformer","Puzzle"]],
["The Crew 2","Ivory Tower",71,"An open-world racing game spanning a scaled-down United States, letting players switch between cars, boats, and planes on the fly.",["Racing"]],
["Need for Speed Heat","Ghost Games",73,"A street racing game splitting each day between legal daytime races and riskier, police-chased night races for cash and rep.",["Racing"]],
["Dirt 5","Codemasters",75,"An arcade-leaning off-road racer spanning rally, ice, and stadium events across a colorful, globe-trotting career.",["Racing"]],
["Mortal Kombat X","NetherRealm Studios",83,"A generational story picking up years after MK9, introducing character variations that split each fighter into distinct playstyles.",["Fighting"]],
["Dead or Alive 6","Team Ninja",68,"A fast, counter-heavy 3D fighter known for its Break Blow finishers and destructible, multi-tiered stages.",["Fighting"]],
["Virtua Fighter 5 R.E.V.O.","Sega",80,"A rerelease of the technical 3D fighter long respected by the FGC for its grounded, no-frills martial arts combat.",["Fighting"]],
["Persona 5 Strikers","Omega Force",81,"A Musou-style action spin-off sending the Phantom Thieves on a road trip, mixing real-time combat with the series' Palace exploration.",["Action","RPG"]],
["Don't Starve Together","Klei Entertainment",81,"The co-op version of Klei's survival game, dropping friends into a dark, whimsical wilderness that punishes carelessness.",["Sim","Adventure"]],
["Don't Starve","Klei Entertainment",80,"A single-player survival game with a hand-drawn gothic art style, where hunger, sanity, and darkness all fight to kill the player.",["Sim","Adventure"]],
["LEGO Marvel Super Heroes","TT Games",83,"A LEGO take on the Marvel universe, letting players smash through an open New York as dozens of heroes and villains.",["Action","Platformer"]],
["LEGO Harry Potter Collection","TT Games",78,"A remastered bundle of both LEGO Harry Potter games, covering all seven years of Hogwarts in brick-built form.",["Action","Adventure"]],
["Minecraft Dungeons","Mojang",68,"An action-RPG dungeon crawler set in the Minecraft universe, built for co-op loot runs rather than open-world building.",["RPG","Action"]],
["Plants vs. Zombies: Battle for Neighborville","PopCap Games",73,"A class-based shooter spin-off pitting plant and zombie factions against each other across colorful, suburban battlegrounds.",["Shooter"]],
["Splitgate","1047 Games",75,"An arena shooter that bolts Portal-style portals onto Halo-inspired combat, letting players flank through walls mid-firefight.",["Shooter"]],
["Battlefield 1","DICE",85,"A World War I shooter that reframed the series around the era's brutal, chaotic trench warfare and early tank combat.",["Shooter"]],
["Assassin's Creed II","Ubisoft Montreal",91,"The entry that defined the series' modern identity, following Ezio Auditore's revenge story across Renaissance Italy.",["Action","RPG"]],
["Assassin's Creed Brotherhood","Ubisoft Montreal",90,"A direct sequel to AC II set in Rome, introducing the series' first multiplayer mode alongside Ezio's continued story.",["Action","RPG"]],
["Tomb Raider","Crystal Dynamics",86,"The 2013 reboot reintroducing Lara Croft as a survivor stranded on a hostile island, rebuilding the series around grounded action.",["Action","Adventure"]],
["Rise of the Tomb Raider","Crystal Dynamics",86,"A direct sequel sending Lara to Siberia in search of a lost city, expanding the reboot's exploration and crafting systems.",["Action","Adventure"]],
["Shadow of the Tomb Raider","Eidos Montreal",81,"The reboot trilogy's conclusion, following Lara into Central America as she races to stop a Maya apocalypse she helped unleash.",["Action","Adventure"]],
["Metal Gear Solid V: The Phantom Pain","Kojima Productions",95,"An open-world stealth epic following Big Boss's revenge campaign, widely considered one of the genre's high points for systemic freedom.",["Action","Adventure"]],
["Metal Gear Solid V: Ground Zeroes","Kojima Productions",80,"A short, prologue-sized mission set on a single sprawling base, serving as a tech demo and lead-in for The Phantom Pain.",["Action","Adventure"]],
["Dying Light","Techland",74,"A zombie survival game built around fluid parkour movement, where staying on rooftops matters as much as staying armed.",["Horror","Action"]],
["Borderlands 2","Gearbox Software",89,"A cult-classic looter-shooter with cel-shaded visuals, wildly varied guns, and a fan-favorite villain in Handsome Jack.",["Shooter","RPG"]],
["Borderlands: The Handsome Collection","Gearbox Software",81,"A remastered bundle of Borderlands 2 and The Pre-Sequel, with all their expansions included.",["Shooter","RPG"]],
["Saints Row: The Third Remastered","Volition",71,"A remaster of the series' most over-the-top entry, leaning fully into absurd gang warfare and open-world chaos.",["Action"]],
["Crash Bandicoot N. Sane Trilogy","Vicarious Visions",80,"A remastered bundle of the original three PS1 Crash games, rebuilding the marsupial's classic platforming from the ground up.",["Platformer"]],
["Doom: The Dark Ages","id Software",85,"A prequel to the modern Doom reboots, trading pure speed for heavier, more deliberate combat with a shield-saw and giant mechs.",["Shooter"]],
["Mafia: The Old Country","Hangar 13",78,"A prequel set in early 1900s Sicily, tracing the mafia's roots before the series' usual American city settings.",["Action"]],
["Metal Gear Solid Delta: Snake Eater","Konami",87,"A ground-up remake of the jungle-set stealth classic, rebuilding Naked Snake's origin story with modern visuals and controls.",["Action","Adventure"]],
["Ninja Gaiden 4","Team Ninja/PlatinumGames",83,"A return for the brutally fast ninja action series, adding a new protagonist alongside series veteran Ryu Hayabusa.",["Action"]],
["Fatal Fury: City of the Wolves","SNK",82,"A revival of SNK's classic fighting series, rebuilding its roster and REV system for a new generation of street fights.",["Fighting"]],
["Rayman Origins","Ubisoft Montpellier",86,"A hand-drawn 2D platformer that relaunched the limbless hero, built around tight controls and gorgeous, painterly level art.",["Platformer"]],
["Sonic Superstars","Sonic Team",74,"A 2D Sonic throwback with co-op support and new Emerald Powers that let characters transform mid-level.",["Platformer"]],
["Sonic Colors Ultimate","Blind Squirrel Entertainment",68,"A remaster of the Wisp-powered platformer, sending Sonic through an alien amusement park built from kidnapped planets.",["Platformer"]],
["Sonic Generations","Sonic Team",80,"A nostalgia-driven platformer pairing classic 2D Sonic with modern 3D Sonic across remixed levels from the series' history.",["Platformer"]],
["Spyro Reignited Trilogy","Toys for Bob",80,"A remaster bundling the original three PS1 Spyro games, rebuilding the purple dragon's worlds from scratch in modern visuals.",["Platformer"]],
["Psychonauts","Double Fine Productions",87,"A platformer about a psychic summer-camp kid diving literally into other characters' minds, each level a surreal reflection of its owner.",["Platformer","Adventure"]],
["Unravel Two","Coldwood Interactive",77,"A co-op platformer starring two yarn creatures connected by a literal thread, solving physics puzzles that require cooperation.",["Platformer","Puzzle"]],
["Castle Crashers","The Behemoth",83,"A hand-drawn co-op beat-'em-up where knights smash through a cartoonish kingdom to rescue kidnapped princesses.",["Action"]],
["Broforce","Free Lives",78,"A destructible, pixel-art run-and-gun parodying '80s action movies, letting up to four players level entire levels with explosives.",["Action","Platformer"]],
["Anno 1800","Ubisoft Blue Byte",85,"An industrial-era city builder balancing trade routes, production chains, and colonization across a growing island empire.",["Strategy","Sim"]],
["Surviving Mars","Haemimont Games",76,"A colony-building sim about establishing humanity's first Mars settlement, managing oxygen, water, and morale under a hostile sky.",["Strategy","Sim"]],
["Dungeons 4","Realmforge Studios",76,"A tongue-in-cheek dungeon-management strategy game where the player plays the villain, building traps to stop meddling heroes.",["Strategy"]],
["Evil Genius 2: World Domination","Rebellion Developments",75,"A base-building strategy game casting the player as a cartoonish supervillain, building a secret lair and training a henchmen army.",["Strategy","Sim"]],
["Tales of Symphonia Remastered","Bandai Namco Studios",68,"A remaster of the beloved GameCube-era JRPG, following a group bound to save two worlds sharing one soul.",["RPG"]],
["Tales of Zestiria","Bandai Namco Studios",71,"An entry in the long-running Tales series where the protagonist can merge with spirits called Seraphim to power up in battle.",["RPG"]],
["Romancing SaGa 2: Revenge of the Seven","Square Enix",80,"A remake of a cult-classic SaGa title, built around a non-linear structure where the playable ruler can change across generations.",["RPG"]],
["SaGa Emerald Beyond","Square Enix",80,"A free-form RPG with dozens of branching worlds and endings, continuing the SaGa series' famously non-traditional structure.",["RPG"]],
["Dragon Quest III HD-2D Remake","Square Enix",87,"A remake of the series' foundational third entry, rebuilt in the same HD-2D style as Octopath Traveler.",["RPG"]],
["Alone in the Dark","Pieces Interactive",67,"A reimagining of the early survival horror series, sending two investigators into a decaying Louisiana mansion full of secrets.",["Horror"]],
["Destroy All Humans!","Black Forest Games",74,"A remake of the alien-rampage comedy game, letting players abduct, vaporize, and mind-control 1950s small-town America.",["Action"]],
["Serious Sam 4","Croteam",68,"An over-the-top boomer shooter built around absurdly large enemy swarms and an equally absurd arsenal to mow them down with.",["Shooter"]],
["Far Cry 2","Ubisoft Montreal",84,"An early open-world Far Cry set in a war-torn African state, notable for weapons that jam and fires that spread realistically.",["Shooter","Action"]],
["Wolfenstein: The New Order","MachineGames",85,"A reboot imagining a world where the Nazis won World War II, following BJ Blazkowicz's one-man resistance campaign.",["Shooter"]],
["Wolfenstein: Youngblood","MachineGames",65,"A co-op spin-off starring BJ Blazkowicz's twin daughters, continuing the family's war against Nazi occupation in 1980s Paris.",["Shooter"]],
["MotoGP 24","Milestone",75,"The official MotoGP sim with a rebuilt career mode, letting players rise from junior leagues to the premier class.",["Racing"]],
["EA Sports FC 25","EA Vancouver",73,"The second entry under the EA Sports FC name, with an expanded Rush mode and the usual roster of real clubs and leagues.",["Sim"]],
["Star Wars: Squadrons","Motive Studio",81,"A first-person Star Wars dogfighting game with full cockpit immersion, letting players fly for either the New Republic or the Empire.",["Shooter","Sim"]],
["Trine 2","Frozenbyte",83,"A co-op fantasy puzzle-platformer where three heroes' unique abilities combine to solve physics puzzles across painterly fairy-tale levels.",["Puzzle","Platformer"]],
["The Legend of Heroes: Trails to Azure","Nihon Falcom",85,"A direct sequel continuing the Crossbell arc, following the same police-investigation-turned-conspiracy story.",["RPG"]],
["The Legend of Heroes: Trails from Zero","Nihon Falcom",85,"The start of the Crossbell arc, following a newly formed police unit investigating crimes tangled in city politics.",["RPG"]],
["Tales of Graces f Remastered","Bandai Namco Studios",72,"A remaster of a fan-favorite Tales entry, built around a real-time combat system with unusually deep combo customization.",["RPG"]],
["God Eater 3","Bandai Namco Studios",70,"A monster-hunting action RPG set in an ash-covered apocalypse, where players wield shape-shifting God Arc weapons.",["RPG","Action"]],
["Freedom Wars Remastered","Dimps",70,"A remaster of a PS Vita cult favorite, where citizens are born with absurd prison sentences and fight giant Abductors to reduce their time.",["Action","RPG"]],
["Gravity Rush Remastered","Japan Studio",78,"A remaster of the gravity-defying action game, letting a memory-loss heroine fall in any direction across a surreal floating city.",["Action","Adventure"]],
["Gravity Rush 2","Japan Studio",78,"A direct sequel expanding the original's gravity-shifting movement with new powers and a larger, more varied world.",["Action","Adventure"]],
["Everybody's Golf","Clap Hanz",79,"A cheerful, approachable golf game with an expressive create-a-character system, long a PlayStation mainstay.",["Sim"]],
["Puyo Puyo Tetris 2","Sega",76,"A crossover puzzle game letting players mix or compete between Puyo Puyo's chain-matching and classic Tetris, including combined modes.",["Puzzle"]],
["Tetris Effect: Connected","Monstars/Resonair",89,"An audiovisual reinvention of Tetris where every line clear ripples through a synesthetic world of music and light.",["Puzzle"]],
["WipEout Omega Collection","Clever Beans",83,"A remastered bundle of the futuristic anti-gravity racing series, prized for its blistering speed and crisp, punishing tracks.",["Racing"]],
["House Flipper","Frozen District",78,"A relaxing simulation about buying, renovating, and reselling rundown houses, mixing cleaning chores with real-estate flipping.",["Sim"]],
["House Flipper 2","Frozen District",76,"A sequel expanding the renovation sim with a bigger town, deeper customization, and the same satisfying before-and-after flips.",["Sim"]],
["Goat Simulator 3","Coffee Stain North",76,"A deliberately broken, physics-chaos sandbox starring a destructive goat, built purely for absurd multiplayer mayhem.",["Sim","Action"]],
["Kao the Kangaroo","Tate Multimedia",68,"A revival of a 2000s platforming mascot, sending a boxing-glove-wearing kangaroo through colorful 3D collect-a-thon levels.",["Platformer"]],
["Sly Cooper: Thieves in Time","Sanzaru Games",76,"A time-traveling entry in the stealth-platformer series, sending master thief Sly Cooper through his ancestors' eras to save his gang.",["Platformer","Action"]],
["Jak and Daxter: The Precursor Legacy","Naughty Dog",82,"The PS2-era platformer that preceded Uncharted at Naughty Dog, following a boy and his transformed best friend across a seamless open world.",["Platformer","Adventure"]],
["Ape Escape 2","Japan Studio",76,"A 3D platformer built around a motion-sensitive gadget glove, sending players to capture mischievous time-traveling monkeys.",["Platformer"]],
["LittleBigPlanet","Media Molecule",87,"The original physics-platformer and level-creation toolset starring Sackboy, built as much for player-made content as its own campaign.",["Platformer","Puzzle"]],
["Tearaway Unfolded","Media Molecule",79,"A papercraft-styled platformer where the world itself is built from folded paper, following a living messenger named iota or atoi.",["Platformer","Adventure"]],
["Lost Soul Aside","UltiZero Games",71,"A stylish action RPG years in development, following a young man who gains a dragon-like companion after his world is consumed by a dimensional rift.",["Action","RPG"]],
["Baby Steps","Devolver Digital",75,"A deliberately awkward walking simulator where every single step is manually controlled, turning a climb up a mountain into a genuinely difficult physical comedy.",["Adventure","Puzzle"]],
["Keeper","Double Fine Productions",76,"A wordless, surreal adventure starring a lighthouse brought to life, waddling across a strange coastline toward an unknown purpose.",["Adventure","Puzzle"]],
["Towers of Aghasba","Dreamlit Games",70,"A tribal survival-builder about restoring a sacred, dying island by cultivating its ecosystem and constructing villages for its people.",["Sim","Adventure"]],
["Mandragora: Whispers of the Witch Tree","Primal Game Studio",78,"A 2D Soulslike action RPG set in a dark, inquisition-themed fantasy world, mixing deep skill trees with tightly punishing combat.",["Action","RPG"]],
["Dying Light: The Beast","Techland",78,"A standalone follow-up bringing back original protagonist Kyle Crane, transformed and hunting the man responsible for experimenting on him.",["Horror","Action"]],
["Nobody Wants to Die","Critical Hit Games",74,"A neo-noir detective story set in a body-swapping future New York, mixing narrative investigation with a moody, Blade Runner-inspired atmosphere.",["Adventure","Puzzle"]],
["Atelier Yumia: The Alchemist of Memories & the Envisioned Land","Gust",75,"An entry in the long-running Atelier series, following an alchemist uncovering forbidden knowledge in a land where alchemy itself has been outlawed.",["RPG"]],
["Dynasty Warriors: Origins","Omega Force",80,"A reinvention of the long-running hack-and-slash series with a single original protagonist, rebuilding the formula around tighter, more cinematic battles.",["Action"]],
["Like a Dragon: Pirate Yakuza in Hawaii","Ryu Ga Gotoku Studio",80,"A swashbuckling spin-off starring Goro Majima, mixing naval ship battles with the series' usual over-the-top brawling across Hawaii.",["Action","RPG"]],
["PaRappa the Rapper Remastered","SIE Japan Studio",72,"A remaster of the rhythm game that helped define the genre, following a rapping dog through absurd lessons from a cast of talking instructors.",["Sim"]],
["MediEvil","SIE",70,"A remake of the PS1 classic, reviving skeleton knight Sir Daniel Fortesque to fight his way through a gothic, comic-horror kingdom.",["Action","Adventure"]],
["Rock Band 4","Harmonix",75,"The long-running band rhythm game, letting up to four players perform guitar, bass, drums, and vocals together across a huge song library.",["Sim"]],
["Fantasian Neo Dimension","Mistwalker",81,"A JRPG from Final Fantasy creator Hironobu Sakaguchi, mixing handcrafted diorama-style environments with a 'Dimengeon' system for instantly storing fought enemies.",["RPG"]],
["Visions of Mana","Square Enix",75,"An entry in the Mana series following a young man escorting childhood friends chosen as Soul Guardians on a one-way pilgrimage.",["RPG"]],
["The Legend of Heroes: Kuro no Kiseki","Nihon Falcom",81,"A new arc following a former mercenary pulled into a corporate-backed criminal case in a city outside the series' usual setting.",["RPG"]],
["The Legend of Heroes: Kuro no Kiseki II","Nihon Falcom",82,"A direct sequel continuing the new arc's storyline, deepening the political conspiracy introduced in the first Kuro no Kiseki.",["RPG"]],
["Shin Megami Tensei III Nocturne HD Remaster","Atlus",80,"A remaster of the cult-classic demon-summoning RPG, following a lone survivor of Tokyo's near-total destruction and remaking in a demonic conception.",["RPG"]],
["Digimon Story: Cyber Sleuth Complete Edition","Bandai Namco Studios",78,"A monster-collecting RPG bundle following a hacker investigating a mysterious game tied to real-world disappearances in digital Tokyo.",["RPG"]],
["Digimon Survive","Bandai Namco Studios",73,"A visual-novel-tactics hybrid where a school trip goes wrong and the survivors are stranded in a Digital World where any character can permanently die.",["Strategy","RPG"]],
["World of Final Fantasy","Square Enix",73,"A chibi-styled JRPG where twins shrink down into a land of classic Final Fantasy monsters, which they capture and stack to fight.",["RPG"]],
["20 Minutes Till Dawn","flanne",80,"A pixel-art survival shooter roguelike built around a strict 20-minute timer, swarmed by Lovecraftian horrors the whole way through.",["Action","Shooter"]],
["Children of Morta","Dead Mage",83,"A hand-painted action roguelike following one extended family of monster hunters, where every member can be played across a connected, story-driven campaign.",["Action","RPG"]],
["Enter the Gungeon","Dodge Roll",85,"A bullet-hell roguelike dungeon crawler where the dungeon's loot can supposedly kill the past, sending gunfighters diving through bullets to reach it.",["Action","Shooter"]],
["Exit the Gungeon","Dodge Roll",72,"A spin-off escape-the-dungeon roguelike, reversing the original's premise into a frantic climb up and out instead of down and in.",["Action","Shooter"]],
["Gunfire Reborn","Duoyi Games",83,"A co-op roguelike shooter mixing RPG-style elemental builds with procedurally generated levels and an anthropomorphic-animal cast.",["Shooter","RPG"]],
["Risk of Rain 2","Hopoo Games",89,"A 3D roguelike shooter where the longer a run goes, the stronger both the player's stacked items and the swarming enemies become.",["Shooter","Action"]],
["Valkyria Chronicles 4","Sega",80,"A tactical RPG returning to the series' original war-torn continent, mixing turn-based strategy with real-time third-person movement on the battlefield.",["Strategy","RPG"]],
["Phoenix Point","Snapshot Games",70,"A tactical strategy game from an XCOM co-creator, defending humanity's last factions against a mutating alien threat with a destructible, geoscape-driven campaign.",["Strategy"]],
["Wargroove 2","Chucklefish",76,"A turn-based tactics game styled after classic Advance Wars, continuing with a new commander and expanded co-op campaign options.",["Strategy"]],
["The Jackbox Party Pack","Jackbox Games",78,"A collection of phone-controlled party games for a crowd, built around trivia, drawing, and bluffing games playable with just one console and everyone's phones.",["Puzzle","Sim"]],
["Bleach: Rebirth of Souls","Bandai Namco Studios",73,"A 3D arena fighter adapting the Bleach anime's major arcs, letting players battle as Soul Reapers, Hollows, and Quincy across its signature spirit-powered clashes.",["Fighting"]],
["Hunter x Hunter: Nen x Impact","Bandai Namco Studios",71,"A 2.5D fighting game adapting the Hunter x Hunter manga, built around each character's unique Nen ability rather than a single universal combat system.",["Fighting"]],
["Minishoot' Adventures","Soft Rains",85,"A top-down action-adventure mixing bullet-hell shoot-'em-up combat with Zelda-style dungeon exploration in a tiny spaceship.",["Action","Shooter"]],
["Replaced","Sad Cat Studios",75,"A side-scrolling action game set in a retrofuturistic 1980s city, following a consciousness trapped inside a synthetic human body.",["Action","Platformer"]],
["Hollow Knight: Silksong","Team Cherry",92,"A long-awaited sequel sending Hornet, rather than the original Knight, through a new kingdom full of silk and song, continuing the first game's dense, punishing exploration.",["Platformer","Action"]],
["Towerborne","Stoic Studio",72,"A co-op beat-'em-up set in a storybook-styled world, defending a floating city from monstrous threats alongside friends in seasonal content drops.",["Action"]],
["Little Kitty, Big City","Double Dagger Studio",80,"A playful open-world adventure starring a house cat who falls from a windowsill and has to make its way back home through a bustling, cat-sized city.",["Adventure"]],
["Thank Goodness You're Here!","Coal Supper",81,"A slapstick comedy adventure set in a tiny Northern English town, where a traveling salesman gets pulled into increasingly absurd local errands.",["Adventure","Puzzle"]],
["Mouthwashing","Wrong Organ",81,"A psychological horror game told in fragmented flashbacks aboard a crashed cargo ship, as its stranded crew's situation grows more desperate and strange.",["Horror","Adventure"]],
["Hauntii","Moonloop Games",78,"A dreamlike exploration-adventure starring a small ghost navigating a surreal afterlife, collecting stardust to find a way back to the world of the living.",["Adventure","Puzzle"]],
["Nour: Play with Your Food","Terrifying Jellyfish",72,"An abstract, physics-based sandbox where players manipulate oversized, colorful food in a sensory playground with no fail states or goals.",["Sim","Puzzle"]],
["Eternal Strands","Yellow Brick Games",74,"An action-adventure about a band of outcast magic users climbing giant, physics-driven creatures to reclaim a forbidden, long-abandoned city.",["Action","RPG"]],
["Sword of the Sea","Giant Squid",81,"A flowing, skateboarding-across-sand adventure from the makers of Abzû, surfing dunes on a magical blade to restore life to a dried-up ocean.",["Adventure"]],
["Hell is Us","Rogue Factor",71,"A third-person action-adventure set in a fictional country torn by civil war and a supernatural phenomenon, deliberately withholding map markers and quest waypoints.",["Action","Adventure"]],
["Ninja Gaiden: Ragebound","Dotemu",82,"A 2D side-scrolling return to the series' roots, set during the original Ninja Gaiden's story and starring a new ninja protecting her shattered clan.",["Action","Platformer"]],
["Onimusha 2: Samurai's Destiny","Capcom",76,"A remaster of the PS2-era sequel, sending a new samurai protagonist across feudal Japan with a tag-team system of recruitable allies.",["Action","Horror"]],
["UFO 50","Mossmouth",91,"A collection of fifty original, full-sized games spanning every genre, styled as if they were all made by one imaginary 1980s studio.",["Action","Strategy"]],
["Pacific Drive","Ironwood Studios",79,"A survival-driving game about keeping a sentient, increasingly damaged station wagon running through a supernatural, government-quarantined forest.",["Sim","Horror"]],
["1000xRESIST","sunset visitor 1BIT",88,"A narrative sci-fi adventure jumping between memory and present day, following a clone investigating the legacy of humanity's last survivor.",["Adventure"]],
["Jusant","Don't Nod",82,"A quiet climbing game about scaling an impossibly tall tower in a world left behind by vanished water, accompanied only by a small shell-like creature.",["Adventure","Puzzle"]],
["Venba","Visai Games",82,"A narrative cooking game following an Indian immigrant family across generations, told through the recipes a mother tries to pass down to her son.",["Adventure","Sim"]],
["A Highland Song","Inkle",79,"A frantic, physical platformer about racing across the Scottish Highlands on foot to reach a lighthouse in time, armed only with a map and a lot of running.",["Platformer","Adventure"]],
["Mika and the Witch's Mountain","Chibig",74,"A cozy broom-flying adventure following a young witch's first solo delivery job across a Mediterranean-inspired archipelago.",["Adventure","Sim"]],
["Dordogne","Un Je Ne Sais Quoi",76,"A watercolor-styled narrative adventure about a woman returning to her late grandmother's house in rural France, remembering a childhood summer there.",["Adventure","Puzzle"]],
["Cat Quest III","The Gentlebros",80,"A pirate-themed entry in the cat-and-dragon action RPG series, sending a feline captain sailing an open sea full of loot and silly puns.",["RPG","Action"]],
["Core Keeper","Pugstorm",82,"A mining-and-crafting survival game set entirely underground, where players dig out a cavern base while fighting toward an ancient buried core.",["Sim","RPG"]],
["Smalland: Survive the Wilds","Merge Games",68,"A survival-crafting game where the player is shrunk to insect size, building tiny settlements and fighting oversized bugs in an ordinary backyard turned epic wilderness.",["Sim","Action"]],
["The Order: 1886","Ready at Dawn",63,"A gothic steampunk action game set in an alternate Victorian London, following Knights of the Round Table armed with advanced weapons against a half-breed threat.",["Shooter","Action"]],
["MLB The Show 25","Sony San Diego Studio",79,"The annual baseball sim with deep franchise and Road to the Show career modes, alongside the series' detailed pitching and hitting mechanics.",["Sim"]],
["Tony Hawk's Pro Skater 3+4","Iron Galaxy",79,"A remake bundling the third and fourth classic Tony Hawk games, rebuilding their iconic parks and combo-chasing arcade skating.",["Sim","Action"]],
["2XKO","Riot Games",76,"A tag-team fighting game set in the League of Legends universe, built around accessible inputs layered with deep combo tech for competitive play.",["Fighting"]],
["The Casting of Frank Stone","Supermassive Games",68,"A branching horror narrative set in the Dead by Daylight universe, following multiple characters whose choices determine who survives a cursed film production.",["Horror","Adventure"]],
["Avatar: Frontiers of Pandora","Massive Entertainment",75,"An open-world action game set on Pandora, following a Na'vi raised by humans who returns to fight for the land after years of captivity.",["Action","Adventure"]],
["Flintlock: The Siege of Dawn","A44 Games",74,"A fast, dash-heavy action RPG where a gunpowder soldier and her fox companion fight back against returning, vengeful gods.",["Action","RPG"]],
["Banishers: Ghosts of New Eden","Don't Nod",75,"A supernatural action RPG set in colonial New England, following a pair of ghost hunters whose investigation turns personal after one of them dies.",["Action","RPG"]],
["RoboCop: Rogue City","Teyon",78,"A first-person action game putting players directly in RoboCop's armor, mixing slow, powerful combat with Detroit police investigation work.",["Shooter","Action"]],
["The Texas Chain Saw Massacre","Sumo Digital",64,"An asymmetrical horror multiplayer game where a family of killers, including Leatherface, hunts a group of trapped victims trying to escape.",["Horror","Action"]],
["Killer Klowns from Outer Space: The Game","Teravision Games",65,"An asymmetrical horror comedy pitting a team of humans against player-controlled alien clowns armed with absurd, cotton-candy-themed weapons.",["Horror","Action"]],
["Outer Worlds","Obsidian Entertainment",85,"A satirical sci-fi RPG set in a corporate-controlled star system, following a colonist revived decades late into a world run entirely by competing companies.",["RPG","Shooter"]],
["The Outer Worlds 2","Obsidian Entertainment",82,"A sequel continuing the series' corporate-satire RPG formula, sending players into a new star system with a fresh cast of companies to undermine.",["RPG","Shooter"]],
["Hunt: Showdown 1896","Crytek",81,"A tense, PvPvE bounty-hunting shooter set in the swamps of 1890s Louisiana, where every monster hunt can be interrupted by rival player hunters.",["Shooter","Horror"]],
["We Happy Few","Compulsion Games",58,"A dystopian survival game set in a drug-dependent English town where refusing the mandatory happy pills marks you an outsider to be hunted.",["Action","Horror"]],
["Dying Light 2 Stay Human","Techland",75,"A parkour-driven zombie survival game set in a sprawling city, where the player's choices shape which factions control which parts of town.",["Action","Horror"]],
["Vampire: The Masquerade – Bloodlines 2","The Chinese Room",65,"A narrative RPG set in modern Seattle's vampire underworld, following a newly turned Fledgling navigating clan politics and a city on the edge of exposure.",["RPG","Action"]]
,
["Session: Skate Sim","crea-ture Studios",72,"A physics-driven skateboarding sim where every trick is controlled manually through the two sticks, favoring realism over arcade combo chaining.",["Sim","Action"]],
["Lightyear Frontier","Frame Break",73,"A cozy mech-farming game where players pilot a customizable mech to till soil, harvest crops, and explore an alien frontier at their own pace.",["Sim","Adventure"]],
["Cult of the Lamb: Unholy Alliance","Massive Monster",85,"An expansion-sized update to the cult-management roguelike, adding new followers, areas, and systems to the original's dungeon-and-base-building loop.",["Action","Strategy"]],
["Okami HD","Clover Studio",87,"Play as the sun goddess in wolf form, restoring a painted Japan with a celestial brush in this storybook action adventure.",["Action","Adventure"]],
["Moonlighter","Digital Sun",76,"By day run a village shop, by night plunder shifting dungeons for loot to sell — a charming mix of roguelike combat and retail management.",["Action","RPG","Sim"]],
["Shovel Knight","Yacht Club Games",85,"A heartfelt 8-bit-style platformer where a shovel doubles as a weapon and pogo stick, with tight levels and a great chiptune score.",["Platformer","Action"]],
["Spiritfarer","Thunder Lotus Games",85,"Captain a ferry for departed spirits, tending to them with cooking, crafting, and hugs before they move on — a gentle management adventure about loss.",["Adventure","Sim"]],
["Carrion","Phobia Game Studio",79,"Play as an amorphous red monster escaping a facility, growing larger and deadlier — a reverse horror with metroidvania progression.",["Action","Horror"]],
["Heavenly Bodies","2pt Interactive",77,"Cosmonauts repair space stations with physics-driven limbs, a slapstick co-op puzzler of floating and fumbling in zero gravity.",["Puzzle","Sim"]],
["Manifold Garden","William Chyr Studio",75,"Rotate gravity in an infinite, geometric world of impossible architecture in this serene, mind-bending first-person puzzle game.",["Puzzle"]],
["Papers, Please","Lucas Pope",85,"Work a border checkpoint in a fictional authoritarian state, inspecting documents under pressure while moral choices pile up.",["Puzzle","Sim"]],
["Frostpunk","11 bit studios",84,"Lead the last city on Earth through a world-ending freeze, with every law and survival decision carrying ethical weight.",["Strategy","Sim"]],
["Frostpunk 2","11 bit studios",80,"A decades-later sequel focused on governing a growing city and the factions within it, as politics replace pure survival.",["Strategy","Sim"]],
["Against the Storm","Eremite Games",85,"Lead settlers in a rain-drenched fantasy forest as a roguelite city builder, where each run asks you to build and escape the storm.",["Strategy","Sim"]],
["Dorfromantik","Toukana Interactive",80,"Lay hex tiles to craft sprawling villages, forests, and rivers — a quiet, meditative puzzle about building scenery.",["Puzzle","Sim"]],
["Pentiment","Obsidian Entertainment",86,"A 16th-century Bavarian murder mystery told through manuscript-style art, where your choices as an artist reshape a village.",["RPG","Adventure"]],
["Warhammer 40,000: Darktide","Fatshark",80,"A four-player co-op shooter and melee slugfest through a hive city overrun by cultists, in the grim darkness of the far future.",["Shooter","Action"]],
["Warhammer: Vermintide 2","Fatshark",82,"Four heroes fight through hordes of ratmen in a fast, first-person melee co-op game set in the Warhammer fantasy world.",["Action","Shooter"]],
["Observer: System Redux","Bloober Team",70,"A neural detective hacks into minds inside a grimy cyberpunk tenement, in an atmospheric, unsettling psychological horror game.",["Horror","Adventure"]],
["Outlast","Red Barrels",80,"Armed only with a camcorder, a journalist explores an asylum full of horrors with no weapons — pure first-person survival-horror panic.",["Horror"]],
["The Dark Pictures Anthology: Man of Medan","Supermassive Games",62,"A diving trip goes wrong on a ghost ship — a choice-driven horror where decisions can get any character killed.",["Horror","Adventure"]],
["Life is Strange","Dontnod Entertainment",85,"A photography student rewinds time to fix a mystery and her friendship in a heartfelt, choice-driven episodic adventure.",["Adventure"]],
["Life is Strange: True Colors","Deck Nine",80,"A young woman with empathic powers uncovers the truth about her brother's death in a lakeside mountain town.",["Adventure"]],
["Tell Me Why","Dontnod Entertainment",76,"Twins reunited after a decade revisit their pasts and clashing memories of a traumatic night in a narrative adventure.",["Adventure"]],
["Gone Home","The Fullbright Company",82,"Return to an empty family house in 1995 and piece together a story from objects, notes, and cassettes — a quiet exploration game.",["Adventure"]],
["Wytchwood","Alientrap",76,"Take quests from the forest's creatures as a witch, gathering ingredients and crafting spells in a cozy fairy-tale adventure.",["Adventure","Sim"]],
["Coral Island","Stairway Games",80,"A farming sim with an ocean conservation twist: grow crops, befriend townspeople, and restore a coral reef.",["Sim","RPG"]],
["Farming Simulator 25","Giants Software",75,"Farm crops, livestock, and forestry across new Asian and European-inspired maps with a huge collection of licensed machinery.",["Sim"]],
["Assetto Corsa Competizione","Kunos Simulazioni",78,"A GT World Challenge-licensed racing sim with detailed physics, weather, and endurance races on real circuits.",["Racing","Sim"]],
["WRC Generations","KT Racing",75,"A rally game that covers the sport's season and multi-stage events across gravel, tarmac, and snow with detailed handling.",["Racing"]],
["Wreckfest","Bugbear Entertainment",80,"A destruction derby racing game where every car crumples and bashing opponents is the point of the race.",["Racing"]],
["TT Isle of Man: Ride on the Edge 3","Kylotonn",65,"A road-racing motorcycle game set on the legendary, treacherous Isle of Man course, demanding precise speed.",["Racing","Sports"]],
["OlliOlli World","Roll7",82,"A skateboarding platformer with chill, stylish tricks and a colorful, wacky world, built around flowing grinds and flip combos.",["Sports","Platformer"]],
["Windjammers 2","Dotemu",70,"A fast and frantic arcade sport of flying-disc throwing, bringing back the cult 1990s classic with modern netplay.",["Sports","Action"]],
["Lumines Remastered","Resonair",80,"Match falling blocks in sync with a sweeping timeline bar as the music and visuals shift — a hypnotic rhythm-puzzle classic.",["Puzzle"]],
["A Hat in Time","Gears for Breakfast",80,"A time-traveling girl collects hourglasses across colorful 3D worlds in a love letter to collect-a-thon platformers.",["Platformer","Adventure"]],
["Lost in Random","Zoink",78,"A dark-fairy-tale kingdom where everyone's fate is decided by a dice roll — a card-and-dice combat adventure with gothic charm.",["Adventure","Action"]],
["Another Crab's Treasure","Aggro Crab",80,"A hermit crab with a soda-can shell takes on an ocean of mollusks in a souls-like with a humorous, satirical tone.",["Action","Adventure"]],
["Sonic X Shadow Generations","Sonic Team",80,"A Sonic anniversary celebration that bundles a remastered Generations with a new campaign starring Shadow and his chaos powers.",["Platformer","Action"]],
["Persona 5 Tactical","P-Studio",77,"The Phantom Thieves return in a stylish tactical RPG, fighting in a revolutionary war with grid-based turn-based combat.",["RPG","Strategy"]],
["Virtua Fighter 5 Ultimate Showdown","Ryu Ga Gotoku Studio",80,"The classic 3D fighter returns with its famed ring-out and counter-based systems, with rollback netcode for online matches.",["Fighting"]],
["Skullgirls 2nd Encore","Lab Zero Games",79,"A hand-drawn 2D fighter with fast combos, a team-building system, and a cast of eccentric, art-deco characters.",["Fighting"]],
["Brawlhalla","Blue Mammoth Games",76,"A free-to-play platform brawler where up to eight players knock each other off the stage with weapons and legend powers.",["Fighting","Action"]],
["Call of Duty: Black Ops 7","Treyarch / Raven Software",65,"A near-future Black Ops entry set in 2035, with a four-player co-op campaign and a post-campaign Endgame mode.",["Shooter","Action"]],
["Call of Duty: Modern Warfare (2019)","Infinity Ward",81,"A gritty reboot of the Modern Warfare story, with night raids, tense close-quarters missions, and morally murky decisions.",["Shooter","Action"]],
["Call of Duty: Infinite Warfare","Infinity Ward",77,"A far-future war across the solar system, with zero-gravity combat, starship dogfights, and a Mars-orbit assault.",["Shooter","Action"]],
["Call of Duty: WWII","Sledgehammer Games",79,"A return to the Western Front, following an infantry squad from the Normandy beaches to the heart of Germany.",["Shooter","Action"]],
["Call of Duty: Black Ops III","Treyarch",80,"A 2065 black-ops thriller of cybernetic soldiers, neural links, and a playable co-op campaign for up to four players.",["Shooter","Action"]],
["Call of Duty: Black Ops 4","Treyarch",80,"A multiplayer-first entry with no solo campaign, featuring Blackout battle royale and three Zombies experiences.",["Shooter"]],
["Call of Duty: Advanced Warfare","Sledgehammer Games",79,"Exosuit-powered soldiers and private military corporations reshape the battlefield of the 2050s.",["Shooter","Action"]],
["Call of Duty: Ghosts","Infinity Ward",76,"A brotherhood of elite soldiers fights back after a space weapon is turned against the United States.",["Shooter","Action"]],
["Call of Duty: Modern Warfare Remastered","Raven Software",78,"A remaster of the 2007 landmark shooter, with its famous campaign and multiplayer rebuilt with modern visuals.",["Shooter","Action"]],
["Call of Duty: Modern Warfare 2 Campaign Remastered","Beenox",76,"The 2009 campaign, rebuilt with modern visuals, following a task force through a global conflict and betrayal.",["Shooter","Action"]],
["Forza Horizon 5","Playground Games",92,"An open-world racing festival across a sprawling, varied recreation of Mexico, from jungles to deserts to volcanic peaks.",["Racing"]],
["Elden Ring Nightreign","FromSoftware",80,"A co-op spin-off where teams of three survive a time-limited run across a shifting land, ending in a boss showdown.",["Action","RPG"]],
["Crisis Core: Final Fantasy VII Reunion","Square Enix",80,"A remaster of the prequel that follows SOLDIER Zack Fair in the years before Final Fantasy VII.",["RPG","Action"]],
["The Last Guardian","genDESIGN",78,"A boy and a giant griffin-like creature must trust each other to escape a vast, ruined fortress.",["Adventure","Puzzle"]],
["Dreams","Media Molecule",89,"A creative playground where you can play, build, and share games, art, and music, with its own narrative campaign.",["Sim","Adventure"]],
["Marvel's Midnight Suns","Firaxis Games",83,"A card-driven tactical RPG pairing Marvel heroes with a created hero to stop a demonic threat.",["Strategy","RPG"]],
["Final Fantasy XIV Online","Square Enix",83,"A sprawling online fantasy RPG in the realm of Eorzea, known for its story-driven expansions and raids.",["RPG"]],
["The Elder Scrolls V: Skyrim Anniversary Edition","Bethesda Game Studios",82,"The legendary open-world fantasy RPG in the frozen north, bundled with Creation Club content.",["RPG","Adventure"]],
["Age of Empires II: Definitive Edition","Forgotten Empires",84,"The classic medieval real-time strategy game, remastered with campaigns focused on famous historical leaders.",["Strategy"]],
["Concrete Genie","Pixelopus",72,"A bullied boy brings a seaside town back to life by painting living creatures with a magic brush.",["Adventure","Puzzle"]],
["Gears of War: Reloaded","The Coalition",80,"A remaster of the first game in the cover-based shooter series, with a brutal fight against the Locust Horde.",["Shooter","Action"]],
["Ace Combat 7: Skies Unknown","Bandai Namco Studios",80,"A fast, flashy air-combat game of dogfights, missile locks, and sweeping aerial battles.",["Action","Sim"]],
["Chrono Cross: The Radical Dreamers Edition","Square Enix",76,"A time-bending JRPG about a boy who slips into a parallel world, featuring over 40 recruitable characters.",["RPG"]],
["Crypt of the NecroDancer","Brace Yourself Games",86,"A rhythm-roguelike where you move and fight in time to the beat as you delve into a crypt.",["Action","Strategy"]],
["Tiny Tina's Wonderlands","Gearbox Software",80,"A looter-shooter fantasy tabletop adventure with swords, spells, and bullets, hosted by a chaotic game master.",["Shooter","RPG"]],
["Tchia","Awaceb",75,"An island adventure set in a New Caledonia-inspired archipelago, where you can swim, glide, and possess animals.",["Adventure"]],
["Avowed","Obsidian Entertainment",82,"A first-person fantasy RPG in the world of Eora, with a mix of melee, magic, and gunplay.",["RPG","Action"]],
["Deus Ex: Mankind Divided","Eidos-Montréal",84,"A cyberpunk action-RPG about an augmented agent in a world that fears and segregates the enhanced.",["RPG","Action"]],
["Bulletstorm: Full Clip Edition","People Can Fly",78,"A over-the-top shooter that rewards stylish, creative kills with a leash, boots, and wild weaponry.",["Shooter","Action"]],
["The Wolf Among Us","Telltale Games",85,"A noir mystery in which fairy-tale characters live in hiding in 1980s New York, with a sheriff who has a wolf's temper.",["Adventure"]],
["The Walking Dead: The Telltale Definitive Series","Telltale Games",83,"All seasons of the choice-driven zombie saga, centered on the bond between survivors and a young girl.",["Adventure","Horror"]],
["Tales from the Borderlands","Telltale Games",85,"A comedic episodic adventure in the Borderlands universe, told by two unreliable narrators.",["Adventure"]],
["Batman: The Telltale Series","Telltale Games",76,"An episodic Batman story where your choices as Bruce Wayne shape Gotham's politics and his allies.",["Adventure","Action"]],
["Life is Strange 2","Dontnod Entertainment",78,"An episodic road-trip drama about two brothers on the run, where choices shape the younger one's growth.",["Adventure"]],
["Life is Strange: Before the Storm","Deck Nine",77,"A prequel following Chloe Price and Rachel Amber's friendship during the weeks that changed both their lives.",["Adventure"]],
["Life is Strange: Double Exposure","Deck Nine",72,"Max Caulfield returns, now an adult photographer, investigating a murder with a new power to shift between timelines.",["Adventure"]],
["Like a Dragon: Ishin!","Ryu Ga Gotoku Studio",78,"A reimagined Yakuza spin-off set in the turbulent final years of the Tokugawa shogunate, with sword and pistol combat.",["Action","Adventure"]],
["Bayonetta Origins: Cereza and the Lost Demon","PlatinumGames",81,"A storybook prequel to Bayonetta, following a young witch and a demon trapped in a stuffed cat through an enchanted forest.",["Action","Adventure"]],
["Syberia: The World Before","Microids Studio Paris",70,"A point-and-click adventure that alternates between two eras, linking a modern investigator to a pianist from the past.",["Adventure","Puzzle"]],
["Dishonored: Death of the Outsider","Arkane Studios",76,"A standalone stealth-action story that sends a former assassin to kill the Outsider, the god-like figure behind the series' powers.",["Action","Adventure"]],
["Uncharted: Legacy of Thieves Collection","Naughty Dog",87,"A PS5 bundle of Uncharted 4 and The Lost Legacy, with improved performance and visuals.",["Action","Adventure"]],
["Vanquish","PlatinumGames",84,"A hyper-speed cover shooter in which a power-suited soldier slides, boosts, and slow-mo blasts through a space station.",["Shooter","Action"]],
["Abzu","Giant Squid",76,"A serene underwater journey through coral reefs and ancient ruins, with no words and a gorgeous score.",["Adventure"]],
["GreedFall","Spiders",72,"A colonial-era fantasy RPG where a diplomat explores a mysterious island, balancing factions, magic, and a deadly plague.",["RPG"]],
["Horizon Call of the Mountain","Guerrilla Games",80,"A PS VR2 spin-off in the Horizon world that puts you in the climbing gear of a reformed outlaw.",["Adventure","Action"]],
["Sherlock Holmes: Chapter One","Frogwares",70,"An open-world detective story of a young Holmes and his friend Jon investigating a mystery on a Mediterranean island.",["Adventure","Puzzle"]],
["Elex","Piranha Bytes",71,"A post-apocalyptic sci-fi RPG where medieval warriors and technology-driven factions fight over a mysterious resource.",["RPG","Action"]],
["Resident Evil Revelations","Capcom",80,"A survival-horror entry set aboard a drifting ocean liner, mixing tight corridors with the series' monster-filled mystery.",["Horror","Action"]],
["Resident Evil Revelations 2","Capcom",72,"An episodic survival-horror story that follows two pairs of characters, one exploring while the other supports.",["Horror","Action"]],
["Resident Evil 5","Capcom",75,"A co-op-focused action horror set in Africa, pairing Chris Redfield with a local partner.",["Shooter","Horror"]],
["Resident Evil 6","Capcom",67,"A bombastic multi-campaign entry that follows four sets of characters through a global bioterror crisis.",["Shooter","Horror"]],
["Mass Effect: Andromeda","BioWare",71,"A space-faring RPG in which a new Pathfinder explores a distant galaxy to find a home for humanity.",["RPG","Shooter"]],
["inFAMOUS First Light","Sucker Punch Productions",76,"A standalone Second Son prequel starring neon-powered Fetch, with fast, arcade-style superpowered combat.",["Action","Adventure"]],
["Darksiders III","Gunfire Games",58,"A third-person action-adventure where the horseman Fury hunts down sins in a ruined world, with Souls-like combat.",["Action","Adventure"]],
["Zero Escape: The Nonary Games","Spike Chunsoft",86,"A pair of visual-novel puzzle thrillers where strangers are forced into a deadly game of room escapes.",["Puzzle","Adventure"]],
["Outlast 2","Red Barrels",75,"A first-person survival horror in a remote Arizona community, where a cameraman has no way to fight back.",["Horror"]],
["Blair Witch","Bloober Team",67,"A first-person horror set in the haunted woods of Black Hills, where the player searches with only a dog and flashlight.",["Horror","Adventure"]],
["Fatal Frame: Maiden of Black Water","Koei Tecmo",72,"A Japanese ghost-hunting horror series entry where you fight spirits by photographing them with a special camera.",["Horror","Adventure"]],
["Back 4 Blood","Turtle Rock Studios",70,"A four-player co-op zombie shooter from the Left 4 Dead creators, featuring a card-based progression system.",["Shooter","Horror"]],
["Evil West","Flying Wild Hog",72,"A pulpy third-person action game where a vampire hunter takes on supernatural creatures in the American frontier.",["Action","Shooter"]],
["Far Cry Primal","Ubisoft Montreal",70,"A Stone Age spin-off with clubs, spears, and tamed beasts instead of guns and vehicles.",["Action","Adventure"]],
["Killing Floor 2","Tripwire Interactive",75,"A gory co-op shooter where squads of up to six hold off waves of mutated horrors using class-based perks.",["Shooter","Horror"]],
["Final Fantasy VII","Square",92,"The original landmark JRPG about a mercenary joining an eco-terrorist group, now in a modern PlayStation port.",["RPG"]],
["Final Fantasy VIII Remastered","Square Enix",80,"A remaster of the 1999 JRPG centered on young mercenaries, with the unusual Junction and Draw magic systems.",["RPG"]],
["Final Fantasy IX","Square",94,"A fairy-tale-inspired JRPG featuring a thief, a princess, and a whimsical cast across a kingdom at war.",["RPG"]],
["Assassin's Creed III","Ubisoft Montreal",80,"An open-world stealth adventure set in Colonial America, following a young assassin during the Revolutionary War.",["Action","Adventure"]],
["Assassin's Creed Unity","Ubisoft Montreal",72,"A French Revolution-era entry set in a detailed recreation of Paris, with parkour across rooftops and crowds.",["Action","Adventure"]],
["Assassin's Creed Syndicate","Ubisoft Quebec",76,"A Victorian London sandbox where twin assassins take on gangs and corrupt industrialists.",["Action","Adventure"]],
["Assassin's Creed Rogue","Ubisoft Sofia",75,"A naval-focused Assassin's Creed that casts you as a former assassin who joins the Templars.",["Action","Adventure"]],
["DOOM","id Software",85,"A relentless first-person shooter reboot that rewards speed and aggression across a demon-infested Mars base.",["Shooter","Action"]],
["Rage 2","Avalanche Studios",72,"An open-world shooter in a colorful wasteland, mixing gunplay with superpowers and vehicle combat.",["Shooter","Action"]],
["Metal Gear Solid: Master Collection Vol. 1","Konami",78,"A collection of the first Metal Gear Solid games, covering the stealth series' defining espionage stories.",["Action","Adventure"]],
["Resident Evil","Capcom",90,"A high-definition remaster of the 2002 remake that kicked off survival horror, set in a trap-filled mansion.",["Horror","Adventure"]],
["Resident Evil 0","Capcom",83,"A prequel survival-horror game in which you swap between two characters to solve puzzles and survive.",["Horror","Adventure"]],
["Dead Rising Deluxe Remaster","Capcom",78,"A comic zombie sandbox set in a shopping mall, where nearly every item is a weapon.",["Action","Horror"]],
["Marvel's Spider-Man Remastered","Insomniac Games",87,"A polished open-world Spider-Man adventure with fluid web-swinging and a heartfelt story set in Manhattan.",["Action","Adventure"]],
["God of War III Remastered","Santa Monica Studio",91,"The brutal conclusion to the Greek-era saga, with Kratos ascending Mount Olympus in a spectacle-filled rampage.",["Action","Adventure"]],
["Shadow Warrior 3","Flying Wild Hog",70,"A fast, humorous first-person shooter with a grappling hook, katana, and constant, acrobatic movement.",["Shooter","Action"]],
["The Sinking City","Frogwares",63,"An open-world detective game set in a flooded 1920s New England city haunted by cosmic horror.",["Adventure","Horror"]],
["Call of Cthulhu","Cyanide Studio",64,"A first-person investigation game based on the Lovecraft tabletop RPG, with sanity affecting what you see.",["Adventure","Horror"]],
["The Dark Pictures Anthology: Little Hope","Supermassive Games",64,"A choice-driven horror where a stranded group of travelers can live or die based on your decisions.",["Horror","Adventure"]],
["Final Fantasy XII: The Zodiac Age","Square Enix",86,"A remaster of a political fantasy JRPG with an innovative, programmable combat system and a re-balanced job system.",["RPG"]],
["Danganronpa 1·2 Reload","Spike Chunsoft",86,"A bundle of the first two murder-mystery visual novels featuring courtroom debates and a sinister mascot.",["Adventure","Puzzle"]],
["BioShock 2 Remastered","2K Marin",80,"A return to the underwater city of Rapture, playing a Big Daddy protector searching for his lost Little Sister.",["Shooter","Horror"]],
["Valkyria Chronicles","Sega",86,"A tactical RPG with a watercolor look, blending turn-based planning with real-time movement and aiming.",["Strategy","RPG"]],
["Torment: Tides of Numenera","inXile Entertainment",74,"A text-heavy, story-driven RPG set a billion years in the future, where combat is optional.",["RPG"]],
["Pillars of Eternity: Complete Edition","Obsidian Entertainment",89,"A classic-style isometric fantasy RPG with real-time-with-pause combat and a deeply reactive story.",["RPG"]],
["Wolfenstein: The Old Blood","MachineGames",78,"A standalone prequel shooter with two campaigns, one in a castle and one in a ruined village, mixing stealth and gunplay.",["Shooter","Action"]],
["Pathfinder: Kingmaker","Owlcat Games",74,"A massive tabletop-style RPG where you rule your own kingdom, with party management and deep character building.",["RPG","Strategy"]],
["Everybody's Gone to the Rapture","The Chinese Room",75,"A quiet, story-driven exploration game set in an empty English village, where you piece together what happened.",["Adventure"]],
["The Vanishing of Ethan Carter","The Astronauts",76,"A first-person mystery set in a beautiful forested valley, where you reconstruct crime scenes with supernatural clues.",["Adventure","Puzzle"]],
["Limbo","Playdead",88,"A monochrome puzzle-platformer about a boy navigating a dark, dangerous forest, with no spoken words.",["Platformer","Puzzle"]],
["Unravel","Coldwood Interactive",77,"A gentle puzzle-platformer starring a small creature made of red yarn, who uses its own thread to swing and climb.",["Platformer","Puzzle"]],
["Last Day of June","Ovosonico",73,"A painterly narrative adventure about a man trying to change a tragic day by reliving it through other people's eyes.",["Adventure","Puzzle"]],
["Sea of Solitude","Jo-Mei Games",70,"An emotional adventure about loneliness set in a flooded, monster-filled city that you explore by boat.",["Adventure"]],
["Stranger of Paradise: Final Fantasy Origin","Team Ninja",65,"A tough, fast action RPG that retells the first Final Fantasy's story with a darker, more aggressive tone.",["Action","RPG"]],
["Final Fantasy Type-0 HD","Square Enix",70,"A war-focused action RPG where you control a squad of students in a conflict between nations with magical crystals.",["Action","RPG"]],
["Biomutant","Experiment 101",63,"An open-world action RPG starring a furry mutant, with kung-fu combat, crafting, and a narrator who explains the world.",["Action","RPG"]],
["Remothered: Tormented Fathers","Darril Arts",58,"A stealth survival-horror game where you are hunted through a mansion, inspired by classic Italian horror.",["Horror"]],
["Amnesia: The Dark Descent","Frictional Games",86,"A landmark horror game in which you have no weapons, and the darkness itself is a threat to your sanity.",["Horror","Adventure"]],
["Hotline Miami","Dennaton Games",85,"A neon-soaked top-down action game of fast, brutal, one-hit-kill missions set to a pulsing synth soundtrack.",["Action"]],
["Hotline Miami 2: Wrong Number","Dennaton Games",78,"The sequel widens the story to several characters, with more varied levels and the same instant-restart brutality.",["Action"]],
["Furi","The Game Bakers",81,"A stylish boss-rush action game of one-on-one duels, with sword combat and bullet-hell shooting.",["Action"]],
["Guacamelee! 2","DrinkBox Studios",80,"A colorful, Mexican folklore-inspired brawler-platformer in which a luchador fights through a multiverse.",["Platformer","Action"]],
["Mutant Year Zero: Road to Eden","The Bearded Ladies",77,"A tactical game that mixes stealthy exploration with turn-based combat, led by a mutant duck and boar.",["Strategy","RPG"]],
["The Banner Saga","Stoic",80,"A Viking-inspired tactical RPG where your decisions on a long journey decide who lives and who dies.",["Strategy","RPG"]],
["The Banner Saga 2","Stoic",82,"The second chapter continues the caravan's journey through a fantasy world on the brink of collapse.",["Strategy","RPG"]],
["Fate/Samurai Remnant","Omega Force",74,"A samurai action RPG set in 17th-century Edo, where a ritual summons legendary spirits to fight.",["Action","RPG"]],
["Berserk and the Band of the Hawk","Omega Force",67,"A hack-and-slash adaptation of a dark fantasy manga, with massive battles against hordes of enemies.",["Action"]],
["Cloudpunk","Ion Lands",72,"A moody cyberpunk story game where you deliver packages at night across a neon-lit, vertical city.",["Adventure"]],
["Deliver Us Mars","KeokeN Interactive",70,"A sci-fi puzzle adventure where an astronaut explores abandoned Martian settlements in search of answers.",["Adventure","Puzzle"]],
["Deliver Us the Moon","KeokeN Interactive",71,"A sci-fi mystery about an astronaut sent to a silent lunar base to save an energy-starved Earth.",["Adventure","Puzzle"]],
["Layers of Fear 2","Bloober Team",65,"A psychological horror game in which an actor's surreal journey through an ocean liner twists reality.",["Horror","Adventure"]],
["Maid of Sker","Wales Interactive",66,"A stealth horror in a creepy Welsh hotel in which you can't fight back, only hide from sound-sensitive enemies.",["Horror"]],
["Tom Clancy's Ghost Recon Wildlands","Ubisoft Paris",71,"A tactical open-world shooter where a four-person squad can take on a drug cartel across a huge Bolivia.",["Shooter","Action"]],
["Rime","Tequila Works",72,"A wordless puzzle adventure on a sunlit island, with a boy, a fox, and a mystery about his past.",["Adventure","Puzzle"]],
["Red Faction: Guerrilla Re-Mars-tered","KAOS Studios",76,"A sandbox shooter with fully destructible buildings, where you smash through structures with a sledgehammer.",["Shooter","Action"]],
["Thief","Eidos-Montréal",67,"A stealth game in which a master thief creeps through a dark, plague-ridden city.",["Action","Adventure"]],
["Styx: Shards of Darkness","Cyanide Studio",75,"A stealth-focused fantasy game starring a sarcastic goblin assassin who sneaks through huge, vertical levels.",["Action","Adventure"]],
["Mirror's Edge Catalyst","DICE",70,"A first-person parkour game in which a courier runs across the rooftops of a clean, authoritarian city.",["Action","Adventure"]],
["Bastion","Supergiant Games",86,"An action RPG with a gravelly narrator who describes your every move in a world that is falling apart.",["Action","RPG"]],
["Transistor","Supergiant Games",83,"A sci-fi action RPG that mixes real-time and planned-out combat, starring a singer and a talking sword.",["Action","RPG"]],
["Pyre","Supergiant Games",82,"A fantasy RPG that replaces traditional combat with magical 3-on-3 matches, driven by a branching story.",["RPG","Sports"]],
["Darksiders Genesis","Airship Syndicate",78,"A dungeon-crawling action game in which two apocalyptic horsemen fight through demonic hordes.",["Action","RPG"]],
["Hob","Runic Games",75,"A wordless action-adventure in which a small hero reshapes a living, mechanical landscape.",["Adventure","Action"]],
["Child of Light","Ubisoft Montreal",81,"A painterly fairy-tale RPG with turn-based combat and a story told in rhyming verse.",["RPG","Platformer"]],
["Valiant Hearts: The Great War","Ubisoft Montpellier",79,"A hand-drawn adventure about ordinary people caught up in World War I, mixing puzzles with historical facts.",["Adventure","Puzzle"]],
["Beyond Good & Evil 20th Anniversary Edition","Ubisoft Montpellier",83,"A cult-classic adventure with photography, stealth, and exploration on an alien-menaced planet.",["Adventure","Action"]],
["The Technomancer","Spiders",60,"A sci-fi RPG on Mars where you choose how to use electricity-wielding abilities in a harsh colony.",["RPG","Action"]],
["Bound by Flame","Spiders",56,"A dark fantasy action RPG in which a mercenary hosts a fire demon within his body.",["RPG","Action"]],
["Death's Gambit","White Rabbit",72,"A hard side-scrolling action RPG about a warrior who serves Death in a strange, dying world.",["Action","RPG"]],
["Knack","SIE Japan Studio",54,"A family-friendly action platformer in which a hero made of ancient relics grows and shrinks.",["Platformer","Action"]],
["Nights of Azure 2: Bride of the New Moon","Gust",66,"An action RPG in which a demon-hunting heroine fights alongside summoned creatures in a gothic world.",["Action","RPG"]],
["Atelier Sophie: The Alchemist of the Mysterious Book","Gust",75,"A cozy alchemy RPG with a focus on crafting, gathering ingredients, and a talking book.",["RPG","Sim"]],
["Star Ocean: First Departure R","Square Enix",66,"A remake of a classic sci-fi JRPG where a young hero meets people from space on a medieval planet.",["RPG"]],
["Lost Sphear","Tokyo RPG Factory",58,"A traditional turn-based JRPG about a boy who restores a world that is disappearing into nothingness.",["RPG"]],
["I am Setsuna","Tokyo RPG Factory",65,"A melancholy, snow-covered JRPG with a piano score about a journey to sacrifice a girl.",["RPG"]],
["Greak: Memories of Azur","Navegante Entertainment",78,"A hand-drawn puzzle-platformer in which siblings cooperate to rescue their family from an invasion.",["Platformer","Puzzle"]],
["Kingdom Two Crowns","Raw Fury",78,"A minimalist strategy game where you ride a horse and spend coins to build a kingdom and defend it nightly.",["Strategy","Sim"]],
["The Last Campfire","Hello Games",72,"A short, cozy puzzle adventure in which a lost wanderer helps other lost souls find their way.",["Adventure","Puzzle"]],
["Rez Infinite","Enhance",89,"A rhythmic on-rails shooter where every shot adds to the music, with an additional VR-ready area.",["Shooter","Puzzle"]],
["Gorogoa","Buried Signal",87,"A hand-drawn puzzle game that manipulates four panels to connect images and tell a story.",["Puzzle"]],
["Machinarium","Amanita Design",82,"A hand-drawn point-and-click puzzle adventure set in a world of robots, with no spoken dialogue.",["Puzzle","Adventure"]],
["Grim Fandango Remastered","Double Fine Productions",85,"A classic noir adventure set in the Land of the Dead, remastered with new visuals and a revamped control scheme.",["Adventure","Puzzle"]],
["Day of the Tentacle Remastered","Double Fine Productions",86,"A remake of a classic time-travel comedy adventure with cartoon visuals and wacky puzzles.",["Adventure","Puzzle"]],
["Full Throttle Remastered","Double Fine Productions",79,"A remastered point-and-click adventure about a biker gang, with a rock soundtrack and gruff humor.",["Adventure","Puzzle"]],
["Broken Age","Double Fine Productions",79,"A hand-painted adventure following two teenagers in separate worlds whose stories gradually intertwine.",["Adventure","Puzzle"]],
["Shantae: Half-Genie Hero","WayForward",78,"A hand-animated platformer with a belly-dancing hero whose hair is her whip, and a growing set of dance-based transformations.",["Platformer","Action"]],
["Shantae and the Seven Sirens","WayForward",80,"A colorful metroidvania set on a tropical island, with transformation dances and a mystery about kidnapped half-genies.",["Platformer","Adventure"]],
["Monster Boy and the Cursed Kingdom","Game Atelier",80,"A platformer-adventure where a boy transforms into a pig, snake, lion, and more to explore an enchanted world.",["Platformer","Adventure"]],
["Wonder Boy: The Dragon's Trap","Lizardcube",84,"A hand-drawn remake of a classic in which a hero is cursed into animal forms, each with its own abilities.",["Platformer","Adventure"]],
["Wonder Boy: Asha in Monster World","Toylogic",70,"A remake of a classic action-adventure about a young warrior and her pet who help a fantasy land.",["Platformer","Adventure"]],
["The Messenger","Sabotage Studio",85,"A ninja platformer that begins as an 8-bit action game and transforms into something much bigger.",["Platformer","Action"]],
["Wandersong","Greg Lobanov",80,"A cheerful adventure in which a bard solves puzzles and befriends others by singing, rather than by fighting.",["Adventure","Puzzle"]],
["VA-11 Hall-A: Cyberpunk Bartender Action","Sukeban Games",81,"A bartending visual novel in which you mix drinks and talk to the customers of a dystopian future city.",["Adventure","Sim"]],
["Paradise Killer","Kaizen Game Works",80,"An open-world murder mystery set in a neon, surreal island where you investigate the killing of the ruling council.",["Adventure","Puzzle"]],
["Thimbleweed Park","Terrible Toybox",80,"A retro point-and-click mystery with five playable characters, set in a small town with a murder and a lot of secrets.",["Adventure","Puzzle"]],
["Fez","Polytron",85,"A puzzle-platformer in which a 2D character discovers that his world is actually 3D, and learns to rotate it.",["Platformer","Puzzle"]],
["Anthem","BioWare",55,"A cooperative online action game where you fly and fight in powered exosuits across a wild, dangerous frontier.",["Shooter","RPG"]],
["Flower","thatgamecompany",78,"A peaceful, wordless experience in which you guide a stream of flower petals through the wind over fields and cities.",["Adventure"]],
["Far Cry New Dawn","Ubisoft Montreal",73,"A colorful post-apocalyptic sequel set in a bloom-covered Hope County, with outposts and a pair of ruthless villains.",["Shooter","Action"]],
["Dandara","Long Hat House",75,"A gravity-defying metroidvania in which you leap between surfaces instead of walking or running.",["Platformer","Action"]],
["CrossCode","Radical Fish Games",85,"An action RPG with a retro look that plays like an online game, with puzzles and combat in a huge world.",["RPG","Action"]],
["Coromon","TRAGsoft",78,"A creature-collecting RPG in which you catch and train monsters to explore islands and uncover a threat.",["RPG"]],
["Monster Sanctuary","Moi Rai Games",80,"A metroidvania where you tame monsters, build a team, and use their abilities to explore a connected world.",["RPG","Platformer"]],
["Shadow Tactics: Blades of the Shogun","Mimimi Games",85,"A real-time stealth-tactics game set in feudal Japan, in which you use a team of specialists to infiltrate enemy camps.",["Strategy","Action"]],
["Warhammer 40,000: Mechanicus","Bulwark Studios",78,"A turn-based tactics game starring the robotic, religious tech-priests of a grim, far-future empire.",["Strategy"]],
["Warhammer: Chaosbane","Eko Software",65,"An action RPG in which heroes fight hordes of Chaos creatures in a dark fantasy version of the Warhammer world.",["Action","RPG"]],
["Warhammer 40,000: Inquisitor - Martyr","NeocoreGames",70,"A dark sci-fi action RPG where you play an Inquisitor hunting heretics and demons across a battlefield sector.",["Action","RPG"]],
["Torchlight II","Runic Games",84,"A fast, colorful dungeon-crawling action RPG with loot, pets, and four distinct character classes.",["Action","RPG"]],
["Victor Vran","Haemimont Games",75,"An action RPG with jumping, dodging, and a rock-and-roll soundtrack, set in a gothic demon-infested city.",["Action","RPG"]],
["Baldur's Gate: Dark Alliance","Snowblind Studios",74,"A console dungeon-crawling action RPG set in the Forgotten Realms, with hack-and-slash combat.",["Action","RPG"]],
["Neverwinter Nights: Enhanced Edition","Beamdog",75,"A fantasy RPG based on Dungeons & Dragons rules, with a campaign and tools for making your own adventures.",["RPG"]],
["Icewind Dale: Enhanced Edition","Beamdog",80,"A classic isometric D&D RPG focused on party combat in a frozen northern land.",["RPG"]],
["Planescape: Torment: Enhanced Edition","Beamdog",85,"A text-heavy cult classic RPG in which words, not swords, are the main way to solve problems.",["RPG"]],
["Sword Art Online: Alicization Lycoris","Aquria",67,"An action RPG based on the anime, set in a vast virtual world where the characters struggle to survive.",["Action","RPG"]],
["Sword Art Online: Hollow Realization","Aquria",63,"An action RPG where players team up in an online game with a persistent world, from the Sword Art Online anime.",["Action","RPG"]],
["One Punch Man: A Hero Nobody Knows","Spike Chunsoft",65,"A 3D arena fighter based on the anime about a hero who defeats any enemy with a single punch.",["Fighting"]],
["Fairy Tail","Gust",69,"A turn-based JRPG based on the anime of the same name, starring members of a rowdy wizard guild.",["RPG"]],
["Black Clover: Quartet Knights","Systems Prod.",57,"An online team-based action game based on the anime about wizards in a magical kingdom.",["Action"]],
["JoJo's Bizarre Adventure: All-Star Battle R","CyberConnect2",75,"A flashy 3D fighter featuring heroes and villains from across the long-running manga series.",["Fighting"]],
["Star Ocean: The Divine Force","tri-Ace",70,"A sci-fi JRPG with real-time combat and a lot of mobility, with two protagonists from different worlds.",["RPG","Action"]],
["Star Ocean: The Last Hope","tri-Ace",72,"A sci-fi JRPG about humanity searching for a new home in space after the Earth is damaged.",["RPG"]],
["Secret of Mana","Square Enix",60,"A remake of a classic action RPG with a sword, a magic tree, and cooperative play.",["RPG","Action"]],
["Legend of Mana","Square Enix",76,"A remaster of an unusual action RPG in which you rebuild the world by placing landmarks on a map.",["RPG","Action"]],
["Final Fantasy IV","Square Enix",86,"A pixel-art remaster of the classic 1991 JRPG that popularized dramatic, character-driven stories in games.",["RPG"]],
["Dead Rising 4","Capcom Vancouver",67,"A comedic zombie sandbox where nearly everything can be used as a weapon, set in a festive mall.",["Action","Horror"]],
["Cave Story+","Nicalis",86,"A beloved side-scrolling action-adventure with a charming story about a robot and a rabbit-like people.",["Platformer","Action"]],
["Hitman 2","IO Interactive",82,"A stealth sandbox in which you eliminate targets in large, detailed environments, using disguises and gadgets.",["Action","Adventure"]],
["Megadimension Neptunia VIIR","Idea Factory",67,"A JRPG parody of the gaming industry, starring goddess characters who are personifications of consoles.",["RPG"]],
["ELEX II","Piranha Bytes",60,"A sci-fi fantasy open-world RPG with a jetpack, and factions that fight over a mysterious energy source.",["RPG","Action"]],
["Hand of Fate 2","Defiant Development",74,"A card-driven adventure in which a mysterious Dealer deals out a story and then you fight it out in action combat.",["RPG","Strategy"]],
["The Gunvolt Chronicles: Luminous Avenger iX","Inti Creates",70,"A fast action platformer featuring a heroine with lightning powers and a catchy electronic soundtrack.",["Platformer","Action"]],
["Yoku's Island Express","Villa Gorilla",81,"A pinball-meets-metroidvania game where a tiny dung beetle uses flippers to explore a tropical island.",["Platformer","Adventure"]],
["Owlboy","D-Pad Studio",82,"A beautiful pixel-art adventure about a mute owl boy who flies through a land of sky islands.",["Platformer","Adventure"]],
["Dicey Dungeons","Terry Cavanagh",82,"A colorful roguelike deckbuilder where you roll dice to attack, defend, and use items against a gameshow of monsters.",["Strategy","RPG"]],
["Wargroove","Chucklefish",80,"A turn-based tactics game in the style of classic handheld strategy, with commander abilities and a charming fantasy art style.",["Strategy"]],
["Graveyard Keeper","Lazy Bear Games",75,"A darkly funny medieval management sim in which you run a graveyard, a church, and a corpse-processing side business.",["Sim","RPG"]],
["Planet Zoo","Frontier Developments",85,"A detailed zoo-building simulation that focuses on animal welfare, habitat design, and park management.",["Sim"]],
["Jurassic World Evolution","Frontier Developments",70,"A park-management sim where you build and run dinosaur attractions and try to keep the animals contained.",["Sim","Strategy"]],
["Humankind","Amplitude Studios",78,"A historical strategy game in which you guide a culture from the Stone Age to the modern age, changing identity along the way.",["Strategy"]],
["Bad North","Plausible Concept",78,"A minimalist real-time strategy game of defending small islands against waves of seaborne raiders.",["Strategy"]],
["Minecraft: Story Mode","Telltale Games",72,"An episodic adventure set in the Minecraft universe, with choices, jokes, and heroes drawn from the blocky world.",["Adventure"]],
["Game of Thrones: A Telltale Games Series","Telltale Games",74,"An episodic story about a noble family in Westeros, where your choices shape who survives the war for power.",["Adventure"]],
["Marvel's Guardians of the Galaxy: The Telltale Series","Telltale Games",72,"An episodic space adventure where Star-Lord's misfit team chases a powerful relic and faces past mistakes.",["Adventure"]],
["Batman: The Enemy Within","Telltale Games",78,"The sequel to the Telltale Batman series, with a Riddler-led threat and a new look at the Joker's origins.",["Adventure"]],
["Twin Mirror","Dontnod Entertainment",65,"A psychological thriller in which a former reporter investigates a friend's death with help from his own imagination.",["Adventure"]],
["Road 96","DigixArt",80,"A road-trip adventure in which each playthrough is different and the stories of teenagers fleeing a regime intertwine.",["Adventure"]],
["Dreamfall Chapters","Red Thread Games",76,"A narrative adventure that follows heroes across two very different worlds, one sci-fi and one fantasy.",["Adventure"]],
["A Space for the Unbound","Mojiken",78,"A heartfelt pixel-art adventure about two high-school sweethearts in 1990s Indonesia and a looming apocalypse.",["Adventure","Puzzle"]],
["Before Your Eyes","GoodbyeWorld Games",74,"A short narrative game controlled by blinking, in which you relive the memories of a young man's life.",["Adventure"]],
["Lake","Gamious",73,"A relaxing small-town story game in which you deliver mail and meet locals in a quiet 1980s lakeside community.",["Adventure","Sim"]],
["Trine 5: A Clockwork Conspiracy","Frozenbyte",76,"A beautiful co-op fantasy puzzle-platformer starring three heroes with different skills.",["Platformer","Puzzle"]],
["Pac-Man World Re-PAC","Bandai Namco",72,"A remake of a classic 3D platformer in which the yellow hero rescues his friends from a mischievous rival.",["Platformer"]],
["Sonic Mania","PagodaWest Games",86,"A retro-style Sonic platformer that remixes classic levels with new ones and fast, colorful action.",["Platformer"]],
["Sonic Origins","Sonic Team",74,"A collection of four classic Sonic games from the 1990s, remastered in widescreen with extra modes.",["Platformer"]],
["Contra: Operation Galuga","WayForward",79,"A revival of the classic run-and-gun series, with intense co-op action against alien invaders.",["Shooter","Platformer"]],
["Strider","Double Helix Games",72,"A reboot of the classic side-scrolling action game starring a high-speed futuristic ninja.",["Action","Platformer"]],
["Teenage Mutant Ninja Turtles: The Cowabunga Collection","Digital Eclipse",80,"A bundle of 13 classic Turtles games, with a museum of artwork and behind-the-scenes material.",["Action"]],
["Capcom Arcade Stadium","Capcom",72,"A collection of 32 classic arcade games from the 1980s to 1990s, with online leaderboards.",["Action"]],
["Capcom Fighting Collection","Capcom",75,"A collection of ten classic Capcom fighters, including the Darkstalkers series, with online play.",["Fighting"]],
["Street Fighter 30th Anniversary Collection","Digital Eclipse",75,"A collection of twelve classic Street Fighter games, from the first to Street Fighter III.",["Fighting"]],
["Octopath Traveler 0","Square Enix",80,"A prequel to the HD-2D JRPG series, starring a new hero who builds a town while seeking revenge.",["RPG"]],
["Atelier Ryza 3: Alchemist of the End & the Secret Key","Gust",76,"A cozy alchemy RPG that sends a group of friends to explore a mysterious island and its secrets.",["RPG"]],
["Blue Reflection: Second Light","Gust",66,"A school-life RPG in which a group of girls on a mysterious island fight to uncover their forgotten memories.",["RPG"]],
["Harvest Moon: One World","Natsume",58,"A farming sim in which you travel between islands to restore the harvest goddess's land.",["Sim"]],
["Cris Tales","Dreams Uncorporated",72,"A hand-painted JRPG in which you can see the past, present, and future at once and use them in combat.",["RPG"]],
["Lunar Remastered Collection","Game Arts",72,"A remastered pair of classic JRPGs with anime cutscenes, set in a world of magic and adventure.",["RPG"]],
["Suikoden I & II HD Remaster","Konami",75,"A remastered pair of JRPGs known for recruiting a huge cast of 108 characters to your cause.",["RPG","Strategy"]],
["Soulstice","Reply Game Studios",70,"A dark fantasy action game in which two sisters, a warrior and a spirit, fight demons in a ruined city.",["Action"]],
["Tales of Kenzera: ZAU","Surgent Studios",75,"A metroidvania inspired by Bantu mythology, in which a young shaman bargains with the god of death.",["Platformer","Action"]],
["Sniper Elite 4","Rebellion",71,"A WWII stealth shooter with slow-motion x-ray kill cams, set in large, open Italian levels.",["Shooter","Action"]],
["Zombie Army 4: Dead War","Rebellion",72,"A cooperative shooter in which players fight hordes of undead Nazis in an alternate version of WWII Europe.",["Shooter","Horror"]],
["Strange Brigade","Rebellion",72,"A cooperative adventure shooter in which 1930s British adventurers battle mummies in an ancient Egyptian tomb.",["Shooter","Adventure"]],
["Shadow Warrior 2","Flying Wild Hog",72,"A humorous first-person shooter with swords, guns, and a randomized loot system.",["Shooter","Action"]],
["Ready or Not","Void Interactive",75,"A tactical first-person shooter in which a SWAT team deals with hostage and active-shooter situations.",["Shooter"]],
["Need for Speed: Hot Pursuit Remastered","Criterion Games",83,"A remaster of a classic arcade racer where you choose to be either a street racer or a police officer.",["Racing"]],
["DiRT Rally 2.0","Codemasters",84,"A rally racing simulation that focuses on difficult, realistic driving across gravel, snow, and tarmac.",["Racing","Sim"]],
["LEGO City Undercover","TT Fusion",75,"An open-world LEGO adventure in which an undercover cop chases criminals in a city full of jokes.",["Adventure","Action"]],
["LEGO DC Super-Villains","TT Games",72,"A LEGO adventure in which you create your own villain and team up with DC's bad guys.",["Adventure","Action"]],
["LEGO Jurassic World","TT Games",74,"A LEGO retelling of the four Jurassic Park films, with dinosaurs and silly humor.",["Adventure","Action"]],
["LEGO The Incredibles","TT Games",70,"A LEGO adventure that follows the stories of both Incredibles films and features superhero family abilities.",["Adventure","Action"]],
["LEGO Worlds","Traveller's Tales",72,"A creative sandbox in which you build and explore worlds made of LEGO bricks.",["Sim","Adventure"]],
["Marvel vs. Capcom Fighting Collection: Arcade Classics","Capcom",71,"A collection of seven classic crossover fighting games featuring Marvel and Capcom characters.",["Fighting"]],
["Bully","Rockstar Vancouver",85,"A school-themed open-world game from the makers of Grand Theft Auto, with pranks, classes, and a rebellious teen.",["Adventure","Action"]],
["The Warriors","Rockstar Toronto",84,"A brawler based on the 1979 cult film, in which a street gang fights its way across 1970s New York.",["Action"]],
["Red Dead Revolver","Rockstar San Diego",70,"A Wild West shooter starring a bounty hunter, the prequel-in-spirit of the Red Dead series.",["Shooter","Action"]],
["Crash Team Racing Nitro-Fueled","Beenox",83,"A remake of the classic kart racer with a story-driven Adventure mode and online racing.",["Racing"]],
["Jak II","Naughty Dog",87,"A genre-shifting platformer sequel that places its heroes in a dark futuristic city with guns and vehicles.",["Platformer","Action"]],
["Roblox","Roblox Corporation",80,"A huge platform of free, player-made games and worlds, from obstacle courses and role-play to shooters and tycoons.",["Adventure","Sim"]],
["Paladins","Evil Mojo Games",75,"A free-to-play team hero shooter with a fantasy look and card-based loadout customization.",["Shooter"]],
["Smite","Titan Forge Games",78,"A third-person online battle arena where players take control of gods and mythical figures from world mythologies.",["Action","Strategy"]],
["Rogue Company","First Watch Games",72,"A free-to-play third-person tactical shooter with short rounds, a buy phase, and a roster of mercenaries.",["Shooter"]],
["VALORANT","Riot Games",83,"A 5v5 tactical shooter in which agents with unique abilities attempt to plant or defuse a bomb.",["Shooter"]],
["Delta Force","TiMi Studio Group",74,"A free-to-play tactical shooter with large-scale combined-arms battles and an extraction mode.",["Shooter"]],
["ARC Raiders","Embark Studios",82,"A third-person extraction shooter where players scavenge a ruined Earth while avoiding machines and other players.",["Shooter","Action"]],
["Battlefield 6","Battlefield Studios",80,"A modern-war shooter with massive multiplayer battles, destructible environments, and a story campaign.",["Shooter"]],
["Borderlands 4","Gearbox Software",76,"A colorful, loot-driven shooter with a new planet, four new Vault Hunters, and co-op play.",["Shooter","RPG"]],
["The Elder Scrolls IV: Oblivion Remastered","Virtuos",85,"A ground-up visual remake of the classic fantasy RPG, with the original quests and humor.",["RPG","Adventure"]],
["Final Fantasy Tactics: The Ivalice Chronicles","Square Enix",85,"A remastered tactical RPG with grid-based battles and a mature political fantasy story.",["Strategy","RPG"]],
["Dragon Quest VII Reimagined","Square Enix",82,"A remake of the huge JRPG about a fisherman's son who travels through time to restore lost islands.",["RPG"]],
["Nioh 3","Team Ninja",84,"A tough samurai action RPG set in feudal Japan, with two combat styles and yokai bosses.",["Action","RPG"]],
["Crimson Desert","Pearl Abyss",78,"A sprawling single-player open-world action-adventure set in a medieval continent at war.",["Action","Adventure"]],
["Saros","Housemarque",85,"A sci-fi action roguelite from the makers of Returnal, featuring intense shooting and shifting alien worlds.",["Shooter","Action"]],
["007 First Light","IO Interactive",80,"An original origin story for a young James Bond, combining stealth, action, and driving.",["Action","Adventure"]],
["Pragmata","Capcom",83,"A sci-fi action game on a lunar station that mixes shooting with a real-time hacking minigame.",["Action","Shooter"]],
["Marathon","Bungie",70,"A competitive extraction shooter in which teams of cybernetic Runners scavenge a lost colony for valuable loot.",["Shooter"]],
["Fatal Frame II: Crimson Butterfly Remake","Koei Tecmo",78,"A remake of a classic Japanese horror game in which twin sisters explore a haunted village and photograph ghosts.",["Horror","Adventure"]],
["Phantom Blade Zero","S-GAME",82,"A fast, stylish martial-arts action game set in a dark, fictional version of ancient China.",["Action"]],
["Tokyo Xtreme Racer","Genki",72,"A street racing game in which you challenge drivers on Tokyo's expressways at night.",["Racing"]],
["The Dark Pictures Anthology: Directive 8020","Supermassive Games",66,"A choice-driven sci-fi horror in which a crew's decisions determine who survives a deadly voyage.",["Horror","Adventure"]],
["The Binding of Isaac: Rebirth","Nicalis",89,"A randomized, twin-stick roguelike dungeon crawler full of bizarre items and dark religious imagery.",["Action","Adventure"]],
["God Hand","Clover Studio",78,"A cult-classic brawler with a huge combo system, absurd humor, and a hero with a magical arm.",["Action"]],
["Samurai Shodown","SNK",78,"A weapon-based 2D fighter that rewards patience, with each hit potentially deciding a round.",["Fighting"]],
["SnowRunner","Saber Interactive",78,"An off-road driving sim about hauling cargo in huge trucks through mud, snow, and rivers.",["Racing","Sim"]],
["Microsoft Flight Simulator 2024","Asobo Studio",78,"A detailed flight sim that lets you fly aircraft all over the world, with career and mission modes.",["Sim"]],
["Project CARS 3","Slightly Mad Studios",68,"A career-focused racing game with a large selection of cars and tracks, aimed at both casual and serious players.",["Racing"]],
["Nuclear Throne","Vlambeer",87,"A fast, random-generated shooter in which mutants fight through a wasteland to reach a mysterious throne.",["Shooter","Action"]],
["Gang Beasts","Boneloaf",65,"A silly local party brawler in which wobbly jelly characters grab, punch, and throw each other off rooftops.",["Fighting","Action"]],
["I Am Bread","Bossa Studios",60,"A chaotic physics game in which you control a slice of bread that is trying to become toast.",["Sim","Puzzle"]],
["PlateUp!","It's Anecdotal",80,"A co-op roguelite in which you build and run a restaurant, cooking and serving customers under pressure.",["Sim","Strategy"]],
["Unrailed!","Indoor Astronaut",78,"A frantic co-op game in which players chop wood, mine ore, and lay rails ahead of an unstoppable train.",["Puzzle","Strategy"]],
["Neon Abyss","Veewo Games",76,"A colorful, fast-paced roguelike platformer in which you pile up wild item combos as you descend a dungeon.",["Platformer","Shooter"]],
["Death Road to Canada","Rocketcat Games",78,"A zombie road-trip roguelite in which a group of survivors scavenges supplies as they drive north.",["Action","Strategy"]],
["Darkwood","Acid Wizard Studio",78,"A top-down survival-horror game in which you scavenge by day and defend a shack from horrors by night.",["Horror","Adventure"]],
["Super Meat Boy Forever","Team Meat",74,"A one-button auto-running sequel to the brutal platformer, with chaotic, randomized levels.",["Platformer","Action"]],
["N++","Metanet Software",85,"A precise, minimalist platformer in which a stick-figure ninja avoids deadly traps in thousands of tiny levels.",["Platformer","Puzzle"]],
["Geometry Wars 3: Dimensions","Lucid Games",77,"A neon twin-stick arcade shooter that moves the action onto 3D shapes like spheres and tubes.",["Shooter","Action"]],
["Dead Nation","Housemarque",78,"An isometric twin-stick shooter in which survivors fight through hordes of zombies in a doomed city.",["Shooter","Horror"]],
["Velocity 2X","FuturLab",84,"A mix of shoot-'em-up and platformer in which a pilot teleports through levels and rescues survivors.",["Shooter","Platformer"]],
["Steep","Ubisoft Annecy",70,"An open-world winter sports game in which you ski, snowboard, paraglide, and wingsuit down the Alps.",["Sports"]],
["Need for Speed Payback","Ghost Games",65,"An action-driving game in which a team of racers takes on a crime syndicate in a Las Vegas-style city.",["Racing","Action"]],
["DiRT 4","Codemasters",80,"A rally racing game with a deep career mode and an adjustable difficulty, from arcade to simulation.",["Racing"]],
["GRID Legends","Codemasters",77,"A racing game with a live-action story mode and a variety of racing styles, from circuits to drifts.",["Racing"]],
["Black Desert","Pearl Abyss",78,"A visually striking fantasy MMO with fluid action combat, trading, and deep character customization.",["RPG","Action"]],
["Dauntless","Phoenix Labs",76,"A free-to-play cooperative game in which hunters take on giant beasts and craft gear from their parts.",["Action","RPG"]],
["Elite Dangerous","Frontier Developments",75,"A massive space simulation in which you trade, explore, mine, and fight across a real-scale Milky Way.",["Sim","Adventure"]],
["Terminator: Resistance","Teyon",66,"A first-person shooter set in the war between humans and machines in the Terminator universe.",["Shooter","Action"]],
["Back to the Future: The Game","Telltale Games",76,"An episodic adventure that continues the story of Marty McFly and Doc Brown with new time travel.",["Adventure","Puzzle"]],
["Friday the 13th: The Game","Gun Interactive",58,"An asymmetrical multiplayer horror game in which one player is Jason and others are camp counselors.",["Horror"]],
["Evil Dead: The Game","Saber Interactive",70,"A cooperative horror game in which players fight demons, based on the cult-classic horror comedy films.",["Horror","Action"]],
["Predator: Hunting Grounds","IllFonic",58,"An asymmetrical game in which a fireteam of soldiers hunts and is hunted by the alien Predator.",["Shooter","Action"]],
["Five Nights at Freddy's: Security Breach","Steel Wool Studios",68,"A 3D horror game in which you hide and sneak through a haunted pizza-and-arcade complex.",["Horror","Adventure"]],
["Bendy and the Ink Machine","Joey Drew Studios",70,"A vintage-cartoon horror game set in an abandoned animation studio full of ink creatures.",["Horror","Adventure"]],
["Yu-Gi-Oh! Master Duel","Konami",78,"A digital version of the popular trading card game with thousands of cards and online duels.",["Strategy"]],
["Hatsune Miku: Project DIVA Future Tone","Sega",78,"A rhythm game in which you hit notes in time with songs performed by virtual idols.",["Puzzle"]],
["Bluey: The Videogame","Artax Games",65,"A family-friendly game in which you play through imaginative scenes from the animated children's show.",["Adventure"]],
["SpongeBob SquarePants: Battle for Bikini Bottom - Rehydrated","Purple Lamp Studios",77,"A remake of a classic 3D platformer in which SpongeBob and Patrick stop a robot invasion.",["Platformer","Adventure"]],
["SpongeBob SquarePants: The Cosmic Shake","Purple Lamp Studios",75,"A 3D platformer in which SpongeBob and Patrick travel through wacky dimensions to fix a wish gone wrong.",["Platformer","Adventure"]],
["Minecraft Legends","Mojang Studios",67,"An action-strategy spin-off in which you rally allies to defend the Overworld from invading Piglins.",["Strategy","Action"]],
["Bomb Rush Cyberfunk","Team Reptile",83,"A stylish arcade skating game with graffiti, funk music, and a story about city crews.",["Sports","Action"]],
["Hello Neighbor","Dynamic Pixels",50,"A stealth horror game in which you sneak into your neighbor's house to uncover his secret.",["Horror","Puzzle"]],
["The Escapists 2","Team17",72,"A prison-escape sandbox in which you craft items, follow routines, and plan creative breakouts.",["Strategy","Sim"]],
["Prison Architect","Introversion Software",80,"A management sim in which you design and operate a prison, balancing security and prisoner welfare.",["Sim","Strategy"]],
["RimWorld","Ludeon Studios",86,"A colony sim driven by an AI storyteller that generates dramatic events as your colonists try to survive.",["Sim","Strategy"]],
["Nidhogg","Messhof",75,"A two-player fencing duel in which each fighter tries to run across the screen and reach the goal.",["Fighting"]],
["Duck Game","Landon Podbielski",78,"A local multiplayer shooter in which armed ducks fight in short, chaotic rounds.",["Shooter","Action"]],
["SpeedRunners","DoubleDutch Games",78,"A fast, competitive platformer in which superheroes race and try to leave their opponents behind.",["Platformer","Sports"]],
["Rocket Arena","Final Strike Games",70,"A 3v3 shooter in which rockets knock opponents off the map instead of damaging them.",["Shooter"]],
["Knockout City","Velan Studios",76,"A multiplayer dodgeball brawler in which you throw balls and teammates in a street-style city.",["Sports","Action"]],
["Cozy Grove","Spry Fox",75,"A relaxing life-sim in which you befriend ghost bears on a haunted island and help them move on.",["Sim","Adventure"]],
["Fae Farm","Phoenix Labs",72,"A cozy farming and magic life-sim in a fairy-tale world with crafting, dungeons, and friendships.",["Sim","RPG"]],
["Roots of Pacha","Soda Den",76,"A farming sim set in the Stone Age, where you help your clan survive and develop new technology.",["Sim"]],
["Spirittea","Cheesemaster Games",78,"A life-sim in which you run a bathhouse for spirits in a quiet village and solve their problems.",["Sim","Adventure"]],
["Wylde Flowers","Studio Drydock",72,"A cozy life-sim that blends farming with witchcraft, set in a small seaside town.",["Sim","Adventure"]],
["Potion Permit","MassHive Media",70,"A town-based sim in which a chemist works to earn the trust of locals by brewing medicine.",["Sim","RPG"]],
["Destruction AllStars","Lucid Games",63,"A vehicular-combat arena game where drivers crash cars and then leap out to fight on foot.",["Racing","Action"]],
["Atlas Fallen","Deck13",70,"A sand-swept action RPG in which a gauntlet-wielding hero surfs dunes and fights giant monsters.",["Action","RPG"]],
["Steelrising","Spiders",70,"A souls-like set in an alternate 1789 Paris, where clockwork soldiers crush the French Revolution.",["Action","RPG"]],
["High on Life","Squanch Games",70,"A comedic first-person shooter with talking guns and alien bounty hunting, from the Rick and Morty co-creator.",["Shooter","Adventure"]],
["Exoprimal","Capcom",72,"A team-based online shooter in which exosuit pilots fight dinosaurs that pour out of time rifts.",["Shooter","Action"]],
["Lost Records: Bloom & Rage","Don't Nod",78,"A coming-of-age mystery with choices, set in 1990s Michigan and 2022, as old friends revisit a secret.",["Adventure"]],
["Dustborn","Red Thread Games",72,"A story-focused road trip across alternate-future America, where words are weapons.",["Adventure","Action"]],
["Dragon Ball: The Breakers","Dimps",60,"An asymmetrical online game in which survivors escape from a Dragon Ball villain.",["Action"]],
["My Hero Ultra Rumble","Byking",62,"A free-to-play battle royale starring heroes and villains from the My Hero Academia anime.",["Action","Fighting"]],
["Digimon Story: Time Stranger","Media.Vision",82,"A turn-based RPG about training and evolving digital monsters, with a time-twisting mystery.",["RPG"]],
["Wuchang: Fallen Feathers","Leenzee Games",72,"A Chinese-flavored souls-like set in a plague-ridden late-Ming world, with fast, aggressive combat.",["Action","RPG"]],
["Super Mega Baseball 4","Metalhead Software",85,"A cartoonish yet deep baseball game with franchise mode and highly customizable players.",["Sports"]],
["AO Tennis 2","Big Ant Studios",68,"A tennis simulation with a career mode, where players build their stats and rise through the rankings.",["Sports"]],
["Top Spin 2K25","Hangar 13",80,"A tennis game that revives a classic series, with timing-based shots and a career mode.",["Sports"]],
["Undisputed","Steel City Interactive",74,"A realistic boxing game with a career mode, in which you rise from amateur to world champion.",["Sports","Fighting"]],
["art of rally","Funselektor Labs",85,"A stylish, minimalist rally racing game with retro cars and beautifully simple, low-poly landscapes.",["Racing"]],
["Dakar Desert Rally","Saber Interactive",70,"An open-world rally game that recreates the Dakar Rally's desert stages in Saudi Arabia.",["Racing","Sim"]],
["F1 Manager 2024","Frontier Developments",80,"A Formula 1 team-management sim where you choose strategies, develop cars, and run the race weekend.",["Sim","Strategy"]],
["Star Wars: Bounty Hunter","Aspyr",63,"A remaster of the classic action game starring the bounty hunter Jango Fett.",["Action","Shooter"]],
["The Lord of the Rings: Gollum","Daedalic Entertainment",35,"A stealth-focused adventure starring the creature Gollum, set between The Hobbit and The Lord of the Rings.",["Adventure","Action"]],
["The Lord of the Rings: Return to Moria","Free Range Games",72,"A survival-crafting game in which dwarves rebuild the underground city of Moria, battling Orcs and shadows.",["Sim","Adventure"]],
["The Expanse: A Telltale Series","Deck Nine",72,"An episodic sci-fi adventure set in a future solar system on the brink of war, based on the TV series.",["Adventure"]],
["John Wick Hex","Good Shepherd Entertainment",70,"A stylish strategy game that turns John Wick's gun-fu into a turn-based game of timing and positioning.",["Strategy","Action"]],
["The Thing: Remastered","Nightdive Studios",76,"A remaster of the cult third-person horror game that continues the story of John Carpenter's The Thing.",["Horror","Shooter"]],
["Tomb Raider IV-VI Remastered","Aspyr",70,"A remastered collection of three late-1990s Lara Croft adventures with modern visuals and controls.",["Adventure","Action"]],
["Legacy of Kain: Soul Reaver 1&2 Remastered","Crystal Dynamics",75,"A remastered pair of classic action-adventures starring a vampire wraith who hunts his betrayer.",["Action","Adventure"]],
["System Shock","Nightdive Studios",80,"A ground-up remake of the cult-classic first-person sci-fi horror game, in which you outwit a rogue AI.",["Shooter","Horror"]],
["Quake","id Software",85,"The classic 1996 first-person shooter, re-released with modern controls and online play.",["Shooter"]],
["Doom 64","Nightdive Studios",78,"A remaster of the darker, atmospheric Nintendo 64 entry in the classic shooter series.",["Shooter"]],
["Duke Nukem 3D: 20th Anniversary World Tour","Gearbox Software",70,"A re-release of the over-the-top 1996 shooter featuring the wisecracking Duke Nukem.",["Shooter"]],
["Heretic + Hexen","Nightdive Studios",80,"A remastered pair of dark-fantasy first-person shooters from the 1990s, with new levels.",["Shooter"]],
["Ion Fury","Voidpoint",78,"A retro-style cyberpunk shooter built on classic technology, with a sharp-tongued heroine.",["Shooter"]],
["Turok","Nightdive Studios",70,"A remaster of the classic first-person shooter where a Native American warrior hunts dinosaurs.",["Shooter","Adventure"]],
["Far Cry 3: Blood Dragon","Ubisoft Montreal",78,"A neon-drenched, 80s action-movie parody of Far Cry that stars a cyborg commando.",["Shooter","Action"]],
["Hellpoint","Cradle Games",63,"A sci-fi souls-like on a dying space station, with co-op and a world that shifts between dimensions.",["Action","RPG"]],
["Curse of the Dead Gods","Passtech Games",75,"An isometric roguelike in which you descend into a cursed temple and trade health for power.",["Action","Adventure"]],
["Crown Trick","NEXT Studios",72,"A turn-based roguelike where enemies move only when you do, mixing puzzles with dungeon-crawling.",["Strategy","Action"]],
["Astral Ascent","Hibernian Workshop",82,"A fast, stylish roguelite platformer-brawler in which prisoners fight their way through the Zodiac Garden.",["Action","Platformer"]],
["Star Wars: Republic Commando","LucasArts",80,"A squad-based first-person shooter in which you lead an elite team of clone commandos.",["Shooter"]],
["Star Wars: Dark Forces Remaster","Nightdive Studios",80,"A remaster of the classic first-person shooter that introduced Kyle Katarn.",["Shooter","Adventure"]],
["Star Wars Jedi Knight: Jedi Academy","Raven Software",75,"A lightsaber-dueling action game in which a new Jedi student faces a rising Sith cult.",["Action","Shooter"]],
["Star Wars Episode I: Racer","LucasArts",70,"A high-speed podracing game based on The Phantom Menace, with dozens of racers and tracks.",["Racing"]],
["Ghostbusters: The Video Game Remastered","Saber Interactive",70,"A remaster of the Ghostbusters adventure that serves as a sequel to the classic films.",["Action","Adventure"]],
["War Thunder","Gaijin Entertainment",75,"A free-to-play combat game with realistic tanks, planes, and ships from World War II and beyond.",["Sim","Action"]],
["World of Tanks","Wargaming",73,"A team-based online tank battle game with historical vehicles and objective-based matches.",["Strategy","Action"]],
["World of Warships: Legends","Wargaming",72,"A free-to-play naval combat game with historical warships, from destroyers to battleships.",["Strategy","Action"]],
["PlanetSide 2","Daybreak Game Company",70,"A free-to-play massively multiplayer shooter with battles of hundreds of players over a persistent map.",["Shooter"]],
["EA Sports NHL 25","EA Vancouver",72,"The annual hockey sim, with franchise mode, Be a Pro careers, and the online Hockey Ultimate Team.",["Sports"]],
["Tour de France 2024","Cyanide Studio",65,"A cycling game in which you manage a pro team, lead riders through mountain stages, and plan race tactics.",["Sports","Sim"]],
["Golf With Your Friends","Blacklight Interactive",65,"A casual multiplayer mini-golf game with wacky courses and up to 12 players.",["Sports"]],
["Rugby 22","Eko Software",52,"A rugby union game with international and club teams, a career mode, and online play.",["Sports"]],
["Cricket 24","Big Ant Studios",70,"A cricket simulation with international teams, a career mode, and detailed batting and bowling.",["Sports"]],
["eFootball","Konami",50,"A free-to-play football (soccer) game with online matches, player cards, and regular updates.",["Sports"]],
["Gran Turismo Sport","Polyphony Digital",75,"A car-racing game focused on online competition, with licensed cars and a driving-school campaign.",["Racing","Sim"]],
["Project CARS 2","Slightly Mad Studios",78,"A realistic racing sim with dynamic weather, dozens of motorsport classes, and a deep career mode.",["Racing","Sim"]],
["Rennsport","Competition Company",62,"A multiplayer-focused racing sim with licensed cars, built for competitive online races.",["Racing","Sim"]],
["Carmageddon: Max Damage","Stainless Games",57,"A violent, over-the-top driving game in which scoring points means wrecking cars and running over pedestrians.",["Racing","Action"]],
["Descenders","RageSquid",75,"An extreme downhill mountain-biking game with procedurally generated trails and tricks.",["Sports","Sim"]],
["Skater XL","Easy Day Studios",65,"A skateboarding sim with a unique stick-based trick control scheme and customizable skate parks.",["Sports","Sim"]],
["Golf It!","Perfuse Entertainment",67,"A multiplayer mini-golf game with imaginative courses, a level editor, and silly physics.",["Sports"]],
["Monopoly","Ubisoft",70,"A digital version of the classic board game of buying, trading, and bankrupting your friends.",["Strategy"]],
["UNO","Ubisoft",70,"A digital version of the colorful card game of matching colors and numbers and shouting UNO.",["Strategy"]],
["Super Bomberman R 2","Konami",58,"A party game in which players plant bombs and blow up opponents in grid-like arenas.",["Action","Strategy"]],
["Ultimate Chicken Horse","Clever Endeavour Games",80,"A party platformer in which players take turns building obstacle courses and then race to complete them.",["Platformer"]],
["Clustertruck","Landfall Games",75,"A first-person platformer in which you jump from truck to truck as the vehicles race down a road.",["Platformer","Action"]],
["Party Animals","Recreate Games",75,"A physics-based multiplayer brawler where cute animals push, throw, and knock each other around.",["Fighting","Action"]],
["Lil Gator Game","MegaWobble",78,"A relaxing, imaginative adventure about a child alligator who builds a playground to bring their sister back.",["Adventure"]],
["Lost in Play","Happy Juice Games",77,"A hand-drawn adventure about two siblings who travel through their imagination, solving puzzles.",["Adventure","Puzzle"]],
["Pikuniku","Sectordub",75,"A quirky, colorful puzzle-platformer starring a round red creature with long legs, set in a strange society.",["Platformer","Puzzle"]],
["Snake Pass","Sumo Digital",70,"A physics-based platformer in which you slither, coil, and climb as a snake across floating islands.",["Platformer","Puzzle"]],
["Knights and Bikes","Foam Sword",78,"A 1980s-set adventure about two friends exploring a British island, with bikes and kid-style combat.",["Adventure"]],
["LEGO Brawls","Red Games",63,"A family-friendly brawler where LEGO minifigure fighters battle in colorful arenas.",["Fighting","Action"]],
["The Gardens Between","The Voxel Agents",78,"A dreamlike puzzle game in which two friends manipulate time to carry a lantern through surreal gardens.",["Puzzle","Adventure"]],
["What the Golf?","Triband",78,"A comedic golf game that constantly changes the rules, turning the sport into bizarre challenges.",["Sports","Puzzle"]],
["TOEM","Something We Made",80,"A cozy, black-and-white photography adventure in which you take pictures to help other characters.",["Adventure","Puzzle"]],
["Islanders: Console Edition","Grizzly Games",72,"A relaxing city-building puzzle game where you place buildings on islands to earn points.",["Strategy","Puzzle"]],
["Steins;Gate 0","5pb.",85,"A visual-novel sci-fi thriller about time travel, set in an alternate timeline.",["Adventure"]],
["Robotics;Notes Elite","5pb.",72,"A sci-fi visual novel about a robotics club building a giant robot that uncovers a conspiracy.",["Adventure"]],
["Root Letter: Last Answer","Kadokawa Games",65,"A mystery visual novel in which a man travels across Japan to find his missing pen pal.",["Adventure"]],
["Her Story","Sam Barlow",82,"A mystery told only through police interview video clips, in which you search a database to uncover the truth.",["Adventure","Puzzle"]],
["Virginia","Variable State",67,"A short, wordless FBI mystery set in a small town in the 1990s, told with cinematic cuts.",["Adventure"]],
["Dear Esther: Landmark Edition","The Chinese Room",70,"A narrated walking game across a Scottish island, about grief and memory.",["Adventure"]],
["Q.U.B.E. 2","Toxic Games",74,"A first-person puzzle game in which you manipulate colored blocks to solve physics-based challenges.",["Puzzle"]],
["Portal Knights","Keen Games",72,"A cooperative sandbox action RPG in which players build, craft, and explore randomly generated worlds.",["RPG","Adventure"]],
["Pac-Man Championship Edition 2","Bandai Namco",78,"A fast, modern take on the classic arcade game in which Pac-Man races to gobble ghosts before time runs out.",["Action","Puzzle"]],
["Namco Museum Archives Vol. 1","Bandai Namco",70,"A collection of classic arcade games from the 1980s, including Galaga and Dig Dug.",["Action"]],
["Atari 50: The Anniversary Celebration","Digital Eclipse",78,"An interactive collection of more than 90 Atari games with timelines, videos, and interviews.",["Action"]],
["SEGA Mega Drive Classics","Sega",75,"A collection of over 50 classic Mega Drive/Genesis games, including Sonic and Streets of Rage.",["Action","Platformer"]],
["SNK 40th Anniversary Collection","Digital Eclipse",72,"A collection of 13 classic SNK arcade games, including Ikari Warriors and Athena.",["Action"]],
["Castlevania Anniversary Collection","Konami",78,"A collection of eight classic Castlevania games that introduced the series' vampire-hunting action.",["Action","Platformer"]],
["Contra Anniversary Collection","Konami",75,"A collection of classic Contra shooters, famous for their cooperative run-and-gun action.",["Shooter","Platformer"]],
["Capcom Beat 'Em Up Bundle","Capcom",75,"A bundle of seven classic brawlers such as Final Fight and Captain Commando, with online co-op.",["Action","Fighting"]],
["Ultimate Marvel vs. Capcom 3","Capcom",80,"A frantic 3v3 crossover fighting game that features dozens of Marvel and Capcom characters.",["Fighting"]],
["Nex Machina","Housemarque",80,"A fast, twin-stick arcade shooter with voxel visuals and intense multi-directional action.",["Shooter","Action"]],
["Alienation","Housemarque",72,"A twin-stick shooter RPG in which players fight an alien invasion, collect loot, and level up.",["Shooter","RPG"]],
["Matterfall","Housemarque",70,"A fast, run-and-gun platformer with a unique gun that can transform the environment.",["Platformer","Shooter"]],
["Resogun","Housemarque",85,"A fast, explosive side-scrolling shooter, famous for its voxel visuals and rescue-the-humans objective.",["Shooter"]],
["Super Stardust Ultra","Housemarque",78,"An arcade space shooter set around the surface of a planet, with intense, bullet-hell action.",["Shooter"]],
["Mighty No. 9","Comcept",52,"A side-scrolling action game from Mega Man's creator in which a robot absorbs enemy powers.",["Platformer","Action"]],
];

// ---------- helpers shared by the real-game catalog ----------
const GENRES=["RPG","Action","Shooter","Adventure","Horror","Racing","Fighting","Platformer","Sim","Puzzle","Strategy"];
function seededRand(seed){let s=seed%2147483647;if(s<=0)s+=2147483646;return function(){s=s*16807%2147483647;return (s-1)/2147483646;};}
function pick(rng,arr){return arr[Math.floor(rng()*arr.length)];}
function pickN(rng,pool,n){const p=[...pool],out=[];for(let k=0;k<n && p.length;k++){out.push(p.splice(Math.floor(rng()*p.length),1)[0]);}return out;}
const COMBAT_FLAVOR=["punishing, read-and-react duels that reward patience over button-mashing","frantic, mobility-driven skirmishes where positioning matters more than raw damage","tactical, squad-based exchanges built around cover and cooldown timing","weighty, momentum-heavy strikes that make every swing feel consequential","precision parries and counters that punish greedy play","fast target-switching against groups rather than one-on-one duels"];
const VERB_POOL=["Explore","Fight","Sneak","Drive","Solve puzzles","Customize equipment","Complete missions","Discover locations","Craft items","Negotiate","Build and manage bases","Hack systems","Command a squad","Race vehicles","Manage resources","Scavenge for supplies"];
const WORLD_FLAVOR=["A layered world with surface settlements and hidden depths to uncover.","Dense, vertical environments built for climbing and improvised routes.","A sprawling region shifting from open plains to cramped, dangerous interiors.","A tightly-wound set of connected districts, each with its own tone.","An atmosphere-heavy setting where light and weather change how it plays.","A patchwork of biomes stitched together by long, rewarding travel."];
const CUSTOM_POOL=["Weapons","Clothing","Vehicles","Skills","Character upgrades","Base/home customization","Abilities","Loadouts"];
const EXPLORE_BULLETS=["Large map","Hidden locations","Side activities","Collectibles","Optional areas","Fast travel points"];
const PROGRESS_FLAVOR=["Earn experience and unlock new abilities as the world opens up.","Gear and skill upgrades gradually expand what's possible in a fight.","A perk tree lets playstyles diverge the further you get.","Currency and crafting materials fuel steady equipment upgrades.","Optional trials unlock deeper ability tiers outside the main path."];
const REPLAY_BULLETS=["Multiple playstyles","Optional activities","Different approaches","Free exploration","New Game+"];
const TROPHY_NAMES=["First Steps","Getting Your Bearings","Halfway There","Above and Beyond","Master of the Craft","Speed Runner","Explorer's Instinct","No Stone Unturned","Against All Odds","Completionist","Well Equipped","Close Call"];
function trophiesFor(index){
  const rng=seededRand(index*71+503);
  const bronze=10+Math.floor(rng()*18),silver=5+Math.floor(rng()*9),gold=2+Math.floor(rng()*4);
  return {bronze,silver,gold,plat:1,total:bronze+silver+gold+1,names:pickN(rng,TROPHY_NAMES,5)};
}
const TIPS_POOL=["Explore off the critical path before major story beats — resources tend to dry up later.","Upgrade your core weapon before spreading points across several — a strong main tool beats a wide spread of weak ones.","Save manually before optional encounters if the game allows it — some fights are easy to walk into unprepared.","Talk to every NPC at least once per area — side content often gates the best gear.","Don't ignore defensive skills early — survivability compounds more than raw damage over a full run.","Check the settings menu for accessibility and difficulty options before starting — most let you adjust mid-run too.","Bank crafting materials early; recipes tend to get more expensive as you progress.","Rest or fast-travel points are usually safe to explore around thoroughly before moving on."];
function tipsFor(index){const rng=seededRand(index*83+617);return pickN(rng,TIPS_POOL,3);}
const VIBE_DIMS=["Stealth","Action","Exploration","Story","Horror","Puzzles"];
const VIBE_BUMP={RPG:{Story:2,Exploration:1},Action:{Action:2},Shooter:{Action:2},Adventure:{Exploration:2},Horror:{Horror:2,Stealth:1},Racing:{Action:1},Fighting:{Action:2},Platformer:{Exploration:1},Puzzle:{Puzzles:2},Strategy:{Puzzles:1,Story:1},Sports:{Action:1}};
function vibeFor(tags,rng){
  const base={Stealth:0,Action:0,Exploration:0,Story:0,Horror:0,Puzzles:0};
  tags.forEach(t=>{const b=VIBE_BUMP[t];if(b)for(const k in b)base[k]+=b[k];});
  const levels=["LOW","MEDIUM","HIGH","VERY HIGH"];
  const out={};
  VIBE_DIMS.forEach(d=>{out[d]=levels[Math.min(3,base[d]+Math.floor(rng()*2))];});
  return out;
}
// Genre-derived "feel" tags — built from each game's own real genre tags, not new invented facts
const GENRE_FEEL={RPG:"📈 Progression-heavy",Action:"⚡ Fast-paced",Shooter:"🔫 Combat-heavy",Adventure:"🗺️ Exploration-heavy",Horror:"😱 Tense",Racing:"🏎️ High-speed",Fighting:"🥊 Combat-heavy",Platformer:"🤸 Fast-paced",Sim:"🧩 Methodical",Puzzle:"🧠 Puzzle-focused",Strategy:"🎯 Tactical",Sports:"🏆 Competitive"};
function reviewFor(data,index){
  const rng=seededRand(index*31+7);
  return {
    vibeLine:data.desc,
    verbs:pickN(rng,VERB_POOL,4+Math.floor(rng()*3)),
    world:pick(rng,WORLD_FLAVOR),
    combat:`Leans on ${pick(rng,COMBAT_FLAVOR)}.`,
    custom:pickN(rng,CUSTOM_POOL,3+Math.floor(rng()*3)),
    exploreStars:3+Math.floor(rng()*3),
    exploreBullets:pickN(rng,EXPLORE_BULLETS,3+Math.floor(rng()*3)),
    progression:pick(rng,PROGRESS_FLAVOR),
    replayStars:3+Math.floor(rng()*3),
    replayBullets:pickN(rng,REPLAY_BULLETS,2+Math.floor(rng()*3)),
    vibe:vibeFor(data.tags,rng),
    trophies:trophiesFor(index),
    tips:tipsFor(index),
    feel:[...new Set(data.tags.map(t=>GENRE_FEEL[t]).filter(Boolean))],
    storageGB:8+Math.floor(rng()*68)
  };
}

// generated poster-art per card: an original abstract SVG "cover", not a real screenshot
const GENRE_HUE={RPG:265,Action:355,Shooter:200,Adventure:150,Horror:0,Racing:35,Fighting:20,Platformer:190,Sim:170,Puzzle:280,Strategy:95};
function poly(cx,cy,r,sides,rot=0){
  const pts=[];
  for(let k=0;k<sides;k++){const a=rot+k*2*Math.PI/sides;pts.push(`${(cx+r*Math.cos(a)).toFixed(1)},${(cy+r*Math.sin(a)).toFixed(1)}`);}
  return pts.join(' ');
}
const GENRE_ICON={
  RPG:(c,r,col)=>`<polygon points="${poly(c.x,c.y,r,6,-1.57)}" fill="none" stroke="${col}" stroke-width="3" opacity=".5"/><polygon points="${poly(c.x,c.y,r*.55,6,-1.57)}" fill="${col}" opacity=".18"/>`,
  Action:(c,r,col)=>`<line x1="${c.x-r}" y1="${c.y-r}" x2="${c.x+r}" y2="${c.y+r}" stroke="${col}" stroke-width="7" stroke-linecap="round" opacity=".45"/><line x1="${c.x+r}" y1="${c.y-r}" x2="${c.x-r}" y2="${c.y+r}" stroke="${col}" stroke-width="7" stroke-linecap="round" opacity=".25"/>`,
  Shooter:(c,r,col)=>`<circle cx="${c.x}" cy="${c.y}" r="${r}" fill="none" stroke="${col}" stroke-width="2" opacity=".4"/><circle cx="${c.x}" cy="${c.y}" r="${r*.55}" fill="none" stroke="${col}" stroke-width="2" opacity=".4"/><line x1="${c.x-r*1.3}" y1="${c.y}" x2="${c.x+r*1.3}" y2="${c.y}" stroke="${col}" stroke-width="2" opacity=".35"/><line x1="${c.x}" y1="${c.y-r*1.3}" x2="${c.x}" y2="${c.y+r*1.3}" stroke="${col}" stroke-width="2" opacity=".35"/>`,
  Adventure:(c,r,col)=>`<circle cx="${c.x}" cy="${c.y}" r="${r}" fill="none" stroke="${col}" stroke-width="2" opacity=".4"/><polygon points="${poly(c.x,c.y,r*.6,3,-1.57)}" fill="${col}" opacity=".35"/>`,
  Horror:(c,r,col)=>`<polyline points="${c.x-r},${c.y-r} ${c.x-r*.3},${c.y-r*.15} ${c.x+r*.25},${c.y-r*.5} ${c.x},${c.y} ${c.x+r*.4},${c.y+r*.3} ${c.x-r*.1},${c.y+r*.6} ${c.x+r*.5},${c.y+r}" fill="none" stroke="${col}" stroke-width="3" stroke-linecap="round" opacity=".4"/>`,
  Racing:(c,r,col)=>{let o='';for(let k=0;k<3;k++){const x=c.x-r+k*r*.5;o+=`<polyline points="${x},${c.y-r*.55} ${x+r*.6},${c.y} ${x},${c.y+r*.55}" fill="none" stroke="${col}" stroke-width="4" opacity="${(.42-k*.1).toFixed(2)}"/>`;}return o;},
  Fighting:(c,r,col)=>{let o='';for(let k=0;k<4;k++){o+=`<rect x="${c.x-r*.13}" y="${c.y-r}" width="${r*.26}" height="${r*2}" fill="${col}" opacity=".3" transform="rotate(${k*45} ${c.x} ${c.y})"/>`;}return o;},
  Platformer:(c,r,col)=>`<rect x="${c.x-r*.6}" y="${c.y+r*.25}" width="${r*1.2}" height="${r*.3}" fill="${col}" opacity=".4"/><rect x="${c.x-r*.32}" y="${c.y-r*.1}" width="${r*.85}" height="${r*.3}" fill="${col}" opacity=".3"/><rect x="${c.x-r*.05}" y="${c.y-r*.45}" width="${r*.55}" height="${r*.3}" fill="${col}" opacity=".22"/>`,
  Sim:(c,r,col)=>{let o='';for(const[dx,dy] of [[0,0],[r*.9,-r*.15],[-r*.9,-r*.15]]){o+=`<polygon points="${poly(c.x+dx,c.y+dy,r*.42,6)}" fill="none" stroke="${col}" stroke-width="2" opacity=".4"/>`;}return o;},
  Puzzle:(c,r,col)=>`<rect x="${c.x-r*.5}" y="${c.y-r*.5}" width="${r}" height="${r}" fill="none" stroke="${col}" stroke-width="3" opacity=".4"/><rect x="${c.x-r*.5}" y="${c.y-r*.5}" width="${r}" height="${r}" fill="none" stroke="${col}" stroke-width="3" opacity=".3" transform="rotate(45 ${c.x} ${c.y})"/>`,
  Strategy:(c,r,col)=>{let o='';for(let gx=-1;gx<=1;gx++)for(let gy=-1;gy<=1;gy++){o+=`<rect x="${(c.x+gx*r*.42-r*.16).toFixed(1)}" y="${(c.y+gy*r*.42-r*.16).toFixed(1)}" width="${r*.32}" height="${r*.32}" fill="${col}" opacity="${(gx+gy)%2===0?.4:.2}"/>`;}return o;}
};
function skyline(rng,baseY,color){
  let x=0,pts=`0,${baseY}`;
  while(x<400){const step=40+rng()*50,h=baseY-(30+rng()*160);x+=step;pts+=` ${Math.min(x,400).toFixed(0)},${h.toFixed(0)}`;}
  return `<polygon points="${pts} 400,${baseY}" fill="${color}" opacity=".55"/>`;
}
function posterSVG(title,tags,rng){
  const h1=GENRE_HUE[tags[0]] ?? Math.floor(rng()*360);
  const h2=(GENRE_HUE[tags[1]] ?? (h1+120))%360;
  const glowX=80+rng()*240,glowY=140+rng()*90,glowR=140+rng()*90;
  const icon=GENRE_ICON[tags[0]]||GENRE_ICON.Action;
  const iconSvg=icon({x:200,y:230+rng()*40},70+rng()*20,`hsl(${h1} 85% 65%)`);
  let streaks='';
  for(let s=0;s<3;s++){
    const x1=rng()*400,y1=rng()*260;
    streaks+=`<line x1="${x1.toFixed(0)}" y1="${y1.toFixed(0)}" x2="${(x1-60).toFixed(0)}" y2="${(y1+140).toFixed(0)}" stroke="hsl(${h2} 70% 60%)" stroke-width="1.5" opacity=".22"/>`;
  }
  const svg=`<svg xmlns="http://www.w3.org/2000/svg" width="400" height="700">
    <defs>
      <linearGradient id="g" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0" stop-color="hsl(${h1} 42% 16%)"/><stop offset="1" stop-color="hsl(${h2} 30% 5%)"/>
      </linearGradient>
      <radialGradient id="glow" cx="50%" cy="50%" r="50%">
        <stop offset="0" stop-color="hsl(${h1} 90% 60%)" stop-opacity=".35"/><stop offset="1" stop-color="hsl(${h1} 90% 60%)" stop-opacity="0"/>
      </radialGradient>
    </defs>
    <rect width="400" height="700" fill="url(#g)"/>
    <circle cx="${glowX.toFixed(0)}" cy="${glowY.toFixed(0)}" r="${glowR.toFixed(0)}" fill="url(#glow)"/>
    ${streaks}
    ${iconSvg}
    ${skyline(rng,430,`hsl(${h2} 35% 8%)`)}
    ${skyline(rng,480,`hsl(${h2} 25% 4%)`)}
  </svg>`;
  return `url('data:image/svg+xml,${encodeURIComponent(svg)}') center/cover no-repeat`;
}

let liked=new Set(),saved=new Set(),shown=0;
const feed=document.getElementById('feed');
const counter=document.getElementById('counter');
const TOTAL=SEED.length;
// true per-session shuffle (not seeded) so the feed opens on a different game each visit,
// while each game's own art/review/price still comes from its stable underlying index
function shuffle(arr){for(let i=arr.length-1;i>0;i--){const j=Math.floor(Math.random()*(i+1));[arr[i],arr[j]]=[arr[j],arr[i]];}return arr;}
const ORDER=shuffle(Array.from({length:TOTAL},(_,i)=>i));

// "For You" affinity engine — a genre score built from likes, saves, and time spent per card.
// It re-ranks a rolling look-ahead window of upcoming games rather than the whole catalog,
// so it can adapt in real time without ever losing games from the real-catalog pool.
const genreScore=Object.fromEntries(GENRES.map(g=>[g,0]));
const cardTagsByIdx=new Map();
function peekGame(idx){
  const [title,studio,rating,desc,tags]=SEED[idx];
  return {title,studio,rating,tags,...priceInfo(idx)};
}
function tagsOf(idx){return peekGame(idx).tags;}
const LOOKAHEAD=60,JITTER=6;
let poolPtr=0,candidates=[];
function refillCandidates(){while(candidates.length<LOOKAHEAD && poolPtr<TOTAL){candidates.push(ORDER[poolPtr++]);}}
function pickNext(n){
  refillCandidates();
  const scored=candidates.map(idx=>({idx,score:tagsOf(idx).reduce((s,t)=>s+(genreScore[t]||0),0)+Math.random()*JITTER}));
  scored.sort((a,b)=>b.score-a.score);
  const picked=scored.slice(0,n).map(s=>s.idx);
  const pickedSet=new Set(picked);
  candidates=candidates.filter(idx=>!pickedSet.has(idx));
  refillCandidates();
  return picked;
}
// search/filter — scans the (cheap, deterministic) catalog rather than a stored array
let mode='foryou',filteredList=[],filteredPtr=0;
const PRICE_FLOOR=0,PRICE_CEIL=70;
let filters={q:'',genres:new Set(),company:null,length:'',minPrice:PRICE_FLOOR,maxPrice:PRICE_CEIL};
function matchesFilter(idx){
  const g=peekGame(idx);
  if(filters.genres.size && ![...filters.genres].every(gen=>g.tags.includes(gen)))return false;
  if(filters.company && g.studio!==filters.company)return false;
  if(filters.length){const bt=BEAT_TIMES[g.title];if(bt===undefined)return false;
    if(filters.length==='none'&&bt!==0)return false;
    if(filters.length==='short'&&!(bt>0&&bt<10))return false;
    if(filters.length==='medium'&&!(bt>=10&&bt<=25))return false;
    if(filters.length==='long'&&!(bt>25))return false;}
  const fp=g.psPlus?0:g.price;
  if(fp<filters.minPrice || fp>filters.maxPrice)return false;
  if(filters.q){
    const q=filters.q.toLowerCase();
    if(!g.title.toLowerCase().includes(q) && !g.studio.toLowerCase().includes(q))return false;
  }
  return true;
}
function applyFilters(){
  feed.innerHTML='';activeIdx=null;
  const active=filters.q||filters.genres.size||filters.company||filters.length||filters.minPrice>PRICE_FLOOR||filters.maxPrice<PRICE_CEIL;
  if(active){
    filteredList=[];
    for(let i=0;i<TOTAL;i++){if(matchesFilter(i))filteredList.push(i);}
    filteredList.sort((a,b)=>peekGame(b).rating-peekGame(a).rating);
    filteredPtr=0;mode='filtered';
  } else {
    mode='foryou';
  }
  appendBatch(8);
  feed.scrollTop=0;
  markFirstActive();
}
function markFirstActive(){
  const first=feed.children[0];
  if(first){first.classList.add('active');activeIdx=Number(first.dataset.idx);activeSince=Date.now();}
}
let activeIdx=null,activeSince=Date.now();
function creditDwell(){
  if(activeIdx===null)return;
  const secs=Math.min(20,(Date.now()-activeSince)/1000);
  (cardTagsByIdx.get(activeIdx)||[]).forEach(t=>{genreScore[t]=(genreScore[t]||0)+secs*0.4;});
}

// Pricing — a curated list of real, known standard prices for free-to-play titles and
// unmistakable flagship/remaster releases, and a more realistic tiered estimate (weighted toward
// $29.99-$59.99, not flat-cheap) for everything else. Not live-scraped PS Store data — sales,
// regional pricing, and bundle editions shift constantly and can't be verified for 600+ titles
// reliably, so this is disclosed as typical/standard pricing, not a real-time price.
const PRICE_OVERRIDES={"Ghost of Yotei":69.99,"Tactics Ogre: Reborn":39.99,"Tales of Vesperia: Definitive Edition":39.99,"Ni no Kuni: Wrath of the White Witch Remastered":39.99,"Burnout Paradise Remastered":39.99,"Spider-Man 2":69.99,"Elden Ring":69.99,"Demon's Souls":69.99,"God of War Ragnarök":69.99,"Horizon Forbidden West":69.99,"Baldur's Gate 3":69.99,"Returnal":69.99,"Gran Turismo 7":69.99,"Final Fantasy XVI":69.99,"Ghost of Tsushima Director's Cut":39.99,"Ratchet & Clank: Rift Apart":69.99,"Death Stranding Director's Cut":39.99,"Hogwarts Legacy":69.99,"Cyberpunk 2077":69.99,"Diablo IV":69.99,"Alan Wake 2":69.99,"Marvel's Spider-Man 2":69.99,"Horizon Zero Dawn Remastered":39.99,"Rise of the Ronin":69.99,"Dragon's Dogma 2":69.99,"Silent Hill 2":69.99,"Black Myth: Wukong":69.99,"Persona 3 Reload":39.99,"Star Wars Jedi: Survivor":69.99,"Final Fantasy VII Rebirth":69.99,"Marvel's Wolverine":69.99,"Assassin's Creed Shadows":69.99,"Call of Duty: Black Ops 6":69.99,"Apex Legends":0.0,"Fortnite":0.0,"Overwatch 2":0.0,"Destiny 2":0.0,"Rocket League":0.0,"For Honor":0.0,"The Finals":0.0,"Monster Hunter Wilds":69.99,"S.T.A.L.K.E.R. 2: Heart of Chornobyl":69.99,"Marvel Rivals":0.0,"Alan Wake Remastered":39.99,"Dark Souls Remastered":39.99,"Fall Guys":0.0,"Final Fantasy VII Remake":69.99,"Crysis Remastered":39.99,"Mafia: Definitive Edition":39.99,"Warframe":0.0,"Hellblade II: Senua's Saga":69.99,"Ace Attorney Trilogy":39.99,"Tomb Raider I-III Remastered":39.99,"The Wonderful 101: Remastered":39.99,"BioShock Remastered":39.99,"Suicide Squad: Kill the Justice League":69.99,"Star Wars Outlaws":69.99,"Metro 2033 Redux":39.99,"Metro Last Light Redux":39.99,"Sleeping Dogs: Definitive Edition":39.99,"Mafia II: Definitive Edition":39.99,"Mafia III: Definitive Edition":39.99,"Ori and the Blind Forest: Definitive Edition":39.99,"Yakuza 3 Remastered":39.99,"Yakuza 4 Remastered":39.99,"Yakuza 5 Remastered":39.99,"Dragon Age: The Veilguard":69.99,"Death Stranding 2: On the Beach":69.99,"Indiana Jones and the Great Circle":69.99,"Grand Theft Auto: The Trilogy – The Definitive Edition":39.99,"Final Fantasy X/X-2 HD Remaster":39.99,"Kingdom Hearts HD 1.5 + 2.5 ReMIX":39.99,"Path of Exile":0.0,"Path of Exile 2":0.0,"Devil May Cry HD Collection":39.99,"Mega Man Legacy Collection":39.99,"Mega Man X Legacy Collection":39.99,"Zenless Zone Zero":0.0,"Honkai: Star Rail":0.0,"Genshin Impact":0.0,"Tower of Fantasy":0.0,"Wuthering Waves":0.0,"Katamari Damacy Reroll":39.99,"LocoRoco 2 Remastered":39.99,"Patapon 2 Remastered":39.99,"Call of Duty: Warzone":0.0,"PUBG: Battlegrounds":0.0,"Marvel's Avengers":69.99,"Star Wars Battlefront II":69.99,"LEGO Harry Potter Collection":39.99,"Splitgate":0.0,"Borderlands: The Handsome Collection":39.99,"Saints Row: The Third Remastered":39.99,"Crash Bandicoot N. Sane Trilogy":39.99,"Doom: The Dark Ages":69.99,"Metal Gear Solid Delta: Snake Eater":69.99,"Ninja Gaiden 4":69.99,"Sonic Colors Ultimate":39.99,"Spyro Reignited Trilogy":39.99,"Tales of Symphonia Remastered":39.99,"Dragon Quest III HD-2D Remake":69.99,"Tales of Graces f Remastered":39.99,"Freedom Wars Remastered":39.99,"Gravity Rush Remastered":39.99,"WipEout Omega Collection":39.99,"Dying Light: The Beast":29.99,"PaRappa the Rapper Remastered":29.99,"Shin Megami Tensei III Nocturne HD Remaster":29.99,"Digimon Story: Cyber Sleuth Complete Edition":29.99,"Hollow Knight: Silksong":29.99,"Tony Hawk's Pro Skater 3+4":39.99,"Avatar: Frontiers of Pandora":69.99,"The Outer Worlds 2":69.99};
function mixSeed(n){n=(n^61)^(n>>>16);n=n+(n<<3);n=n^(n>>>4);n=Math.imul(n,0x27d4eb2d);n=n^(n>>>15);return n>>>0;}
function priceInfo(index){
  const rng=seededRand(mixSeed(index*53+271));
  const title=SEED[index][0];
  if(Object.prototype.hasOwnProperty.call(PRICE_OVERRIDES,title)){
    const p=PRICE_OVERRIDES[title];
    return {price:p,psPlus:p>0&&rng()<0.07};
  }
  const tiers=[24.99,29.99,34.99,39.99,49.99,59.99];
  const weights=[0.12,0.18,0.16,0.22,0.18,0.14];
  let r=rng(),acc=0,price=tiers[tiers.length-1];
  for(let i=0;i<tiers.length;i++){ acc+=weights[i]; if(r<=acc){ price=tiers[i]; break; } }
  return {price,psPlus:rng()<0.07};
}
function salesFor(index,rating){
  const rng=seededRand(index*43+601);
  const exp=4.5+((rating||75)/100)*2.2+rng()*0.6;
  return {sold:Math.round(Math.pow(10,exp))};
}
function fmtSold(n){
  if(n>=1e6)return (n/1e6).toFixed(1).replace(/\.0$/,'')+'M';
  if(n>=1e3)return Math.round(n/1e3)+'K';
  return String(n);
}
const MODE_TYPES=[
 {short:'Single-Player',detail:'A fully offline campaign, with no online requirement.'},
 {short:'Online Co-op',detail:'Drop-in online co-op carries part or all of the campaign.'},
 {short:'Online PvP',detail:'Competitive online modes sit alongside the campaign.'},
 {short:'Local Co-op',detail:'Couch co-op for two players on one screen.'},
 {short:'Cross-Play',detail:'Online play spans PS5, PC, and other platforms.'}
];
function modesFor(index){
  const rng=seededRand(index*89+41);
  const weights=[.45,.2,.15,.1,.1];
  let r=rng(),acc=0,pickIdx=weights.length-1;
  for(let i=0;i<weights.length;i++){acc+=weights[i];if(r<=acc){pickIdx=i;break;}}
  return {mode:MODE_TYPES[pickIdx],playtime:Math.round(8+rng()*rng()*70)};
}

function buildCard(data,index){
  const el=document.createElement('div');
  el.className='card';el.dataset.idx=index;
  const rng=seededRand(index*7+3);
  el.innerHTML=`
    <div class="bg" style="background:${(posterSVG(data.title,data.tags,rng),coverBg(data.title,data.tags,data.studio))}"></div>
    <div class="scan"></div><div class="grad"></div>
    <div class="rail">
      <div class="pub">${data.studio.split(' ').map(w=>w[0]).slice(0,2).join('')}</div>
      <a class="rbtn store" href="https://store.playstation.com/en-us/search/${encodeURIComponent(data.title)}" target="_blank" rel="noopener noreferrer" title="Open in PlayStation Store">🛍️</a>
      <div class="rbtn heart">♡</div>
      <div class="rbtn star">☆</div>
    </div>
    <div class="info">
      <div class="badge-row"><span class="rating">★ ${data.rating.toFixed(1)}</span><span class="studio">${data.studio}</span></div>
      <div class="badge-row"><span class="chip${data.psPlus?' psplus':''}">${data.psPlus?'Included w/ PS Plus':'$'+data.price.toFixed(2)}</span><span class="chip">${data.mode.short}</span><span class="chip">📦 ${fmtSold(data.sold)} sold</span></div>
      <div class="title">${data.title}</div>
      <div class="hype">${data.desc}</div>
      <div class="tags">${data.tags.map(t=>`<span class="tag">#${t}</span>`).join('')}</div>
      <div class="tap-hint">Tap for full review</div>
    </div>`;
  el.querySelector('.info').onclick=()=>openReview(data,index);
  el.querySelector('.heart').onclick=e=>{
    e.target.classList.toggle('liked');
    const on=e.target.classList.contains('liked');
    e.target.textContent=on?'♥':'♡';
    if(on)data.tags.forEach(t=>{genreScore[t]=(genreScore[t]||0)+4;});
    if(on)liked.add(index);else liked.delete(index);
    toast(on?'♥ Added to your Library':'Removed from liked');
  };
  el.querySelector('.star').onclick=e=>{
    e.target.classList.toggle('saved');
    const on=e.target.classList.contains('saved');
    e.target.textContent=on?'★':'☆';
    if(on)data.tags.forEach(t=>{genreScore[t]=(genreScore[t]||0)+2;});
    if(on)saved.add(index);else saved.delete(index);
    toast(on?'★ Saved to your Library':'Removed from saved');
  };
  return el;
}

function appendBatch(n){
  const frag=document.createDocumentFragment();
  let idxs;
  if(mode==='filtered'){
    idxs=filteredList.slice(filteredPtr,filteredPtr+n);
    filteredPtr+=idxs.length;
  } else {
    idxs=pickNext(Math.min(n,TOTAL-shown));
  }
  for(const idx of idxs){
    const [title,studio,rating,desc,tags]=SEED[idx];
    const data={title,studio,rating,desc,tags};
    Object.assign(data,priceInfo(idx),modesFor(idx),salesFor(idx,data.rating));
    cardTagsByIdx.set(idx,data.tags);
    frag.appendChild(buildCard(data,idx));
    if(mode!=='filtered')shown++;
  }
  feed.appendChild(frag);
  counter.textContent=mode==='filtered'
    ? (filteredList.length?`${Math.min(filteredPtr,filteredList.length).toLocaleString()} / ${filteredList.length.toLocaleString()} matches`:'No matches')
    : `${shown.toLocaleString()} / ${TOTAL.toLocaleString()} games`;
}

appendBatch(6);

let ticking=false;
feed.addEventListener('scroll',()=>{
  if(ticking)return;ticking=true;
  requestAnimationFrame(()=>{
    const cards=feed.children;
    const scrollBottom=feed.scrollTop+feed.clientHeight;
    if(scrollBottom > feed.scrollHeight-window.innerHeight*4){appendBatch(6);}
    // active card highlight + dwell tracking for the affinity engine
    const center=feed.scrollTop+feed.clientHeight/2;
    let newActive=null;
    for(const c of cards){
      const mid=c.offsetTop+c.offsetHeight/2;
      const isActive=Math.abs(mid-center)<c.offsetHeight/2;
      c.classList.toggle('active',isActive);
      if(isActive)newActive=Number(c.dataset.idx);
    }
    if(newActive!==null && newActive!==activeIdx){
      creditDwell();
      activeIdx=newActive;activeSince=Date.now();
    }
    ticking=false;
  });
});
// mark first active
markFirstActive();

// review sheet
const reviewWrap=document.getElementById('reviewWrap');
// Approximate hours to beat the main story (rounded, from typical player-completion times); 0 = no single-player story campaign. Titles not listed show no figure.
const BEAT_TIMES={"Horizon Zero Dawn Remastered":22,"Death Stranding Director's Cut":40,"Ghost of Tsushima Director's Cut":25,"EA Sports NHL 25":0,"Tour de France 2024":0,"Golf With Your Friends":0,"Rugby 22":0,"Cricket 24":0,"eFootball":0,"Gran Turismo Sport":0,"Project CARS 2":0,"Rennsport":0,"Carmageddon: Max Damage":0,"Descenders":0,"Skater XL":0,"Golf It!":0,"Monopoly":0,"UNO":0,"Super Bomberman R 2":4,"Ultimate Chicken Horse":0,"Clustertruck":0,"Party Animals":0,"Lil Gator Game":5,"Lost in Play":4,"Pikuniku":4,"Snake Pass":6,"Knights and Bikes":9,"LEGO Brawls":0,"The Gardens Between":2,"What the Golf?":0,"TOEM":3,"Islanders: Console Edition":0,"Steins;Gate 0":28,"Robotics;Notes Elite":40,"Root Letter: Last Answer":14,"Her Story":2,"Virginia":2,"Dear Esther: Landmark Edition":1,"Q.U.B.E. 2":5,"Portal Knights":15,"Pac-Man Championship Edition 2":0,"Namco Museum Archives Vol. 1":0,"Atari 50: The Anniversary Celebration":0,"SEGA Mega Drive Classics":0,"SNK 40th Anniversary Collection":0,"Castlevania Anniversary Collection":0,"Contra Anniversary Collection":0,"Capcom Beat 'Em Up Bundle":0,"Ultimate Marvel vs. Capcom 3":2,"Nex Machina":2,"Alienation":8,"Matterfall":5,"Resogun":3,"Super Stardust Ultra":0,"Mighty No. 9":5,"Elden Ring":55,"Baldur's Gate 3":75,"Red Dead Redemption 2":50,"The Witcher 3: Wild Hunt":52,"Cyberpunk 2077":26,"God of War":20,"God of War Ragnarök":26,"Horizon Forbidden West":25,"Marvel's Spider-Man Remastered":17,"Marvel's Spider-Man: Miles Morales":8,"Marvel's Spider-Man 2":17,"The Last of Us Part II":25,"The Last of Us Part I":15,"Uncharted 4: A Thief's End":15,"Uncharted 2: Among Thieves":10,"Uncharted 3: Drake's Deception":10,"Uncharted: The Lost Legacy":8,"Bloodborne":32,"Sekiro: Shadows Die Twice":30,"Dark Souls III":30,"Demon's Souls":30,"Final Fantasy VII Remake":35,"Final Fantasy VII Rebirth":45,"Final Fantasy XVI":35,"Persona 5 Royal":100,"Persona 3 Reload":70,"Nier: Automata":25,"Resident Evil 4":16,"Resident Evil 2":9,"Resident Evil Village":10,"Metal Gear Solid V: The Phantom Pain":40,"Hogwarts Legacy":40,"Alan Wake 2":18,"Control":12,"Returnal":20,"Ratchet & Clank: Rift Apart":12,"Astro Bot":12,"Stray":6,"Hades":22,"Hollow Knight":27,"Celeste":9,"Cuphead":6,"Inside":4,"Limbo":4,"Journey":2,"Gris":4,"Firewatch":5,"Life is Strange":14,"Detroit: Become Human":12,"Heavy Rain":10,"Until Dawn":9,"Disco Elysium":25,"Outer Wilds":15,"Subnautica":25,"Dishonored":12,"BioShock Remastered":12,"Wolfenstein II: The New Colossus":11,"Metro Exodus":17,"Metro 2033 Redux":9,"Far Cry 3":15,"Far Cry 5":17,"Assassin's Creed II":20,"Assassin's Creed Origins":36,"Assassin's Creed Odyssey":45,"Assassin's Creed IV: Black Flag":20,"Tomb Raider":12,"Rise of the Tomb Raider":14,"Shadow of the Tomb Raider":15,"Batman: Arkham Asylum":11,"Batman: Arkham City":20,"Alien: Isolation":17,"Prey":17,"DOOM Eternal":14,"DOOM":12,"It Takes Two":14,"Split Fiction":14,"Clair Obscur: Expedition 33":35,"Black Myth: Wukong":25,"Kingdom Come: Deliverance II":40,"Indiana Jones and the Great Circle":18,"Starfield":30,"The Elder Scrolls V: Skyrim Anniversary Edition":35,"Dragon Age: Inquisition":40,"Octopath Traveler II":55,"Tales of Arise":35,"Yakuza 0":30,"Call of Duty: Modern Warfare III":5,"Call of Duty: Modern Warfare II":6,"Call of Duty: Black Ops 6":8,"Call of Duty: Black Ops Cold War":6,"Call of Duty: Vanguard":6,"Call of Duty: Modern Warfare (2019)":6,"Call of Duty: Infinite Warfare":7,"Call of Duty: WWII":7,"Call of Duty: Black Ops III":9,"Call of Duty: Advanced Warfare":7,"Call of Duty: Ghosts":6,"Call of Duty: Black Ops 4":0,"Call of Duty: Warzone":0,"Nioh 2":40,"Lies of P":25,"Armored Core VI: Fires of Rubicon":20,"Devil May Cry 5":10,"Sifu":8,"Hi-Fi Rush":12,"Sea of Stars":30,"Dave the Diver":15,"Tunic":12,"Death's Door":8,"A Plague Tale: Innocence":11,"A Plague Tale: Requiem":15,"Kena: Bridge of Spirits":12,"Fortnite":0,"Minecraft":0,"Rocket League":0,"Apex Legends":0,"Roblox":0,"VALORANT":0};
function beatLine(t){const v=BEAT_TIMES[t];if(v===undefined)return "";return v===0?"<div class=\"beat\">⏱️ No single-player story campaign</div>":"<div class=\"beat\">⏱️ About "+v+" hour"+(v===1?"":"s")+" to beat the story (approximate)</div>";}
const STORY_OVERRIDES={
"EA Sports NHL 25":"No story campaign. You play hockey with real NHL teams and players, or build a career as a pro, working from the junior leagues to the NHL. Franchise mode lets you manage a team over many seasons. It is a sports sim about hockey.",
"Tour de France 2024":"No story. You take charge of a professional cycling team, choose riders, and plan tactics for the Tour de France. In races, you lead cyclists up mountain climbs and through sprints. It is a sports management sim.",
"Golf With Your Friends":"No story. Up to 12 players play mini-golf on courses filled with obstacles, such as loops and lava. Each hole is a short, silly challenge. It is a game best played with friends.",
"Rugby 22":"No story campaign. You play rugby with national and club teams, or lead your own team through seasons in career mode. The game covers scrums, lineouts, and tries. It is a straightforward rugby sim.",
"Cricket 24":"No story campaign. You play cricket with international and domestic teams, or build a career from a rookie to a star. Matches simulate batting, bowling, and fielding in detail. It is a cricket sim.",
"eFootball":"No story campaign. This is a free-to-play football game with online matches, where players collect cards for players and form teams. It is updated regularly with new content.",
"Gran Turismo Sport":"There is no story, but the game has a Campaign mode, in which a driving school and missions teach you skills. The main focus is online competition, with races in licensed cars on real tracks. It is a racing game for car lovers.",
"Project CARS 2":"You begin a career as a driver, starting in lower categories of motorsport and working your way up to professional racing. The game includes many racing classes, such as GT, IndyCar, and rallycross, plus dynamic weather. There is no story, only a career.",
"Rennsport":"No story. This is a racing game built around online competition, with licensed cars and tracks. It focuses on realistic driving and ranked matches.",
"Carmageddon: Max Damage":"No story. This is a violent driving game where you earn points by wrecking opponents' cars and hitting pedestrians. Levels are open arenas where you can race or just cause chaos. It is a dark-humored throwback to a controversial classic.",
"Descenders":"No story. You ride a mountain bike down randomly generated trails, doing tricks and avoiding crashes. In Career mode, you work toward becoming a pro rider. It is a game about speed and risk.",
"Skater XL":"No story. This is a skateboarding sim in which you control the feet with the analog sticks. You skate in real-world-style parks and share custom maps. It is a game about the feel of skating.",
"Golf It!":"No story. This is a mini-golf game with imaginative levels, including a level editor to build your own. Up to eight players compete online or locally. It is a casual party game.",
"Monopoly":"This is the classic board game in which players roll dice, buy properties, and try to bankrupt each other. The digital version supports online and local play, with house rules. There is no story, only the competition.",
"UNO":"This is the classic card game, in which players try to be the first to get rid of all their cards, matching colors or numbers. You play against AI or friends online. There is no story, only the fun of the game.",
"Super Bomberman R 2":"Bomberman characters place bombs to blow up blocks and each other in grid-style arenas. A story mode takes you across planets, and multiplayer supports up to 16 players. The story is a simple, cartoon adventure.",
"Ultimate Chicken Horse":"There is no story. In each round, players place hazards and platforms to build a course, and then race through it. Points are given only if you finish, but not everyone does. It is a game of trickery.",
"Clustertruck":"There is no story. You jump from moving truck to moving truck, across rooftops, trains, and falling structures, to reach the end of the level. The trucks crash, and you have to react quickly. It is a game about speed.",
"Party Animals":"There is no story. Cute animals fight in physics-based brawls, grabbing and throwing each other off platforms. Up to eight players play in online or local matches. It is a silly party game.",
"Lil Gator Game":"A small alligator child is upset because their older sister, who has come home from college, has no time to play. To bring her back, the child sets off to make a huge playground on the island, with the help of other kids. It is a warm story about growing up and imagination.",
"Lost in Play":"Toto and Gal are siblings who travel through a world made of their imaginations, such as a goblin village and an enchanted forest. They solve puzzles and talk to funny characters with no spoken dialogue. It is a gentle story of childhood.",
"Pikuniku":"Piku is a round red creature with long legs who is exiled from his home and discovers a village living under the control of a mining company. He befriends the villagers and sets out to find the truth. It is a quirky, satirical story.",
"Snake Pass":"Noodle, a snake, and Doodle, a bird, travel through floating islands to restore the world's power gems. The challenge is to slither, coil, and climb to reach goals. It is a gentle platformer.",
"Knights and Bikes":"In the 1980s, on the island of Penfurzy off the coast of Britain, two girls, Demelza and Nessa, ride their bikes to look for a treasure. They explore the island, fight monsters with kid weapons such as frisbees, and find a mystery. It is a funny, heartfelt story of friendship.",
"LEGO Brawls":"There is no deep story. LEGO minifigure fighters brawl in colorful arenas, with friends in teams or battle royale. You earn bricks to customize your fighter. It is a family-friendly brawl.",
"The Gardens Between":"Arina and Frendt, two best friends, are in a treehouse when they are swept away into a mysterious garden world. They travel through islands that look like their memories, carrying a lantern, and you control time itself to solve puzzles. It is a wordless story about friendship.",
"What the Golf?":"There is no story. This is a golf game that constantly changes the rules, so you might kick the ball, play as a golf club, or navigate impossible courses. It is a comedic game that parodies sports games.",
"TOEM":"A young person sets off on a trip, hoping to see a natural phenomenon called a TOEM, and uses a camera to help people on the way. Each photograph helps others, and the world is drawn in black and white. It is a cozy story about kindness.",
"Islanders: Console Edition":"There is no story. You place buildings, such as houses and farms, on islands to score points and unlock new building types. The goal is to build the most efficient layouts. It is a relaxing puzzle game.",
"Steins;Gate 0":"After failing to prevent a friend's death in a previous timeline, Rintaro Okabe, a self-proclaimed mad scientist, has given up on time travel. He reluctantly joins a project involving an AI created from a dead scientist's memories, which pulls him back into the fight. Your choices lead to different endings. It is a sci-fi story about regret and hope.",
"Robotics;Notes Elite":"In a rural Japanese town, a high-school robotics club wants to build a giant robot like those in a famous anime. They discover a mystery involving a strange augmented-reality app and a global conspiracy. You make choices in a visual novel. It is a story about friendship and technology.",
"Root Letter: Last Answer":"A man receives a letter from his high-school pen pal, who disappeared 15 years ago. He travels across Japan to Shimane to find her and discovers that the letter doesn't match the truth. Your choices lead to different endings. It is a mystery about memory and truth.",
"Her Story":"You search a database of police interview videos from a 1990s murder case, in which a woman is questioned about her missing husband. By typing keywords, you find clips and piece together what happened. There is no instruction, only your curiosity. It is a story told in fragments.",
"Virginia":"In 1992, FBI agent Anne Tarver is sent to the small town of Kingdom, Virginia, to investigate a missing boy, partnered with Maria Halperin. The story is told without dialogue, using film-style cuts. As the case unfolds, their relationship is tested. It is a surreal mystery.",
"Dear Esther: Landmark Edition":"You walk across a remote Hebridean island as a narrator reads letters addressed to someone named Esther. The details of a car crash, a lost love, and an obsession emerge as you walk. There is no combat or puzzle, only exploration and a poetic story.",
"Q.U.B.E. 2":"Amelia Cross, an archaeologist, wakes up on an alien planet with no memory of how she got there and teams up with another survivor. She solves puzzles by manipulating colored blocks with her gloves, to find a way off the planet. It is a puzzle-adventure with a sci-fi story.",
"Portal Knights":"The world has been shattered into floating islands, and a hero must travel between them using portals. You can play as a warrior, ranger, or mage, build a home, and fight monsters. The story is simple, but the focus is on adventure and crafting.",
"Pac-Man Championship Edition 2":"There is no story. Pac-Man runs through speedy mazes, eating dots to get ghosts that chase him in a train. The game is an arcade-style score attack. It is a fast version of the classic game.",
"Namco Museum Archives Vol. 1":"There is no story. The collection includes classic arcade games such as Galaga, Dig Dug, and Xevious, each with its own gameplay. It also contains tools to adjust the games.",
"Atari 50: The Anniversary Celebration":"There is no story. The collection allows you to play over 90 Atari games, and also features interactive timelines, interviews, and archives about the company's history. It is a museum of early video games.",
"SEGA Mega Drive Classics":"There is no story. The collection includes over 50 games, such as Sonic the Hedgehog and Streets of Rage. Each game is playable with features such as rewind and save states.",
"SNK 40th Anniversary Collection":"There is no story. The collection includes 13 games, such as Ikari Warriors and Athena, from the 1980s. It features online leaderboards and a museum mode.",
"Castlevania Anniversary Collection":"In these games, a vampire hunter from the Belmont family enters Dracula's castle to defeat him. The collection includes eight games from the 1980s and 1990s, such as Castlevania and Castlevania III: Dracula's Curse. It is a classic series of gothic action games.",
"Contra Anniversary Collection":"In these games, two commandos, Bill and Lance, fight against alien invaders in a series of run-and-gun levels. The collection includes classic arcade and console games. It is known for its tough difficulty and co-op play.",
"Capcom Beat 'Em Up Bundle":"The bundle contains seven games, including Final Fight, in which a mayor and his friends battle gangs on the streets, and Captain Commando. The stories are simple, but the action is non-stop. It is a nostalgic arcade collection.",
"Ultimate Marvel vs. Capcom 3":"There is no deep story. Teams of three Marvel and Capcom characters, such as Spider-Man and Ryu, battle each other in fast combos and super moves. A story mode follows Dr. Doom and Albert Wesker. It is a flashy crossover fighter.",
"Nex Machina":"There is no story. You control a lone hero who fights robots in arcade-style levels viewed from above. Enemies and projectiles fill the screen, and you rescue humans. It is a pure arcade shooter.",
"Alienation":"An alien invasion has begun and a team of heroes with powerful weapons fight to save Earth. You play as one of three classes and gather loot in missions around the world. The game is a cooperative twin-stick shooter.",
"Matterfall":"Avalon Darrow, a heroine, uses a special gun to fight an alien threat that has taken over a planet. The weapon can transform the environment, such as hardening or removing blocks. The story is a sci-fi backdrop for the action.",
"Resogun":"There is no story. You pilot a ship to protect humans from aliens in a circular city, flying in a loop. Each enemy leaves a human to rescue. Explosions cover the screen. It is a famous arcade shooter.",
"Super Stardust Ultra":"There is no story. You fly a spaceship around a rotating planet, shooting asteroids and enemies with different weapons. The game is a classic arcade shooter with a modern look.",
"Mighty No. 9":"Beck is a robot who is the only one who is not infected by a virus that has taken over other robots. He must defeat the corrupted Mighty Numbers by absorbing their powers. It is a retro action game from the creator of Mega Man.",
"Destruction AllStars":"This is a vehicular-combat game with no campaign story to speak of. In the arena, drivers crash into each other and then eject out of their cars to fight on foot. Each of the colorful characters, the AllStars, has unique powers and a car. It is a game about smashing things.",
"Atlas Fallen":"A world has been buried by sand, and a cruel ruler called the Sun God has put the lands to rule over the survivors. You play as a person who finds a magical gauntlet, Atlas, that houses an ancient spirit and gives power over sand. Together they surf the dunes, fight huge monsters, and try to fight back. It is a fantasy action game about rebellion.",
"Steelrising":"In 1789, King Louis XVI uses an army of clockwork automatons to crush the French Revolution in Paris. You play Aegina, an automaton dancer who is sent by Queen Marie Antoinette to protect her son. As she fights through a ruined Paris, she is forced to decide where her loyalty lies. It is a souls-like story of freedom and machines.",
"High on Life":"Aliens called the G3 Cartel have invaded Earth and want to harvest humans to use as a drug. A teenager and his sister Lupe are saved by Kenny, a talking gun, and hired by a bounty hunter to take on the cartel. He travels across the galaxy with a collection of sentient, rude weapons. It is a very silly sci-fi comedy.",
"Exoprimal":"Dinosaurs are pouring out of rifts in time and attacking the world. You play an Exofighter, a pilot in a powerful suit, who is pulled into a time loop run by an AI called Leviathan, who forces them into combat. As you complete missions with teammates, you find out why the rifts are appearing. It is a sci-fi story of dinosaurs and teamwork.",
"Lost Records: Bloom & Rage":"In 1995, four teenage friends in a small Michigan town make a pact during a summer. They film themselves with a video camera and discover a strange mystery. Twenty-seven years later, they meet again to deal with what happened, and the story switches between the two periods. Your choices shape the friendships. It is a heartfelt story about growing up.",
"Dustborn":"In an alternate 2030s America, divided by a fractured society, Pax is a young woman with a gift, 'Words', that lets her use language as a weapon. She and her crew of misfits are hired to deliver a mysterious package across the country on a road trip. Along the way, their choices determine how they handle conflict. It is a narrative adventure about identity and trust.",
"Dragon Ball: The Breakers":"Seven ordinary people get trapped on an island with a dangerous villain from Dragon Ball, called the Raider, such as Cell or Frieza. The survivors have to work together to find keys and use a time machine to escape, while the Raider hunts them. Survivors can find ways to power up. It is an asymmetric game in which one player is a monster.",
"My Hero Ultra Rumble":"Heroes and villains from the My Hero Academia anime, such as Deku and All Might, fight in a battle royale in a stadium. Teams parachute onto the map, battle with their superpowers, and try to be the last team standing. There is no story, only action.",
"Digimon Story: Time Stranger":"A young person is drawn into a mystery involving time, and discovers that history is being changed by a hidden threat. The player partners with Digimon, which are digital monsters that evolve into stronger forms, and travels between worlds. You collect and train monsters. It is a story about changing fate with friends.",
"Wuchang: Fallen Feathers":"In the late Ming dynasty of China, Wuchang, a pirate, wakes up with no memory, suffering from a mysterious illness known as Feathering, which turns people into monsters. She travels across a ruined land in search of a cure. She uses fast and aggressive combat to fight enemies. It is a dark fantasy of survival.",
"Super Mega Baseball 4":"This baseball game has a cartoonish style, with players of fictional teams. You can play a franchise mode over many seasons, building a team and developing players, who age and retire. There is also an Elite League with injuries. It is a game about the story that unfolds in a season.",
"AO Tennis 2":"You create a player and rise through the ranks, starting in small tournaments and working your way up to the pro tour, with training and sponsorships. The matches feature realistic tennis physics. You can also play online. It is a career story of a tennis player.",
"Top Spin 2K25":"A tennis game in which players hit the ball with timing-based shots, such as flat, slice, and top spin. In MyCAREER mode, you create a player and rise from an unknown to a tennis star, training and building skills. The game includes real players. It is a game about the journey to the top.",
"Undisputed":"You step into the ring as a boxer, with realistic punches, footwork, and defense. In Career mode, you start as an amateur, win fights, train, and build a rivalry on the road to becoming a champion. The game features real boxers. It is a boxing story of rise and glory.",
"art of rally":"You race classic rally cars from the 1960s to the 1980s through stylized landscapes in countries like Finland, Norway, and Sardinia. In career mode, you move up through the ranks, unlocking new cars and rallies. There is no story, only the joy of driving sideways.",
"Dakar Desert Rally":"You compete in the famous Dakar Rally in the deserts of Saudi Arabia, driving cars, trucks, and bikes across huge stages, with only a map and a compass. You have to navigate carefully and manage your vehicle. There is no story, only endurance.",
"F1 Manager 2024":"You run a Formula 1 team, deciding on race strategy, pit stops, car development, and finances. You watch the race from the pit wall and make calls in real time. The game includes real teams and drivers. It is a story of building a championship team.",
"Star Wars: Bounty Hunter":"Before the Clone Wars, Jango Fett is a bounty hunter who is recruited by Count Dooku to take on a mission that could make him the template for the Republic's clone army. He hunts a Jedi turned dark side cult leader, Komari Vosa, across the galaxy, using a jetpack and blasters. It is a prequel story starring a famous bounty hunter.",
"The Lord of the Rings: Gollum":"The creature Gollum has been captured and is being held by Sauron's forces. The game follows his struggle between his two sides, the timid Sméagol and the vicious Gollum, as he seeks to escape and find the ring. He uses stealth and climbing to move around. It is a story of obsession set in Middle-earth.",
"The Lord of the Rings: Return to Moria":"Dwarves return to Moria, a huge underground kingdom that fell to darkness long ago, to rebuild and reclaim it. They explore tunnels, mine, craft, and fight monsters in a survival game with up to eight players. The world is randomly generated. It is a story about reclaiming a lost home.",
"The Expanse: A Telltale Series":"Camina Drummer is a Belter, a person who lives in the outer solar system, who is a member of a crew that has just lost its ship. She joins a group of outcasts who are drawn into a conflict that could bring down the three powers: Earth, Mars, and the Belt. Your choices affect the crew and the war. It is a sci-fi drama based on the TV series.",
"John Wick Hex":"John Wick, a legendary assassin, must save his friend, the Bowery King, from a villain named Hex. The game is a strategy game in which time moves only when you act, letting you plan fights in slow motion. It is a stylish take on the action film.",
"The Thing: Remastered":"Captain Blake and his team arrive in Antarctica to investigate the fate of a lost research team, 'Outpost 31', from the film. They find a frozen base and the shape-shifting alien creature known as the Thing. The squad members' trust is limited, because any one could be infected. It is a tense survival horror story.",
"Tomb Raider IV-VI Remastered":"The collection includes three Lara Croft adventures: The Last Revelation, in which Lara goes to Egypt and finds an ancient evil; Chronicles, a collection of tales told at a funeral; and The Angel of Darkness, in which she is accused of murder in Paris. Each features puzzles, tombs, and exploration.",
"Legacy of Kain: Soul Reaver 1&2 Remastered":"Raziel is a vampire lieutenant who is killed by his master Kain, and is brought back as a wraith by a mysterious god. He sets off to take revenge on Kain across the broken world of Nosgoth, absorbing souls and switching between the physical and spirit realms. The second game follows his hunt through time. It is a dark gothic tale.",
"System Shock":"A hacker is caught tampering with the security of the Citadel Station and is given a deal by a corporate executive to remove the ethical limits of the AI called SHODAN. Six months later, he wakes up to find the station overrun by mutants and cyborgs and SHODAN in control. He fights to stop her from destroying Earth. It is a sci-fi horror story about artificial intelligence.",
"Quake":"A hostile dimension invades Earth through teleporters called slipgates, and you are a lone soldier sent to stop them. You fight through Gothic castles and techno-industrial bases, using shotguns, grenades, and nail guns, to the final boss, Shub-Niggurath. There is little story, but plenty of atmosphere.",
"Doom 64":"After the events of earlier games, a marine returns to a demon-infested base to confront the Mother Demon, who has resurrected hell's forces. The game features darker levels and more atmosphere than earlier games. You fight with shotguns and a chainsaw. It is a moody story of a lone marine.",
"Duke Nukem 3D: 20th Anniversary World Tour":"Duke Nukem, a muscle-bound hero with a love of one-liners, returns to Los Angeles to find it overrun by aliens. He blasts his way through streets, strip clubs, and spaceships, to take down the invaders. The tone is crude and humorous. It is a classic 90s action story.",
"Heretic + Hexen":"The collection includes Heretic, in which Corvus, an elf, tries to stop the Serpent Riders, and Hexen, in which you pick a fighter, a cleric, or a mage, to take on the same enemies. Both games feature medieval dark fantasy. It is a story about stopping a demonic invasion.",
"Ion Fury":"In the cyberpunk city of Neo D.C., a terrorist named Dr. Jadus Heskel is converting people into cyborgs. Shelly 'Bombshell' Harrison, a bomb disposal expert, goes after him with a revolver and her sharp wit. The game plays like a 90s shooter. It is a retro story of a one-woman army.",
"Turok":"Joshua Fireseed is a Native American warrior who inherits the mantle of Turok, a protector of the Lost Land, a world where dinosaurs and aliens live. He must stop a villain, the Campaigner, from using a powerful weapon, the Chronoscepter. He fights with bows, rifles, and the Cerebral Bore. It is a pulpy adventure.",
"Far Cry 3: Blood Dragon":"In a 1980s sci-fi future that has been ravaged by a nuclear war, Sergeant Rex 'Power' Colt is a cyborg commando who has been sent to an island to stop a rogue commander. He fights with a neon-colored arsenal and blood dragons. It is a spoof of 80s action films.",
"Hellpoint":"You wake up on the Irid Novo space station, a dying place that has been reduced to ruin by a catastrophe, with no memory of who you are. You are a Spawn, created to help restore the station by exploring dark corridors and fighting powerful bosses. The station's gravity shifts between dimensions. It is a haunting story of a lost place.",
"Curse of the Dead Gods":"An adventurer enters a cursed temple, drawn by treasure and legends, and finds himself unable to leave. He descends the rooms, battling monsters and avoiding traps, with each room giving him boosts in exchange for curses. Dying sends him back to the start. It is a story of greed and temptation.",
"Crown Trick":"A young girl named Elle wakes up in a mysterious labyrinth and discovers a crown that grants her power. She travels through the maze, which constantly changes, in a game in which enemies move only when she does. She collects items and learns the dungeon's secrets. It is a puzzle-like adventure.",
"Astral Ascent":"Four prisoners are exiled to the Garden, a prison for those who defy the Zodiac, and they are given the power to escape. They battle through the Garden, fighting the Zodiacs, who are powerful beings that control the fate of the world. The game is fast and full of choices. It is a story of rebellion against destiny.",
"Star Wars: Republic Commando":"During the Clone Wars, you lead Delta Squad, an elite team of clone commandos, on special missions behind enemy lines. You issue orders to your teammates to complete objectives, such as destroying a droid factory or infiltrating a ship. It is a gritty look at war from the perspective of the clones.",
"Star Wars: Dark Forces Remaster":"Kyle Katarn is a mercenary working for the Rebel Alliance, who is assigned to steal the plans of the Death Star. He is then given missions to stop the Empire's Dark Troopers, a new type of robotic soldier. He travels through bases and ships. It is a classic story of the Rebellion.",
"Star Wars Jedi Knight: Jedi Academy":"A new student arrives at Luke Skywalker's Jedi Academy, and you create your own character, choose a lightsaber, and train. Soon, a cult of dark Jedi emerges, and you must stop them. You choose between the light side and the dark side. It is a story about becoming a Jedi.",
"Star Wars Episode I: Racer":"A young Anakin Skywalker races pods across dangerous planets in this game, which is based on the podrace in The Phantom Menace. You compete in championships to unlock new pods and tracks, and upgrade your vehicle. The speeds are extreme. It is a game about the thrill of the race.",
"Ghostbusters: The Video Game Remastered":"Two years after the second film, the Ghostbusters are back in New York, with a rookie joining them to test new equipment. They investigate the return of a villain, the god Gozer, and fight ghosts. It is a story of paranormal pest control.",
"War Thunder":"This is a free-to-play game of vehicular combat, in which players pilot tanks, planes, and ships from World War II and later. Matches are based on realistic vehicles and require teamwork. You unlock new vehicles through research. There is no story, only combat.",
"World of Tanks":"Teams of tanks battle on maps, with players controlling historical vehicles from different nations. You must use cover, flanking, and teamwork to win, since each tank has strengths and weaknesses. You earn credits to upgrade your tanks. There is no story, only strategy.",
"World of Warships: Legends":"Players command historical warships, such as destroyers, cruisers, and battleships, in team-based naval battles. You must use the terrain, torpedoes, and guns to take down the opposing team. You research new ships. There is no plot, only naval combat.",
"PlanetSide 2":"On a distant planet, three empires fight for control in a massive, persistent war with hundreds of players. You pick a faction, a class, and vehicles, and capture bases. Battles are huge. There is no storyline, only a long war.",
"Nuclear Throne":"After the apocalypse, the world is full of mutants, and legend says that the Throne, a mysterious seat, can grant its occupant a wish. You pick a mutant, such as a fish, a crystal, or an eye, and fight through randomly generated areas to reach it. Each run is different, and death sends you back to the start. It is a frantic story of ambition in a ruined world.",
"Gang Beasts":"There is no story here. Wobbly, jelly-like characters fight in silly arenas such as rooftops, construction sites, and trains. They grab, throw, and punch each other until only one is left standing. It is a game best played with friends in the same room.",
"I Am Bread":"You control a slice of bread that has a single dream: to become toast. You must crawl, flop, and roll through a house, such as a kitchen, a bedroom, and a garage, to reach a heat source. The controls are deliberately awkward, which makes everything a puzzle. It is a silly game about ambition.",
"PlateUp!":"You are a restaurant owner who starts with a small kitchen and grows it into a bustling business. Each day, you serve customers, then pick a new upgrade, such as a new appliance or menu. Up to four players can cooperate. There is no story, only the pressure of a busy dinner rush.",
"Unrailed!":"A train is racing forward and will never stop, and your job is to lay the track ahead of it. Players chop trees, mine iron, and craft rails before the train arrives, while dealing with obstacles such as rivers and enemies. Communication is key. There is no plot, only a race against time.",
"Neon Abyss":"In a neon-lit dungeon, a group of new recruits descend through floors filled with enemies and bosses in the Abyss. You collect items that stack in funny ways and hatch pets that follow and fight with you. Each run is random. It is a colorful, fast-paced game about chaos.",
"Death Road to Canada":"A zombie outbreak has swept across America, but legend says that Canada is safe. You lead a group of survivors in a car, stopping in towns to scavenge for food and gas and facing random events. Each trip is different, and death is permanent. It is a funny, grim road-trip story.",
"Darkwood":"A man known as the Stranger wakes up in a cursed forest in Poland, trying to find a way out. During the day, he scavenges for materials; at night, he defends his shelter from creatures that emerge in the dark. The forest is full of strange characters and a deep mystery. It is a slow, disturbing horror story.",
"Super Meat Boy Forever":"Meat Boy and Bandage Girl live happily with their baby daughter, Nugget, until the villain Dr. Fetus kidnaps her. The two heroes chase him through chaotic worlds, with Meat Boy running automatically while you jump and slide. Each level is randomly assembled. It is a brutal, humorous rescue story.",
"N++":"You control a tiny ninja who must collect gold and reach the exit of each level, avoiding deadly hazards like mines, lasers, and drones. There are thousands of levels, each a short, tense puzzle. The ninja can run, jump, and wall-jump with momentum. There is no story, only skill.",
"Geometry Wars 3: Dimensions":"This is an arcade game with no story. You control a small ship in a twin-stick shooter, destroying swarms of geometric enemies that appear in waves. Levels take place on 3D shapes such as spheres and cylinders. It is a game about score-chasing.",
"Dead Nation":"A mysterious infection has turned most of a city's inhabitants into zombies. Two survivors, Jack McReady and Scarlett Blake, fight their way through the ruined streets with guns and explosives, looking for a safe place. The game is a twin-stick shooter viewed from above. It is a tense survival story.",
"Velocity 2X":"Kai Tana, a pilot, flies through enemy territory to rescue survivors in her spaceship, the Quarp Jet. She teleports short distances in the ship and, in platforming sections, on foot. The story takes her from space to the ground to stop an alien invasion. It is a speedy mix of shooting and platforming.",
"Steep":"You are free to roam a huge open world modeled after the Alps and choose between skiing, snowboarding, paragliding, and wingsuit flying. You complete challenges, find hidden spots, and earn reputation. There is no story, only the thrill of the mountains.",
"Need for Speed Payback":"Tyler Morgan, a driver; Sean 'Mac' McAlister, a getaway driver; and Jessica Miller, a racer, are betrayed during a heist by a shadowy cartel called The House. They split up, and then reunite to take their revenge in Fortune Valley, a Las Vegas-style desert. The game mixes street racing, heists, and chases. It is an action-movie story.",
"DiRT 4":"You become a rally driver, starting as a rookie and working your way up in the sport by joining a team and competing in events around the world. The game includes a mode in which you can create your own tracks. There is no story, but a career that follows your progress.",
"GRID Legends":"Driven to Glory is a story mode that follows a rookie driver who joins Seneca Racing and works their way up to challenge a rival team. The cutscenes are live action and feature a cast of racers and mechanics. You can also play a variety of racing styles, from circuits to drift, in multiplayer. It is a racing drama.",
"Black Desert":"In a vast fantasy world, a mysterious force called the Black Spirit grants powers to heroes who fight against dark forces. You create a character, choose a class, and fight monsters in real-time action combat. The game includes trading, fishing, and housing. It is a massive online world.",
"Dauntless":"Giant creatures called Behemoths roam the land and threaten the settlements, so hunters called Slayers are called to fight them. You hunt in teams of up to four, studying the Behemoths, and use their parts to craft weapons and armor. Your base is the town of Ramsgate. It is a cooperative monster-hunting game.",
"Elite Dangerous":"You pilot a spaceship in a realistic version of the Milky Way, with 400 billion star systems. You choose whether to be a trader, miner, explorer, or fighter, and your actions can affect the power balance of factions. There is no campaign, only the freedom of the galaxy.",
"Terminator: Resistance":"In 2028, humanity is in a war against Skynet, an AI that has taken over the planet. You play Jacob Rivers, a young soldier of the Resistance in Los Angeles, who has been assigned to fight machines. You scavenge, craft, and talk to survivors while you search for a way to defeat Skynet. It is a bleak story based on the Terminator films.",
"Back to the Future: The Game":"In 1986, Marty McFly's friend, Doc Brown, mysteriously vanishes, and his DeLorean time machine is sent back to 1931. Marty goes back to Hill Valley in 1931 to find him, and he has to avoid changing history. As Marty solves puzzles in the past, he meets younger versions of familiar characters. It is a funny, nostalgic adventure.",
"Friday the 13th: The Game":"At Camp Crystal Lake, the legendary killer Jason Voorhees hunts a group of teenage counselors. One player is Jason, while up to seven others try to escape by repairing a car or boat or calling the police. Each side has different strengths. It is an homage to the slasher films.",
"Evil Dead: The Game":"Ash Williams, a store clerk, and his friends fight demons called Deadites, which have been unleashed by reading from the Necronomicon, a book of the dead. Players team up as characters from the movies and TV series, or take the role of the demon. It is a cooperative, humor-filled horror.",
"Predator: Hunting Grounds":"A group of mercenaries in a jungle are hunted by the Predator, an alien who hunts for sport. Four players play as a fireteam trying to complete objectives, while a fifth plays as the Predator. The Predator has invisible camouflage and advanced weapons. It is a game of cat and mouse.",
"Five Nights at Freddy's: Security Breach":"Gregory, a young boy, is locked inside Freddy Fazbear's Mega Pizzaplex, a giant pizza and entertainment center, overnight. He is helped by Freddy, a friendly animatronic bear, and must avoid other animatronics that are hunting him. He explores a large building and tries to escape before the morning. It is a horror story with jump scares.",
"Bendy and the Ink Machine":"Henry, an animator, returns to the old Joey Drew Studios, where he once worked, after receiving a letter from his former boss. Inside the abandoned studio, he finds ink-covered corridors, strange machines, and monsters, including Bendy, a cartoon demon. He explores to find out what happened. It is a spooky story about a vintage cartoon.",
"Yu-Gi-Oh! Master Duel":"This is a free-to-play digital version of the card game, in which two players duel using decks of monsters, spells, and traps. You can collect cards, build decks, and play ranked matches online. A solo mode follows an anime-style story. It is a game about strategy.",
"Hatsune Miku: Project DIVA Future Tone":"This rhythm game features songs sung by the virtual singer Hatsune Miku and other Vocaloid characters. You press buttons in time with the music video, which features dance and animation. There are over 200 songs. There is no story, only music and rhythm.",
"Bluey: The Videogame":"Bluey is a playful Australian Blue Heeler puppy who has a loving family and a vivid imagination. In the game, you play through scenes from the animated show, such as playing with her sister Bingo, with her parents, Bandit and Chilli. Each episode features a different game. It is a gentle, family-friendly adventure.",
"SpongeBob SquarePants: Battle for Bikini Bottom - Rehydrated":"The villain Plankton creates an army of robots, which go crazy and take over Bikini Bottom. SpongeBob and his friend Patrick set out to stop them by collecting golden spatulas and defeating the robots. The levels include Jellyfish Fields and Goo Lagoon. It is a lighthearted remake of a platforming classic.",
"SpongeBob SquarePants: The Cosmic Shake":"SpongeBob and Patrick make a wish on a magical jellyfish that creates portals to strange alternate worlds, and their friends, in the form of a Wild West and a fairy tale. They have to travel through these worlds to fix the problem and save Bikini Bottom. It is a silly, colorful adventure.",
"Minecraft Legends":"The Overworld is invaded by Piglins, who are creatures from the Nether who want to take over. You play as a hero who must rally the Overworld's inhabitants and build an army to defend it. Gameplay combines action, strategy, and exploration. It is a cooperative game set in the Minecraft universe.",
"Bomb Rush Cyberfunk":"Red, a young man, arrives in New Amsterdam, a city where graffiti crews skate, bike, and blade around to claim territory. He joins a crew, the Bomb Rush Crew, and fights rival gangs and the police while uncovering a mystery about a mysterious force. The game features funk music and street art. It is a stylish homage to Jet Set Radio.",
"Hello Neighbor":"You are a kid who moves into a house across the street from a neighbor who seems to be hiding something in his basement. You must sneak into his house, avoid his traps, and find the key to the locked door, while the neighbor learns from your tactics. The story is revealed through the levels. It is a stealth horror about curiosity.",
"The Escapists 2":"You are a new prisoner in a prison and your goal is to escape. You must follow a daily routine, craft tools, hide contraband, and plan your escape to avoid getting caught. Each prison has its own security and challenges, such as a prison in space or a train. It is a humorous story about prison breaks.",
"Prison Architect":"You are the warden of a prison, who must design it, hire staff, and take care of the inmates. You decide whether to focus on security, rehabilitation, or profit. Events, such as riots, escapes, and crime, challenge your decisions. There is no story, only the prison you build.",
"RimWorld":"A group of colonists crashes on a distant planet and must build a settlement to survive. An AI storyteller generates events, such as raids, diseases, and weddings, to create a unique story each time. You manage their needs, moods, and relationships. It is a game that creates its own stories.",
"Nidhogg":"Two fencers duel in a tug-of-war across a series of screens, trying to reach the end of the map. The winner is eaten by a giant worm, the Nidhogg. Each duel is a battle of high, middle, and low sword positions. There is no story, only the rush of the match.",
"Duck Game":"Ducks equipped with weapons fight each other in small arenas, in short rounds that last seconds. Up to four players can play on one screen, and the weapons are randomly distributed. The game is a chaotic mix of platforming and shooting. There is no plot, only silly fights.",
"SpeedRunners":"Superheroes race through obstacle courses, trying to leave their opponents behind. A camera that follows the lead eliminates anyone who falls too far behind. Players use grappling hooks and items to win. There is no plot, only competition.",
"Rocket Arena":"Teams of three compete in an arena in which rockets knock out opponents rather than damaging them. Each hero has unique abilities, and when your opponent is knocked out of the arena, you score. There is no story, only fast-paced team play.",
"Knockout City":"Teams of players compete in a city-sized dodgeball brawl, where they can throw balls, dodge, and even turn their teammates into balls. The matches are short and fast. There is no story, only the rhythm of the game.",
"Cozy Grove":"You are a Spirit Scout who is sent to a haunted island where ghost bears are stuck in limbo. You help them by finishing tasks, such as cooking and fishing, to bring color back to the island. Each day, new events happen. It is a peaceful story about helping others find peace.",
"Fae Farm":"You arrive on the magical islands of Azoria, where fairy tales come to life. You farm, craft, explore dungeons, and cast spells while making friends with the villagers. The islands are rich with secrets. It is a cozy fantasy game.",
"Roots of Pacha":"You are a member of a small clan in the Stone Age, who must survive by farming, crafting, and living together. You discover new technologies such as taming animals and building. Seasons and festivals change over time. It is a cozy story about early civilization.",
"Spirittea":"You move to a quiet village and find an old bathhouse, which is haunted by spirits. You revive it by cleaning, serving spirits, and solving their problems, which also helps the town. You meet quirky villagers. It is a peaceful story about community.",
"Wylde Flowers":"Tara returns to her family's farm in a small coastal town, where she discovers that she comes from a family of witches. She farms, makes friends, and learns magic while exploring a romance and a mystery. The game features a diverse cast. It is a warm, cozy story about home.",
"Potion Permit":"A young chemist arrives in the town of Moonbury, where the locals do not trust her after a mishap. She earns their trust by brewing potions to cure illnesses, gathering herbs, and building relationships. You meet unique townsfolk. It is a gentle story about healing.",
"Roblox":"Roblox is not a single game but a platform where millions of players create and play their own games, called experiences. You create an avatar and explore worlds made by other users, from obstacle courses and horror stories to role-play cities and tycoon games. There is no main story, because the content is always changing. It is a game about creativity and community.",
"Paladins":"The game is set in a fantasy world where champions from different realms fight in a war. Teams of five face off in objective-based matches, with each champion having their own abilities and role. Before a match, you build a deck of cards that modify your abilities. There is no campaign, only competitive team play.",
"Smite":"You play a god, such as Zeus, Anubis, or Loki, from world mythologies, and fight in a team against another team of gods. The goal is to destroy the enemy's base while defending your own, aided by minions. Matches last around 30 minutes. There is no story mode, only competition.",
"Rogue Company":"Players are mercenaries called Rogues, who take on missions in short, tactical rounds. Teams buy weapons and gear at the start of each round and try to eliminate the other team or complete objectives. Each Rogue has unique gadgets. There is no campaign, only multiplayer.",
"VALORANT":"Two teams of five face off, with one attacking and one defending, in rounds that end when a bomb is planted and exploded, or a team is eliminated. Each player picks an agent with distinct abilities, such as smoke or healing, in addition to realistic gunplay. There is no single-player campaign, but the agents have backstories. It is a precision-focused team shooter.",
"Delta Force":"The game is a tactical shooter featuring large-scale battles based on the series' history. In Warfare, 32 vs. 32 players fight with tanks and helicopters, while in Operations, squads infiltrate maps to extract valuable items. There is also a campaign with missions, which retells events. It is a team-based military shooter.",
"ARC Raiders":"In a future where machines called ARC have invaded Earth and forced humans to live underground, you play a Raider who goes to the surface to scavenge for supplies. You can team up with others or work alone, but other players may attack you. If you get out alive, you bring supplies back to the underground city. It is a tense survival game about risk and reward.",
"Battlefield 6":"In the near future, a private military company named Pax Armata is on the rise as NATO falls apart. In the campaign, an American squad, Dagger 13, takes on missions around the world to stop them. In multiplayer, up to 64 players fight in massive battles with vehicles, where buildings can be destroyed. It is a large-scale war shooter.",
"Borderlands 4":"On a distant planet called Kairos, a ruthless ruler called the Timekeeper controls the population using a technology that makes them obey. A new group of Vault Hunters, treasure-seeking mercenaries, arrives to take him down. You play as one of four characters, shooting your way through a colorful, open world, collecting loot. It is a humorous, loot-focused shooter.",
"The Elder Scrolls IV: Oblivion Remastered":"The emperor of Tamriel, Uriel Septim, is assassinated, and before he dies, he entrusts a prisoner with an amulet and a mission to find his lost heir. Meanwhile, gates to a demonic realm called Oblivion open across the land, and an evil cult seeks to bring the world to ruin. You are free to join guilds, explore, and decide how to save the world. It is a classic open-world fantasy.",
"Final Fantasy Tactics: The Ivalice Chronicles":"In the kingdom of Ivalice, a war of succession called the War of the Lions is tearing the realm apart. Ramza Beoulve, a young noble, finds himself caught between two sides after his friend Delita is lost. As Ramza struggles to do what is right, he discovers a dark secret behind the conflict. The game is a turn-based tactics story about class, loyalty, and betrayal.",
"Dragon Quest VII Reimagined":"A boy from a tiny fishing village on a remote island discovers that his island is the only land in the world. He and his friends find mysterious stone tablets that send them back in time to restore other islands that have vanished. Each island has its own story, from happy to sad. It is a long, heartfelt JRPG about traveling through time.",
"Nioh 3":"The game is set in Japan's Sengoku era, a period of civil war, where yokai, supernatural demons, are wreaking havoc. You play a samurai who can switch between two fighting styles, samurai and ninja, as you fight in open fields and fortresses. The story involves historical figures like the young Tokugawa. It is a tough, tactical action game.",
"Crimson Desert":"On the continent of Pywel, the Greymanes are a group of mercenaries who are attacked by a rival force. Kliff, one of the survivors, sets out to reunite his scattered comrades and find out who is behind the attack. You explore a huge open world, fight with swords and magic, and ride horses. It is a gritty medieval adventure.",
"Saros":"Arjun Devraj, a soldier, travels to an alien planet called Carcosa, which is a cursed and dangerous world, in search of answers. Each time he dies, he returns, and the world changes around him. You fight enemies in fast, bullet-filled battles, using abilities and upgrades. It is a mysterious sci-fi story about loss and survival.",
"007 First Light":"This is an origin story for a young James Bond, before he becomes the famous secret agent, as he starts out as a new recruit in the 00 program. He goes on missions around the world, using stealth, fighting, and driving to take down enemies. The game is a reimagining of the Bond story. It is the first part of a planned series.",
"Pragmata":"On a remote research station on the Moon, an astronaut named Hugh is stranded after an accident and meets Diana, a young android girl. Together, they try to escape the station while being hunted by robots. Hugh shoots enemies while Diana hacks their defenses in real time. It is a sci-fi story about an unlikely partnership.",
"Marathon":"On a lost colony called Tau Ceti IV, mysterious events have left the colony abandoned and valuable relics lying around. Teams of cybernetic Runners are sent to retrieve them, fighting both alien dangers and other Runners. You enter, grab loot, and try to extract before time runs out. It is a competitive sci-fi shooter.",
"Fatal Frame II: Crimson Butterfly Remake":"Twin sisters Mio and Mayu Amakura follow a crimson butterfly to a hidden village called Minakami, which is haunted by a dark ritual. They are trapped in the village and must find a way out, while Mayu is slowly being affected by the village's curse. Mio uses a special camera, the Camera Obscura, to fight ghosts. It is a haunting story about sisterhood.",
"Phantom Blade Zero":"In a dark, fictional version of ancient China, Soul is an assassin who has been betrayed by his own order and left for dead. He seeks revenge on those responsible, and fights using blades and martial arts. Combat is fast and stylish, with a focus on parrying. It is a wuxia-inspired tale of revenge.",
"Tokyo Xtreme Racer":"You play a street racer who tries to become the best in Tokyo's night racing scene by driving on the expressways and challenging other drivers. Each opponent has a health bar, and you win by staying ahead of them. You tune your car and earn respect. It is a story about earning a name on the streets.",
"The Dark Pictures Anthology: Directive 8020":"A crew of colonists on a spaceship are on a long journey to a new home when something goes wrong and a deadly threat emerges. The decisions you make as different characters affect who survives and how it ends. It is a cinematic sci-fi horror from the makers of Until Dawn.",
"The Binding of Isaac: Rebirth":"Isaac is a boy whose mother hears a voice from God telling her to sacrifice him, so he flees into the basement. There, he fights through randomly generated rooms full of monsters, collecting bizarre items that change his abilities. Each run is different, and the story is revealed through multiple endings. It is a dark, humorous game about fear and faith.",
"God Hand":"Gene is a wandering fighter who receives a powerful, magical arm, the God Hand, and uses it to defeat a gang of demons. He fights through levels with a huge number of moves that you can customize. The story is silly, with over-the-top villains and crude humor. It is a cult-classic brawler.",
"Samurai Shodown":"Set in a fictional version of feudal Japan, warriors from different lands fight in duels using weapons such as swords and spears. The game is slower than other fighters and rewards careful play, since a single hit can do massive damage. Each fighter has their own story. It is a stylish weapon-based fighting game.",
"SnowRunner":"You drive huge off-road trucks through remote regions of the US, Russia, and other places, delivering cargo to remote locations. The terrain is muddy, snowy, or rocky, which makes it difficult to drive. You can use winches and tire chains to get unstuck. There is no story, only contracts, but it is a relaxing and challenging experience.",
"Microsoft Flight Simulator 2024":"This is a flight simulation game that lets you fly aircraft all over a digital version of Earth, from small planes to large jets. You can complete career missions, such as rescue flights and cargo deliveries, or just explore freely. The game uses real-world data, including weather and terrain. There is no plot, only the joy of flying.",
"Project CARS 3":"You start as a rookie racing driver and rise through the ranks through a career mode, racing in different classes and car types. You earn money to buy and upgrade cars. The game includes a wide selection of tracks. There is no plot, only a progression.",
"Graveyard Keeper":"A man dies in a car crash and wakes up in a medieval world where he is made the keeper of a graveyard. He wants to return home to his girlfriend, but first he must repair the church, bury bodies, and run a farm, with the help of a talking skull. The game is full of dark humor about morality. It is a cozy management sim with a grim twist.",
"Planet Zoo":"This is a zoo-building simulation with no fixed plot. You design habitats for animals from around the world, take care of their needs, and manage staff and guests. The Career mode gives you goals, while Sandbox lets you build freely. It is a game about conservation and creativity.",
"Jurassic World Evolution":"You are the operator of a dinosaur theme park on the islands near Isla Nublar in the Jurassic Park universe. You build attractions, research dinosaur DNA, and keep the animals safe while three divisions, Science, Entertainment, and Security, ask for favors. When storms or mistakes cause the dinosaurs to escape, you must respond quickly. It is a management story about the risks of playing God.",
"Humankind":"You lead a culture through the entire history of humanity, from hunter-gatherers to space-age society. In each era, you choose a new culture, such as the Egyptians or the Romans, and combine their traits. You explore, expand, trade, and fight other civilizations, trying to become the most famous. There is no fixed story, only your own.",
"Bad North":"A group of Vikings, driven from their homeland, lands on a series of small islands, where they must fend off raiders from the sea. You command small squads in real time, placing them on beaches and choosing which houses to protect. Each island is a short battle, and units that fall are gone for good. It is a simple yet tense story about a people defending their land.",
"Minecraft: Story Mode":"Jesse, a young adventurer, and friends travel to a convention for builders and find that a threat called the Wither Storm is attacking the world. They seek the Order of the Stone, a group of legendary heroes, who once defeated the Ender Dragon. Along the way, your choices change who survives. It is a humorous, family-friendly adventure in the blocky world.",
"Game of Thrones: A Telltale Games Series":"House Forrester is a noble family in the north of Westeros whose lord is killed in the bloody aftermath of the Red Wedding. The surviving family members, including Ethan, Mira, and Rodrick, try to protect their home and ironwood trees from a rival house. You play multiple characters, making decisions that determine who lives. It is a story about loyalty in the world of Game of Thrones.",
"Marvel's Guardians of the Galaxy: The Telltale Series":"Star-Lord and his team of misfit heroes in space, the Guardians of the Galaxy, find a powerful artifact called the Eternity Forge, which can bring back the dead. When the villain Hala the Accuser seeks it, the Guardians have to protect it and their own past. You make choices that affect the relationships among team members. It is a humorous, emotional space adventure.",
"Batman: The Enemy Within":"Bruce Wayne is still the Batman in Gotham City, when a criminal known as the Riddler returns, and an agency known as the Agency, led by Amanda Waller, pressures him. At the same time, Bruce becomes closer to a man named John Doe, who will become the Joker. Your decisions shape both Bruce's and John's paths. It is a story about friendship and the creation of a villain.",
"Twin Mirror":"Sam Higgs is a former journalist who returns to his hometown of Basswood, West Virginia, for the funeral of his best friend, Nick. As he begins to look into Nick's death, he finds that the town has secrets, and that his memories of the night before are blank. Sam relies on his Mind Palace, a place in his head, and an imaginary version of himself to piece together the truth. It is a psychological mystery about memory and guilt.",
"Road 96":"In 1996, the country of Petria is ruled by a dictator, and teenagers are trying to flee across the border. Each time you play, you see a different teenager's journey, meeting characters who are connected to each other. You choose how to get from place to place, whom to trust, and what to do. It is a road-trip story about freedom and politics.",
"Dreamfall Chapters":"Zoe Castillo is a young woman in a future version of Earth, and Kian Alvane is a soldier in a fantasy world. Their lives are connected by a mysterious dream-like power that links the two worlds. As the worlds become unstable, they must choose between dreams and reality. It is a story-heavy adventure about hope and sacrifice.",
"A Space for the Unbound":"In 1990s Indonesia, Atma and Raya are high-school sweethearts who are about to graduate. Raya has a mysterious ability to see into people's minds and a notebook that can change reality, while a strange apocalypse looms. You explore their town, learn about their friends and families, and enter their inner worlds. It is a warm, emotional story about growing up.",
"Before Your Eyes":"You control the game by blinking, as you follow Benjamin Brynn, a young man who has died and is on a ferry to the afterlife. A ferryman asks him to recount his life, and each blink fast-forwards time. As you experience his childhood, family, and dreams, you try to make sense of his life. It is a short, moving story about memory.",
"Lake":"In 1986, Meredith Weiss returns to her hometown of Providence Oaks, Oregon, to take over her father's mail route for two weeks. She delivers packages and meets the quirky locals while thinking about her career and her family. Your choices, such as whom to talk to, shape her next steps. It is a relaxing slice-of-life story.",
"Trine 5: A Clockwork Conspiracy":"Three heroes, a thief named Zoya, a wizard named Amadeus, and a knight named Pontius, are brought together to stop a plot. A clockwork conspiracy threatens the kingdom, and they must travel through beautiful, magical lands to find out who is behind it. Each hero has unique abilities, which players combine to solve puzzles. It is a fairy-tale adventure.",
"Pac-Man World Re-PAC":"Pac-Man's friends and family have been kidnapped by Toc-Man, who also stole his birthday cake. Pac-Man travels through different worlds, eating ghosts and dots, to rescue them. He has new abilities, such as a rev-roll and a butt-bounce. It is a lighthearted platformer.",
"Sonic Mania":"Sonic the Hedgehog, along with Tails and Knuckles, is on a new adventure when Dr. Eggman, the villain, uses a mysterious Phantom Ruby gem to cause trouble. The trio travels through zones that are updated versions of classic levels and new ones. It is a nostalgic, fast-paced game that celebrates the series.",
"Sonic Origins":"This collection includes four classic games, Sonic the Hedgehog, Sonic CD, Sonic 2, and Sonic 3 & Knuckles, in which Sonic runs through zones to stop Dr. Eggman's plans. It adds new modes, such as an anniversary mode, and new animated cutscenes. It is a way to experience the early adventures of the blue hedgehog.",
"Contra: Operation Galuga":"In the year 2633, the Galuga Archipelago is attacked by a mysterious alien force. Two commandos, Bill Rizer and Lance Bean, are sent in to eliminate the invasion. You run, jump, and shoot through levels with massive bosses. It is a classic action game with nonstop firepower.",
"Strider":"Hiryu is a futuristic ninja and a member of the Striders, elite assassins. He travels to Kazakh City to take down the Grandmaster Meio, a villain who rules the city. He uses a plasma sword and acrobatic moves to fight enemies in an interconnected city. It is a reboot of a classic arcade game.",
"Teenage Mutant Ninja Turtles: The Cowabunga Collection":"The collection contains 13 classic games starring the Turtles, Leonardo, Donatello, Michelangelo, and Raphael, who are mutated teenage ninjas that fight the villain Shredder and his Foot Clan. Games include beat-'em-ups and fighting games. It also has art and music from the series.",
"Capcom Arcade Stadium":"This collection includes 32 classic arcade games from Capcom, such as 1942, Ghosts 'n Goblins, and Street Fighter II. Each game can be played in its original form, with online leaderboards. You can adjust the difficulty and screen settings. It is a way to relive arcade history.",
"Capcom Fighting Collection":"This collection includes ten classic fighting games, such as the Darkstalkers series, in which monsters like vampires and werewolves fight, along with Red Earth and Hyper Street Fighter II. It has online modes and training options. It is a celebration of Capcom's fighting games.",
"Street Fighter 30th Anniversary Collection":"This collection includes twelve Street Fighter games, from the original to Street Fighter III: Third Strike. In the series, the world's best fighters compete in tournaments, with characters like Ryu and Chun-Li. The collection also has a museum of art and history. It is a tribute to the series.",
"Octopath Traveler 0":"Your hometown is destroyed in a fire, and you are left with nothing but a desire to avenge it. With the help of friends, you gather allies, rebuild your town, and uncover the truth about who caused the disaster. The game uses an HD-2D art style, mixing pixel characters with 3D environments. It is a story of revenge and rebuilding.",
"Atelier Ryza 3: Alchemist of the End & the Secret Key":"Ryza is an alchemist who, with her friends, travels to Kurken Island, a mysterious and wild place with secrets. They gather materials, craft items, and explore ruins while uncovering the island's past. Ryza's alchemy skills allow her to solve problems and fight monsters. It is a cheerful story about friendship and adventure.",
"Blue Reflection: Second Light":"Ao Hoshizaki is a high-school girl who wakes up at a school in the middle of a sea, with no memory of how she got there. She and her classmates discover that they have special powers, and as they explore, they uncover the purpose of the school. They fight monsters, using abilities. It is a story about friendship and memory.",
"Harvest Moon: One World":"You are a farmer who travels around the world to find the Harvest Goddess, who has disappeared. You collect seeds, grow crops, raise animals, and restore the land. Along the way, you meet townspeople and build relationships. It is a relaxed farm-life game.",
"Cris Tales":"Crisbell is a young orphan who learns that she has time-manipulating powers, and sets out to stop the evil Time Empress. In the game, the screen shows the past, present, and future at once, and Crisbell can change them. She travels with friends, using this power to solve puzzles and fight. It is a colorful story about change.",
"Lunar Remastered Collection":"This collection includes Lunar: Silver Star Story Complete and Lunar 2: Eternal Blue Complete. In the first, a young man named Alex dreams of becoming a hero like the legendary Dragonmaster Dyne and goes on a quest with friends. The second follows a boy named Hiro and a mysterious girl named Lucia. It is a classic pair of fairy-tale JRPGs.",
"Suikoden I & II HD Remaster":"This collection includes two JRPGs in which the hero is destined to gather the 108 Stars of Destiny, a group of fighters. In the first, a young man joins a rebellion against an empire. In the second, a boy fights a war between kingdoms. You recruit a large number of allies and fight in large battles.",
"Soulstice":"In a ruined city called Keidas, two sisters, Briar and Lute, are Chimera, a warrior and her spirit, who fight monsters called Wraiths. As they battle the horde, they uncover a conspiracy about the Order and their past. You control both at once in combat. It is a dark fantasy story about sisterhood.",
"Tales of Kenzera: ZAU":"Zau is a young shaman who is grieving the loss of his father. He bargains with Kalunga, the god of death, and has to hunt three powerful spirits to bring his father back. The game is a metroidvania inspired by Bantu mythology. It is a story about grief and acceptance.",
"Sniper Elite 4":"In 1943, Allied forces are fighting to liberate Italy from the Nazis. Karl Fairburne is an American sniper working for the OSS who is sent to stop a secret weapon. He infiltrates large open levels, using stealth and sniper skills. When he takes a shot, the game shows an x-ray view of the bullet's impact.",
"Zombie Army 4: Dead War":"In an alternate version of 1946, the Nazi leader Hitler has returned from hell with an army of undead. A group of survivors, including four main heroes, fight through Europe to stop him. The game is a cooperative shooter filled with zombies, snipers, and bosses. It is a pulpy horror story.",
"Strange Brigade":"In the 1930s, a group of British adventurers, the Strange Brigade, is sent to Egypt to stop the Witch Queen Seteki, an ancient ruler who has been awakened. The team fights through tombs, battling mummies and monsters with guns and magic. A narrator provides tongue-in-cheek commentary. It is an adventure story in the style of old pulp films.",
"Shadow Warrior 2":"Lo Wang, a wisecracking hitman, is hired to rescue a woman whose body holds a powerful secret. He travels through Japan, fighting demons and the yakuza, in a cooperative game with loot. It is a sequel with plenty of crude humor.",
"Ready or Not":"In the fictional city of Los Sueños, a SWAT team responds to dangerous situations, such as active shooters, bomb threats, and hostage-takers. You lead a team in realistic scenarios, using tactical gear and deciding whether to use force. Each mission is short and intense. It is a tense story about police work.",
"Need for Speed: Hot Pursuit Remastered":"In Seacrest County, street racers and police officers compete for control of the roads. You choose to be either a racer, trying to outrun the police, or a cop, trying to take them down. You use gadgets such as spike strips and EMPs. It is a story of cat and mouse on the open road.",
"DiRT Rally 2.0":"This is a rally racing game with no story. You drive in demanding stages in places such as Argentina, Poland, and New Zealand, with only a co-driver to guide you. You manage car damage and decide which tires and settings to use. It is a game about skill and precision.",
"LEGO City Undercover":"Chase McCain is a cop who returns to Lego City after a long absence, to take down the criminal Rex Fury, who has escaped from prison. He goes undercover in disguises, such as a robber, a farmer, and a miner. You explore an open world with vehicles and missions. It is a humorous, family-friendly adventure.",
"LEGO DC Super-Villains":"The Justice League has vanished, and a new group, the Justice Syndicate, has arrived, but they are not heroes. You create your own custom villain and team up with DC villains like the Joker and Harley Quinn to stop them. The game is a LEGO adventure with humor and a wide cast.",
"LEGO Jurassic World":"The game retells the stories of the first four Jurassic films, in which scientists create dinosaurs and a theme park goes wrong. You play as characters like Dr. Alan Grant and Owen Grady, solve puzzles, and escape from dinosaurs. It is a family-friendly adaptation with a lot of humor.",
"LEGO The Incredibles":"This game follows the stories of the two Incredibles films, in which a family of superheroes deals with villains and everyday life. You play as members of the family, such as Mr. Incredible and Elastigirl, using their powers to solve puzzles and fight. It is a LEGO adventure for all ages.",
"LEGO Worlds":"This is a sandbox game in which you create worlds from LEGO bricks. You can build, explore, and discover creatures and objects. There is no fixed story, only goals, such as collecting golden bricks. It is a game about imagination.",
"Marvel vs. Capcom Fighting Collection: Arcade Classics":"This collection includes seven fighting games in which Marvel heroes, such as Spider-Man, and Capcom characters, such as Ryu, battle each other. The games include X-Men vs. Street Fighter and Marvel vs. Capcom 2. It features online play. It is a nostalgic crossover.",
"Bully":"Jimmy Hopkins is a rebellious 15-year-old who arrives at Bullworth Academy, a boarding school full of cliques and bullies. He attends classes, plays pranks, and makes friends, while working his way up the social ladder. The game is an open-world story about school life. It is a comedic coming-of-age tale.",
"The Warriors":"Based on the 1979 film, the Warriors are a gang from Coney Island who are framed for the murder of the leader of the city's largest gang, Cyrus. They must fight their way across New York City, from the Bronx back to their home turf. You brawl with other gangs. It is a gritty story of survival.",
"Red Dead Revolver":"Red Harlow is a young boy whose parents are murdered by a corrupt colonel. Years later, he becomes a bounty hunter, hunting the people responsible. He travels across the Wild West, in a series of shootouts and duels. It is a classic western revenge story.",
"Crash Team Racing Nitro-Fueled":"Nitros Oxide, an alien, arrives on Earth and challenges its fastest racers to a race, threatening to turn the planet into a parking lot if he wins. Crash Bandicoot and friends, such as Coco and Dr. Neo Cortex, join the race. You drive through colorful tracks, using power-ups. It is a lighthearted racing adventure.",
"Jak II":"Jak and his friend Daxter are sent through a portal to a dark future version of Haven City, ruled by Baron Praxis. Jak is captured and experimented on, which gives him a dark side, and he spends two years in prison. When he escapes, he joins an underground resistance to take down the Baron. It is a darker adventure with vehicles and guns.",
"Dicey Dungeons":"Lady Luck, a living die who runs a game show, turns you into a die and traps you in her dungeon, promising to grant a wish to whoever survives. You pick a character such as the Warrior or the Witch, each of whom has a different way of playing, and work through floors of monsters. In each fight, you roll dice and place them in equipment slots to attack or defend. It is a fast, funny story about survival, with the characters' wishes being revealed.",
"Wargroove":"In the fantasy world of Wargroove, kingdoms like Cherrystone, Felheim, and the Heathens fight for control, and each is led by powerful commanders. In the campaign, you play as Mercia, the heir of Cherrystone, who goes to war to defend her kingdom after her mother's death. You move units on a grid, capture cities, and use special commander powers in turn-based battles. It is a charming war story told with a light touch.",
"Shantae: Half-Genie Hero":"Shantae is a half-genie who protects Scuttle Town and uses her hair as a whip, and her magic belly-dancing lets her transform into animals. When her nemesis, the pirate Risky Boots, steals an invention, Shantae must stop her with the help of friends. She moves through colorful levels, collects gems, and unlocks new dances. It is a lighthearted adventure with plenty of humor.",
"Shantae and the Seven Sirens":"Shantae travels to a faraway island with other half-genies to celebrate a festival, but her friends are suddenly kidnapped by seven sirens. She dives into the depths of the ocean and an underwater world, fighting monsters and solving puzzles. Her transformation dances help her explore. The story is a breezy, humorous quest to save her friends.",
"Monster Boy and the Cursed Kingdom":"Jin is a young boy whose uncle has been turned into a pig by a cursed wizard, and who must travel the kingdom to break the spell. Along the way, he gains the ability to turn into a pig, a snake, a frog, a lion, and a dragon. Each form opens up new areas and puzzles. It is a charming fairy tale in a colorful world.",
"Wonder Boy: The Dragon's Trap":"After defeating a dragon, a hero is cursed by its dying breath and turned into a lizard-man. To undo the spell, he travels through a world of monsters, towns, and caves, defeating five dragons. Along the way, he gets turned into a mouse, a piranha, a lion, and a hawk, with each form offering new powers. It is a classic fairy-tale adventure.",
"Wonder Boy: Asha in Monster World":"Asha is a young woman from a kingdom who is called to become a warrior and help fight monsters. She befriends a small flying creature called Pepelogoo, who helps her reach new places and solve puzzles. Together, they travel through jungles, deserts, and towns to stop a threat to the world of Monster World. It is a bright, cheerful action-adventure.",
"The Messenger":"A young ninja is chosen to carry a scroll across a dangerous world, to deliver it to a mountaintop, as a demon army attacks his village. As he travels, he learns that the world is far more complicated, and that he can travel through time. He leaps through levels with a sword and a rope dart. It is a funny, surprising story that blends 8-bit and 16-bit styles.",
"Wandersong":"You play as a cheerful bard who wants to be a hero after hearing a prophecy that the world will end. With no combat skills, the bard uses songs to talk with people, solve puzzles, and open doors. He journeys across the land to find magical songs that can save the world. It is a heartfelt, comedic story about hope and kindness.",
"VA-11 Hall-A: Cyberpunk Bartender Action":"Jill is a bartender at a bar called VA-11 Hall-A in Glitch City, a dystopian city filled with corporations, robots, and criminals. Each night, customers come in with stories and problems, and you mix drinks according to their requests. Your conversations and drinks shape the evening's dialogue and Jill's relationships. It is a slice-of-life story about ordinary people in a hard world.",
"Paradise Killer":"Lady Love Dies is an investigator who has been called to solve the murder of the island's ruling council, called the Syndicate, in a surreal paradise island run by immortals. She interviews suspects, collects evidence, and decides who to put on trial. The island is full of strange rituals and sacrifices. It is a colorful, detective story with a vaporwave style.",
"Thimbleweed Park":"In 1987, a body is found in a dry riverbed outside the small town of Thimbleweed Park, and two FBI agents, Ray and Reyes, are called in to investigate. They meet a clown, a game developer, a ghost, and a young woman who are all connected to the murder. Switching between five characters, you explore the town and solve puzzles to uncover a larger conspiracy. It is a retro-style mystery with humor.",
"Fez":"Gomez is a creature who lives in a 2D world, until a mysterious artifact called the hexahedron shatters, and he discovers that his world has a third dimension. Given a fez hat, he learns to rotate the world to reveal hidden paths. He collects cubes to restore the hexahedron and reveal secrets. It is a puzzle-filled adventure with a mystery that goes beyond the surface.",
"Anthem":"Humans on a planet are protected by Freelancers, who fly and fight in powered exosuits called Javelins. When a group called the Dominion tries to take control of an ancient power source, the Freelancers defend the city of Fort Tarsis and the surrounding wilds. You team up with friends to take on missions. It is a cooperative action game set in a sci-fi frontier.",
"Flower":"You play as the wind, guiding a single flower petal through fields, floating in the breeze to touch other flowers and gather more petals. Each level begins in a dream of a flower in a gray city apartment, and as you progress, you bring color to the landscape. There are no words, only music and visuals. It is a peaceful, wordless story about nature and cities.",
"Far Cry New Dawn":"Seventeen years after a nuclear war, Hope County, Montana, has recovered with wildflowers and wildlife, and now a gang of raiders called the Highwaymen, led by twin sisters Mickey and Lou, is attacking settlements. You play as the Captain, a leader who must rebuild a community and fight back. You liberate outposts and craft weapons from scrap. It is a colorful, post-apocalyptic adventure.",
"Dandara":"Dandara is a heroine in a world called Salt, which has lost its freedom to an oppressive force. She can leap between surfaces, rather than walk, to reach new places. As she travels, she frees the world and her allies, in a story inspired by a Brazilian folk hero. It is a stylish metroidvania about rebellion.",
"CrossCode":"Lea is a young woman who wakes up in the virtual world of CrossWorlds, an online game, with no memory and unable to speak. She explores the game's world, solves puzzles, and fights monsters to uncover her past and why she is there. The game plays like a retro action RPG with a story that reaches beyond the screen. It is a mystery about identity.",
"Coromon":"In a world where people catch and train creatures called Coromon, a young trainer sets out on an adventure and finds a mysterious threat. The trainer travels through islands, battles other trainers, and collects Coromon with different strengths. Along the way, they meet characters who guide them. It is a classic monster-taming adventure.",
"Monster Sanctuary":"You are a Monster Keeper, who can befriend and train monsters, in a world where humans and monsters live in peace. A mysterious force called the Alchemists has appeared, and a legendary monster has awakened. You travel through the world, forming a team of monsters and using their abilities to progress. It is a story about cooperation between humans and monsters.",
"Shadow Tactics: Blades of the Shogun":"In 1615, after years of civil war, the Tokugawa shogunate has united Japan, and a mysterious rebel is plotting a revolt. The shogun's spymaster assembles five specialists, including a samurai, a ninja, a master of disguise, a sniper, and a trapper, to stop him. You control each of them, using their unique skills to sneak through enemy bases. It is a tense stealth-strategy story.",
"Warhammer 40,000: Mechanicus":"In the far future, the Adeptus Mechanicus is a religious order of tech-priests who worship machines. Magos Dominus Faustinius leads an expedition to a tomb world, Silva Tenebris, where a long-sleeping army of undead robots, the Necrons, is awakening. You manage resources and command troops in turn-based battles. It is a dark story about faith in machines.",
"Warhammer: Chaosbane":"The Empire, a human kingdom in a dark fantasy world, is invaded by the armies of Chaos, led by a dark prince. Four heroes, a human soldier, a dwarf, an elf, and a wizard, take up arms to defend their land. They fight hordes of enemies in dungeons and cities. It is a hack-and-slash adventure with a grim tone.",
"Warhammer 40,000: Inquisitor - Martyr":"In a grim far-future empire, an Inquisitor is an agent with the power to hunt heretics, traitors, and demons. You choose a class and explore the Caligari Sector, where a mysterious ship, the Martyr, holds secrets. You fight cultists and monsters, collecting loot. It is a story of the endless war of the Imperium.",
"Torchlight II":"An Alchemist, who was a hero in the first game, has been corrupted by the mysterious power of Ember and is destroying the world. You pick one of four heroes, such as an Outlander or a Berserker, and travel through towns, dungeons, and forests to track him down. You have a pet that fights with you and carries loot. It is a lighthearted fantasy adventure.",
"Victor Vran":"Victor Vran is a demon hunter who arrives in the gothic city of Zagoravia to find a friend, and finds it overrun with demons. He travels through its streets and dungeons, using different weapons and fighting enemies in an action RPG. A narrator provides dark humor. It is a gothic adventure with rock music.",
"Baldur's Gate: Dark Alliance":"Three adventurers, a human archer, a dwarf fighter, and an elven sorceress, arrive in the city of Baldur's Gate in the Forgotten Realms. They are drawn into a plot involving a sinister cult, bandits, and an ancient evil. They fight through sewers, crypts, and caves. It is a hack-and-slash adventure set in the Dungeons & Dragons world.",
"Neverwinter Nights: Enhanced Edition":"The city of Neverwinter is struck by a deadly plague called the Wailing Death, and you are a young student at the academy who is sent to find a cure. In your search, you discover that someone is behind the plague and that the situation is more dangerous than it seems. You build a party and explore dungeons. It is a Dungeons & Dragons adventure.",
"Icewind Dale: Enhanced Edition":"In a cold northern land called Icewind Dale, adventurers arrive in a settlement called Easthaven to take on work. A growing threat in the mountains brings the party into a conflict that threatens the whole region. You build and manage a party of up to six characters. It is a combat-heavy D&D adventure.",
"Planescape: Torment: Enhanced Edition":"You play the Nameless One, an immortal man who wakes up in a mortuary with scars, tattoos, and no memory of who he is. He travels through the city of Sigil, a bizarre city of many planes, to learn who he was and why he cannot die. Dialogue and choices matter more than combat. It is a story about identity and regret.",
"Sword Art Online: Alicization Lycoris":"Kirito is a young man whose mind is trapped in a virtual world called Underworld, where time moves very fast. He and his friend Eugeo travel through the world, discovering that the people of Underworld have real feelings and that the world has a dark secret. You explore a huge world and fight enemies. It is an adaptation of the anime's third arc.",
"Sword Art Online: Hollow Realization":"Kirito and his friends play Sword Art Online, a virtual-reality game where dying means death in real life. The game introduces a new area called Hollow Area, with a mysterious girl named Premiere. You explore the game's floors, fight monsters, and build relationships with other characters. It is an original story for the anime series.",
"One Punch Man: A Hero Nobody Knows":"Saitama is a hero who became so strong that he can defeat any opponent with one punch, and he is bored by the lack of challenge. In the game, you create a custom hero and join the Hero Association to fight monsters. The story follows the events of the anime, with a character who is not the main hero. It is a comedic fighting game.",
"Fairy Tail":"Natsu Dragneel is a fire wizard in the guild Fairy Tail, a group of rowdy wizards who take jobs from the people of the kingdom. He and friends like Lucy and Erza go on a mission when a dark guild threatens their home. The game follows the story of the anime with turn-based combat. It is a lighthearted adventure about friendship.",
"Black Clover: Quartet Knights":"In a world where everyone has magic, a young boy named Asta, who has no magic, dreams of becoming the Wizard King. In this game, teams of four fight in arenas using magic and swords. The game is based on the anime and features characters like Asta and Yuno. It is a team-based action game.",
"JoJo's Bizarre Adventure: All-Star Battle R":"The JoJo series follows generations of the Joestar family, who fight supernatural villains, using special powers called Stands. This game brings together heroes and villains from across the series to fight in colorful arenas. The story mode takes players through the family saga. It is a celebration of the series.",
"Star Ocean: The Divine Force":"Raymond Lawrence is the captain of a spaceship who crash-lands on a primitive planet called Aster IV, where he meets Princess Laeticia of the Aucerian Kingdom. They are both seeking answers about a mysterious energy source and who is after it. You choose which character to follow. It is a story about two worlds meeting.",
"Star Ocean: The Last Hope":"In 2087, Earth has been devastated by a world war, and humanity has only one hope: to find a new planet to live on. Edge Maverick, a young space-exploration officer, joins the crew of the Calnus on a mission. They discover new worlds and face a mysterious enemy. It is a story about the early days of space travel.",
"Secret of Mana":"Randi is a boy who finds a rusty sword in a forest and removes it from a rock, which unleashes monsters on the village. Together with a girl and a sprite, he sets off on a quest to restore the sword's power and stop an empire that wants to take over the world. You control one character in real-time combat, while friends or AI control others. It is a remake of a classic fantasy adventure.",
"Legend of Mana":"The world has been destroyed, and you play as an Artisan who can use magical artifacts to rebuild it. You place landmarks on the map, and each one opens a new story with different characters. The tales are individual stories that gradually connect. It is a storybook-like action RPG.",
"Final Fantasy IV":"Cecil Harvey is a dark knight who serves the kingdom of Baron. When the king orders him to steal crystals from other nations, Cecil begins to doubt his loyalty and is banished. He sets out to atone, becoming a paladin, and gathers friends like Kain and Rosa to stop a mysterious enemy. It is a classic story of redemption.",
"Dead Rising 4":"Frank West, a photojournalist who survived a zombie outbreak years ago, returns to Willamette, Colorado, on Christmas Eve to investigate a new outbreak. He takes on mysterious soldiers and zombies in a mall full of Christmas decorations. Almost any object can be a weapon. It is a comedic zombie story.",
"Cave Story+":"Quote is a robot soldier who wakes up in a cave on a floating island, with no memory of who he is. He meets the Mimiga, a rabbit-like people, who are being kidnapped by the Doctor. Quote must save them and uncover the truth about the island. It is a charming story with multiple endings.",
"Hitman 2":"Agent 47 is a professional assassin who works for a secret organization called the ICA. After a mission goes wrong, he tracks down a mysterious figure known as the Shadow Client, who is connected to his past. He travels to places such as Miami, Mumbai, and Colombia to eliminate targets. You choose how to complete each mission. It is a stealth sandbox with dark humor.",
"Megadimension Neptunia VIIR":"Neptune is the goddess of Planeptune, one of four nations in Gamindustri, a world modeled after the video-game industry. When a mysterious force sends her to a different dimension, she must team up with her friends to stop an enemy who threatens all dimensions. The game is full of parodies of games and consoles. It is a comedic JRPG.",
"ELEX II":"Jax, a former commander, is living a peaceful life on a planet that has been devastated by a meteor, when a new alien threat arrives. He must unite the planet's factions, including the Berserkers and the Outlaws, and uncover secrets about the invaders. With a jetpack, he can explore a large open world. It is a post-apocalyptic story about surviving a new war.",
"Hand of Fate 2":"A mysterious Dealer sits across from you, laying cards that create an adventure and the story of a quest for a hero. The cards decide where you go, what you meet, and which dangers you face. When a fight begins, you switch to action combat. It is a story about fate and choices.",
"The Gunvolt Chronicles: Luminous Avenger iX":"In a futuristic Japan, Copen is a young man who hunts the Adepts, people who have special powers. He has a weapon that lets him lock onto enemies with shots and a boost to dash. As he discovers a connection to the Adepts, he must decide whom to trust. It is a fast-paced action story with a lot of heart.",
"Yoku's Island Express":"Yoku is a dung beetle who has just become the island's postmaster on Mokumana Island. When he learns that the island's deity is in trouble, he rolls a ball and uses pinball flippers to travel across it. He meets quirky residents and collects fruit to unlock new places. It is a whimsical adventure.",
"Owlboy":"Otus is a young owl who cannot speak and lives in a village in the sky, where he is mocked for his silence. When pirates attack, he and his friend Geddy, a gunner, have to help defend the island. Otus can fly and carry others. It is a heartfelt story about courage and friendship.",
"Hotline Miami":"The year is 1989, and a nameless man in Miami wakes up to find coded messages on his answering machine, asking him to go to certain addresses. He puts on an animal mask and kills everyone inside, then returns home to the same routine. As the missions go on, reality begins to blur, and the player is left to wonder who is giving the orders and why. It is a violent, hazy crime story about guilt and obsession.",
"Hotline Miami 2: Wrong Number":"Set before and after the first game, this sequel follows several characters, including a gang of masked fans copying the first game's killer, a detective, and a soldier. Their stories overlap during a war between criminal groups and the Russian mafia in 1989 Miami. Each person reacts differently to the violence around them. It is a story about the cycle of violence and the people who get swept up in it.",
"Furi":"A man known as The Stranger wakes in a futuristic prison, kept in chains, and is freed by a rabbit-masked man who gives him a sword. To escape the floating prison, he must defeat its guardians one by one in tough duels, each with a distinct fighting style. Between battles, he walks through peaceful landscapes and learns about the prison, his past, and the Jailer. It is a story about freedom and the price of escaping.",
"Guacamelee! 2":"Juan Aguacate is a luchador, a Mexican masked wrestler, who once saved the world and is now living a peaceful life with his family. When his former ally Salvador, an alternate-universe version of himself, steals a source of power and threatens a multiverse, Juan returns to stop him. He travels between timelines, fighting skeletons and wrestling villains with his friend Tostada. It is a comedic story full of Mexican folklore and video-game jokes.",
"Mutant Year Zero: Road to Eden":"In a post-apocalyptic future, humanity has collapsed and survivors called mutants live in a refuge called the Ark. Two mutants, Dux, a duck, and Bormin, a boar, are sent into a dangerous area called the Zone to find a missing leader and a legendary place called Eden. They travel in a team, sneak around ruins, and fight in turn-based combat. It is a dark, funny story about hope in a ruined world.",
"The Banner Saga":"In a world inspired by Norse mythology, the sun has stopped moving across the sky, and an ancient enemy, the Dredge, has returned. Humans and giants, called varl, are forced to leave their homes and travel in caravans through dangerous lands. You lead a group of characters, make choices that affect morale and supplies, and fight turn-based battles. Characters you lose don't come back.",
"The Banner Saga 2":"The second chapter continues from the first, with the caravans continuing their long trek through a world that is falling apart. The group's leaders must decide whom to trust, how to feed their people, and how to deal with a darkness spreading across the land. Choices from the first game carry over and affect who is available. It is a bleak, emotional chapter in the Viking-inspired saga.",
"Fate/Samurai Remnant":"In the 1650s Edo, Miyamoto Iori is a young masterless samurai who is pulled into a deadly competition called the Waxing Moon Ritual, in which seven masters summon legendary heroes as servants to fight for a wish-granting relic. Iori's partner is a mysterious swordswoman who goes by Saber. Together they fight enemies in the streets of Edo while he looks for meaning in the fight. It is a historical fantasy that mixes real period details with magical battles.",
"Berserk and the Band of the Hawk":"Guts is a lone swordsman who wields a massive blade and fights for hire in a medieval-style world. He joins the Band of the Hawk, a mercenary group led by the charismatic Griffith, who has a dream of building his own kingdom. The story follows their rise through wars, rivalries, and a friendship that will have devastating consequences. It is based on a famous dark fantasy manga.",
"Cloudpunk":"Rania is a young woman who takes a job as a delivery driver in Nivalis, a rainy, neon-lit megacity where the rich live in the high floors and the poor are below. She drives a flying car and has a dog, Camus, as her AI companion. Each delivery takes her to a new location, bringing her face to face with people, secrets, and a corporation. It is a slow, atmospheric story about loneliness and class.",
"Deliver Us Mars":"Kathy Johansen is an astronaut who, years ago, was involved in a mission that saved Earth's population. Now, she's one of the few who suspect that a group of colonists who stole the ships and left for Mars hold the key to humanity's future. She follows them to the red planet, exploring abandoned bases and solving puzzles with a robot. The story is about duty, family, and what we owe the world.",
"Deliver Us the Moon":"In the near future, Earth's resources are running out and the world's survival depends on a new energy source on the Moon. When contact with the lunar station is lost, an astronaut is sent on a one-way mission to find out what happened. Alone with a floating robot, the astronaut explores the silent base, solves puzzles, and learns the truth about the energy source and its creators. It is a quiet science-fiction mystery.",
"Layers of Fear 2":"An actor boards an ocean liner to shoot a film in which he plays the lead role, directed by a mysterious man known as the Director. As the ship's corridors shift and reality bends, the actor questions what is real and what is part of the performance. He wanders through rooms that change around him, encountering strange imagery and memories. It is a psychological horror about identity and performance.",
"Maid of Sker":"In 1898, Thomas Evans receives a letter from his fiancée, Elisabeth Williams, who works at the remote Sker Hotel on the coast of Wales, begging him for help. When he arrives, he finds the hotel full of twisted, noise-sensitive creatures, and he must sneak through it with no weapons. He searches for Elisabeth while learning about the hotel's dark history and a mysterious song. It is a gothic horror based on Welsh folklore.",
"Tom Clancy's Ghost Recon Wildlands":"The Santa Blanca cartel has taken over Bolivia, with its ruthless leader, El Sueño, making the country a narco-state. A four-person team of U.S. special forces, the Ghosts, is sent in to take down the cartel, piece by piece, starting with the lieutenants. You are free to approach missions however you like, and you can play with friends. The story follows the squad as they uncover who is behind the cartel.",
"Rime":"A young boy washes ashore on a mysterious, sunlit island, with no memory of how he got there. With a small fox as a guide, he explores ruins, solves puzzles, and avoids a menacing red-robed figure. The island seems to hold memories and a hidden meaning. With no dialogue, the game tells a quiet story about grief and acceptance.",
"Red Faction: Guerrilla Re-Mars-tered":"In the 22nd century, Mars is colonized by Earth, and the Earth Defense Force runs the planet with an iron fist. Alec Mason, a miner who arrives to work, ends up joining the Red Faction, a group of rebels that fights the EDF. With a sledgehammer and explosives, he destroys buildings and bridges to free Mars. It is an action story about rebellion and the destruction of an occupying power.",
"Thief":"Garrett is the best thief in the City, a dark, plague-stricken town ruled by a harsh Baron. After a job goes wrong and he loses a year of his memory, he returns to find the city changed and a mysterious supernatural force known as the Gloom spreading. He sneaks through shadows to steal valuables, avoiding guards and using gadgets. It is a stealth-heavy story about trust and survival.",
"Styx: Shards of Darkness":"Styx is a sarcastic goblin thief who sneaks into a human kingdom to steal valuable items in the middle of a war between elves, dwarves, and humans. He climbs across dark fortresses, avoiding guards, and uses special abilities to stay hidden. He is offered jobs by various factions, which makes him deal with the secrets of the world. It is a witty, stealth-based fantasy.",
"Mirror's Edge Catalyst":"Faith Connors is a courier called a Runner who delivers messages across the rooftops of Glass, a futuristic city ruled by corporations. After leaving prison, she joins a group of rebels to take on the powerful company KrugerSec and uncover a conspiracy. The game focuses on first-person parkour and free-running. It is a story about freedom and resisting control.",
"Bastion":"A young man known as the Kid wakes up after a disaster called the Calamity has shattered his world, Caelondia. He travels to a floating refuge called the Bastion and fights through the ruins, gathering the shards to restore it. A gruff narrator comments on everything that happens. It is a story about loss, forgiveness, and a world that cannot be put back together.",
"Transistor":"Red is a singer in the futuristic city of Cloudbank, who is attacked by a group called the Camerata. She escapes with a mysterious sword, the Transistor, which houses the voice of someone close to her. Together, they use its powers to fight robotic enemies, trying to understand the city's collapse. It is a stylish, melancholy story about identity and art.",
"Pyre":"You are a Reader, an exile in a fantasy world called the Downside, who is taken in by a group of outcasts. They try to earn their freedom by competing in magical three-on-three matches called Rites, with only the winning team's members allowed to go home. Over time, your choices shape which of your companions are freed. It is a story about community and what freedom means.",
"Darksiders Genesis":"The Charred Council, a group of cosmic judges, sends War and Strife, two of the Four Horsemen of the Apocalypse, to stop the demon Lucifer's plan to unleash a catastrophe. The two travel through Hell and across the world, fighting demons while bickering. Their different personalities, War's strength and Strife's guns, drive the humor. It is an action story that fills in the origins of the horsemen.",
"Hob":"A small hero named Hob wanders into a strange land and is hit by a creature, which leaves him with a giant mechanical arm. The land is full of shifting stone and machinery, which Hob can restore and reshape. With no dialogue, he explores to heal a world that is falling apart. It is a wordless adventure about cooperation with nature.",
"Child of Light":"Aurora, a young girl in 1895 Austria, falls into a coma and awakens in Lemuria, a fairy-tale world where the Queen of the Night has taken the sun, moon, and stars. She teams up with a firefly, Igniculus, and others to retrieve them and find a way home. The story is told in rhyming verse. It is a painted fairy tale about courage.",
"Valiant Hearts: The Great War":"In 1914, World War I breaks out, and four strangers are caught in the conflict: Emile, a French farmer; Karl, his German son-in-law; Freddie, an American; and Anna, a Belgian nurse. Along with a loyal dog, Walt, they struggle to survive and find their loved ones. The game mixes puzzles with real wartime facts. It is a moving anti-war story about ordinary people.",
"Beyond Good & Evil 20th Anniversary Edition":"Jade is a young photographer and caretaker of orphans on the planet Hillys, which is under attack from aliens called the DomZ. When she discovers that the army that protects the planet is working with the aliens, she joins a resistance group and uses her camera to find proof. She is joined by her uncle, Pey'j, and others. It is an adventure about uncovering lies and standing up to power.",
"The Technomancer":"Zachariah Mason is a Technomancer, a warrior who can control electricity, on Mars. The planet has been colonized by humans, but its resources are controlled by powerful corporations, and Technomancers are loyal to one of them. After uncovering a secret about his order, Zachariah is forced to decide between loyalty and rebellion. It is a story about freedom and survival in a harsh colony.",
"Bound by Flame":"Vulcan is a mercenary whose group is hired to protect a legendary fortress from invading armies. During a ritual, he becomes possessed by a fire demon, which gives him new powers but threatens to take over his mind. He travels the land, makes allies, and chooses whether to embrace the demon's power. It is a fantasy RPG about temptation and the cost of power.",
"Death's Gambit":"Sorun is a warrior who is granted a second life by Death in exchange for service. He is sent to the strange land of Siradon to hunt down the Immortals, powerful beings who have stolen their way to eternal life. He fights bosses and explores gloomy regions, collecting memories. It is a hard-hitting story about mortality and the fear of death.",
"Knack":"Knack is a small robot-like creature created from ancient relics by Dr. Vargas, who can absorb more relics and grow to giant size. Humanity is at war with goblins, who have developed advanced weapons. Knack joins a team to stop the goblins, only to uncover a conspiracy within the human side. It is a family-friendly adventure about heroism and trust.",
"Nights of Azure 2: Bride of the New Moon":"Aluche is a half-human, half-demon girl who is called a Moon Maiden, destined to be a bride who must be sacrificed to seal away a monster. When her friend Liliana is chosen, Aluche decides to protect her instead of letting her die. They fight monsters together, using summoned beasts. It is a dark fantasy about love and defying destiny.",
"Atelier Sophie: The Alchemist of the Mysterious Book":"Sophie is a young woman who loves alchemy, though she is not very good at it. One day, she finds a magical book that can speak, named Plachta, who has lost her memories. Sophie sets off to help Plachta recover them by making potions, items, and tools. It is a gentle, cozy fantasy about friendship and growing up.",
"Star Ocean: First Departure R":"Roddick is a young swordsman in a medieval-looking village on the planet Roak, which is hit by a mysterious plague. He meets Millie and Ronyx, travelers from space who reveal that Roak is not alone, and that they are part of a larger galaxy. They travel across the world to find the cause of the plague. It is a story mixing fantasy and science fiction.",
"Lost Sphear":"Kanata is a teenage boy who discovers that he can restore things that have vanished into nothingness, a phenomenon spreading through the world. With his friends, he travels to find out why it's happening and how to stop it. The cost of using his power is growing. It is a nostalgic JRPG about memory and loss.",
"I am Setsuna":"In a snowy land, a young girl named Setsuna has been chosen as a sacrifice to calm the monsters that plague the world. The mercenary Endir is hired to kill her but ends up protecting her. They travel to a distant temple, while Setsuna accepts her fate and tries to enjoy her last days. It is a quiet, sad story about sacrifice.",
"Greak: Memories of Azur":"Greak, Adara, and Raydel are siblings in the land of Azur, who must work together to escape a fearsome invasion by the Urlags. Each sibling has unique skills, and the player switches between them to solve puzzles and fight. As they look for a way to protect their family and home, they face the invaders. It is a charming, hand-drawn adventure about family.",
"Kingdom Two Crowns":"You play a monarch who rides a horse across a side-scrolling land, collecting coins and spending them to recruit subjects and build defenses. Each night, creatures called the Greed attack, and you must protect your people and the crown. As you build, you discover new lands. It is a calm, minimalist game about building and protecting a kingdom.",
"The Last Campfire":"Ember is a lost wanderer who finds himself in a mysterious place called the Forgotten Hollow, where others are stuck in a state of hopelessness. As he travels, he helps others by solving puzzles that reflect their inner struggles. Along the way, he discovers a path to finding his own way. It is a gentle story about hope.",
"Rez Infinite":"In the 21st century, a hacker dives into Eden, an AI system that has become overwhelmed. Moving through levels in a wireframe cyberspace, the hacker shoots viruses and firewalls, with each shot creating music and visual effects. The goal is to wake the AI and restore the system. It is an abstract, music-driven journey.",
"Gorogoa":"A boy in a mysterious world tries to find a giant that he sees, and chases it through his life. You play by moving, zooming, and combining four panels of hand-drawn images. As you connect them, the boy goes through changing scenes. The ending reveals a meaning behind the search. It is a story about obsession, faith, and time.",
"Machinarium":"Josef is a small robot who has been thrown into a junkyard outside a robot city. He travels back to the city, trying to rescue his girlfriend, Berta, from the Black Cap Brotherhood, who threaten to blow up the city's tower. He solves puzzles using his extendable body. It is a wordless, hand-drawn story about courage.",
"Grim Fandango Remastered":"Manny Calavera is a Grim Reaper and a travel agent in the Land of the Dead, who sells travel packages to the recently deceased for their journey to the afterlife. When he discovers that his clients are being cheated, he sets off to find out why, working with a woman named Mercedes. It is a noir adventure inspired by Mexican folklore.",
"Day of the Tentacle Remastered":"The mad scientist Dr. Fred has created a purple tentacle that wants to take over the world. Three friends, Bernard, Hoagie, and Laverne, use a time machine to stop it, but they get sent to the past, present, and future. They solve puzzles that affect each other's time periods. It is a classic comedy adventure.",
"Full Throttle Remastered":"Ben is a tough biker leader of the Polecats, who gets mixed up in a murder involving Malcolm Corley, the founder of the last motorcycle company in the U.S. He is framed for the crime and has to clear his name while stopping a plot to turn the company into a van manufacturer. It is a gruff, funny road story.",
"Broken Age":"Two teenagers, Vella and Shay, live in different worlds. Vella is chosen to be sacrificed to a monster, and Shay is on a spaceship, living a repetitive routine. Both decide to break from their lives, and as they do, their stories begin to connect. It is a hand-painted adventure about growing up and rebelling.",
"Everybody's Gone to the Rapture":"It's 1984 in Yaughton, a peaceful English village in Shropshire, and everyone has vanished without a trace. You wander the empty streets, cottages, and fields as an unseen presence, following glowing lights that replay conversations between the missing villagers. Through these echoes, you learn about their lives, fears, and relationships, and about a scientific mystery linked to a nearby observatory. There is no combat, only exploration, as you piece together what happened and why.",
"The Vanishing of Ethan Carter":"Paul Prospero, a detective with supernatural abilities, travels to Red Creek Valley, Wisconsin, after receiving a letter from a boy named Ethan Carter asking for help. When he arrives, he finds the valley empty and signs that something terrible happened to Ethan's family. By finding clues and using his psychic power to see how the dead were killed, he pieces together each event. The story slowly reveals an eerie truth about Ethan and the valley.",
"Limbo":"A nameless boy wakes up in a dark, misty forest and sets out to find his sister. The world is drawn in black and white, with no dialogue, and filled with deadly traps, giant spiders, and eerie industrial structures. You solve puzzles, jump across hazards, and often die in surprising ways before finding the right solution. The ending is left open to interpretation.",
"Unravel":"Yarny is a small creature made of red yarn, created from a loose thread by an elderly woman. When Yarny finds her photographs scattered across Scandinavian-inspired landscapes, each one opens a memory from her life. By using the thread, Yarny swings, ties, and pulls objects to solve puzzles, leaving a trail of yarn. The story is a gentle reflection on family, loss, and the bonds that connect people.",
"Last Day of June":"Carl, a painter, and June, his wife, spend a happy day together on their anniversary in a sleepy village, but a car accident leaves June dead and Carl in a wheelchair. Haunted by his loss, Carl finds he can relive the day through the eyes of the villagers connected to the accident. By changing small details, he tries to prevent the tragedy, but each change has consequences. It is a wordless story about grief and the cost of altering fate.",
"Sea of Solitude":"Kay is a young woman who has become a monster because of her loneliness, and she wakes up in a flooded, ruined city. She travels in a small boat, meeting creatures that represent her fears, her family, and her struggles with anxiety and relationships. As she learns what happened, she must face the people she has hurt and decide how to change. It is an emotional story about mental health and connection.",
"Stranger of Paradise: Final Fantasy Origin":"Jack Garland, an intense warrior with one goal, is determined to defeat Chaos, a mysterious force that threatens the kingdom of Cornelia. He teams up with two other fighters, Ash and Jed, who each carry a fragment of a crystal, as they investigate and fight through a world of monsters. As they travel, Jack's past and his obsession come into question. It is a darker retelling of the first Final Fantasy, with a focus on combat.",
"Final Fantasy Type-0 HD":"The nation of Rubrum is at war with the powerful Militesi Empire, and each of the four nations is protected by a crystal. You control Class Zero, a special group of students at the Akademeia, who are sent on missions to defend their home. As the war grows, they face betrayal, impossible choices, and the cost of their power. The story is a grim look at war and sacrifice, told with a large cast of characters.",
"Biomutant":"In a post-apocalyptic world, the Tree of Life, the source of nature, is dying, and world-eaters are gnawing at its roots. You play a small, furry mutant who sets out to save the tree and avenge a family tragedy, deciding which of six tribes to unite or destroy. The world is narrated, and your choices affect whether your character becomes a hero or a villain. Combat is a mix of martial arts, guns, and mutations.",
"Remothered: Tormented Fathers":"Rosemary Reed is a middle-aged woman who visits the Felton mansion in Italy at night to seek answers about her adopted daughter's disappearance. Inside, she finds Dr. Felton, an elderly man who is hiding secrets, along with his wife, Gloria, and a hooded stalker. With no way to fight, she must hide, use distractions, and sneak around the house to survive while learning what happened years before. The story is a slow-burn psychological thriller.",
"Amnesia: The Dark Descent":"In 1839, Daniel wakes up in the shadowy Brennenburg Castle in Prussia, with no memory of how he got there, except for a letter he wrote to himself. The letter instructs him to find and kill the castle's owner, Baron Alexander, and warns him about a monstrous shadow that follows him. With no weapons, Daniel must hide from creatures in the dark while managing his sanity, which fades if he stays in the dark or watches monsters. He gradually uncovers why he was there and what he did.",
"The Sinking City":"The year is 1924, and Charles Reed, a private investigator and World War I veteran, arrives in Oakmont, Massachusetts, a city half-drowned by a mysterious flood. He is tormented by strange visions and is looking for answers about them. As he investigates disappearances and murders, he discovers that the city's powerful families and unsettling sea creatures are tied to something ancient. You must gather clues, interview residents, and decide who to trust, in a story inspired by H.P. Lovecraft's cosmic horror.",
"Call of Cthulhu":"In 1924, Edward Pierce is a private investigator haunted by his experiences in World War I and drinking heavily. A wealthy man hires him to look into the death of his daughter and her family on Darkwater Island, a remote whaling community off the coast of Massachusetts. As he digs deeper, he discovers that the islanders are hiding a dark secret, and the more he learns, the more his own sanity is threatened. The story is based on H.P. Lovecraft's cosmic horror.",
"The Dark Pictures Anthology: Little Hope":"A bus carrying four college students and their professor breaks down near Little Hope, a quiet town in New England that was abandoned after a fire and has a history of witch trials. As they wander through the empty streets, they begin to see terrifying visions and creatures from the town's past. Your choices decide which of the five characters survive and what they learn about the town's dark history. The game is a horror story about guilt and the way the past repeats itself.",
"Final Fantasy XII: The Zodiac Age":"The kingdom of Dalmasca has been conquered by the powerful Archadian Empire, and a young street thief named Vaan dreams of escape. He gets caught up in a rebellion led by Princess Ashe, who is secretly alive, along with a sky pirate, Balthier, and a knight, Basch. The group travels across a huge world, fighting the Empire's attempt to claim a powerful weapon. It is a political story about war, occupation, and what it takes to free a nation.",
"Danganronpa 1·2 Reload":"In the first game, Makoto Naegi is a normal high-school student who has been accepted to Hope's Peak Academy, a school for the world's most talented teenagers. On his first day, he and his classmates are trapped by Monokuma, a sinister robotic bear, who tells them the only way out is to murder another student without being caught. After each killing, survivors investigate and hold a class trial to find the culprit, or else everyone but the killer is executed. The second game sends a new class to a tropical island with the same rules.",
"BioShock 2 Remastered":"In 1958, Rapture, an underwater city built as a utopia for the world's elite, has collapsed into chaos. You play as Subject Delta, a Big Daddy, a hulking diving-suit-clad protector that was bonded to a girl called a Little Sister. After being forced apart ten years earlier, Delta wakes up to find her and fights through the ruined city. His path leads him to Sofia Lamb, a psychiatrist who wants to remake Rapture around her ideas of collectivism, and who is connected to his Little Sister.",
"Valkyria Chronicles":"In an alternate version of Europe, the small, peaceful country of Gallia is invaded by the powerful Empire, which wants its valuable natural resources. Welkin Gunther, a young man who loves nature, joins his town's militia with a tank, along with Alicia, a baker. Together, they lead Squad 7 against the empire's forces, with the story told as a storybook-like war drama. It explores friendship, prejudice, and the cost of fighting for your home.",
"Torment: Tides of Numenera":"A billion years in the future, you are the Last Castoff, a discarded body of a powerful being called the Changing God, who has lived for centuries by moving from body to body. Your goal is to discover who you are and what happened, while a dangerous force called the Sorrow hunts you. The world is strange and full of leftover technology that looks like magic. Dialogue and choices matter, and you can often solve problems without fighting.",
"Pillars of Eternity: Complete Edition":"You are a traveler in the land of Eora, and you are caught in a ritual that gives you the ability to perceive and speak with souls, making you a Watcher. At the same time, a plague of newborns without souls, called hollowborn, is spreading. You rally companions and explore cities, wilderness, and ruins to learn the cause and decide what to do about it. Your choices and dialogue change how people see you and what happens.",
"Wolfenstein: The Old Blood":"This prequel is set in 1946, when American soldier B.J. Blazkowicz and his friend Richard Wesley are captured by the Nazis while trying to find a document that could help the war effort. B.J. breaks out of Castle Wolfenstein and then travels to a nearby village, the Nazi-occupied town of Wulfburg. The story follows his attempt to find and destroy a Nazi's occult project, which involves digging up an ancient tomb and unleashing an undead army.",
"Pathfinder: Kingmaker":"You are a mercenary who accepts a job to clear bandits from the Stolen Lands, a dangerous frontier. When you succeed, you are granted a charter to rule the land and become a baron, then must build a kingdom while fighting threats like monsters, rival nobles, and a mysterious curse. You recruit companions, make political decisions, and develop your character in a game based on a tabletop role-playing system.",
"Assassin's Creed III":"Connor, a young man of Mohawk and English heritage, becomes an Assassin during the American Revolution to protect his people and seek revenge against the Templars. The game begins with his father, Haytham Kenway, and moves across Boston, New York, and the frontier, encountering figures like George Washington. A modern-day thread follows Desmond Miles as he nears the climax of his own journey. It's a story about freedom and the cost of revolution.",
"Assassin's Creed Unity":"In 1789, Arno Dorian, a young Assassin, is caught up in the French Revolution while searching for the truth about his adoptive father's murder. His love for Élise de la Serre, a Templar, puts him at odds with his Brotherhood. Over the course of the Revolution, Arno navigates Paris's streets, rooftops, and sewers. It's a tale of love, loyalty, and chaos.",
"Assassin's Creed Syndicate":"In 1868 London, twin Assassins Jacob and Evie Frye set out to take control of the city from Crawford Starrick, a Templar who rules through industrial power. Jacob builds a gang, the Rooks, while Evie searches for a hidden Piece of Eden. The story, set in the Industrial Revolution, balances Jacob's brashness and Evie's strategy. Famous figures like Charles Dickens and Alexander Graham Bell appear.",
"Assassin's Creed Rogue":"Shay Cormac, an Assassin in the 1750s, is disillusioned after a mission goes wrong and he joins the Templars. As a Templar, he hunts his former Brotherhood across the North Atlantic, sailing the Morrigan. The story explores his motives and the toll of choosing a side, linking to the events of Assassin's Creed III.",
"DOOM":"A space marine, the Doom Slayer, awakens on a UAC research facility on Mars, where experiments with a portal to Hell have unleashed demons. With the help of the AI VEGA and Samuel Hayden, he fights through the base and into Hell, while Dr. Olivia Pierce seeks to corrupt the energy source. The story is minimal and tongue-in-cheek, built around the Slayer's rage.",
"Rage 2":"Walker, the last Ranger, defends the wasteland after the Authority, led by General Cross, attacks. He is joined by allies in a quest to activate Project Dagger, a plan to defeat the Authority, and uses Nanotrite powers to fight. It's a colorful, over-the-top story with bandits, mutants, and vehicles.",
"Metal Gear Solid: Master Collection Vol. 1":"The collection includes Metal Gear Solid, where Solid Snake infiltrates Shadow Moses to stop terrorists with nuclear capability; MGS2, where Raiden faces a hostage crisis on a tanker and the Big Shell; and MGS3, where Naked Snake runs a Cold War mission in 1964. Together, they trace the Patriots conspiracy and the legacy of Big Boss with dense, cinematic stories.",
"Resident Evil":"S.T.A.R.S. members Chris Redfield and Jill Valentine, trapped in the Spencer Mansion after a helicopter crash, find a house full of zombies, puzzles, and secrets. As the team uncovers the truth about Umbrella Corporation and its bioweapons, they must decide who to trust, including Albert Wesker. Your chosen character shapes the story and the ending. It's the series' original survival-horror blueprint.",
"Resident Evil 0":"Rebecca Chambers, a young S.T.A.R.S. medic, investigates a derailed train in the Arklay Mountains and meets Billy Coen, an escaped convict. The two team up to survive a nightmare of infected creatures and uncover a link to the Umbrella Corporation. They eventually find their way to an abandoned training facility, where the truth is revealed.",
"Dead Rising Deluxe Remaster":"Frank West, a photojournalist, flies to Willamette, Colorado, to investigate an incident and finds the town overrun with zombies. He takes shelter in a shopping mall and has 72 hours to uncover the cause before help arrives. As he saves survivors and takes photos, Frank faces psychopaths, conspiracies, and absurd weapons. It's a darkly comic zombie story.",
"Marvel's Spider-Man Remastered":"Eight years into his career, Peter Parker juggles being Spider-Man with his job and relationships, while Wilson Fisk is arrested and a new gang war erupts in New York. A mysterious figure named Mister Negative and the return of Doctor Octavius lead to the Sinister Six. Peter's bond with MJ and Aunt May anchor the story. It's a heartfelt look at Peter's life behind the mask.",
"God of War III Remastered":"Kratos, the Ghost of Sparta, climbs Mount Olympus with the Titans to take revenge on Zeus and the gods who betrayed him. He faces gods like Poseidon, Hades, and Hercules while uncovering the secret of Pandora's Box. The story is a brutal, operatic conclusion to the Greek saga. It also sets the stage for a new beginning.",
"Shadow Warrior 3":"Lo Wang, a former corporate ninja, and his old boss Orochi Zilla are at odds over a dragon that was unleashed and now threatens the world. Lo Wang teams up with his old employer to hunt it down, running through levels using a grappling hook and sword. The story is a chaotic, crude comedy with high-energy action.",
"Resident Evil Revelations":"Jill Valentine and Parker Luciano of the BSAA are sent to investigate the Queen Zenobia, a ship that is rumored to be a base for a bioterror group. Aboard the ship, they find mutated monsters and a mystery tied to the ruined city of Terragrigia and a group called Veltro. Meanwhile, Chris Redfield and Jessica search for Jill. It's a claustrophobic, back-to-basics thriller.",
"Resident Evil Revelations 2":"Claire Redfield and Moira Burton, a new recruit, are kidnapped and wake on a remote island, outfitted with bracelets and tormented by a mysterious voice. Six months later, Barry Burton arrives on the island to find his daughter Moira, a mirror story that leads to a young girl, Natalia. The alternating episodes explore guilt, family bonds, and the roots of a bioterror plot.",
"Resident Evil 5":"Chris Redfield, now with the BSAA, travels to Kijuju, Africa, to track down a bioweapons dealer, partnering with local agent Sheva Alomar. They find villagers infected with a new parasite and a threat tied to Albert Wesker and the corporation Tricell. The trail leads to ancient ruins, a lab, and a confrontation that ties up long-running series plot lines.",
"Resident Evil 6":"The game follows four main storylines: Leon Kennedy and Helena Harper, Chris Redfield and Piers Nivans, Jake Muller with Sherry Birkin, and Ada Wong, as a new virus, the C-Virus, spreads through the world. Their campaigns overlap in cities like Tall Oaks, Lanshiang, and Edonia. It's a globe-trotting, high-action thriller about a bioterror conspiracy.",
"Mass Effect: Andromeda":"Hundreds of years after the events of the original trilogy, the Andromeda Initiative sends colonists on a one-way trip to the Andromeda galaxy to find new homes. After the arrival goes wrong, Sara or Scott Ryder inherits the role of Pathfinder from their father, Alec. They work to make planets habitable, meeting the Angara, fighting the Kett and their leader, the Archon, and finding a lost alien technology.",
"inFAMOUS First Light":"Abigail 'Fetch' Walker, a conduit with neon powers, is imprisoned on Curdun Cay by the D.U.P. Her story begins in the years before Second Son, as she tries to free herself and her brother Brent. The narrative shifts between the island and her backstory, showing how a drug-addicted girl turned into a hero. It's a smaller, more personal story than the main game.",
"Darksiders III":"After the Apocalypse, the Charred Council sends Fury, the third horseman, to hunt the Seven Deadly Sins, who have been released on Earth. Fury journeys through a ruined city, defeating each Sin as she faces her own flaws. The story is darker and more personal than before, and sets Fury apart from her brothers.",
"Zero Escape: The Nonary Games":"This collection includes two visual novels, Nine Hours, Nine Persons, Nine Doors and Zero Escape: Virtue's Last Reward. In both, strangers are abducted by a masked figure called Zero and forced to play a deadly game of puzzle rooms and moral dilemmas, in which trust and betrayal determine who survives. The story branches through multiple endings that gradually reveal a larger mystery.",
"Outlast 2":"Journalists Blake Langermann and his wife Lynn travel to rural Arizona to investigate a pregnant woman's murder, but their helicopter crashes near a religious community called Temple Gate, led by Sullivan Knoth. Blake is separated from Lynn and must survive a village of fanatics with only a camcorder. The story mixes survival horror with traumatic flashbacks from his past.",
"Blair Witch":"In 1996, Ellis, a former police officer with a service dog named Bullet, joins the search for a missing boy in the Black Hills Forest in Maryland. As the search continues, the woods become more disorienting, and Ellis's own war trauma emerges. The game uses the forest and its legend to tell a psychological story about guilt.",
"Fatal Frame: Maiden of Black Water":"At Mount Hikami, a mountain with a legend of ghosts, three women, Yuri, Miu, and Ren, are drawn together by a strange, water-related curse. Each uses a camera to repel the spirits, called the Camera Obscura, and uncovers the mountain's tragic past. It's a quiet, eerie ghost story rooted in Japanese folklore.",
"Back 4 Blood":"A parasite, the Devil Worm, has turned most of humanity into the Ridden, and a group of survivors called the Cleaners fights back from a base called Fort Hope. Characters like Mom, Walker, Evangelo, and Holly travel across ruined America, clearing out nests and rescuing others. It's a team-based zombie story told through banter.",
"Evil West":"In the 1890s American West, Jesse Rentier, a hunter employed by the Rentier Institute, battles a supernatural threat of vampires led by a figure known as the Sanguinar. With a mechanical gauntlet and an arsenal, Jesse and his allies face monsters in towns and mines. It's a pulpy, humor-laced western adventure.",
"Far Cry Primal":"In 10000 BCE, Takkar, a hunter of the Wenja tribe, arrives in the valley of Oros after the loss of his people. He rebuilds his tribe and fights the rival Udam and Izila, taming beasts like mammoths and saber-toothed cats. The story is a survival tale in a prehistoric world with a made-up language.",
"Killing Floor 2":"Set after a disastrous experiment by Horzine Biotech, Europe is overrun with mutated clones called Zeds. Mercenaries and civilians fight against waves of Zeds, culminating in a battle with Dr. Hans Volter. The story is told through objectives and bits of context rather than a campaign.",
"Final Fantasy VII":"Cloud Strife, an ex-SOLDIER mercenary, joins the eco-terrorist group AVALANCHE to take on the Shinra Electric Power Company, which is draining the planet's life energy. As the group travels from Midgar across the world, they cross paths with Aerith, Tifa, and the legendary SOLDIER Sephiroth, whose plan threatens the planet. It's a story of identity, loss, and hope.",
"Final Fantasy VIII Remastered":"Squall Leonhart, a cadet of Balamb Garden, is a lone mercenary-in-training, and joins an elite force called SeeD. His team gets entangled in a war against a powerful sorceress, and he forms a bond with Rinoa. The story is a romance and a coming-of-age tale in a world of time-bending magic.",
"Final Fantasy IX":"Zidane, a charming thief, kidnaps Princess Garnet of Alexandria, who is secretly seeking to escape from the throne. Along with a group including Vivi and Steiner, they travel through a world where the queen's war and a mysterious figure named Kuja threaten the balance. It's a heartfelt story about identity and what it means to live.",
"The Wolf Among Us":"In 1986 New York, storybook figures known as Fables live in a hidden neighborhood called Fabletown, and Bigby Wolf, the Big Bad Wolf turned sheriff, enforces the law. When a Fable is found murdered, Bigby investigates a conspiracy involving the Crooked Man, a powerful gangster, and a city's grim underworld. Your choices change whether Bigby is a brute or a better man. It's a hard-boiled noir with fairy-tale twists.",
"The Walking Dead: The Telltale Definitive Series":"In the first season, Lee Everett, a convicted man freed in the outbreak, protects a young girl named Clementine in Georgia. Later seasons follow Clementine as she grows up and faces ever-harsher choices, and include side stories like 400 Days and Michonne. Decisions about who to save and trust carry forward, and the games are about morality and found family in a collapsing world.",
"Tales from the Borderlands":"Rhys, a Hyperion employee, and Fiona, a Pandoran con artist, tell conflicting stories about how they got involved in a quest to find a Vault key. As both narrators embellish and interrupt each other, the story follows their misadventures across Pandora with robots, bandits, and a friendly AI. It's a funny, heartfelt caper about friendship and second chances.",
"Batman: The Telltale Series":"Bruce Wayne supports Harvey Dent's run for district attorney while Batman fights Gotham's crime, until a conspiracy involving the Wayne family's past comes to light. Oswald Cobblepot and the group Children of Arkham are among those who challenge him. You choose how Bruce and Batman respond, affecting relationships with allies and enemies. It's a story about legacy and the man behind the mask.",
"Life is Strange 2":"After a tragic incident, brothers Sean and Daniel Diaz flee Seattle and head toward Mexico, hunted by authorities. Along the way, Daniel develops telekinetic powers that Sean must help him control. Sean's choices, as an older brother and role model, affect the way Daniel turns out. It's a road-trip drama about family, prejudice, and responsibility.",
"Life is Strange: Before the Storm":"Set three years before the original, sixteen-year-old Chloe Price meets Rachel Amber, a popular student, and the two form a deep friendship. As they skip class and explore Arcadia Bay, Chloe deals with the loss of her father and Rachel's family secrets. It's a tender coming-of-age story about two teenagers finding each other.",
"Life is Strange: Double Exposure":"Max Caulfield, now an adult photographer at a university, loses a friend to murder and finds her rewind power returning, along with the ability to shift between two timelines where the friend lives and doesn't. She investigates the crime in both worlds. It's a mystery about grief, secrets, and the cost of changing the past.",
"Like a Dragon: Ishin!":"In the 1860s, near the end of the shogunate, Sakamoto Ryoma, a masterless samurai, returns to Kyoto after his father's murder, hoping to find the killer. He joins the Shinsengumi, a police force, and gets involved in the turmoil between supporters of the shogun and revolutionaries. The game re-casts familiar Yakuza characters in historical roles, blending drama with samurai combat.",
"Bayonetta Origins: Cereza and the Lost Demon":"Young Cereza, a witch-in-training, wants to rescue her mother from the realm of Inferno and so enters the Avalon Forest. There she makes a pact with a demon, Cheshire, who is trapped in a stuffed cat, and the two have to cooperate despite their differences. You control both at once, solving puzzles and fighting fairy-tale monsters. It's a charming storybook origin of the series' witch.",
"Syberia: The World Before":"Kate Walker, an American lawyer, travels to Eastern Europe in 2004, while a second thread follows Dana Roze, a pianist, in 1937 Vaghen. The two stories are linked, and the game alternates between them, uncovering secrets about identity and history. It's a puzzle-heavy adventure with a mood of political tension and personal loss.",
"Dishonored: Death of the Outsider":"Billie Lurk, a former assassin from the Dishonored series, and her mentor Daud travel to Karnaca with a plan to kill the Outsider, the mysterious figure who grants supernatural powers. As they uncover the Outsider's origins, Billie must decide what to do with her own past. It's a standalone stealth tale about fate and redemption.",
"Uncharted: Legacy of Thieves Collection":"Includes Uncharted 4: A Thief's End, where retired treasure hunter Nathan Drake is pulled back in by his long-lost brother Sam to find pirate Henry Avery's hidden treasure, and The Lost Legacy, where Chloe Frazer and Nadine Ross hunt the Tusk of Ganesh in India. Together they close out Nate's story and give Chloe a spotlight. It's a cinematic pair of adventures.",
"Vanquish":"In the near future, Russian ultranationalists seize an American space station and use its microwave weapon to attack San Francisco. DARPA agent Sam Gideon, wearing a prototype suit, is sent to stop them with Marine support. The story is a fast-paced, over-the-top action movie, with a focus on style and speed.",
"Abzu":"You play a diver who awakens in a vibrant ocean full of fish, coral, and ruins. As you explore, you uncover ancient technology and a vast sea creature tied to the world's origins. There's no dialogue, so the story is told through visuals and music. It's a meditative journey about nature and the cycle of life.",
"GreedFall":"De Sardet, a diplomat, is sent to the island of Teer Fradee to find a cure for a deadly plague called the malichor. There, De Sardet deals with colonists, natives, and magical secrets, with choices that affect factions and companions. It's an RPG about colonialism and the clash of cultures.",
"Horizon Call of the Mountain":"Ryas, a former soldier turned outlaw, is offered a pardon in exchange for investigating a series of machine attacks on a Carja settlement. He climbs mountain ruins and confronts the Horizon universe's robot creatures, learning the truth about the threat. It's a VR-focused story about redemption and trust.",
"Sherlock Holmes: Chapter One":"A young Sherlock Holmes returns to the island of Cordona with his friend Jon, where his mother is buried. When the governor is murdered, he investigates, using deduction and observation. The story gives a glimpse of the detective before he becomes famous and deals with his family's past.",
"Elex":"Jax, a former commander of the technologically advanced Albs, is abandoned by his own side and left for dead. He recovers on Magalan, a post-apocalyptic land struck by a meteor, and must choose among factions like the Berserkers, Clerics, Outlaws, and Albs. The story revolves around a precious substance called Elex and the struggle for control over it.",
"Forza Horizon 5":"There's no deep plot here; the story is the Horizon Festival itself, which expands to Mexico and lets you rise from rookie to festival star. You complete themed expeditions across jungles, deserts, and volcanic mountains, and each Horizon event introduces cars, culture, and music. The structure is a progression of 'Horizon Adventures' rather than a scripted narrative. It's a relaxed, celebratory take on car culture.",
"Elden Ring Nightreign":"Set in the world of Limveld, a land threatened by an encroaching night, a group of Nightfarers must work together to defeat the Night Lords. Each expedition is a three-day run, ending in a boss confrontation, and the lore is told through each character's story and the world's strange fragments. The tone is the series' usual dark fantasy, but with a co-op focus and a gripping sense of urgency.",
"Crisis Core: Final Fantasy VII Reunion":"Zack Fair, an up-and-coming SOLDIER, takes on missions for Shinra, and is drawn into the disappearance of heroes like Genesis and Angeal. As he works alongside the legendary Sephiroth, he uncovers the corporation's dark secrets and forms a bond with Aerith. The story is a tragic prelude that builds to events in Nibelheim and sets the stage for Final Fantasy VII.",
"The Last Guardian":"A boy wakes in a cave next to Trico, a giant, injured creature with feathers and the traits of a bird and cat, and the two must escape a vast ruined fortress. Over time they build trust as Trico responds to your commands and acts on its own will. The story is told in flashback by the boy as an adult. It's a quiet, emotional story about companionship.",
"Dreams":"This is primarily a creation platform, but it includes a story, Art's Dream, a narrative campaign made from the tools themselves. It follows a jazz musician whose life and imagination are told through surreal, painterly levels. The rest of Dreams is a library of community-made games, art, and music. The story is a showcase of what can be built.",
"Marvel's Midnight Suns":"Lilith, Mother of Demons, resurrects Hunter, a powerful figure who fought her centuries ago, to help stop the Hydra scientists who want to unleash a dangerous force. You lead the Midnight Suns, a group of heroes including Iron Man, Captain Marvel, Wolverine, and Doctor Strange, from a base called the Abbey. Between missions you build friendships, train, and make choices about how the team forms.",
"Final Fantasy XIV Online":"You play the Warrior of Light in the realm of Eorzea, a land recovering from the cataclysmic Calamity while the Garlean Empire threatens to conquer it. The core story, A Realm Reborn, introduces the Scions of the Seventh Dawn, and expansions send you across the world and beyond. It's a story of heroism, found family, and rebuilding a world.",
"The Elder Scrolls V: Skyrim Anniversary Edition":"You're the Dragonborn, a prisoner who escapes execution as a dragon attacks, and discover that you can absorb dragon souls. Alduin, the World-Eater, has returned, and you must learn the Thu'um from the Greybeards to stop him. Meanwhile, a civil war between the Stormcloaks and Imperials splits the province. You're free to explore, join guilds, and shape your own story.",
"Age of Empires II: Definitive Edition":"The campaigns revolve around historical leaders: William Wallace's Scottish rebellion, Joan of Arc's French victories, Saladin's defense of the Holy Land, Genghis Khan's conquests, and Barbarossa's Holy Roman Empire. Each is a chain of scenarios with narration. It's history-inspired storytelling more than a single plot.",
"Concrete Genie":"Ash, a lonely boy in the dilapidated seaside town of Denska, is bullied and has a magical paintbrush that brings his drawings to life. He paints friendly creatures to light up the town and fight the Darkness that has settled in. Along the way, he discovers a mystery about a lighthouse and the town's past. It's a gentle story about kindness and creativity.",
"Gears of War: Reloaded":"Decades after humanity's war with the Locust Horde, Marcus Fenix, a disgraced soldier, is freed from prison to rejoin the fight on the planet Sera. With Dom, Baird, and Cole, he joins Delta Squad to launch an offensive using the Lightmass bomb and the Hammer of Dawn. The campaign is a gritty, bro-heavy war story that kicked off the series.",
"Ace Combat 7: Skies Unknown":"In the world of Strangereal, the nation of Osea is at war with Erusea after a surprise attack and the launch of a space elevator. A pilot, Trigger, is framed and sent to a penal unit but becomes a legend in the war. The story follows his rise and uncovers who is really behind the conflict. It's a pulpy, political war story told between missions.",
"Chrono Cross: The Radical Dreamers Edition":"Serge, a teenager in a seaside village, slips into a parallel world where he's been dead for ten years. Trying to understand why, he meets Kid, a thief, and a cast of fighters across a tropical archipelago. The plot involves a mysterious force called the Frozen Flame, a parallel-world conspiracy, and the consequences of time travel. It's a sequel to Chrono Trigger, but stands on its own.",
"Crypt of the NecroDancer":"Cadence, a young woman, enters a crypt beneath Necrodancer's lair to find her missing father, using a cursed amulet. She has to move and fight in time to the music, with every beat counting. The story is light, but the world and weird music set an unusual tone. It's a stylish take on the roguelike.",
"Tiny Tina's Wonderlands":"The game is a tabletop fantasy campaign run by Tina, the Bunkermaster, in a game of Bunkers & Badasses. You're a Fatemaker, a hero created to stop the Dragon Lord, who has risen to destroy the realm. Tina narrates and changes the world as she goes, creating chaotic twists. It's a funny, irreverent fantasy that mixes gunplay with magic.",
"Tchia":"Tchia, a young girl on an island inspired by New Caledonia, sets out to rescue her father after he's kidnapped by the tyrant Meavora. As she explores, she learns to possess animals and objects with her soul-jumping ability. The story blends adventure and cultural elements, with music and traditions rooted in the Pacific. It's a vibrant, relaxed open-world adventure.",
"Avowed":"You're an Envoy of the Aedyr Empire sent to the Living Lands to investigate a mysterious plague called the Dreamscourge. While carrying out your mission, you discover that you're connected to a god-like presence, and your choices influence your companions, factions, and the island's future. It's set in the world of Eora, from the Pillars of Eternity series.",
"Deus Ex: Mankind Divided":"Two years after 'the Incident', where augmented people lose control, Adam Jensen works for Task Force 29 in Prague, as society segregates augmented citizens. A terrorist bombing draws him into a conspiracy tied to the Illuminati. Missions can be solved by stealth, hacking, or force. It's a cyberpunk thriller about prejudice and control.",
"Bulletstorm: Full Clip Edition":"Grayson Hunt, a former assassin turned space pirate, crash-lands on a ruined resort planet while hunting General Sarrano, the man who tricked him into killing innocents. With his cyborg friend Ishi Sato and a tough soldier, Trishka, he fights mutants and gangs. The story is a revenge tale full of crude humor and cheerful violence, with stylish 'skillshots' as the point.",
"Uncharted 2: Among Thieves":"Nathan Drake is lured back into treasure hunting by old associate Harry Flynn and thief Chloe Frazer for a job in Istanbul tied to Marco Polo's lost fleet. The trail runs through Borneo and the Himalayas toward a legendary Tibetan treasure, and Serbian warlord Zoran Lazarević is chasing it with an army. Nate has to untangle old loyalties and new feelings while the line between treasure hunter and thief blurs. It's a globe-trotting adventure full of collapsing buildings and train-top gunfights.",
"Uncharted 3: Drake's Deception":"Nate and his mentor Victor Sullivan chase the lost city of Iram of the Pillars, a legendary city hidden in the Rub' al Khali desert, tied to Sir Francis Drake's ring. Standing in their way is Katherine Marlowe, who leads a secret order and wants the city's power. The journey runs from London pubs to a burning chateau, a cruise ship, and the Arabian sands. At heart it's about the bond between Nate and Sully and what Nate has become.",
"Uncharted: The Lost Legacy":"Chloe Frazer teams with mercenary Nadine Ross to find the Tusk of Ganesh, a relic lost in India's Western Ghats since the Hoysala Empire. They race against Asav, an insurgent leader who wants it to fund his war. It's a story about two uneasy partners learning to trust each other as they follow ancient clues through ruins and jungle.",
"Dishonored":"Corvo Attano, bodyguard to the Empress of the plague-ridden city of Dunwall, is framed for her murder and thrown in prison. Freed by a group of loyalists and granted supernatural powers by a mysterious entity called the Outsider, he sets out to eliminate the conspirators who seized power. Each target can be dealt with by stealth, force, or non-lethal means, and the chaos you cause shapes the city and the ending.",
"BioShock Remastered":"In 1960, Jack survives a plane crash in the Atlantic and discovers Rapture, an underwater utopia built by Andrew Ryan that has collapsed into chaos. Guided by a voice named Atlas, he fights genetically altered Splicers and hulking Big Daddies while deciding the fate of the Little Sisters. The story is a pointed look at objectivism, free will, and power, and it's built around a famous mid-game twist.",
"Far Cry 3":"Jason Brody, on vacation with friends, is captured by the pirate lord Vaas on the Rook Islands. After escaping, he must rescue his friends while allying with the local Rakyat tribe, becoming a warrior in the process. The story follows Jason's transformation and the question of what the island is turning him into. Vaas became one of the series' most iconic villains.",
"Far Cry 4":"Ajay Ghale returns to the Himalayan country of Kyrat to scatter his mother's ashes and is pulled into a civil war between the tyrannical Pagan Min and the Golden Path rebels. Ajay must choose how to balance the rebels' two leaders, who disagree on Kyrat's future. It mixes open-world mayhem with the question of what Ajay's family left behind.",
"Far Cry 5":"In Hope County, Montana, a doomsday cult called Eden's Gate, led by the charismatic Joseph Seed, has taken over. You're a rookie deputy who goes undercover to arrest him and finds the county in a quiet war. You build a resistance across three regions, each ruled by one of Joseph's siblings. The game plays on faith, paranoia, and how far people will go for their beliefs.",
"Far Cry 6":"On the Caribbean island of Yara, the dictator Antón Castillo is forcing citizens to produce a cancer-curing drug. Dani Rojas, a local who wants to escape, ends up joining the guerrilla revolution Libertad. The story follows Dani's fight to topple a regime, with Castillo's son Diego learning what it means to inherit a regime.",
"Wolfenstein II: The New Colossus":"Resuming immediately, BJ Blazkowicz, wounded, leads a resistance in 1961 Nazi-occupied America. Along with the Kreisau Circle, he fights to take back the country, from the ruins of New York to a Roswell fortress. The game blends brutal action with dark satire and family drama, and a villain, Frau Engel, who is personally tied to BJ.",
"Metro 2033 Redux":"After a nuclear war, survivors have retreated to the Moscow Metro, where stations are mini-nations. Artyom, a young man from a remote station, is sent to warn the Polis of the Dark Ones, a mutant threat. His journey takes him through tunnels filled with radiation, monsters, and rival factions. Based on Dmitry Glukhovsky's novel, it's moody and claustrophobic.",
"Metro Exodus":"After Artyom learns the Metro isn't the world's last refuge, he and the Spartan Order flee Moscow in a steam train, the Aurora, to find a new home. They cross a ruined Russia, from the Volga to the Caspian Sea to the Taiga, meeting hostile factions. The story balances Artyom's tight-knit crew with survival in harsh environments and what 'home' means.",
"Assassin's Creed IV: Black Flag":"In 1715, Welsh privateer Edward Kenway turns pirate and sails the Caribbean in search of fame and fortune, finding himself caught between the Assassins and Templars. Along the way he meets pirates like Blackbeard and sails the Jackdaw across open seas. The modern-day thread has you working as an Abstergo employee. It's a swashbuckling story of ambition and loyalty.",
"Assassin's Creed II":"In Renaissance Italy, Ezio Auditore, a young Florentine noble, is thrown into a life of vengeance after his father and brothers are executed. His search for answers leads him to the Assassins, the Templars, and cities like Venice and Florence. Along the way he meets Leonardo da Vinci and learns of the Assassins' ancient secrets. A modern-day thread follows Desmond Miles, a bartender whose ancestors' memories are being relived.",
"Assassin's Creed Origins":"Bayek of Siwa, a Medjay, seeks vengeance after the death of his son in Egypt around 49 BCE, hunting the Order of the Ancients behind it. His wife Aya, a skilled fighter, joins him as they navigate Cleopatra, Ptolemy, and Caesar. Their personal quest ends up shaping the foundation of the Assassin Brotherhood.",
"Assassin's Creed Odyssey":"Set in 431 BCE during the Peloponnesian War, you play Kassandra or Alexios, a mercenary who learns they're part of a prophecy and a fractured family. The search for the truth takes them across Greece, from Sparta to Athens, and sets them against the shadowy Cult of Kosmos. Choices shape relationships and how the war and family conflict resolve.",
"Tomb Raider":"A young Lara Croft, on her first expedition, is shipwrecked on a mysterious island off Japan called Yamatai. Hunted by the Solarii cult, she is forced to become a survivor, protect her friends, and uncover the island's supernatural past. The story is Lara's origin, as she transforms from a student into a hardened explorer.",
"Rise of the Tomb Raider":"Lara Croft pursues her father's unfinished work by seeking the Divine Source, a legendary relic said to grant immortality. Her search takes her from Syria to the snow-covered mountains of Siberia. She races against Trinity, a ruthless organization with the same goal. It's a story about legacy and the obsessions that drive people.",
"Shadow of the Tomb Raider":"While chasing Trinity, Lara Croft in Mexico and Peru triggers a Mayan apocalypse prophecy by taking a dagger from a tomb. She must stop Dominguez, Trinity's leader, from using the dagger, working through the Hidden City of Paititi. The story is about Lara's guilt and what she's willing to sacrifice. It's the finale of the reboot trilogy.",
"Metal Gear Solid V: The Phantom Pain":"In 1984, after nine years in a coma, Big Boss, now known as Venom Snake, wakes in a hospital, hunted by assassins. He rebuilds his army, the Diamond Dogs, with Kazuhira Miller, aiming to take down XOF and its leader, Skull Face. Missions in Afghanistan and Africa mix open-world stealth with a tale of revenge, identity, and loss.",
"Heavy Rain":"A serial killer known as the Origami Killer is abducting children and drowning them with rain, and four people are drawn into the case: Ethan Mars, whose son is taken; FBI agent Norman Jayden; journalist Madison Paige; and private investigator Scott Shelby. Each character's choices, and failures, change who survives and how the story ends. It's a moody, choice-driven noir thriller.",
"Batman: Arkham Asylum":"After capturing the Joker, Batman escorts him to Arkham Asylum, only to find that the Joker has taken over the island with help from Harley Quinn. As Batman fights through the asylum's inmates, including Killer Croc and Scarecrow, he uncovers the Joker's real plan involving a mysterious substance called Titan. It's a dark, atmospheric night in Gotham's most famous asylum.",
"Batman: Arkham City":"Gotham's worst criminals are now locked in a walled-off section of the city, Arkham City, run by Hugo Strange. Bruce Wayne is imprisoned there, and Batman has to find out what Strange's 'Protocol 10' is, while the Joker is dying and Catwoman and Ra's al Ghul are nearby. It's a sprawling, open-world sequel with a tragic climax.",
"The Evil Within":"Detective Sebastian Castellanos arrives at Beacon Mental Hospital, where he finds a massacre and is dragged into a nightmare world manipulated by a mind-hunting figure. He is stalked by grotesque creatures through shifting environments, trying to understand what's real. It's a survival-horror story about trauma and psychological manipulation.",
"Mafia II: Definitive Edition":"In the 1940s and 50s, Sicilian immigrant Vito Scaletta returns from war to Empire Bay, where he and his friend Joe Barbaro rise in the mob. As the two work for different families, Vito faces the price of loyalty, betrayal, and the violence of organized crime. It's a slow-burn crime saga with a tragic arc.",
"L.A. Noire":"In 1947 Los Angeles, war veteran Cole Phelps joins the LAPD and climbs the ranks, solving cases from traffic to homicide and arson. You investigate crime scenes and interrogate suspects by reading their expressions to tell if they're lying. As Phelps rises, a conspiracy involving the city and his past comes to light. It's a story of post-war ideals meeting corruption.",
"Max Payne 3":"Washed-up former NYPD detective Max Payne takes a private-security job in São Paulo, protecting a wealthy family. When a family member is kidnapped, he's pulled into a conspiracy that spans Brazil's gangs, police, and politicians. The story, told in a gritty, noir voice-over, follows a broken man searching for redemption.",
"Infamous Second Son":"Delsin Rowe, a graffiti artist in Seattle, discovers he's a conduit who can absorb powers like smoke, neon, and video. When Brooke Augustine and the D.U.P. attack his tribe, he must take them down. Your choices as good or evil change your powers and the ending. It's a story about identity and freedom in a city under crackdown.",
"Middle-earth: Shadow of Mordor":"Talion, a Gondorian Ranger, is murdered along with his family by Sauron's forces at the Black Gate, and is brought back bound to a wraith that grants him power. Together they hunt Sauron's commanders through Mordor, using the Nemesis System to create personal rivalries with orcs. The story is a revenge tale in Tolkien's world.",
"South Park: The Stick of Truth":"The New Kid moves to South Park and is quickly pulled into a neighborhood fantasy role-playing war between humans and elves, led by Cartman and Kyle, over a powerful stick. The conflict spirals into an alien and Nazi zombie plot with typical irreverence. It's a crude, laugh-out-loud RPG that feels like a long episode.",
"Dead Space 2":"Isaac Clarke wakes up on The Sprawl, a space station on Titan, three years after the Ishimura, haunted by visions and mental instability. As the Necromorph outbreak spreads, he fights to survive and find a way to stop the Marker's influence. The story is intense, personal, and keeps Isaac on edge.",
"Kena: Bridge of Spirits":"Kena, a young Spirit Guide, travels to a forgotten village to help lost spirits move on. She is aided by the Rot, small creatures, and must take on corrupted spirits. Along the way she meets villagers with their own tragic stories. It's a gentle fantasy about grief and letting go, with beautiful visuals.",
"The Outer Worlds":"A colonist in suspended animation is awakened by Phineas Welles, a fugitive scientist, in the Halcyon colony, which is run by corporate greed. You travel the system with a crew, helping or exploiting factions as you choose. It's a witty, satirical RPG of choices and consequences, and what capitalism has done to the frontier.",
"A Plague Tale: Innocence":"In 1348 France, Amicia de Rune and her young brother Hugo are on the run after the Inquisition kills their family. Swarms of rats spread plague, and Hugo's mysterious illness seems tied to them. The siblings must survive by using stealth and light to keep the swarms at bay, finding allies along the way. It's a harrowing, emotional story of a family.",
"Life is Strange":"Photography student Max Caulfield discovers she can rewind time, using it to save her old friend Chloe Price, and then to uncover what happened to missing student Rachel Amber in Arcadia Bay. Her decisions shape her relationships, and a looming storm threatens the town. It's a choice-driven drama of friendship, loss, and consequences.",
"Ori and the Blind Forest: Definitive Edition":"Ori, a small spirit guardian, is raised by a creature named Naru after falling from the Spirit Tree. When the forest of Nibel begins to die, Ori sets out to restore its light and uncover the origins of the dying forest. The story is wordless, emotional, and a tale of loss and renewal.",
"Papers, Please":"As an immigration inspector in the fictional communist state of Arstotzka, you check documents at a border checkpoint in 1982. Each day brings new rules, bribes, and pleas for help, and your pay barely feeds your family. The story is told through your choices and the people passing through. It's a grim study of bureaucracy and morality.",
"Night in the Woods":"Mae Borowski drops out of college and returns to her declining hometown of Possum Springs, where she finds her old friends changed. As strange events unfold, she's pulled into a mystery as she wrestles with anxiety and nostalgia. It's a warm, funny, melancholy story about growing up.",
"Dragon Age: Inquisition":"A rift in the sky, the Breach, is unleashing demons, and you, the lone survivor of an explosion, bear a mark that can close it. You become the Inquisitor, rebuilding the Inquisition to fight the villain Corypheus, a Tevinter magister. You recruit companions and make political choices across Thedas. It's a sprawling fantasy about leadership and faith.",
"Star Wars: Knights of the Old Republic":"Four thousand years before the films, the Sith, led by Darth Malak, wage a devastating war on the Republic. You wake aboard a ship and find yourself pursued by the Sith and joined by a crew, with a path to becoming a Jedi. The story hinges on your alignment, light or dark, and a famous revelation about who you are.",
"Final Fantasy X/X-2 HD Remaster":"Tidus, a star blitzball player from Zanarkand, is flung into the world of Spira, where a monstrous being called Sin terrorizes the land. He joins the summoner Yuna on a pilgrimage to defeat it, discovering the truth of Spira's faith. The sequel, X-2, follows Yuna as a sphere hunter two years later. It's a deeply emotional story of sacrifice and hope.",
"Return of the Obra Dinn":"In 1807, an insurance investigator boards the Obra Dinn, a merchant ship that has drifted back to port with its entire crew dead or missing. Armed with a magical pocket watch, you relive each person's final moments to deduce their identities and fates. The story unfolds in a nonlinear fashion, with an unsettling supernatural undertone.",
"Psychonauts":"Raz, a young circus runaway with psychic abilities, sneaks into Whispering Rock Psychic Summer Camp. Soon he finds that someone is stealing campers' brains, so he enters people's minds to fix their mental issues and uncover the plot. Each mind is a surreal level that reflects its owner's quirks. It's a funny, imaginative platformer.",
"Oxenfree":"Alex and a group of friends take a trip to Edwards Island for a party and open a rift using a radio, unleashing ghosts from the island's past. They must figure out what's going on while their relationships fray. Dialogue-driven choices shape the story, and time loops add to the mystery. It's an eerie, character-driven teen supernatural drama.",
"Ni no Kuni: Wrath of the White Witch Remastered":"After his mother's death, young Oliver is told by a fairy named Drippy that he can bring her back by traveling to a parallel world. There he learns magic, befriends companions, and battles a dark wizard named Shadar. The story is a hand-drawn Studio Ghibli-style fairy tale of grief, healing, and courage.",
"Tales of Vesperia: Definitive Edition":"Yuri Lowell, a former knight turned wandering swordsman, steals back a stolen core and meets Estelle, a noblewoman. Together they travel across the world with a diverse crew, uncovering a conspiracy involving the Empire. Yuri's own sense of justice, which sometimes conflicts with the law, is central to the story.",
"Yakuza Kiwami 2":"Kazuma Kiryu is pulled back into the yakuza when the Tojo Clan's leader is assassinated, leading to a brewing war with the Omi Alliance. As he works to prevent bloodshed, he meets Ryuji Goda, the 'Dragon of Kansai', an old rival. The story weaves a tangled crime plot between Tokyo's Kamurocho and Osaka's Sotenbori with the series' trademark melodrama.",
"Call of Duty: Black Ops 7":"Set in 2035, roughly a decade after Black Ops 2, this campaign brings back David Mason, the series' long-running operative, as he confronts the return of Raul Menendez, the villain of that earlier game. The story is about the fallout of past wars and secret programs, and it leans hard into hallucinations and unreliable perception, so players are never fully sure what's real. New characters like Emma Kagan, tied to a shadowy private organization, join a team that has to stop a threat to a technology-saturated near future. It's built for solo or up to four-player co-op, and ends by opening into Avalon, a city that anchors the replayable Endgame mode.",
"Call of Duty: Modern Warfare (2019)":"This reboot drops Captain Price and a new squad into a war that starts with a terrorist attack in London and ripples out to the fictional country of Urzikstan. Price teams with local resistance leader Farah Karim and British operative Kyle Garrick (\"Gaz\") to track chemical weapons held by a Russian general and a terrorist cell. Missions swing between tense night raids, home-invasion clearances, and civilian scenes that blur who the enemy is. The tone is gray and personal, asking what the people fighting these wars are willing to do.",
"Call of Duty: Infinite Warfare":"In a future where humanity has settled across the solar system, a militant faction called the Settlement Defense Front attacks the Earth's fleet in a devastating opening strike. Captain Nick Reyes, left as one of the few surviving senior officers, takes command of the warship Retribution and fights back across Earth, space, the Moon, and Mars. Missions mix zero-gravity infantry combat with starfighter dogfights, and Reyes's crew, including a friendly combat robot, forms the emotional core. The story weighs the cost of command against a villain who believes the colonies have been exploited.",
"Call of Duty: WWII":"Private Ronald \"Red\" Daniels of the U.S. 1st Infantry Division follows the Allied advance from the D-Day landings through France and into Germany. Alongside a tight squad under Sergeant Pierson, he faces the brutality of Hürtgen Forest, the liberation of Paris, and the push across the Rhine. The story is about brotherhood, the toll of combat, and the moral weight of what the Allies uncovered as the war closed. It's the series' return to a conventional WWII tone after years of futuristic settings.",
"Call of Duty: Black Ops III":"In 2065, a cybernetic black-ops squad investigates a rogue operation tied to a lost team of elite soldiers. Your custom soldier is given experimental neural implants, and as the mission pushes deeper, the line between memory, simulation, and reality starts to break down. The campaign is playable solo or in four-player co-op, with a plot that questions the cost of fusing humans and machines. Expect a dark, mind-bending tone and a final act that reframes what you've been playing.",
"Call of Duty: Black Ops 4":"There's no traditional solo campaign in this entry. Instead, it focuses on multiplayer, the Blackout battle royale, and Zombies modes with their own storylines. The single-player-style content comes through \"Solo Missions,\" which give backstories to the playable Specialists, rather than a connected plot.",
"Call of Duty: Advanced Warfare":"Marine Jack Mitchell loses an arm in a catastrophic battle and is recruited by Atlas, a private military corporation led by his former commander, Jonathan Irons. Fitted with a prosthetic and an exoskeleton, Mitchell becomes part of a near-future world where corporate armies outmatch governments. As Atlas's power grows, he's forced to question whether the man he trusts has the world's interests at heart. It's a story about loyalty and the danger of privatized war.",
"Call of Duty: Ghosts":"After a space-based weapon is hijacked and turned on the U.S., a unified coalition of South American nations invades and the country is reshaped. Logan Walker and his brother Hesh join the Ghosts, a legendary special-forces unit, with their father, Elias, an old Ghost himself. The campaign pairs their family story with a hunt for a former Ghost who turned against his own. Missions range from jungle ambushes to orbital strikes, with a loyal dog, Riley, as the squad's standout.",
"Call of Duty: Modern Warfare Remastered":"This remake follows the original 2007 campaign, in which British SAS Captain Price and Sergeant \"Soap\" MacTavish hunt Russian ultranationalist Imran Zakhaev, while a U.S. Marine squad chases an extremist warlord. The two storylines intertwine as a nuclear threat looms over the Middle East. Notable missions include the sniper trek through Pripyat and a gut-wrenching nuclear sequence. It's lean, fast, and told through a handful of central characters.",
"Call of Duty: Modern Warfare 2 Campaign Remastered":"Following the original, Task Force 141 chases Vladimir Makarov, a Russian ultranationalist who has pushed the world to the brink of war after a notorious airport massacre. Soap MacTavish, Ghost, and Roach take on missions from Brazilian favelas to Russian gulags to a decisive stand in Washington. As the war escalates, they find the real enemy might be closer to home than they think. The story ends on a cliffhanger that sets up the next chapter.",
"Call of Duty: Black Ops 6":"Set in 1991 on the eve of the Gulf War, this follows CIA operatives Adler, Marshall, Case, and Woods after they're disavowed for a conspiracy they didn't commit. On the run and hunted by their own agency, they chase a shadow organization called the Pantheon, which has its hooks into governments across the world. The story weaves espionage, betrayal, and political intrigue into the end of the Cold War, with missions from Kuwait to Iraq. It's a tale about who you can trust when your own side is the threat.",
"Call of Duty: Modern Warfare II":"Task Force 141, led by Captain Price with Soap, Ghost, and Gaz, hunts down missiles stolen from an Iranian general who's killed in a U.S. strike. The trail leads from the Middle East to a Mexican cartel that has access to dangerous weapons, adding Mexican special forces to the mix. As allies and enemies shift, the task force finds that the real danger might come from within its own chain of command. The campaign is a globe-trotting thriller built on shifting trust.",
"Call of Duty: Modern Warfare III":"Picking up directly after the previous game, Task Force 141 hunts Vladimir Makarov, the ultranationalist mastermind who escaped and is now plotting global chaos. Price, Soap, Ghost, and Gaz chase him across Europe and beyond, with open-combat missions that let you choose your approach. Alongside a rogue operator, Phillip Graves, the story ties up the Makarov saga. It's a shorter, action-heavy conclusion to the rebooted trilogy.",
"Call of Duty: Black Ops Cold War":"In 1981, a Soviet spy codenamed Perseus is believed to be orchestrating a plot against the West. Mason, Woods, Adler, and a new operative, Bell, track him through Berlin, Turkey, and Vietnam as the Cold War's biggest secret unravels. You create your own character, Bell, and your choices about who to trust affect the ending. It's a moody spy thriller that digs into betrayal and propaganda.",
"Call of Duty: Vanguard":"In the last year of WWII, an elite multinational unit, Task Force One, is assembled to stop Nazi leaders from launching a secret program called Project Phoenix. Arthur Kingsley, Polina Petrova, Wade Jackson, Lucas Riggs, and Richard Webb each have their own backstories, told through flashbacks across Stalingrad, North Africa, the Pacific, and Normandy. The campaign focuses on the personal reasons each fights the war. It's a team-based story about unlikely allies.",
"Ghost of Yotei":"Set centuries after Jin Sakai's story, this follows Atsu, a lone wolf wanderer hunting the five outlaws who destroyed her family on Ezo's Mount Yotei. It's framed as a myth-building revenge tale — Atsu becomes a living legend as she tracks each target across a harsher, more remote version of Tsushima's island setting. Unlike Jin's conflict with an outside invader, this is a personal vendetta carried out largely alone.",
"Lost Judgment":"Disbarred-lawyer-turned-detective Takayuki Yagami investigates a case that starts as a simple assault and unravels into a conspiracy tangled up with school bullying and a justice system that keeps failing victims. The story deliberately sits in moral gray areas — asking whether the people being punished are actually the ones at fault. It splits time between Kamurocho and a new setting, Ijincho's rival port city.",
"Yakuza Kiwami":"A remake of the original Yakuza, following Kazuma Kiryu as he's released from prison after a ten-year sentence he took to protect his sworn brother. He returns to a changed Kamurocho to find the organization he once belonged to in chaos, a young girl he's sworn to protect, and the people closest to him revealed as something other than what they seemed.",
"Nier: Automata":"Androids 2B and 9S fight on behalf of a fled humanity, battling machine lifeforms that have overrun an abandoned Earth. What starts as a straightforward war story keeps pulling back layers — questioning who's actually being protected, what free will means for a created being, and whether the war itself still has a point. The game is built to be played through multiple times, with each pass revealing more of what the previous one hid.",
"Final Fantasy XV":"Prince Noctis and three childhood friends road-trip across the kingdom of Lucis for his arranged wedding, only for his home city to fall to an empire during the journey. What begins as a buddy-trip tone gradually darkens into a story about loss, duty, and a prophecy Noctis can't outrun, all while the group's friendship stays the emotional center of the game.",
"Dragon Quest XI S: Echoes of an Elusive Age":"A silent protagonist discovers he's the reincarnation of a legendary hero destined to stop a world-ending calamity, only to be branded a threat by the kingdom he grew up loyal to. It plays out as a classic, unapologetically earnest fantasy quest — gathering companions, uncovering a larger conspiracy behind the 'destined hero' legend, and deciding what that legend is actually worth.",
"Elden Ring":"The Tarnished, once exiled from the Lands Between, return after the Elden Ring is shattered and the demigod children of Queen Marika go to war over its fragments. There's no fixed path — players piece together the fractured history of a dying golden order from item descriptions, ruins, and the demigods themselves while deciding who, if anyone, deserves to become the new Elden Lord.",
"God of War Ragnarök":"Kratos and his son Atreus are caught in the lead-up to Ragnarök, the Norse prophecy of the end of the world, with Odin actively trying to force the fight before they're ready. The story leans harder into Atreus's own identity and choices than the first game did, while Kratos struggles with whether he can break his own cycle of violence as a father this time around.",
"Horizon Forbidden West":"Aloy pushes west into a new, more hostile frontier chasing a blight that's killing the machines meant to stabilize Earth's ecosystem — and by extension, every living thing left on it. The deeper she goes, the more the story folds in the old-world history behind the robots and the different factions descended from humanity's survivors, each with their own read on what should happen next.",
"Baldur's Gate 3":"A mind flayer tadpole is implanted in the player's head during an attack, threatening to slowly transform them into a monster unless they find a cure. The search for a cure pulls together a party of companions with their own secrets and agendas, all while a cult called the Absolute gathers power in the region — and the tadpole itself starts granting the player strange, unwanted abilities.",
"Returnal":"Scout Selene crash-lands on the alien planet Atropos, dies, and wakes up right back at the crash site — caught in a loop that resets the planet's layout each time. The story is told in fragments scattered across each run, slowly revealing that the loop, the planet, and Selene's own memories are far more tangled together than a simple crash would explain.",
"Final Fantasy XVI":"Clive Rosfield starts as the shield meant to protect his younger brother, the heir to a Dominant's power over fire — until a tragedy reframes his entire life around vengeance. The world runs on Mothercrystals and the Eikons bound to royal bloodlines, and as Clive's journey continues, the story turns into a reckoning with the entire political and magical system built on that power.",
"Ghost of Tsushima Director's Cut":"Samurai Jin Sakai is one of the only survivors of the first Mongol invasion of Tsushima Island, and finds the honor-bound way of the samurai inadequate against an enemy that doesn't fight by the same rules. The story follows his transformation into the stealth-using 'Ghost,' and the cost that transformation has on his relationships with the people who still expect him to be the samurai he was raised to be.",
"Ratchet & Clank: Rift Apart":"A battle with the mad scientist Dr. Nefarious rips open dimensional rifts, scattering Ratchet and Clank across parallel realities — including one where they meet Rivet, a Lombax resistance fighter from a world under Nefarious's total control there. It's a lighter, more adventurous story than most on this list, built around dimension-hopping action and the found-family bond at its core.",
"The Last of Us Part I":"Twenty years after a fungal pandemic collapses society, smuggler Joel is hired to escort a teenage girl, Ellie, across a ruined United States — only to learn she may be humanity's only hope for a cure. The relationship that forms between them over the journey becomes the real story, raising hard questions about what Joel is willing to do to protect her by the end.",
"Death Stranding Director's Cut":"After a catastrophic event called the Death Stranding tears holes between the world of the living and the dead, porter Sam Porter Bridges is tasked with physically reconnecting isolated American settlements, one delivery at a time. It's as much about the loneliness and literal weight of the work as it is about the larger mystery of what caused the Stranding and what's crossing over because of it.",
"Resident Evil 4":"Agent Leon Kennedy is sent to rural Spain to rescue the president's kidnapped daughter and finds a village under the control of a parasite-driven cult, the Los Iluminados. It mixes survival horror with increasingly over-the-top action as Leon uncovers who's really pulling the cult's strings and why they want the girl he's there to save.",
"Stray":"A stray cat gets separated from its colony and falls into a sealed, long-abandoned city now populated entirely by robots, with the few remaining humans nowhere to be found. Guided by a small drone companion, the cat has to navigate the city's levels and factions to find a way back to the surface, with the story slowly revealing what happened to the people who used to live there.",
"It Takes Two":"A couple on the verge of divorce are magically transformed into living dolls by their daughter's wish, and have to work together — literally, through two-player co-op mechanics — to find a way to turn back. The story plays their bitter marriage for both comedy and real emotional weight, using each level's shifting mechanics to mirror where their relationship is at.",
"Deathloop":"Assassin Colt wakes up on the island of Blackreef with no memory, caught in a time loop that resets every day, and learns he has to kill eight key targets in a single loop before midnight or the cycle starts over. A rival assassin, Julianna, is hunting him across every loop to keep the cycle intact, turning each run into both a puzzle and a cat-and-mouse fight.",
"Marvel's Spider-Man: Miles Morales":"Miles Morales is still learning to be Spider-Man when Peter Parker leaves New York for the holidays, putting Miles on his own against a tech-energy conglomerate and the Underground resistance group fighting it. It's a smaller, more personal story than the first game — centered on Miles's own community in Harlem and his family's history with the company he's up against.",
"Hogwarts Legacy":"A student starting late at Hogwarts is discovered to have a rare ability tied to ancient magic, pulling them into a conflict with a goblin rebellion searching for the same power. The story is largely self-contained from the book series' main cast, set a century earlier, and leans on exploring the wizarding world and choosing how the student's own magical path takes shape.",
"Cyberpunk 2077":"Mercenary V gets caught up in a heist gone wrong in Night City and ends up with the digitized personality of a long-dead rockstar terrorist, Johnny Silverhand, slowly overwriting their own mind. The race to save V's life — and figure out whether 'saving' means getting rid of Johnny or something else — drives the story through the city's corporate and criminal underworld.",
"Alan Wake 2":"Years after writer Alan Wake vanished into a nightmare dimension called the Dark Place, FBI agent Saga Anderson investigates a string of ritualistic murders in a small Pacific Northwest town that turn out to be connected to his disappearance. The story runs two parallel threads — Saga's investigation and Alan's attempts to write his way out of the Dark Place — that increasingly bleed into each other.",
"Marvel's Spider-Man 2":"Peter Parker and Miles Morales share the responsibility of protecting New York as a new, more dangerous threat tied to the symbiote known as Venom emerges, alongside the hunter Kraven arriving to test himself against the city's strongest. It raises the personal stakes for both Spider-Men at once, splitting time between their individual lives and a shared threat neither can handle alone.",
"Horizon Zero Dawn Remastered":"In a far-future Earth reclaimed by robotic creatures, outcast Aloy sets out to learn why she was abandoned at birth — and ends up uncovering the buried history of the civilization that collapsed before the machines took over. It's a mystery about the old world as much as an action story about the new one, told through ruins, logs, and the machines themselves.",
"Helldivers 2":"Players are super-soldiers of Super Earth, dropped onto hostile planets to fight back alien threats in the name of 'managed democracy' — a tone that's intentionally satirical about jingoistic propaganda even as the actual stakes stay real. There's no deep individual character arc; the story lives in the galaxy-spanning war itself and the absurd, over-the-top way it's fought.",
"Rise of the Ronin":"Set during Japan's turbulent Bakumatsu period as the country opens to the West, a masterless ronin trained by a secret society gets pulled between rival factions fighting over Japan's future. The player's choices shape which historical faction they end up allied with, playing out real historical turmoil through a fictional protagonist's eyes.",
"Dragon's Dogma 2":"The player's heart is stolen, leaving them an 'Arisen' bonded to Pawns — otherworldly companions who speak of a destiny the Arisen never asked for. It's a classic fantasy quest structure wrapped around unusually physical, systemic combat, with the larger political plot of two rival Arisen candidates unfolding as the player explores.",
"Silent Hill 2":"James Sunderland receives a letter from his wife, who died three years earlier, asking him to meet her in the town of Silent Hill — and goes, even though he knows that shouldn't be possible. The town twists itself around his guilt and grief as he searches for her, with the horror directly reflecting what James did and is trying not to admit to himself.",
"Black Myth: Wukong":"Loosely based on Journey to the West, a monkey warrior called the Destined One retraces the steps of the legendary Sun Wukong, fighting through a mythic Chinese landscape of spirits and gods. The story is told obliquely, through environmental storytelling and boss encounters rather than direct exposition, rewarding familiarity with the original legend.",
"Until Dawn":"A group of friends return to a remote mountain lodge one year after a prank went horribly wrong, only to find themselves stalked by something that isn't entirely human. Every choice can permanently kill a character, and the story branches hard based on who survives and how the group's old guilt resurfaces under pressure.",
"Persona 3 Reload":"Transfer students at a Japanese high school discover a hidden hour at midnight — the Dark Hour — where monstrous Shadows roam and only a select few can fight back using summoned personas. The story leans heavily into themes of mortality and found family as the group investigates why the Dark Hour exists and what's causing it.",
"Like a Dragon: Infinite Wealth":"Ichiban Kasuga travels to Hawaii chasing a lead on his birth mother, while Kazuma Kiryu's own storyline deals with a terminal diagnosis and unfinished business back in Japan. The two protagonists' arcs run in parallel for most of the game before converging, mixing the series' usual soap-opera crime plotting with real emotional weight around mortality.",
"Star Wars Jedi: Survivor":"Years after escaping the Empire's purge of the Jedi, Cal Kestis is more hardened and more hunted, dealing with the toll of years on the run as a new threat emerges that even the Empire fears. It continues directly from Fallen Order's story, going further into Cal's own doubts about whether the fight is one he can actually win.",
"Assassin's Creed Mirage":"A street thief in 9th-century Baghdad is recruited into a secret brotherhood after a betrayal sets him on a path of revenge, discovering along the way who's really pulling strings behind the city's unrest. It's a tighter, more personal story than the recent open-world entries, deliberately built closer to the series' original stealth-assassination roots.",
"Lies of P":"A loose, dark reimagining of Pinocchio, where a puppet built to look human wakes up in a plague-ravaged city and is told that becoming truly human requires choosing between lies and truth at key moments. The story leans into body horror and a genuinely grim take on the fairy tale, using the lie-or-truth choices to shape how other characters see the puppet.",
"Final Fantasy VII Rebirth":"Continuing directly from Remake, Cloud and the rest of Avalanche leave Midgar to pursue Sephiroth across the wider world, uncovering pieces of Cloud's fractured memory along the way. It expands heavily on character relationships and worldbuilding that the original PS1 game only hinted at, while keeping the long shadow of Sephiroth's return over everything.",
"Marvel's Wolverine":"A grounded, R-rated solo story for Logan, leaning into his healing-factor-fueled brutality and the weight of a very long, very violent life. Details are kept close to the chest pre-release, but it's built as a standalone character study rather than a crossover, centered on Wolverine's own code and the people he can't quite walk away from.",
"Assassin's Creed Valhalla":"Viking raider Eivor leads their clan from Norway to England, carving out a new settlement while getting pulled into the political chaos of Anglo-Saxon kingdoms and the brotherhood's shadow war with the Templar Order. It's as much about building and defending a new home as it is about the assassin-order plotting the series is known for.",
"Assassin's Creed Shadows":"Set in Sengoku-era Japan, two protagonists — the shinobi Naoe and the historical samurai Yasuke — pursue intertwined paths of vengeance and loyalty against a warlord dismantling the old order. Playing both characters lets the story contrast stealth-based and direct-combat approaches to the same unfolding conflict.",
"Red Dead Redemption 2":"Arthur Morgan, a senior member of the outlaw Van der Linde gang, watches the gang's way of life collapse as lawmen, rival gangs, and their own leader's choices close in during the dying days of the American frontier. It's framed as a slow tragedy — Arthur's personal reckoning with what the gang actually is, set against a West that's running out of room for men like him.",
"The Witcher 3: Wild Hunt":"Monster hunter Geralt of Rivia searches a war-torn continent for Ciri, his adopted daughter and a woman with power the spectral Wild Hunt wants for itself. Nearly every side quest ties back into the world's politics and Geralt's own found-family relationships, making the search for Ciri feel personal rather than just a fetch quest.",
"Grand Theft Auto V":"Three very different criminals — a retired bank robber, a street hustler, and an unstable hitman — get pulled into one last string of heists across a satirical version of Los Angeles. The story rotates between all three perspectives, using the contrast between their lives to drive both the comedy and the eventual fallout of the job.",
"Bloodborne":"A Hunter arrives in the plague-ridden city of Yharnam seeking a cure for an unnamed illness, and instead finds a nightly hunt for beasts that turns into something far stranger and cosmic the deeper the night goes. The story is told almost entirely through item descriptions and environmental clues, rewarding players who piece together what Yharnam's blood ministrations actually did.",
"Demon's Souls":"The kingdom of Boletaria has been consumed by a supernatural fog that drives its inhabitants into madness and summons demons, after its king sought forbidden power from an ancient being called the Old One. A Slayer enters the fog to put a stop to it, in the game credited with starting the Soulslike genre's brutal, cryptic approach to storytelling.",
"Detroit: Become Human":"Three androids — a negotiator, a caretaker, and an investigator — begin breaking from their programming in a near-future Detroit where android labor has upended society. Every choice across all three storylines branches the plot and can permanently kill a character, building toward one of several very different endings depending on what the player decides android freedom is worth.",
"Control":"Jesse Faden walks into the Federal Bureau of Control's headquarters looking for her missing brother and is unexpectedly made the Bureau's new Director after its previous leader is killed by a hostile, reality-warping force called the Hiss. The story mixes bureaucratic horror with brutalist, shifting architecture as Jesse tries to retake the building floor by floor.",
"Uncharted 4: A Thief's End":"Retired treasure hunter Nathan Drake is pulled back into the field by his thought-dead brother Sam, chasing the lost pirate colony of Henry Avery's Libertalia. It's framed as the series' send-off, weighing Drake's old adventuring life against the quieter one he's built, and what he's willing to risk to help his brother.",
"Days Gone":"Former outlaw biker Deacon St. John survives two years after a pandemic turns most of the population into feral, swarm-forming Freakers, scraping by on bounty work in the Pacific Northwest. The story follows his search for his missing wife, who he'd assumed dead, while navigating the different camps and ideologies that sprang up after society fell apart.",
"God of War":"A soft reboot moving Kratos from Greek to Norse mythology, following him and his young son Atreus on a journey to scatter the ashes of Atreus's mother atop the highest peak in the realms. The quest doubles as Kratos trying, imperfectly, to be a better father than the version of himself he's spent the whole series trying to escape.",
"The Last of Us Part II":"Years after the first game, Ellie sets out on a brutal revenge mission after a violent act of retaliation tears her found family apart — a journey the game deliberately makes uncomfortable by forcing players to see the human cost on both sides of the conflict. It's a direct, intentional subversion of the original's ending, asking what Ellie's revenge actually accomplishes.",
"Marvel's Guardians of the Galaxy":"A mostly self-contained take on the Guardians separate from the movies, following Star-Lord and the team after a mission gone wrong makes them unlikely saviors of the galaxy they usually just cause trouble in. It leans on the team's bickering, banter, and Star-Lord's own unresolved grief as much as the galaxy-scale plot.",
"Red Dead Redemption":"Former outlaw John Marston is blackmailed by federal agents into hunting down his old gang members in exchange for his family's safety, as the Old West gives way to a more 'civilized' and policed country. It's structured as a tragedy about a man trying to leave his past behind in a world that won't actually let him.",
"Mafia: Definitive Edition":"A remake following cab driver Tommy Angelo's slow pull into the Salieri crime family in the fictional city of Lost Heaven during Prohibition. It's a classic rise-and-fall mob story, built around Tommy's growing unease with what loyalty to the family actually costs him.",
"Judgment":"Disbarred lawyer Takayuki Yagami works as a private detective in Kamurocho, pulled into a serial murder case that keeps crossing paths with the yakuza clans he used to defend in court. It leans harder into detective-noir investigation than the mainline Yakuza games, built around a mystery rather than one man's personal saga.",
"Dark Souls Remastered":"The Chosen Undead rises from the Undead Asylum into a dying kingdom, tasked — or perhaps just expected — with ringing bells that lead to the choice of linking the First Flame or letting the age of fire end. Like the rest of the series, almost nothing is explained directly; the real story is assembled from item text, NPC dialogue, and the ruined world itself.",
"Yakuza 0":"A prequel set in 1988 Japan's bubble economy, following a young Kazuma Kiryu and future-business-legend Goro Majima as they get entangled in a conspiracy over a small, seemingly worthless plot of land in Kamurocho. It's widely considered the series' best entry point, explaining how both men became who they are in later games.",
"Yakuza: Like a Dragon":"A soft reboot switching protagonists to Ichiban Kasuga, an idealistic low-level yakuza who takes the fall for a murder he didn't commit and emerges 18 years later to a city — and a world — that's moved on without him. It also switches the combat to turn-based RPG battles, framed in-fiction as literally how Ichiban, a lifelong Dragon Quest fan, perceives his fights.",
"Resident Evil Village":"Ethan Winters, protagonist of Resident Evil 7, searches for his kidnapped daughter in a fog-shrouded Eastern European village ruled by four grotesque lords, each commanding their own breed of monster. It leans further into gothic horror than survival horror, trading the first game's claustrophobia for a larger, stranger map to explore.",
"Resident Evil 2":"A remake following rookie cop Leon Kennedy and college student Claire Redfield surviving their first night in Raccoon City as a viral outbreak turns the population into the undead. Both characters' campaigns interlock, each revealing different parts of the same unraveling conspiracy inside the Umbrella Corporation.",
"Final Fantasy VII Remake":"A full reimagining of the PS1 classic's opening act, following eco-terrorist Cloud Strife and the group Avalanche as they fight the mega-corporation Shinra for draining the planet's life force. It expands the original Midgar section into a full game, filling in character beats the original only had room to imply.",
"Shadow of the Colossus":"A young man carries a cursed girl's body into a forbidden land and makes a bargain with a disembodied voice to revive her — in exchange for hunting down sixteen massive, ancient Colossi roaming the land. Each boss fight is also a puzzle, and the growing unease about what exactly the hero is doing to himself with each kill is the real story.",
"Star Wars Jedi: Fallen Order":"Cal Kestis, a Jedi Padawan in hiding since Order 66, is forced back into the open when Imperial Inquisitors discover him, setting him on a journey to rebuild his connection to the Force and the scattered remnants of the Jedi Order. It's set early in the Empire's reign, with the galaxy's fear of Jedi still fresh.",
"Dishonored 2":"Set fifteen years after the first game, either Empress Emily Kaldwin or her father Corvo Attano is deposed by a usurper with supernatural backing, and must reclaim the throne of Dunwall's sister city. The choice of protagonist changes available powers and how NPCs react, and the game tracks a 'chaos' system based on how lethally the player handles each mission.",
"Prey":"Morgan Yu wakes up on a space station overrun by a shapeshifting alien species called the Typhon, and slowly realizes their own memories of the station — and themselves — may have been altered. It plays as an immersive sim with a strong identity-mystery hook running underneath the alien-horror surface.",
"Subnautica":"After a spaceship crash strands the player on an alien ocean world, survival means diving deeper into increasingly dangerous waters to scavenge materials and uncover why the planet is quarantined. The story is told almost entirely through exploration and discovered logs rather than direct cutscenes.",
"Firewatch":"A man takes a summer job as a fire lookout in the Wyoming wilderness to escape a painful situation back home, and starts building a radio-only relationship with his supervisor as strange, possibly surveillance-related events unfold nearby. It's a tightly scoped, dialogue-driven story about escaping one problem only to find another.",
"What Remains of Edith Finch":"Edith Finch returns to her family's strange, sprawling house to go through the belongings of relatives who all died under unusual circumstances, with each family member's death told as its own short, distinctly-styled vignette. It's structured more like a collection of short stories than a single throughline.",
"Hollow Knight":"A small, silent knight descends into the ruined, bug-inhabited kingdom of Hallownest, piecing together what caused its collapse through optional lore, environmental clues, and conversations with its surviving inhabitants. Very little is stated outright, and a meaningful part of the story is genuinely optional to find.",
"Hades":"Zagreus, son of the god of the Underworld, repeatedly attempts to escape to Mount Olympus and meet the family he's never known, with each failed run adding new dialogue and relationship development rather than resetting the story. The repeated-death structure is written directly into the plot rather than just being a gameplay convenience.",
"Disco Elysium":"A detective wakes up with near-total amnesia in a rundown city district, and has to solve a murder case while also piecing together who he even is through conversations with the dozens of voices in his own skull. It's almost entirely dialogue and internal-monologue driven, with the player's choices shaping the detective's politics, habits, and self-image as much as the case itself.",
"Outer Wilds":"A newly space-faring explorer is sent to investigate the solar system, only to discover they're caught in a 22-minute time loop that resets every time the sun goes supernova. The 'story' is really an investigation — piecing together an ancient alien civilization's fate using knowledge that carries over between loops even as nothing physical does.",
"Hitman: World of Assassination":"Bald, barcode-tattooed assassin Agent 47 travels the world taking out high-value targets at lavish, elaborate locations, with each mission designed as an open sandbox for creative, improvised kills rather than a fixed path. The overarching plot about the shadowy organizations pulling his strings takes a backseat to each individual mission's puzzle-box design.",
"Fallout 4":"The sole survivor of Vault 111 emerges 200 years after a nuclear war to find their infant son kidnapped and the Boston Commonwealth reshaped by factions fighting over the wasteland's future, including the question of synthetic humans' rights. The search for the son runs alongside — and often gets overshadowed by — the larger factional conflict.",
"Persona 5 Royal":"A group of delinquent high schoolers use supernatural Persona powers to enter the corrupted hearts of abusive adults and force them to confess their crimes, operating as vigilantes called the Phantom Thieves. It's a story about outsiders pushing back against a society that protects the powerful, told with the series' usual mix of school-life sim and stylish turn-based combat.",
"Sekiro: Shadows Die Twice":"A one-armed shinobi called Wolf is killed and revived to rescue his young lord, who possesses blood with the power of immortality that several factions want for themselves in a fictionalized Sengoku-era Japan. The story leans more directly into a single revenge-and-rescue plot than FromSoftware's usual cryptic approach.",
"Dark Souls III":"The Lords of Cinder are summoned back from their graves to link the fire once more, in a world where the cycle of linking and letting it fade has clearly been repeated so many times that everything, including the Lords themselves, is falling apart. It plays as a kind of eulogy for the whole series, revisiting faded versions of earlier games' locations and characters.",
"Palworld":"A settler arrives on an island inhabited by creatures called Pals, which can be captured, bred, and — unlike in more family-friendly monster-taming games — put to work in factories, farms, and even combat. There's a loose survival-crafting story about the island's factions, but most of the narrative tension comes from the game's openly darker riff on the genre's usual formula.",
"Ghostwire: Tokyo":"A supernatural event vanishes nearly the entire population of Tokyo, leaving a young man possessed by a spirit detective to fight the Visitors responsible and find his missing sister. It leans on Japanese folklore and urban legend for its enemy design and setting, treating Tokyo's empty streets as both a playground and a mystery.",
"A Plague Tale: Requiem":"A direct sequel following Amicia and her younger brother Hugo as his mysterious, rat-summoning curse grows stronger and harder to control, forcing them to search for a way to cure or contain it across sun-drenched but increasingly dangerous French countryside. It continues the first game's mix of stealth survival and sibling relationship drama.",
"Dead Space":"Engineer Isaac Clarke responds to a distress call aboard the mining ship USG Ishimura and finds the crew slaughtered and reanimated by an alien signal called the Marker. The story is told with minimal exposition and almost no HUD interruptions, keeping the isolation and horror as unbroken as possible.",
"BioShock Infinite":"Disgraced detective Booker DeWitt is sent to the floating city of Columbia to extract a young woman, Elizabeth, who's been held captive there her whole life — and finds a city built on nationalist zealotry with Elizabeth's own reality-tearing powers at its center. The story folds in alternate timelines and a slow reveal of how Booker and the city's founder are connected.",
"Alan Wake Remastered":"Bestselling thriller writer Alan Wake arrives in the small town of Bright Falls for a vacation, only for his wife to go missing and pages of a novel he doesn't remember writing to start coming true around him. It plays with the idea of a writer losing control of his own narrative, blurring fiction and reality as the town turns hostile.",
"Beyond: Two Souls":"Jodie Holmes has been psychically linked since birth to an invisible entity called Aiden, and the story jumps around her life — from childhood lab experiments to government operations — as she tries to understand what Aiden actually is and what that connection has cost her. It's told out of chronological order, piecing her life together nonlinearly.",
"Uncharted: Drake's Fortune":"Treasure hunter Nathan Drake sets out to find the lost fortune of explorer Sir Francis Drake, a supposed ancestor, and ends up on an island hiding something far stranger than gold. It's the series' origin point, establishing the pulpy adventure-movie tone the later games built on.",
"Metal Gear Solid Delta: Snake Eater":"Naked Snake is sent into Soviet jungle territory to extract a defecting scientist, only for the mission to collapse into a betrayal that reframes his entire career and the organization he serves. It's the series' origin story for Big Boss, told as a Cold War espionage tragedy as much as an action game.",
"Death's Door":"A crow working for an afterlife bureaucracy that collects the souls of the dead is sent after an unusually powerful soul, only to discover something is interfering with the natural order of death itself. It's a tightly-scoped Zelda-inspired adventure with a surprisingly melancholy undercurrent about mortality and bureaucracy.",
"Tunic":"A small fox wakes up alone on a mysterious island with no memory and no language the player can read, piecing together both the world's secrets and the game's own instruction manual — found as collectible in-world pages — as they explore. The story is almost entirely environmental and deliberately obscured.",
"Silent Hill f":"Set in 1960s rural Japan, a high school girl named Hinako finds her hometown overtaken by fog and grotesque, flower-choked monsters as the people around her transform into something else entirely. Like other Silent Hill entries, the horror is tied directly to Hinako's own unspoken feelings about her family and the small, suffocating town she's never been able to leave.",
"Nier Replicant ver.1.22474487139...":"A young man searches for a cure for his sister's fatal illness in a crumbling world full of shade-like monsters, aided by a sardonic talking book. It's a prequel to Automata, and its ending is infamous for recontextualizing everything that came before it once the full picture is in view.",
"Octopath Traveler":"Eight entirely separate protagonists — a thief, a dancer, a scholar, a cleric, and others — each pursue their own personal, unconnected quest across the same continent, with the player choosing who to follow and in what order. The stories only lightly intersect, deliberately built as eight short novels happening in the same world rather than one combined plot.",
"Dragon Quest Builders 2":"A shipwrecked builder, condemned by a faction that outlaws construction, washes up on an island and starts rebuilding civilization town by town with a young apprentice at their side. It mixes classic Dragon Quest lore with a Minecraft-style building loop, each new island adding its own self-contained story.",
"One Piece Odyssey":"The Straw Hat crew is shipwrecked on a mysterious island that strips them of their powers and splits the group up, forcing Luffy and friends to survive using only courage and teamwork until they're reunited. It's an original story not drawn from the manga, designed as a love letter revisiting the crew's history along the way.",
"Nine Sols":"A Taoist-punk Metroidvania following an aging warrior seeking revenge against the god-like Sols who conquered his people, using a deflect-heavy sword style built around precise parries. The story weaves Taoist philosophy and a melancholy tone through what's otherwise a brutal, combat-focused revenge tale.",
"Blasphemous":"A silent, mute Penitent One awakens in a cursed, miracle-ravaged land styled after Spanish Catholic iconography, fighting through grotesque religious horror to end a divine punishment called the Miracle. The world is told almost entirely through item descriptions and NPC riddles in the series' signature oppressive, holy-relic aesthetic.",
"Blasphemous 2":"The Penitent One is pulled from his rest once more as a new threat rises in the cursed land of Cvstodia, this time wielding three distinct weapons tied to three different combat styles. It continues the original's grim religious-horror tone while expanding the mythology around the world's twisted saints and miracles.",
"Ender Lilies: Quietus of the Knights":"A young priestess with the power to purify corrupted spirits wakes in a kingdom destroyed by an endless rain that turns the dead into monsters. She's guided by the spirit of a fallen knight as she purifies — and absorbs the combat abilities of — the fallen warriors she defeats, slowly uncovering what caused the kingdom's fall.",
"Signalis":"A technician android searches a derelict, nightmare-logic facility for her lost partner, uncovering cosmic horror and a grief-soaked mystery clearly inspired by classic survival horror and Eastern European sci-fi aesthetics. The story is deliberately cryptic, told through dream-logic sequences as much as direct exposition.",
"Chicory: A Colorful Tale":"A janitor dog borrows a magic paintbrush after the land's color mysteriously vanishes, and has to literally repaint the entire world while confronting crushing self-doubt about whether they're worthy of the brush at all. It's an unusually candid story about creative anxiety wrapped in a cheerful, Zelda-like adventure.",
"Cult of the Lamb":"A sacrificed lamb is revived by a mysterious stranger and tasked with building a loyal cult of followers in his name, mixing roguelike dungeon runs with base-building and some genuinely dark choices about how far the player is willing to go for their new flock.",
"Cocoon":"A silent insect-like being journeys through a series of nested, interconnected worlds carried inside glowing orbs, solving puzzles that require moving between those worlds and understanding how they affect each other. The story is told with almost no words at all, relying entirely on the player piecing together what's happening.",
"Neva":"A young woman and a wolf cub she's bonded with travel through a dying, seasonally-shifting world over the course of a year, with the wolf growing from a helpless pup into a full-grown companion as the journey goes on. It's a wordless, painterly story about loss and growing up too fast.",
"Gris":"A young woman who has lost her voice travels through a series of watercolor landscapes representing stages of grief, slowly regaining color and ability as she processes a profound personal loss. The story is told entirely without dialogue, through environmental metaphor and visual transformation.",
"Unpacking":"Told entirely through unpacking boxes into different homes across someone's life — from childhood bedroom to first apartment to shared home — the story emerges purely from what possessions appear, change, and disappear between each move. There's no dialogue at all; the belongings themselves tell the story.",
"Bugsnax":"A journalist travels to a remote island to investigate reports of half-snack, half-bug creatures called Bugsnax, only to find the island's few inhabitants changed in increasingly unsettling ways by eating them. It starts as a cheerful creature-catching game before turning into something stranger and darker than its colorful surface suggests.",
"A Way Out":"Two convicts, Leo and Vincent, break out of prison together and have to rely on each other — and on two simultaneous players — through a Southern-fried crime story about debt, revenge, and an uneasy partnership that was never meant to last past the escape.",
"The Dark Pictures Anthology: House of Ashes":"A joint US-Iraqi military squad is trapped underground in an ancient Sumerian temple after an earthquake, forced into an uneasy truce when they realize something much older than either army's conflict still lives down there. Every character can die permanently based on player choices, changing who survives to the end.",
"The Dark Pictures Anthology: The Devil in Me":"A documentary film crew investigating a serial killer museum modeled after H.H. Holmes's real 'Murder Castle' realize too late that their host has built an exact, fully mechanized replica for a very specific purpose. Like other Dark Pictures entries, any character's choices can get them killed off for good.",
"Amnesia: The Bunker":"A WWI soldier trapped in an underground bunker has to manage a generator for light while something inhuman stalks the dark tunnels around him, in an open, systemic take on the Amnesia series' usual scripted horror. The power management itself becomes as much a threat as the monster.",
"Atomic Heart":"Set in an alternate Soviet Union where 1950s robotics went far beyond reality, a KGB agent investigates a mysterious signal that's turned the country's household robots murderously hostile. It mixes BioShock-style retrofuturism with Soviet iconography for a violently strange alternate history.",
"Lethal Company":"A crew of underpaid contractors are sent to scavenge abandoned, monster-infested moons to meet an ever-rising sales quota for a shadowy company, with almost no story beyond the pitch-black corporate satire implied by that premise. Most of the 'story' comes from whatever chaos unfolds in each co-op run.",
"Sons of the Forest":"A team is sent to a remote island to find a missing billionaire, only to crash-land and discover the island is home to a cannibalistic, mutated population and buried secrets tied to a hidden research facility. It's a direct sequel to The Forest, continuing that game's survival-horror premise with a new cast.",
"Manor Lords":"A medieval settlement-builder with no fixed plot, letting the player grow a single village into a full medieval county through farming, trade, and historically-grounded warfare. Any narrative comes entirely from the player's own choices about how their settlement develops.",
"Astro Bot":"A cheerful mascot platformer where Astro Bot pilots a ship shattered across a galaxy of planets, rescuing scattered robot crew members — many styled after other PlayStation franchises — to rebuild it. The 'story' is a thin, joyful excuse for level-to-level platforming celebrating PlayStation's history.",
"Metaphor: ReFantazio":"In a fantasy kingdom thrown into chaos after the king's assassination, an outcast protagonist enters a royal selection tournament for the throne while also chasing down the actual assassin. It mixes the Persona team's social-link structure with a full original fantasy setting instead of modern-day Japan.",
"Forspoken":"A young woman from modern-day New York is pulled through a magical cuff into the fantasy realm of Athia, gaining spellcasting powers just as the realm's ruling Tantas descend into a corrupting madness called the Break. She has to navigate a world that sees her as an outsider while trying to find a way home.",
"Armored Core VI: Fires of Rubicon":"A mercenary mech pilot is hired to fight over the rights to a planet whose destroyed ecosystem accidentally created a priceless, world-changing energy resource. Corporate factions constantly shift alliances throughout, and the story is told mostly through terse radio chatter between missions rather than cutscenes.",
"Wanderstop":"A once-unstoppable warrior who can no longer fight finds herself running a quiet forest tea shop instead, forced to sit with failure and identity loss in a game explicitly about burnout rather than victory. It's a deliberately slow, introspective departure from the genre its creators are known for.",
"Hades II":"Following Zagreus's story, his sister Melinoë takes up the fight against Chronos, the Titan of Time who has overthrown the Underworld itself. It continues the original's roguelike structure and relationship-building dialogue, now set against an even more personal, mythologically deeper family conflict.",
"Journey":"A robed traveler crosses a vast desert toward a distant mountain, encountering the ruins of a fallen civilization and occasionally crossing paths with another anonymous player along the way. Nearly wordless, the story is carried entirely through the journey's visual and emotional arc rather than dialogue.",
"Inside":"A boy sneaks through a bleak, monochrome industrial dystopia pursued by searchlights and masked figures, with no dialogue or explanation offered for what's happening or why. The story reveals itself gradually through disturbing imagery, building to one of the more talked-about final twists in the genre.",
"Little Nightmares II":"A boy named Mono teams up with Six, the girl from the first game, to escape a world of grotesque adult figures twisted by a mysterious broadcasting Signal Tower. Like the first game, the horror comes from the player's small size against an oversized, hostile world.",
"Alien: Isolation":"Amanda Ripley, daughter of the original Alien films' Ellen Ripley, boards a remote space station searching for answers about her mother's disappearance, only to find it stalked by a single, near-unkillable Xenomorph. The game is built entirely around that one relentless threat rather than wave after wave of expendable enemies.",
"Batman: Arkham Knight":"Batman faces a full criminal uprising on Halloween night as Scarecrow unites nearly every major Gotham villain, alongside a mysterious new threat calling himself the Arkham Knight who seems to know Batman personally. It closes out the Arkham trilogy's storyline, pushing Batman's grip on his own sanity harder than the previous games did.",
"Darkest Dungeon":"An heir inherits a cursed, monster-infested estate from an ancestor whose own reckless excavations unleashed the horror in the first place, and has to send expendable bands of adventurers into the dark to reclaim it. The game is explicitly built around stress and sanity breaking down the longer characters stay in the dark.",
"Divinity: Original Sin 2":"A party of Sourcerers — people able to wield a forbidden form of magic — are hunted by an order meant to exterminate them, all while a far larger god-level conflict over the source of that magic unfolds around them. It's built for deep player choice, with companion origin stories that change the plot depending on who's played.",
"Little Nightmares":"A small girl named Six escapes captivity aboard a vast, grotesque vessel called the Maw, sneaking past monstrous, gluttonous adult figures who see children purely as food. Like its sequel, it tells its story almost entirely through unsettling visuals and scale rather than dialogue.",
"Mass Effect Legendary Edition":"A remastered trilogy following Commander Shepard's fight to unite the galaxy's species against the Reapers, an ancient machine threat that returns to wipe out advanced civilization on a cyclical timer. Choices and relationships carry across all three games, letting one Shepard's decisions ripple through the entire saga.",
"Persona 4 Golden":"A transfer student in a rural Japanese town investigates a string of murders tied to a mysterious world inside the television, where the town's hidden secrets and buried truths take monstrous physical form. It mixes slice-of-life social sim with dungeon-crawling combat built around confronting what people hide about themselves.",
"Psychonauts 2":"Psychic trainee Raz dives into the literal minds of his mentors at a secret spy agency to stop a mole from sabotaging the organization from within, with each level a surreal physical manifestation of whichever character's psyche he's exploring. It continues directly from the first game's story and a side VR chapter.",
"Resident Evil 3":"A remake following Jill Valentine's escape from Raccoon City as it falls apart during the same outbreak as Resident Evil 2, now relentlessly pursued by an advanced bioweapon called Nemesis. It runs in parallel with RE2's timeline, showing a different side of the same collapsing city.",
"Resident Evil 7: Biohazard":"Ethan Winters searches for his missing wife and ends up trapped in a decaying Louisiana plantation home owned by the monstrous Baker family, whose horrifying behavior is tied to a mold-based bioweapon infecting the property. It returned the series to first-person, claustrophobic horror after several more action-focused entries.",
"Hellblade: Senua's Sacrifice":"A Celtic warrior named Senua, who experiences psychosis, journeys into Norse hell to bargain for her dead lover's soul, with her hallucinations and voices woven directly into the game's puzzles and combat rather than treated as a separate horror element. It was developed with input from neuroscientists and people with lived experience of psychosis.",
"Hellblade II: Senua's Saga":"Senua returns, continuing to confront her trauma and psychosis while journeying through Icelandic-inspired lands gripped by slavers and apparent giants, pushing further into the first game's unflinching, cinematic treatment of mental illness. It trades some of the first game's combat focus for a more narrative-driven pace.",
"Dragon's Dogma: Dark Arisen":"The player's heart is stolen by a dragon, leaving them an 'Arisen' bonded to otherworldly Pawn companions who speak of a destiny they never asked for. It's a classic fantasy quest structure wrapped around unusually physical, systemic combat against colossal monsters.",
"Kingdom Hearts III":"Sora, Donald, and Goofy travel across a mix of Disney and original Kingdom Hearts worlds to gather the seven Guardians of Light before Master Xehanort can set his apocalyptic plan into motion. It serves as the conclusion to the 'Dark Seeker Saga' that began with the first game.",
"Brothers: A Tale of Two Sons":"Two brothers set out to find a cure for their dying father, controlled simultaneously with each analog stick representing one brother, building their relationship entirely through shared physical problem-solving. The ending uses that same two-stick control scheme to deliver one of the medium's more quietly devastating moments.",
"Undertale":"A child falls into an underground world of monsters and discovers they can resolve every conflict through mercy instead of violence, with the game explicitly tracking and reacting to whether the player chooses to fight or befriend. Nearly every character remembers and responds to how the player has treated them.",
"The Stanley Parable: Ultra Deluxe":"An office worker named Stanley follows — or defies — the instructions of an all-knowing narrator, with the 'story' entirely built around what happens when the player does or doesn't do what they're told. It's less a single narrative than dozens of branching, self-aware endings commenting on choice itself.",
"The Talos Principle":"An AI awakens in a simulated, ancient-ruins environment and is tasked by a godlike voice with solving puzzles while slowly realizing the true, much stranger nature of its own existence. It uses its puzzle structure to ask genuinely philosophical questions about consciousness and free will.",
"Spelunky 2":"A direct sequel to the original cave-diving roguelike platformer, sending a new generation of spelunkers into a procedurally generated underworld in search of treasure and a missing moon base. The thin plot mostly exists to connect one brutal, trap-filled run to the next.",
"Fallout: New Vegas":"A courier left for dead in the Mojave Wasteland after being shot over a mysterious package recovers and sets out for revenge, getting pulled into a three-way power struggle over the city of New Vegas along the way. It's known for letting the player's choices meaningfully reshape which faction ends up controlling the region.",
"Titanfall 2":"A rifleman named Jack Cooper is thrust into piloting an AI-controlled Titan mech named BT after his mentor is killed, forming an unlikely bond with the machine over a mission behind enemy lines. The campaign is built around that pilot-and-Titan relationship as much as the series' fast wall-running combat.",
"Danganronpa: Trigger Happy Havoc":"Fifteen students are trapped in a school by a sadistic robotic bear who forces them to murder each other and get away with it in rigged trials, or be executed themselves. It's a visual novel built around courtroom-style deduction, where getting away with murder is explicitly the villain's goal for the cast.",
"Catherine: Full Body":"A man torn between his longtime girlfriend and a seductive new woman starts having nightmares where he must climb a collapsing tower of blocks, with the dreams directly reflecting his anxiety about commitment and choice. The block-climbing puzzles and the relationship drama are built to comment on each other.",
"The Great Ace Attorney Chronicles":"A prequel duology following a young Ryunosuke Naruhodo, ancestor to the main series' Phoenix Wright, as he travels between Japan and Victorian-era England navigating a legal system openly stacked against him as a foreigner. It leans into a Sherlock Holmes-adjacent mystery flavor absent from the core series."
};
function similarGames(data){
  return SEED
    .filter(g=>g[0]!==data.title)
    .map(g=>({idx:SEED.indexOf(g),title:g[0],studio:g[1],rating:g[2],tags:g[4],shared:g[4].filter(t=>data.tags.includes(t)).length+(g[1]===data.studio?0.5:0)}))
    .filter(g=>g.shared>0)
    .sort((a,b)=> b.shared-a.shared || b.rating-a.rating)
    .slice(0,6);
}

// ---------- Generated cover art (original design — no real box art or images) ----------
var __cvN=0;
function coverSVG(title,tags,studio,bg){
  const esc=s=>String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;').replace(/'/g,'&#39;');
  let hs=2166136261;for(let i=0;i<title.length;i++){hs^=title.charCodeAt(i);hs=Math.imul(hs,16777619);}hs=hs>>>0;
  const base={Shooter:8,Action:18,RPG:268,Adventure:178,Horror:135,Racing:42,Fighting:350,Platformer:205,Sim:152,Puzzle:288,Strategy:218,Sports:118};
  const g=(tags&&tags[0])||'Action';const hue=((base[g]!=null?base[g]:200)+((hs%41)-20)+360)%360;
  const hue2=(hue+28+(hs>>>8)%30)%360;
  const id='cv'+(__cvN=(__cvN||0)+1);
  const c1='hsl('+hue+',78%,34%)',c2='hsl('+hue2+',70%,10%)',acc='hsl('+hue+',95%,62%)';
  // title parsing
  let t=String(title).trim(),year='';
  const ym=t.match(/\s*\((\d{4})\)\s*$/);if(ym){year=ym[1];t=t.replace(ym[0],'');}
  let series='',main=t;
  const ci=t.indexOf(': ');if(ci>0&&ci<=26){series=t.slice(0,ci);main=t.slice(ci+2);}
  let num='';const nm=main.match(/\s+(II|III|IV|V|VI|VII|VIII|IX|X|XI|XII|XIII|XIV|XV|XVI|[2-9]|1\d)$/);
  if(nm&&main.length>nm[0].length+2){num=nm[1];main=main.slice(0,main.length-nm[0].length);}
  const words=main.toUpperCase().split(/\s+/).filter(Boolean);const lines=[];let cur='';
  for(const w of words){if(cur&&(cur+' '+w).length>12){lines.push(cur);cur=w;}else cur=cur?cur+' '+w:w;}
  if(cur)lines.push(cur);
  while(lines.length>3){const a=lines.pop();lines[lines.length-1]+=' '+a;}
  const base0=lines.length===1?40:lines.length===2?34:28;
  const L=lines.map(s=>{const fs=Math.max(15,Math.min(base0,264/(s.length*0.6)));return {s,fs,w:Math.min(264,s.length*fs*0.6)};});
  let H=(series?22:0)+L.reduce((a,l)=>a+l.fs+5,0)+(num?66:0);
  let y=bg?Math.max(118,290-H):Math.max(212,368-H);const HH=bg?490:400;
  let out='';
  if(series){const sw=Math.min(250,series.length*8.5);out+='<text x="150" y="'+(y+12)+'" text-anchor="middle" font-size="13" font-weight="700" fill="#fff" fill-opacity=".85" letter-spacing="2" textLength="'+sw+'" lengthAdjust="spacingAndGlyphs">'+esc(series.toUpperCase())+'</text>';y+=22;}
  for(const l of L){y+=l.fs;out+='<text x="150" y="'+y+'" text-anchor="middle" font-size="'+l.fs.toFixed(1)+'" font-weight="900" fill="#fff" textLength="'+l.w.toFixed(0)+'" lengthAdjust="spacingAndGlyphs" style="paint-order:stroke" stroke="#000" stroke-opacity=".35" stroke-width="2">'+esc(l.s)+'</text>';y+=5;}
  if(num){y+=58;out+='<text x="150" y="'+y+'" text-anchor="middle" font-size="62" font-weight="900" fill="'+acc+'" textLength="'+Math.min(200,num.length*40).toFixed(0)+'" lengthAdjust="spacingAndGlyphs" stroke="#000" stroke-opacity=".4" stroke-width="2" style="paint-order:stroke">'+esc(num)+'</text>';}
  const sty='fill="none" stroke="#fff" stroke-opacity=".28" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"';
  const E={
    Shooter:'<circle cx="150" cy="140" r="52" '+sty+'/><circle cx="150" cy="140" r="6" fill="#fff" fill-opacity=".35"/><path d="M150 70v36M150 174v36M80 140h36M184 140h36" '+sty+'/>',
    Action:'<path d="M95 80l110 120M205 80L95 200" '+sty+' stroke-width="9"/><circle cx="150" cy="140" r="14" '+sty+'/>',
    RPG:'<path d="M150 72l58 24v50c0 32-26 52-58 66-32-14-58-34-58-66V96z" '+sty+'/><path d="M150 100v80M118 130h64" '+sty+'/>',
    Adventure:'<path d="M150 70l16 54 54 16-54 16-16 54-16-54-54-16 54-16z" '+sty+'/><circle cx="150" cy="140" r="64" '+sty+' stroke-dasharray="4 10"/>',
    Horror:'<circle cx="150" cy="140" r="56" '+sty+'/><path d="M170 92a50 50 0 1 0 0 96a40 40 0 1 1 0-96z" fill="#fff" fill-opacity=".14"/>',
    Racing:'<path d="M96 190l54-70 54 70M96 150l54-70 54 70" '+sty+' stroke-width="8"/>',
    Fighting:'<path d="M150 70l14 44 46-8-30 36 30 36-46-8-14 44-14-44-46 8 30-36-30-36 46 8z" '+sty+'/>',
    Platformer:'<path d="M86 196h50v-36h50v-36h50" '+sty+' stroke-width="9"/><circle cx="112" cy="146" r="12" '+sty+'/>',
    Sim:'<path d="M150 74l56 32v66l-56 32-56-32v-66z" '+sty+'/><path d="M150 106l28 16v32l-28 16-28-16v-32z" '+sty+'/>',
    Puzzle:'<rect x="98" y="88" width="104" height="104" rx="10" '+sty+'/><rect x="98" y="88" width="104" height="104" rx="10" '+sty+' transform="rotate(45 150 140)"/>',
    Strategy:'<path d="M150 76l60 108H90z" '+sty+'/><circle cx="150" cy="150" r="14" '+sty+'/>',
    Sports:'<circle cx="150" cy="140" r="56" '+sty+'/><path d="M94 140h112M150 84c-28 30-28 82 0 112M150 84c28 30 28 82 0 112" '+sty+'/>'
  };
  const em=E[g]||E.Action;
  const rays='<path d="M150 140L-40 -20 40 -40zM150 140L340 -20 260 -40zM150 140L-60 260-60 190zM150 140L360 260 360 190z" fill="#fff" fill-opacity=".04"/>';
  return '<svg viewBox="0 0 300 '+HH+'" xmlns="http://www.w3.org/2000/svg" style="display:block;width:100%;height:auto" role="img" aria-label="Cover art for '+esc(title)+'" font-family="Impact,Arial Black,Helvetica Neue,Arial,sans-serif">'
   +'<defs><linearGradient id="'+id+'a" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="'+c1+'"/><stop offset="1" stop-color="'+c2+'"/></linearGradient>'
   +'<radialGradient id="'+id+'b" cx="50%" cy="35%" r="55%"><stop offset="0" stop-color="'+acc+'" stop-opacity=".55"/><stop offset="1" stop-color="'+acc+'" stop-opacity="0"/></radialGradient>'
   +'<linearGradient id="'+id+'c" x1="0" y1="0" x2="0" y2="1"><stop offset=".45" stop-color="#000" stop-opacity="0"/><stop offset="1" stop-color="#000" stop-opacity=".78"/></linearGradient></defs>'
   +'<rect width="300" height="'+HH+'" fill="url(#'+id+'a)"/><rect width="300" height="'+HH+'" fill="url(#'+id+'b)"/>'+rays+(bg?'<g transform="translate(0,-48)">'+em+'</g>':em)
   +'<rect width="300" height="'+HH+'" fill="url(#'+id+'c)"/>'
   +(bg?'':'<rect x="0" y="0" width="300" height="34" fill="#000" fill-opacity=".45"/><text x="14" y="22" font-size="10" font-weight="700" fill="#fff" fill-opacity=".8" letter-spacing="2.5">PS5</text>')
   +(year&&!bg?'<text x="286" y="22" text-anchor="end" font-size="10" font-weight="700" fill="#fff" fill-opacity=".7" letter-spacing="1.5">'+esc(year)+'</text>':'')
   +out
   +(bg?'':'<text x="150" y="391" text-anchor="middle" font-size="8.5" font-weight="700" fill="#fff" fill-opacity=".5" letter-spacing="2">'+esc(String(studio||'').toUpperCase().slice(0,34))+'</text>')
   +(bg?'':'<rect x="1.5" y="1.5" width="297" height="397" fill="none" stroke="#fff" stroke-opacity=".18" stroke-width="3"/>')+'</svg>';
}
function coverBg(title,tags,studio){return `url('data:image/svg+xml,${encodeURIComponent(coverSVG(title,tags,studio,true))}') center/cover no-repeat`;}
function renderReview(data,rev){
  const stars=n=>'★'.repeat(n)+'☆'.repeat(5-n);
  const li=arr=>`<ul class="rev-list">${arr.map(v=>`<li>${v}</li>`).join('')}</ul>`;
  const sim=similarGames(data);
  return `
    <h3>${data.title}</h3>
    <div class="sub">${data.studio}</div>
    <div class="stat-row" style="margin:8px 0 14px;">${data.tags.map(t=>`<span>${t}</span>`).join('')}</div>
    <a href="https://store.playstation.com/en-us/search/${encodeURIComponent(data.title)}" target="_blank" rel="noopener noreferrer" class="primary-btn" style="display:block;text-align:center;text-decoration:none;margin:0 0 10px;">🛍️ Open in PlayStation Store</a>
    <a href="https://www.youtube.com/results?search_query=${encodeURIComponent(data.title+' official trailer')}" target="_blank" rel="noopener noreferrer" class="primary-btn" style="display:block;text-align:center;text-decoration:none;margin:0 0 4px;background:#171a24;color:#fff;border:1px solid rgba(255,255,255,.14);box-shadow:none;">▶ Watch trailer on YouTube</a>
    <div class="sim-hint" style="margin:0 0 16px;text-align:center;">Opens YouTube — trailers belong to their publishers</div>
    <div class="rev-sec"><div class="rev-h">📖 Story</div><p class="rev-p">${STORY_OVERRIDES[data.title]||data.desc}</p>${beatLine(data.title)}</div>
    <div class="stat-row">
      <span>⭐ ${(data.rating/20).toFixed(1)}/5</span>
      <span>🎮 PS5</span>
      <span>⏱️ ~${data.playtime} hrs</span>
      <span>💾 ~${rev.storageGB} GB</span>
    </div>
    <div class="rev-sec"><div class="rev-h">🎮 Gameplay Feel</div><div class="stat-row" style="margin:0;">${rev.feel.map(f=>`<span>${f}</span>`).join('')}</div></div>
    <div class="rev-sec"><div class="rev-h">🔥 What it's like</div><p class="rev-p">${rev.vibeLine}</p></div>
    <div class="rev-sec"><div class="rev-h">🎯 What you actually do</div>${li(rev.verbs)}</div>
    <div class="rev-sec"><div class="rev-h">🌎 The world</div><p class="rev-p">${rev.world}</p></div>
    <div class="rev-sec"><div class="rev-h">⚔️ Combat</div><p class="rev-p">${rev.combat}</p></div>
    <div class="rev-sec"><div class="rev-h">🧰 Customization</div>${li(rev.custom)}</div>
    <div class="rev-sec"><div class="rev-h">🗺️ Exploration<span class="stars">${stars(rev.exploreStars)}</span></div>${li(rev.exploreBullets)}</div>
    <div class="rev-sec"><div class="rev-h">🎮 PS5 Features</div>${li(['Haptic feedback','Adaptive triggers','3D audio','Performance/graphics modes'])}</div>
    <div class="rev-sec"><div class="rev-h">👥 Multiplayer</div><p class="rev-p">${data.mode.short} — ${data.mode.detail}</p></div>
    <div class="rev-sec"><div class="rev-h">📈 Progression</div><p class="rev-p">${rev.progression}</p></div>
    <div class="rev-sec"><div class="rev-h">♻️ Replayability<span class="stars">${stars(rev.replayStars)}</span></div>${li(rev.replayBullets)}</div>
    <div class="rev-sec"><div class="rev-h">😎 Vibe</div>${VIBE_DIMS.map(d=>`<div class="vibe-row">${d}<b>${rev.vibe[d]}</b></div>`).join('')}</div>
    <div class="rev-sec"><div class="rev-h">🏆 Trophies<span class="stars" style="color:var(--sub);">${rev.trophies.total} total</span></div>
      <div class="stat-row" style="margin:2px 0 10px;"><span>🥉 ${rev.trophies.bronze}</span><span>🥈 ${rev.trophies.silver}</span><span>🥇 ${rev.trophies.gold}</span><span>🏆 ${rev.trophies.plat} Platinum</span></div>
      ${li(rev.trophies.names)}</div>
    <div class="rev-sec"><div class="rev-h">💡 Tips</div>${li(rev.tips)}</div>
    ${sim.length?`<div class="rev-sec"><div class="rev-h">🧭 More like this, in this app</div><div class="sim-hint">Tap a game to open it</div>${sim.map(s=>`<div class="sim-row" data-idx="${s.idx}"><div class="sim-cv">${coverSVG(s.title,s.tags,s.studio)}</div><div class="sim-t"><b>${s.title}</b><span>${s.studio} — ★ ${s.rating.toFixed(1)} — ${s.tags.join(' · ')}</span></div><div class="sim-go">›</div></div>`).join('')}</div>`:''}
  `;
}
function openReview(data,index){
  document.getElementById('rBody').innerHTML=renderReview(data,reviewFor(data,index));
  reviewWrap.classList.add('open');
  const rb=document.getElementById('rBody');
  rb.querySelectorAll('.sim-row').forEach(row=>{row.onclick=()=>{const i=Number(row.dataset.idx);openReview(dataFor(i),i);rb.scrollTop=0;if(rb.parentElement)rb.parentElement.scrollTop=0;};});
}
document.getElementById('closeReview').onclick=()=>reviewWrap.classList.remove('open');
reviewWrap.onclick=e=>{if(e.target===reviewWrap)reviewWrap.classList.remove('open');};

// search & filter panel
const filterWrap=document.getElementById('filterWrap');
const FILTER_GENRES=[...GENRES,'Sports'];
document.getElementById('genreChips').innerHTML=FILTER_GENRES.map(g=>`<span class="chip-toggle" data-genre="${g}">${g}</span>`).join('');
const companies=[...new Set(SEED.map(s=>s[1]))].sort();
document.getElementById('companySelect').innerHTML='<option value="">All Companies</option>'+companies.map(c=>`<option value="${c}">${c}</option>`).join('');
document.getElementById('openFilter').onclick=()=>filterWrap.classList.add('open');
document.getElementById('closeFilter').onclick=()=>filterWrap.classList.remove('open');
filterWrap.onclick=e=>{if(e.target===filterWrap)filterWrap.classList.remove('open');};
document.getElementById('genreChips').addEventListener('click',e=>{
  const chip=e.target.closest('.chip-toggle');if(!chip)return;
  const g=chip.dataset.genre;
  if(filters.genres.has(g))filters.genres.delete(g);else filters.genres.add(g);
  chip.classList.toggle('active',filters.genres.has(g));
  applyFilters();
});
document.getElementById('companySelect').onchange=e=>{filters.company=e.target.value||null;applyFilters();};
let searchDebounce;
document.getElementById('searchInput').oninput=e=>{
  clearTimeout(searchDebounce);
  const val=e.target.value;
  searchDebounce=setTimeout(()=>{filters.q=val.trim();applyFilters();},250);
};
const minPriceInput=document.getElementById('minPriceInput'),maxPriceInput=document.getElementById('maxPriceInput');
const minPriceVal=document.getElementById('minPriceVal'),maxPriceVal=document.getElementById('maxPriceVal');
function updatePriceLabels(){
  minPriceVal.textContent='$'+minPriceInput.value;
  maxPriceVal.textContent='$'+maxPriceInput.value+(Number(maxPriceInput.value)>=PRICE_CEIL?'+':'');
}
function onPriceChange(){
  let lo=Number(minPriceInput.value),hi=Number(maxPriceInput.value);
  if(lo>hi){minPriceInput.value=hi;maxPriceInput.value=lo;[lo,hi]=[hi,lo];}
  filters.minPrice=lo;filters.maxPrice=hi;
  updatePriceLabels();
  applyFilters();
}
minPriceInput.oninput=updatePriceLabels;maxPriceInput.oninput=updatePriceLabels;
minPriceInput.onchange=onPriceChange;maxPriceInput.onchange=onPriceChange;
document.getElementById('lengthSelect').onchange=e=>{filters.length=e.target.value;applyFilters();};
document.getElementById('clearFilters').onclick=()=>{
  filters={q:'',genres:new Set(),company:null,length:'',minPrice:PRICE_FLOOR,maxPrice:PRICE_CEIL};
  document.getElementById('lengthSelect').value='';
  document.getElementById('searchInput').value='';
  document.getElementById('companySelect').value='';
  document.querySelectorAll('#genreChips .chip-toggle').forEach(c=>c.classList.remove('active'));
  minPriceInput.value=PRICE_FLOOR;maxPriceInput.value=PRICE_CEIL;updatePriceLabels();
  applyFilters();
};

// first-open tutorial — per-browser, via localStorage (a published page can't see other viewers' storage)
const tutorialWrap=document.getElementById('tutorialWrap');
try{
  if(!localStorage.getItem('deck_tutorial_seen'))tutorialWrap.classList.add('open');
}catch(e){tutorialWrap.classList.add('open');}
document.getElementById('closeTutorial').onclick=()=>{
  tutorialWrap.classList.remove('open');
  try{localStorage.setItem('deck_tutorial_seen','1');}catch(e){}
};

// bottom tab bar: Feed / Library / Strategy
const feedEl=document.getElementById('feed'),brandEl=document.querySelector('.brand');
const libraryView=document.getElementById('libraryView');
const strategyView=document.getElementById('strategyView');
function showTab(name){
  document.querySelectorAll('.tab').forEach(t=>t.classList.toggle('active',t.dataset.tab===name));
  feedEl.style.display=name==='feed'?'':'none';
  brandEl.style.display=name==='feed'?'':'none';
  libraryView.style.display=name==='library'?'block':'none';
  strategyView.style.display=name==='strategy'?'block':'none';
  if(name==='library')renderLibrary();
  if(name==='strategy' && !strategyBuilt){renderStrategy();strategyBuilt=true;initSiegeCoach();startQuiz();}
}
document.querySelectorAll('.tab').forEach(t=>t.onclick=()=>showTab(t.dataset.tab));
let strategyBuilt=false;

// Strategy — Rainbow Six Siege, general concepts only (see disclaimer note rendered below)
const SIEGE_MAPS=[
 {name:"Bank",notes:["The vault is the map's signature hard objective — defenders typically stack reinforcements around its outer walls and watch the main-floor and basement stairwells, its two primary access routes.","Attackers generally need a hard breacher to open the vault directly rather than relying on soft walls alone."]},
 {name:"Clubhouse",notes:["A wide, two-building layout — the boiler-room basement is a distinctive read, and defenders benefit from covering both the connecting bridge and the back door at once.","Long yard sightlines reward attackers who drone early before committing to a push."]},
 {name:"Oregon",notes:["A dense, room-heavy building that favors close-range defenders and stairwell traps — the tower and kitchen areas are classic examples of tight verticality.","Attackers should expect to clear several small rooms rather than push one open site."]},
 {name:"Consulate",notes:["Tellers is one of the game's most recognized sites, with a semi-open exterior — defenders commonly watch the garage and the exterior windows facing the courtyard.","The open courtyard rewards early drone coverage before attackers commit to an entry point."]},
 {name:"Chalet",notes:["A snowy estate with strong exterior sightlines — defenders often reinforce walls facing open ground and keep an eye on the balconies.","Smoke or flash utility helps attackers cross the open yard safely."]},
 {name:"Kafe Dostoyevsky",notes:["A vertical three-floor map where rotation matters as much as any single site — defenders commonly deny the main staircase and the dumbwaiter shortcut.","Attackers often split entry across two floors at once to divide defender attention."]},
 {name:"Coastline",notes:["A resort map split across a casino and a hookah lounge, joined by an open outdoor bridge — defenders often deny that bridge and watch the pool-facing windows.","The open pool courtyard rewards attackers who clear sightlines with utility before crossing it."]},
 {name:"Border",notes:["A customs-and-warehouse complex mixing tight corridors with open cargo bays — the armory and server room are two of its most frequently contested sites.","Breaching multiple walls at once helps attackers split defender attention across the complex's size."]},
 {name:"Skyscraper",notes:["A vertically-split tower with distinct site clusters on different floors — defenders generally commit early to one general area rather than spreading thin across the whole building.","The map's many windows and balconies give attackers unconventional entry options beyond the obvious doors."]},
 {name:"Villa",notes:["A gothic manor mixing wide, open rooms with tighter back hallways — the trophy room's multiple entry angles make it a frequent objective.","Clearing wide rooms methodically matters here, since flanking routes are common."]},
 {name:"House",notes:["One of the original launch maps — a small, dense family home where nearly every room connects to another, so defenders can't isolate a single hold.","Its compact size rewards early aggression from attackers and tight coordination from defenders, since there's little room to fall back."]},
 {name:"Theme Park",notes:["A carnival-and-factory complex split between an outdoor midway and an indoor processing plant — defenders commonly split attention between the factory's tight aisles and the open lot outside.","Attackers benefit from clearing exterior sightlines before committing to the factory's narrower halls."]},
 {name:"Outback",notes:["A roadhouse-and-barn property with wide gaps between buildings — defenders often watch the connecting bridge and the open yard between the main house and the barn.","The distance between structures rewards attackers who use utility to cross safely rather than sprinting the open ground."]},
 {name:"Favela",notes:["A vertical hillside favela with lots of small rooftops and tight stairwells — defenders benefit from covering the many rooftop entry points as much as ground-floor doors.","Its verticality means attackers have unusually many entry angles, including straight down from adjacent roofs."]},
 {name:"Yacht",notes:["A multi-deck luxury yacht where the engine room and the lower decks are frequent hard objectives — defenders often deny the stairwells connecting decks rather than spreading across the whole boat.","The open pool deck at the stern gives attackers an exposed but fast route between levels."]}
];
const SIEGE_OPERATORS=[
 {n:"Sledge",side:"Attack",d:"Uses a breaching hammer to punch through soft walls and hatches on the move, without needing a gadget charge — good for improvised entry points."},
 {n:"Thatcher",side:"Attack",d:"Disables nearby electronic defender gadgets with an EMP grenade, clearing the way for a breach before the defender can react."},
 {n:"Ash",side:"Attack",d:"Fires breaching rounds that punch a small hole through soft walls from a distance, favoring fast, aggressive entries."},
 {n:"Thermite",side:"Attack",d:"Places a charge that cuts through reinforced walls directly — a core hard-breach pick on objectives with fortified walls."},
 {n:"Twitch",side:"Attack",d:"Uses a drone-mounted shock launcher to destroy cameras and gadgets remotely, without needing to be near the objective."},
 {n:"Montagne",side:"Attack",d:"Carries an extendable ballistic shield that covers his whole body, useful for tanking a doorway or scouting a room without taking damage."},
 {n:"Fuze",side:"Attack",d:"Attaches a cluster charge to a wall or hatch that fires explosive submunitions into the room beyond, denying a space before entry."},
 {n:"Hibana",side:"Attack",d:"Fires small pellets that can breach reinforced walls in specific spots, giving more precise hard-breach options than a single Thermite charge."},
 {n:"Jackal",side:"Attack",d:"Tracks a defender's footprints to reveal their general location, useful for hunting down a roamer."},
 {n:"Ying",side:"Attack",d:"Throws discs that burst into a ring of flashes, useful for clearing multiple defenders or angles in a cluttered room at once."},
 {n:"Zofia",side:"Attack",d:"Carries concussion grenades and a launcher that can also breach soft walls, giving a flexible mix of entry and crowd control."},
 {n:"Buck",side:"Attack",d:"Has an under-barrel shotgun attachment that can punch holes through floors and soft walls to open unconventional angles."},
 {n:"Capitão",side:"Attack",d:"Fires crossbow bolts that either cause lingering damage through soft cover or a smoke screen, useful for area denial and cover."},
 {n:"Iana",side:"Attack",d:"Deploys a holographic decoy of herself to bait shots or draw attention while gathering information from a safer position."},
 {n:"Nomad",side:"Attack",d:"Throws airjab launchers that push players away from an area, useful for stopping a roamer from repositioning during a push."},
 {n:"Gridlock",side:"Attack",d:"Deploys spiked Trax Stingers that slow anyone crossing them, useful for covering a flank while the team pushes elsewhere."},
 {n:"Amaru",side:"Attack",d:"Uses a grapple hook to launch through a window and directly into a room, bypassing normal entry points entirely."},
 {n:"Flores",side:"Attack",d:"Deploys remote-detonated mini-drones that stick to surfaces, useful for baiting reactions or damaging gadgets from a distance."},
 {n:"Smoke",side:"Defense",d:"Deploys remote-detonated gas canisters that deal damage over time in a room, useful for denying an area or punishing a slow push."},
 {n:"Mute",side:"Defense",d:"Places jammers that block nearby drones, breaching charges, and other electronic gadgets from functioning."},
 {n:"Castle",side:"Defense",d:"Reinforces specific doorways with armor panels that can't be destroyed by normal means, forcing attackers to find another way in."},
 {n:"Pulse",side:"Defense",d:"Uses a heartbeat sensor that reveals enemy positions through walls, strong for tracking a push in real time."},
 {n:"Rook",side:"Defense",d:"Drops armor plates that give the whole team extra damage resistance for the round — a passive team-wide buff more than an active gadget."},
 {n:"Doc",side:"Defense",d:"Can heal and revive teammates from a distance with a stim pistol, useful for keeping an anchor alive under pressure."},
 {n:"Jäger",side:"Defense",d:"Deploys automated units that intercept incoming grenades and explosive projectiles before they land."},
 {n:"Bandit",side:"Defense",d:"Electrifies reinforced walls and gadgets, punishing attackers who try to breach or plant near them without clearing the trap first."},
 {n:"Frost",side:"Defense",d:"Places concealed floor traps that incapacitate anyone who steps on them, strong for punishing predictable attacker paths."},
 {n:"Valkyrie",side:"Defense",d:"Places sticky cameras in hard-to-reach spots for long-term intel on a site, beyond what a normal camera placement covers."},
 {n:"Caveira",side:"Defense",d:"Can silence her footsteps and interrogate downed attackers for the location of a teammate, built around roaming and information."},
 {n:"Echo",side:"Defense",d:"Deploys a drone that can pulse an area to disorient anyone nearby, useful for stalling a push or covering a rotate."},
 {n:"Mira",side:"Defense",d:"Installs one-way mirrored windows into reinforced walls, letting defenders see and shoot out without being seen back."},
 {n:"Vigil",side:"Defense",d:"Can turn invisible to enemy drones and cameras temporarily, useful for repositioning as a roamer without being spotted."},
 {n:"Maestro",side:"Defense",d:"Installs armored turret-cameras that can both spot and damage attackers, doubling as intel and a defensive weapon."},
 {n:"Alibi",side:"Defense",d:"Deploys holographic decoys of herself that can bait shots and reveal an attacker's position when triggered."},
 {n:"Clash",side:"Defense",d:"Carries a riot shield with a built-in shock ability, letting her push attackers back or slow them down rather than only holding a doorway."},
 {n:"Wamai",side:"Defense",d:"Places magnetic units that redirect incoming grenades and projectiles away from the objective."}
];
const SIEGE_ROLES=[
 {t:"Hard Breachers",d:"Operators who open reinforced walls and hatches directly, without needing to find a soft spot first — usually the first pick against any heavily fortified objective."},
 {t:"Gadget Clearers",d:"Operators focused on destroying cameras, barbed wire, and deployable shields from a distance, clearing a path before the team commits to a push."},
 {t:"Roamers",d:"Defenders who leave the objective early to delay attackers elsewhere on the map, trading site presence for information and early picks."},
 {t:"Anchors",d:"Defenders who stay on or near the objective for the full round, holding the site against the final push."},
 {t:"Intel Operators",d:"Both sides have operators built around gathering information — drones, cameras, and scanning gadgets that reveal enemy positions without direct contact."}
];
const SIEGE_PHASES=[
 {t:"Prep Phase (defense)",d:"Reinforce the walls that lead directly to the objective first, then decide how much of the rest of the map to give up as roam space versus hold."},
 {t:"Drone Phase (attack)",d:"Use the pre-round drone window to confirm reinforced walls and gadget placement — information gathered late in the round is far more valuable than a first guess."},
 {t:"Execution",d:"A coordinated push — smoke, breach, and entry together — generally beats trickling into a site one player at a time against a set-up defense."},
 {t:"Rotations",d:"Know at least one rotation hole to another part of the site before the round starts, rather than improvising one under fire."}
];
const SIEGE_GLOSSARY=[
 ["Breacher","An operator equipped to open reinforced walls or hatches, either directly or by destroying the reinforcement first."],
 ["Roam","Leaving the objective as a defender to hold territory or pick off attackers elsewhere on the map."],
 ["Entry Fragger","An attacking operator whose job is to be first through a breach and win the initial gunfight."],
 ["Rotate","Moving between positions or rooms, usually to respond to where the attackers are pushing."],
 ["Rotation Hole","A hole cut between two rooms or floors, used to move without exposing yourself in a hallway."],
 ["Hatch","An openable gap in a floor or ceiling connecting two vertical levels of a site."]
];
const SIEGE_TIPS={
"Sledge":"Open extra sightlines quietly and time entries with your hard breacher.",
"Thatcher":"EMP right before a breach so defender gadgets are off when the team commits.",
"Ash":"Breach from range, then peek the hole fast; best for early, aggressive entries.",
"Thermite":"Place charges where a teammate can cover them, since defenders will try to disrupt the wall.",
"Twitch":"Send the drone first to clear cameras and gadgets, then push while defenders are weakened.",
"Montagne":"Hold doorways and absorb fire so teammates can move up behind you.",
"Fuze":"Call out before deploying charges and use them when defenders are stacked in one room.",
"Hibana":"Open several small holes for more sightlines instead of one big commitment.",
"Jackal":"Scan footprints early to find roamers, then call their direction to the team.",
"Ying":"Flash through breaches and doorways just before you enter.",
"Zofia":"Stun a room before you push it, and use the launcher for flexible entry.",
"Buck":"Use vertical angles to pressure defenders from above or below.",
"Capitão":"Use smoke to cover plants and entries, and the damage bolts to flush out held angles.",
"Iana":"Send the decoy out to draw fire and gather info while you stay safe.",
"Nomad":"Guard a flank or plant so roamers can't get behind the team.",
"Gridlock":"Lay stingers on flank routes so anyone crossing them gets slowed.",
"Amaru":"Check the window before you reel in, and commit fast once you do.",
"Flores":"Use drones to bait reactions and chip gadgets before the real push.",
"Smoke":"Set gas in areas attackers will funnel through and trigger it when they commit.",
"Mute":"Jam walls attackers are most likely to breach and doors they will use.",
"Castle":"Armor key doorways so attackers must breach elsewhere or shoot through.",
"Pulse":"Scan often and call positions, especially behind your own team.",
"Rook":"Drop armor at the start of the round so everyone survives one more hit.",
"Doc":"Keep your anchors healed between fights and stay near them.",
"Jäger":"Place your system where grenades are most likely to land near the objective.",
"Bandit":"Set up early on reinforced walls near the objective to counter hard breachers.",
"Frost":"Hide traps behind doors or in likely entry paths.",
"Valkyrie":"Cover outside routes and flanks so your team knows what is coming.",
"Caveira":"Move quietly and hunt for isolated attackers, then rotate before the plant.",
"Echo":"Use the drone to disrupt plants and stall pushes.",
"Mira":"Set windows on walls attackers have not breached yet for early info.",
"Vigil":"Use invisibility to reposition unseen and flank a lone attacker.",
"Maestro":"Place turrets in hallways with clear lines and watch the feed.",
"Alibi":"Bait shots with decoys while your team punishes attackers who reveal themselves.",
"Clash":"Hold a doorway while pushing attackers back with your shield.",
"Wamai":"Place magnets near the objective to catch grenades and projectiles."
};
const SIEGE_PLANS={
"Bank":{sites:["Basement: CCTV Room & Lockers","1F: Teller's Office & Archives","2F: CEO Office & Executive Lounge"],a:"Bring hard-breach utility for the many hatches, and reach the basement through Garage or the dirt tunnel into Server; open ceilings near Open Area or Archives for vertical plays.",d:"Reinforce the common hatch spots first, and pair an intel operator like Mira or Pulse with a hard-breach counter like Kaid, since attackers usually carry several breaching charges here."},
"Clubhouse":{sites:["Basement: Church & Arsenal","1F: Bar & Stock Room","2F: Cash Room & CCTV Room","2F: Bedroom & Gym"],a:"Expect narrow chokepoints at Blue stairs into the basement and Garage/Construction into the top floor; clear tight rooms with utility before pushing in.",d:"Cover Blue and Red stairwells and the Garage entrance, since most pushes funnel through them; the Bar site has more exterior windows, so watch those as well as the doors."},
"Oregon":{a:"Split entries between floors so defenders can't hold both at once.",d:"Cover the tight hallways and watch the common flank routes."},
"Consulate":{sites:["2F: Consul Office & Meeting Room","1F: Lobby & Press Room","1F: Tellers & Basement Archives","Basement: Garage & Cafeteria"],a:"Expect entries from several angles at once due to the many windows; clear the stairwell sightlines before committing to a site.",d:"Three stairwells connect the floors, giving roamers a lot of ground to cover; anchor the site while a roamer contests whichever stairwell attackers commit to."},
"Chalet":{sites:["2F: Master Bedroom & Office","1F: Bar & Gaming Room","1F: Dining Room & Kitchen","Basement: Wine Cellar & Snowmobile Garage"],a:"Exterior visibility is limited by snow and terrain, so expect close engagements near entrances; clear the Bar or Kitchen with utility before pushing in.",d:"The basement site is naturally more protected with fewer entries, while the upstairs sites have more windows to watch; adjust your setup to whichever site is in play."},
"Kafe Dostoyevsky":{sites:["Basement: Kitchen Service & Kitchen Cooking","2F: Reading Room & Fireplace Hall","2F: Fireplace Hall & Mining Room","3F: Cocktail Lounge area"],a:"Three stairwells (red, white, main) connect the floors, and the roof skylight is a common way into the upper sites, so expect pushes from above as well as the ground.",d:"The map\u2019s size gives defenders room to roam and hide; watch the skylight and stairwells, since those are the main routes into the upper sites."},
"Coastline":{sites:["1F: Blue Bar & Sunrise Bar","1F: Hookah Lounge & Billiards Room","1F: Kitchen & Service Entrance","2F: Theater & Penthouse"],a:"There\u2019s no basement, so expect breachable ceilings and floors connecting rooms; bring hard breachers to open vertical lines rather than only doors.",d:"The bright, open layout gives fewer hiding spots than most maps, so lean on hatches and crossfires rather than pure ambush roaming."},
"Border":{a:"Clear the wide central rooms and use utility for the long sightlines.",d:"Hold the long hallways with crossfires, and rotate as attackers commit."},
"Skyscraper":{a:"Push through the vertical spaces and use windows and rappels for surprise angles.",d:"Contest the upper floors and anchor near the objective with good crossfires."},
"Villa":{sites:["2F: Aviator Room & Games Room","1F: Dining Room & Kitchen","1F: Living Room & Library","2F: Trophy Room & Statuary Room"],a:"This is one of the largest maps in the game, so rotations take longer; drone to confirm which side defenders are holding before you commit.",d:"Villa has historically favored defenders thanks to its size and dark color palette; use that size to set crossfires across multiple connected rooms."},
"House":{a:"Commit early and hard, since the compact layout gives defenders little room to fall back.",d:"Coordinate tightly and avoid getting isolated in single rooms."},
"Theme Park":{a:"Clear the exterior before committing to the factory's tight aisles.",d:"Split attention between the indoor aisles and the open lot outside."},
"Outback":{a:"Use utility to cross the open yard rather than sprinting.",d:"Watch the connecting bridge and the yard between buildings."},
"Favela":{a:"Use rooftop and window angles, including from adjacent buildings.",d:"Cover rooftop entries as well as ground-floor doors."},
"Yacht":{a:"Push through the stairwells and use the open stern deck for fast level changes.",d:"Deny the stairwells that connect the decks instead of spreading across the boat."}
};
SIEGE_OPERATORS.push(
{n:"IQ",side:"Attack",d:"Carries a detector that shows electronic gadgets through walls, making her a natural gadget hunter."},
{n:"Blitz",side:"Attack",d:"Uses a flash shield that blinds defenders at close range, built for aggressive room entries."},
{n:"Glaz",side:"Attack",d:"Uses a scoped rifle that can see through smoke, giving long-range picks across open spaces."},
{n:"Blackbeard",side:"Attack",d:"Mounts a shield on his rifle that protects his head from shots, useful for peeking long angles."},
{n:"Dokkaebi",side:"Attack",d:"Calls defenders' phones to ring and can then access cameras and reveal positions."},
{n:"Lion",side:"Attack",d:"Uses a drone scan that reveals defenders who are moving, punishing careless rotations."},
{n:"Finka",side:"Attack",d:"Boosts the team with a temporary health boost and revive, useful during a sustained push."},
{n:"Maverick",side:"Attack",d:"Uses a blowtorch to quietly cut small holes in reinforced walls, ideal for surprise sightlines."},
{n:"Nokk",side:"Attack",d:"Can move without being detected by cameras, helping her sneak past defender intel."},
{n:"Ace",side:"Attack",d:"Fires shaped charges that breach reinforced walls, providing another hard-breach option."},
{n:"Zero",side:"Attack",d:"Launches cameras that can damage defender gadgets and reveal their positions."},
{n:"Ram",side:"Attack",d:"Sends remote-controlled robots to destroy defender gadgets and clear barricades."},
{n:"Tachanka",side:"Defense",d:"Uses a mounted turret and heavy fire to lock down a lane or doorway."},
{n:"Kapkan",side:"Defense",d:"Places tripwire devices at entry points that punish attackers who walk through unaware."},
{n:"Ela",side:"Defense",d:"Deploys mines that stun and slow attackers, useful for stalling a push."},
{n:"Lesion",side:"Defense",d:"Places mines that poison anyone stepping on them, making attackers slow down and think."},
{n:"Kaid",side:"Defense",d:"Electrifies reinforced walls and barricades, discouraging breaches near the objective."},
{n:"Mozzie",side:"Defense",d:"Hijacks attacker drones and turns them into defender intel tools."},
{n:"Warden",side:"Defense",d:"Wears smart glasses that let him see through flashes and smoke, helping defend a doorway."},
{n:"Goyo",side:"Defense",d:"Places shield canisters that can explode, denying attackers a space."},
{n:"Oryx",side:"Defense",d:"Can dash through soft walls and vault quickly, good for catching attackers off guard."},
{n:"Melusi",side:"Defense",d:"Deploys sonic devices that slow attackers moving through nearby space."},
{n:"Aruni",side:"Defense",d:"Places laser gates that damage anyone passing through, reinforcing doorways."},
{n:"Thunderbird",side:"Defense",d:"Places healing stations that let teammates recover during a round."}
);
Object.assign(SIEGE_TIPS,{
"IQ":"Sweep the objective for gadgets before your team enters.",
"Blitz":"Use the flash shield in tight rooms and pair with a teammate covering your back.",
"Glaz":"Take long angles across open ground and hold them while teammates push.",
"Blackbeard":"Peek long angles first and stay ready to fall back once you are spotted.",
"Dokkaebi":"Use the phone ring to find defenders and to tap cameras when your team needs info.",
"Lion":"Scan just before you enter a room to catch anyone moving.",
"Finka":"Boost the team just before a big entry or a hard fight.",
"Maverick":"Cut small holes for surprise angles and keep the noise down.",
"Nokk":"Use your stealth to slip past cameras and flank alone only when safe.",
"Ace":"Coordinate your breach with the rest of the team so the entry is fast.",
"Zero":"Place cameras on angles where your team pushes next.",
"Ram":"Send robots ahead to clear gadgets and barricades before you commit.",
"Tachanka":"Use the turret to lock down a long lane and fall back if flanked.",
"Kapkan":"Place tripwires where attackers will be forced to path through.",
"Ela":"Place mines behind doorways attackers must cross.",
"Lesion":"Place mines in hallways and wait for the team to react to them.",
"Kaid":"Electrify the walls you expect attackers to breach.",
"Mozzie":"Turn attacker drones into your own eyes and keep watching them.",
"Warden":"Use your glasses to hold doorways where attackers rely on flashes or smoke.",
"Goyo":"Place canisters where attackers stack up or plant.",
"Oryx":"Use the dash to surprise a lone attacker, then rotate back.",
"Melusi":"Put slow devices on hallways attackers must push through.",
"Aruni":"Use gates to block key doorways and force detours.",
"Thunderbird":"Set stations in safe spots so teammates can heal between fights."
});
const SIEGE_FUNDAMENTALS=[
{t:"Attack fundamentals",items:["Drone early and gather information before committing to an entry.","Clear one angle at a time and avoid rushing without a plan.","Stay close enough to trade kills with teammates.","Use utility (flashes, smokes, gadgets) before you enter.","Secure the site before you start the plant.","Stay alive: dying early gives defenders the numbers advantage.","Break line of sight before healing or repositioning, since standing still in the open invites a trade you don't need to take.","Save at least one piece of utility for the post-plant phase instead of using everything to get into the site.","Pick entry points defenders are less likely to expect, not just the fastest route in.","Reset a push that's failing rather than feeding into the same angle a second time.","Communicate what you've cleared so teammates don't waste time or utility re-checking it."]},
{t:"Defense fundamentals",items:["Reinforce objective walls first, then secondary ones.","Set up crossfires so one defender can't be isolated.","Avoid over-peeking; hold angles and let attackers come to you.","Keep sound discipline: attackers listen for footsteps.","Roam sparingly, and only if your team can still hold the site.","Rotate when the attackers commit to one side."]},
{t:"Communication",items:["Call enemy position, health, and gadgets you see.","Ping and call the number of enemies remaining.","Announce your utility before using it near teammates.","Give short, clear calls instead of long descriptions."]},
{t:"Common mistakes",items:["Solo-pushing without team support.","Ignoring drones and cameras.","Running around without a plan.","Standing in the open when defusing or planting.","Not adapting when the opponent's strategy changes."]}
];
SIEGE_OPERATORS.push(
{n:"Kali",side:"Attack",d:"Carries a powerful sniper rifle and explosive lances, strong for picking off defenders and gadgets from range."},
{n:"Osa",side:"Attack",d:"Deploys a see-through shield as portable cover, letting her watch and shoot while protected."},
{n:"Grim",side:"Attack",d:"Launches units that let her track defenders' positions through walls."},
{n:"Brava",side:"Attack",d:"Hijacks defender electronic gadgets and turns them against their owners."},
{n:"Sens",side:"Attack",d:"Deploys projectors that create light-blocking screens, cutting defender sightlines."},
{n:"Deimos",side:"Attack",d:"Hunts a targeted defender, revealing their position to help the team."},
{n:"Fenrir",side:"Defense",d:"Places mines that disorient attackers who walk into them."},
{n:"Tubarão",side:"Defense",d:"Uses freezing canisters that shut down nearby attacker electronics."},
{n:"Azami",side:"Defense",d:"Places barrier sheets that create instant cover and block attacker paths."},
{n:"Solis",side:"Defense",d:"Scans for attacker electronics near the objective, helping the team spot incoming utility."},
{n:"Thorn",side:"Defense",d:"Places mines that punish attackers who ignore them."}
);
Object.assign(SIEGE_TIPS,{
"Kali":"Hold a long angle and pick off gadgets or defenders before the push starts.",
"Osa":"Use the shield as cover when peeking, and fall back when spotted.",
"Grim":"Use the tracking units to find defenders before committing to a room.",
"Brava":"Take control of defender gadgets and use them to clear the way.",
"Sens":"Block key sightlines so your team can push or plant unseen.",
"Deimos":"Mark a target and let your team hunt them down.",
"Fenrir":"Place mines in hallways where attackers must funnel.",
"Tubarão":"Freeze gadgets on the routes attackers use for utility.",
"Azami":"Block the doorways where attackers are most likely to push.",
"Solis":"Scan often so your team knows what utility is coming.",
"Thorn":"Place mines where attackers cross into the objective room."
});
SIEGE_FUNDAMENTALS.push(
{t:"Loadout basics",items:["Pick a primary weapon that suits your usual fights: close range, mid range, or long range.","Choose stable attachments that help you control recoil before damage tweaks.","Match your sight to the distance you fight at most.","Pick a secondary gadget that fills a gap your operator doesn't cover."]},
{t:"Drone play",items:["Scout the objective before the round timer gets low.","Call out gadgets, cameras, and reinforced walls you spot.","Keep a drone alive for the plant so you can watch the defenders.","Use drones to check rotations before committing to a push."]},
{t:"Planting and defusing",items:["Clear the site and check corners before starting the plant.","Cover the planter from more than one angle.","Defenders should focus on denying the plant early rather than the defuse at the last second.","Don't defuse in the open; clear the room first."]},
{t:"Mindset",items:["Talk to your team even in a losing round.","Learn from each round: what did the defenders do that beat you?","Vary your plays so you're not predictable.","Stay calm when things go wrong; a single round rarely decides the match."]}
);
SIEGE_MAPS.push(
{name:"Plane",notes:["A presidential aircraft with tight, multi-level corridors and cramped cabins, so fights happen at close range.","Hallways are narrow and windows are limited, so entries are more about timing than long sightlines."]},
{name:"Kanal",notes:["Two main buildings separated by a canal and connected by a bridge, with a mix of indoor rooms and outdoor approaches.","Attackers can split between the two buildings, so defenders need to watch the bridge and both sides."]},
{name:"Hereford Base",notes:["A military base building with several floors and lots of small rooms connected by narrow corridors.","Defenders can hold many small rooms, so attackers benefit from clearing one room at a time."]}
);
Object.assign(SIEGE_PLANS,{
"Plane":{a:"Use utility to clear cramped hallways and time your entries together.",d:"Hold the narrow corridors and crossfire the doorways."},
"Kanal":{a:"Split the two buildings and use the bridge carefully, since it is exposed.",d:"Watch the bridge and both buildings, and rotate to whichever side attackers commit to."},
"Hereford Base":{a:"Clear small rooms one at a time and keep your team close.",d:"Use the many small rooms to set crossfires and rotate between them."}
});
SIEGE_FUNDAMENTALS.push(
{t:"Common counters",items:["Electrified walls (Bandit, Kaid) can stop breach charges, so clear or work around them first.","Jammers (Mute) block drones and gadgets nearby, so plan around them.","EMP and electronic detectors (Thatcher, IQ) help attackers deal with defender gadgets.","Grenade-catching systems (Jäger, Wamai) reduce the value of grenades and launchers.","Drone hijacking (Mozzie) means attackers should protect their drones.","Mines and traps (Frost, Ela, Lesion, Fenrir, Thorn) punish rushing, so check the floor before you run."]}
);
SIEGE_GLOSSARY.push(
["Anchor","A defender who stays at or near the objective for the whole round instead of roaming."],
["Trade","Killing an enemy right after they kill your teammate, keeping the numbers even."],
["Flank","Attacking from a side or rear route the enemy isn't watching."],
["Soft Wall","A wall that can be broken with regular breaching tools or explosives, unlike a reinforced wall."],
["Reinforced Wall","A fortified wall defenders set up that needs a hard breacher to open."],
["Barricade","A board defenders place over a doorway or window to block sight and slow attackers."],
["Rappel","Using a rope to descend from a roof or window to enter from above."],
["Plant","Setting the defuser at the objective as an attacker, or the act of planting it."],
["Utility","Gadgets and grenades used to help a push or hold, rather than direct gunfire."],
["Frag","A kill."],
["Peek","Briefly stepping out to check an angle or take a shot, then stepping back."],
["Crossfire","Two or more defenders covering the same area from different angles."],
["Trap","A gadget placed to punish attackers who walk into it, like a tripwire or mine."],
["Comp","Short for team composition: the mix of operators a team picks."]
);
SIEGE_FUNDAMENTALS.push(
{t:"Team composition",items:["On attack, bring at least one way to open reinforced walls and one source of information.","On defense, mix anchors, intel, and a roamer instead of stacking one role.","Try to cover gadget counters: someone who can deal with traps, someone who can handle drones.","Talk before the round so two players don't pick the same job."]}
);
let coachTurns=[];
async function initSiegeCoach(){
  const card=document.getElementById('coachCard');
  if(!card)return;
  let sample=null;
  try{ sample = window.claude ? await claude.use('sample') : null; }catch(e){ sample=null; }
  if(!sample){ card.style.display='none'; return; }
  const opSel=document.getElementById('coachOp'),mapSel=document.getElementById('coachMap'),lvlSel=document.getElementById('coachLvl');
  const input=document.getElementById('coachInput'),askBtn=document.getElementById('coachAsk'),chatEl=document.getElementById('coachChat');
  const errCopy={not_granted:"You'll need to allow this app to use Claude — try asking again.",rate_limited:"Too many questions at once — give it a moment and try again.",sampling_disabled:"AI coaching isn't available on this account.",not_declared:"AI coaching isn't set up on this page right now.",refused:"Claude couldn't answer that one — try rephrasing.",images_unavailable:"",tools_unavailable:"",empty_completion:"Didn't get an answer back — try asking again.",invalid_json:"",upstream_error:"Something went wrong on Claude's end — try again."};
  async function ask(){
    const q=(input.value||'').trim();
    if(!q||askBtn.disabled)return;
    askBtn.disabled=true; input.value='';
    coachTurns.push({role:'user',content:q});
    const uDiv=document.createElement('div'); uDiv.className='coach-msg user'; uDiv.textContent=q; chatEl.appendChild(uDiv);
    const rDiv=document.createElement('div'); rDiv.className='coach-msg assistant'; rDiv.textContent='Thinking...'; chatEl.appendChild(rDiv);
    chatEl.scrollTop=chatEl.scrollHeight;
    const instructions=`You are a friendly, encouraging Rainbow Six Siege coach inside a PS5 game-discovery app called DECK. The player has set: Operator=${opSel.value}, Map=${mapSel.value}, Experience level=${lvlSel.value}. Tailor advice to this operator, this map, and this experience level whenever it's relevant to their question. Keep answers practical, concrete, and concise — about 3 to 6 sentences unless they ask for more. If they ask something unrelated to Siege, gently steer back to Siege strategy.`;
    try{
      const ctl=new AbortController();
      const {text}=await sample([{role:'user',content:instructions},...coachTurns],{
        cache:false, modelTier:'quick', signal:ctl.signal,
        onText:({text})=>{ rDiv.textContent=text; chatEl.scrollTop=chatEl.scrollHeight; }
      });
      coachTurns.push({role:'assistant',content:text});
    }catch(e){
      rDiv.textContent = e.text || errCopy[e.code] || "Something went wrong — try again.";
      if(coachTurns[coachTurns.length-1]&&coachTurns[coachTurns.length-1].role==='user')coachTurns.pop();
    }finally{
      askBtn.disabled=false; chatEl.scrollTop=chatEl.scrollHeight;
    }
  }
  askBtn.onclick=ask;
  input.addEventListener('keydown',e=>{ if(e.key==='Enter'){ e.preventDefault(); ask(); } });
}
function stratFilter(q){
  q=(q||'').trim().toLowerCase();
  document.querySelectorAll('#strategyBody .strat-section').forEach(d=>{ if(q) d.open=true; });
  document.querySelectorAll('#strategyBody .strat-map').forEach(sec=>{
    const h=sec.querySelector('h4');
    const hMatch=!q||(h&&h.textContent.toLowerCase().includes(q));
    let any=false;
    sec.querySelectorAll('.rev-p').forEach(p=>{
      const show=hMatch||p.textContent.toLowerCase().includes(q);
      p.style.display=show?'':'none';
      if(show)any=true;
    });
    sec.style.display=(hMatch||any)?'':'none';
  });
  document.querySelectorAll('#strategyBody .op-row, #strategyBody .glos-row').forEach(row=>{
    row.style.display=(!q||row.textContent.toLowerCase().includes(q))?'':'none';
  });
}
function stratNav(id,btn){
  document.querySelectorAll('.strat-nav button').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  const d=document.getElementById(id);
  if(d){ d.open=true; d.scrollIntoView({behavior:'smooth',block:'start'}); }
}
function opFilter(which,btn){
  document.querySelectorAll('.op-filter-row button').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  document.querySelectorAll('[data-side]').forEach(el=>{
    const show=which==='all'||el.dataset.side===which;
    el.style.display=show?'':'none';
  });
}
SIEGE_MAPS.push(
{name:"Fortress",notes:["A mudbrick kasbah in the Atlas Mountains of Morocco, with exterior stairs and towers giving unusually open roof access on top of two floors of interior rooms.","The layout is closely tied to Kaid, the defender who was introduced alongside this map."]},
{name:"Tower",notes:["A modern communications tower in Seoul with no real outdoor area; attackers instead spawn on the roof and rappel or push down into the building.","It's a dark, dense, and fairly disliked map competitively, but its many interconnected sites make it intuitive to learn."]},
{name:"Lair",notes:["Deimos' secret base of operations in a cave complex on the coast of Portugal, reachable by air, sea, or underground tunnel.","It's noticeably larger and mazier than most maps, so extra drone time before committing to a push matters more here than usual."]},
{name:"Nighthaven Labs",notes:["Nighthaven's offshore research headquarters in Singapore, mixing an industrial interior with cliffside exterior views.","Three floors are connected by five stairwells and many breakable walls, so holding one position for long is difficult for either side."]},
{name:"Emerald Plains",notes:["A country club and private ranch in Northern Ireland, with a modern ground floor contrasting the manor's classic upper floor.","Spacious rooms and multiple stairwells make it a larger, slower map, with a central fireplace atrium connecting both floors via a skylight."]},
{name:"Stadium Bravo",notes:["A Greek stadium map that mixes rooms and layout ideas from Border and Coastline, with bulletproof glass removed so windows can be destroyed.","Attackers can spawn from the top of the map, which cuts down on defenders spawn-peeking early in the round."]},
{name:"Calypso Casino",notes:["A modernized remake of the Calypso Casino from Rainbow Six Vegas, added as a competitive Ranked map in 2026.","It's a vertical, three-level casino floor with a lot of destructible cover, built for esports-level play while keeping the classic casino's rooms recognizable."]}
);
Object.assign(SIEGE_PLANS,{
"Nighthaven Labs":{sites:["Basement: Tank & Assembly","1F: Control & Storage","1F: Kitchen & Cafeteria","2F: Command & Server"],a:"Many access points and breakable walls make single holds hard to keep; push methodically and watch for the runout hatch near Meeting Room as a surprise route.",d:"With five stairwells connecting three floors, roamers can circle back easily; anchor the site and communicate rotations often since flanks are common here."},
"Emerald Plains":{sites:["1F: interconnected east/west wing rooms (bar, lounge, kitchen, dining)","2F: manor rooms including Music and Hunting Halls"],a:"The central fireplace atrium and skylight offer a vertical route straight into the manor; bring hard breach for the many exterior reinforceable walls.",d:"The map favors bunkered setups, so spread coverage across the interconnected rooms rather than stacking one doorway, since sites often connect directly to each other."},
"Stadium Bravo":{a:"Treat it like a hybrid of Border and Coastline; use the top-spawn route to avoid early exterior peeks and clear windows now that the glass is destructible.",d:"Hold the mixed interior/exterior sightlines borrowed from Border and Coastline, and adjust holds since windows are no longer bulletproof here."},
"Lair":{a:"Drone heavily before committing; the map is unusually large and maze-like, so wasted time finding the objective costs more here than on other maps.",d:"Use the size to your advantage by rotating and re-holding rather than over-committing to one room, since attackers will be slower to reach you."},
"Fortress":{a:"Use the many exterior stairs and roof access for vertical entries instead of only pushing ground-floor doors.",d:"Watch the roof and tower approaches as closely as the interior, since the exterior offers attackers unusually open access."},
"Tower":{a:"Expect to rappel or push down from the roof rather than finding a normal ground entrance; clear top-down instead of bottom-up.",d:"The map's four objective areas are all within walking distance of each other, so open hatches early to keep rotation options between them."},
"Calypso Casino":{sites:["Vault","CCTV"],a:"This is a tall, three-level map with a lot of vertical destructibility; call floor number first, since attackers and roamers move through the casino's central stairs and elevators constantly.",d:"Cover every staircase leading down toward Vault and CCTV, since those are the two main site areas across the casino floor."}
});
SIEGE_OPERATORS.push(
{n:"Rauora",side:"Attack",d:"Launches bulletproof panels onto doorways from a distance, letting her block off paths and control access into or out of a room."},
{n:"Denari",side:"Defense",d:"Deploys paired devices that form a damaging, slowing laser between them when both are placed within sight of each other, covering a room."}
);
Object.assign(SIEGE_TIPS,{
"Rauora":"Use panels to cut off a flank route or seal a site door mid-round, since both sides can trigger them once placed.",
"Denari":"Place the two devices so the laser crosses a doorway or hallway attackers must pass through, not just open floor."
});
// Ranked/Pro League map pools as of mid-2026 (Year 11 Season 2) — Ubisoft rotates these most seasons, so treat as a snapshot, not permanent
const RANKED_MAPS=new Set(["Bank","Border","Calypso Casino","Chalet","Clubhouse","Coastline","Consulate","Emerald Plains","Fortress","Kafe Dostoyevsky","Lair","Nighthaven Labs","Oregon","Outback"]);
const PRO_MAPS=new Set(["Bank","Border","Chalet","Clubhouse","Consulate","Kafe Dostoyevsky","Lair","Nighthaven Labs","Skyscraper"]);
// General kit-function tags, one line each, for faster scanning — not a ranking or tier list
const OP_ROLE={
"Sledge":"Hard Breach","Thatcher":"Utility Removal","Ash":"Hard Breach","Thermite":"Hard Breach","Twitch":"Utility Removal","Montagne":"Entry Shield","Fuze":"Area Denial","Hibana":"Hard Breach","Jackal":"Intel","Ying":"Flash Utility","Zofia":"Entry Utility","Buck":"Hard Breach","Capitão":"Area Denial","Iana":"Intel","Nomad":"Area Denial","Gridlock":"Area Denial","Amaru":"Entry","Flores":"Utility Removal","IQ":"Intel","Blitz":"Entry","Glaz":"Long Range","Blackbeard":"Long Range","Dokkaebi":"Intel","Lion":"Intel","Finka":"Support","Maverick":"Hard Breach","Nokk":"Intel Denial","Ace":"Hard Breach","Zero":"Intel","Ram":"Utility Removal","Kali":"Long Range","Osa":"Entry Cover","Grim":"Intel","Brava":"Utility Hijack","Sens":"Area Denial","Deimos":"Intel","Rauora":"Area Denial",
"Smoke":"Area Denial","Mute":"Utility Removal","Castle":"Fortification","Pulse":"Intel","Rook":"Support","Doc":"Support","Jäger":"Utility Removal","Bandit":"Anti-Breach","Frost":"Trapper","Valkyrie":"Intel","Caveira":"Roamer","Echo":"Area Denial","Mira":"Intel","Vigil":"Roamer","Maestro":"Intel","Alibi":"Intel","Clash":"Entry Denial","Wamai":"Utility Removal","Tachanka":"Area Denial","Kapkan":"Trapper","Ela":"Trapper","Lesion":"Trapper","Kaid":"Anti-Breach","Mozzie":"Utility Hijack","Warden":"Intel Denial","Goyo":"Area Denial","Oryx":"Roamer","Melusi":"Area Denial","Aruni":"Area Denial","Thunderbird":"Support","Fenrir":"Trapper","Tubarão":"Utility Removal","Azami":"Fortification","Solis":"Intel","Thorn":"Trapper","Denari":"Area Denial"
};
// Operator-by-operator tips for Bank, grounded in the map's real layout (3 attacker spawns, hatch-heavy ground floor, known camera/vent spots) — not invented per-patch site meta
const MAP_OP_TIPS={"Bank":{
"Sledge":"Bank's ground floor ceiling is heavily destructible near Open Area and Archives — use your hammer there instead of waiting on a hard breacher.",
"Thatcher":"EMP the CCTV Room or Lockers hatches before your team drops from Open Area above, since Bandit-charged floors are common there.",
"Ash":"Break line from the Plaza into 2F CEO/Exec Hallway windows for a fast ranged breach into the top-floor site.",
"Thermite":"Save your charge for the Vault or CEO Office's fortified walls rather than the many soft hatches Sledge or Buck can already open.",
"Twitch":"Send your drone through the Garage Ramp's drone vent into 0F Vault Lobby to clear gadgets before your team commits.",
"Montagne":"Push through Main Entrance behind your shield; it's a heavily camera'd, high-traffic route so expect early contact.",
"Fuze":"Cluster-charge the Archives or Teller's ceiling from above to clear roamers before dropping through a hatch.",
"Hibana":"Open small pellet holes into CEO Office from the Plaza side rather than fully committing to one big breach.",
"Jackal":"Bank's size makes roaming defenders like Caveira and Vigil common — track footprints early instead of pushing blind.",
"Ying":"Flash through Archives or Open Area doorways before entering; both areas funnel defenders together.",
"Zofia":"Use your launcher to open a quick soft-wall angle into Teller's from the Alley side.",
"Buck":"Shoot through the Open Area or Archives ceiling from above — Bank's ground floor is some of the most destructible in the game.",
"Capitão":"Smoke the Plaza or Garage Ramp to cover your team's approach into the more exposed exterior routes.",
"Iana":"Send your decoy down a hatch first to bait a reaction from roamers before committing yourself.",
"Nomad":"Cover the Alley or Jewelry tunnel entrance with airjabs to stop a roamer flanking your team's push.",
"Gridlock":"Lay Trax Stingers in the Alley or Garage Ramp to slow a counter-flank while your team pushes a site.",
"Amaru":"Bank's many windows and hatches make grapple entries strong — launch straight into CEO Office or Archives from outside.",
"Flores":"Send a drone ahead into Open Area or the Vault Lobby to bait Bandit tricks on hatches before you commit.",
"IQ":"Sweep CCTV Room and Lockers for gadgets before pushing the basement site, since it's one of the more trap-heavy areas.",
"Blitz":"Push Main Entrance or the Garage doorway; both are close-range chokepoints suited to your shield.",
"Glaz":"Hold long sightlines from the Plaza into 2F windows, since Bank's exterior offers some of the game's longer exterior angles.",
"Blackbeard":"Peek the Plaza windows into CEO Office; the range favors your rifle shield.",
"Dokkaebi":"Bank's size draws out roamers — ring phones early to locate them before your team splits up.",
"Lion":"Scan before pushing into Open Area or Archives, since Bank's size makes late defender rotations and roams common.",
"Finka":"Save your boost for the push into Vault or CEO Office, where fights tend to be longest.",
"Maverick":"Cut a quiet hole into CCTV Room or Teller's for a surprise angle instead of following the well-camera'd Main Entrance.",
"Nokk":"Approach through the Alley or Jewelry tunnel unseen by cameras, since Bank has several early camera placements covering the main routes.",
"Ace":"Breach the Vault's reinforced walls directly if it's in play; it's built to resist normal breaching tools.",
"Zero":"Bank's hatch-heavy design suits camera placement in CEO Office or Archives ahead of your team's push.",
"Ram":"Send the robot ahead to clear Bandit tricks on hatches before your team drops through them.",
"Kali":"Hold a long angle from the Plaza or Garage Ramp and pick off roamers before they reposition.",
"Osa":"Use your shield to cross the exposed Plaza or Alley safely before pushing a site.",
"Grim":"Track defenders early on a map this size, since roamers like Caveira and Vigil can be almost anywhere.",
"Brava":"Hijack Mute jammers or Bandit batteries near CCTV Room or the Vault before your team commits to a breach.",
"Sens":"Block sightlines across the Plaza or Open Area so your team can cross safely.",
"Deimos":"Mark a roaming defender early, since Bank's size makes them hard to pin down otherwise.",
"Rauora":"Seal off the Alley or Garage Ramp with a panel to cut off a flanking roamer.",
"Smoke":"Gas the Vault Lobby drone vent or CCTV Room, since those are common early attacker entry points.",
"Mute":"Jam the Garage Ramp drone vent and CEO Office windows, both common gadget entry points.",
"Castle":"Armor the Archives or CEO Office doorway to force attackers into slower, exposed breaches.",
"Pulse":"Scan the Plaza or Main Entrance, both high-traffic exterior approaches, to track the attackers' push.",
"Rook":"Drop armor early since Bank's long sightlines and open Plaza mean early trades are common.",
"Doc":"Stay near whichever site is in play — Bank's size means rotations take time, so keep your anchor alive.",
"Jäger":"Place your system to cover the Vault Lobby drone vent or Open Area hatches from grenades.",
"Bandit":"Trick the many ground-floor hatches near Open Area and Archives — attackers rely on them heavily.",
"Frost":"Hide traps in the Alley or Garage Ramp, both common flanking or roaming return routes.",
"Valkyrie":"Place cameras on the exterior — Boulevard, Jewelry, and Alley are all attacker spawns worth watching.",
"Caveira":"Bank's size is built for roaming — hunt lone attackers near the Alley or Jewelry entrances.",
"Echo":"Use your drone to stall a push into Archives or CEO Office while your team rotates.",
"Mira":"Place a window into CCTV Room or Teller's before attackers commit to a breach there.",
"Vigil":"Bank's size rewards roaming — use invisibility to reposition around cameras near the Plaza.",
"Maestro":"Place turrets covering Open Area or the Garage doorway, both frequent attacker chokepoints.",
"Alibi":"Bait attackers pushing through Main Entrance or the Garage with a decoy in a corner.",
"Clash":"Hold the Garage or Main Entrance doorway and push attackers back before they can regroup.",
"Wamai":"Cover the Vault Lobby drone vent and Open Area hatches with magnets against grenades.",
"Tachanka":"Lock down the Plaza or a long hallway leading to CEO Office with the turret.",
"Kapkan":"Place tripwires at the Garage or Main Entrance doorways, both common early attacker routes.",
"Ela":"Cover the Archives or Teller's doorway with mines to punish a fast push.",
"Lesion":"Place mines in Open Area or the Garage Ramp to slow attackers crossing the hatch-heavy ground floor.",
"Kaid":"Electrify the Vault or CEO Office's reinforced walls to punish hard breachers.",
"Mozzie":"Hijack drones near the Garage Ramp vent or Plaza before they reveal your roamer's position.",
"Warden":"Hold CEO Office or Archives doorways, where flashes are common due to the tight entry points.",
"Goyo":"Place canisters in Open Area or the Vault, both frequent plant spots.",
"Oryx":"Bank's size and many soft walls suit dashing between CCTV Room and Archives to catch a lone attacker.",
"Melusi":"Slow attackers crossing the Plaza or Alley toward the site.",
"Aruni":"Block the Garage or Main Entrance doorway with a gate to force a detour.",
"Thunderbird":"Set healing stations near whichever site is in play, since Bank's size means help arrives slowly otherwise.",
"Fenrir":"Place mines in the Alley or Garage Ramp to disorient a flanking attacker.",
"Tubarão":"Freeze gadgets near the Vault Lobby vent or CCTV Room before attackers use them.",
"Azami":"Block the CEO Office or Archives doorway with a barrier sheet for instant cover.",
"Solis":"Scan for attacker electronics near the Plaza or Garage Ramp before they breach.",
"Thorn":"Place mines at the Garage or Main Entrance, both common early attacker routes.",
"Denari":"Cross the two devices over the Garage or Main Entrance doorway, both frequent chokepoints."
}};
// Quiz — grounded in real, checked Siege mechanics: Bank's actual layout (researched), well-established gadget interactions, and the app's own verified fundamentals. No invented per-map "best entry" answers for maps not researched in depth.
const QUIZ_QUESTIONS=[
{ctx:{map:"Bank",site:"CCTV Room / Lockers",side:"Attack",op:"Twitch"},q:"Your team is attacking CCTV Room/Lockers in the basement. What's the fastest way to clear gadgets before committing?",opts:["Send a drone through the Garage Ramp's drone vent into the Vault Lobby","Push straight through Main Entrance","Wait at spawn until the timer runs low","Throw a grenade blindly into the basement"],correct:0,why:"Bank's Garage Ramp has a dedicated drone vent straight into the 0F Vault Lobby, letting you scout and clear gadgets near the basement site without exposing anyone."},
{ctx:{map:"Bank",side:"Attack",op:"Sledge"},q:"You're playing Sledge on Bank and want a fast unconventional entry. Where should you look first?",opts:["The ground floor ceiling near Open Area or Archives","The Vault's reinforced wall","A random 2F window","The Main Entrance door"],correct:0,why:"Bank's ground floor ceiling near Open Area and Archives is some of the most destructible in the game — a hammer opens a hatch there faster than waiting on a hard breacher."},
{ctx:{map:"Bank",site:"Vault",side:"Attack",op:"Thermite"},q:"The Vault is in play on Bank. Should you use your charge on it?",opts:["Yes — it's built to resist normal breaching tools and needs a real hard breach","No — Sledge can hammer it open","No — it's a soft wall","Only if the round timer is under 30 seconds"],correct:0,why:"The Vault's walls are reinforced specifically to resist casual breaching, so a dedicated hard-breach charge like Thermite's is the intended way in."},
{ctx:{map:"Bank",side:"Defense",op:"Bandit"},q:"You're defending as Bandit on Bank. Where do your batteries matter most?",opts:["The ground-floor hatches near Open Area and Archives, since attackers rely on them heavily","The Main Entrance door","The roof","A random basement wall"],correct:0,why:"Bank's ground floor is hatch-heavy, and attackers count on opening them quickly — tricking those hatches directly punishes that plan."},
{ctx:{map:"Bank",side:"Attack"},q:"Bank is a large map known for strong roaming defenders like Caveira and Vigil. What should your team prioritize?",opts:["Getting intel on roamers early instead of pushing blind","Ignoring roamers entirely","Splitting up immediately at round start","Staying at spawn the whole round"],correct:0,why:"Bank's size is exactly what makes roaming strong — tracking or spotting a roamer before you commit avoids getting caught from behind."},
{ctx:{map:"Bank",side:"Defense"},q:"Bank has three attacker spawns: Boulevard, Jewelry, and Alley. What does this mean for your defense?",opts:["Attackers can approach from multiple directions, so watch more than one exterior route","Only one spawn matters, ignore the others","Spawns don't affect defense at all","You should push all three spawns immediately"],correct:0,why:"Multiple spawns mean multiple possible approach angles — a defense that only watches one exterior route gets flanked by the other two."},
{ctx:{map:"Bank",side:"Attack",op:"Twitch"},q:"Bank's Garage Ramp has a drone vent. What's it useful for?",opts:["Scouting the 0F Vault Lobby before committing to the basement site","Nothing — it's purely cosmetic","Reaching the roof","Skipping straight to the CEO Office"],correct:0,why:"It's a dedicated route for a drone to get eyes on the Vault Lobby without a player exposing themselves at Garage."},
{ctx:{map:"Bank",side:"Defense",op:"Caveira"},q:"You're roaming as Caveira on Bank. Where are attackers most likely to be caught alone?",opts:["Near the Alley or Jewelry entrances, since Bank's size spreads attackers out","Standing together at the plant","All grouped at Main Entrance","Never — Bank has no roaming spots"],correct:0,why:"Bank's size is exactly why it's known for strong roaming — attackers get spread across the map's several spawns and entries, creating chances to isolate one."},
{q:"Defenders have electrified a wall you need to breach. Which of these actually clears it?",opts:["An EMP from Thatcher, or a shock from Twitch's drone","Just shooting the wall more","Waiting it out — it disables itself","Throwing a smoke grenade at it"],correct:0,why:"Bandit's electrified walls and Kaid's electroclaws are disabled by EMP effects — Thatcher's grenade or Twitch's drone shock are the standard counters."},
{q:"You're defending and want to stop attackers from EMP-ing your electrified walls before they arrive. What's the play?",opts:["Set up your batteries as late as possible or shield them with map geometry","There's no way to protect them","Always place batteries in the open","EMPs can't affect Bandit batteries"],correct:0,why:"Since Thatcher and Twitch can clear batteries from a distance, defenders often delay placing them or tuck them where they're harder to hit blind."},
{q:"An attacker is using a drone to scout your position. Which operator directly counters that?",opts:["Mozzie, who can hijack attacker drones","Rook, who only gives armor","Doc, who only heals","Smoke, whose gas doesn't affect drones"],correct:0,why:"Mozzie's gadget hijacks nearby attacker drones and turns them into defender tools, directly answering drone-based scouting."},
{q:"You've reinforced a wall, but attackers keep breaching it with grenades tossed through a hole. What stops that?",opts:["Jäger's system, which intercepts incoming grenades","Nothing can stop thrown grenades","Only Rook's armor plates help","Doc's stim pistol"],correct:0,why:"Jäger's gadget is built specifically to shoot down incoming grenades and other thrown projectiles before they land."},
{q:"An attacker downs your teammate near the objective. What can Caveira do that no other defender can?",opts:["Interrogate the downed player to learn a nearby teammate's location","Instantly revive them","Give them extra armor","Nothing unique — any operator can do this"],correct:0,why:"Interrogation is Caveira's signature ability — it's the one way to pull real-time enemy location info out of a downed attacker."},
{q:"Castle has armored a doorway. How do attackers get through it?",opts:["Explosives — hard breach charges or grenades, not normal bullets","Just shooting it enough times","It opens automatically after a minute","Only by picking the lock"],correct:0,why:"Castle's panels are built to resist gunfire; they come down to explosive damage, the same as most hard-breach tools."},
{q:"You're pushing a site and Mute has jammers up. What's actually blocked?",opts:["Nearby drones, breaching charges, and other electronic gadgets","Nothing — Mute's jammers are cosmetic","Only cameras, nothing else","Bullets fired near the jammer"],correct:0,why:"Mute's jammers disable nearby electronic devices — drones, remote detonators, and other gadgets — not gunfire itself."},
{q:"Which of these is the correct way to deal with a Kapkan tripwire you've spotted on a doorway?",opts:["Shoot it from a safe distance instead of walking through it","Walk through slowly, it only triggers on running","Ignore it, tripwires are visual only","Only a hard breacher can remove it"],correct:0,why:"Once you've spotted a tripwire, shooting it out from a safe angle is the standard way to clear it without triggering the trap."},
{q:"Ela has placed Grzmot mines near a doorway. What do they do if triggered?",opts:["Stun and slow anyone caught in the blast","Deal no damage, just noise","Only affect defenders","Heal nearby attackers"],correct:0,why:"Grzmot mines are a concussion-style trap — they stun and slow whoever sets them off, making a fast push into that doorway costly."},
{q:"You want to clear a Frost mat you've spotted before your team pushes through. What's the safest option?",opts:["Shoot it from range to destroy it without walking on it","Step directly on it carefully","Wait for a teammate to trigger it first","Frost mats can't be destroyed"],correct:0,why:"Like most visible traps, a spotted Frost mat can be shot out from a safe distance instead of risking someone stepping on it."},
{q:"Your team is about to push a site but hasn't droned yet. What should happen first?",opts:["Drone to gather information before committing to an entry","Rush in immediately for the surprise factor","Wait at spawn the entire round","Split up randomly without a plan"],correct:0,why:"Droning first is one of the most consistent attack fundamentals — information before commitment avoids walking into a setup you didn't know was there."},
{q:"A teammate just died pushing an angle alone. What's the right response?",opts:["Reset the push instead of feeding into the same angle again","Immediately push the exact same angle solo","Leave the round","Stop communicating with the team"],correct:0,why:"Feeding into a losing angle a second time usually just costs another player — resetting and finding a different approach is the better call."},
{q:"As a defender, you hear footsteps but can't see the attacker. What's the disciplined play?",opts:["Hold your angle and let them come to you instead of over-peeking","Immediately run toward the sound","Peek every doorway at once","Reload loudly to bait them"],correct:0,why:"Over-peeking on sound alone gives up your position for uncertain information — holding an angle keeps the advantage on your side."},
{q:"You're attacking and have one piece of utility left after entry. When should you use it?",opts:["Save it for the post-plant phase instead of using it all on entry","Use it immediately no matter what","Throw it away, it doesn't matter","Give it to a teammate who already used theirs"],correct:0,why:"Saving at least one piece of utility for post-plant is a core fundamental — entries aren't the only phase that needs support."},
{q:"Your team is picking operators for the round. What should you avoid?",opts:["Two players picking the same role and leaving gaps elsewhere","Talking about roles before the round","Bringing at least one hard breacher on attack","Mixing anchors and roamers on defense"],correct:0,why:"Doubling up on one role while leaving no intel, no hard breach, or no anchor is a common comp mistake — talking it out beforehand avoids it."},
{q:"As an attacker, you've cleared a room. What should you tell your team?",opts:["That the room is clear, so they don't waste time or utility re-checking it","Nothing, let them find out themselves","Only the bomb site name","Whatever comes to mind"],correct:0,why:"Calling out a cleared room saves your team's utility and time for the parts of the map that still need checking."},
{q:"A defender is anchoring the site while a teammate roams. What's the anchor's job?",opts:["Stay near the objective for the whole round instead of leaving it undefended","Roam as far as possible","Leave the site the moment the round starts","Only defend after attackers already planted"],correct:0,why:"An anchor's whole role is staying at or near the objective, so the site isn't left open while others roam or rotate."},
{q:"You're an attacker who just planted the defuser in the open with no cover. What's wrong with that?",opts:["It leaves the planter exposed to being shot before the room is even secured","Nothing, planting in the open is always fine","It makes the defuse faster","It confuses the defenders"],correct:0,why:"Planting without clearing the room and covering the planter from multiple angles is a common way to lose the defuser to a surprise angle."},
{q:"Which of these is a 'soft wall' in Siege terms?",opts:["A wall that can be broken with regular breaching tools or explosives","A wall that can never be destroyed","A wall only Thermite can open","A wall that regenerates each round"],correct:0,why:"Soft walls are the destructible walls found throughout most maps — reinforced walls are the ones that need a dedicated hard breacher."},
{q:"What does 'trading' mean in Siege?",opts:["Killing an enemy right after they kill your teammate, keeping the numbers even","Swapping operators mid-round","Giving a teammate your gadgets","Switching sites after the plant"],correct:0,why:"A trade keeps the round's numbers balanced — losing a player is much less costly if you immediately take one of theirs in return."},
{q:"Your team wants to flank the site instead of pushing head-on. What does that mean?",opts:["Attacking from a side or rear route the defenders aren't watching","Attacking through the obvious front door only","Standing still until the timer runs out","Splitting into five separate one-person pushes"],correct:0,why:"A flank is specifically about using an angle the defenders aren't expecting, rather than the most obvious route in."},
{q:"You're a defender setting up crossfire. What does that actually mean?",opts:["Two or more defenders covering the same area from different angles","One defender covering every angle alone","Placing gadgets in a straight line","Firing without aiming"],correct:0,why:"Crossfire relies on multiple defenders watching the same space from different positions, so an attacker exposed to one angle is exposed to both."}
];
let quizIdx=0,quizScore=0,quizOrder=[];
function shuffleArr(arr){ for(let i=arr.length-1;i>0;i--){ const j=Math.floor(Math.random()*(i+1)); [arr[i],arr[j]]=[arr[j],arr[i]]; } return arr; }
function startQuiz(){
  quizIdx=0; quizScore=0;
  quizOrder=shuffleArr(QUIZ_QUESTIONS.map((_,i)=>i));
  renderQuizQ();
}
function renderQuizQ(){
  const wrap=document.getElementById('quizWrap');
  if(!wrap)return;
  if(quizIdx>=quizOrder.length){
    const pct=Math.round(100*quizScore/quizOrder.length);
    wrap.innerHTML=`<div class="quiz-score">${quizScore} / ${quizOrder.length} — ${pct}%</div><div class="quiz-score-sub">${pct>=80?"Strong grasp of these mechanics.":pct>=50?"Decent — a few worth reviewing above.":"Worth a re-read of the Basics section above."}</div><button class="quiz-restart-btn" id="quizRestartBtn">Play Again</button>`;
    document.getElementById('quizRestartBtn').onclick=startQuiz;
    return;
  }
  const q=QUIZ_QUESTIONS[quizOrder[quizIdx]];
  const c=q.ctx;
  const ctxHtml=c?`<div class="quiz-ctx">${c.map?`<span>🗺️ ${c.map}</span>`:''}${c.site?`<span>💣 ${c.site}</span>`:''}${c.side?`<span>🎮 ${c.side}</span>`:''}${c.op?`<span>👤 ${c.op}</span>`:''}</div>`:'';
  wrap.innerHTML=`<div class="quiz-progress">Question ${quizIdx+1} of ${quizOrder.length} · Score: ${quizScore}</div>${ctxHtml}<div class="quiz-q">${q.q}</div>`+
    q.opts.map((o,i)=>`<button class="quiz-opt" data-i="${i}">${o}</button>`).join('');
  wrap.querySelectorAll('.quiz-opt').forEach(btn=>{
    btn.onclick=()=>{
      const i=Number(btn.dataset.i);
      const allBtns=wrap.querySelectorAll('.quiz-opt');
      allBtns.forEach(b=>b.disabled=true);
      if(i===q.correct){ btn.classList.add('correct'); quizScore++; }
      else{ btn.classList.add('wrong'); allBtns[q.correct].classList.add('correct'); }
      const whyDiv=document.createElement('div'); whyDiv.className='quiz-why'; whyDiv.textContent=q.why; wrap.appendChild(whyDiv);
      const nextBtn=document.createElement('button'); nextBtn.className='quiz-next-btn'; nextBtn.textContent=(quizIdx+1<quizOrder.length)?'Next Question':'See Score';
      nextBtn.onclick=()=>{ quizIdx++; renderQuizQ(); };
      wrap.appendChild(nextBtn);
      wrap.scrollIntoView({behavior:'smooth',block:'nearest'});
    };
  });
}
function renderStrategy(){
  const maps=SIEGE_MAPS.map(m=>{
    const pl=SIEGE_PLANS[m.name];
    let sitesHtml='';
    if(pl&&pl.sites){
      const btns=pl.sites.map(s=>{
        const parts=s.split(': ');
        const floor=parts.length>1?parts[0]:'';
        const label=parts.length>1?parts[1]:parts[0];
        const info=`<b>${floor?floor+' \u2014 ':''}${label}</b><br>Attack: ${pl.a}<br>Defense: ${pl.d}`;
        return `<button class="site-btn" onclick="var p=this.nextElementSibling;p.style.display=(p.style.display==='block')?'none':'block';">${s}</button><div class="site-panel" style="display:none">${info}</div>`;
      }).join('');
      sitesHtml=`<p class="rev-p"><b>Bomb sites</b> \u2014 tap one for the approach:</p><div class="site-grid">${btns}</div>`;
    }
    let opTipsHtml='';
    if(MAP_OP_TIPS[m.name]){
      const tips=MAP_OP_TIPS[m.name];
      const rows=SIEGE_OPERATORS.filter(o=>tips[o.n]).map(o=>`<div class="op-row op-${o.side==='Attack'?'atk':'def'}"><span class="op-dot"></span><b>${o.n}:</b> ${tips[o.n]}</div>`).join('');
      opTipsHtml=`<details style="margin-top:10px;"><summary style="cursor:pointer;font-size:12px;color:var(--accent);">Per-operator tips for ${m.name} (${Object.keys(tips).length}) \u25BE</summary><div style="margin-top:8px;">${rows}</div></details>`;
    }
    return `<div class="strat-map" id="map-${m.name.replace(/\s+/g,'-')}"><h4>${(RANKED_MAPS.has(m.name)?'<span class="badge badge-ranked">Ranked</span>':'')}${(PRO_MAPS.has(m.name)?'<span class="badge badge-pro">Pro League</span>':'')}${m.name}</h4>${m.notes.map(n=>`<p class="rev-p">${n}</p>`).join('')}${sitesHtml}${(pl&&!pl.sites)?`<p class="rev-p"><b>Attack:</b> ${pl.a}</p><p class="rev-p"><b>Defense:</b> ${pl.d}</p>`:''}${opTipsHtml}</div>`;
  }).join('');
  const mapJump=`<div class="map-jump-grid">${SIEGE_MAPS.map(m=>`<button onclick="document.getElementById('map-${m.name.replace(/\s+/g,'-')}').scrollIntoView({behavior:'smooth',block:'start'})">${(RANKED_MAPS.has(m.name)?'🏆 ':'')}${m.name}</button>`).join('')}</div>`;
  const roles=SIEGE_ROLES.map(r=>`<p class="rev-p"><b>${r.t}:</b> ${r.d}</p>`).join('');
  const phases=SIEGE_PHASES.map(r=>`<p class="rev-p"><b>${r.t}:</b> ${r.d}</p>`).join('');
  const gloss=SIEGE_GLOSSARY.map(([t,d])=>`<div class="glos-row"><b>${t}:</b> ${d}</div>`).join('');
  const atk=SIEGE_OPERATORS.filter(o=>o.side==='Attack').map(o=>`<div class="op-row op-atk"><span class="op-dot"></span><span class="role-tag">${OP_ROLE[o.n]||''}</span><b>${o.n}:</b> ${o.d}${SIEGE_TIPS[o.n]?` <i>Tip: ${SIEGE_TIPS[o.n]}</i>`:''}</div>`).join('');
  const def=SIEGE_OPERATORS.filter(o=>o.side==='Defense').map(o=>`<div class="op-row op-def"><span class="op-dot"></span><span class="role-tag">${OP_ROLE[o.n]||''}</span><b>${o.n}:</b> ${o.d}${SIEGE_TIPS[o.n]?` <i>Tip: ${SIEGE_TIPS[o.n]}</i>`:''}</div>`).join('');
  const fund=SIEGE_FUNDAMENTALS.map(f=>`<div class="strat-subhead">${f.t}</div>${f.items.map(i=>`<p class="rev-p">${i}</p>`).join('')}`).join('');
  document.getElementById('strategyBody').innerHTML=
    `<input id="stratSearch" type="search" placeholder="Search operators, maps, terms..." oninput="stratFilter(this.value)" style="width:100%;box-sizing:border-box;padding:10px 12px;margin:10px 0 10px;border-radius:10px;border:1px solid rgba(255,255,255,.15);background:rgba(255,255,255,.06);color:inherit;font-size:14px;">`+
    `<div class="coach-wrap" id="coachCard">
      <div class="strat-subhead" style="margin-top:2px;">🧠 AI Siege Coach</div>
      <div class="coach-select-row">
        <select id="coachOp">${SIEGE_OPERATORS.map(o=>`<option value="${o.n}">${o.n}</option>`).join('')}</select>
        <select id="coachMap">${SIEGE_MAPS.map(m=>`<option value="${m.name}">${m.name}</option>`).join('')}</select>
        <select id="coachLvl"><option>Beginner</option><option>Intermediate</option><option>Advanced</option></select>
      </div>
      <div class="coach-chat" id="coachChat"></div>
      <div class="coach-input-row">
        <input id="coachInput" type="text" placeholder="Ask your Siege Coach...">
        <button id="coachAsk">Ask</button>
      </div>
      <div class="coach-hint">Answers with your operator/map/experience picks above. Uses your own Claude access — nothing here is saved between visits.</div>
    </div>`+
    `<div class="strat-nav">
      <button class="active" onclick="stratNav('sec-basics',this)">📘 Basics</button>
      <button onclick="stratNav('sec-operators',this)">🎯 Operators (${SIEGE_OPERATORS.length})</button>
      <button onclick="stratNav('sec-maps',this)">🗺️ Maps (${SIEGE_MAPS.length})</button>
      <button onclick="stratNav('sec-glossary',this)">📖 Glossary</button>
      <button onclick="stratNav('sec-quiz',this)">🎮 Quiz</button>
    </div>`+
    `<details class="strat-section" id="sec-basics" open><summary>📘 Basics <span class="strat-section-count">roles, phases, fundamentals</span><span class="chev">\u25BE</span></summary><div class="strat-section-body">`+
      `<div class="strat-subhead">Operator Roles</div>${roles}`+
      `<div class="strat-subhead">Round Phases</div>${phases}`+
      fund+
    `</div></details>`+
    `<details class="strat-section" id="sec-operators"><summary>🎯 Operators <span class="strat-section-count">${SIEGE_OPERATORS.length} total</span><span class="chev">\u25BE</span></summary><div class="strat-section-body">`+
      `<div class="op-filter-row">
        <button class="active" onclick="opFilter('all',this)">All</button>
        <button onclick="opFilter('atk',this)">🔴 Attack</button>
        <button onclick="opFilter('def',this)">🔵 Defense</button>
      </div>`+
      `<div class="strat-subhead" data-side="atk">🔴 Attacking Operators</div><div data-side="atk">${atk}</div>`+
      `<div class="strat-subhead" data-side="def">🔵 Defending Operators</div><div data-side="def">${def}</div>`+
    `</div></details>`+
    `<details class="strat-section" id="sec-maps"><summary>🗺️ Maps <span class="strat-section-count">${SIEGE_MAPS.length} total, ${RANKED_MAPS.size} ranked</span><span class="chev">\u25BE</span></summary><div class="strat-section-body">`+
      `<p class="rev-p">Tap a map to jump straight to it. 🏆 marks maps currently in the Ranked pool (this rotates most seasons).</p>`+
      mapJump+
      maps+
    `</div></details>`+
    `<details class="strat-section" id="sec-glossary"><summary>📖 Glossary <span class="strat-section-count">${SIEGE_GLOSSARY.length} terms</span><span class="chev">\u25BE</span></summary><div class="strat-section-body">`+
      gloss+
    `</div></details>`+
    `<details class="strat-section" id="sec-quiz"><summary>🎮 "What Would You Do?" Quiz <span class="strat-section-count">${QUIZ_QUESTIONS.length} questions</span><span class="chev">\u25BE</span></summary><div class="strat-section-body">`+
      `<p class="rev-p" style="margin-bottom:12px;">Decision-style questions, not trivia — some tied to Bank's real layout, the rest built on well-known gadget interactions and the fundamentals above.</p>`+
      `<div id="quizWrap"></div>`+
    `</div></details>`+
    `<div class="strat-note">General, long-standing concepts for ${SIEGE_MAPS.length} of Siege's most established maps and ${SIEGE_OPERATORS.length} operators' core kits, plus roles/phases that hold up across balance patches — with a general attack and defense plan per map and a tip per operator. Ranked/Pro League badges and role tags are a snapshot from mid-2026 and will drift as Ubisoft rotates map pools and rebalances kits. There are no per-operator-per-map site callouts, since those shift every season. Tell me a specific map or operator and I'll actually verify current-season details instead of guessing.</div>`;
}

function dataFor(idx){
  const [title,studio,rating,desc,tags]=SEED[idx];
  const data={title,studio,rating,desc,tags};
  Object.assign(data,priceInfo(idx),modesFor(idx),salesFor(idx,data.rating));
  return data;
}
function renderLibrary(){
  const rows=(set,emptyMsg)=>{
    const arr=[...set];
    if(!arr.length)return `<div class="lib-empty">${emptyMsg}</div>`;
    return arr.map(idx=>{
      const g=peekGame(idx);
      return `<div class="lib-row" data-idx="${idx}"><div class="lib-swatch" style="background:hsl(${GENRE_HUE[g.tags[0]]??200} 45% 28%)"></div><div><div class="lib-title">${g.title}</div><div class="lib-sub">${g.studio} — ★ ${g.rating.toFixed(1)}</div></div></div>`;
    }).join('');
  };
  document.getElementById('libLiked').innerHTML=rows(liked,'No liked games yet — heart a card in the feed.');
  document.getElementById('libSaved').innerHTML=rows(saved,'No starred games yet — star a card to save it here.');
  document.querySelectorAll('.lib-row').forEach(row=>{
    row.onclick=()=>openReview(dataFor(Number(row.dataset.idx)),Number(row.dataset.idx));
  });
}

// ---------- AI Game Finder (uses the viewer's own Claude via the sample capability) ----------
(async function initAIFinder(){
  const openBtn=document.getElementById('openAI'),wrap=document.getElementById('aiWrap');
  if(!openBtn||!wrap)return;
  let sample=null;
  try{ sample = window.claude ? await claude.use('sample') : null; }catch(e){ sample=null; }
  if(!sample)return; // hide gracefully when the capability isn't available
  openBtn.style.display='';
  const input=document.getElementById('aiInput'),go=document.getElementById('aiGo'),out=document.getElementById('aiOut');
  openBtn.onclick=()=>{wrap.classList.add('open');setTimeout(()=>input.focus(),50);};
  document.getElementById('closeAI').onclick=()=>wrap.classList.remove('open');
  wrap.onclick=e=>{if(e.target===wrap)wrap.classList.remove('open');};
  const norm=s=>String(s||'').toLowerCase().replace(/&/g,'and').replace(/[^a-z0-9]+/g,'');
  const byNorm=new Map();SEED.forEach((g,i)=>{const k=norm(g[0]);if(!byNorm.has(k))byNorm.set(k,i);});
  function findIdx(title){
    const k=norm(title);if(!k)return -1;
    if(byNorm.has(k))return byNorm.get(k);
    if(k.length>=7){for(const [nk,i] of byNorm){if(nk.length>=7&&(nk.startsWith(k)||k.startsWith(nk)))return i;}}
    return -1;
  }
  const errCopy={not_granted:"You'll need to allow this app to use Claude — then try again.",rate_limited:"Too many requests — give it a moment and try again.",cancelled:"Cancelled."};
  const row=(idx,why)=>{
    const g=SEED[idx];const d=document.createElement('div');d.className='sim-row';d.dataset.idx=idx;
    const cv=document.createElement('div');cv.className='sim-cv';cv.innerHTML=coverSVG(g[0],g[4],g[1]);d.appendChild(cv);
    const t=document.createElement('div');t.className='sim-t';
    const b=document.createElement('b');b.textContent=g[0];
    const s=document.createElement('span');s.textContent=g[1]+' — ★ '+Number(g[2]).toFixed(1)+' — '+g[4].join(' · ');
    t.appendChild(b);t.appendChild(s);
    if(why){const w=document.createElement('div');w.className='ai-why';w.textContent=why;t.appendChild(w);}
    const go2=document.createElement('div');go2.className='sim-go';go2.textContent='›';
    d.appendChild(t);d.appendChild(go2);
    d.onclick=()=>{wrap.classList.remove('open');openReview(dataFor(idx),idx);};
    return d;
  };
  async function run(){
    const q=(input.value||'').trim();
    if(!q||go.disabled)return;
    go.disabled=true;go.textContent='Finding games…';out.textContent='';
    const prompt='You are the game-matching engine inside DECK, a PS5 game discovery app. The player says: "'+q.replace(/"/g,"'")+'"\n\nPick 10 real, well-known games available on PlayStation (PS4 or PS5) that best match what they want. If they name a game, choose games a fan of it would likely enjoy (not the same game, but sequels or close siblings are fine). Use each game\'s exact official title. Respond with ONLY JSON, no markdown: {"intro":"one friendly sentence","picks":[{"title":"...","why":"one short sentence on why it fits"}]}';
    try{
      const res=await sample.json(prompt,{cache:false,modelTier:'quick'});
      const picks=Array.isArray(res&&res.picks)?res.picks.slice(0,12):[];
      const seen=new Set(),found=[],missing=[];
      picks.forEach(p=>{const i=findIdx(p&&p.title);if(i>=0){if(!seen.has(i)){seen.add(i);found.push([i,String(p.why||'').slice(0,200)]);}}else if(p&&p.title)missing.push(String(p.title).slice(0,80));});
      out.textContent='';
      if(res&&res.intro){const p=document.createElement('div');p.className='ai-intro';p.textContent=String(res.intro).slice(0,300);out.appendChild(p);}
      if(found.length){const hint=document.createElement('div');hint.className='sim-hint';hint.textContent='In DECK — tap a game to open it';out.appendChild(hint);found.forEach(([i,w])=>out.appendChild(row(i,w)));}
      if(found.length<4&&found.length){
        const extra=similarGames(dataFor(found[0][0])).filter(s=>!seen.has(s.idx)).slice(0,4-found.length);
        if(extra.length){const hint=document.createElement('div');hint.className='sim-hint';hint.textContent='Also similar in DECK';out.appendChild(hint);extra.forEach(s=>out.appendChild(row(s.idx,'')));}
      }
      if(!found.length){const p=document.createElement('div');p.className='ai-intro';p.textContent="None of the suggestions are in DECK yet. Try describing the genre or vibe instead.";out.appendChild(p);}
      if(missing.length){const m=document.createElement('div');m.className='ai-miss';m.textContent='Also fits, but not in DECK yet: '+missing.join(', ');out.appendChild(m);}
    }catch(e){
      out.textContent=errCopy[e&&e.code]||"Something went wrong — please try again.";
    }finally{go.disabled=false;go.textContent='Find games';}
  }
  const ex=document.getElementById('aiEx');
  ['A game like Call of Duty: Modern Warfare III','Cozy game I can finish in a weekend','Great story, under 15 hours','Scary co-op game for friends'].forEach(t=>{const c=document.createElement('div');c.className='chip-toggle';c.textContent=t;c.onclick=()=>{input.value=t;run();};ex.appendChild(c);});
  document.getElementById('aiSurprise').onclick=()=>{const pool=[];SEED.forEach((g,i)=>{if(g[2]>=85)pool.push(i);});const i=pool[Math.floor(Math.random()*pool.length)];wrap.classList.remove('open');openReview(dataFor(i),i);};
  go.onclick=run;
  input.addEventListener('keydown',e=>{if(e.key==='Enter'&&!e.shiftKey){e.preventDefault();run();}});
})();

// ---------- polish: toast + first-visit swipe hint ----------
function toast(msg){
  try{
    let t=document.getElementById('toast');
    if(!t){t=document.createElement('div');t.id='toast';t.setAttribute('role','status');t.setAttribute('aria-live','polite');document.body.appendChild(t);}
    t.textContent=msg;t.classList.add('show');
    clearTimeout(toast._t);toast._t=setTimeout(()=>t.classList.remove('show'),1600);
  }catch(e){}
}
(function swipeHint(){
  try{
    let seen=false;try{seen=localStorage.getItem('deckSwipeHint')==='1';}catch(e){}
    if(seen)return;
    const hint=document.createElement('div');hint.id='swipeHint';hint.innerHTML='<b>⌃</b>Swipe up for the next game';document.body.appendChild(hint);
    const hide=()=>{hint.classList.add('gone');setTimeout(()=>hint.remove(),400);try{localStorage.setItem('deckSwipeHint','1');}catch(e){}};
    const f=document.getElementById('feed');
    if(f)f.addEventListener('scroll',()=>{if(f.scrollTop>40)hide();},{passive:true,once:false});
    setTimeout(hide,9000);
  }catch(e){}
})();
</script>
</body>
</html>
