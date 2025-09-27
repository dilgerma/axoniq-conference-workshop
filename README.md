## AXONIQ Conference 2025 - Workshop

Welcome to the AxonIQ Conference Workshop - Event Modeling / Event Sourcing / Slice Based Architectures

### Part I - Event Modeling ( ~ 45 Minutes )

We will work on an Event Model together - goal is for you to see how Event Modeling is used in a real world scenario.

### Part II - Code Generation ( ~ 65 Minutes )

In this part of the workshop, we will divide into groups and work on Slices.

You´ll assign yourself a slice from the Event Model and work on that.

### Part III - QA ( ~10 Minutes )

We´ll use the last 10 minutes of the Workshop for discussion and your questions. 
Of course we can discuss also after the Workshop - feel free to just ask your questions, whenever you meet me.

### Preparation

Fork this Git Repository:

[Git Repository](https://github.com/dilgerma/axoniq-conference-workshop)

Put your Name and Github User into the Grid, to get access to the Repo.

[Add your Name here](https://miro.com/app/board/uXjVIo6VNAA=/?moveToWidget=3458764642092291064&cot=14)

Get a free Miro Account ( or use one you already own )

[Miro](https://miro.com/app/dashboard/)

Install the Miro Event Modeling Toolkit

[Miro Event Modeling Toolkit](https://miro.com/marketplace/eventmodeling/)

Download the Code Gen Container
```
docker pull nebulit/codegen
```

Programming Languages / Frameworks used:

Kotlin
Spring
Spring Modulith
Axon ( using Postgres as Event Store)

### Miro Board

The Miro Board we use is here:
https://miro.com/app/board/uXjVIo6VNAA=/?moveToWidget=3458764642074524614&cot=14

### Import Event Model to your own Board

In case you want add new Slices, Given / When / Thens or extend the Event Model, import it to your own Board to work on it with the 
Event Modeling Toolkit.

Open the Code-Tab ( last one ) in the Toolkit

![image](/images/code.png)

Scroll down to "Import Model"

![image](/images/import_model.png)

Paste the config.json and click "Restore Model from JSON"

![image](/images/restore_model.png)

Wait until the import in Miro is finished ( intentionally running slow to not hit API Limits)

Select the imported Model and click "Restore Links" - fixing some linkings after the Import.

![image](/images/restore.png)

You can now work on your imported Model - depending on the structure of the original Model - some Links (especially for screens) need to be adjusted.

![image](/images/eventmodel.png)

## Code Generation

To use the code generation, you start a local docker container. The Event Model in Miro communicates with the Docker Container.

Run this the root of the Git Repository ( sources will be generated here )
```
docker run -ti -p 3001:3000 -v $PWD:/workspace  --name codegen --rm nebulit/codegen:latest
```

You can check if the generator is available on the Code Tab
![image](/images/generator.png)

The container keeps running in an interactive Shell.

![image](/images/gen.png)

Whenever you click "Create Config", the current Event Model is exported to your local file system and is
accessible by the Code Generator.

You can start the Code generator with the "gen" command.
![image](/images/shell.png)

Choose the Axon Generator

![image](/images/shell2.png)

The Skeleton-Generator creates the bare spring application. This already happened, you can focus on 
Aggregates and Slices.

Typically you will need both - choose Aggregates to generate Command- and Event Sourcing Handlers, 
choose Slices to generate Commands, Events, Rest Controllers and JPA Repositories and Entities.

If you generate Aggregates - new changes are generated into an ${aggregate}.kt.**generated** File. 
You can then copy & paste the Command Handlers to your aggregate and delete the .generated File.

If you defined GWTs - they are generated as inline-comments into the Aggregate as guideline for AI.

![image](/images/gwt.png)

## Our "Sprint"

When you take a Slice into Implementation, take a black Assignee-Sticky and pin it to the Slice, so everybody knows it´s in progress.

Slices can be implemented multiple times.

![image](/images/assignee.png)

![image](/images/assign.png)

Generate the Command Handlers, Projections, and also Test Cases you defined.

For each finished Slice, create a Pull Request on Github to merge to main.

Goal is to have working software on main at the end of the Workshop.

## Things to try

### AI Integration

To use the AI Integration, you need to provide an Open AI or Antrophic Token.

![image](/images/ai.png)
![image](/images/ai2.png)

Choose your Model ( in case of Antrophic, put it in manually )

![image](/images/ai3.png)

#### Chat with your Model

You can now chat with your Model and ask questions.
![image](/images/ai4.png)

#### Create new Slices

Use AI to create new Slices ( extend your Model ).
Just describe your requirements.

![image](/images/ai6.png)

#### Create Screen Layouts

Use AI to create screen layouts. Just describe the screen.

#### Create Given / When / Thens with AI

Create Given / When / Thens using AI. First select a Slice,then describe the rules you want to desribe.
![image](/images/ai7.png)
