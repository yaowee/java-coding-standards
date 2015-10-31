# Code Organisation #

The following conventions are around how we organise both test and production source code.

## Guiding Principles ##

When considering how to organise our code we take into account the following principles outlined in http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf.

  * The Release Reuse Equivalency Principle (REP): The granule of reuse is the granule of release.
  * The Common Closure Principle (CCP): Classes that change together, belong together.
  * The Common Reuse Principle (CRP):  Classes that aren’t reused together should not be grouped together.