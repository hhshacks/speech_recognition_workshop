# speech_recognition_workshop

Welcome to Hack Club's Speech Recognition workshop to show you the awesome capabilities of computational linguistics!

FINAL CODE AND LIVE DEMO HERE (IF YOU GET STUCK): https://repl.it/@HHSHack/WavyTrustingLegacysystem

# How to Start
1. Create a new Repl on repl.it, with the programming language set to HTML, CSS, and Javascript.
2. Replace HTML with this:
```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width">
    <title>Speech Recognition</title>
    <link rel="stylesheet" href="style.css">
  </head>
</html>
```

3. Create a body tag and add this code to it.
```
<body>
    <h1>Speech Recognition</h1>
    <script src="script.js"></script>
</body>
```
This will give us some text on the page and link our Javascript file to our HTML page.



4. Let's add a paragraph in the middle of the page to let our users know which words our program can detect. It's blank right now, but we'll be putting stuff in it later. It'll show what words our program is able to detect. Put it underneath the "h1" tag.

```
<p class="hints"></p>
```

Then let's add in another text box on the bottom to give our users some instructions. Put it underneath the "hints" paragraph.
```
<div>
  <p class="output"><em>Tap anywhere and try speaking!</em></p>
</div>
```

5. Let's add some style to this webpage! Add this to your "style.css" file. If you don't have one already, create one.
```
body, html {
  margin: 0;
}

html {
  height: 100%;
}

body {
  height: inherit;
  overflow: hidden;
}

h1, p {
  font-family: sans-serif;
  text-align: center;
  padding: 20px;
}

div {
  height: 100px;
  overflow: auto;
  position: absolute;
  bottom: 0px;
  right: 0;
  left: 0;
  background-color: rgba(255,255,255,0.2);
}
```

This will give some basic visual properties to our elements, centering everything and making it all look nice :)

### Your code should look something like this at this point:
![alt text](https://github.com/hhshacks/speech_recognition_workshop/blob/master/Screen%20Shot%202018-11-02%20at%201.46.19%20PM.png)

Now that we're all done with the HTML and CSS, it's time to move on to the magic: the Javascript part that makes all the speech recognition work!

# Javascript
1. We'll be using a built-in Chrome API to do the speech recognition. In order to call it, put this at the top of your Javascript file: 
```
var SpeechRecognition = SpeechRecognition || webkitSpeechRecognition
var SpeechGrammarList = SpeechGrammarList || webkitSpeechGrammarList
var SpeechRecognitionEvent = SpeechRecognitionEvent || webkitSpeechRecognitionEvent
```
This creates the objects that we'll use to store and track the user's speech.

2. Let's add the words that our program will detect. In this case, it'll be different colors. We'll be using an <strong>array</strong> to store our colors. An array is a list of values, which can be words (strings), numbers, or any other data type. In this case, we use an array to store all the different types of words our program will recognize.

```
var words = [ 'aqua' , 'azure' , 'beige', 'bisque', 'black', 'blue', 'brown', 'chocolate', 'coral', 'crimson', 'cyan', 'fuchsia', 'ghostwhite', 'gold', 'goldenrod', 'gray', 'green', 'indigo', 'ivory', 'khaki', 'lavender', 'lime', 'linen', 'magenta', 'maroon', 'moccasin', 'navy', 'olive', 'orange', 'orchid', 'peru', 'pink', 'plum', 'purple', 'red', 'salmon', 'sienna', 'silver', 'snow', 'tan', 'teal', 'thistle', 'tomato', 'turquoise', 'violet', 'white', 'yellow'];
```

Then add this to our code: 
```
var grammar = '#JSGF V1.0; grammar words; public <color> = ' + words.join(' | ') + ' ;'

var recognition = new SpeechRecognition();
var speechRecognitionList = new SpeechGrammarList();
speechRecognitionList.addFromString(grammar, 1);
recognition.grammars = speechRecognitionList;
recognition.lang = 'en-US';
recognition.interimResults = false;
recognition.maxAlternatives = 1;

var diagnostic = document.querySelector('.output');
var bg = document.querySelector('html');
var hints = document.querySelector('.hints');
```
This will set the grammar, language, and other settings that our speech recognizer will use so that it knows the words it's trying to detect are going to spoken in English. It also sets up other variables corresponding to HTML elements on the page that we can modify later.

## Let's add in the colors to our page.
```
var colorHTML= '';
words.forEach(function(v, i, a){
  console.log(v, i);
  colorHTML += '<span style="background-color:' + v + ';"> ' + v + ' </span>';
});

hints.innerHTML = 'Tap/click then say a color to change the background color of the app. Try '+ colorHTML + '.'
```
This code will create a list in that "hints" paragraph text that we set up before. The code loops through our colors array and adds each one to this text box with a cool background color so that the user knows what the available options are.
