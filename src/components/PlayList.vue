<template>
<div>
    <div class="sellection">

        <div >
            <div class="added_list" >
                <h2 @click="select_Play_song">{{selectedSong[`title`]}}</h2>
                <p> Artist Name:{{selectedSong[`artist`]}}</p>
                <img :src="selectedSong[`image_url`]" alt="song album image">         
            </div>
        </div>
    </div>
</div>
</template>

<script>

export default {
   
    props: {
            selectedSong: Object,
    },
   
    data() {
        return {
            displaySongTitle:undefined,
            displaySongArtist:undefined,
            displaySongId: undefined,
            currentPlayingSong:[]
        }
    },
    methods: {
        select_Play_song: function ( details ) {
            let get_title = details[`target`].innerText;
            this.currentPlayingSong.push(this.selectedSong)
            for ( let i = 0; i < this.currentPlayingSong.length; i++ ){
                if ( get_title ===  this.currentPlayingSong[i][`title`]){
                    this.$emit( `select_Play_song`, this.currentPlayingSong[i][`title`])
                 
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
width: 40%;
}
.add_btn{
    justify-self: end;
}
img{
    max-width: 100%;
    
}
</style>