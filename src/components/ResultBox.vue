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
      icon="pi-refresh" />

    <!-- open modal btn -->
    <button-item
      @click="showModal"
      :size="4"
      :movement="-0.5"
      :font-size="1.5"
      icon="pi-question"
      style="margin-left: 10px;" />

    <modal-item
      v-if="modalVisible"
      @cancel="hideModal">

      <template v-slot:header>
        About the app
      </template>

      <template v-slot:body>
        Mix three colors to create the perfect one!
      </template>

      <template v-slot:footer>
	      <button-item icon="pi-thumbs-up" />
      </template>

    </modal-item>

  </div>
</template>

<script>
import FlaskItem from './shared/FlaskItem'
import ButtonItem from './shared/ButtonItem';
import ModalItem from './shared/ModalItem.vue';
import modalMixin from '../mixins/ModalMixin';

export default {
  name: 'ResultsBox',
  mixins: [modalMixin],
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
    FlaskItem, ButtonItem, ModalItem
  }
}
</script>
