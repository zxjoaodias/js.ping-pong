// váriaveis da bolinha
let xBolinha = 300;
let yBolinha = 200;
let diametro = 20;
let raio = diametro / 2;

// velocidade da bolinha
let velocidadeXBolinha = 1;
let velocidadeYBolinha = 2;

//variáveis da minha raquete
let xMinhaRaquete = 3;
let yMinhaRaquete = 150;
let wRaquete = 12;
let hRaquete = 90;

//variáveis do oponente
let xRaqueteOponente = 585;
let yRaqueteOponente = 150;
let velocidadeYOponente;

//váriaveis do placar
let meusPontos = 0;
let pontosOponente = 0;

//variaveis do som
let raquetada;
let trilha;
let ponto;


let colidiu = false;

function preload(){
 raquetada = loadSound ("raquetada.mp3");
 trilha = loadSound ("trilha.mp3");
 ponto = loadSound ("ponto.mp3");
                     
}

function setup() {
  createCanvas(600, 400);
  trilha.loop();
}

function draw() {
  background(205, 152, 218); //RGB Value
  mostrarBolinha();
  mostrarRaquete(xMinhaRaquete, yMinhaRaquete);
  mostrarRaquete(xRaqueteOponente, yRaqueteOponente);
  movimentarBolinha();
  movimentarMinhaRaquete();
//movimentarRaqueteOponentePC();
  movimentarRaqueteOponente();
  verificaColisaoBolinha();
  verificaColisaoRaquete(xRaqueteOponente, yRaqueteOponente);
  verificaColisaoRaquete(xMinhaRaquete, yMinhaRaquete);
  mostrarPlacar();
  pontuação();
}

function mostrarBolinha() {
  fill(color (249, 211, 249));
  stroke(color(249, 211, 249))
  circle(xBolinha, yBolinha, diametro);
}

function mostrarRaquete(x, y) {
  fill(color(186, 65, 211));
  stroke(color(186, 65, 211));
  rect(x, y, wRaquete, hRaquete);
}

function movimentarBolinha() {
  xBolinha += velocidadeXBolinha;
  yBolinha += velocidadeYBolinha;
}

function movimentarMinhaRaquete() {
  if (keyIsDown(UP_ARROW)) {
    yMinhaRaquete -= 10;
  }
  if (keyIsDown(DOWN_ARROW)) {
    yMinhaRaquete += 10;
  }
}

function movimentarRaqueteOponente(){
  if (keyIsDown(87)) {
    yRaqueteOponente -= 10;
  }
  if (keyIsDown(83)){
    yRaqueteOponente += 10;
  }
}

function movimentarRaqueteOponentePC() {
  velocidadeYOponente = yBolinha - yRaqueteOponente - wRaquete / 2 - 50;
  yRaqueteOponente += velocidadeYOponente;
}    yMinhaRaquete -= 10;
82
  }
83
  if (keyIsDown(DOWN_ARROW)) {
84
    yMinhaRaquete += 10;
85
  }
86
}
87
​
88
function movimentarRaqueteOponente(){
89
  if (keyIsDown(87)) {
90
    yRaqueteOponente -= 10;
91
  }
92
  if (keyIsDown(83)){
93
    yRaqueteOponente += 10;
94
  }
95
}
96
​
97
function movimentarRaqueteOponentePC() {
98
  velocidadeYOponente = yBolinha - yRaqueteOponente - wRaquete / 2 - 50;
99
  yRaqueteOponente += velocidadeYOponente;
100
}
101
​
102
function verificaColisaoBolinha() {
103
  if (xBolinha + raio > width || xBolinha - raio < 0) {
104
    velocidadeXBolinha *= -1;
105
  }
106
​
107
  if (yBolinha + raio > height || yBolinha - raio < 0) {
108
    velocidadeYBolinha *= -1;
109
  }
110
}
111
​
112
function verificaColisaoRaquete(x, y) {
113
  colidiu = collideRectCircle(x,y,wRaquete,hRaquete,xBolinha,yBolinha,raio);
114
  if (colidiu) {
115
    velocidadeXBolinha *= -1;
116
    raquetada.play();
117
  }
118
}
119
​
120
function mostrarPlacar() {
121
  textAlign(CENTER);
122
  textSize(16);
123
  fill(255);
124
  rect(150,10,40,20)
125
  fill(color(77,77,77));
126
  text(meusPontos, 170, 26);
127
  fill(255);
128
  rect(450,10,40,20)
129
  fill(color(77,77,77));
130
  text(pontosOponente, 470, 26);
131
}
132
​
133
function pontuação() {
134
  if (xBolinha > 590) {
135
    meusPontos += 1;
136
    ponto.play();
137
  }
138
​
139
  if (xBolinha < 10 ) {
140
    pontosOponente += 1;
141
    ponto.play();
142
  }
143
}

function verificaColisaoBolinha() {
  if (xBolinha + raio > width || xBolinha - raio < 0) {
    velocidadeXBolinha *= -1;
  }

  if (yBolinha + raio > height || yBolinha - raio < 0) {
    velocidadeYBolinha *= -1;
  }
}

function verificaColisaoRaquete(x, y) {
  colidiu = collideRectCircle(x,y,wRaquete,hRaquete,xBolinha,yBolinha,raio);
  if (colidiu) {
    velocidadeXBolinha *= -1;
    raquetada.play();
  }
}

function mostrarPlacar() {
  textAlign(CENTER);
  textSize(16);
  fill(255);
  rect(150,10,40,20)
  fill(color(77,77,77));
  text(meusPontos, 170, 26);
  fill(255);
  rect(450,10,40,20)
  fill(color(77,77,77));
  text(pontosOponente, 470, 26);
}

function pontuação() {
  if (xBolinha > 590) {
    meusPontos += 1;
    ponto.play();
  }

  if (xBolinha < 10 ) {
    pontosOponente += 1;
    ponto.play();
  }
}
