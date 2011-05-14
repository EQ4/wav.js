wav.js
======

Description
-----
wav.js is a javascript library to parse headers of WAVE files following the RIFF specification.

It also supports slicing uncompressed PCM files into smaller files - which can be handy if you don't want to load the whole file into memory to play just a small chunk.

Usage:
----

* Read format header

    var wavFile = new wave(in Blob blob);
    wavFile.onloadend = function () {
        // 'this' refers to the wav instance
        console.log(this);
    }; 

* Slice file into a smaller wav chunk

    // returns the first 30 seconds 
    wavFile.slice(0, 30, success); 

    // returns a 60 second chunk, starting 30 seconds in
    wavFile.slice(30, 60, success); 

The success callback is passed the resulting slice as an ArrayBuffer - this buffer represents a new WAVE file of the slice (with WAVE headers).


Example
-----

* Read format of file: http://jsbin.com/ffdead-audio-wav/231/


Limitations
-----
wav.js only supports the Canonical Wave format for now: http://www.lightlink.com/tjweber/StripWav/Canon.html
This assumes that the sample data chunk starts directly after the file header.