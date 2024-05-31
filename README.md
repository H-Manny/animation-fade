# Animation Fade In/Out Function
Fade in/out source code written in vanilla JS.

## Javascript
### Fade In
```javascript
/**
 * Fades in an element by gradually increasing its opacity to 1.
 *
 * @param {HTMLElement} element - The element to fade in.
 * @param {string} [display="block"] - The display style to apply to the element. Defaults to "block".
 * @param {number} duration - The duration of the fade-out animation in milliseconds.
 */
const fadeInElement = (element, display, duration) => {
  const startTime = performance.now();
  element.style.display = display || "block";

  function animate(currentTime) {
    const elapsedTime = currentTime - startTime;
    const opacity = elapsedTime / duration;
    if(opacity > 1) {
      element.style.opacity = 1;
    } else {
      element.style.opacity = opacity;
      requestAnimationFrame(animate);
    }
  }

  animate(performance.now());
};
```
### Fade Out
```javascript
/**
 * Fades out an element by gradually decreasing its opacity to 0.
 *
 * @param {HTMLElement} element - The element to fade out.
 * @param {number} duration - The duration of the fade-out animation in milliseconds.
 */
const fadeOutElement = (element, duration) => {
  const startTime = performance.now();

  /**
   * Animation function that gradually decreases the opacity of the element.
   *
   * @param {DOMHighResTimeStamp} currentTime - The current time of the animation.
   */
  function animate(currentTime) {
    const elapsedTime = currentTime - startTime;
    const opacity = 1 - (elapsedTime / duration);

    if (opacity > 0) {
      element.style.opacity = opacity;
      requestAnimationFrame(animate);
    } else {
      element.style.display = 'none';
    }
  }

  requestAnimationFrame(animate);
};
```
### Usage
```javascript
// Example
const element = document.querySelector('.foo');

fadeInElement(element, 'block', 3000);  // Display over 3 seconds
fadeOutElement(element, 3000);  // Hide over 3 seconds
```
