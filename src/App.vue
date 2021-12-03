<template>
  <div id="app">
    <div class="left">
      <h1>My Top 2000</h1>
      <transition name="fade">
        <img v-show="showCoverArt" :src="'/static/images/' + selectedSong.image" :alt="`${selectedSong.songTitle} cover art`" />
      </transition>
    </div>
    <ul>
      <li v-for="song in getMyTop2000Songs" :key="song.songTitle">
        <span @mouseover="onSongMouseOver(song)" @mouseleave="onSongMouseLeave()">{{ song.artist }} - {{ song.songTitle }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {},
  data() {
    return {
      showCoverArt: false,
      selectedSong: {
        image: '',
      },
      myTopSongs: [
        {
          artist: 'The Cult',
          songTitle: 'She Sells Sanctuary',
          image: 'the_cult-she_sells_sanctuary.jpg',
        },
        {
          artist: 'Foo Fighters',
          songTitle: 'Best of You',
          image: 'foo_fighters-best-of-you.jpg',
        },
        {
          artist: 'Foo Fighters',
          songTitle: 'Times Like These',
          image: 'foo_fighters-times_like_these.jpg',
        },
        {
          artist: 'Foo Fighters',
          songTitle: 'Learn to Fly',
          image: 'foo_fighters-learn-to-fly.jpg',
        },
        {
          artist: 'The Beatles',
          songTitle: 'Get Back',
          image: 'the_beatles-get_back.jpg',
        },
        {
          artist: 'The Beatles',
          songTitle: 'Something',
          image: 'the_beatles-something.jpg',
        },
        {
          artist: 'The Beatles',
          songTitle: 'Dear Prudence',
          image: 'the_beatles-dear_prudence.jpg',
        },
        {
          artist: 'The Beatles',
          songTitle: 'While My Guitar Gently Weeps',
          image: 'the_beatles-while_my_guitar_gently_weeps.jpg',
        },
        {
          artist: 'The Beatles',
          songTitle: 'Got To Get You Into My Life',
          image: 'the_beatles-got_to_get_you_into_my_life.jpg',
        },
        {
          artist: 'Electric Light Orchestra',
          songTitle: 'Mr. Blue Sky',
          image: 'electric_light_orchestra-mr._blue_sky.jpg',
        },
        {
          artist: 'Cream',
          songTitle: 'White Room',
          image: 'cream-white_room.jpg',
        },
        {
          artist: 'Tom Petty',
          songTitle: 'Runnin\' Down A Dream',
          image: 'tom_petty-runnin\'_down_a_dream.jpg',
        },
        {
          artist: 'Kansas',
          songTitle: 'Carry On Wayward Son',
          image: 'kansas-carry_on_wayward_son.jpg',
        },
        {
          artist: 'Creedence Clearwater Revival',
          songTitle: 'Green River',
          image: 'creedence_clearwater_revival-green_river.jpg',
        },
        {
          artist: 'Creedence Clearwater Revival',
          songTitle: 'Have You Ever Seen The Rain',
          image: 'creedence_clearwater_revival-have_you_ever_seen_the_rain.jpg',
        },
        {
          artist: 'Creedence Clearwater Revival',
          songTitle: 'Long As I Can See The Light',
          image: 'creedence_clearwater_revival-long_as_i_can_see_the_light.jpg',
        },
        {
          artist: 'Derek & The Dominos',
          songTitle: 'Layla',
          image: 'derek_&_the_dominos-layla.jpg',
        },
        {
          artist: 'Eddie Rabbitt',
          songTitle: 'Drivin\' My Life Away',
          image: 'eddie_rabbitt-drivin_my_life_away.jpg',
        },
        {
          artist: 'Van Morrison',
          songTitle: 'Bright Side Of The Road',
          image: 'van_morrison-bright_side_of_the_road.jpg',
        },
        {
          artist: 'Led Zeppelin',
          songTitle: 'Stairway To Heaven',
          image: 'led_zeppelin-stairway_to_heaven.jpg',
        },
        {
          artist: 'Jackson Browne',
          songTitle: 'Running On Empty',
          image: 'jackson_browne-running_on_empty.jpg',
        },
        {
          artist: 'Pearl Jam',
          songTitle: 'Alive',
          image: 'pearl_jam-alive.jpg',
        },
        {
          artist: 'Hollies',
          songTitle: 'Long Cool Woman (In A Black Dress)',
          image: 'hollies-long_cool_woman_(in_a_black_dress).jpg',
        },
        {
          artist: 'Living Colour',
          songTitle: 'Solace Of You',
          image: 'living_colour-solace_of_you.jpg',
        },
        {
          artist: 'Rolling Stones',
          songTitle: 'Gimme Shelter',
          image: 'rolling_stones-gimme_shelter.jpg',
        },
        {
          artist: 'Muse',
          songTitle: 'Plug In Baby',
          image: 'muse-plug_in_baby.jpg',
        },
        {
          artist: 'Queen',
          songTitle: 'A Kind Of Magic',
          image: 'queen-a_kind_of_magic.jpg',
        },
        {
          artist: 'Red Hot Chili Peppers',
          songTitle: 'Under The Bridge',
          image: 'red_hot_chili_peppers-under_the_bridge.jpg',
        },
        {
          artist: 'Pink Floyd',
          songTitle: 'Echoes',
          image: 'pink_floyd-echoes.jpg',
        },
        {
          artist: 'Elvis Presley',
          songTitle: 'Burning Love',
          image: 'elvis_presley-burning_Love.jpg'
        },
        {
          artist: 'Elvis Presley',
          songTitle: 'Suspicious Minds',
          image: 'elvis_presley-suspicious_minds.jpg'
        },
        {
          artist: 'Jimi Hendrix Experience',
          songTitle: 'The Wind Cries Mary',
          image: 'jimi_hendrix_experience-the_wind_cries_mary.jpg',
        },
        {
          artist: 'Fleetwood Mac',
          songTitle: 'Dreams',
          image: 'fleetwood_mac-dreams.jpg',
        },
        {
          artist: 'Paul Simon',
          songTitle: 'The Boy In The Bubble',
          image: 'paul_simon-the_boy_in_the_bubble.jpg',
        },
        {
          artist: 'Terence Trent D\'Arby',
          songTitle: 'Wishing Well',
          image: 'terence_trent_darby-wishing_well.jpg',
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
  methods: {
    onSongMouseOver(song) {
      this.selectedSong = song;
      this.showCoverArt = true;
    },
    onSongMouseLeave() {
      this.showCoverArt = false;
    },
  }
};
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
  font-size: 1.8em;
}

@supports not(-webkit-text-stroke: 2px red) {
  li:hover {
    font-size: 2.2em;
    text-shadow: 3px 3px 0 var(--mainColor),
    -1px -1px 0 var(--mainColor),
    1px -1px 0 var(--mainColor),
    -1px 1px 0 var(--mainColor),
    1px 1px 0 var(--mainColor);
  }
}

.fade-enter-active {
  transition: opacity 2s ease-in-out;
}

.fade-enter-to {
  opacity: 1;
}

.fade-enter {
  opacity: 0;
}
</style>
