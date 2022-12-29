   
  Custom **debounce throttle function** to avoid redundant checking.
  
  
  When still having changes in 2 seconds, start throttled checking every 1 second
  instead of check based on input
  
  
  ```js
  debounceThrottleUpdateChecking = () => {
    /* When a new cycle of changes started */
    if (!this.isUpdateRecently) {
      // console.log("start modify");

      this.isUpdateRecently = true;
      this.shouldSkipChecking = false;

      this.debounceTimeout = setTimeout(() => {
        this.isUpdateRecently = false;
        // console.log("end by start modify");
      }, 2000);
    } else {
      // console.log("still modify");
      this.shouldSkipChecking = true;

      if (!this.isCheckingThrottled) {
        this.shouldSkipChecking = false;

        // console.log("should do checking");

        this.isCheckingThrottled = true;

        this.throttleTimeout = setTimeout(() => {
          this.isCheckingThrottled = false;
        }, 1000);
      }

      clearTimeout(this.debounceTimeout);

      this.debounceTimeout = setTimeout(() => {
        this.isUpdateRecently = false;
        // console.log("end by still modify");
      }, 2000);
    }
  };
```
