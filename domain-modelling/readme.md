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

So maybe a course will look something like this:
```gql
Course {
  id: text
  name: text
}
```

And we could describe a student as
```gql
Student {
  id: text
  name: text
  age: number
}
```

# Adapting to Changes

scenario addition
- want the ability to have more than 1 window
- maybe customize window type / door type?

# Balancing Hypothetical and Current Needs

something about how much to do / not to do considerations about potential future needs
