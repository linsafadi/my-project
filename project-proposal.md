Degree level: Master’s
# Project proposal

## 1. The problem and goal

(Explain the problem you want to solve and why it matters. Describe what you
want to improve, how you will measure improvement, and which limits or
requirements must be respected. A short example can help someone outside your
field understand the problem.)

**The problem and goal in my project:**

The problem is "evergreening" of patents by innovative pharmaceutical companies. Evergreening is a practice where a company extends its monopoly on a drug by patenting minor modifications to a known active ingredient. These include prodrugs, crystalline forms and salt forms. The patent on the active ingredient itself eventually expires. The innovative company then keeps its monopoly through these secondary patents, which blocks competitors from producing affordable alternatives.
The goal of this project is to build an automated system that helps competitors design around these secondary patents. The system will design a new molecule or drug-delivery form that keeps the medical properties of the original active ingredient but changes the surrounding structure, so that it does not infringe the secondary patents. Examples are prodrugs (inactive forms that the body converts into the active ingredient) and salts.
Improvement will be measured by three metrics: toxicity, physical properties and efficacy. The requirement is that the new design must match or improve on all three metrics, compared with the molecules described in the patents.

## 2. The simulator

(Describe a program or model that could simulate your system and calculate what
happens under different conditions. Explain what inputs it takes and what
results it produces. State whether it can run on your computer and accept inputs
in a text file, such as JSON or YAML. If you have not chosen a simulator yet,
name an option you want to explore and explain what you need to check.)

**The simulator in my project:**

The simulators will compute the three metrics. All three tools are yet to be identified.
Simulator 1: drugability (physical stability). It checks that the molecule is physically stable enough to be used as a drug. The threshold is defined according to guidelines, which the simulator applies.
Simulator 2: toxicity. It checks that the toxicity stays within the required limit. The threshold is defined according to available regulatory guidelines, which the simulator applies.
Simulator 3: efficacy. It checks that the molecule still binds to and affects the disease target as well as the reference drug.
Each simulator takes a molecular structure as input. Each returns a score that is compared with the value for the molecules described in the patents, or with the data available online for this drug.

## 3. The agent's role

(Explain what the language-model-based agent will decide or change, and how it
will use the simulator's results to choose its next action. If known, list the
variables it may change and their allowed ranges. Explain what you expect the
language model to contribute: could a simple program that tries different
options and picks the best result achieve the same goal? Include one question
you still need to answer.)

**The agent in my project:**

The language-model-based agent will act as a hybrid patent lawyer and chemical engineer.
It reads the patent claims and identifies exactly which features are legally protected, such as a specific polymer coating or crystalline structure.
It proposes specific chemical or physical modifications, based on available data, that avoid those claims while preserving the active ingredient. Examples are adding salts or using a prodrug approach.
It sends the design through the three simulators.
If any simulator returns a score below the defined threshold (a negative result), the design goes back to the agent. The agent reasons about the failure and proposes a new design. A negative result means one of three things:
The molecule exceeds the toxicity limit.
Efficacy is below that of the reference drug.
The molecule does not meet the required stability standard.
A simple random-mutation program could not do this. It requires natural language understanding to interpret complex legal patent claims as physical and chemical constraints. It also requires reasoning about why a design failed.
One question I still need to answer: Is there a simulator that can check whether the agent has evaluated legal standards correctly, taking into account updated legal precedents and known doctrines, when judging its own chemical changes?

## Explain your project to someone outside your field

(Now describe your whole project again, as if you were explaining it to someone
from another field who has no background in your topic. For example, if you
study chemical engineering, imagine explaining it to a physicist; if you study
aeronautical engineering, imagine explaining it to someone in medicine; if you
study data science, imagine explaining it to a materials engineer. In one or two
short paragraphs, connect all three parts: the problem you want to solve, how
the simulator helps you test ideas, and what the agent will decide or change.
Use everyday language, explain any technical terms you need, and avoid
unexplained abbreviations. Do not simply copy your answers above.)

**My project in simple words:**

Imagine a company invents a chocolate cake. Anyone can read the recipe, but for a set number of years no one else is allowed to sell that cake (a patent). Those years are almost up, so soon anyone will be free to bake it.
There's a catch: the cake is always sold with icing, and that's how everyone expects to eat it. The icing recipe is public too, but it's protected by a newer receipe that won't expire for many years. The cake is the active drug ingredient; the icing is the modifications around it . So a newcomer can bake the cake but can't use the icing, which makes the market very hard to enter. This strategy is called evergreening. In my project, an AI agent acts as the competitor's recipe developer. It reads the patented icing recipe and invents a new, legal way to frost the same cake. To make sure the new icing works, it goes through three computer simulators:

1. **Stability:** the icing won't melt or fall apart.
2. **Toxicity:** it's safe to eat.
3. **Efficacy:** the cake still does its job for the customer as well as before.

The new recipe must be at least as good as the original on all three, and it must not copy the protected icing. If it fails any check, the AI goes back to the drawing board until it finds a recipe that is both legally safe and just as good.
