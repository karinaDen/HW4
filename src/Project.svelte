<script lang="ts">
    interface Inpt {
        url: string;
    }
    let getData = async () => {
        let response = await fetch("https://random.dog/woof.json");
        let myInpt: Inpt = await response.json();
        console.log(myInpt.url);
        return myInpt.url;
    }
    async function call() {
        event.preventDefault();
        let img = document.getElementById('image') as HTMLImageElement;
        img.src   = await getData();
    }
</script>
<main>
    <body>
    <div class="flexbox-container">
        <div class="flexbox1">
            psst, want some dog pictures? click on button👽
        </div>
        <div class="flexbox2">
            <button id="generate1" on:click = {call}>
                click
            </button>
        </div>

        <div class="image-container">

            <img id = "image" src="">
        </div>


    </div>
    </body>
</main>

<style>

    body {
        font-family: 'Inika', serif;
        position: relative;

        width: 100%;
        top: 74px;
        height: calc(1000px - 260px);

        background: #FFECEB;
    }
    .flexbox-container{
        display: flex;
        flex-direction: column;
        align-items: center;
        top: 74px;
    }
    .flexbox1{
        display: flow-root;
        text-align: center;
        margin-top: 20px;
        font-size: 30px;
    }

</style>