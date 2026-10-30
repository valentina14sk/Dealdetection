# DealDetective — Shiny dashboard for large local datasets

This version is intended for the original 8+ GB local CSV workflow. It does not upload or load the huge source CSV inside Shiny. Instead, it reads the compact CSV summaries and PNG charts created by `DealDetective_full_R_code.R`.

## Run

Install packages once:

```r
install.packages(c("shiny", "data.table", "ggplot2", "DT", "scales"))
```

Open `app.R` in RStudio and click **Run App**, or run:

```r
shiny::runApp()
```

## Use your existing analysis results

1. Run your original `DealDetective_full_R_code.R` script against `ecommerce_processed.csv`.
2. Confirm that the script has created `DealDetective_Output`.
3. In the dashboard's left panel, enter the full path to that folder. Example:
   `/Users/yourname/Downloads/DealDetective_Output`
4. Click **Load analysis outputs**.

The dashboard reads the original script's output files: missingness summary, flag counts, discount consistency check, sample summary, product summary, weekly history, review candidates, and PNG visualizations.

## If you don't know the full folder path on Mac

In Finder, locate `DealDetective_Output`. You can drag the folder into Terminal to reveal its path. Copy the path into the app's folder field. You can also use R:

```r
normalizePath("~/Downloads/DealDetective_Output", mustWork = FALSE)
```

Adjust the example path to the folder's actual location.

## Important

- This dashboard uses existing results, so the 8+ GB CSV is not uploaded to the browser.
- If an optional PNG or CSV was not created by the original script (some outputs depend on available data), the dashboard explains that the file is missing.
- The original script's review candidates are screening signals only, not proof of deceptive pricing.
- `fake_discount_flag` is treated as a dataset-provided label, not ground truth.
