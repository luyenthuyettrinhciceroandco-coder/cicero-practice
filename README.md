<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Cicero – Luyện thuyết trình</title>
<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<style>
:root{--mint:#bfe7e5;--mint2:#d8f0ec;--cream:#fffdf5;--deep:#246b58;--ink:#173c37;--line:#c7e2d8;--peach:#fff1e3}
*{box-sizing:border-box}
body{margin:0;color:var(--ink);font-family:Arial,Helvetica,sans-serif;background:repeating-linear-gradient(90deg,#c1e8e6 0px,#c1e8e6 27px,#d5efeb 27px,#d5efeb 55px);min-height:100vh}
.page{max-width:1080px;margin:24px auto;padding:clamp(12px,3vw,28px)}
.hero,.panel{background:rgba(255,253,245,.97);border:1px solid #d5e9df;border-radius:24px;box-shadow:0 8px 24px #315f5010;padding:clamp(16px,3vw,28px);margin-bottom:18px}
.hero{text-align:center}
.logo{font-size:clamp(30px,6vw,48px);font-weight:800;letter-spacing:.5px;color:var(--deep);margin:2px}
.subtitle{margin:8px auto 0;max-width:650px;line-height:1.6;color:#55766d}
h2{font-size:clamp(20px,3vw,26px);margin:0 0 14px}
h3{margin:0 0 10px}
label{display:block;font-weight:700;margin:12px 0 7px}
input,textarea,select{font:inherit;width:100%;border:1px solid var(--line);border-radius:13px;padding:13px 14px;background:white;color:var(--ink);min-height:46px}
textarea{min-height:110px;resize:vertical}
button{font:inherit;font-weight:700;border:0;border-radius:13px;padding:12px 17px;background:var(--deep);color:white;cursor:pointer;min-height:44px}
button.secondary{background:#e7f4ee;color:var(--deep);border:1px solid #d1e7dc}
button:disabled{opacity:.5;cursor:not-allowed}
.buttons{display:flex;gap:9px;flex-wrap:wrap;margin-top:12px}
.grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:18px}
.note{background:var(--peach);padding:13px 15px;border-radius:14px;line-height:1.5;margin-top:14px}
.muted{color:#638078;font-size:.94rem;line-height:1.5}
.camera-wrap{background:#e8f3ed;border-radius:18px;overflow:hidden;min-height:180px;display:flex;align-items:center;justify-content:center;position:relative}
video{width:100%;max-height:440px;object-fit:cover;display:block;transform:scaleX(-1)}
#handStatus{padding:10px 12px;background:#edf7f1;border-radius:12px;margin-top:10px;font-size:.95rem}
.question{font-size:1.15rem;font-weight:700;line-height:1.55;padding:18px;border:1px solid var(--line);border-radius:16px;background:#f5fbf6}
.score{font-size:34px;font-weight:800;color:var(--deep)}
.hidden{display:none!important}
.table-wrap{overflow:auto}
table{width:100%;border-collapse:collapse}
th,td{text-align:left;padding:11px 9px;border-bottom:1px solid #e1eee7}
small{color:#6b877d}
.status{margin-top:10px;font-size:.94rem;line-height:1.5;overflow-wrap:anywhere}
.section-heading{display:flex;align-items:flex-start;justify-content:space-between;gap:16px}
.section-heading h2{margin-bottom:6px}
.section-heading .muted{margin-top:0}
.admin-settings{margin:8px 0 22px}
.admin-settings details{background:rgba(255,253,245,.88);border:1px solid #d5e9df;border-radius:16px;padding:14px 18px;color:#55766d}
.admin-settings summary{cursor:pointer;font-weight:700;color:#246b58}
.admin-inner{padding-top:10px}
.admin-inner .note{margin-bottom:2px}
.modal-backdrop{position:fixed;inset:0;background:#173c3777;display:flex;align-items:center;justify-content:center;padding:18px;z-index:9999}
.modal-card{width:min(100%,420px);background:#fffdf5;border:2px solid #c7e2d8;border-radius:22px;padding:25px;text-align:center;box-shadow:0 18px 60px #173c3740;animation:popIn .18s ease-out}
.modal-card h2{color:#246b58;margin:0 0 10px}
.modal-card p{line-height:1.55}
.modal-card button{min-width:130px}
@keyframes popIn{from{transform:scale(.94);opacity:.4}to{transform:scale(1);opacity:1}}
@media(max-width:700px){
.page{margin:0 auto;padding:10px}
.hero,.panel{border-radius:18px;padding:16px}
.grid{grid-template-columns:1fr}
.buttons button{flex:1 1 130px}
input,textarea{font-size:16px}
.camera-wrap{min-height:210px}
.section-heading{flex-direction:column}
.section-heading button{width:100%}
.table-wrap table{min-width:480px}
}
</style>
</head>

<body>
<main class="page">

<header class="hero">
  <div class="logo">🌿 CICERO</div>
  <div class="subtitle">Không gian luyện thuyết trình — luyện tập, ghi hình, nhận phản hồi và rèn phản xạ trả lời câu hỏi.</div>
</header>

<section class="panel">
<h2>🎤 Bài luyện tập</h2>
<div class="grid">
<div>
  <label for="topic">Chủ đề thuyết trình</label>
  <input id="topic" placeholder="Ví dụ: Bảo vệ môi trường" value="Bảo vệ môi trường">

  <label for="minutes">Thời lượng mục tiêu (phút)</label>
  <input id="minutes" type="number" min="1" max="60" value="3">

  <label for="keywords">Từ khóa chính (ngăn cách bằng dấu phẩy)</label>
  <input id="keywords" placeholder="Ví dụ: rác thải, tái chế, cộng đồng">
</div>

<div>
  <label>Camera</label>
  <div class="camera-wrap">
    <video id="video" autoplay muted playsinline class="hidden"></video>
    <div id="cameraPlaceholder" class="muted">Camera chưa bật</div>
  </div>
  <div class="buttons">
    <button id="cameraBtn">Bật camera</button>
    <button id="handBtn" class="secondary">Bật nhận diện tay</button>
  </div>
  <div id="handStatus">Cử chỉ tay: chưa bật</div>
</div>
</div>

<div class="buttons">
  <button id="startBtn">Bắt đầu luyện tập</button>
  <button id="stopBtn" class="secondary" disabled>Kết thúc</button>
  <button id="micBtn" class="secondary">Bật micro nhận giọng nói</button>
</div>

<div class="status" id="timer">Thời gian: 00:00</div>
<p class="muted">Hãy cho phép camera/micro khi trình duyệt hỏi. Camera hoạt động trên HTTPS hoặc localhost. Nhận diện giọng nói phụ thuộc trình duyệt.</p>
</section>

<section class="panel">
<h2>📝 Bản ghi và chấm điểm</h2>
<label for="transcript">Nội dung thuyết trình</label>
<textarea id="transcript" placeholder="Nội dung nhận diện sẽ xuất hiện ở đây; bạn cũng có thể tự nhập hoặc sửa..."></textarea>
<div class="buttons">
  <button id="scoreBtn">Chấm điểm</button>
  <button id="clearBtn" class="secondary">Xóa nội dung</button>
</div>
<div id="feedback" class="note hidden"></div>
<div id="scoreResult" class="status"></div>
</section>

<section class="panel">
<h2>🎲 Câu hỏi phản xạ ngẫu nhiên</h2>
<p class="muted">Câu hỏi mẫu để luyện phản xạ theo chủ đề. Nhấn đổi câu để lấy câu khác.</p>
<div id="question" class="question">Nhấn “Lấy câu hỏi” để bắt đầu.</div>
<div class="buttons"><button id="newQuestion">🔀 Lấy câu hỏi / Đổi câu</button></div>
<label for="answer">Câu trả lời của bạn</label>
<textarea id="answer" placeholder="Nhập câu trả lời của bạn..."></textarea>
<div class="buttons"><button id="reviewAnswer">Nhận xét câu trả lời</button></div>
<div id="answerFeedback" class="note hidden"></div>
</section>

<section class="panel account-panel">
<h2>👤 Tài khoản học sinh</h2>
<p class="muted">Đăng nhập để lưu điểm luyện tập và tham gia bảng xếp hạng Cicero.</p>
<div class="grid">
  <div><label for="displayName">Tên hiển thị</label><input id="displayName" placeholder="Tên dùng trên BXH"></div>
  <div><label for="email">Email</label><input id="email" type="email" autocomplete="email" placeholder="ban@example.com"></div>
</div>
<label for="password">Mật khẩu</label>
<input id="password" type="password" autocomplete="current-password" placeholder="Ít nhất 6 ký tự">
<div class="buttons">
  <button id="signup">Đăng ký</button>
  <button id="signin" class="secondary">Đăng nhập</button>
  <button id="signout" class="secondary">Đăng xuất</button>
</div>
<div id="authStatus" class="status">Chưa kết nối Supabase.</div>
</section>

<section class="panel leaderboard-panel">
<div class="section-heading">
  <div><h2>🏆 Bảng xếp hạng Cicero</h2><p class="muted">Thành tích của học sinh đã đăng nhập và lưu điểm.</p></div>
  <button id="refreshBoard" class="secondary">↻ Làm mới</button>
</div>
<div class="table-wrap">
<table>
<thead><tr><th>Hạng</th><th>Học sinh</th><th>Điểm</th><th>Chủ đề</th></tr></thead>
<tbody id="board"><tr><td colspan="4">Đăng nhập để tải bảng xếp hạng.</td></tr></tbody>
</table>
</div>
</section>

<section class="admin-settings">
<details>
<summary>⚙️ Cài đặt kết nối (dành cho người quản lý)</summary>
<div class="admin-inner">
  <p class="muted">Chỉ người quản lý cần nhập thông tin Supabase một lần trên thiết bị này. Không nhập service_role/secret key.</p>
  <label for="supabaseUrl">Supabase Project URL</label>
  <input id="supabaseUrl" placeholder="https://xxxx.supabase.co">
  <label for="supabaseKey">Supabase publishable / anon key</label>
  <input id="supabaseKey" placeholder="sb_publishable_... hoặc anon public key">
  <div class="buttons">
    <button id="connect">Kết nối</button>
    <button id="disconnect" class="secondary">Ngắt kết nối</button>
  </div>
  <div class="note">Cần tạo project Supabase, bật Email Auth, tạo bảng public.scores và chính sách RLS trước khi BXH trực tuyến hoạt động. Điểm được tính ở trình duyệt nên chưa chống gian lận cho cuộc thi chính thức.</div>
</div>
</details>
</section>

<div id="timeModal" class="modal-backdrop hidden" role="dialog" aria-modal="true" aria-labelledby="timeModalTitle">
<div class="modal-card">
  <div style="font-size:38px;margin-bottom:8px">⏰</div>
  <h2 id="timeModalTitle">Bạn đã hết thời gian!</h2>
  <p id="timeModalMessage">Bài luyện tập đã tự động kết thúc và được chấm điểm.</p>
  <button id="closeTimeModal">Đã hiểu</button>
</div>
</div>

<footer class="muted" style="text-align:center;padding:10px">Cicero · Luyện tập để tự tin hơn 🌱</footer>
</main>

<script>
const $ = id => document.getElementById(id);

let stream = null;
let recorder = null;
let chunks = [];
let startedAt = 0;
let timerInt = null;
let recognition = null;
let recognitionOn = false;
let client = null;
let currentUser = null;
let handEnabled = false;
let handTimer = null;
let timedOut = false;

const questions = [
'Bạn sẽ đề xuất hành động cụ thể nào để giải quyết vấn đề này? Vì sao?',
'Bạn có ví dụ thực tế nào để chứng minh quan điểm của mình không?',
'Nếu có người không đồng ý với ý kiến của bạn, bạn sẽ phản hồi thế nào?',
'Điều gì là khó khăn lớn nhất khi thực hiện giải pháp bạn vừa nêu?',
'Bạn sẽ thuyết phục người nghe bằng lý lẽ hoặc bằng chứng nào?',
'Nếu chỉ có 30 giây để tóm tắt thông điệp chính, bạn sẽ nói gì?',
'Có quan điểm trái chiều nào cần xem xét trước khi kết luận không?',
'Làm thế nào để biết giải pháp của bạn thực sự hiệu quả?',
'Bạn rút ra bài học gì từ chủ đề này và áp dụng vào đời sống ra sao?',
'Nếu được làm lại phần trình bày, bạn sẽ cải thiện điều gì đầu tiên?'
];

let questionPool = [];

function setStatus(t) {
  $('authStatus').textContent = t;
}

function fmt(s) {
  return String(Math.floor(s / 60)).padStart(2, '0') + ':' +
         String(s % 60).padStart(2, '0');
}

/* CAMERA: chỉ xin quyền camera, không bắt buộc micro */
async function camera() {
  try {
    if (!navigator.mediaDevices || !navigator.mediaDevices.getUserMedia) {
      alert('Camera chưa được trình duyệt hỗ trợ. Hãy mở Cicero bằng Chrome qua đường dẫn HTTPS.');
      return;
    }

    stream = await navigator.mediaDevices.getUserMedia({
      video: { facingMode: 'user' },
      audio: false
    });

    $('video').srcObject = stream;
    $('video').classList.remove('hidden');
    $('cameraPlaceholder').classList.add('hidden');
    $('cameraBtn').textContent = 'Tắt camera';

    try {
      await $('video').play();
    } catch (e) {
      console.log('Không thể tự phát video:', e);
    }
  } catch (e) {
    alert('Không bật được camera. Hãy kiểm tra quyền camera của Chrome. Chi tiết: ' + e.message);
  }
}

$('cameraBtn').onclick = async () => {
  if (stream) {
    stream.getTracks().forEach(track => track.stop());
    stream = null;
    $('video').srcObject = null;
    $('video').classList.add('hidden');
    $('cameraPlaceholder').classList.remove('hidden');
    $('cameraBtn').textContent = 'Bật camera';
    stopHand();
  } else {
    await camera();
  }
};

function finishPractice(auto = false) {
  if (!$('stopBtn').disabled) {
    clearInterval(timerInt);
    $('timer').textContent = 'Thời gian: ' +
      fmt(Math.floor((Date.now() - startedAt) / 1000));
    $('startBtn').disabled = false;
    $('stopBtn').disabled = true;

    if (recorder && recorder.state !== 'inactive') {
      try { recorder.stop(); } catch (e) {}
    }

    stopSpeech();
  }

  if (auto) {
    timedOut = true;
    gradePresentation(true);
    $('timeModalMessage').textContent =
      'Bạn đã hết thời gian quy định. Cicero đã tự động kết thúc bài luyện tập và chấm điểm.';
    $('timeModal').classList.remove('hidden');
  }
}

$('startBtn').onclick = async () => {
  if (!stream) await camera();
  if (!stream) return;

  const mins = Math.max(1, Math.min(60, Number($('minutes').value) || 3));
  $('minutes').value = mins;
  timedOut = false;
  startedAt = Date.now();
  $('startBtn').disabled = true;
  $('stopBtn').disabled = false;

  const limitSeconds = mins * 60;
  clearInterval(timerInt);

  timerInt = setInterval(() => {
    const elapsed = Math.floor((Date.now() - startedAt) / 1000);
    $('timer').textContent = 'Thời gian: ' +
      fmt(Math.min(elapsed, limitSeconds)) + ' / ' + fmt(limitSeconds);

    if (elapsed >= limitSeconds) finishPractice(true);
  }, 250);

  /* Ghi hình nếu trình duyệt hỗ trợ MediaRecorder */
  try {
    chunks = [];
    if (window.MediaRecorder) {
      recorder = new MediaRecorder(stream);
      recorder.ondataavailable = e => {
        if (e.data && e.data.size) chunks.push(e.data);
      };
      recorder.start();
    }
  } catch (e) {
    console.warn('Không thể ghi hình trên trình duyệt này:', e);
  }

  await startSpeech();
};

$('stopBtn').onclick = () => finishPractice(false);
$('closeTimeModal').onclick = () => $('timeModal').classList.add('hidden');

$('timeModal').addEventListener('click', e => {
  if (e.target === $('timeModal')) $('timeModal').classList.add('hidden');
});

/* MICRO: xin quyền riêng, độc lập với camera */
async function startSpeech() {
  const SR = window.SpeechRecognition || window.webkitSpeechRecognition;

  if (!SR) {
    alert('Trình duyệt này chưa hỗ trợ nhận diện giọng nói. Hãy thử mở trực tiếp bằng Chrome. Bé vẫn có thể nhập nội dung bằng tay.');
    return;
  }

  try {
    if (!navigator.mediaDevices || !navigator.mediaDevices.getUserMedia) {
      alert('Không thể truy cập micro. Hãy mở Cicero bằng Chrome qua đường dẫn HTTPS.');
      return;
    }

    const micPermission = await navigator.mediaDevices.getUserMedia({
      audio: true
    });

    micPermission.getTracks().forEach(track => track.stop());

    recognition = new SR();
    recognition.lang = 'vi-VN';
    recognition.continuous = true;
    recognition.interimResults = true;

    recognition.onresult = e => {
      let out = '';
      for (let i = 0; i < e.results.length; i++) {
        out += e.results[i][0].transcript +
          (e.results[i].isFinal ? ' ' : '');
      }
      $('transcript').value = out;
    };

    recognition.onerror = e => {
      console.log('Lỗi nhận diện giọng nói:', e.error);

      if (e.error === 'not-allowed' || e.error === 'service-not-allowed') {
        alert('Micro chưa được cấp quyền. Hãy vào cài đặt trang web trong Chrome và cho phép Micro.');
      } else if (e.error === 'network') {
        alert('Nhận diện giọng nói gặp lỗi mạng. Hãy kiểm tra Internet rồi thử lại.');
      }
    };

    recognition.onend = () => {
      recognitionOn = false;
      $('micBtn').textContent = 'Bật micro nhận giọng nói';
    };

    recognition.start();
    recognitionOn = true;
    $('micBtn').textContent = 'Tắt nhận giọng nói';

  } catch (e) {
    alert('Không truy cập được micro. Hãy kiểm tra quyền micro của Chrome. Chi tiết: ' + e.message);
  }
}

function stopSpeech() {
  if (recognition && recognitionOn) {
    recognitionOn = false;
    try { recognition.stop(); } catch (e) {}
  }
  $('micBtn').textContent = 'Bật micro nhận giọng nói';
}

$('micBtn').onclick = () => {
  if (recognitionOn) {
    stopSpeech();
  } else {
    startSpeech();
  }
};

/* CHẤM ĐIỂM */
async function gradePresentation(auto = false) {
  const text = $('transcript').value.trim();

  if (!text && !auto) {
    alert('Hãy nói hoặc nhập nội dung trước khi chấm điểm.');
    return;
  }

  const words = text ? text.split(/\s+/).filter(Boolean) : [];
  const kw = $('keywords').value.split(',')
    .map(x => x.trim().toLowerCase()).filter(Boolean);
  const lower = text.toLowerCase();
  const found = kw.filter(k => lower.includes(k)).length;

  const score = text
    ? Math.max(20, Math.min(100, Math.round(
        35 + Math.min(words.length, 180) / 6 +
        (kw.length ? found / kw.length * 20 : 10) +
        (/[.!?]/.test(text) ? 5 : 0)
      )))
    : 0;

  $('feedback').classList.remove('hidden');
  $('feedback').innerHTML =
    '<b>Điểm tham khảo: ' + score + '/100</b><br>' +
    '• Độ dài bản nói: ' + words.length + ' từ.<br>' +
    '• Từ khóa đã đề cập: ' + found + '/' + kw.length + '.<br>' +
    '• ' + (text
      ? 'Gợi ý: nêu luận điểm rõ, thêm ví dụ cụ thể và kết luận ngắn gọn.'
      : 'Chưa ghi nhận được nội dung lời nói; hãy kiểm tra quyền micro hoặc nhập bản nói.');

  $('scoreResult').innerHTML =
    '<div class="score">' + score + '/100</div>' +
    '<p class="muted">Đây là điểm tham khảo tự động dựa trên độ dài và từ khóa, không phải đánh giá chuyên sâu bằng AI.</p>' +
    (auto ? '<p><b>Trạng thái:</b> Tự động chấm khi hết thời gian.</p>' : '');

  window.lastScore = score;
  window.lastTopic = $('topic').value.trim() || 'Chưa đặt chủ đề';

  if (client && currentUser && text) {
    await saveScore(score, window.lastTopic);
  }
}

$('scoreBtn').onclick = () => gradePresentation(false);

$('clearBtn').onclick = () => {
  $('transcript').value = '';
  $('feedback').classList.add('hidden');
  $('scoreResult').textContent = '';
};

/* CÂU HỎI PHẢN XẠ */
function nextQuestion() {
  if (!questionPool.length) questionPool = questions.slice();
  const i = Math.floor(Math.random() * questionPool.length);
  $('question').textContent = questionPool.splice(i, 1)[0];
  $('answer').value = '';
  $('answerFeedback').classList.add('hidden');
}

$('newQuestion').onclick = nextQuestion;

$('reviewAnswer').onclick = () => {
  const a = $('answer').value.trim();

  if (!a) {
    alert('Nhập câu trả lời trước.');
    return;
  }

  const words = a.split(/\s+/).filter(Boolean).length;
  const hasWhy = /vì|bởi|do|nên|bởi vì/i.test(a);
  const hasExample = /ví dụ|chẳng hạn|như là/i.test(a);

  $('answerFeedback').classList.remove('hidden');
  $('answerFeedback').innerHTML =
    '<b>Gợi ý nhận xét</b><br>' +
    '• Độ dài: ' + words + ' từ.<br>' +
    '• ' + (hasWhy ? 'Đã có dấu hiệu giải thích lý do.' : 'Nên giải thích rõ vì sao bạn nghĩ như vậy.') + '<br>' +
    '• ' + (hasExample ? 'Đã có dấu hiệu đưa ví dụ.' : 'Hãy bổ sung một ví dụ cụ thể.') + '<br>' +
    '• Kết thúc bằng một kết luận hoặc giải pháp rõ ràng.';
};

/* SUPABASE */
function connect() {
  const url = $('supabaseUrl').value.trim();
  const key = $('supabaseKey').value.trim();

  if (!url || !key) {
    setStatus('Nhập Project URL và publishable/anon key trước.');
    return;
  }

  try {
    client = window.supabase.createClient(url, key);
    localStorage.setItem('cicero_supabase_url', url);
    localStorage.setItem('cicero_supabase_key', key);
    setStatus('Đã khởi tạo kết nối. Hãy đăng nhập để kiểm tra và xem BXH.');
  } catch (e) {
    setStatus('Không kết nối được: ' + e.message);
  }
}

$('connect').onclick = connect;

$('disconnect').onclick = () => {
  client = null;
  currentUser = null;
  setStatus('Đã ngắt kết nối.');
  $('board').innerHTML =
    '<tr><td colspan="4">Đăng nhập để tải bảng xếp hạng.</td></tr>';
};

try {
  const u = localStorage.getItem('cicero_supabase_url');
  const k = localStorage.getItem('cicero_supabase_key');

  if (u && k) {
    $('supabaseUrl').value = u;
    $('supabaseKey').value = k;
    connect();
  }
} catch (e) {}

async function signup() {
  if (!client)
Đã gửi
Soạn
Viết cho Shi Shu


