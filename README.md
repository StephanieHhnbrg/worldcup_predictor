# World Cup Predictor
Goal: Predict whether a team wins a World Cup match

only players who scored, no info about defenders, midfield control, tactics


## Data analysis and preperation
Historical data from FIFA tournaments from the current century.
https://github.com/jfjelstul/worldcup/tree/master/data-csv

goals: goal_id, match_id, scoring_team, opponent_team, player_id, player_name

matches: match_id, scoring_team, opponent_team, winner_score, loser_score

players: player_id, player_name, birth_year, age, goal_keeper, defender, midfielder, forward, count_tournaments, list_tournament_years

- draws within group stage matches in data are treated as losses 


### Feature engineering
Goals + matches → team features

team_stats: team, total_goals, num_players_with_goals, max_goals_by_single_player, total_matches, matches_with_goals, matches_without_goals, avg_goals_per_match


Matches → long format with labels
Join team features to matches
Compute differences → model-ready table

## Model training

currently simple Random Forest

# TODO: Model tuning
- Random Forest / XGBoost / LightGBM or Logistic Regression (great baseline)
- Gradient Boosted Trees?


## Evaluate + Feature Importance


## Applying model to 2026 matches
Since some countries have not qualified for the 21th century worldcups, no data is present in the team_stats.csv
Therefore we apply the average team strength to them, so that the model does not unfairly punish or boost them.

For more realistic output, the region avarage or external ratings could have been considered.


## Automatization by Kubeflow

# TODO: Wrap everything into a Kubeflow pipeline for reproducibility
checkout https://github.com/kubeflow/examples/tree/master/financial_time_series

## Future work
Add more team features (age, player positions, WC experience)

