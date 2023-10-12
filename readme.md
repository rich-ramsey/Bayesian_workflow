readme

## Background and aims ##

This file tries to take aspects of the Bayesian workflow paper by Gelman and 
colleagues and apply them to an example scenario in experimental psychology / cognitive neuroscience.

The Bayesian workflow paper can be found here: http://arxiv.org/abs/2011.01808

The workflow that I present is broken down into several different stages. Each stage has its own markdown file. I found it easier to organise things in this way such that each script represents a little self-contained module or sub-process. The different scripts are detailed below.

*One important caveat*. This is not an exhaustive or complete application of the Bayesian workflow that was outlined by Gelman and colleagues. It is simply a selection from a set of processes that are then applied to an example in experimental psychology. I've found it useful to think about things in this way and so I wanted to write it down. There is much more richness and subtlety in the article than I have tried to convey in these scripts. There is also an important iterative dimension that I don't really talk about in these scripts, even though the scripts themselves developed in an iterative process. The iterative part is important though because Gelman and co. talk about cycling through different stages as knowledge and understanding develops. See Figure 1 in the above paper for a visualisation of the non-serial and iterative nature of the workflow.

Anyway, it's a really good paper, and I didn't want to spoil all the fun for you. So just go and read it.

## Project organsiation and folder structure ##

The overall Bayesian workflow that I outline here will be split up into several sections, as follows:

1. prior predictions.
2. planning for power/precision via simulation.
3. build a series of models and perform model checking and model comparison.
4. evaluate the posterior.

*scripts*

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

*folders*

There are three main folders:

*/data/*

*/figures/*

*/models/*

These folders have self-explanatory titles. Inside each one, there may be sub-directories, which hopefully also have sensible titles. e.g., a sub-directory called /plan/ holds figures/models/data from the plan.Rmd file and phase of the workflow.



