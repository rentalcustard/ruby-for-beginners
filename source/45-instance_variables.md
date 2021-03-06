# Instance variables

*An object's own knowledge*

Now that you understand how the string that we pass to the method `new`
ends up being passed to the new object's `initialize` method, we can start
improving `initialize`, so it actually does something with the string:

```ruby
class Person
  def initialize(name)
    @name = name
  end
end
```

This introduces another new concept: `@name` is a new type of variable, called
an "instance variable".

The body of the `initialize` method now does nothing else but assign the value
of the local variable `name` to an instance variable `@name`.

You remember how we said that each method has it's own local scope, which is
created when the method is called, and populated with local variables from the
arguments list. You have also learned that this scope is erased, and thrown
away when Ruby exits the method body and returns from the method. And that
local variables that are visible in one method are not visible in other
methods: they are local.

Now, the thing is: Every *object* also has its own scope.

An object's scope is populated with instance variables, in the moment we assign
something to them. And they are visible *everywhere* in the object, that is, in
every method that the object has.

You can think of the object's scope as your own knowledge, or memories. For
example, you know your name, your email address, and your email password.
You keep this knowledge around, and you can use it. Likewise, an object keeps
its instance variables around, as long as the object exists.

On top of this, the object's scope also contains the object's method names.
That is to say, the object knows about its own methods, and it can call them,
internally from other methods, if that's useful.

If you now create, and output a person instance, you'll see that Ruby now
prints out the instance variable, too:

```ruby
person = Person.new("Ada")
p person
```

The first line creates a new instance of the class `Person`, passing the string
`"Ada"`, and assign this new object to the variable `person`. The second line
will then print it out:

```
#<Person:0x007fd8947aa868 @name="Ada">
```

As you can see that includes the instance variable `@name` with the value
`"Ada"`.

You can think of this as that you, as a programmer, create this new person, and
in the moment of its creation, its birth, you also give it a name. Which kind
of is, how it works with real people, too, isn't it?
