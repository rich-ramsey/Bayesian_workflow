Readme

## Background and aims ##

This file tries to take aspects of the Bayesian workflow paper by [Gelman and 
colleagues](http://arxiv.org/abs/2011.01808) and apply them to an example scenario in experimental psychology / cognitive neuroscience.

The workflow that I present is broken down into several different stages. Each stage has its own markdown file. I found it easier to organise things in this way. This means that each script represents a self-contained module or sub-process, which is taken from the overall workflow. The different scripts are detailed below.

**One important caveat**. This is not an exhaustive or complete application of the Bayesian workflow that was outlined by Gelman and colleagues. It is simply a selection from a set of processes that are then applied to an example in experimental psychology. I've found it useful to think about things in this way and so I wanted to write it down. There is much more richness and subtlety in the article than I have tried to convey in these scripts. There is also an important iterative dimension that Gelman and co. focus on, which I don't really talk about in these scripts, even though the scripts themselves developed in an iterative process. The iterative part is important though because Gelman and co. emphasise how cycling through different stages as knowledge and understanding develops is part of the workflow. See Figure 1 in the above paper for a visualisation of the non-serial and iterative nature of the workflow.

Anyway, it's a really good paper, and I didn't want to spoil all the fun for you. So, just go and read it.

### A few quotes from Gelman & Co. to set the scene... ###

Here is a snippet from page 3 of Gelman and Co. that distinguishes Bayesian inference from a Bayesian workflow, which I find instructive to set the scene:

> *Bayesian inference* is just the formulation and computation of conditional probability or probability densities, p(θ|y) ∝ p(θ)p(y|θ). *Bayesian workflow* includes the three steps of model building, inference, and model checking/improvement, along with the comparison of different models, not just for the purpose of model choice or model averaging but more importantly to better understand these models. That is, for example, why some models have trouble predicting certain aspects of the data, or why uncertainty estimates of important parameters can vary across models. Even when we have a model we like, it will be useful to compare its inferences to those from simpler and more complicated models as a way to understand what the model is doing.


And they go on to say on page 4...


> In a typical Bayesian workflow we end up fitting a series of models, some of which are in retrospect poor choices (for reasons including poor fit to data; lack of connection to relevant substantive theory or practical goals; priors that are too weak, too strong, or otherwise inappropriate; or simply from programming errors), some of which are useful but flawed (for example, a regression that adjusts for some confounders but excludes others, or a parametric form that captures some but not all of a functional relationship), and some of which are ultimately worth reporting. The hopelessly wrong models and the seriously flawed models are, in practice, unavoidable steps along the way toward fitting the useful models. Recognizing this can change how we set up and apply statistical methods.


Finally, also on page 4, Why do we need a Bayesian workflow?

>We need a Bayesian workflow, rather than mere Bayesian inference, for several reasons: \ 
<br/><br/>
        - Computation can be a challenge, and we often need to work through   various steps including fitting simpler or alternative models, approximate computation that is less accurate but faster, and exploration of the fitting process, in order to get to inferences that we trust. \
        - In difficult problems we typically do not know ahead of time what model we want to fit, and even in those rare cases that an acceptable model has been chosen ahead of time, we will generally want to expand it as we gather more data or want to ask more detailed questions of the data we have. \
        - Even if our data were static, and we knew what model to fit, and we had no problems fitting it, we still would want to understand the fitted model and its relation to the data, and that understanding can often best be achieved by comparing inferences from a series of related models. \
        - Sometimes different models yield different conclusions, without one of them being clearly favourable. In such cases, presenting multiple models is helpful to illustrate the uncertainty in model choice.

## Project organisation and folder structure ##

### basic structure ###

The overall Bayesian workflow that I outline here will be split up into several sections, as follows:

1. prior predictions.
2. planning for power/precision via simulation.
3. build a series of models and perform model checking and model comparison.
4. evaluate the posterior.

### files ###

There are four main R Markdown files, each of which is associated with a distinct role in the workflow (1-4 above).

1. Prior.Rmd

This file samples the prior distribution to generate predictions. The main aim
is to check to see if the priors generate values that look sensible, given our
domain knowledge of the type of data.

2. Plan.Rmd

This file simulates a series of datasets and build models to estimate the likely power and precision of future experiments. It is one way to plan sample sizes, for example.

3. Model.Rmd

This file builds a series of Bayesian regression models, performs model checks 
and model comparisons.

4. Post.Rmd

This file visualises and tabulates parameters from the posterior distributions of model/s that were built in the model.Rmd file.

### folders ###

There are three main folders:

**/data/**

**/figures/**

**/models/**

These folders have self-explanatory titles. Inside each one, there may be sub-directories, which hopefully also have sensible titles. e.g., a sub-directory called /plan/ holds figures/models/data from the plan.Rmd file and phase of the workflow.

## Overview of the gaze-cueing task ##

We use a task from experimental psychology that involves speeded responses and the recording of reaction time and accuracy. The basic task is based on the Posner cueing paradigm [Posner, 1980](https://doi.org/10.1080/00335558008248231), which uses arrows as a central directional cue (left or right) and targets that can either be congruent (same as the location cued by the arrow) or incongruent (opposite to the location cued by the arrow). Typically, a reaction time cost is observed in the incongruent compared to congruent condition.

In this workflow, the example we use is based on this Posner cueing paradigm, but it uses faces and eye-gaze as a directional cue instead of arrows (see, for example: [Driver et al., (1999)](http://www.informaworld.com/10.1080/135062899394920); [Langton & Bruce, (1999)](https://doi.org/10.1080/135062899394939); And for a review, see: [Frischen et al., (2007)](https://psycnet.apa.org/record/2007-09203-007)).
