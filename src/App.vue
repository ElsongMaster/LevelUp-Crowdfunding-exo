<template>
  <div id="app">
    <header>
      <div class="logo"><img src="./assets/logo.svg" alt="" /></div>
      <nav>
        <ul class="nav-list">
          <li><a href="">About</a></li>
          <li><a href="">Discover</a></li>
          <li><a href="">Get Started</a></li>
        </ul>
      </nav>
    </header>

    <div class="main-content">
      <img
        class="logo-mastercraft"
        src="./assets/logo-mastercraft.svg"
        alt="log mastercraft"
      />
      <div class="general-info">
        <h1>Mastercraft Bamboo Monitor Riser</h1>
        <p>
          A beautiful & handcraft Monitor stand to reduce neck and eye stran.
        </p>
        <div class="content-btn">
          <button class="back-btn" @click="displayOptions()">
            Back this project
          </button>

          <button @click="bookmarkedPage()">
            <i class="fas fa-bookmark"></i>Bookmarked
          </button>
        </div>
      </div>

      <div class="container-numbers">
        <div class="numbers-content">
          <div class="number-card">
            <div>
              <p class="number">${{ number }}</p>
              <p class="total">of $100,000 backed</p>
            </div>
          </div>
          <div class="number-card borderTwoSides">
            <div>
              <p class="number">$5,0007</p>
              <p class="total">total backers</p>
            </div>
          </div>
          <div class="number-card">
            <div>
              <p class="number">56</p>
              <p class="total">days left</p>
            </div>
          </div>
        </div>
        <div class="barsProgress-content">
          <div id="myProgress">
            <div id="myBar"></div>
          </div>
        </div>
      </div>

      <div class="about-container">
        <h2>About this project</h2>

        <p>
          The Mastercradt Bamboo Monitor Riser is a sturdy and stylish platform
          that elevates your screen to a more comfortable viewing height.
          Placing your monitor at eye level has the potential to improve your
          posture and make you more comfortable while at work, helping you stay
          focused on the task at hand
        </p>

        <p>
          Featuring artisan craftsmanship, the simplicity of design creates
          extra desk space below your cocmputer to allow notepads, pens, and USB
          sticks to be stored under the stand.
        </p>
        <div class="main-container-pledgcard">
          <PledgeCard
            v-for="(pledgeData, index) in dataPledgeCard"
            :key="index"
            :pledgeData="pledgeData"
            :index="index"
            @getIndexSelected="displayIndex"
          />
        </div>
      </div>
    </div>
    <div v-if="displayBackOption" class="PledgeCardSelect-container">
      <div class="mainContent-PladgeCardSelect">
        <div class="title-container">
          <h2>Back this project</h2>
          <div class="container-close">
            <button @click="hideOptions()">
              <i class="fas fa-times"></i>
            </button>
          </div>
        </div>
        <p>
          Want to support us in bringing Mastercraft Bamboo Monitor Riser out in
          the world?
        </p>
        <PledgeCardSelect
          v-for="(pledgeData, index) in tabPledge"
          :key="index"
          :pledgeData="pledgeData"
          :selected="false"
          :index="index"
          @checkBoxIndex="resetIsSelected"
          @getPrice="updateData"
        />
      </div>
    </div>
    <GratefulMsg
      v-if="displayGratefulMsg"
      @displayGratefulMsg="updateGratefulMsg"
    />
  </div>
</template>

<script>
import PledgeCard from "./components/PledgeCard.vue";
import PledgeCardSelect from "./components/PledgeCardSelect.vue";
import GratefulMsg from "./components/GratefulMsg.vue";

export default {
  name: "App",
  components: {
    PledgeCard,
    PledgeCardSelect,
    GratefulMsg,
  },

  data() {
    return {
      displayBackOption: false,
      displayGratefulMsg: false,
      number: 89914,
      tabPledge: [
        {
          nom: "Pledge with no reward",
          price: null,
          days: null,
          isGivenReward: false,
          isSelected: false,
          index: 0,
        },
        {
          nom: "Bamboo Stand",
          price: 25,
          days: 101,
          isGivenReward: true,
          isSelected: false,
          index: 1,
        },
        {
          nom: "Black Edition Stand",
          price: 75,
          days: 64,
          isGivenReward: true,
          isSelected: false,
          index: 2,
        },
        {
          nom: "Mahogamy Special Edition",
          price: 200,
          days: 0,
          isGivenReward: true,
          isSelected: false,
          index: 3,
        },
      ],
      indexOptSelected: null,
    };
  },

  methods: {
    displayOptions() {
      this.displayBackOption = true;
      let heightElt = null;
      setTimeout(() => {
        let elt = document.getElementsByClassName(
          "PledgeCardSelect-container"
        )[0];
        console.log(elt.clientHeight);
        heightElt = elt.clientHeight - 100;
        let styleNode = "height:" + heightElt + "px; overflow:hidden;";
        console.log(styleNode);
        let appNode = document.getElementById("app");
        appNode.style = styleNode;
        //  console.log(elt.style)
        console.log(appNode);
      }, 500);
    },
    hideOptions() {
      this.displayBackOption = false;
      let appNode = document.getElementById("app");
      appNode.style = "";
      this.tabPledge.forEach((elt) => {
        elt.isSelected = false;
      });
    },

    bookmarkedPage() {
      let btn = document.getElementsByClassName("fa-bookmark")[0];
      btn = btn.parentElement;
      btn.classList.add("btn-Bookmark-visited");
      // const urlPage = window.location.href.split('?')[0]
      // console.log(urlPage)
      // var createBookmark = browser.bookmarks.create({
      //   title: "bookmarks.create() on MDN",
      //   url: urlPage
      // });

      // createBookmark.then(onCreated);
    },
    displayIndex(index) {
      this.indexOptSelected = index + 1;
      console.log("displayIndex", index);
      this.tabPledge[index + 1].isSelected = true;

      let btnBack = document.getElementsByClassName("back-btn")[0];

      btnBack.click();
    },

    resetIsSelected(index) {
      console.log("resetIsSelected", index);
      for (let i = 0; i < this.tabPledge.length; i++) {
        if (i != index) {
          this.tabPledge[i].isSelected = false;
        } else {
          this.tabPledge[i].isSelected = true;
        }
      }
    },
    updateGratefulMsg(bool) {
      let appNode = document.getElementById("app");
      this.displayGratefulMsg = bool;
      if (this.displayBackOption) {
        this.displayBackOption = false;
        console.log("updateGratefulMsg");
        if (appNode.classList.contains("allScreen")) {
          appNode.classList.remove("allScreen");
        } else {
          appNode.style="";
          appNode.classList.add("allScreen");
        }
      }
    },

    updateData(tab) {
      console.log("updateData", tab);
      this.number += tab[1] !=null? parseInt(tab[1]):0;
      this.updateGratefulMsg(tab[0]);
      let width = Math.round((this.number / 100000) * 100);
      this.updateBarProgress(width);
    },

    updateBarProgress(width) {
      var elem = document.getElementById("myBar");
      elem.style.width = width + "%";
    },
  },

  computed: {
    dataPledgeCard() {
      let tab = [];
      for (let i = 0; i < this.tabPledge.length; i++) {
        if (i > 0) {
          tab.push(this.tabPledge[i]);
        }
      }

      return tab;
    },
  },
};

// var i = 0;
// function move() {
//   if (i == 0) {
//     i = 1;
//     var elem = document.getElementById("myBar");
//     var width = 1;
//     var id = setInterval(frame, 10);
//     function frame() {
//       if (width >= 100) {
//         clearInterval(id);
//         i = 0;
//       } else {
//         width++;
//         elem.style.width = width + "%";
//       }
//     }
//   }
// }
</script>

<style lang="scss">
#app {
  min-height: 100vh;
  font-family: "Commissioner", sans-serif;
  background-color: rgb(250, 250, 250);
  display: flex;
  flex-direction: column;
  background-image: url(./assets/image-hero-desktop.jpg);
  background-repeat: no-repeat;
  background-position: top;
  background-size: contain;
  header {
    display: flex;

    height: 250px;

    z-index: 1;
    width: 100%;
    margin-bottom: 20px;
    .logo {
      width: 30%;
      display: flex;
      height: 35%;
      justify-content: center;
      align-items: center;
    }
    nav {
      width: 70%;
      display: flex;
      justify-content: flex-end;
      align-items: center;
      padding: 5px;
      height: 35%;
      .nav-list {
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        color: rgb(219, 217, 217);
        width: 40%;
        height: fit-content;
        padding-right: 40px;
        li a:hover {
          cursor: url("data:image/x-icon;base64,AAACAAEAICACAAAAAAAwAQAAFgAAACgAAAAgAAAAQAAAAAEAAQAAAAAAgAAAAAAAAAAAAAAAAgAAAAAAAAAAAAAA////AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/gAAAf4AAAPVAAAH1QAAB9WAAA3VgAAd/4AAGbaAAAG2gAABtgAAAYAAAAGAAAABgAAAAYAAAAAAAAA//////////////////////////////////////////////////////////////////////////////////////gD///4A///8AP//+AB///AAf//wAD//4AA//8AAP//AAD//5AA///wAf//8Af///D////w////8P////n///8="),
            auto;
        }
      }
    }
  }
  .main-content {
    width: 50%;
    height: fit-content;
    margin: 0 auto;
    position: relative;
    .logo-mastercraft {
      position: absolute;
      left: 45%;
      top: -40px;
    }
    .general-info {
      width: 100%;
      height: 200px;
      background-color: white;

      border-radius: 10px;
      padding: 20px;
      h1 {
        font-weight: bolder;
        font-size: 25px;
        text-align: center;
        margin-top: 10px;
      }
      p {
        color: rgb(163, 153, 153);
        font-size: 13px;
        text-align: center;
      }
      .content-btn {
        height: 100%;
        display: flex;
        justify-content: space-between;
        margin-top: 20px;
        button,
        span {
          height: fit-content;
          width: fit-content;
        }
        button:first-child {
          color: white;
          background-color: rgb(25, 170, 160);
          padding: 0.5em 2em;
          border-radius: 60px;
        }
        button:nth-child(2) {
          position: relative;
          color: rgb(25, 170, 160);
          background-color: rgb(235, 226, 226);
          padding: 0.5em 3em;
          border-radius: 60px;

          i {
            position: absolute;
            bottom: 0;
            left: 0;
            background-color: rgb(25, 170, 160);
            width: 40px;
            height: 40px;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            border-radius: 50%;
          }
        }

        button:hover {
          cursor: url("data:image/x-icon;base64,AAACAAEAICACAAAAAAAwAQAAFgAAACgAAAAgAAAAQAAAAAEAAQAAAAAAgAAAAAAAAAAAAAAAAgAAAAAAAAAAAAAA////AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/gAAAf4AAAPVAAAH1QAAB9WAAA3VgAAd/4AAGbaAAAG2gAABtgAAAYAAAAGAAAABgAAAAYAAAAAAAAA//////////////////////////////////////////////////////////////////////////////////////gD///4A///8AP//+AB///AAf//wAD//4AA//8AAP//AAD//5AA///wAf//8Af///D////w////8P////n///8="),
            auto;
          background-color: rgb(20, 121, 115);
          color: white;
        }
        span {
          display: flex;
          justify-content: space-between;
          align-items: center;
          background-color: rgb(221, 215, 215);
          color: rgb(20, 121, 115);
          border-radius: 50px;
          padding: 0.1em 0.5em 0 0;
          width: 150px;

          img {
            height: 40px;
            width: 40px;
          }
        }
      }
    }

    .borderTwoSides {
      border-right: 1px solid rgb(190, 190, 190);
      border-left: 1px solid rgb(190, 190, 190);
    }
    .container-numbers {
      width: 100%;
      height: 200px;
      background-color: white;

      border-radius: 10px;
      padding: 20px;

      margin-top: 30px;

      .numbers-content {
        width: 90%;
        height: 70%;
        margin: 0 auto;
        display: flex;
        .number-card {
          display: flex;
          flex-direction: column;
          justify-content: flex-end;
          align-items: center;
          width: 100%;
          height: 70%;
          // padding: 5% 10%;
          div {
            // border: 2px solid;
            height: fit-content;
            width: fit-content;
            .number {
              font-size: 30px;
              font-weight: bolder;
            }
            .total {
              font-size: 13px;
              color: rgb(196, 196, 196);
            }
          }
        }
      }
      .barsProgress-content {
        margin: 0 20px;
      }
    }
    .about-container {
      margin-top: 30px;
      background-color: white;
      padding: 20px;

      h2 {
        font-weight: bolder;
      }
      p {
        margin: 20px 0;
        color: rgb(196, 196, 196);
        font-size: 13px;
      }
    }
  }
  .PledgeCardSelect-container {
    min-height: 100vh;
    width: 100vw;
    background-color: rgb(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    padding: 60px 0;
    // overflow: hidden;
    .mainContent-PladgeCardSelect {
      width: 50vw;
      height: fit-content;
      background-color: white;
      border-radius: 5px;
      padding: 30px;
      .title-container {
        display: flex;
        h2,
        .container-close {
          width: 50%;
        }
        h2 {
          font-weight: bold;
        }
        .container-close {
          display: flex;
          justify-content: flex-end;
          button {
            i {
              color: rgb(163, 153, 153);
              // color: blue;
              // border: 2px solid;
            }
            i:hover {
              cursor: url("data:image/x-icon;base64,AAACAAEAICACAAAAAAAwAQAAFgAAACgAAAAgAAAAQAAAAAEAAQAAAAAAgAAAAAAAAAAAAAAAAgAAAAAAAAAAAAAA////AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/gAAAf4AAAPVAAAH1QAAB9WAAA3VgAAd/4AAGbaAAAG2gAABtgAAAYAAAAGAAAABgAAAAYAAAAAAAAA//////////////////////////////////////////////////////////////////////////////////////gD///4A///8AP//+AB///AAf//wAD//4AA//8AAP//AAD//5AA///wAf//8Af///D////w////8P////n///8="),
                auto !important;
            }
          }
        }
      }
      p {
        color: rgb(163, 153, 153);
        font-size: 13px;
        margin: 10px 0;
      }
    }
  }
  .hide {
    display: none !important;
  }
}
.allScreen {
  height: 100vh;
  width: 100vw;
  overflow: hidden;
}
#app {
  .general-info {
    .content-btn {
      .btn-Bookmark-visited {
        position: relative;
        color: rgb(112, 112, 112);
        background-color: rgb(235, 226, 226) !important;
        padding: 0.5em 3em;
        border-radius: 60px;

        i {
          position: absolute;
          bottom: 0;
          left: 0;
          background-color: rgb(112, 112, 112) !important;
          width: 40px;
          height: 40px;
          color: rgb(177, 177, 177) !important;
          display: flex;
          justify-content: center;
          align-items: center;
          border-radius: 50%;
        }
      }
    }
  }
}

#myProgress,
#myBar {
  height: 20px;
}

#myProgress {
  width: 100%;
  border-radius: 30px;
  background-color: rgb(207, 207, 207);
}

#myBar {
  width: 89.914%;
  // height: 30px;
  border-radius: 30px;
  padding-left: 20px;
  // margin-left: 5px;

  background-color: rgb(20, 121, 115);
}
</style>
