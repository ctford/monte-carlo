# Monte Carlo Project Completion Estimator

A single-page web application that uses Monte Carlo simulation to estimate project completion dates based on historical cycle time data.

## Overview

This tool helps project teams make data-driven predictions about project completion dates by:

1. **Analyzing historical performance**: Takes your actual cycle time data from completed work items
2. **Running simulations**: Performs thousands of Monte Carlo simulations to model potential project outcomes
3. **Providing percentile estimates**: Shows p50 (median), p80, and p90 completion dates
4. **Visualizing uncertainty**: Displays an S-curve showing the cumulative probability distribution

## How It Works

The Monte Carlo simulation works by:

1. **Calculating statistics** from your historical cycle times (mean and standard deviation)
2. **Running N simulations** (default 10,000) where each simulation:
   - Randomly samples cycle times from a normal distribution based on your historical data
   - Accumulates completion times until reaching your total work remaining
3. **Generating predictions** from the simulation results:
   - **p50 (50th percentile)**: The most likely completion date (50% chance of completing by this date)
   - **p80 (80th percentile)**: A conservative estimate (80% confidence)
   - **p90 (90th percentile)**: A very conservative estimate (90% confidence)

## Using the App

### Local Development

1. Clone this repository
2. Open `index.html` in a web browser
3. Enter your historical cycle times (one per line, in days)
4. Enter the total amount of work remaining
5. Click "Calculate Estimate"

### Deployment to GitHub Pages

1. Push this repository to GitHub
2. Go to Settings → Pages
3. Set source to "Deploy from a branch"
4. Select the branch containing this code
5. Your app will be available at `https://username.github.io/repo-name/`

## Input Parameters

- **Historical Throughput**: Enter the number of items completed per week from your past projects. More data points = more accurate estimates. At least 3 data points are required.
  
- **Total Work Remaining**: The number of items/units you still need to complete.

- **Iterations**: The number of iterations to run. More iterations are more accurate but slower. Default 10,000 is usually sufficient.

## Understanding the Results

The app shows three key percentiles:

- **p50 (Median)**: There's a 50% chance you'll finish by this date. This is the "expected" completion date.
- **p85**: There's an 85% chance you'll finish by this date. Use this for commitments requiring higher confidence.
- **p95**: There's a 95% chance you'll finish by this date. Very conservative, for when you need maximum confidence.

The S-curve visualization shows how completion probability increases over time, making it easy to see the range of likely outcomes.

## Best Practices

1. **Use sufficient historical data**: Aim for at least 10-20 historical data points for reliable estimates
2. **Keep work items consistently sized**: If your work items vary dramatically in size, consider using a different metric (story points, hours, etc.)
3. **Account for systematic changes**: If your team's velocity has recently improved or declined, weight recent data more heavily
4. **Recalculate regularly**: Update estimates as more data becomes available
5. **Remember the limits**: Estimates assume your future performance will be similar to your past performance

## Technology

- Pure HTML5, CSS3, and JavaScript
- No external dependencies
- Canvas API for visualization
- Normal distribution sampling using Box-Muller transform

## License

MIT License - See LICENSE file for details

## Author

Created as an open-source project for better project planning.
