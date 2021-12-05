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
          <button>Back this project</button>

          <span><img src="./assets/icon-bookmark.svg" alt="" />Bookmarked</span>
        </div>
      </div>

      <div class="container-numbers">
        <div class="numbers-content">
          <div class="number-card">
            <div>
              <p class="number">$89,914</p>
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
            v-for="(pledgeData, index) in tabPledge"
            :key="index"
            :pledgeData="pledgeData"
          />
        </div>
      </div>
    </div>
    <div class="PledgeCardSelect-container">
      <div class="mainContent-PladgeCardSelect">
        <div class="title-container">
          <h2>Back this project</h2>
          <div class="container-close">
            <i class="fas fa-times"></i>
          </div>
        </div>
        <p>
          Want to support us in bringing Mastercraft Bamboo Monitor Riser out in
          the world?
        </p>
      <PledgeCardSelect />
      </div>
    </div>
    <GratefulMsg />
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
      tabPledge: [
        {
          nom: "Bamboo Stand",
          price: 25,
          days: 101,
        },
        {
          nom: "Black Edition Stand",
          price: 75,
          days: 64,
        },
        {
          nom: "Mahogamy Special Edition",
          price: 200,
          days: 0,
        },
      ],
    };
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
        button {
          color: white;
          background-color: rgb(20, 121, 115);
          padding: 0.5em 2em;
          border-radius: 60px;
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
    height: 100vh;
    width: 100vw;
    background-color: rgb(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    position: absolute;
    .mainContent-PladgeCardSelect {
      width: 50vw;
      height: fit-content;
      background-color: white;
      border-radius: 5px;
      padding: 30px;
      .title-container {
        display: flex;
        h2,.container-close{
          width: 50%;

        }
        h2 {
          font-weight: bold;
        }
        .container-close {
          display: flex;
          justify-content: flex-end;
          i {
            color: rgb(163, 153, 153);
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
