<script lang="ts">
    interface Inptut {
        url: string;
    }
    let getAPI = async () => {
        let res = await fetch("https://random.dog/woof.json");
        let Json: Inptut = await res.json();
        console.log(Json.url);
        return Json.url;
    }
    async function click() {
        event.preventDefault();
        let pic = document.getElementById('dogImage') as HTMLImageElement;
        pic.src   = await getAPI();
    }
</script>
<main>
    <body>
    <div class="grid-container3">
        <div class="item1">
            psst, want some dog pictures? click on button👽
        </div>
        <div class="item2">
            <button id="generate1" on:click = {click}>
                click
            </button>
        </div>

        <div class="item3">

            <img id = "dogImage" src="">
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
    .item1 {
        align-items: center;
        grid-area: header;
        text-align: center;

    }

    .item2 {
        align-items: center;
        grid-area: main;
        text-align: center;

    }
    .item3{
        align-items: center;
        grid-area: photo;
        text-align: center;

    }

    .grid-container3 {
        background-repeat: repeat;
        display: grid;
        align-items: center;
        grid-template-areas:
                    'header '
                    'main '
                    'photo ';

    }

</style>