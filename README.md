# Factory Constructor 
### A factory constructor in Flutter is a special type of constructor that doesn't always create a new instance of its class. Instead, it may return an existing instance or even an instance of a different class. This flexibility allows developers to control the object creation process more precisely.

For example, a factory constructor can be used to implement a singleton pattern, where only one instance of a class is allowed to exist.

class Singleton {
  static Singleton _instance;

  factory Singleton() {
    if (_instance == null) {
      _instance = Singleton._privateConstructor();
    }
    return _instance;
  }

  Singleton._privateConstructor();
}
