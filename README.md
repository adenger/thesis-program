##Descripton

This program calculates the effects of nsSNPs (non-synonymous single nucleotide polymorphisms) in the protein-coding regions of the human genome on the resulting protein-protein interaction network (PPIN). It was written as part of my Bachelor Thesis at the Chair of Computational Biology, Saarland University.

## Installation

Clone and import into Eclipse or download the jar and json files from the *jar* folder

## Parameters

A general *main* method is provided in the class *Main* in the *framework* folder. 
The command line options are:

* **-m** *\<file\>* 

   File containing RefSNP identifiers (rs#), one per line. Required parameter.
* **-c** *\<name\>* 

   The classification score used to predict deletions of PPIs. The options are:
  * *properties*
  * *blosum\<number\>* (Availlable numbers are 30,35,40...100. Also 62.)
  * *polyphen2hc*
  * *polyphen2*
  * *sifthc*
  * *sift*
  * *null*
  * *hotspot*
  * *pshc*
  * *hpshc*
  
   This parameter is optional, the default is *polyphen2hc*
* **-p** *\<file\>* 

   File containing protein-protein interactions, one interaction per line, tab-separated, Uniprot AC format. Optional parameter, otherwise a consensus PPIN (IntAct + BioGRID) is used.
* **-update_ppin** 

   Data on the default consensus PPIN is saved in *protein_tmp.json*. If this flag is activated, the data is updated. This can take several minutes. The option should also be activated if a user-specified PPIN is provided.
* **-localmutations** 

   Data on the last set of evaluated mutations is saved locally to *mutation_tmp.json*. If the same set of mutations is evaluated twice or more in a row, this option can be activated to use the locally stored data instead of downloading it every time.
* **-lologfile** 

   Prevents *log.txt* from being created. 
* **-nolog** 

   Prevents logging system from printing to the console.

##API Reference

Otherwise, the *MutationEvaluator* class encompasses all the functions of the program. 
To change any settings, the *Settings* class should be used. The settings are:
* **LOCAL_MUTATION_DATA** 

   Data on the last set of evaluated mutations is saved locally to *mutation_tmp.json*. If the same set of mutations is evaluated twice or more in a row, this option can be activated to use the locally stored data instead of downloading it every time. Default: *false*
* **LOCAL_PROTEIN_DATA** 

   Data on the default consensus PPIN is saved in *protein_tmp.json*. If this flag is activated, the data is updated. This can take several minutes. The option should also be activated if a user-specified PPIN is provided. Default: *true*
* **DOMAIN_DATA_3DID** 

   Include 3did data in the DDI database. Default: *true*
* **DOMAIN_DATA_IPFAM** 

   Include iPfam data in the DDI database. Default: *true*
* **DOMAIN_DATA_IDDI** 

   Include IDDI data in the DDI database. Default: *true*
* **DOMAIN_DATA_DOMINE** 

   Include DOMINE data in the DDI database. Default: *true*
* **DOMAIN_DATA_NO_PREDICTIONS** 

   Only use experiment-based data. Default: *false*
* **DISABLE_LOG**  

   Prevent logging system from printing to console. Default: *false*
* **DISABLE_LOG_FILE** 

   Prevent logging system from writing a file. Default: *false*
* **CLASSIFIER_BLOSUM_MATRIX** 

   *BlosumMatrixName* enum type incdicating which matrix to use. Default: *BlosumMatrixName.BLOSUM100*
* **BINDING_SITE_CLASSIFIER** 

   *ClassifierScore* enum type indicating which classifier to use. Default: *ClassifierScore.POLYPHEN_2_HC*

## Tests

The evaluation can be run by executing the *main* method in the *eval* subfolder. The testing data can be recreated using the scripts in the *scripts* folder.