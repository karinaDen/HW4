<script>
    let src1 = '../img/myPhoto.jpg'
    let src2 = '../img/Briefly_about_me.svg'
</script>
<main>
    <body>
    <div class="grid-container2">

            <div class="intro">
                <div class="item3">
                    <img class="picture" src={src1} alt="">
                </div>
                <div class="item2">
                    <img class="text" src={src2}>
                </div>
            </div>
    </div>
    </body>
</main>
<style>

    .item2 {
        grid-area: main;
    }
    .item3 {
        grid-area: photo;
    }

    .grid-container2 {
        margin: 0;
        padding: 0;
        display: grid;
        grid-template-areas:
                    'header header'
                    'photo main ';
    }

    body {
        font-family: 'Inika', serif;
        position: relative;
        height: calc(1000px - 260px);

        width: 100%;
        top: 74px;

        background: #FFECEB;
        margin: 0;
        padding: 0;
    }
    .picture {
        position: absolute;
        width: 450px;
        height: 641px;
        left: 82px;
        top: 11%;
        border-radius: 216.5px;
    }

    .text {
        position: absolute;
        width: 711px;
        height: 600px;
        left: 661px;
        top: 10%;


        color: #000000;
    }

</style>