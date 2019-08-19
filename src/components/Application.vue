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
              <input v-bind="URL" type="text" name="URL" :placeholder="URL" />
              <input v-bind="applyName" type="text" name="name" id />
              <input v-bind="applyEmail" type="text" name="email" id />
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
      <p>{{applyName}}</p>
      <p>{{applyEmail}}</p>
    </div>
    <hr />
    <div>
      <h1>Response</h1>
      <p>
      </p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import URL from "../constants/Url";
export default {
  data() {
    return {
      URL,
      applyName: "",
      applyEmail: ""
    };
  },
  computed: {
    getToken: function(URL) {
      let token = axios.get(url);
      console.log(token);
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