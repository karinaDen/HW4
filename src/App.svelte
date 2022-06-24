<style>
	* {
		margin: 0;
		padding: 0;
	}

	h1, h2 {
		margin: 0;
	}

	.item1 {
		grid-area: header;
	}

	.item2 {
		grid-area: main;
	}

	.grid-container1 {
		background-repeat: repeat;
		display: grid;
		grid-template-areas:
                    'header header '
                    'main main';

	}
	.grid-container2 {

		display: grid;
		grid-template-areas:
                    'header header'
                    'photo main ';
	}

	body {
		font-family: 'Inika', serif;
		position: relative;

		width: 100%;
		top: 74px;

		background: #FFECEB;
	}

	.header {
		width: 100%;
		position: absolute;
		height: 70px;
		background: #FFECEB;
		border-bottom: 4px solid #FFFFFF;
		align-items: center;
	}

	.header_inner {
		display: flex;
		height: 70px;
		justify-content: space-between;
		align-items: center;
		top: 5%;
	}

	.header_Home {
		font-family: 'Inika';
		font-style: normal;
		font-weight: 400;
		font-size: 20px;
		line-height: 47px;
		display: flex;
		align-items: center;
		text-align: center;
		text-decoration-line: none;
		text-transform: uppercase;

		color: #876D6D;
	}

	.header_Home:hover {
		color: #594646;
		text-decoration-line: underline;
	}

	.nav {
		text-transform: uppercase;

	}

	.nav_link:hover {
		color: #594646;
		text-decoration-line: underline;

	}

	.nav_link {
		display: inline-block;
		vertical-align: top;
		margin: 26px;
		color: #876D6D;
		text-decoration: none;
		font-family: 'Inika';
		font-style: normal;
		font-weight: 400;
		font-size: 20px;
		line-height: 47px;

		transition: color .2s linear;
	}


	/* end of header block */

	.intro {
		height: calc(1000px - 270px);
		width: 100%;

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


	.intro-title1 {
		position: absolute;
		top: 299px;
		left: 25%;

		font-family: 'Inika';
		font-style: normal;
		font-weight: 400;
		font-size: 64px;
		line-height: 83px;
		display: flex;
		align-items: center;
		text-align: center;

		color: #000000;

	}

	.intro-title2 {
		position: absolute;
		left: 40%;
		top: 400px;

		font-style: normal;
		font-weight: 400;
		font-size: 24px;
		line-height: 31px;
		display: flex;
		align-items: center;
		text-align: center;

		color: #000000;

	}
</style>
<script>
	import {getContext, setContext} from 'svelte'
	import {createUrlStore} from './url'
	import Project from './project.svelte'


	let src1 = '../public/img/myPhoto.jpg'
	let src2 = '../public/img/Briefly_about_me.svg'

	export let ssrUrl = ''

	setContext('APP', {url: createUrlStore(ssrUrl)})

	const {url} = getContext('APP')

	function handleLinkClick(e) {
		e.preventDefault()
		const href = e.target.href
		history.pushState(href, '', href)
	}
</script>

<head>
	<link rel="preconnect" href="https://fonts.googleapis.com">
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
	<link href="https://fonts.googleapis.com/css2?family=Inika&display=swap" rel="stylesheet">
</head>
<header>
	<div class="header">
		<div class="header_inner">
			<div class="item1">
				<div class="header_logo">
					<a class="header_Home" href="/" on:click={handleLinkClick}>Home</a>
				</div>
			</div>
			<div class="item1">
				<nav class="nav">
					<a class="nav_link" href="/about" on:click={handleLinkClick}>About</a>
					<a class="nav_link" href="/projects" on:click={handleLinkClick}>Projects</a>
				</nav>
			</div>
		</div>
	</div>
</header>

{#if $url.pathname === '/'}
	<body>
	<div class="grid-container1">
		<main>
			<div class="item2">
				<div class="intro">
					<h1 class="intro-title1">Hi! I am Karina Denisova</h1>
					<h2 class="intro-title2"> Beginer Front-End Developer</h2>
				</div>
			</div>
		</main>
	</div>
	</body>
{:else if $url.pathname === '/about'}
	<body>
	<div class="grid-container2">
		<main>
			<div class="intro">
				<div class="item2">
					<img class="picture" {src1} alt="">
				</div>
				<div class="item3">
					<img class="text" {src2}>
				</div>
			</div>
		</main>
	</div>

	</body>
{:else}
	<Project/>
{/if}