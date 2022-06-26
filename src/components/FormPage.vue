<template>

<div class="window">
        <!-- information -->
        
        <form class="information formStyle" @submit.prevent="add">

            <label for="activity-title">Picture URL</label>
            <input type="text" v-model="picture" />   

            <label for="activity-title">Activiey Name</label>
            <input type="text" v-model="title" />

            <!-- <label for="activity-introduction">Introduction:</label> -->
            <!-- <textarea rows="4" cols="50" v-model="introduction">...</textarea> -->

            <label for="activity-time">Choose a activity time:</label>
            <input type="datetime-local" v-model="time" />

            <label for="activity-location">Location:</label>
            <input type="text" v-model="location" />

            <label for="activity-register">Register:</label>
            <input type="text" v-model="register" />

          

              <label><input type="radio" v-model="current" value="Comp_int" /> 活動介紹</label>
              <label><input type="radio" v-model="current" value="Comp_act" /> 活動內容</label>

              <div v-if ="current === 'Comp_int'">
                <vue-editor v-model="introduction" ></vue-editor>
              </div>
               <div v-if ="current === 'Comp_act'">
              <vue-editor v-model="HTMLcontent" ></vue-editor>
                </div>
 
              <button class="buttonStyle" >add</button>
         </form>

        <!-- VIEW -->
        <div class="view">
          
        <activity-page :activity-info="activityArr" @delete="remove(index)"  ref="content"></activity-page>
        <button class="buttonStyle" @click="transfer">Transfer</button>
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
            picture:"",
            activityArr:[],
            register:"",
            HTMLcontent: "",
            current:"Comp_int",
            mjms_start:`<mjml>
  <mj-body background-color="#F4F4F4" color="#55575d" font-family="Arial, sans-serif">
    <mj-section background-color="#ffffff" background-repeat="repeat" padding-bottom="0px" padding-top="0px" padding="20px 0" text-align="center" vertical-align="top">
      <mj-column>
        <mj-image align="center" padding="0px 0px" src="https://i.imgur.com/vPqoFgC.jpg" target="_blank" width=""></mj-image>
      </mj-column>
    </mj-section>
    <mj-section background-color="#ffffff" background-repeat="repeat" padding-bottom="0px" padding="20px 0" text-align="center" vertical-align="top">
      <mj-column>`,

             mjms_end:`<mj-divider border-color="#808080" border-style="solid" border-width="1px" padding-left="100px" padding-right="100px" padding-bottom="20px" padding-top="20px"></mj-divider>
    <mj-section background-color="#ffffff" background-repeat="repeat" padding="20px 0" text-align="center" vertical-align="top">
      <mj-column>
        <mj-social align="center">
          <mj-social-element name="facebook" href="https://www.facebook.com/zhongziaoChan"></mj-social-element>
        </mj-social>
        <mj-text align="left" color="#55575d" font-family="Arial, sans-serif" font-size="13px" line-height="22px" padding-bottom="0px" padding-left="40px" padding-right="40px" padding-top="0px" padding="10px 25px">
          <p style="margin: 10px 0; color:#151e23; font-size:16px; font-family:Georgia,Helvetica,Arial,sans-serif">
          <p style="text-align: center;"><span style="color: #808080;">Copyright &copy; 2022 zhongziaoChan. All rights reserved.</span><br /><br /><span style="color: #808080;">忠孝禪修會館&nbsp; </span></p>
          <p style="text-align: center;"><span style="color: #808080;"><strong>地址</strong>:106台北市大安區忠孝東路四段170巷17弄1號</span><br /><span style="color: #808080;">Email<strong> : </strong>86gheartchan@gmail.com</span><br /><span style="color: #808080;">Facebook: 忠孝禪修會館</span></p>
        </mj-text>
      </mj-column>
    </mj-section>
  </mj-body>
</mjml>`
            
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
        getActivity_img(image){
          let info =  
          `<mj-section>
            <mj-column>
              <mj-image  src= ${image} />
            </mj-column>
          </mj-section>`
          return info
        },
        getActivity_content(title,introduction,content,time,location){
          let info =  
          `<mj-text
            align="left"
            color="#55575d"
            font-family="Arial, sans-serif"
            font-size="13px"
            line-height="22px"
            padding-bottom="0px"
            padding-left="40px"
            padding-right="40px"
            padding-top="0px"
            padding="10px 25px"
          >
          
            <img :src="picture">
            <p
              style="
                margin: 10px 0;
                color: #151e23;
                font-size: 16px;
                font-family: Georgia, Helvetica, Arial, sans-serif;
              "
            >
            
              <b>${title}</b>
              <p>${introduction}</p>
              <br />✨課程時間&amp;內容
              <br />${content}
              <br />🔺時間:${time}
              <br />🔺地點:${location}
            
          </mj-text>`
          return info
        },
        getActivity_register(register){
          let info=` <mj-section
            background-color="#ffffff"
            background-repeat="repeat"
            padding-bottom="0px"
            padding="20px 0"
            text-align="center"
            vertical-align="top"
          >
            <mj-column>
              <mj-button
                align="center"
                background-color="#354552"
                border-radius="3px"
                color="#ffffff"
                font-family="Georgia, Helvetica, Arial, sans-serif"
                font-size="14px"
                font-weight="normal"
                inner-padding="10px 25px"
                padding="10px 25px"
                text-decoration="none"
                href= "${register}"
                text-transform="none"
                vertical-align="middle"
                >報名</mj-button
              >
            </mj-column>
          </mj-section>`
          return info
        },
        transfer(){
          let allActivity =[];

          
           for(let activityInfor of this.activityArr){
            const {title,time,location,picture,content,introduction,register} = activityInfor
            let activityString = 
            this.getActivity_img(picture) + 
            this.getActivity_content(title,introduction,content,time,location) +
            this.getActivity_register(register)
            allActivity.push(activityString)
          }
          let result = this.mjms_start + allActivity.join(" ") +this.mjms_end

          console.log(result)
        }
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