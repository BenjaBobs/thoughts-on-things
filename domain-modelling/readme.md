# Domain Modelling

something about the motivation

# Talking About Data

describe some data types and how to "define" data

When talking about modelling we're gonna have to talk about data, so for the purposes of this writeup this will be the nomenclature.

I'm going to refer to basic types such as 

- `number` - `5` for example
- `text` - any kind of text such as `"this is a text"`
- `timestamp` - a date and a time
- `ref` - 

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

With this we could setup the following scenario:

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
- want the ability to have more than 1 window
- maybe customize window type / door type?

# Balancing Hypothetical and Current Needs

something about how much to do / not to do considerations about potential future needs
