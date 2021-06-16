# Custom VS Code snippets for Frontend Development

JavaScript and React snippets in ES7+ for [VS Code](https://code.visualstudio.com/)

## Installation

Copy the `frontend-snippets` folder to `~/.vscode/extensions` and reload VS Code.

## Supported languages (file extensions)

- JavaScript (.js)
- JavaScript React (.jsx)
- TypeScript (.ts)
- TypeScript React (.tsx)

## Snippets
### `rcc`

```typescript
/**
 * Module dependencies.
 */
import { color, media, units } from '@untile/react-components';
import { ifProp, prop } from 'styled-tools';
import React, { ReactElement } from 'react';
import styled, { css } from 'styled-components';

/**
 * `Props` type.
 */

type Props = {
  className?: string
};

/**
 * `Wrapper` styled component.
 */

const Wrapper = styled.div`

`;

/**
 * `ComponentName` component.
 */

const ComponentName = (props: Props): ReactElement => {
  const { className } = props;

  return (
    <Wrapper className={className} />
  );
};

/**
 * Export `ComponentName` component.
 */

export default ComponentName;
```

### `useState`

```typescript
  const [state, setstate] = useState<>();
```

### `useEffect`

```typescript
useEffect(() => {

}, []);
```

### `useCallback`

```typescript
useCallback(() => {

}, []);
```

### `useMemo`

```typescript
useMemo(() => {

}, []);
```

### `styled`

```typescript
/**
 * `` styled component.
 */

const  = styled.`

`;
```

### `typ`

```typescript
/**
 * `TypeName` type.
 */

type TypeName = {

};
```

### `imp`

```typescript
import {  } from '';
```

### `dcc`

```typescript
/**
 * ``.
 */
```
