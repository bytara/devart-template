I am overwhelmed with the technology options to be considered for the String Theory Project.

I have narrowed it down to these 3 possibilities:
    -Processing using Minim for audio inputs
    -WebGL & Web Audio API for audio inputs
    -Python with PyAudio for audio inputs

I would like my code to run on all platforms.  It may not be possible at this time, as the core feature will be the ability to access the microphone for audio input.

In testing Processing and the Minim library, I find success in Java mode, but not Javascript mode.  I am using a shim, the minim.js library to emulate the minim java library.  This has some audio support, such as playback, but no support for audio input.  I did toy with the idea to record the sound, but I don't want to lose the real-time aspect, which is important to the piece.

If using WebGL and the Web Audio API, the big limitation is with IOS and it's lack of support for WebGL.  Safari only offers partial support.  Google Chrome's modern browser, on the other hand, does offer full support and my initial testing, proves this to be true.

In researching the Python and PyAudio option, I have come across a few examples of work, but nothing that has any benefit over Processing or WebGL.  In addition, the PyAudio library is still very much in beta mode.

In conclusion, it appears that some compromise will need to be made.  I have determined that WebGL and the Audio API will give me a stable environment in which to work, enabling me to take advantage of modern web technologies, including HTML5 and also to harness the power of Google Chrome.