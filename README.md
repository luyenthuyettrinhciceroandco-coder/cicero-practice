
async function camera() {
  if (!navigator.mediaDevices?.getUserMedia) {
    alert('Trình duyệt không hỗ trợ camera/micro. Hãy mở Cicero trực tiếp bằng Chrome qua HTTPS.');
    return;
  }

  try {
    // Bật camera riêng
    const videoStream = await navigator.mediaDevices.getUserMedia({
      video: { facingMode: 'user' },
      audio: false
    });

    stream = videoStream;
    $('video').srcObject = stream;
    $('video').classList.remove('hidden');
    $('cameraPlaceholder').classList.add('hidden');
    $('cameraBtn').textContent = 'Tắt camera';

    // Xin quyền micro riêng
    try {
      const audioStream = await navigator.mediaDevices.getUserMedia({
        video: false,
        audio: true
      });

      audioStream.getAudioTracks().forEach(track => {
        stream.addTrack(track);
      });

      console.log('Camera và micro đã sẵn sàng.');
    } catch (audioError) {
      console.error('Lỗi micro:', audioError);
      alert('Camera đã bật nhưng micro chưa truy cập được. Hãy kiểm tra quyền Micro của Cicero trong Chrome.');
    }
  } catch (error) {
    console.error('Lỗi camera:', error);
    alert('Không mở được camera: ' + error.name + '. Hãy kiểm tra quyền Máy ảnh.');
  }
}
