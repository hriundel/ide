# ide

Despite being quite new to Scala (~2 months of on and off work), I decided to take a risk and attempt to write this project in it. There where a couple of reasons for that. First, I've only worked professionally in Ruby, which is a weakly-typed language. As our codebase grew larger, I've found myself wishing to have more tight control over object's types in order to reduce the number of unexpected behaviors (or code review times) after code changes. Scala's type safety reduces the cognitive load of keeping the whole project structure in my head as I modify it. Second, a lot of 'Big Data' tools are written in Scala. It seemed fitting to implement this in something that could be easily extended to run on parallel machines using available frameworks (like Spark), even if this was only a test project. And finally, I figured that even if I'm not accepted, at least I would have learned a lot of new things in just a few days that otherwise could have taken months..

With that in mind, here is how I've approached the problem.

First order of business was to abstract away data input and output. Data can be coming from a file or a stream or something else and, similarly, could be written to a file or S3 or maybe even persisted in memory for further use. None of that should affecte internal logic, so I've added `Source` and `Sink`. The process then is to take a `Tweet` from `Source` and send it off to all consumers, each of which will perform a series of operations on it and store the output to its respective `Sink`.


### Visual Overview 
![alt tag](public/images/ide.png)
