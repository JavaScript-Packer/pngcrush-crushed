Portable standalone pngcrush_1_7_85_w64.exe (DOS or Linux only)	on http://sourceforge.net/projects/pmt/files/pngcrush-executables/1.7.85/ is 665.8 kB, but we can make a web version even smaller, less than third the size with the same exact functions and ours will run in any operating system with a web browser (ipods, Android, ipad, Unix, Macs, smart watches, etc)! But, we will have to port C++ source codes to large (friggin' huge) and hard to handle JavaScipt byte code (I have seen some ports over 50MB), yikes...

* Number 1 This is our original web app in bytecode (compiled C++ source code of pngcrush with Emscripten):
original-untouched.html (2.8 MB)

* Number 2 Here is a JavaScript minified version of the original web app:
embed-JS-minified.html (1.07 MB)

* Number 3 Here is the original app only compressed with LZMA:
compressed-LZMA-only.html (427 KB)

* Number 4 Here is the original minified and then LZMA compressed:
minifed-then-LZMA-compressed.html (271 KB)

# Our winner is Number 4 @ 271 kB! You can even host it on JSfiddle: http://jsfiddle.net/z7e0jthc/show/

* compressed-BZIP-only.html (443 KB),
compressed-PNG-LZF-only.html (834 KB) and compressed-GZIP-only.html (580 KB) were made on http://www.whak.ca/packer/JavaScript.htm (dragged & dropped the original HTML file in, compressed, changed eval to document write, added script tags and saved as HTML file) using the original 2,800 KB file called "original-untouched.html".

* compressed-PNG-HACK-only.html (619 KB) was made @ http://www.whak.ca/packer/PNG.htm with the original 2,8 MB sample. JavaScript source code is actually turned into an embedded (datauri) PNG image with zlib compression!

* alternate-PNG-Crush-original.html (2.1 MB) modded (rid of worker and embedded all JS to HTML) from https://github.com/richardassar/pngcrush.js is an alternate compiled version that I find actually works in Google's Chrome web browser (the other requires FireFox) and gives back smaller PNGs. The LZMA packing did not work on it, but you can see the original file (2,100 KB), minified version (956 kilobytes) and a bzip2 compressed (246 KB, almost 90% reduction) version (just JavaScript is compressed). Here is the uglified & compressed live demonstration: http://jsfiddle.net/mqezaknv/show/

* We also added 2 other demos (3D gears and Hello World). Can you believe a Hello World compiled with Emscripten is almost 500 kB?

# WTF? 
Compress huge files produced by bytecode (WebAssembly)! I embed JS/CSS into a HTML web page and then compress it on www.scriptcompress.com/LZMA.htm - DEMO: PNGcrush (C++ compiled software.exe file converted to bytecode with Emscripten) compressed to a 420KB standalone web application (originally was over 2,800 KB) on http://jsfiddle.net/8gz9qr2y/show/. Now if I embed all HTML/CSS to JavaScript and then minify I got about 1MB before any real compression, but with compression ot gets down to 275 KB compressed: http://jsfiddle.net/d6Lntnqz/show/ (less than 10% the size of the original). Gzip alone only got the original down to 619 KB, so my tool beats gzip's ass, plus my compressed files self extract and execute with any web browser (mobile phone, tablets, #Linux ,  #Mac , ipad, #Windows , #wearables  etc) without any server needed (can even run offline, use free hosting spots that do not provide server side, embed to free blogs like blogger, etc)!

# WHY? OH GOD, WHY?
Client side decompression (extracts and runs in your web browser without need of a server) is useful for places without server side compression like blogs, cell phone applications, free hosting spots, storing local self extracting/executable web pages, standalone web page applications in HTML5 and more. It can also come in handy for embedding codes to HTML, escaping codes for HTML/JavaScript, encoding code (why bother with base64 encoding that makes everything 30% bigger, use our bzip packer instead for 50% smaller), hosting where you are limited space and/or bandwidth (server and/or get twice as much on a 10MB free web host), obfuscating your source codes (major obfuscation on www.whak.ca main page, but not compressors) and much more...

# About Emscripten Compiler/Converter
* Emscripten is a type of source-to-source compiler that runs as a back end to the LLVM compiler and produces a subset of JavaScript known as asm.js. This allows applications and libraries originally designed to be run as standard executables to be integrated into client side web applications. asm.js can be compiled by browsers ahead of time meaning that the compiled programs can run much faster than those traditionally written in JavaScript.
Emscripten has been used to port, among other things, Unreal Engine 3, SQLite, and Bullet physics.
* http://kripken.github.io/emscripten-site/

# About pngcrush.exe (before porting to JS):
* Pngcrush is an optimizer for PNG (Portable Network Graphics) files. It can be run from a commandline in an MSDOS window, or from a UNIX or LINUX commandline.
* It is a free, open source command-line utility for optimizing PNG image files. It reduces the size of the file losslessly — that is, the resulting "crushed" image will have the same quality as the source image. The main purpose of pngcrush is to reduce the size of the PNG IDAT datastream by trying various combinations of compression methods and delta filters. However, pngcrush can also be used for various manipulations of PNG images, such as changing the bit depth, removing unwanted ancillary chunks, or adding certain chunks including gAMA, tRNS, iCCP, and textual chunks.
* The pixel data in a PNG file is compressed using LZ77 algorithm (which tries to find repeated byte sequences in the source data), and then further compressed with Huffman algorithm. This combination is referred to as DEFLATE compression. Before compressing, non-destructive delta filters are applied on the pixel data.
* pngcrush compresses the image with multiple different combinations and then stores the smallest of the resulting files. Since it is not possible to go through all the combinations, pngcrush uses heuristics to choose the methods to try.
* http://sourceforge.net/projects/pmt/files/
