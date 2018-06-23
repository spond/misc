### A simple simulator for sampling from an exponentially decaying reservoir

The goal of this simulator is to estimate what might happen if you sampled `N` replication compentent sequences from the DNA reservoir of an individual who is on a (presumed) suppressive therapy. Several assumptions are made.

1. The reservoir is continuously seeded between the origin of infection all the way until the time that treatment is initiated (at time T<sub>treatment</sub>, measured by convention as weeks post-infection) 
2. Once sequences from timepoint `t` enter the reservoir, they begin exponential decay with some rate `c`, goverened by the half-life parameter
3. When the treatment is initiated, there is no further replenishment of the reservoir, only exponential decay of existing sequences
4. We don't model the carrying capacity of the reservoir.
5. There are K timepoints in [0,T<sub>treatment</sub>] for which we have RNA sequences for the virus.
6. At some point (under the previous assumputions, it doesn't actually matter at what point afterwards), following T<sub>treatment</sub>, we obtain `N` replication compentent sequences from the reservoir, each of which has some (unobserved) time of origin ([0,T<sub>treatment</sub>])  and assign them to one the K RNA populations, i.e. "time" them.
7. The previous assigment is imprecise, i.e. we don't always assign them to the closest population in time, but can make some a>ssignment errors.


It step 6 above, the sampling distribution for the unobserved time has the CDF of _(EXP(-c t) - 1) / (EXP(-c T<sub>treatment</sub>) - 1)_, and it step 7 above, we sample the assignment group based on the normal density cenetred at the true sampling time `t` with the standard deviation parameter set at 6 months.

The simulator generates 100 replicates from two models, each defined by it's own half-life, and presents 

1. the mean (over 100 replicates) of QVOA samples &rarr; RNA samples assignment, as a pie-chart.
2. The distributuon of RNA samples over all simulated replicates 
3. The pie-chart for the measured distributions of the measured samples.
