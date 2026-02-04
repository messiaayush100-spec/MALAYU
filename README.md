<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Will you be my Valentine? 💛</title>
  <style>
    :root{
      --cream:#fff6d8;
      --pink:#ffe3ef;
      --butter:#fffbe8;
      --card: rgba(255,255,255,0.82);
      --text:#2c1b07;
      --muted:#5a452e;
      --gold:#f4c430;
      --rose:#ff5a7a;
      --shadow: 0 18px 55px rgba(44,27,7,.16);
      --border: rgba(130,90,35,.14);
    }

    *{ box-sizing:border-box; }
    body{
      margin:0;
      min-height:100vh;
      font-family: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, "Apple Color Emoji","Segoe UI Emoji";
      color:var(--text);
      background:
        radial-gradient(1100px 650px at 12% 10%, rgba(244,196,48,.42), transparent 60%),
        radial-gradient(900px 650px at 88% 18%, rgba(255,90,122,.22), transparent 62%),
        radial-gradient(900px 800px at 55% 92%, rgba(34,197,94,.14), transparent 60%),
        linear-gradient(135deg, var(--cream), var(--pink), var(--butter));
      overflow-x:hidden;
    }

    /* floating yellow-rose vibes */
    .floaties{
      position:fixed; inset:0;
      pointer-events:none;
      z-index:0;
      opacity:.75;
    }
    .floater{
      position:absolute;
      animation: floatUp linear infinite;
      filter: drop-shadow(0 10px 18px rgba(44,27,7,.12));
      user-select:none;
    }
    @keyframes floatUp{
      from{ transform: translateY(25vh) translateX(0) rotate(0deg); opacity:0;}
      12%{opacity:1}
      to{ transform: translateY(-130vh) translateX(70px) rotate(25deg); opacity:0;}
    }

    .wrap{
      position:relative;
      z-index:1;
      min-height:100vh;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:26px 14px;
    }

    .card{
      width:min(980px, 100%);
      background:var(--card);
      border:1px solid var(--border);
      border-radius:26px;
      box-shadow: var(--shadow);
      overflow:hidden;
      backdrop-filter: blur(10px);
    }

    .topbar{
      display:flex;
      justify-content:space-between;
      align-items:center;
      padding:14px 18px;
      border-bottom:1px solid rgba(130,90,35,.12);
      background: linear-gradient(90deg, rgba(244,196,48,.16), rgba(255,90,122,.10));
    }
    .badge{
      display:inline-flex;
      align-items:center;
      gap:10px;
      padding:8px 12px;
      border-radius:999px;
      background: rgba(255,255,255,0.70);
      border:1px solid rgba(130,90,35,.14);
      font-size:13px;
      color:var(--muted);
      font-weight:650;
    }
    .tiny{ font-size:13px; color:var(--muted); }

    .content{
      display:grid;
      grid-template-columns: 1.1fr .9fr;
      gap:18px;
      padding:22px;
    }
    @media (max-width: 880px){
      .content{ grid-template-columns:1fr; }
    }

    .panel{
      padding:18px;
      border-radius:20px;
      border:1px solid rgba(130,90,35,.14);
      background: rgba(255,255,255,.70);
    }

    h1{
      margin:6px 0 10px;
      font-size: clamp(28px, 3.2vw, 42px);
      line-height:1.08;
      letter-spacing:-0.02em;
    }
    h2{
      margin:0 0 10px;
      font-size: clamp(20px, 2.3vw, 27px);
      letter-spacing:-0.01em;
    }
    p{
      margin:10px 0;
      font-size:15.7px;
      line-height:1.65;
      color:var(--muted);
    }
    .bigline{
      color:var(--text);
      font-weight:850;
    }
    .highlight{
      color:var(--rose);
      font-weight:900;
    }

    .miniCard{
      margin-top:14px;
      padding:14px 14px;
      border-radius:18px;
      border:1px dashed rgba(130,90,35,.22);
      background: rgba(255,255,255,.78);
      position:relative;
      overflow:hidden;
    }
    .miniCard:before{
      content:"🌼💛🌼💛🌼";
      position:absolute;
      top:10px;
      right:12px;
      font-size:14px;
      opacity:.55;
      letter-spacing:4px;
    }

    .playArea{
      position:relative;
      width:100%;
      min-height:170px;
      margin-top:10px;
    }

    .btnRow{
      display:flex;
      gap:14px;
      flex-wrap:wrap;
      align-items:center;
    }

    button{
      border:none;
      cursor:pointer;
      border-radius:14px;
      padding:12px 16px;
      font-weight:900;
      font-size:16px;
      transition: transform .12s ease, filter .12s ease;
      user-select:none;
      -webkit-tap-highlight-color: transparent;
    }
    button:active{ transform: scale(.98); }

    #yesBtn{
      background: linear-gradient(135deg, var(--gold), #ffe28a);
      color:#2b1b00;
      box-shadow: 0 16px 32px rgba(244,196,48,.28);
      transform-origin:center;
    }
    #noBtn{
      background: rgba(255,255,255,0.85);
      color:var(--text);
      border:1px solid rgba(130,90,35,.18);
    }

    #noWrap{
      position:absolute;
      left: 160px;
      top: 62px;
      display:inline-block;
    }

    .status{
      margin-top:10px;
      min-height:26px;
      font-size:14px;
      color: rgba(44,27,7,.75);
      font-weight:800;
    }
    .hint{
      margin-top:6px;
      font-size:13px;
      color: rgba(44,27,7,.62);
    }

    .page{ display:none; }
    .page.active{ display:block; }

    .photo{
      width:100%;
      max-width:360px;
      border-radius:20px;
      border:1px solid rgba(130,90,35,.16);
      box-shadow: 0 18px 50px rgba(44,27,7,.18);
      background: rgba(255,255,255,.55);
    }

    .letter{
      white-space:pre-line;
      font-size:15.7px;
      line-height:1.75;
      padding:14px;
      border-radius:16px;
      border:1px solid rgba(130,90,35,.14);
      background: rgba(255,255,255,.80);
      color: rgba(44,27,7,.84);
    }

    .footer{
      padding:16px 22px 22px;
      font-size:12.5px;
      color: rgba(44,27,7,.58);
      text-align:center;
    }

    /* music button */
    .musicBtn{
      position:fixed;
      right:16px;
      bottom:16px;
      z-index:10;
      padding:10px 14px;
      border-radius:999px;
      background: rgba(255,255,255,.82);
      border:1px solid rgba(130,90,35,.18);
      font-weight:900;
    }
  </style>
</head>

<body>
  <div class="floaties" id="floaties"></div>

  <!-- Background music (works if you upload song.mp3 next to index.html) -->
  <audio id="bgMusic" loop>
    <source src="song.mp3" type="audio/mpeg">
  </audio>
  <button class="musicBtn" id="musicBtn">▶️ Play music</button>

  <div class="wrap">
    <div class="card">
      <div class="topbar">
        <div class="badge">💛🌼 Valentine surprise for <b>Ranjita</b></div>
        <div class="tiny" id="dateLine"></div>
      </div>

      <!-- PAGE 1 -->
      <div class="page active" id="page1">
        <div class="content">
          <div class="panel">
            <h1>Hi Ranjita 💛</h1>
            <p class="bigline">
              I call you <span class="highlight">Mayalu</span>.
            </p>
            <p>
              I love talking to you. I don’t know why… but even from all this distance, I care for you.
            </p>

            <div class="miniCard">
              <h2>Will you be my Valentine? 🌼💛</h2>

              <div class="playArea" id="playArea">
                <div class="btnRow">
                  <button id="yesBtn">YES 😍🌼</button>
                  <span id="noWrap"><button id="noBtn">NO 🙄</button></span>
                </div>
              </div>

              <div class="status" id="status"></div>
              <div class="hint">Tip: “No” might be broken… by love 😌💛</div>
            </div>
          </div>

          <div class="panel">
            <h2>One small thing 💌</h2>
            <p>
              If the music doesn’t start automatically, tap the “Play music” button once.
              Phones usually block autoplay until the first tap.
            </p>
            <p class="bigline">Okay… now choose 😄💛</p>
          </div>
        </div>
      </div>

      <!-- PAGE 2 -->
      <div class="page" id="page2">
        <div class="content">
          <div class="panel">
            <h1>My Mayalu… 😭💛🌼</h1>
            <p class="bigline">You said YES… and my heart is smiling.</p>

            <div class="letter">
My Ranjita (my Mayalu) 💛,

I love talking to you.
I don’t even know why…
but from all this distance, I care for you — deeply.

You feel close even when you’re far.
And I don’t want to lose that feeling.

So I’m asking with my whole heart:
Will you be my Valentine, Mayalu? 🌼💛

Always yours,
— Aayush 🫶
            </div>

            <div class="btnRow" style="margin-top:14px;">
              <button id="flowersBtn">Give you flowers 🌼💛</button>
              <button id="backBtn" style="background:rgba(255,255,255,.85); border:1px solid rgba(130,90,35,.18);">Back</button>
            </div>
            <div class="status" id="status2"></div>
          </div>

          <div class="panel">
            <h2>Her photo 📸</h2>
            <img class="photo" alt="Ranjita" src="data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/7QCEUGhvdG9zaG9wIDMuMAA4QklNBAQAAAAAAGgcAigAYkZCTUQwMTAwMGU0MDI3MDAwMDA4MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAw
