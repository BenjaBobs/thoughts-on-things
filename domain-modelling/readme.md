# Domain Modelling

_something about the motivation_

# Talking About Data

_describe some data types and how to "define" data_

When talking about modelling we're gonna have to talk about data, so for the purposes of this writeup this will be the nomenclature.

I'm going to refer to basic types such as 

- `number` - `5` for example
- `text` - any kind of text such as `"this is a text"`
- `[]` - a list of things, e.g. a list of numbers: `[1, 2, 3]`
- `{}` - a composite type, e.g. `Circle { x: number, y: number, radius: number }`
- `#` - comments for things

# Example Model

So in this scenario, imagine that we're going to be designing a solution for assigning school grades for students in a school.
We'll need to be able to describe courses as well as students.

So let's start with a course.
In order to be able to describe it, we need to really think about what it is.
So maybe a we could say a course is a set of classes about a specific subject, tought by a teacher.
Each class might have a specific topic of the day.

There are many ways to go about this, but one way is to model a course as something self-contained.
E.g.
```gql
Course {
  id: number
  teacher: string
  subject: string
  classes: number
  topics: [string]
}
```

with that we could describe a `Course` of math consisting of twelve classes like so:
|id|teacher|subject|classes|topics|
|-|-|-|-|-|
|`1`|`"Mrs Doubtfire"`|`"Math"`|`3`|`["arithmetic", "geometry", "algebra"]`|

Alternatively, we can split out the classes and topics like so:
```gql
Course {
  id: number
  teacher: string
  subject: string
}

Class {
  id: number
  courseId: number
  topic: string
}
```

This way we could represent it in data like so:

### Course

|id|teacher|subject|
|-|-|-|
|`1`|`"Mrs Doubtfire"`|`"Math"`|

### Classes

|id|courseId|topic|
|-|-|-|
|`1`|`1`|`"arithmetic"`|
|`2`|`1`|`"geometry"`|
|`3`|`1`|`"algebra"`|

In this scenario we have three classes each as their own entity, and then referencing the course we defined.

So what's the difference between the two representations?
Why would you choose one over another?
The answer is that it depends.
The first representation is faster to get working, and more focused on the `Course`.
If the system doesn't require any deeper information about the classes, it's 


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
