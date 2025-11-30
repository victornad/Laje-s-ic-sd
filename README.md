# 🧱 Laje’s — Projeto IC + SD (CESAR School)

◈ Projeto desenvolvido para as disciplinas de **Introdução à Computação** e **Sistemas Digitais**, na **CESAR School** (período 2025.2).  
Este site documenta todo o processo de criação, montagem e funcionamento do projeto **Laje’s**, reunindo descrição, código, componentes, aprendizados e vídeo demonstrativo.

🔗 **Acesse o site do projeto:**  
👉 [https://victornad.github.io/Laje-s-ic-sd/](https://victornad.github.io/Laje-s-ic-sd/)

---

## 📘 Sobre o Projeto
Conheça nossa motivação! O objetivo e o contexto do nosso "Medidor de Força de Peteleco - Flick Force" 💥

### 💡 Motivação
➤ Mostrar como a tecnologia pode transformar uma brincadeira em aprendizado e curiosidade científica.

### 🎯 Objetivo
➤ Criar um sistema que mede a força de um peteleco, unindo interação, física, geometria e eletrônica.

### 🌍 Contextualização
➤ Aplicado na área de eletrônica e educação, o projeto torna o estudo de impactos mais simples e divertido.

---

## 🧩 Esquema Conceitual
<img src="![Prótotipo Flick Force - Canva](https://github.com/user-attachments/assets/ecf3c75d-b05c-437f-83b3-e3f2ce464dc5)
" width="600px" alt="Esquema conceitual do projeto">

---

## 🔑 Palavras-chave
`Arduino` · `Automação` · `Sensores` · `Sistemas Digitais` · `Tecnologia`

---

## 👥 Autores

| Nome | GitHub | LinkedIn |
|------|--------|----------|
| Luis Carlos Barros Galliza Gomes | [@luisgalliza](https://github.com/luisgalliza) | [LinkedIn](https://linkedin.com/in/usuario1) |
| Victor de Lavor Nadler da Silva | [@victornad](https://github.com/victornad) | [LinkedIn](https://linkedin.com/in/usuario2) |
| João Pedro Castro Monte Teixeira | [@jpcmt-eng](https://github.com/jpcmt-eng) | [LinkedIn](https://www.linkedin.com/in/jo%C3%A3o-pedro-castro-monte-teixeira-94a55730a?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=ios_app) |
| Maria Luísa Dijck Muniz | [@mldm2-art](https://github.com/mldm2-art) | [LinkedIn](https://www.linkedin.com/in/maria-luísa-muniz?utm_source=share_via&utm_content=profile&utm_medium=member_ios) |
| Mateus Xavier Ramos Rocha | [@mateusxavier](https://github.com/mateusxavierr) | [LinkedIn](https://www.linkedin.com/in/mateus-xavier-25265a340?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=ios_app) |
| Rubens Sousa Carvalho da Rocha | [@rubensmontreal-blip](https://github.com/rubensmontreal-blip) | [LinkedIn](https://linkedin.com/in/usuario6) |
| Kaio Cerqueira Santos da Silva | [@kaiocerqueira](https://github.com/kaiocerqueira) | [LinkedIn](www.linkedin.com/in/kaio-cerqueira-287b4b398) |

---

## ⚙️ Componentes e Suprimentos

| Componente | Descrição |
|-------------|------------|
| 1x Placa Arduino UNO | Microcontrolador responsável pelo controle principal |
| 1x Sensor de Batida Piezo | Transforma a batida em um sinal elétrico que o sistema pode interpretar. |
| 1x Protoboard | Permite montar e testar circuitos eletrônicos sem solda, de forma rápida e reutilizável |
| 12x Jumpers | Servem para ligar pontos do circuito na protoboard, permitindo conectar componentes entre si de forma rápida e organizada |
| 1x Displey LCD | Mostra os números. A “tela” onde o dispositivo mostra os dados de forma clara e visual |
| 1x Buzzer | Emite sons ou alertas sonoros |
| 1x Cabo USB | Usado para energia e troca de dados entre dispositivos |

---

## 🧰 Aplicativos e Plataformas

- **Arduino IDE** – versão 2.3.2  
- **Visual Studio Code** – versão 1.93  
- **GitHub** – repositório e hospedagem do site  
- **YouTube** – vídeo de demonstração do projeto
- **Discord** - Meio de comunicação do grupo

---

## 🪜 Passo a Passo da Montagem

1. Conexão com o Computador:
- Conecte o Arduino ao computador utilizando um cabo USB. Em seguida, abra a IDE, selecione a porta correta e carregue o código no microcontrolador;
2. Testes de Funcionamento:
- Após o carregamento do programa, execute os testes do sistema, verificando se o sensor responde aos estímulos, se os dados são exibidos corretamente no display e se o buzzer emite os sinais sonoros;
3. Ajustes Finais:
- Realize os ajustes de sensibilidade do sensor e dos tempos de resposta diretamente no código, conforme a necessidade prática do projeto, garantindo precisão e confiabilidade.

---

## 💻 Código

Trecho de exemplo:

```c
#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);

// PINOS
int sensorPin = A0;
int buzzer = 9;

// AJUSTES
int minimoImpacto = 80;   // sensibilidade do piezo
int maxLeitura   = 1023;  // valor máximo do analógico

// RECORDE (0 a 999)
int recorde = 0;

// -------------------- SOM DE RECORDE --------------------
void somDeRecorde() {
  tone(buzzer, 500, 120);
  delay(130);

  tone(buzzer, 650, 120);
  delay(130);

  tone(buzzer, 800, 140);
  delay(150);

  tone(buzzer, 950, 160);
  delay(170);

  tone(buzzer, 1100, 180);
  delay(190);

  tone(buzzer, 950, 120);
  delay(130);

  tone(buzzer, 1250, 260);
  delay(280);

  noTone(buzzer);
}

// -------------------- SOM NORMAL --------------------
void somNormal() {
  tone(buzzer, 600, 120);
  delay(140);

  tone(buzzer, 800, 150);
  delay(170);

  noTone(buzzer);
}

// -------------------- MOSTRAR VALOR COM 3 DÍGITOS --------------------
void print3dig(int valor) {
  if (valor < 10) {
    lcd.print("00");
  } 
  else if (valor < 100) {
    lcd.print("0");
  }

  lcd.print(valor);
}

// -------------------- TELA PADRÃO --------------------
void mostrarTelaRecorde() {
  lcd.clear();

  lcd.setCursor(0, 0);
  lcd.print("FLICK FORCE");

  lcd.setCursor(0, 1);
  lcd.print("REC: ");
  print3dig(recorde);
}

// -------------------- ANIMAÇÃO DO RECORDE SUBINDO --------------------
void animarNovoRecorde(int antigo, int novo) {
  lcd.clear();

  lcd.setCursor(0, 0);
  lcd.print("NOVO RECORDE!");

  for (int i = antigo; i <= novo; i++) {
    lcd.setCursor(0, 1);
    lcd.print("REC: ");
    print3dig(i);
    delay(15);   // velocidade da animação
  }
}

// -------------------- SETUP --------------------
void setup() {
  lcd.init();
  lcd.backlight();
  lcd.clear();

  pinMode(buzzer, OUTPUT);

  lcd.setCursor(0, 0);
  lcd.print("FLICK FORCE");
  delay(1500);

  mostrarTelaRecorde();
}

// -------------------- LOOP --------------------
void loop() {
  int leitura = analogRead(sensorPin);

  if (leitura > minimoImpacto) {

    delay(60); // anti-ruído

    int nivelForca = map(leitura, minimoImpacto, maxLeitura, 0, 999);

    if (nivelForca < 0)   nivelForca = 0;
    if (nivelForca > 999) nivelForca = 999;

    bool novoRecorde = false;
    int recordeAntigo = recorde;

    if (nivelForca > recorde) {
      recorde = nivelForca;
      novoRecorde = true;
    }

    // SOM
    if (novoRecorde) {
      somDeRecorde();
    } 
    else {
      somNormal();
    }

    // TELA DO IMPACTO
    lcd.clear();

    lcd.setCursor(0, 0);
    if (novoRecorde) {
      lcd.print("NOVO RECORDE!");
    } 
    else {
      lcd.print("FORCA MEDIDA");
    }

    lcd.setCursor(0, 1);
    lcd.print("NIVEL: ");
    print3dig(nivelForca);

    delay(1500);

    // ANIMAÇÃO DO RECORDE SE FOR NOVO
    if (novoRecorde) {
      animarNovoRecorde(recordeAntigo, recorde);
      delay(800);
    }

    // VOLTA PARA TELA PADRÃO
    mostrarTelaRecorde();
  }
}
