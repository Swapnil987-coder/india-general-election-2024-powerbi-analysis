1️⃣ Table: states_master
| Column Name | Data Type    | Description                      |
| ----------- | ------------ | -------------------------------- |
| State_ID    | Whole Number | Unique identifier for each state |
| State_Name  | Text         | Name of the Indian state         |

Purpose: Used as dimension table for state-level analysis.

2️⃣ Table: state_results
| Column Name | Data Type    | Description                                |
| ----------- | ------------ | ------------------------------------------ |
| State       | Text         | Name of the state                          |
| Total_Seats | Whole Number | Total constituencies in the state          |
| NDA_Seats   | Whole Number | Seats won by NDA alliance                  |
| INDIA_Seats | Whole Number | Seats won by I.N.D.I.A alliance            |
| Other_Seats | Whole Number | Seats won by independent and other parties |

Purpose: Used for state-level seat distribution and map visualization.

3️⃣ Table: party_results
| Column Name | Data Type    | Description                  |
| ----------- | ------------ | ---------------------------- |
| Party_Name  | Text         | Name of political party      |
| Alliance    | Text         | NDA / I.N.D.I.A / OTHER      |
| Seats_Won   | Whole Number | Total seats won by the party |

Purpose: Used for alliance analysis and donut chart visualizations.

4️⃣ Table: constituency_results
| Column Name       | Data Type    | Description                                   |
| ----------------- | ------------ | --------------------------------------------- |
| Constituency      | Text         | Name of constituency                          |
| State             | Text         | State name                                    |
| Winning_Candidate | Text         | Candidate with highest votes                  |
| Winning_Party     | Text         | Party of winning candidate                    |
| EVM_Votes         | Whole Number | Votes cast via EVM                            |
| Postal_Votes      | Whole Number | Postal ballot votes                           |
| Total_Votes       | Calculated   | EVM_Votes + Postal_Votes                      |
| Margin            | Calculated   | Difference between winner and runner-up votes |

Purpose: Used for constituency-level analysis dashboard.

5️⃣ Table: constituency_details
| Column Name    | Data Type    | Description                           |
| -------------- | ------------ | ------------------------------------- |
| Candidate_Name | Text         | Name of candidate                     |
| Party          | Text         | Candidate’s political party           |
| Votes          | Whole Number | Votes secured by candidate            |
| Vote_Share_%   | Calculated   | (Candidate Votes / Total Votes) × 100 |

Purpose: Used for candidate performance comparison in Constituency Analysis dashboard.

🧮 Calculated Measures (DAX)
| Measure Name | Description                        |
| ------------ | ---------------------------------- |
| Total Votes  | SUM(EVM_Votes) + SUM(Postal_Votes) |
| NDA Seat %   | (NDA Seats / Total Seats) × 100    |
| INDIA Seat % | (INDIA Seats / Total Seats) × 100  |
| Other Seat % | (Other Seats / Total Seats) × 100  |
| Vote Share % | Candidate Votes / Total Votes      |

🔄 Data Transformation Summary

Data cleaning and transformation steps were performed using Power Query inside Power BI:

Removed null values

Standardized party names

Created Alliance mapping column

Calculated Total Votes

Created Margin column

Optimized data types

Established relationships using Star Schema
