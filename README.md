<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Will you be my Valentine?</title>

  <style>
    body{
      margin:0;
      min-height:100vh;
      display:flex;
      flex-direction:column;
      align-items:center;
      justify-content:center;
      font-family: system-ui, -apple-system, Arial, sans-serif;
      background:white;
      text-align:center;
      padding:20px;
    }

    h1{
      font-size:1.8rem;
      margin:16px 0;
    }

    #photo{
      max-width:320px;
      width:100%;
      border-radius:12px;
      margin-bottom:12px;
    }

    .buttons{
      display:flex;
      gap:16px;
      margin-top:12px;
    }

    button{
      font-size:1.1rem;
      padding:12px 20px;
      border-radius:999px;
      border:none;
      cursor:pointer;
      font-weight:700;
    }

    #yes{
      background:#ff3b7a;
      color:white;
    }

    #no{
      background:#e5e7eb;
      color:#111;
      transition:transform .15s ease;
    }

    #message{
      margin-top:16px;
      font-weight:600;
      min-height:48px;
    }
  </style>
</head>

<body>

  <img id="photo" src="start.jpg" alt="valentine" />

  <h1 id="title">Will you be my Valentine?</h1>

  <div class="buttons">
    <button id="yes">Yes ❤️</button>
    <button id="no">No 🙃</button>
  </div>

  <div id="message"></div>

  <script>
    const photo = document.getElementById("photo");
    const yes = document.getElementById("yes");
    const no = document.getElementById("no");
    const message = document.getElementById("message");

    let noCount = 0;

    const memes = [
      { src: "meme1.jpg", text: "You sure about that?" },
      { src: "meme2.gif", text: "Are you REALLY sure?" },
      { src: "meme3.jpg", text: "You sure abt that bud?" },
      { src: "meme4.gif", text: "Last chance." }
    ];

    no.addEventListener("click", () => {
      noCount++;

      // Change meme
      const pick = memes[Math.min(noCount - 1, memes.length - 1)];
      photo.src = pick.src;
      message.textContent = pick.text;

      // Shrink button
      const scale = Math.max(0.3, 1 - noCount * 0.2);
      no.style.transform = `scale(${scale})`;

      // FINAL: disable No completely
      if (noCount >= memes.length) {
        no.disabled = true;
        no.style.cursor = "not-allowed";
        no.style.opacity = 0.4;
        message.textContent = "No is no longer an option 😌";
      }
    });

    yes.addEventListener("click", () => {
      photo.src = "yay.gif";
      message.innerHTML = `
        YAY 😭💖<br>
        Dinner + movie night?<br>
        <strong>Sunday, Feb 15th • 7:00 PM</strong>
      `;
      no.style.display = "none";
      yes.textContent = "Date confirmed ✅";
      yes.disabled = true;
    });
  </script>

</body>
</html>
