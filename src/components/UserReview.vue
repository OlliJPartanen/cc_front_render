
<script>

// Comment string lists
let positiveString = [
    "This was a positive comment!",
    "A positive comment!",
    "----Positive----",
    "You really like this!"
];

let neutralString = [
    "This was neutral",
    "...meh",
    "----Neutral----",
    "You really have no opinion about this, do you?"
];

let negativeString = [
    "This was negative",
    "A negative comment!",
    "----Negative----",
    "Wow you must really hate this"
];

// VUE-syntax
export default {
    methods: {
        // Take unput field value
        inputFieldPresenter(userinput) {
            // Debug it on console
            console.log(userinput);
            // change the you
            if (userinput == undefined) {
                document.getElementById("youwrote").innerHTML = "You wrote: Nothing.... why?";
            } else {
                document.getElementById("youwrote").innerHTML = "You wrote: " + userinput;
                this.analysisRandomizer()

            }

        },

        // Randomizes a response and a corresponding image
        analysisRandomizer(){
            var randomNum =  Math.floor(Math.random() * 3);
            // Debug random value to log. 0 pos, 1 neu, 2 neg
            console.log(randomNum)
            if (randomNum == 0) {
                document.getElementById("analysisimage").src = "src/assets/positive.jpg"
                return document.getElementById("analysis").innerHTML = this.randomizeString(positiveString)
            } 
            else if (randomNum == 1) {
                document.getElementById("analysisimage").src = "src/assets/neutral.jpg"
                return document.getElementById("analysis").innerHTML = this.randomizeString(neutralString)
            } 
            else {
              document.getElementById("analysisimage").src = "src/assets/negative.jpg"
              return document.getElementById("analysis").innerHTML = this.randomizeString(negativeString)
            }

        },

        // Returns a random string from a list of strings, takes a string as a variable
        randomizeString(listOfStrings) {

            var randomString  = listOfStrings[Math.floor(Math.random() * listOfStrings.length)];

            return randomString;
        }

    }
}
</script>

<template>
    
  <div class="inputText" id="inputter">
    <label for="Text to be analyzed:">Press the button to analyze your comment!: </label>
    <br>
    <br>
    <!--V-model acts as kind of a binder for this-->
    <input v-model="userinput"></input>

    <!--call on inputFieldPresenter method when pressed, and pass userinput as a variable-->
    <button v-on:click=inputFieldPresenter(userinput)>Analyze review text</button>
    <br>

    <!--Texts and images are handeled by methods-->
    <h2 id="youwrote"></h2>
    <h1 id="analysis"></h1>
    <img id="analysisimage">
  </div>
  
</template>


<style scoped>
h1 h2 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.inputtext h1,
.inputtext h3 {
  text-align: center;
}

img {
    max-width: 50%;
    max-height: 50%;
}

div {
    text-align: center;
}

@media (min-width: 1024px) {
  .inputtext h1,
  .inputtext h3 {
    text-align: left;
  }
}
</style>
