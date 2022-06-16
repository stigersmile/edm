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

            <label for="activity-content">Content:</label>
            <textarea rows="4" cols="50" v-model="content">...</textarea> 

            <label for="activity-time">Choose a activity time:</label>
            <input type="datetime-local" v-model="time" />

            <label for="activity-location">Location:</label>
            <input type="text" v-model="location" />

            <button>add</button>
            </form>
        <!-- VIEW -->
        <div class="view">

        <section class="activityBox" v-for= "(elm,index) in activityArr" v-bind:key="index">
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
                href="https://www.surveycake.com/s/3p7nr"
                text-transform="none"
                vertical-align="middle"
                >報名</mj-button
              >
            </mj-column>
          </mj-section>

            <!-- <button v-on:click="this.delete(index)">delete</button> -->
        </section>

<!-- view -->
</div>

<!-- window -->
</div> 
</template>

<script>
export default 'FormPage'({

     data:{

            title:"",
            time:"",
            location:"忠孝東路四段170巷17弄1號1樓",
            introduction:"",
            content:"",
            picture:"",
            activityArr:[]
        
    },
     methods:{
        add(){
            //push the message to messageArr
            let activity={
                 title:this.title,
                 time:this.time,
                 location:this.location,
                 introduction:this.introduction,
                 content:this.content,
                 picture:this.picture,
            }
            this.activityArr.push(activity)
            console.log(this.activityArr)
        },
        delete(index){
             console.log("delete"+index)
            // splice the message to messageArr
            this.activityArr.splice(index,1)
        },
    }
})
</script>
