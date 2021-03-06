*This repository is a mirror of the [component](http://component.io) module [xcoderzach/touch-velocity](http://github.com/xcoderzach/touch-velocity). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/xcoderzach-touch-velocity`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
#touch-velocity

  Calculate (nearly) instantaneous velocity for a thing. 
Things like touch or mouse events.  Calculating the velocity 
by looking at the last two events is wildly inaccurate, since 
the time difference between the two events being fired is often &lt; 1ms.

  This library smooths that out a bit by calculating over the last
100ms.

##example

```javascript
  var Velocity = require('touch-velocity')
    , velocity = new Velocity
    , touchTarget = document.querySelector('#touch-target')
  
  touchTarget.addEventListener('touchmove', function(evt) {
    velocity.updatePosition(evt.touches[0].pageX)
  })

  touchTarget.addEventListener('touchend', function(evt) {
    console.log(velocity.getVelocity())
  })
```

##api

###updatePosition(newPosition)

  Updates the current position of the thing whose velocity you are tracking.
You should do this any time you know that the thing's position has changed i.e. 
a touch event.

###getVelocity()

  Gets the (nearly) instantaneous velocity of the thing you're tracking.
