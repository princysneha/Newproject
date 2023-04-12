<template>
  <div>
    <span>
      <avatar
        :first_name="this.user.first_name"
        :last_name="this.user.last_name"
        :profile="this.user.profile_pic"
      ></avatar>
    </span>
    <div class="row">
      <form>
        <div class="form-group">
          <label>First Name:</label>

          <input type="text" class="form-control" v-model="first_name" />
        </div>
        <div class="form-group">
          <label>Last Name:</label>

          <input type="text" class="form-control" v-model="last_name" />
        </div>
        <div class="form-group">
          <label>Email:</label>
          <input type="email" class="form-control" v-model="email" />
        </div>
        <button @click.prevent="save">Save</button>
      </form>
    </div>
  </div>
</template>
<script>
import avatar from "../common/avatar.vue";
export default {
  name: "edit",
  components: {
    avatar
  },
  props: {
    user: {
      default: []
    }
  },
  data() {
    return {
      first_name: "",
      last_name: "",
      email: ""
    };
  },
  methods: {
    save() {
      console.log("formm", this.first_name);
    }
  }
};
</script>
