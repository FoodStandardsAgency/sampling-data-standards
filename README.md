# Data Standards for Food and Feed Sampling Directly Commissioned by the FSA

## Introduction
This document describes the data and metadata standards that we expect partners undertaking directly commissioned sampling on behalf of the FSA to follow.

This document contains a schema for returns as well as some guidance on associated metadata, but it does not cover the specifics of data transfer.

### Basic Technical Standards
In addition to any return of data which uses a spreadsheet, the FSa requires all suppliers to provide sampling data in machine readable formats. Currently, acceptable formats are comma separated values `.csv` and javascript object notation `.json` files.

Data provided to the FSA must be in the unicode encoding standard `UTF-8`.

Where a date is required, but may be imprecise, the FSA expects to still recieve a fully qualified ISO8601 date and time value, but with a substituted time or day where appropriate. For example, a best before date of "April 2022" should default to midnight at the first of April, i.e., `2022-04-01T00:00:00Z` or a sampling date where the time is unavailable should use midnight as the default time, i.e., `2022-01-04T00:00:00Z`. Dates which are imprecise by more than a day should not be used.

### Overview

There is also a JSON Schema in this repository for the standard.

Index|Field Name|Description|Data Type|Controlled Vocabulary|Source
-----|----------|-----------|---------|---------------------|-------
1|`lab_id`|A unique identifier for the analysis, which is resolvable within the testing laboratories' records|String|No|N/A|
2|`analysing_lab`|The name of the laboratory undertaking the analysis|String|No|N/A|
3|`risk`|The risk being assessed|String|Yes|[Hazard Concept Scheme](https://data.food.gov.uk/codes/alerts/def/_hazard)|
4|`test_id`|The test being used to assess the risk, the FSA will provide controlled vocabularies to each survey|String|Yes|N/A|
5|`lod_loq`|The value for the limits of detection or quantification (where applicable)|String|No|N/A|
6|`outcome`|The outcome of the analysis|String|Yes|See detailed description|
7|`sample_timestamp`|A timestamp for when the sample was taken|Date/Time|No|N/A|
8|`certificate_of_analysis`|A boolean to show whether the certficiate of analysis for this sample has been provided to the FSA|Boolean|No|N/A|
9|`photos`|A boolean to show whether accompanying photographs have been provided to the FSA for this sample|Boolean|No|N/A|
10|`product_type`|A product classification, each commissioned survey will provide the controlled vocabulary for that survey to ensure consistency|String|Yes|N/A|
11|`brand_name`|The brand name of the sampled product|String|No|N/A|
12|`batch_number`|The batch number or unique identifier of the batch of the sproduct being sampled|String|No|N/A|
13|`country_of_origin`|The country of origin of the sample, using the two character ISO country code|String (2)|Yes|[ISO Country Codes](https://en.wikipedia.org/wiki/List_of_ISO_3166_country_codes)|
14|`shelf_life`|The best before or use-by date of the sample|Date|No|N/A|
15|`business_name`|The name of the business where the sample was taken|String|No|N/A|
16|`business_address_line_1`|The first line of the address of the premises where the sample was taken|String|No|N/A|
17|`business_address_line_2`|The second line of the address of the premises where the sample was taken|String|No|N/A|
18|`business_address_line_3`|The third line of the address of the premises where the sample was taken|String|No|N/A|
19|`business_postcode`|The postcode of the premises where the sample was taken|String|No|N/A|
20|`business_type`|The type of business as described by our unified business types list|String|Yes|[Unified Establishment Types](https://data.food.gov.uk/codes/business/_unified-establishment-type)|

## Field Definitions

#### Optional Fields
Some fields are listed as "optional". This means that not all records will have a value in these fields, but the fields are still required as part of the schema. Nulls are acceptable in these fields.

### 1. Laboratory Reference
**Field Name:** `lab_id`  
**Data Type:** String  
**Optional:** No  
**Comments:** This is the identifier as used in the laboratory undertaking the analysis. Should teams have enquiries about the analysis that require contacting the laboratory, this is the reference that should be used - it is not the internal FSA reference.  

### 2. Analysing Laboratory
**Field Name:** `analysing_lab`  
**Data Type:** String  
**Optional:** No  
**Comments:** The name of the laboratory where the analysis was completed.  

### 3. Risk Name
**Field Name:** `risk`  
**Data Type:** String  
**Optional:** No  
**Comments:** The type of risk being tested for through sampling. These must be notation values from our [Hazard Concept Scheme](https://data.food.gov.uk/codes/alerts/def/_hazard). For example, `allergens` for allergen testing.  

### 4. Test Used
**Field Name:** `test_id`  
**Data Type:** String  
**Optional:** No  
**Comments:** The name of the test being used to assess the risk. For each survey, the FSA will provide a controlled vocabulary which must be used in this field.  

### 5. Limits of Detection / Limits of Quantification
**Field Name:** `lod_loq`  
**Data Type:** String  
**Optional:** Yes  
**Comments:** The specified limits of detection or quantification associated with this test.  

### 6. Outcome
**Field Name:** `outcome`  
**Data Type:** String  
**Optional:** No  
**Comments:** The outcome of the analysis. The acceptable values for this field are `compliant`, `non-compliant`, and `inconclusive`.  

### 7. Sample Timestamp
**Field Name:** `sample_timestamp`  
**Data Type:** String  
**Optional:** No  
**Comments:** The timestamp of when the sample was taken, in ISO 8601 format (i.e., `2021-11-27T10:15:00Z`). Where the time is unavailable, a pre-agreed time should be used for consistency.  

### 8. Certificate of Analysis Supplied
**Field Name:** `certificate_of_analysis`  
**Data Type:** Boolean (`True` or `False`)  
**Optional:** No  
**Comments:** Indicates whether the certificate of analysis for this sample has been supplied to the FSA as part of the survey return. Certificates of anaylsis supplied to the FSA should have the laboratory reference in the file name.  

### 9. Photographs Supplied
**Field Name:** `photos`  
**Data Type:** Boolean (`True` or `False`)  
**Optional:** No  
**Comments:** Indicates whether photographs associated with the sample or test have been supplied to the FSA as part of the survey return.  

### 10. Product Type
**Field Name:** `product_type`  
**Data Type:** String  
**Optional:** No  
**Comments:** Each survey will provide a list of acceptable terms which must be used to describe the sample that has been taken.  

### 11. Brand Name
**Field Name:** `brand_name`  
**Data Type:** String  
**Optional:** No  
**Comments:** The brand name of the sample product.  

### 12. Batch Number
**Field Name:** `batch_number`  
**Data Type:** String  
**Optional:** Yes  
**Comments:** The batch number of the sample product.  

### 13. Country of Origin
**Field Name:** `country_of_origin`  
**Data Type:** String  
**Optional:** No  
**Comments:** The country of origin of the sample product. Only two-character ISO country codes are acceptable in this field.  

### 14. Shelf Life
**Field Name:** `shelf_life`  
**Data Type:** String  
**Optional:** Yes  
**Comments:** The brand name of the sample product.  

### 15. Business Name
**Field Name:** `business_name`  
**Data Type:** String  
**Optional:** No  
**Comments:** The name of the business where the sample was taken.

### 16. Business Address Line 1
**Field Name:** `business_address_line_1`  
**Data Type:** String  
**Optional:** No  
**Comments:** The first line of the address of the business where the sample was taken.  

### 17. Business Address Line 2
**Field Name:** `business_address_line_2`  
**Data Type:** String  
**Optional:** Yes  
**Comments:** The second line of the address of the business where the sample was taken.  

### 18. Business Address Line 3
**Field Name:** `business_address_line_3`  
**Data Type:** String  
**Optional:** Yes  
**Comments:** The third line of the address of the business where the sample was taken.  

### 19. Business Post Code
**Field Name:** `business_postcode`  
**Data Type:** String  
**Optional:** No  
**Comments:** The post code of the business where the sample was taken.  

### 20. Business Type
**Field Name:** `business_type`  
**Data Type:** String  
**Optional:** No  
**Comments:** The type of business as described by our [Unified Establishment Types](https://data.food.gov.uk/codes/business/_unified-establishment-type).  
