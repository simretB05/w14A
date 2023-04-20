<template>
    <div>
        <div class="current">
                    <h3 class="sellection_title">Currently playing song</h3>
                    <div class="now_playing">
                        <p> Currently-Playing Song:<br><span class="change">{{currentPlayingSong}}</span></p>
                    </div>
                  

                </div>
    </div>
</template>

<script>
    export default {
        props: {
            currentPlayingSong:String,
         
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