






# Quick testing sandbox

_This is a chapter for quickly previewing and testing how content appears_

We fit a generalized additive model with fast restricted maximum likelihood
estimation [@Wood2017; @Soskuthy2017 for a tutorial for linguists; see Box 1].
We included main effects of study year. These *parametric* terms work like
conventional regression effects and determined the growth curve's average
values. We used age-4 as the reference year, so the model's intercept
represented the average looking probability at age 4. The model's year effects
therefore represented differences between age 4 vs. age 3 and age 4 vs. age 5.

We included a *smooth* term for time. We included a smooth term for trial time
to represent a general effect of time following noun onset across all studies,
and we also included smooth terms for time for each study. These study-specific
smooths estimate how the shape of the data differs in each individual study. As
an equation, our model estimated: [@Barr2008;]
[vers. 2.3; @itsadug]