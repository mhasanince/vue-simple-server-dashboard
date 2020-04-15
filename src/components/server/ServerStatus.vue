<template>
  <div class="server-status">
    <template v-if="Object.entries(server).length === 0">
      <h4>Select any server.</h4>
    </template>
    <template v-else>
      <p>
        <b>Name: </b>
        {{ server.name }}
      </p>
      <p>
        <b>Status: </b>
        <span :class="status">{{ server.status }}</span>
      </p>
      <p>
        <b>Info: </b>
        {{ server.info }}
      </p>
      <button v-if="show" @click="handleClick">
        Fix Server
      </button>
    </template>
  </div>
</template>

<script>
export default {
  name: 'ServerStatus',
  props: {
    server: {
      type: Object,
    },
    fixServer: Function,
  },
  methods: {
    handleClick() {
      this.fixServer(this.server.id);
    },
  },
  computed: {
    status() {
      return this.server.status.toLowerCase();
    },
    show() {
      return this.server.status.toLowerCase() !== 'normal';
    },
  },
};
</script>

<style lang="scss" scoped>
.server-status {
  p span {
    padding: 1px 5px;
  }
  span.normal {
    background-color: #2f91d3;
    color: #ffffff;
  }
  span.unknown {
    background-color: #788586;
    color: #ffffff;
  }
  span.critical {
    background-color: #de4536;
    color: #ffffff;
  }
}
</style>
