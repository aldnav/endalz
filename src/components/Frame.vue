<template>
  <div class="container effect7">
    <canvas id="canvas"></canvas>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },

  mounted() {

    document.addEventListener('DOMContentLoaded', function() {
      let canvas = document.getElementById('canvas');
      canvas.width  = canvas.parentElement.clientWidth;
      canvas.height = canvas.parentElement.clientHeight;

      let layer1 = {
        top: canvas.height - 100,
        height: 100,
        width: canvas.width
      };

      if (canvas.getContext) {
        let ctx = canvas.getContext('2d');

        ctx.fillStyle = '#4a0d66';
        ctx.fillRect(0, layer1.top, layer1.width, layer1.height);

        let fontSize = 180;
        ctx.font = `bold ${fontSize}px Arial`;
        ctx.fillStyle = '#5b236f';
        ctx.fillText("#", 80, 485);


        fontSize = 30;
        ctx.font = `bold ${fontSize}px Arial`;
        ctx.fillStyle = '#FFFFFF';
        ctx.fillText("#ENDALZ", layer1.width/2 - fontSize * 2, layer1.top + layer1.height/2);
      }
    });

  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.container {
  width: 480px;
  height: 480px;
  background: #fff;
  position: relative;
  z-index: 2;
  margin-top: -120px;
  display: block;
  margin-left: auto;
  margin-right: auto;
}


/* Effects */
.effect7
{
    -webkit-box-shadow:0 4px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
       -moz-box-shadow:0 4px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
            box-shadow:0 4px 4px rgba(0, 0, 0, 0.3), 0 0 40px rgba(0, 0, 0, 0.1) inset;
}
.effect7:after
{
    right:10px;
    left:auto;
    -webkit-transform:skew(8deg) rotate(3deg);
       -moz-transform:skew(8deg) rotate(3deg);
        -ms-transform:skew(8deg) rotate(3deg);
         -o-transform:skew(8deg) rotate(3deg);
            transform:skew(8deg) rotate(3deg);
}

#canvas {
  width: 100%;
  height: 100%;
}

</style>
