<script>
export default {
	props: {
		title: String,
		description: String,
		list: Array
	},
	data() {
		return {
			isOpen: false,
		}
	},
	methods: {
		toggle() {
			this.isOpen = !this.isOpen;
		}
	}
}
</script>
<template>
	<div class="cmp-AboutCard-btn" v-on:click="toggle()">
		{{ title }}
		<i class="fa-solid" :class="{ 'fa-chevron-up': isOpen, 'fa-chevron-down': !isOpen }"></i>
	</div>

	<div v-if="isOpen" class="cmp-AboutCard-description">
		<p v-if="description != null">{{ description }}</p>
		<ul v-else>
			<li v-for="item, index in list" :key="index">{{ item }}</li>
		</ul>
	</div>
</template>
<style>
.cmp-about-card-container {
	margin: 0 50px 0;
}

.cmp-AboutCard-btn {
	position: relative;
	display: flex;
	justify-content: space-between;
	background-color: var(--primary);
	color: white;
	border-radius: 5px;
	padding: 10px;
	margin: 20px 0 0;
	z-index: 1;
	cursor: pointer;
}

.cmp-AboutCard-description {
	position: relative;
	background-color: #f6f6f6;
	border-bottom-left-radius: 5px;
	border-bottom-right-radius: 5px;
	padding: 40px 15px 20px;
	margin-top: -10px;
	font-weight: 400;
	z-index: 0;
}

.cmp-AboutCard-description>li {
	list-style: none;
	padding: 0 5px 5px;
}

@media screen and (max-width: 767px) {
	.cmp-about-card-container {
		margin: 0;
	}

	.cmp-AboutCard-btn {
		font-size: 13px;
	}

	.cmp-AboutCard-description {
		font-size: 12px;
	}
}</style>