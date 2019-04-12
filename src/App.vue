<template>
	<div id="app" ref="appToucher">
		<div class="box" ref="box">
			<h3>Touch my TA-LA-LA</h3>
		</div>

		<h3 ref="statusdiv">{{ statusDiv }}</h3>
	</div>
</template>

<script>

	export default {
		data() {
			return {
				counter: 0,
				statusDiv: ''
			}
		},
		mounted() {
			this.touchMyTaLaLa()
		},
		methods: {
			touchMyTaLaLa() {
				// body.addEventListener('touchstart', (e) => {
				// 	this.counter++
				// 	console.log(e.changedTouches[0].pageX);
				// },)
				let box = this.$refs.box
				let statusdiv = this.$refs.statusdiv
				let startx = 0
				let dist = 0

				box.addEventListener('touchstart', (e) => {
					let touchobj = e.changedTouches[0]
					startx = parseInt(touchobj.clientX)
					this.statusDiv = `Status: touchSTART ClientX: ${startx}px`
					e.preventDefault()
				}, false)

				box.addEventListener('touchmove', (e) => {
					let touchobj = e.changedTouches[0]
					let dist = parseInt(touchobj.clientX) - startx
					this.statusDiv = `Status: touchMOVE Horizontal distance traveled: ${dist}px`
					e.preventDefault()
				}, false)

				box.addEventListener('touchend', (e) => {
					let touchobj = e.changedTouches[0]
					this.statusDiv = `Status: touchEND Resting x coordinate: ${touchobj}px`
					e.preventDefault()
				}, false)
			}
		}
	}
</script>

<style>
	* {
		padding : 0;
		margin  : 0;
	}

	#app {
		height : 100vh;
		width  : 100vw;
	}

	.box {
		width      : 200px;
		height     : 300px;
		background : plum;
	}


</style>
