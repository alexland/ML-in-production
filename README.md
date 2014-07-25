ML-in-production
================

implementing distributed machine learning classifiers in production systems

most common & most significant obstacles to implementing ML systems in production:

* poor resolution

  * high cycle times in model training

  * poor data access during prototyping

* slow implementation cycle time
  
  - solution: 75% of the workflow from model building to implementation in production can be automated--these steps are invariant (or else hightly constrained) & their position in the workflow sequence rarely if ever changes
  
  - nearly all ML-based systems share a common high-level architecture, which ought to be designed & built separate from any signle project

* incompatible interfaces

  - negotiate the service endpoints & method signature at the beginning of the project





====================

My ToolBox:

* ipython notebook

  - parallel computation
  
  - plugin architecture for eg, 
  
    - custom timing functions
	
	- cython refactoring
	
  - code, equations, plotting & interpreter results--all inlined

* vagrant

* redis-based datamarts for modeler data access

* resolution, performance, & status dashboard

  - node.js + socket.io + d3.js app showing 
  
    - precision & recall of all models currently in production
	
	- precision & recall of all models currently running on dev server

* github, travis CI, coveralls

* pytest

  - acceptance criteria are embodied in a pre-agreed-upon unit test suite based on precision & recall thresholds
  
  - pre-coded fixtures reusable across projects

* data processing toolkit

  - sturdy implementations of various techiques to improve the modeler's understanding of the relevant data
   
     - feature selection: eg, unsupervised techniques (PCA, kPCA), recursive feature elimination
	 
	 - feature ranking: eg, decision tree

* simple, well-defined architecture w/ clear intuitive contracts

  - the main module injects a 'trained model' into a post-processing pipeline in which:
  
    - the model is serialized (format determined by model type); and
	
	- persisted in a redis data store (schema based on model type); and
	
	- retrievable by an instantiated factory function accessible to the Thirft server


