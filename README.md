# Aadi-git1-
This is my first git repository 
<br>
Author - Aaditya
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Platformer Adventure — Playable Demo</title>
  <style>
    :root {
      color-scheme: light;
      color: #111;
      background: #eef7ff;
      font-family: Inter, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      --text-primary: #111;
      --text-secondary: #4f5b72;
      --text-muted: #5c677d;
      --bg-panel: #ffffff;
      --border: #d8e2ef;
      --shadow: 0 22px 40px rgba(40, 70, 140, 0.08);
      --radius: 22px;
      --accent: #2563eb;
    }
    * { box-sizing: border-box; }
    body { margin: 0; min-height: 100vh; background: linear-gradient(180deg,#eaf4ff 0%,#f8fbff 100%); color: var(--text-primary); }
    body, button { font: 16px Inter, system-ui, sans-serif; }
    .page { max-width: 960px; margin: 0 auto; padding: 28px 24px 42px; }
    header { margin-bottom: 24px; }
    h1 { margin: 0 0 12px; font-size: clamp(2rem, 4vw, 3rem); line-height: 1.05; }
    p.lead { margin: 0; color: var(--text-secondary); max-width: 40rem; }
    .card { background: var(--bg-panel); border: 1px solid var(--border); border-radius: var(--radius); box-shadow: var(--shadow); padding: 24px; }
    .game-panel { margin-top: 24px; }
    .game-header { display: flex; flex-wrap: wrap; align-items: center; justify-content: space-between; gap: 16px; margin-bottom: 18px; }
    .game-header p { margin: 0; color: var(--text-secondary); }
    .controls { display:flex; flex-wrap: wrap; gap: 10px; }
    .game-btn { border: none; background: #f4f8ff; color: var(--text-primary); padding: 12px 18px; border-radius: 14px; cursor: pointer; transition: transform .2s ease, background .2s ease; }
    .game-btn:hover { transform: translateY(-1px); background: #eff6ff; }
    .resume-link { display:inline-flex; align-items:center; gap:8px; text-decoration:none; background:#2563eb; color:#fff; padding:12px 18px; border-radius:14px; margin-top:16px; }
    .resume-link:hover { background:#1d4ed8; }
    canvas { width:100%; max-width:640px; display:block; border-radius:20px; margin: 0 auto; background:#cfe8fa; }
    .note { margin: 18px 0 0; color: var(--text-muted); font-size: 0.95rem; }
    .project-info { margin-top: 24px; display: grid; gap: 18px; }
    .project-info li { margin-bottom: 8px; }
    footer { margin-top: 40px; color: var(--text-muted); font-size: 0.95rem; }
    .visually-hidden { position:absolute;width:1px;height:1px;padding:0;margin:-1px;overflow:hidden;clip:rect(0,0,0,0);white-space:nowrap;border:0; }
  </style>
</head>
<body>
  <div class="page">
    <header>
      <h1>Platformer Adventure</h1>
      <p class="lead">A playable HTML5 platformer demo you can add to your resume or portfolio. Use this page as a static project showcase and publish it to GitHub Pages, Netlify, or any static host.</p>
      <a class="resume-link" href="https://<your-username>.github.io/<repo>/" target="_blank" rel="noreferrer">Replace with your live link</a>
    </header>

    <section class="card">
      <div class="game-header">
        <div>
          <strong>Playable demo</strong>
          <p>Use keyboard controls or the on-screen buttons below.</p>
        </div>
        <div class="controls">
          <button class="game-btn" disabled>← Left</button>
          <button class="game-btn" disabled>→ Right</button>
          <button class="game-btn" disabled>↑ Jump</button>
        </div>
      </div>
      <div class="game-panel">
        <h2 class="visually-hidden">Game area</h2>
        <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:10px;">
          <div style="display:flex;gap:18px;align-items:center;">
            <div style="font-size:14px;color:var(--text-secondary);">Score <span id="score" style="font-weight:500;color:var(--text-primary);margin-left:4px;">0</span></div>
            <div id="lives" style="display:flex;align-items:center;gap:2px;"></div>
          </div>
          <button id="btn-restart" class="game-btn" style="min-width:auto;min-height:auto;padding:8px 12px;" aria-label="Restart game">Restart</button>
        </div>
        <canvas id="game" width="640" height="360"></canvas>
        <div id="banner" style="text-align:center;margin-top:10px;font-size:15px;font-weight:500;min-height:20px;"></div>
        <div class="pad-row" style="display:flex;align-items:center;justify-content:space-between;margin-top:14px; gap:12px; flex-wrap: wrap;">
          <div class="pad-group" style="display:flex;gap:10px;">
            <button id="btn-left" class="game-btn" aria-label="Move left">Left</button>
            <button id="btn-right" class="game-btn" aria-label="Move right">Right</button>
          </div>
          <button id="btn-jump" class="game-btn" aria-label="Jump" style="min-width:100px;">Jump</button>
        </div>
        <p class="note">Arrow keys or WASD to move, space or up to jump — or use the buttons above.</p>
      </div>
    </section>

    <section class="project-info card">
      <h2>Project details</h2>
      <ul>
        <li>Built with vanilla HTML, CSS, and JavaScript.</li>
        <li>Includes player movement, platform collision, coins, enemies, and a finish goal.</li>
        <li>Designed to be hosted as a static website.</li>
      </ul>
      <p class="note">To publish this as a live URL, push this folder to a GitHub repository and enable GitHub Pages.</p>
    </section>

    <footer>
      <p>Note: Replace the demo link above with your actual GitHub Pages or static-host URL once deployed.</p>
    </footer>
  </div>

  <script>
  (function(){
    const canvas = document.getElementById('game');
    const ctx = canvas.getContext('2d');
    const scoreEl = document.getElementById('score');
    const livesEl = document.getElementById('lives');
    const bannerEl = document.getElementById('banner');
    const LW = 640, LH = 360;
    const GRAVITY = 0.55, JUMP_VEL = -10.4, MOVE_SPEED = 3.4, MAX_FALL = 11;
    const GROUND_Y = 304;
    const WORLD_W = 2720;
    const GOAL_X = 2620;

    const platforms = [
      {x:0,y:GROUND_Y,w:440,h:56},
      {x:540,y:GROUND_Y,w:300,h:56},
      {x:940,y:GROUND_Y,w:340,h:56},
      {x:1380,y:GROUND_Y,w:300,h:56},
      {x:1780,y:GROUND_Y,w:940,h:56},
      {x:140,y:230,w:80,h:16},
      {x:650,y:220,w:80,h:16},
      {x:1420,y:230,w:90,h:16},
      {x:1950,y:230,w:90,h:16},
      {x:2300,y:230,w:90,h:16}
    ];

    const enemyDefs = [
      {x:600,min:560,max:780},
      {x:1000,min:960,max:1220},
      {x:1450,min:1400,max:1620},
      {x:1850,min:1800,max:2050},
      {x:2400,min:2350,max:2600}
    ];

    let coins, enemies, player, camX, keys, frame;

    function buildCoins(){
      const c = [];
      [[40,420],[560,820],[960,1260],[1400,1660],[1800,2600]].forEach(function(seg){
        for(let x=seg[0]; x<seg[1]; x+=70) c.push({x:x, y:GROUND_Y-40, r:9, got:false});
      });
      [140,650,1420,1950,2300].forEach(function(px){
        c.push({x:px+15, y:200, r:9, got:false});
        c.push({x:px+45, y:200, r:9, got:false});
      });
      return c;
    }

    function rectsOverlap(a,b){
      return a.x < b.x+b.w && a.x+a.w > b.x && a.y < b.y+b.h && a.y+a.h > b.y;
    }

    function updateHud(){
      scoreEl.textContent = player.score;
      let hearts = '';
      for(let i=0;i<Math.max(player.lives,0);i++){
        hearts += '♥';
      }
      livesEl.textContent = hearts;
    }

    function respawnSafe(){
      let target = null;
      for(const p of platforms){
        if(p.h >= 50 && p.x + p.w <= player.x + player.w){
          if(!target || p.x > target.x) target = p;
        }
      }
      if(target){
        player.x = target.x + 10;
        player.y = target.y - player.h;
      } else {
        player.x = 30;
        player.y = GROUND_Y - player.h;
      }
      player.vx = 0; player.vy = 0;
    }

    function loseLife(){
      player.lives--;
      player.invuln = 60;
      if(player.lives <= 0){
        player.dead = true;
        bannerEl.textContent = 'Game over — tap restart to try again';
        bannerEl.style.color = '#dc2626';
      } else {
        respawnSafe();
      }
      updateHud();
    }

    function reset(){
      coins = buildCoins();
      enemies = enemyDefs.map(function(e){ return {x:e.x,y:GROUND_Y-22,w:30,h:22,min:e.min,max:e.max,dir:1,alive:true}; });
      player = {x:30,y:GROUND_Y-40,w:26,h:40,vx:0,vy:0,grounded:false,facing:1,lives:3,score:0,invuln:0,dist:0,dead:false,won:false};
      camX = 0;
      keys = {left:false,right:false,jumpQ:false};
      frame = 0;
      bannerEl.textContent = '';
      bannerEl.style.color = '#334155';
      updateHud();
    }

    function fit(){
      const w = canvas.clientWidth || LW;
      const h = Math.round(w * LH / LW);
      canvas.style.height = h + 'px';
      const dpr = window.devicePixelRatio || 1;
      canvas.width = Math.round(w * dpr);
      canvas.height = Math.round(h * dpr);
      ctx.setTransform((w*dpr)/LW, 0, 0, (h*dpr)/LH, 0, 0);
    }

    window.addEventListener('resize', fit);
    window.addEventListener('keydown', function(e){
      if(e.key==='ArrowLeft'||e.key==='a'||e.key==='A') keys.left = true;
      if(e.key==='ArrowRight'||e.key==='d'||e.key==='D') keys.right = true;
      if((e.key===' '||e.key==='ArrowUp'||e.key==='w'||e.key==='W') && !e.repeat) keys.jumpQ = true;
      if(['ArrowLeft','ArrowRight','ArrowUp',' '].indexOf(e.key) !== -1) e.preventDefault();
    });
    window.addEventListener('keyup', function(e){
      if(e.key==='ArrowLeft'||e.key==='a'||e.key==='A') keys.left = false;
      if(e.key==='ArrowRight'||e.key==='d'||e.key==='D') keys.right = false;
    });

    function bindHold(id, on, off){
      const el = document.getElementById(id);
      el.addEventListener('pointerdown', function(e){ e.preventDefault(); on(); });
      el.addEventListener('pointerup', off);
      el.addEventListener('pointerleave', off);
      el.addEventListener('pointercancel', off);
    }
    bindHold('btn-left', function(){keys.left=true;}, function(){keys.left=false;});
    bindHold('btn-right', function(){keys.right=true;}, function(){keys.right=false;});
    document.getElementById('btn-jump').addEventListener('pointerdown', function(e){ e.preventDefault(); keys.jumpQ = true; });
    document.getElementById('btn-restart').addEventListener('click', reset);

    function update(){
      if(player.won || player.dead) return;
      frame++;

      const targetVx = keys.left ? -MOVE_SPEED : (keys.right ? MOVE_SPEED : 0);
      player.vx += (targetVx - player.vx) * 0.35;
      if(Math.abs(player.vx) < 0.05) player.vx = 0;
      if(player.vx > 0.1) player.facing = 1;
      if(player.vx < -0.1) player.facing = -1;
      player.dist += Math.abs(player.vx);

      if(keys.jumpQ){
        if(player.grounded){
          player.vy = JUMP_VEL;
          player.grounded = false;
        }
        keys.jumpQ = false;
      }

      player.vy = Math.min(player.vy + GRAVITY, MAX_FALL);

      player.x += player.vx;
      player.x = Math.max(0, Math.min(player.x, WORLD_W - player.w));
      for(const p of platforms){
        if(rectsOverlap(player, p)){
          if(player.vx > 0) player.x = p.x - player.w;
          else if(player.vx < 0) player.x = p.x + p.w;
        }
      }

      player.y += player.vy;
      player.grounded = false;
      for(const p of platforms){
        if(rectsOverlap(player, p)){
          if(player.vy > 0){ player.y = p.y - player.h; player.vy = 0; player.grounded = true; }
          else if(player.vy < 0){ player.y = p.y + p.h; player.vy = 0; }
        }
      }

      if(player.y > LH + 100) loseLife();
      if(player.invuln > 0) player.invuln--;

      for(const c of coins){
        if(!c.got && Math.abs((player.x+player.w/2)-c.x) < 22 && Math.abs((player.y+player.h/2)-c.y) < 24){
          c.got = true;
          player.score += 10;
        }
      }

      for(const en of enemies){
        if(!en.alive) continue;
        en.x += en.dir * 1.1;
        if(en.x < en.min || en.x > en.max) en.dir *= -1;
        if(rectsOverlap(player, en)){
          const stomp = player.vy > 0 && (player.y + player.h) - en.y < 16;
          if(stomp){
            en.alive = false;
            player.vy = JUMP_VEL * 0.55;
            player.score += 50;
          } else if(player.invuln <= 0){
            player.lives--;
            player.invuln = 70;
            player.vx = -player.facing * 4;
            player.vy = -7;
            if(player.lives <= 0){
              player.dead = true;
              bannerEl.textContent = 'Game over — tap restart to try again';
              bannerEl.style.color = '#dc2626';
            }
          }
        }
      }

      if(!player.dead && player.x + player.w >= GOAL_X){
        player.won = true;
        bannerEl.textContent = 'You reached the flag — score ' + player.score;
        bannerEl.style.color = '#16a34a';
      }

      camX = Math.max(0, Math.min(player.x - LW/2, WORLD_W - LW));
      updateHud();
    }

    function drawBackground(){
      ctx.fillStyle = '#cfe8fa';
      ctx.fillRect(0,0,LW,LH);

      ctx.fillStyle = '#ffffff';
      const cloudOffset = camX * 0.2;
      for(let i=-1;i<4;i++){
        const baseX = i*220 - (cloudOffset % 220);
        ctx.beginPath(); ctx.ellipse(baseX+60,50,26,16,0,0,Math.PI*2); ctx.fill();
        ctx.beginPath(); ctx.ellipse(baseX+95,62,18,12,0,0,Math.PI*2); ctx.fill();
      }

      ctx.fillStyle = '#C0DD97';
      const hillOffset = camX * 0.45;
      for(let i=-1;i<5;i++){
        const baseX = i*260 - (hillOffset % 260);
        ctx.beginPath();
        ctx.ellipse(baseX+130, GROUND_Y+10, 150, 60, 0, 0, Math.PI*2);
        ctx.fill();
      }
    }

    function drawPlatform(p){
      const x = p.x - camX, y = p.y;
      if(x + p.w < 0 || x > LW) return;
      if(p.h >= 50){
        ctx.fillStyle = '#633806';
        ctx.fillRect(x, y+10, p.w, p.h-10);
        ctx.fillStyle = '#639922';
        ctx.fillRect(x, y, p.w, 12);
      } else {
        ctx.fillStyle = '#5F5E5A';
        ctx.fillRect(x, y, p.w, p.h);
        ctx.fillStyle = '#888780';
        ctx.fillRect(x, y, p.w, 4);
      }
    }

    function drawGoal(){
      const x = GOAL_X - camX;
      if(x < -50 || x > LW + 50) return;
      ctx.fillStyle = '#5F5E5A';
      ctx.fillRect(x-2, GROUND_Y-150, 4, 150);
      ctx.fillStyle = player.won ? '#1D9E75' : '#D4537E';
      ctx.beginPath();
      ctx.moveTo(x+2, GROUND_Y-150);
      ctx.lineTo(x+34, GROUND_Y-138);
      ctx.lineTo(x+2, GROUND_Y-126);
      ctx.closePath();
      ctx.fill();
    }

    function drawCoin(c){
      if(c.got) return;
      const cx = c.x - camX, cy = c.y;
      if(cx < -20 || cx > LW+20) return;
      const spin = Math.abs(Math.cos(frame*0.08 + c.x));
      ctx.save();
      ctx.translate(cx, cy);
      ctx.scale(0.3 + spin*0.7, 1);
      ctx.fillStyle = '#FAC775';
      ctx.beginPath(); ctx.arc(0,0,c.r,0,Math.PI*2); ctx.fill();
      ctx.strokeStyle = '#854F0B';
      ctx.lineWidth = 1.5;
      ctx.stroke();
      ctx.restore();
    }

    function drawEnemy(en){
      if(!en.alive) return;
      const ex = en.x - camX + en.w/2, ey = en.y + en.h/2;
      if(ex < -20 || ex > LW+20) return;
      const squash = 1 + Math.sin(frame*0.15 + en.x)*0.08;
      ctx.save();
      ctx.translate(ex, ey);
      ctx.scale(squash, 1/squash);
      ctx.fillStyle = '#EF9F27';
      ctx.beginPath();
      ctx.ellipse(0,2,15,11,0,0,Math.PI*2);
      ctx.fill();
      ctx.fillStyle = '#412402';
      ctx.beginPath(); ctx.arc(-5,-1,1.8,0,Math.PI*2); ctx.arc(5,-1,1.8,0,Math.PI*2); ctx.fill();
      ctx.restore();
    }

    function drawPlayer(){
      const px = player.x - camX + player.w/2;
      const py = player.y + player.h/2;
      ctx.save();
      ctx.translate(px, py);
      if(player.facing < 0) ctx.scale(-1,1);
      if(player.invuln > 0 && frame % 10 < 5) ctx.globalAlpha = 0.35;

      const moving = player.grounded && Math.abs(player.vx) > 0.3;
      const legSwing = moving ? Math.sin(player.dist * 0.4) * 6 : 0;
      const airTuck = !player.grounded ? 4 : 0;

      ctx.fillStyle = '#2C2C2A';
      ctx.fillRect(-9 + legSwing*0.4, 12 - airTuck, 7, 9 + airTuck);
      ctx.fillRect(2 - legSwing*0.4, 12 - airTuck, 7, 9 + airTuck);

      ctx.fillStyle = '#0F6E56';
      ctx.beginPath();
      ctx.moveTo(-11,-2);
      ctx.lineTo(11,-2);
      ctx.lineTo(9,14);
      ctx.lineTo(-9,14);
      ctx.closePath();
      ctx.fill();

      ctx.fillStyle = '#FAEEDA';
      ctx.beginPath();
      ctx.arc(0,-12,9,0,Math.PI*2);
      ctx.fill();

      ctx.fillStyle = '#412402';
      ctx.beginPath(); ctx.arc(4,-12,1.6,0,Math.PI*2); ctx.fill();

      ctx.fillStyle = '#D85A30';
      ctx.beginPath();
      ctx.moveTo(-9,-22);
      ctx.lineTo(9,-22);
      ctx.lineTo(13,-18);
      ctx.lineTo(-9,-18);
      ctx.closePath();
      ctx.fill();

      ctx.restore();
      ctx.globalAlpha = 1;
    }

    function draw(){
      drawBackground();
      for(const p of platforms) drawPlatform(p);
      drawGoal();
      for(const c of coins) drawCoin(c);
      for(const en of enemies) drawEnemy(en);
      drawPlayer();
    }

    function loop(){
      update();
      draw();
      requestAnimationFrame(loop);
    }

    reset();
    fit();
    requestAnimationFrame(loop);
  })();
  </script>
</body>
</html>
