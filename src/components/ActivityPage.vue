<template>

<div>
        <section class="activityBox" v-for= "(elm,index) in activityInfo" v-bind:key="index">
          <mj-text
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
            
              <b>{{elm.title}}</b>
              <p>{{elm.introduction}}</p>
              <br />✨課程時間&amp;內容
              <br />{{elm.content}}
              <br />🔺時間:{{elm.time}}
              <br />🔺地點:{{elm.location}}
            
          </mj-text>

          <mj-section
            background-color="#ffffff"
            background-repeat="repeat"
            padding-bottom="0px"
            padding="20px 0"
            text-align="center"
            vertical-align="top"
          >
            <mj-column>
              <button style="display:block margin: 0 auto"
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
                v-bind:href= "register"
                text-transform="none"
                vertical-align="middle"
                >報名</button
              >
            </mj-column>
          </mj-section>

          <button class="buttonStyle" @click="remove(index)">delete</button> 
        </section>
</div>
</template>

<script>
export default {
    props:["activityInfo"],
   
    methods:{
         remove(index){
            this.$emit('delete',index); 
        }
    },
    data(){
      return{
      }
    }
}
</script>

<style scoped>
.activityBox {
  border: 1px solid black;
}

.buttonStyle{
  width: 100%;
  margin: 16px auto;
  display: block;
}
</style>