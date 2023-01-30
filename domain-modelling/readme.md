# Domain Modelling

_something about the motivation_

# Talking About Data

_describe some data types and how to "define" data_

When talking about modelling we're gonna have to talk about data, so for the purposes of this writeup this will be the nomenclature.

I'm going to refer to basic types such as 

- `number` - `5` for example
- `text` - any kind of text such as `"this is a text"`
- `timestamp` - a date and a time

# Example Model

So in this scenario, imagine that we're going to be designing a solution for assigning school grades for students in a school.
We'll need to be able to describe courses as well as students.

So maybe a very bare bones model of a course will look something like this:
```gql
Course {
  id: number
  name: text
}
```

And we could describe a student as
```gql
Student {
  id: number
  name: text
  age: number
}
```

And for starters, let's say the way we describe students enrolling to classes is like so:
```gql
Enrolment {
  id: number
  Student: ref
  Course: ref
}
```

With this we could describe a scenario where John is taking an English course:

### Student
|id|name|age|
|-|-|-|
|`12`|`"John Doe"`|`16`|

### Course
|id|name|
|-|-|
|`5`|`"English"`|

### Enrolment
|id|Student|Course|
|-|-|-|
|`1`|`12`|`5`|



# Adapting to Changes

scenario addition
- students could rent books?
- classrooms with monitors / white boards?

# Balancing Hypothetical and Current Needs

_something about how much to do / not to do considerations about potential future needs_

So with all that said, too much modelling increase development viscosity.
Having to use time and effort saving and manipulating data that isn't used will hurt productivity.

On the other hand, not modelling enough and finding out down the line that you didn't model the domain extensively enough or accurately enough can result in technical walls that cost a lot of time and effort to redo.

Striking the balance between theorizing future needs and current needs takes practice.
I find that at the very least, the domain should represent
- The data models of each entity
- Actions that transform the data
