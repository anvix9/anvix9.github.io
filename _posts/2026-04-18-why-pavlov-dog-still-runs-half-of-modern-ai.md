---
layout: post
title:  "Why Pavlov's Dog Still Runs Half of Modern AI, and Why That's a Problem"
date:   2025-04-18
last_modified_at: 2025-04-18
categories: [Learning Theory]
tags: [Philosophy of science, AI, Machine learning, science, Learning Theories]
---

<br/><br/>

# Series Progress
<br/>

- <strong>[Post #1: Why Pavlov's Dog Still Runs Half of Modern AI, And Why That's a Problem](#)</strong>
- Post #2: Why Syntax Still Matters in the Transformer Era *(coming soon)*
- Post #3: The Unsolved Problem at the Heart of AI, Systematicity *(coming soon)*
- Post #4: What Would It Mean for a Machine to Genuinely Understand Language? *(coming soon)*

<br/>
<figure style="text-align: center;">
    <img src="https://cdn.britannica.com/31/166131-004-9A7E454E.jpg" alt="Man sitting on a bench" width="200"/>
    <br />
    <figcaption>Ivan Pavlov.
    </figcaption>
</figure>
<br/><br/>

# Introduction
<br/>

<p style="text-align: justify;">
There is a dog that changed the history of science. And without knowing it, it also shaped the history of artificial intelligence.
</p>
<p style="text-align: justify;">
You probably know the story. Ivan Pavlov, in the late 19th century, was studying digestion in dogs. He noticed something odd: his dogs would start salivating not just when food arrived, but when they heard the footsteps of the person who brought the food. The stimulus was not the food. It was the <em>association</em> with food. So he ran an experiment: ring a bell, present food, repeat. After enough repetitions, the bell alone was enough. The dog salivated at a sound.
</p>

<p style="text-align: justify;">
Pavlov called this <strong>conditioning</strong>. Psychologists called it <strong>Behaviorism</strong>. And somewhere along the line, computer scientists built it into the foundations of what we now call Reinforcement Learning.
</p>

<p style="text-align: justify;">
I have been spending a lot of time lately thinking about where our ideas about machine learning actually come from. Not the mathematics, not the architectures, but the <em>deeper assumptions</em>, the ones so old they became invisible. What I found is that modern AI is, in large part, from philosophy but most concretely from psychology in disguise. And that disguise has hidden some fundamental problems from us.
</p>

<p style="text-align: justify;">
This is the first post in a series about learning paradigms, where they come from, how they became machine learning, and what they cannot do.
</p>

<br/><br/>

# The Three Paradigms That Built Machine Learning

<p style="text-align: justify;">
Psychology spent most of the 20th century arguing about how learning works. Three major schools emerged: Behaviorism, Cognitivism, and Constructivism. Each one captured something real. Each one also missed something important. And without realizing it, the field of artificial intelligence inherited all three, including the parts that were missing.
</p>

<br/>

## Behaviorism: the Black Box School
<br/>
<figure style="text-align: center;">
    <img src="https://static.independent.co.uk/s3fs-public/thumbnails/image/2014/07/15/18/pg-32-mod-art-theiner.jpg" width="300"/>
    <br />
    <figcaption>'Black Square' from Kasimir Malevich.
    </figcaption>
</figure>
<br/> 

<p style="text-align: justify;">
Behaviorism made a radical bet: the mind is a black box, and we should not try to open it. What matters is what goes <em>in</em> and what comes <em>out</em>. Stimulus, response. Stimulus, response.
</p>

<p style="text-align: justify;">
Pavlov's dog is the poster child. But the deeper figure is B.F. Skinner, who extended the idea to humans. Want a pigeon to press a lever? Reward it when it does. Want a student to memorize facts? Reward correct answers. The internal experience, what the pigeon <em>thinks</em>, what the student <em>feels</em>... is irrelevant. What matters is the observable behavior.
</p>


<p style="text-align: justify;">
The connection to Reinforcement Learning is almost embarrassingly direct. An agent acts in an environment. It receives a reward or a punishment. It adjusts its policy. Repeat. There is no internal model of the world, no introspection, no understanding but only the optimization of a reward signal. Some few factors of the environment condition the agent just as Pavlov conditioned his dog.
</p>

<p style="text-align: justify;">
This is kind of powerful. Reinforcement Learning has produced game-playing agents that beat world champions at Go and chess and StarCraft. It has trained robots to walk across uneven terrain. The conditioning paradigm <em>works</em> for well-defined environments and conditions with clear reward signals.
</p>

<p style="text-align: justify;">
But here is the problem Behaviorism never solved, and Reinforcement Learning has not solved either: <strong>what happens when the reward signal runs out?</strong> A dog conditioned to salivate at a bell does not understand bells. It cannot generalize its knowledge of bells to door chimes or alarm clocks or simply the <strong>word</strong> "ding." It has learned an association, not a structure. And associations, without structure, cannot adapt to genuinely new situations.
</p>

<p style="text-align: justify;">
Modern RL systems face the same wall. Change the environment slightly for example move the reward, alter the physics, introduce a new obstacle, and the agent collapses. It has not learned the <em>rules</em> of the domain. It has learned the <em>statistics</em> of the training distribution. And when the distribution shifts, the association can surprisingly breaks in ways we can meditate on.
</p>

<br/>

## Cognitivism: Opening the Black Box
<br/>
<figure style="text-align: center;">
    <img src="https://www.stargate-fusion.com/uploads/files/block/1129/2a14e74689246374eaff-block.jpg?v=363aa53d8114f38752c09ab3791120a8" width="300"/>
    <br />
    <figcaption>Pandora Box.
    </figcaption>
</figure>
<br/> 


<p style="text-align: justify;">
By the late 1950s, psychologists were frustrated. Behaviorism had left out too much. It could not explain language acquisition. It could not explain how humans solve problems they have never seen before. It could not explain <em>thinking</em>.
</p>

<p style="text-align: justify;">
Cognitivism opened the black box. It said: the mind processes information. It receives inputs, organizes them, stores them, and retrieves them. Learning is not just stimulus-response, it is the active transformation of information into organized knowledge.
</p>

<p style="text-align: justify;">
This sounds quite obvious now. That is because Deep Learning is built almost entirely on cognitivist intuitions.
</p>

<p style="text-align: justify;">
Think about what a neural network actually does. The input layer receives raw data. Each subsequent layer transforms it, extracts features, abstracts patterns, compresses representations. The final layer produces an output. This is almost a direct translation of the cognitivist framework: receive, organize, store, retrieve. Even the specific techniques have cognitivist equivalents: attention mechanisms echo the psychology of selective attention; Long Short-Term Memory networks echo the study of working memory; meta-learning echoes the cognitivist idea of <em>learning to learn</em>.
</p>

<br/>
<p style="text-align: justify;">
Yet Cognitivism had its own fatal flaw, one that Deep Learning inherits perfectly: <strong>the internal representations are opaque.</strong> Cognitivism could describe the functional stages of information processing but could not directly observe them. Deep Learning produces embeddings that encode statistical structure but cannot be interpreted in terms of rules, logic, or meaning. We can measure what the network does. We cannot explain <em>why</em> it does it or predict when it will fail.
</p>

<p style="text-align: justify;">
There is something uncomfortable about the fact that the most successful AI systems in history produce results no one fully understands. We call this <strong>the interpretability problem</strong>. But it is not really a technical problem. It is kind of a philosophical one, inherited from Cognitivism's fundamental limitation: it opened the black box but could not see clearly inside it.
</p>

<br/>

## Constructivism: the Learner Builds the World
<br/>
<br/>
<figure style="text-align: center;">
    <img src="https://m.media-amazon.com/images/I/71BaTvlPz9L._AC_UF894,1000_QL80_.jpg" width="300"/>
    <br />
    <figcaption>Evolution theory (from Darwin).
    </figcaption>
</figure>
<br/> 

<p style="text-align: justify;">
Constructivism takes a different angle. It says: knowledge is not received, it is <em>constructed</em>. The learner does not passively absorb information, the learner actively builds representations of the world by connecting new experience to what they already know.
</p>

<p style="text-align: justify;">
For example Jean Piaget, the Swiss developmental psychologist, watched children learn for decades. He noticed that they do not simply accumulate facts. They build <em>schemas</em>, mental frameworks, and they update those schemas when experience contradicts them. A child who thinks all four-legged animals are dogs will eventually encounter a cat, experience a small crisis, and revise the schema. This process of assimilation and accommodation is what learning actually looks like from the inside.
</p>

<p style="text-align: justify;">
The connection to AI is more diffuse here, which is interesting. Constructivism's fingerprints are everywhere but nowhere explicitly acknowledged.
</p>

<p style="text-align: justify;">
Curriculum learning, for instance which the technique of presenting training examples in order from simple to complex is pure Constructivism. The model builds on what it already knows. Transfer learning assumes that a model trained on one domain can carry its representations into another, which is exactly the constructivist idea that prior knowledge scaffolds new understanding, that knowledge is built on top of knowledge, not nothing at all. Even the recent interest in compositional generalization, can a model that knows A and knows B understand A+B without having seen it? is a constructivist question in disguise.
</p>

<br/>
<p style="text-align: justify;">
But here is what Constructivism never quite solved, and AI has not solved either: <strong>how does the learner know when to update a schema versus when to discard it entirely?</strong> Piaget described the process. He did not formalize the logic. And machine learning systems, despite their sophistication, still lack a principled account of when to generalize from prior knowledge and when to start fresh. This shows up as catastrophic forgetting or hallucination, the phenomenon where a neural network, trained on a new task, loses its ability to perform the old one or mess them up. The network has no stable schema architecture. It has only weights.
</p>

<br/><br/>

# What the Three Paradigms Have in Common and What None of Them Solved yet
<br/>

<p style="text-align: justify;">
Looking at this together, something becomes clear. Each paradigm described a real aspect of learning:
</p>

<ul>
  <li>Behaviorism captured how conditioning shapes behavior through environment</li>
  <li>Cognitivism captured how information is processed, organized, and retrieved</li>
  <li>Constructivism captured how prior knowledge scaffolds the acquisition of new knowledge</li>
</ul>

<br/>
<p style="text-align: justify;">
And machine learning has absorbed all three:
</p>

<ul>
  <li>Reinforcement Learning is applied Behaviorism</li>
  <li>Deep Learning is applied Cognitivism</li>
  <li>Curriculum and Transfer Learning are applied Constructivism</li>
</ul>

<br/>
<p style="text-align: justify;">
But there is something none of them solved yet, and something AI has therefore also not solved. None of them explained how a learner produces <em>systematic</em> behavior as a <em>necessary consequence</em> of its architecture (quite an obscure sentence right?).
</p>

<br/>
<p style="text-align: justify;">
What do I mean by systematic? Here is a simple example. If you understand the sentence "John loves Mary," you automatically understand "Mary loves John." (the possible understanding of it) Not because you were taught that sentence. Not because you have seen it before. But because you understand the <em>structure</em> — subject, verb, object — and that structure applies uniformly to anything you can put in those positions.
</p>

<br/>
<p style="text-align: justify;">
This is so obvious it seems trivial. But it is <strong>not trivial at all</strong>. It is one of the deepest unsolved problems in cognitive science and artificial intelligence. A Behaviorist system could learn to parse "John loves Mary" without ever being able to generalize to "Mary loves John." (GPT4 and some older ones can, but on surface, this is due to what we call a recursive Language of Thoughts, but we will come to in next posts) A Cognitivist system could process both sentences but might not guarantee it would handle a third structurally related sentence it has never seen. A Constructivist system might build the right schema or might not, depending on the training data.
</p>


<p style="text-align: justify;">
The point is: none of these architectures <em>guarantees</em> systematic behavior. They can produce it. They can fail to produce it. The theory is silent on which outcome obtains.
</p>


<p style="text-align: justify;">
This is the problem my research is trying to address but that is for another post also :).
</p>

<br/><br/>

# Why This Matters Right Now
<br/>

<p style="text-align: justify;">
You might wonder: does any of this matter practically? We have GPT-4, we have Claude, we have systems that pass bar exams and write code and translate between languages. Why go back to Pavlov?
</p>

<br/>
<p style="text-align: justify;">
Because these systems fail in ways that are predictable once you understand where they came from.
</p>

<br/>
<p style="text-align: justify;">
They fail when the distribution shifts, because they are Behaviorist at heart, conditioned on statistics rather than structured knowledge. They fail at compositional generalization and systematicity because their Cognitivist architecture compresses information without guaranteeing structural preservation. They fail at genuine adaptation because the Constructivist scaffolding is implicit in the training process rather than explicit in the architecture.
</p>

<br/>
<p style="text-align: justify;">
The techniques we use to patch these failures like Chain-of-Thought prompting, Retrieval-Augmented Generation, Reinforcement Learning from Human Feedback or newly seen Constitutional AI, are themselves borrowed from these same psychological or philosophy paradigms, applied as corrections after the fact. They work to a degree. But they do not resolve the underlying issue. They are treatments for symptoms, not cures for causes.
</p>

<br/>
<p style="text-align: justify;">
Understanding where the ideas come from is not nostalgia. It is diagnosis.
</p>

<br/><br/>

# Conclusion
<br/>

<p style="text-align: justify;">
Pavlov's dog is still running. Every time a model learns by trial and error with a reward signal, it is Pavlov's dog. Every time a neural network transforms input into layered representations, it is Cognitivism in silico. Every time a curriculum is designed to present easier examples before harder ones, Piaget is somewhere in the room.
</p>

<p style="text-align: justify;">
This is not a criticism. These are genuine insights, translated into powerful tools. But the limits of those insights are also the limits of those tools.
</p>

<p style="text-align: justify;">
The next post in this series will go deeper into one specific problem that emerges from all three paradigms, the problem of <em>systematicity</em> and why solving it requires something that none of Behaviorism, Cognitivism, or Constructivism could provide.
</p>

<p style="text-align: justify;">
Until then, I will leave you with a question that I find genuinely interesting: if a system can learn to behave as if it understands something without actually understanding it, how would you tell the difference?
</p>

<p style="text-align: justify;">
<em>This post is part of a series on learning theory, artificial intelligence, and the problem of machine understanding. The ideas here are developed in depth in my ongoing PhD research at CIC-IPN and in my paper <a href="https://arxiv.org/abs/2603.18203">"How Psychological Learning Paradigms Shaped and Constrained Artificial Intelligence"</a> (arXiv:2603.18203).</em>
</p>

<p style="text-align: justify;">
<em>Next: Why neither neural networks nor symbolic systems are systematic by design, and what that means for AGI.</em>
</p>

<br/><br/>

---

# References
<br/>

## Behaviorism and Conditioning
<br/>

<p style="text-align: justify;">
Pavlov, I. P. (1927). <em>Conditioned Reflexes: An Investigation of the Physiological Activity of the Cerebral Cortex.</em> Oxford University Press.
</p>

<p style="text-align: justify;">
Skinner, B. F. (1938). <em>The Behavior of Organisms: An Experimental Analysis.</em> Appleton-Century-Crofts.
</p>

<p style="text-align: justify;">
Watson, J. B. (1913). Psychology as the behaviorist views it. <em>Psychological Review, 20</em>(2), 158–177.
</p>

<br/>

## Cognitivism
<br/>

<p style="text-align: justify;">
Ertmer, P. A., & Newby, T. J. (1993). Behaviorism, cognitivism, constructivism: Comparing critical features from an instructional design perspective. <em>Performance Improvement Quarterly, 6</em>(4), 50–72.
</p>

<p style="text-align: justify;">
Miller, G. A. (1956). The magical number seven, plus or minus two: Some limits on our capacity for processing information. <em>Psychological Review, 63</em>(2), 81–97.
</p>

<p style="text-align: justify;">
Neisser, U. (1967). <em>Cognitive Psychology.</em> Appleton-Century-Crofts.
</p>

<br/>

## Constructivism
<br/>

<p style="text-align: justify;">
Piaget, J. (1952). <em>The Origins of Intelligence in Children.</em> International Universities Press.
</p>

<p style="text-align: justify;">
Vygotsky, L. S. (1978). <em>Mind in Society: The Development of Higher Psychological Processes.</em> Harvard University Press.
</p>

<p style="text-align: justify;">
Dewey, J. (1938). <em>Experience and Education.</em> Macmillan.
</p>

<br/>

## Machine Learning Connections
<br/>

<p style="text-align: justify;">
Sutton, R. S., & Barto, A. G. (2018). <em>Reinforcement Learning: An Introduction</em> (2nd ed.). MIT Press.
</p>

<p style="text-align: justify;">
Hochreiter, S., & Schmidhuber, J. (1997). Long short-term memory. <em>Neural Computation, 9</em>(8), 1735–1780.
</p>

<p style="text-align: justify;">
Bengio, Y., Louradour, J., Collobert, R., & Weston, J. (2009). Curriculum learning. <em>Proceedings of the 26th Annual International Conference on Machine Learning (ICML)</em>, pp. 41–48.
</p>

<p style="text-align: justify;">
Michalski, R. S., Carbonell, J. G., & Mitchell, T. M. (Eds.). (1983). <em>Machine Learning: An Artificial Intelligence Approach.</em> Tioga Publishing.
</p>

<br/>

## The Systematicity Problem
<br/>

<p style="text-align: justify;">
Fodor, J. A., & Pylyshyn, Z. W. (1988). Connectionism and cognitive architecture: A critical analysis. <em>Cognition, 28</em>(1–2), 3–71.
</p>

<p style="text-align: justify;">
Aizawa, K. (1997). Explaining systematicity. <em>Mind & Language, 12</em>(2), 115–136.
</p>

<p style="text-align: justify;">
Lake, B. M., & Baroni, M. (2018). Generalization without systematicity: On the compositional skills of sequence-to-sequence recurrent networks. <em>Proceedings of the 35th International Conference on Machine Learning (ICML)</em>, pp. 2873–2882.
</p>

<br/><br/>
