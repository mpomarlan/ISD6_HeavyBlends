# ISD6_HeavyBlends
Contains example OWL files for the "It Is What It Tends To Do" paper submitted to Image Schema Day 2021.

The example files are in the owl folder, and they are the following:

background_knowledge.owl: this is called the "heavyblend" ontology, and contains the agent's background knowledge

geeral_heavy.owl: contains a single axiom defining "Heavy" in a situation independent way

X_knowledge.owl: (where X is one of lid, paperweight, hammer, backpack, press) contains some axioms describing situation specific knowledge but NOT a definition for Heavy

X\_heavy.owl: contains one axiom defining a situation-dependent concept Heavy\_X

X\_problem.owl: simply imports all owl files relevant for a particular problem, and is a convenient file to load in Protege.

We are working on an implementation of the blending algorithm at the moment, so the example files are just to provide the context for the axioms mentioned in the paper, and to check that the various situation-dependent definitions of Heavy are actually subsumed by the general one. To check this, load one of the X\_problem.owl files in Protege and run an ALC-capable reasoner.

The way in which the axioms are split between the owl files is not accidental however, and is meant to show how our approach will work once the algorithm is implemented. So, to combine several situation-dependent definitions (e.g. lid, paperweight, hammer), the algorithm would be called with:

Q = {lid\_heavy.owl, paperweight\_heavy.owl, hammer\_heavy.owl} (Heavy\_Lid, Heavy\_Paperweight, Heavy\_Hammer would all be renamed to Heavy)

Oinit = background_knowledge.owl+{lid\_knowledge.owl, paperweight\_knowledge.owl, hammer\_knowledge.owl}

X = Heavy
