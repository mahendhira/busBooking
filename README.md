# 🚌 MahiBus - Complete Bus Booking Website

A modern, full-featured bus ticket booking platform built with React and Vite. This application provides a seamless experience for users to search, select seats, and book bus tickets online.

## 🌟 Features

### 1. **User Authentication**
- Login & Sign Up functionality with validation
- Demo login for testing
- User profile management
- Persistent login using localStorage
- Password validation (minimum 6 characters)
- Email validation

### 2. **Bus Search & Discovery**
- Search buses by departure city, destination, and date
- 6 sample buses from major Indian operators
- Support for 12 major Indian cities
- Filter by number of passengers (1-6)
- Swap cities functionality for return trips
- Real-time bus availability display

### 3. **Seat Selection**
- Interactive 3D-style seat map visualization
- Real-time seat availability
- Visual distinction: Available (white), Selected (red), Booked (gray)
- Maximum 6 seats per booking limit
- **Duplicate booking prevention** - prevents same seat from being booked twice
- Live seat count and pricing updates

### 4. **Booking Management**
- Complete 2-step booking process:
  - Step 1: Select seats and review summary
  - Step 2: Enter passenger details
- Passenger information form (Name, Age, Email, Phone)
- Form validation with error messages
- Price breakdown with taxes (5%) & fees
- Simulated payment processing
- Booking confirmation with reference ID

### 5. **My Bookings Dashboard**
- View all your completed bookings
- Booking details with journey information (From → To, Date, Time)
- Passenger list with seat assignments
- Booking status tracking (Confirmed/Cancelled)
- Cancel bookings functionality
- Price information display

### 6. **Duplicate Booking Prevention**
This application implements multiple layers of duplicate booking prevention:
- Seat locking: Once booked, seats cannot be selected again
- Real-time validation against all confirmed bookings
- Maximum 6 seats per single booking (prevents abuse)
- BookingContext maintains centralized booking state
- localStorage persistence ensures data consistency
- UI prevents selecting already-booked seats

## 📦 Tech Stack

- **Frontend Framework**: React 19.2.6
- **Build Tool**: Vite 8.0.12
- **Routing**: React Router DOM v6
- **Icons**: Lucide React
- **State Management**: React Context API
- **Styling**: CSS3 with BEM methodology
- **Data Storage**: localStorage (Client-side)
- **Icons**: Lucide React for UI icons

## 🏗️ Project Structure

```
src/
├── pages/
│   ├── Home.jsx                 # Landing page with features
│   ├── Login.jsx                # Authentication (signup/login)
│   ├── BusSearch.jsx            # Bus search & listing
│   ├── SeatSelection.jsx        # Interactive seat selection
│   ├── Booking.jsx              # Passenger details & confirmation
│   └── MyBookings.jsx           # Booking history & management
├── components/
│   ├── Header.jsx               # Navigation header
│   ├── Footer.jsx               # Footer component
│   ├── BusCard.jsx              # Bus listing card component
│   └── ProtectedRoute.jsx       # Authentication route wrapper
├── context/
│   ├── AuthContext.jsx          # User authentication state
│   └── BookingContext.jsx       # Booking & seat state management
├── utils/
│   ├── mockData.js              # Mock buses, cities, seat layout
│   └── api.js                   # Simulated API functions
├── styles/
│   ├── globals.css              # Global styles & utilities
│   ├── header.css               # Header & navigation styles
│   ├── footer.css               # Footer styles
│   ├── login.css                # Login page styles
│   ├── bussearch.css            # Bus search page styles
│   ├── buscard.css              # Bus card component styles
│   ├── seatselection.css        # Seat selection page styles
│   ├── booking.css              # Booking page styles
│   ├── mybookings.css           # My bookings page styles
│   └── home.css                 # Home page styles
├── App.jsx                      # Main app with routing
└── main.jsx                     # React DOM entry point
```

## 🚀 Getting Started

### Prerequisites
- Node.js 16 or higher
- npm or yarn package manager

### Installation

1. **Navigate to project directory**
```bash
cd MahiBus
```

2. **Install dependencies**
```bash
npm install
```

3. **Start development server**
```bash
npm run dev
```

4. **Open in browser**
- The app will be available at: `http://localhost:5174`
- If port 5174 is in use, Vite will use the next available port

## 📖 User Guide

### 1. **Homepage**
- Overview of MahiBus features and benefits
- Quick statistics about the platform
- Call-to-action button to start booking

### 2. **Login/Signup**
- **New Users**: Click "Sign up here" to create an account
  - Enter: Name, Email, Phone (10 digits), Password (min 6 chars)
- **Returning Users**: Enter email and password
- **Demo Access**: Click "Try Demo Login" for instant access

### 3. **Search Buses**
```
1. Select departure city (From)
2. Select destination city (To)
3. Choose travel date
4. Select number of passengers (1-6)
5. Click "Search" to see available buses
```

### 4. **Select Seats**
```
1. View interactive seat map
2. Click on available seats to select (up to 6)
3. See real-time price update with taxes
4. Review booking summary
5. Click "Continue to Booking"
```

### 5. **Complete Booking**
```
1. Enter passenger details for each seat:
   - Full Name
   - Age (5-120)
   - Email
   - Phone number
2. Review final booking summary
3. Click "Confirm & Pay"
4. Wait for payment processing
5. View confirmation with booking reference
```

### 6. **Manage Bookings**
```
1. Click "My Bookings" in navigation
2. View all your confirmed bookings
3. See passenger details and seat numbers
4. Cancel bookings (if available)
5. Check booking status
```

## 🔐 Duplicate Booking Prevention Implementation

### How It Works:

1. **Seat Status Tracking**
   ```javascript
   - Each bus maintains a list of booked seats
   - User selections are separate from confirmed bookings
   - UI prevents selecting already-booked seats
   ```

2. **Booking Context Management**
   ```javascript
   - isBookingSeatBooked(busId, seatNumber)
   - Checks if seat is already confirmed in any booking
   - Returns true if seat cannot be booked
   ```

3. **Real-time Validation**
   ```javascript
   - As user selects seats, system checks:
     - If seat is in bus.bookedSeats
     - If seat exists in confirmed bookings
     - Displays seat as "booked" if unavailable
   ```

4. **Booking Confirmation**
   ```javascript
   - New bookings are saved to BookingContext
   - Seats are marked as booked
   - Future searches show updated availability
   ```

5. **Data Persistence**
   ```javascript
   - Bookings stored in localStorage with key "bookings"
   - Persists across browser sessions
   - Survives page refreshes
   ```

## 🎨 UI/UX Features

### Responsive Design
- Mobile-first approach
- Tablet optimization (768px breakpoint)
- Desktop layout (1024px+)
- Touch-friendly buttons and forms

### Visual Feedback
- Hover effects on interactive elements
- Loading states with spinners
- Error messages in alert boxes
- Success confirmations
- Animated transitions

### Accessibility
- Semantic HTML structure
- Proper form labels
- Color-coded seat status
- Clear navigation
- Error messaging

## 📊 Mock Data

Pre-configured data includes:

### Buses (6 samples)
- MahiBus Premium (₹450)
- MakeMyTrip Travel (₹380)
- Redbus Express (₹320)
- Sharma Travels Deluxe (₹550)
- SkyLine Travels (₹400)
- Night Rider Premium (₹480)

### Cities (12 major)
- Mumbai, Delhi, Bangalore, Hyderabad
- Chennai, Kolkata, Pune, Jaipur
- Lucknow, Chandigarh, Ahmedabad, Indore

### Seat Layout
- 45 seats total
- 9 rows × 5 columns
- Middle column as aisle

## 🔄 Data Flow

```
Authentication
    ↓
Home Page
    ↓
Bus Search → Select Route
    ↓
View Buses → Choose Bus
    ↓
Seat Selection → Pick Seats
    ↓
Enter Passenger Details
    ↓
Review & Confirm Booking
    ↓
Booking Confirmation
    ↓
View in My Bookings Dashboard
```

## 💾 Storage Structure

### localStorage Keys

1. **user**
   ```json
   {
     "id": "email",
     "name": "John Doe",
     "email": "email@example.com",
     "phone": "9876543210"
   }
   ```

2. **bookings**
   ```json
   [
     {
       "id": "BK1234567890",
       "busId": "BUS001",
       "seats": [5, 6, 7],
       "passengers": [...],
       "status": "confirmed",
       "totalPrice": 1500
     }
   ]
   ```

3. **selectedSeats** - Temporary user selection

4. **selectedBus** - Current bus context

5. **searchParams** - Last search criteria

## 🧪 Testing Checklist

### Authentication
- [ ] Signup with valid credentials
- [ ] Signup validation (email, phone format)
- [ ] Login with credentials
- [ ] Demo login works
- [ ] Logout functionality
- [ ] Session persists after refresh

### Bus Search
- [ ] Search with all parameters filled
- [ ] Validation on empty fields
- [ ] Swap cities functionality
- [ ] Result listing displays correctly
- [ ] Bus sorting/filtering options

### Seat Selection
- [ ] Seat map displays correctly
- [ ] Can select available seats
- [ ] Cannot select booked seats
- [ ] Maximum 6 seat limit
- [ ] Price updates on selection
- [ ] Deselection works

### Booking
- [ ] Passenger form validation
- [ ] All fields required
- [ ] Age validation (5-120)
- [ ] Phone format validation
- [ ] Payment simulation
- [ ] Confirmation page displays

### Duplicate Prevention
- [ ] Booked seats show as unavailable
- [ ] Cannot select same seat twice
- [ ] Bookings persist after refresh
- [ ] Multiple bookings don't overlap
- [ ] Seat count accurate

### My Bookings
- [ ] View all bookings
- [ ] Booking details correct
- [ ] Passenger info displays
- [ ] Cancel booking works
- [ ] Status updates correctly

## 🛠️ Development Commands

```bash
# Start development server (with HMR)
npm run dev

# Build for production
npm run build

# Preview production build locally
npm run preview

# Run ESLint
npm run lint
```

## 📱 Browser Support

| Browser | Support |
|---------|---------|
| Chrome  | ✅ Latest |
| Firefox | ✅ Latest |
| Safari  | ✅ Latest |
| Edge    | ✅ Latest |

## 🎓 Learning Resources Demonstrated

This project showcases:
- React Hooks: useState, useContext, useEffect
- Context API for global state management
- React Router for multi-page navigation
- Form handling and validation
- localStorage API
- CSS Grid and Flexbox layouts
- Responsive design patterns
- Component composition
- Protected routes
- Mock API implementation
- Error handling

## 🚀 Future Enhancements

- Real payment gateway (Stripe/PayPal)
- SMS/Email notifications
- WebSocket for real-time updates
- Admin panel for bus management
- Advanced filters (Bus type, Amenities)
- Promotional codes
- Multi-language support (i18n)
- User reviews and ratings
- Round-trip bookings
- Travel insurance options
- Seat selection preferences
- Recurring bookings
- Customer support chat

## 📄 License

This project is created for educational purposes.

## 👨‍💻 Created By

Full-stack bus booking application demonstration

## 📞 Support

For questions or issues, please refer to the application's help section or contact: support@Mahibus.com

---

**Happy Booking! 🎉**
