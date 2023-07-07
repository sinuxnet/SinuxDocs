# Software Engineering

### A practitioner's Approach

###### Rogger S. Pressman, Bruce R. Maxim

---

## Chapter 1 - Software & software Engineering

**Computer Software** is a work **<u>product</u>** that software professionals build and then **<u>support</u>** over many years.

**Software Engineering** encompasses a process, a collection of methods (practice), and an array of tools that allow professionals to build highquality computer software.

you must recognize a few simple realities:

* A concerted effort should be made to understand the problem before a software solution is developed.

* Design has become a pivotal activity

* Software should exhibit high quality.

* Software should be maintainable

**Result:** Software in all its forms and across all its application domains should be engineered.

## 1.1 The Nature of Software

### 1.1.1 Defining Software

Software is: **<u>(1) instructions</u>** (computer programs) that when executed provide desired features, function, and performance; **<u>(2) data structures</u>** that enable the programs to adequately manipulate information; and **<u>(3) descriptive information</u>** in both hard copy and virtual forms that describes the operation and use of the programs.

1. Instruction (programs)

2. Data structures

3. Descriptive Information (Documentation)

Software is a logical rather than a physical system element. Therefore, software has one fundamental characteristic that makes it considerably different from hardware: _Software doesn’t “wear out.”_ 

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Software%20Engineering\images\Failure%20curve%20for%20hardware.jpg) 

**Failure curve for hardware**

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Software%20Engineering\images\Failure%20curve%20for%20software.jpg)

**Failure curve for software**

In software, Undiscovered defects will cause high failure rates early in the life of a program.

NOTE: Software doesn’t wear out. But it does deteriorate!

This seeming contradiction can best be explained by considering the actual curve in Figure. During its life, software will undergo change. As changes are made, it is likely that errors will be introduced, causing the failure rate curve to spike as shown
in the “actual curve”. Before the curve can return to the original steadystate failure rate, another change is requested, causing the curve to spike again. Slowly, the minimum failure rate level begins to rise—the software is deteriorating due to change.

### 1.1.2 Software Application Domains

* **System software**

* **Aplication software**

* **Engineering/scientific software**

* **Embedded software**

* **Product-line software**

* **Web/mobile applications**

* **Artificial intelligence software**

### 1.1.3 Legacy Software

As time passes, legacy systems often evolve for one or more of the following reasons:

* The software must be adapted to meet the needs of **new computing  environments or technology.**

* The software must be enhanced to implement **new business requirements.**

* The software must be extended to make it work with other more **modern systems or databases**.

* The software must be **re-architected** to make it viable within an evolving
  computing environment.

## 1.2 Defining The Discipline

**IEEE defention for software engineering:**  The application of a systematic, disciplined, quantifiable approach to the development, operation, and maintenance of software.

And yet, a “systematic, disciplined, and quantifiable” approach applied by one software team may be burdensome to another. We need discipline, but we also need adaptability and agility.

![](D:\OneDrive\z%20-%20My%20Docs\md%20docs\Software%20Engineering\images\Software%20Engineering%20Layers.jpg)

**Software Engineering Layers**

Software engineering is a layered technology.

1. Any engineering approach (including software engineering) must rest on an organizational commitment to **quality**. The bedrock that supports software engineering is a **quality focus**.

2. The foundation for software engineering is the **process** layer. Process defines a framework that must be established for effective delivery of software engineering technology.

3. Software engineering methods provide the technical how-to’s for building software. (communication, requirements analysis, design modeling, program construction, testing, and support)

4. Software engineering tools provide automated or semi-automated support for the process and the methods.

## 1.3 The Software Process

**Process:** A collection of activities, actions, and tasks that are performed when some work product is to be created.

* **<u>Activitiy</u>:** An activity strives to achieve a broad objective (e.g., communication with stakeholders) and is applied regardless of the application domain, size of the project, complexity of the effort, or degree of rigor with which software engineering is to be applied.

* **<u>Action</u>:** An action (e.g., architectural design) encompasses a set of tasks that produce a major work product (e.g., an architectural model).

* **<u>Task</u>:** A task focuses on a small, but well-defined objective (e.g., conducting a unit test) that produces a tangible outcome.

### 1.3.1 The Process Framework

The process framework encompasses a set of *umbrella activities* that are applicable across the entire software process.

 A generic process framework for software engineering encompasses five activities:

* **<u>Communication</u>**: To undrestand stakeholders’ **objectives**, gather **requirements** to define software **features** and **functions**.

* **<u>Planning</u>:** To describing the technical **tasks** to be conducted, the **risks** that are likely, the **resources** that will be required, the work products to be **produced**, and a work **schedule**.

* **<u>Modeling</u>:** To better understand software requirements and the design that will achieve those requirements.

* **<u>Construction</u>:** It is **code generation** and **testing**  that is required to uncover errors in the code.

* **<u>Deployment</u>:**  To be **delivered to the customer** who evaluates the delivered product and provides **feedback** based on the **evaluation**.

NOTE: The details of the software process will be quite different in each case of software development projeccts, but the <u>framework activities remain the same</u>.

### 1.3.2 Umbrella Activities

Software engineering process framework activities are complemented by a number of umbrella activities.

Typical umbrella activities include:

* **<u>Software project tracking and control.</u>**
  
  * To assess progress against the project plan
  
  * To  take any necessary action to maintain the schedule

* **<u>Risk management. </u>**
  
  * To assesses risks that may affect the outcome of the project or the quality of the product.

* **<u>Software quality assurance.</u>**
  
  * To defines and conducts the activities required to ensure software quality.

* **<u>Technical reviews. </u>**
  
  * To assess software engineering work products in an effort to uncover and remove errors before they are propagated to the next activity.

* **<u>Measurement.</u>**
  
  * To defines and collects process, project, and product measures that assist the team in delivering software that meets stakeholders’ needs.

* **<u>Software configuration management.</u>**
  
  * To manages the effects of change throughout the software process.

* **<u>Reusability management.</u>**
  
  * To Defines criteria for work product reuse (including software components) and establishes mechanisms to achieve reusable components.

* **<u>Work product preparation and production.</u>**
  
  * Encompasses the activities required to create work products such as models, documents, logs, forms, and lists

### 1.3.3 Process Adaption

A process adopted for one project might be significantly different than a process adopted for another project.

## 1.4 Software Engineering Practice

### 1.4.1 The Essence of Practice

1. Understand the problem (communication and analysis).

2. Plan a solution (modeling and software design).

3. Carry out the plan (code generation).

4. Examine the result for accuracy (testing and quality assurance).

### 1.4.2 General Principles

**Principle:** An important underlying law  or assumption required in a system of thoght

Principles help you establish a mind-set for solid software engineering practice.

**<u>The First Principle: *The Reason It All Exists</u>***

A software system exists for one reason: <u>*to provide value to its users</u>*. 

Before doing any processes or tasks, ask yourself questions such as: 

                                    “*Does this add real value to the system?*” 

If the answer is no, don’t do it. All other principles support this one.

**<u>The Second Principle: *KISS (Keep It Simple, Stupid!)*</u>**

*All design should be as simple as possible, but no simpler.*

This is not to say that features should be discarded in the name of simplicity. Indeed, the more elegant designs are usually the simpler ones. Simple does not mean “quick and dirty.”

**<u>The Third Principle: *Maintain the Vision*</u>**

*A clear vision is essential to the success of a software project.*

**<u>The Fourth Principle: *What You Produce, Others Will Consume*</u>**

*Always specify, design, document, and implement knowing someone else will have to understand what you are doing.*

**<u>The Fifth Principle: _Be Open to the Future_</u>**

*Never design yourself into a corner*. Always ask “what if,” and prepare for all possible answers by creating systems that solve the general problem, not just the specific one.

**<u>The Sixth Principle: *Plan Ahead for Reuse*</u>**

*Planning ahead for reuse reduces the cost and increases the value of both the reusable components and the systems into which they are incorporated.*

**<u>The Seventh Principle: *Think!*</u>**

*Placing clear, complete thought before action almost always produces better results.* When you think about something, you are more likely to do it right. You also gain knowledge about how to do it right again. If you do think about something and still do it wrong, it becomes a valuable experience.

When clear thought has gone into a system, value comes out.

# 
