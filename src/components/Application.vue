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
    getToken: async function(URL) {
      let token = await axios.get(`${URL}/api/v1/key`).then(res => {
        console.log(res);
        return res;
      });
      return token;
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