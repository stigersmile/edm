<template>
<div class="header">
    <span></span>
    <h1>EDM GENERATOR</h1>
        <!-- <h1>{{mjms}}</h1> -->
    <button class="transfer" @click="transfer">Transfer</button>
</div>
</template>

<script>
export default {

    data(){
        return{
            activity:"123456",
            mjms:`<mjml>
  <mj-body background-color="#F4F4F4" color="#55575d" font-family="Arial, sans-serif">
    <mj-section background-color="#ffffff" background-repeat="repeat" padding-bottom="0px" padding-top="0px" padding="20px 0" text-align="center" vertical-align="top">
      <mj-column>
        <mj-image align="center" padding="0px 0px" src="https://i.imgur.com/vPqoFgC.jpg" target="_blank" width=""></mj-image>
      </mj-column>
    </mj-section>
    <mj-section background-color="#ffffff" background-repeat="repeat" padding-bottom="0px" padding="20px 0" text-align="center" vertical-align="top">
      <mj-column>
        

     ${this.activity}              
         
          
    <mj-divider border-color="#808080" border-style="solid" border-width="1px" padding-left="100px" padding-right="100px" padding-bottom="20px" padding-top="20px"></mj-divider>
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
        transfer(){
            console.log(`fsdf ${this.activity}    `)
        }
    }
}
</script>

<style scoped>

.header{
     display:flex;
     justify-content:space-between;
}
.transfer{
    height:32px;
    width:64px;
}
</style>

    