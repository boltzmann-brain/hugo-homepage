+++ 
draft = true
date = 2020-04-09T16:23:44-04:00
title = "MisSHAPpen Explanations"
description = ""
slug = "" 
tags = []
categories = []
externalLink = ""
series = []
+++

Pardon the pun. I'm writing this to summarize my takeaways from a couple of recent papers criticizing the popular SHAP method for machine learning explanations. **tl;dr:** SHAP tries to thread the needle by providing explanations that ostensibly have some 'nice' properties that make explanations easy to understand, while also being model-agnostic (applicable to even models that don't have those 'nice' properties). This tension means that it gives some unexpected results when faced with conditions like feature correlations, interactions and so on---all conditions that don't play well with the 'nice' properties that SHAP aims to emulate. 

## Why can't we have nice explanations?

So much of what motivates many ML explanation methods is attempting to simulate some of the properties that make linear models easy to understand. In a linear model, under certain conditions (link), we can attribute an influence to each variable based on its coefficient. ML experts keep trying to come up with explanation methods that emulate this but that are somehow applicable to models that have much more complex underlying mathematics. Unfortunately, we don't have a perturbation theory equivalent in ML---so the validity of these approximate explanations is determined by experiment and not based on any theoretical guarantee.

The tension between having a nice linear-like explanation and accurately emulating the underlying mathematics is a common theme in the two papers I'll discuss. A third tension that enters the mix is satisfying our intuitions about what happens when we intervene on features. In the special case of linear models under certain conditions, these tensions all resolve. But the real world is recalcitrant to simple explanations, especially when it comes to modeling highly interactive social phenomena.

## Imprisoned by intuition

There's a broader dynamic happening here at the meta-explanation level, which is our contradictory desire both to want unusual (non-human) insight from machine learning, and to want machine learning explanations to be easily explicable. As pointed out by Barocas and Selbst, part of the appeal of ML is supposed to be that it can extract insights that humans are unable to fully understand. Yet, when we validate a ML model, we often fall back on checking if the model matches our prior intuitions. I see this same dynamic going on with the debate over explanations---on the one hand, we would like explanations to match our intuitions about the underlying causal processes; on the other hand, we want to use models that are effective because they use correlations that go beyond what we know of the underlying causal processes.