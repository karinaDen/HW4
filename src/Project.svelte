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
    <div class="flexbox-container">
        <div class="flexbox1">
            psst, want some dog pictures? click on button👽
        </div>
        <div class="flexbox2">
            <button id="generate1" on:click = {click}>
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