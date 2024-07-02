<template>
  <div class="page">
    <page-title>Home</page-title>
    <Message class="animate__animated animate__shakeY animate__delay-2s" severity="warn">Warning! This app is still in development...</Message>
  </div>
</template>

<script>
import Message from 'primevue/message';
import PageTitle from '../components/shared/PageTitle';

export default {
  name: 'HomePage', 
  components: {
    Message, PageTitle
  }
}
</script>