# Parameters and training compute in notable AI models

This report asks whether notable AI models with more parameters also needed more training compute, and whether that link changed across the three eras of AI development.

## Final report

- [View the knitted report in the browser](https://htmlpreview.github.io/?https://github.com/yangLiu57670838/report-training-computation-parameters-analysis/blob/master/training-computation-parameters-analysis.html)
- [HTML file in this repository](training-computation-parameters-analysis.html) (download it and open it in a browser)
- [R Markdown source](training-computation-parameters-analysis.Rmd)

## Data

The data comes from Epoch AI (2026), with major processing by Our World in Data. Both files were downloaded on 24 October 2026 and are kept unchanged in `Data/raw/`:

- [Training computation vs. dataset size](https://ourworldindata.org/grapher/training-computation-vs-dataset-size-in-notable-ai-systems): `training-computation-vs-dataset-size-in-notable-ai-systems.csv`
- [Number of parameters](https://ourworldindata.org/grapher/parameters-in-notable-artificial-intelligence-systems): `parameters-in-notable-artificial-intelligence-systems.csv`

## Data preparation

There is no separate data script. The first code chunk in Data set introduction section of the report does the preparation every time the report is knitted:

1. It joins the two files on `Entity` and `Day`.
2. It creates `year` from `Day`, and `era` from `year`, using the three eras from Sevilla et al. (2022): Pre-deep learning (before 2010), Deep learning (2010–2015) and Large-scale (2016 onwards).
3. It keeps five columns (`parameters`, `training_compute`, `dataset_size`, `year`, `era`) and drops rows with missing values, leaving 409 models.
4. It writes the result to `Data/merged.csv`. This file is an output of the knit, not an input.

## How to knit the report

1. Open `report-training-computation-parameters-analysis.Rproj` in RStudio.
2. Install the packages if needed: `install.packages(c("dplyr", "ggplot2", "knitr", "rmarkdown"))`.
3. Open `training-computation-parameters-analysis.Rmd` and click **Knit**. This rebuilds `Data/merged.csv` and the HTML report.

## Folders

- `Data/raw/`: the two original downloads
- `Data/merged.csv`: the analysis table written by the report
- `Image/`: the screenshot of the inline R code used in Section 4

## References

Epoch AI (2026) – with major processing by Our World in Data. "Parameter, Compute and Data Trends in Machine Learning." Retrieved 24 October 2026 from Our World in Data.

Sevilla, J., Heim, L., Ho, A., Besiroglu, T., Hobbhahn, M., and Villalobos, P. (2022). Compute Trends Across Three Eras of Machine Learning. arXiv:2202.05924. <https://arxiv.org/abs/2202.05924>

Fedus, W., Zoph, B., and Shazeer, N. (2022). Switch Transformers: Scaling to Trillion Parameter Models with Simple and Efficient Sparsity. *Journal of Machine Learning Research*, 23(120), 1–39. <https://jmlr.org/papers/v23/21-0998.html>
