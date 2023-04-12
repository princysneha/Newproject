<template>
  <div>
    <div v-if="this.selectedUser && hideDelete">
      <span data-v-c43a1b98="">
        <avatar
          :first_name="this.selectedUser.first_name"
          :last_name="this.selectedUser.last_name"
          :profile="this.selectedUser.profile_pic"
        ></avatar>
      </span>
      <span
        >{{ this.selectedUser.first_name }}
        {{ this.selectedUser.last_name }}</span
      >
      <p>Username: {{ this.selectedUser.username }}</p>
      <p>
        Address: {{ this.selectedUser.street_address }}
        {{ this.selectedUser.city }}
      </p>
      <p>{{ this.selectedUser.bio }}</p>
      <div class="footer" v-if="hideDelete">
        <button type="button" class="btn btn-danger" @click="removeEmployee">
          Delete
        </button>
        <button type="button" class="btn btn-primary" @click="updateEmployee">
          Edit
        </button>
      </div>
    </div>
    <div>
      <edit v-if="showForm" :user="selectedUser"></edit>
    </div>
  </div>
</template>

<script>
import avatar from "../common/avatar.vue";
import edit from "./edit.vue";
export default {
  name: "detail",
  props: {
    selectedUser: {
      default: []
    }
  },
  components: { avatar, edit },
  data() {
    return {
      showForm: false,

      hideDelete: true
    };
  },
  methods: {
    removeEmployee() {
      this.$emit("clicked", this.selectedUser.id);
    },
    updateEmployee() {
      console.log("emittttt", this.selectedUser.id);
      this.showForm = true;
      this.hideDelete = false;
    }
  }
};
</script>
