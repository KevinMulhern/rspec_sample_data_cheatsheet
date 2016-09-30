# Rspec Sample Data Cheatsheet

_Bullet-pointed MD cheat sheet of Rspec's sample data handling: mocks/doubles, stubs, let/let!, before, subject, and factories. The variety of ways to set up sample data in Rspec has proved to be one of the most difficult concepts for me to grasp, so this cheat sheet is for my own benefit but may prove helpful to other Rspec beginners. This is a work in progress - your contributions much appreciated! (Special thanks to the [Odin Project community](http://www.theodinproject.com/) for their input.)_

### Summary
You won't get far in testing without sample data (objects, methods, states, etc.). Rspec offers multiple solutions to this problem. 

## Mocking / Doubles
**Nutshell:** 
_Mocks (Doubles in Rspec) are dummy *classes/objects*. They are dumb (strict) by default until you tell them what methods they can respond to. You can optionally *allow* or *expect* them to respond with canned responses (sometimes called [messages](https://relishapp.com/rspec/rspec-mocks/v/3-5/docs/basics/allowing-messages), essentially stubs - see below)._

**Basic Syntax** 
```ruby
my_double = double("optional string name", :optional_method => 11)
allow(my_double).to receive(:optional_method)
expect(my_double.optional_method).to eq(11)
```
**When to Use**
* Need an object to act on but it doesn't yet exist or you don't want to instantiate it.
* The above keeps test examples nicely isolated from each other.

**Gotchas**
* Because none of this is "real", you can get false positives, tests that pass but contain methods that you never create or change at some later point. Mitigate this by using [verifying doubles](https://relishapp.com/rspec/rspec-mocks/v/3-5/docs/verifying-doubles)

**Reference**
* [Tutorial](https://www.tutorialspoint.com/rspec/rspec_test_doubles.htm)
* [Official Docs](https://relishapp.com/rspec/rspec-mocks/v/3-5/docs/basics) 

## Stubs


## Let/Let!


## Before


## Subject


## Factories






