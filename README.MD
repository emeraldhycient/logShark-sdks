
```markdown
# LogShark SDK

LogShark SDK is a powerful, lightweight logging tool designed to capture events, page views, errors, and more across different frameworks. Whether you're working with React, Vue, Angular, or plain Vanilla JS, LogShark is here to help you monitor and log key activities in your applications.

## Features

- **Automatic Page View Capture**: Automatically track every page your users visit.
- **Frontend Event Capture**: Capture user interactions like clicks, form submissions, input changes, and more.
- **Error Handling**: Gracefully handle and log errors that occur in your app.
- **Crash Reporting**: Automatically report crashes and errors to the LogShark API.
- **Custom Event Logging**: Capture any custom events of your choice with associated data.
- **Scroll Depth & Heatmap (React)**: Track scroll depth and visualize heatmaps for user interactions.

---

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
  - [React](#react)
  - [Vue](#vue)
  - [Angular](#angular)
  - [Vanilla JS](#vanilla-js)
- [Customization Options](#customization-options)
- [Contributing](#contributing)
- [License](#license)

---

## Installation

Install LogShark SDK for your preferred framework via npm:

### React

```bash
npm install logshark-react
```

### Vue

```bash
npm install logshark-vue
```

### Angular

```bash
npm install logshark-angular
```

### Vanilla JS

```bash
npm install logshark
```

---

## Usage

### React

To start using LogShark in your React application:

1. **Initialize LogShark**:

    ```tsx
    import React from 'react';
    import { LogSharkCore, LogSharkErrorBoundary } from 'logshark-react';

    const logShark = new LogSharkCore({
      apiKey: 'YOUR_API_KEY',
      projectId: 'YOUR_PROJECT_ID',
      excludedUrls: ['/login', '/signup'],
    });

    const App = () => (
      <LogSharkErrorBoundary logShark={logShark}>
        <YourAppComponents />
      </LogSharkErrorBoundary>
    );

    export default App;
    ```

2. **Capture Custom Events**:

    ```tsx
    logShark.capture('button_click', window.location.pathname, { buttonId: 'save-btn' });
    ```

3. **Capture Scroll Depth**:

    ```tsx
    logShark.captureScrollDepth();
    ```

4. **Capture Heatmap**:

    ```tsx
    logShark.captureHeatmap();
    ```

---

### Vue

1. **Initialize LogShark in Vue**:

    ```javascript
    import Vue from 'vue';
    import LogSharkPlugin from 'logshark-vue';

    Vue.use(LogSharkPlugin, {
      apiKey: 'YOUR_API_KEY',
      projectId: 'YOUR_PROJECT_ID',
      excludedUrls: ['/admin', '/settings'],
    });

    new Vue({
      render: h => h(App),
    }).$mount('#app');
    ```

2. **Capture Custom Events**:

    ```javascript
    this.$logShark.capture('custom_event', window.location.pathname, { key: 'value' });
    ```

3. **Auto Capture Events**:

    LogShark will automatically capture page views, button clicks, form submissions, and input changes.

---

### Angular

1. **Initialize LogShark in Angular**:

    **app.module.ts**:

    ```typescript
    import { BrowserModule } from '@angular/platform-browser';
    import { NgModule, ErrorHandler } from '@angular/core';
    import { AppComponent } from './app.component';
    import { LogSharkService } from 'logshark-angular';
    import { LogSharkErrorHandler } from 'logshark-angular';

    const logShark = new LogSharkService({
      apiKey: 'YOUR_API_KEY',
      projectId: 'YOUR_PROJECT_ID',
      excludedUrls: ['/admin', '/settings'],
    });

    @NgModule({
      declarations: [AppComponent],
      imports: [BrowserModule],
      providers: [
        { provide: ErrorHandler, useClass: LogSharkErrorHandler },
        { provide: 'logShark', useValue: logShark },
      ],
      bootstrap: [AppComponent],
    })
    export class AppModule {}
    ```

2. **Capture Custom Events**:

    ```typescript
    this.logShark.capture('custom_event', window.location.pathname, { key: 'value' });
    ```

---

### Vanilla JS

1. **Initialize LogShark in Vanilla JS**:

    ```javascript
    import LogSharkCore from 'logshark-core';

    const logShark = new LogSharkCore({
      apiKey: 'YOUR_API_KEY',
      projectId: 'YOUR_PROJECT_ID',
      excludedUrls: ['/login', '/profile'],
    });

    // Auto-capture events
    logShark.autoCaptureEvents();

    // Capture page view
    logShark.capturePageView(window.location.pathname);
    ```

2. **Capture Custom Events**:

    ```javascript
    logShark.capture('custom_event', window.location.pathname, { key: 'value' });
    ```

---

## Customization Options

When initializing LogShark, you can customize the following options:

- **apiKey**: Your API key for authenticating with the LogShark API.
- **projectId**: The project ID associated with your application.
- **excludedUrls**: An array of URLs that you don't want to track.
  
Example initialization:

```javascript
const logShark = new LogSharkCore({
  apiKey: 'YOUR_API_KEY',
  projectId: 'YOUR_PROJECT_ID',
  excludedUrls: ['/admin', '/settings'],
});
```

---

## Contributing

Contributions are welcome! Please follow these steps to contribute:

1. Fork the repository.
2. Create your feature branch (`git checkout -b feature/my-feature`).
3. Commit your changes (`git commit -am 'Add some feature'`).
4. Push to the branch (`git push origin feature/my-feature`).
5. Open a pull request.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```

This is formatted for Markdown, and you can copy and paste it directly into your README file.