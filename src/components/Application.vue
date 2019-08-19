<template>
  <div>
    <div>
      <h1>Send Application</h1>
    </div>
    <hr />
    <div>
      <form action>
        <fieldset>
          <legend>Application Form</legend>
          <div id="field-wrapper">
            <div>
              <label>Sending to</label>
              <label>Name</label>
              <label>Email</label>
            </div>
            <div>
              <input v-model.lazy="URL" type="text" name="URL" :placeholder="URL" />
              <input v-model.lazy="name" type="text" name="name" id />
              <input v-model.lazy="email" type="text" name="email" id />
            </div>
          </div>
          <button>Submit</button>
        </fieldset>
      </form>
      <button @click="Apply">Show Applies</button>
    </div>
    <hr />
    <div>
      <h1>Applied Form</h1>
      <p>{{URL}}</p>
      <p>{{getToken}}</p>
      <p>{{name}}</p>
      <p>{{email}}</p>
    </div>
    <hr />
    <div>
      <h1>Response</h1>
      <p></p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import URL from "../constants/Url";
import { constants } from "crypto";
export default {
  data() {
    return {
      URL,
      name: "",
      email: ""
    };
  },
  computed: {
    handleResponse: res => {
      return res.data;
    },
    handleError: err => {
      console.log(err);
    },

    getToken: async function(URL) {
      // two ways to handle promises you got to play them really well here
      let token1 = new Promise(this.handleResponse, this.handleError);
      console.log(token1);
      let token = axios.get("https://interns.bcgdvsydney.com/api/v1/key");
      //   let token = axios.get(`${URL}/api/v1/key`);
      let result = await token.then(res => {
        // console.log(res.data.key);
        return res.data.key;
      });
      let final = await result;
      //   console.log(final)
      return final;
      //   you need to resolve this maybe a new function??
    }
  },
  methods: {
    Apply: function() {
      console.log(this.getToken);
    }
  }
};
</script>

<style >
#field-wrapper {
  display: flex;
  justify-content: space-around;
}

#field-wrapper div {
  display: flex;
  flex-direction: column;
}
</style>