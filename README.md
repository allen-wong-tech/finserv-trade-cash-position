# Financial Services Asset Management on Snowflake Demo Version 2.0

## Releases
    v2.0    Use Knoema instead of deprecated Zepl Share; Added Python Faker for synthetic trader creation; Rewrote Snowsight Tiles
            Removed: company_profile, stock_latest, finservam_datascience_wh, snowflake_sample_data, share_now, middleware
    v1.0    Use Zepl Marketplace share

### Problem
Big banks and Asset managers have spent millions of dollars to accurately give a Single Version of Truth (SVOT) in real-time.  What would such a system look like on Snowflake?

### Solution
    Snowflake has high performance at low TCO due to its out-of-the-box operation, near-zero maintenance, and low learning curve
    SVOT makes trading, risk management, regulatory reporting, and Financial Services big data use cases significantly easier
    Unlimited Compute and Concurrency enable quick data-driven decisions

### What we will see
    Use the Snowflake Data Marketplace to instantly get stock history so the business doesn't have to wait for IT.
    Populate only the trade table and use window functions to generate cash, positions, and Profit-and-Loss (PnL) so that you can have real-time updates.
    Use SnowSight - Snowflake's complimentary User Interface (UI) - to generate dashboards that can be shared with the business.


## Demo and Technical Deep-Dive of Version 1.0
[Youtube Playlist](https://www.youtube.com/playlist?list=PLyKI7j42vSkbryDXuB7kEhzk66lmdNJ3Z)

[Medium Blog](https://allenwongtech.medium.com/what-would-snowflake-for-an-asset-manager-look-like-part-1-a0583c0e5822)

## How to Install (Takes under 7 minutes; each script is idempotent)

    Create a database named snowflake_sample_data from the sample_data share [see above pic]
    Find a share named "Knoema Economy Data Atlas" from the Snowflake Data Marketplace and name the database economy_data_atlas
    
    Run Script 10: Sets up the environment
    Run Script 20: Connects to the Data Marketplace to get free stock history
    Run Script 30: Populates the trade table.  Creates Window Function Views for cash, positions, and PnL
    Run Script 40: This is the smoke test and what the business queries

## How to Setup SnowSight Demo:
    In snowsight subfolder:
        Add filters in script "33 filter SnowSight"
        Build SnowSight dashboard using script "35 SnowSight".
    
### Optional Setting:
In the first few lines of script 30, you can set the variable *limit_trader = x*.

It's default is set to 100 traders to populate in the trader table which when multplied by 40+ years of daily trades will create 3-billion-plus trades. 
    
limit_trader  | Trades generated | Script 30 Run-time with xxlarge compute
--------------|------------------|------------------------------
100 (default) | 3 billion        | under 4 minutes
200           |                  | 
300           |                  | 
    
## Partner Demos on top of this demo

[Data Build Tool (DBT)](https://github.com/ruwhite11/AssetManagement): Open-Sourced by a hedge fund prospect.  DBT gives you software engineering best practices on big data with concepts like Don't Repeat Yourself and Analytics Engineer.

[Sigma Computing](https://sigmacomputing.wistia.com/medias/w7ck8dugdp): Excel-like analysis over 2 billion rows powered with only Snowflake Small compute power.
  
## To remove Demo
    Run "optional\finserv 90 reset.sql".
    If you implemented SnowSight, delete Filters and Dashboard in snowsight subfolder: scripts 33 and 35.
