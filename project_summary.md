# String Theory Project
Using technology to explore the hidden powers beneath the strings.


## Authors
- Tara Manuel, https://github.com/bytara

## Description
The String Theory Project is an interactive art installation that merges music, sound, code and technology. The String Theory Project installation will use a traditional stringed instrument, the harp, known for it's healing vibrations, to map and visualize sound waves.  The emphasis will be on connections to the body and mind.

The project will investigate the transformative powers of harp sounds, gaining insights into sound energies.  Mathematics, music, vibration, visualization and mapping sound techniques will recast harp vibrations into something physical, something we can see.

![quote](/project_images/harpquote_sm.jpg?raw=true "Harp Quote")

The technology behind the String Theory Project is a Google Chrome App, written with HTML, Javascript and CSS.

I am an artist, coder, mathematician and most recently, harpist.  When I first heard the harp instrument live, I was personally touched by the angelic sounds of the instrument, giving inspiration to the project and excitement to it's development.


## Link to Prototype
[String Theory Project](http://taramanuel.com/stringtheory/index.html "String Theory Prototype")
This prototype demonstrates the working technology behind the String Theory Project.  The final project will be a projection of this application, using live audio input.  The room will contain 12 fiber strings, hung floor to ceiling.  The projection will be through the strings, adding dimension and reflection.

## Example Code
Using the Web Audio API, determine compatibility for live input. If all looks good, get the input stream and create an analyzer.
  ```
 function getLiveInput(){
     if(navigator.webkitGetUserMedia){
         if(isplaying){source.stop(0);}
         navigator.webkitGetUserMedia({audio:true}, onStream, onStreamError);
     }
     else {
       alert("Sorry, your browser does not support the Web Audio API for live input.  Please enjoy the experience using the demo audio.");
     }
 }
 function onStream(stream){
     input=audioContext.createMediaStreamSource(stream);
     analyser=audioContext.createAnalyser();
     analyser.fftSize = 2048;
     input.connect(analyser);
     requestAnimationFrame(render);
 }

  ```
 Use data from the analyzer to create visualizations and render to the canvas.
   ```
  function draw(){
      analyser.getByteTimeDomainData( buf );
      autoCorrelate( buf, audioContext.sampleRate );
      var freqs = new Uint8Array(analyser.frequencyBinCount);
      analyser.getByteFrequencyData(freqs);
      for (var i = 0; i < analyser.frequencyBinCount; i++) {
        drawContext1.beginPath();
        drawContext2.beginPath();
        drawContext1.arc(i * C_WIDTH+C_WIDTH, magnitude,B_WIDTH-2,0,2*Math.PI);
        drawContext2.arc(width-i * C_WIDTH-C_WIDTH, magnitude,B_WIDTH-2,0,2*Math.PI);
        drawContext1.fill();
        drawContext2.fill();
      }

function render(){
    drawContext1.clearRect(0,0,width,height);
    drawContext2.clearRect(0,0,width,height);
    draw();
    requestAnimationFrame(render);
}
   ```


