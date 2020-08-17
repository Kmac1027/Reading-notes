# Read: 11 - Assorted Topics

## Duckett HTML

### Chapter 16: Images (p. 406-427)

- specify the dimentions of an image using CSS. this is for when you use the same sized images on several pages of your site
- images can be aligned both horizontally and vertically using CSS
- you can use a background image behind the box created by an element on a page
  1. repeat: background image is replaced both horizontally and vertically
  1. repeat-x: the image is repeated horizontally
  1. repeat-y: the image is repeated verticlly
  1. no-repeat: the image is only shown once
  1. fixed: the background image stays in the same position
  1. scroll: the background image mioves up and down as the user scrolls up and down the page
- background images can appear just once or be repeated accross the background of the box
- you can create image rollover effects by moving the background p[osition of an image
- to reduce the number of images your browser has to load, you can create image sprites

### Chapter 19: Practical Information (p. 476-492)

- SEO - Search Engine Optimization
- SEO helps visitors find your site when using search engines
- analytics tools such as Google analytics allow you to see how many people visit your site, how they find it, and what they do when they get there
  1. Brainstorm
  1. Organize
  1. Reasearch
  1. Compare
  1. Refine
  1. map
- to put your site on the web, you will need to obtain a domain name and web hosting
- FTP programs allow you to transfer files from your local computer to your web server
- you will need to use the FTP (File Transfer Protocol) to transfer all your files and assets to your hosting company
- Many companies provide platforms for blogging, email newsletters, e-commerce and other popular website tools.

### Video and Audio APIs

- The < video > and < audio > elements allow us to embed video and audio into web pages.
- controls: will add controls to the video or audio element
- source taken from developer.mozilla.org
```
<div class="player">
  <video controls>
    <source src="video/sintel-short.mp4" type="video/mp4">
    <source src="video/sintel-short.webm" type="video/webm">
    <!-- fallback content here -->
  </video>
  <div class="controls">
    <button class="play" data-icon="P" aria-label="play pause toggle"></button>
    <button class="stop" data-icon="S" aria-label="stop"></button>
    <div class="timer">
      <div></div>
      <span aria-label="timer">00:00</span>
    </div>
    <button class="rwd" data-icon="B" aria-label="rewind"></button>
    <button class="fwd" data-icon="F" aria-label="fast forward"></button>
  </div>
</div>
```
- link to article - https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Video_and_audio_APIs

### Chapter 9: Flash, Audio, and Video

- Flash is no longer supported by many browsers but is an important part of history.

[Back to code 201 notes](../201.md)