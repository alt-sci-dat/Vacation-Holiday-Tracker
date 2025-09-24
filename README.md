# Vacation Holiday Tracker

A comprehensive holiday calendar application that helps you track holidays across multiple countries with an intuitive, visually appealing interface. Built with React.js frontend and Node.js backend, this application provides real-time holiday information with multiple viewing modes.

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Screenshots](#-screenshots)
- [Installation](#-installation)
- [Usage](#-usage)
- [API Reference](#-api-reference)
- [Project Structure](#-project-structure)
- [Configuration](#-configuration)
- [Contributing](#-contributing)
- [License](#-license)

## ✨ Features

### 🌍 Multi-Country Support
- Support for 10+ countries including US, UK, Canada, India, Australia, Germany, France, Japan, Brazil, and Mexico
- Real-time country selection with flag indicators
- Automatic holiday data fetching based on selected country

### 📅 Multiple View Modes
- **Monthly View**: Detailed month-by-month holiday calendar
- **Quarterly View**: 3-month overview with consolidated holiday information
- **Yearly View**: Complete year overview with all holidays

### 🎨 Visual Calendar Features
- **Color-coded Weeks**: 
  - Light green for weeks with 1 holiday
  - Dark green for weeks with 2+ holidays
  - Clean white background for regular weeks
- **Interactive Navigation**: Easy month/quarter/year navigation
- **Holiday Tooltips**: Hover to see holiday names and details
- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile devices

### 🔄 Smart Data Management
- **API Integration**: Connects to Calendarific API for real-time holiday data
- **Fallback System**: Mock data support when API is unavailable
- **Error Handling**: Graceful error states with user-friendly messages
- **Loading States**: Smooth loading indicators during data fetching

### 🛡️ Security & Performance
- **Rate Limiting**: Protected API endpoints
- **CORS Configuration**: Secure cross-origin requests
- **Input Validation**: Comprehensive request validation
- **Error Boundaries**: React error boundaries for crash prevention

## 🛠️ Tech Stack

### Frontend
- **React.js 18** - Modern React with hooks
- **Moment.js** - Date manipulation and formatting
- **CSS3** - Custom styling with responsive design
- **Axios** - HTTP client for API requests

### Backend
- **Node.js** - JavaScript runtime
- **Express.js** - Web application framework
- **Moment.js** - Server-side date handling
- **Helmet** - Security middleware
- **CORS** - Cross-origin resource sharing
- **Express Rate Limit** - API rate limiting

### External Services
- **Calendarific API** - Holiday data provider
- **Mock Data System** - Fallback for offline usage

## 📸 Screenshots

### Monthly View

<img width="1710" height="1112" alt="Screenshot 2025-09-24 at 6 54 19 PM" src="https://github.com/user-attachments/assets/471ae377-0ffe-4038-8580-ca5636d5253e" />

*Clean monthly calendar showing holidays with color-coded weeks*

### Quarterly View  

<img width="1710" height="1112" alt="Screenshot 2025-09-24 at 7 19 27 PM" src="https://github.com/user-attachments/assets/d3de085c-3878-4cf4-8966-45382850f7fe" />

*Three-month overview with consolidated holiday information*

### Yearly View 

<img width="1710" height="1112" alt="Screenshot 2025-09-24 at 7 13 40 PM" src="https://github.com/user-attachments/assets/53f73f23-ec89-409a-b0e1-47d8bbea7b70" />

*Yearly overview with consolidated holiday information (If observed carefully the transparent dark green represents multiple holidays where somewhat light transparent green shows one holiday in a week and it also highlights the main holiday-Days)*

### Country Selection

<img width="1710" height="1112" alt="Screenshot 2025-09-24 at 6 54 29 PM" src="https://github.com/user-attachments/assets/4df9a564-e7ae-4e25-a432-539147b6bd19" />

*Dropdown menu with country flags and names for easy selection*

### Holiday Details

<img width="911" height="565" alt="Screenshot 2025-09-24 at 7 21 27 PM" src="https://github.com/user-attachments/assets/f8bc6bde-1e37-4dcb-b6b1-ca3eedfcd7b1" />

*Detailed view showing holiday names and dates*

## 🚀 Installation

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- Git

### Clone the Repository
```bash
git clone https://github.com/alt-sci-dat/Vacation-Holiday-Tracker.git
cd Vacation-Holiday-Tracker
```

### Backend Setup
```bash
cd backend
npm install

# Copy environment file
cp .env.example .env

# Add your API key (optional)
# Edit .env file and add: CALENDARIFIC_API_KEY=your_key_here

# Start the backend server
npm run dev
```

The backend server will start on `http://localhost:3001`

### Frontend Setup
```bash
cd frontend
npm install

# Start the React development server
npm start
```

The frontend application will start on `http://localhost:3000`

## 💡 Usage

### Basic Usage
1. **Start the Application**: Follow the installation steps above
2. **Select Country**: Use the dropdown to choose your preferred country
3. **Choose View Mode**: Select between Monthly, Quarterly, or Yearly view
4. **Navigate Dates**: Use the navigation buttons to browse different time periods
5. **View Holidays**: Hover over colored weeks to see holiday details

### API Key Configuration (Optional)
1. Get a free API key from [Calendarific](https://calendarific.com/)
2. Add it to your `backend/.env` file:
   ```
   CALENDARIFIC_API_KEY=your_api_key_here
   ```
3. Restart the backend server

**Note**: The application works with mock data if no API key is provided.

## 🔌 API Reference

### Get Holidays
```http
GET /api/holidays?country={country_code}&year={year}&month={month}
```

**Parameters:**
- `country` (required): Two-letter country code (e.g., 'US', 'IN')
- `year` (required): Four-digit year (e.g., 2024)
- `month` (optional): Month number 1-12

### Get Quarterly Holidays
```http
GET /api/holidays/quarterly?country={country_code}&year={year}&quarter={quarter}
```

**Parameters:**
- `country` (required): Two-letter country code
- `year` (required): Four-digit year
- `quarter` (required): Quarter number 1-4

### Get Countries
```http
GET /api/countries
```

Returns list of supported countries with codes and names.

## 📁 Project Structure

```
Vacation-Holiday-Tracker/
├── backend/
│   ├── middleware/
│   │   └── validation.js          # Request validation middleware
│   ├── routes/
│   │   ├── countries.js           # Country-related routes
│   │   └── holidays.js            # Holiday-related routes
│   ├── services/
│   │   ├── countryService.js      # Country data service
│   │   └── holidayService.js      # Holiday API integration
│   ├── .env.example               # Environment variables template
│   ├── package.json               # Backend dependencies
│   └── server.js                  # Express server setup
├── frontend/
│   ├── public/
│   │   ├── index.html             # HTML template
│   │   └── manifest.json          # PWA manifest
│   ├── src/
│   │   ├── components/
│   │   │   ├── CountrySelector.js # Country selection component
│   │   │   ├── ErrorBoundary.js   # Error handling component
│   │   │   ├── HolidayCalendar.js # Main calendar component
│   │   │   ├── HolidayCalendar.css# Calendar styling
│   │   │   ├── HolidayLegend.js   # Color legend component
│   │   │   ├── LoadingSpinner.js  # Loading indicator
│   │   │   └── ViewSelector.js    # View mode selector
│   │   ├── services/
│   │   │   ├── countryService.js  # Frontend country service
│   │   │   └── holidayService.js  # Frontend holiday service
│   │   ├── App.js                 # Main React component
│   │   ├── App.css                # Application styling
│   │   ├── index.js               # React entry point
│   │   └── index.css              # Global styles
│   └── package.json               # Frontend dependencies
└── .gitignore                     # Git ignore file
```

## ⚙️ Configuration

### Environment Variables
Create a `.env` file in the backend directory:

```env
# Optional: Calendarific API key for real holiday data
CALENDARIFIC_API_KEY=your_api_key_here

# Server configuration
PORT=3001
NODE_ENV=development

# Rate limiting
RATE_LIMIT_WINDOW_MS=900000
RATE_LIMIT_MAX_REQUESTS=100
```

### Supported Countries
The application supports holidays for the following countries:
- 🇺🇸 United States (US)
- 🇬🇧 United Kingdom (GB)
- 🇨🇦 Canada (CA)
- 🇮🇳 India (IN)
- 🇦🇺 Australia (AU)
- 🇩🇪 Germany (DE)
- 🇫🇷 France (FR)
- 🇯🇵 Japan (JP)
- 🇧🇷 Brazil (BR)
- 🇲🇽 Mexico (MX)

## 🎯 Features in Detail

### Color-Coded Week System
The calendar uses an intelligent color-coding system:
- **White Background**: No holidays in the week
- **Light Green (#90EE90)**: Exactly 1 holiday in the week
- **Dark Green (#228B22)**: 2 or more holidays in the week

### Responsive Design
The application is fully responsive and works on:
- Desktop computers (1200px+)
- Tablets (768px - 1199px)
- Mobile phones (320px - 767px)

### Error Handling
Comprehensive error handling includes:
- Network connectivity issues
- API rate limiting
- Invalid date ranges
- Malformed API responses
- Server downtime fallbacks

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines
- Follow existing code style and conventions
- Add appropriate comments for complex logic
- Test your changes thoroughly
- Update documentation as needed

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

If you encounter any issues or have questions:

1. Check the [Issues](https://github.com/alt-sci-dat/Vacation-Holiday-Tracker/issues) page
2. Create a new issue with detailed information
3. Include steps to reproduce the problem
4. Mention your operating system and browser version

---

**Made with ❤️ by the Alt Sci Dat Team**

*Enjoy tracking holidays around the world! 🌍*
