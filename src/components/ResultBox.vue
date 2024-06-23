<template>
  <div>

    <!-- text between -->
    <p
      v-text="'And the result...'" />

    <!-- mixture effect -->
    <flask-item
      :size="15"
      :color="mixtureEffectFill"
      :amount="100" 
      :buttonsVisible="false"
      :style="margin"/>

    <!-- refresh btn -->
    <button-item
      @click="$emit('refresh')"
      :size="4"
      :movement="-0.5"
      :font-size="1.5"
      icon="sync" />

  </div>
</template>

<script>
import FlaskItem from './shared/FlaskItem'
import ButtonItem from './shared/ButtonItem';

export default {
  name: 'ResultsBox',
  props: {
    mixtures: {
      type: Array,
      required: true
    }
  },
  computed: {
    mixtureEffectFill () {
      const [redCol, greenCol, blueCol] = this.mixtures.map(item => Math.floor(item.amount * 2.5))
      const toHex = (value) => value.toString(16).padStart(2, '0');
      const hexColor = `#${toHex(redCol)}${toHex(greenCol)}${toHex(blueCol)}`;
      return hexColor;
    },
    margin() {
      return {margin: '3rem auto' }
    }
  },
  components: {
    FlaskItem, ButtonItem
  }
}
</script>
