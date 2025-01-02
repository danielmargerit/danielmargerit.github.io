---
title: "Quand les maths s'animent : des maths plein les yeux."
date: 2022-12-23 10:00:00 +0100
categories: 
 - art
 - math
tags:
  - math
  - geometry
  - digital art
  - vulgarisation
use_math: true
published: true
author: "Daniel Margerit"
credits: "HTML par Arnaud Chéritat"
originally_published: "2022-12-19"
original_link: "https://jeux.lesmathsenscene.fr/avent-2022/surprises/S-D8CTBLuP9EKEgqSrrVTyvC6NCoOsuMBp/"
---

<div style="text-align: justify; font-size: 100%; margin-top: 60px;">
L’outil numérique permet à des artistes de nous révéler des mondes imaginaires d’une grande beauté mathématique; mondes géométriques qui peuvent parfois être animés pour mieux encore nous les faire découvrir. Tel est le cas des mondes de Jos Leys, qui est « Un grand maître ès images mathématiques ! » (Citation d’<a href="https://perso.ens-lyon.fr/ghys/liens/">Etienne Ghys</a> qui a réalisé avec lui et Aurélien Alvarez le film <a href="http://dimensions-math.org/Dim_fr.htm">Dimensions</a>), ainsi que des univers d’autres artistes tels que Douglas Hilário da Cruz, Etienne Jacob, « Jo », Matt Taylor, Dave Whyte et Jérémie Brunet.
</div>
<p>
<div style="text-align: center;">
  <div style="position: relative; width: 640px; height: 640px; display: inline-block;">
    <img src="/images/posts/2022-12-23/aire.png" alt="Illustration de Jos Leys">
    <canvas width="640" height="640" id="aire" style="position: absolute; top: 0; left: 0;"></canvas>
  </div>
</div>
</p>
Pour cette période de Noël, les univers de ces six artistes « mathématiciens » se sont invités ou incrustés ci-dessus sur le monde <a href="http://www.josleys.com/show_image.php?galid=267&imageid=8348">Kleinian jewelry</a> créé par Jos Leys et disponible sur son site <a href="http://www.josleys.com/">Mathematical Imagery</a>&nbsp;: pour cela clique sur les six incrustations. Cette surprise est donc une invitation à partir dans ces univers&nbsp;: bon voyage mathématico géométrique&nbsp;!
<p>
<hr style="width: 200px;">
</p>

<script>
let canvas = document.getElementById("aire");
let w = canvas.width;
let h = canvas.height;
let ctx = canvas.getContext("2d");

let circles = [
  { x: 141, y: 308, r: 38, link: "https://www.instagram.com/artmathbeauty/" },
  { x: 156, y: 406, r: 59, link: "https://bleuje.com/animationsite/" },
  { x: 255, y: 500, r: 78, link: "https://www.instagram.com/davebeesbombs/" },
  { x: 406, y: 495, r: 73, link: "https://www.instagram.com/emty01/" },
  { x: 493, y: 400, r: 53, link: "https://www.instagram.com/jn3oo8/" },
  { x: 508, y: 311, r: 35, link: "https://www.youtube.com/user/bib993" },
];

function getMousePos(canvas, evt) {
  var rect = canvas.getBoundingClientRect();
  return {
    x: evt.clientX - rect.left,
    y: evt.clientY - rect.top,
  };
}

function distSq(a, b) {
  return (a.x - b.x) * (a.x - b.x) + (a.y - b.y) * (a.y - b.y);
}

let highlight = null;

function paint() {
  ctx.clearRect(0, 0, w, h);
  for (let i = 0; i < circles.length; i++) {
    let c = circles[i];
    ctx.beginPath();
    ctx.arc(c.x, c.y, c.r, 0, 2 * Math.PI);
    ctx.strokeStyle = "rgba(0, 0, 255, 0.2)"; // Bordure légère
    ctx.lineWidth = 2;
    ctx.stroke();
  }
  if (highlight !== null) {
    ctx.beginPath();
    ctx.arc(highlight.x, highlight.y, highlight.r, 0, 2 * Math.PI);
    ctx.strokeStyle = "red";
    ctx.lineWidth = 3;
    ctx.stroke();
  }
}

canvas.onmousemove = function (e) {
  var p = getMousePos(canvas, e);
  highlight = null; // Reset highlight
  canvas.style.cursor = "default";
  for (let i = 0; i < circles.length; i++) {
    let c = circles[i];
    if (distSq(p, c) < c.r * c.r) {
      highlight = c;
      canvas.style.cursor = "pointer"; // Curseur "main"
      break;
    }
  }
  paint();
};

canvas.onclick = function () {
  if (highlight !== null) {
    window.open(highlight.link, "_blank");
  }
};

paint(); // Initial draw
</script>

### Remerciements
- Mise en forme HTML réalisée par **Arnaud Chéritat**. Un grand merci pour son aide précieuse dans la création de cette surprise interactive !

---

### Origine de cet article
Ce post a été publié initialement le **19 décembre 2022** dans les surprises du Calendrier de l'Avent Mathématiques Les Maths En Scène.  
Retrouvez la version originale ici : [Surprise du 19 décembre 2022](https://jeux.lesmathsenscene.fr/avent-2022/surprises/S-D8CTBLuP9EKEgqSrrVTyvC6NCoOsuMBp/).

