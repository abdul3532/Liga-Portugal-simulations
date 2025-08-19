# 🏆 Liga Portugal Season Simulator

A comprehensive Monte Carlo simulation tool for predicting Liga Portugal season outcomes using historical data, advanced team strength calculations, and transfer impact analysis.

## ✨ Features

- **Historical Data Integration**: Pulls real match data from football-data.co.uk
- **Advanced Team Ratings**: Combines ELO ratings, offensive/defensive metrics, and weighted historical performance
- **Transfer Impact Analysis**: Accounts for key player departures and arrivals
- **Promotion/Relegation Handling**: Properly adjusts ratings for newly promoted teams
- **Monte Carlo Simulation**: Runs thousands of season simulations for statistical accuracy
- **Rich Visualizations**: Championship probability charts and league table predictions
- **Configurable Parameters**: Adjustable simulation count, home advantage, and random seeds

## 🚀 Quick Start

### Installation

```bash
git clone https://github.com/yourusername/liga-portugal-simulator.git
cd liga-portugal-simulator
pip install -r requirements.txt
```

### Basic Usage

```bash
# Run with default settings (1,000 simulations)
python liga_simulator.py

# Run with custom parameters
python liga_simulator.py --sims 10000 --home-adv 0.12 --seed 42

# Offline mode (uses default ratings)
python liga_simulator.py --offline --no-plots
```

## 📊 2025/26 Season Configuration

The simulator is currently configured for the **2025/26 Liga Portugal season** with:

**✅ Promoted Teams:**
- 🆕 Alverca FC
- 🆕 CD Tondela
- 🔄 CD Santa Clara (returning)
- 🔄 CD Nacional (returning)

**❌ Relegated Teams:**
- SC Farense
- Boavista FC

**🔄 Transfer Adjustments:**
- Major departures (e.g., Viktor Gyökeres from Sporting)
- Key signings and squad changes
- Weighted impact on team strength ratings

## 🛠️ Command Line Arguments

| Argument | Type | Default | Description |
|----------|------|---------|-------------|
| `--sims` | int | 1000 | Number of Monte Carlo simulations |
| `--home-adv` | float | 0.15 | Home advantage factor (0.0-0.3) |
| `--seed` | int | None | Random seed for reproducible results |
| `--no-plots` | flag | False | Disable matplotlib visualizations |
| `--offline` | flag | False | Skip data download, use default ratings |

## 📈 Methodology

### Team Strength Calculation

The simulator uses a multi-factor approach to determine team strengths:

1. **ELO Ratings (60%)**: Dynamic ratings updated based on match results
2. **Offensive Performance (25%)**: Goals scored per game with seasonal weighting  
3. **Defensive Performance (15%)**: Goals conceded per game with seasonal weighting

### Seasonal Weighting

Historical data is weighted to emphasize recent performance:

- **2024/25 Season**: 80% weight (most recent form)
- **2023/24 Season**: 10% weight
- **2022/23 Season**: 5% weight
- **2021/22 Season**: 3% weight
- **2020/21 Season**: 2% weight

### Transfer Impact

Teams receive strength adjustments (-5 to +5) based on:
- Key player departures/arrivals
- Squad depth changes
- Manager changes
- Financial situation

### Match Simulation

Each match is simulated using:
- Team strength differential
- Home advantage factor (default 15%)
- Poisson distribution for goal generation
- League-average goals per game (2.6 for Liga Portugal)

## 📋 Requirements

```
pandas>=1.3.0
numpy>=1.20.0
requests>=2.25.0
matplotlib>=3.3.0
scipy>=1.7.0
```

## 📁 Project Structure

```
liga-portugal-simulator/
├── liga_simulator.py          # Main simulation engine
├── requirements.txt           # Python dependencies
├── README.md                 # Project documentation
└── data/                     # Cached historical data (auto-generated)
```

## 🎯 Sample Output

```
🏆 CHAMPIONSHIP PROBABILITIES (based on 10,000 simulations)
-----------------------------------------------------------------
 1. Sporting CP               ████████████████████████  48.2% (4,820 wins)
 2. Benfica                   ████████████████████      32.1% (3,210 wins)
 3. Porto                     ██████████████           19.7% (1,970 wins)

📊 AVERAGE FINAL POSITIONS & POINTS
--------------------------------------------------
 1. Sporting CP               Pos:  1.7 | Points: 84.2
 2. Benfica                   Pos:  2.1 | Points: 79.8
 3. Porto                     Pos:  2.9 | Points: 72.4
```

## 🔧 Customization

### Adding New Teams

Update the `current_teams` list and add corresponding entries to:
- `team_mapping` (for name standardization)
- `transfer_adjustments` (strength modifications)
- `promoted_team_minimums` (for newly promoted sides)

### Adjusting Transfer Impact

Modify the `transfer_adjustments` dictionary:

```python
self.transfer_adjustments = {
    'Sporting CP': -4,  # Lost key players
    'Benfica': +3,      # Strong signings
    'Porto': -2,        # Moderate departures
    # ... other teams
}
```

### Historical Data Sources

The simulator automatically fetches data from:
- **Source**: football-data.co.uk
- **League**: Portuguese Primera Liga (P1)
- **Format**: CSV with match results, goals, dates
- **Seasons**: 2020/21 to 2024/25

## 🐛 Troubleshooting

**Data Download Issues:**
```bash
# Use offline mode if network/data issues occur
python liga_simulator.py --offline
```

**Missing Dependencies:**
```bash
# Install all requirements
pip install pandas numpy requests matplotlib scipy
```

**Visualization Problems:**
```bash
# Skip plots if matplotlib issues arise
python liga_simulator.py --no-plots
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Historical match data provided by [football-data.co.uk](https://www.football-data.co.uk)
- ELO rating system adapted for football applications
- Portuguese football community for insights and feedback

## 📧 Contact

For questions, suggestions, or issues:
- Create an [Issue](https://github.com/yourusername/liga-portugal-simulator/issues)
- Discussion forum: [Discussions](https://github.com/yourusername/liga-portugal-simulator/discussions)

---

**⚽ Vamos Portugal! 🇵🇹**
