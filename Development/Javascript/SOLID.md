1. Single Responsibility
	1. A class or module should have only a single purpose. 
	2. e.g. A car class should not hold the logging logic with it
2. Open-Closed
	1. Code should be open for extension but closed for modification. 
	2. e.g. A vehicle class should be able to have additional features added without requiring modification of existing code
3. Liskov Substitution
	1. Any class should be suitable for its parent class without unexpected consequences.
	2. e.g. If the classes `Cat` and `Dog` extend the class `Animal` all functionality held within `Animal` should behave normally for a `Cat` and `Dog` object.
4. Interface Segregation
	1. An entity should never be forced to implement an interface that contains elements which it will never use.
	2. e.g. a `Penguin` should never be forced to implement a `Bird` interface if that `Bird` interface includes functionality relating to flying, as penguins cannot fly.
5. Dependency Inversion
	1. High level code should never depend on low level interfaces and should instead use abstractions. It is all about decoupling code.


