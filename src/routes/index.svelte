<script>
    //init
    import jsonData from './songs.json';
    import {Howl, Howler} from 'howler';
    var id = 1;
    var title = JSON.stringify(jsonData.songs[id].title).replace(/['"]+/g, '');
    var artist = JSON.stringify(jsonData.songs[id].artist).replace(/['"]+/g, '');
    var filePath = JSON.stringify(jsonData.songs[id].filePath).replace(/['"]+/g, '');
    var bruh = artist + " - " + title;
    var isPlaying = false;


    function update(){
        console.log(id)
        console.log(bruh);
        title = JSON.stringify(jsonData.songs[id].title).replace(/['"]+/g, '');
        artist = JSON.stringify(jsonData.songs[id].artist).replace(/['"]+/g, '');
        bruh = artist + " - " + title;
    }
    function nextSong(){
        id++;
        update()
    }
    function prevSong(){
        id--;
        update()
    }
    function stopSong(){
        var filePath = JSON.stringify(jsonData.songs[id].filePath).replace(/['"]+/g, '');
        var audio = new Audio(filePath);
        audio.pause();
        audio.currentTime = 0;
    }
    function playSong(){
        var sound = new Audio(filePath);
        sound.play();
    }
</script>

<main>
    <p>{bruh}</p>
    <audio id="Audio">
        <source src="{filePath}" type="audio/mpeg">
        Your browser does not support the audio element.
    </audio>
    <div class="player">
        <button on:click="{prevSong}">prev</button>
        <button on:click="{playSong}">play</button>
        <button on:click="{nextSong}">next</button>
    </div>
</main>
<style>
.player{
    background-color: aliceblue;
    border-radius: 10px;
    
}
main{
    text-align: center;
    
}
</style>