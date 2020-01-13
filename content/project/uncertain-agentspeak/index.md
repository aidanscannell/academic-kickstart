---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Uncertain Agentspeak"
summary: "During the first (taught) year of the FARSCOPE CDT program I conducted my masters thesis under the supervision of Professor Weiru Liu and Dr Kevin McAreavey titled “Extending BDI Agents to Model and Reason with Uncertainty”. I implemented and extended the AgentSpeak(L) (agent-based programing) language to enable agents to model and reason with uncertainty in a computationally efficient manner."
authors: ["Aidan Scannell"]
tags: ["ai", "java"]
categories: []
date: 2018-09-20

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_pdf: "masters_dissertation_BDI-updated.pdf"
url_code: "https://github.com/aidanscannell/uncertain-agentspeak"
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
During the first (taught) year of the FARSCOPE CDT program I conducted my masters thesis under the supervision of Professor Weiru Liu and Dr Kevin McAreavey titled “Extending BDI Agents to Model and Reason with Uncertainty”.

This work attempted to extend BDI agents, in particular AgenSpeak(L) agents, to model and reason with uncertain information. The extended AgentSpeak(L) language uses epistemic states to model an agent’s uncertain beliefs about the world. The implemented extended AgentSpeak(L) language effectively allows agents to model and reason with uncertainty in a computationally efficient manner. Agents are capable of modelling their beliefs as either probabilistic or possibilistic compact epistemic states and the implementation of epistemic states provides a base for easily implementing instantiations of different uncertainty theories, e.g. Demspter-Shafer theory.

A language L∏ for constructing formulas that can reason over these uncertain beliefs is detailed. This language is capable of forming sentences of the form: psi is more plausible than phi (psi &gt; phi). This language is used to construct agent’s plan contexts and test goals, which were previously just a conjunction of literals. This provides the agents with extended reasoning capabilities. The agent’s belief base was modelled as a Global Uncertain Belief (GUB), acting as a set of formulas from the language L∏. This enables agents to select applicable plans from the set of relevant plans by querying if a logical formula is entailed by the GUB.

A development environment for defining and simulating MASs written in the extended AgentSpeak(L) language is introduced. A simulation environment that a programmer can easily extend to a specific scenario is detailed. It uses a multi-threaded approach to enable multiple agents to run on a single machine and ensures that agents act on and perceive an environment without any thread interference or memory inconsistency issues. All of the work in this project is then brought together in a mars exploration MAS that demonstrates the extended modelling and reasoning capabilities as well as the power of the development environment as a whole.

### Short Intro &amp; Background

Intelligent autonomous systems offer great potential, however, the development of systems that are robust enough to operate in the real-world is extremely difficult. There is currently a lack of frameworks for modelling and reasoning with uncertainty. Traditional Belief-Desire-Intention (BDI) architectures for designing and developing intelligent agent systems are less adequate for modelling uncertain knowledge, beliefs and evidence, whilst the real-world is almost always pervaded with uncertainty (Kwisthout and Dastani 2006).

Architectures such as the Belief-Desire-Intention (BDI) architecture (Bratman 1987) allow dynamic knowledge and beliefs to be explicitly modelled through decomposing a complex problem into a set of autonomous and interacting agents. BDI agents consist of their own ’Beliefs’, ’Desires’ and ’Intentions’; beliefs model the agent’s understanding of the environment, desires represent the states that the agent wants to achieve and intentions are the desires that the agent has acted upon. Using these, the agents are able to respond accordingly to the situations that they find themselves in. In recent years, BDI agents have received a great deal of interest due to their potential for replacing current methods for analysing, designing and implementing complex, large-scale intelligent systems (Herzig et al. 2017).

Many agent-based programming languages based on the BDI architecture have been proposed over the years. Although these languages have successfully been used to model some modern systems, they are not well-suited to model more complex systems as they are not able to model or reason about uncertain information. In most real-world scenarios, agent’s beliefs do not take the form of binary true or false values but rather are uncertain. Uncertainty can arise from many different sources, for example, sensor noise or incomplete information. The computational complexity of uncertainty theories extends this issue further as BDI agents rely on reactive behaviour and most uncertainty theories do not consider tractability.

Uncertain input can be dealt with in different ways: (i) it can act as a constraint that must be satisfied after belief revision, or (ii) it can be treated as a new belief with an associated weight. Ma and Liu (2011a) proposed a framework for dealing with uncertainty where new information from multiple sources is used to strengthen or weaken existing beliefs and not necessarily cancel out existing beliefs. However, this framework relies on semantic belief change operators, restricting it’s practical applicability due to it’s computational cost. There have been approaches suggested that use syntactic operators, however, these are limited to classical beliefs (Alchourron, Gardenfors, and Makinson 1985; Nebel 1995). There are far less approaches that use syntactic operators for iterated belief revision. Ordinal Conditional Functions (OCF) are a popular approach to defining epistemic states (Spohn 1988) and Williams (1995) proposed a syntactic representation of OCF. However, this representation is not a general framework and leads to issues when attempting to instantiate into different uncertainty theories. Bauters et al. (2017) propose an approach for managing different sources of uncertainty in a BDI framework. They offer a new approach for modelling the beliefs of an agent as well as a novel syntactic approach for revising beliefs with uncertain information. This paper offers the theoretical foundations and the base for a lot of the work presented here.
