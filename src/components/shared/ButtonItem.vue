<template>
  <button
    :style="btnStyles"
    class="btn">
    <!-- icon -->
		<span
  		v-if="icon"
  		:class="`${iconSet} ${icon}`"  style="font-size: inherit;"/>

		<!-- text -->
		<span
  		v-if="text"
  		v-text="text" />

  </button>
</template>
  
<script>
export default {
  name: 'ButtonItem',
	props: {
  	icon: {
    	type: String,
    	required: true
  	},
		iconSet: {
  		type: String,
  		default: 'pi'
		},
		text: {
  		type: String
		},
  	size: {
    	type: Number,
    	default: 2
  	},
  	fontSize: {
    	type: Number,
    	default: 1
  	},
  	movement: {
    	type: Number,
    	default: 0.5
  	}
	}, 
	computed: {
  	btnStyles () {
    	return {
      	width: `${this.size}rem`,
      	height: `${this.size}rem`,
      	fontSize: `${this.fontSize}rem`,
		'--movement': `${this.movement}rem`
    	}
  	}
	}
}
</script>
  
<style lang="scss" scoped>
.btn {
  background-color: $background-color;
  background-image: linear-gradient(0deg, #9a9a9a 0%, #e8fdff 100%);
  border: none;
  border-radius: 50%;
  cursor: pointer;
  box-shadow: $box-shadow;
  transition: .3s;
  outline: none;
  font-size: 1.5rem;
  color: $color;

	&:hover {
  margin-top: var(--movement);
}
}
</style>