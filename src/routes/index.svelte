<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	const bgCall = async () => {
		var response = await fetch('https://frame.kitzu.me/rdm/');
		var result = await response.json();
		return result;
	}
	
	let setBG = bgCall();
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

	@media only screen and (max-width: 600px) {
		.desp {
			width: 100%;

			padding-left: 1rem;
			padding-right: 1rem;
		}
	}
</style>