<template>
<div>
    <div class="sellection">
        <div >
            <div  @click="select_Play_song" class="added_list" :playId="selectedSong[`song_id`]" >
                <h2 >{{selectedSong[`title`]}}</h2>
                <img :src="selectedSong[`image_url`]" alt="song album image"> 
                <p> Artist Name:{{selectedSong[`artist`]}}</p>
                        
            </div>
        </div>
    </div>
</div>
</template>

<script>

export default {
    //created a props that keeps the value of selectedSong(a binded Attribute), which is in an object form 
    props: {
            selectedSong: Object,
    },
   
    data() {
        return {
        //created variables with undefind values , and with  empty array  
            displaySongTitle:undefined,
            displaySongArtist:undefined,
            displaySongId: undefined,
            currentPlayingSong:[]
        }
    },
    methods: {
        //created a method that takes details as Argument
        select_Play_song: function ( details ) {
            let get_id = details[`target`].getAttribute( `playId` );
        // pushed the value of our props (object) in to the empty arry
            this.currentPlayingSong.push(this.selectedSong)
            for ( let i = 0; i < this.currentPlayingSong.length; i++ ){
            // looped through the currentlyPlayingSong Array and check if we have the same  id number 
            //if the id are the same we will  set emite  function call with name  and data in this case the title and artist values
                if ( get_id === this.currentPlayingSong[i][`song_id`] ) {
                    
                    this.$emit( `select_Play_song`, this.currentPlayingSong[i][`title`] )
                    this.$emit( `select_Play_song`, this.currentPlayingSong[i][`artist`])

                    break
                }
            }
      }
        
      
    }
       
    }
    
</script>

<style scoped>
.sellection{
    min-height: 20vh;
    align-self: start;
    display: grid;
  place-items:center ;
  align-self: start;
  
}
.sellection_title{
font-size: 3rem;
    width: 100%;
}
.sellection_title ~p{
    font-size: 2rem;

}
.selected_songs{
     font-size: 1.3rem;
     color: green;
}
.added_list{
place-items: center;
background-color: papayawhip;
width: 100%;
}
.add_btn{
    justify-self: end;
}
img{
    max-width: 100%;
    
}
</style>