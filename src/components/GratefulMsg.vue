<template>
  <div class="grateful-Maincontainer">
      <div class="grateful-content">
          <div class="icon-container">
              <i class="fas fa-check"></i>
          </div>
          <p class="thanks-p">Thanks for your support!</p>
          <p class="msg-p">Your pledge birng us one step closer to sharing Mastercraft Bamboo Monitor Riser worldwide. You will get an email once our campaign is completed</p>
          <div>

             <button @click="hideComponent(this)">Got it!</button>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name:"GratefulMsg",

    methods:{

        hideComponent(){
            let elt = document.getElementsByClassName('grateful-Maincontainer')[0]
            elt.classList.add('hide');
        }
    }
}
</script>

<style  lang="scss">
    .hide{
        display: none !important;
    }
    #app{
        // height: 100vh;
        // width: 100vw;
        // overflow: hidden !important;
        .grateful-Maincontainer{
            height: 100vh;
            width: 100vw;
            background-color: rgb(0,0,0,0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            position: absolute;
            display: none;
            .grateful-content{
                height: 60vh;
                width: 40vw;
                background-color: white;
                border-radius: 10px;
                padding: 30px;
                .icon-container{
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    height: 30%;
    
                    i{
                        color: white;
                        // font-weight: ;
                        font-size: 3vw;
                        padding: 20px ;
                        border-radius: 50%;
                        background-color:rgb(31, 179, 169)  ;
                    }
                }
                .thanks-p{
                    font-weight: bold;
                    font-size: 20px;
                    text-align: center;
                }
                .msg-p{
                    text-align: center;
                    margin-top: 10px ;
                    margin-bottom: 30px;
                    color:rgba(102, 100, 100, 0.61) ;
                    font-size: 14px;
                }
                div{
                    display: flex;
                    justify-content: center;
                    button{

                        background-color: rgb(31, 179, 169) ;
                        padding: 0.7em 1.4em;
                        color: white;
                        border-radius: 30px;
                    }
                }
            }
        }
    }
</style>