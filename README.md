# Rspec Sample Data Cheatsheet

_Bullet-pointed MD cheat sheet of Rspec's sample data handling: mocks/doubles, stubs, let/let!, before, subject, and factories. The variety of ways to set up sample data in Rspec has proved to be one of the most difficult concepts for me to grasp, so this cheat sheet is for my own benefit but may prove helpful to other Rspec beginners. This is a work in progress - your contributions much appreciated! (Special thanks to the [Odin Project community](http://www.theodinproject.com/) for their input.)_

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
* Because none of this is "real", you can get false positives, tests that pass but contain methods that you never create or change at some later point. Mitigate this by using [verifying doubles](https://relishapp.com/rspec/rspec-mocks/v/3-5/docs/verifying-doubles).

**Reference**
* [Sitepoint Tutorial](https://www.tutorialspoint.com/rspec/rspec_test_doubles.htm)
* [Official Docs on Relish](https://relishapp.com/rspec/rspec-mocks/v/3-5/docs/basics) 

## Stubs


## Let/Let!
**Nutshell:** 
_let basically creates a variable within a describe group that is equal to its block's return value. The variable can be accessed by all examples (including nested) within the group (but watch out for the gotchas below), and is evaluated only when called. let! is identical but is evaluated immediately_

**Basic Syntax** 
```ruby
describe "#my_method" do
  let(:instantiated_object) { SomeObject.new("parameter", "another_param") }

  it "uses the let variable in this test"
    expect(instantiated_object.my_method).to  # do something appropriate
  end
end
```
**When to Use**
* Instantiate classes or set up a basic state
* [Generally preferred](http://stackoverflow.com/questions/5359558/when-to-use-rspec-let/5359979#5359979) over setting up instance variables in before blocks

**Gotchas**
* Let is "memoized" (basically cached) within an example but not between examples, so calling it 1000 times within an example would always return the same (cached) value. However, calling it again in a later example will cause it to be reevaluated. See [these examples](https://www.relishapp.com/rspec/rspec-core/v/2-5/docs/helper-methods/let-and-let).
* Let! should be used with care.

**Reference**
* [Semaphore Tutorial - halfway down](https://semaphoreci.com/community/tutorials/rspec-subject-helpers-hooks-and-exception-handling)
* [Official Docs on Relish](https://www.relishapp.com/rspec/rspec-core/v/3-5/docs/helper-methods/let-and-let) 

## Before


## Subject


## Factories






