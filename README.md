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

#Javascript
We'll be using a built-in Chrome API to do the speech recognition. In order to call it, put this at the top of your Javascript file: 
```
var SpeechRecognition = SpeechRecognition || webkitSpeechRecognition
var SpeechGrammarList = SpeechGrammarList || webkitSpeechGrammarList
var SpeechRecognitionEvent = SpeechRecognitionEvent || webkitSpeechRecognitionEvent
```
This creates the objects that we'll use to store and track the user's speech.
