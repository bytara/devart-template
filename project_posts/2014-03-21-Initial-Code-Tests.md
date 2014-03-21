Code Snippets

First, I'd like to be able to get the audio input functioning, since this is the key component to the piece.  The main function getUserMedia() will only be available on select platforms so I will need to perform a check and respond accordingly.  I will begin by testing for Chrome only and work from there.  For iOS and browsers that do not support Web Audio, I will create sound recordings as well as enable the user to load their own files.  Additionally, I would like to build an interactive virtual harp, but this is secondary.

I have successfully been able to access the microphone and have confirmed that it is working.

I am using the following code, initially testing with Chrome.  Firefox currently work as well.
<pre>
<code>     window.addEventListener('load', onload, false);
           document.addEventListener('webkitvisibilitychange',onVisibilityChange);
           window.AudioContext = window.AudioContext || window.webkitAudioContext;

           function onload(){
               //test compatibility
               if(navigator.webkitGetUserMedia){
                   navigator.webkitGetUserMedia({audio:true}, onStream, onStreamError)
               }
               else{
                   //load something else
               }
           }

           function onStream(stream){
               var context=new AudioContext();
               var input=context.createMediaStreamSource(stream);
               var filter=context.createBiquadFilter();
               filter.frequency.value=60.0;
               filter.type=filter.NOTCH;
               filter.Q=10.0;
               var analyser=context.createAnalyser();
               input.connect(filter);
               filter.connect(analyser);
               //add code to analyze & process audio
           }

           function onStreamError(e){
               console.error(e);
           }

           function onVisibilityChange(){
               if(document.webkitHidden){
                   source.stop(0);
               }
               else{
                   source.start(0);
               }
           }
</code>
</pre>