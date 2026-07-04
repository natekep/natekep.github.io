<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Messi vs Ronaldo — A Career at Every Age</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Inter:wght@400;500;600;700&family=Space+Grotesk:wght@400;500;700&display=swap" rel="stylesheet">
<style>
:root{
  --pitch:#0b1510;
  --panel:#101e16;
  --panel2:#0e1a13;
  --line:#24352b;
  --chalk:#efebdd;
  --muted:#93a096;
  --leo:#86c7ee;
  --leo-deep:#183b52;
  --cr7:#e14b52;
  --cr7-deep:#54222a;
  --gold:#d9a82e;
  --maxgoals:73;
}
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
body{
  background:var(--pitch);
  color:var(--chalk);
  font-family:'Inter',system-ui,sans-serif;
  line-height:1.6;
  overflow-x:hidden;
}
/* floodlight wash */
body::before{
  content:"";position:fixed;inset:0;pointer-events:none;z-index:0;
  background:
    radial-gradient(1200px 600px at 15% -10%, rgba(134,199,238,.07), transparent 60%),
    radial-gradient(1200px 600px at 85% -10%, rgba(225,75,82,.07), transparent 60%),
    radial-gradient(900px 900px at 50% 110%, rgba(217,168,46,.05), transparent 60%);
}
::selection{background:var(--gold);color:#0b1510}

.display{font-family:'Anton',Impact,sans-serif;letter-spacing:.01em;font-weight:400}
.numeral{font-family:'Space Grotesk',monospace}

/* ---------- halfway-line spine ---------- */
.spine{
  position:fixed;left:50%;top:0;bottom:0;width:1px;
  background:linear-gradient(to bottom, transparent, rgba(239,235,221,.16) 8%, rgba(239,235,221,.16) 92%, transparent);
  z-index:1;pointer-events:none;
}
@media(max-width:820px){.spine{display:none}}

/* ---------- sticky age marker ---------- */
.age-marker{
  position:fixed;top:18px;left:50%;transform:translateX(-50%);
  z-index:50;display:flex;flex-direction:column;align-items:center;gap:2px;
  opacity:0;transition:opacity .4s ease;pointer-events:none;
}
.age-marker.on{opacity:1}
.age-marker .ring{
  width:74px;height:74px;border-radius:50%;
  border:1px solid rgba(239,235,221,.35);
  background:rgba(11,21,16,.82);backdrop-filter:blur(6px);
  display:flex;flex-direction:column;align-items:center;justify-content:center;
  box-shadow:0 6px 30px rgba(0,0,0,.5);
}
.age-marker .lbl{font-size:.55rem;letter-spacing:.28em;color:var(--muted);text-transform:uppercase}
.age-marker .num{font-size:1.9rem;line-height:1;color:var(--chalk)}
.progress{
  position:fixed;top:0;left:0;height:2px;width:100%;z-index:60;transform-origin:0 50%;transform:scaleX(0);
  background:linear-gradient(90deg,var(--leo),var(--gold),var(--cr7));
}

/* ---------- hero ---------- */
.hero{
  position:relative;min-height:100svh;display:flex;flex-direction:column;
  align-items:center;justify-content:center;text-align:center;
  padding:6rem 1.5rem 4rem;z-index:2;
}
.hero .kick{font-size:.72rem;letter-spacing:.4em;text-transform:uppercase;color:var(--muted);margin-bottom:1.6rem}
.hero-shirts{display:flex;align-items:baseline;gap:3vw;justify-content:center}
.hero-shirts .n{font-size:clamp(6rem,22vw,17rem);line-height:.9}
.hero-shirts .n.leo{color:var(--leo);text-shadow:0 0 80px rgba(134,199,238,.25)}
.hero-shirts .n.cr7{color:var(--cr7);text-shadow:0 0 80px rgba(225,75,82,.25)}
.hero-shirts .vs{font-size:clamp(1.2rem,4vw,2.6rem);color:var(--gold)}
.hero h1{font-size:clamp(1.6rem,4.5vw,3rem);margin:1.4rem 0 .9rem;text-transform:uppercase;letter-spacing:.05em}
.hero p{max-width:620px;color:var(--muted);font-size:.98rem}
.hero .names{display:flex;gap:2.5rem;justify-content:center;margin-top:2rem;font-family:'Space Grotesk';font-size:.8rem;letter-spacing:.12em;text-transform:uppercase}
.hero .names .l{color:var(--leo)}.hero .names .r{color:var(--cr7)}
.scroll-cue{margin-top:3.2rem;color:var(--muted);font-size:.7rem;letter-spacing:.3em;text-transform:uppercase;animation:bob 2.4s ease-in-out infinite}
@keyframes bob{0%,100%{transform:translateY(0);opacity:.55}50%{transform:translateY(8px);opacity:1}}

/* ---------- age sections ---------- */
.age{
  position:relative;z-index:2;
  max-width:1180px;margin:0 auto;
  padding:7rem 1.5rem 4.5rem;
}
.age-head{display:flex;align-items:center;justify-content:center;margin-bottom:3rem;position:relative}
.age-head .big{
  font-size:clamp(4.5rem,12vw,9rem);line-height:1;color:var(--chalk);
  background:var(--pitch);padding:0 1.6rem;position:relative;z-index:2;
  opacity:0;transform:translateY(30px);transition:opacity .7s ease,transform .7s ease;
}
.age.in .age-head .big{opacity:1;transform:none}
.age-head .years{
  position:absolute;bottom:-1.3rem;left:50%;transform:translateX(-50%);
  font-size:.68rem;letter-spacing:.3em;text-transform:uppercase;color:var(--muted);white-space:nowrap;
  font-family:'Space Grotesk';
}
.duo{display:grid;grid-template-columns:1fr 1fr;gap:2.4rem}
@media(max-width:820px){.duo{grid-template-columns:1fr;gap:1.4rem}}

.card{
  background:linear-gradient(180deg,var(--panel),var(--panel2));
  border:1px solid var(--line);
  border-radius:10px;padding:1.7rem 1.7rem 1.5rem;
  position:relative;overflow:hidden;
  opacity:0;transition:opacity .8s ease,transform .8s ease;
}
.card.leo{transform:translateX(-40px);border-top:3px solid var(--leo)}
.card.cr7{transform:translateX(40px);border-top:3px solid var(--cr7)}
.age.in .card{opacity:1;transform:none}
.age.in .card.cr7{transition-delay:.12s}
.card .who{display:flex;justify-content:space-between;align-items:baseline;margin-bottom:.9rem}
.card .who .name{font-family:'Space Grotesk';font-weight:700;font-size:.8rem;letter-spacing:.18em;text-transform:uppercase}
.card.leo .who .name{color:var(--leo)}
.card.cr7 .who .name{color:var(--cr7)}
.card .who .season{font-family:'Space Grotesk';font-size:.72rem;color:var(--muted);letter-spacing:.06em;text-align:right}
.card h3{font-size:1.25rem;line-height:1.25;margin-bottom:.7rem;text-transform:uppercase;letter-spacing:.03em}
.card h3.display{font-size:1.35rem}
.card p{font-size:.9rem;color:#c9cec2;margin-bottom:.75rem}
.card p strong{color:var(--chalk)}
.card p:last-of-type{margin-bottom:1rem}
.chips{display:flex;flex-wrap:wrap;gap:.45rem;margin-top:auto}
.chip{
  font-family:'Space Grotesk';font-size:.66rem;letter-spacing:.05em;
  padding:.28rem .6rem;border-radius:99px;border:1px solid var(--line);color:var(--muted);
}
.chip.trophy{border-color:rgba(217,168,46,.55);color:var(--gold)}
.chip.ballon{background:var(--gold);border-color:var(--gold);color:#141005;font-weight:700}
.chip.boot{border-color:rgba(217,168,46,.85);color:var(--gold);border-style:dashed}
.chip.dark{border-color:#4a3038;color:#c98e93}

/* ---------- goal duel bars ---------- */
.duel{margin-top:2.6rem}
.duel .duel-title{
  text-align:center;font-family:'Space Grotesk';font-size:.66rem;
  letter-spacing:.3em;text-transform:uppercase;color:var(--muted);margin-bottom:.8rem;
}
.duel .track{display:grid;grid-template-columns:1fr 1fr;gap:2px;align-items:center;position:relative}
.duel .half{display:flex;align-items:center;gap:.7rem}
.duel .half.left{justify-content:flex-end}
.duel .bar{height:14px;border-radius:3px;width:0;transition:width 1.1s cubic-bezier(.2,.7,.2,1) .25s}
.duel .half.left .bar{background:linear-gradient(90deg,rgba(134,199,238,.25),var(--leo));border-radius:3px 0 0 3px}
.duel .half.right .bar{background:linear-gradient(90deg,var(--cr7),rgba(225,75,82,.25));border-radius:0 3px 3px 0}
.duel .val{font-family:'Anton';font-size:1.5rem;min-width:2.2ch}
.duel .half.left .val{color:var(--leo)}
.duel .half.right .val{color:var(--cr7)}
@media(max-width:600px){.duel .val{font-size:1.15rem}.duel .bar{height:10px}}

/* interludes */
.interlude{
  position:relative;z-index:2;max-width:760px;margin:0 auto;
  padding:6rem 1.5rem;text-align:center;
}
.interlude .big-q{font-size:clamp(1.5rem,4vw,2.5rem);text-transform:uppercase;line-height:1.2;color:var(--chalk)}
.interlude .sub{color:var(--muted);margin-top:1rem;font-size:.95rem}
.interlude .gold{color:var(--gold)}

/* ---------- finale ---------- */
.finale{position:relative;z-index:2;max-width:1180px;margin:0 auto;padding:6rem 1.5rem 5rem}
.finale h2{font-size:clamp(2rem,6vw,4rem);text-align:center;text-transform:uppercase;margin-bottom:.6rem}
.finale .sub{text-align:center;color:var(--muted);max-width:640px;margin:0 auto 4rem;font-size:.95rem}
.chart-wrap{
  background:linear-gradient(180deg,var(--panel),var(--panel2));
  border:1px solid var(--line);border-radius:10px;padding:2rem 1.4rem 1.2rem;margin-bottom:4rem;
}
.chart-wrap .chart-title{font-family:'Space Grotesk';font-size:.7rem;letter-spacing:.28em;text-transform:uppercase;color:var(--muted);text-align:center;margin-bottom:1.4rem}
#chart{width:100%;height:auto;display:block}
.legend{display:flex;gap:2rem;justify-content:center;margin-top:1rem;font-family:'Space Grotesk';font-size:.72rem;letter-spacing:.1em;text-transform:uppercase}
.legend .l{color:var(--leo)}.legend .r{color:var(--cr7)}
.legend span::before{content:"";display:inline-block;width:22px;height:3px;margin-right:.5rem;vertical-align:middle}
.legend .l::before{background:var(--leo)}
.legend .r::before{background:var(--cr7)}

.ledger{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:1.2rem;margin-bottom:4rem}
.stat{
  background:linear-gradient(180deg,var(--panel),var(--panel2));
  border:1px solid var(--line);border-radius:10px;padding:1.4rem;text-align:center;
  opacity:0;transform:translateY(26px);transition:opacity .7s ease,transform .7s ease;
}
.finale .in .stat, .stat.in{opacity:1;transform:none}
.stat .cat{font-family:'Space Grotesk';font-size:.64rem;letter-spacing:.26em;text-transform:uppercase;color:var(--muted);margin-bottom:.9rem}
.stat .row{display:flex;justify-content:center;align-items:baseline;gap:1.1rem}
.stat .v{font-family:'Anton';font-size:2.3rem;line-height:1}
.stat .v.l{color:var(--leo)}.stat .v.r{color:var(--cr7)}
.stat .dash{color:var(--muted);font-family:'Space Grotesk'}
.stat .note{font-size:.7rem;color:var(--muted);margin-top:.7rem;font-family:'Space Grotesk';letter-spacing:.04em}

.outro{text-align:center;padding:2rem 1rem 6rem;position:relative;z-index:2}
.outro .date{font-size:clamp(3rem,10vw,7rem);color:var(--gold)}
.outro p{color:var(--muted);max-width:560px;margin:1.2rem auto 0;font-size:.95rem}
footer{position:relative;z-index:2;text-align:center;color:#5d6a60;font-size:.7rem;padding:0 1rem 3rem;font-family:'Space Grotesk';letter-spacing:.06em}

@media(prefers-reduced-motion:reduce){
  *{animation:none!important;transition:none!important;scroll-behavior:auto!important}
  .card,.age-head .big,.stat{opacity:1!important;transform:none!important}
  .duel .bar{transition:none!important}
}
</style>
</head>
<body>

<div class="spine" aria-hidden="true"></div>
<div class="progress" id="progress" aria-hidden="true"></div>
<div class="age-marker" id="ageMarker" aria-hidden="true">
  <div class="ring">
    <span class="lbl">Age</span>
    <span class="num numeral display" id="ageNum">17</span>
  </div>
</div>

<!-- ================= HERO ================= -->
<header class="hero">
  <div class="kick">The greatest rivalry in sport · Season by season · Age by age</div>
  <div class="hero-shirts display" aria-hidden="true">
    <span class="n leo">10</span>
    <span class="vs">VS</span>
    <span class="n cr7">7</span>
  </div>
  <h1 class="display">Messi &amp; Ronaldo, at every age</h1>
  <p>Born two and a half years apart, they have spent more than two decades measured against each other. This page removes the calendar and lines them up the only fair way: what each man had done <em>at the same age</em> — the goals, the Ballon d'Ors, the Golden Boot races, the trophies, and the international agony and ecstasy. Scroll from 17 to 41.</p>
  <div class="names">
    <span class="l">Lionel Messi · b. 24 Jun 1987</span>
    <span class="r">Cristiano Ronaldo · b. 5 Feb 1985</span>
  </div>
  <div class="scroll-cue">Scroll ↓</div>
</header>

<!-- ================= AGE 17 ================= -->
<section class="age" data-age="17">
  <div class="age-head"><div class="big display">17</div><div class="years">Leo 2004–05 · Cris 2002–03</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona · La Liga debut</span></div>
      <h3 class="display">A 63-kilo secret in Barcelona</h3>
      <p>Messi makes his league debut in October 2004, aged 17 years and 3 months, in the derby against Espanyol — then one of Barça's youngest debutants ever. On 1 May 2005 he scores his first senior goal, a delicate chip against Albacete, lobbed in from Ronaldinho's flick; the Brazilian carries him on his back in celebration.</p>
      <p>He plays only 9 games and scores once, but he leaves the season with a <strong>La Liga winner's medal</strong> — a trophy before most people know his name.</p>
      <div class="chips">
        <span class="chip trophy">🏆 La Liga 2004–05</span>
        <span class="chip">First senior goal at 17y 10m</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Sporting CP · Primeira Liga</span></div>
      <h3 class="display">The kid who beat Man United alone</h3>
      <p>A whippet-thin winger with frosted tips, Ronaldo scores twice on his full Sporting debut against Moreirense and finishes his only senior season in Lisbon with 5 goals in 31 games. Every step-over is an audition.</p>
      <p>The audition that matters comes in August 2003: in a friendly to open Sporting's new stadium he torments Manchester United so badly that <strong>United's players demand Ferguson sign him on the flight home</strong>. Days later, he's a Red Devil.</p>
      <div class="chips">
        <span class="chip">5 goals for Sporting</span>
        <span class="chip">Scouted by half of Europe</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="1">0</span><div class="bar" data-goals="1"></div></div>
      <div class="half right"><div class="bar" data-goals="5"></div><span class="val numeral" data-count="5">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 18 ================= -->
<section class="age" data-age="18">
  <div class="age-head"><div class="big display">18</div><div class="years">Leo 2005–06 · Cris 2003–04</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona + Argentina U20</span></div>
      <h3 class="display">World youth champion, European champion</h3>
      <p>Summer 2005: Messi drags Argentina to the <strong>FIFA U20 World Cup title</strong>, winning both the <strong>Golden Ball and Golden Boot</strong> (6 goals, including two in the final). His senior Argentina debut in August lasts 2 minutes — a farcical red card against Hungary.</p>
      <p>At Barça he scores 8 in 25, announces himself against Chelsea in the Champions League, then tears a hamstring in March. Barcelona win the <strong>Liga and Champions League double</strong>; Messi, in tears watching the Paris final from the stands, initially refuses to celebrate a medal he feels he didn't earn.</p>
      <div class="chips">
        <span class="chip trophy">🏆 U20 World Cup</span>
        <span class="chip trophy">🏆 Champions League</span>
        <span class="chip trophy">🏆 La Liga</span>
        <span class="chip ballon">U20 Golden Ball + Boot</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Manchester United · Premier League</span></div>
      <h3 class="display">Number 7, £12.24m, first silverware</h3>
      <p>United pay <strong>£12.24m — a record for a teenager in British football</strong> — and Ferguson hands him the No. 7 of Best, Cantona and Beckham. His debut cameo against Bolton brings a standing ovation; the season brings 6 goals and endless step-overs in search of an end product.</p>
      <p>It ends with substance: Ronaldo opens the scoring with a header in the <strong>2004 FA Cup final</strong> win over Millwall — his first major trophy, aged 19 by then but earned across his age-18 season.</p>
      <div class="chips">
        <span class="chip trophy">🏆 FA Cup 2003–04</span>
        <span class="chip">Record teenage fee</span>
        <span class="chip">Inherits the United No. 7</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="8">0</span><div class="bar" data-goals="8"></div></div>
      <div class="half right"><div class="bar" data-goals="6"></div><span class="val numeral" data-count="6">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 19 ================= -->
<section class="age" data-age="19">
  <div class="age-head"><div class="big display">19</div><div class="years">Leo 2006–07 · Cris 2004–05</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona + World Cup 2006</span></div>
      <h3 class="display">The Clásico hat-trick and the Maradona goal</h3>
      <p>At the 2006 World Cup he becomes <strong>Argentina's youngest World Cup player and scorer</strong> (vs Serbia &amp; Montenegro), then watches the quarter-final loss to Germany as an unused sub — a national controversy.</p>
      <p>The club season is a one-man highlight reel in a trophyless year: a <strong>hat-trick in a 3-3 Clásico</strong> to rescue Barça three times, the <strong>slalom against Getafe</strong> that replicates Maradona's 1986 goal almost stride for stride, and even his own "Hand of God" against Espanyol. 17 goals; Real Madrid steal the league on head-to-head.</p>
      <div class="chips">
        <span class="chip">Youngest ARG World Cup scorer</span>
        <span class="chip">Clásico hat-trick at 19</span>
        <span class="chip dark">Trophyless season</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Man United + Euro 2004</span></div>
      <h3 class="display">Tears in Lisbon, growing pains in Manchester</h3>
      <p>Euro 2004, on home soil: Ronaldo scores against Greece and in the semi-final, but Portugal lose the <strong>final to Greece</strong> and the cameras find a 19-year-old sobbing on the pitch. It becomes the founding wound of his international career.</p>
      <p>At United: 9 goals, a run to the FA Cup final (lost on penalties to Arsenal), and the <strong>FIFPro Special Young Player of the Year</strong> award — promise still outrunning production.</p>
      <div class="chips">
        <span class="chip dark">Euro 2004 runner-up</span>
        <span class="chip">FIFPro Young Player award</span>
        <span class="chip dark">FA Cup final defeat</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="17">0</span><div class="bar" data-goals="17"></div></div>
      <div class="half right"><div class="bar" data-goals="9"></div><span class="val numeral" data-count="9">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 20 ================= -->
<section class="age" data-age="20">
  <div class="age-head"><div class="big display">20</div><div class="years">Leo 2007–08 · Cris 2005–06</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona + Copa América 2007</span></div>
      <h3 class="display">Podiums and pulled muscles</h3>
      <p>Argentina cruise to the <strong>Copa América 2007 final</strong> — Messi is named the tournament's best young player and scores a gorgeous chip against Mexico — then collapse 3-0 to Brazil. Second international final, second defeat.</p>
      <p>A stop-start club season (16 goals, recurring thigh injuries) as Rijkaard's era decays, but the world has noticed: Messi finishes <strong>3rd in the 2007 Ballon d'Or</strong> and 2nd for FIFA World Player — at 20, already on the podium behind Kaká and Ronaldo.</p>
      <div class="chips">
        <span class="chip">Ballon d'Or 2007 — 3rd</span>
        <span class="chip dark">Copa América runner-up</span>
        <span class="chip dark">Recurring injuries</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Man United + World Cup 2006</span></div>
      <h3 class="display">The wink</h3>
      <p>12 goals and a <strong>League Cup</strong> (with a goal in the final against Wigan) at United — but the summer defines the year. At the 2006 World Cup Portugal reach the <strong>semi-finals</strong>; in the quarter-final against England, club teammate Wayne Rooney is sent off and Ronaldo's wink to the bench makes him public enemy No. 1 in England.</p>
      <p>He returns to Manchester expecting hostility. Ferguson convinces him to stay and channel it. What follows is one of the great responses in football history.</p>
      <div class="chips">
        <span class="chip trophy">🏆 League Cup 2005–06</span>
        <span class="chip">World Cup semi-final</span>
        <span class="chip dark">Most booed man in England</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="16">0</span><div class="bar" data-goals="16"></div></div>
      <div class="half right"><div class="bar" data-goals="12"></div><span class="val numeral" data-count="12">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 21 ================= -->
<section class="age" data-age="21">
  <div class="age-head"><div class="big display">21</div><div class="years">Leo 2008–09 · Cris 2006–07</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona + Beijing Olympics</span></div>
      <h3 class="display">The first Treble — sealed against Ronaldo</h3>
      <p><strong>Olympic gold</strong> in Beijing (assist for the winner in the final), then Guardiola's first season: Messi inherits the No. 10, scores <strong>38 goals</strong>, and Barcelona win <strong>La Liga, the Copa del Rey and the Champions League</strong> — Spain's first-ever treble.</p>
      <p>In the Rome final against Manchester United, the 1.70m Messi rises above Rio Ferdinand and <strong>heads</strong> the clinching goal past Van der Sar — with Cristiano Ronaldo watching in a losing shirt. He finishes as CL top scorer (9) and Ballon d'Or runner-up... to Ronaldo.</p>
      <div class="chips">
        <span class="chip trophy">🏆 Treble: Liga + Copa + UCL</span>
        <span class="chip trophy">🏆 Olympic gold 2008</span>
        <span class="chip boot">UCL top scorer (9)</span>
        <span class="chip">Ballon d'Or 2008 — 2nd</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Manchester United · Premier League</span></div>
      <h3 class="display">From show pony to superstar</h3>
      <p>The breakout. <strong>23 goals</strong>, a first <strong>Premier League title</strong>, and a near-unprecedented awards sweep: <strong>PFA Player of the Year, PFA Young Player of the Year and FWA Footballer of the Year</strong> — the first man to win both PFA awards in the same season since 1977.</p>
      <p>The booing never stopped; the goals simply drowned it out. He ends 2007 as <strong>Ballon d'Or runner-up</strong> to Kaká, one place ahead of a certain Argentine.</p>
      <div class="chips">
        <span class="chip trophy">🏆 Premier League 2006–07</span>
        <span class="chip">PFA POTY + Young POTY</span>
        <span class="chip">Ballon d'Or 2007 — 2nd</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="38">0</span><div class="bar" data-goals="38"></div></div>
      <div class="half right"><div class="bar" data-goals="23"></div><span class="val numeral" data-count="23">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 22 ================= -->
<section class="age" data-age="22">
  <div class="age-head"><div class="big display">22</div><div class="years">Leo 2009–10 · Cris 2007–08</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona · the sextuple year</span></div>
      <h3 class="display">First Ballon d'Or, six trophies in one year</h3>
      <p>Barça complete an unprecedented <strong>sextuple</strong> across 2009: Messi chests in the winner in the <strong>Club World Cup final</strong>, adds the UEFA Super Cup and Spanish Supercup, then retains <strong>La Liga</strong> with a career-best <strong>47 goals</strong>.</p>
      <p>He wins his <strong>first Pichichi (34) and first European Golden Shoe</strong>, is Champions League top scorer again — four in one night against Arsenal — and takes his <strong>first Ballon d'Or (2009) by a record margin</strong>, plus FIFA World Player of the Year.</p>
      <div class="chips">
        <span class="chip ballon">★ Ballon d'Or 2009</span>
        <span class="chip boot">Golden Shoe + Pichichi (34)</span>
        <span class="chip trophy">🏆 La Liga</span>
        <span class="chip trophy">🏆 Club World Cup</span>
        <span class="chip boot">UCL top scorer (8)</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Man United · Premier League + UCL double</span></div>
      <h3 class="display">42 goals from the wing — and the Ballon d'Or</h3>
      <p>Ronaldo's masterpiece season: <strong>42 goals</strong>, an absurd total for a winger, with <strong>31 in the league</strong> to take the <strong>Premier League Golden Boot and the European Golden Shoe</strong>. United retain the title.</p>
      <p>In the rain of Moscow he heads United ahead in the <strong>Champions League final</strong>, misses in the shootout, weeps, and is rescued by John Terry's slip. Champion of Europe at 23; by December, the <strong>2008 Ballon d'Or and FIFA World Player of the Year</strong> follow.</p>
      <div class="chips">
        <span class="chip ballon">★ Ballon d'Or 2008</span>
        <span class="chip boot">Golden Shoe + PL Golden Boot (31)</span>
        <span class="chip trophy">🏆 Champions League</span>
        <span class="chip trophy">🏆 Premier League</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="47">0</span><div class="bar" data-goals="47"></div></div>
      <div class="half right"><div class="bar" data-goals="42"></div><span class="val numeral" data-count="42">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 23 ================= -->
<section class="age" data-age="23">
  <div class="age-head"><div class="big display">23</div><div class="years">Leo 2010–11 · Cris 2008–09</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona + World Cup 2010</span></div>
      <h3 class="display">Wembley, and the all-Barça podium</h3>
      <p>The World Cup in South Africa is a blank — quarter-final humiliation by Germany under Maradona, zero goals — and yet Messi wins the <strong>first FIFA Ballon d'Or (2010)</strong> anyway, ahead of Iniesta and Xavi in an all-Barcelona podium that enrages half the football world.</p>
      <p>The club season justifies it: <strong>53 goals</strong>, another <strong>La Liga</strong>, and a Champions League final masterclass at Wembley — man of the match, the killer goal against United again, and <strong>12 UCL goals</strong> to lead the competition a third straight year.</p>
      <div class="chips">
        <span class="chip ballon">★ Ballon d'Or 2010</span>
        <span class="chip trophy">🏆 Champions League</span>
        <span class="chip trophy">🏆 La Liga</span>
        <span class="chip boot">UCL top scorer (12)</span>
        <span class="chip dark">World Cup QF, 0 goals</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Man United → Real Madrid, €94m</span></div>
      <h3 class="display">Three-peat, then the world-record move</h3>
      <p>A third straight <strong>Premier League title</strong>, a <strong>League Cup</strong>, the <strong>Club World Cup</strong>, and the small matter of collecting the <strong>2008 Ballon d'Or</strong> in December. The one blemish is enormous: the 2009 Champions League final in Rome, where Messi's Barcelona dismantle United.</p>
      <p>Weeks later, Real Madrid pay a <strong>world-record €94m</strong>. Eighty thousand people attend his Bernabéu unveiling. The rivalry now has one stage: Spain.</p>
      <div class="chips">
        <span class="chip trophy">🏆 Premier League (3rd straight)</span>
        <span class="chip trophy">🏆 Club World Cup</span>
        <span class="chip ballon">★ Ballon d'Or 2008 (awarded Dec)</span>
        <span class="chip dark">UCL final loss to Messi's Barça</span>
        <span class="chip">World-record €94m transfer</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="53">0</span><div class="bar" data-goals="53"></div></div>
      <div class="half right"><div class="bar" data-goals="26"></div><span class="val numeral" data-count="26">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 24 ================= -->
<section class="age" data-age="24">
  <div class="age-head"><div class="big display">24</div><div class="years">Leo 2011–12 · Cris 2009–10</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona · the 73-goal season</span></div>
      <h3 class="display">73 goals. Seventy-three.</h3>
      <p>The most prolific single season in the history of Europe's top leagues: <strong>73 goals in all competitions</strong>, including <strong>50 in La Liga</strong> (still the record), <strong>five in one Champions League match</strong> against Leverkusen — a first — and 14 in the UCL overall. In March he passes César Rodríguez to become <strong>Barcelona's all-time top scorer, at 24</strong>.</p>
      <p>A third straight <strong>Ballon d'Or</strong>, another Golden Shoe, plus the Copa del Rey, Club World Cup and two Super Cups. The asterisks: Madrid take the league, Chelsea knock Barça out of the UCL — Messi's penalty clangs off the bar — and Copa América 2011 ends in a home-soil quarter-final shootout loss.</p>
      <div class="chips">
        <span class="chip ballon">★ Ballon d'Or 2011</span>
        <span class="chip boot">Golden Shoe (50 league goals)</span>
        <span class="chip trophy">🏆 Copa del Rey + Club WC</span>
        <span class="chip">Barça all-time top scorer at 24</span>
        <span class="chip dark">Copa América QF exit</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Real Madrid · debut season</span></div>
      <h3 class="display">33 goals, zero trophies, total war begins</h3>
      <p>Ronaldo's first year in white is individually superb — <strong>33 goals in 35 games</strong> — and collectively barren: Barcelona retain La Liga with 99 points, and Madrid fall to Lyon in the Champions League last 16.</p>
      <p>He finishes <strong>runner-up to Messi in the 2009 Ballon d'Or</strong>. It is the first of many silver medals in the Messi era — and the fuel for everything that follows.</p>
      <div class="chips">
        <span class="chip">33 goals in 35 apps</span>
        <span class="chip">Ballon d'Or 2009 — 2nd</span>
        <span class="chip dark">Trophyless debut season</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="73">0</span><div class="bar" data-goals="73"></div></div>
      <div class="half right"><div class="bar" data-goals="33"></div><span class="val numeral" data-count="33">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 25 ================= -->
<section class="age" data-age="25">
  <div class="age-head"><div class="big display">25</div><div class="years">Leo 2012–13 · Cris 2010–11</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona · 91 goals in a calendar year</span></div>
      <h3 class="display">The Gerd Müller record falls</h3>
      <p>Calendar year 2012 closes with <strong>91 goals for club and country</strong> — past Gerd Müller's 85, a Guinness world record — and a <strong>fourth consecutive Ballon d'Or</strong>, something no player had ever done.</p>
      <p>2012–13: <strong>60 goals</strong>, a <strong>La Liga title with 100 points</strong>, 46 league goals for another <strong>Pichichi and Golden Shoe</strong>, and a run of scoring against all 19 league opponents in consecutive games. Spring turns sour: hamstring trouble, and a 7-0 aggregate Champions League semi-final demolition by Bayern.</p>
      <div class="chips">
        <span class="chip ballon">★ Ballon d'Or 2012 (4th straight)</span>
        <span class="chip">91 goals in 2012 — world record</span>
        <span class="chip trophy">🏆 La Liga (100 pts)</span>
        <span class="chip boot">Golden Shoe + Pichichi (46)</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Real Madrid + World Cup 2010</span></div>
      <h3 class="display">40 league goals and a trophy off Barça's head</h3>
      <p>The 2010 World Cup ends in a last-16 exit to eventual champions Spain (one goal, against North Korea). The club response under Mourinho is ferocious: <strong>53 goals</strong>, including a then-record <strong>40 in La Liga</strong> for his first <strong>Pichichi and second Golden Shoe</strong> — outscoring even Messi.</p>
      <p>And in the Copa del Rey final, in extra time, Ronaldo climbs above Barcelona's defence and <strong>heads home the only goal</strong> — his first trophy in Spain, taken directly off his rival's team.</p>
      <div class="chips">
        <span class="chip trophy">🏆 Copa del Rey (winner vs Barça)</span>
        <span class="chip boot">Golden Shoe + Pichichi (40)</span>
        <span class="chip dark">World Cup R16 exit</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="60">0</span><div class="bar" data-goals="60"></div></div>
      <div class="half right"><div class="bar" data-goals="53"></div><span class="val numeral" data-count="53">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 26 ================= -->
<section class="age" data-age="26">
  <div class="age-head"><div class="big display">26</div><div class="years">Leo 2013–14 · Cris 2011–12</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona · the injury year</span></div>
      <h3 class="display">The first wobble</h3>
      <p>Three separate hamstring injuries limit Messi to <strong>41 goals</strong> — a down year only by his standards — and for the first time since 2008 he wins nothing: La Liga lost to Atlético on the final day, the Copa final lost to Madrid, no Champions League.</p>
      <p>He cedes the Pichichi to Ronaldo, finishes <strong>2nd in the 2013 Ballon d'Or</strong>, and whispers begin — prematurely — that the machine is slowing.</p>
      <div class="chips">
        <span class="chip dark">Trophyless season</span>
        <span class="chip">Ballon d'Or 2013 — 2nd</span>
        <span class="chip dark">3 hamstring injuries</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Real Madrid · La Liga champions</span></div>
      <h3 class="display">100 points, 121 goals, a league wrestled back</h3>
      <p>Mourinho's Madrid finally break Guardiola's Barcelona: a <strong>La Liga title with 100 points and 121 goals</strong>, both records at the time. Ronaldo contributes <strong>46 league goals and 60 in all competitions</strong>, scoring in six consecutive Clásicos along the way.</p>
      <p>Remarkably, 46 league goals win him nothing individual — Messi scored 50. It is the definitive snapshot of the era: historic numbers, and still second. Ballon d'Or 2011: runner-up again.</p>
      <div class="chips">
        <span class="chip trophy">🏆 La Liga (100 pts)</span>
        <span class="chip">60 goals — no Golden Shoe (Messi: 50)</span>
        <span class="chip">Ballon d'Or 2011 — 2nd</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="41">0</span><div class="bar" data-goals="41"></div></div>
      <div class="half right"><div class="bar" data-goals="60"></div><span class="val numeral" data-count="60">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 27 ================= -->
<section class="age" data-age="27">
  <div class="age-head"><div class="big display">27</div><div class="years">Leo 2014–15 · Cris 2012–13</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona + World Cup 2014</span></div>
      <h3 class="display">Heartbreak at the Maracanã, then a second Treble</h3>
      <p>Brazil 2014: Messi carries Argentina to the <strong>World Cup final</strong> — four goals, four man-of-the-match awards — then watches Götze's volley win it for Germany in extra time. He collects the <strong>Golden Ball</strong> looking like a man at a funeral.</p>
      <p>The response is the MSN season: a <strong>second Treble</strong> (Liga, Copa, Champions League), <strong>58 goals</strong>, the slalom Copa-final goal against Athletic, and the night in the UCL semi he sits Jérôme Boateng down and chips Neuer. He also becomes <strong>La Liga's all-time top scorer</strong>, passing Zarra's 251.</p>
      <div class="chips">
        <span class="chip trophy">🏆 Treble #2: Liga + Copa + UCL</span>
        <span class="chip ballon">World Cup Golden Ball</span>
        <span class="chip dark">World Cup final defeat</span>
        <span class="chip boot">UCL joint top scorer (10)</span>
        <span class="chip">La Liga all-time top scorer</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Real Madrid + Euro 2012</span></div>
      <h3 class="display">55 goals in a season of near-misses</h3>
      <p>Euro 2012: three goals and a semi-final against Spain that ends on penalties — Ronaldo, saved for the decisive fifth kick, never gets to take one. The debate rages for years.</p>
      <p>2012–13 brings <strong>55 goals</strong> and a Supercopa, but Madrid lose the league to Barça, the Copa final to Atlético, and a UCL semi to Dortmund. He is Ballon d'Or runner-up for 2012, his third silver in four years — and by season's end, Mourinho is gone.</p>
      <div class="chips">
        <span class="chip">Euro 2012 semi-final</span>
        <span class="chip trophy">🏆 Supercopa de España</span>
        <span class="chip">Ballon d'Or 2012 — 2nd</span>
        <span class="chip boot">UCL joint top scorer (12)</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="58">0</span><div class="bar" data-goals="58"></div></div>
      <div class="half right"><div class="bar" data-goals="55"></div><span class="val numeral" data-count="55">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 28 ================= -->
<section class="age" data-age="28">
  <div class="age-head"><div class="big display">28</div><div class="years">Leo 2015–16 · Cris 2013–14</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona + Copa América 2015</span></div>
      <h3 class="display">A fifth Ballon d'Or — and more penalties, more pain</h3>
      <p>Chile 2015: another final, another defeat — Argentina lose the <strong>Copa América final on penalties</strong>. Messi reportedly refuses the tournament's best-player award.</p>
      <p>At Barça: <strong>41 goals</strong> despite a knee ligament tear, a <strong>Liga + Copa double</strong>, the UEFA Super Cup and Club World Cup to complete the MSN trophy sweep, his <strong>500th career goal</strong>, and the audacious tap-across penalty "assist" to Suárez against Celta. December brings <strong>Ballon d'Or No. 5</strong>, reclaimed from Ronaldo.</p>
      <div class="chips">
        <span class="chip ballon">★ Ballon d'Or 2015</span>
        <span class="chip trophy">🏆 La Liga + Copa del Rey</span>
        <span class="chip trophy">🏆 Club World Cup</span>
        <span class="chip dark">Copa América final loss (pens)</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Real Madrid · La Décima</span></div>
      <h3 class="display">La Décima and the tearful Ballon d'Or</h3>
      <p>November 2013: a one-man <strong>World Cup playoff hat-trick against Ibrahimović's Sweden</strong> drags Portugal to Brazil. January 2014: he wins the <strong>2013 Ballon d'Or</strong> — his first for five years — and cries on stage, son in his arms, ending Messi's four-year monopoly.</p>
      <p>Then the crown: Madrid's obsession, <strong>La Décima</strong> — a tenth European Cup — won in Lisbon against Atlético, with Ronaldo scoring the final penalty and setting a <strong>Champions League single-season record of 17 goals</strong> that still stands. <strong>51 goals</strong>, plus the Copa del Rey.</p>
      <div class="chips">
        <span class="chip ballon">★ Ballon d'Or 2013</span>
        <span class="chip trophy">🏆 Champions League (La Décima)</span>
        <span class="chip trophy">🏆 Copa del Rey</span>
        <span class="chip boot">Record 17 UCL goals</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="41">0</span><div class="bar" data-goals="41"></div></div>
      <div class="half right"><div class="bar" data-goals="51"></div><span class="val numeral" data-count="51">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 29 ================= -->
<section class="age" data-age="29">
  <div class="age-head"><div class="big display">29</div><div class="years">Leo 2016–17 · Cris 2014–15</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona + Copa América Centenario</span></div>
      <h3 class="display">"I'm done with the national team"</h3>
      <p>June 2016: a <strong>third consecutive final defeat</strong> — Chile again, penalties again, and this time Messi blazes his kick over. In the mixed zone he announces his <strong>international retirement</strong>. Argentina begs; murals go up; weeks later, he returns.</p>
      <p>The club year is defiant: <strong>54 goals</strong>, a <strong>Pichichi (37)</strong>, the Copa del Rey, and the iconic Clásico moment — a 92nd-minute winner at the Bernabéu, his <strong>500th Barcelona goal</strong>, celebrated by holding his shirt up to the Madrid crowd.</p>
      <div class="chips">
        <span class="chip dark">Copa América final loss #3</span>
        <span class="chip dark">Brief international retirement</span>
        <span class="chip trophy">🏆 Copa del Rey</span>
        <span class="chip boot">Pichichi (37)</span>
        <span class="chip">500th Barça goal, at the Bernabéu</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Real Madrid + World Cup 2014</span></div>
      <h3 class="display">61 goals — his Everest</h3>
      <p>The 2014 World Cup is a write-off: playing through a knee injury, one goal, group-stage exit. The season is anything but: a career-high <strong>61 goals</strong>, a <strong>record 48 in La Liga</strong> for the Pichichi and a <strong>fourth Golden Shoe</strong>, plus the UEFA Super Cup and Club World Cup.</p>
      <p>January 2015: <strong>Ballon d'Or 2014</strong>, back to back, his third overall — punctuated by the infamous "¡Siii!" scream on stage. Madrid win no league or UCL, but no one on earth is scoring like him.</p>
      <div class="chips">
        <span class="chip ballon">★ Ballon d'Or 2014</span>
        <span class="chip boot">Golden Shoe + Pichichi (48)</span>
        <span class="chip trophy">🏆 Club World Cup</span>
        <span class="chip dark">World Cup group exit</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="54">0</span><div class="bar" data-goals="54"></div></div>
      <div class="half right"><div class="bar" data-goals="61"></div><span class="val numeral" data-count="61">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 30 ================= -->
<section class="age" data-age="30">
  <div class="age-head"><div class="big display">30</div><div class="years">Leo 2017–18 · Cris 2015–16</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona · domestic double</span></div>
      <h3 class="display">An unbeaten league, carried on one back</h3>
      <p>With Neymar gone, Messi drags a transitional Barça to a <strong>Liga + Copa double</strong>, going 43 league games unbeaten across the campaign. <strong>45 goals</strong>, another <strong>Pichichi and a record fifth Golden Shoe (34)</strong>.</p>
      <p>The scars are European — a shock UCL quarter-final collapse at Roma — but at 30, in a team being rebuilt around him, he remains the league's dominant force.</p>
      <div class="chips">
        <span class="chip trophy">🏆 La Liga + Copa del Rey</span>
        <span class="chip boot">Golden Shoe + Pichichi (34)</span>
        <span class="chip dark">UCL QF collapse vs Roma</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Real Madrid · La Undécima</span></div>
      <h3 class="display">The penalty that won Europe — again</h3>
      <p>Zidane arrives mid-season and Madrid win the <strong>Champions League (La Undécima)</strong> in Milan — Atlético again, penalties again, and Ronaldo, of course, buries the winning kick, ripping his shirt off in the now-iconic pose.</p>
      <p><strong>51 goals</strong>, and a <strong>record 16 in the Champions League</strong> to top the competition's scoring for a fifth season running. The greatest summer of his life is still one page away.</p>
      <div class="chips">
        <span class="chip trophy">🏆 Champions League</span>
        <span class="chip boot">UCL top scorer (16)</span>
        <span class="chip">Winning penalty in the final</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="45">0</span><div class="bar" data-goals="45"></div></div>
      <div class="half right"><div class="bar" data-goals="51"></div><span class="val numeral" data-count="51">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 31 ================= -->
<section class="age" data-age="31">
  <div class="age-head"><div class="big display">31</div><div class="years">Leo 2018–19 · Cris 2016–17</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona (captain) + World Cup 2018</span></div>
      <h3 class="display">A new armband, an old wound reopened</h3>
      <p>Russia 2018 ends in the last 16 against eventual champions France — one goal, against Nigeria, in a chaotic Argentina campaign. Named <strong>Barcelona captain</strong>, he answers with <strong>51 goals</strong>, another <strong>La Liga title</strong>, a <strong>third straight Golden Shoe (36)</strong> and the <strong>Champions League top scorer</strong> crown (12) — including a legendary free-kick against Liverpool.</p>
      <p>Then Anfield: a 3-0 lead becomes a 4-0 second-leg collapse, one of the most painful nights of his career. Copa América 2019 adds a semi-final loss to Brazil and a red card in the third-place game.</p>
      <div class="chips">
        <span class="chip trophy">🏆 La Liga</span>
        <span class="chip boot">Golden Shoe + Pichichi (36)</span>
        <span class="chip boot">UCL top scorer (12)</span>
        <span class="chip dark">Anfield 0-4 collapse</span>
        <span class="chip dark">World Cup R16 exit</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Real Madrid + EURO 2016 CHAMPION</span></div>
      <h3 class="display">Portugal's ghost is exorcised</h3>
      <p>Paris, July 2016: Ronaldo is scythed down after 8 minutes of the <strong>Euro 2016 final</strong>, leaves in tears on a stretcher — and then coaches the team from the touchline like a man possessed as Éder's strike wins <strong>Portugal's first-ever major trophy</strong>.</p>
      <p>The club year completes the sweep: back-to-back <strong>Champions Leagues (La Duodécima)</strong> with two goals in the final against Juventus, a first <strong>La Liga since 2012</strong>, and UCL top scorer again. December: <strong>Ballon d'Or 2016</strong>. He is, briefly, indisputably No. 1.</p>
      <div class="chips">
        <span class="chip trophy">🏆 EURO 2016</span>
        <span class="chip trophy">🏆 Champions League + La Liga</span>
        <span class="chip ballon">★ Ballon d'Or 2016</span>
        <span class="chip boot">UCL top scorer (12)</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="51">0</span><div class="bar" data-goals="51"></div></div>
      <div class="half right"><div class="bar" data-goals="42"></div><span class="val numeral" data-count="42">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 32 ================= -->
<section class="age" data-age="32">
  <div class="age-head"><div class="big display">32</div><div class="years">Leo 2019–20 · Cris 2017–18</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona · the collapse</span></div>
      <h3 class="display">A sixth Ballon d'Or as the walls cave in</h3>
      <p>December 2019: <strong>Ballon d'Or No. 6</strong>, breaking his tie with Ronaldo, plus <strong>FIFA The Best</strong>. On the pitch: <strong>31 goals</strong> and a sixth <strong>Pichichi (25)</strong> in the pandemic-shortened season.</p>
      <p>Institutionally, Barcelona is burning: the league is lost, and the Champions League ends in the <strong>8-2 annihilation by Bayern</strong>. Weeks later Messi sends the infamous <strong>burofax</strong> demanding to leave. Blocked by his contract, he stays — furious.</p>
      <div class="chips">
        <span class="chip ballon">★ Ballon d'Or 2019 (6th)</span>
        <span class="chip boot">Pichichi (25)</span>
        <span class="chip dark">Bayern 8-2</span>
        <span class="chip dark">The burofax</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Real Madrid · the three-peat</span></div>
      <h3 class="display">The bicycle kick Juventus applauded</h3>
      <p>The Champions League becomes his personal property: a <strong>third consecutive title</strong> (and 5th overall), <strong>15 UCL goals</strong> for a sixth straight top-scorer crown, and in Turin, the <strong>overhead kick against Juventus</strong> so outrageous the home fans stand and applaud. December 2017: <strong>Ballon d'Or No. 5</strong>, level with Messi.</p>
      <p>The 2018 World Cup opens with a <strong>hat-trick against Spain</strong> — capped by a stoppage-time free kick — before a last-16 exit to Uruguay. Days later, at 33, he shocks Madrid by joining <strong>Juventus for €100m</strong>.</p>
      <div class="chips">
        <span class="chip trophy">🏆 Champions League 3-peat</span>
        <span class="chip ballon">★ Ballon d'Or 2017 (5th)</span>
        <span class="chip boot">UCL top scorer (15)</span>
        <span class="chip">WC hat-trick vs Spain</span>
        <span class="chip">€100m to Juventus at 33</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="31">0</span><div class="bar" data-goals="31"></div></div>
      <div class="half right"><div class="bar" data-goals="44"></div><span class="val numeral" data-count="44">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 33 ================= -->
<section class="age" data-age="33">
  <div class="age-head"><div class="big display">33</div><div class="years">Leo 2020–21 · Cris 2018–19</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Barcelona · the final season</span></div>
      <h3 class="display">One last trophy in blaugrana</h3>
      <p>Forced to stay after the burofax, Messi still delivers: <strong>38 goals</strong>, a seventh <strong>Pichichi (30)</strong>, and a masterful two-goal performance in the <strong>Copa del Rey final</strong> — his <strong>35th and final Barcelona trophy</strong>. He also passes Xavi as Barça's all-time appearance maker.</p>
      <p>No one yet knows it's a farewell tour. The Copa América awaits in the summer — and everything is about to change.</p>
      <div class="chips">
        <span class="chip trophy">🏆 Copa del Rey (35th Barça trophy)</span>
        <span class="chip boot">Pichichi (30)</span>
        <span class="chip">Barça all-time appearance record</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Juventus + Nations League</span></div>
      <h3 class="display">Conquering a third league</h3>
      <p>Juventus debut season: <strong>28 goals</strong>, the <strong>Serie A title</strong>, the Supercoppa, and the inaugural <strong>Serie A MVP award</strong> — league champion now in England, Spain and Italy. In the UCL he single-handedly overturns Atlético with a last-16 hat-trick before a quarter-final exit to Ajax.</p>
      <p>June 2019: he opens the <strong>Nations League</strong> semi-final with a hat-trick against Switzerland and Portugal lift the inaugural trophy on home soil — international title No. 2.</p>
      <div class="chips">
        <span class="chip trophy">🏆 Serie A + Supercoppa</span>
        <span class="chip trophy">🏆 UEFA Nations League 2019</span>
        <span class="chip">Serie A MVP</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="38">0</span><div class="bar" data-goals="38"></div></div>
      <div class="half right"><div class="bar" data-goals="28"></div><span class="val numeral" data-count="28">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 34 ================= -->
<section class="age" data-age="34">
  <div class="age-head"><div class="big display">34</div><div class="years">Leo 2021–22 · Cris 2019–20</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Copa América champion → PSG</span></div>
      <h3 class="display">Maracanã redemption — then tears at a podium</h3>
      <p>10 July 2021: Argentina beat Brazil at the Maracanã and Messi wins the <strong>Copa América — his first senior international trophy after four final defeats</strong>, taking the tournament's best player and top scorer awards (4 goals, 5 assists). His teammates hoist him like a nation exhaling.</p>
      <p>Weeks later, La Liga's salary rules make the unthinkable real: a sobbing Messi leaves Barcelona and signs for <strong>PSG</strong>. The first Paris season is his leanest in 15 years — a <strong>Ligue 1 title</strong> but only 11 goals (with 14 assists) and whistles at the Parc. Still: <strong>Ballon d'Or No. 7</strong> in December 2021.</p>
      <div class="chips">
        <span class="chip trophy">🏆 COPA AMÉRICA 2021</span>
        <span class="chip ballon">★ Ballon d'Or 2021 (7th)</span>
        <span class="chip trophy">🏆 Ligue 1</span>
        <span class="chip dark">Leaves Barcelona in tears</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Juventus · Serie A back-to-back</span></div>
      <h3 class="display">Still the machine in Turin</h3>
      <p>A second straight <strong>Serie A title</strong> in the COVID-interrupted season, with <strong>31 league goals</strong> — the first player ever to hit 25+ in a season in England, Spain and Italy. 37 in all competitions.</p>
      <p>The frustrations are familiar: a Coppa Italia final lost on penalties and a limp Champions League exit to Lyon. The numbers refuse to age; the team around him does.</p>
      <div class="chips">
        <span class="chip trophy">🏆 Serie A (2nd straight)</span>
        <span class="chip">31 league goals at 35</span>
        <span class="chip dark">UCL R16 exit</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="11">0</span><div class="bar" data-goals="11"></div></div>
      <div class="half right"><div class="bar" data-goals="37"></div><span class="val numeral" data-count="37">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 35 ================= -->
<section class="age" data-age="35">
  <div class="age-head"><div class="big display">35</div><div class="years">Leo 2022–23 · Cris 2020–21</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">PSG + WORLD CUP 2022 CHAMPION</span></div>
      <h3 class="display">Lusail. The greatest final. The crown.</h3>
      <p>18 December 2022: Messi wins the <strong>World Cup</strong>. Seven goals, three assists, a goal in <strong>every knockout round</strong> (a first in a single World Cup), two in an all-time-great final against Mbappé's France, and a converted penalty in the shootout. He becomes the <strong>first two-time World Cup Golden Ball winner</strong>. The GOAT debate, for hundreds of millions, closes that night.</p>
      <p>He also wins the <strong>Finalissima</strong> against Italy that June, retains <strong>Ligue 1</strong> with 21 goals and 20 assists, and takes <strong>FIFA The Best 2022</strong>. The PSG marriage still sours — boos, a brief suspension — and in June 2023 he stuns everyone by choosing <strong>Inter Miami</strong>.</p>
      <div class="chips">
        <span class="chip trophy">🏆 WORLD CUP 2022</span>
        <span class="chip ballon">WC Golden Ball (2nd time)</span>
        <span class="chip trophy">🏆 Finalissima + Ligue 1</span>
        <span class="chip">FIFA The Best 2022</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Juventus · Capocannoniere</span></div>
      <h3 class="display">Top scorer in a third country</h3>
      <p><strong>29 league goals</strong> make him Serie A's <strong>Capocannoniere</strong> — completing top-scorer titles in England, Spain and Italy — alongside the Coppa Italia and Supercoppa. He passes Pelé's official career goal tally along the way.</p>
      <p>But Juve slump to fourth and exit the UCL in the last 16 again. In September 2021 he scores twice against Ireland to become <strong>men's international football's all-time top scorer</strong>, passing Ali Daei's 109.</p>
      <div class="chips">
        <span class="chip boot">Capocannoniere (29)</span>
        <span class="chip trophy">🏆 Coppa Italia + Supercoppa</span>
        <span class="chip">All-time int'l top scorer (111+)</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="21">0</span><div class="bar" data-goals="21"></div></div>
      <div class="half right"><div class="bar" data-goals="36"></div><span class="val numeral" data-count="36">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 36 ================= -->
<section class="age" data-age="36">
  <div class="age-head"><div class="big display">36</div><div class="years">Leo 2023–24 · Cris 2021–22</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Inter Miami · the American landing</span></div>
      <h3 class="display">An eighth Ballon d'Or, a pink revolution</h3>
      <p>Messi's Miami debut is cinema: a stoppage-time free-kick winner, then <strong>10 goals in 7 games</strong> to win the <strong>2023 Leagues Cup — the club's first-ever trophy</strong>. MLS attendance, shirt sales and streaming numbers explode.</p>
      <p>October 2023: <strong>Ballon d'Or No. 8</strong>, for the World Cup year, plus <strong>FIFA The Best 2023</strong> and TIME Athlete of the Year. He begins 2024 by leading Miami to the top of MLS.</p>
      <div class="chips">
        <span class="chip ballon">★ Ballon d'Or 2023 (8th)</span>
        <span class="chip trophy">🏆 Leagues Cup 2023</span>
        <span class="chip">FIFA The Best 2023</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Man United return + Euro 2020</span></div>
      <h3 class="display">Homecoming, and the Golden Boot at 36</h3>
      <p>At <strong>Euro 2020</strong> (played 2021) Ronaldo wins the tournament <strong>Golden Boot with 5 goals</strong> despite a last-16 exit — at 36, top scorer of a major international tournament.</p>
      <p>Then the fairytale: back to <strong>Manchester United</strong>. Two goals on his re-debut, dramatic UCL winners, <strong>24 goals</strong> and three Premier League Player of the Month awards in a dismal 6th-place team. Individually remarkable; collectively, the cracks are showing.</p>
      <div class="chips">
        <span class="chip boot">Euro 2020 Golden Boot (5)</span>
        <span class="chip">Return to Old Trafford</span>
        <span class="chip">24 goals in a broken team</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="25">0</span><div class="bar" data-goals="25"></div></div>
      <div class="half right"><div class="bar" data-goals="24"></div><span class="val numeral" data-count="24">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 37 ================= -->
<section class="age" data-age="37">
  <div class="age-head"><div class="big display">37</div><div class="years">Leo 2024–25 · Cris 2022–23</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Inter Miami + Copa América 2024</span></div>
      <h3 class="display">Back-to-back Copas and a record-breaking Shield</h3>
      <p>Summer 2024: Argentina retain the <strong>Copa América</strong>, beating Colombia in the final while Messi weeps on the bench with an injured ankle — his second Copa, alongside a World Cup, in three years.</p>
      <p>In MLS, Miami win the <strong>Supporters' Shield with a league-record 74 points</strong>; Messi takes <strong>2024 MLS MVP</strong> with 20 goals in 19 regular-season games. The asterisk: a shock first-round playoff exit to Atlanta United.</p>
      <div class="chips">
        <span class="chip trophy">🏆 Copa América 2024</span>
        <span class="chip trophy">🏆 Supporters' Shield (record 74 pts)</span>
        <span class="chip ballon">MLS MVP 2024</span>
        <span class="chip dark">Playoff round-one exit</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Man United exit → Al-Nassr + WC 2022</span></div>
      <h3 class="display">The interview, the bench, the pivot east</h3>
      <p>The darkest stretch: frozen out under Ten Hag, Ronaldo gives the incendiary <strong>Piers Morgan interview</strong> and United <strong>terminate his contract</strong> mid–World Cup. In Qatar he becomes the <strong>first man to score at five World Cups</strong> (penalty vs Ghana) — then is benched for the knockouts and exits the quarter-final against Morocco in tears.</p>
      <p>January 2023: he signs for <strong>Al-Nassr</strong> on the largest contract in football history (reported ~€200m/year), instantly rewiring the sport's economics and putting Saudi football on the map. 14 goals arrive in his first half-season.</p>
      <div class="chips">
        <span class="chip">First to score at 5 World Cups</span>
        <span class="chip dark">United contract terminated</span>
        <span class="chip dark">WC quarter-final, benched</span>
        <span class="chip">Record contract at Al-Nassr</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="33">0</span><div class="bar" data-goals="33"></div></div>
      <div class="half right"><div class="bar" data-goals="17"></div><span class="val numeral" data-count="17">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 38 ================= -->
<section class="age" data-age="38">
  <div class="age-head"><div class="big display">38</div><div class="years">Leo 2025 · Cris 2023–24</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Inter Miami · MLS Cup champion</span></div>
      <h3 class="display">The MLS Golden Boot — and finally, the Cup</h3>
      <p>The most complete American season imaginable: the <strong>2025 MLS Golden Boot (29 goals)</strong>, a second straight <strong>MLS MVP</strong>, his 60th career hat-trick on the final day of the regular season — and then a playoff run that ends with Miami lifting the <strong>2025 MLS Cup, the club's first</strong>.</p>
      <p>At the expanded Club World Cup, Miami beat Porto — a landmark first competitive win for an MLS side over a European power. Old friends Jordi Alba and Sergio Busquets retire at season's end; the last dance approaches.</p>
      <div class="chips">
        <span class="chip trophy">🏆 MLS CUP 2025</span>
        <span class="chip boot">MLS Golden Boot (29)</span>
        <span class="chip ballon">MLS MVP (back-to-back)</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Al-Nassr · the goals never stop</span></div>
      <h3 class="display">50 goals at 38 — top scorer on the planet</h3>
      <p>His first full Saudi season is a scoring monsoon: <strong>a record 35 Saudi Pro League goals</strong> to win the league's Golden Boot, roughly <strong>50 in all competitions</strong>, and more goals in calendar 2023 than any player on earth. He lifts the <strong>Arab Club Champions Cup</strong> in August 2023.</p>
      <p>The frustration: no league title, and a King's Cup final lost on penalties to Al-Hilal. The goals are historic; the silverware drought at Al-Nassr becomes the storyline.</p>
      <div class="chips">
        <span class="chip trophy">🏆 Arab Club Champions Cup</span>
        <span class="chip boot">SPL Golden Boot (record 35)</span>
        <span class="chip">World's top scorer, 2023</span>
        <span class="chip dark">Cup final loss on pens</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals that season</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="43">0</span><div class="bar" data-goals="43"></div></div>
      <div class="half right"><div class="bar" data-goals="50"></div><span class="val numeral" data-count="50">0</span></div>
    </div>
  </div>
</section>

<!-- ================= AGE 39/40 ================= -->
<section class="age" data-age="39">
  <div class="age-head"><div class="big display">39–40</div><div class="years">Leo 2026 · Cris 2024–26</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Inter Miami · just turned 39</span></div>
      <h3 class="display">One more summer</h3>
      <p>Messi turned 39 on 24 June 2026 — mid-World Cup. His 2026 club season began quietly (a rebuilt Miami without Alba, Busquets, or coach Mascherano), because everything has been pointed at one thing: a <strong>sixth World Cup</strong>, a record no outfield player has ever touched.</p>
      <p>The story of his age 39 is being written right now — see below.</p>
      <div class="chips">
        <span class="chip">Record 6th World Cup</span>
        <span class="chip">~916 career goals</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Al-Nassr · ages 39–40</span></div>
      <h3 class="display">A second Nations League, and the Saudi title at last</h3>
      <p>Age 39 (2024–25): another <strong>SPL top-scorer season (25)</strong>, his <strong>900th career goal</strong>, but Al-Nassr again finish empty-handed. Age 40 changes the script: in June 2025 he scores in the semi and final as Portugal win a <strong>second UEFA Nations League</strong>, beating Spain on penalties.</p>
      <p>Then, in 2025–26, with ~30 more goals, Al-Nassr finally win the <strong>Saudi Pro League</strong> — Ronaldo's first Saudi title and a fourth different country in which he's been champion. Career total: roughly <strong>973 goals</strong>, with the mythical 1,000 now within sight.</p>
      <div class="chips">
        <span class="chip trophy">🏆 Nations League 2025</span>
        <span class="chip trophy">🏆 Saudi Pro League 2025–26</span>
        <span class="chip">Champion in 4 countries</span>
        <span class="chip">27 goals from 1,000</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">Club goals · Leo 2025–26 · Cris 2025–26</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="32">0</span><div class="bar" data-goals="32"></div></div>
      <div class="half right"><div class="bar" data-goals="30"></div><span class="val numeral" data-count="30">0</span></div>
    </div>
  </div>
</section>

<!-- ================= NOW ================= -->
<section class="age" data-age="41">
  <div class="age-head"><div class="big display">NOW</div><div class="years">World Cup 2026 · Leo 39 · Cris 41</div></div>
  <div class="duo">
    <article class="card leo">
      <div class="who"><span class="name">Messi</span><span class="season">Argentina · World Cup 2026</span></div>
      <h3 class="display">All-time World Cup top scorer</h3>
      <p>Messi opened his sixth World Cup — a record — with a <strong>hat-trick against Algeria</strong>, tying and then smashing Miroslav Klose's all-time World Cup scoring record. He <strong>leads the 2026 Golden Boot race with 7 goals</strong> and has passed Pelé for total World Cup goal contributions.</p>
      <p>Argentina topped their group and drew the kinder half of the bracket: Cape Verde in the round of 32, with the title defense fully alive.</p>
      <div class="chips">
        <span class="chip boot">2026 WC Golden Boot leader (7)</span>
        <span class="chip">All-time WC top scorer</span>
        <span class="chip">Most WC appearances ever</span>
      </div>
    </article>
    <article class="card cr7">
      <div class="who"><span class="name">Ronaldo</span><span class="season">Portugal · World Cup 2026</span></div>
      <h3 class="display">First man to score at six World Cups</h3>
      <p>After a rough opener against DR Congo and brutal criticism at home, Ronaldo answered with a <strong>brace against Uzbekistan</strong> — becoming the <strong>first player ever to score at six men's World Cups</strong>. He holds the all-time records for international goals (145) and caps (230).</p>
      <p>Portugal finished second in their group and face Croatia in the round of 32, on the brutal side of the draw. The World Cup remains the one trophy he has never touched.</p>
      <div class="chips">
        <span class="chip">Scored in 6 World Cups — first ever</span>
        <span class="chip">145 int'l goals · 230 caps</span>
        <span class="chip dark">The one missing trophy</span>
      </div>
    </article>
  </div>
  <div class="duel">
    <div class="duel-title">World Cup 2026 goals so far</div>
    <div class="track">
      <div class="half left"><span class="val numeral" data-count="7">0</span><div class="bar" data-goals="7" data-scale="10"></div></div>
      <div class="half right"><div class="bar" data-goals="2" data-scale="10"></div><span class="val numeral" data-count="2">0</span></div>
    </div>
  </div>
</section>

<div class="interlude">
  <div class="big-q display">They can only meet in one place:<br><span class="gold">the final.</span></div>
  <p class="sub">Argentina and Portugal landed on opposite sides of the 2026 bracket. Twenty-two years after they first shared a pitch, the only remaining stage for Messi vs Ronaldo is the World Cup final — 19 July 2026, New Jersey.</p>
</div>

<!-- ================= FINALE ================= -->
<section class="finale" id="finale">
  <h2 class="display">The Ledger</h2>
  <p class="sub">Two decades, side by side. Season club goals at every age — and the career scoreboard as it stands mid-2026.</p>

  <div class="chart-wrap">
    <div class="chart-title">Club goals per season, by age (17 → 41)</div>
    <svg id="chart" viewBox="0 0 900 380" role="img" aria-label="Line chart of club goals per season by age for Messi and Ronaldo"></svg>
    <div class="legend"><span class="l">Messi</span><span class="r">Ronaldo</span></div>
  </div>

  <div class="ledger" id="ledger">
    <div class="stat"><div class="cat">Career goals</div><div class="row"><span class="v l numeral">916</span><span class="dash">—</span><span class="v r numeral">973</span></div><div class="note">All competitions, club + country (mid-2026)</div></div>
    <div class="stat"><div class="cat">Ballon d'Or</div><div class="row"><span class="v l numeral">8</span><span class="dash">—</span><span class="v r numeral">5</span></div><div class="note">Most in history — and 2nd most</div></div>
    <div class="stat"><div class="cat">Career assists</div><div class="row"><span class="v l numeral">453</span><span class="dash">—</span><span class="v r numeral">307</span></div><div class="note">Messi: most assists ever recorded</div></div>
    <div class="stat"><div class="cat">Champions Leagues</div><div class="row"><span class="v l numeral">4</span><span class="dash">—</span><span class="v r numeral">5</span></div><div class="note">Ronaldo: all-time UCL top scorer (140)</div></div>
    <div class="stat"><div class="cat">European Golden Shoes</div><div class="row"><span class="v l numeral">6</span><span class="dash">—</span><span class="v r numeral">4</span></div><div class="note">Plus 8 Pichichis vs 3</div></div>
    <div class="stat"><div class="cat">League titles</div><div class="row"><span class="v l numeral">12</span><span class="dash">—</span><span class="v r numeral">8</span></div><div class="note">Leo: Spain, France · Cris: England, Spain, Italy, Saudi</div></div>
    <div class="stat"><div class="cat">Major international titles</div><div class="row"><span class="v l numeral">4</span><span class="dash">—</span><span class="v r numeral">3</span></div><div class="note">Leo: WC '22, 2 Copas, Finalissima · Cris: Euro '16, 2 Nations Leagues</div></div>
    <div class="stat"><div class="cat">International goals</div><div class="row"><span class="v l numeral">119+</span><span class="dash">—</span><span class="v r numeral">145</span></div><div class="note">Ronaldo: all-time record, 230 caps</div></div>
    <div class="stat"><div class="cat">Head to head</div><div class="row"><span class="v l numeral">16</span><span class="dash">—</span><span class="v r numeral">10</span></div><div class="note">35 meetings, 9 draws · 22 goals each</div></div>
    <div class="stat"><div class="cat">World Cup goals</div><div class="row"><span class="v l numeral">18+</span><span class="dash">—</span><span class="v r numeral">10</span></div><div class="note">Messi: all-time record, still counting</div></div>
  </div>
</section>

<div class="outro">
  <div class="date display">19 · 07 · 26</div>
  <p>If both keep winning, the last chapter of the greatest rivalry in sport writes itself at MetLife Stadium. Either way — from a 63-kilo teenager in Barcelona and a frosted-tipped winger in Lisbon to nearly 1,900 goals between them — there has never been anything like these two, at any age.</p>
</div>

<footer>Stats reflect commonly cited all-competition totals as of early July 2026 · World Cup 2026 figures are mid-tournament and will change</footer>

<script>
(function(){
  const reduce = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  // Progress bar
  const prog = document.getElementById('progress');
  function onScroll(){
    const h = document.documentElement;
    const p = h.scrollTop / (h.scrollHeight - h.clientHeight);
    prog.style.transform = 'scaleX(' + p + ')';
  }
  document.addEventListener('scroll', onScroll, {passive:true});
  onScroll();

  // Age marker
  const marker = document.getElementById('ageMarker');
  const ageNum = document.getElementById('ageNum');
  const ageSections = document.querySelectorAll('.age');

  const markerObs = new IntersectionObserver(entries=>{
    entries.forEach(e=>{
      if(e.isIntersecting){
        const a = e.target.dataset.age;
        ageNum.textContent = a === '41' ? '★' : (a === '39' ? '39+' : a);
        marker.classList.add('on');
      }
    });
  }, {rootMargin:'-40% 0px -50% 0px'});
  ageSections.forEach(s=>markerObs.observe(s));

  // Hide marker on hero & finale
  const edges = new IntersectionObserver(entries=>{
    entries.forEach(e=>{ if(e.isIntersecting) marker.classList.remove('on'); });
  }, {rootMargin:'-30% 0px -30% 0px'});
  document.querySelectorAll('.hero,.finale,.outro,.interlude').forEach(el=>edges.observe(el));

  // Reveal sections + animate bars + count-ups
  function countUp(el){
    const raw = el.dataset.count;
    const target = parseInt(raw,10);
    if(reduce || isNaN(target)){ el.textContent = raw; return; }
    const dur = 900; const t0 = performance.now();
    function tick(t){
      const k = Math.min(1,(t-t0)/dur);
      el.textContent = Math.round(target * (1-Math.pow(1-k,3)));
      if(k<1) requestAnimationFrame(tick); else el.textContent = raw;
    }
    requestAnimationFrame(tick);
  }

  const revealObs = new IntersectionObserver(entries=>{
    entries.forEach(e=>{
      if(!e.isIntersecting) return;
      const sec = e.target;
      sec.classList.add('in');
      sec.querySelectorAll('.bar').forEach(b=>{
        const g = parseFloat(b.dataset.goals);
        const scale = parseFloat(b.dataset.scale) || 73;
        b.style.width = Math.max(3,(g/scale)*100) + '%';
      });
      sec.querySelectorAll('[data-count]').forEach(countUp);
      revealObs.unobserve(sec);
    });
  }, {threshold:0.18});
  ageSections.forEach(s=>revealObs.observe(s));

  // Ledger reveal
  const stats = document.querySelectorAll('.stat');
  const statObs = new IntersectionObserver(entries=>{
    entries.forEach((e)=>{
      if(e.isIntersecting){
        const i=[...stats].indexOf(e.target);
        setTimeout(()=>e.target.classList.add('in'), reduce?0:i*70);
        statObs.unobserve(e.target);
      }
    });
  },{threshold:0.2});
  stats.forEach(s=>statObs.observe(s));

  // ---------- Chart ----------
  const ages = [17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41];
  const leo  = [1,8,17,16,38,47,53,73,60,41,58,41,54,45,51,31,38,11,21,25,33,43,null,null,null];
  const cr7  = [5,6,9,12,23,42,26,33,53,60,55,51,61,51,42,44,28,37,36,24,17,50,35,30,null];

  const svg = document.getElementById('chart');
  const W=900,H=380,padL=44,padR=16,padT=18,padB=40,maxY=80;
  const x = i => padL + (i/(ages.length-1))*(W-padL-padR);
  const y = v => H-padB - (v/maxY)*(H-padT-padB);
  const NS='http://www.w3.org/2000/svg';
  function el(n,attrs){const e=document.createElementNS(NS,n);for(const k in attrs)e.setAttribute(k,attrs[k]);return e;}

  // gridlines
  for(let v=0; v<=maxY; v+=20){
    svg.appendChild(el('line',{x1:padL,x2:W-padR,y1:y(v),y2:y(v),stroke:'rgba(239,235,221,.08)','stroke-width':1}));
    const t=el('text',{x:padL-8,y:y(v)+4,'text-anchor':'end',fill:'#93a096','font-size':'11','font-family':'Space Grotesk'});
    t.textContent=v; svg.appendChild(t);
  }
  // x labels
  ages.forEach((a,i)=>{
    if(a%2!==0 && a!==17 && a!==41) return;
    const t=el('text',{x:x(i),y:H-padB+22,'text-anchor':'middle',fill:'#93a096','font-size':'11','font-family':'Space Grotesk'});
    t.textContent=a; svg.appendChild(t);
  });
  const axisLbl=el('text',{x:(padL+W-padR)/2,y:H-4,'text-anchor':'middle',fill:'#5d6a60','font-size':'10','font-family':'Space Grotesk','letter-spacing':'3'});
  axisLbl.textContent='AGE'; svg.appendChild(axisLbl);

  function drawLine(data,color){
    let d='',started=false;
    data.forEach((v,i)=>{
      if(v==null) return;
      d += (started?' L':'M')+x(i)+' '+y(v); started=true;
    });
    const p=el('path',{d:d,fill:'none',stroke:color,'stroke-width':2.5,'stroke-linejoin':'round','stroke-linecap':'round'});
    svg.appendChild(p);
    data.forEach((v,i)=>{
      if(v==null) return;
      svg.appendChild(el('circle',{cx:x(i),cy:y(v),r:3.2,fill:'#0b1510',stroke:color,'stroke-width':2}));
    });
    if(!reduce){
      const len=p.getTotalLength();
      p.style.strokeDasharray=len; p.style.strokeDashoffset=len;
      return p;
    }
    return null;
  }
  const pL=drawLine(leo,'#86c7ee');
  const pR=drawLine(cr7,'#e14b52');

  // annotate the 73 peak
  const peakT=el('text',{x:x(7),y:y(73)-10,'text-anchor':'middle',fill:'#86c7ee','font-size':'12','font-family':'Space Grotesk','font-weight':'700'});
  peakT.textContent='73'; svg.appendChild(peakT);
  const peakR=el('text',{x:x(12),y:y(61)-10,'text-anchor':'middle',fill:'#e14b52','font-size':'12','font-family':'Space Grotesk','font-weight':'700'});
  peakR.textContent='61'; svg.appendChild(peakR);

  if(!reduce && (pL||pR)){
    const chartObs=new IntersectionObserver(es=>{
      es.forEach(e=>{
        if(e.isIntersecting){
          [pL,pR].forEach(p=>{
            if(!p) return;
            p.style.transition='stroke-dashoffset 2.2s ease';
            requestAnimationFrame(()=>p.style.strokeDashoffset='0');
          });
          chartObs.disconnect();
        }
      });
    },{threshold:0.3});
    chartObs.observe(svg);
  }
})();
</script>
</body>
</html>
