<template>
  <div v-bind:id="playerId">
<!--    <div  class="prism-player" id="J_prismPlayer"></div>-->
  </div>
</template>
<script>
  export default {
    name: 'player',
    props: {
      playerId: {
        default: "player-div"
      },
    },
    data: function () {
      return {
        aliPlayer: {}, // 播放器实例
      }
    },
    methods: {
      playUrl(url) {
        let _this = this;
        console.log("开始播放:", url);

        //如果已经有播放器了，则将播放器div删除
        if (_this.aliPlayer) {
          _this.aliPlayer = null;
          $("#" + _this.playerId + '-player').remove();
        }

        // 初始化播放器
        $("#" + _this.playerId).append("<div class=\"prism-player\" id=\"" + _this.playerId + "-player\"></div>");
        _this.aliPlayer = new Aliplayer({
          id: _this.playerId + '-player',
          width: '100%',
          autoplay: false,
          source: url,
          cover: 'http://zj-course.oss-cn-shanghai.aliyuncs.com/logo.jpg',
        }, function (player) {
          console.log('播放器创建好了。')
        });
      },

      playVod (vod) {
        let _this = this;
        Loading.show();
        _this.$ajax.get(process.env.VUE_APP_SERVER + '/file/admin/get-auth/' + vod).then((response)=>{
          Loading.hide();
          let resp = response.data;
          if (resp.success) {
            //如果已经有播放器了，则将播放器div删除
            if (_this.aliPlayer) {
              _this.aliPlayer = null;
              $("#" + _this.playerId + '-player').remove();
            }

            // 初始化播放器
            $("#" + _this.playerId).append("<div class=\"prism-player\" id=\"" + _this.playerId + "-player\"></div>");
            _this.aliPlayer = new Aliplayer({
              id: _this.playerId + '-player',
              width: '100%',
              autoplay: false,
              vid: vod,
              playauth: resp.content,
              cover: 'http://zj-course.oss-cn-shanghai.aliyuncs.com/logo.jpg',
              encryptType:1, //当播放私有加密流时需要设置。
            },function(player){
              console.log('播放器创建好了。')
            });
          } else {
            Toast.warning('播放错误。')
          }
        })

      }
    }
  }
</script>