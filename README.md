# capstoneCodex





# Preprocessing Steps for Predictive Model
## Financial Toll of Weather Disruptions on Airlines

### 1. **Data Integration**
* Loaded datasets related to:
  * Flight delays (`delay_df`).
  * Airport-centric weather events (`weather_events_df`).

### 2. **Time Adjustments**

* **Datetime Conversion**:
  * Converted `CRS_DEP_TIME` and `CRS_ARR_TIME` columns in `delay_df` to a proper datetime format, taking the flight date and time into account.

* **Time Zone Integration**:
  * Merged the `delay_df` with the `weather_events_df` to obtain time zone data for each origin (`ORIGIN_TimeZone`) and destination (`ORIGIN_TimeZone_DEST`).
  * Adjusted departure and arrival times to UTC to match with the weather data.

### 3. **Weather Events Association**

* **Origin Analysis**:
  * Identified flights in `delay_df` whose departure time (`DEP_DATETIME_UTC`) was affected by weather events occurring at the origin airport.
* **Destination Analysis**:
  * Identified flights in `delay_df` whose arrival time (`ARR_DATETIME_UTC`) was affected by weather events occurring at the destination airport.

### 4. **Merging Results**

* Combined the results from the origin and destination analysis to get a holistic view of flights affected by weather events.
* Removed duplicate records to ensure accuracy.

### 5. **Initial Analysis**

* Computed mean delay (`mean_delay`) caused due to weather events.
* Computed total flight cancellations (`total_cancellations`) due to weather events.
