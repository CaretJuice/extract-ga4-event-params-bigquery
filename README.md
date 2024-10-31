# extract-ga4-event-params-bigquery
Extract event parameters and user properties from a GA4 BigQuery table.

The purpose of this notebook is to make it easier for data engineers and data analysts working with the GA4 raw BigQuery export to uncover which events, event parameters and user properties need to be modeled. In particular, it is designed for configuration the [dbt-ga4 package](https://github.com/Velir/dbt-ga4) and this workbook was released as part of the [Advanced dbt-GA4 course](https://caretjuice.com/courses/advanced-dbt-ga4/).

The workbook outputs to a Google Sheet with a name of the form `project_name:dataset_name:table_name`.

The sheet will have a tab for universal parameters, a tab for each event, and a tab for user properties.

## Configuration
All configuration happens in the first cell.

You need to set the source project, dataset, and table.
```
source_project = ''
source_dataset = ''
source_table = ''
```

The source table should be a full partition. Wild cards may work but will query all data all time. This workbook takes a decent amount of time to process as it is so wild cards in `source_table` are not recommend and could be expensive.

The output includes a "Universal parameters" tab in the Google Sheet that includes common event parameter keys that you may want to treat as being present in all GA4 events.

The `threshold` variable sets the percentage of events containing an event parameter key above which the parameter should be included in the "Universal parameters" tab. The default is 0.7 or 70 percent. This should be a value between 0 and 1.
```
threshold = 0.7
```
The intent of this workbook is to discover custom parameters. GA4 includes a number of default parameters in all events as well as debug parameters that are not of interest when discovering custom parameters. 

These standard parameters are excluded from the output by the `exclude_parameters` variable. You may wish to edit this variable if you are using this workbook for a different purpose.
```
exclude_parameters = ['page_title', 'batch_ordering_id', 'engaged_session_event', 'batch_page_id', 'page_location',
                      'ignore_referrer', 'gtm_container_id', 'engagement_time_msec', 'gtm_container_version', 'page_referrer',
                      'session_engaged', 'gtm_debug_mode', 'ga_session_number' , 'ga_session_id', 'medium', 'term', 'campaign',
                      'source', 'gclid', 'gclsrc', 'gtm_environment', 'debug_mode']
```

## Installation
This notebook uses some Google-specific Google Colab functions so it only runs in Colab.

To install this on Google Colab, 

1. Create an empty notebook
2. In the main menu, select **File** > **Upload Notebook** to open the upload dialog
3. In the upload dialog, switch to the **GitHub** tab
4. In the search box, paste the URL for this repository [https://github.com/CaretJuice/extract-ga4-event-params-bigquery](https://github.com/CaretJuice/extract-ga4-event-params-bigquery) and click on the search icon to populate matching notebook files
5. Click on the matching notebook and the code should load into your Colab notebook
