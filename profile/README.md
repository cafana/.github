# The CAFAna Framework

## "What's this?"

CAFAna is a set of C++ tools designed to facilitate construction and analysis of distributions from event records in high energy physics datasets.
Its main design goals are speed, modularity, and simplicity and consistency of user experience.
It evolved as the main day-to-day analysis framework used by [the NOvA experiment](https://novaexperiment.fnal.gov/).
CAFAna provides tools for:
 * fast iteration over data files to produce histograms
 * extensive efficient histogram manipulation (using [Eigen](https://eigen.tuxfamily.org/) as a backend)
 * a library with a number of "calculators" for neutrino oscillation probabilities in various contexts
 * means for efficient fitting of histograms produced by the framework under neutrino oscillation or systematic uncertainty variations.

The name originates from "Common Analysis Files" (or "Common Analysis Format" files; the oral history is conflicted)&mdash;CAFs&mdash;which remain the foundation of the approach, but the system has since been generalized beyond the NOvA format.
Current applications include efforts on NOvA as well as users from the [DUNE collaboration](https://www.dunescience.org/) and the [Fermilab SBN program](https://sbn.fnal.gov/).

More on the history, design, and possible future directions of CAFAna may be found at [arXiv:2203.13768 [hep-ex]](https://arxiv.org/abs/2203.13768).


## Using CAFAna

The repositories underneath the CAFAna GitHub organization implement various components of the framework:

* [`SRProxy`](https://github.com/cafana/SRProxy) is a toolkit for simple and fast traversal of the `StandardRecord` data format expected by CAFAna in [ROOT](https://root.cern.ch/) format file storage. 

* [`CAFAnaCore`](https://github.com/cafana/CAFAnaCore) contains the foundation `Spectrum` (histogram) classes and API, basic storage access classes, and other miscellaneous shared tools.

* [`CAFAnaFit`](https://github.com/cafana/CAFAnaFit) provides implementations of several different approaches for fitting `Spectrum` objects (gradient-descent minimization of chi-squared; Hamiltonian Markov Chain Monte Carlo)

* [`OscLib`](https://github.com/cafana/OscLib) offers a number of "calculators" that can compute neutrino oscillation probabilities using various approximations.


Regular users of CAFAna will likely want their input prepared in files with `StandardRecord` objects (or "flattened" ROOT trees that CAFAna's `FlatReader` can read).
This will require a specialization of the workhorse `_Var` , `_Cut`, `_Weight`, and `Spectrum` types using a `StandardRecord` that fits their needs.
As examples, see the implementations by [SBN](https://github.com/SBNSoftware/sbnana/tree/develop/sbnana/CAFAna) or [DUNE](https://github.com/DUNE/lblpwgtools/tree/master/CAFAna).
It would be nice to have a full technical digest of how to do this written up here, but in the meantime, please contact the CAFAna Code Librarian (@cafana/librarian) and we can discuss your use case.

## Contributing

We welcome input with suggestions, bug reports, and (especially!) pull requests with proposed changes to the code base.

Once a pull request is opened:
* the CAFAna Stakeholders (representatives from the neutrino experiments who use CAFAna in analysis workflows) will discuss it in the `managing_cafana`/`cafana-admin` cross-workspace Slack channel.
* Each Stakeholder experiment will be required to approve the pull request in GitHub.
* Once all the required approvals are in place, the @cafana/librarian will merge the pull request.
* The @cafana/librarian will also be responsible for setting the timetable for subsequent officially tagged releases of CAFAna (but of course a user is free to use the repository at any state they like).

The @cafana/librarian is responsible for ensuring that reviews from the Stakeholders are received in a timely fashion.  Pull request authors should feel free to communicate with the Librarian if their request is languishing.

