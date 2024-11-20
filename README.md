# datafun-06-eda
Project 6 for Data Fundamentals grad course

## External Dependencies

This project requires the following external libraries. Local Python environment recommended. 

- jupyterlab
- matplotlib
- pandas
- pyarrow
- seaborn

## Objective

Perform and publish a custom EDA project to demonstrate skills with Jupyter, pandas, Seaborn and popular tools for data analytics. The notebook should tell a data story and visually present findings in a clear and engaging manner.


## Data 

Going to dive into NBA data, specifically to analyze usage rates and how they compare to efficiency, PER, True Shooting Percentage, Points per Weighted Shot and the traditional stats. Then I breakdown and visualize those relationships by position.

### 1. **Project Setup**
1. **Choose Your Stack**:
   - Frontend: HTML/CSS, JavaScript (React, D3, Plotly)
   - Backend: Python (Flask or Django) if you want a server-side component.
   - Database: SQLite for data storage.

### 2. **Data Acquisition**
1. **Fetch NBA Data**:
   - Use APIs like [NBA Stats API](https://rapidapi.com/api-sports/api/api-nba) or [Basketball Reference](https://www.basketball-reference.com/).
   - Use the `requests` library in Python to fetch data.

### 3. **Data Processing**
1. **Clean and Prepare Data**:
   - Use `pandas` and `numpy` for data manipulation.
   - Store the cleaned data in an SQLite database.

### 4. **Backend Development** (Optional)
1. **API Development**:
   - Create endpoints for fetching player and team data.
   - Use Flask or Django to build your API.

### 5. **Frontend Development**
1. **Setup React App**:
   - Create a new React application using Create React App.
   - Organize your project structure.

2. **Implement Data Fetching**:
   - Use `fetch` or `axios` to retrieve data from your backend or directly from the API.

3. **Build Dashboard Components**:
   - **Filters**: Create dropdowns or toggle buttons to switch between player and team data.
   - **Player Statistics**: 
     - Use D3 or Plotly to create a spider/radar chart displaying six key statistics (points per game, assists per game, rebounds per game, true shooting percentage, PER).
   - **Team Statistics**: Display team-level data in an interactive table or chart.

### 6. **Visualization**
1. **D3/Plotly Integration**:
   - Integrate D3 or Plotly with React to build interactive charts.

2. **Styling**:
   - Use CSS or libraries like Styled-components to style your dashboard.

### 7. **Deployment**
1. **Deploy to GitHub Pages**:
   - Build your React app using `npm run build`.
   - Push the build to the `gh-pages` branch of your GitHub repository.
   - Configure GitHub Pages settings to serve your site from the `gh-pages` branch.

### 8. **Testing and Optimization**
1. **Testing**:
   - Test the interactive features and ensure data updates correctly.

2. **Optimization**:
   - Optimize your code for performance and responsiveness.

### 9. **Documentation**
1. **Write Documentation**:
   - Create a README.md file with instructions on how to run and use your project.
   - Document the code and provide comments for clarity.

---

Here's a simplified example structure for the frontend using React and Plotly:

```javascript
// src/App.js
import React, { useState, useEffect } from 'react';
import axios from 'axios';
import Plot from 'react-plotly.js';

function App() {
  const [data, setData] = useState([]);
  const [view, setView] = useState('player'); // 'player' or 'team'

  useEffect(() => {
    // Fetch data from API
    axios.get('/api/nba-data').then((response) => setData(response.data));
  }, []);

  const renderPlayerChart = () => (
    <Plot
      data={[
        {
          type: 'scatterpolar',
          r: [30, 20, 25, 22, 18, 24],
          theta: ['PPG', 'APG', 'RPG', 'TS%', 'PER'],
          fill: 'toself',
        },
      ]}
      layout={{ polar: { radialaxis: { visible: true } }, showlegend: false }}
    />
  );

  return (
    <div>
      <h1>NBA Data Dashboard</h1>
      <button onClick={() => setView('player')}>Player Stats</button>
      <button onClick={() => setView('team')}>Team Stats</button>
      {view === 'player' ? renderPlayerChart() : <div>Team Stats Component</div>}
    </div>
  );
}

export default App;
```
