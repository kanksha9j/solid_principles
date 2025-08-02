## Table of Contents
- [SOLID Principles](#solid-principles)
- [Design Patterns](#design-patterns)


# SOLID Principles

1. S - [Single Responsibility Principle](#single-responsibility-principle)
2. O - [Open/Closed principle](#openclosed-principle)
3. L - [Liskov Substitution Principle](#liskov-substitution-principle)
4. I - [Interface Segregation Principle](#interface-segregation-principle)
5. D - [Dependency Inversion Principle](#dependency-inversion-principle)

## Single Responsibility Principle

	Class should have only 1 single responsibility or only 1 reason to change

1. Example 1:
- A CAN Bus interface class only deals with reading raw CAN frames from the vehicle bus.
- And the class changes only if CAN hardware or driver changes (i.e migration from Socket CAN to vector hardware)

2. Example 2:
- A logger class will only write logs to file/database for local diagnostics.
- And the class changes only if Logging format or backend (CSV to SQLite changes) 

3. Other examples: Utility Class, Sending data to server, etc.

## Open/Closed Principle
	
	Software entities should be open for extension but closed for modification.

- This includes applying inheritance and polymorphism in C++.

1. Example:

- In Fleet management system of vehicles, there exist many vehicle models and ECUs.
- So you must be able to add suppport for new devices or ECUs over time. And it should not break existing support for old vehicle models or ECUs.
- To avoid hardcoding when there is a new ECU added, you can use a JSON config file to describe models and ECUs used.
- And use a factory pattern to create decoders dynamically at runtime.

## Liskov Substitution Principle 

	Objects of a superclass must be replaceable with objects of subclass

- Here focus is on Inheritance.

1. Example:
- A base class ECU has function collectData() that collects general data from sensors.
- A separate class PositionProvider has function getCoordinates() collects GPS coordinates.

- BatteryECU, TemperatureECU subclasses do not need GPS coordinates.
- TelematicsECU subclass needs coordinates.
- If you would have combined collectData() and getCoordinates(), then BatteryECU or TemperatureECU would be forced to implement getCoordinates(), even though it makes no sense for them. this violates LSP principle.

## Interface Segregation Principle

	Clients should not be forced to depend on interfaces they do not use.

- Here focus is on class design, Interface size ot responsibility
- It says to break down large, generic interfaces into smaller and more focused / specific abstract classes.
- This ensures that classes depend only on the interfaces they need.
- Example: IVehicle interface contains Drive() and Fly() functions. Car and Plane both inherit from this interface. While the car would not need the Fly() function and the Plane would not need Drive() function.
- Hence in such case you need to have seperate interfaces for drive and fly functionality.


## Dependency Inversion Principle
 
	High level modules should not depend on low level modules, both should depend on abstractions

- It means a clas should not call a concrete class directly.
- Concrete class means :
	- A non-abstract Base class
	- Class which is not an abstract class.


# Design Patterns

A design pattern is a tested solution to a recurring problem.
Ensures best practice.
Build on experience : Avoid common pitfalls and reinventing the wheel.

Patterns:

1. Creational: Ways of creating objects
2. Structural: How objects are built into large structures
3. Behavioral: relate to run time behaviour


## To learn how to create a readMe file you can use the following interactive tutorial:
<https://commonmark.org/help/tutorial/>
