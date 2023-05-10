<template>
  <div class="row">
    <div class="col-12">
      <div class="row max game">
        <div class="col-5 col-sm-12 col-md-7 p-t large">
          <div class="row justify-center game-name p-top">Tic Tac Toe</div>
          <div class="row justify-center start">
            Game start at tab to the Box
          </div>
          <div class="row justify-center player-1">1st player x</div>
          <div class="row justify-center player-2">2nd player 0</div>
          <div class="row">
            <div class="col-12">
              <div
                v-for="(box, row) in arr"
                :key="row"
                class="row justify-center"
              >
                <input
                  type="text"
                  :disabled="arr[row][column] != '' || win"
                  v-for="(boxes, column) in arr"
                  :key="column"
                  class="col-1-3 p-auto b1 text-center"
                  v-model="arr[row][column]"
                  @click="addValue(row, column)"
                  readonly
                />
              </div>
            </div>
          </div>
          <div class="row justify-center reset">
            <button type="button" @click="reset">Reset</button>
          </div>
          <div class="row justify-center won" ref="winner">
            {{ whoWon() }}{{ matchTie() }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      flag: 1,
      bool: false,
      arr: [
        ["", "", ""],
        ["", "", ""],
        ["", "", ""],
      ],
      win: false,
      count: 3,
      Tie: "",
    };
  },
  methods: {
    addValue(row, column) {
      if (this.flag === 1) {
        this.arr[row][column] = "x";
        this.flag = 0;
        this.$refs.winner.innerHTML = "Player 0 turn";
      } else {
        this.arr[row][column] = "0";
        this.$refs.winner.innerHTML = "Player x turn";
        this.flag = 1;
      }
    },

    whoWon() {
      for (var i = 0; i < this.arr.length; i++) {
        // harizontal line
        if (
          this.arr[i][0] === "x" &&
          this.arr[i][1] === "x" &&
          this.arr[i][2] === "x"
        ) {
          this.$refs.winner.innerHTML = "player x won";
          this.win = true;
          alert("Player x won");
          alert("Tab to reset button to continiue");
        }
        //  vertical line
        if (
          this.arr[0][i] === "x" &&
          this.arr[1][i] === "x" &&
          this.arr[2][i] === "x"
        ) {
          this.$refs.winner.innerHTML = "player x won";
          this.win = true;
          alert("Player x won");
          alert("Tab to reset button to continiue");
        }
        // // diagonal
        if (
          this.arr[0][2] === "x" &&
          this.arr[1][1] === "x" &&
          this.arr[2][0] === "x"
        ) {
          this.$refs.winner.innerHTML = "Player x won";
          this.win = true;
          alert("Player x won");
          alert("Tab to reset button to continiue");
        }
        if (
          this.arr[0][0] === "x" &&
          this.arr[1][1] === "x" &&
          this.arr[2][2] === "x"
        ) {
          this.$refs.winner.innerHTML = "Player x won";
          this.win = true;
          alert("Player x won");
          alert("Tab to reset button to continiue");
        }
        // harizontal line
        if (
          this.arr[i][0] === "0" &&
          this.arr[i][1] === "0" &&
          this.arr[i][2] === "0"
        ) {
          this.$refs.winner.innerHTML = "player 0 won";
          this.win = true;
          alert("Player x won");
          alert("Tab to reset button to continiue");
        }
        //  vertical line
        if (
          this.arr[0][i] === "0" &&
          this.arr[1][i] === "0" &&
          this.arr[2][i] === "0"
        ) {
          this.$refs.winner.innerHTML = "player 0 won";
          this.win = true;
          alert("Player x won");
          alert("Tab to reset button to continiue");
        }
        // diagonal
        if (
          this.arr[0][2] === "0" &&
          this.arr[1][1] === "0" &&
          this.arr[2][0] === "0"
        ) {
          this.$refs.winner.innerHTML = "Player 0 won";
          this.win = true;
          alert("Player x won");
          alert("Tab to reset button to continiue");
        }
        if (
          this.arr[0][0] === "0" &&
          this.arr[1][1] === "0" &&
          this.arr[2][2] === "0"
        ) {
          this.$refs.winner.innerHTML = "Player 0 won";
          this.win = true;
          alert("Player x won");
          alert("Tab to reset button to continiue");
        }
      }
    },
    matchTie() {
      if (
        this.arr[0][0] !== "" &&
        this.arr[0][1] !== "" &&
        this.arr[0][2] !== "" &&
        this.arr[1][0] !== "" &&
        this.arr[1][1] !== "" &&
        this.arr[1][2] !== "" &&
        this.arr[2][1] !== "" &&
        this.arr[2][2] !== "" &&
        this.arr[2][3] !== ""
      ) {
        this.$refs.winner.innerHTML = "Match tie";
      }
    },
    reset() {
      for (var i = 0; i < this.arr.length; i++) {
        for (var j = 0; j < this.arr.length; j++) {
          this.arr[j] = "";
          window.location.reload();
        }
      }
    },
  },
};
</script>
<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.row {
  display: flex;
  flex-flow: row wrap;
}

.text-center {
  text-align: center;
}

.justify-center {
  justify-content: center;
}

.align-center {
  align-items: center;
}

.col-1-3 {
  flex: 0 0 17%;
}

.col-12 {
  flex: 0 0 100%;
}

.game {
  height: 100vh;
}

.b1,
.b2,
.b3,
.b3,
.b4,
.b5,
.b6,
.b7,
.b8,
.b9 {
  border: 1px solid violet;
  outline: 1px solid violet;
  width: 70%;
  height: 70px;
  cursor: pointer;
  border-radius: 5px;
  margin: 5px;
  font-size: 40px;
}

.head {
  padding-top: 0px;
  font-size: 40px;
}

.game-name {
  font-size: 50px;
  padding-bottom: 20px;
  color: brown;
}

.start {
  font-size: 25px;
  padding-bottom: 5px;
}

.player-1 {
  font-size: 20px;
  padding-bottom: 5px;
}

.player-2 {
  font-size: 20px;
  padding-bottom: 20px;
}

.reset {
  padding-top: 20px;
}

.reset > button {
  font-size: 20px;
  padding: 5px 15px 5px 15px;
  cursor: pointer;
  background-color: dimgray;
  color: white;
  outline: none;
  border: none;
  border-radius: 4px;
}

.reset > button:hover {
  box-shadow: 0 0 10px #9ecaed;
  border: 1px solid lawngreen;
}

.won {
  font-size: 20px;
  padding-top: 20px;
}

/* Extra small devices (phones, 600px and down) */
@media only screen and (max-width: 600px) {
  .col-sm-12 {
    flex: 0 0 100%;
  }

  .p-t {
    padding-top: 30px;
  }
}

/* Small devices (portrait tablets and large phones, 600px and up) */
@media only screen and (min-width: 600px) {
  .max {
    justify-content: center;
    background-color: beige;
  }

  .col-md-7 {
    flex: 0 0 58.33%;
  }

  .p-top {
    padding-top: 30px;
  }
}

/* Medium devices (landscape tablets, 768px and up) */
@media only screen and (min-width: 768px) {
}

/* Large devices (laptops/desktops, 992px and up) */
@media only screen and (min-width: 992px) {
  .large {
    justify-content: center;
    align-items: center;
    height: 100vh;
  }

  .col-5 {
    flex: 0 0 50%;
  }
}
</style>