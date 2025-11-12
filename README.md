# 🧱 Laje’s — Projeto IC + SD (CESAR School)

Projeto desenvolvido para as disciplinas de **Introdução à Computação** e **Sistemas Digitais**, na **CESAR School** (período 2024.2).  
Este site documenta todo o processo de criação, montagem e funcionamento do projeto **Laje’s**, reunindo descrição, código, componentes, aprendizados e vídeo demonstrativo.

🔗 **Acesse o site do projeto:**  
👉 [https://victornad.github.io/Laje-s-ic-sd/](https://victornad.github.io/Laje-s-ic-sd/)

---

## 📘 Sobre o Projeto
Conheça nossa motivação! O objetivo e o contexto do nosso "Medidor de Força de Peteleco - Flick Force" 💥

### 💡 Motivação
Mostrar como a tecnologia pode transformar uma brincadeira em aprendizado e curiosidade científica.

### 🎯 Objetivo
Criar um sistema que mede a força de um peteleco, unindo interação, física e eletrônica.

### 🌍 Contextualização
Aplicado na área de eletrônica e educação, o projeto torna o estudo de impactos mais simples e divertido.

---

## 🧩 Esquema Conceitual
<img src="assets/images/esquema.png" width="600px" alt="Esquema conceitual do projeto">

---

## 🔑 Palavras-chave
`Arduino` · `Automação` · `Sensores` · `Sistemas Digitais` · `Tecnologia`

---

## 👥 Autores

| Nome | GitHub | LinkedIn |
|------|--------|----------|
| Nome do Autor 1 | [@usuario1](https://github.com/usuario1) | [LinkedIn](https://linkedin.com/in/usuario1) |
| Nome do Autor 2 | [@usuario2](https://github.com/usuario2) | [LinkedIn](https://linkedin.com/in/usuario2) |

---

## ⚙️ Componentes e Suprimentos

| Componente | Descrição |
|-------------|------------|
| Arduino Uno | Microcontrolador responsável pelo controle principal |
| Sensor Ultrassônico | Mede a distância entre o objeto e o sensor |
| Protoboard e Jumpers | Usados para montagem e conexão dos componentes |
| LEDs | Indicadores visuais do estado do sistema |
| Resistores | Controlam a corrente elétrica dos LEDs |

---

## 🧰 Aplicativos e Plataformas

- **Arduino IDE** – versão 2.3.2  
- **Visual Studio Code** – versão 1.93  
- **GitHub** – repositório e hospedagem do site  
- **YouTube** – vídeo de demonstração do projeto  

---

## 🪜 Passo a Passo da Montagem

1. Monte o circuito conforme o esquema conceitual acima.  
2. Conecte o Arduino ao computador e carregue o código.  
3. Teste o funcionamento dos sensores e LEDs.  
4. Ajuste os valores e tempos de resposta conforme a necessidade.

📸 *Adicione imagens de cada etapa na pasta `/assets/images`.*

---

## 💻 Código

Trecho de exemplo:

```c
int led = 13;

void setup() {
  pinMode(led, OUTPUT);
}

void loop() {
  digitalWrite(led, HIGH);
  delay(1000);
  digitalWrite(led, LOW);
  delay(1000);
}
