# Android Widget - Website Opener

## Лабораторная работа № 2. Создание виджета

This Android widget allows users to open a website by clicking on it. The URL can be configured through the widget's configuration screen.

## Project Structure

```
app/
├── src/main/
│   ├── java/com/example/dtpweb/
│   │   ├── NewAppWidget.java                    # Main widget implementation
│   │   └── NewAppWidgetConfigureActivity.java   # Configuration activity
│   ├── res/
│   │   ├── xml/
│   │   │   └── new_app_widget_info.xml          # Widget metadata
│   │   ├── layout/
│   │   │   ├── new_app_widget.xml               # Widget layout
│   │   │   └── new_app_widget_configure.xml     # Configuration screen layout
│   │   └── values/
│   │       ├── strings.xml                       # String resources
│   │       ├── dimens.xml                        # Dimension resources
│   │       └── colors.xml                        # Color resources
│   └── AndroidManifest.xml                       # App manifest with permissions
├── build.gradle                                  # App-level build configuration
└── proguard-rules.pro                           # ProGuard rules
```

## Features

1. **Widget Click Action**: Opens a web browser to navigate to a specified URL
2. **Configuration Screen**: Allows users to input a custom URL when adding the widget
3. **Default URL**: Opens google.com if no URL is configured
4. **Internet Permission**: Includes necessary permission to access the internet

## Implementation Details

### Widget Behavior

- **Default Action**: When clicked without configuration, opens https://google.com
- **Custom URL**: After configuration, opens the user-specified URL
- **Update Period**: Set to 0 to disable automatic updates

### Configuration Screen

- **URL Input Field**: Text field with "http://" hint for easy input
- **Add Button**: Confirms the configuration and adds the widget
- Uses `RelativeLayout` for flexible UI arrangement

### Widget Layout

- **TextView**: Displays "Open Website" text
- **Background Color**: Blue (#09C)
- **Styling**: White, bold, italic text at 24sp

## How to Build

1. Open the project in Android Studio
2. Build the project using Gradle:
   ```
   ./gradlew build
   ```

## How to Use

1. Long-press on the home screen
2. Select "Widgets"
3. Find "DTP Web Widget"
4. Drag it to the home screen
5. Enter the desired URL in the configuration screen
6. Click "Add widget"
7. Tap the widget to open the website

## Requirements

- Android SDK 21 (Lollipop) or higher
- Target SDK 34
- Internet permission

## Customization Options

### Widget Appearance (res/layout/new_app_widget.xml)
- Change background color
- Modify text size, color, and style
- Adjust layout arrangement

### Configuration Screen (res/layout/new_app_widget_configure.xml)
- Modify layout arrangement (RelativeLayout used)
- Change hint text in the URL input field
- Customize button appearance

## Code Changes from Lab Instructions

The implementation follows the lab instructions with these key components:

1. **AndroidManifest.xml**: Added INTERNET permission before `<application>` tag
2. **new_app_widget_info.xml**: Set `updatePeriodMillis` to 0
3. **NewAppWidget.java**: Implements `updateAppWidget()` method to open URL on click
4. **NewAppWidgetConfigureActivity.java**: Provides configuration UI for custom URLs
5. **Layout files**: Configured for user-friendly interface with RelativeLayout

## Notes

- The `onDeleted()` method was removed as specified in the lab instructions
- The widget uses `PendingIntent.FLAG_IMMUTABLE` for security compliance with modern Android versions
- The configuration activity is automatically launched when the widget is added to the home screen
