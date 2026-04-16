# SynapseEnglishTest
# 📖
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>IT English Test</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #070b14;
  --bg2: #0d1220;
  --card: #0f1623;
  --card2: #131c2e;
  --border: #1a2540;
  --border2: #243050;
  --green: #22c55e;
  --green2: #16a34a;
  --green-glow: rgba(34,197,94,0.15);
  --blue: #3b82f6;
  --blue-glow: rgba(59,130,246,0.15);
  --text: #e2e8f0;
  --text2: #64748b;
  --text3: #94a3b8;
  --red: #ef4444;
  --orange: #f97316;
  --yellow: #eab308;
}

*{margin:0;padding:0;box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{
  background:var(--bg);
  color:var(--text);
  font-family:'DM Sans',sans-serif;
  min-height:100vh;
  overflow-x:hidden;
}

/* ── ANIMATED BACKGROUND ── */
#bgCanvas{position:fixed;inset:0;z-index:0;pointer-events:none;}

body::before{
  content:'';position:fixed;inset:0;
  background-image:
    linear-gradient(rgba(34,197,94,0.022) 1px,transparent 1px),
    linear-gradient(90deg,rgba(34,197,94,0.022) 1px,transparent 1px);
  background-size:60px 60px;
  pointer-events:none;z-index:0;
  animation:gridPulse 8s ease-in-out infinite;
}
@keyframes gridPulse{0%,100%{opacity:1;}50%{opacity:0.45;}}

.bg-orb{position:fixed;border-radius:50%;filter:blur(90px);pointer-events:none;z-index:0;}
.bg-orb1{width:700px;height:700px;background:radial-gradient(circle,rgba(34,197,94,0.06) 0%,transparent 65%);top:-200px;left:-150px;animation:orb1Float 12s ease-in-out infinite;}
.bg-orb2{width:500px;height:500px;background:radial-gradient(circle,rgba(59,130,246,0.05) 0%,transparent 65%);bottom:0;right:-100px;animation:orb2Float 15s ease-in-out infinite;}
.bg-orb3{width:350px;height:350px;background:radial-gradient(circle,rgba(34,197,94,0.03) 0%,transparent 65%);top:40%;left:50%;animation:orb3Float 18s ease-in-out infinite;}
@keyframes orb1Float{0%,100%{transform:translate(0,0) scale(1);}33%{transform:translate(40px,-30px) scale(1.05);}66%{transform:translate(-20px,20px) scale(0.95);}}
@keyframes orb2Float{0%,100%{transform:translate(0,0) scale(1);}50%{transform:translate(-50px,-40px) scale(1.08);}}
@keyframes orb3Float{0%,100%{transform:translate(-50%,-50%) scale(1);opacity:0.6;}50%{transform:translate(-50%,-50%) scale(1.3);opacity:1;}}

.scan-line{
  position:fixed;left:0;right:0;height:1px;z-index:0;pointer-events:none;
  background:linear-gradient(90deg,transparent 0%,rgba(34,197,94,0.12) 30%,rgba(34,197,94,0.35) 50%,rgba(34,197,94,0.12) 70%,transparent 100%);
  animation:scanMove 9s linear infinite;
  box-shadow:0 0 10px rgba(34,197,94,0.18);
}
@keyframes scanMove{0%{top:-2px;opacity:0;}5%{opacity:1;}95%{opacity:1;}100%{top:100vh;opacity:0;}}

/* ── HEADER ── */
.header{
  position:sticky;top:0;z-index:100;
  display:flex;align-items:center;justify-content:space-between;
  padding:0 32px;height:64px;
  background:rgba(7,11,20,0.82);
  backdrop-filter:blur(20px);
  border-bottom:1px solid var(--border);
}
.logo{display:flex;align-items:center;gap:10px;text-decoration:none;}
.logo-hex{width:32px;height:32px;position:relative;display:flex;align-items:center;justify-content:center;}
.logo-hex svg{width:32px;height:32px;}
.logo-text{font-family:'Syne',sans-serif;font-weight:800;font-size:18px;letter-spacing:4px;color:var(--text);}
.header-right{display:flex;align-items:center;gap:16px;}
.header-badge{
  background:var(--green-glow);
  border:1px solid rgba(34,197,94,0.3);
  color:var(--green);font-size:11px;font-weight:500;
  padding:4px 12px;border-radius:100px;letter-spacing:0.5px;
}
.about-link{
  color:var(--text2);font-size:14px;text-decoration:none;transition:color 0.2s;
  cursor:pointer;background:none;border:none;font-family:'DM Sans',sans-serif;
}
.about-link:hover{color:var(--text);}

/* ── HIDDEN ADMIN ICON ── */
.admin-trigger{
  position:fixed;right:18px;bottom:24px;z-index:150;
  width:22px;height:22px;
  opacity:0.12;
  cursor:pointer;
  transition:opacity 0.3s,transform 0.3s,box-shadow 0.3s;
  border-radius:6px;
  display:flex;align-items:center;justify-content:center;
  font-size:14px;
  filter:grayscale(0.6);
}
.admin-trigger:hover{
  opacity:0.55;
  transform:scale(1.3);
  box-shadow:0 0 14px rgba(34,197,94,0.5);
  filter:grayscale(0);
}

/* ── MODAL OVERLAY ── */
.modal-overlay{
  display:none;
  position:fixed;inset:0;z-index:300;
  background:rgba(7,11,20,0.75);
  backdrop-filter:blur(10px);
  align-items:center;justify-content:center;
}
.modal-overlay.open{display:flex;animation:modalFadeIn 0.3s ease;}
@keyframes modalFadeIn{from{opacity:0;}to{opacity:1;}}

.modal-box{
  background:rgba(15,22,35,0.92);
  border:1px solid var(--border2);
  border-radius:20px;
  padding:40px 36px;
  width:100%;max-width:400px;
  position:relative;
  box-shadow:0 0 60px rgba(34,197,94,0.1),0 20px 60px rgba(0,0,0,0.6);
  animation:modalScaleIn 0.3s cubic-bezier(0.34,1.56,0.64,1);
}
@keyframes modalScaleIn{from{opacity:0;transform:scale(0.88);}to{opacity:1;transform:scale(1);}}
.modal-box::before{
  content:'';position:absolute;top:0;left:0;right:0;height:1px;
  background:linear-gradient(90deg,transparent,rgba(34,197,94,0.5),transparent);
  border-radius:20px 20px 0 0;
}

.modal-close{
  position:absolute;top:14px;right:16px;
  background:none;border:none;color:var(--text2);
  font-size:20px;cursor:pointer;transition:color 0.2s;
  line-height:1;padding:4px;
}
.modal-close:hover{color:var(--text);}
.modal-title{
  font-family:'Syne',sans-serif;
  font-size:22px;font-weight:800;margin-bottom:6px;letter-spacing:-0.5px;
}
.modal-sub{color:var(--text3);font-size:13px;margin-bottom:28px;}

.field-group{margin-bottom:16px;}
.field-label{color:var(--text3);font-size:11px;font-weight:500;letter-spacing:1px;text-transform:uppercase;margin-bottom:6px;}
.field-input{
  width:100%;
  background:var(--card2);
  border:1px solid var(--border2);
  border-radius:10px;
  padding:12px 14px;
  font-size:14px;
  font-family:'DM Sans',sans-serif;
  color:var(--text);
  outline:none;
  transition:border-color 0.2s,box-shadow 0.2s;
}
.field-input:focus{
  border-color:var(--green);
  box-shadow:0 0 0 2px rgba(34,197,94,0.12);
}
.modal-error{
  background:rgba(239,68,68,0.1);
  border:1px solid rgba(239,68,68,0.3);
  color:#f87171;
  border-radius:8px;padding:10px 14px;
  font-size:13px;margin-bottom:16px;
  display:none;
}

/* ── ABOUT PAGE ── */
#aboutPage{display:none;position:fixed;inset:0;z-index:200;background:var(--bg);overflow-y:auto;}
.about-content{max-width:700px;margin:0 auto;padding:80px 24px;position:relative;z-index:1;}
.about-back{
  display:inline-flex;align-items:center;gap:8px;
  color:var(--text2);font-size:14px;cursor:pointer;margin-bottom:40px;
  background:none;border:none;transition:color 0.2s;font-family:'DM Sans',sans-serif;
}
.about-back:hover{color:var(--text);}
.about-h1{font-family:'Syne',sans-serif;font-size:48px;font-weight:800;letter-spacing:-2px;margin-bottom:16px;}
.about-p{color:var(--text3);font-size:15px;line-height:1.8;margin-bottom:14px;}
.team-grid{display:flex;flex-wrap:wrap;gap:16px;margin:40px 0;}
.team-card{
  background:var(--card);border:1px solid var(--border);
  border-radius:16px;padding:28px 24px;text-align:center;
  flex:1 1 160px;min-width:0;transition:all 0.3s;
}
.team-card:hover{border-color:rgba(34,197,94,0.3);transform:translateY(-4px);box-shadow:0 8px 32px rgba(34,197,94,0.1);}
.team-av{font-size:44px;margin-bottom:12px;}
.team-name{font-family:'Syne',sans-serif;font-weight:700;font-size:18px;margin-bottom:6px;}
.team-role{color:var(--green);font-size:13px;}

/* ── PAGES ── */
.page{display:none;position:relative;z-index:1;}
.page.active{display:block;}
.page-enter{animation:fadeIn 0.4s ease forwards;}
@keyframes fadeIn{from{opacity:0;transform:translateY(16px);}to{opacity:1;transform:translateY(0);}}

/* ── LANDING ── */
.hero{text-align:center;padding:80px 20px 52px;position:relative;z-index:1;}
.hero-eyebrow{
  display:inline-flex;align-items:center;gap:8px;
  background:var(--green-glow);
  border:1px solid rgba(34,197,94,0.25);
  color:var(--green);font-size:12px;font-weight:500;
  letter-spacing:1.5px;padding:6px 16px;border-radius:100px;
  margin-bottom:28px;text-transform:uppercase;
}
.hero-eyebrow::before{content:'';width:6px;height:6px;background:var(--green);border-radius:50%;animation:pulse 2s infinite;}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1);}50%{opacity:0.5;transform:scale(0.8);}}
.hero-title{
  font-family:'Syne',sans-serif;
  font-size:clamp(38px,6vw,74px);font-weight:800;line-height:1.05;
  letter-spacing:-2px;margin-bottom:22px;
}
.hero-title .accent{
  background:linear-gradient(135deg,#22c55e 0%,#4ade80 50%,#86efac 100%);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.hero-sub{color:var(--text3);font-size:clamp(15px,2vw,18px);max-width:560px;margin:0 auto 44px;line-height:1.75;font-weight:300;}

/* ── BUTTONS ── */
.btn{
  display:inline-flex;align-items:center;gap:8px;
  background:linear-gradient(135deg,#22c55e,#16a34a);
  color:#fff;font-size:15px;font-weight:600;
  padding:14px 32px;border-radius:12px;border:none;
  cursor:pointer;transition:all 0.25s;
  box-shadow:0 0 24px rgba(34,197,94,0.3);
  font-family:'DM Sans',sans-serif;letter-spacing:0.3px;
}
.btn:hover{transform:translateY(-2px);box-shadow:0 0 36px rgba(34,197,94,0.45);}
.btn:active{transform:translateY(0);}
.btn-ghost{background:transparent;border:1px solid var(--border2);color:var(--text3);box-shadow:none;}
.btn-ghost:hover{border-color:var(--green);color:var(--green);box-shadow:0 0 18px rgba(34,197,94,0.15);}
.btn-outline{background:transparent;border:1px solid rgba(34,197,94,0.4);color:var(--green);box-shadow:0 0 12px rgba(34,197,94,0.1);}
.btn-outline:hover{background:var(--green-glow);box-shadow:0 0 24px rgba(34,197,94,0.25);}
.btn-red{background:linear-gradient(135deg,#ef4444,#dc2626);box-shadow:0 0 20px rgba(239,68,68,0.25);}
.btn-red:hover{box-shadow:0 0 32px rgba(239,68,68,0.4);}

/* FEATURES */
.features{position:relative;z-index:1;display:flex;flex-wrap:wrap;gap:20px;justify-content:center;padding:0 20px 60px;max-width:960px;margin:0 auto;}
.feat-card{
  background:var(--card);border:1px solid var(--border);
  border-radius:16px;padding:28px 28px 24px;
  flex:1;min-width:220px;max-width:280px;
  transition:all 0.3s;position:relative;overflow:hidden;
}
.feat-card::before{content:'';position:absolute;inset:0;background:linear-gradient(135deg,rgba(34,197,94,0.04) 0%,transparent 60%);pointer-events:none;}
.feat-card:hover{border-color:rgba(34,197,94,0.3);transform:translateY(-4px);box-shadow:0 8px 32px rgba(34,197,94,0.1);}
.feat-icon{font-size:28px;margin-bottom:14px;}
.feat-title{font-family:'Syne',sans-serif;font-weight:700;font-size:15px;margin-bottom:8px;color:var(--text);}
.feat-desc{color:var(--text3);font-size:13px;line-height:1.65;}

/* SETUP */
.setup-wrap{max-width:520px;margin:0 auto;padding:60px 20px;text-align:center;position:relative;z-index:1;}
.setup-title{font-family:'Syne',sans-serif;font-size:clamp(26px,4vw,38px);font-weight:800;margin-bottom:12px;letter-spacing:-1px;}
.setup-sub{color:var(--text3);font-size:14px;margin-bottom:40px;}
.count-grid{display:flex;gap:14px;justify-content:center;flex-wrap:wrap;margin-bottom:36px;}
.count-btn{
  background:var(--card);border:1px solid var(--border2);border-radius:14px;padding:20px 32px;
  cursor:pointer;transition:all 0.25s;color:var(--text);font-size:28px;font-weight:700;
  font-family:'Syne',sans-serif;min-width:110px;
}
.count-btn:hover{border-color:var(--green);box-shadow:0 0 20px rgba(34,197,94,0.15);}
.count-btn.selected{border-color:var(--green);background:var(--green-glow);color:var(--green);box-shadow:0 0 24px rgba(34,197,94,0.2);}
.count-label{font-size:11px;color:var(--text2);font-weight:400;margin-top:4px;letter-spacing:0.5px;}

/* TEST */
.test-wrap{max-width:680px;margin:0 auto;padding:40px 20px 80px;position:relative;z-index:1;}
.progress-row{display:flex;align-items:center;justify-content:space-between;margin-bottom:20px;}
.progress-label{color:var(--text3);font-size:13px;}
.progress-score{background:var(--green-glow);border:1px solid rgba(34,197,94,0.25);border-radius:100px;padding:4px 14px;font-size:12px;color:var(--green);font-weight:500;}
.progress-bar-wrap{background:var(--card);border:1px solid var(--border);border-radius:100px;height:6px;margin-bottom:32px;overflow:hidden;}
.progress-bar-fill{height:100%;border-radius:100px;background:linear-gradient(90deg,#22c55e,#4ade80);transition:width 0.5s cubic-bezier(0.4,0,0.2,1);box-shadow:0 0 10px rgba(34,197,94,0.4);}
.q-card{
  background:var(--card);border:1px solid var(--border);
  border-radius:20px;padding:36px 36px 28px;margin-bottom:20px;
  backdrop-filter:blur(10px);position:relative;overflow:hidden;
}
.q-card::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,rgba(34,197,94,0.4),transparent);}
.q-word-label{color:var(--text2);font-size:11px;font-weight:500;letter-spacing:2px;text-transform:uppercase;margin-bottom:12px;}
.q-word{
  font-family:'Syne',sans-serif;font-size:clamp(28px,5vw,48px);
  font-weight:800;letter-spacing:-1px;margin-bottom:8px;
  background:linear-gradient(135deg,#e2e8f0,#94a3b8);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.q-prompt{color:var(--text3);font-size:14px;margin-top:4px;}
.options-grid{display:flex;flex-direction:column;gap:10px;margin-bottom:20px;}
.opt-btn{
  background:var(--card2);border:1px solid var(--border);
  border-radius:14px;padding:16px 22px;cursor:pointer;transition:all 0.2s;
  display:flex;align-items:center;gap:14px;font-size:15px;
  font-family:'DM Sans',sans-serif;color:var(--text);text-align:left;
  position:relative;overflow:hidden;
}
.opt-btn::before{content:'';position:absolute;inset:0;background:linear-gradient(90deg,var(--green-glow),transparent);opacity:0;transition:opacity 0.2s;}
.opt-btn:hover:not(:disabled)::before{opacity:1;}
.opt-btn:hover:not(:disabled){border-color:rgba(34,197,94,0.35);transform:translateX(4px);}
.opt-btn:disabled{cursor:default;}
.opt-letter{width:28px;height:28px;border-radius:8px;background:var(--border2);display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:700;color:var(--text3);flex-shrink:0;transition:all 0.2s;}
.opt-btn.correct{border-color:var(--green)!important;background:rgba(34,197,94,0.08)!important;box-shadow:0 0 20px rgba(34,197,94,0.15);}
.opt-btn.correct .opt-letter{background:var(--green);color:#fff;}
.opt-btn.wrong{border-color:var(--red)!important;background:rgba(239,68,68,0.08)!important;}
.opt-btn.wrong .opt-letter{background:var(--red);color:#fff;}
.opt-btn.dimmed{opacity:0.35;}
.feedback-box{border-radius:12px;padding:14px 18px;font-size:13px;line-height:1.6;margin-bottom:16px;border:1px solid;animation:feedbackIn 0.3s ease;}
@keyframes feedbackIn{from{opacity:0;transform:translateY(6px);}to{opacity:1;transform:translateY(0);}}
.feedback-box.ok{background:rgba(34,197,94,0.08);border-color:rgba(34,197,94,0.3);color:#4ade80;}
.feedback-box.fail{background:rgba(239,68,68,0.08);border-color:rgba(239,68,68,0.3);color:#f87171;}
.next-row{display:flex;justify-content:flex-end;}

/* RESULTS */
.results-wrap{max-width:640px;margin:0 auto;padding:52px 20px 80px;text-align:center;position:relative;z-index:1;}
.result-score-ring{width:160px;height:160px;margin:0 auto 32px;position:relative;}
.result-score-ring svg{width:160px;height:160px;transform:rotate(-90deg);}
.ring-bg{fill:none;stroke:var(--border2);stroke-width:10;}
.ring-fill{fill:none;stroke-width:10;stroke-linecap:round;transition:stroke-dashoffset 1.2s cubic-bezier(0.4,0,0.2,1);}
.score-center{position:absolute;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;}
.score-pct{font-family:'Syne',sans-serif;font-size:36px;font-weight:800;line-height:1;}
.score-label{color:var(--text3);font-size:11px;letter-spacing:1.5px;margin-top:4px;}
.result-title{font-family:'Syne',sans-serif;font-size:26px;font-weight:800;margin-bottom:8px;}
.result-tip{color:var(--text3);font-size:14px;margin-bottom:36px;line-height:1.6;}
.stats-row{display:flex;gap:14px;justify-content:center;margin-bottom:36px;flex-wrap:wrap;}
.stat-card{background:var(--card);border:1px solid var(--border);border-radius:14px;padding:18px 26px;flex:1;min-width:120px;}
.stat-num{font-family:'Syne',sans-serif;font-size:28px;font-weight:800;}
.stat-num.green{color:var(--green);}
.stat-num.red{color:var(--red);}
.stat-text{color:var(--text2);font-size:11px;margin-top:4px;letter-spacing:0.5px;}
.errors-section{background:var(--card);border:1px solid var(--border);border-radius:16px;margin-bottom:24px;overflow:hidden;}
.errors-section.collapsed .errors-body{display:none;}
.errors-header{display:flex;align-items:center;justify-content:space-between;padding:16px 22px;cursor:pointer;border-bottom:1px solid var(--border);user-select:none;transition:background 0.2s;}
.errors-header:hover{background:rgba(255,255,255,0.02);}
.errors-header-left{display:flex;align-items:center;gap:10px;}
.errors-badge{background:rgba(239,68,68,0.15);border:1px solid rgba(239,68,68,0.3);color:var(--red);font-size:11px;padding:2px 9px;border-radius:100px;font-weight:600;}
.errors-toggle{color:var(--text2);font-size:18px;transition:transform 0.3s;}
.errors-section:not(.collapsed) .errors-toggle{transform:rotate(180deg);}
.errors-body{max-height:400px;overflow-y:auto;}
.errors-body::-webkit-scrollbar{width:4px;}
.errors-body::-webkit-scrollbar-track{background:transparent;}
.errors-body::-webkit-scrollbar-thumb{background:var(--border2);border-radius:2px;}
.error-item{display:flex;align-items:flex-start;gap:14px;padding:14px 22px;border-bottom:1px solid var(--border);}
.error-item:last-child{border-bottom:none;}
.error-word{font-weight:600;font-size:14px;min-width:160px;color:var(--text);flex-shrink:0;}
.error-meta{font-size:12px;line-height:1.7;text-align:left;}
.error-correct{color:var(--green);}
.error-wrong{color:var(--red);}
.results-actions{display:flex;gap:14px;justify-content:center;flex-wrap:wrap;}

/* SHIMMER */
@keyframes shimmer{0%{background-position:200% center;}100%{background-position:-200% center;}}
.shimmer-text{background:linear-gradient(90deg,#22c55e,#86efac,#22c55e,#4ade80);background-size:200% auto;-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;animation:shimmer 3s linear infinite;}

/* ══════════════════════════════════
   ADMIN PAGE
══════════════════════════════════ */
#adminPage{
  display:none;
  position:fixed;inset:0;z-index:250;
  background:var(--bg);
  overflow-y:auto;
}
.admin-wrap{
  max-width:900px;margin:0 auto;
  padding:60px 24px 140px;
  position:relative;z-index:1;
}
.admin-header-row{
  display:flex;align-items:center;justify-content:space-between;
  flex-wrap:wrap;gap:14px;
  margin-bottom:40px;
}
.admin-title{
  font-family:'Syne',sans-serif;
  font-size:32px;font-weight:800;letter-spacing:-1px;
}
.admin-title span{
  background:linear-gradient(135deg,#22c55e,#86efac);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
}
.admin-badge{
  background:rgba(34,197,94,0.12);
  border:1px solid rgba(34,197,94,0.3);
  color:var(--green);font-size:11px;font-weight:600;
  padding:4px 12px;border-radius:100px;letter-spacing:1px;
}

/* TABLE */
.admin-table-wrap{
  background:var(--card);border:1px solid var(--border);
  border-radius:16px;overflow:hidden;margin-bottom:20px;
}
.admin-table{width:100%;border-collapse:collapse;}
.admin-table thead th{
  padding:14px 18px;
  background:var(--card2);
  border-bottom:1px solid var(--border2);
  color:var(--text3);font-size:11px;font-weight:600;
  letter-spacing:1.5px;text-transform:uppercase;
  text-align:left;
}
.admin-table tbody tr{
  border-bottom:1px solid var(--border);
  transition:background 0.15s;
}
.admin-table tbody tr:last-child{border-bottom:none;}
.admin-table tbody tr:hover{background:rgba(34,197,94,0.02);}
.admin-table td{padding:10px 12px;vertical-align:middle;}
.tbl-idx{
  color:var(--text2);font-size:12px;
  width:44px;text-align:center;font-family:'Syne',sans-serif;
}
.tbl-input{
  width:100%;background:transparent;border:1px solid transparent;
  border-radius:8px;padding:8px 10px;
  color:var(--text);font-size:14px;font-family:'DM Sans',sans-serif;
  outline:none;transition:border-color 0.2s,background 0.2s;
}
.tbl-input:focus{
  border-color:var(--green);
  background:rgba(34,197,94,0.05);
}
.tbl-input.empty-field{border-color:rgba(239,68,68,0.4);background:rgba(239,68,68,0.04);}
.tbl-del{
  width:48px;text-align:center;
}
.del-btn{
  background:rgba(239,68,68,0.1);
  border:1px solid rgba(239,68,68,0.25);
  color:var(--red);border-radius:8px;
  width:32px;height:32px;cursor:pointer;
  font-size:16px;font-weight:700;
  display:inline-flex;align-items:center;justify-content:center;
  transition:all 0.2s;
  line-height:1;
}
.del-btn:hover{
  background:rgba(239,68,68,0.2);
  box-shadow:0 0 14px rgba(239,68,68,0.35);
  transform:scale(1.1);
}

/* ADD BUTTON */
.btn-add{
  display:inline-flex;align-items:center;gap:8px;
  background:var(--green-glow);
  border:1px solid rgba(34,197,94,0.4);
  color:var(--green);font-size:14px;font-weight:600;
  padding:11px 22px;border-radius:10px;
  cursor:pointer;transition:all 0.25s;
  font-family:'DM Sans',sans-serif;
}
.btn-add:hover{background:rgba(34,197,94,0.2);box-shadow:0 0 20px rgba(34,197,94,0.25);}

/* SAVE BUTTON */
.btn-save{
  display:block;width:100%;
  background:linear-gradient(90deg,#22c55e,#4ade80,#22c55e);
  background-size:200% auto;
  color:#fff;font-size:16px;font-weight:700;
  padding:16px 32px;border-radius:12px;border:none;
  cursor:pointer;transition:all 0.3s;
  box-shadow:0 0 28px rgba(34,197,94,0.35);
  font-family:'Syne',sans-serif;letter-spacing:0.5px;
  animation:savePulse 3s linear infinite;
}
@keyframes savePulse{0%{background-position:0% center;}100%{background-position:200% center;}}
.btn-save:hover{transform:translateY(-2px);box-shadow:0 0 44px rgba(34,197,94,0.55);}
.btn-save:disabled{
  background:var(--card2);color:var(--text2);
  box-shadow:none;cursor:not-allowed;
  animation:none;transform:none;
  border:1px solid var(--border);
}
.save-hint{color:var(--text2);font-size:12px;text-align:center;margin-top:10px;}

/* ADMIN SCROLL BUTTONS */
.admin-scroll-btns{
  position:fixed;right:22px;bottom:80px;z-index:260;
  display:none;flex-direction:column;gap:10px;
}
.admin-scroll-btns.visible{display:flex;}
.scroll-fab{
  width:42px;height:42px;border-radius:12px;
  background:rgba(15,22,35,0.88);
  border:1px solid var(--border2);
  color:var(--green);font-size:18px;
  display:flex;align-items:center;justify-content:center;
  cursor:pointer;transition:all 0.25s;
  backdrop-filter:blur(12px);
  box-shadow:0 0 14px rgba(34,197,94,0.12);
}
.scroll-fab:hover{
  border-color:var(--green);
  box-shadow:0 0 22px rgba(34,197,94,0.35);
  transform:translateY(-2px);
}

/* SAVE TOAST */
.save-toast{
  position:fixed;bottom:32px;left:50%;transform:translateX(-50%) translateY(80px);
  background:rgba(15,22,35,0.95);
  border:1px solid rgba(34,197,94,0.4);
  border-radius:12px;padding:12px 24px;
  color:var(--green);font-size:14px;font-weight:500;
  z-index:400;transition:transform 0.4s cubic-bezier(0.34,1.56,0.64,1),opacity 0.3s;
  opacity:0;white-space:nowrap;
  box-shadow:0 0 30px rgba(34,197,94,0.2);
}
.save-toast.show{transform:translateX(-50%) translateY(0);opacity:1;}

@media(max-width:520px){
  .header{padding:0 16px;}
  .q-card{padding:24px 20px 18px;}
  .feat-card{min-width:160px;}
  .admin-table thead th:first-child{display:none;}
  .tbl-idx{display:none;}
}
</style>
</head>
<body>

<!-- BG LAYERS -->
<canvas id="bgCanvas"></canvas>
<div class="bg-orb bg-orb1"></div>
<div class="bg-orb bg-orb2"></div>
<div class="bg-orb bg-orb3"></div>
<div class="scan-line"></div>

<!-- HEADER -->
<header class="header">
  <a class="logo" href="#" onclick="goTo('landing');return false;">
    <div class="logo-hex">
      <svg viewBox="0 0 32 32" fill="none">
        <path d="M16 2L28 9V23L16 30L4 23V9L16 2Z" stroke="#22c55e" stroke-width="1.5" fill="rgba(34,197,94,0.08)"/>
        <path d="M16 8L22 11.5V18.5L16 22L10 18.5V11.5L16 8Z" fill="rgba(34,197,94,0.15)" stroke="#22c55e" stroke-width="0.8"/>
      </svg>
    </div>
    <span class="logo-text">SYNAPSE</span>
  </a>
  <div class="header-right">
    <span class="header-badge">IT ENGLISH</span>
    <button class="about-link" onclick="showAbout()">О команде</button>
  </div>
</header>

<!-- HIDDEN ADMIN TRIGGER -->
<div class="admin-trigger" onclick="openAdminModal()" title="">⚙</div>

<!-- ══ MODAL: ADMIN LOGIN ══ -->
<div class="modal-overlay" id="adminModal" onclick="closeAdminModalOutside(event)">
  <div class="modal-box">
    <button class="modal-close" onclick="closeAdminModal()">✕</button>
    <div class="modal-title">Вход в Админ-Панель</div>
    <div class="modal-sub">Доступ только для авторизованных</div>
    <div class="modal-error" id="loginError">Неверный логин или пароль</div>
    <div class="field-group">
      <div class="field-label">Логин</div>
      <input class="field-input" id="loginUser" type="text" autocomplete="off" placeholder="Введите логин" onkeydown="if(event.key==='Enter')doLogin()">
    </div>
    <div class="field-group">
      <div class="field-label">Пароль</div>
      <input class="field-input" id="loginPass" type="password" autocomplete="off" placeholder="Введите пароль" onkeydown="if(event.key==='Enter')doLogin()">
    </div>
    <button class="btn" style="width:100%;justify-content:center;margin-top:8px;" onclick="doLogin()">Войти</button>
  </div>
</div>

<!-- ══════════════ PAGE: LANDING ══════════════ -->
<div id="page-landing" class="page active page-enter">
  <div class="hero">
    <div class="hero-eyebrow">Vocabulary Trainer</div>
    <h1 class="hero-title">
      IT English<br>
      <span class="accent">Test</span>
    </h1>
    <p class="hero-sub">
      Проверь свои знания английского языка в сфере IT. Учи термины, тренируй память и анализируй ошибки.
    </p>
    <button class="btn" onclick="goTo('setup')">
      Начать тестирование &rarr;
    </button>
  </div>

  <div class="features">
    <div class="feat-card">
      <div class="feat-icon">🎯</div>
      <div class="feat-title">Практика IT-лексики</div>
      <div class="feat-desc">Более 290 реальных IT-терминов: сети, ПО, интерфейс, безопасность и многое другое.</div>
    </div>
    <div class="feat-card">
      <div class="feat-icon">⚡</div>
      <div class="feat-title">Быстрое тестирование</div>
      <div class="feat-desc">20, 45 или 100 вопросов на скорость — выбери нагрузку под своё настроение.</div>
    </div>
    <div class="feat-card">
      <div class="feat-icon">📊</div>
      <div class="feat-title">Анализ результатов</div>
      <div class="feat-desc">Точная статистика и список всех ошибок с правильными переводами после теста.</div>
    </div>
  </div>
</div>

<!-- ══════════════ PAGE: SETUP ══════════════ -->
<div id="page-setup" class="page">
  <div class="setup-wrap">
    <h2 class="setup-title">Выбери количество<br><span class="accent">вопросов</span></h2>
    <p class="setup-sub">Слова берутся случайно из базы в 290+ IT-терминов</p>

    <div class="count-grid">
      <div class="count-btn" data-count="20" onclick="selectCount(20,this)">
        <div>20</div>
        <div class="count-label">БЫСТРО</div>
      </div>
      <div class="count-btn" data-count="45" onclick="selectCount(45,this)">
        <div>45</div>
        <div class="count-label">СТАНДАРТ</div>
      </div>
      <div class="count-btn" data-count="100" onclick="selectCount(100,this)">
        <div>100</div>
        <div class="count-label">МАРАФОН</div>
      </div>
    </div>

    <button class="btn" id="startBtn" onclick="startTest()" disabled style="opacity:0.4;cursor:not-allowed;">
      Начать тест
    </button>
    <br><br>
    <button class="btn btn-ghost" onclick="goTo('landing')" style="font-size:13px;padding:10px 22px;">
      ← Назад
    </button>
  </div>
</div>

<!-- ══════════════ PAGE: TEST ══════════════ -->
<div id="page-test" class="page">
  <div class="test-wrap">
    <div class="progress-row">
      <span class="progress-label" id="progressLabel">1 / 20</span>
      <span class="progress-score" id="scoreLabel">✓ 0</span>
    </div>
    <div class="progress-bar-wrap">
      <div class="progress-bar-fill" id="progressFill" style="width:0%"></div>
    </div>

    <div class="q-card">
      <div class="q-word-label">СЛОВО</div>
      <div class="q-word" id="qWord">—</div>
      <div class="q-prompt">Переводится как:</div>
    </div>

    <div class="options-grid" id="optionsGrid"></div>
    <div id="feedbackBox"></div>
    <div class="next-row" id="nextRow" style="display:none;">
      <button class="btn" onclick="nextQuestion()">Следующий вопрос →</button>
    </div>
  </div>
</div>

<!-- ══════════════ PAGE: RESULTS ══════════════ -->
<div id="page-results" class="page">
  <div class="results-wrap">
    <div class="result-score-ring">
      <svg viewBox="0 0 160 160">
        <circle class="ring-bg" cx="80" cy="80" r="68"/>
        <circle class="ring-fill" id="ringFill" cx="80" cy="80" r="68"
          stroke-dasharray="427.26" stroke-dashoffset="427.26" stroke="#22c55e"/>
      </svg>
      <div class="score-center">
        <div class="score-pct" id="scorePct" style="color:#22c55e">0%</div>
        <div class="score-label">РЕЗУЛЬТАТ</div>
      </div>
    </div>

    <h2 class="result-title" id="resultTitle">Результаты теста</h2>
    <p class="result-tip" id="resultTip"></p>

    <div class="stats-row">
      <div class="stat-card"><div class="stat-num green" id="statCorrect">0</div><div class="stat-text">ПРАВИЛЬНО</div></div>
      <div class="stat-card"><div class="stat-num red" id="statWrong">0</div><div class="stat-text">ОШИБОК</div></div>
      <div class="stat-card"><div class="stat-num" id="statPct" style="color:#3b82f6">0%</div><div class="stat-text">ПРОЦЕНТ</div></div>
    </div>

    <div class="errors-section collapsed" id="errorsSection">
      <div class="errors-header" onclick="toggleErrors()">
        <div class="errors-header-left">
          <span style="font-weight:600;font-size:14px;">Мои ошибки</span>
          <span class="errors-badge" id="errorsBadge">0</span>
        </div>
        <span class="errors-toggle">▾</span>
      </div>
      <div class="errors-body" id="errorsBody"></div>
    </div>

    <div class="results-actions">
      <button class="btn btn-outline" onclick="goTo('setup')">Пройти ещё раз</button>
      <button class="btn btn-ghost" onclick="goTo('landing')">← На главную</button>
    </div>
  </div>
</div>

<!-- ══════════════ ABOUT PAGE ══════════════ -->
<div id="aboutPage">
  <div class="bg-orb bg-orb1"></div>
  <div class="bg-orb bg-orb2"></div>
  <div class="about-content">
    <button class="about-back" onclick="hideAbout()">← Назад</button>
    <h1 class="about-h1">Команда<br><span style="background:linear-gradient(135deg,#22c55e,#86efac);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;">Synapse</span></h1>
    <p class="about-p">Мы — студенты ВСГУТУ (Улан-Удэ, Бурятия), специальность «Информационные системы и программирование».</p>
    <p class="about-p">Этот тренажёр IT-лексики создан командой Synapse для практики английского языка в сфере информационных технологий.</p>
    <div class="team-grid">
      <div class="team-card">
        <div class="team-av">🧠</div>
        <div class="team-name">Ярослав</div>
        <div class="team-role">Разработчик</div>
      </div>
      <div class="team-card">
        <div class="team-av">👨‍💻</div>
        <div class="team-name">Владислав</div>
        <div class="team-role">Разработчик, Редактор Текста</div>
      </div>
      <div class="team-card">
        <div class="team-av">🎨</div>
        <div class="team-name">Арина</div>
        <div class="team-role">Дизайнер</div>
      </div>
    </div>
  </div>
</div>

<!-- ══════════════ ADMIN PAGE ══════════════ -->
<div id="adminPage">
  <div class="bg-orb bg-orb1"></div>
  <div class="bg-orb bg-orb2"></div>
  <div class="admin-wrap">
    <div class="admin-header-row">
      <div>
        <div style="display:flex;align-items:center;gap:12px;margin-bottom:4px;">
          <h1 class="admin-title">Админ-<span>Панель</span></h1>
          <span class="admin-badge">ADMIN</span>
        </div>
        <p style="color:var(--text2);font-size:13px;">Редактирование словаря. Изменения сохраняются в localStorage.</p>
      </div>
      <div style="display:flex;gap:10px;flex-wrap:wrap;">
        <button class="btn-add" onclick="addAdminRow()">+ Добавить слово</button>
        <button class="btn btn-ghost" style="font-size:13px;padding:10px 20px;" onclick="closeAdmin()">← Выйти</button>
      </div>
    </div>

    <div class="admin-table-wrap">
      <table class="admin-table">
        <thead>
          <tr>
            <th class="tbl-idx">#</th>
            <th>Слово (English)</th>
            <th>Перевод (Русский)</th>
            <th class="tbl-del"></th>
          </tr>
        </thead>
        <tbody id="adminTableBody"></tbody>
      </table>
    </div>

    <button class="btn-save" id="saveBtn" onclick="saveVocab()">💾 Сохранить</button>
    <p class="save-hint" id="saveHint"></p>
  </div>
</div>

<!-- ADMIN SCROLL BUTTONS -->
<div class="admin-scroll-btns" id="adminScrollBtns">
  <div class="scroll-fab" onclick="adminPage.scrollTo({top:0,behavior:'smooth'})" title="Наверх">↑</div>
  <div class="scroll-fab" onclick="adminPage.scrollTo({top:adminPage.scrollHeight,behavior:'smooth'})" title="Вниз">↓</div>
</div>

<!-- SAVE TOAST -->
<div class="save-toast" id="saveToast">✓ Словарь сохранён!</div>

<script>
// ════════════════════════════════════
//  DEFAULT VOCABULARY (290 слов)
// ════════════════════════════════════
const DEFAULT_VOCAB = [
  {word:"Access",translation:"Доступ"},
  {word:"Accessory",translation:"Дополнительное Устройство"},
  {word:"According To",translation:"Согласно"},
  {word:"Adapter",translation:"Адаптер"},
  {word:"Adjust",translation:"Настраивать"},
  {word:"Affect",translation:"Влиять"},
  {word:"Algorithm",translation:"Алгоритм"},
  {word:"Align",translation:"Выравнивать"},
  {word:"Animation",translation:"Анимация"},
  {word:"Antenna",translation:"Антенна"},
  {word:"Appear",translation:"Появляться"},
  {word:"Application",translation:"Приложение"},
  {word:"ASCII",translation:"Таблица Символов"},
  {word:"Attachment",translation:"Вложение"},
  {word:"Audio",translation:"Аудио"},
  {word:"Automatically",translation:"Автоматически"},
  {word:"Background",translation:"Фон"},
  {word:"Back-Up",translation:"Резервная Копия"},
  {word:"Back Sth Up",translation:"Создавать Резервную Копию"},
  {word:"Band Mode",translation:"Частотный Режим"},
  {word:"Bandwidth",translation:"Пропускная Способность"},
  {word:"Bill",translation:"Счёт"},
  {word:"Binary",translation:"Двоичный"},
  {word:"Blink",translation:"Мигать"},
  {word:"Broadband",translation:"Широкополосный Интернет"},
  {word:"Browse",translation:"Просматривать"},
  {word:"Browser",translation:"Браузер"},
  {word:"Button",translation:"Кнопка"},
  {word:"Carbon Copy",translation:"Копия Письма"},
  {word:"Categorize",translation:"Классифицировать"},
  {word:"CD-Rewriter",translation:"Устройство Записи CD"},
  {word:"CD-ROM",translation:"Компакт-Диск Только Для Чтения"},
  {word:"Character",translation:"Символ"},
  {word:"Chat Room",translation:"Онлайн-Чат"},
  {word:"Click",translation:"Щёлкать"},
  {word:"Client",translation:"Клиент"},
  {word:"Clipboard",translation:"Буфер Обмена"},
  {word:"Code",translation:"Код"},
  {word:"Coding System",translation:"Система Кодирования"},
  {word:"Combine",translation:"Объединять"},
  {word:"Command",translation:"Команда"},
  {word:"Commerce",translation:"Электронная Торговля"},
  {word:"Communication",translation:"Общение"},
  {word:"Compatible",translation:"Совместимый"},
  {word:"Component",translation:"Компонент"},
  {word:"Compose",translation:"Составлять"},
  {word:"Computer Programmer",translation:"Программист"},
  {word:"Confident",translation:"Уверенный"},
  {word:"Confusing",translation:"Запутанный"},
  {word:"Connection",translation:"Соединение"},
  {word:"Consistent",translation:"Последовательный"},
  {word:"Consumer",translation:"Пользователь"},
  {word:"Convenient",translation:"Удобный"},
  {word:"Copyright Law",translation:"Закон Об Авторском Праве"},
  {word:"Counter",translation:"Счётчик"},
  {word:"CPU",translation:"Центральный Процессор"},
  {word:"Crash",translation:"Сбой Системы"},
  {word:"Cross-Platform",translation:"Кроссплатформенный"},
  {word:"Cursor",translation:"Курсор"},
  {word:"Custom",translation:"Индивидуальный"},
  {word:"Cut",translation:"Вырезать"},
  {word:"Cyberspace",translation:"Киберпространство"},
  {word:"Data",translation:"Данные"},
  {word:"Database",translation:"База Данных"},
  {word:"Database Administrator",translation:"Администратор Базы Данных"},
  {word:"Deal With Sth",translation:"Обрабатывать"},
  {word:"Decrease",translation:"Уменьшать"},
  {word:"Default",translation:"По Умолчанию"},
  {word:"Delete",translation:"Удалять"},
  {word:"Design",translation:"Проектирование"},
  {word:"Desktop",translation:"Рабочий Стол"},
  {word:"Desktop Publishing",translation:"Настольная Верстка"},
  {word:"Detachable",translation:"Съёмный"},
  {word:"Develop",translation:"Разрабатывать"},
  {word:"Device",translation:"Устройство"},
  {word:"Dialog Box",translation:"Диалоговое Окно"},
  {word:"Digital",translation:"Цифровой"},
  {word:"Dimension",translation:"Размерность"},
  {word:"Directory",translation:"Каталог"},
  {word:"Display",translation:"Дисплей"},
  {word:"Display Screen",translation:"Экран"},
  {word:"Distance Learning",translation:"Дистанционное Обучение"},
  {word:"DNS",translation:"Система Доменных Имён"},
  {word:"Domain Name",translation:"Доменное Имя"},
  {word:"Double-Click",translation:"Двойной Щелчок"},
  {word:"Download",translation:"Скачать"},
  {word:"Draft",translation:"Черновик"},
  {word:"Drive",translation:"Накопитель"},
  {word:"Drop-Down Menu",translation:"Выпадающее Меню"},
  {word:"Dual",translation:"Двойной"},
  {word:"E-Commerce",translation:"Электронная Торговля"},
  {word:"Edit",translation:"Редактировать"},
  {word:"Else",translation:"Иначе"},
  {word:"E-Mail",translation:"Электронная Почта"},
  {word:"Emoticon",translation:"Смайлик"},
  {word:"Empty",translation:"Пустой"},
  {word:"EPS",translation:"Графический Формат"},
  {word:"Erase",translation:"Стирать"},
  {word:"Exclude",translation:"Исключать"},
  {word:"Existing",translation:"Существующий"},
  {word:"Export",translation:"Экспортировать"},
  {word:"E-Zine",translation:"Онлайн-Журнал"},
  {word:"Faceplate",translation:"Передняя Панель"},
  {word:"FAQ",translation:"Часто Задаваемые Вопросы"},
  {word:"Feature",translation:"Функция"},
  {word:"Fee",translation:"Плата"},
  {word:"Field",translation:"Поле"},
  {word:"File",translation:"Файл"},
  {word:"File Extension",translation:"Расширение Файла"},
  {word:"Fit",translation:"Подходить"},
  {word:"Flash",translation:"Технология Анимации"},
  {word:"Flip Cover",translation:"Откидная Крышка"},
  {word:"Floppy Disk",translation:"Дискета"},
  {word:"Folder",translation:"Папка"},
  {word:"Font",translation:"Шрифт"},
  {word:"Format",translation:"Формат"},
  {word:"Frame",translation:"Кадр"},
  {word:"Freeware",translation:"Бесплатное ПО"},
  {word:"FTP",translation:"Протокол Передачи Файлов"},
  {word:"Function",translation:"Функция"},
  {word:"Generate",translation:"Генерировать"},
  {word:"GIF",translation:"Графический Формат"},
  {word:"Gigabyte",translation:"Гигабайт"},
  {word:"Gigahertz",translation:"Гигагерц"},
  {word:"Graphics",translation:"Графика"},
  {word:"Guarantee",translation:"Гарантия"},
  {word:"Hard Disk",translation:"Жёсткий Диск"},
  {word:"Hardware",translation:"Аппаратное Обеспечение"},
  {word:"High Level Language",translation:"Язык Высокого Уровня"},
  {word:"Highlight",translation:"Выделять"},
  {word:"Home Page",translation:"Главная Страница"},
  {word:"HTML",translation:"Язык Разметки"},
  {word:"HTTP",translation:"Протокол Передачи Данных"},
  {word:"Hyperlink",translation:"Гиперссылка"},
  {word:"Icon",translation:"Значок"},
  {word:"Illegal",translation:"Незаконный"},
  {word:"Image",translation:"Изображение"},
  {word:"Import",translation:"Импортировать"},
  {word:"Income",translation:"Доход"},
  {word:"Incoming",translation:"Входящие"},
  {word:"Increase",translation:"Увеличивать"},
  {word:"Information Technology",translation:"Информационные Технологии"},
  {word:"Input",translation:"Ввод"},
  {word:"Insert",translation:"Вставлять"},
  {word:"Instant",translation:"Мгновенный"},
  {word:"Instead Of",translation:"Вместо"},
  {word:"Integrate",translation:"Интегрировать"},
  {word:"Interact",translation:"Взаимодействовать"},
  {word:"Internet",translation:"Интернет"},
  {word:"Internet Protocol Address",translation:"IP-Адрес"},
  {word:"Invasion",translation:"Вторжение"},
  {word:"ISDN",translation:"Цифровая Сеть"},
  {word:"Java Script",translation:"Язык Программирования"},
  {word:"JPEG",translation:"Графический Формат"},
  {word:"Junk Mail",translation:"Спам"},
  {word:"Keyboard",translation:"Клавиатура"},
  {word:"Keypad",translation:"Клавишная Панель"},
  {word:"Keyword",translation:"Ключевое Слово"},
  {word:"LAN",translation:"Локальная Сеть"},
  {word:"Link",translation:"Ссылка"},
  {word:"Locate",translation:"Находить"},
  {word:"Location",translation:"Местоположение"},
  {word:"Logical Operator",translation:"Логический Оператор"},
  {word:"Machine Language",translation:"Машинный Язык"},
  {word:"Mail Server",translation:"Почтовый Сервер"},
  {word:"Main",translation:"Основной"},
  {word:"Manual",translation:"Ручной"},
  {word:"Maximize",translation:"Развернуть"},
  {word:"Means",translation:"Средство"},
  {word:"Megabyte",translation:"Мегабайт"},
  {word:"Megahertz",translation:"Мегагерц"},
  {word:"Menu Bar",translation:"Строка Меню"},
  {word:"Minimize",translation:"Свернуть"},
  {word:"Mobile Phone",translation:"Мобильный Телефон"},
  {word:"Modem",translation:"Модем"},
  {word:"Monitor",translation:"Монитор"},
  {word:"Mouse",translation:"Мышь"},
  {word:"Multilingual",translation:"Многоязычный"},
  {word:"Multimedia",translation:"Мультимедиа"},
  {word:"Multiple",translation:"Множественный"},
  {word:"Narrow",translation:"Сужать"},
  {word:"Navigate",translation:"Перемещаться"},
  {word:"Navigation",translation:"Навигация"},
  {word:"Navigation Bar",translation:"Панель Навигации"},
  {word:"Network",translation:"Сеть"},
  {word:"Notebook",translation:"Ноутбук"},
  {word:"Offline",translation:"Офлайн"},
  {word:"Online",translation:"Онлайн"},
  {word:"Online Community",translation:"Онлайн-Сообщество"},
  {word:"Operate",translation:"Управлять"},
  {word:"Optional",translation:"Необязательный"},
  {word:"Organize",translation:"Организовывать"},
  {word:"Original",translation:"Оригинальный"},
  {word:"Originate",translation:"Возникать"},
  {word:"Outgoing",translation:"Исходящий"},
  {word:"Output",translation:"Вывод"},
  {word:"Paint",translation:"Рисовать"},
  {word:"Password",translation:"Пароль"},
  {word:"Paste",translation:"Вставлять"},
  {word:"PC",translation:"Персональный компьютер"},
  {word:"Peer-To-Peer",translation:"Одноранговый"},
  {word:"Performance",translation:"Производительность"},
  {word:"Peripheral",translation:"Периферийное Устройство"},
  {word:"Personal Information",translation:"Личная Информация"},
  {word:"Personalize",translation:"Персонализировать"},
  {word:"Pict",translation:"Пиктограмма"},
  {word:"Plug-In",translation:"Подключаемый Модуль"},
  {word:"Pointer",translation:"Указатель"},
  {word:"Pop-Up Ad",translation:"Всплывающая Реклама"},
  {word:"Printer",translation:"Принтер"},
  {word:"Privacy",translation:"Конфиденциальность"},
  {word:"Privacy Policy",translation:"Политика Конфиденциальности"},
  {word:"Procedure",translation:"Процедура"},
  {word:"Process",translation:"Процесс"},
  {word:"Program",translation:"Программа"},
  {word:"Protocol",translation:"Протокол"},
  {word:"RAM",translation:"ОЗУ"},
  {word:"Random",translation:"Случайный"},
  {word:"Real Time",translation:"Реальное Время"},
  {word:"Recipient",translation:"Получатель"},
  {word:"Recycle Bin",translation:"Корзина"},
  {word:"Register",translation:"Регистрироваться"},
  {word:"Related",translation:"Связанный"},
  {word:"Relevant",translation:"Актуальный"},
  {word:"Reliable",translation:"Надёжный"},
  {word:"Removable Disk",translation:"Съёмный Диск"},
  {word:"Restore",translation:"Восстанавливать"},
  {word:"Retailer",translation:"Розничный Продавец"},
  {word:"Retrieve",translation:"Извлекать"},
  {word:"Ring Tone",translation:"Рингтон"},
  {word:"Rotate",translation:"Вращать"},
  {word:"Run",translation:"Запускать"},
  {word:"Save",translation:"Сохранять"},
  {word:"Save As Type",translation:"Сохранить Как Тип Файла"},
  {word:"Save In",translation:"Сохранить В"},
  {word:"Scanner",translation:"Сканер"},
  {word:"Screen Saver",translation:"Экранная Заставка"},
  {word:"Scroll Bar",translation:"Полоса Прокрутки"},
  {word:"Scroll Key",translation:"Клавиша Прокрутки"},
  {word:"Search",translation:"Поиск"},
  {word:"Search Engine",translation:"Поисковая Система"},
  {word:"Secure",translation:"Безопасный"},
  {word:"Security",translation:"Безопасность"},
  {word:"Server",translation:"Сервер"},
  {word:"Setting",translation:"Настройка"},
  {word:"Share",translation:"Делиться"},
  {word:"Shareware",translation:"Условно-Бесплатное ПО"},
  {word:"Shortcut",translation:"Ярлык"},
  {word:"Simulation",translation:"Симуляция"},
  {word:"Small Talk",translation:"Светская Беседа"},
  {word:"SMS",translation:"Служба Коротких Сообщений"},
  {word:"Software",translation:"Программное Обеспечение"},
  {word:"Source",translation:"Источник"},
  {word:"Spam",translation:"Спам"},
  {word:"Special Effects",translation:"Спецэффекты"},
  {word:"Specific",translation:"Конкретный"},
  {word:"Specification",translation:"Спецификация"},
  {word:"Stand For Sth",translation:"Означать"},
  {word:"Stand-Alone",translation:"Автономный"},
  {word:"Standard",translation:"Стандартный"},
  {word:"Store",translation:"Хранить"},
  {word:"Structure",translation:"Структурировать"},
  {word:"Stylish",translation:"Стильный"},
  {word:"Subject",translation:"Тема"},
  {word:"Support",translation:"Поддержка"},
  {word:"Surf",translation:"Серфить"},
  {word:"Swap",translation:"Обменивать"},
  {word:"System",translation:"Система"},
  {word:"Techno-Nerd",translation:"Айтишник"},
  {word:"Template",translation:"Шаблон"},
  {word:"Text Box",translation:"Текстовое Поле"},
  {word:"Text Editor",translation:"Текстовый Редактор"},
  {word:"Text Message",translation:"Текстовое Сообщение"},
  {word:"Text Wrap",translation:"Перенос Текста"},
  {word:"Thesaurus",translation:"Тезаурус"},
  {word:"3D",translation:"Трёхмерный"},
  {word:"TIFF",translation:"Графический Формат Изображения"},
  {word:"Tool",translation:"Инструмент"},
  {word:"Toolbar",translation:"Панель Инструментов"},
  {word:"Tower",translation:"Системный Блок"},
  {word:"Transaction",translation:"Транзакция"},
  {word:"Transfer",translation:"Передавать"},
  {word:"Translate",translation:"Переводить"},
  {word:"Transmission",translation:"Передача"},
  {word:"Trial Membership",translation:"Пробная Подписка"},
  {word:"Underscore",translation:"Подчёркивание"},
  {word:"Unsolicited",translation:"Нежелательный"},
  {word:"Untitled",translation:"Без Названия"},
  {word:"Upload",translation:"Загружать"},
  {word:"URL",translation:"Адрес Ресурса"},
  {word:"Utility",translation:"Служебная Программа"},
  {word:"Video Conferencing",translation:"Видеоконференция"},
  {word:"View",translation:"Просматривать"},
  {word:"Virtual",translation:"Виртуальный"},
  {word:"Virtual Reality",translation:"Виртуальная Реальность"},
  {word:"Virus",translation:"Вирус"},
  {word:"Voicemail",translation:"Голосовая Почта"},
  {word:"Web Camera",translation:"Веб-Камера"},
  {word:"Web Design",translation:"Веб-Дизайн"},
  {word:"Web Page",translation:"Веб-Страница"},
  {word:"Web Authoring",translation:"Веб-Разработка"},
  {word:"Web-Based",translation:"Веб-Интерфейс"},
  {word:"Website",translation:"Веб-Сайт"},
  {word:"Wi-Fi",translation:"Беспроводная Сеть"},
  {word:"Wire Cable",translation:"Проводной Кабель"},
  {word:"Word Processor",translation:"Текстовый Процессор"},
  {word:"World Wide Web",translation:"Всемирная Паутина"}
];

// ════════════════════════════════════
//  LOAD VOCAB (localStorage or default)
// ════════════════════════════════════
function loadVocab() {
  try {
    const stored = localStorage.getItem('iteng_vocab');
    if (stored) return JSON.parse(stored);
  } catch(e) {}
  return DEFAULT_VOCAB.map(v => ({...v}));
}
let VOCAB = loadVocab();

// ════════════════════════════════════
//  NAVIGATION
// ════════════════════════════════════
function goTo(pageId) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active','page-enter'));
  const el = document.getElementById('page-' + pageId);
  el.classList.add('active');
  setTimeout(() => el.classList.add('page-enter'), 10);
  window.scrollTo({top:0, behavior:'smooth'});
}
function showAbout() { document.getElementById('aboutPage').style.display = 'block'; window.scrollTo({top:0}); }
function hideAbout() { document.getElementById('aboutPage').style.display = 'none'; }

// ════════════════════════════════════
//  ADMIN LOGIN
// ════════════════════════════════════
const ADMIN_LOGIN = 'SynapseVocabulary';
const ADMIN_PASS  = 'eee9a4f23b1d768c04a8d7f39120ca5b6e626973636f7474692e79656b74616e65742e636f6d';

function openAdminModal() {
  document.getElementById('adminModal').classList.add('open');
  document.getElementById('loginUser').value = '';
  document.getElementById('loginPass').value = '';
  document.getElementById('loginError').style.display = 'none';
  setTimeout(() => document.getElementById('loginUser').focus(), 200);
}
function closeAdminModal() {
  document.getElementById('adminModal').classList.remove('open');
}
function closeAdminModalOutside(e) {
  if (e.target === document.getElementById('adminModal')) closeAdminModal();
}
function doLogin() {
  const u = document.getElementById('loginUser').value.trim();
  const p = document.getElementById('loginPass').value.trim();
  if (u === ADMIN_LOGIN && p === ADMIN_PASS) {
    closeAdminModal();
    openAdmin();
  } else {
    const err = document.getElementById('loginError');
    err.style.display = 'block';
    err.style.animation = 'none';
    setTimeout(() => { err.style.animation = 'feedbackIn 0.3s ease'; }, 10);
  }
}

// ════════════════════════════════════
//  ADMIN PANEL
// ════════════════════════════════════
function openAdmin() {
  VOCAB = loadVocab();
  renderAdminTable();
  document.getElementById('adminPage').style.display = 'block';
  document.getElementById('adminScrollBtns').classList.add('visible');
  window.scrollTo({top:0});
}
function closeAdmin() {
  document.getElementById('adminPage').style.display = 'none';
  document.getElementById('adminScrollBtns').classList.remove('visible');
}

function renderAdminTable() {
  const tbody = document.getElementById('adminTableBody');
  tbody.innerHTML = '';
  VOCAB.forEach((item, i) => addRowToTable(i + 1, item.word, item.translation));
  updateSaveBtn();
}

function addRowToTable(idx, wordVal, transVal) {
  const tbody = document.getElementById('adminTableBody');
  const tr = document.createElement('tr');
  tr.innerHTML = `
    <td class="tbl-idx">${tbody.rows.length + 1}</td>
    <td><input class="tbl-input" type="text" value="${escapeHtml(wordVal)}" placeholder="Слово..." oninput="updateSaveBtn()"></td>
    <td><input class="tbl-input" type="text" value="${escapeHtml(transVal)}" placeholder="Перевод..." oninput="updateSaveBtn()"></td>
    <td class="tbl-del"><button class="del-btn" onclick="deleteRow(this)" title="Удалить">−</button></td>
  `;
  tbody.appendChild(tr);
}

function escapeHtml(str) {
  return String(str).replace(/&/g,'&amp;').replace(/"/g,'&quot;').replace(/</g,'&lt;').replace(/>/g,'&gt;');
}

function addAdminRow() {
  addRowToTable(0, '', '');
  reindexRows();
  updateSaveBtn();
  // Scroll to new row
  const adminPage = document.getElementById('adminPage');
  setTimeout(() => adminPage.scrollTo({top: adminPage.scrollHeight, behavior:'smooth'}), 50);
}

function deleteRow(btn) {
  btn.closest('tr').remove();
  reindexRows();
  updateSaveBtn();
}

function reindexRows() {
  const rows = document.querySelectorAll('#adminTableBody tr');
  rows.forEach((tr, i) => {
    const idx = tr.querySelector('.tbl-idx');
    if (idx) idx.textContent = i + 1;
  });
}

function updateSaveBtn() {
  const rows = document.querySelectorAll('#adminTableBody tr');
  let hasEmpty = false;
  rows.forEach(tr => {
    const inputs = tr.querySelectorAll('.tbl-input');
    inputs.forEach(inp => {
      if (inp.value.trim() === '') {
        hasEmpty = true;
        inp.classList.add('empty-field');
      } else {
        inp.classList.remove('empty-field');
      }
    });
  });
  const btn = document.getElementById('saveBtn');
  const hint = document.getElementById('saveHint');
  if (hasEmpty) {
    btn.disabled = true;
    hint.textContent = 'Заполни все поля, чтобы сохранить';
    hint.style.color = 'var(--red)';
  } else {
    btn.disabled = false;
    hint.textContent = '';
  }
}

function saveVocab() {
  const rows = document.querySelectorAll('#adminTableBody tr');
  const newVocab = [];
  rows.forEach(tr => {
    const inputs = tr.querySelectorAll('.tbl-input');
    const w = inputs[0].value.trim();
    const t = inputs[1].value.trim();
    if (w && t) newVocab.push({word: w, translation: t});
  });
  VOCAB = newVocab;
  try {
    localStorage.setItem('iteng_vocab', JSON.stringify(VOCAB));
  } catch(e) {}
  showToast();
}

function showToast() {
  const toast = document.getElementById('saveToast');
  toast.classList.add('show');
  setTimeout(() => toast.classList.remove('show'), 2800);
}

// Scroll buttons reference
const adminPage = document.getElementById('adminPage');

// ════════════════════════════════════
//  TEST: SETUP
// ════════════════════════════════════
let totalQ = 0, questions = [], currentIdx = 0, correct = 0, errors = [];
let answered = false;

function selectCount(n, el) {
  document.querySelectorAll('.count-btn').forEach(b => b.classList.remove('selected'));
  el.classList.add('selected');
  totalQ = n;
  const btn = document.getElementById('startBtn');
  btn.disabled = false;
  btn.style.opacity = '1';
  btn.style.cursor = 'pointer';
}

// ════════════════════════════════════
//  TEST: BUILD QUESTIONS
// ════════════════════════════════════
function buildQuestions(n) {
  const vocab = loadVocab(); // always fresh
  const pool = [...vocab].sort(() => Math.random() - 0.5);
  let arr = pool.slice(0, Math.min(n, vocab.length));
  while (arr.length < n) {
    const extra = [...vocab].sort(() => Math.random() - 0.5);
    arr = arr.concat(extra.slice(0, n - arr.length));
  }
  arr = arr.slice(0, n).sort(() => Math.random() - 0.5);
  return arr.map(item => {
    const wrong = getWrong(item.translation, vocab, 2);
    const opts = shuffle([item.translation, ...wrong]);
    return {word: item.word, correct: item.translation, options: opts};
  });
}

function getWrong(correctT, vocab, count) {
  const pool = vocab.filter(v => v.translation !== correctT);
  return pool.sort(() => Math.random() - 0.5).slice(0, count).map(v => v.translation);
}

function shuffle(arr) { return arr.sort(() => Math.random() - 0.5); }

// ════════════════════════════════════
//  TEST: START
// ════════════════════════════════════
function startTest() {
  if (!totalQ) return;
  questions = buildQuestions(totalQ);
  currentIdx = 0; correct = 0; errors = [];
  goTo('test');
  renderQuestion();
}

// ════════════════════════════════════
//  TEST: RENDER QUESTION
// ════════════════════════════════════
function renderQuestion() {
  answered = false;
  const q = questions[currentIdx];
  const pct = (currentIdx / questions.length) * 100;
  document.getElementById('progressLabel').textContent = `${currentIdx + 1} / ${questions.length}`;
  document.getElementById('scoreLabel').textContent = `✓ ${correct}`;
  document.getElementById('progressFill').style.width = pct + '%';
  document.getElementById('qWord').textContent = q.word;
  document.getElementById('feedbackBox').innerHTML = '';
  document.getElementById('nextRow').style.display = 'none';

  const letters = ['A','B','C'];
  const grid = document.getElementById('optionsGrid');
  grid.innerHTML = '';
  q.options.forEach((opt, i) => {
    const btn = document.createElement('button');
    btn.className = 'opt-btn';
    btn.innerHTML = `<span class="opt-letter">${letters[i]}</span><span>${opt}</span>`;
    btn.onclick = () => answerQuestion(opt, btn);
    grid.appendChild(btn);
  });
}

// ════════════════════════════════════
//  TEST: ANSWER
// ════════════════════════════════════
function answerQuestion(chosen, btn) {
  if (answered) return;
  answered = true;
  const q = questions[currentIdx];
  const isRight = chosen === q.correct;
  document.querySelectorAll('.opt-btn').forEach(b => {
    b.disabled = true;
    const optText = b.querySelector('span:last-child').textContent;
    if (optText === q.correct) b.classList.add('correct');
    else if (b === btn && !isRight) b.classList.add('wrong');
    else b.classList.add('dimmed');
  });
  const fb = document.getElementById('feedbackBox');
  if (isRight) {
    correct++;
    fb.innerHTML = `<div class="feedback-box ok">✓ Правильно! <strong>${q.word}</strong> — это «${q.correct}»</div>`;
  } else {
    errors.push({word: q.word, correct: q.correct, chosen});
    fb.innerHTML = `<div class="feedback-box fail">✗ Ты выбрал «${chosen}», но правильный перевод <strong>${q.word}</strong> — это «${q.correct}»</div>`;
  }
  document.getElementById('nextRow').style.display = 'flex';
  if (currentIdx + 1 >= questions.length) {
    const nb = document.querySelector('#nextRow .btn');
    nb.textContent = 'Смотреть результаты →';
    nb.onclick = showResults;
  }
}

// ════════════════════════════════════
//  TEST: NEXT QUESTION
// ════════════════════════════════════
function nextQuestion() {
  currentIdx++;
  if (currentIdx >= questions.length) showResults();
  else renderQuestion();
}

// ════════════════════════════════════
//  TEST: RESULTS
// ════════════════════════════════════
function showResults() {
  const total = questions.length;
  const pct = Math.round((correct / total) * 100);
  const circumference = 2 * Math.PI * 68;
  const offset = circumference - (pct / 100) * circumference;
  const ring = document.getElementById('ringFill');

  let color, title, tip;
  if (pct <= 30) {
    color = '#ef4444'; title = 'Нужно больше практики';
    tip = 'Не сдавайся — повторяй слова каждый день, и результат улучшится.';
  } else if (pct <= 50) {
    color = '#f97316'; title = 'Неплохое начало!';
    tip = 'Неплохо, но есть куда расти. Попробуй пройти тест ещё раз.';
  } else if (pct <= 80) {
    color = '#3b82f6'; title = 'Хороший результат!';
    tip = 'Ты хорошо знаешь IT-лексику. Ещё немного — и станешь экспертом.';
  } else {
    color = '#22c55e'; title = 'Отлично! Ты почти эксперт 🚀';
    tip = 'Превосходно! Твои знания IT-английского на высоком уровне.';
  }

  ring.style.stroke = color;
  const sp = document.getElementById('scorePct');
  sp.style.color = color;
  sp.textContent = pct + '%';
  pct >= 90 ? sp.classList.add('shimmer-text') : sp.classList.remove('shimmer-text');

  document.getElementById('resultTitle').textContent = title;
  document.getElementById('resultTip').textContent = tip;
  document.getElementById('statCorrect').textContent = correct;
  document.getElementById('statWrong').textContent = errors.length;
  document.getElementById('statPct').textContent = pct + '%';
  document.getElementById('errorsBadge').textContent = errors.length;

  const body = document.getElementById('errorsBody');
  body.innerHTML = errors.length === 0
    ? '<div style="padding:20px;text-align:center;color:var(--text3);font-size:13px;">Ошибок нет — идеальный результат! 🎉</div>'
    : errors.map(e => `
        <div class="error-item">
          <div class="error-word">${e.word}</div>
          <div class="error-meta">
            <div class="error-correct">✓ Правильно: ${e.correct}</div>
            <div class="error-wrong">✗ Ты ответил: ${e.chosen}</div>
          </div>
        </div>`).join('');

  // Reset errors section
  document.getElementById('errorsSection').classList.add('collapsed');

  goTo('results');
  setTimeout(() => { ring.style.strokeDashoffset = offset; }, 300);
}

function toggleErrors() {
  document.getElementById('errorsSection').classList.toggle('collapsed');
}

// ════════════════════════════════════
//  PARTICLE CANVAS
// ════════════════════════════════════
(function() {
  const canvas = document.getElementById('bgCanvas');
  const ctx = canvas.getContext('2d');
  let W, H, particles = [];

  function resize() {
    W = canvas.width = window.innerWidth;
    H = canvas.height = window.innerHeight;
  }

  function Particle() {
    this.x = Math.random() * W;
    this.y = Math.random() * H;
    this.r = Math.random() * 1.5 + 0.3;
    this.vx = (Math.random() - 0.5) * 0.3;
    this.vy = (Math.random() - 0.5) * 0.3;
    this.alpha = Math.random() * 0.5 + 0.1;
    this.color = Math.random() > 0.6 ? '34,197,94' : '59,130,246';
  }

  function init() {
    resize();
    particles = Array.from({length: 90}, () => new Particle());
  }

  function draw() {
    ctx.clearRect(0, 0, W, H);
    particles.forEach(p => {
      p.x += p.vx; p.y += p.vy;
      if (p.x < 0) p.x = W; if (p.x > W) p.x = 0;
      if (p.y < 0) p.y = H; if (p.y > H) p.y = 0;
      ctx.beginPath();
      ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
      ctx.fillStyle = `rgba(${p.color},${p.alpha})`;
      ctx.fill();
    });
    for (let i = 0; i < particles.length; i++) {
      for (let j = i + 1; j < particles.length; j++) {
        const dx = particles[i].x - particles[j].x;
        const dy = particles[i].y - particles[j].y;
        const dist = Math.sqrt(dx * dx + dy * dy);
        if (dist < 110) {
          ctx.beginPath();
          ctx.moveTo(particles[i].x, particles[i].y);
          ctx.lineTo(particles[j].x, particles[j].y);
          ctx.strokeStyle = `rgba(34,197,94,${0.04 * (1 - dist / 110)})`;
          ctx.lineWidth = 0.5;
          ctx.stroke();
        }
      }
    }
    requestAnimationFrame(draw);
  }

  window.addEventListener('resize', resize);
  init();
  draw();
})();
</script>
</body>
</html>
