# 🚀 Professional Flutter Project Template

A comprehensive Flutter project template with modern architecture, best practices, and professional organization for rapid app development.

## 📋 Table of Contents

- [Features](#-features)
- [Architecture](#-architecture)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Configuration](#-configuration)
- [Usage Examples](#-usage-examples)
- [Best Practices](#-best-practices)
- [Contributing](#-contributing)
- [License](#-license)

## ✨ Features

### 🏗️ Architecture & State Management
- **GetX** for state management, dependency injection, and routing
- **MVC Pattern** with clear separation of concerns
- **Repository Pattern** for data layer abstraction
- **Service Layer** for business logic and external integrations

### 🌐 Network & API
- **HTTP Client** with built-in error handling and logging
- **Token Management** with automatic refresh
- **Request/Response Interceptors**
- **Network connectivity monitoring**

### 🎨 UI & Design
- **Responsive Design** with flutter_screenutil
- **Light/Dark Theme** support with system theme detection
- **Google Fonts** integration with local font fallback
- **Professional Color Schemes** and typography
- **Consistent Design System**

### 🌍 Localization
- **Multi-language Support** with GetX translations
- **Dynamic Language Switching**
- **RTL Support Ready**
- **Locale Persistence**

### 💾 Storage & Persistence
- **Secure Storage** for sensitive data (tokens, credentials)
- **Local Storage** for app preferences and cache
- **Storage Service** with encryption support

### 📱 Device Integration
- **Image Picker** with permission handling
- **File Upload** with progress tracking
- **Permission Handler** for device features
- **Device Info** collection

### 🔧 Development Tools
- **Logger Service** with colorful console output
- **Error Handling** with crash reporting ready
- **Validation Utilities** for forms and data
- **Code Organization** with feature-based structure

### 🚀 Performance & Optimization
- **Lazy Loading** of controllers and services
- **Memory Management** with proper disposal
- **Image Caching** for network images
- **Efficient Scrolling** with optimized lists

## 🏛️ Architecture

This template follows **Clean Architecture** principles with **MVC Pattern**:

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Presentation  │    │    Business     │    │      Data       │
│     Layer       │◄──►│     Layer       │◄──►│     Layer       │
│                 │    │                 │    │                 │
│ • Screens (UI)  │    │ • Controllers   │    │ • Repositories  │
│ • Widgets       │    │ • Services      │    │ • Data Sources  │
│ • Bindings      │    │ • Use Cases     │    │ • Models        │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```

### Key Principles:
- **Separation of Concerns**: Each layer has a single responsibility
- **Dependency Inversion**: Higher layers don't depend on lower layers
- **Single Responsibility**: Each class has one reason to change
- **Interface Segregation**: Small, focused interfaces

## 📁 Project Structure

```
lib/
├── 📁 core/                          # Core functionality
│   ├── 📁 bindings/                  # Dependency injection
│   │   └── initial_binding.dart      # App-wide dependencies
│   ├── 📁 constants/                 # App constants
│   │   └── app_constants.dart        # Configuration & constants
│   ├── 📁 services/                  # Core services
│   │   ├── http_service.dart         # HTTP client service
│   │   ├── local_storage_service.dart # Storage service
│   │   └── logger_service.dart       # Logging service
│   ├── 📁 theme/                     # App theming
│   │   └── app_theme.dart            # Light & dark themes
│   └── 📁 utils/                     # Utility functions
│       └── app_utils.dart            # Helper functions
├── 📁 features/                      # Feature modules
│   ├── 📁 home/                      # Home feature
│   │   ├── 📁 controllers/           # Business logic
│   │   │   └── home_controller.dart
│   │   ├── 📁 repositories/          # Data layer
│   │   │   └── home_repository.dart
│   │   └── 📁 screens/               # UI layer
│   │       └── home_screen.dart
│   └── 📁 splash/                    # Splash feature
│       └── 📁 screens/
│           └── splash_screen.dart
├── 📁 localization/                  # Multi-language support
│   └── app_localization.dart         # Translation strings
├── 📁 routes/                        # Navigation & routing
│   ├── app_pages.dart                # Route definitions
│   └── app_routes.dart               # Route constants
└── main.dart                         # App entry point
```

## 🚀 Getting Started

### Prerequisites
- Flutter SDK (latest stable version)
- Dart SDK
- Android Studio / VS Code
- Git

### Installation

1. **Clone this repository:**
   ```bash
   git clone https://github.com/your-username/flutter-project-template.git
   cd flutter-project-template
   ```

2. **Install dependencies:**
   ```bash
   flutter pub get
   ```

3. **Generate launcher icons (optional):**
   ```bash
   flutter packages pub run flutter_launcher_icons:main
   ```

4. **Run the app:**
   ```bash
   flutter run
   ```

### Quick Setup for New Project

1. **Rename the project:**
   ```bash
   # Update pubspec.yaml name field
   # Update Android package name
   flutter packages pub run change_app_package_name:main com.yourcompany.appname
   ```

2. **Configure API endpoints:**
   ```dart
   // lib/core/constants/app_constants.dart
   static const String baseApiUrl = 'https://your-api.com';
   ```

3. **Update app branding:**
   - Replace logo and icons in `assets/`
   - Update app name in `pubspec.yaml`
   - Customize theme colors in `app_theme.dart`

## ⚙️ Configuration

### Environment Setup

Update constants in `lib/core/constants/app_constants.dart`:

```dart
class AppConstants {
  // API Configuration
  static const String baseApiUrl = 'https://your-api.com';
  static const String apiVersion = 'v1';
  
  // App Configuration
  static const String appName = 'Your App Name';
  static const String packageName = 'com.yourcompany.yourapp';
  
  // Feature Flags
  static const bool enableAnalytics = true;
  static const bool enableCrashReporting = true;
}
```

### Theme Customization

Modify `lib/core/theme/app_theme.dart`:

```dart
// Update color schemes
static const ColorScheme _lightColorScheme = ColorScheme(
  brightness: Brightness.light,
  primary: Color(0xFF1976D2), // Your primary color
  // ... other colors
);
```

### Localization Setup

Add translations in `lib/localization/app_localization.dart`:

```dart
'en_US': {
  'your_key': 'Your English Text',
},
'es_ES': {
  'your_key': 'Tu Texto en Español',
},
```

## 💡 Usage Examples

### Creating a New Feature

1. **Create feature directory:**
   ```
   lib/features/profile/
   ├── controllers/profile_controller.dart
   ├── repositories/profile_repository.dart
   └── screens/profile_screen.dart
   ```

2. **Create controller:**
   ```dart
   class ProfileController extends GetxController {
     final ProfileRepository _repository = ProfileRepository();
     
     // Reactive variables
     final RxBool isLoading = false.obs;
     final Rx<User?> user = Rx<User?>(null);
     
     // Methods
     Future<void> loadProfile() async {
       // Implementation
     }
   }
   ```

3. **Create repository:**
   ```dart
   class ProfileRepository {
     final HttpService _httpService = HttpService.instance;
     
     Future<User> getProfile() async {
       final response = await _httpService.get('user/profile');
       if (response.isSuccess) {
         return User.fromJson(response.data);
       }
       throw Exception(response.message);
     }
   }
   ```

4. **Create screen:**
   ```dart
   class ProfileScreen extends GetView<ProfileController> {
     @override
     Widget build(BuildContext context) {
       return Scaffold(
         appBar: AppBar(title: Text('profile'.tr)),
         body: Obx(() => controller.isLoading.value
           ? Center(child: CircularProgressIndicator())
           : ProfileContent(),
         ),
       );
     }
   }
   ```

### Making API Calls

```dart
// GET request
final response = await HttpService.instance.get('users');

// POST request with body
final response = await HttpService.instance.post(
  'users',
  body: {'name': 'John', 'email': 'john@example.com'},
);

// File upload
final response = await HttpService.instance.uploadFile(
  'upload',
  File('path/to/file.jpg'),
  fieldName: 'avatar',
);
```

### Using Storage Services

```dart
// Secure storage (for sensitive data)
await LocalStorageService.setAccessToken('your_token');
final token = await LocalStorageService.getAccessToken();

// Regular storage (for app preferences)
LocalStorageService.setThemeMode(ThemeMode.dark);
final theme = LocalStorageService.getThemeMode();

// Custom data
LocalStorageService.write('user_settings', {'notifications': true});
final settings = LocalStorageService.read('user_settings');
```

### Navigation

```dart
// Navigate to route
Get.toNamed(AppRoutes.PROFILE);

// Navigate with arguments
Get.toNamed(AppRoutes.USER_DETAILS, arguments: {'userId': 123});

// Replace current route
Get.offNamed(AppRoutes.HOME);

// Clear all and navigate
Get.offAllNamed(AppRoutes.LOGIN);
```

## 🎯 Best Practices

### Code Organization
- ✅ Group related files in feature folders
- ✅ Use meaningful file and class names
- ✅ Keep controllers focused on business logic
- ✅ Use repositories for data access
- ✅ Implement proper error handling

### State Management
- ✅ Use reactive variables (RxString, RxBool, etc.)
- ✅ Keep UI reactive with Obx() widgets
- ✅ Dispose resources in onClose()
- ✅ Use dependency injection with Get.lazyPut()

### Performance
- ✅ Use lazy loading for controllers
- ✅ Implement proper image caching
- ✅ Optimize list rendering with ListView.builder
- ✅ Minimize widget rebuilds

### Security
- ✅ Store sensitive data in secure storage
- ✅ Implement proper token refresh logic
- ✅ Validate all user inputs
- ✅ Use HTTPS for all API calls

### Testing
- ✅ Write unit tests for controllers
- ✅ Test repository methods
- ✅ Mock external dependencies
- ✅ Test UI with widget tests

## 📦 Dependencies

### Core Dependencies
```yaml
dependencies:
  flutter:
    sdk: flutter
  
  # State Management & Navigation
  get: ^4.6.1
  
  # HTTP & Networking
  http: ^1.4.0
  connectivity_plus: ^5.0.1
  
  # Storage
  get_storage: ^2.1.1
  flutter_secure_storage: ^9.2.4
  
  # UI & Design
  flutter_screenutil: ^5.9.3
  google_fonts: ^6.2.1
  cached_network_image: ^3.4.1
  
  # Utilities
  logger: ^2.6.0
  intl: ^0.20.2
  
  # Device Features
  image_picker: ^1.1.2
  permission_handler: ^11.0.1
  
  # Icons & Animations
  iconsax: ^0.0.8
  lottie: ^2.4.2
  shimmer: ^3.0.0
  flutter_easyloading: ^3.0.5
```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Contribution Guidelines
- Follow the existing code style
- Write meaningful commit messages
- Add tests for new features
- Update documentation as needed
- Ensure CI/CD passes

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Flutter team for the amazing framework
- GetX team for state management solution
- Community contributors and package maintainers

## 📞 Support

If you find this template helpful, please consider:
- ⭐ Starring the repository
- 🐛 Reporting issues
- 💡 Suggesting improvements
- 🤝 Contributing to the project

---

**Happy Coding! 🚀**

Built with ❤️ by [Your Team Name]te

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

**END**
