# Extract GA4 Event Parameters and User Properties from BigQuery
This Colab Notebook parses the reads a single day worth of data from the GA4 raw export to BigQuery and lists all of the non-standard event parameters and user properties.

To use this notebook, you will need to set the required variables in the first cell, select **Runtime** > **Run all**, and follow any dialogs that open. In particular, you will need to log in to your Google account that has access to the desired data.

The output appears at the bottom of the notebook. You will likely want to copy and paste it to a text document.

Detailed documentation is inline in the notebook.

## Installation
This notebook uses some Google-specific Google Colab functions so it only runs in Colab.

To install this on Google Colab, 

1. Create an empty notebook
2. In the main menu, select **File** > **Upload Notebook** to open the upload dialog
3. In the upload dialog, switch to the **GitHub** tab
4. In the search box, paste the URL for this repository (https://github.com/CaretJuice/ga4-list-tags-params) and click on the search icon to populate matching notebook files
5. Click on the matching notebook and the code should load into your Colab notebook