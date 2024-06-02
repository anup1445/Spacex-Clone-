
# SpaceX clone

This is a SpaceX clone website built using HTML, CSS, and JavaScript. The website emulates the design and some of the functionalities of the official SpaceX site. The main features include a responsive mobile menu, an overlay effect, and animated counters that increment when the user scrolls past a certain point.


## Documentation

[Give the website a go!](https://anup1445.github.io/Spacex-Clone-/)

## Table of Contents

1. [Installation](#installation)
2. [Usage](#usage)
3. [Code Explanation](#code-explanation)
4. [Contributing](#contributing)
5. [License](#license)

## Installation

1. Clone the repository to your local machine:
    ```bash
    git clone https://github.com/anup1445/Spacex-Clone-.git
    ```
2. Navigate to the project directory:
    ```bash
    cd spacex-clone
    ```
3. Open `index.html` in your preferred web browser to view the website.

## Usage

- Click the menu button to open and close the mobile menu.
- Scroll down the page to see the counters animate and count up.
- Scroll back up to reset the counters to zero.

## Code Explanation

### HTML Structure

- The main structure of the website is defined in `index.html`.
- Key elements include the menu button (`#menu-btn`), the overlay (`#overlay`), the mobile menu (`#mobile-menu`), and the counters (`.counter`).

### CSS Styling

- The styling is defined in `style.css` and includes responsive design rules to ensure the website looks good on all devices.
- Classes like `open`, `overlay-show`, `stop-scrolling`, and `show-menu` control the visibility and behavior of the menu and overlay.

### JavaScript Functionality

#### Mobile Menu Toggle

```javascript
function navToggle() {
  btn.classList.toggle('open');
  overlay.classList.toggle('overlay-show');
  document.body.classList.toggle('stop-scrolling');
  menu.classList.toggle('show-menu');
}
```
- Toggles classes to open/close the mobile menu and overlay, and disable/enable scrolling.

#### Scroll Event Handling

```javascript
function scrollPage() {
  const scrollPos = window.scrollY;

  if (scrollPos > 100 && !scrollStarted) {
    countUp();
    scrollStarted = true;
  } else if (scrollPos < 100 && scrollStarted) {
    reset();
    scrollStarted = false;
  }
}
```
- Checks the scroll position and triggers the `countUp` function when the user scrolls past 100 pixels.
- Resets the counters when the user scrolls back up.

#### Counter Animation

```javascript
function countUp() {
  counters.forEach((counter) => {
    counter.innerText = '0';

    const updateCounter = () => {
      const target = +counter.getAttribute('data-target');
      const c = +counter.innerText;
      const increment = target / 100;

      if (c < target) {
        counter.innerText = `${Math.ceil(c + increment)}`;
        setTimeout(updateCounter, 10);
      } else {
        counter.innerText = target;
      }
    };

    updateCounter();
  });
}
```
- Initializes counters to zero and updates their values incrementally until they reach the target value.
- Uses `setTimeout` to create a smooth counting animation.

#### Reset Counters

```javascript
function reset() {
  counters.forEach((counter) => (counter.innerHTML = '0'));
}
```
- Resets all counters to zero when called.

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit them (`git commit -am 'Add new feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Create a new Pull Request.



---

Feel free to customize the sections and content as per your project's specific details and requirements.


