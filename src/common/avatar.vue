<template>
   
        <span 
        v-tooltip="{
        content:getFullName(),
        trigger:'hover click'
        }"
        class="inline-block relative">
        <span v-if="profile==='' || profile === null">
            <span :class="['block','m-1',size]">
            <span :class="initialsClass">
            {{ this.getInitials() }}
            </span>
            </span>
        </span>
        <span v-else>
            <img v-bind:src="profile"
            :class="['rounded-circle','m-1','object-cover','shadow-lg',size]" alt="">
        </span>
    </span>
        
</template>

<script>
export default {
    props: {
        "first_name":{
            type:String,
            default:""
        }, 
        "last_name":{
            type:String,
            default:""
        }, 
        "text":{
            type:String,
            default:""
        },
        "profile":{
            type:String,
            default:""
        },
        "size":{
            type:String,
            default:"avatar-xs"
        },
        "initialsClass":{
            type:String,
            default:"font-bold avatar-title rounded-circle text-primary bg-white shadow-lg"
        },
        "business_name":{
            type:String,
            default:""
        }, 
        "type":{
          // type:Boolean,
            default:1  
        }
    },
    name: "avatar",
    methods: {
        getInitials() {
            if(this.type==3){
                var words = this.text.split(" ").shift();
                var last = this.text.split(" ").pop();
                return ((words.trim().charAt(0)).toUpperCase()) + ((last.charAt(0)).toUpperCase());
            }
            if(this.first_name===null&&this.last_name===null){
                return "";
            }
            return ((this.first_name.trim().charAt(0)).toUpperCase()) + ((this.last_name.trim().charAt(0)).toUpperCase());
        },
        getFullName() {
             let fullName = this.first_name + ' ' + this.last_name;
            // if(this.business_name==''){
            //     return fullName.trim();
            // }
            
            // If the user is accosiate then no tooltip show and tooltip showing with b2B partner and Team as well
            if(this.type==2){
             return this.business_name;
            }
            return fullName;
        }
    }

}
</script>

<style>
    .avatar-xs {
    height: 1.5rem;
    width: 1.5rem;
    line-height: 1.5rem;
    font-size: .65rem;
    }
    .shadow-lg {
    box-shadow: 0 10px 15px -3px rgba(0,0,0,.1),0 4px 6px -2px rgba(0,0,0,.05)!important;
    }
    .object-cover {
    -o-object-fit: cover!important;
    object-fit: cover!important;
    }
    .rounded-circle {
    border-radius: 50%!important;
    }
    img {
    vertical-align: middle;
    border-style: none;
    }
    
</style>
