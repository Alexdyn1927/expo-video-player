# Expo Video Player: Flexible and Customizable Video Playback for React Native

## Project Overview

Expo Video Player is a highly customizable and flexible video player library designed specifically for Expo and React Native applications. It provides developers with a robust solution for embedding and controlling video playback in mobile apps with minimal configuration and maximum flexibility.

### Key Features

- **Easy Integration**: Seamlessly works with Expo and React Native projects
- **Comprehensive Customization**: Extensive styling and configuration options
- **Multiple Video Sources**: Supports both remote URI and local video files
- **Flexible Controls**: Configurable playback controls including play/pause, fullscreen, and volume
- **Responsive Design**: Adapts to different screen sizes and orientations

### Core Capabilities

- Autoplay and manual play/pause functionality
- Fullscreen mode with custom enter/exit behaviors
- Volume control and mute options
- Custom styling for video background, controls, and icons
- Support for both streaming and local video sources
- Resize mode configuration
- Optional custom header and icon support

This library simplifies video integration in mobile applications, offering developers a powerful yet intuitive tool for creating rich media experiences with minimal overhead.

## Getting Started, Installation, and Setup

### Prerequisites
- React Native project
- Expo SDK 38 or higher
- Node.js and Yarn/npm

### Installation
Install the package and its peer dependencies using your preferred package manager:

```bash
# Using Yarn
yarn add expo-video-player
expo install expo-av @react-native-community/slider

# Using npm
npm install expo-video-player
expo install expo-av @react-native-community/slider
```

### Quick Start
Import the `VideoPlayer` component and add it to your React Native application:

```typescript
import { ResizeMode } from 'expo-av'
import VideoPlayer from 'expo-video-player'

function MyComponent() {
  return (
    <VideoPlayer
      videoProps={{
        shouldPlay: true,
        resizeMode: ResizeMode.CONTAIN,
        source: {
          uri: 'https://example.com/sample-video.mp4',
        },
      }}
    />
  )
}
```

### Development
To set up the project for development:

1. Clone the repository
2. Install dependencies:
   ```bash
   yarn install
   ```

3. Build the project:
   ```bash
   yarn build
   ```

### Project Build
To build the production version:
```bash
yarn build
```

This will compile TypeScript files and generate JavaScript files in the `dist` directory.

### Compatibility
| Library Version | Expo SDK Version |
|----------------|------------------|
| 2.1.x | >= SDK 45 |
| 2.x.x | >= SDK 38 |

### Important Notes
- The `source` prop is required in `videoProps`
- Refer to the Props section for extensive configuration options
- Check the [example app](https://github.com/ihmpavel/expo-video-player/tree/master/example-app) for advanced usage examples

## API Reference

### Main Component

#### `VideoPlayer`

A React component for rendering and controlling video playback with customizable UI and behavior.

##### Props

The `VideoPlayer` component accepts a comprehensive set of configuration props:

###### Required Props
- `videoProps` (Object): Extends `expo-av` VideoProps with additional configuration
  - Includes a reference to the underlying video component
  - Supports all standard `expo-av` video properties

###### Optional Props
- `errorCallback` (Function): Called when an error occurs 
  - Receives an `ErrorType` object with details about the error
- `playbackCallback` (Function): Triggered on playback status changes
  - Receives an `AVPlaybackStatus` object
- `defaultControlsVisible` (Boolean): Initial visibility of player controls
- `timeVisible` (Boolean): Toggle display of video time
- `header` (ReactNode): Custom header component to be displayed
- `autoHidePlayer` (Boolean): Automatically hide controls
- `textStyle` (TextStyle): Custom styling for text elements
- `style` (Object): Customize video player dimensions and colors
  - `width`: Player width
  - `height`: Player height
  - `videoBackgroundColor`: Background color of video area
  - `controlsBackgroundColor`: Background color of control elements
- `slider` (Object): Configure video progress slider
  - Supports all `@react-native-community/slider` props
  - `visible`: Toggle slider visibility
- `icon` (Object): Customize control icons
  - `size`: Icon size
  - `color`: Icon color
  - `style`: Icon text style
  - Custom icon elements for various states (play, pause, replay, etc.)
- `fullscreen` (Object): Fullscreen mode configuration
  - `enterFullscreen`: Callback when entering fullscreen
  - `exitFullscreen`: Callback when exiting fullscreen
  - `inFullscreen`: Current fullscreen state
  - `visible`: Fullscreen toggle visibility
- `mute` (Object): Mute functionality configuration
  - `enterMute`: Callback when muting
  - `exitMute`: Callback when unmuting
  - `isMute`: Current mute state
  - `visible`: Mute control visibility

##### Example Usage

```typescript
import VideoPlayer from 'your-video-player-library';
import { Video } from 'expo-av';

function MyVideoComponent() {
  return (
    <VideoPlayer 
      videoProps={{
        source: { uri: 'https://example.com/video.mp4' },
        resizeMode: Video.RESIZE_MODE_CONTAIN
      }}
      defaultControlsVisible={true}
      fullscreen={{ visible: true }}
    />
  );
}
```

### Enums and Types

#### `ControlStates`
Represents the visibility state of video controls
- `Visible`
- `Hidden`

#### `PlaybackStates`
Represents the current state of video playback
- `Loading`
- `Playing`
- `Paused`
- `Buffering`
- `Error`
- `Ended`

#### `ErrorSeverity`
Represents the severity of an error
- `Fatal`
- `NonFatal`

#### `ErrorType`
Error object structure
- `type`: Error severity
- `message`: Error description
- `obj`: Additional error details

### Utility Functions

#### `ErrorMessage`
Renders an error message with custom styling
- Accepts `message` and `style` props

#### `getMinutesSecondsFromMilliseconds(ms: number)`
Converts milliseconds to a formatted time string (MM:SS)

#### `TouchableButton`
A flexible touchable button component supporting various touch interactions

#### `deepMerge(target: Object, source: Object)`
Deeply merges two objects, combining nested properties

### Predefined Styles

A collection of predefined styles for various video player components, including:
- `errorWrapper`
- `videoWrapper`
- `iconWrapper`
- `bottomInfoWrapper`
- `topInfoWrapper`
- `timeLeft`
- `timeRight`
- `slider`

## Project Structure

The project is organized into several key directories and files that support its functionality:

### Root Directory
The root directory contains configuration files and project-level documentation:
- `package.json`: Defines project metadata, dependencies, and scripts
- `tsconfig.json`: TypeScript configuration for the project
- `LICENSE`: Project licensing information
- `CHANGELOG.md`: Record of version changes and updates
- `.gitignore` and `.npmignore`: Specifies files to be ignored by Git and npm
- Configuration files for code formatting and linting:
  - `.eslintrc.js`: ESLint configuration
  - `.prettierrc.js`: Prettier code formatting rules

### Source Code
The `lib/` directory contains the core source code:
- `lib/index.tsx`: Main entry point for the library
- `lib/constants.tsx`: Shared constants used across the project
- `lib/props.tsx`: Prop type definitions and related utilities
- `lib/utils.tsx`: Utility functions and helper methods

### Compiled Output
The `dist/` directory contains the compiled JavaScript and TypeScript declaration files:
- Compiled versions of source files from `lib/`
- Includes both `.js` and `.d.ts` files for TypeScript type definitions

### Example Application
The `example-app/` directory provides a demonstration of the library's usage:
- `App.tsx`: Main application component
- `app.json`: Expo configuration
- `assets/`: Contains application icons and splash screens
- `tsconfig.json`: TypeScript configuration specific to the example app

### GitHub Support Files
The `.github/` directory contains community and workflow support files:
- `FUNDING.yml`: Information about project sponsorship
- `ISSUE_TEMPLATE/`: Templates for bug reports and feature requests
- `dependabot.yml`: Configuration for dependency updates

### Migration Guide
- `migration-1x-to-2x.md`: Documentation for migrating between major versions

This structure supports a modular, well-organized TypeScript project with clear separation of concerns between source code, compiled output, and example usage.

## Technologies Used

### Core Technologies
- [React Native](https://reactnative.dev/): Cross-platform mobile application framework
- [Expo](https://expo.dev/): Framework and platform for universal React Native apps

### Programming Languages
- [TypeScript](https://www.typescriptlang.org/): Primary programming language
- [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript): Secondary language

### Key Libraries and Dependencies
- [expo-av](https://docs.expo.dev/versions/latest/sdk/av/): Video and audio playback library
- [@react-native-community/slider](https://github.com/react-native-slider/slider): Customizable slider component
- [tslib](https://github.com/Microsoft/tslib): Runtime library for TypeScript

### Development Tools
- [ESLint](https://eslint.org/): Code linting and quality tool
- [Prettier](https://prettier.io/): Code formatting tool
- [TypeScript Compiler](https://www.typescriptlang.org/docs/handbook/compiler.html): TypeScript transpilation

### Build and Packaging
- [Expo CLI](https://docs.expo.dev/workflow/expo-cli/): Command-line interface for Expo development
- [Yarn](https://yarnpkg.com/): Package management

### Compatibility
- Supports Expo projects from version 38.0.0 and above
- Compatible with React Native versions 0.70.x

## Additional Notes

### Project Philosophy
This library extends Expo's native Video component by adding rich, YouTube-like user interface controls and extensive customization options. It's designed to provide developers with a flexible and feature-rich video player solution for Expo and React Native projects.

### Known Limitations
- Subtitles are not natively supported (refer to [GitHub Issue #1](https://github.com/ihmpavel/expo-video-player/issues/1))
- Internet connection interruptions require manual handling by the developer
- Fullscreen and mute functionality require custom implementation

### Performance Considerations
- The library adds a layer of complexity to the native Expo Video component
- For optimal performance, use with local video sources or stable network connections
- Customize animations and controls to match your app's specific requirements

### Maintenance Status
- Actively maintained by the original author
- Open to community contributions and sponsorships
- Regular updates to maintain compatibility with latest Expo SDK versions

### Future Roadmap
- Implement comprehensive test coverage
- Potential expansion of customization options
- Continued SDK compatibility improvements

### Inspiration and Resources
This project was inspired by the deprecated [expo/videoplayer](https://github.com/expo/videoplayer) and draws from best practices in React Native and Expo component development.

## Contributing

We welcome contributions to this project! To ensure a smooth collaboration, please follow these guidelines:

### Reporting Issues

If you encounter a bug or have a feature request, please use our GitHub issue templates:
- For bug reports, provide a clear description, steps to reproduce, and any relevant environment details
- For feature requests, explain the problem you're solving and your proposed solution

### Code Contribution Process

1. Fork the repository
2. Create a new branch for your feature or bugfix
3. Make your changes, ensuring you follow our coding standards

### Coding Standards

#### Code Style
- We use Prettier for code formatting
- Use 2 spaces for indentation
- Prefer single quotes
- Maximum line length is 100 characters
- No semicolons

#### Linting
- We use ESLint with TypeScript and React plugins
- Run `yarn lint` to check your code before submitting a pull request
- Resolve any linting errors before submission

### Pull Request Guidelines

- Provide a clear, descriptive title for your pull request
- Include a detailed description of your changes
- Ensure all tests pass
- Update documentation if necessary

### Development Setup

- Use Yarn as the package manager
- Install dependencies with `yarn install`
- Run tests with `yarn test`

### Code of Conduct

Please be respectful and considerate of others. Harassment and discriminatory behavior are not tolerated.

### Questions?

If you have any questions about contributing, please open an issue for discussion.

## License

This project is licensed under the MIT License. 

#### Full License Text

The project is released under the MIT License, which is a permissive free software license that allows you to:
- Use the software commercially
- Modify the software
- Distribute the software
- Privately use the software

#### Key Conditions
- Include the original license and copyright notice in any substantial portion of the software
- The software is provided "as is" without warranty

For the complete license text, please see the [LICENSE](LICENSE) file in the repository.

#### Copyright
Copyright (c) 2021 @ihmpavel/expo-video-player