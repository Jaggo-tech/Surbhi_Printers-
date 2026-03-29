<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Surbhi Printers - Complete Printing Solutions</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        body {
            box-sizing: border-box;
            background: #000000;
            color: #ffffff;
            overflow-x: hidden;
            position: relative;
        }
        
        /* Sparkle Animation Background */
        .sparkle-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
            overflow: hidden;
        }
        
        .sparkle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: radial-gradient(circle, #60a5fa, #a855f7, #ec4899);
            border-radius: 50%;
            animation: sparkleFloat 8s infinite linear;
            box-shadow: 0 0 10px rgba(96, 165, 250, 0.8);
        }
        
        @keyframes sparkleFloat {
            0% {
                transform: translateY(100vh) translateX(0) scale(0);
                opacity: 0;
            }
            10% {
                opacity: 1;
                transform: translateY(90vh) translateX(10px) scale(1);
            }
            90% {
                opacity: 1;
                transform: translateY(10vh) translateX(-10px) scale(1);
            }
            100% {
                transform: translateY(-10vh) translateX(0) scale(0);
                opacity: 0;
            }
        }
        
        .sparkle:nth-child(2n) {
            animation-delay: -2s;
            background: radial-gradient(circle, #a855f7, #ec4899, #60a5fa);
        }
        
        .sparkle:nth-child(3n) {
            animation-delay: -4s;
            background: radial-gradient(circle, #ec4899, #60a5fa, #a855f7);
        }
        
        .sparkle:nth-child(4n) {
            animation-delay: -6s;
            width: 6px;
            height: 6px;
        }
        
        .sparkle:nth-child(5n) {
            animation-delay: -1s;
            width: 3px;
            height: 3px;
        }
        
        /* Flowing Dots Background */
        .dots-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }
        
        .flowing-dot {
            position: absolute;
            width: 2px;
            height: 2px;
            background: linear-gradient(45deg, #3b82f6, #8b5cf6, #ec4899);
            border-radius: 50%;
            animation: flowDots 12s infinite linear;
            opacity: 0.6;
        }
        
        @keyframes flowDots {
            0% {
                transform: translateX(-10px) translateY(100vh);
                opacity: 0;
            }
            10% {
                opacity: 0.6;
            }
            90% {
                opacity: 0.6;
            }
            100% {
                transform: translateX(100vw) translateY(-10vh);
                opacity: 0;
            }
        }
        
        .flowing-dot:nth-child(odd) {
            animation-delay: -3s;
            animation-duration: 15s;
        }
        
        .flowing-dot:nth-child(even) {
            animation-delay: -6s;
            animation-duration: 10s;
        }
        
        /* Main Content Styling */
        .main-content {
            position: relative;
            z-index: 10;
            background: rgba(0, 0, 0, 0.8);
            backdrop-filter: blur(10px);
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, #1e1b4b 0%, #581c87 50%, #7c2d12 100%);
            position: relative;
            overflow: hidden;
        }
        
        .gradient-bg::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, transparent 30%, rgba(96, 165, 250, 0.1) 50%, transparent 70%);
            animation: shimmer 3s infinite;
        }
        
        @keyframes shimmer {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }
        
        .service-card {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            background: linear-gradient(145deg, #1a1a1a, #2d2d2d);
            border: 1px solid rgba(96, 165, 250, 0.2);
            position: relative;
            overflow: hidden;
        }
        
        .service-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(96, 165, 250, 0.2), transparent);
            transition: left 0.5s;
        }
        
        .service-card:hover::before {
            left: 100%;
        }
        
        .service-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 20px 40px rgba(96, 165, 250, 0.3);
            border-color: rgba(96, 165, 250, 0.5);
        }
        
        .shine-effect {
            animation: shine 2s infinite;
        }
        
        @keyframes shine {
            0%, 100% { color: #60a5fa; text-shadow: 0 0 20px rgba(96, 165, 250, 0.5); }
            50% { color: #a855f7; text-shadow: 0 0 30px rgba(168, 85, 247, 0.8); }
        }
        
        .shine-button {
            position: relative;
            overflow: hidden;
        }
        
        .shine-button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            transition: left 0.5s;
        }
        
        .shine-button:hover::before {
            left: 100%;
        }
        
        .admin-sidebar {
            transition: transform 0.3s ease;
            background: linear-gradient(180deg, #1a1a1a, #2d2d2d);
            border-right: 1px solid rgba(96, 165, 250, 0.2);
        }
        
        @media (max-width: 768px) {
            .admin-sidebar.hidden {
                transform: translateX(-100%);
            }
        }
        
        .loading {
            display: inline-block;
            width: 20px;
            height: 20px;
            border: 3px solid rgba(96, 165, 250, 0.3);
            border-top: 3px solid #60a5fa;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .notification {
            animation: slideIn 0.3s ease-out;
            backdrop-filter: blur(10px);
        }
        
        @keyframes slideIn {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
        
        /* Black theme overrides */
        .bg-white {
            background: linear-gradient(145deg, #1a1a1a, #2d2d2d) !important;
            color: #ffffff !important;
            border: 1px solid rgba(96, 165, 250, 0.2);
        }
        
        .bg-gray-50 {
            background: #000000 !important;
        }
        
        .bg-gray-100 {
            background: linear-gradient(145deg, #1a1a1a, #2d2d2d) !important;
            color: #ffffff !important;
        }
        
        .text-gray-800, .text-gray-700, .text-gray-600 {
            color: #ffffff !important;
        }
        
        .border {
            border-color: rgba(96, 165, 250, 0.3) !important;
        }
        
        input, textarea, select {
            background: rgba(26, 26, 26, 0.8) !important;
            color: #ffffff !important;
            border: 1px solid rgba(96, 165, 250, 0.3) !important;
        }
        
        input:focus, textarea:focus, select:focus {
            border-color: #60a5fa !important;
            box-shadow: 0 0 0 3px rgba(96, 165, 250, 0.1) !important;
        }
        
        .shadow, .shadow-lg, .shadow-xl, .shadow-2xl {
            box-shadow: 0 10px 30px rgba(96, 165, 250, 0.2) !important;
        }
        
        table {
            background: rgba(26, 26, 26, 0.8) !important;
        }
        
        .border-t {
            border-color: rgba(96, 165, 250, 0.2) !important;
        }
        
        .hover\:bg-purple-50:hover {
            background: rgba(96, 165, 250, 0.1) !important;
        }
    </style>
</head>
<body class="bg-gray-50">
    <!-- Sparkle Animation Background -->
    <div class="sparkle-container" id="sparkleContainer">
        <!-- Sparkles will be generated by JavaScript -->
    </div>
    
    <!-- Flowing Dots Background -->
    <div class="dots-container" id="dotsContainer">
        <!-- Flowing dots will be generated by JavaScript -->
    </div>
    
    <!-- Main Content Wrapper -->
    <div class="main-content">
    <!-- Navigation -->
    <nav class="bg-black bg-opacity-80 backdrop-filter backdrop-blur-lg shadow-lg fixed w-full top-0 z-50 border-b border-blue-500 border-opacity-30">
        <div class="max-w-7xl mx-auto px-4">
            <div class="flex justify-between items-center py-4">
                <div class="flex items-center space-x-4">
                    <i class="fas fa-print text-3xl text-blue-400 shine-effect"></i>
                    <div>
                        <h1 class="text-2xl font-bold text-white shine-effect">Surbhi Printers</h1>
                        <p class="text-sm text-blue-300">Complete Printing Solutions</p>
                    </div>
                </div>
                <div class="hidden md:flex items-center space-x-6">
                    <a href="#home" class="nav-link text-white hover:text-blue-400 font-medium transition-colors duration-300">Home</a>
                    <a href="#services" class="nav-link text-white hover:text-blue-400 font-medium transition-colors duration-300">Services</a>
                    <a href="#contact" class="nav-link text-white hover:text-blue-400 font-medium transition-colors duration-300">Contact</a>
                    <button onclick="showAdminLogin()" class="bg-gradient-to-r from-blue-600 to-purple-600 text-white px-4 py-2 rounded-lg hover:from-blue-700 hover:to-purple-700 shine-button transition-all duration-300">Admin</button>
                </div>
                <button class="md:hidden" onclick="toggleMobileMenu()">
                    <i class="fas fa-bars text-2xl text-white"></i>
                </button>
            </div>
        </div>
        <!-- Mobile Menu -->
        <div id="mobileMenu" class="hidden md:hidden bg-black bg-opacity-90 border-t border-blue-500 border-opacity-30">
            <div class="px-4 py-2 space-y-2">
                <a href="#home" class="block py-2 text-white hover:text-blue-400">Home</a>
                <a href="#services" class="block py-2 text-white hover:text-blue-400">Services</a>
                <a href="#contact" class="block py-2 text-white hover:text-blue-400">Contact</a>
                <button onclick="showAdminLogin()" class="block w-full text-left py-2 text-blue-400 hover:text-blue-300">Admin Login</button>
            </div>
        </div>
    </nav>

    <!-- Customer Interface -->
    <div id="customerInterface">
        <!-- Hero Section -->
        <section id="home" class="gradient-bg text-white pt-32 pb-24 min-h-screen flex items-center">
            <div class="max-w-7xl mx-auto px-4 text-center relative z-10">
                <h2 class="text-7xl md:text-8xl font-bold mb-8 shine-effect">Welcome to Surbhi Printers</h2>
                <p class="text-2xl md:text-3xl mb-12 max-w-4xl mx-auto text-blue-200">Your trusted partner for all printing needs. From wedding invitations to business cards, we deliver quality printing services with care and precision.</p>
                <div class="flex flex-col md:flex-row justify-center items-center space-y-6 md:space-y-0 md:space-x-8">
                    <a href="https://api.whatsapp.com/send?phone=919993434992" target="_blank" rel="noopener noreferrer" class="bg-gradient-to-r from-green-500 to-green-600 hover:from-green-600 hover:to-green-700 text-white px-10 py-4 rounded-lg font-semibold flex items-center text-xl shine-button transition-all duration-300 transform hover:scale-105">
                        <i class="fab fa-whatsapp mr-3 text-2xl"></i> WhatsApp Us
                    </a>
                    <a href="tel:+919993434992" class="bg-gradient-to-r from-blue-500 to-blue-600 hover:from-blue-600 hover:to-blue-700 text-white px-10 py-4 rounded-lg font-semibold flex items-center text-xl shine-button transition-all duration-300 transform hover:scale-105">
                        <i class="fas fa-phone mr-3 text-2xl"></i> Call Now
                    </a>
                    <button onclick="openGoogleMaps()" class="bg-gradient-to-r from-purple-500 to-purple-600 hover:from-purple-600 hover:to-purple-700 text-white px-10 py-4 rounded-lg font-semibold flex items-center text-xl shine-button transition-all duration-300 transform hover:scale-105">
                        <i class="fas fa-map-marker-alt mr-3 text-2xl"></i> Get Directions
                    </button>
                </div>
            </div>
        </section>

        <!-- Shop Details -->
        <section class="py-16 bg-white">
            <div class="max-w-7xl mx-auto px-4">
                <div class="grid md:grid-cols-2 gap-12 items-center">
                    <div>
                        <h3 class="text-3xl font-bold text-gray-800 mb-6">About Surbhi Printers</h3>
                        <div class="space-y-4 text-gray-600">
                            <p class="flex items-center"><i class="fas fa-user text-purple-600 mr-3"></i> <strong>Owner:</strong> Sanjay Vishwakarma</p>
                            <p class="flex items-start"><i class="fas fa-map-marker-alt text-purple-600 mr-3 mt-1"></i> <span><strong>Address:</strong> Mangod Kanwan Road, near bus stop Dasai, District Dhar, Pincode 454441</span></p>
                            <p class="flex items-center"><i class="fas fa-phone text-purple-600 mr-3"></i> <strong>Contact:</strong> 9993434992, 8770065770</p>
                        </div>
                    </div>
                    <div class="bg-gray-100 p-8 rounded-lg">
                        <h4 class="text-xl font-semibold mb-4">Why Choose Us?</h4>
                        <ul class="space-y-3 text-gray-600">
                            <li class="flex items-center"><i class="fas fa-check text-green-500 mr-3"></i> High Quality Printing</li>
                            <li class="flex items-center"><i class="fas fa-check text-green-500 mr-3"></i> Fast Delivery</li>
                            <li class="flex items-center"><i class="fas fa-check text-green-500 mr-3"></i> Competitive Prices</li>
                            <li class="flex items-center"><i class="fas fa-check text-green-500 mr-3"></i> Professional Service</li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <!-- Services Section -->
        <section id="services" class="py-16 bg-gray-50">
            <div class="max-w-7xl mx-auto px-4">
                <h3 class="text-4xl font-bold text-center text-gray-800 mb-12">Our Services</h3>
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8" id="servicesContainer">
                    <!-- Services will be loaded dynamically -->
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="py-16 bg-white">
            <div class="max-w-7xl mx-auto px-4">
                <h3 class="text-4xl font-bold text-center text-gray-800 mb-12">Contact Us</h3>
                <div class="grid md:grid-cols-2 gap-12">
                    <div>
                        <h4 class="text-2xl font-semibold mb-6">Get in Touch</h4>
                        <div class="space-y-4">
                            <p class="flex items-center text-gray-600">
                                <i class="fas fa-phone text-purple-600 mr-4"></i>
                                <span>9993434992 (WhatsApp & Call)</span>
                            </p>
                            <p class="flex items-center text-gray-600">
                                <i class="fas fa-phone text-purple-600 mr-4"></i>
                                <span>8770065770</span>
                            </p>
                            <p class="flex items-start text-gray-600">
                                <i class="fas fa-map-marker-alt text-purple-600 mr-4 mt-1"></i>
                                <span>Mangod Kanwan Road, near bus stop Dasai, District Dhar, Pincode 454441</span>
                            </p>
                        </div>
                        <div class="mt-8 flex space-x-4">
                            <a href="https://wa.me/919993434992" target="_blank" class="bg-green-500 hover:bg-green-600 text-white px-6 py-3 rounded-lg">
                                <i class="fab fa-whatsapp mr-2"></i> WhatsApp
                            </a>
                            <a href="tel:+919993434992" class="bg-blue-500 hover:bg-blue-600 text-white px-6 py-3 rounded-lg">
                                <i class="fas fa-phone mr-2"></i> Call
                            </a>
                        </div>
                    </div>
                    <div>
                        <h4 class="text-2xl font-semibold mb-6">Send us a Message</h4>
                        <form onsubmit="handleContactForm(event)" class="space-y-4">
                            <div>
                                <label class="block text-gray-700 text-sm font-bold mb-2">Name</label>
                                <input type="text" id="contactName" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                            </div>
                            <div>
                                <label class="block text-gray-700 text-sm font-bold mb-2">Phone</label>
                                <input type="tel" id="contactPhone" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                            </div>
                            <div>
                                <label class="block text-gray-700 text-sm font-bold mb-2">Message</label>
                                <textarea id="contactMessage" rows="4" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required></textarea>
                            </div>
                            <button type="submit" class="w-full bg-purple-600 text-white py-2 rounded-lg hover:bg-purple-700">
                                Send Message
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- Admin Interface -->
    <div id="adminInterface" class="hidden min-h-screen bg-gray-100">
        <!-- Admin Header -->
        <header class="bg-white shadow-sm border-b">
            <div class="flex items-center justify-between px-6 py-4">
                <div class="flex items-center space-x-4">
                    <button onclick="toggleAdminSidebar()" class="md:hidden text-gray-600">
                        <i class="fas fa-bars text-xl"></i>
                    </button>
                    <h1 class="text-2xl font-bold text-gray-800">Admin Dashboard</h1>
                </div>
                <div class="flex items-center space-x-4">
                    <span class="text-gray-600">Welcome, <span id="adminName">Sanjay</span></span>
                    <button onclick="logout()" class="bg-red-500 text-white px-4 py-2 rounded hover:bg-red-600">
                        <i class="fas fa-sign-out-alt mr-2"></i> Logout
                    </button>
                </div>
            </div>
        </header>

        <div class="flex">
            <!-- Admin Sidebar -->
            <aside id="adminSidebar" class="admin-sidebar bg-white w-64 min-h-screen shadow-sm">
                <nav class="p-4">
                    <ul class="space-y-2">
                        <li><a href="#" onclick="showAdminSection('dashboard')" class="admin-nav-link flex items-center p-3 text-gray-700 rounded hover:bg-purple-50 hover:text-purple-600">
                            <i class="fas fa-chart-bar mr-3"></i> Dashboard
                        </a></li>
                        <li><a href="#" onclick="showAdminSection('orders')" class="admin-nav-link flex items-center p-3 text-gray-700 rounded hover:bg-purple-50 hover:text-purple-600">
                            <i class="fas fa-shopping-cart mr-3"></i> Orders
                        </a></li>
                        <li><a href="#" onclick="showAdminSection('services')" class="admin-nav-link flex items-center p-3 text-gray-700 rounded hover:bg-purple-50 hover:text-purple-600">
                            <i class="fas fa-cogs mr-3"></i> Services
                        </a></li>
                        <li><a href="#" onclick="showAdminSection('customers')" class="admin-nav-link flex items-center p-3 text-gray-700 rounded hover:bg-purple-50 hover:text-purple-600">
                            <i class="fas fa-users mr-3"></i> Customers
                        </a></li>
                        <li><a href="#" onclick="showAdminSection('analytics')" class="admin-nav-link flex items-center p-3 text-gray-700 rounded hover:bg-purple-50 hover:text-purple-600">
                            <i class="fas fa-chart-line mr-3"></i> Analytics
                        </a></li>
                        <li><a href="#" onclick="showAdminSection('inventory')" class="admin-nav-link flex items-center p-3 text-gray-700 rounded hover:bg-purple-50 hover:text-purple-600">
                            <i class="fas fa-boxes mr-3"></i> Inventory
                        </a></li>
                        <li><a href="#" onclick="showAdminSection('settings')" class="admin-nav-link flex items-center p-3 text-gray-700 rounded hover:bg-purple-50 hover:text-purple-600">
                            <i class="fas fa-cog mr-3"></i> Settings
                        </a></li>
                    </ul>
                </nav>
            </aside>

            <!-- Admin Content -->
            <main class="flex-1 p-6">
                <!-- Dashboard Section -->
                <div id="adminDashboard" class="admin-section">
                    <h2 class="text-3xl font-bold text-gray-800 mb-6">Dashboard Overview</h2>
                    
                    <!-- Stats Cards -->
                    <div class="grid md:grid-cols-4 gap-6 mb-8">
                        <div class="bg-white p-6 rounded-lg shadow">
                            <div class="flex items-center">
                                <div class="p-3 bg-blue-100 rounded-full">
                                    <i class="fas fa-shopping-cart text-blue-600"></i>
                                </div>
                                <div class="ml-4">
                                    <p class="text-gray-600">Total Orders</p>
                                    <p class="text-2xl font-bold" id="totalOrders">0</p>
                                </div>
                            </div>
                        </div>
                        <div class="bg-white p-6 rounded-lg shadow">
                            <div class="flex items-center">
                                <div class="p-3 bg-green-100 rounded-full">
                                    <i class="fas fa-check-circle text-green-600"></i>
                                </div>
                                <div class="ml-4">
                                    <p class="text-gray-600">Completed</p>
                                    <p class="text-2xl font-bold" id="completedOrders">0</p>
                                </div>
                            </div>
                        </div>
                        <div class="bg-white p-6 rounded-lg shadow">
                            <div class="flex items-center">
                                <div class="p-3 bg-yellow-100 rounded-full">
                                    <i class="fas fa-clock text-yellow-600"></i>
                                </div>
                                <div class="ml-4">
                                    <p class="text-gray-600">Pending</p>
                                    <p class="text-2xl font-bold" id="pendingOrders">0</p>
                                </div>
                            </div>
                        </div>
                        <div class="bg-white p-6 rounded-lg shadow">
                            <div class="flex items-center">
                                <div class="p-3 bg-purple-100 rounded-full">
                                    <i class="fas fa-rupee-sign text-purple-600"></i>
                                </div>
                                <div class="ml-4">
                                    <p class="text-gray-600">Today's Income</p>
                                    <p class="text-2xl font-bold" id="todayIncome">₹0</p>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Recent Orders -->
                    <div class="bg-white rounded-lg shadow">
                        <div class="p-6 border-b">
                            <h3 class="text-xl font-semibold">Recent Orders</h3>
                        </div>
                        <div class="p-6">
                            <div class="overflow-x-auto">
                                <table class="w-full">
                                    <thead>
                                        <tr class="text-left text-gray-600">
                                            <th class="pb-3">Customer</th>
                                            <th class="pb-3">Service</th>
                                            <th class="pb-3">Status</th>
                                            <th class="pb-3">Amount</th>
                                        </tr>
                                    </thead>
                                    <tbody id="recentOrdersTable">
                                        <!-- Recent orders will be populated here -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Orders Section -->
                <div id="adminOrders" class="admin-section hidden">
                    <div class="flex justify-between items-center mb-6">
                        <h2 class="text-3xl font-bold text-gray-800">Order Management</h2>
                        <div class="flex space-x-2">
                            <button onclick="exportOrders()" class="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700">
                                <i class="fas fa-download mr-2"></i> Export
                            </button>
                            <button onclick="showAddOrderModal()" class="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">
                                <i class="fas fa-plus mr-2"></i> Add Order
                            </button>
                        </div>
                    </div>

                    <!-- Order Filters -->
                    <div class="bg-white p-4 rounded-lg shadow mb-6">
                        <div class="grid md:grid-cols-4 gap-4">
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">Status</label>
                                <select id="statusFilter" onchange="filterOrders()" class="w-full px-3 py-2 border rounded-lg">
                                    <option value="">All Status</option>
                                    <option value="Pending">Pending</option>
                                    <option value="In Progress">In Progress</option>
                                    <option value="Completed">Completed</option>
                                    <option value="Delivered">Delivered</option>
                                </select>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">Service</label>
                                <select id="serviceFilter" onchange="filterOrders()" class="w-full px-3 py-2 border rounded-lg">
                                    <option value="">All Services</option>
                                </select>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">Date From</label>
                                <input type="date" id="dateFromFilter" onchange="filterOrders()" class="w-full px-3 py-2 border rounded-lg">
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-1">Date To</label>
                                <input type="date" id="dateToFilter" onchange="filterOrders()" class="w-full px-3 py-2 border rounded-lg">
                            </div>
                        </div>
                    </div>

                    <div class="bg-white rounded-lg shadow">
                        <div class="p-6">
                            <div class="overflow-x-auto">
                                <table class="w-full">
                                    <thead>
                                        <tr class="text-left text-gray-600 border-b">
                                            <th class="pb-3">Order ID</th>
                                            <th class="pb-3">Customer</th>
                                            <th class="pb-3">Phone</th>
                                            <th class="pb-3">Service</th>
                                            <th class="pb-3">Status</th>
                                            <th class="pb-3">Payment</th>
                                            <th class="pb-3">Amount</th>
                                            <th class="pb-3">Deadline</th>
                                            <th class="pb-3">Actions</th>
                                        </tr>
                                    </thead>
                                    <tbody id="ordersTable">
                                        <!-- Orders will be populated here -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Services Section -->
                <div id="adminServices" class="admin-section hidden">
                    <div class="flex justify-between items-center mb-6">
                        <h2 class="text-3xl font-bold text-gray-800">Service Management</h2>
                        <button onclick="showAddServiceModal()" class="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">
                            <i class="fas fa-plus mr-2"></i> Add Service
                        </button>
                    </div>

                    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6" id="servicesGrid">
                        <!-- Services will be populated here -->
                    </div>
                </div>

                <!-- Customers Section -->
                <div id="adminCustomers" class="admin-section hidden">
                    <h2 class="text-3xl font-bold text-gray-800 mb-6">Customer Management</h2>
                    
                    <div class="bg-white rounded-lg shadow">
                        <div class="p-6">
                            <div class="overflow-x-auto">
                                <table class="w-full">
                                    <thead>
                                        <tr class="text-left text-gray-600 border-b">
                                            <th class="pb-3">Name</th>
                                            <th class="pb-3">Phone</th>
                                            <th class="pb-3">Email</th>
                                            <th class="pb-3">Total Orders</th>
                                            <th class="pb-3">Total Spent</th>
                                            <th class="pb-3">Last Order</th>
                                            <th class="pb-3">Actions</th>
                                        </tr>
                                    </thead>
                                    <tbody id="customersTable">
                                        <!-- Customers will be populated here -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Analytics Section -->
                <div id="adminAnalytics" class="admin-section hidden">
                    <h2 class="text-3xl font-bold text-gray-800 mb-6">Analytics & Reports</h2>
                    
                    <div class="grid md:grid-cols-2 gap-6 mb-8">
                        <div class="bg-white p-6 rounded-lg shadow">
                            <h3 class="text-xl font-semibold mb-4">Daily Income</h3>
                            <canvas id="dailyIncomeChart" width="400" height="200"></canvas>
                        </div>
                        <div class="bg-white p-6 rounded-lg shadow">
                            <h3 class="text-xl font-semibold mb-4">Service Distribution</h3>
                            <canvas id="serviceChart" width="400" height="200"></canvas>
                        </div>
                    </div>

                    <div class="bg-white p-6 rounded-lg shadow mb-8">
                        <h3 class="text-xl font-semibold mb-4">Monthly Overview</h3>
                        <canvas id="monthlyChart" width="800" height="300"></canvas>
                    </div>

                    <!-- Performance Metrics -->
                    <div class="grid md:grid-cols-3 gap-6">
                        <div class="bg-white p-6 rounded-lg shadow">
                            <h4 class="text-lg font-semibold mb-4">Top Services</h4>
                            <div id="topServices">
                                <!-- Top services will be populated here -->
                            </div>
                        </div>
                        <div class="bg-white p-6 rounded-lg shadow">
                            <h4 class="text-lg font-semibold mb-4">Customer Insights</h4>
                            <div id="customerInsights">
                                <!-- Customer insights will be populated here -->
                            </div>
                        </div>
                        <div class="bg-white p-6 rounded-lg shadow">
                            <h4 class="text-lg font-semibold mb-4">Revenue Trends</h4>
                            <div id="revenueTrends">
                                <!-- Revenue trends will be populated here -->
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Inventory Section -->
                <div id="adminInventory" class="admin-section hidden">
                    <div class="flex justify-between items-center mb-6">
                        <h2 class="text-3xl font-bold text-gray-800">Inventory Management</h2>
                        <button onclick="showAddInventoryModal()" class="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">
                            <i class="fas fa-plus mr-2"></i> Add Item
                        </button>
                    </div>

                    <div class="grid md:grid-cols-4 gap-6 mb-8">
                        <div class="bg-white p-6 rounded-lg shadow">
                            <div class="flex items-center">
                                <div class="p-3 bg-blue-100 rounded-full">
                                    <i class="fas fa-boxes text-blue-600"></i>
                                </div>
                                <div class="ml-4">
                                    <p class="text-gray-600">Total Items</p>
                                    <p class="text-2xl font-bold" id="totalInventoryItems">0</p>
                                </div>
                            </div>
                        </div>
                        <div class="bg-white p-6 rounded-lg shadow">
                            <div class="flex items-center">
                                <div class="p-3 bg-red-100 rounded-full">
                                    <i class="fas fa-exclamation-triangle text-red-600"></i>
                                </div>
                                <div class="ml-4">
                                    <p class="text-gray-600">Low Stock</p>
                                    <p class="text-2xl font-bold" id="lowStockItems">0</p>
                                </div>
                            </div>
                        </div>
                        <div class="bg-white p-6 rounded-lg shadow">
                            <div class="flex items-center">
                                <div class="p-3 bg-green-100 rounded-full">
                                    <i class="fas fa-rupee-sign text-green-600"></i>
                                </div>
                                <div class="ml-4">
                                    <p class="text-gray-600">Inventory Value</p>
                                    <p class="text-2xl font-bold" id="inventoryValue">₹0</p>
                                </div>
                            </div>
                        </div>
                        <div class="bg-white p-6 rounded-lg shadow">
                            <div class="flex items-center">
                                <div class="p-3 bg-yellow-100 rounded-full">
                                    <i class="fas fa-chart-line text-yellow-600"></i>
                                </div>
                                <div class="ml-4">
                                    <p class="text-gray-600">Monthly Usage</p>
                                    <p class="text-2xl font-bold" id="monthlyUsage">0</p>
                                </div>
                            </div>
                        </div>
                    </div>

                    <div class="bg-white rounded-lg shadow">
                        <div class="p-6">
                            <div class="overflow-x-auto">
                                <table class="w-full">
                                    <thead>
                                        <tr class="text-left text-gray-600 border-b">
                                            <th class="pb-3">Item Name</th>
                                            <th class="pb-3">Category</th>
                                            <th class="pb-3">Current Stock</th>
                                            <th class="pb-3">Min Stock</th>
                                            <th class="pb-3">Unit Price</th>
                                            <th class="pb-3">Total Value</th>
                                            <th class="pb-3">Status</th>
                                            <th class="pb-3">Actions</th>
                                        </tr>
                                    </thead>
                                    <tbody id="inventoryTable">
                                        <!-- Inventory items will be populated here -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Settings Section -->
                <div id="adminSettings" class="admin-section hidden">
                    <h2 class="text-3xl font-bold text-gray-800 mb-6">Settings</h2>
                    
                    <div class="grid md:grid-cols-2 gap-8">
                        <!-- Business Settings -->
                        <div class="bg-white p-6 rounded-lg shadow">
                            <h3 class="text-xl font-semibold mb-4">Business Information</h3>
                            <form onsubmit="updateBusinessSettings(event)">
                                <div class="space-y-4">
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Business Name</label>
                                        <input type="text" id="businessName" value="Surbhi Printers" class="w-full px-3 py-2 border rounded-lg">
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Owner Name</label>
                                        <input type="text" id="ownerName" value="Sanjay Vishwakarma" class="w-full px-3 py-2 border rounded-lg">
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Phone Numbers</label>
                                        <input type="text" id="phoneNumbers" value="9993434992, 8770065770" class="w-full px-3 py-2 border rounded-lg">
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Address</label>
                                        <textarea id="businessAddress" rows="3" class="w-full px-3 py-2 border rounded-lg">Mangod Kanwan Road, near bus stop Dasai, District Dhar, Pincode 454441</textarea>
                                    </div>
                                    <button type="submit" class="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">
                                        Update Business Info
                                    </button>
                                </div>
                            </form>
                        </div>

                        <!-- System Settings -->
                        <div class="bg-white p-6 rounded-lg shadow">
                            <h3 class="text-xl font-semibold mb-4">System Settings</h3>
                            <div class="space-y-4">
                                <div class="flex items-center justify-between">
                                    <span class="text-gray-700">Email Notifications</span>
                                    <label class="relative inline-flex items-center cursor-pointer">
                                        <input type="checkbox" id="emailNotifications" class="sr-only peer" checked>
                                        <div class="w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-purple-300 rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-purple-600"></div>
                                    </label>
                                </div>
                                <div class="flex items-center justify-between">
                                    <span class="text-gray-700">SMS Notifications</span>
                                    <label class="relative inline-flex items-center cursor-pointer">
                                        <input type="checkbox" id="smsNotifications" class="sr-only peer" checked>
                                        <div class="w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-purple-300 rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-purple-600"></div>
                                    </label>
                                </div>
                                <div class="flex items-center justify-between">
                                    <span class="text-gray-700">Auto Backup</span>
                                    <label class="relative inline-flex items-center cursor-pointer">
                                        <input type="checkbox" id="autoBackup" class="sr-only peer" checked>
                                        <div class="w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-purple-300 rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-purple-600"></div>
                                    </label>
                                </div>
                                <div>
                                    <label class="block text-sm font-medium text-gray-700 mb-1">Currency</label>
                                    <select id="currency" class="w-full px-3 py-2 border rounded-lg">
                                        <option value="INR" selected>Indian Rupee (₹)</option>
                                        <option value="USD">US Dollar ($)</option>
                                        <option value="EUR">Euro (€)</option>
                                    </select>
                                </div>
                                <div>
                                    <label class="block text-sm font-medium text-gray-700 mb-1">Tax Rate (%)</label>
                                    <input type="number" id="taxRate" value="18" min="0" max="100" step="0.01" class="w-full px-3 py-2 border rounded-lg">
                                </div>
                                <button onclick="updateSystemSettings()" class="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">
                                    Update Settings
                                </button>
                            </div>
                        </div>
                    </div>

                    <!-- Data Management -->
                    <div class="mt-8 bg-white p-6 rounded-lg shadow">
                        <h3 class="text-xl font-semibold mb-4">Data Management</h3>
                        <div class="grid md:grid-cols-3 gap-4">
                            <button onclick="exportAllData()" class="bg-green-600 text-white px-4 py-2 rounded hover:bg-green-700">
                                <i class="fas fa-download mr-2"></i> Export All Data
                            </button>
                            <button onclick="showImportModal()" class="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700">
                                <i class="fas fa-upload mr-2"></i> Import Data
                            </button>
                            <button onclick="confirmDataReset()" class="bg-red-600 text-white px-4 py-2 rounded hover:bg-red-700">
                                <i class="fas fa-trash mr-2"></i> Reset All Data
                            </button>
                        </div>
                    </div>
                </div>
            </main>
        </div>
    </div>

    <!-- Login Modal -->
    <div id="loginModal" class="hidden fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
        <div class="bg-white p-8 rounded-lg shadow-xl max-w-md w-full mx-4">
            <h3 class="text-2xl font-bold text-gray-800 mb-6 text-center">Admin Login</h3>
            <form onsubmit="handleLogin(event)">
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Username</label>
                    <input type="text" id="username" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Password</label>
                    <input type="password" id="password" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="flex justify-between">
                    <button type="button" onclick="hideLoginModal()" class="bg-gray-500 text-white px-4 py-2 rounded hover:bg-gray-600">Cancel</button>
                    <button type="submit" class="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">
                        <span id="loginButtonText">Login</span>
                        <div id="loginSpinner" class="loading hidden ml-2"></div>
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- Add Order Modal -->
    <div id="addOrderModal" class="hidden fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
        <div class="bg-white p-8 rounded-lg shadow-xl max-w-md w-full mx-4 max-h-96 overflow-y-auto">
            <h3 class="text-2xl font-bold text-gray-800 mb-6">Add New Order</h3>
            <form onsubmit="handleAddOrder(event)">
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Customer Name</label>
                    <input type="text" id="customerName" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Phone Number</label>
                    <input type="tel" id="customerPhone" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Email (Optional)</label>
                    <input type="email" id="customerEmail" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500">
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Service Type</label>
                    <select id="serviceType" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                        <option value="">Select Service</option>
                    </select>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Quantity</label>
                    <input type="number" id="orderQuantity" min="1" value="1" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Amount</label>
                    <input type="number" id="orderAmount" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Advance Payment</label>
                    <input type="number" id="advancePayment" value="0" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500">
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Delivery Date</label>
                    <input type="date" id="deliveryDate" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Special Instructions</label>
                    <textarea id="orderInstructions" rows="3" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500"></textarea>
                </div>
                <div class="flex justify-between">
                    <button type="button" onclick="hideAddOrderModal()" class="bg-gray-500 text-white px-4 py-2 rounded hover:bg-gray-600">Cancel</button>
                    <button type="submit" class="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">Add Order</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Add Service Modal -->
    <div id="addServiceModal" class="hidden fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
        <div class="bg-white p-8 rounded-lg shadow-xl max-w-md w-full mx-4">
            <h3 class="text-2xl font-bold text-gray-800 mb-6">Add New Service</h3>
            <form onsubmit="handleAddService(event)">
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Service Name</label>
                    <input type="text" id="serviceName" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Description</label>
                    <textarea id="serviceDescription" rows="3" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required></textarea>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Base Price</label>
                    <input type="number" id="servicePrice" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Category</label>
                    <select id="serviceCategory" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                        <option value="">Select Category</option>
                        <option value="printing">Printing</option>
                        <option value="photography">Photography</option>
                        <option value="design">Design</option>
                        <option value="documentation">Documentation</option>
                    </select>
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Icon Class</label>
                    <input type="text" id="serviceIcon" placeholder="fas fa-print" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="flex justify-between">
                    <button type="button" onclick="hideAddServiceModal()" class="bg-gray-500 text-white px-4 py-2 rounded hover:bg-gray-600">Cancel</button>
                    <button type="submit" class="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">Add Service</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Add Inventory Modal -->
    <div id="addInventoryModal" class="hidden fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
        <div class="bg-white p-8 rounded-lg shadow-xl max-w-md w-full mx-4">
            <h3 class="text-2xl font-bold text-gray-800 mb-6">Add Inventory Item</h3>
            <form onsubmit="handleAddInventory(event)">
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Item Name</label>
                    <input type="text" id="inventoryName" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Category</label>
                    <select id="inventoryCategory" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                        <option value="">Select Category</option>
                        <option value="paper">Paper</option>
                        <option value="ink">Ink & Toner</option>
                        <option value="equipment">Equipment</option>
                        <option value="supplies">Supplies</option>
                    </select>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Current Stock</label>
                    <input type="number" id="inventoryStock" min="0" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Minimum Stock Level</label>
                    <input type="number" id="inventoryMinStock" min="0" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 text-sm font-bold mb-2">Unit Price</label>
                    <input type="number" id="inventoryPrice" step="0.01" class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:border-purple-500" required>
                </div>
                <div class="flex justify-between">
                    <button type="button" onclick="hideAddInventoryModal()" class="bg-gray-500 text-white px-4 py-2 rounded hover:bg-gray-600">Cancel</button>
                    <button type="submit" class="bg-purple-600 text-white px-4 py-2 rounded hover:bg-purple-700">Add Item</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Notification Container -->
    <div id="notificationContainer" class="fixed top-20 right-4 z-50 space-y-2">
        <!-- Notifications will be added here -->
    </div>

    <script>
        // Full Stack Application Logic
        class SurbhiPrintersApp {
            constructor() {
                this.apiUrl = 'https://api.surbhiprinters.com'; // Mock API URL
                this.isOnline = navigator.onLine;
                this.currentUser = null;
                this.services = [];
                this.orders = [];
                this.customers = [];
                this.inventory = [];
                this.settings = this.getDefaultSettings();
                
                this.initializeApp();
                this.setupEventListeners();
                this.loadInitialData();
            }

            getDefaultSettings() {
                return {
                    businessName: 'Surbhi Printers',
                    ownerName: 'Sanjay Vishwakarma',
                    phoneNumbers: '9993434992, 8770065770',
                    address: 'Mangod Kanwan Road, near bus stop Dasai, District Dhar, Pincode 454441',
                    currency: 'INR',
                    taxRate: 18,
                    emailNotifications: true,
                    smsNotifications: true,
                    autoBackup: true
                };
            }

            initializeApp() {
                // Initialize service worker for offline functionality
                if ('serviceWorker' in navigator) {
                    navigator.serviceWorker.register('/sw.js').catch(console.error);
                }

                // Setup offline/online detection
                window.addEventListener('online', () => {
                    this.isOnline = true;
                    this.showNotification('Connection restored', 'success');
                    this.syncOfflineData();
                });

                window.addEventListener('offline', () => {
                    this.isOnline = false;
                    this.showNotification('Working offline', 'warning');
                });
            }

            setupEventListeners() {
                // Auto-save functionality
                document.addEventListener('input', (e) => {
                    if (e.target.matches('[data-autosave]')) {
                        this.debounce(() => this.saveToLocalStorage(), 1000)();
                    }
                });

                // Keyboard shortcuts
                document.addEventListener('keydown', (e) => {
                    if (e.ctrlKey || e.metaKey) {
                        switch(e.key) {
                            case 'n':
                                e.preventDefault();
                                if (this.currentUser) showAddOrderModal();
                                break;
                            case 's':
                                e.preventDefault();
                                this.saveAllData();
                                break;
                        }
                    }
                });
            }

            async loadInitialData() {
                try {
                    // Load from localStorage first (for offline support)
                    this.loadFromLocalStorage();
                    
                    // Then try to sync with server if online
                    if (this.isOnline) {
                        await this.syncWithServer();
                    }
                    
                    this.renderServices();
                } catch (error) {
                    console.error('Error loading initial data:', error);
                    this.showNotification('Error loading data', 'error');
                }
            }

            loadFromLocalStorage() {
                const savedData = localStorage.getItem('surbhiPrintersData');
                if (savedData) {
                    const data = JSON.parse(savedData);
                    this.services = data.services || this.getDefaultServices();
                    this.orders = data.orders || [];
                    this.customers = data.customers || [];
                    this.inventory = data.inventory || this.getDefaultInventory();
                    this.settings = { ...this.settings, ...data.settings };
                } else {
                    this.services = this.getDefaultServices();
                    this.inventory = this.getDefaultInventory();
                }
            }

            saveToLocalStorage() {
                const data = {
                    services: this.services,
                    orders: this.orders,
                    customers: this.customers,
                    inventory: this.inventory,
                    settings: this.settings,
                    lastUpdated: new Date().toISOString()
                };
                localStorage.setItem('surbhiPrintersData', JSON.stringify(data));
            }

            async syncWithServer() {
                // Mock API calls - in real implementation, these would be actual HTTP requests
                try {
                    // Simulate API delay
                    await new Promise(resolve => setTimeout(resolve, 500));
                    
                    // In a real app, you would make actual API calls here
                    console.log('Syncing with server...');
                    
                    // Mock successful sync
                    this.showNotification('Data synced successfully', 'success');
                } catch (error) {
                    console.error('Sync failed:', error);
                    this.showNotification('Sync failed, working offline', 'warning');
                }
            }

            getDefaultServices() {
                return [
                    {
                        id: 'srv001',
                        name: 'Hand Patrika Printing',
                        description: 'Wedding, Shok, Maan Patrika, Grah Pravesh invitations',
                        basePrice: 500,
                        category: 'printing',
                        icon: 'fas fa-scroll',
                        color: 'purple',
                        active: true
                    },
                    {
                        id: 'srv002',
                        name: 'Photocopy Services',
                        description: 'All sizes, high quality photocopying',
                        basePrice: 2,
                        category: 'printing',
                        icon: 'fas fa-copy',
                        color: 'blue',
                        active: true
                    },
                    {
                        id: 'srv003',
                        name: 'Passport Photos',
                        description: 'Professional passport size photographs',
                        basePrice: 50,
                        category: 'photography',
                        icon: 'fas fa-camera',
                        color: 'green',
                        active: true
                    },
                    {
                        id: 'srv004',
                        name: 'Pamphlets',
                        description: 'Marketing pamphlets and flyers',
                        basePrice: 100,
                        category: 'printing',
                        icon: 'fas fa-file-alt',
                        color: 'yellow',
                        active: true
                    },
                    {
                        id: 'srv005',
                        name: 'Banner Printing',
                        description: 'Large format banner printing',
                        basePrice: 300,
                        category: 'printing',
                        icon: 'fas fa-flag',
                        color: 'red',
                        active: true
                    },
                    {
                        id: 'srv006',
                        name: 'Bill Book Making',
                        description: 'Custom bill books for businesses',
                        basePrice: 200,
                        category: 'printing',
                        icon: 'fas fa-book',
                        color: 'indigo',
                        active: true
                    },
                    {
                        id: 'srv007',
                        name: 'PAN Card Making',
                        description: 'PAN card application assistance',
                        basePrice: 150,
                        category: 'documentation',
                        icon: 'fas fa-id-card',
                        color: 'pink',
                        active: true
                    },
                    {
                        id: 'srv008',
                        name: 'Big Photo Frames',
                        description: 'Large format photo printing and framing',
                        basePrice: 800,
                        category: 'photography',
                        icon: 'fas fa-image',
                        color: 'teal',
                        active: true
                    }
                ];
            }

            getDefaultInventory() {
                return [
                    {
                        id: 'inv001',
                        name: 'A4 Paper',
                        category: 'paper',
                        currentStock: 500,
                        minStock: 100,
                        unitPrice: 0.5,
                        supplier: 'Paper Mart',
                        lastUpdated: new Date().toISOString()
                    },
                    {
                        id: 'inv002',
                        name: 'Black Ink Cartridge',
                        category: 'ink',
                        currentStock: 25,
                        minStock: 10,
                        unitPrice: 800,
                        supplier: 'Ink Solutions',
                        lastUpdated: new Date().toISOString()
                    },
                    {
                        id: 'inv003',
                        name: 'Color Ink Cartridge',
                        category: 'ink',
                        currentStock: 15,
                        minStock: 8,
                        unitPrice: 1200,
                        supplier: 'Ink Solutions',
                        lastUpdated: new Date().toISOString()
                    }
                ];
            }

            renderServices() {
                const container = document.getElementById('servicesContainer');
                if (!container) return;

                container.innerHTML = '';
                this.services.filter(service => service.active).forEach(service => {
                    const serviceCard = document.createElement('div');
                    serviceCard.className = 'service-card p-8 rounded-xl shadow-2xl';
                    serviceCard.innerHTML = `
                        <div class="text-center">
                            <i class="${service.icon} text-5xl text-blue-400 mb-6 shine-effect"></i>
                            <h4 class="text-2xl font-semibold mb-4 text-white">${service.name}</h4>
                            <p class="text-gray-300 mb-6 text-lg">${service.description}</p>
                            <p class="text-xl font-bold text-blue-400 mb-6">Starting from ₹${service.basePrice}</p>
                            <button onclick="app.orderService('${service.id}')" class="bg-gradient-to-r from-blue-600 to-purple-600 hover:from-blue-700 hover:to-purple-700 text-white px-6 py-3 rounded-lg font-semibold transition-all duration-300 shine-button">
                                Order Now
                            </button>
                        </div>
                    `;
                    container.appendChild(serviceCard);
                });
            }

            async orderService(serviceId) {
                const service = this.services.find(s => s.id === serviceId);
                if (!service) return;

                let message = `🖨️ *Surbhi Printers - Service Inquiry*\n\n`;
                message += `Hello! I would like to order: *${service.name}*\n\n`;
                message += `💰 Base Price: ₹${service.basePrice}\n`;
                message += `📋 Description: ${service.description}\n\n`;
                message += `Please provide details about:\n`;
                message += `📏 Specifications\n`;
                message += `📅 Delivery time\n`;
                message += `💳 Payment options\n\n`;
                message += `📞 Contact: ${this.settings.phoneNumbers.split(',')[0]}\n`;
                message += `📍 Location: ${this.settings.address}\n\n`;
                message += `Thank you! 🙏`;
                
                const whatsappUrl = `https://wa.me/91${this.settings.phoneNumbers.split(',')[0].trim()}?text=${encodeURIComponent(message)}`;
                
                if (confirm(`Send inquiry for ${service.name} via WhatsApp?`)) {
                    window.open(whatsappUrl, '_blank', 'noopener,noreferrer');
                    this.showNotification(`Service inquiry sent for ${service.name}`, 'success');
                    
                    // Track inquiry in analytics
                    this.trackEvent('service_inquiry', { serviceId, serviceName: service.name });
                }
            }

            async handleContactForm(event) {
                event.preventDefault();
                
                const formData = {
                    name: document.getElementById('contactName').value,
                    phone: document.getElementById('contactPhone').value,
                    message: document.getElementById('contactMessage').value,
                    timestamp: new Date().toISOString()
                };

                try {
                    // Save to local storage
                    const inquiries = JSON.parse(localStorage.getItem('customerInquiries') || '[]');
                    inquiries.push(formData);
                    localStorage.setItem('customerInquiries', JSON.stringify(inquiries));

                    // Send WhatsApp message
                    let whatsappMessage = `📞 *New Customer Inquiry*\n\n`;
                    whatsappMessage += `👤 Name: ${formData.name}\n`;
                    whatsappMessage += `📱 Phone: ${formData.phone}\n`;
                    whatsappMessage += `💬 Message: ${formData.message}\n\n`;
                    whatsappMessage += `🕒 Time: ${new Date().toLocaleString()}`;

                    const whatsappUrl = `https://wa.me/91${this.settings.phoneNumbers.split(',')[0].trim()}?text=${encodeURIComponent(whatsappMessage)}`;
                    window.open(whatsappUrl, '_blank', 'noopener,noreferrer');

                    // Reset form
                    event.target.reset();
                    this.showNotification('Message sent successfully!', 'success');
                    
                } catch (error) {
                    console.error('Error sending message:', error);
                    this.showNotification('Error sending message', 'error');
                }
            }

            showNotification(message, type = 'info', duration = 5000) {
                const container = document.getElementById('notificationContainer');
                const notification = document.createElement('div');
                
                const colors = {
                    success: 'bg-green-500',
                    error: 'bg-red-500',
                    warning: 'bg-yellow-500',
                    info: 'bg-blue-500'
                };

                const icons = {
                    success: 'fas fa-check-circle',
                    error: 'fas fa-times-circle',
                    warning: 'fas fa-exclamation-triangle',
                    info: 'fas fa-info-circle'
                };

                notification.className = `notification ${colors[type]} text-white p-4 rounded-lg shadow-lg max-w-sm`;
                notification.innerHTML = `
                    <div class="flex items-center">
                        <i class="${icons[type]} mr-2"></i>
                        <span class="flex-1">${message}</span>
                        <button onclick="this.parentElement.parentElement.remove()" class="ml-4 text-white hover:text-gray-200">
                            <i class="fas fa-times"></i>
                        </button>
                    </div>
                `;

                container.appendChild(notification);

                setTimeout(() => {
                    if (notification.parentElement) {
                        notification.remove();
                    }
                }, duration);
            }

            debounce(func, wait) {
                let timeout;
                return function executedFunction(...args) {
                    const later = () => {
                        clearTimeout(timeout);
                        func(...args);
                    };
                    clearTimeout(timeout);
                    timeout = setTimeout(later, wait);
                };
            }

            trackEvent(eventName, data) {
                // Analytics tracking
                const event = {
                    name: eventName,
                    data: data,
                    timestamp: new Date().toISOString(),
                    userAgent: navigator.userAgent
                };

                const analytics = JSON.parse(localStorage.getItem('analytics') || '[]');
                analytics.push(event);
                localStorage.setItem('analytics', JSON.stringify(analytics));
            }

            // Admin functions
            async login(username, password) {
                // Mock authentication - in real app, this would be a secure API call
                if (username === 'Sanjay2025' && password === 'Surbhi@123') {
                    this.currentUser = {
                        id: 'admin001',
                        username: 'Sanjay2025',
                        name: 'Sanjay Vishwakarma',
                        role: 'admin',
                        loginTime: new Date().toISOString()
                    };
                    
                    // Request location permission
                    this.requestLocationPermission();
                    
                    return true;
                } else {
                    throw new Error('Invalid credentials');
                }
            }

            requestLocationPermission() {
                if ("geolocation" in navigator) {
                    navigator.geolocation.getCurrentPosition(
                        (position) => {
                            console.log("Location access granted");
                            this.showNotification("Location access granted! You can now use location-based features.", "success");
                        },
                        (error) => {
                            console.log("Location access denied or failed");
                            this.showNotification("Location access is recommended for better service delivery tracking.", "warning");
                        },
                        {
                            enableHighAccuracy: true,
                            timeout: 10000,
                            maximumAge: 60000
                        }
                    );
                } else {
                    this.showNotification("Geolocation is not supported by this browser.", "error");
                }
            }

            logout() {
                this.currentUser = null;
                this.showNotification('Logged out successfully', 'success');
            }

            // Data management functions
            exportAllData() {
                const data = {
                    services: this.services,
                    orders: this.orders,
                    customers: this.customers,
                    inventory: this.inventory,
                    settings: this.settings,
                    exportDate: new Date().toISOString(),
                    version: '1.0'
                };

                const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
                const url = URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.href = url;
                a.download = `surbhi-printers-data-${new Date().toISOString().split('T')[0]}.json`;
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                URL.revokeObjectURL(url);

                this.showNotification('Data exported successfully', 'success');
            }

            async saveAllData() {
                try {
                    this.saveToLocalStorage();
                    if (this.isOnline) {
                        await this.syncWithServer();
                    }
                    this.showNotification('Data saved successfully', 'success');
                } catch (error) {
                    console.error('Error saving data:', error);
                    this.showNotification('Error saving data', 'error');
                }
            }
        }

        // Initialize the application
        const app = new SurbhiPrintersApp();

        // Global functions for HTML event handlers
        function toggleMobileMenu() {
            const menu = document.getElementById('mobileMenu');
            menu.classList.toggle('hidden');
        }

        function showAdminLogin() {
            document.getElementById('loginModal').classList.remove('hidden');
        }

        function hideLoginModal() {
            document.getElementById('loginModal').classList.add('hidden');
        }

        async function handleLogin(event) {
            event.preventDefault();
            
            const loginButton = document.getElementById('loginButtonText');
            const loginSpinner = document.getElementById('loginSpinner');
            
            loginButton.textContent = 'Logging in...';
            loginSpinner.classList.remove('hidden');
            
            try {
                const username = document.getElementById('username').value;
                const password = document.getElementById('password').value;
                
                await app.login(username, password);
                
                hideLoginModal();
                document.getElementById('customerInterface').classList.add('hidden');
                document.getElementById('adminInterface').classList.remove('hidden');
                
                // Initialize admin dashboard
                showAdminSection('dashboard');
                initializeCharts();
                
                app.showNotification('Login successful', 'success');
                
            } catch (error) {
                app.showNotification('Invalid credentials! Please check your username and password.', 'error');
            } finally {
                loginButton.textContent = 'Login';
                loginSpinner.classList.add('hidden');
            }
        }

        function logout() {
            app.logout();
            document.getElementById('adminInterface').classList.add('hidden');
            document.getElementById('customerInterface').classList.remove('hidden');
        }

        function showAdminSection(section) {
            // Hide all sections
            document.querySelectorAll('.admin-section').forEach(el => el.classList.add('hidden'));
            
            // Show selected section
            const sectionElement = document.getElementById('admin' + section.charAt(0).toUpperCase() + section.slice(1));
            if (sectionElement) {
                sectionElement.classList.remove('hidden');
            }
            
            // Update navigation
            document.querySelectorAll('.admin-nav-link').forEach(el => {
                el.classList.remove('bg-purple-50', 'text-purple-600');
                el.classList.add('text-gray-700');
            });
            
            // Load section-specific data
            switch(section) {
                case 'dashboard':
                    updateDashboardStats();
                    break;
                case 'orders':
                    loadOrders();
                    break;
                case 'services':
                    loadAdminServices();
                    break;
                case 'customers':
                    loadCustomers();
                    break;
                case 'inventory':
                    loadInventory();
                    break;
                case 'analytics':
                    loadAnalytics();
                    break;
            }
        }

        function updateDashboardStats() {
            const totalOrders = app.orders.length;
            const completedOrders = app.orders.filter(o => o.status === 'Completed' || o.status === 'Delivered').length;
            const pendingOrders = app.orders.filter(o => o.status === 'Pending' || o.status === 'In Progress').length;
            const todayIncome = app.orders
                .filter(o => o.orderDate === new Date().toISOString().split('T')[0] && o.payment === 'Paid')
                .reduce((sum, o) => sum + o.amount, 0);

            document.getElementById('totalOrders').textContent = totalOrders;
            document.getElementById('completedOrders').textContent = completedOrders;
            document.getElementById('pendingOrders').textContent = pendingOrders;
            document.getElementById('todayIncome').textContent = `₹${todayIncome}`;

            loadRecentOrders();
        }

        function loadRecentOrders() {
            const tbody = document.getElementById('recentOrdersTable');
            if (!tbody) return;
            
            tbody.innerHTML = '';
            
            const recentOrders = app.orders.slice(-5).reverse();
            recentOrders.forEach(order => {
                const row = document.createElement('tr');
                row.className = 'border-t';
                const statusClass = order.status === 'Completed' || order.status === 'Delivered' 
                    ? 'bg-green-100 text-green-800' 
                    : order.status === 'Pending' 
                    ? 'bg-yellow-100 text-yellow-800' 
                    : 'bg-blue-100 text-blue-800';
                
                row.innerHTML = `
                    <td class="py-3">${order.customerName}</td>
                    <td class="py-3">${order.service}</td>
                    <td class="py-3"><span class="${statusClass} px-2 py-1 rounded text-sm">${order.status}</span></td>
                    <td class="py-3">₹${order.amount}</td>
                `;
                tbody.appendChild(row);
            });
        }

        function loadOrders() {
            const tbody = document.getElementById('ordersTable');
            if (!tbody) return;
            
            tbody.innerHTML = '';
            
            app.orders.forEach(order => {
                const row = document.createElement('tr');
                row.className = 'border-t';
                row.innerHTML = `
                    <td class="py-3">${order.id}</td>
                    <td class="py-3">${order.customerName}</td>
                    <td class="py-3">${order.phone}</td>
                    <td class="py-3">${order.service}</td>
                    <td class="py-3">
                        <select onchange="updateOrderStatus('${order.id}', this.value)" class="px-2 py-1 rounded text-sm ${order.status === 'Completed' ? 'bg-green-100 text-green-800' : order.status === 'Pending' ? 'bg-yellow-100 text-yellow-800' : 'bg-blue-100 text-blue-800'}">
                            <option value="Pending" ${order.status === 'Pending' ? 'selected' : ''}>Pending</option>
                            <option value="In Progress" ${order.status === 'In Progress' ? 'selected' : ''}>In Progress</option>
                            <option value="Completed" ${order.status === 'Completed' ? 'selected' : ''}>Completed</option>
                            <option value="Delivered" ${order.status === 'Delivered' ? 'selected' : ''}>Delivered</option>
                        </select>
                    </td>
                    <td class="py-3">
                        <select onchange="updatePaymentStatus('${order.id}', this.value)" class="px-2 py-1 rounded text-sm ${order.payment === 'Paid' ? 'bg-green-100 text-green-800' : 'bg-red-100 text-red-800'}">
                            <option value="Pending" ${order.payment === 'Pending' ? 'selected' : ''}>Pending</option>
                            <option value="Paid" ${order.payment === 'Paid' ? 'selected' : ''}>Paid</option>
                        </select>
                    </td>
                    <td class="py-3">₹${order.amount}</td>
                    <td class="py-3">${order.deliveryDate}</td>
                    <td class="py-3">
                        <button onclick="sendWhatsAppUpdate('${order.phone}', '${order.customerName}', '${order.service}')" class="bg-green-500 text-white px-2 py-1 rounded text-sm hover:bg-green-600 mr-2">
                            <i class="fab fa-whatsapp"></i>
                        </button>
                        <button onclick="deleteOrder('${order.id}')" class="bg-red-500 text-white px-2 py-1 rounded text-sm hover:bg-red-600">
                            <i class="fas fa-trash"></i>
                        </button>
                    </td>
                `;
                tbody.appendChild(row);
            });

            // Populate service filter
            const serviceFilter = document.getElementById('serviceFilter');
            if (serviceFilter) {
                const services = [...new Set(app.orders.map(o => o.service))];
                serviceFilter.innerHTML = '<option value="">All Services</option>';
                services.forEach(service => {
                    const option = document.createElement('option');
                    option.value = service;
                    option.textContent = service;
                    serviceFilter.appendChild(option);
                });
            }
        }

        function loadAdminServices() {
            const servicesGrid = document.getElementById('servicesGrid');
            if (!servicesGrid) return;

            servicesGrid.innerHTML = '';
            app.services.forEach(service => {
                const serviceCard = document.createElement('div');
                serviceCard.className = 'bg-white p-6 rounded-lg shadow';
                serviceCard.innerHTML = `
                    <div class="text-center">
                        <i class="${service.icon} text-4xl text-${service.color}-600 mb-4"></i>
                        <h4 class="text-xl font-semibold mb-3">${service.name}</h4>
                        <p class="text-gray-600 mb-2">${service.description}</p>
                        <p class="text-lg font-bold text-${service.color}-600 mb-4">₹${service.basePrice}</p>
                        <div class="flex justify-center space-x-2">
                            <button onclick="editService('${service.id}')" class="bg-${service.color}-600 text-white px-3 py-1 rounded text-sm hover:bg-${service.color}-700">Edit</button>
                            <button onclick="toggleServiceStatus('${service.id}')" class="bg-${service.active ? 'yellow' : 'green'}-500 text-white px-3 py-1 rounded text-sm hover:bg-${service.active ? 'yellow' : 'green'}-600">
                                ${service.active ? 'Disable' : 'Enable'}
                            </button>
                        </div>
                    </div>
                `;
                servicesGrid.appendChild(serviceCard);
            });
        }

        function loadCustomers() {
            const tbody = document.getElementById('customersTable');
            if (!tbody) return;
            
            tbody.innerHTML = '';
            
            app.customers.forEach(customer => {
                const row = document.createElement('tr');
                row.className = 'border-t';
                row.innerHTML = `
                    <td class="py-3">${customer.name}</td>
                    <td class="py-3">${customer.phone}</td>
                    <td class="py-3">${customer.email || 'N/A'}</td>
                    <td class="py-3">${customer.totalOrders}</td>
                    <td class="py-3">₹${customer.totalSpent}</td>
                    <td class="py-3">${customer.lastOrder || 'N/A'}</td>
                    <td class="py-3">
                        <button onclick="sendWhatsAppUpdate('${customer.phone}', '${customer.name}', 'general update')" class="bg-green-500 text-white px-2 py-1 rounded text-sm hover:bg-green-600">
                            <i class="fab fa-whatsapp"></i>
                        </button>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function loadInventory() {
            const tbody = document.getElementById('inventoryTable');
            if (!tbody) return;
            
            tbody.innerHTML = '';
            
            let totalItems = 0;
            let lowStockItems = 0;
            let totalValue = 0;

            app.inventory.forEach(item => {
                totalItems++;
                if (item.currentStock <= item.minStock) lowStockItems++;
                totalValue += item.currentStock * item.unitPrice;

                const row = document.createElement('tr');
                row.className = 'border-t';
                const stockStatus = item.currentStock <= item.minStock ? 'Low Stock' : 'In Stock';
                const statusClass = item.currentStock <= item.minStock ? 'bg-red-100 text-red-800' : 'bg-green-100 text-green-800';
                
                row.innerHTML = `
                    <td class="py-3">${item.name}</td>
                    <td class="py-3 capitalize">${item.category}</td>
                    <td class="py-3">${item.currentStock}</td>
                    <td class="py-3">${item.minStock}</td>
                    <td class="py-3">₹${item.unitPrice}</td>
                    <td class="py-3">₹${(item.currentStock * item.unitPrice).toFixed(2)}</td>
                    <td class="py-3"><span class="${statusClass} px-2 py-1 rounded text-sm">${stockStatus}</span></td>
                    <td class="py-3">
                        <button onclick="updateStock('${item.id}')" class="bg-blue-500 text-white px-2 py-1 rounded text-sm hover:bg-blue-600 mr-2">
                            Update
                        </button>
                        <button onclick="deleteInventoryItem('${item.id}')" class="bg-red-500 text-white px-2 py-1 rounded text-sm hover:bg-red-600">
                            Delete
                        </button>
                    </td>
                `;
                tbody.appendChild(row);
            });

            // Update inventory stats
            document.getElementById('totalInventoryItems').textContent = totalItems;
            document.getElementById('lowStockItems').textContent = lowStockItems;
            document.getElementById('inventoryValue').textContent = `₹${totalValue.toFixed(2)}`;
        }

        function initializeCharts() {
            // Daily Income Chart
            const dailyCtx = document.getElementById('dailyIncomeChart');
            if (dailyCtx) {
                new Chart(dailyCtx.getContext('2d'), {
                    type: 'line',
                    data: {
                        labels: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
                        datasets: [{
                            label: 'Daily Income (₹)',
                            data: [1200, 1900, 800, 1500, 2000, 2450, 1800],
                            borderColor: 'rgb(147, 51, 234)',
                            backgroundColor: 'rgba(147, 51, 234, 0.1)',
                            tension: 0.4
                        }]
                    },
                    options: {
                        responsive: true,
                        scales: {
                            y: {
                                beginAtZero: true
                            }
                        }
                    }
                });
            }

            // Service Distribution Chart
            const serviceCtx = document.getElementById('serviceChart');
            if (serviceCtx) {
                new Chart(serviceCtx.getContext('2d'), {
                    type: 'doughnut',
                    data: {
                        labels: ['Patrika', 'Photocopy', 'Passport', 'Banner', 'Others'],
                        datasets: [{
                            data: [30, 25, 20, 15, 10],
                            backgroundColor: [
                                'rgb(147, 51, 234)',
                                'rgb(59, 130, 246)',
                                'rgb(16, 185, 129)',
                                'rgb(245, 158, 11)',
                                'rgb(239, 68, 68)'
                            ]
                        }]
                    },
                    options: {
                        responsive: true
                    }
                });
            }

            // Monthly Overview Chart
            const monthlyCtx = document.getElementById('monthlyChart');
            if (monthlyCtx) {
                new Chart(monthlyCtx.getContext('2d'), {
                    type: 'bar',
                    data: {
                        labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
                        datasets: [{
                            label: 'Monthly Income (₹)',
                            data: [25000, 32000, 28000, 35000, 42000, 38000],
                            backgroundColor: 'rgba(147, 51, 234, 0.8)',
                            borderColor: 'rgb(147, 51, 234)',
                            borderWidth: 1
                        }]
                    },
                    options: {
                        responsive: true,
                        scales: {
                            y: {
                                beginAtZero: true
                            }
                        }
                    }
                });
            }
        }

        // Modal functions
        function showAddOrderModal() {
            // Populate service dropdown
            const serviceSelect = document.getElementById('serviceType');
            serviceSelect.innerHTML = '<option value="">Select Service</option>';
            app.services.filter(s => s.active).forEach(service => {
                const option = document.createElement('option');
                option.value = service.id;
                option.textContent = service.name;
                serviceSelect.appendChild(option);
            });

            document.getElementById('addOrderModal').classList.remove('hidden');
        }

        function hideAddOrderModal() {
            document.getElementById('addOrderModal').classList.add('hidden');
        }

        function showAddServiceModal() {
            document.getElementById('addServiceModal').classList.remove('hidden');
        }

        function hideAddServiceModal() {
            document.getElementById('addServiceModal').classList.add('hidden');
        }

        function showAddInventoryModal() {
            document.getElementById('addInventoryModal').classList.remove('hidden');
        }

        function hideAddInventoryModal() {
            document.getElementById('addInventoryModal').classList.add('hidden');
        }

        // Form handlers
        function handleAddOrder(event) {
            event.preventDefault();
            
            const serviceId = document.getElementById('serviceType').value;
            const service = app.services.find(s => s.id === serviceId);
            
            const newOrder = {
                id: 'ORD' + String(app.orders.length + 1).padStart(3, '0'),
                customerName: document.getElementById('customerName').value,
                phone: document.getElementById('customerPhone').value,
                email: document.getElementById('customerEmail').value,
                service: service.name,
                serviceId: serviceId,
                quantity: parseInt(document.getElementById('orderQuantity').value),
                status: 'Pending',
                payment: 'Pending',
                amount: parseInt(document.getElementById('orderAmount').value),
                advancePayment: parseInt(document.getElementById('advancePayment').value) || 0,
                orderDate: new Date().toISOString().split('T')[0],
                deliveryDate: document.getElementById('deliveryDate').value,
                instructions: document.getElementById('orderInstructions').value
            };
            
            app.orders.push(newOrder);
            
            // Update or add customer
            let customer = app.customers.find(c => c.phone === newOrder.phone);
            if (customer) {
                customer.totalOrders++;
                customer.totalSpent += newOrder.amount;
                customer.lastOrder = newOrder.orderDate;
            } else {
                app.customers.push({
                    id: 'CUST' + String(app.customers.length + 1).padStart(3, '0'),
                    name: newOrder.customerName,
                    phone: newOrder.phone,
                    email: newOrder.email,
                    totalOrders: 1,
                    totalSpent: newOrder.amount,
                    lastOrder: newOrder.orderDate,
                    joinDate: newOrder.orderDate
                });
            }
            
            app.saveToLocalStorage();
            loadOrders();
            updateDashboardStats();
            hideAddOrderModal();
            
            app.showNotification('Order added successfully', 'success');
            event.target.reset();
        }

        function handleAddService(event) {
            event.preventDefault();
            
            const colors = ['purple', 'blue', 'green', 'yellow', 'red', 'indigo', 'pink', 'teal'];
            const randomColor = colors[Math.floor(Math.random() * colors.length)];
            
            const newService = {
                id: 'srv' + String(app.services.length + 1).padStart(3, '0'),
                name: document.getElementById('serviceName').value,
                description: document.getElementById('serviceDescription').value,
                basePrice: parseInt(document.getElementById('servicePrice').value),
                category: document.getElementById('serviceCategory').value,
                icon: document.getElementById('serviceIcon').value,
                color: randomColor,
                active: true
            };
            
            app.services.push(newService);
            app.saveToLocalStorage();
            app.renderServices();
            loadAdminServices();
            hideAddServiceModal();
            
            app.showNotification('Service added successfully', 'success');
            event.target.reset();
        }

        function handleAddInventory(event) {
            event.preventDefault();
            
            const newItem = {
                id: 'inv' + String(app.inventory.length + 1).padStart(3, '0'),
                name: document.getElementById('inventoryName').value,
                category: document.getElementById('inventoryCategory').value,
                currentStock: parseInt(document.getElementById('inventoryStock').value),
                minStock: parseInt(document.getElementById('inventoryMinStock').value),
                unitPrice: parseFloat(document.getElementById('inventoryPrice').value),
                supplier: '',
                lastUpdated: new Date().toISOString()
            };
            
            app.inventory.push(newItem);
            app.saveToLocalStorage();
            loadInventory();
            hideAddInventoryModal();
            
            app.showNotification('Inventory item added successfully', 'success');
            event.target.reset();
        }

        function handleContactForm(event) {
            app.handleContactForm(event);
        }

        // Utility functions
        function updateOrderStatus(orderId, status) {
            const order = app.orders.find(o => o.id === orderId);
            if (order) {
                const oldStatus = order.status;
                order.status = status;
                app.saveToLocalStorage();
                loadOrders();
                updateDashboardStats();
                
                app.showNotification(`Order ${orderId} status updated from ${oldStatus} to ${status}`, "success");
                
                if (status === 'Completed' || status === 'Delivered') {
                    if (confirm(`Send WhatsApp notification to ${order.customerName} about order completion?`)) {
                        sendWhatsAppUpdate(order.phone, order.customerName, order.service);
                    }
                }
            }
        }

        function updatePaymentStatus(orderId, payment) {
            const order = app.orders.find(o => o.id === orderId);
            if (order) {
                const oldPayment = order.payment;
                order.payment = payment;
                app.saveToLocalStorage();
                loadOrders();
                updateDashboardStats();
                
                app.showNotification(`Order ${orderId} payment updated from ${oldPayment} to ${payment}`, "success");
            }
        }

        function sendWhatsAppUpdate(phone, customerName, service) {
            const order = app.orders.find(o => o.phone === phone && o.customerName === customerName && o.service === service);
            let message = `Hello ${customerName}!\n\n`;
            
            if (order) {
                message += `📋 Order Update for: ${service}\n`;
                message += `📊 Status: ${order.status}\n`;
                message += `💰 Amount: ₹${order.amount}\n`;
                message += `📅 Delivery Date: ${order.deliveryDate}\n`;
                message += `💳 Payment: ${order.payment}\n\n`;
                
                if (order.status === 'Completed') {
                    message += `✅ Great news! Your order is ready for pickup.\n`;
                } else if (order.status === 'In Progress') {
                    message += `🔄 Your order is currently being processed.\n`;
                } else if (order.status === 'Pending') {
                    message += `⏳ Your order is in queue and will be processed soon.\n`;
                }
                
                message += `\n📞 Contact us: ${app.settings.phoneNumbers.split(',')[0]}\n`;
                message += `📍 ${app.settings.businessName}, ${app.settings.address}\n\n`;
                message += `Thank you for choosing ${app.settings.businessName}! 🙏`;
            } else {
                message += `Your order for ${service} has been updated. Please contact us for more details.\n\n`;
                message += `📞 Call: ${app.settings.phoneNumbers.split(',')[0]}\n`;
                message += `📍 ${app.settings.businessName}, ${app.settings.address}`;
            }
            
            const cleanPhone = phone.replace(/[^\d+]/g, '');
            const whatsappUrl = `https://wa.me/${cleanPhone.startsWith('+') ? cleanPhone.slice(1) : '91' + cleanPhone}?text=${encodeURIComponent(message)}`;
            
            if (confirm(`Send WhatsApp message to ${customerName} (${phone})?`)) {
                window.open(whatsappUrl, '_blank', 'noopener,noreferrer');
                app.showNotification(`WhatsApp message sent to ${customerName}`, "success");
            }
        }

        function deleteOrder(orderId) {
            if (confirm('Are you sure you want to delete this order?')) {
                app.orders = app.orders.filter(o => o.id !== orderId);
                app.saveToLocalStorage();
                loadOrders();
                updateDashboardStats();
                app.showNotification('Order deleted successfully', 'success');
            }
        }

        function filterOrders() {
            // Implementation for order filtering
            const statusFilter = document.getElementById('statusFilter').value;
            const serviceFilter = document.getElementById('serviceFilter').value;
            const dateFromFilter = document.getElementById('dateFromFilter').value;
            const dateToFilter = document.getElementById('dateToFilter').value;

            let filteredOrders = app.orders;

            if (statusFilter) {
                filteredOrders = filteredOrders.filter(o => o.status === statusFilter);
            }
            if (serviceFilter) {
                filteredOrders = filteredOrders.filter(o => o.service === serviceFilter);
            }
            if (dateFromFilter) {
                filteredOrders = filteredOrders.filter(o => o.orderDate >= dateFromFilter);
            }
            if (dateToFilter) {
                filteredOrders = filteredOrders.filter(o => o.orderDate <= dateToFilter);
            }

            // Re-render filtered orders
            const tbody = document.getElementById('ordersTable');
            tbody.innerHTML = '';
            
            filteredOrders.forEach(order => {
                const row = document.createElement('tr');
                row.className = 'border-t';
                row.innerHTML = `
                    <td class="py-3">${order.id}</td>
                    <td class="py-3">${order.customerName}</td>
                    <td class="py-3">${order.phone}</td>
                    <td class="py-3">${order.service}</td>
                    <td class="py-3">
                        <select onchange="updateOrderStatus('${order.id}', this.value)" class="px-2 py-1 rounded text-sm ${order.status === 'Completed' ? 'bg-green-100 text-green-800' : order.status === 'Pending' ? 'bg-yellow-100 text-yellow-800' : 'bg-blue-100 text-blue-800'}">
                            <option value="Pending" ${order.status === 'Pending' ? 'selected' : ''}>Pending</option>
                            <option value="In Progress" ${order.status === 'In Progress' ? 'selected' : ''}>In Progress</option>
                            <option value="Completed" ${order.status === 'Completed' ? 'selected' : ''}>Completed</option>
                            <option value="Delivered" ${order.status === 'Delivered' ? 'selected' : ''}>Delivered</option>
                        </select>
                    </td>
                    <td class="py-3">
                        <select onchange="updatePaymentStatus('${order.id}', this.value)" class="px-2 py-1 rounded text-sm ${order.payment === 'Paid' ? 'bg-green-100 text-green-800' : 'bg-red-100 text-red-800'}">
                            <option value="Pending" ${order.payment === 'Pending' ? 'selected' : ''}>Pending</option>
                            <option value="Paid" ${order.payment === 'Paid' ? 'selected' : ''}>Paid</option>
                        </select>
                    </td>
                    <td class="py-3">₹${order.amount}</td>
                    <td class="py-3">${order.deliveryDate}</td>
                    <td class="py-3">
                        <button onclick="sendWhatsAppUpdate('${order.phone}', '${order.customerName}', '${order.service}')" class="bg-green-500 text-white px-2 py-1 rounded text-sm hover:bg-green-600 mr-2">
                            <i class="fab fa-whatsapp"></i>
                        </button>
                        <button onclick="deleteOrder('${order.id}')" class="bg-red-500 text-white px-2 py-1 rounded text-sm hover:bg-red-600">
                            <i class="fas fa-trash"></i>
                        </button>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function exportOrders() {
            const orders = app.orders;
            const csv = [
                ['Order ID', 'Customer Name', 'Phone', 'Service', 'Status', 'Payment', 'Amount', 'Order Date', 'Delivery Date'],
                ...orders.map(order => [
                    order.id,
                    order.customerName,
                    order.phone,
                    order.service,
                    order.status,
                    order.payment,
                    order.amount,
                    order.orderDate,
                    order.deliveryDate
                ])
            ].map(row => row.join(',')).join('\n');

            const blob = new Blob([csv], { type: 'text/csv' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `orders-${new Date().toISOString().split('T')[0]}.csv`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);

            app.showNotification('Orders exported successfully', 'success');
        }

        function toggleAdminSidebar() {
            const sidebar = document.getElementById('adminSidebar');
            sidebar.classList.toggle('hidden');
        }

        function openGoogleMaps() {
            const address = app.settings.address;
            const businessName = app.settings.businessName;
            
            if ("geolocation" in navigator) {
                navigator.geolocation.getCurrentPosition(
                    function(position) {
                        const userLat = position.coords.latitude;
                        const userLng = position.coords.longitude;
                        const directionsUrl = `https://api.googlemaps.com/maps/dir/${userLat},${userLng}/${encodeURIComponent(businessName + ', ' + address)}`;
                        window.open(directionsUrl, '_blank', 'noopener,noreferrer');
                        app.showNotification("Opening directions to " + businessName, "success");
                    },
                    function(error) {
                        const mapsUrl = `https://api.googlemaps.com/maps/search/?api=1&query=${encodeURIComponent(businessName + ', ' + address)}`;
                        window.open(mapsUrl, '_blank', 'noopener,noreferrer');
                        app.showNotification("Opening location in Google Maps", "success");
                    }
                );
            } else {
                const mapsUrl = `https://api.googlemaps.com/maps/search/?api=1&query=${encodeURIComponent(businessName + ', ' + address)}`;
                window.open(mapsUrl, '_blank', 'noopener,noreferrer');
                app.showNotification("Opening location in Google Maps", "success");
            }
        }

        // Sparkle and Dot Animation Functions
        function createSparkles() {
            const sparkleContainer = document.getElementById('sparkleContainer');
            const numberOfSparkles = 50;
            
            for (let i = 0; i < numberOfSparkles; i++) {
                const sparkle = document.createElement('div');
                sparkle.className = 'sparkle';
                sparkle.style.left = Math.random() * 100 + '%';
                sparkle.style.animationDelay = Math.random() * 8 + 's';
                sparkle.style.animationDuration = (Math.random() * 4 + 6) + 's';
                sparkleContainer.appendChild(sparkle);
            }
        }

        function createFlowingDots() {
            const dotsContainer = document.getElementById('dotsContainer');
            const numberOfDots = 100;
            
            for (let i = 0; i < numberOfDots; i++) {
                const dot = document.createElement('div');
                dot.className = 'flowing-dot';
                dot.style.top = Math.random() * 100 + '%';
                dot.style.animationDelay = Math.random() * 12 + 's';
                dot.style.animationDuration = (Math.random() * 8 + 10) + 's';
                dotsContainer.appendChild(dot);
            }
        }

        // Initialize animations when page loads
        document.addEventListener('DOMContentLoaded', function() {
            createSparkles();
            createFlowingDots();
            
            // Regenerate sparkles periodically for continuous effect
            setInterval(function() {
                const sparkleContainer = document.getElementById('sparkleContainer');
                sparkleContainer.innerHTML = '';
                createSparkles();
            }, 30000);
            
            // Regenerate dots periodically
            setInterval(function() {
                const dotsContainer = document.getElementById('dotsContainer');
                dotsContainer.innerHTML = '';
                createFlowingDots();
            }, 45000);
        });

        // Initialize minimum date for delivery date input
        document.addEventListener('DOMContentLoaded', function() {
            const today = new Date().toISOString().split('T')[0];
            const deliveryDateInput = document.getElementById('deliveryDate');
            if (deliveryDateInput) {
                deliveryDateInput.setAttribute('min', today);
            }
        });

        // Smooth scrolling for navigation links
        document.querySelectorAll('.nav-link').forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.getAttribute('href').substring(1);
                const targetElement = document.getElementById(targetId);
                if (targetElement) {
                    targetElement.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
    </script>
    </div> <!-- Close main-content wrapper -->
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'984c8e34d1997fa7',t:'MTc1ODgyNDYzNi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
