# collecting_events
Analysis of different approach for collecting Twitter data for events.

## Preparing data
1. Extract create date and tweet id.

		cat <the tweets> | jq -r '[.id_str, .created_at] | @csv'

2. Split into git-sized files.
	
		split --line-bytes=100m --additional-suffix=.csv -d <base filename>.csv <base filename>-
		gzip <base_filename>-*.csv
		rm <base_filename>.csv

3. Copy to `data/` directory.