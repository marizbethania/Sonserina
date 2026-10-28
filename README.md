<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<title>Casa Sonserina</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Almendra+Display&family=Alegreya:ital,wght@0,400;0,500;0,700;1,400&family=Alegreya+Sans+SC:wght@500;700&display=swap">
<style>
/* Ajustes básicos de página (o publicador do artifact já fazia isso sozinho) */
body { margin: 0; }
img { max-width: 100%; }
[hidden] { display: none !important; }

/* Layout concept: uma descida da superfície do Lago Negro até as masmorras. O fundo escurece conforme a página rola e um trilho à esquerda marca a profundidade. */
:root {
  --abyss: #020706;
  --deep: #051410;
  --moss: #0a241b;
  --surface: #0a2f25;
  --emerald: #2fa876;
  --silver: #cdd7d3;
  --mist: #8ba39a;
  --line: #183028;
  --glow: rgba(47, 168, 118, 0.13);
  --lamp: rgba(47, 168, 118, 0.3);
  --fog: rgba(139, 163, 154, 0.11);
  --fog-green: rgba(47, 168, 118, 0.08);
  --bubble: rgba(139, 163, 154, 0.4);
  --shade-a: rgba(2, 7, 6, 0.22);
  --shade-b: rgba(2, 7, 6, 0.62);
  --font-display: "Almendra Display", "Palatino Linotype", Georgia, serif;
  --font-body: "Alegreya", Georgia, serif;
  --font-label: "Alegreya Sans SC", "Trebuchet MS", sans-serif;
  color-scheme: dark;
}

* { box-sizing: border-box; }

body {
  margin: 0;
  background: var(--abyss);
  color: var(--silver);
  font-family: var(--font-body);
  font-size: 1.125rem;
  line-height: 1.65;
}

a { color: var(--emerald); }
a:focus-visible, button:focus-visible, input:focus-visible { outline: 2px solid var(--emerald); outline-offset: 3px; }

.lake {
  background: linear-gradient(180deg, var(--surface) 0, var(--deep) 520px, var(--abyss) 1200px);
}

.band { padding-block: 4.5rem; }

.inner {
  max-width: 68rem;
  margin-inline: auto;
  padding-left: max(16px, env(safe-area-inset-left, 0px));
  padding-right: max(16px, env(safe-area-inset-right, 0px));
}

.eyebrow {
  margin: 0 0 0.75rem;
  font-family: var(--font-label);
  font-weight: 700;
  font-size: 0.95rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--mist);
}

h1, h2 {
  margin: 0;
  font-family: var(--font-display);
  font-weight: 400;
  line-height: 1.05;
  text-wrap: balance;
}

h2 { font-size: clamp(2rem, 5vw, 3.1rem); color: var(--silver); }

p { margin: 0 0 1.1rem; max-width: 62ch; }

/* Hero */
.hero { position: relative; overflow: hidden; isolation: isolate; padding-block: 2rem 0; }
.hero::before, .hero::after {
  content: "";
  position: absolute;
  inset: -20% -10%;
  z-index: -1;
  background:
    radial-gradient(40% 30% at 20% 22%, var(--glow), transparent 70%),
    radial-gradient(35% 25% at 78% 12%, var(--glow), transparent 70%);
  animation: drift 22s ease-in-out infinite alternate;
}
.hero::after { opacity: 0.7; animation-duration: 31s; animation-direction: alternate-reverse; }
@keyframes drift {
  from { transform: translate3d(-3%, 0, 0); }
  to { transform: translate3d(4%, 6%, 0); }
}

.top ul {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem 1.75rem;
  margin: 0;
  padding: 0;
  list-style: none;
  font-family: var(--font-label);
  font-weight: 500;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  font-size: 0.95rem;
}
.top a { color: var(--silver); text-decoration: none; padding-block: 0.25rem; border-bottom: 1px solid transparent; }
.top a:hover { border-bottom-color: var(--emerald); }

.hero-body { padding-block: 5rem 3rem; }

h1 {
  font-size: clamp(3.6rem, 13vw, 9.5rem);
  letter-spacing: 0.01em;
  color: var(--silver);
  background: linear-gradient(100deg, var(--mist) 0%, var(--silver) 40%, var(--emerald) 50%, var(--silver) 60%, var(--mist) 100%);
  background-size: 250% 100%;
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: drop-shadow(0 0 28px var(--glow));
  animation: sheen 11s ease-in-out infinite alternate;
}
@keyframes sheen {
  from { background-position: 100% 0; }
  to { background-position: 0 0; }
}

.motto {
  margin: 0.5rem 0 1.5rem;
  font-style: italic;
  font-size: 1.4rem;
  color: var(--mist);
}

.lead { font-size: 1.3rem; max-width: 46ch; }

.actions { display: flex; flex-wrap: wrap; gap: 0.75rem; margin-top: 2rem; }

.btn {
  display: inline-block;
  padding: 0.7rem 1.4rem;
  font-family: var(--font-label);
  font-weight: 700;
  font-size: 1rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  text-decoration: none;
  border: 1px solid var(--emerald);
  border-radius: 2px;
  background: var(--emerald);
  color: var(--abyss);
  cursor: pointer;
}
.btn:hover { background: var(--silver); border-color: var(--silver); }
.btn.ghost { background: transparent; color: var(--silver); border-color: var(--mist); }
.btn.ghost:hover { border-color: var(--silver); background: var(--glow); }

.scales {
  height: 8rem;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='48' height='24' viewBox='0 0 48 24'%3E%3Cg fill='none' stroke='%2334b583' stroke-opacity='.38' stroke-width='1.2'%3E%3Ccircle cx='0' cy='0' r='24'/%3E%3Ccircle cx='48' cy='0' r='24'/%3E%3Ccircle cx='24' cy='24' r='24'/%3E%3C/g%3E%3C/svg%3E");
  background-size: 48px 24px;
  -webkit-mask-image: linear-gradient(180deg, transparent, #000);
  mask-image: linear-gradient(180deg, transparent, #000);
}

/* Valores */
.traits { display: grid; gap: 0; margin: 2.5rem 0 0; grid-template-columns: minmax(0, 1fr); }
.traits > div { padding-block: 1.4rem; border-top: 1px solid var(--line); }
.traits dt { font-family: var(--font-display); font-size: 2rem; color: var(--emerald); line-height: 1.1; }
.traits dd { margin: 0.4rem 0 0; max-width: 40ch; }
.note { margin-top: 2rem; color: var(--mist); }

/* Blocos em duas colunas */
.split { display: grid; gap: 2rem 4rem; grid-template-columns: minmax(0, 1fr); }
.split > * { min-width: 0; }

/* Ficha */
.sheet { margin: 0; padding: 0.5rem 1.5rem; background: var(--deep); border: 1px solid var(--line); }
.sheet > div { padding-block: 0.9rem; border-top: 1px solid var(--line); }
.sheet > div:first-child { border-top: 0; }
.sheet dt {
  font-family: var(--font-label);
  font-weight: 700;
  font-size: 0.85rem;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--mist);
}
.sheet dd { margin: 0.1rem 0 0; }

/* Pessoas */
.people { list-style: none; margin: 2.5rem 0 0; padding: 0; }
.people li {
  display: grid;
  gap: 0.25rem 2rem;
  grid-template-columns: minmax(0, 1fr);
  padding-block: 1.3rem;
  border-top: 1px solid var(--line);
}
.people strong { font-family: var(--font-display); font-weight: 400; font-size: 1.6rem; line-height: 1.15; }
.people span { color: var(--silver); max-width: 54ch; }

/* Teste */
.quiz { margin-top: 2.5rem; max-width: 40rem; }
.q { border: 0; margin: 0 0 2rem; padding: 0; min-width: 0; }
.q legend { font-family: var(--font-display); font-size: 1.4rem; line-height: 1.25; padding: 0; margin-bottom: 0.9rem; }
.opt {
  display: flex;
  gap: 0.75rem;
  align-items: flex-start;
  padding: 0.7rem 0.9rem;
  margin-bottom: 0.5rem;
  border: 1px solid var(--line);
  border-radius: 3px;
  cursor: pointer;
}
.opt:hover { border-color: var(--mist); }
.opt:has(input:checked) { border-color: var(--emerald); background: var(--glow); }
.opt input { accent-color: var(--emerald); margin-top: 0.4rem; flex: none; }
.result { margin-top: 1.5rem; padding: 1.25rem 1.5rem; border: 1px solid var(--emerald); background: var(--glow); }
.result[hidden] { display: none; }
.result h3 { margin: 0 0 0.4rem; font-family: var(--font-display); font-weight: 400; font-size: 1.8rem; line-height: 1.1; }
.result p { margin: 0; }

footer { padding-block: 3rem 4rem; border-top: 1px solid var(--line); color: var(--mist); font-size: 0.95rem; }
footer p { max-width: 70ch; }

/* Efeitos: lampião, névoa, bolhas e lanterna */
.lamp {
  position: absolute;
  top: -8rem;
  right: 6%;
  width: min(26rem, 80vw);
  height: min(26rem, 80vw);
  z-index: -1;
  background: radial-gradient(circle, var(--lamp), transparent 65%);
  animation: flicker 7s infinite;
}
@keyframes flicker {
  0%, 100% { opacity: 0.9; }
  8% { opacity: 0.55; }
  10% { opacity: 0.95; }
  22% { opacity: 0.7; }
  24% { opacity: 1; }
  47% { opacity: 0.8; }
  49% { opacity: 0.5; }
  51% { opacity: 0.9; }
  73% { opacity: 0.75; }
}

.fx { position: fixed; inset: 0; pointer-events: none; z-index: 4; overflow: hidden; }
.fog { position: absolute; left: 0; width: 200%; background-repeat: repeat-x; background-size: 50% 100%; will-change: transform; }
.fog.a {
  top: 6%;
  height: 52%;
  background-image:
    radial-gradient(38% 50% at 35% 50%, var(--fog), transparent 72%),
    radial-gradient(28% 42% at 74% 38%, var(--fog-green), transparent 72%);
  animation: fogmove 90s linear infinite;
}
.fog.b {
  bottom: 0;
  height: 48%;
  background-image:
    radial-gradient(40% 55% at 30% 70%, var(--fog), transparent 72%),
    radial-gradient(24% 50% at 72% 60%, var(--fog), transparent 72%);
  animation: fogmove 62s linear infinite reverse;
}
.fog.c {
  top: 30%;
  height: 40%;
  background-image:
    radial-gradient(36% 48% at 40% 50%, var(--fog-green), transparent 72%),
    radial-gradient(26% 44% at 68% 55%, var(--fog), transparent 72%);
  animation: fogmove 120s linear infinite;
}
@keyframes fogmove {
  from { transform: translate3d(0, 0, 0); }
  to { transform: translate3d(-50%, 0, 0); }
}

.bubbles { position: absolute; inset: 0; }
.bubbles i {
  position: absolute;
  bottom: -24px;
  left: var(--x);
  width: var(--s);
  height: var(--s);
  border: 1px solid var(--bubble);
  border-radius: 50%;
  background: radial-gradient(circle at 30% 30%, var(--bubble), transparent 60%);
  opacity: 0;
  animation: rise var(--d) linear var(--delay) infinite;
}
@keyframes rise {
  0% { transform: translate3d(0, 0, 0); opacity: 0; }
  10% { opacity: 0.7; }
  90% { opacity: 0.45; }
  100% { transform: translate3d(var(--sway), -108vh, 0); opacity: 0; }
}

.vignette {
  position: absolute;
  inset: 0;
  background: radial-gradient(circle 60vmax at var(--mx, 50%) var(--my, 35%), transparent 0, transparent 10%, var(--shade-a) 50%, var(--shade-b) 100%);
}

.traits dt { transition: text-shadow 0.4s; }
.traits > div:hover dt { text-shadow: 0 0 20px var(--emerald); }
.people li { transition: background 0.5s; }
.people li:hover { background: linear-gradient(90deg, var(--glow), transparent 70%); }
.sheet { box-shadow: 0 0 48px var(--glow); }

/* Navegação entre seções: só uma aparece por vez */
.top a[aria-current="page"] { color: var(--emerald); border-bottom-color: var(--emerald); }

[data-view]:not([hidden]) { animation: emerge 0.6s ease-out; }
@keyframes emerge {
  from { opacity: 0; transform: translateY(14px); }
  to { opacity: 1; transform: translateY(0); }
}

/* A faixa de escamas só combina com a página inicial */
body:not([data-vista="inicio"]) .scales { display: none; }

.voltar {
  display: inline-block;
  margin-top: 2.5rem;
  padding-block: 0.5rem;
  font-family: var(--font-label);
  font-weight: 700;
  font-size: 0.95rem;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--emerald);
  text-decoration: none;
  border-bottom: 1px solid transparent;
  transition: border-color 0.3s, text-shadow 0.3s;
}
.voltar:hover { border-bottom-color: var(--emerald); text-shadow: 0 0 14px var(--glow); }
.voltar:focus-visible { outline: 2px solid var(--emerald); outline-offset: 3px; }

/* Trilho de profundidade */
.rail { display: none; }

@media (min-width: 720px) {
  .traits { grid-template-columns: repeat(2, minmax(0, 1fr)); column-gap: 3rem; }
  .people li { grid-template-columns: minmax(0, 5fr) minmax(0, 7fr); align-items: baseline; }
}
@media (min-width: 820px) {
  .split { grid-template-columns: minmax(0, 5fr) minmax(0, 7fr); }
  .split.flip { grid-template-columns: minmax(0, 7fr) minmax(0, 5fr); }
}
@media (min-width: 1180px) {
  .rail {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.75rem;
    position: fixed;
    left: max(14px, env(safe-area-inset-left, 0px));
    top: 7rem;
    bottom: 5rem;
    width: 1.4rem;
    z-index: 5;
    font-family: var(--font-label);
    font-weight: 700;
    font-size: 0.8rem;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: var(--mist);
  }
  .rail span { writing-mode: vertical-rl; }
  .track { position: relative; flex: 1; width: 1px; background: var(--line); }
  .mark {
    position: absolute;
    left: 50%;
    top: 0;
    width: 9px;
    height: 9px;
    border-radius: 50%;
    background: var(--emerald);
    transform: translate(-50%, -50%);
  }
}

@media (prefers-reduced-motion: reduce) {
  .hero::before, .hero::after, .lamp, .fog, h1, [data-view] { animation: none; }
}
</style>
</head>
<body>
<div class="fx" aria-hidden="true">
  <div class="fog c"></div>
  <div class="fog a"></div>
  <div class="fog b"></div>
  <div class="bubbles" id="bubbles"></div>
  <div class="vignette" id="vignette"></div>
</div>

<aside class="rail" aria-hidden="true">
  <span>Lago</span>
  <div class="track"><i class="mark" id="mark"></i></div>
  <span>Masmorras</span>
</aside>

<div class="lake">
  <header class="band hero">
    <div class="lamp" aria-hidden="true"></div>
    <div class="inner">
      <nav class="top" aria-label="Seções">
        <ul>
          <li><a href="#inicio">Início</a></li>
          <li><a href="#valores">Valores</a></li>
          <li><a href="#fundador">Fundador</a></li>
          <li><a href="#salao">Salão Comunal</a></li>
          <li><a href="#pessoas">Sonserinos</a></li>
          <li><a href="#teste">Teste</a></li>
        </ul>
      </nav>
      <div class="hero-body" id="inicio" data-view>
        <p class="eyebrow">Hogwarts · Escola de Magia e Bruxaria</p>
        <h1>Sonserina</h1>
        <p class="motto">Verde, prata e uma serpente.</p>
        <p class="lead">A casa de quem tem ambição, astúcia e determinação. O Salão Comunal fica nas masmorras, abaixo do Lago Negro.</p>
        <div class="actions">
          <a class="btn" href="#valores">Conhecer a casa</a>
          <a class="btn ghost" href="#teste">Fazer o teste</a>
        </div>
      </div>
    </div>
    <div class="scales" aria-hidden="true"></div>
  </header>

  <main>
    <section class="band" id="valores" data-view>
      <div class="inner">
        <p class="eyebrow">O que a casa valoriza</p>
        <h2>Quatro traços que a Sonserina procura</h2>
        <dl class="traits">
          <div>
            <dt>Ambição</dt>
            <dd>Quem chega à Sonserina quer ir longe. A casa respeita metas altas e a disciplina para alcançá-las.</dd>
          </div>
          <div>
            <dt>Astúcia</dt>
            <dd>Ler a situação antes de agir, escolher o momento e dizer o que convence. Pensar à frente é uma virtude.</dd>
          </div>
          <div>
            <dt>Determinação</dt>
            <dd>Sonserinos não largam um objetivo no primeiro obstáculo. Insistem, ajustam o plano e tentam de novo.</dd>
          </div>
          <div>
            <dt>Engenhosidade</dt>
            <dd>Quando falta um caminho direto, a casa encontra outro. Improvisar com poucos recursos faz parte da fama.</dd>
          </div>
        </dl>
        <p class="note">A casa carrega uma reputação sombria, porque muitos bruxos das trevas passaram por ela. Os livros também mostram sonserinos que se voltaram contra Voldemort, como Severus Snape e Regulus Black.</p>
        <a class="voltar" href="#inicio">← Voltar à página inicial</a>
      </div>
    </section>

    <section class="band" id="fundador" data-view>
      <div class="inner split">
        <div>
          <p class="eyebrow">Quem fundou a casa</p>
          <h2>Salazar Slytherin</h2>
        </div>
        <div>
          <p>Salazar Slytherin foi um dos quatro fundadores de Hogwarts, ao lado de Godric Gryffindor, Helga Hufflepuff e Rowena Ravenclaw. Era um bruxo de grande talento e queria escolher os alunos da própria casa por critérios rígidos, em especial a ascendência bruxa.</p>
          <p>As diferenças com os outros fundadores cresceram até que ele deixou a escola. Segundo a lenda, antes de partir construiu a Câmara Secreta e deixou ali um basilisco, que só o seu herdeiro poderia controlar.</p>
          <a class="voltar" href="#inicio">← Voltar à página inicial</a>
        </div>
      </div>
    </section>

    <section class="band" id="salao" data-view>
      <div class="inner split flip">
        <div>
          <p class="eyebrow">Onde a casa vive</p>
          <h2>Sob as águas do Lago Negro</h2>
          <p style="margin-top:1.5rem">O Salão Comunal fica nas masmorras de Hogwarts, abaixo do nível do lago. A entrada é uma parede de pedra lisa que se abre quando o aluno diz a senha.</p>
          <p>Lá dentro há um salão longo e baixo, de paredes de pedra bruta. Lampiões esverdeados pendem do teto, e as janelas dão para a água, onde às vezes passa a lula gigante. Cadeiras entalhadas e uma lareira de pedra completam o ambiente.</p>
          <a class="voltar" href="#inicio">← Voltar à página inicial</a>
        </div>
        <dl class="sheet">
          <div><dt>Fundador</dt><dd>Salazar Slytherin</dd></div>
          <div><dt>Cores</dt><dd>Verde e prata</dd></div>
          <div><dt>Animal</dt><dd>Serpente</dd></div>
          <div><dt>Elemento</dt><dd>Água</dd></div>
          <div><dt>Fantasma</dt><dd>Barão Sangrento</dd></div>
          <div><dt>Chefes da casa</dt><dd>Horácio Slughorn, depois Severus Snape</dd></div>
          <div><dt>Local</dt><dd>Masmorras, sob o Lago Negro</dd></div>
        </dl>
      </div>
    </section>

    <section class="band" id="pessoas" data-view>
      <div class="inner">
        <p class="eyebrow">Quem passou pela casa</p>
        <h2>Sonserinos conhecidos</h2>
        <ul class="people">
          <li>
            <strong>Severus Snape</strong>
            <span>Professor de Poções, depois de Defesa Contra as Artes das Trevas, chefe da Sonserina e por fim diretor de Hogwarts.</span>
          </li>
          <li>
            <strong>Draco Malfoy</strong>
            <span>Colega de ano de Harry, vindo de uma família bruxa tradicional e rival constante dele.</span>
          </li>
          <li>
            <strong>Horácio Slughorn</strong>
            <span>Professor de Poções e chefe da casa. Reunia alunos promissores no Clube do Slug.</span>
          </li>
          <li>
            <strong>Tom Riddle</strong>
            <span>Aluno brilhante e monitor-chefe, que mais tarde se tornou Lord Voldemort.</span>
          </li>
          <li>
            <strong>Regulus Black</strong>
            <span>Irmão mais novo de Sirius Black. Entrou para os Comensais da Morte e depois se voltou contra Voldemort.</span>
          </li>
          <li>
            <strong>Bellatrix Lestrange</strong>
            <span>Comensal da Morte e uma das seguidoras mais fiéis de Voldemort.</span>
          </li>
        </ul>
        <a class="voltar" href="#inicio">← Voltar à página inicial</a>
      </div>
    </section>

    <section class="band" id="teste" data-view>
      <div class="inner">
        <p class="eyebrow">Para se divertir</p>
        <h2>Você seria sonserino?</h2>
        <p style="margin-top:1.25rem">Quatro perguntas rápidas. O resultado é uma brincadeira e não decide a sua casa.</p>

        <form class="quiz" id="quiz">
          <fieldset class="q">
            <legend>Você vai liderar um trabalho em grupo. O que faz primeiro?</legend>
            <label class="opt"><input type="radio" name="q1" value="2"> Escolho quem tem as melhores habilidades para cada parte.</label>
            <label class="opt"><input type="radio" name="q1" value="1"> Estudo o tema sozinho antes de falar com alguém.</label>
            <label class="opt"><input type="radio" name="q1" value="0"> Reúno todos e divido as tarefas por igual.</label>
          </fieldset>

          <fieldset class="q">
            <legend>Um prêmio disputado está aberto a todos. Qual é o seu plano?</legend>
            <label class="opt"><input type="radio" name="q2" value="0"> Participo para me divertir com os amigos.</label>
            <label class="opt"><input type="radio" name="q2" value="2"> Treino mais que todos e descubro como os outros vão jogar.</label>
            <label class="opt"><input type="radio" name="q2" value="1"> Preparo um bom resultado sem chamar atenção.</label>
          </fieldset>

          <fieldset class="q">
            <legend>Alguém contesta a sua ideia diante de todos. Como reage?</legend>
            <label class="opt"><input type="radio" name="q3" value="1"> Defendo a ideia com firmeza na hora.</label>
            <label class="opt"><input type="radio" name="q3" value="2"> Escuto, espero e respondo no momento em que a resposta vai pesar mais.</label>
            <label class="opt"><input type="radio" name="q3" value="0"> Aceito a crítica e ajusto o plano sem discutir.</label>
          </fieldset>

          <fieldset class="q">
            <legend>Qual lugar combina mais com você?</legend>
            <label class="opt"><input type="radio" name="q4" value="0"> Uma torre alta, com lareira e vista para as montanhas.</label>
            <label class="opt"><input type="radio" name="q4" value="2"> Um salão sob um lago, com luz verde nas paredes.</label>
            <label class="opt"><input type="radio" name="q4" value="1"> Uma biblioteca silenciosa, cheia de livros antigos.</label>
          </fieldset>

          <div class="actions">
            <button class="btn" type="submit">Ver resultado</button>
            <button class="btn ghost" type="reset">Recomeçar</button>
          </div>

          <div class="result" id="result" role="status" aria-live="polite" hidden>
            <h3 id="result-title"></h3>
            <p id="result-text"></p>
          </div>
        </form>

        <a class="voltar" href="#inicio">← Voltar à página inicial</a>
      </div>
    </section>
  </main>

  <footer>
    <div class="inner">
      <p>Todos os direitos reservados. Site feito por Bethânia Borgo. &copy; <span id="ano-atual"> </span> </p>
    </div>
  </footer>
  <script>
  document.getElementById("ano-atual").textContent = new Date().getFullYear();
</script>
</div>

<script>
(function () {
  try {
    var mark = document.getElementById('mark');
    function updateDepth() {
      if (!mark) return;
      var max = document.documentElement.scrollHeight - window.innerHeight;
      var p = max > 0 ? Math.min(1, Math.max(0, window.scrollY / max)) : 0;
      mark.style.top = (p * 100) + '%';
    }
    window.addEventListener('scroll', function () { window.requestAnimationFrame(updateDepth); }, { passive: true });
    window.addEventListener('resize', updateDepth);
    updateDepth();
  } catch (err) {}

  try {
    var form = document.getElementById('quiz');
    var box = document.getElementById('result');
    var title = document.getElementById('result-title');
    var text = document.getElementById('result-text');

    var tiers = [
      { max: 2, title: 'Outra casa te chama', text: 'Suas respostas valorizam o grupo e a franqueza. A Grifinória ou a Lufa-Lufa devem te receber bem.' },
      { max: 5, title: 'Traços de sonserino', text: 'Você mistura estratégia com cautela. Falta decidir quanto da sua ambição quer mostrar.' },
      { max: 8, title: 'Sonserino de coração', text: 'Você planeja, escolhe seus aliados e não desiste fácil. O Salão Comunal já tem uma poltrona reservada.' }
    ];

    form.addEventListener('submit', function (e) {
      e.preventDefault();
      var total = 0;
      var answered = 0;
      for (var i = 1; i <= 4; i++) {
        var checked = form.querySelector('input[name="q' + i + '"]:checked');
        if (checked) { answered++; total += Number(checked.value); }
      }
      box.hidden = false;
      if (answered < 4) {
        title.textContent = 'Faltam respostas';
        text.textContent = 'Responda as quatro perguntas para ver o resultado.';
        return;
      }
      for (var t = 0; t < tiers.length; t++) {
        if (total <= tiers[t].max) {
          title.textContent = tiers[t].title;
          text.textContent = tiers[t].text;
          break;
        }
      }
    });

    form.addEventListener('reset', function () {
      box.hidden = true;
    });
  } catch (err) {}
})();

(function () {
  var reduce = false;
  try { reduce = window.matchMedia('(prefers-reduced-motion: reduce)').matches; } catch (err) {}

  try {
    var holder = document.getElementById('bubbles');
    if (holder && !reduce) {
      for (var i = 0; i < 22; i++) {
        var b = document.createElement('i');
        var size = 4 + Math.random() * 14;
        b.style.setProperty('--x', (Math.random() * 100).toFixed(1) + '%');
        b.style.setProperty('--s', size.toFixed(1) + 'px');
        b.style.setProperty('--d', (16 + Math.random() * 22).toFixed(1) + 's');
        b.style.setProperty('--delay', (-Math.random() * 30).toFixed(1) + 's');
        b.style.setProperty('--sway', ((Math.random() - 0.5) * 80).toFixed(0) + 'px');
        holder.appendChild(b);
      }
    }
  } catch (err) {}

  try {
    var vg = document.getElementById('vignette');
    var cx = window.innerWidth / 2, cy = window.innerHeight * 0.35;
    var tx = cx, ty = cy, raf = 0;
    function paint() {
      raf = 0;
      if (reduce) { cx = tx; cy = ty; } else { cx += (tx - cx) * 0.12; cy += (ty - cy) * 0.12; }
      vg.style.setProperty('--mx', cx.toFixed(1) + 'px');
      vg.style.setProperty('--my', cy.toFixed(1) + 'px');
      if (Math.abs(tx - cx) > 0.5 || Math.abs(ty - cy) > 0.5) { raf = window.requestAnimationFrame(paint); }
    }
    window.addEventListener('pointermove', function (e) {
      tx = e.clientX; ty = e.clientY;
      if (!raf) { raf = window.requestAnimationFrame(paint); }
    }, { passive: true });
    paint();
  } catch (err) {}
})();

/* Navegação: mostra uma seção por vez, guiada pelo #endereço da página */
(function () {
  var views = document.querySelectorAll('[data-view]');
  var links = document.querySelectorAll('.top a');

  function current() {
    var id = window.location.hash.replace('#', '');
    for (var i = 0; i < views.length; i++) { if (views[i].id === id) { return id; } }
    return 'inicio';
  }

  function show(id) {
    for (var i = 0; i < views.length; i++) { views[i].hidden = views[i].id !== id; }
    for (var j = 0; j < links.length; j++) {
      if (links[j].getAttribute('href') === '#' + id) { links[j].setAttribute('aria-current', 'page'); }
      else { links[j].removeAttribute('aria-current'); }
    }
    document.body.setAttribute('data-vista', id);
    window.scrollTo(0, 0);
    try { window.dispatchEvent(new Event('scroll')); } catch (err) {}
  }

  window.addEventListener('hashchange', function () { show(current()); });
  show(current());
})();
</script>
</body>
</html>
