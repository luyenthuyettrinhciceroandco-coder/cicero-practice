<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0">
<title>Cicero&amp;Co</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800;900&display=swap" rel="stylesheet">
<style>
:root{
  --ink:#477b70;
  --teal:#cceee5;
  --mint:#dcf8ec;
  --yellow:#fff4c9;
  --deep:#087f83;
  --shadow:0 10px 28px #347f6a18;
}
*{box-sizing:border-box;margin:0;padding:0}
html,body{
  width:100%;
  min-height:100vh;
  overflow-x:hidden;
  -webkit-text-size-adjust:100%;
  scroll-behavior:smooth;
}
body{
  font-family:'Nunito','Trebuchet MS',Arial,sans-serif;
  color:var(--ink);
  background-color:#d9f5ef;
  background-image:repeating-linear-gradient(
    90deg,
    rgba(255,255,255,.32) 0,
    rgba(255,255,255,.32) 18px,
    rgba(139,211,203,.18) 18px,
    rgba(139,211,203,.18) 36px
  );
}
button,input,textarea,select{font:inherit}
button{touch-action:manipulation}
img,video,canvas,iframe{max-width:100%}

/* Bố cục tràn full màn hình trên Desktop */
.app{
  width:100%;
  max-width:100%;
  min-height:100vh;
  margin:0;
  display:grid;
  grid-template-columns:240px minmax(0,1fr);
}
aside.cicero-sidebar{
  position:sticky;
  top:0;
  height:100vh;
  overflow-y:auto;
  display:flex;
  flex-direction:column;
  align-items:stretch;
  gap:8px;
  padding:18px 14px;
  background:#d9fff2;
  border-right:1px solid #b8e8df;
  z-index:80;
}
.mobile-menu-head{
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:10px;
  margin-bottom:8px;
}
.logo{
  font-family:Georgia,serif;
  font-style:italic;
  font-weight:900;
  font-size:24px;
  text-decoration:underline;
  color:#087f83;
  cursor:pointer;
  white-space:nowrap;
}
.mobile-menu-toggle{display:none}
.nav-group{
  padding:8px;
  border-radius:16px;
  background:rgba(255,255,255,.48);
  border:1px solid #bfe9df;
}
.nav-group-title{
  display:flex;
  align-items:center;
  justify-content:space-between;
  font-size:13px;
  font-weight:900;
  color:#2b7a78;
  padding:8px 10px;
  cursor:pointer;
  user-select:none;
}
.nav-group-title::after{content:"⌄";font-size:16px;transition:transform .18s ease}
.nav-group.is-collapsed .nav-group-title::after{transform:rotate(-90deg)}
.nav-group.is-collapsed .sidebtn{display:none}
.cicero-sidebar .sidebtn{
  width:100%;
  min-height:40px;
  border:0;
  border-radius:12px;
  text-align:left;
  padding:9px 12px;
  margin:3px 0;
  background:transparent;
  color:#28777a;
  font-size:14px;
  font-weight:800;
  cursor:pointer;
  display:flex;
  align-items:center;
  gap:8px;
}
.cicero-sidebar .sidebtn:hover,.cicero-sidebar .sidebtn.active{
  background:#fff;
  color:#087f83;
  box-shadow:0 3px 10px #28777a14;
}

main{
  min-width:0;
  width:100%;
  padding:18px 28px 40px;
}
.topbar{
  position:sticky;
  top:10px;
  z-index:50;
  display:flex;
  justify-content:space-between;
  align-items:center;
  flex-wrap:wrap;
  gap:10px;
  background:#f5fffff2;
  border-radius:22px;
  padding:12px 18px;
  box-shadow:0 8px 22px #428d8b20;
}
.topbar-brand{font-weight:900;color:#087f83;font-size:15px}
.topbar-actions{display:flex;gap:8px;align-items:center;flex-wrap:wrap}
.topbar .nav{
  border:0;
  background:#e8f8f4;
  color:#087f83;
  border-radius:99px;
  padding:8px 14px;
  font-weight:900;
  font-size:13px;
  cursor:pointer;
}
.topbar .nav:hover,.topbar .nav.active{background:#087f83;color:#fff}

.cicero-global-access{
  display:flex;
  gap:8px;
  align-items:center;
  flex-wrap:wrap;
  margin-top:10px;
  padding:10px 14px;
  border-radius:16px;
  background:rgba(255,255,255,.85);
  border:1px solid #d5eee2;
}
.cicero-global-access button{
  border:0;
  border-radius:11px;
  padding:8px 12px;
  background:#e4f8ef;
  color:#287b69;
  font-weight:800;
  font-size:13px;
  cursor:pointer;
}
.cicero-global-access button[aria-pressed="true"]{background:#087f83;color:#fff}

#view{width:100%;max-width:1440px;margin:0 auto}
.hero{
  text-align:center;
  margin:24px 0 20px;
  color:#fff;
  text-shadow:0 2px 6px #3a7c7c88;
  font-size:clamp(22px,2.8vw,32px);
  font-weight:900;
}
.content-area{width:100%;max-width:1280px;margin:0 auto}
.panel{
  background:#ffffffed;
  border-radius:24px;
  padding:24px;
  box-shadow:var(--shadow);
  color:#276f7b;
}
.panel h2{margin:0 0 10px;color:#087f83;text-align:center}
.panel h3{color:#087f83;margin:12px 0 6px}
.panel p{line-height:1.55;margin-bottom:8px}

.companion-home{
  display:flex;
  align-items:center;
  flex-wrap:wrap;
  gap:14px;
  background:#fff8d9;
  border-radius:20px;
  padding:14px 18px;
  margin:0 auto 18px;
  max-width:980px;
  box-shadow:var(--shadow);
}
.companion-home .mascot{font-size:42px}
.grid{
  display:grid;
  grid-template-columns:repeat(3,minmax(0,1fr));
  gap:16px;
  max-width:980px;
  margin:0 auto;
}
.skill{
  min-height:155px;
  background:#fff;
  border:2px solid #e2f5ef;
  border-radius:24px;
  box-shadow:var(--shadow);
  padding:16px 12px;
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  gap:8px;
  cursor:pointer;
  color:var(--deep);
  transition:transform .18s,box-shadow .18s;
}
.skill:hover{transform:translateY(-3px);border-color:#9bdcb9}
.art{
  width:88px;
  height:78px;
  border-radius:50%;
  display:flex;
  align-items:center;
  justify-content:center;
  background:#fff3c7;
  font-size:46px;
}
.skill:nth-child(2) .art,.skill:nth-child(5) .art{background:#d9f7f0}
.skill:nth-child(3) .art,.skill:nth-child(4) .art{background:#f4f1ff}
.skill-label{font-size:15px;font-weight:900;line-height:1.25;text-align:center}
.notice{
  margin:20px auto 0;
  max-width:980px;
  text-align:center;
  color:#337f87;
  font-size:14px;
  font-weight:800;
  background:#ffffffcc;
  border-radius:16px;
  padding:14px;
}

.btn{
  border:0;
  border-radius:13px;
  padding:11px 16px;
  background:linear-gradient(135deg,#0b9692,#087f83);
  color:#fff;
  font-weight:800;
  cursor:pointer;
  margin:4px 4px 4px 0;
  display:inline-flex;
  align-items:center;
  justify-content:center;
  gap:6px;
}
.btn:hover{filter:brightness(1.05)}
.btn:disabled{opacity:.45;cursor:not-allowed}
.btn.alt{background:#e4f7f2;color:#087f83}
.btn.yellow{background:#fff0b5;color:#7c6322}
.field{
  width:100%;
  padding:11px 13px;
  border:1px solid #c4e5e4;
  border-radius:12px;
  margin:6px 0 12px;
  background:#fff;
  color:#275d67;
}
.result{
  background:#fff5c9;
  padding:14px 16px;
  border-radius:15px;
  margin-top:12px;
  color:#5b5322;
}
.small-note{font-size:13px;color:#5a7c82;line-height:1.5}
.hidden{display:none!important}
.pill{display:inline-block;background:#e3f8f5;border-radius:30px;padding:4px 10px;font-size:12px;font-weight:800}

/* Studio & Camera */
.practice-layout{
  display:grid;
  grid-template-columns:minmax(0,1.25fr) minmax(300px,.75fr);
  gap:18px;
  margin-top:16px;
  align-items:start;
}
.studio-card{
  background:#fff;
  border:1px solid #d9f0ed;
  border-radius:22px;
  padding:20px;
  box-shadow:0 10px 26px #287d8312;
  min-width:0;
}
.studio-head{
  display:flex;
  align-items:center;
  gap:12px;
  margin-bottom:14px;
}
.studio-icon{
  width:44px;
  height:44px;
  flex:0 0 44px;
  border-radius:14px;
  background:#e0f8f3;
  display:grid;
  place-items:center;
  font-size:22px;
}
.camera-frame{
  position:relative;
  width:100%;
  height:clamp(340px,54vh,640px);
  background:#14383d;
  border-radius:20px;
  overflow:hidden;
  display:grid;
  place-items:center;
  margin:12px 0;
  border:3px solid #a9e8df;
}
.camera-frame video{
  position:absolute;
  inset:0;
  width:100%;
  height:100%;
  object-fit:contain;
  transform-origin:center center;
  transition:transform .15s ease;
}
.camera-placeholder{
  padding:24px;
  text-align:center;
  color:#d9f5ef;
  z-index:2;
}
.camera-placeholder .big{font-size:46px;display:block;margin-bottom:8px}
.camera-frame.cicero-camera-full{
  position:fixed!important;
  inset:0!important;
  width:100vw!important;
  height:100dvh!important;
  z-index:99999!important;
  border-radius:0!important;
  margin:0!important;
  border:0!important;
}
.cicero-camera-tools{
  display:flex;
  gap:8px;
  flex-wrap:wrap;
  align-items:center;
  margin:10px 0;
}
.cicero-camera-tools select{
  border:1px solid #bfe7e5;
  border-radius:10px;
  padding:8px 12px;
  background:#fff;
  color:#087f83;
  font-weight:800;
}
.session-controls{display:flex;flex-wrap:wrap;gap:8px;align-items:center;margin-top:8px}
.countdown{font-size:clamp(30px,4.5vw,44px);font-weight:900;color:#087f83;margin:6px 0}
.live-pill{
  display:inline-flex;
  align-items:center;
  gap:7px;
  background:#fff0f1;
  color:#bf5365;
  border-radius:999px;
  padding:6px 12px;
  font-size:12px;
  font-weight:800;
}
.live-dot{width:8px;height:8px;border-radius:50%;background:#ec6275}

/* Sửa lỗi chèn chữ ở khối Hướng dẫn từng bước (Hình 2) */
.body-guide-card{
  display:flex!important;
  flex-direction:column!important;
  gap:12px!important;
}
#bodyHandGuide{
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  text-align:center;
  background:#f0fbf8;
  border:1px solid #ccece5;
  border-radius:18px;
  padding:18px 14px;
  width:100%;
}
#bodyHandGuide svg{width:88px;height:88px;margin-bottom:8px;flex-shrink:0}
#bodyStepTitle{font-size:17px;color:#087f83;margin-bottom:6px;display:block}
#bodyStepDesc{font-size:14px;line-height:1.5;color:#275d67;max-width:100%;word-break:break-word}

.metric-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:10px;margin-top:12px}
.metric{background:#f5fbfb;border:1px solid #e2f0ef;border-radius:16px;padding:12px}
.metric-top{display:flex;justify-content:space-between;gap:6px;font-size:13px;font-weight:800;color:#087f83}
.metric strong{display:block;font-size:22px;color:#147f88;margin:6px 0}
.meter{height:7px;background:#e2eeee;border-radius:99px;overflow:hidden}
.meter span{display:block;height:100%;width:0;background:linear-gradient(90deg,#70d2c4,#087f83)}
.score-hero{display:flex;align-items:center;gap:16px;background:linear-gradient(120deg,#e2fbf4,#f0efff);border-radius:18px;padding:16px;margin:12px 0;flex-wrap:wrap}
.score-ring{width:80px;height:80px;flex:0 0 80px;border-radius:50%;display:grid;place-items:center;background:#087f83;color:#fff;font-size:20px;font-weight:900}
.feedback-list{display:grid;gap:8px;margin-top:12px}
.feedback-item{background:#f8fcfc;border:1px solid #e2f0ef;border-radius:13px;padding:12px;color:#355d66;line-height:1.5}
.activity-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:12px}
.mini{background:#f1fffc;border:1px solid #d5f0ec;border-radius:16px;padding:14px;margin-bottom:8px}
.animal-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(130px,1fr));gap:12px;margin-top:14px}
.animal-card{border:1px solid #d7eee2;background:#fff;border-radius:18px;padding:14px 8px;text-align:center;cursor:pointer;color:#477b70}
.animal-card .animal{display:block;font-size:36px;margin-bottom:6px}
.animal-card.locked{opacity:.65}
.animal-card.selected{outline:3px solid #087f83;background:#eafff8}
.badge-count{display:inline-flex;align-items:center;gap:8px;border-radius:999px;background:#fff4c9;padding:8px 14px;font-weight:800;color:#8b7840;margin:8px 0}
.body-guide,.reading-box,.guide-box{border:1px solid #bfe7e5;border-radius:16px;background:#f2fffb;padding:14px;margin:12px 0}
.cicero-transcript{background:#f3fbf9;border:1px solid #d8eee8;border-radius:14px;padding:12px;min-height:80px;max-height:200px;overflow:auto;white-space:pre-wrap;line-height:1.55}
.cicero-slide{background:#f5fbfa;border:2px dashed #c5e7df;border-radius:15px;min-height:100px;padding:12px;display:grid;place-items:center;text-align:center;margin-top:8px}
.cicero-global-large #view{font-size:1.15em}
.cicero-global-contrast{filter:contrast(1.22)}

/* Tối ưu hoàn toàn cho Điện thoại & Tablet (<= 820px) */
@media(max-width:820px){
  .app{
    display:flex;
    flex-direction:column;
    width:100%;
    min-height:100dvh;
  }
  aside.cicero-sidebar{
    position:sticky;
    top:0;
    height:auto;
    max-height:85vh;
    overflow-y:auto;
    width:100%;
    padding:10px 14px;
    border-right:0;
    border-bottom:1px solid #b8e8df;
  }
  .mobile-menu-head{margin-bottom:0}
  .mobile-menu-toggle{
    display:inline-flex;
    align-items:center;
    justify-content:center;
    width:42px;
    height:42px;
    border:1px solid #bce8d6;
    border-radius:12px;
    background:#fff;
    color:#087f83;
    font-size:22px;
    font-weight:900;
    cursor:pointer;
  }
  aside.cicero-sidebar .nav-group{display:none}
  aside.cicero-sidebar.menu-open .nav-group{display:block;margin-top:8px}
  aside.cicero-sidebar.menu-open .nav-group .sidebtn{display:flex}

  main{padding:12px 12px 32px}
  .topbar{position:static;padding:10px 12px;border-radius:16px}
  .topbar-brand{font-size:13px;width:100%}
  .topbar-actions{width:100%}
  .topbar .nav{flex:1;text-align:center;padding:9px 8px;font-size:12px}
  .cicero-global-access{padding:8px 10px;gap:6px}
  .cicero-global-access strong{width:100%;font-size:12px}
  .cicero-global-access button{flex:1 1 calc(50% - 6px);text-align:center;padding:8px 6px;font-size:12px}

  .panel{padding:16px 14px;border-radius:18px}
  .grid{grid-template-columns:repeat(2,minmax(0,1fr));gap:10px}
  .skill{min-height:132px;padding:12px 8px;border-radius:18px}
  .art{width:68px;height:62px;font-size:36px}
  .skill-label{font-size:13px}

  .practice-layout{grid-template-columns:1fr;gap:14px}
  .studio-card{padding:14px;border-radius:18px}
  .camera-frame{height:52vh;min-height:280px}
  .session-controls .btn{width:100%;margin:3px 0}
  .activity-grid,.metric-grid{grid-template-columns:1fr}
}
@media(max-width:380px){
  .grid{grid-template-columns:1fr}
}
</style>
</head>
<body>
<div class="app">
  <aside class="cicero-sidebar" id="sidebarMenu">
    <div class="mobile-menu-head">
      <div class="logo" data-page="Luyện tập" role="button">Cicero&amp;Co</div>
      <button class="mobile-menu-toggle" id="mobileMenuBtn" type="button" aria-label="Mở menu" aria-expanded="false">☰</button>
    </div>
    <div class="nav-group">
      <div class="nav-group-title">📚 Học tập</div>
      <button class="sidebtn" data-page="Luyện tập">🎤 Luyện tập</button>
      <button class="sidebtn" data-page="Đánh giá">📊 Đánh giá</button>
      <button class="sidebtn" data-page="Kiến thức">📖 Kiến thức</button>
      <button class="sidebtn" data-page="Trợ lý ảo">🤖 Trợ lý ảo</button>
    </div>
    <div class="nav-group">
      <div class="nav-group-title">💬 Cộng đồng</div>
      <button class="sidebtn" data-page="Bạn bè">👥 Bạn bè</button>
      <button class="sidebtn" data-page="Thi đấu">🏅 Thi đấu</button>
      <button class="sidebtn" data-page="Bảng xếp hạng">🏆 Bảng xếp hạng</button>
    </div>
    <div class="nav-group">
      <div class="nav-group-title">👤 Tài khoản</div>
      <button class="sidebtn" data-page="Tài khoản">🔐 Đăng nhập</button>
      <button class="sidebtn" data-page="Cá nhân">🌷 Cá nhân</button>
      <button class="sidebtn" data-page="Nhân vật">🧸 Nhân vật</button>
      <button class="sidebtn" data-page="Đổi quà">🎁 Đổi quà</button>
    </div>
    <div class="nav-group">
      <div class="nav-group-title">✉️ Khác</div>
      <button class="sidebtn" data-page="Góp ý">💌 Góp ý</button>
    </div>
  </aside>

  <main>
    <nav class="topbar">
      <div class="topbar-brand">Cicero&amp;Co · Cùng bạn tự tin tỏa sáng</div>
      <div class="topbar-actions">
        <button class="nav" data-page="Đánh giá">📈 Tiến độ</button>
        <button class="nav" data-page="Tài khoản">👤 Tài khoản</button>
      </div>
    </nav>
    <div class="cicero-global-access" aria-label="Truy cập dễ dàng">
      <strong>Truy cập dễ dàng:</strong>
      <button type="button" id="ciceroGlobalText" aria-pressed="false">A+ Cỡ chữ</button>
      <button type="button" id="ciceroGlobalContrast" aria-pressed="false">◐ Tương phản</button>
      <button type="button" id="ciceroGlobalRead">🔊 Đọc nội dung</button>
      <button type="button" id="ciceroGlobalStop">■ Dừng đọc</button>
    </div>
    <div id="view"></div>
  </main>
</div>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>
<script>
const skills=[
 {name:'Luyện ngôn ngữ cơ thể',emoji:'🕺',desc:'Tập tư thế đứng, ánh mắt, nét mặt và cử chỉ tự nhiên.',task:'Hãy giới thiệu bản thân trong 45 giây. Đứng thẳng, nhìn vào camera và dùng tay minh họa vừa phải.',steps:['Đứng thẳng, thả lỏng vai','Nhìn vào camera như đang nhìn người nghe','Dùng cử chỉ để nhấn mạnh 2 ý chính']},
 {name:'Luyện diễn đạt',emoji:'🗣️',desc:'Luyện nói rõ ý, sắp xếp ý theo trình tự và tránh nói vòng vo.',task:'Nói trong 60 giây về một cuốn sách, bộ phim hoặc môn học em yêu thích.',steps:['Nêu ý chính trong câu đầu','Đưa ra 2 lý do hoặc ví dụ','Kết lại bằng một câu tổng kết']},
 {name:'Luyện giọng nói',emoji:'🎤',desc:'Luyện âm lượng, tốc độ, phát âm và nhấn nhá.',task:'Đọc một đoạn văn ngắn trong 30–60 giây. Thử thay đổi giọng ở câu quan trọng.',steps:['Đọc rõ từng từ','Dừng ngắn ở dấu câu','Nhấn giọng ở từ khóa, không nói quá nhanh']},
 {name:'Luyện phản xạ & ứng biến',emoji:'💬',desc:'Tập trả lời câu hỏi bất ngờ bằng ý rõ ràng và bình tĩnh.',task:'Bốc một câu hỏi, suy nghĩ 10 giây rồi trả lời trong 30 giây.',steps:['Trả lời thẳng vào câu hỏi','Nêu một lý do','Đưa ví dụ ngắn để làm rõ']},
 {name:'Luyện tập tổng hợp',emoji:'🧠',desc:'Kết hợp ngôn ngữ cơ thể, diễn đạt, giọng nói và phản xạ.',task:'Thuyết trình 90 giây về chủ đề “Một thay đổi nhỏ giúp trường học tốt hơn”.',steps:['Mở đầu thu hút','Trình bày 2 ý kèm ví dụ','Kết luận và sẵn sàng trả lời câu hỏi']}
];

const view=document.getElementById('view');
let timerInt=null,seconds=0,stream=null,questionIndex=0,sessionInt=null,sessionEndAt=0,sessionSeconds=0,recognition=null,recognitionText='',recognitionProcessed=0,audioCtx=null,analyser=null,levelLoop=null,levelSamples=[],speechMarks=[];
const qs=[
 'Nếu em có thể thay đổi một điều ở trường học, em sẽ chọn điều gì và vì sao?',
 'Hãy kể về một lần em học được điều mới từ người khác.',
 'Theo em, làm việc nhóm cần điều gì nhất? Hãy đưa ra ví dụ.',
 'Nếu gặp một vấn đề khó mà chưa biết đáp án, em sẽ làm gì trước tiên?',
 'Hãy thuyết phục bạn thử một thói quen học tập có ích.',
 'Em nghĩ mạng xã hội mang lại lợi ích và thách thức nào cho học sinh?',
 'Nếu có một phút để giới thiệu bản thân trước lớp, em sẽ nói những gì?',
 'Theo em, một người biết lắng nghe thể hiện điều đó bằng hành động nào?'
];

let bodyGuideRetry=false,isAnswerRound=false,presentationSeconds=0,questionPhaseTimer=null,selectedRoundQuestion='',firstRoundTranscript='',firstRoundSamples=[],firstRoundMarks=[],activeSkill=0;

function escapeHtml(s){return String(s??'').replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]))}
function getBadges(){return Number(localStorage.getItem('ciceroBadges')||0)}
function setBadges(n){localStorage.setItem('ciceroBadges',String(Math.max(0,n)))}
function awardBadges(n,reason){setBadges(getBadges()+n);return `+${n} huy hiệu chăm chỉ ${reason||''} · Tổng: ${getBadges()}`}
function stopTimer(){if(timerInt){clearInterval(timerInt);timerInt=null}}

const CICERO_SUPABASE_URL='https://odddbacmtfgooorkyvav.supabase.co';
const CICERO_SUPABASE_KEY='sb_publishable_qeUMK_C2SU_mGLBHF0pUdA_QIr91-KC';
const ciceroSupabase=window.supabase?.createClient(CICERO_SUPABASE_URL,CICERO_SUPABASE_KEY);
let ciceroCloudUser=null;
(async()=>{try{const {data}=await ciceroSupabase.auth.getSession();ciceroCloudUser=data.session?.user||null;ciceroSupabase.auth.onAuthStateChange((_e,s)=>{ciceroCloudUser=s?.user||null});}catch(e){}})();

/* Hàm gắn điều khiển Zoom & Toàn màn hình hoạt động trên cả PC và Mobile */
function attachCameraControls(frameId, videoId, isMirrored=true){
  const frame=document.getElementById(frameId);
  const video=document.getElementById(videoId);
  if(!frame || !video || frame.dataset.zoomReady==='1') return;
  frame.dataset.zoomReady='1';

  const bar=document.createElement('div');
  bar.className='cicero-camera-tools';
  bar.innerHTML=`
    <label for="${videoId}Zoom"><b>🔍 Zoom camera:</b></label>
    <select id="${videoId}Zoom">
      <option value="0.75">0.75×</option>
      <option value="1" selected>1× (Mặc định)</option>
      <option value="1.25">1.25×</option>
      <option value="1.5">1.5×</option>
      <option value="2">2×</option>
      <option value="2.5">2.5×</option>
      <option value="3">3×</option>
    </select>
    <button type="button" class="btn alt" id="${videoId}FullBtn">⛶ Toàn màn hình</button>
  `;
  frame.insertAdjacentElement('afterend', bar);

  const sel=document.getElementById(videoId+'Zoom');
  const fullBtn=document.getElementById(videoId+'FullBtn');

  const applyZoom=()=>{
    const z=parseFloat(sel.value)||1;
    const mirror=isMirrored ? 'scaleX(-1) ' : '';
    video.style.transform=`${mirror}scale(${z})`;
    // Nếu thiết bị hỗ trợ zoom phần cứng qua MediaTrackConstraints
    try{
      const track=video.srcObject?.getVideoTracks?.()[0];
      const caps=track?.getCapabilities?.();
      if(caps && caps.zoom){
        const clamped=Math.min(caps.zoom.max, Math.max(caps.zoom.min, z));
        track.applyConstraints({advanced:[{zoom:clamped}]}).catch(()=>{});
      }
    }catch(e){}
  };
  sel.addEventListener('change', applyZoom);

  fullBtn.addEventListener('click',()=>{
    const isFull=frame.classList.toggle('cicero-camera-full');
    fullBtn.textContent=isFull?'✕ Thu nhỏ':'⛶ Toàn màn hình';
    if(isFull){
      // Thêm nút thoát nổi bên trong khung khi phóng full
      let exitOverlay=frame.querySelector('.exit-full-overlay');
      if(!exitOverlay){
        exitOverlay=document.createElement('button');
        exitOverlay.type='button';
        exitOverlay.className='btn exit-full-overlay';
        exitOverlay.textContent='✕ Thoát toàn màn hình';
        exitOverlay.style.cssText='position:absolute;top:16px;right:16px;z-index:100000;';
        exitOverlay.onclick=()=>fullBtn.click();
        frame.appendChild(exitOverlay);
      }
    }else{
      frame.querySelector('.exit-full-overlay')?.remove();
    }
  });
}

function home(){
  stopTimer();
  let chosen=Number(localStorage.getItem('ciceroCharacter')||0);
  const critters=[['🐰','Thỏ Mây'],['🦊','Cáo Cam'],['🐼','Gấu Trúc'],['🐱','Mèo Mun'],['🐶','Cún Bông'],['🦉','Cú Đêm'],['🐸','Ếch Xanh'],['🦋','Bướm Ngọc'],['🐧','Cánh Cụt'],['🦄','Kỳ Lân']];
  const pet=critters[chosen]||critters[0];
  view.innerHTML=`
    <h1 class="hero">Chọn nội dung luyện tập</h1>
    <div class="companion-home">
      <span class="mascot">${pet[0]}</span>
      <div style="flex:1;min-width:180px">
        <b>Bạn đồng hành: ${pet[1]}</b>
        <div class="small-note">Chạm để chọn một người bạn khác.</div>
      </div>
      <button class="btn alt" id="chooseCompanionHome">🐾 Chọn bạn đồng hành</button>
    </div>
    <section class="grid">
      ${skills.map((s,i)=>`<button class="skill" data-skill="${i}"><span class="art">${s.emoji}</span><span class="skill-label">${s.name}</span></button>`).join('')}
      <button class="skill" id="ciceroAccessTile" type="button">
        <span class="art">🦯</span>
        <span class="skill-label">Thuyết trình cho người khiếm thị</span>
      </button>
    </section>
    <div class="notice">Chọn một kỹ năng để bắt đầu luyện tập ✨</div>
  `;
  view.querySelectorAll('[data-skill]').forEach(b=>b.onclick=()=>openSkill(+b.dataset.skill));
  document.getElementById('chooseCompanionHome').onclick=()=>page('Nhân vật');
  document.getElementById('ciceroAccessTile').onclick=()=>renderAccessiblePresentation();
}

function cleanupPractice(){
  if(sessionInt){clearInterval(sessionInt);sessionInt=null}
  if(levelLoop){cancelAnimationFrame(levelLoop);levelLoop=null}
  try{if(recognition){recognition.onresult=null;recognition.onerror=null;recognition.onend=null;recognition.stop()}}catch(e){}
  recognition=null;
  if(stream){stream.getTracks().forEach(t=>t.stop());stream=null}
  if(audioCtx){try{audioCtx.close()}catch(e){} audioCtx=null}
  analyser=null;
  const video=document.getElementById('cam');
  if(video){video.srcObject=null;video.classList.add('hidden')}
  const placeholder=document.getElementById('cameraPlaceholder');
  if(placeholder)placeholder.classList.remove('hidden');
  const btn=document.getElementById('cameraBtn');
  if(btn){btn.textContent='Bắt đầu buổi luyện';btn.disabled=false}
  const pill=document.getElementById('livePill');
  if(pill)pill.classList.add('hidden');
}

function endPractice(showResults=true,reason='manual'){
  const wasActive=!!stream||!!sessionInt;
  if(!wasActive)return;
  cleanupPractice();
  if(showResults)renderScore(reason);
}

function renderScore(reason){
  const box=document.getElementById('scoreResult');if(!box)return;
  const words=(recognitionText.match(/[\p{L}\p{N}]+/gu)||[]);
  const mins=Math.max(sessionSeconds/60,1/60);
  const wpm=Math.round(words.length/mins);
  const overall=words.length<5?60:Math.min(96,70+Math.floor(words.length/3));
  box.classList.remove('hidden');
  const pinned=document.getElementById('currentScore');if(pinned)pinned.textContent=overall+'/100';
  box.innerHTML=`
    <div class="studio-card" style="margin-top:16px">
      <h2>📊 Kết quả buổi luyện: ${overall}/100</h2>
      <p class="small-note">Thời gian: ${Math.floor(sessionSeconds/60)} phút ${sessionSeconds%60} giây · Nhận diện: ${words.length} từ · Tốc độ: ${words.length<5?'—':wpm+' từ/phút'}</p>
      <details style="margin-top:10px"><summary style="cursor:pointer;font-weight:800">Xem nội dung đã nói</summary><p class="small-note">${escapeHtml(recognitionText||'Chưa ghi nhận được lời nói.')}</p></details>
      <div class="session-controls"><button class="btn alt" id="retryPractice">Luyện lại</button></div>
    </div>`;
  let arr=JSON.parse(localStorage.getItem('ciceroResults')||'[]');
  arr.unshift({skill:skills[activeSkill].name,date:new Date().toLocaleString('vi-VN'),seconds:sessionSeconds,score:overall});
  localStorage.setItem('ciceroResults',JSON.stringify(arr));
  document.getElementById('retryPractice').onclick=()=>openSkill(activeSkill);
}

function renderBodyLanguageRoom(){
  const steps=[
    {title:'Tay nghỉ tự nhiên',desc:'Đặt hai tay trước bụng hoặc ngang eo, vai thả lỏng.',tip:'Giữ tay trong khung hình, không cần đứng im cứng nhắc.'},
    {title:'Mở lòng bàn tay',desc:'Khi giải thích một ý, mở lòng bàn tay nhẹ nhàng hướng lên.',tip:'Không chĩa ngón tay vào người nghe.'},
    {title:'Đếm ý bằng ngón tay',desc:'Dùng 1–3 ngón tay khi liệt kê ý chính.',tip:'Đưa tay lên ngang ngực, tránh đưa sát mặt.'},
    {title:'Kết thúc và thả lỏng',desc:'Hạ tay về vị trí nghỉ khi nói xong ý.',tip:'Tránh vung tay liên tục hoặc che mắt, mũi, miệng.'}
  ];
  let stepIndex=0,streamLocal=null;
  view.innerHTML=`
    <h1 class="hero">Luyện ngôn ngữ cơ thể</h1>
    <section class="content-area">
      <div class="panel">
        <button class="btn alt" id="back">← Quay lại kỹ năng</button>
        <div class="body-guide">
          <b>🌿 Nhắc nhở trước khi bắt đầu</b>
          <p>Đặt điện thoại/máy tính ngang tầm mắt, để thấy từ đầu đến hông và cả hai bàn tay.</p>
        </div>
        <div class="practice-layout">
          <div class="studio-card">
            <div class="studio-head"><div class="studio-icon">📷</div><div><h2>Camera luyện tập</h2><div class="small-note">Chỉ dùng camera · Không bật micro</div></div></div>
            <div class="camera-frame" id="bodyCamFrame">
              <div class="camera-placeholder" id="bodyCamPlaceholder"><span class="big">👐</span><b>Sẵn sàng luyện tay?</b><p>Bấm mở camera để tự quan sát tư thế.</p></div>
              <video id="bodyCam" autoplay muted playsinline class="hidden" style="transform:scaleX(-1)"></video>
            </div>
            <div class="session-controls">
              <button class="btn" id="bodyCamStart">Mở camera</button>
              <button class="btn alt" id="bodyCamStop" disabled>⏹ Kết thúc luyện tập</button>
            </div>
            <p id="bodyCamMsg" class="small-note" style="margin-top:8px">Nếu camera chưa mở, hãy cấp quyền camera trên trình duyệt.</p>
          </div>

          <div class="studio-card body-guide-card">
            <div class="studio-head" style="margin-bottom:0"><div class="studio-icon">🖐️</div><div><h2>Hướng dẫn từng bước</h2><div class="small-note">Một động tác mỗi lần để không rối</div></div></div>
            <div id="bodyHandGuide">
              <svg viewBox="0 0 120 120" aria-label="Hình minh họa bàn tay" role="img"><path d="M37 100 Q27 91 29 76 L32 53 Q33 46 39 48 Q44 49 43 56 L43 31 Q44 24 50 25 Q56 25 56 32 L56 48 L57 19 Q58 12 64 14 Q70 15 69 22 L69 48 L72 28 Q74 21 80 24 Q85 26 83 33 L81 53 L86 42 Q90 37 95 41 Q99 44 96 50 L88 79 Q85 95 71 103 Z" fill="#f6c7a9" stroke="#d49a7b" stroke-width="2"/><path d="M47 74 Q58 81 72 73" fill="none" stroke="#d49a7b" stroke-width="2" stroke-linecap="round"/></svg>
              <b id="bodyStepTitle">Tay nghỉ tự nhiên</b>
              <p id="bodyStepDesc"></p>
            </div>
            <p id="bodyStepTip" class="small-note"></p>
            <div class="session-controls">
              <button class="btn alt" id="bodyPrev">← Trước</button>
              <button class="btn" id="bodyNext">Động tác tiếp →</button>
            </div>
            <div class="small-note" id="bodyStepCount">Động tác 1/4</div>
          </div>
        </div>
      </div>
    </section>
  `;
  attachCameraControls('bodyCamFrame','bodyCam',true);

  const renderStep=()=>{
    const st=steps[stepIndex];
    document.getElementById('bodyStepTitle').textContent=st.title;
    document.getElementById('bodyStepDesc').textContent=st.desc;
    document.getElementById('bodyStepTip').textContent='💡 Nhắc nhở: '+st.tip;
    document.getElementById('bodyStepCount').textContent=`Động tác ${stepIndex+1}/${steps.length}`;
    document.getElementById('bodyPrev').disabled=stepIndex===0;
    document.getElementById('bodyNext').textContent=stepIndex===steps.length-1?'Bắt đầu lại →':'Động tác tiếp →';
  };
  renderStep();
  document.getElementById('bodyPrev').onclick=()=>{stepIndex=Math.max(0,stepIndex-1);renderStep()};
  document.getElementById('bodyNext').onclick=()=>{stepIndex=(stepIndex+1)%steps.length;renderStep()};

  document.getElementById('bodyCamStart').onclick=async()=>{
    try{
      streamLocal=await navigator.mediaDevices.getUserMedia({video:{facingMode:'user'},audio:false});
      const v=document.getElementById('bodyCam');
      v.srcObject=streamLocal;
      v.classList.remove('hidden');
      await v.play().catch(()=>{});
      document.getElementById('bodyCamPlaceholder').classList.add('hidden');
      document.getElementById('bodyCamStart').disabled=true;
      document.getElementById('bodyCamStop').disabled=false;
      document.getElementById('bodyCamMsg').textContent='Camera đang bật. Bạn có thể chọn mức Zoom ngay bên dưới khung hình.';
    }catch(e){
      document.getElementById('bodyCamMsg').textContent='Không mở được camera. Hãy cấp quyền camera và mở trang bằng HTTPS.';
    }
  };
  const stopBodyCam=()=>{
    if(streamLocal){streamLocal.getTracks().forEach(t=>t.stop());streamLocal=null}
    const v=document.getElementById('bodyCam');if(v){v.srcObject=null;v.classList.add('hidden')}
    document.getElementById('bodyCamPlaceholder').classList.remove('hidden');
    document.getElementById('bodyCamStart').disabled=false;
    document.getElementById('bodyCamStop').disabled=true;
  };
  document.getElementById('bodyCamStop').onclick=stopBodyCam;
  document.getElementById('back').onclick=()=>{stopBodyCam();home()};
}

function openSkill(i){
  stopTimer();cleanupPractice();activeSkill=i;
  if(i===0){renderBodyLanguageRoom();return;}
  let s=skills[i];
  const randomPrompt=qs[Math.floor(Math.random()*qs.length)];
  sessionSeconds=0;recognitionText='';
  view.innerHTML=`
    <h1 class="hero">${s.name}</h1>
    <section class="content-area">
      <div class="panel">
        <button class="btn alt" id="back">← Quay lại kỹ năng</button>
        <div class="result"><b>🎯 Nhiệm vụ của bạn</b><p>${s.task}</p><p class="small-note">${s.steps.join(' · ')}</p></div>
        ${i===3?`<div class="reading-box"><b>🎲 Câu hỏi ngẫu nhiên</b><p id="randomQuestionText">${randomPrompt}</p><button type="button" class="btn alt" id="newRandomQuestion">🎲 Bốc câu hỏi khác</button></div>`:''}
        ${i===2?`<div class="reading-box"><b>📖 Đoạn mẫu luyện đọc</b><textarea class="field" id="readingText" rows="3">Xin chào mọi người. Hôm nay, tôi muốn chia sẻ một ý tưởng nhỏ có thể tạo nên thay đổi tích cực.</textarea></div>`:''}
        <div class="result" style="display:flex;justify-content:space-between;align-items:center"><b>🏆 ĐIỂM BUỔI LUYỆN</b><strong id="currentScore" style="font-size:20px">Chưa chấm</strong></div>
        <div class="practice-layout">
          <div class="studio-card">
            <div class="studio-head"><div class="studio-icon">🎥</div><div><h2>Phòng luyện nói</h2><div class="small-note">Camera + micro · Tự kết thúc khi hết giờ</div></div></div>
            <div class="camera-frame" id="mainCamFrame">
              <div class="camera-placeholder" id="cameraPlaceholder"><span class="big">🎬</span><b>Sẵn sàng lên hình?</b><p>Chọn thời lượng và bấm bắt đầu.</p></div>
              <video id="cam" class="hidden" autoplay muted playsinline style="transform:scaleX(-1)"></video>
            </div>
            <div class="session-controls">
              <label for="duration"><b>Thời lượng (phút):</b></label>
              <input class="field" id="duration" type="number" min="0.25" max="60" step="0.25" value="2" style="width:100px;margin:0">
              <span id="livePill" class="live-pill hidden"><span class="live-dot"></span> ĐANG LUYỆN</span>
            </div>
            <div class="countdown" id="countdown">02:00</div>
            <div class="session-controls">
              <button class="btn" id="cameraBtn">Bắt đầu buổi luyện</button>
              <button class="btn alt" id="finishBtn" disabled>Kết thúc sớm</button>
            </div>
            <p id="camMsg" class="small-note" style="margin-top:8px">Bấm bắt đầu để mở camera và micro.</p>
          </div>
          <div class="studio-card">
            <div class="studio-head"><div class="studio-icon">📈</div><div><h2>Chỉ số trực tiếp</h2></div></div>
            <div class="metric-grid">
              <div class="metric"><div class="metric-top"><span>Tốc độ nói</span><span>🗣️</span></div><strong id="liveWpm">—</strong><p class="small-note">Từ/phút</p></div>
              <div class="metric"><div class="metric-top"><span>Số từ nhận diện</span><span>📝</span></div><strong id="liveWords">0</strong><p class="small-note">Từ đã nói</p></div>
            </div>
          </div>
        </div>
        <div id="scoreResult" class="hidden"></div>
      </div>
    </section>
  `;
  attachCameraControls('mainCamFrame','cam',true);
  document.getElementById('back').onclick=()=>{endPractice(false);home()};
  const rq=document.getElementById('newRandomQuestion');
  if(rq)rq.onclick=()=>{document.getElementById('randomQuestionText').textContent=qs[Math.floor(Math.random()*qs.length)]};
  const fmtTime=n=>String(Math.floor(n/60)).padStart(2,'0')+':'+String(n%60).padStart(2,'0');
  document.getElementById('duration').onchange=e=>{if(!stream){const n=Math.round(+e.target.value*60);if(n>0)document.getElementById('countdown').textContent=fmtTime(n)}};
  document.getElementById('finishBtn').onclick=()=>endPractice(true,'manual');
  document.getElementById('cameraBtn').onclick=async()=>{
    const btn=document.getElementById('cameraBtn');btn.disabled=true;
    try{
      stream=await navigator.mediaDevices.getUserMedia({video:{facingMode:'user'},audio:true});
      const video=document.getElementById('cam');video.srcObject=stream;video.classList.remove('hidden');await video.play().catch(()=>{});
      document.getElementById('cameraPlaceholder').classList.add('hidden');
      const total=Math.round(+document.getElementById('duration').value*60);
      sessionEndAt=Date.now()+total*1000;
      document.getElementById('livePill').classList.remove('hidden');
      document.getElementById('finishBtn').disabled=false;
      btn.textContent='Đang luyện…';
      const SR=window.SpeechRecognition||window.webkitSpeechRecognition;
      if(SR){
        recognition=new SR();recognition.lang='vi-VN';recognition.continuous=true;recognition.interimResults=true;
        recognition.onresult=e=>{
          let txt='';for(let k=0;k<e.results.length;k++)txt+=e.results[k][0].transcript+' ';
          recognitionText=txt;
          const words=(txt.match(/[\p{L}\p{N}]+/gu)||[]).length;
          document.getElementById('liveWords').textContent=words;
        };
        try{recognition.start()}catch(e){}
      }
      sessionInt=setInterval(()=>{
        const left=Math.max(0,Math.ceil((sessionEndAt-Date.now())/1000));
        sessionSeconds=total-left;
        document.getElementById('countdown').textContent=fmtTime(left);
        const w=(recognitionText.match(/[\p{L}\p{N}]+/gu)||[]).length;
        document.getElementById('liveWpm').textContent=w?Math.round(w/Math.max(sessionSeconds/60,1/60)):'—';
        if(left<=0)endPractice(true,'timeout');
      },300);
    }catch(e){
      cleanupPractice();
      document.getElementById('camMsg').textContent='Không mở được camera/micro: '+e.message;
    }
  };
}

function renderAccessiblePresentation(){
  cleanupPractice();
  view.innerHTML=`
    <h1 class="hero">🦯 Thuyết trình cho người khiếm thị</h1>
    <section class="content-area">
      <div class="panel">
        <button class="btn alt" id="backA11y">← Quay lại trang chính</button>
        <div class="reading-box">
          <label for="a11yScript"><b>Nội dung / kịch bản bài nói</b></label>
          <textarea id="a11yScript" class="field" rows="6" placeholder="Nhập hoặc dán nội dung bài thuyết trình tại đây..."></textarea>
          <div class="session-controls">
            <button class="btn" id="a11yReadScript">🔊 Đọc bài nói</button>
            <button class="btn alt" id="a11yStopScript">■ Dừng đọc</button>
          </div>
        </div>
        <div class="studio-card">
          <h2>🎥 Camera luyện tập</h2>
          <div class="camera-frame" id="a11yCamFrame">
            <div class="camera-placeholder" id="a11yCamPlaceholder"><span class="big">📷</span><b>Camera đang tắt</b></div>
            <video id="a11yCamVideo" class="hidden" autoplay muted playsinline style="transform:scaleX(-1)"></video>
          </div>
          <div class="session-controls">
            <button class="btn" id="a11yCamera">Bật camera</button>
            <button class="btn alt" id="a11yCameraStop">Tắt camera</button>
          </div>
        </div>
      </div>
    </section>
  `;
  attachCameraControls('a11yCamFrame','a11yCamVideo',true);
  let a11yStream=null;
  document.getElementById('backA11y').onclick=()=>{a11yStream?.getTracks().forEach(t=>t.stop());home()};
  document.getElementById('a11yReadScript').onclick=()=>{
    const t=document.getElementById('a11yScript').value.trim();
    if(t){speechSynthesis.cancel();const u=new SpeechSynthesisUtterance(t);u.lang='vi-VN';speechSynthesis.speak(u)}
  };
  document.getElementById('a11yStopScript').onclick=()=>speechSynthesis.cancel();
  document.getElementById('a11yCamera').onclick=async()=>{
    try{
      a11yStream=await navigator.mediaDevices.getUserMedia({video:{facingMode:'user'},audio:false});
      const v=document.getElementById('a11yCamVideo');v.srcObject=a11yStream;v.classList.remove('hidden');await v.play().catch(()=>{});
      document.getElementById('a11yCamPlaceholder').classList.add('hidden');
    }catch(e){alert('Không mở được camera: '+e.message)}
  };
  document.getElementById('a11yCameraStop').onclick=()=>{
    a11yStream?.getTracks().forEach(t=>t.stop());a11yStream=null;
    const v=document.getElementById('a11yCamVideo');v.srcObject=null;v.classList.add('hidden');
    document.getElementById('a11yCamPlaceholder').classList.remove('hidden');
  };
}

function page(name){
  stopTimer();cleanupPractice();
  if(name==='Luyện tập'){home();return}
  const pages={
    'Cá nhân':`<h1 class="hero">Hồ sơ cá nhân</h1><div class="content-area panel"><h2>🌷 Góc của bạn</h2><label>Tên hiển thị</label><input class="field" id="username" placeholder="Nhập tên của bạn"><button class="btn" id="saveProfile">Lưu hồ sơ</button><div id="profileMsg" class="small-note"></div></div>`,
    'Kiến thức':`<h1 class="hero">Kiến thức thuyết trình</h1><div class="content-area panel"><h2>📚 Bí quyết nói tự tin</h2><div class="activity-grid"><div class="mini"><h3>1. Mở đầu</h3><p>Chào người nghe, nêu chủ đề và đặt một câu hỏi gợi tò mò.</p></div><div class="mini"><h3>2. Triển khai</h3><p>Mỗi ý chính nên có giải thích và ví dụ cụ thể.</p></div><div class="mini"><h3>3. Giọng nói</h3><p>Nói vừa đủ nghe, ngắt nghỉ ở dấu câu và nhấn từ khóa.</p></div><div class="mini"><h3>4. Kết thúc</h3><p>Tóm tắt thông điệp và cảm ơn người nghe.</p></div></div></div>`,
    'Đánh giá':`<h1 class="hero">Đánh giá tiến bộ</h1><div class="content-area panel"><h2>📈 Nhật ký luyện tập</h2><div id="history"></div><button class="btn alt" id="clearHistory">Xóa lịch sử</button></div>`,
    'Bảng xếp hạng':`<h1 class="hero">Bảng xếp hạng</h1><div class="content-area panel"><h2>🏆 Đấu trường Cicero</h2><div class="badge-count">🏅 Huy hiệu chăm chỉ: ${getBadges()}</div><p class="small-note">Hãy luyện tập thường xuyên để tích lũy huy hiệu và điểm số.</p></div>`,
    'Đổi quà':`<h1 class="hero">Đổi quà</h1><div class="content-area panel"><h2>🎁 Cửa hàng phần thưởng</h2><div class="badge-count">🏅 Huy hiệu hiện có: ${getBadges()}</div><p>Tích lũy huy hiệu từ các buổi luyện tập để mở khóa thêm bạn đồng hành mới!</p></div>`,
    'Góp ý':`<h1 class="hero">💌 Góp ý</h1><div class="content-area panel"><h2>Gửi phản hồi</h2><textarea id="feedbackMessage" class="field" rows="4" placeholder="Bạn muốn Cicero cải thiện điều gì?"></textarea><button class="btn" id="sendFb">✉️ Gửi góp ý</button><p id="fbStatus" class="small-note"></p></div>`,
    'Trợ lý ảo':`<h1 class="hero">Trợ lý ảo Cicero</h1><div class="content-area panel"><h2>💬 Hỏi đáp thuyết trình</h2><textarea id="aiQuestion" class="field" rows="3" placeholder="Nhập câu hỏi về cách mở đầu, giảm run, giọng nói..."></textarea><button class="btn" id="askCicero">Gửi câu hỏi ✨</button><div id="aiReply" class="result hidden"></div></div>`,
    'Nhân vật':`<h1 class="hero">Bạn đồng hành</h1><div class="content-area panel"><h2>🐾 Chọn nhân vật</h2><div class="animal-grid" id="animalGrid"></div><div id="characterMsg" class="result">Chọn nhân vật bạn thích.</div></div>`,
    'Bạn bè':`<h1 class="hero">Bạn bè</h1><div class="content-area panel"><h2>🔗 Chia sẻ liên kết</h2><input id="shareUrl" class="field" readonly><button class="btn" id="copyShareUrl">Sao chép liên kết</button><p id="shareMsg" class="small-note"></p></div>`,
    'Thi đấu':`<h1 class="hero">Đấu trường hùng biện</h1><div class="content-area panel"><h2>🎤 Thử thách 30 giây</h2><div id="question" class="result" style="font-weight:800;font-size:17px">${qs[0]}</div><div class="countdown" id="challengeTimer">00:30</div><button class="btn" id="startChallenge">Bắt đầu 30 giây</button><button class="btn alt" id="nextQuestion">Câu hỏi khác</button></div>`,
    'Tài khoản':`<h1 class="hero">Tài khoản Cicero</h1><div class="content-area panel"><h2>🌿 Đăng nhập / Đăng ký</h2><label>Email</label><input class="field" id="accountEmail" type="email" placeholder="ban@example.com"><label>Mật khẩu</label><input class="field" id="accountPass" type="password" placeholder="Ít nhất 6 ký tự"><button class="btn" id="loginAccount">Đăng nhập</button><div id="accountMsg" class="result">${ciceroCloudUser?'Đang đăng nhập: '+escapeHtml(ciceroCloudUser.email):'Chưa đăng nhập.'}</div></div>`
  };
  view.innerHTML=pages[name]||pages['Luyện tập'];

  if(name==='Cá nhân'){
    let p=JSON.parse(localStorage.getItem('ciceroProfile')||'{}');
    document.getElementById('username').value=p.name||'';
    document.getElementById('saveProfile').onclick=()=>{
      localStorage.setItem('ciceroProfile',JSON.stringify({name:document.getElementById('username').value.trim()}));
      document.getElementById('profileMsg').textContent='Đã lưu hồ sơ.';
    };
  }
  if(name==='Đánh giá'){
    const el=document.getElementById('history');
    let arr=JSON.parse(localStorage.getItem('ciceroResults')||'[]');
    el.innerHTML=arr.length?arr.map(x=>`<div class="mini"><b>${escapeHtml(x.skill)}</b> · <small>${escapeHtml(x.date)}</small><p>Điểm: <b>${x.score}/100</b> (${x.seconds} giây)</p></div>`).join(''):'<p>Chưa có buổi luyện tập nào.</p>';
    document.getElementById('clearHistory').onclick=()=>{localStorage.removeItem('ciceroResults');page('Đánh giá')};
  }
  if(name==='Nhân vật'){
    const animals=[['🐰','Thỏ Mây'],['🦊','Cáo Cam'],['🐼','Gấu Trúc'],['🐱','Mèo Mun'],['🐶','Cún Bông'],['🦉','Cú Đêm'],['🐸','Ếch Xanh'],['🦋','Bướm Ngọc'],['🐧','Cánh Cụt'],['🦄','Kỳ Lân']];
    document.getElementById('animalGrid').innerHTML=animals.map((a,i)=>`<button class="animal-card" data-animal="${i}"><span class="animal">${a[0]}</span><b>${a[1]}</b></button>`).join('');
    document.querySelectorAll('[data-animal]').forEach(b=>b.onclick=()=>{
      localStorage.setItem('ciceroCharacter',b.dataset.animal);
      document.getElementById('characterMsg').textContent='Đã chọn '+animals[+b.dataset.animal][1]+' làm bạn đồng hành ✨';
    });
  }
  if(name==='Bạn bè'){
    const u=document.getElementById('shareUrl');u.value=location.href.split('#')[0];
    document.getElementById('copyShareUrl').onclick=async()=>{await navigator.clipboard?.writeText(u.value);document.getElementById('shareMsg').textContent='Đã sao chép liên kết!'};
  }
  if(name==='Thi đấu'){
    document.getElementById('nextQuestion').onclick=()=>{questionIndex=(questionIndex+1)%qs.length;document.getElementById('question').textContent=qs[questionIndex]};
    document.getElementById('startChallenge').onclick=()=>{
      stopTimer();let left=30;document.getElementById('challengeTimer').textContent='00:30';
      timerInt=setInterval(()=>{left--;document.getElementById('challengeTimer').textContent='00:'+String(left).padStart(2,'0');if(left<=0){stopTimer();document.getElementById('challengeTimer').textContent='Hết giờ!'}},1000);
    };
  }
  if(name==='Trợ lý ảo'){
    document.getElementById('askCicero').onclick=()=>{
      const q=document.getElementById('aiQuestion').value.trim().toLowerCase();
      const rep=document.getElementById('aiReply');rep.classList.remove('hidden');
      if(/run|hồi hộp|sợ/.test(q))rep.textContent='Mẹo giảm run: Hít sâu 4 giây, thở ra 6 giây 3 lần trước khi nói; chuẩn bị thật kỹ 2 câu mở đầu và nhìn vào trán/vai người nghe thay vì nhìn thẳng vào mắt.';
      else if(/mở đầu/.test(q))rep.textContent='Mở đầu ấn tượng trong 20 giây: Nêu một con số bất ngờ, đặt một câu hỏi gợi mở hoặc kể một tình huống ngắn liên quan trực tiếp đến người nghe.';
      else rep.textContent='Cấu trúc bài nói 3 phần chuẩn: (1) Mở đầu thu hút và nêu vấn đề → (2) Trình bày 2–3 luận điểm kèm ví dụ thực tế → (3) Tóm tắt thông điệp cốt lõi và cảm ơn.';
    };
  }
  if(name==='Góp ý'){
    document.getElementById('sendFb').onclick=()=>{document.getElementById('fbStatus').textContent='Cảm ơn bạn đã gửi góp ý cho Cicero&Co!'};
  }
}

/* Điều khiển menu trên điện thoại */
const sidebarMenu=document.getElementById('sidebarMenu');
const mobileMenuBtn=document.getElementById('mobileMenuBtn');
mobileMenuBtn.addEventListener('click',()=>{
  const opened=sidebarMenu.classList.toggle('menu-open');
  mobileMenuBtn.setAttribute('aria-expanded',String(opened));
  mobileMenuBtn.textContent=opened?'✕':'☰';
});

/* Đóng/mở nhóm menu trên Desktop */
document.querySelectorAll('.nav-group-title').forEach(title=>{
  title.addEventListener('click',()=>title.parentElement.classList.toggle('is-collapsed'));
});

/* Chuyển trang */
document.querySelectorAll('[data-page]').forEach(b=>{
  b.addEventListener('click',()=>{
    document.querySelectorAll('[data-page]').forEach(x=>x.classList.remove('active'));
    b.classList.add('active');
    sidebarMenu.classList.remove('menu-open');
    mobileMenuBtn.setAttribute('aria-expanded','false');
    mobileMenuBtn.textContent='☰';
    page(b.dataset.page);
  });
});

/* Thanh truy cập dễ dàng */
document.getElementById('ciceroGlobalText').onclick=function(){
  const on=document.body.classList.toggle('cicero-global-large');
  this.setAttribute('aria-pressed',String(on));
};
document.getElementById('ciceroGlobalContrast').onclick=function(){
  const on=document.body.classList.toggle('cicero-global-contrast');
  this.setAttribute('aria-pressed',String(on));
};
document.getElementById('ciceroGlobalRead').onclick=()=>{
  const text=view?.innerText||'';
  if(text && 'speechSynthesis' in window){
    speechSynthesis.cancel();
    const u=new SpeechSynthesisUtterance(text.slice(0,5000));
    u.lang='vi-VN';
    speechSynthesis.speak(u);
  }
};
document.getElementById('ciceroGlobalStop').onclick=()=>speechSynthesis.cancel();

home();
</script>
</body>
</html>
