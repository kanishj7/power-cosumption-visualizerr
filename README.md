# power-cosumption-visualizerr
Energy Consumption Visualizer is a web app built with HTML, CSS and JavaScript. Users sign up and log in to view a dashboard with total usage, estimated bill, daily average and savings, plus appliance breakdown, a bill calculator, saving tips and dark mode. Data is stored locally in the browser.
Energy Consumption Visualizer is a single-page web application for tracking household electricity usage. It is written in plain HTML, CSS and JavaScript, with no frameworks or external libraries, and the whole project fits in one file, energy-visualizer.html. Users create an account, sign in, and reach a dashboard that shows how much electricity they use, what it costs, which appliances use the most, and how to reduce it. All costs are in Indian rupees (₹) at a tariff of ₹6.50 per unit.
Energy Consumption Visualizer is a single-page web application for tracking household electricity usage. It is written in plain HTML, CSS and JavaScript, with no frameworks or external libraries, and the whole project fits in one file, energy-visualizer.html. Users create an account, sign in, and reach a dashboard that shows how much electricity they use, what it costs, which appliances use the most, and how to reduce it. All costs are in Indian rupees (₹) at a tariff of ₹6.50 per unit.

How the Application Works

The app has three screens inside one page. JavaScript shows one and hides the others, so there are no page reloads.

Sign In is the first screen. The user enters a 10-digit mobile number and a password, and a Show/Hide button reveals the password while typing. A link at the bottom leads to account creation.
Create Account collects a full name, mobile number and password.
Dashboard opens after a successful sign-in or sign-up. This is the “second page” of the flow.

When the page loads, it checks whether a session already exists. If so, it goes straight to the dashboard. Otherwise it shows the Sign In screen.

Authentication and Validation

Authentication is handled entirely in the browser:

Mobile number: must be exactly 10 digits.
Password: must be at least 6 characters when creating an account.
Duplicate check: a mobile number that is already registered cannot sign up again.
Error messages: clear text appears on the form for each case, such as “No account found” or “Incorrect password.”
Password storage: passwords are not saved as plain text. They are converted to a SHA-256 hash using the browser’s built-in Web Crypto API, and sign-in compares hashes.
Session: after login, the mobile number is stored as the active session. Logout removes it and returns to the Sign In screen.
Dashboard Sections

The dashboard has a top navigation bar with six tabs, plus a theme toggle, a greeting (“Hi, [first name]”) and a Logout button.

Dashboard is the home tab. It shows the current month (November 2026) and the tariff, followed by four summary cards:

Total Energy Usage: 265.9 kWh
Estimated Electricity Bill: ₹1728.35
Average Daily Consumption: 8.9 kWh
Energy Saved: 12.1%

The figures are linked. The total is the sum of the appliance readings, the bill is the total times the tariff, and the daily average is the total divided by 30.

Energy Usage shows weekly consumption for the month as horizontal bars scaled against the highest week, so the busiest week is visible at a glance.

Appliances is a table listing each appliance’s monthly usage in kWh and its percentage share of the total. The sample appliances are Air Conditioner, Refrigerator, Water Heater, Lighting, Fans, Washing Machine, Television and Others. The air conditioner is the largest consumer.

Bill Calculator is interactive. The user enters units consumed and a rate per unit, and the estimated bill updates as they type. It starts with the sample usage and the ₹6.50 tariff.

Energy Saving Tips lists practical advice, including setting the AC to 24–26 °C, using LED bulbs, unplugging standby devices, running full washing loads, choosing star-rated appliances and managing the water heater.

About is a short paragraph explaining the app’s purpose.

Design and User Experience

The interface uses a clean card-based layout with rounded corners, soft borders and a green and blue colour scheme. The green logo badge appears on every screen. Each summary card has a small icon (⚡, ₹, 📅, 🍃).

A Dark/Light mode button switches the whole theme. The choice is saved in the browser and restored on the next visit. The colours are CSS variables, so the switch is instant and consistent.

The layout is responsive. The cards use a flexible grid that rearranges to fit the screen width, and the navigation wraps on narrow screens.

Technical Structure
HTML: three view containers (sign-in, sign-up, dashboard) and six dashboard sections.
CSS: embedded in the same file, using CSS variables for theming and a .hidden class for showing and hiding views and tabs.
JavaScript: embedded in the same file, covering view switching, form validation, hashing, rendering data, the calculator, tabs, theme control and logout.
Storage: localStorage holds three things: registered users (name and hashed password, keyed by mobile number), the active session, and the theme preference.
Limitations
Not real security: authentication runs in the browser, so anyone with access to the browser’s developer tools can inspect or alter stored data. The hashing is unsalted. A real product needs a backend server with secure authentication.
Sample data: the usage figures are fixed demo values, not live meter readings, and the “Energy Saved” percentage is a static example.
Single device: accounts exist only in the browser where they were created.
Possible Future Improvements
A backend and database for real accounts and password security
Real usage data through manual entry, CSV upload or smart-meter integration
Charting for monthly trends and appliance comparisons
Slab-based tariff calculation, as many electricity boards use tiered rates
Usage alerts and budget goals
Month-by-month history and exportable reports

versal link:https://energy-visualizer-five.vercel.app/
