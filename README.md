# AndroidAppUpdater

AndroidAppUpdater is a lightweight Android library designed to streamline the process of checking for updates within an Android application. With a simple and easy-to-use API, this library provides the ability to easily distribute updates without the need to depend on external services or app stores. 

## Features

- Check for updates without depending on external services or app stores
- Retrieve update URLs and changelog from a JSON source
- Download and install updates directly within the app
- Support for Android Q storage using Storage Access Framework
- Optional update prompt with customizable interface (dialog or notification based)

## Getting Started

These instructions will help you get started with using AndroidAppUpdater in your Android project.

### Requirements

- Android API level 16 (JellyBean) or higher

### Installation

Add the following to your project's `build.gradle` file:

```gradle
repositories {
    jcenter() // or mavenCentral()
}

dependencies {
    implementation 'com.github.thisisyoussef:android-app-updater:1.0.0'
}
```

## Usage

Using the AndroidAppUpdater library is easy. First, initialize the `AndroidAppUpdater` instance with a JSON file or URL containing the version and update URL information. For example, this JSON file might contain:

```json
{
  "version": "1.0.1",
  "update_url": "https://example.com/your_app.apk",
  "changelog": "Bugfixes and performance improvements."
}
```

Then, use the `checkForUpdates()` method to check for updates and handle them appropriately:

```java
AndroidAppUpdater appUpdater = new AndroidAppUpdater(this, "https://example.com/update.json");

appUpdater.checkForUpdates(new UpdateListener() {
    @Override
    public void onNewUpdateAvailable(UpdateInfo updateInfo) {
        // Show an update prompt or notification to the user
        appUpdater.showUpdateDialog(updateInfo.getChangelog());
    }
    
    @Override
    public void onUpdateDownloadStarted() {
        // Show a progress bar or other UI element to indicate the download progress
    }
   
    @Override
    public void onNoUpdatesAvailable() {
        // No updates available; continue with the app logic as usual
    }
    
    @Override
    public void onError(Exception e) {
        // Handle any errors that occurred during the update process
    }
});
```

## Contributing

Contributions to the project are welcome. To contribute, please follow these steps:

1. Fork the project
2. Create a feature branch (`git checkout -b feature/NewFeature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/NewFeature`)
5. Open a pull request

Please ensure your code adheres to the project's coding standards and includes appropriate tests and documentation.

## License

This project is licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for more details.

## Contact

If you have any questions, issues, or recommendations, please feel free to open an issue on the [GitHub repository](https://github.com/thisisyoussef/AndroidAppUpdater). You can also reach out to the maintainer of this library through their GitHub profile.

## Acknowledgments

This project uses the following technologies and tools:

- Android Studio
- Gradle
- GitHub
- Travis CI

These tools contribute to the project's success by simplifying development, building, versioning, and continuous integration processes. They support the overall goal of making app updating as effortless as possible for both developers and end-users.