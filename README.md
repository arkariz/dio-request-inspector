<p align="center">
    <img src="https://user-images.githubusercontent.com/91040581/210127198-791f085b-61b8-4a77-8168-986c9a90d806.png" width="200" height="185">
</p>

<h3 align="center">Dio Requests Inspector</h3>

<p align="center">
A HTTP inspector for Dio, which can intercept and log HTTP requests and responses.
  <br>
  <br>
  <br>
  <br>
</p>

![ss](https://github.com/bayunugroho2022/dio-request-inspector/assets/91040581/efd6d3c9-c068-4fed-a94e-a30b9cd616ab)
<br>

## Features

- [X] Intercept and log HTTP requests and responses
- [X] Secure HTTP requests with passwords
- [X] Filter logs by request time, method, and status
- [X] Search logs by path
- [X] Easily share request and response data
- [X] Beautify JSON data
- [X] Image support for responses
- [X] Response body searching
- [X] Summary flag support
- [X] Copy to cURL
- [X] Beautiful user interface

## How to use

- Add the package with command

```bash
flutter pub add dio_request_inspector
```

- Create and configure `DioRequestInspector` instance

```dart
final DioRequestInspector inspector = DioRequestInspector(
  isInspectorEnabled: true,
  password: '123456', // optional, remove if you don't need password
  showSummary: true, // optional, default is true
);
```

- add interceptor to your Dio instance

```dart
dio.interceptors.add(inspector.getDioRequestInterceptor());
```

- Wrap your `myApp` with `DioRequestInspectorMain`

```dart
void main() {
  WidgetsFlutterBinding.ensureInitialized();
  runApp(
    DioRequestInspectorMain(
      inspector: inspector,
      child: const MyApp(),
    ),
  );
}
```

- add `navigatorObservers` to your `MaterialApp`

```dart
navigatorObservers: [
  DioRequestInspector.navigatorObserver,
],
```

## Usage

### Show Inspector UI

You can open the DioRequestInspector in two ways:

1. **Long press** on your screen to show DioRequestInspector UI (if using `DioRequestInspectorMain`)

2. **Programmatically** call:

```dart
inspector.goToInspector();
```

## Parameters

- `isInspectorEnabled` - Enable or disable the inspector (required)
- `password` - Optional password protection for the inspector
- `showSummary` - Show summary view (default: true)

## Example

See the [example](example/) directory for a complete working example.