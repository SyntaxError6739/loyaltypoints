# loyaltypoints<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Business Loyalty System</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            text-align: center;
            color: white;
            margin-bottom: 30px;
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .header p {
            font-size: 1.2em;
            opacity: 0.9;
        }

        .main-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-bottom: 30px;
        }

        .card {
            background: white;
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.3);
        }

        .card h2 {
            color: #667eea;
            margin-bottom: 20px;
            font-size: 1.8em;
            border-bottom: 2px solid #f0f0f0;
            padding-bottom: 10px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #555;
        }

        .form-group input,
        .form-group select {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 16px;
            transition: border-color 0.3s ease;
        }

        .form-group input:focus,
        .form-group select:focus {
            outline: none;
            border-color: #667eea;
        }

        .btn {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: all 0.3s ease;
            width: 100%;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        .btn-secondary {
            background: linear-gradient(45deg, #28a745, #20c997);
            margin-top: 10px;
        }

        .customer-list {
            grid-column: 1 / -1;
        }

        .customer-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .customer-card {
            background: linear-gradient(135deg, #f8f9fa, #e9ecef);
            border-radius: 12px;
            padding: 20px;
            border-left: 5px solid #667eea;
            transition: all 0.3s ease;
        }

        .customer-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
        }

        .customer-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }

        .customer-name {
            font-size: 1.3em;
            font-weight: 700;
            color: #333;
        }

        .customer-phone {
            color: #666;
            font-size: 0.95em;
        }

        .visit-info {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 15px;
        }

        .stat {
            text-align: center;
            padding: 10px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .stat-number {
            font-size: 1.8em;
            font-weight: 700;
            color: #667eea;
        }

        .stat-label {
            font-size: 0.9em;
            color: #666;
            margin-top: 5px;
        }

        .reward-status {
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.9em;
            font-weight: 600;
            text-align: center;
        }

        .reward-eligible {
            background: linear-gradient(45deg, #28a745, #20c997);
            color: white;
        }

        .reward-progress {
            background: linear-gradient(45deg, #ffc107, #fd7e14);
            color: white;
        }

        .action-buttons {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }

        .btn-small {
            padding: 8px 15px;
            font-size: 14px;
            flex: 1;
        }

        .success-message,
        .error-message {
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            font-weight: 600;
        }

        .success-message {
            background: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }

        .error-message {
            background: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }

        .search-bar {
            margin-bottom: 20px;
        }

        .stats-overview {
            grid-column: 1 / -1;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            margin-bottom: 20px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .overview-stat {
            text-align: center;
            padding: 20px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
        }

        .overview-number {
            font-size: 2.5em;
            font-weight: 700;
            margin-bottom: 5px;
        }

        @media (max-width: 768px) {
            .main-grid {
                grid-template-columns: 1fr;
            }

            .customer-grid {
                grid-template-columns: 1fr;
            }

            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="header">
            <h1>🏪 Business Loyalty System</h1>
            <p>Track customer visits and reward loyal patrons</p>
        </div>

        <div id="message-container"></div>

        <div class="card stats-overview">
            <h2 style="color: white; border-bottom-color: rgba(255,255,255,0.3);">📊 Business Overview</h2>
            <div class="stats-grid">
                <div class="overview-stat">
                    <div class="overview-number" id="total-customers">0</div>
                    <div>Total Customers</div>
                </div>
                <div class="overview-stat">
                    <div class="overview-number" id="total-visits">0</div>
                    <div>Total Visits</div>
                </div>
                <div class="overview-stat">
                    <div class="overview-number" id="rewards-earned">0</div>
                    <div>Rewards Earned</div>
                </div>
                <div class="overview-stat">
                    <div class="overview-number" id="avg-visits">0</div>
                    <div>Avg Visits/Customer</div>
                </div>
            </div>
        </div>

        <div class="main-grid">
            <div class="card">
                <h2>👤 Register New Customer</h2>
                <form id="register-form">
                    <div class="form-group">
                        <label for="customer-name">Customer Name</label>
                        <input type="text" id="customer-name" required placeholder="Enter customer name">
                    </div>
                    <div class="form-group">
                        <label for="customer-phone">Phone Number</label>
                        <input type="tel" id="customer-phone" required placeholder="(555) 123-4567">
                    </div>
                    <button type="submit" class="btn">Register Customer</button>
                </form>
            </div>

            <div class="card">
                <h2>📱 Record Visit</h2>
                <form id="visit-form">
                    <div class="form-group">
                        <label for="visit-phone">Customer Phone</label>
                        <input type="tel" id="visit-phone" required placeholder="(555) 123-4567">
                    </div>
                    <div class="form-group">
                        <label for="visit-amount">Purchase Amount ($)</label>
                        <input type="number" id="visit-amount" step="0.01" min="0" placeholder="0.00">
                    </div>
                    <button type="submit" class="btn">Record Visit</button>
                    <button type="button" class="btn btn-secondary" onclick="findCustomer()">Find Customer</button>
                </form>
            </div>
        </div>

        <div class="card customer-list">
            <h2>👥 Customer Database</h2>
            <div class="search-bar">
                <input type="text" id="search-input" placeholder="Search by name or phone number..."
                    style="margin-bottom: 0;">
            </div>
            <div class="customer-grid" id="customer-grid">
                <!-- Customer cards will be dynamically generated here -->
            </div>
        </div>
    </div>

    <script>
        // In-memory storage for customer data
        let customer = {};
        let setting = {
            visitsForReward: 10,
            rewardAmount: 10.00
        };

        // Initialize with sample data
        function initializeSampleData() {
            const sampleCustomers = [
                { name: 'John Smith', phone: '(555) 123-4567', visits: 5, totalSpent: 125.50, rewards: 0 },
                { name: 'Sarah Johnson', phone: '(555) 987-6543', visits: 12, totalSpent: 340.75, rewards: 1 },
                { name: 'Mike Davis', phone: '(555) 456-7890', visits: 8, totalSpent: 89.25, rewards: 0 }
            ];

            sampleCustomers.forEach(customer => {
                customers[customer.phone] = {
                    name: customer.name,
                    visits: customer.visits,
                    totalSpent: customer.totalSpent,
                    rewards: customer.rewards,
                    lastVisit: new Date().toLocaleDateString(),
                    joinDate: new Date().toLocaleDateString()
                };
            });

            updateDisplay();
        }

        // Format phone number
        function formatPhone(phone) {
            const cleaned = phone.replace(/\D/g, '');
            if (cleaned.length === 10) {
                return `(${cleaned.slice(0, 3)}) ${cleaned.slice(3, 6)}-${cleaned.slice(6)}`;
            }
            return phone;
        }

        // Show message
        function showMessage(text, type = 'success') {
            const container = document.getElementById('message-container');
            const message = document.createElement('div');
            message.className = type === 'success' ? 'success-message' : 'error-message';
            message.textContent = text;
            container.appendChild(message);

            setTimeout(() => {
                container.removeChild(message);
            }, 5000);
        }

        // Register new customer
        document.getElementById('register-form').addEventListener('submit', function (e) {
            e.preventDefault();

            const name = document.getElementById('customer-name').value.trim();
            const phone = formatPhone(document.getElementById('customer-phone').value);

            if (customers[phone]) {
                showMessage('Customer with this phone number already exists!', 'error');
                return;
            }

            customers[phone] = {
                name: name,
                visits: 0,
                totalSpent: 0,
                rewards: 0,
                lastVisit: null,
                joinDate: new Date().toLocaleDateString()
            };

            showMessage(`Customer ${name} registered successfully!`);
            this.reset();
            updateDisplay();
        });

        // Record visit
        document.getElementById('visit-form').addEventListener('submit', function (e) {
            e.preventDefault();

            const phone = formatPhone(document.getElementById('visit-phone').value);
            const amount = parseFloat(document.getElementById('visit-amount').value) || 0;

            if (!customers[phone]) {
                showMessage('Customer not found! Please register first.', 'error');
                return;
            }

            const customer = customers[phone];
            customer.visits++;
            customer.totalSpent += amount;
            customer.lastVisit = new Date().toLocaleDateString();

            // Check for reward eligibility
            const visitsToReward = settings.visitsForReward - (customer.visits % settings.visitsForReward);
            if (customer.visits % settings.visitsForReward === 0) {
                customer.rewards++;
                showMessage(`🎉 ${customer.name} earned a reward! Total rewards: ${customer.rewards}`);
            } else {
                showMessage(`Visit recorded for ${customer.name}! ${visitsToReward} more visits until next reward.`);
            }

            this.reset();
            updateDisplay();
        });

        // Find customer
        function findCustomer() {
            const phone = formatPhone(document.getElementById('visit-phone').value);

            if (customers[phone]) {
                const customer = customers[phone];
                const visitsToReward = settings.visitsForReward - (customer.visits % settings.visitsForReward);
                showMessage(`Found: ${customer.name} - ${customer.visits} visits, ${visitsToReward} visits until next reward`);
            } else {
                showMessage('Customer not found!', 'error');
            }
        }

        // Redeem reward
        function redeemReward(phone) {
            const customer = customers[phone];
            if (customer.rewards > 0) {
                customer.rewards--;
                showMessage(`Reward redeemed for ${customer.name}! Remaining rewards: ${customer.rewards}`);
                updateDisplay();
            }
        }

        // Delete customer
        function deleteCustomer(phone) {
            if (confirm(`Are you sure you want to delete ${customers[phone].name}?`)) {
                delete customers[phone];
                showMessage('Customer deleted successfully!');
                updateDisplay();
            }
        }

        // Update display
        function updateDisplay() {
            const grid = document.getElementById('customer-grid');
            const searchTerm = document.getElementById('search-input').value.toLowerCase();

            // Calculate stats
            const totalCustomers = Object.keys(customers).length;
            const totalVisits = Object.values(customers).reduce((sum, c) => sum + c.visits, 0);
            const totalRewards = Object.values(customers).reduce((sum, c) => sum + c.rewards, 0);
            const avgVisits = totalCustomers > 0 ? (totalVisits / totalCustomers).toFixed(1) : 0;

            document.getElementById('total-customers').textContent = totalCustomers;
            document.getElementById('total-visits').textContent = totalVisits;
            document.getElementById('rewards-earned').textContent = totalRewards;
            document.getElementById('avg-visits').textContent = avgVisits;

            // Filter customers
            const filteredCustomers = Object.entries(customers).filter(([phone, customer]) => {
                return customer.name.toLowerCase().includes(searchTerm) ||
                    phone.toLowerCase().includes(searchTerm);
            });

            // Sort by visits (descending)
            filteredCustomers.sort((a, b) => b[1].visits - a[1].visits);

            grid.innerHTML = '';

            if (filteredCustomers.length === 0) {
                grid.innerHTML = '<p style="text-align: center; color: #666; grid-column: 1 / -1;">No customers found.</p>';
                return;
            }

            filteredCustomers.forEach(([phone, customer]) => {
                const visitsToReward = settings.visitsForReward - (customer.visits % settings.visitsForReward);
                const isEligible = customer.rewards > 0;

                const card = document.createElement('div');
                card.className = 'customer-card';
                card.innerHTML = `
                    <div class="customer-info">
                        <div>
                            <div class="customer-name">${customer.name}</div>
                            <div class="customer-phone">${phone}</div>
                        </div>
                    </div>
                    
                    <div class="visit-info">
                        <div class="stat">
                            <div class="stat-number">${customer.visits}</div>
                            <div class="stat-label">Visits</div>
                        </div>
                        <div class="stat">
                            <div class="stat-number">${customer.rewards}</div>
                            <div class="stat-label">Rewards</div>
                        </div>
                    </div>
                    
                    <div class="reward-status ${isEligible ? 'reward-eligible' : 'reward-progress'}">
                        ${isEligible ? '🎁 Reward Available!' : `⭐ ${visitsToReward} visits to reward`}
                    </div>
                    
                    <div style="font-size: 0.9em; color: #666; margin-top: 10px;">
                        <div>Total Spent: $${customer.totalSpent.toFixed(2)}</div>
                        <div>Last Visit: ${customer.lastVisit || 'Never'}</div>
                        <div>Joined: ${customer.joinDate}</div>
                    </div>
                    
                    <div class="action-buttons">
                        <button class="btn btn-small" onclick="redeemReward('${phone}')" 
                                ${customer.rewards === 0 ? 'disabled style="opacity: 0.5"' : ''}>
                            Redeem Reward
                        </button>
                        <button class="btn btn-small" onclick="deleteCustomer('${phone}')" 
                                style="background: linear-gradient(45deg, #dc3545, #c82333);">
                            Delete
                        </button>
                    </div>
                `;

                grid.appendChild(card);
            });
        }

        // Search functionality
        document.getElementById('search-input').addEventListener('input', updateDisplay);

        // Initialize the app
        initializeSampleData();
    </script>
</body>

</html>
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Business Loyalty System</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            text-align: center;
            color: white;
            margin-bottom: 30px;
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .header p {
            font-size: 1.2em;
            opacity: 0.9;
        }

        .main-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-bottom: 30px;
        }

        .card {
            background: white;
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.3);
        }

        .card h2 {
            color: #667eea;
            margin-bottom: 20px;
            font-size: 1.8em;
            border-bottom: 2px solid #f0f0f0;
            padding-bottom: 10px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #555;
        }

        .form-group input,
        .form-group select {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 16px;
            transition: border-color 0.3s ease;
        }

        .form-group input:focus,
        .form-group select:focus {
            outline: none;
            border-color: #667eea;
        }

        .btn {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: all 0.3s ease;
            width: 100%;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        .btn-secondary {
            background: linear-gradient(45deg, #28a745, #20c997);
            margin-top: 10px;
        }

        .customer-list {
            grid-column: 1 / -1;
        }

        .customer-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .customer-card {
            background: linear-gradient(135deg, #f8f9fa, #e9ecef);
            border-radius: 12px;
            padding: 20px;
            border-left: 5px solid #667eea;
            transition: all 0.3s ease;
        }

        .customer-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
        }

        .customer-info {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }

        .customer-name {
            font-size: 1.3em;
            font-weight: 700;
            color: #333;
        }

        .customer-phone {
            color: #666;
            font-size: 0.95em;
        }

        .visit-info {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-bottom: 15px;
        }

        .stat {
            text-align: center;
            padding: 10px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .stat-number {
            font-size: 1.8em;
            font-weight: 700;
            color: #667eea;
        }

        .stat-label {
            font-size: 0.9em;
            color: #666;
            margin-top: 5px;
        }

        .reward-status {
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.9em;
            font-weight: 600;
            text-align: center;
        }

        .reward-eligible {
            background: linear-gradient(45deg, #28a745, #20c997);
            color: white;
        }

        .reward-progress {
            background: linear-gradient(45deg, #ffc107, #fd7e14);
            color: white;
        }

        .action-buttons {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }

        .btn-small {
            padding: 8px 15px;
            font-size: 14px;
            flex: 1;
        }

        .success-message,
        .error-message {
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            font-weight: 600;
        }

        .success-message {
            background: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }

        .error-message {
            background: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }

        .search-bar {
            margin-bottom: 20px;
        }

        .stats-overview {
            grid-column: 1 / -1;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            margin-bottom: 20px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .overview-stat {
            text-align: center;
            padding: 20px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
        }

        .overview-number {
            font-size: 2.5em;
            font-weight: 700;
            margin-bottom: 5px;
        }

        @media (max-width: 768px) {
            .main-grid {
                grid-template-columns: 1fr;
            }

            .customer-grid {
                grid-template-columns: 1fr;
            }

            .stats-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="header">
            <h1>🏪 Business Loyalty System</h1>
            <p>Track customer visits and reward loyal patrons</p>
        </div>

        <div id="message-container"></div>

        <div class="card stats-overview">
            <h2 style="color: white; border-bottom-color: rgba(255,255,255,0.3);">📊 Business Overview</h2>
            <div class="stats-grid">
                <div class="overview-stat">
                    <div class="overview-number" id="total-customers">0</div>
                    <div>Total Customers</div>
                </div>
                <div class="overview-stat">
                    <div class="overview-number" id="total-visits">0</div>
                    <div>Total Visits</div>
                </div>
                <div class="overview-stat">
                    <div class="overview-number" id="rewards-earned">0</div>
                    <div>Rewards Earned</div>
                </div>
                <div class="overview-stat">
                    <div class="overview-number" id="avg-visits">0</div>
                    <div>Avg Visits/Customer</div>
                </div>
            </div>
        </div>

        <div class="main-grid">
            <div class="card">
                <h2>👤 Register New Customer</h2>
                <form id="register-form">
                    <div class="form-group">
                        <label for="customer-name">Customer Name</label>
                        <input type="text" id="customer-name" required placeholder="Enter customer name">
                    </div>
                    <div class="form-group">
                        <label for="customer-phone">Phone Number</label>
                        <input type="tel" id="customer-phone" required placeholder="(555) 123-4567">
                    </div>
                    <button type="submit" class="btn">Register Customer</button>
                </form>
            </div>

            <div class="card">
                <h2>📱 Record Visit</h2>
                <form id="visit-form">
                    <div class="form-group">
                        <label for="visit-phone">Customer Phone</label>
                        <input type="tel" id="visit-phone" required placeholder="(555) 123-4567">
                    </div>
                    <div class="form-group">
                        <label for="visit-amount">Purchase Amount ($)</label>
                        <input type="number" id="visit-amount" step="0.01" min="0" placeholder="0.00">
                    </div>
                    <button type="submit" class="btn">Record Visit</button>
                    <button type="button" class="btn btn-secondary" onclick="findCustomer()">Find Customer</button>
                </form>
            </div>
        </div>

        <div class="card customer-list">
            <h2>👥 Customer Database</h2>
            <div class="search-bar">
                <input type="text" id="search-input" placeholder="Search by name or phone number..."
                    style="margin-bottom: 0;">
            </div>
            <div class="customer-grid" id="customer-grid">
                <!-- Customer cards will be dynamically generated here -->
            </div>
        </div>
    </div>

    <script>
        // In-memory storage for customer data
        let customers = {};
        let settings = {
            visitsForReward: 10,
            rewardAmount: 10.00
        };

        // Initialize with sample data
        function initializeSampleData() {
            const sampleCustomers = [
                { name: 'John Smith', phone: '(555) 123-4567', visits: 5, totalSpent: 125.50, rewards: 0 },
                { name: 'Sarah Johnson', phone: '(555) 987-6543', visits: 12, totalSpent: 340.75, rewards: 1 },
                { name: 'Mike Davis', phone: '(555) 456-7890', visits: 8, totalSpent: 89.25, rewards: 0 }
            ];

            sampleCustomers.forEach(customer => {
                customers[customer.phone] = {
                    name: customer.name,
                    visits: customer.visits,
                    totalSpent: customer.totalSpent,
                    rewards: customer.rewards,
                    lastVisit: new Date().toLocaleDateString(),
                    joinDate: new Date().toLocaleDateString()
                };
            });

            updateDisplay();
        }

        // Format phone number
        function formatPhone(phone) {
            const cleaned = phone.replace(/\D/g, '');
            if (cleaned.length === 10) {
                return `(${cleaned.slice(0, 3)}) ${cleaned.slice(3, 6)}-${cleaned.slice(6)}`;
            }
            return phone;
        }

        // Show message
        function showMessage(text, type = 'success') {
            const container = document.getElementById('message-container');
            const message = document.createElement('div');
            message.className = type === 'success' ? 'success-message' : 'error-message';
            message.textContent = text;
            container.appendChild(message);

            setTimeout(() => {
                container.removeChild(message);
            }, 5000);
        }

        // Register new customer
        document.getElementById('register-form').addEventListener('submit', function (e) {
            e.preventDefault();

            const name = document.getElementById('customer-name').value.trim();
            const phone = formatPhone(document.getElementById('customer-phone').value);

            if (customers[phone]) {
                showMessage('Customer with this phone number already exists!', 'error');
                return;
            }

            customers[phone] = {
                name: name,
                visits: 0,
                totalSpent: 0,
                rewards: 0,
                lastVisit: null,
                joinDate: new Date().toLocaleDateString()
            };

            showMessage(`Customer ${name} registered successfully!`);
            this.reset();
            updateDisplay();
        });

        // Record visit
        document.getElementById('visit-form').addEventListener('submit', function (e) {
            e.preventDefault();

            const phone = formatPhone(document.getElementById('visit-phone').value);
            const amount = parseFloat(document.getElementById('visit-amount').value) || 0;

            if (!customers[phone]) {
                showMessage('Customer not found! Please register first.', 'error');
                return;
            }

            const customer = customers[phone];
            customer.visits++;
            customer.totalSpent += amount;
            customer.lastVisit = new Date().toLocaleDateString();

            // Check for reward eligibility
            const visitsToReward = settings.visitsForReward - (customer.visits % settings.visitsForReward);
            if (customer.visits % settings.visitsForReward === 0) {
                customer.rewards++;
                showMessage(`🎉 ${customer.name} earned a reward! Total rewards: ${customer.rewards}`);
            } else {
                showMessage(`Visit recorded for ${customer.name}! ${visitsToReward} more visits until next reward.`);
            }

            this.reset();
            updateDisplay();
        });

        // Find customer
        function findCustomer() {
            const phone = formatPhone(document.getElementById('visit-phone').value);

            if (customers[phone]) {
                const customer = customers[phone];
                const visitsToReward = settings.visitsForReward - (customer.visits % settings.visitsForReward);
                showMessage(`Found: ${customer.name} - ${customer.visits} visits, ${visitsToReward} visits until next reward`);
            } else {
                showMessage('Customer not found!', 'error');
            }
        }

        // Redeem reward
        function redeemReward(phone) {
            const customer = customers[phone];
            if (customer.rewards > 0) {
                customer.rewards--;
                showMessage(`Reward redeemed for ${customer.name}! Remaining rewards: ${customer.rewards}`);
                updateDisplay();
            }
        }

        // Delete customer
        function deleteCustomer(phone) {
            if (confirm(`Are you sure you want to delete ${customers[phone].name}?`)) {
                delete customers[phone];
                showMessage('Customer deleted successfully!');
                updateDisplay();
            }
        }

        // Update display
        function updateDisplay() {
            const grid = document.getElementById('customer-grid');
            const searchTerm = document.getElementById('search-input').value.toLowerCase();

            // Calculate stats
            const totalCustomers = Object.keys(customers).length;
            const totalVisits = Object.values(customers).reduce((sum, c) => sum + c.visits, 0);
            const totalRewards = Object.values(customers).reduce((sum, c) => sum + c.rewards, 0);
            const avgVisits = totalCustomers > 0 ? (totalVisits / totalCustomers).toFixed(1) : 0;

            document.getElementById('total-customers').textContent = totalCustomers;
            document.getElementById('total-visits').textContent = totalVisits;
            document.getElementById('rewards-earned').textContent = totalRewards;
            document.getElementById('avg-visits').textContent = avgVisits;

            // Filter customers
            const filteredCustomers = Object.entries(customers).filter(([phone, customer]) => {
                return customer.name.toLowerCase().includes(searchTerm) ||
                    phone.toLowerCase().includes(searchTerm);
            });

            // Sort by visits (descending)
            filteredCustomers.sort((a, b) => b[1].visits - a[1].visits);

            grid.innerHTML = '';

            if (filteredCustomers.length === 0) {
                grid.innerHTML = '<p style="text-align: center; color: #666; grid-column: 1 / -1;">No customers found.</p>';
                return;
            }

            filteredCustomers.forEach(([phone, customer]) => {
                const visitsToReward = settings.visitsForReward - (customer.visits % settings.visitsForReward);
                const isEligible = customer.rewards > 0;

                const card = document.createElement('div');
                card.className = 'customer-card';
                card.innerHTML = `
                    <div class="customer-info">
                        <div>
                            <div class="customer-name">${customer.name}</div>
                            <div class="customer-phone">${phone}</div>
                        </div>
                    </div>
                    
                    <div class="visit-info">
                        <div class="stat">
                            <div class="stat-number">${customer.visits}</div>
                            <div class="stat-label">Visits</div>
                        </div>
                        <div class="stat">
                            <div class="stat-number">${customer.rewards}</div>
                            <div class="stat-label">Rewards</div>
                        </div>
                    </div>
                    
                    <div class="reward-status ${isEligible ? 'reward-eligible' : 'reward-progress'}">
                        ${isEligible ? '🎁 Reward Available!' : `⭐ ${visitsToReward} visits to reward`}
                    </div>
                    
                    <div style="font-size: 0.9em; color: #666; margin-top: 10px;">
                        <div>Total Spent: $${customer.totalSpent.toFixed(2)}</div>
                        <div>Last Visit: ${customer.lastVisit || 'Never'}</div>
                        <div>Joined: ${customer.joinDate}</div>
                    </div>
                    
                    <div class="action-buttons">
                        <button class="btn btn-small" onclick="redeemReward('${phone}')" 
                                ${customer.rewards === 0 ? 'disabled style="opacity: 0.5"' : ''}>
                            Redeem Reward
                        </button>
                        <button class="btn btn-small" onclick="deleteCustomer('${phone}')" 
                                style="background: linear-gradient(45deg, #dc3545, #c82333);">
                            Delete
                        </button>
                    </div>
                `;

                grid.appendChild(card);
            });
        }

        // Search functionality
        document.getElementById('search-input').addEventListener('input', updateDisplay);

        // Initialize the app
        initializeSampleData();
    </script>
</body>

</html>
