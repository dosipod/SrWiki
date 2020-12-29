In order to be able to use leds[i] in WLED, we add the following global variable:

```
uint32_t ledData[MAX_LEDS];                 // See const.h for a value of 1500.
```

In the routines, we are adding:

```
  CRGB *leds = (CRGB*) ledData;
```

This works with SEGMENTS in that two different animations don't clash. The questions I have are:

* Am I lucky that they don't clash, in that maybe one routine just overwrites the other in the same memory space?
* Or are we creating a new array of [MAX_LEDS] for each segment.

If the latter, would that not be very inefficient?

If inefficient, would it not make more sense to use:

```
 if (!SEGENV.allocateData(sizeof(CRGB)*SEGLEN)) return mode_static(); //Allocates based on the size of a CRGB
  CRGB* leds = reinterpret_cast<CRGB*>(SEGENV.data);

  // leds[i] code in here

  setPixels(leds);
  return FRAMETIME;
```

That being said, an associate with embedded system support says that dynamic memory allocation is NOT a good thing to perform on embedded systems.

Thoughts?  