<template>
  <div class="live-info">
      <div class="top" ref="top">
          <div class="user-info" ref="userInfo">
              <div class="user-pic" @click="toUserIndex">
                <img :src="userInfo.userpic" class="pic">
              </div>
              <div class="user-name" @click="toUserIndex">{{userInfo.name}}</div>
              <a @click="toAbout" class="focus" >关注</a>
          </div>
          <div class="people" v-if="!liveEnded" :style="{ width: width + 'px' }">
            <div class="people-pic" v-for="(item, index) in poepleNum" :style="{ background: 'url(' + watcherInfo.userpic + ') no-repeat center', backgroundSize: '100%'}" :key="index" @click="showPeople(watcherInfo, index)">
              <div class="vlevel">V4</div>
            </div>
          </div>
      </div>
      <div class="bottom">
        <div class="id">富聊ID:{{userInfo.userid}}</div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'LiveInfo',
  props: ['userInfo', 'watcherInfo', 'liveEnded'],
  data () {
    return {
      poepleNum: Array.from({ length: Math.ceil(Math.random() * 10) }),
      width: 0
    }
  },
  methods: {
    toUserIndex () {
      this.$emit('toUserIndex', this.userInfo.userid)
    },
    showPeople (watcherInfo, index) {
      this.$emit('showPeople', watcherInfo, index + 1)
    },
    toAbout () {
      this.$router.push({
        name: 'About'
      })
    }
  },
  mounted () {
    let width = document.body.offsetWidth / 100
    this.width = this.$refs.top.offsetWidth - this.$refs.userInfo.offsetWidth - width * 2 - 1
  }
}
</script>

<style lang="less" scroped>
.live-info {
  .wrapper(@height: 20vw;);
  box-sizing: border-box;
  padding: 2vw;
  background: linear-gradient(rgba(0, 0, 0, 0.6), rgba(255, 255, 255, 0));
  .top {
      .wrapper(@height: 8vw; @left: 2vw; @width: 96vw; @top: 2vw;);
      .user-info {
        position: relative;
        float: left;
        height: 100%;
        background-color: rgba(0, 0, 0, .8);
        border-radius: 8vw;
        margin-right: 2vw;
        .user-pic {
          float: left;
          width: 8vw;
          height: 8vw;
          border-radius: 50%;
          margin-left: 1px;
          overflow: hidden;
          .pic {
            width: 100%;
            height: 100%;
          }
        }
        .user-name {
          float: left;
          line-height: 8vw;
          font-size: 2.5vw;
          padding: 0 2vw;
          color: #fff;
        }
        .focus {
          float: left;
          font-size: 3vw;
          color: #fff;
          .wrapper(@position: relative; @top: 1.5vw;);
          margin-right: 1vw;
          .line-height-height(5vw);
          text-align: center;
          width: 8vw;
          background-color: orangered;
          border-radius: 8vw;
        }
      }
      .people {
        float: left;
        overflow: scroll;
        white-space: nowrap;
        height: 12vw;
        .people-pic {
          display: inline-block;
          position: relative;
          width: 8vw;
          height: 8vw;
          margin-right: 1vw;
          border-radius: 50%;
          .vlevel {
            .wrapper(@height: 2vw; @width: 4vw; @top: auto; @bottom: 0; @left: 50%;);
            margin-left: -2vw;
            background-color:deepskyblue;
            text-align: center;
            font-size: 1vw;
          }
        }
      }
  }
  .bottom {
    .wrapper(@height: 8vw; @top: auto; @bottom: 2vw; @left: 2vw; @width: 96vw;);
    .id {
      line-height: 8vw;
      color: #fff;
    }
  }
}
</style>
