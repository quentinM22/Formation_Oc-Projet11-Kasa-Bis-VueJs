<script>
import { RouterLink } from 'vue-router';

export default {
	components: {
		RouterLink,
	},
	data() {
		return {
			logo: '/src/assets/images/Logo.png',
		};
	},
};
</script>
<template>
	<header>
		<RouterLink to="/">
			<img :src='logo' alt="Kasa Logo" />
		</RouterLink>
		<nav>
			<ul>
				<li>
					<RouterLink to="/">Accueil</RouterLink>
				</li>
				<li>
					<RouterLink to="/about">A propos</RouterLink>
				</li>
			</ul>
		</nav>
	</header>
</template>

<style>
header {
	width: calc(100% - 100px);
	display: flex;
	align-items: center;
	justify-content: space-between;
	padding: 50px 50px 50px;
}

header>a>img {
	width: 200px;
}

header>nav {
	width: 75%;
}

header>nav>ul {
	display: flex;
	align-items: center;
	justify-content: flex-end;
	flex-flow: row wrap;
	padding: 0;
}

header>nav>ul>li {
	list-style: none;
	padding: 0 0 0 15px;
	text-align: center;
}

header>nav>ul>li>a {
	color: var(--primary);
	text-decoration: none;
	padding-bottom: 2px;
}

header>nav>ul>li>a:hover,
header>nav>ul>li>.active {
	border-bottom: solid 1px var(--primary);
}

@media screen and (max-width: 767px) {
	header {
		width: calc(100% - 40px);
		padding: 20px 20px 20px;
	}

	header>a>img {
		width: 125px;
	}

	header>nav>ul>li>a {
		font-size: 12px;
	}
}</style>