# NFL Game Odds Prediction

A machine learning project that predicts NFL game outcomes and tests whether better-calibrated win probabilities can generate profit against sportsbook moneylines.

---

## File inclusions


- `game_odds_prediction.ipynb`: Main analysis — a Jupyter Notebook (interactive Python doc with code + outputs inline); covers full pipeline
- `games.csv`: Game-level data with team matchups, moneyline odds, and sportsbook-implied probabilities --> sourced from nflverse
- `2017-2025_scores.csv`: Raw NFL scores across 8 seasons used to compute outcomes and historical win rates --> sourced from Kaggle



## How it works

The model is trained on historical game features (win rates, point differentials, rest days, home/away splits) using **temporal cross-validation** — trained only on past games, validated on future ones — to avoid data leakage. Predictions feed into an **overround-based profit simulation** that bets only when the model's confidence meaningfully exceeds the sportsbook's implied probability.

Three risk tiers were tested: conservative (>65% confidence), moderate (>58%), and aggressive (>52%). Filtering to high-confidence bets (~65%+) yielded the best ROI (~+8–12%), while aggressive betting produced negative expected value — confirming that bet selection matters more than raw model accuracy.



## Results & Takeaways

- Model accuracy: ~67% vs. ~56% baseline (always picking home team)
- Profitable only with selective, high-confidence bet filtering
- Sportsbook overround (~4–6%) is the primary barrier — the model must consistently clear that margin to be worthwhile
- Home field advantage and recent momentum turned out to be the strongest features

---

## Potential next steps

Adding live injury/weather data, player-level metrics (QB EPA, DVOA), and ensemble modeling would likely improve calibration. Extending the simulation to point spreads and totals, and testing Kelly criterion bankroll strategies, were thought about in this project; could be worthwhile to include in the future!

---

*For educational purposes only.*
