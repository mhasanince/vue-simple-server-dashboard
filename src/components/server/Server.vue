<template>
  <div :class="[status, 'server']" @click="handleClick">
    <p>
      <b>{{ serverName }}</b> <span>#{{ serverID }}</span>
    </p>
  </div>
</template>

<script>
export default {
  name: 'Server',
  props: {
    serverName: String,
    serverID: String,
    serverStatus: String,
    selectServer: Function,
  },
  methods: {
    handleClick() {
      this.selectServer(this.serverID);
    },
  },
  computed: {
    status() {
      return this.serverStatus.toLowerCase();
    },
  },
};
</script>

<style lang="scss" scoped>
.server {
  padding-left: 1rem;
  box-sizing: border-box;
  border: 1px solid #ffffff;
  border-radius: 5px;
  p {
    span {
      float: right;
      margin-right: 20px;
      font-weight: 100;
      font-size: 0.8rem;
    }
  }
}
.normal {
  background-color: #2f91d3;
  color: #ffffff;
}
.unknown {
  background-color: #788586;
  color: #ffffff;
}
.critical {
  background-color: #de4536;
  color: #ffffff;
}
</style>
