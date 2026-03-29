---
title: "Styled Components Example"
tag: "programming"
---

# Styled Components Example with ReactJS

_January 19, 2022 by Ulan Rakymzhanov_

Styled Components is one of the great ways to apply CSS into React apps. So we are going to do that in this blog.

Prerequisites:

- ReactJS, CSS, JS, HTML knowledge is required.

**Caveats:** We want to show/hide progress bar depending on some condition.

For that reason, lets create 4 cards data and store it inside an array.

I am going to use **[react-icons](https://react-icons.github.io/react-icons/icons?name=bs)** for our icons.

Create a new app:

- `npx create-react-app <app-name>`

Install required libraires:

- `npm install styled-components react-icons`

Cleanup `App.js` and import required icons on top:

```js
import {
  BsBadgeVrFill,
  BsBadge4KFill,
  BsCollectionPlayFill,
  BsBadgeHdFill,
} from "react-icons/bs";
```

Then create our 4 data for cards:

```js
const cards = [
  { id: 1, icon: <BsBadge4KFill />, stats: 278, comment: "New Posts", progresbar: true, value: 80 },
  { id: 2, icon: <BsBadgeVrFill />, stats: 156, comment: "New Posts", progresbar: true, value: 50 },
  { id: 3, icon: <BsCollectionPlayFill />, stats: "64.89%", comment: "Bounce Rate", progresbar: true, value: 10 },
  { id: 4, icon: <BsBadgeHdFill />, stats: 423, comment: "Total Visits", progresbar: false, value: 90 },
];
```

Then create a `styled.js` file inside **src** folder and put below code inside:

```js
import styled, { createGlobalStyle } from "styled-components";

export const GlobalStyle = createGlobalStyle`
  svg { height: 60px; width: 60px; }
`;

export const AppDiv = styled.div`
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin-top: 40px;
`;
```

To use **GlobalStyle** import it inside `index.js` and put below `<App/>`:

```js
ReactDOM.render(
  <React.StrictMode>
    <App />
    <GlobalStyle />
  </React.StrictMode>,
  document.getElementById("root")
);
```

Create `components/Card.js` and `components/styled.js`:

```js
import styled from "styled-components";

export const CardContainer = styled.div`
  border: 1px solid;
  height: auto;
  width: 300px;
  text-align: center;
  padding: 20px;
`;
export const Stats = styled.h1`color: darkgreen; margin-bottom: 0;`;
export const Comment = styled.p`color: gray; margin-top: 5px;`;
export const ProgressBar = styled.progress`
  width: 100%;
  opacity: ${(props) => props.progresbar === false && 0};
`;
```

As you can see `ProgressBar` opacity depends on the **progresbar prop**. Pass it inside `Card.js`:

```js
function Card({ card }) {
  return (
    <CardContainer>
      <div>{card.icon}</div>
      <Stats>{card.stats}</Stats>
      <Comment>{card.comment}</Comment>
      <ProgressBar progresbar={card.progresbar} value={card.value} max="100" />
    </CardContainer>
  );
}
export default Card;
```

As a final word — you can practice shifting the **orders** of Icon and Stats/Comment using the `left: true/false` boolean from the data above.
