# Requirements in Power Platform solutions

## A fairy tale about planning and building software in a modern way

Power Apps - or Power Platform Solutions in general - are supposedly “quick and easy” to build: once the idea is in your head, the app can be “built” (by clicking or defining - or whatever 😃). It's uncomplicated and very efficient - this is software development in its most “modern” form! For _Makers_ (according to Microsoft, Makers are users who create and customize applications, workflows, and dashboards without needing extensive coding knowledge) and also consultants (the aim of the latter is to make their own customers even better with good advice), this is a really nice starting point, which is great fun and can be achieved straight-forward.

But if only it were really that easy! The promise that “every employee can build their own app - all they need is a good idea” doesn't match my experience. It is so important to **give sufficient and good thought to the requirements for an app** – not just as a consultant, even as a Maker.

## Requirements are (still) important today

This means that requirements engineering has regained the importance that is familiar from software development in its “non-modern” form (or we could say "from the old days"). Nothing has actually changed in this respect - on the contrary. Even an experienced (modern) software architect or developer will certainly confirm this: if requirements are insufficiently defined, an app will never deliver what the idea originally promised. It's usually not as “simple” or “modern” as you think!

> [!TIP] 
> **From consultant to consultant**<br>
> Your customers need _you_ – otherwise they would not have entrusted you with the task of designing and implementing a (Power Platform) app together with them. Therefore, invest in good and, above all, clean envisioning your work / app, which involves describing the project and **above all, clearly specifying the requirements**.

**Therefore, I recommend ALWAYS including the following chapters in a basic / minimalistic requirements document.**

## Outline of a leightweight requirements document (suggestion)

The requirements document should **show up the purpose of an app from a functional perspective**. It's not a solution architecture that goes deep and defines all nodes, systems and the interfaces in details. Rather, it should summarize the subject(s) of an app and highlight all functional (and non-functional) requirements in a lean structure.

This structure is leightweight and easy-to-go:

```text
1. Background
   1.1 Assumptions

2. Scope
   2.1 Context diagram
   2.2 Out of scope
   2.3 Users & roles
   2.4 Main process(es)

3. Requirements Specification
   3.1 Functional Requirements
   3.2 Non-functional Requirements
```

### Content

**1. Background**
: Insert the main goal and the purpose of the requirement specifications

- Assumptions
  : Declare all your assumptions that are relevant to know for all coming chapters. These can point to data abstractions, tools and things that are not known at the time of writing the document.

**2. Scope**
: The scope follows the question on WHAT is going to be build upon this specification. It clearly points out all the subjects that play a crucial role, without going into details. It's more about giving a guideline on the topics that will be covered in your solution / app.

- Context diagram
  : A great way to visualize the new solution / app (as a "blackbox" – without looking "into" the solution itself) and to put it in relation to the actors / users (on the left hand side) as well as the data consuming and providing systems (on the right hand side). It also should show the exchanged data between all nodes by an according arrow pointing to the appropriate direction.<br>
  $\rightarrow$ Don't use any fancy modelling language; work with boxes, stick figures and arrows.
- Out of scope
  : Declare in bullet points what this requirements do NOT cover – and therefore what features / systems the app will not cover.
- Users & roles
  : List all the users and their roles that are relevant within the scope. Describe their main tasks / intentions and their purpose of using the new app.
- Main process(es)
  : Explaining the main process(es) that are relevant for the new solutin / app as a process diagram can say more than 1000 words. The process diagram can help to understand the whole "application flow" from a high-level perspective.

**3. Requirements Specification**
: summarizes the requirements in detail. These include:

- Functional Requirements
  : The functional requirements describe the _capabilities_, _performance_, _responsibilities_ and beh_avior of the functional units or your new app from a technical perspective (system functionality). They can be formulated as _User Stories_ or _Use Cases_ (without wanting to appear purist in "terms and conditions": take what you like better – depending on your personal preference) and presented as a table.<br>
  $\rightarrow$ If the requirements are formulated as use cases, a graphical representation as a use case diagram (UML) is recommended. I also recommend that you always describe use cases according to the style defined by [Alistair Cockburn](https://alistaircockburn.com/de).

  As a best-practise recommendation, requirements should contain the following (minimum) properties:

  - **Number:** unique designation / numbering
  - **Description:** Description of what the requirement is about
  - **Participants:** List of users and roles to which the requirement applies
  - **Acceptance criteria:** Points that must be fulfilled for the requirement to be considered fulfilled by the customer

    > Without acceptance criteria, there would be an increased risk of overlooking or misinterpreting essential functionalities.

- Non-functional Requirements
  : Non-functional requirements determine the architecture of the app by ◊defining quality attributes. These can be summarized as a table in the form of a scenario in the following specification:

  - **Source:** Source of the action
  - **Trigger:** actual action or trigger of the action
  - **Artifact:** affected parts of the system / app
  - **Response:** (type of) reaction of the system to the trigger
  - **Response metric:** criterion for how the response can be measured

  > It is worth using this scheme so that – especially from the customer's point of view - no discussions arise due to misinterpretations.
