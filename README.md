<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cicero&amp;Co</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800;900&display=swap" rel="stylesheet">
<style>
:root{
  --ink:#2c6e73;
  --deep:#087d8b;
  --teal:#cceee5;
  --mint:#dcf8ec;
  --yellow:#fff2bd;
  --shadow:0 10px 26px rgba(34,124,135,.12);
}
*{box-sizing:border-box}
html,body{
  width:100%;
  min-height:100%;
  margin:0;
  padding:0;
  font-family:'Nunito','Trebuchet MS',Arial,sans-serif;
  color:var(--ink);
  background:repeating-linear-gradient(90deg,#d8f5f0 0 32px,#c7ece6 32px 64px) fixed;
  overflow-x:hidden;
  scroll-behavior:smooth;
}
button,input,textarea,select{font:inherit;max-width:100%}
img,video,canvas,iframe{max-width:100%}
button{touch-action:manipulation}

/* Full-screen / Full-width layout */
.app{
  width:100%;
  max-width:100%;
  min-height:100vh;
  margin:0;
  display:grid;
  grid-template-columns:236px minmax(0,1fr);
}

/* Sidebar */
aside.cicero-sidebar{
  position:sticky;
  top:0;
  height:100vh;
  overflow-y:auto;
  background:rgba(217,255,240,.92);
  backdrop-filter:blur(8px);
  border-right:1px solid #b5e5dc;
  padding:16px 12px 24px;
  display:flex;
  flex-direction:column;
  gap:8px;
  z-index:80;
}
.mobile-menu-head{
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:8px;
  padding:4px 6px 10px;
}
.mobile-menu-toggle{
  display:none;
  align-items:center;
  justify-content:center;
  width:42px;
  height:42px;
  border:1px solid #bce8d6;
  border-radius:12px;
  background:#ffffff;
  color:var(--deep);
  font-size:22px;
  font-weight:900;
  cursor:pointer;
}
.logo{
  font-family:Georgia,serif;
  font-style:italic;
  font-weight:900;
  font-size:22px;
  color:var(--deep);
  text-decoration:underline;
  cursor:pointer;
  user-select:none;
}
.nav-group{
  background:rgba(255,255,255,.55);
  border:1px solid #d4efe9;
  border-radius:16px;
  padding:6px;
}
.nav-group-title{
  display:flex;
  align-items:center;
  justify-content:space-between;
  padding:8px 10px;
  font-size:12px;
  font-weight:900;
  color:#48898e;
  cursor:pointer;
  user-select:none;
  border-radius:11px;
}
.nav-group-title:hover{background:rgba(255,255,255,.7)}
.nav-group-title::after{content:"⌄";font-size:15px;transition:transform .18s ease}
.nav-group.is-collapsed .nav-group-title::after{transform:rotate(-90deg)}
.nav-group.is-collapsed .sidebtn{display:none}
.sidebtn{
  width:100%;
  border:0;
  border-radius:12px;
  background:transparent;
  color:var(--ink);
  font-weight:800;
  font-size:13px;
  text-align:left;
  padding:9px 11px;
  margin:2px 0;
  cursor:pointer;
  transition:background .15s,color .15s,transform .15s;
}
.sidebtn:hover,.sidebtn.active{
  background:#ffffff;
  color:var(--deep);
  box-shadow:0 4px 12px rgba(8,125,139,.08);
}

/* Main full-width workspace */
main{
  min-width:0;
  width:100%;
  padding:16px clamp(16px,2.5vw,36px) 44px;
}
.topbar{
  position:sticky;
  top:10px;
  z-index:50;
  width:100%;
  min-height:58px;
  border-radius:24px;
  background:rgba(245,255,255,.92);
  backdrop-filter:blur(8px);
  border:1px solid #ffffff;
  box-shadow:var(--shadow);
  padding:10px 18px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:12px;
  flex-wrap:wrap;
}
.topbar-brand{
  font-weight:900;
  font-size:15px;
  color:var(--deep);
}
.topbar-brand span{font-weight:600;color:#538c91}
.topbar-actions{
  display:flex;
  align-items:center;
  gap:8px;
  flex-wrap:wrap;
}
.nav{
  border:0;
  border-radius:999px;
  background:#e5f7f3;
  color:var(--deep);
  font-weight:800;
  font-size:13px;
  padding:8px 14px;
  cursor:pointer;
  transition:background .15s,transform .15s;
}
.nav:hover,.nav.active{
  background:#287b69;
  color:#ffffff;
}

/* Global accessibility bar */
.cicero-global-access{
  width:100%;
  display:flex;
  gap:8px;
  align-items:center;
  flex-wrap:wrap;
  margin-top:10px;
  padding:8px 14px;
  border-radius:16px;
  background:rgba(255,255,255,.78);
  border:1px solid #d5eee2;
  font-size:13px;
}
.cicero-global-access button,.cicero-camera-global button{
  border:0;
  border-radius:10px;
  padding:7px 11px;
  background:#e4f8ef;
  color:#247c69;
  font-weight:800;
  font-size:12
