<template>
    <main>
        <h1>Best of 80's Hits Collections by Various Artists ...</h1>
        <now-playing :currentPlayingSong="currentPlayingSong" :currentPlayingArtist="currentPlayingArtist" ></now-playing>

    <section>
            <div class="container">
                <div class="main_card">

                    <article   v-for="(song, i) in songs" :key="i" >
                        <h2 >{{song[`title`]}}</h2>
                        <p> Artist Name:{{song[`artist`]}}</p>
                        <img :src="song[`image_url`]" alt="song album image">
                        <button   @click="add_songs" :songid="song[`song_id`]">Add to Play-List</button>
                    </article>
                </div>

            </div>
            <div class="play_list_card" >
                <h1 class="play_list_title">Your play List</h1>
                <p class="check_selection" v-if="noSelectedSongs">{{noSelectedSongs}}</p>
                <div class="play_list">
                <play-list   @select_Play_song="getCurrentPlaying" v-for="(selectedSong, i) in selectedSongs" :key="i"  :selectedSong="selectedSongs[i]"></play-list>
            </div>
            <div class="now_playing">    
            </div>
            </div>
    </section>
  
</main>
</template>

<script>
import PlayList from '@/components/PlayList.vue';
import NowPlaying from './NowPlaying.vue';

export default {
    components: {
        PlayList,
        NowPlaying,
    },
        data() {
            return {
                noSelectedSongs: ' Please select a song!',
                currentPlayingArtist: undefined,
                currentPlayingSong:undefined,
                selectedSongs: [],

                songs:[
                        {
                            title: "Billie Jean",
                            artist: "Michael Jackson",
                            song_id:  "123",
                            image_url:"https://i.ytimg.com/vi/gZRFJyeJLAM/maxresdefault.jpg"
                        },
                        {
                            title: "Sweet Child o' Mine",
                            artist: "Guns N' Roses",
                            song_id: "456",
                            image_url: "https://yt3.googleusercontent.com/XYdITfFzeQBLoNsIIpthkC1jfK9r-jVijx_ULuralq1KaN35Z_tJdgyoB9O-eSCm_NdEgN1E-Ok=s900-c-k-c0x00ffffff-no-rj"
                        },
                        {
                            title: "Like a Prayer",
                            artist: "Madonna",
                            song_id: "789",
                            image_url: "https://i.ytimg.com/vi/IlPCW6nLheM/hq720.jpg?sqp=-oaymwEhCK4FEIIDSFryq4qpAxMIARUAAAAAGAElAADIQj0AgKJD&rs=AOn4CLDFG0GI5nVGiefJK1PwGAW_prr6UA"

                        },
                        {
                            title: "Livin' on a Prayer",
                            artist: "Bon Jovi",
                            song_id: "1011",
                            image_url: "https://i.ebayimg.com/images/g/JNIAAOSw62hjGSQb/s-l1600.jpg"

                        },
                        {
                            title: "Take On Me",
                            artist: "a-ha",
                            song_id: "1213",
                            image_url: "https://i.ytimg.com/vi/djV11Xbc914/maxresdefault.jpg"
                        }
                    ]
                }
    },
    methods: {
        add_songs: function ( details ){
            let get_id = details[`target`].getAttribute(`songid`);
            for ( let i = 0; i < this.songs.length; i++ ){
            if ( get_id===this.songs[i][`song_id`]){
                this.selectedSongs.unshift( this.songs[i] )
                this.noSelectedSongs =''
                break
            }
            }
                
        }, 
        getCurrentPlaying( title, artist){
            this.currentPlayingArtist = artist
            this.currentPlayingSong = title
            console.log( artist )
            console.log(title)

      }
    },

   
}
</script>

<style scoped>
main{
    display:grid;
    place-items: center;
    

}
section{
    display:grid;
    place-items: center;
    min-height: 80vh;
    display: grid;
    grid-template-columns:1fr 1fr;

    

}
.container{
    display:grid;
    place-items: center;
    min-height: 80vh;
    width: 100%;
    grid-template-columns:  1fr 1fr;
}
h1{
    color:rgb(29, 132, 234);
    justify-self: start;
    font-size: 2rem;
    align-self: start;
}
.main_card{
    display:grid;
    place-items: center;
    min-height: 100vh;
    gap:16px;

}
article{
    display:grid;
    place-items: center;
    background-color: lightblue;
    width: 90%;
    padding: 16px;
    min-height: 30%;
    grid-template-columns: 1fr 1fr 1fr;
}
img{
    width:100px;
}
p{
    text-align: start;
    padding: 6px;
    font-weight: 700;

}
.play_list_card{
    display:grid;
    place-items: center;
    align-self: start;
    width: 100%;
    height: 100vh;
    border: 2px solid red;
}
.check_selection{
    align-self: start;
    justify-self: start;
    font-size: 2rem;
    color: red;
}
.play_list_title{
    align-self: start;
}
.play_list{
display:grid;
place-items: center;
  align-self: start;
  justify-self: start;
  grid-template-columns: 1fr 1fr 1fr;
width: 100%;
  max-height: 100%;
  gap:10px;
 

  
}
</style>