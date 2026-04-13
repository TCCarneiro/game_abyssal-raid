<h1 align="center">⚔️ Abyssal Raid</h1>
<p align="center">
  A browser-based 3D dungeon crawler where you pick a starting build, raid a procedurally generated forest, and stack powerups until your character is an absolute nightmare.
</p>
<hr>
 
<h2>📖 Overview</h2>
<p>
You are a raider. The forest wants you dead.
</p>
<p>
<strong>Abyssal Raid</strong> is a roguelite dungeon crawler built entirely in the browser using Three.js. Pick a starting combat seed, raid one of four increasingly hostile forest zones, and keep stacking powerups every level until you're simultaneously slashing, shooting fireballs, spawning holy rings, and firing laser beams — all at once.
</p>
<p>
Find the portal. Escape. Keep your loot. Come back stronger.
</p>
<p>
Or die and lose everything except your gear. That works too.
</p>
 
<h2>🎮 Gameplay</h2>
<ul>
  <li><strong>Pick a Seed</strong>, choose Blade, Shadow, Arcane, or Divine as your starting attack style. Everything else is built from there.</li>
  <li><strong>WASD to move</strong>, Space to jump, Shift to dash.</li>
  <li><strong>Auto-attack</strong>, your character targets and hits the nearest enemy in range automatically.</li>
  <li><strong>Level up mid-raid</strong>, choose one of three random powerups each level. Stack attack types on top of each other until the screen is chaos.</li>
  <li><strong>Collect XP gems</strong>, enemies drop glowing gems you walk over to collect. The magnet powerup pulls them to you from further away.</li>
  <li><strong>Find the portal</strong>, it spawns after 50 kills or when you defeat a boss. Step through to escape with your loot.</li>
  <li><strong>Die and try again</strong>, session stats reset but your equipment carries over.</li>
</ul>
 
<h2>🌲 The Four Raid Zones</h2>
<table>
  <thead>
    <tr>
      <th>Zone</th>
      <th>Vibe</th>
      <th>Danger</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Whisperwood</td><td>Bright green ancient forest</td><td>⚔ Low</td></tr>
    <tr><td>Rotwood Hollow</td><td>Fungal, sickly, glowing mushrooms</td><td>⚔⚔ Medium</td></tr>
    <tr><td>Moonveil Thicket</td><td>Dead branches, purple moonlight</td><td>⚔⚔⚔ High</td></tr>
    <tr><td>Ashfire Grove</td><td>Burning embers, choking ash</td><td>⚔⚔⚔⚔ Brutal</td></tr>
  </tbody>
</table>
<p>
Each zone has different fog density, lighting colour, enemy scaling, and a doom meter that fills over time — when it maxes out, you take constant damage until you either escape or die.
</p>
 
<h2>⚡ Attack System</h2>
<p>
Start with your seed's base attack. Every level you can add new attack layers on top:
</p>
<ul>
  <li><strong>⚔ Slash</strong> — instant arc strike, close range</li>
  <li><strong>🔪 Fan</strong> — spread of blades in a wide arc</li>
  <li><strong>🔥 Fireball</strong> — homing projectile with explosion</li>
  <li><strong>✨ Holy Ring</strong> — expanding pulse that damages everything in radius</li>
  <li><strong>🌀 Orbiting Blades</strong> — rotate around you and hit enemies automatically</li>
  <li><strong>⚡ Beam</strong> — piercing laser through multiple enemies</li>
  <li><strong>💥 Chain Slash</strong> — kills trigger additional nearby slashes</li>
  <li><strong>🏹 Multishot</strong> — fireballs split into 3 on spawn</li>
  <li><strong>💀 Death Nova</strong> — each kill explodes outward</li>
</ul>
<p>
By wave 10 your screen will look unhinged. That's the goal.
</p>
 
<h2>🏰 The Guild (Between Raids)</h2>
<ul>
  <li><strong>Stash</strong>, equipment found in raids is kept here between runs.</li>
  <li><strong>Salvage</strong>, break down items you don't need for Guild XP.</li>
  <li><strong>Permanent Upgrades</strong>, spend Guild XP on persistent stat boosts that carry into every raid — ATK, HP, Speed, Range, Attack Speed, Magnet Range.</li>
  <li><strong>Guild Rank</strong>, levels up as you earn Guild XP across all your runs.</li>
</ul>
 
<h2>👹 Enemy Types</h2>
<table>
  <thead>
    <tr>
      <th>Enemy</th>
      <th>Behaviour</th>
      <th>Model</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Goblin</td><td>Fast melee rush</td><td><code>goblin.glb</code></td></tr>
    <tr><td>Archer</td><td>Ranged, strafes to maintain distance, fires 3-arrow volley</td><td><code>archer.glb</code></td></tr>
    <tr><td>Troll</td><td>Slow, heavy melee, large separation radius</td><td><code>troll.glb</code></td></tr>
    <tr><td>Boss</td><td>Spawns every 3 waves, high HP, drops portal on death</td><td><code>boss.glb</code></td></tr>
  </tbody>
</table>
<p>
All enemy models are custom GLBs generated with <strong>TripoAI</strong> and exported with their original textures. Enemies use a procedural attack animation system — no skeleton required, driven entirely by mesh rotation and translation curves.
</p>
 
<h2>🛠️ Built With</h2>
<ul>
  <li><strong>Anthropic Claude</strong>, the entire game was designed, architected, and built through a conversational AI-assisted workflow — systems, mechanics, rendering, UI, and iteration</li>
  <li><strong>TripoAI</strong>, all 3D character models generated with TripoAI and exported as GLB with textures</li>
  <li><strong>Three.js r128</strong>, all 3D rendering, scene management, lighting, shadows</li>
  <li><strong>Vanilla HTML / CSS / JS</strong>, no framework, no build step, runs in any browser</li>
  <li><strong>Python http.server</strong>, for local development with GLB loading</li>
</ul>
 
<h2>⚙️ Technical Highlights</h2>
<ul>
  <li>Procedural forest generation — open clearings connected by dirt paths, 180+ trees, rocks, roots, and mushroom lights placed per run</li>
  <li>Pooled particle system using a single <code>THREE.Points</code> object with pre-allocated buffer geometry — zero <code>scene.add/remove</code> calls during gameplay</li>
  <li>Per-type GLB model cache — each model loaded once at run start and cloned from cache for every spawn</li>
  <li>Enemy separation system — repulsion force prevents stacking during melee, scales by enemy size</li>
  <li>Procedural attack animations — mesh tilt, lunge, and lift driven by <code>sin(t*PI)</code> curves</li>
  <li>Big damage numbers — scale with damage amount, crits pop with a burst animation</li>
</ul>
 
<h2>🚀 How to Run</h2>
<p>
No install. No build. Just:
</p>
<ol>
  <li>Clone or download the repo</li>
  <li>Put all GLB files in the same folder as <code>index.html</code></li>
  <li>Open a terminal in that folder and run:</li>
</ol>
<pre><code>python3 -m http.server 8080</code></pre>
<ol start="4">
  <li>Open <code>http://localhost:8080</code> in Chrome</li>
</ol>
<p>
That's it. GLBs need a local server because browsers block direct file access for security reasons.
</p>
<p><strong>Required files in the same folder:</strong></p>
<pre><code>index.html
player.glb
goblin.glb
archer.glb
troll.glb
boss.glb</code></pre>
 
<h2>📸 Screenshots / Demo</h2>
<p>
Add gameplay screenshots or GIF here.
</p>
<pre><code>&lt;img src="your-screenshot-here.png" alt="Abyssal Raid gameplay" width="800"&gt;</code></pre>
 
<h2>🧪 Why This Project Exists</h2>
<p>
This started as a question: how far can you push a browser game built entirely through conversation with an AI?
</p>
<p>
Every system in this game — the combat, the procedural forest, the particle engine, the GLB loading pipeline, the guild progression — was designed and built through an iterative back-and-forth with Claude. No separate codebase, no engine, no boilerplate. Just a conversation that slowly became a game.
</p>
<p>
The 3D characters were generated with TripoAI and dropped straight in as GLBs. The whole thing runs in a single HTML file.
</p>
 
<h2>🧠 Learnings</h2>
<ul>
  <li>Three.js is a surprisingly capable game engine if you treat it like one</li>
  <li>Particle systems with individual mesh objects will destroy your frame rate. Buffer geometry pools are the move.</li>
  <li>Procedural content doesn't need to be complex to feel alive — a few well-placed trees and some coloured lighting goes a long way</li>
  <li>Camera lerp feels smooth in theory but adds real perceived lag during fast movement. Snap it.</li>
  <li>GLB models from AI generation tools tend to share the same forward-axis baked orientation issue. A simple <code>rotation.y</code> offset in the clone function fixes it across all of them</li>
</ul>
 
<h2>🤝 Contributing</h2>
<p>
Personal project, but if you build something wild on top of it — show me.
</p>
 
<h2>📄 License</h2>
<p>
Fork it. Just let me know what you made.
</p>
 
<h2>👤 Author</h2>
<p>
<strong>Thiago Carneiro</strong><br>
Unreal Engine Artist, Technical Artist, Educator
</p>
 
<h2>💬 Final Note</h2>
<p>
Built across many late nights, one feature at a time, one conversation at a time.
</p>
<p>
The forest is procedurally generated but the chaos is very real.
</p>
 
