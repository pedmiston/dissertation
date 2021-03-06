
Analysis of familiar word recognition
===========================================================================









Growth curve analysis
------------------------------------------------------------------------

Looks to the familiar image were analyzed using Bayesian mixed
effects logistic regression. I used *logistic* regression because
the outcome measurement is a probability (the log-odds of looking to the
target image versus a distractor). I used *mixed-effects* models
to estimate a separate growth curve for each child (to
measure individual differences in word recognition) but also treat each
child's individual growth curve as a draw from a distribution of related
curves. I used *Bayesian* techniques to study a generative model of the
data. Instead of reporting and describing a single, best-fitting model
of some data, Bayesian methods consider an entire distribution of
plausible models that are consistent with the data and any prior
information we have about the models. By using this approach, one can
explicitly quantify uncertainty about statistical effects and draw
inferences using estimates of uncertainty (instead of using statistical
significance—which is not a straightforward matter for mixed-effects
models).[^2]

[^2]: It is tempting to further justify this approach by comparing
    Bayesian versus classical/frequentist statistics, but my goals in
    using this method are simple: To estimate statistical effects and
    quantify uncertainty about those effects. This pragmatic brand of
    Bayesian statistics is illustrated in texts by @GelmanHill and 
    @RethinkingBook.

The eyetracking growth curves were fit using an orthogonal cubic
polynomial function of time [a now-conventional approach; see
@Mirman2014]. Put differently, I modeled the probability of looking to
the target during an eyetracking task as:

$$
\text{log-odds}(\textit{looking}\,) = 
  \beta_0 + 
  \beta_1\text{Time}^1 + 
  \beta_2\text{Time}^2 + 
  \beta_3\text{Time}^3
$$

That the time terms are *orthogonal* means that $\text{Time}^1$,
$\text{Time}^2$ and $\text{Time}^3$ are transformed so that they
are uncorrelated. Under this formulation, the parameters $\beta_0$ and
$\beta_1$ have a direct interpretation in terms of lexical processing
performance. The intercept, $\beta_0$, measures the area under the
growth curve—or the probability of fixating on the target word averaged
over the whole window. We can think of $\beta_0$ as a measure of *word
recognition reliability*. The linear time parameter, $\beta_1$,
estimates the steepness of the growth curve—or how the probability of
fixating changes from frame to frame. We can think of $\beta_1$ as a
measure of *processing efficiency*, because growth curves with stronger
linear features exhibit steeper frame-by-frame increases in looking
probability.[^3]


[^3]: The polynomial other terms are less important—or rather, they have
    do not map as neatly onto behavioral descriptions as the accuracy
    and efficiency parameters. The primary purpose of quadratic and
    cubic terms is to ensure that the estimated growth curve adequately
    fits the data. In this kind of data, there is a steady baseline at
    chance probability before the child hears the word, followed a
    window of increasing probability of fixating on the target as the
    child recognizes the word, followed by a period of plateauing and
    then diminishing looks to target. The cubic polynomial allows the
    growth curve to be fit with two inflection points: the point when
    the looks to target start to increase from baseline and the point
    when the looks to target stops increasing.

To study how word recognition changes over time, I modeled how the
growth curves change over developmental time. This amounted to studying
how the growth curve parameters changes year over year. I included
dummy-coded indicators for Age 3, Age 4, and Age 5 and allowed these
indicators interact with the growth curve parameters. These
year-by-growth-curve terms captured how the shape of the growth curves
changed each year. The model also included random effects to represent
child-by-year effects.


### Growth curve features as measures of word recognition performance

As mentioned above, two of the model's growth curve features have
straightforward interpretations in terms of lexical processing
performance: The model's intercept parameter corresponds to the average
proportion or probability of looking to the named image over the trial
window, and the linear time parameter corresponds to slope of the growth
curve or lexical processing efficiency. I also was interested in *peak*
proportion of looks to the target. I derived this value by computing the
growth curves from the model and taking the median of the five highest
points on the curve. Figure \@ref(fig:curve-features) shows three
simulated growth curves and how each of these growth curve features
relate to word recognition performance.

(ref:curve-features) Illustration of the three growth curve features and
how they describe lexical processing performance. The three curves used
are simulations of new participants at Age 4.

<div class="figure">
<img src="12-aim1-notebook_files/figure-html/curve-features-1.png" alt="(ref:curve-features)" width="80%" />
<p class="caption">(\#fig:curve-features)(ref:curve-features)</p>
</div>



Year over year changes in word recognition performance
------------------------------------------------------------------------

The mixed-effects model estimated a population-average growth curve
("fixed" effects) and how individual children deviated from average
("random" effects). Figure \@ref(fig:average-growth-curves) shows 200
posterior samples of the average growth curves for each study. On
average, the growth curves become steeper and achieve higher looking
probabilities with each year of the study.

(ref:average-growth-curves) The model estimated an average word
recognition growth for each study, and the colored lines represent 200
posterior samples of these growth curves. The thick dark lines represent
the observed average growth curve in each study.

<div class="figure">
<img src="12-aim1-notebook_files/figure-html/average-growth-curves-1.png" alt="(ref:average-growth-curves)" width="50%" />
<p class="caption">(\#fig:average-growth-curves)(ref:average-growth-curves)</p>
</div>

Figure \@ref(fig:effects2) depicts uncertainty intervals with
the model's average effects of each timepoint on the growth curve
features. The intercept and linear time effects increased each year,
confirming that children become more reliable and faster at recognizing
words as they grow older. The peak accuracy also increased each year.
For each effect, the change from age 3 to age 4 is approximately the
same as the change from age 4 to age 5, as visible in
Figure \@ref(fig:pairwise-effects).

(ref:effects2) Uncertainty intervals for the effects of study years on
growth curve features. The intercept and peak features were converted from
log-odds to proportions to ease interpretation.

<div class="figure">
<img src="12-aim1-notebook_files/figure-html/effects2-1.png" alt="(ref:effects2)" width="80%" />
<p class="caption">(\#fig:effects2)(ref:effects2)</p>
</div>

(ref:pairwise-effects) Uncertainty intervals for the differences between study
timepoints. Again, the intercept and peak features were converted to
proportions.

<div class="figure">
<img src="12-aim1-notebook_files/figure-html/pairwise-effects-1.png" alt="(ref:pairwise-effects)" width="50%" /><img src="12-aim1-notebook_files/figure-html/pairwise-effects-2.png" alt="(ref:pairwise-effects)" width="50%" />
<p class="caption">(\#fig:pairwise-effects)(ref:pairwise-effects)</p>
</div>



The average looking probability (intercept feature) was 0.38
[90% UI: 0.37--0.40] at age 3, 0.49
[0.47--0.50] at age 4, and 0.56 [0.54--0.57] at
age 5. The averages increased by 0.10
[0.09--0.11] from age 3 to age 4 and by 0.07
[0.06--0.09] from age 4 to age 5. The peak looking
probability was 0.55 [0.53--0.57] at age 3,
0.68 [0.67--0.70] at age 4, and 0.77
[0.76--0.78] at age 5. The peak values increased by
0.13 [0.11--0.16] from age 3 to age 4 and
by 0.09 [0.07--0.10] from age 4 to age 5.
These results numerically confirm the hypothesis that children would
improve in their word recognition reliability, both in terms of average
looking and in terms of peak accuracy, each year.

**Summary**. The average growth curve features increased year over year,
so that children looked to the target more quickly and more reliably.



Exploring plausible ranges of performance over time
------------------------------------------------------------------------



Bayesian models are generative; they describe how the data could have
been generated. This model assumed that each child's growth curve was
drawn from a population of related growth curves, and it tried to infer
the parameters over that distribution. These two aspects---a generative
model and learning about the population of growth curves---allow the
model to simulate new samples from that distribution of growth curves.
That is, we can predict a set of growth curves for a hypothetical,
unobserved child drawn from the same distribution as the
195 observed children. This procedure allows
one to explore the plausible degrees of variability in performance at
each age.

Figure \@ref(fig:new-participants) shows the posterior predictions
for 1,000 simulated participants, which demonstrates how the model
expects new participants to improve longitudinally but also exhibit
stable individual differences over time. Figure
\@ref(fig:new-participants-intervals) shows uncertainty intervals for
these simulations. The model learned to predict less accurate and more
variable performance at age 3 with improving accuracy and narrowing
variability at age 4 and age 5.

(ref:new-participants) Posterior predictions for hypothetical
*unobserved* participants. Each line represents the predicted
performance for a new participant. The three dark lines highlight
predictions from one single simulated participant. The simulated
participant shows both longitudinal improvement in word recognition and
similar relative performance compared to other simulations each year,
indicating that the model would predict new children to improve year
over year and show stable individual differences over time.


<div class="figure">
<img src="12-aim1-notebook_files/figure-html/new-participants-1.png" alt="(ref:new-participants)" width="80%" />
<p class="caption">(\#fig:new-participants)(ref:new-participants)</p>
</div>

(ref:new-participants-intervals) Uncertainty intervals for the simulated
participants. Variability is widest at age 3 and narrowest at age 5,
consistent with the prediction that children become less variable as
they grow older.

<div class="figure">
<img src="12-aim1-notebook_files/figure-html/new-participants-intervals-1.png" alt="(ref:new-participants-intervals)" width="80%" />
<p class="caption">(\#fig:new-participants-intervals)(ref:new-participants-intervals)</p>
</div>

I hypothesized that children would become less variable as they grew
older and converged on a mature level of performance. I address this
question by inspecting the ranges of predictions for the simulated
participants. The claim that children become less variable would imply
that the range of predictions should be narrower age 5 than for age 4
than age 3. Figure \@ref(fig:new-ranges) depicts the range of the
predictions, both in terms of the 90 percentile range (i.e., the range
of the middle 90% of the data) and in terms of the 50 percentile
(interquartile) range. The ranges of performance decrease from age 3 to
age 4 to age 5, consistent with the hypothesized reduction in
variability.

(ref:new-ranges) Ranges of predictions for simulated participants over
the course of a trial. The ranges are most similar during the first half
of the trial when participants are at chance performance, and the ranges
are most different at the end of the trial as children reliably fixate
on the target image. The ranges of performance decreases with each year
of the study as children show less variability.

<div class="figure">
<img src="12-aim1-notebook_files/figure-html/new-ranges-1.png" alt="(ref:new-ranges)" width="80%" />
<p class="caption">(\#fig:new-ranges)(ref:new-ranges)</p>
</div>

The developmental pattern of increasing reliability and decreasing
variability was also observed for the growth curve peaks. For the
synthetic participants, the model predicted that individual peak
probabilities will increase each year, peak<sub>3</sub> =
0.55 [90% UI: 0.35--0.77],
peak<sub>4</sub> = 0.69 [0.48--0.86],
peak<sub>5</sub> = 0.78 [0.59--0.91].
Moreover, the range of plausible values for the individual peaks
narrowed each for the simulated data. For instance, the difference
between the 95^th^ and 5^th^ percentiles was 0.43 for
age 3, 0.38 for age 4, and 0.32
for age 5.

**Summary**. I used the model's random effects estimates to simulate
growth curves from 1,000 hypothetical, unobserved participants. The
simulated dataset showed increasing looking probability and decreasing
variability with each year of the study. These simulations confirmed the
hypothesis that variability would be diminish as children converge on a
mature level of performance on this task.



Are individual differences stable over time?
------------------------------------------------------------------------



I predicted that children would show stable individual differences such
that children who are faster and more reliable at recognizing words at
age 3 remain relatively faster and more reliable at age 5. To evaluate
this hypothesis, I used Kendall's *W* (the coefficient of correspondence
or concordance). This nonparametric statistic measures the degree of
agreement among *J* judges who are rating *I* items. For these purposes,
the items are the 123 children who provided reliable eyetracking
for all three years of the study. (That is, I excluded children who only
had reliable eyetracking data for one or two years.) The judges are the
sets of growth curve parameters from each year of study. For example,
the intercept term provides three sets of ratings: The participants'
intercept terms from year 1 are one set of ratings and the terms from
years 2 and 3 provide two more sets of ratings. These three ratings are
the "judges" used to compute the intercept's *W*. Thus, I computed five
groups of *W* coefficients, one for each set of growth curve features:
Intercept, Time^1^, Time^2^, Time^3^, and Peak looking probability.




Because I used a Bayesian model, there is a distribution of ratings and
thus a distribution of concordance statistics. Each sample of the
posterior distribution fits a growth curve for each child in each study,
so each posterior sample provides a set of ratings for concordance
coefficients. The distribution of *W*'s lets us quantify our uncertainty
because we can compute *W*'s for each of the 4000 samples from
the posterior distribution.

One final matter is how to assess whether a concordance statistic is
meaningful. To tackle this question, I also included a "null rater", a
fake parameter that assigned each child in each year a random number. I
use the distribution of *W*'s generated by randomly rating children as a
benchmark for assessing whether the other concordance statistics differ
meaningfully from chance.

(ref:kendall-stats) Uncertainty intervals for the Kendall's coefficient
of concordance. Random ratings provide a baseline of null *W*
statistics. The intercept and linear time features are decisively
non-null, indicating a significant degree of correspondence in
children's relative word recognition reliability and efficiency over
three years of study.

<div class="figure">
<img src="12-aim1-notebook_files/figure-html/kendall-stats-1.png" alt="(ref:kendall-stats)" width="80%" />
<p class="caption">(\#fig:kendall-stats)(ref:kendall-stats)</p>
</div>

We used the `kendall()` function in the irr R package
[vers. 0.84; @irr] to compute concordance
statistics. Figure \@ref(fig:kendall-stats) depicts uncertainty intervals
for the Kendall *W*'s for these growth curve features. The 90%
uncertainty interval of *W* statistics from random ratings
[0.28--0.39] subsumes the intervals for the Time^2^
effect [0.30--0.35] and the Time^3^ effect
[0.28--0.35], indicating that these values do not
differentiate children in a longitudinally stable way. That is, the
Time^2^ and Time^3^ features differentiate children across studies as
well as random numbers. Earlier, I stated that only the intercept,
linear time, and peak features have psychologically meaningful
interpretations and that the higher-order features of these models serve
to capture the shape of the growth curve data. These concordance
statistics support that assertion.

Concordance is strongest for the peak feature, *W* = 0.59
[0.57--0.60] and the intercept term, *W* =
0.58 [0.57--0.60], followed by the
linear time term, *W* = 0.50 [0.48--0.52].
Because these values are far removed from the statistics for random
ratings, I conclude that there is a credible degree of correspondence
across studies when ranking children using their peak looking
probability, average look probability (the intercept) or their growth
curve slope (linear time).

**Summary**. Growth curve features reflected individual differences in
word recognition performance. By using Kendall's *W* to
measure the degree of concordance among growth curve features over
time, I tested whether individual differences in lexical
processing persisted over development. I found that the peak looking
probability, average looking probability and linear time features were
stable over time.



Predicting future vocabulary size
------------------------------------------------------------------------







I hypothesized that individual differences in word recognition at age 3
will be more discriminating and predictive future language outcomes than
differences at age 4 or age 5. To test this hypothesis, we calculated
the correlations of growth curve features with age 5 expressive
vocabulary size and age 4 receptive vocabulary. (The receptive test was
not administered during the last year of the study for logistical
reasons.) As with the concordance analysis, I computed each of the
correlations for each sample of the posterior distribution to obtain a
distribution of correlations.

Figure \@ref(fig:evt2-gca-cors) shows the correlations of the peak
looking probability, average looking probability and linear time
features with expressive vocabulary size at age 5, and
Figure \@ref(fig:ppvt4-gca-cors) shows analogous correlations for the
receptive vocabulary at age 4. For all cases, the strongest correlations
were found between the growth curve features at age 3.

Growth curve peaks from age 4 correlated with age 5 vocabulary with
*r* = .52, 90% UI
[.50--.54], but the concurrent peaks from age 5
showed a correlation of just *r* = .31,
[.29--.33], a difference between age 3 and
age 5 of *r*<sub>3−5</sub> = .21,
[.18--.24]. A similar pattern held for
lexical processing efficiency values. Linear time features from age 3
correlated with age 5 vocabulary with *r* =
.41, [.39--.44],
whereas the concurrent lexical processing values from age 5 only showed
a correlation of *r* = .28,
[.26--.31], a difference of *r*<sub>3−5</sub> =
.13,
[.10--.16]. For the average looking
probabilities, the correlation for age 3, *r* =
.39, [.39--.44], was
probably only slightly greater than the correlation for age 4,
*r*<sub>3−4</sub> = .02,
[&minus;.01--.04] but considerably greater than the
concurrent correlation at age 5, *r*<sub>3−5</sub> =
.08,
[.05--.10].

(ref:evt2-gca-cors) Uncertainty intervals for the correlations of growth
curve features at each time point with expressive vocabulary (EVT-2
standard scores) at age 5. The bottom rows provide intervals for the
pairwise differences in correlations between timepoints.

<div class="figure">
<img src="12-aim1-notebook_files/figure-html/evt2-gca-cors-1.png" alt="(ref:evt2-gca-cors)" width="80%" />
<p class="caption">(\#fig:evt2-gca-cors)(ref:evt2-gca-cors)</p>
</div>

Peak looking probabilities from age 3 were strongly correlated with
age 4 receptive vocabulary, *r* = .62,
[.61--.64], and this correlation was much
greater than the correlation observed for the age 4 growth curve peaks,
*r*<sub>3−4</sub> = .26,
[.26]. The correlation of age 3
average looking probabilities, *r* = .45,
[.44--.47], was greater than the age 4
correlation, *r*<sub>TP1−TP2</sub> =
.08,
[.08], and the correlation for age 3
linear time features, *r* = .51,
[.49--.54], was likewise greater,
*r*<sub>3−4</sub> = .22,
[.19--.26].

(ref:ppvt4-gca-cors) Uncertainty intervals for the correlations of
growth curve features at each time point with expressive vocabulary
(PPVT-4 standard scores) at age 4. The bottom row shows pairwise
differences between the correlations from timepoints.

<div class="figure">
<img src="12-aim1-notebook_files/figure-html/ppvt4-gca-cors-1.png" alt="(ref:ppvt4-gca-cors)" width="80%" />
<p class="caption">(\#fig:ppvt4-gca-cors)(ref:ppvt4-gca-cors)</p>
</div>

**Summary**. Although individual differences in word recognition were
stable over time, early differences were more significant than later
ones. The strongest predictors of future vocabulary size were the growth
curve features from age 3.

<!-- ### Relationships with other child-level predictors -->

<!-- _TJM: This is where I would analyze the other test scores as we have discussed._ -->


Discussion
------------------------------------------------------------------------

In the preceding analyses, I analyzed many aspects of children's
recognition of familiar words. First, I examined how children's looking
patterns *on average* changed year over year. Children's word
recognition improved each year: The growth curves grew steeper, reached
higher peaks, and increased in their average value each year. This
result was unsurprising, but it was valueable because it confirmed that
this word recognition task scaled with development. The task was simple
enough that children could recognize words at age&nbsp;3, but challenging
enough for children's performance to improve each year.

After establishing how the averages changed each year, I next asked how
variability changed each year. To tackle this question, I used posterior
predictive inference to have the model simulate samples of data, and in
particular, to simulate new participants. The range of performance
narrowed each year, so that children were most variable at age 3 and
least variable at age 5. This result is consistent with a model of
development children vary widely early on and converge on a more mature
level of performance. From this perspective, word recognition as a skill
is like articulation where most children grow out of immature speech
patterns by grade school. An alternative outcome would have been
troubling: Word recognition differences that expanded with age, the
emergence of a word recognition "gap".

Although the range of individual differences decreased with age,
differences did not disappear over time. When children at each age were
ranked using growth curve features, we found a high degree of
correspondence among these ratings. Children who were faster or more
accurate at age 3 remained relatively fast or accurate at age 5. Thus,
differences in word recognition were longitudinally stable over the
preschool years. Extrapolating forwards in time, these differences
likely would become smaller and smaller until they are irrelevant.
Alternatively, they might matter in more adverse listening conditions.
It is conceivable that children's differences would re-emerge in a more
difficult word recognition task. [_Study Bob's paper on older children._]


***

  - the vocabulary results
  - Stitch these pieces together
  - The shape and structure of words do not change with age. The amount
    of information needed to identify a word from a closed set is
    constant with age. So it makes sense that word recognition
    development follows a trajectory where differences narrow. As a skill, word
    recognition is a necessary foundation to later more sophisticated
    degrees of language comprehension. If word recognition is such a foundation,
    then slow listerners might show challenges in these more difficulty
    comprehension situations. 


*** 

**Summary**. Although individual differences in word recognition are
stable over time, early differences are more significant than later
ones. The strongest predictors of future vocabulary size were the growth
curve features from age 3. That is, word recognition performance from
age 3 was more strongly correlated with age 5 expressive vocabulary than
word recognition performance at age 5. A similar pattern of results held
for predicting receptive vocabulary at age 4.





<!-- The growth curve changes each year involved peak accuracy and steepness -->
<!-- of the curve. They reach higher heights, and they hit year 1 peak -->
<!-- earlier each year. -->

  <!-- - Word recognition performance is a skill where variation is greatest -->
  <!--   at younger ages. -->
  <!-- - What mechanisms might come to bear on this? Does variability narrow -->
  <!--   developmentally for vocabulary? -->
  <!-- - Children different in their word-learning trajectories, so the early -->
  <!--   differences in word recognition could be from younger children who -->
  <!--   are relatively early/late in word-learning. The SDs of the EVT-2 -->
  <!--   scores narrows a small amount each year, even when we only consider -->
  <!--   the children who participated at all three years. -->
  <!-- - (It will be easier to fold this in to the mechanism discussion once -->
  <!--   we have firmer results for the looks-to-foils analysis.) -->
  <!-- - If differences in word recognition matter (and they do) and the -->
  <!--   differences are greatest at younger ages, then they are most -->
  <!--   informative at younger ages. -->
  <!-- - Maybe a few words on why individual differences are worth studying? -->

<!--   - Although the range of variability decreases, individual differences -->
<!--     do not wash out. -->
<!--   - Lexical processing is a stable ability over the preschool years. -->
<!--   - Extrapolating outwards, the differences probably diminish to the -->
<!--     point that they are not meaningful. But traces of those early -->
<!--     differences can reappear years later on some test scores. -->


  <!-- - This finding is surprising because vocabulary scores from the same -->
  <!--   week as the eyetracking data are less correlated than scores from -->
  <!--   two year earlier. -->
  <!-- - This establishes that the differences are greatest and most -->
  <!--   predictive at younger ages. -->















































