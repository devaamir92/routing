<template>
	<div>
		<b-navbar toggleable="lg" type="dark" variant="dark">
			<b-navbar-brand><router-link class="nav-link" to="/">Home</router-link></b-navbar-brand>
			<b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
			<b-collapse id="nav-collapse" is-nav>
				<b-navbar-nav>
					<b-nav-item>
					<router-link class="nav-link" to="/about">About</router-link></b-nav-item>
					<b-nav-item><router-link class="nav-link" to="/details">Details</router-link></b-nav-item>
					<b-nav-item><router-link class="nav-link" to="/contact">contact</router-link></b-nav-item>
					<b-nav-item><router-link class="nav-link" to="/login">Login</router-link></b-nav-item>

				</b-navbar-nav>
			</b-collapse>
		</b-navbar>
	</div>
</template>
<style>
	.navbar {
    padding: 0.0rem 1rem;
}
</style>