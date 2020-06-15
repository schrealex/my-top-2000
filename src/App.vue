<template>
  <div id="app">
    <div class="left">
      <h1>My Top 2000</h1>
      <img v-if="selectedSong" :src="'/static/images/' + selectedSong.image" />
    </div>
    <ul>
      <li v-for="song in getMyTop2000Songs" :key="song.songTitle" @mouseover="selectedSong = song" @mouseleave="selectedSong = null">
        {{ song.artist }} - {{ song.songTitle }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      selectedSong: null,
      myTopSongs: [
        {
          artist: 'Danny Vera',
          songTitle: 'Rollercoaster',
          image: 'danny_vera-rollercoaster.jpg',
        },
        {
          artist: 'Danny Vera',
          songTitle: 'Distant Rumble',
          image: 'danny_vera-distant_rumble.jpg',
        },
        {
          artist: 'The Cult',
          songTitle: 'She Sells Sanctuary',
          image: 'the_cult-she_sells_sanctuary.webp',
        },
        {
          artist: 'Foo Fighters',
          songTitle: 'Everlong',
          image: 'foo_fighters-everlong.jpg',
        },
        {
          artist: 'Foo Fighters',
          songTitle: 'Times Like These',
        },
        {
          artist: 'Foo Fighters',
          songTitle: 'These Days',
        },
        {
          artist: 'The Beatles',
          songTitle: 'I\'m Looking Through You',
        },
        {
          artist: 'The Beatles',
          songTitle: 'Blackbird',
        },
        {
          artist: 'The Beatles',
          songTitle: 'While My Guitar Gently Weeps',
        },
        {
          artist: 'The Beatles',
          songTitle: 'Here Comes The Sun',
        },
        {
          artist: 'The Beatles',
          songTitle: 'Dear Prudence',
        },
        {
          artist: 'Electric Light Orchestra',
          songTitle: 'Mr. Blue Sky',
        },
        {
          artist: 'Cream',
          songTitle: 'White Room',
        },
        {
          artist: 'Tom Petty',
          songTitle: 'Runnin\' Down A Dream',
        },
        {
          artist: 'Kansas',
          songTitle: 'Carry On Wayward Son',
        },
        {
          artist: 'The Beatles',
          songTitle: 'Got To Get You Into My Life',
        },
        {
          artist: 'Creedence Clearwater Revival',
          songTitle: 'Fortunate Son',
        },
        {
          artist: 'Creedence Clearwater Revival',
          songTitle: 'Long As I Can See The Light',
        },
        {
          artist: 'Creedence Clearwater Revival',
          songTitle: 'Bad Moon Rising',
        },
        {
          artist: 'Soundgarden',
          songTitle: 'Black Hole Sun',
        },
        {
          artist: 'Dire Straits',
          songTitle: 'Sultans Of Swing',
        },
        {
          artist: 'Blind Melon',
          songTitle: 'No Rain',
        },
        {
          artist: 'Led Zeppelin',
          songTitle: 'Stairway To Heaven',
        },
        {
          artist: 'Steely Dan',
          songTitle: 'Reelin\' In The Years',
        },
        {
          artist: 'Pearl Jam',
          songTitle: 'Even Flow',
        },
        {
          artist: 'Kings of Leon',
          songTitle: 'Notion',
        },
        {
          artist: 'Living Colour',
          songTitle: 'Solace Of You',
        },
        {
          artist: 'Living Colour',
          songTitle: 'Love Rears Its Ugly Head',
        },
        {
          artist: 'Muse',
          songTitle: 'Plug In Baby',
        },
        {
          artist: 'Free',
          songTitle: 'All Right Now',
        },
        {
          artist: 'Red Hot Chili Peppers',
          songTitle: 'Under The Bridge',
        },
        {
          artist: 'U2',
          songTitle: 'With Or Without You',
        },
        {
          artist: 'Elvis Presley',
          songTitle: 'Suspicious Minds',
        },
        {
          artist: 'Jimi Hendrix Experience',
          songTitle: 'The Wind Cries Mary',
        },
        {
          artist: 'Jimi Hendrix Experience',
          songTitle: 'Hey Joe',
        },
      ],
    };
  },
  computed: {
    getMyTop2000Songs() {
      return this.myTopSongs.slice().sort((a, b) => {         
        if (a.artist === b.artist) {
          return a.songTitle.localeCompare(b.songTitle);
        }
        return a.artist > b.artist ? 1 : -1;
      });
    },
  },
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Montserrat:900');

html, body {
  margin: 0;
  padding: 0;
  background-color: #222222;
}

#app {
  font-family: 'Montserrat', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #222222;

  display: flex;
  font-size: 1.3em;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-start;
}

.left {
  margin-left: 100px;

  img {
    position: fixed;
    top: calc(50% - 254px);
    border: 8px solid #f3c500;
  }
}

h1 {
  -webkit-text-stroke: 2px #f3c500;
}

ul {
  width: 1300px;
  list-style: none;
  text-align: left;
  padding: 0;

  li {
    color: var(--mainColor);
    text-decoration: none;
    text-align: center;
    cursor: pointer;
    transition: 0.6s;
  }
}

:root {
  --mainColor: #808080;
}

li:hover {
  color: transparent;
  -webkit-text-stroke: 2px #f3c500;
  font-size: 1.9em;
}

@supports not(-webkit-text-stroke: 2px red) {
  li:hover {
    font-size: 2.2em;
    text-shadow:
      3px 3px 0 var(--mainColor),
      -1px -1px 0 var(--mainColor),
      1px -1px 0 var(--mainColor),
      -1px 1px 0 var(--mainColor),
      1px 1px 0 var(--mainColor);
  }
}
</style>
