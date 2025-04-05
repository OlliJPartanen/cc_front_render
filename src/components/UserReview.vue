
<script>
//This is a test comment. This is used to test comment changes on different branches

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
            // change the you
            if (userinput == undefined) {
                document.getElementById("youwrote").innerHTML = "You wrote: Nothing.... why?";
            } else {
                document.getElementById("youwrote").innerHTML = "You wrote: " + userinput;
                
                // This uses a randomizer, which is not used in this branch
                //this.analysisRandomizer()
                var testi = this.commentAnalyzer(userinput)
                document.getElementById("youwrote").innerHTML = "You wrote: " + userinput;

            }

        },

        // ChatGPT was used to help create this method. 
        // ChatGPT-created a base code which was used as a frame to create this method
        // Check report for further info
        async commentAnalyzer(userinput){
            
            // Try to fetch response from URL (sentiment endpoint)
            // Use userinput as a body to post to backend
            try {
                const res = await fetch("https://cc-backend-open-cloud-computing.2.rahtiapp.fi/sentiment", {
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    body: JSON.stringify({comment:  userinput})
                });

                // Wait for a response
                const data = await res.json();
                this.response = data.response;
                let analysis = this.response;
                
                // DEBUG, log response and show data on page
                console.log(this.response)
                console.log("POS: " + analysis.pos)
                console.log("NEG: " + analysis.neg)
                console.log("NEU: " + analysis.neu)
                document.getElementById("values").innerHTML = ("Positive: " + analysis.pos + ", Neutral: " + analysis.neu + ", Negative: " + analysis.neg)

                
                // Iterate through values and take highest value and key into variables
                // Source: https://stackoverflow.com/questions/27376295/getting-key-with-the-highest-value-from-object
                let highestValue = 0;
                let highestValueKey = "";
                for(let x in analysis) {
                    if(analysis[x] > highestValue) {
                        highestValue = analysis[x];
                        highestValueKey = x
                    }
                }

                this.analysisCommenter(highestValueKey)

            } catch (e) {
                console.error("THIS IS AN ERROR: ", e)
            }
        },

        // Get photo and text change with a method
        analysisCommenter(valueText) {


            if (valueText == "pos") {
                document.getElementById("analysisimage").src = "/positive.jpg"
                return document.getElementById("analysis").innerHTML = this.randomizeString(positiveString)
            } 
            else if (valueText == "neu") {
                document.getElementById("analysisimage").src = "/neutral.jpg"
                return document.getElementById("analysis").innerHTML = this.randomizeString(neutralString)
            } else {
                document.getElementById("analysisimage").src = "/negative.jpg"
                return document.getElementById("analysis").innerHTML = this.randomizeString(negativeString)
            }

        },

        /*
        THIS is a randomizer, which is not used in this branch (check task 3) 
        Randomizes a response and a corresponding image
        analysisRandomizer(){
            var randomNum =  Math.floor(Math.random() * 3);
            // Debug random value to log. 0 pos, 1 neu, 2 neg
            console.log(randomNum)
            if (randomNum == 0) {
                document.getElementById("analysisimage").src = "/positive.jpg"
                return document.getElementById("analysis").innerHTML = this.randomizeString(positiveString)
            } 
            else if (randomNum == 1) {
                document.getElementById("analysisimage").src = "/neutral.jpg"
                return document.getElementById("analysis").innerHTML = this.randomizeString(neutralString)
            } 
            else {
              document.getElementById("analysisimage").src = "/negative.jpg"
              return document.getElementById("analysis").innerHTML = this.randomizeString(negativeString)
            }
              

        },
        */

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
    <h3 id="youwrote"></h3>
    <h3 id="values"></h3>
    <h1 id="analysis"></h1>
    <img id="analysisimage">
  </div>
  
</template>


<style scoped>
h1 h2 {
  font-weight: 500;
  font-size: 2.6rem;

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

</style>
