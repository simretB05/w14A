<template>
    <div>
        <div class="current">
                    <h3 class="sellection_title">Currently playing song</h3>
                    <div class="now_playing">
                        <p> Currently-Playing Song:<br><span class="change">{{currentPlayingSong}}</span></p>
                        <p> Artist:<br><span class="change">{{currentPlayingArtist}}</span></p>
                    </div>
                </div>
    </div>
</template>

<script>
    //created a props that keeps the value of currentPlayingSong and  currentPlayingArtist(a binded Attribute) which are made available throgh props,
    //  which are in string form  and used them to displaythe title and Artist values,
    //  in my case only the title becouse I coudnt figure out why the name of the artist is not displaying

    export default {
        props: {
            currentPlayingSong: String,
            currentPlayingArtist:String
         
    },
    }
</script>

<style scoped>
.current{
    border: 2px solid rgb(16, 75, 34);
    width:100%;
}
.change{
    color: rgb(226, 43, 61);
    font-weight:600;
}
</style>