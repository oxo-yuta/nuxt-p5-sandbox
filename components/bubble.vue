<template>
  <v-row>
    <v-col>
      <v-card width="500" height="500">
        <div :id="`canvas-${_uid}`"></div>
      </v-card>
    </v-col>
  </v-row>
</template>

<script lang="ts">
import p5 from 'p5'
import Vue from 'vue'

export default Vue.extend({
  mounted(){
    console.log(this._uid)
    const uid = this._uid
    const script = function (p5: p5) {
      const color1 = p5.color("#fffbe3");
      const color2 = p5.color("#24495c");
      let color1amount = 1;

      p5.setup = () => {
        console.log(uid)
        // setup canvas
        const canvas = p5.createCanvas(500, 500)
        canvas.parent(`canvas-${uid}`);

        // codes
        p5.background(0);
        p5.angleMode(p5.DEGREES);
        p5.noStroke();
        p5.background("#131821");
        p5.blendMode(p5.LIGHTEST);
      }

      p5.draw = () => {
        p5.fill(p5.lerpColor(color2, color1, color1amount));
        p5.translate(p5.width / 2, p5.height / 2);
        p5.rotate(p5.frameCount * 13);
        p5.ellipse(p5.frameCount / 2, 0, p5.frameCount, p5.frameCount / 3);
        color1amount *= 0.995;
      }
    }
    const P5 = require('p5')
    new P5(script)
  }
})

</script>