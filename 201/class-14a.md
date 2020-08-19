# Read: 14a - CSS Transforms, Transitions, and Animations

## Transforms - https://learn.shayhowe.com/advanced-html-css/css-transforms/

- transform - general layout techniques can be revisited with alternative ways to size, position, and change elements.

### Transform Syntax

```
div {
  -webkit-transform: scale(1.5);
     -moz-transform: scale(1.5);
       -o-transform: scale(1.5);
          transform: scale(1.5);
}
```
- 2D Transforms - works on x and y axis
- html
```
<figure class="box-1">Box 1</figure>
<figure class="box-2">Box 2</figure>
```
- CSS
```
.box-1 {
  transform: rotate(20deg);
}
.box-2 {
  transform: rotate(-55deg);
}
```
- 2D Scale - Using the scale value within the transform property allows you to change the appeared size of an element. The default scale value is 1, therefore any value between .99 and .01 makes an element appear smaller while any value greater than or equal to 1.01 makes an element appear larger.
- It is possible to scale only the height or width of an element using the scaleX and scaleY values. The scaleX value will scale the width of an element while the scaleY value will scale the height of an element. To scale both the height and width of an element but at different sizes, the x and y axis values may be set simultaneously. To do so, use the scale transform declaring the x axis value first, followed by a comma, and then the y axis value.
- 2D Translate - The translate value works a bit like that of relative positioning, pushing and pulling an element in different directions without interrupting the normal flow of the document. Using the translateX value will change the position of an element on the horizontal axis while using the translateY value will change the position of an element on the vertical axis.
- 2D Skew - The last transform value in the group, skew, is used to distort elements on the horizontal axis, vertical axis, or both. The syntax is very similar to that of the scale and translate values. Using the skewX value distorts an element on the horizontal axis while the skewY value distorts an element on the vertical axis. To distort an element on both axes the skew value is used, declaring the x axis value first, followed by a comma, and then the y axis value.%p
- you can combine transforms
- perspective - In order for three-dimensional transforms to work the elements need a perspective from which to transform. The perspective for each element can be thought of as a vanishing point, similar to that which can be seen in three-dimensional drawings.


- 3D Transforms - we use three new transform values, including rotateX, rotateY, and rotateZ.
Using the rotateX value allows you to rotate an element around the x axis, as if it were being bent in half horizontally. Using the rotateY value allows you to rotate an element around the y axis, as if it were being bent in half vertically. Lastly, using the rotateZ value allows an element to be rotated around the z axis.
- 

## Transitions & Animations - https://learn.shayhowe.com/advanced-html-css/transitions-animations/

- for a transition to take place, an element must have a change in state, and different styles must be identified for each state. The easiest way for determining styles for different states is by using the :hover, :focus, :active, and :target pseudo-classes.
- Transitional Property - The transition-property property determines exactly what properties will be altered in conjunction with the other transitional properties. By default, all of the properties within an element’s different states will be altered upon change. However, only the properties identified within the transition-property value will be affected by any transitions.
- It is important to note, not all properties may be transitioned, only properties that have an identifiable halfway point. Colors, font sizes, and the alike may be transitioned from one value to another as they have recognizable values in-between one another. The display property, for example, may not be transitioned as it does not have any midpoint. A handful of the more popular transitional properties include the following.
- Transition Duration - The duration in which a transition takes place is set using the transition-duration property. The value of this property can be set using general timing values, including seconds (s) and milliseconds (ms). These timing values may also come in fractional measurements, .2s for example.
- Transition Delay
- ANIMATIONS - use when more control is needed over transitions

### 8 SIMPLE CSS3 TRANSITIONS THAT WILL WOW YOUR USERS - http://www.webdesignerdepot.com/2014/05/8-simple-css3-transitions-that-will-wow-your-users/

1. Fade in
```
.fade
{
        opacity:0.5;
}
.fade:hover
{
        opacity:1;
}
```
1. Change color
```
.color:hover
{
        background:#53a7ea;
}
```
1. Grow and Shrink
```
.grow:hover
{
        -webkit-transform: scale(1.3);
        -ms-transform: scale(1.3);
        transform: scale(1.3);
}

.shrink:hover
{
        -webkit-transform: scale(0.8);
        -ms-transform: scale(0.8);
        transform: scale(0.8);
}
```
1. Rotate Elements
```
.rotate:hover
{
        -webkit-transform: rotateZ(-30deg);
        -ms-transform: rotateZ(-30deg);
        transform: rotateZ(-30deg);
}
```
1. Square to circle
```
.circle:hover
{
        border-radius:50%;
}
```
1. 3D shadow
```
.threed:hover
{
        box-shadow:
                1px 1px #53a7ea,
                2px 2px #53a7ea,
                3px 3px #53a7ea;
        -webkit-transform: translateX(-3px);
        transform: translateX(-3px);
}
```
1. Swing
```
@-webkit-keyframes swing
{
    15%
    {
        -webkit-transform: translateX(5px);
        transform: translateX(5px);
    }
    30%
    {
        -webkit-transform: translateX(-5px);
       transform: translateX(-5px);
    } 
    50%
    {
        -webkit-transform: translateX(3px);
        transform: translateX(3px);
    }
    65%
    {
        -webkit-transform: translateX(-3px);
        transform: translateX(-3px);
    }
    80%
    {
        -webkit-transform: translateX(2px);
        transform: translateX(2px);
    }
    100%
    {
        -webkit-transform: translateX(0);
        transform: translateX(0);
    }
}
@keyframes swing
{
    15%
    {
        -webkit-transform: translateX(5px);
        transform: translateX(5px);
    }
    30%
    {
        -webkit-transform: translateX(-5px);
        transform: translateX(-5px);
    }
    50%
    {
        -webkit-transform: translateX(3px);
        transform: translateX(3px);
    }
    65%
    {
        -webkit-transform: translateX(-3px);
        transform: translateX(-3px);
    }
    80%
    {
        -webkit-transform: translateX(2px);
        transform: translateX(2px);
    }
    100%
    {
        -webkit-transform: translateX(0);
        transform: translateX(0);
    }
}


.swing:hover
{
        -webkit-animation: swing 1s ease;
        animation: swing 1s ease;
        -webkit-animation-iteration-count: 1;
        animation-iteration-count: 1;
}
```
1. Inset border
```
.border:hover
{
        box-shadow: inset 0 0 0 25px #53a7ea;
}
```

## 6 button animated - https://codepen.io/retyui/pen/ByoaXV

- HTML
```
<div class="group">
		<button class="blam">Blam</button>
		<button style="-webkit-animation-delay: .3s;animation-delay: .3s;" class="syke">Syke</button>
		<button style="-webkit-animation-delay: .6s;animation-delay: .6s;" class="later">Later</button>
	</div>
  ```
- CSS
```
@import url(https://fonts.googleapis.com/css?family=Droid+Sans:700);
		*{
			margin: 0;
			padding: 0;
			box-sizing: border-box;
			transition: all .1s;
		}
		body{
		background-color: #424242;
			font-family: 'Droid Sans', sans-serif;
		}
		.group{
			text-align: center;
			margin: 20px auto;
		}
		.group button{
			margin-top: 10px;
		}
		button{
/*			box-sizing: border-box;*/
			background: NONE;
			border: none;
			outline: none;
			border-radius: 3px;
			padding: 15px 70px;
			color:white;
			text-transform: uppercase;
			font-weight: 700;
			text-shadow: 0 1px 3px rgba(0, 0, 0, 0.41);
			box-shadow: 0 3px 0 0 #383838;
			border:3px solid transparent;
			
		
			animation: pulse 1s linear infinite alternate;
			-webkit-animation: pulse 1s linear infinite alternate;
		}
		.active,
		button:active{
			background-image: linear-gradient(rgba(0,0,0,.1) 13%, transparent 13%,transparent);
			box-shadow: 0 1px 0 0 #383838;
			color: rgba(0, 0, 0,.45);
			text-shadow: none;
			
			
			-webkit-animation-play-state: paused; 
    	animation-play-state: paused;
		}
		button:focus,
		button:hover{
			-webkit-animation-play-state: paused; 
    	animation-play-state: paused;
		}
		
		
		.blam:focus,
		.blam:hover{
			background-color:#0097bd;
		}
		.blam{
			background-color:#00bff0;
			border-color: #00bff0;
		}
		
		.syke:focus,
		.syke:hover{
			background-color:#ad4e4e;
		}
		.syke{
			background-color:#e06464;
			border-color:#e06464;
		}
		
		.later:focus,
		.later:hover{
			background-color:#7c8b8f;
		}
		.later{
			background-color:#a8bdc2;
			border-color:#a8bdc2;
		}
		
		@-webkit-keyframes pulse {
			100% {
				transform: translateY(6.9px); 
			} 
		}

		@keyframes pulse {
			100% {
				transform: translateY(6.9px); 
			} 
		}
```

## CSS3 Animation Key frame

- HTML
```
<h1>CSS3 Animations: Keyframes</h1>


<div class="exampleDiv">
  <div class="ball" style="-webkit-animation: bouncing 2s 15 linear;-moz-animation: bouncing 2s 15 linear;"></div>
</div>


<!-- WhatsHelp.io widget -->
<script type="text/javascript">
    (function () {
        var options = {
            facebook: "220186546416", // Facebook page ID
            company_logo_url: "//storage.whatshelp.io/widget/d2/d2db/d2dbaa07f22d96b7ad8426beb00493d0/20031613_10154783116346417_1007255058190022230_n.png", // URL of company logo (png, jpg, gif)
            greeting_message: "Hello, how may I help you? Just send us a message now to get assistance.", // Text of greeting message
            call_to_action: "Message me", // Call to action
            position: "right", // Position may be 'right' or 'left'
        };
        var proto = document.location.protocol, host = "whatshelp.io", url = proto + "//static." + host;
        var s = document.createElement('script'); s.type = 'text/javascript'; s.async = true; s.src = url + '/widget-send-button/js/init.js';
        s.onload = function () { WhWidgetSendButton.init(host, proto, options); };
        var x = document.getElementsByTagName('script')[0]; x.parentNode.insertBefore(s, x);
    })();
</script>
```
- CSS
```
@import url(https://fonts.googleapis.com/css?family=Montserrat:700);
body {
  background-color: #ffcc46;
}

::-webkit-scrollbar {
    width: 8px;
}

::-webkit-scrollbar-thumb {
    background: rgba(0,0,0,0.12);
}

::-webkit-scrollbar-track {
    visibility: hidden;
}

h1 {
  font-family: 'Montserrat', helvetica, arial;
  sans-serif;
  margin: 20px;
}

.exampleDiv {
  height: 200px;
  width: 200px;
  border: 1px solid rgba(0, 0, 0, 0.1);
  float: left;
  margin: 20px;
  text-align: center;
  position: relative;
  background-color: #ffffff;
  border-radius: 4px;
}

.ball {
  position: absolute;
  height: 20px;
  width: 20px;
  border-radius: 10px;
  background-color: #c0392b;
}

@-webkit-keyframes bouncing {
  40%, 70%, 90% {
    bottom: 0;
    -webkit-animation-timing-function: ease-out;
  }
  0% {
    bottom: 200px;
    left: 0;
    -webkit-animation-timing-function: ease-in;
  }
  55% {
    bottom: 50px;
    -webkit-animation-timing-function: ease-in;
  }
  80% {
    bottom: 25px;
    -webkit-animation-timing-function: ease-in;
  }
  95% {
    bottom: 10px;
    -webkit-animation-timing-function: ease-out;
  }
  100% {
    left: 110px;
    bottom: 0;
    -webkit-animation-timing-function: ease-out;
  }
  @-moz-keyframes bouncing {
    40%, 70%, 90% {
      bottom: 0;
      -webkit-animation-timing-function: ease-out;
    }
    0% {
      bottom: 200px;
      left: 0;
      -webkit-animation-timing-function: ease-in;
    }
    55% {
      bottom: 50px;
      -webkit-animation-timing-function: ease-in;
    }
    80% {
      bottom: 25px;
      -webkit-animation-timing-function: ease-in;
    }
    95% {
      bottom: 10px;
      -webkit-animation-timing-function: ease-out;
    }
    100% {
      left: 110px;
      bottom: 0;
      -webkit-animation-timing-function: ease-out;
    }
```
## 404 - https://codepen.io/kieranfivestars/pen/MYdQxX
- HTML
```
<h1>4</h1>
<h1>0</h1>
<h1>4</h1>
```
-CSS
```
body {
  margin:0;
  font-family:sans-serif;
  color:#f25252;
  background:#f7f7f7;
}
h1 {
  font-size:11rem;
  position:absolute;
  transform:translate(-50%,-50%);
  margin:0;
}
h1:nth-of-type(1){
  animation: range 4s infinite;
}
h1:nth-of-type(2){
  left:50%;
  top:50%;
  animation: size 4s infinite;
}
h1:nth-of-type(3){
  animation: range2 4s infinite;
}
@keyframes range {
  0%  {left:42%;top:50%;font-size:11rem;}
  25% {left:50%;top:40%;font-size:4.5rem;}
  50% {left:58%;top:50%;font-size:11rem;}
  75% {left:50%;top:60%;font-size:4.5rem;}
  100%{left:42%;top:50%;font-size:11rem;}
}
@keyframes range2 {
  0%  {left:58%;top:50%;font-size:11rem;}
  25% {left:50%;top:60%;font-size:4.5rem;}
  50% {left:42%;top:50%;font-size:11rem;}
  75% {left:50%;top:40%;font-size:4.5rem;}
  100%{left:58%;top:50%;font-size:11rem;}
}
@keyframes size {
  0%  {font-size:11rem;}
  25% {font-size:26rem;}
  50% {font-size:11rem;}
  75% {font-size:26rem;}
  100%{font-size:11rem;}
}
```
## Pure CSS Bounce Animation - https://codepen.io/dp_lewis/pen/gCfBv
- HTML
```
	<div class="animation animation-1">
		<div class="ball"></div>
	</div>
	<div class="animation animation-2">
		<div class="ball"></div>
	</div>
	<div class="animation animation-3">
		<div class="ball"></div>
	</div>	
```
- CSS
```
@keyframes balltransform {
	0% {
		border-radius:50%;
		height:100%;
		width:60%;
	}
	29% {
		height:100%;
		width:60%;
	}
	30% {
		height:50%;
		width:100%;
	}
	40% {
		height:80%;
		width:80%;
	}
	59% {
		height:100%;
		width:60%;
	}
	60% {
		height:50%;
		width:100%;
		border-radius:50%;
		transform:rotate(0);
	}
	100% {
		height:80%;
		width:80%;
		border-radius:0;
		transform: rotate(-180deg);
	}
}

@keyframes ballbounce {
	/* up */
	0% {
		top:-30%;
		animation-timing-function: ease-in;
	}
	/* floor */
	30% {
		top:80%;
		animation-timing-function: ease-out;
	}
	/* up */
	40% {
		top: 20%;
	}
	/* up */
	45% {
		top:17%;
		animation-timing-function: ease-in;
	}
	/* floor */
	60% {
		top:80%;
		animation-timing-function: ease-out;
	}
	/* up */
	75% {
		top:30%;
	}
	90% {
		top:25%;
		animation-timing-function: ease-in;
	}
	/* floor */
	100% {
		top:110%;
		animation-timing-function:ease-out;
	}
}

@keyframes scalemask {
	0% {
		mask-size:0%;
	}
	65% {
		mask-size:0%;
	}
	78%,100% {
		mask-size:300%;
	}
}

@keyframes scalemask2 {
	0% {
		-webkit-mask-size:0%;
	}
	83% {
		-webkit-mask-size:0%;
	}
	100% {
		-webkit-mask-size: 300%;
	}
}

* {
	box-sizing:border-box;
}

body {
	padding:0;
	margin: 0;
}

/* Ball -------------------- */
.ball {
	width:5rem;
	height:5rem;
	left:50%;
	position:absolute;
	z-index:1;
	margin-left:-2.5rem;
	animation:ballbounce 4s 1s infinite;
	animation-fill-mode:both;
}

.ball:after {
	content:" ";
	color:#fff;
	display:block;
	margin:auto;
	border-radius:50%;
	background:#fff;
	width:100%;
	height:100%;
	animation: balltransform 4s 1s infinite;
}

/* Animation containers -------------------- */
.animation {
	background:#297acb;
	height:100vh;
	width:100vw;
	position:relative;
	z-index:1;
}

.animation-2,
.animation-3 {
	position:absolute;
	top:0;
	left:0;
	-webkit-mask-size:0;
	-webkit-mask-image:radial-gradient(circle closest-side,black 0%,black 90%,rgba(255,255,255,0) 92%);
	-webkit-mask-repeat:no-repeat;
	-webkit-mask-position:center center;
	animation-fill-mode:both;
}

.animation-2 {
	background:purple;
	animation:scalemask 4s 1s infinite;
}

.animation-3 {
	animation:scalemask2 4s 1s infinite;
}

.animation-2 .ball:after {
	background: #297acb;
}
```
[Back to code 201 notes](../201.md)