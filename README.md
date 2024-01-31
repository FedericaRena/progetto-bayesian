# Project A2

Goal: Clustering weekly data of one year of PM10 (plus covariates - see AGRIMONIA project)   
Models & R packages:  
- drpm (Page, Quintana, Dahl (2022) "Dependent Modeling of Temporal Sequences of Random Partitions", JCGS, R-package on Github)    
- ppmSuite (various models implemented, also PPMs) on https://cran.r-project.org/web/packages/ppmSuite/index.html   
Data: old https://zenodo.org/records/7563265 new https://zenodo.org/records/7956006   


# Models order
**Important**: for models fitting let's use `df_weekly_scaled_centered` loaded from `include.R`, which has (now it's done):

- numerical covariates scaled
- spatial coordinates also scaled (fitting appears to be better)
- PM10 just centered, not scaled

And for models evaluation see file `Metrics and workflow.Rmd` (now it's done).
See also that for understand how to create the plots of the clusters.

**Models recap**:

- DRPM (Federico): with time and space
- Gaussian PPMx (Federica): just covariates
- SPPM (Oswaldo): just space
- Curve ppmx (Aby): time and covariates
- Linear (Giulia): time and covariates, simple baseline model

| Model                    | Time     | Space    | Covariates | Clustering|
|--------------------------|----------|----------|------------|-----------|
| DRPM (Federico)          |  ✓       | ✓          |  X      | ✓      | 
| Gaussian PPMx (Federica) |  X       |   X        |  ✓      | ✓      | 
| SPPM (Oswaldo)           |  X       |    ✓       | X      | ✓      |
| Curve PPMx (Aby)         |   ✓     | X           |  ✓     | ✓      |
| CarBayesST               |   ✓     | ✓           |  ✓      |  X    |
| Linear                   |    ✓    |    X        |    ✓    |   X    |


The models without time means that time is not inside the model. Then we can "force" time to be included by looping or doing some other tricks, but time will never be inside the model.

The models without space could consider to use space as a covariate? like the locations longitude and latitude as numerical covariates.

# Report chapters idea
Report here at https://it.overleaf.com/6577451481wwsqvrgxswjy#c9ce5d

1. Data inspection + problem presentation
	- 1.0 Introduction (Ettore)
	- 1.1. NAs treatment, stations descarded (Giulia)
	- 1.2. trends, choice of the year (Federico, but help may be needed)
	- ?
2. Models 
	- 2.1. SPPM, as it is just spatial, like the start point (Oswaldo)
	- 2.2. DRPM, space plus time (Federico)
	- 2.3. Gaussian PPMx, only covariates (Federica) 
	- 2.4. Curve PPMx, covariates and time (Aby)
        - 2.5. Giulia's linear model (Giulia)
 -  2.6  CARBayesST + covariate selection, so Ettore and Giulia work, to prepare for the models with covariates  (only cited as a not determinant attempt) + variable selection, different for every model but summerized in 1 

3. Model choice
	- 3.1. model comparison with the metrics used (Federico)
	- 3.2. why model X is the "best" 
	- CV (?), MSE, ARI  and other metrics used to compare the models (Federico)
4. Analysis of the results
	- 4.1. How do we interpret the model? Why some covariates seem more important than others? (Ettore)
5. Conclusion (Ettore)
6. Further Developments (Ettore)
	- 6.1. model averaging Package‘AICcmodavg’
	- 6.2. weekend-weekday division
	- 6.3. prior dall'anno precedente
7. Appendix
	- plot librairies, animations, html... (Ettore)
	- link (Federico)


## Comments on the models
Write them here so are easily available to everyone, and to be able to build a general frame of the information we can extract.
Write them below each mode model plot.  
Use the visualize html page to see peculiar features of your model, as we are ok interested in common comments, on which all models agree, but also some patterns that a certain model may spot and others models not. So especially use the "Covariates visualization" section in the html page.

![](./src/figures/DRPM/Time%20Series/plt_modemap.png)

1. Comments:
	- ecc
	- ecc

![](./src/figures/sPPM/Time%20Series/plt_modemap.png)

1. Comments:
	- ecc
	- ecc


![](./src/figures/Gaussian%20PPMx/Time%20Series/plt_modemap.png)

1. Comments:
	- ecc
	- ecc


![](./src/figures/Curve%20PPMx/Time%20Series/plt_modemap.png)

1. Comments:
	- ecc
	- ecc


