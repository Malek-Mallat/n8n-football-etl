# n8n Football Standings Workflow

This project contains an automated [n8n](https://n8n.io/) workflow that fetches the latest Premier League (PL) football standings and stores them in a PostgreSQL database.

## Overview

The workflow defined in `football standings.json` performs the following steps:
1. **Schedule Trigger**: Triggers the workflow to run on a set interval.
2. **HTTP Request**: Calls the `football-data.org` API to get the current Premier League standings.
3. **Data Processing**: 
   - Uses a `Split Out` node to extract the table array.
   - Uses a `Code in Python` node to parse the nested JSON and map it to a flat structure.
4. **PostgreSQL**: Upserts (Inserts or Updates) the processed data into a table named `premier_league_standings`, matching on `team_id` to ensure no duplicates.

## Prerequisites

To run this workflow, you need:
- An active n8n instance.
- An API Key (Auth Token) from [football-data.org](https://www.football-data.org/) (passed in the `X-Auth-Token` header).
- A PostgreSQL database to store the standings.

## Database Schema

The workflow expects a table named `premier_league_standings` with the following columns:
- `team_id` (Integer/Primary Key - used for matching)
- `Position` (Integer)
- `team_name` (String)
- `played` (Integer)
- `won` (Integer)
- `draw` (Integer)
- `lost` (Integer)
- `points` (Integer)
- `goals_for` (Integer)
- `goals_against` (Integer)
- `goal_diff` (Integer)

## Setup Instructions

1. Open your n8n instance.
2. Create a new workflow.
3. Select **Import from File...** from the workflow menu and select `My workflow.json`.
4. Update the **HTTP Request** node with your own `X-Auth-Token` if necessary.
5. Configure the **Postgres** node with your database credentials.
6. Activate the workflow!



