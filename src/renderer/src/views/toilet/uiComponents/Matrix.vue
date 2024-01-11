<template>
  <div id="matrix" class="matrix"></div>
</template>

<script setup>
import { onMounted } from 'vue'
import p5 from 'p5'

const s = (sketch) => {
  // let count = 0
  // sketch.setup = function () {
  //   sketch.createCanvas(400, 400) // 创建画布，传入画布尺寸
  //   sketch.background(120) // 设置画布背景色
  // }

  // sketch.draw = function () {
  //   let x = Math.sin(count) * 100 + 200
  //   let y = Math.cos(count) * 100 + 200
  //   sketch.circle(x, y, 50) // 创建圆形
  //   count += 0.1
  // }
  const langs = [
    'Hello World',
    'مرحبا بالعالم',
    'Salam Dünya',
    'Прывітанне Сусвет',
    'Здравей свят',
    'ওহে বিশ্ব',
    'Zdravo svijete',
    'Hola món',
    'Kumusta Kalibutan',
    'Ahoj světe',
    'Helo Byd',
    'Hej Verden',
    'Hallo Welt',
    'Γειά σου Κόσμε',
    'Hello World',
    'Hello World',
    'Hola Mundo',
    'Tere, Maailm',
    'Kaixo Mundua',
    'سلام دنیا',
    'Hei maailma',
    'Bonjour le monde',
    'Dia duit an Domhan',
    'Ola mundo',
    'હેલો વર્લ્ડ',
    'Sannu Duniya',
    'नमस्ते दुनिया',
    'Hello World',
    'Pozdrav svijete',
    'Bonjou Mondyal la',
    'Helló Világ',
    'Բարեւ աշխարհ',
    'Halo Dunia',
    'Ndewo Ụwa',
    'Halló heimur',
    'Ciao mondo',
    'שלום עולם',
    'こんにちは世界',
    'Hello World',
    'Გამარჯობა მსოფლიო',
    'Сәлем Әлем',
    'សួស្តី​ពិភពលោក',
    'ಹಲೋ ವರ್ಲ್ಡ್',
    '안녕하세요 월드',
    'Ciao mondo',
    'ສະ​ບາຍ​ດີ​ຊາວ​ໂລກ',
    'Labas pasauli',
    'Sveika pasaule',
    'Hello World',
    'Kia Ora',
    'Здраво свету',
    'ഹലോ വേൾഡ്',
    'Сайн уу',
    'हॅलो वर्ल्ड',
    'Hai dunia',
    'Hello dinja',
    'မင်္ဂလာပါကမ္ဘာလောက',
    'नमस्कार संसार',
    'Hallo Wereld',
    'Hei Verden',
    'Moni Dziko Lapansi',
    'ਸਤਿ ਸ੍ਰੀ ਅਕਾਲ ਦੁਨਿਆ',
    'Witaj świecie',
    'Olá Mundo',
    'Salut Lume',
    'Привет, мир',
    'හෙලෝ වර්ල්ඩ්',
    'Ahoj svet',
    'Pozdravljen, svet',
    'Waad salaaman tihiin',
    'Përshendetje Botë',
    'Здраво Свете',
    'Lefatše Lumela',
    'Halo Dunya',
    'Hej världen',
    'Salamu, Dunia',
    'ஹலோ வேர்ல்ட்',
    'హలో వరల్డ్',
    'Салом Ҷаҳон',
    'สวัสดีชาวโลก',
    'Kamusta Mundo',
    'Selam Dünya',
    'Привіт Світ',
    'ہیلو ورلڈ',
    'Salom Dunyo',
    'Chào thế giới',
    'העלא וועלט',
    'Mo ki O Ile Aiye',
    '你好，世界',
    '你好，世界',
    '你好，世界',
    'Sawubona Mhlaba'
  ]
  // hello world in 92 Languages

  let charSize = 18
  // let fallRate = charSize / 2;
  let streams

  // -------------------------------
  class Char {
    constructor(value, x, y, speed) {
      this.value = value
      this.x = x
      this.y = y
      this.speed = speed
    }

    draw() {
      const flick = sketch.random(100)
      // 10 percent chance of flickering a number instead
      if (flick < 10) {
        sketch.fill(120, 30, 100)
        sketch.text(sketch.round(sketch.random(9)), this.x, this.y)
      } else {
        sketch.text(this.value, this.x, this.y)
      }

      // fall down
      this.y = this.y > sketch.height ? 0 : this.y + this.speed
    }
  }

  // -------------------------------------
  class Stream {
    constructor(text, x) {
      const y = sketch.random(text.length * 4)
      const speed = sketch.random(2, 10)
      this.chars = []

      for (let i = text.length; i >= 0; i--) {
        this.chars.push(new Char(text[i], x, (y + text.length - i) * charSize, speed))
      }
    }

    draw() {
      sketch.fill(120, 100, 100)
      this.chars.forEach((c, i) => {
        // 30 percent chance of lit tail
        const lit = sketch.random(100)
        if (lit < 30) {
          if (i === this.chars.length - 1) {
            sketch.fill(120, 30, 100)
          } else {
            sketch.fill(120, 100, 90)
          }
        }

        c.draw()
      })
    }
  }

  function createStreams() {
    // create random streams from langs that span the width
    for (let i = 0; i < sketch.width; i += charSize) {
      streams.push(new Stream(sketch.random(langs), i))
    }
  }

  function reset() {
    streams = []
    createStreams()
  }

  sketch.setup = function () {
    sketch.createCanvas(innerWidth, innerHeight).parent('matrix')
    reset()
    sketch.frameRate(60)
    sketch.colorMode(sketch.HSB)
    sketch.noStroke()
    sketch.textSize(charSize)
    sketch.textFont('monospace')
    sketch.background(0)
  }

  sketch.draw = function () {
    sketch.background(0, 0.4)
    streams.forEach((s) => s.draw())
  }

  sketch.windowResized = function () {
    sketch.resizeCanvas(innerWidth, innerHeight)
    sketch.background(0)
    reset()
  }
}

onMounted(() => {
  new p5(s)
})
</script>

<style lang="scss" scoped>
.matrix {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  opacity: 0.6;
  z-index: -1;
}
</style>
