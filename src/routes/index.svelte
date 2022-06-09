<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	const bgCall = async () => {
		var response = await fetch('https://frame.kitzu.me/rdm/');
		var result = await response.json();
		return result;
	}

	const db = async () => {
		var response = await fetch('https://blogbe.suphakit.net/content');
		var result = await response.json();
		return result;
	}
	
	let setBG = bgCall();
	let setDB = db();
	
</script>

<svelte:head>
	<title>Home | Dethz.Blog</title>
	<meta name="description" content="a little blog by detzz for u all :)" />
</svelte:head>

<section>
	<div class="header">
		{#await setBG}
			setting up Background...
		{:then callBG} 
			<div class="bg" style={'background: url(' + callBG.url + ');'}>
				<div class="overlay">
					<h1>
						dethz.Blog
					</h1>
					<h3>
						:D
					</h3>
				</div>
			</div>
		{/await}
	</div>

	<div class="desp">
		<h1>
			Welcome to <a href="https://blog.suphakit.net">Dethz.Blog</a>
		</h1>
		<p>
			สวัสดีครับทุกคน ยินดีต้อนรับเข้าสู่ Blog เล็กๆ แห่งนี้ ซึ่งสำหรับคนที่เคยเข้ามาก่อนแล้วอาจจะรู้สึกแปลกๆ นิดหน่อย เพราะว่าใช่ครับ นี่คือการเปลี่ยน FrameWork ครั้งยิ่งใหญ่อีกครั้ง จาก Nuxt Content 2 ไปเป็น SvelteKit + ExpressJS ครับผม เนื่องด้วยตัวผมเองรู้สึกว่าของเก่านั้นมันแทบจะไม่มีอะไรเลย และแทบจะไม่ได้ฝึกอะไรเพิ่มเลย นั้นแหละครับมันเลยกลายเป็นเหตุผลที่ผมทำเว็บนี้ขึ้นมาใหม่เลย (จริงๆ คือกลัวว่า Vercel รับขนาดไฟล์ที่กำลังจะเข้ามาใหม่ไม่ไหวมากกว่า เลยยอมทำใหม่ให้เก็บข้อมูลลงในฐานข้อมูลแทน ;-;)
		</p>
	</div>

	<div class="content">
		<h1>
			Blog Content :
		</h1>

		{#await setDB}
			Still loading :D
		{:then callDB} 
			<div class="cont-container">
				<div class="cont-card">
					<div class="img-header" style={`background: url("${callDB[0].thumbnail}");`}></div>
					<div class="card-body">
						<div class="card-title">
							{callDB[0].mHeader}
						</div>
						<div class="card-desp">
							{callDB[0].header}
						</div>
						<div class="card-footer">
							<button class="card-button">
								Read More..
							</button>
						</div>
					</div>
				</div>

				<div class="cont-card">
					<div class="img-header" style={`background: url("${callDB[1].thumbnail}");`}></div>
					<div class="card-body">
						<div class="card-title">
							{callDB[1].mHeader}
						</div>
						<div class="card-desp">
							{callDB[1].header}
						</div>
						<div class="card-footer">
							<button class="card-button">
								Read More..
							</button>
						</div>
					</div>
				</div>

				<div class="cont-card">
					<div class="img-header" style={`background: url("${callDB[2].thumbnail}");`}></div>
					<div class="card-body">
						<div class="card-title">
							{callDB[2].mHeader}
						</div>
						<div class="card-desp">
							{callDB[2].header}
						</div>
						<div class="card-footer">
							<button class="card-button">
								Read More..
							</button>
						</div>
					</div>
				</div>

				<div class="cont-card">
					<div class="img-header" style={`background: url("${callDB[3].thumbnail}");`}></div>
					<div class="card-body">
						<div class="card-title">
							{callDB[3].mHeader}
						</div>
						<div class="card-desp">
							{callDB[3].header}
						</div>
						<div class="card-footer">
							<button class="card-button">
								Read More..
							</button>
						</div>
					</div>
				</div>
			</div>
		{/await}
	</div>
</section>

<style>
	.desp {
		width: 80%;

		color: whitesmoke;

		padding-top: 1rem;
		padding-bottom: 1rem;

		margin-left: auto;
		margin-right: auto;

		text-align: center;
	}

	.desp a {
		color: whitesmoke;
		text-decoration: underline;
	}

	.desp a:hover {
		color: whitesmoke;
		opacity: .8;
		text-decoration: none;
	}

	.content {
		color: whitesmoke;
		width: 80%;

		margin-left: auto;
		margin-right: auto;

		padding-bottom: 1rem;
	}

	.cont-container {
		display: flex;
		gap: 1rem;
		justify-content: center;

		flex-wrap: wrap;
	}

	.cont-container .cont-card {
		background-color: whitesmoke;
		color: #2e2f2f;
		border-radius: 1rem;
		width: 18rem;
	}

	.cont-card .img-header {
		width: 100% !important;
		height: 8rem !important;
		border-top-left-radius: 1rem;
		border-top-right-radius: 1rem;

		background-position: center !important;
		background-repeat: no-repeat !important;
		background-size: cover !important;
	}

	.cont-card .card-body {
		width: 16rem;
		margin-left: auto;
		margin-right: auto;
	}

	.cont-card .card-body .card-title {
		width: 100%;
		text-align: center;
		font-size: larger;
		padding-top: .5rem;
		padding-bottom: .5rem;
	}

	.cont-card .card-body .card-desp {
		width: 100%;
		text-align: center;
		font-size: medium;
		color: grey;
		padding-top: .5rem;
		padding-bottom: .5rem;
	}

	.cont-card .card-body .card-footer {
		width: 100%;
		text-align: right;
		padding-top: .5rem;
		padding-bottom: .5rem;
	}

	.cont-card .card-body .card-footer .card-button {
		text-align: right;
		font-size: medium;
		background-color: coral;
		color: whitesmoke;

		border: none;
		padding: 1rem;
		border-radius: 1rem;
	}

	@media only screen and (max-width: 600px) {
		.desp {
			width: auto;

			margin-left: 1rem;
			margin-right: 1rem;
		}
	}
</style>