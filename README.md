# Oyun Fizigi

## Ofis Saatleri

* Persembe 14:00 - 17:00
* Email: guvencu at anadolu edu tr
* Oda: 115

  
## Odevler

Github Classroom Odev Gonderimi (Basitlestirilmis Anlatim): https://gusanmaz.github.io/github-classroom-gonderim.pdf

### Odev 0

https://classroom.github.com/a/i2qkthZN

### Odev 1

https://github.com/abtmyo/oyun-fizigi/blob/main/odev1.md

## Kitap

https://natureofcode.com/

## Videolar

https://www.youtube.com/channel/UCvjgXvBlbQiydffZU7m1_aw (Coding Train - Daniel Shiffman)

## Alistirma Odevi

https://www.instagram.com/reel/DO-gDa6DcMl/?igsh=MXBvemFvYWZ5NHRxMQ==

## P5.js 

* https://p5js.org/tutorials/ 
* https://editor.p5js.org/

## Processing

TBA

## Araclar

https://youtubetotranscript.com/

## Kod Ornekleri

* Nested Loop (3  nested for) - https://editor.p5js.org/gusanmaz/sketches/vNOM8nsq0

## P5.js Notlari

* Donguler 1: https://gusanmaz.github.io/for.html
* Donguler 2: https://gusanmaz.github.io/for2.html
* Kapsamli p5.js Notlari: https://gusanmaz.github.io/p5-course.html

# Collison Detection

https://www.jeffreythompson.org/collision-detection/

## Oyun Oynayarak Kodlama

* Replicube: https://store.steampowered.com/app/3401490/Replicube/

## Nature of Code 

* https://natureofcode.com/
* https://github.com/nature-of-code/noc-book-2
* https://www.youtube.com/playlist?list=PLRqwX-V7Uu6ZV4yEcW3uDwOgGXKUUsPOM

## Istatistik Yardimci Kaynaklar

* https://tr.khanacademy.org/math/statistics-probability/modeling-distributions-of-data/normal-distributions-library/a/normal-distributions-review
* https://tr.khanacademy.org/math/statistics-probability/summarizing-quantitative-data/variance-standard-deviation-population/a/calculating-standard-deviation-step-by-step

## Conways's Game of Life Atolyesi

* https://gusanmaz.github.io/conway.html

## Cellular Automaton

* https://youtu.be/Ggxt06qSAe4
* https://www.youtube.com/watch?v=lsWulRIWzdo
* https://youtu.be/qGxqKUbrXpk
* https://natureofcode.com/cellular-automata/

## JS Oyun Fizigi Kutuphaneleri

* Matter.js - https://brm.io/matter-js/
* p5play.js - https://p5play.org/

## P5.play 
* https://gusanmaz.github.io/p5play-tut/index.html

# NATURE OF CODE TURKCE
* https://gusanmaz.github.io/noc/

# Sayi Sistemleri

* https://gusanmaz.github.io/numbers/

# 31 Aralik 2025
```js
function setup() {
    new Canvas(400, 350);
    world.gravity.y = 10;

    // Zemin
    let floor = new Sprite(200, 330, 400, 20, 'static');
    floor.color = '#2d3436';

    // Farklı sekme değerleri
    let balls = [
        { x: 70,  bounce: 0,   label: '0' },
        { x: 140, bounce: 0.3, label: '0.3' },
        { x: 210, bounce: 0.6, label: '0.6' },
        { x: 280, bounce: 0.9, label: '0.9' },
        { x: 350, bounce: 1,   label: '1' }
    ];

    let colors = ['#ff5f57', '#febc2e', '#00ff88', '#00d4ff', '#c44dff'];

    for (let i = 0; i < balls.length; i++) {
        let b = balls[i];

        let ball = new Sprite(b.x, 50, 35);
        ball.bounciness = b.bounce;
        ball.color = colors[i];
        ball.text = b.label;
        ball.textSize = 12;
    }
}

function draw() {
    background('#1a1a2e');

    fill(255);
    textSize(14);
    textAlign(CENTER);
    text('Bounciness Değerleri', 200, 25);
}

function setup() {
    new Canvas(400, 350);
    world.gravity.y = 10;

    // Zemin
    let floor = new Sprite(200, 330, 400, 20, 'static');
    floor.color = '#2d3436';

    // Farklı sekme değerleri
    let balls = [
        { x: 70,  bounce: 0,   label: '0' },
        { x: 140, bounce: 0.3, label: '0.3' },
        { x: 210, bounce: 0.6, label: '0.6' },
        { x: 280, bounce: 0.9, label: '0.9' },
        { x: 350, bounce: 1,   label: '1' }
    ];

    let colors = ['#ff5f57', '#febc2e', '#00ff88', '#00d4ff', '#c44dff'];

    for (let i = 0; i < balls.length; i++) {
        let b = balls[i];

        let ball = new Sprite(b.x, 50, 35);
        ball.bounciness = b.bounce;
        ball.color = colors[i];
        ball.text = b.label;
        ball.textSize = 12;
    }
}

function draw() {
    background('#1a1a2e');

    fill(255);
    textSize(14);
    textAlign(CENTER);
    text('Bounciness Değerleri', 200, 25);
}
```


