<template>
  <div class="container effect7">
    <canvas id="canvas"></canvas>
    <div class="dl-vignette" v-on:click="download" v-if="hasUploaded">
      <span>Download photo</span>
    </div>
    <div class="actions">
      <input type="file" name="file" id="file" class="inputfile" accept="image/*"/>
      <label for="file" class="btn">Update photo</label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Frame',
  props: {
    msg: String
  },

  data: function() {
    return {
      hasUploaded: false
    };
  },

  methods: {
    download() {
      var link = document.createElement('a');
      link.download = 'endalz.png';
      link.href = document.getElementById('canvas').toDataURL()
      link.click();
    }
  },

  mounted() {
    document.addEventListener('DOMContentLoaded', function() {
      document.fonts.load('10pt "Maven Pro"').then(renderCanvas);

      function renderCanvas() {
        let canvas = document.getElementById('canvas');
        canvas.width  = canvas.parentElement.clientWidth;
        canvas.height = canvas.parentElement.clientHeight;

        if (canvas.getContext) {
          let ctx = canvas.getContext('2d');
          renderFrame(ctx);
        }
      }
    });
    var $this = this;

    function renderFrame(ctx) {
      let canvas = ctx.canvas;
      let layer1 = {
        top: canvas.height - 100,
        height: 100,
        width: canvas.width
      };

      ctx.fillStyle = '#4a0d66';
      ctx.fillRect(0, layer1.top, layer1.width, layer1.height);


      let fontSize = 180;
      ctx.font = `bold ${fontSize}px 'Maven Pro'`;
      ctx.fillStyle = '#5b236f';
      ctx.fillText("#", 140, 480);


      fontSize = 30;
      ctx.font = `bold ${fontSize}px 'Maven Pro'`;
      ctx.fillStyle = '#FFFFFF';
      ctx.fillText("#ENDALZ", layer1.width/2 - fontSize * 2, layer1.top + layer1.height/2 + 8);
    }

    let img = new Image();
    document.getElementById('file').addEventListener('change', handleFiles, false);

    function handleFiles(e) {
      var ctx = document.getElementById('canvas').getContext('2d');
      var reader  = new FileReader();
      var file = e.target.files[0];
      this.hasUploaded = true;
      img.onload = function() {
        $this.hasUploaded = true;
        // @TODO: Scale image or center
        // ctx.canvas.width = img.width;
        // ctx.canvas.height = img.height;
        ctx.drawImage(img, 0, 0
            , ctx.canvas.width, ctx.canvas.height
        );
        renderFrame(ctx);
      }
      reader.onloadend = function () {
          img.src = reader.result;
      }
      reader.readAsDataURL(file);
    }

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
  margin-top: -160px;
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

.dl-vignette {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 2;
  width: 480px;
  height: 480px;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
}

.dl-vignette:hover {
  opacity: 1;
  background-color: rgba(0, 0, 0, 0.7);
}

.dl-vignette span {
  font-size: 18px;
  color: white;
}

.actions {
  padding-top: 30px;
}

.btn {
  font-family: Arial;
  color: #ffffff;
  font-size: 14px;
  background: #333333;
  padding: 16px 40px 16px 40px;
  text-decoration: none;
  cursor: pointer;
}

.btn:hover {
  background: #6e46ae;
  text-decoration: none;
}

.inputfile {
  width: 0.1px;
  height: 0.1px;
  opacity: 0;
  overflow: hidden;
  position: absolute;
  z-index: -1;
}
</style>
