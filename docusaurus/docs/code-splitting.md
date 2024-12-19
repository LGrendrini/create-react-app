// Complete DREAM Project for CodeSandbox

// index.js (Main Entry for Frontend)
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);

// src/App.js
import React from 'react';
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import HomeScreen from './screens/HomeScreen';
import OrderScreen from './screens/OrderScreen';

const App = () => {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<HomeScreen />} />
        <Route path="/order" element={<OrderScreen />} />
      </Routes>
    </Router>
  );
};

export default App;

// src/screens/HomeScreen.js
import React from 'react';
import { Link } from 'react-router-dom';
import './HomeScreen.css';

const HomeScreen = () => {
  return (
    <div className="home-container">
      <h1>Welcome to DREAM</h1>
      <Link to="/order">
        <button className="order-button">Place an Order</button>
      </Link>
    </div>
  );
};

export default HomeScreen;

// src/screens/HomeScreen.css
.home-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-color: #121212;
  color: #facc15;
}

.order-button {
  background-color: #facc15;
  color: #121212;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
  font-weight: bold;
  margin-top: 20px;
}

// src/screens/OrderScreen.js
import React, { useState } from 'react';
import './OrderScreen.css';

const OrderScreen = () => {
  const [order, setOrder] = useState('');

  const handleOrder = () => {
    alert(`Your order for ${order} has been placed!`);
    setOrder('');
  };

  return (
    <div className="order-container">
      <h1>Place Your Order</h1>
      <input
        type="text"
        placeholder="What do you need?"
        value={order}
        onChange={(e) => setOrder(e.target.value)}
        className="order-input"
      />
      <button onClick={handleOrder} className="submit-button">
        Submit Order
      </button>
    </div>
  );
};

export default OrderScreen;

// src/screens/OrderScreen.css
.order-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-color: #121212;
  color: #facc15;
}

.order-input {
  padding: 10px;
  margin: 20px 0;
  font-size: 16px;
  border: 2px solid #facc15;
  border-radius: 5px;
}

.submit-button {
  background-color: #facc15;
  color: #121212;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
  font-weight: bold;
}

// package.json (essential for CodeSandbox setup)
{
  "name": "dream-app",
  "version": "1.0.0",
  "private": true,
  "dependencies": {
    "react": "^18.0.0",
    "react-dom": "^18.0.0",
    "react-router-dom": "^6.4.0"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  }
}
