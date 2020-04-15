<template>
  <div class="server-details">
    <div class="servers">
      <h2>Servers</h2>
      <template v-for="server in servers">
        <Server
          :serverName="server.name"
          :serverID="server.id"
          :serverStatus="server.status"
          :key="server.id"
          :selectServer="selectServer"
        ></Server>
      </template>
    </div>
    <div class="details">
      <h2>Status</h2>
      <!-- <h4>Add new Server</h4>
      <div class="input-field">
        <input
          type="text"
          @input="onChange"
          :value="newServer"
          @keyup.enter="add"
        />
        <button @click="add">Add</button> -->
      <ServerStatus :server="selectedServer" :fixServer="fixServer" />
    </div>
  </div>
</template>

<script>
import Server from './Server';
import ServerStatus from './ServerStatus';
import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'ServerDetails',
  components: {
    Server,
    ServerStatus,
  },
  data() {
    return {
      newServer: '',
      selectedServer: {},
      servers: [
        {
          id: uuidv4(),
          name: 'Istanbul',
          status: 'Normal',
          info:
            'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Consequatur velit reprehenderit quam magnam praesentium fugiat facilis, tempore temporibus officiis cum.',
        },
        {
          id: uuidv4(),
          name: 'Prague',
          status: 'Critical',
          info:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid, animi! Dolor quos explicabo eum dicta alias blanditiis, adipisci eos veritatis dolorem architecto odio, quasi vitae excepturi esse, porro deserunt atque?',
        },
        {
          id: uuidv4(),
          name: 'Berlin',
          status: 'Unknown',
          info:
            'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Vero magni quibusdam cumque cum. Eligendi at nisi sunt vel itaque accusantium sit sint odit enim!',
        },
        {
          id: uuidv4(),
          name: 'New York',
          status: 'Normal',
          info:
            'Lorem, ipsum dolor sit amet consectetur adipisicing elit. Laboriosam necessitatibus vero in?',
        },
        {
          id: uuidv4(),
          name: 'Paris',
          status: 'Unknown',
          info:
            'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Sequi eum magnam iste aperiam iure nisi voluptate est omnis?',
        },
        {
          id: uuidv4(),
          name: 'Londra',
          status: 'Normal',
          info:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Veritatis consectetur quisquam repellat velit voluptatem laboriosam omnis, iste doloremque. Voluptatibus ad odit laboriosam non, laborum alias expedita corrupti qui porro excepturi vel laudantium!',
        },
      ],
    };
  },
  methods: {
    onChange(evt) {
      this.newServer = evt.target.value;
    },
    add() {
      this.servers.push({
        name: this.newServer,
        id: 0,
      });
      this.newServer = '';
    },
    selectServer(id) {
      this.servers.map((server) => {
        if (server.id === id) {
          this.selectedServer = server;
        }
      });
    },
    fixServer(id) {
      this.servers.map((server) => {
        if (server.id === id) {
          server.status = 'Normal';
        }
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.server-details {
  display: flex;
  justify-content: space-between;
  padding: 1rem 0;
  .servers {
    box-sizing: border-box;
    width: 47.5%;
  }
  // .details {
  //   display: flex;
  //   flex-direction: column;
  //   align-items: center;
  //   box-sizing: border-box;
  //   width: 47.5%;
  //   .input-field {
  //     display: flex;
  //     input {
  //       box-sizing: border-box;
  //       font-size: 1.4rem;
  //       padding: 5px;
  //       border: 1px solid #d4d4d4;
  //       border-right: 0;
  //       border-radius: 5px 0 0 5px;
  //     }
  //     button {
  //       box-sizing: border-box;
  //       border: 1px solid #d4d4d4;
  //       border-left: 0;
  //       border-radius: 0 5px 5px 0;
  //       background-color: #03a2ec;
  //       color: #ffffff;
  //       width: 20%;
  //     }
  //   }
  // }
  .details {
    box-sizing: border-box;
    width: 47.5%;
  }
}
</style>
