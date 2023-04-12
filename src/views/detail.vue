<template>
  <div v-if="this.selectedUser">
    <span data-v-c43a1b98="">
      <avatar
        :first_name="this.selectedUser.first_name"
        :last_name="this.selectedUser.last_name"
        :profile="this.selectedUser.profile_pic"
      ></avatar>
      
    </span> 
    <span>{{ this.selectedUser.first_name }} {{ this.selectedUser.last_name }}</span>
    <p>Username: {{ this.selectedUser.username }}</p>
    <p>Address: {{ this.selectedUser.street_address }}
      {{this.selectedUser.city}}
    </p>
    <p>{{this.selectedUser.bio}}</p>
    <div class="footer">
    <button type="button" class="btn btn-danger" @click="removeEmployee(this.selectedUser.id)">Delete</button>
    <button type="button" class="btn btn-primary">Edit</button>
    </div>
  </div>
 
</template>

<script>
import avatar from '../common/avatar.vue';
export default {
  name: "detail",
  props: {
   selectedUser:{
    default:[]
   }
  },
  components: {avatar
  },

  methods: {
    parseMarkdown(content) {
      return marked(content);
    },
    removeEmployee(id){
     // this.$emit("deleteList", id);
    }
  }
};
</script>
