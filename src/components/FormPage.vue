<template>

<div class="window">
        <!-- information -->
       
        <form class="information formStyle" @submit.prevent="add">

            <label for="activity-title">Picture URL</label>
            <input type="text" v-model="picture" />   

            <label for="activity-title">Activiey Name</label>
            <input type="text" v-model="title" />

            <label for="activity-introduction">Introduction:</label>
            <textarea rows="4" cols="50" v-model="introduction">...</textarea>

            <label for="activity-time">Choose a activity time:</label>
            <input type="datetime-local" v-model="time" />

            <label for="activity-location">Location:</label>
            <input type="text" v-model="location" />

            <label for="activity-register">Register:</label>
            <input type="text" v-model="register" />

            <button class="buttonStyle" >add</button>
              <vue-editor v-model="HTMLcontent"></vue-editor>
            </form>

        <!-- VIEW -->
        <div class="view">

          <activity-page :activity-info="activityArr" @delete="remove(index)"></activity-page>
        
        </div>

<!-- window -->          
</div> 

</template>

<script>
import { VueEditor } from "vue2-editor";
import ActivityPage from "./ActivityPage.vue";

export default {
    components:{
       VueEditor,
       ActivityPage
    },
     data(){
       return{
       
            title:"",
            time:"",
            location:"忠孝東路四段170巷17弄1號1樓",
            introduction:"",
            // content:"",
            picture:"",
            activityArr:[],
            register:"",
            HTMLcontent: ""
       }         
     },
     methods:{
        add(){
            //push the message to messageArr
            let activity={
                 title:this.title,
                 time:this.time,
                 location:this.location,
                 introduction:this.introduction,
                 content : this.HTMLcontent,
                 register: this.register,
                 picture:this.picture,
            }
            this.activityArr.push(activity)
            console.log(this.activityArr)
        },
        remove(index){
             console.log("delete"+index)
            // splice the message to messageArr
             this.activityArr.splice(index,1)
        },
    }
}
</script>


<style scoped>

.window {
  display: flex;
  padding: 8px;
}

.information {
  width:50%;
  display: flex;
  flex-direction: column;
  padding: 8px;
  margin: 0 20px 0 20px;
}
.view{
   width:50%;
}

label {
  margin-top: 16px;
}
.activityBox {
  border: 1px solid black;
}

.buttonStyle{
  width: 100%;
  margin: 16px auto;
  display: block;
}
</style>