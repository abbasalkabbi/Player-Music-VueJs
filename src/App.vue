<template>
  <div id="app">
    <div class="container">
      <!------Start Header--->
      <app-header :title="name" />
      <control-player
        :title="current.title"
        :isplaying="isplaying"
        :namehaj="current.artist"
      />
    </div>

    <div class="list-music">
      <app-header :title="namelist" /><app-list :music="songs" :index="index" />
    </div>
  </div>
</template>

<script>
import AppHeader from "@/components/AppHeader.vue";
import ControlPlayer from "@/components/ControlPlayer.vue";
import AppList from "@/components/AppList.vue";
export default {
  name: "App",
  components: {
    AppHeader,
    ControlPlayer,
    AppList,
  },
  data: () => {
    return {
      name: "MY-Music",
      namelist: "Music-List",
      isplaying: false,
      current: {},
      index: 0,
      songs: [
        {
          id: 0,
          title: "Haider",
          artist: " Haj Mahmoud Karimi",
          src: require("./assets/music/Haider.mp3"),
        },
        {
          id: 1,
          title: "FRAR",
          artist: "IRAN",
          src: require("./assets/music/frar.mp3"),
        },
        {
          id: 2,
          title: "ستعجزون",
          artist: "محمد الفتلاوي",
          src: require("./assets/music/ستعجزون ولن نعجز الاصلية لـ الشيخ حسين الاكرف بصوت محمد الفتلاوي ( النسخة العراقية ).mp3"),
        },
        {
          id: 3,
          title: "Tasbeeh Al Zahra'a ",
          artist: "Haj Mahdi Rasoli",
          src: require("./assets/music/Tasbeeh Al Zahra'a Haj Mahdi Rasoli English Sub.mp3"),
        },
        {
          id: 4,
          title: "ليث المعركة ",
          artist: "محمد الخياط",
          src: require("./assets/music/ليث المعركة محمد الخياط Video Clip 2018.mp3"),
        },
      ],
      player: new Audio(),
    };
  },
  created() {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
  },
  methods: {
    play() {
      this.player.play();
      this.isplaying = true;
    },
    pause() {
      this.player.pause();
      this.isplaying = false;
    },
    list(id) {
      this.index = id;
      this.current = this.songs[this.index];
      this.player.src = this.current.src;
      this.play();
    },
    next() {
      if (this.index >= this.songs.length - 1) {
        this.index = 0;
      } else {
        this.index++;
      }
      this.current = this.songs[this.index];
      this.player.src = this.current.src;
      this.play();
    },
    prev() {
      if (this.index == 0) {
        this.index = this.songs.length - 1;
      } else {
        this.index--;
      }

      this.current = this.songs[this.index];
      this.player.src = this.current.src;
      this.play();
    },
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: cursive;
  text-shadow: #000 12px 10px 16px;
}
body {
  background: #dbdbdb;
}
#app {
  text-align: center;
}
.container {
  margin: auto;
  width: 400px;
  height: 100vh;
  background: rgba(0, 0, 0, 0.829);

  box-shadow: 20px 13px 20px 0px rgb(0 0 0 / 50%),
    -20px -13px 20px 0px rgb(0 0 0 / 50%);
}
.list-music {
  margin: auto;
  width: 400px;
  height: 300px;
  box-shadow: 20px 13px 20px 0px rgb(0 0 0 / 20%),
    -20px -13px 20px 0px rgb(0 0 0 / 20%);
}
@media only screen and (max-width: 400px) {
  .container {
    height: 100%;
    padding-bottom: 20px;
  }
}
@media only screen and (min-width: 600px) {
  .container {
    margin: 10px auto;
  }
  #app {
    display: flex;
    justify-content: center;
  }
  .list-music {
    margin-left: 10px;
    width: 400px;
    height: 100vh;
    background: rgba(0, 0, 0, 0.829);
  }
}
</style>
