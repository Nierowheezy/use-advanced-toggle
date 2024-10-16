# use-advanced-toggle

![Version](https://img.shields.io/npm/v/use-advanced-toggle) ![License](https://img.shields.io/badge/license-MIT-brightgreen)

🗄️ **Advanced Toggle Hook**  
A custom React hook that allows you to easily cycle through multiple states (not limited to just true and false). Perfect for use cases such as switching themes, controlling animations, or any scenario where you need to cycle through different options.  
[View project on GitHub](https://github.com/YourUsername/use-advanced-toggle) | ![Deploy Status](https://img.shields.io/badge/deploy-status-brightgreen)

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Installation](#installation)
4. [Usage](#usage)
5. [API](#api)
6. [Testing](#testing)
7. [Contributing](#contributing)
8. [License](#license)

## Overview

`use-advanced-toggle` is a custom React hook designed to enhance the functionality of toggling between multiple states. Unlike simple boolean toggles, this hook allows you to cycle through a variety of values, making it versatile for different applications.

## Features

- Cycle through multiple states using a simple API.
- Supports any type of values, including strings and objects.
- Handles edge cases such as empty states and single states gracefully.
- Easy to integrate into both TypeScript and JavaScript projects.

## Installation

You can install `use-advanced-toggle` via npm or yarn:

```bash
npm install use-advanced-toggle
```

or

```bash
yarn add use-advanced-toggle
```

## Usage

Here’s how to use the `use-advanced-toggle` hook in your React component:

```javascript
import React from 'react';
import useAdvancedToggle from 'use-advanced-toggle';

const MyComponent = () => {
  const [color, toggleColor] = useAdvancedToggle(['red', 'green', 'blue']);

  return (
    <div>
      <p>The current color is: {color}</p>
      <button onClick={toggleColor}>Toggle Color</button>
    </div>
  );
};

export default MyComponent;
```

## API

### `useAdvancedToggle(states: any[])`

#### Parameters

- `states`: An array of states you want to toggle between (can be strings, numbers, or objects).

#### Returns

- An array where:
  - The first element is the current state.
  - The second element is a function to toggle to the next state.

#### Example

```javascript
const [currentState, toggle] = useAdvancedToggle(['state1', 'state2', 'state3']);
```

## Testing

To run tests for the `use-advanced-toggle` hook, ensure you have the testing dependencies installed:

```bash
npm install --save-dev @testing-library/react @testing-library/jest-dom
```

Then you can run your tests using:

```bash
npm test
```

### Example Test Case

Here's an example of how you might test your hook:

```javascript
import { renderHook, act } from '@testing-library/react';
import useAdvancedToggle from '../hooks/useAdvancedToggle';

describe('useAdvancedToggle', () => {
  it('should toggle between states', () => {
    const states = ['red', 'green', 'blue'];
    const { result } = renderHook(() => useAdvancedToggle(states));

    expect(result.current[0]).toBe('red');
    act(() => result.current[1]());
    expect(result.current[0]).toBe('green');
    act(() => result.current[1]());
    expect(result.current[0]).toBe('blue');
    act(() => result.current[1]());
    expect(result.current[0]).toBe('red');
  });
});
```

## Contributing

Contributions are welcome! If you have suggestions for improvements, feel free to open an issue or submit a pull request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/NewFeature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/NewFeature`)
5. Open a pull request

## License

This project is licensed under the MIT License.
