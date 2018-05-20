<template>
	<div class='test'>

		<input type="text" v-model='title'></br>
		<!-- render html that's in the script by using v-html -->
		<h1>{{title}}</h1>
		<!-- render text through handlebars -->
		<p v-if='showName'>{{user.firstName}}</p>
		<p v-else='showName'>Nobody</p>
		<!-- render text through declaring text -->
		<p v-text='user.firstName'></p>
		<p>{{user.lastName}}</p>

		<ul>
			<li v-for='item in items'>{{item.title}}</li>
		</ul>
		<button v-on:click='greet("Hello World")'>Say greeting</button>
		<br />	
		<input type="text" v-on:keyup='pressKey' v-on:keyup.enter='enterhit'>
		<hr />


		<label for="">First Name</label>
		<input type="text" v-model='user.firstName'>
		<br />
		<label for="">Last Name</label>
		<input type="text" v-model='user.lastName'>

		<h3>{{fullName}}</h3>
		<!-- since this is a property, as defined below, you can pass it in the App.vue file -->
		<h2>{{msg}}</h2>
	</div>
</template>

<script>
	export default {
		name: 'Test',
		props: {
			msg: {
				type: String,
				default: 'Foobar'
			}
		},
		data() {
			return {
				title: 'Hello World',
				user: {
					firstName: 'John',
					lastName: 'Doe'
				},
				showName: false,
				items: [
					{title: 'Item One'},
					{title: 'Item Two'},
					{title: 'Item Three'}
				]
			}
		},
		methods: {
			greet: function(greeting){
				alert(greeting);
			},
			pressKey: function(e){
				console.log(e.target.value);
			},
			enterhit: function(){
				console.log('You hit enter');
			}
		},
		computed: {
			fullName: function(){
				return this.user.firstName + ' ' + this.user.lastName;
			}
		}
	}

</script>

<style scoped>

</style>