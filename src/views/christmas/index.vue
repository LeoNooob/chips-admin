<template>
  <div class="main">
    <div v-for="(i, index) in 100" :key="index" class="snow" />
    <div class="text">
      <vue-typed-js :strings="letter" :content-type="'html'" :typedSpeed="200">
        <h1 class="typing" />
      </vue-typed-js>
    </div>
  </div>
</template>

<script>
import { formatTime, parseTime } from '@/utils'
export default {
  data() {
    return {
      letter: [`哈喽？冰洁？看得到么？`]
    }
  },
  beforeMount() {
      const today = new Date()
      const memory = new Date('2021-11-27')
      this.letter.push(
          `今天是${this.parseTime(today, '{y}年{m}月{d}日')}`)
    
        if (parseInt((new Date('2021-12-25') - today) / 1000 / 86400) <= 2) {
            this.letter.push(`Merry Christmas!`)
        } else {
            this.letter.push(`今天只是普普通通的一天，但是`)
        }
        this.letter.push(
          `我们在一起已经有${parseInt((today - memory) / 1000 / 86400)}天`,
          `虽然在一起的时间不长`,
          `远不及我们各自过去的千万分之一`,
          `希望在今后的日子里`,
          `我们可以共同创造独属于我俩的回忆`,
          `无论它们是`
        )
      
  },
  mounted() {},
  methods: {
      parseTime,
      formatTime
  },
}
</script>

<style lang="scss" scoped>
.main {
  text-align: center;
  height: 100vh;
  background: radial-gradient(
    ellipse at bottom,
    #1b2735 0%,
    #090a0f 100%
  ) !important;
  overflow: hidden;
  filter: drop-shadow(0 0 10px white);
}
.text {
  display: flex;
  height: 100vh;
  align-items: center;
  justify-content: center;
  color: #f0f0f0;
}

@function random_range($min, $max) {
  $rand: random();
  $random_range: $min + floor($rand * (($max - $min) + 1));
  @return $random_range;
}

.snow {
  $total: 200;
  position: absolute;
  width: 10px;
  height: 10px;
  background: white;
  border-radius: 50%;

  @for $i from 1 through $total {
    $random-x: random(1000000) * 0.0001vw;
    $random-offset: random_range(-100000, 100000) * 0.0001vw;
    $random-x-end: $random-x + $random-offset;
    $random-x-end-yoyo: $random-x + ($random-offset / 2);
    $random-yoyo-time: random_range(30000, 80000) / 100000;
    $random-yoyo-y: $random-yoyo-time * 100vh;
    $random-scale: random(10000) * 0.0001;
    $fall-duration: random_range(10, 30) * 1s;
    $fall-delay: random(30) * -1s;

    &:nth-child(#{$i}) {
      opacity: random(10000) * 0.0001;
      transform: translate($random-x, -10px) scale($random-scale);
      animation: fall-#{$i} $fall-duration $fall-delay linear infinite;
    }

    @keyframes fall-#{$i} {
      #{percentage($random-yoyo-time)} {
        transform: translate($random-x-end, $random-yoyo-y) scale($random-scale);
      }

      to {
        transform: translate($random-x-end-yoyo, 100vh) scale($random-scale);
      }
    }
  }
}
</style>
