Yes, &....: Ruby's talent for improvisation

About the speaker
- Principal Architect at Launchpad
- Wear a lot of different roles and work with different people in different capacities
- In this improvise a lot
- Also ship a lot of Ruby code

Yes, and...
- Foundational principle of improvisation, and of Ruby as well
- Idea is you accept what's given, and add sometihng new
- Improv - creating something out of nothing
- Might feel like what you do with code
- Some sort of structure, but get to do something creative

Ruby
- Scene partners
- Blocks, procs and lambdsa
- How they adhere to improv rules, and also don't really adhere to the rules

- How they pass control, X and don't play to the script.

  Improv truth
  - One person speaks at a time
  - If don't listen to your partner, you won't know how to respond
  - When you're done, pass that on to your scene partner
 
  - Ruby does this very well with blocks
 A block in action
- scene method
- pass some encapsulated code within do end blocks - in this case passing a statement

scene do
  puts "Sure, I'll just move this button"
end

can also be written as
scene { puts "Sure, I'll just move this button" }

- Blocks in Ruby - like a conversation back and forth
- Do your work, pass it off and then come back
- How "yield" is used in Ruby to pass the mic

Yield - double time


Yield - one block only
- Can only pass one block at a time
- Like one mic that Ruby's passing around
- scene { puts "sure" } { puts "Hi" } - syntax error

&block - naming your scene partner
- To evaluate block you pass in - instead of using yield, you use call
- Ampersand operator behind the scenes converts the block into a proc.
def scene(
...

- Blocks are more like game scene partners where you hit the

Accepting the offer - what happens when you start to introduce arguments
- How they handle arity and argument flexibility
- Core principle improv "never deny the premise" i.e. no but. Accept what your scene partner offers and build on it
- You don't have to take everything they give you, you take what you want.

How to pass an argument into a block - Blocks are flexible with args
def scene(prop)
  yield(prop, "some context")
end
- in top example, trying to pass two arguments into yield, but where called below, it only uses the one thing.

scene("apple") do |offer|
  puts "I'll use this #{offer}!"
end

- This works the other way - if you only pass 1 arg where you are meant to pass two (example below)
- Can be used in gems to accept more arguments while being backwards compatible:
def scene(prop)
  yield(prop)
end

scene("apple") do |offer, context|
  puts "I'll use #{offer} with #{context}"
end

Difference between Procs and Lambdas
- Proc: Loose improviser
- Lambda - Strict

Proc
- AN instance of the Proc class
- Either create with Proc.new, or lowercase version
- Looks a lot like a block
- Proc is a first class object in Ruby that encapsulates a block
- Can pass arguments in the pipes and do what you want with them

loose = Proc.new {|a,b| puts "#{a} and #{b}"}
loose.call("yes")

- You can store proc in a variable

Lambdas
- A lambda is an instance of the proc class with some special flags and behaviours
- Convention: strict = -> (a, b)
- Stabby lambda - [ c.f. https://www.honeybadger.io/blog/using-lambdas-in-ruby/ ]
- Lambdas act more like methods because they are strict with their arguments
- [Can you pass named args]

- Why wouldn't you just use a method
def perform(character, scene)

(slide 35)
- Procs and blocks are closures and remember

- Allow having to pass around one thing the same - establish once - and other things changes over time
- [Why would you use]
- Pass a config option.
- Shopify: A Chang: Configure behaviour to trigger if a query raises a warning. Using to emit instrumentation around what the query was - configured in a proc.
- Rails defines scopes with lambdas
- You can do validations with lambdas - also possible with a Proc.
- Healthcheck route in development often uses a proc
if Rails.env.development?
  get '/', to: proc { [200, {}, [""] }, constraints: { format: 'json' }
end
- Blocks far more common way to use Ruby's attempt at using closures.

Control flow + lexical scope
- When it gets weird
- Sweeping a scene (improv) is when you end the scene.
- Lights go down, whether you're ready or not

Lambda - with return
def scene
  puts "That is the last time I let you drive"
  player = ->
...


Proc...but wait
def 

Proc - nowhere to go
- Redefining proc
- LocalJumpError - proc's lexical scope
- Difference between proc's lexical scope

Takeaway - in terms fo their returns
- Lambda - I'm done - allows the scene to continue
- Proc - we're done - the scene is killed

Summary
- Hold focus - then pass it off - share the stage
- Arity and argument flexibility - accepting what's given and adapting
- Trying to exit the scene early - proc could be a really good fit

Questions
.call -> return value - whatever you made the return value - maybe do something interesting like define a proc or lambda inside a proc or a lambda - and then if 
- if the return is a method you can then call it again.
