# Domain Modelling

One motivation for domain modelling is to ensure that everyone involved in a project is on the same page when it comes to understanding the domain (i.e., the subject matter or problem space) being addressed by the project.
By creating a shared language for talking about the domain, domain modelling can help prevent misunderstandings and miscommunications between team members.

Another motivation for domain modelling is to facilitate the creation of a well-designed software system.
By modelling the domain before beginning visual design or writing code, designers and developers can gain a better understanding of the requirements of the system and the relationships between the various components of the system. This can help ensure that the system is both functional and maintainable.

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
  teacher: text
  subject: text
  classes: number
  topics: [text]
}
```

with that we could describe a `Course` of math consisting of twelve classes like so:

### Courses

|id|teacher|subject|classes|topics|
|-|-|-|-|-|
|`1`|`"Mrs Doubtfire"`|`"Math"`|`3`|`["arithmetic", "geometry", "algebra"]`|

Alternatively, we can split out the classes and topics like so:
```gql
Course {
  id: number
  teacher: text
  subject: text
}

Class {
  id: number
  courseId: number
  topic: text
}
```

This way we could represent it in data like so:

### Courses

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
If the system doesn't require any deeper information about the classes, spending time modelling, creating and maintaining systems around greater details might result in both wasted time and effort.
On the other hand, let's say the teachers also want to be able to describe which materials (books, papers, etc) the students will need for each class.
Then they'd need to be able to do that if the model supports describing individual classes.

Let's expand this scenario a little and add a model to describe students.
In this scenario, the school system needs to be able to describe students.

```gql
Course {
  id: number
  teacher: text
  subject: text
}

Class {
  id: number
  courseId: number
  topic: text
}

Student {
  id: number
  name: text
}
```

And we also need a way describe which courses a student takes, so let's add enrollments.

```gql
Enrollment {
  id: number
  courseId: number
  studentId: number
}
```

Now we can describe students taking classes like so:

### Courses

|id|teacher|subject|
|-|-|-|
|`1`|`"Mrs Doubtfire"`|`"Math"`|

### Classes

|id|courseId|topic|
|-|-|-|
|`1`|`1`|`"arithmetic"`|
|`2`|`1`|`"geometry"`|
|`3`|`1`|`"algebra"`|

### Students

|id|name|
|-|-|
|`1`|`"Student McStudentface"`|

### Enrollments

|id|courseId|studentId|
|-|-|-|
|`1`|`1`|`1`|

So this describes that student `1` (Student McStudentface) takes course `1` (Math).

# Adapting to Changes

scenario addition
- students could rent books?
- classrooms with monitors / white boards?

# Balancing Hypothetical and Current Needs

So with all that said, too much modelling increase development viscosity.
Having to use time and effort saving and manipulating data that isn't used will hurt productivity.

On the other hand, not modelling enough and finding out down the line that you didn't model the domain extensively enough or accurately enough can result in technical walls that cost a lot of time and effort to redo.

Striking the balance between theorizing future needs and current needs takes practice.
I find that at the very least, the domain should represent
- The data models of each entity
- Actions that transform the data

To strike a balance between these two extremes, it can be helpful to focus on the needs of the current project while keeping an eye on potential future needs. When modelling the domain, it can be useful to ask yourself questions like:

- What are the core entities and relationships that are required for the current project?
- What entities and relationships are likely to be needed in the near future?
- What entities and relationships are less certain but could be needed further down the line?

By focusing on the needs of the current project while keeping an eye on potential future needs, you can create a domain model that is both functional and flexible.
