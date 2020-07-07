<template>
  <div>
    <div :class="{blue: bgColor==0, red: bgColor==1, green: bgColor==2, yellow: bgColor==3, gray: bgColor==4}" class="container px-5 py-12 mx-auto border rounded-lg my-10">
      <div class="py-2 w-full flex flex-col items-center justify-center">
        <h1 class="text-white">レジ袋</h1>
        <div class="rounded-lg border bg-white p-4 cursor-pointer w-full shadow relative max-w-sm h-12" v-on:click="bagCounter">
          <p v-for="n in bag.length" :key=bag[n-1] class=" text-center content" v-bind:class="{apper: bagCount==n-1}">{{bag[n-1]}}</p>
        </div>
      </div>
      <div class="py-2 w-full flex flex-col items-center justify-center">
        <h1 class="text-white">ポイントカード</h1>
        <div class="rounded-lg border bg-white p-4 cursor-pointer w-full shadow relative max-w-sm h-12" v-on:click="pointCounter">
          <p v-for="n in point.length" :key=point[n-1] class="text-center content" v-bind:class="{apper: pointCount==n-1}">{{point[n-1]}}</p>
        </div>
      </div>
      <div class="py-2 w-full flex flex-col items-center justify-center">
        <h1 class="text-white">お箸</h1>
        <div class="rounded-lg border bg-white p-4 cursor-pointer w-full shadow relative max-w-sm h-12" v-on:click="stickCounter">
          <p v-for="n in stick.length" :key=stick[n-1] class="text-center content" v-bind:class="{apper: stickCount==n-1}">{{stick[n-1]}}</p>
        </div>
      </div>
      <div class="py-2 w-full flex flex-col items-center justify-center">
        <h1 class="text-white">温め</h1>
        <div class="rounded-lg border bg-white p-4 cursor-pointer w-full relative max-w-sm h-12" v-on:click="heatCounter">
          <p v-for="n in heat.length" :key=heat[n-1] class="text-center content" v-bind:class="{apper: heatCount==n-1}">{{heat[n-1]}}</p>
        </div>
      </div>
      <div class="py-2 w-full flex flex-col items-center justify-center">
        <h1 class="text-white">支払い</h1>
        <div class="rounded-lg border bg-white p-4 cursor-pointer w-full relative max-w-sm h-12" v-on:click="paymentCounter">
          <p v-for="n in payment.length" :key=payment[n-1] class="text-center content" v-bind:class="{apper: paymentCount==n-1}">{{payment[n-1]}}</p>
        </div>
      </div>
    </div>
    <div class="flex w-full p-4 justify-around container px-5 mx-auto my-10">
      <div v-on:click="colorChange" id="0" class="bg-blue-600 rounded-full p-4"></div>
      <div v-on:click="colorChange" id="1" class="bg-red-600 rounded-full p-4"></div>
      <div v-on:click="colorChange" id="2" class="bg-green-600 rounded-full p-4"></div>
      <div v-on:click="colorChange" id="3" class="bg-yellow-600 rounded-full p-4"></div>
      <div v-on:click="colorChange" id="4" class="bg-gray-600 rounded-full p-4"></div>
    </div>
  </div>
  
</template>

<script>
export default {
  data() {
    return {
      bgColor: 0,
      bag: ["いる", "いらない"],
      bagCount: 0,
      point: ["持っている", "持っていない"],
      pointCount: 0,
      stick: ["いる", "いらない"],
      stickCount: 0,
      heat: ["不要", "おにぎり", "弁当", "全部"],
      heatCount: 0,
      payment: ["現金", "クレジット", "電子マネー", "払いたくない"],
      paymentCount: 0,
    }
  },
  methods: {
    colorChange: function (e) {
      var color = e.target.id
      this.bgColor = color
    },
    bagCounter: function () {
      this.bagCount += 1
      if (this.bagCount == this.bag.length) {
        this.bagCount = 0
      }
    },
    pointCounter: function () {
      this.pointCount += 1
      if (this.pointCount == this.point.length) {
        this.pointCount = 0
      }
    },
    stickCounter: function () {
      this.stickCount += 1
      if (this.stickCount == this.stick.length) {
        this.stickCount = 0
      }
    },
    heatCounter: function () {
      this.heatCount += 1
      if (this.heatCount == this.heat.length) {
        this.heatCount = 0
      }
    },
    paymentCounter: function() {
      this.paymentCount +=1
      if (this.paymentCount == this.payment.length) {
        this.paymentCount = 0
      }
    }
  },
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.content {
  position: absolute;
  top:50%;
  left: 50%;
  transform: translate(-50%, -50%);
  transition: all .3s;
  opacity: 0;
}
.apper {
  opacity: 1;
}
.blue {
  @apply bg-blue-600
}
.red {
  @apply bg-red-600
}
.green {
  @apply bg-green-600
}
.yellow {
  @apply bg-yellow-600
}
.gray {
  @apply bg-gray-600
}
</style>
