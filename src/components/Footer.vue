<script>
export default {
	data() {
		return {
			Logo: '/src/assets/images/Logo-footer.png'
		}
	}
}
</script>
<template>
	<footer>
		<img :src='Logo' alt="Logo" />
		<h2>© 2020 Kasa. All rights reserved</h2>
	</footer>
</template>
<style>
footer {
	padding: 50px 0 29px;
	margin: 25px 0 0;
	display: flex;
	justify-content: center;
	align-items: center;
	flex-flow: column nowrap;
	background-color: black;
}

footer>img {
	max-width: 122px;
}

footer>h2 {
	color: white;
	font-weight: 500;
	font-size: 24px;
}
</style>