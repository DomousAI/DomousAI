**DomousAI/DomousAI**<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Music Load</title>
  <style>
    body {margin:0;padding:20px;background:#000;color:#0f0;font-family:Arial;}
    h2 {margin:0 0 15px;text-align:center;}
    button {width:100%;padding:15px;margin:8px 0;border:none;border-radius:8px;font-size:18px;cursor:pointer;}
    #rec {background:#c00;}
    #stop {background:#080;display:none;}
    #play {background:#008;}
    audio {width:100%;margin-top:15px;}
  </style>
</head>
<body>
  <h2>🌌 Music Load 🌌</h2>
  <button id="rec">🔴 RECORD</button>
  <button id="stop">🟢 STOP</button>
  <button id="play">🔵 PLAY</button>
  <audio id="out" controls></audio>

  <script>
    let rec, stream, chunks = [];
    const beep = () => new Audio("data:audio/wav;base/lomlmaamgdjplnhhgnoajlbnlgnpkobl();

    document.getElementById('rec').onclick = async () => {
      stream = await navigator.mediaDevices.getUserMedia({audio:true});
      rec = new MediaRecorder(stream);
      rec.ondataavailable = e => chunks.push(e.data);
      rec.onstop = () => {
        const blob = new Blob(chunks, {type:'audio/webm'});
        const url = URL.createObjectURL(blob);
        document.getElementById('out').src = url;
        document.getElementById('play').disabled = false;
        chunks = [];
      };
      rec.start();
      beep();
      document.getElementById('rec').style.display='none';
      document.getElementById('stop').style.display='block';
    };

    document.getElementById('stop').onclick = () => {
      rec.stop();
      stream.getTracks().forEach(t => t.stop());
      beep();
      document.getElementById('stop').style.display='none';
      document.getElementById('rec').style.display='block';
    };
  </script>
</body>
</html>
