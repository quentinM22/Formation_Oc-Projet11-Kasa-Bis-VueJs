<script>
import logo from '@/assets/images/Logo-footer.png'
export default {
	data() {
		return {
			Logo: logo
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
	width: 100%;
	padding: 70px 0 29px;
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

@media screen and (max-width: 767px) {
	footer {
		padding: 60px 0 29px;
	}

	footer>h2 {
		font-size: 12px;
	}
}
</style>