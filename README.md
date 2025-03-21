---

```markdown
# Responsive Navbar with React

This project demonstrates how to create a responsive navbar using React. The navbar includes a toggle button for mobile view, dynamic height adjustment for the links container, and social media icons. The project utilizes React hooks such as `useState` and `useRef` to manage state and interact with the DOM.

## Features

- **Toggle Button**: A button to show/hide the navigation links on smaller screens.
- **Dynamic Height Adjustment**: The height of the links container is dynamically adjusted based on the number of links.
- **Social Media Icons**: Social media icons are displayed on the right side of the navbar.
- **Responsive Design**: The navbar is fully responsive and adapts to different screen sizes.

## Technologies Used

- **React**: A JavaScript library for building user interfaces.
- **React Icons**: A library that provides popular icons for React applications.
- **CSS**: Custom styles for the navbar and its components.

## How It Works

1. **Toggle Button**:
   - The `FaBars` icon from `react-icons/fa` is used as the toggle button.
   - Clicking the button toggles the `showLinks` state, which controls the visibility of the links container.

2. **Dynamic Height Adjustment**:
   - The `useRef` hook is used to reference the `ul` element containing the links.
   - The `getBoundingClientRect()` method is used to calculate the height of the `ul` element.
   - The height of the `links-container` div is dynamically set based on the `showLinks` state.

3. **Social Media Icons**:
   - Social media icons are mapped from the `social` array and displayed on the right side of the navbar.

## Code Explanation

### State and Refs
```jsx
const [showLinks, setShowLinks] = useState(false);
const linksContainerRef = useRef(null);
const linksRef = useRef(null);
```

- `showLinks`: A state variable to control the visibility of the links container.
- `linksContainerRef`: A reference to the `links-container` div.
- `linksRef`: A reference to the `ul` element containing the links.

### Toggle Function
```jsx
const toggleLinks = () => {
  setShowLinks(!showLinks);
};
```

- This function toggles the `showLinks` state between `true` and `false`.

### Dynamic Styles
```jsx
const linkStyles = {
  height: showLinks
    ? `${linksRef.current.getBoundingClientRect().height}px`
    : '0px',
};
```

- The height of the `links-container` div is dynamically set based on the `showLinks` state.

### JSX Structure
```jsx
<nav>
  <div className='nav-center'>
    <div className='nav-header'>
      <img src={logo} className='logo' alt='logo' />
      <button className='nav-toggle' onClick={toggleLinks}>
        <FaBars />
      </button>
    </div>

    <div
      className='links-container'
      ref={linksContainerRef}
      style={linkStyles}
    >
      <ul className='links' ref={linksRef}>
        {links.map((link) => {
          const { id, url, text } = link;
          return (
            <li key={id}>
              <a href={url}>{text}</a>
            </li>
          );
        })}
      </ul>
    </div>

    <ul className='social-icons'>
      {social.map((socialIcon) => {
        const { id, url, icon } = socialIcon;
        return (
          <li key={id}>
            <a href={url}>{icon}</a>
          </li>
        );
      })}
    </ul>
  </div>
</nav>
```

- The `links-container` div's height is controlled by the `linkStyles` object.
- The `links` and `social` arrays are mapped to render the navigation links and social media icons.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/responsive-navbar.git
   ```
2. Navigate to the project directory:
   ```bash
   cd responsive-navbar
   ```
3. Install dependencies:
   ```bash
   npm install
   ```
4. Start the development server:
   ```bash
   npm start
   ```

## Live Demo

You can view a live demo of this project [here](#) (add your live demo link).

## Screenshots

### Desktop View
![Desktop View](./screenshots/desktop.png)

### Mobile View (Links Hidden)
![Mobile View (Links Hidden)](./screenshots/mobile-hidden.png)

### Mobile View (Links Visible)
![Mobile View (Links Visible)](./screenshots/mobile-visible.png)

## License

This project is licensed under the MIT License. See the [LICENSE](./LICENSE) file for details.

---

Feel free to contribute to this project by opening issues or submitting pull requests. Happy coding! 🚀


