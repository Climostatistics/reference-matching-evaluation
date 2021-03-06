# Reference matching experiments

The notebooks here contain various experiments related to reference matching algorithms. The notebooks are living documents, frequently updated as the algorithms, data and/or the Crossref collection change.

Two approaches to reference matching are tested in these experiments:

  * **STQ**: the currently used matching approach
  * **SBM**: search-based matching

STQ is Crossref's current matching algorithm. STQ internally uses a 3rd party parser and regular expressions and queries the Oracle. I run this matching algorithm using Simple Text Query form.

SBM is a new idea, based on the search functionality of Crossref REST API. It is a very simple algorithm, which doesn't include any reference parsing step. In SBM the entire reference string is used as a query in REST API. The first hit is returned as the matched target document, if its relevance score is high enough. If the relevance score of the first hit is low, no target DOI is assigned and the reference string stays unmatched.

SBMV is a variation of SBM. In SBMV, SBM is first applied and a number of top search results are selected as candidate target documents. Second, during the validation the candidates are re-scored based on the validation similarity between the input string and the candidates. Finally, the most similar candidate is chosen as the final target document, if its similarity is high enough. If the highest similarity is low, null value is returned and the reference string stays unmatched.

The notebooks (reading order):

  * **sampling\_notes**: notes about sampling and confidence intervals. These techniques are used in the following experiments.
  * **relevance\_threshold**: experiments with the relevance score threshold for SBM. The best threshold values are used in the comparison.
  * **comparison**: evaluation and comparison of STQ and SBM on a large set of automatically generated reference strings.
  * **existing\_matches**: comparison of existing links in the system against the current results of STQ and SBM.
