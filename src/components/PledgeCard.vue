<template>
  <div :class="pledgeData.days>0?'container-pledgecard':'container-pledgecard zero-days'">
      <div class="header-pledge">
          <span class="pledgeName">{{pledgeData.nom}}</span>
          <span class="pledgePrice">Pledge ${{pledgeData.price}} or more</span>
      </div>
      <p class="pledge-text">You get an ergonomic stand made of natural bamboo. You've helped us launch our promotional campagn, and you'll be added to a special Backer member list .</p>
      <div class="pledge-footer">
          <span class="days">{{pledgeData.days}} <span class="left">left</span></span>
          <button :class="pledgeData.days >0?'btn-reward':'btn-reward zero-days-bg'" @click="sendIndexSelected(index)">Select Reward</button>
      </div>
  </div>
</template>

<script>
export default {
    name:'PledgeCard',
    props:{
        pledgeData:Object,
        index:Number
        
    },

    methods:{

        sendIndexSelected(index){
            console.log('sendIndexSelected')
            this.$emit('getIndexSelected',index)
        }
    }


}
</script>

<style scoped lang="scss">

    .container-pledgecard{
        min-height: 200px;
        width: 100%;
        border:1px solid rgb(196, 196, 196);
        border-radius: 5px;
        padding:20px;
        margin: 20px 0;

        .header-pledge{
            display: flex;
            justify-content: space-between;

            .pledgeName{
                font-weight: bold;
            }
            .pledgePrice{
                font-size: 12px;
                color: rgb(31, 179, 169) ;
                font-weight: bold;
            }
            .pledgePrice:hover{
                cursor: url("data:image/x-icon;base64,AAACAAEAICACAAAAAAAwAQAAFgAAACgAAAAgAAAAQAAAAAEAAQAAAAAAgAAAAAAAAAAAAAAAAgAAAAAAAAAAAAAA////AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/gAAAf4AAAPVAAAH1QAAB9WAAA3VgAAd/4AAGbaAAAG2gAABtgAAAYAAAAGAAAABgAAAAYAAAAAAAAA//////////////////////////////////////////////////////////////////////////////////////gD///4A///8AP//+AB///AAf//wAD//4AA//8AAP//AAD//5AA///wAf//8Af///D////w////8P////n///8="),
                auto;
            }
        }
        .pledge-text{
            line-height: 2;
        }
        .pledge-footer{
            display: flex;
            justify-content: space-between;
            align-items: center;

            .days{
                font-size: 20px;
                font-weight: bold;
                display: flex;


                .left{
                   color: rgb(196, 196, 196);
                   font-size: 12px;
                   display: flex;
                   align-items: center;
                   margin-left: 4px;
                }
            }
            .btn-reward{
                background-color: rgb(31, 179, 169) ;
                color: white;
                padding: 0.7em 1.2em;
                border-radius: 30px;
                font-size: 12px;
            }
            .btn-reward:hover{
                cursor: url("data:image/x-icon;base64,AAACAAEAICACAAAAAAAwAQAAFgAAACgAAAAgAAAAQAAAAAEAAQAAAAAAgAAAAAAAAAAAAAAAAgAAAAAAAAAAAAAA////AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/gAAAf4AAAPVAAAH1QAAB9WAAA3VgAAd/4AAGbaAAAG2gAABtgAAAYAAAAGAAAABgAAAAYAAAAAAAAA//////////////////////////////////////////////////////////////////////////////////////gD///4A///8AP//+AB///AAf//wAD//4AA//8AAP//AAD//5AA///wAf//8Af///D////w////8P////n///8="),
                    auto;
                background-color: rgb(8, 141, 132) ;

            }
        }
    }
    .zero-days{
        opacity: 0.5;
        pointer-events: none;
    }
    .zero-days-bg{
        background-color: gray !important;
    }

</style>