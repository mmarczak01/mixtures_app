<template>
  <div class="page">
    <page-title>Color</page-title>
		<Message v-if="showAlert" severity="error">This color is invalid! It's not RGB format...</Message>
		<div v-if="!showAlert">
			<p>You have picked a great color!</p>

			<flask-item
				:size="15"
      	:color="color"
      	:amount="100" 
      	:buttonsVisible="false"
      	:style="margin"/>

			<i class="pi pi-share-alt" style="font-size: 1.5rem; margin: 10px; color: #637892;"></i>
			<InputText class="input" type="text" v-model="fullUrl" />
		</div>
  </div>
</template>
  
<script>
import PageTitle from '../components/shared/PageTitle';
import FlaskItem from '../components/shared/FlaskItem'
import InputText from 'primevue/inputtext';
import Message from 'primevue/message';

export default {
  name: 'ColorPage',
	components: { PageTitle, FlaskItem, InputText, Message},
	data: () => ({
		showAlert: false
	}),
	computed: {
		margin () {
      return {margin: '3rem auto' }
    },
		color () {
			const red = parseInt(this.$route.params.red);
      const green = parseInt(this.$route.params.green);
      const blue = parseInt(this.$route.params.blue);
			const toHex = (value) => value.toString(16).padStart(2, '0');
      const hexColor = `#${toHex(red)}${toHex(green)}${toHex(blue)}`;
      return hexColor;
		},
		fullUrl () {
			return 'http://localhost:8080' + this.$route.path;
		}
	},
	methods: {
		isInvalidRGB (red, green, blue) {
			return (
        isNaN(red) || isNaN(green) || isNaN(blue) ||
        red < 0 || red > 255 || 
        green < 0 || green > 255 || 
        blue < 0 || blue > 255
      );
		}
	},
	created() {
		const { red, green, blue } = this.$route.params;
		if (!red || !green || !blue ||
    	isNaN(parseInt(red)) || isNaN(parseInt(green)) || isNaN(parseInt(blue))) {
      this.$router.push('/');
		}

		if (this.isInvalidRGB(red, green, blue)) {
      this.showAlert = true;
    }
	}
}
</script>
<style lang="scss">
.input {
  width: 350px;
	background-color: #f2f8ff;
	text-align: center;
}

</style>