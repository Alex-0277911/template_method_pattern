// ми розробляємо погодний додаток, який отримує дані про погоду з різних джерел
// (наприклад, OpenWeatherMap та AccuWeather) та відображає їх у зручному
// форматі для користувача. Оскільки дані про погоду з різних джерел можуть мати
// різні формати та структури, ми можемо використовувати шаблон Template Method
// для визначення загальної структури отримання та обробки даних про погоду, але
// дозволити кожному джерелу реалізувати власні конкретні деталі.

// Ось приклад реалізації шаблону Template Method у мові Dart:

// У цьому прикладі ми маємо абстрактний клас WeatherService, який визначає
// загальну логіку отримання та відображення даних про погоду. Кожний конкретний
// сервіс (наприклад, OpenWeatherMapService та AccuWeatherService) розширює цей
// клас та надає реалізацію конкретних методів для отримання, парсингу та
// відображення даних про погоду для свого джерела.

// Метод displayWeather використовується для отримання даних про погоду з
// відповідного джерела (за допомогою методу getData), парсингу цих даних
// (за допомогою методу parseData) та відображення їх у зручному форматі для
// користувача (за допомогою методу printWeather).

abstract class WeatherService {
  Future<String> getData(String city);

  void displayWeather(String city) async {
    var data = await getData(city);
    var weather = parseData(data);
    printWeather(weather);
  }

  dynamic parseData(String data) {
    throw UnimplementedError();
  }

  void printWeather(dynamic weather) {
    throw UnimplementedError();
  }
}

class OpenWeatherMapService extends WeatherService {
  @override
  Future<String> getData(String city) async {
    // Отримуємо дані про погоду з OpenWeatherMap API
    return city;
  }

  @override
  dynamic parseData(String data) {
    // Парсимо дані про погоду у форматі OpenWeatherMap
    return data;
  }

  @override
  void printWeather(dynamic weather) {
    // Відображаємо погодні дані у зручному форматі для користувача
    print(weather);
  }
}

class AccuWeatherService extends WeatherService {
  @override
  Future<String> getData(String city) async {
    // Отримуємо дані про погоду з AccuWeather API
    return city;
  }

  @override
  dynamic parseData(String data) {
    // Парсимо дані про погоду у форматі AccuWeather
    return data;
  }

  @override
  void printWeather(dynamic weather) {
    // Відображаємо погодні дані у зручному форматі для користувача
    print(weather);
  }
}

void main() {
  var openWeatherMapService = OpenWeatherMapService();
  var accuWeatherService = AccuWeatherService();

  openWeatherMapService.displayWeather('Київ');
  accuWeatherService.displayWeather('Львів');
}


// Таким чином, за допомогою паттерну Template Method ми можемо визначити загальну
// логіку отримання та відображення даних про погоду та дозволити кожному 
//конкретному сервісу надавати свою власну реалізацію деталей для взаємодії з 
//різними джерелами даних про погоду.