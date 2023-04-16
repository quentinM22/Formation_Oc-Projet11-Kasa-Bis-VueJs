<script>
import { RouterLink } from 'vue-router';

export default {
  components: {
    RouterLink,
  },
  data() {
    return {
      logo: 'src/assets/images/Logo.png',
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
	width: 100%;
	display: flex;
	align-items: center;
	justify-content: space-between;
	margin: 50px 0 50px;
}
header > img {
	width: 25%;
}
header > nav {
	width: 75%;
}
header > nav > ul {
	display: flex;
	align-items: center;
	justify-content: flex-end;
	padding: 0;
}
header > nav > ul > li {
	list-style: none;
	padding: 0 0 0 15px;
	text-align: center;
}
header > nav > ul > li > a {
	color: #ff6060;
	text-decoration: none;
	padding-bottom: 2px;
}
header > nav > ul > li > a:hover {
	border-bottom: solid 1px #ff6060;
}
@media screen and (max-width: 767px) {
	header {
		margin: 20px 0 20px;
	}
	header > nav > ul > li > a {
		font-size: 12px;
	}
}
</style>