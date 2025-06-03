<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Nysa Lister</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/flatpickr/dist/flatpickr.min.css">
    <style>
:root { 
    --primary-color: #FFD700; 
    --secondary-color: #FDB931; 
    --background-dark: #1a1a1f; 
    --text-light: #ffffff; 
    --text-dark: #000000; 
    --accent-gradient: linear-gradient(135deg, var(--primary-color), var(--secondary-color)); 
    --error-color: #ff4444; 
    --success-color: #00C851; 
    --info-color: #33b5e5;
    --warning-color: #ffbb33;
    --border-radius: 8px;
    --box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
    --transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
}

* { 
    box-sizing: border-box; 
    margin: 0; 
    padding: 0; 
}

body { 
    font-family: 'Poppins', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif; 
    background-color: var(--background-dark); 
    color: var(--text-light); 
    line-height: 1.6; 
    overflow-x: hidden; 
    -webkit-font-smoothing: antialiased;
}

.header { 
    padding: 8px 16px; 
    background: rgba(26, 26, 31, 0.95); 
    position: fixed; 
    width: 100%; 
    top: 0; 
    left: 0; 
    z-index: 1000; 
    border-bottom: 2px solid var(--primary-color); 
    backdrop-filter: blur(10px); 
    height: 60px; 
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo { 
    font-size: 1.8em; 
    font-weight: 900; 
    background: var(--accent-gradient); 
    -webkit-background-clip: text; 
    color: transparent; 
    letter-spacing: 1.2px; 
    display: flex;
    align-items: center;
    gap: 8px;
}

.logo-icon {
    font-size: 1.2em;
}

.menu-button { 
    padding: 10px 20px; 
    background: var(--accent-gradient); 
    border: none; 
    border-radius: 50px; 
    color: var(--text-dark); 
    font-weight: 600; 
    cursor: pointer; 
    transition: var(--transition); 
    font-size: 0.95em; 
    display: flex;
    align-items: center;
    gap: 8px;
}

.menu-button:hover {
    transform: translateY(-2px);
    box-shadow: var(--box-shadow);
}

.main-container {
    margin-top: 40px;
    padding: 20px;
    max-width: 1200px;
    margin-left: auto;
    margin-right: auto;
}

.page-title {
    text-align: center; 
    margin-top: 0; 
    margin-bottom: 40px; 
    color: var(--primary-color);
    font-weight: 700;
    font-size: 2rem;
    position: relative;
    padding-bottom: 15px;
}

.page-title::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 100px;
    height: 3px;
    background: var(--accent-gradient);
    border-radius: 3px;
}

.listing-types {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 25px;
    margin-bottom: 40px;
}

.listing-card {
    background: rgba(255, 255, 255, 0.05);
    border-radius: var(--border-radius);
    padding: 25px;
    transition: var(--transition);
    cursor: pointer;
    border: 1px solid rgba(255, 215, 0, 0.1);
    text-align: center;
    display: flex;
    flex-direction: column;
    height: 100%;
}

.listing-card:hover {
    transform: translateY(-5px);
    box-shadow: var(--box-shadow);
    border-color: var(--primary-color);
    background: rgba(255, 255, 255, 0.08);
}

.listing-icon {
    font-size: 40px;
    color: var(--primary-color);
    margin-bottom: 15px;
}

.listing-title {
    font-size: 1.3em;
    margin-bottom: 10px;
    font-weight: 600;
    color: var(--primary-color);
}

.listing-description {
    font-size: 0.9em;
    opacity: 0.8;
    margin-bottom: 20px;
    flex-grow: 1;
}

.listing-button {
    background: var(--accent-gradient);
    color: var(--text-dark);
    border: none;
    padding: 12px 20px;
    border-radius: var(--border-radius);
    font-weight: 600;
    cursor: pointer;
    transition: var(--transition);
    width: 100%;
    font-size: 1em;
    margin-top: auto;
}

.listing-button:hover {
    opacity: 0.9;
    transform: translateY(-2px);
}

.form-container {
    background: rgba(26, 26, 31, 0.95);
    border-radius: var(--border-radius);
    padding: 30px;
    margin-top: 30px;
    border: 1px solid rgba(255, 215, 0, 0.2);
    display: none;
    box-shadow: var(--box-shadow);
}

.active-form {
    display: block;
    animation: fadeIn 0.5s ease;
}

@keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
}

.form-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 25px;
    padding-bottom: 15px;
    border-bottom: 1px solid rgba(255, 215, 0, 0.2);
}

.form-title {
    font-size: 1.5em;
    font-weight: 700;
    color: var(--primary-color);
    display: flex;
    align-items: center;
    gap: 10px;
}

.close-form {
    background: none;
    border: none;
    color: var(--primary-color);
    font-size: 1.5em;
    cursor: pointer;
    padding: 5px;
    transition: var(--transition);
}

.close-form:hover {
    transform: rotate(90deg);
}

.form-group {
    margin-bottom: 20px;
}

.form-label {
    display: block;
    margin-bottom: 8px;
    font-weight: 500;
    color: var(--primary-color);
}

.form-label.required::after {
    content: ' *';
    color: var(--error-color);
}

.form-control {
    width: 100%;
    padding: 12px 15px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 215, 0, 0.2);
    border-radius: var(--border-radius);
    color: var(--text-light);
    font-size: 14px;
    font-family: 'Poppins', sans-serif;
    transition: var(--transition);
}

.form-control:focus {
    outline: none;
    border-color: var(--primary-color);
    box-shadow: 0 0 0 2px rgba(255, 215, 0, 0.2);
}

.form-select {
    width: 100%;
    padding: 12px 15px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 215, 0, 0.2);
    border-radius: var(--border-radius);
    color: var(--text-light);
    font-size: 14px;
    appearance: none;
    background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23FFD700'%3e%3cpath d='M7 10l5 5 5-5z'/%3e%3c/svg%3e");
    background-repeat: no-repeat;
    background-position: right 10px center;
    background-size: 20px;
}

.form-textarea {
    min-height: 120px;
    resize: vertical;
}

.form-radio-group, .form-checkbox-group {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
    margin-top: 10px;
}

.form-radio, .form-checkbox {
    display: flex;
    align-items: center;
    cursor: pointer;
}

.form-radio input, .form-checkbox input {
    margin-right: 8px;
    cursor: pointer;
}

.form-radio-label, .form-checkbox-label {
    cursor: pointer;
}

.form-submit {
    background: var(--accent-gradient);
    color: var(--text-dark);
    border: none;
    padding: 14px 25px;
    border-radius: var(--border-radius);
    font-weight: 600;
    cursor: pointer;
    transition: var(--transition);
    width: 100%;
    margin-top: 30px;
    font-size: 1.1em;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}

.form-submit:hover {
    opacity: 0.9;
    transform: translateY(-2px);
    box-shadow: var(--box-shadow);
}

.form-section {
    margin-bottom: 30px;
    padding-bottom: 20px;
    border-bottom: 1px solid rgba(255, 215, 0, 0.1);
}

.form-section-title {
    color: var(--primary-color);
    font-size: 1.2em;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
    font-weight: 600;
}

.form-section-title i {
    font-size: 1.1em;
}

.form-steps {
    display: flex;
    justify-content: space-between;
    margin-bottom: 30px;
    position: relative;
}

.form-step {
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
    z-index: 2;
    flex: 1;
}

.form-step-number {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background: rgba(255, 215, 0, 0.2);
    color: var(--primary-color);
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 600;
    margin-bottom: 8px;
    border: 2px solid var(--primary-color);
    transition: var(--transition);
}

.form-step.active .form-step-number {
    background: var(--accent-gradient);
    color: var(--text-dark);
    transform: scale(1.1);
}

.form-step-label {
    font-size: 0.85em;
    text-align: center;
    color: rgba(255, 255, 255, 0.7);
}

.form-step.active .form-step-label {
    color: var(--primary-color);
    font-weight: 500;
}

.form-steps::before {
    content: '';
    position: absolute;
    top: 20px;
    left: 0;
    right: 0;
    height: 2px;
    background: rgba(255, 215, 0, 0.2);
    z-index: 1;
}

.form-steps-progress {
    position: absolute;
    top: 20px;
    left: 0;
    height: 2px;
    background: var(--accent-gradient);
    z-index: 1;
    transition: width 0.3s ease;
}

.file-upload {
    position: relative;
    margin-bottom: 15px;
}

.file-upload-input {
    position: absolute;
    left: 0;
    top: 0;
    opacity: 0;
    width: 100%;
    height: 100%;
    cursor: pointer;
}

.file-upload-label {
    display: block;
    padding: 30px;
    border: 2px dashed rgba(255, 215, 0, 0.3);
    border-radius: var(--border-radius);
    text-align: center;
    cursor: pointer;
    transition: var(--transition);
}

.file-upload-label:hover {
    border-color: var(--primary-color);
    background: rgba(255, 215, 0, 0.05);
}

.file-upload-label i {
    font-size: 28px;
    color: var(--primary-color);
    margin-bottom: 10px;
    display: block;
}

.file-upload-text {
    font-size: 0.9em;
    margin-bottom: 5px;
}

.file-upload-hint {
    font-size: 0.8em;
    opacity: 0.7;
}

.file-preview {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin-top: 15px;
}

.file-preview-item {
    position: relative;
    width: 100px;
    height: 100px;
    border-radius: var(--border-radius);
    overflow: hidden;
    border: 1px solid rgba(255, 255, 255, 0.1);
}

.file-preview-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.file-preview-item-remove {
    position: absolute;
    top: 5px;
    right: 5px;
    background: rgba(0, 0, 0, 0.7);
    width: 24px;
    height: 24px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: var(--transition);
}

.file-preview-item-remove:hover {
    background: var(--error-color);
}

.file-preview-item-remove i {
    font-size: 12px;
}

.form-row {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 20px;
}

.form-date-time {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 15px;
}

.form-actions {
    display: flex;
    justify-content: space-between;
    margin-top: 30px;
}

.btn {
    padding: 12px 25px;
    border-radius: var(--border-radius);
    font-weight: 600;
    cursor: pointer;
    transition: var(--transition);
    border: none;
    font-size: 1em;
}

.btn-primary {
    background: var(--accent-gradient);
    color: var(--text-dark);
}

.btn-secondary {
    background: rgba(255, 255, 255, 0.1);
    color: var(--text-light);
    border: 1px solid rgba(255, 215, 0, 0.3);
}

.btn:hover {
    opacity: 0.9;
    transform: translateY(-2px);
    box-shadow: var(--box-shadow);
}

.confirmation-modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 2000;
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s ease;
    backdrop-filter: blur(5px);
}

.confirmation-modal.active {
    opacity: 1;
    visibility: visible;
}

.confirmation-content {
    background-color: var(--background-dark);
    border-radius: var(--border-radius);
    padding: 40px;
    text-align: center;
    max-width: 500px;
    width: 90%;
    border: 1px solid var(--primary-color);
    box-shadow: var(--box-shadow);
    animation: modalFadeIn 0.4s ease;
}

@keyframes modalFadeIn {
    from { opacity: 0; transform: scale(0.9); }
    to { opacity: 1; transform: scale(1); }
}

.confirmation-icon {
    font-size: 60px;
    color: var(--success-color);
    margin-bottom: 20px;
}

.confirmation-title {
    font-size: 1.8em;
    margin-bottom: 15px;
    color: var(--primary-color);
    font-weight: 700;
}

.confirmation-message {
    margin-bottom: 25px;
    line-height: 1.7;
}

.confirmation-button {
    background: var(--accent-gradient);
    color: var(--text-dark);
    border: none;
    padding: 14px 30px;
    border-radius: var(--border-radius);
    font-weight: 600;
    cursor: pointer;
    transition: var(--transition);
    font-size: 1.1em;
    margin-top: 20px;
    width: 100%;
    max-width: 200px;
}

.confirmation-button:hover {
    opacity: 0.9;
    transform: translateY(-2px);
    box-shadow: var(--box-shadow);
}

.form-navigation {
    display: flex;
    justify-content: space-between;
    margin-top: 30px;
}

.form-progress {
    height: 6px;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 3px;
    margin-bottom: 30px;
    overflow: hidden;
}

.form-progress-bar {
    height: 100%;
    background: var(--accent-gradient);
    border-radius: 3px;
    transition: width 0.3s ease;
}

.form-tab {
    display: none;
}

.form-tab.active {
    display: block;
    animation: fadeIn 0.5s ease;
}

.form-footer {
    margin-top: 40px;
    padding-top: 20px;
    border-top: 1px solid rgba(255, 215, 0, 0.1);
    text-align: center;
    font-size: 0.9em;
    opacity: 0.8;
}

/* Responsive adjustments */
@media (max-width: 768px) {
    .listing-types {
        grid-template-columns: 1fr;
    }
    
    .form-container {
        padding: 20px;
    }
    
    .form-row {
        grid-template-columns: 1fr;
    }
    
    .form-steps {
        flex-wrap: wrap;
        gap: 15px;
    }
    
    .form-step {
        flex: 0 0 calc(50% - 15px);
    }
    
    .form-steps::before, .form-steps-progress {
        display: none;
    }
}

@media (max-width: 480px) {
    .header {
        padding: 8px 10px;
    }
    
    .logo {
        font-size: 1.5em;
    }
    
    .menu-button {
        padding: 8px 15px;
        font-size: 0.85em;
    }
    
    .page-title {
        font-size: 1.5em;
        margin-bottom: 30px;
    }
    
    .form-title {
        font-size: 1.3em;
    }
    
    .form-step {
        flex: 0 0 100%;
    }
    
    .form-actions {
        flex-direction: column;
        gap: 15px;
    }
    
    .btn {
        width: 100%;
    }
}

/* Form validation styles */
.form-control.error {
    border-color: var(--error-color);
}

.form-feedback {
    font-size: 0.85em;
    margin-top: 5px;
    padding-left: 5px;
}

.form-feedback.error {
    color: var(--error-color);
}

.form-feedback.success {
    color: var(--success-color);
}

/* Tooltip styles */
.tooltip {
    position: relative;
    display: inline-block;
    margin-left: 5px;
    cursor: pointer;
}

.tooltip-icon {
    color: var(--primary-color);
    font-size: 0.9em;
}

.tooltip-text {
    visibility: hidden;
    width: 200px;
    background-color: rgba(0, 0, 0, 0.8);
    color: #fff;
    text-align: center;
    border-radius: var(--border-radius);
    padding: 8px;
    position: absolute;
    z-index: 1;
    bottom: 125%;
    left: 50%;
    transform: translateX(-50%);
    opacity: 0;
    transition: opacity 0.3s;
    font-size: 0.8em;
    font-weight: normal;
}

.tooltip:hover .tooltip-text {
    visibility: visible;
    opacity: 1;
}

/* Time input styling */
input[type="time"]::-webkit-calendar-picker-indicator {
    filter: invert(1);
    opacity: 0.7;
}

/* Custom scrollbar */
::-webkit-scrollbar {
    width: 8px;
    height: 8px;
}

::-webkit-scrollbar-track {
    background: rgba(255, 255, 255, 0.05);
}

::-webkit-scrollbar-thumb {
    background: rgba(255, 215, 0, 0.5);
    border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
    background: var(--primary-color);
}

body > h1:first-of-type:not(.heading) { 
    display: none !important; 
}

.markdown-body h1:first-child { 
    display: none !important; 
}

.position-relative h1:first-child { 
    display: none !important; 
}

/* Fix for the white underline in titles */
.page-title, 
.form-title {
    text-decoration: none !important;
    background-image: none !important;
}

/* Completely disable the link icon behavior */
.page-title {
    pointer-events: none;
    user-select: none;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
}

/* For Chrome's specific heading link behavior */
h1::before, h2::before, h3::before, h4::before, h5::before, h6::before {
    content: none !important;
    display: none !important;
}

/* Remove any potential pseudo-elements causing underlines */
.page-title::after, 
.form-title::after,
.page-title::before, 
.form-title::before {
    content: none !important;
    background-image: none !important;
}

    </style>
</head>
<body>
    <header class="header">
        <div class="logo">
            <i class="fas fa-list-alt logo-icon"></i>
            Nysa Lister
        </div>
        <button class="menu-button" id="menuButton">
            <i class="fas fa-bars"></i> Menu
        </button>
    </header>

    <div class="main-container">
        <h2 class="page-title">Create a New Listing</h2>
        
        <div class="listing-types" id="listingTypes">
            <!-- Listing cards will be generated by JavaScript -->
        </div>

        <!-- Form containers will be generated by JavaScript -->
        <div id="formsContainer"></div>
    </div>

    <!-- Confirmation Modal -->
    <div class="confirmation-modal" id="confirmationModal">
        <div class="confirmation-content">
            <div class="confirmation-icon">
                <i class="fas fa-check-circle"></i>
            </div>
            <h2 class="confirmation-title">Listing Submitted Successfully!</h2>
            <p class="confirmation-message">Your listing has been successfully submitted and is pending review by our team. You will receive a confirmation email shortly.</p>
            <p class="confirmation-message">All details have been sent to nysaworldofficial@gmail.com for verification.</p>
            <button class="confirmation-button" onclick="hideConfirmation()">Return to Dashboard</button>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/flatpickr"></script>
    <script>
        // Data for listing types and forms
        const listingData = {
            types: [
                {
                    id: 'serviceProvider',
                    title: 'Service Provider',
                    icon: 'fa-tools',
                    description: 'List electricians, plumbers, cleaners, and other service professionals with detailed service offerings and availability'
                },
                {
                    id: 'store',
                    title: 'Store',
                    icon: 'fa-store',
                    description: 'List retail stores, supermarkets, and other businesses with product offerings and store details'
                },
                {
                    id: 'publicPlace',
                    title: 'Public Place',
                    icon: 'fa-landmark',
                    description: 'List parks, malls, hospitals, and other public locations with visitor information and facilities'
                },
                {
                    id: 'realEstate',
                    title: 'Real Estate',
                    icon: 'fa-home',
                    description: 'List properties for sale or rent with detailed specifications and contact information'
                },
                {
                    id: 'job',
                    title: 'Job',
                    icon: 'fa-briefcase',
                    description: 'List job opportunities and vacancies with requirements and application details'
                },
                {
                    id: 'distributor',
                    title: 'Distributor',
                    icon: 'fa-truck',
                    description: 'List distributors with their product ranges and distribution areas'
                },
                {
                    id: 'voiceSeller',
                    title: 'Voice Seller',
                    icon: 'fa-microphone',
                    description: 'List voice over artists and sellers with their specialties and demo samples'
                }
            ],
            
            cities: [
                "Delhi", "Mumbai", "Bangalore", "Hyderabad", "Chennai", 
                "Kolkata", "Pune", "Ahmedabad", "Jaipur", "Lucknow"
            ],
            
            serviceCategories: [
                "Electrician", "Plumber", "Carpenter", "Painter", "Pest Control",
                "House Cleaning", "AC Repair", "Appliance Repair", "Plumbing Services",
                "Carpentry", "Masonry", "Roofing", "Welding", "Tiling", "Fabrication",
                "Gardening", "Commercial Cleaning", "Moving Services", "Laundry Services",
                "Catering", "Event Planning", "Photography", "Videography", "Makeup Artist",
                "Hair Stylist", "Tailoring", "Driving Instructor", "Tutoring", "Fitness Trainer",
                "Yoga Instructor", "Massage Therapist", "Beauty Services", "Pet Care",
                "Computer Repair", "Mobile Repair", "Network Services", "Security Services",
                "CCTV Installation", "Interior Design", "Architecture", "Legal Services",
                "Accounting", "Tax Services", "Business Consulting", "Other Service"
            ],
            
            storeCategories: [
                "Grocery Store", "Electronics", "Clothing", "Pharmacy", "Furniture",
                "Jewelry", "Footwear", "Books & Stationery", "Sports Goods", "Toys & Games",
                "Beauty Products", "Hardware", "Automobile Parts", "Pet Supplies", "Gift Shop",
                "Liquor Store", "Organic Products", "Handicrafts", "Flower Shop", "Bakery",
                "Butcher Shop", "Fish Market", "Vegetable Market", "Fruit Market", "Dairy Products",
                "Sweet Shop", "Tea & Coffee", "Spices", "Mobile Store", "Computer Store",
                "Bicycle Shop", "Fabric Store", "Other"
            ],
            
            jobCategories: [
                "IT/Software", "Sales", "Marketing", "Finance", "Human Resources",
                "Operations", "Customer Service", "Driver", "Delivery", "House Help",
                "Security", "Teacher", "Healthcare", "Hospitality", "Construction",
                "Manufacturing", "Other"
            ]
        };

        // Initialize the application
        document.addEventListener('DOMContentLoaded', function() {
            // Generate listing cards
            generateListingCards();
            
            // Generate forms
            generateForms();
            
            // Initialize event listeners
            initEventListeners();
        });

        // Generate listing cards
        function generateListingCards() {
            const container = document.getElementById('listingTypes');
            
            listingData.types.forEach(type => {
                const card = document.createElement('div');
                card.className = 'listing-card';
                card.onclick = () => showForm(`${type.id}Form`);
                
                card.innerHTML = `
                    <div class="listing-icon"><i class="fas ${type.icon}"></i></div>
                    <h3 class="listing-title">${type.title}</h3>
                    <p class="listing-description">${type.description}</p>
                    <button class="listing-button">List ${type.title.split(' ')[0]}</button>
                `;
                
                container.appendChild(card);
            });
        }

        // Generate all forms
        function generateForms() {
            const container = document.getElementById('formsContainer');
            
            // Service Provider Form
            container.appendChild(createServiceProviderForm());
            
            // Store Form
            container.appendChild(createStoreForm());
            
            // Public Place Form
            container.appendChild(createPublicPlaceForm());
            
            // Real Estate Form
            container.appendChild(createRealEstateForm());
            
            // Job Form
            container.appendChild(createJobForm());
            
            // Distributor Form
            container.appendChild(createDistributorForm());
            
            // Voice Seller Form
            container.appendChild(createVoiceSellerForm());
        }

        // Create Service Provider Form
        function createServiceProviderForm() {
            const form = document.createElement('div');
            form.id = 'serviceProviderForm';
            form.className = 'form-container';
            
            form.innerHTML = `
                <div class="form-header">
                    <h2 class="form-title"><i class="fas fa-tools"></i> Service Provider Listing</h2>
                    <button class="close-form" onclick="hideForms()">
                        <i class="fas fa-times"></i>
                    </button>
                </div>
                
                <div class="form-steps">
                    <div class="form-step active" data-step="1">
                        <div class="form-step-number">1</div>
                        <div class="form-step-label">Basic Info</div>
                    </div>
                    <div class="form-step" data-step="2">
                        <div class="form-step-number">2</div>
                        <div class="form-step-label">Service Details</div>
                    </div>
                    <div class="form-step" data-step="3">
                        <div class="form-step-number">3</div>
                        <div class="form-step-label">Location</div>
                    </div>
                    <div class="form-step" data-step="4">
                        <div class="form-step-number">4</div>
                        <div class="form-step-label">Documents</div>
                    </div>
                    <div class="form-steps-progress" style="width: 25%;"></div>
                </div>
                
                <form id="serviceProviderFormData">
                    <!-- Tab 1: Basic Info -->
                    <div class="form-tab active" data-tab="1">
                        ${createBasicInfoSection('service')}
                        <div class="form-navigation">
                            <button type="button" class="btn btn-secondary" disabled>Previous</button>
                            <button type="button" class="btn btn-primary" onclick="nextTab(1, 'serviceProvider')">Next</button>
                        </div>
                    </div>
                    
                    <!-- Tab 2: Service Details -->
                    <div class="form-tab" data-tab="2">
                        ${createServiceDetailsSection()}
                        <div class="form-navigation">
                            <button type="button" class="btn btn-secondary" onclick="prevTab(2, 'serviceProvider')">Previous</button>
                            <button type="button" class="btn btn-primary" onclick="nextTab(2, 'serviceProvider')">Next</button>
                        </div>
                    </div>
                    
                    <!-- Tab 3: Location -->
                    <div class="form-tab" data-tab="3">
                        ${createLocationSection('service')}
                        <div class="form-navigation">
                            <button type="button" class="btn btn-secondary" onclick="prevTab(3, 'serviceProvider')">Previous</button>
                            <button type="button" class="btn btn-primary" onclick="nextTab(3, 'serviceProvider')">Next</button>
                        </div>
                    </div>
                    
                    <!-- Tab 4: Documents -->
                    <div class="form-tab" data-tab="4">
                        ${createDocumentsSection('service')}
                        <div class="form-navigation">
                            <button type="button" class="btn btn-secondary" onclick="prevTab(4, 'serviceProvider')">Previous</button>
                            <button type="submit" class="btn btn-primary">Submit Listing</button>
                        </div>
                    </div>
                </form>
                
                <div class="form-footer">
                    <p>Your information is secure and will only be used for listing purposes.</p>
                    <p>Need help? Contact support@nysalister.com</p>
                </div>
            `;
            
            return form;
        }

        // Create Store Form
        function createStoreForm() {
            const form = document.createElement('div');
            form.id = 'storeForm';
            form.className = 'form-container';
            
            form.innerHTML = `
                <div class="form-header">
                    <h2 class="form-title"><i class="fas fa-store"></i> Store Listing</h2>
                    <button class="close-form" onclick="hideForms()">
                        <i class="fas fa-times"></i>
                    </button>
                </div>
                
                <div class="form-steps">
                    <div class="form-step active" data-step="1">
                        <div class="form-step-number">1</div>
                        <div class="form-step-label">Basic Info</div>
                    </div>
                    <div class="form-step" data-step="2">
                        <div class="form-step-number">2</div>
                        <div class="form-step-label">Store Details</div>
                    </div>
                    <div class="form-step" data-step="3">
                        <div class="form-step-number">3</div>
                        <div class="form-step-label">Location</div>
                    </div>
                    <div class="form-step" data-step="4">
                        <div class="form-step-number">4</div>
                        <div class="form-step-label">Uploads</div>
                    </div>
                    <div class="form-steps-progress" style="width: 25%;"></div>
                </div>
                
                <form id="storeFormData">
                    <!-- Tab 1: Basic Info -->
                    <div class="form-tab active" data-tab="1">
                        ${createBasicInfoSection('store')}
                        <div class="form-navigation">
                            <button type="button" class="btn btn-secondary" disabled>Previous</button>
                            <button type="button" class="btn btn-primary" onclick="nextTab(1, 'store')">Next</button>
                        </div>
                    </div>
                    
                    <!-- Tab 2: Store Details -->
                    <div class="form-tab" data-tab="2">
                        ${createStoreDetailsSection()}
                        <div class="form-navigation">
                            <button type="button" class="btn btn-secondary" onclick="prevTab(2, 'store')">Previous</button>
                            <button type="button" class="btn btn-primary" onclick="nextTab(2, 'store')">Next</button>
                        </div>
                    </div>
                    
                    <!-- Tab 3: Location -->
                    <div class="form-tab" data-tab="3">
                        ${createLocationSection('store')}
                        <div class="form-navigation">
                            <button type="button" class="btn btn-secondary" onclick="prevTab(3, 'store')">Previous</button>
                            <button type="button" class="btn btn-primary" onclick="nextTab(3, 'store')">Next</button>
                        </div>
                    </div>
                    
                    <!-- Tab 4: Uploads -->
                    <div class="form-tab" data-tab="4">
                        ${createStoreUploadsSection()}
                        <div class="form-navigation">
                            <button type="button" class="btn btn-secondary" onclick="prevTab(4, 'store')">Previous</button>
                            <button type="submit" class="btn btn-primary">Submit Listing</button>
                        </div> 
                                        </div>
            </form>
            
            <div class="form-footer">
                <p>Your information is secure and will only be used for listing purposes.</p>
                <p>Need help? Contact support@nysalister.com</p>
            </div>
        `;
        
        return form;
    }

    // Create Public Place Form
    function createPublicPlaceForm() {
        const form = document.createElement('div');
        form.id = 'publicPlaceForm';
        form.className = 'form-container';
        
        form.innerHTML = `
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-landmark"></i> Public Place Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="form-steps">
                <div class="form-step active" data-step="1">
                    <div class="form-step-number">1</div>
                    <div class="form-step-label">Basic Info</div>
                </div>
                <div class="form-step" data-step="2">
                    <div class="form-step-number">2</div>
                    <div class="form-step-label">Place Details</div>
                </div>
                <div class="form-step" data-step="3">
                    <div class="form-step-number">3</div>
                    <div class="form-step-label">Location</div>
                </div>
                <div class="form-step" data-step="4">
                    <div class="form-step-number">4</div>
                    <div class="form-step-label">Photos</div>
                </div>
                <div class="form-steps-progress" style="width: 25%;"></div>
            </div>
            
            <form id="publicPlaceFormData">
                <!-- Tab 1: Basic Info -->
                <div class="form-tab active" data-tab="1">
                    ${createBasicInfoSection('public')}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" disabled>Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(1, 'publicPlace')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 2: Place Details -->
                <div class="form-tab" data-tab="2">
                    ${createPublicPlaceDetailsSection()}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(2, 'publicPlace')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(2, 'publicPlace')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 3: Location -->
                <div class="form-tab" data-tab="3">
                    ${createLocationSection('public')}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(3, 'publicPlace')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(3, 'publicPlace')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 4: Photos -->
                <div class="form-tab" data-tab="4">
                    ${createPublicPlacePhotosSection()}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(4, 'publicPlace')">Previous</button>
                        <button type="submit" class="btn btn-primary">Submit Listing</button>
                    </div>
                </div>
            </form>
            
            <div class="form-footer">
                <p>Your information is secure and will only be used for listing purposes.</p>
                <p>Need help? Contact support@nysalister.com</p>
            </div>
        `;
        
        return form;
    }

    // Create Real Estate Form
    function createRealEstateForm() {
        const form = document.createElement('div');
        form.id = 'realEstateForm';
        form.className = 'form-container';
        
        form.innerHTML = `
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-home"></i> Real Estate Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="form-steps">
                <div class="form-step active" data-step="1">
                    <div class="form-step-number">1</div>
                    <div class="form-step-label">Basic Info</div>
                </div>
                <div class="form-step" data-step="2">
                    <div class="form-step-number">2</div>
                    <div class="form-step-label">Property Details</div>
                </div>
                <div class="form-step" data-step="3">
                    <div class="form-step-number">3</div>
                    <div class="form-step-label">Location</div>
                </div>
                <div class="form-step" data-step="4">
                    <div class="form-step-number">4</div>
                    <div class="form-step-label">Media</div>
                </div>
                <div class="form-steps-progress" style="width: 25%;"></div>
            </div>
            
            <form id="realEstateFormData">
                <!-- Tab 1: Basic Info -->
                <div class="form-tab active" data-tab="1">
                    ${createBasicInfoSection('realEstate')}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" disabled>Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(1, 'realEstate')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 2: Property Details -->
                <div class="form-tab" data-tab="2">
                    ${createRealEstateDetailsSection()}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(2, 'realEstate')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(2, 'realEstate')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 3: Location -->
                <div class="form-tab" data-tab="3">
                    ${createLocationSection('realEstate')}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(3, 'realEstate')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(3, 'realEstate')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 4: Media -->
                <div class="form-tab" data-tab="4">
                    ${createRealEstateMediaSection()}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(4, 'realEstate')">Previous</button>
                        <button type="submit" class="btn btn-primary">Submit Listing</button>
                    </div>
                </div>
            </form>
            
            <div class="form-footer">
                <p>Your information is secure and will only be used for listing purposes.</p>
                <p>Need help? Contact support@nysalister.com</p>
            </div>
        `;
        
        return form;
    }

    // Create Job Form
    function createJobForm() {
        const form = document.createElement('div');
        form.id = 'jobForm';
        form.className = 'form-container';
        
        form.innerHTML = `
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-briefcase"></i> Job Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="form-steps">
                <div class="form-step active" data-step="1">
                    <div class="form-step-number">1</div>
                    <div class="form-step-label">Basic Info</div>
                </div>
                <div class="form-step" data-step="2">
                    <div class="form-step-number">2</div>
                    <div class="form-step-label">Job Details</div>
                </div>
                <div class="form-step" data-step="3">
                    <div class="form-step-number">3</div>
                    <div class="form-step-label">Requirements</div>
                </div>
                <div class="form-step" data-step="4">
                    <div class="form-step-number">4</div>
                    <div class="form-step-label">Contact Info</div>
                </div>
                <div class="form-steps-progress" style="width: 25%;"></div>
            </div>
            
            <form id="jobFormData">
                <!-- Tab 1: Basic Info -->
                <div class="form-tab active" data-tab="1">
                    ${createBasicInfoSection('job')}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" disabled>Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(1, 'job')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 2: Job Details -->
                <div class="form-tab" data-tab="2">
                    ${createJobDetailsSection()}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(2, 'job')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(2, 'job')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 3: Requirements -->
                <div class="form-tab" data-tab="3">
                    ${createJobRequirementsSection()}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(3, 'job')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(3, 'job')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 4: Contact Info -->
                <div class="form-tab" data-tab="4">
                    ${createJobContactSection()}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(4, 'job')">Previous</button>
                        <button type="submit" class="btn btn-primary">Submit Listing</button>
                    </div>
                </div>
            </form>
            
            <div class="form-footer">
                <p>Your information is secure and will only be used for listing purposes.</p>
                <p>Need help? Contact support@nysalister.com</p>
            </div>
        `;
        
        return form;
    }

    // Create Distributor Form
    function createDistributorForm() {
        const form = document.createElement('div');
        form.id = 'distributorForm';
        form.className = 'form-container';
        
        form.innerHTML = `
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-truck"></i> Distributor Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="form-steps">
                <div class="form-step active" data-step="1">
                    <div class="form-step-number">1</div>
                    <div class="form-step-label">Basic Info</div>
                </div>
                <div class="form-step" data-step="2">
                    <div class="form-step-number">2</div>
                    <div class="form-step-label">Distribution Info</div>
                </div>
                <div class="form-step" data-step="3">
                    <div class="form-step-number">3</div>
                    <div class="form-step-label">Location</div>
                </div>
                <div class="form-step" data-step="4">
                    <div class="form-step-number">4</div>
                    <div class="form-step-label">Documents</div>
                </div>
                <div class="form-steps-progress" style="width: 25%;"></div>
            </div>
            
            <form id="distributorFormData">
                <!-- Tab 1: Basic Info -->
                <div class="form-tab active" data-tab="1">
                    ${createBasicInfoSection('distributor')}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" disabled>Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(1, 'distributor')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 2: Distribution Info -->
                <div class="form-tab" data-tab="2">
                    ${createDistributorInfoSection()}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(2, 'distributor')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(2, 'distributor')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 3: Location -->
                <div class="form-tab" data-tab="3">
                    ${createLocationSection('distributor')}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(3, 'distributor')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(3, 'distributor')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 4: Documents -->
                <div class="form-tab" data-tab="4">
                    ${createDistributorDocumentsSection()}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(4, 'distributor')">Previous</button>
                        <button type="submit" class="btn btn-primary">Submit Listing</button>
                    </div>
                </div>
            </form>
            
            <div class="form-footer">
                <p>Your information is secure and will only be used for listing purposes.</p>
                <p>Need help? Contact support@nysalister.com</p>
            </div>
        `;
        
        return form;
    }

    // Create Voice Seller Form
    function createVoiceSellerForm() {
        const form = document.createElement('div');
        form.id = 'voiceSellerForm';
        form.className = 'form-container';
        
        form.innerHTML = `
            <div class="form-header">
                <h2 class="form-title"><i class="fas fa-microphone"></i> Voice Seller Listing</h2>
                <button class="close-form" onclick="hideForms()">
                    <i class="fas fa-times"></i>
                </button>
            </div>
            
            <div class="form-steps">
                <div class="form-step active" data-step="1">
                    <div class="form-step-number">1</div>
                    <div class="form-step-label">Basic Info</div>
                </div>
                <div class="form-step" data-step="2">
                    <div class="form-step-number">2</div>
                    <div class="form-step-label">Voice Details</div>
                </div>
                <div class="form-step" data-step="3">
                    <div class="form-step-number">3</div>
                    <div class="form-step-label">Samples</div>
                </div>
                <div class="form-step" data-step="4">
                    <div class="form-step-number">4</div>
                    <div class="form-step-label">Contact Info</div>
                </div>
                <div class="form-steps-progress" style="width: 25%;"></div>
            </div>
            
            <form id="voiceSellerFormData">
                <!-- Tab 1: Basic Info -->
                <div class="form-tab active" data-tab="1">
                    ${createBasicInfoSection('voice')}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" disabled>Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(1, 'voiceSeller')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 2: Voice Details -->
                <div class="form-tab" data-tab="2">
                    ${createVoiceDetailsSection()}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(2, 'voiceSeller')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(2, 'voiceSeller')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 3: Samples -->
                <div class="form-tab" data-tab="3">
                    ${createVoiceSamplesSection()}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(3, 'voiceSeller')">Previous</button>
                        <button type="button" class="btn btn-primary" onclick="nextTab(3, 'voiceSeller')">Next</button>
                    </div>
                </div>
                
                <!-- Tab 4: Contact Info -->
                <div class="form-tab" data-tab="4">
                    ${createVoiceContactSection()}
                    <div class="form-navigation">
                        <button type="button" class="btn btn-secondary" onclick="prevTab(4, 'voiceSeller')">Previous</button>
                        <button type="submit" class="btn btn-primary">Submit Listing</button>
                    </div>
                </div>
            </form>
            
            <div class="form-footer">
                <p>Your information is secure and will only be used for listing purposes.</p>
                <p>Need help? Contact support@nysalister.com</p>
            </div>
        `;
        
        return form;
    }

    // Helper functions to create form sections
    function createBasicInfoSection(type) {
        let specificFields = '';
        
        if (type === 'service') {
            specificFields = `
                <div class="form-group">
                    <label class="form-label required">Service Category</label>
                    <select class="form-control" name="serviceCategory" required>
                        <option value="">Select a category</option>
                        ${listingData.serviceCategories.map(cat => `<option value="${cat}">${cat}</option>`).join('')}
                    </select>
                </div>
            `;
        } else if (type === 'store') {
            specificFields = `
                <div class="form-group">
                    <label class="form-label required">Store Category</label>
                    <select class="form-control" name="storeCategory" required>
                        <option value="">Select a category</option>
                        ${listingData.storeCategories.map(cat => `<option value="${cat}">${cat}</option>`).join('')}
                    </select>
                </div>
            `;
        } else if (type === 'job') {
            specificFields = `
                <div class="form-group">
                    <label class="form-label required">Job Category</label>
                    <select class="form-control" name="jobCategory" required>
                        <option value="">Select a category</option>
                        ${listingData.jobCategories.map(cat => `<option value="${cat}">${cat}</option>`).join('')}
                    </select>
                </div>
            `;
        }
        
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-info-circle"></i> Basic Information</h3>
                <div class="form-group">
                    <label class="form-label required">${type === 'job' ? 'Job Title' : (type === 'public' ? 'Place Name' : (type === 'realEstate' ? 'Property Name' : 'Business Name'))}</label>
                    <input type="text" class="form-control" name="name" placeholder="Enter ${type === 'job' ? 'job title' : (type === 'public' ? 'place name' : (type === 'realEstate' ? 'property name' : 'business name'))}" required>
                </div>
                ${specificFields}
                <div class="form-group">
                    <label class="form-label required">Description</label>
                    <textarea class="form-control form-textarea" name="description" placeholder="Provide a detailed description" required></textarea>
                </div>
            </div>
        `;
    }

    function createServiceDetailsSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-clipboard-list"></i> Service Details</h3>
                <div class="form-group">
                    <label class="form-label">Services Offered</label>
                    <textarea class="form-control form-textarea" name="servicesOffered" placeholder="List all services you offer"></textarea>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Hourly Rate (₹)</label>
                        <input type="number" class="form-control" name="hourlyRate" placeholder="e.g. 500">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Service Area (km radius)</label>
                        <input type="number" class="form-control" name="serviceRadius" placeholder="e.g. 10">
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Years of Experience</label>
                    <input type="number" class="form-control" name="experience" placeholder="e.g. 5">
                </div>
                <div class="form-group">
                    <label class="form-label">Certifications</label>
                    <textarea class="form-control form-textarea" name="certifications" placeholder="List any certifications you have"></textarea>
                </div>
            </div>
        `;
    }

    function createStoreDetailsSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-store-alt"></i> Store Details</h3>
                <div class="form-group">
                    <label class="form-label">Products Offered</label>
                    <textarea class="form-control form-textarea" name="productsOffered" placeholder="List the main products you offer"></textarea>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Established Year</label>
                        <input type="number" class="form-control" name="establishedYear" placeholder="e.g. 2010">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Number of Employees</label>
                        <input type="number" class="form-control" name="employeeCount" placeholder="e.g. 5">
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Brands Available</label>
                    <textarea class="form-control form-textarea" name="brandsAvailable" placeholder="List the brands you carry"></textarea>
                </div>
                <div class="form-group">
                    <label class="form-label">Special Offers</label>
                    <textarea class="form-control form-textarea" name="specialOffers" placeholder="List any current special offers"></textarea>
                </div>
            </div>
        `;
    }

    function createPublicPlaceDetailsSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-info-circle"></i> Place Details</h3>
                <div class="form-group">
                    <label class="form-label">Place Type</label>
                    <select class="form-control" name="placeType">
                        <option value="">Select type</option>
                        <option value="Park">Park</option>
                        <option value="Mall">Mall</option>
                        <option value="Hospital">Hospital</option>
                        <option value="School">School</option>
                        <option value="Government Office">Government Office</option>
                        <option value="Religious Place">Religious Place</option>
                        <option value="Tourist Attraction">Tourist Attraction</option>
                        <option value="Other">Other</option>
                    </select>
                </div>
                <div class="form-group">
                    <label class="form-label">Features & Facilities</label>
                    <textarea class="form-control form-textarea" name="facilities" placeholder="List the features and facilities available"></textarea>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Entry Fee (₹)</label>
                        <input type="number" class="form-control" name="entryFee" placeholder="0 if free">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Average Visit Duration (hours)</label>
                        <input type="number" class="form-control" name="visitDuration" placeholder="e.g. 2">
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Rules & Regulations</label>
                    <textarea class="form-control form-textarea" name="rules" placeholder="List any important rules visitors should know"></textarea>
                </div>
            </div>
        `;
    }

    function createRealEstateDetailsSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-home"></i> Property Details</h3>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label required">Property Type</label>
                        <select class="form-control" name="propertyType" required>
                            <option value="">Select type</option>
                            <option value="Apartment">Apartment</option>
                            <option value="Villa">Villa</option>
                            <option value="Plot">Plot</option>
                            <option value="Commercial">Commercial</option>
                            <option value="Farm House">Farm House</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label required">Transaction Type</label>
                        <select class="form-control" name="transactionType" required>
                            <option value="">Select type</option>
                            <option value="Sale">For Sale</option>
                            <option value="Rent">For Rent</option>
                        </select>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Area (sq.ft)</label>
                        <input type="number" class="form-control" name="area" placeholder="e.g. 1200">
                    </div>
                    <div class="form-group">
                        <label class="form-label required">Price (₹)</label>
                        <input type="number" class="form-control" name="price" placeholder="e.g. 5000000" required>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Bedrooms</label>
                        <input type="number" class="form-control" name="bedrooms" placeholder="e.g. 2">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Bathrooms</label>
                        <input type="number" class="form-control" name="bathrooms" placeholder="e.g. 2">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Floors</label>
                        <input type="number" class="form-control" name="floors" placeholder="e.g. 1">
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Amenities</label>
                    <textarea class="form-control form-textarea" name="amenities" placeholder="List all amenities (e.g. Swimming Pool, Gym, Parking)"></textarea>
                </div>
                <div class="form-group">
                    <label class="form-label">Construction Year</label>
                    <input type="number" class="form-control" name="constructionYear" placeholder="e.g. 2015">
                </div>
            </div>
        `;
    }

    function createJobDetailsSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-briefcase"></i> Job Details</h3>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label required">Job Type</label>
                        <select class="form-control" name="jobType" required>
                            <option value="">Select type</option>
                            <option value="Full-time">Full-time</option>
                            <option value="Part-time">Part-time</option>
                            <option value="Contract">Contract</option>
                            <option value="Temporary">Temporary</option>
                            <option value="Internship">Internship</option>
                            <option value="Freelance">Freelance</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label required">Salary (₹)</label>
                        <input type="text" class="form-control" name="salary" placeholder="e.g. 25000 or Negotiable" required>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Experience Required (years)</label>
                        <input type="number" class="form-control" name="experienceRequired" placeholder="e.g. 2">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Vacancies</label>
                        <input type="number" class="form-control" name="vacancies" placeholder="e.g. 3">
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Key Responsibilities</label>
                    <textarea class="form-control form-textarea" name="responsibilities" placeholder="List the key responsibilities for this position"></textarea>
                </div>
                <div class="form-group">
                    <label class="form-label">Benefits</label>
                    <textarea class="form-control form-textarea" name="benefits" placeholder="List any benefits offered"></textarea>
                </div>
            </div>
        `;
    }

    function createDistributorInfoSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-truck-loading"></i> Distribution Information</h3>
                <div class="form-group">
                    <label class="form-label required">Products Distributed</label>
                    <textarea class="form-control form-textarea" name="productsDistributed" placeholder="List all products you distribute" required></textarea>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Minimum Order Quantity</label>
                        <input type="text" class="form-control" name="minOrder" placeholder="e.g. 100 units">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Delivery Time</label>
                        <input type="text" class="form-control" name="deliveryTime" placeholder="e.g. 3-5 days">
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Brands Distributed</label>
                    <textarea class="form-control form-textarea" name="brandsDistributed" placeholder="List the brands you distribute"></textarea>
                </div>
                <div class="form-group">
                    <label class="form-label">Distribution Areas</label>
                    <textarea class="form-control form-textarea" name="distributionAreas" placeholder="List all areas you cover"></textarea>
                </div>
            </div>
        `;
    }

    function createVoiceDetailsSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-microphone-alt"></i> Voice Details</h3>
                <div class="form-group">
                    <label class="form-label required">Voice Type</label>
                    <div class="form-radio-group">
                        <label class="form-radio">
                            <input type="radio" name="voiceType" value="Male" required> Male
                        </label>
                        <label class="form-radio">
                            <input type="radio" name="voiceType" value="Female"> Female
                        </label>
                        <label class="form-radio">
                            <input type="radio" name="voiceType" value="Child"> Child
                        </label>
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label required">Voice Styles</label>
                    <div class="form-checkbox-group">
                        <label class="form-checkbox">
                            <input type="checkbox" name="voiceStyles" value="Commercial"> Commercial
                        </label>
                        <label class="form-checkbox">
                            <input type="checkbox" name="voiceStyles" value="Narrative"> Narrative
                        </label>
                        <label class="form-checkbox">
                            <input type="checkbox" name="voiceStyles" value="Character"> Character
                        </label>
                        <label class="form-checkbox">
                            <input type="checkbox" name="voiceStyles" value="Announcer"> Announcer
                        </label>
                        <label class="form-checkbox">
                            <input type="checkbox" name="voiceStyles" value="Conversational"> Conversational
                        </label>
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Languages</label>
                    <textarea class="form-control form-textarea" name="languages" placeholder="List all languages you can voice in"></textarea>
                </div>
                <div class="form-group">
                    <label class="form-label">Accents</label>
                    <textarea class="form-control form-textarea" name="accents" placeholder="List all accents you can perform"></textarea>
                </div>
                <div class="form-group">
                    <label class="form-label">Hourly Rate (₹)</label>
                    <input type="number" class="form-control" name="hourlyRate" placeholder="e.g. 2000">
                </div>
            </div>
        `;
    }

    function createLocationSection(type) {
        let specificFields = '';
        
        if (type === 'service') {
            specificFields = `
                <div class="form-group">
                    <label class="form-label">Service Areas</label>
                    <textarea class="form-control form-textarea" name="serviceAreas" placeholder="List all areas you serve"></textarea>
                </div>
            `;
        } else if (type === 'store') {
            specificFields = `
                <div class="form-group">
                    <label class="form-label">Store Hours</label>
                    <div class="form-row">
                        <div class="form-group">
                            <label class="form-label">Opening Time</label>
                            <input type="time" class="form-control" name="openingTime">
                        </div>
                        <div class="form-group">
                            <label class="form-label">Closing Time</label>
                            <input type="time" class="form-control" name="closingTime">
                        </div>
                    </div>
                </div>
            `;
        } else if (type === 'public') {
            specificFields = `
                <div class="form-group">
                    <label class="form-label">Opening Hours</label>
                    <div class="form-row">
                        <div class="form-group">
                            <label class="form-label">Opening Time</label>
                            <input type="time" class="form-control" name="openingTime">
                        </div>
                        <div class="form-group">
                            <label class="form-label">Closing Time</label>
                            <input type="time" class="form-control" name="closingTime">
                        </div>
                    </div>
                </div>
            `;
        }
        
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-map-marker-alt"></i> Location Information</h3>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label required">City</label>
                        <select class="form-control" name="city" required>
                            <option value="">Select your city</option>
                            ${listingData.cities.map(city => `<option value="${city}">${city}</option>`).join('')}
                        </select>
                    </div>
                    <div class="form-group">
                        <label class="form-label">Area/Locality</label>
                        <input type="text" class="form-control" name="area" placeholder="Enter your locality">
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label required">Address</label>
                    <textarea class="form-control form-textarea" name="address" placeholder="Enter full address" required></textarea>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Landmark</label>
                        <input type="text" class="form-control" name="landmark" placeholder="Nearby landmark">
                    </div>
                    <div class="form-group">
                        <label class="form-label">Pincode</label>
                        <input type="text" class="form-control" name="pincode" placeholder="6-digit pincode">
                    </div>
                </div>
                ${specificFields}
            </div>
        `;
    }

    function createDocumentsSection(type) {
        let specificFields = '';
        
        if (type === 'service') {
            specificFields = `
                <div class="form-group">
                    <label class="form-label">Service Certifications (if any)</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="serviceCertifications" accept=".pdf,.jpg,.jpeg,.png" multiple>
                        <label for="serviceCertifications" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Certification Files</div>
                            <div class="file-upload-hint">PDF, JPG, PNG (Max 5MB each)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="serviceCertificationsPreview"></div>
                </div>
            `;
        }
        
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-file-alt"></i> Documents & Verification</h3>
                <div class="form-group">
                    <label class="form-label required">ID Proof</label>
                    <select class="form-control" name="idProofType" required>
                        <option value="">Select ID type</option>
                        <option value="Aadhar">Aadhar Card</option>
                        <option value="PAN">PAN Card</option>
                        <option value="Driving License">Driving License</option>
                        <option value="Voter ID">Voter ID</option>
                        <option value="Passport">Passport</option>
                    </select>
                </div>
                <div class="form-group">
                    <label class="form-label required">ID Proof File</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="idProofFile" accept=".pdf,.jpg,.jpeg,.png" required>
                        <label for="idProofFile" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload ID Proof</div>
                            <div class="file-upload-hint">PDF, JPG, PNG (Max 5MB)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="idProofFilePreview"></div>
                </div>
                ${specificFields}
                <div class="form-group">
                    <label class="form-label">Additional Documents (if any)</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="additionalDocs" accept=".pdf,.jpg,.jpeg,.png" multiple>
                        <label for="additionalDocs" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Additional Files</div>
                            <div class="file-upload-hint">PDF, JPG, PNG (Max 5MB each)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="additionalDocsPreview"></div>
                </div>
            </div>
        `;
    }

    function createStoreUploadsSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-images"></i> Store Photos</h3>
                <div class="form-group">
                    <label class="form-label required">Store Front Photo</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="storeFrontPhoto" accept=".jpg,.jpeg,.png" required>
                        <label for="storeFrontPhoto" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Store Front Photo</div>
                            <div class="file-upload-hint">JPG, PNG (Max 5MB)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="storeFrontPhotoPreview"></div>
                </div>
                <div class="form-group">
                    <label class="form-label">Interior Photos (up to 5)</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="interiorPhotos" accept=".jpg,.jpeg,.png" multiple>
                        <label for="interiorPhotos" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Interior Photos</div>
                            <div class="file-upload-hint">JPG, PNG (Max 5MB each)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="interiorPhotosPreview"></div>
                </div>
                <div class="form-group">
                    <label class="form-label">Product Photos (up to 10)</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="productPhotos" accept=".jpg,.jpeg,.png" multiple>
                        <label for="productPhotos" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Product Photos</div>
                            <div class="file-upload-hint">JPG, PNG (Max 5MB each)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="productPhotosPreview"></div>
                </div>
            </div>
        `;
    }

    function createPublicPlacePhotosSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-images"></i> Place Photos</h3>
                <div class="form-group">
                    <label class="form-label required">Main Photo</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="mainPlacePhoto" accept=".jpg,.jpeg,.png" required>
                        <label for="mainPlacePhoto" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Main Photo</div>
                            <div class="file-upload-hint">JPG, PNG (Max 5MB)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="mainPlacePhotoPreview"></div>
                </div>
                <div class="form-group">
                    <label class="form-label">Additional Photos (up to 10)</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="additionalPlacePhotos" accept=".jpg,.jpeg,.png" multiple>
                        <label for="additionalPlacePhotos" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Additional Photos</div>
                            <div class="file-upload-hint">JPG, PNG (Max 5MB each)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="additionalPlacePhotosPreview"></div>
                </div>
                <div class="form-group">
                    <label class="form-label">Map Location Screenshot</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="mapScreenshot" accept=".jpg,.jpeg,.png">
                        <label for="mapScreenshot" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Map Screenshot</div>
                            <div class="file-upload-hint">JPG, PNG (Max 5MB)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="mapScreenshotPreview"></div>
                </div>
            </div>
        `;
    }

    function createRealEstateMediaSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-images"></i> Property Media</h3>
                <div class="form-group">
                    <label class="form-label required">Main Property Photo</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="mainPropertyPhoto" accept=".jpg,.jpeg,.png" required>
                        <label for="mainPropertyPhoto" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Main Photo</div>
                            <div class="file-upload-hint">JPG, PNG (Max 5MB)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="mainPropertyPhotoPreview"></div>
                </div>
                <div class="form-group">
                    <label class="form-label">Exterior Photos (up to 5)</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="exteriorPhotos" accept=".jpg,.jpeg,.png" multiple>
                        <label for="exteriorPhotos" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Exterior Photos</div>
                            <div class="file-upload-hint">JPG, PNG (Max 5MB each)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="exteriorPhotosPreview"></div>
                </div>
                <div class="form-group">
                    <label class="form-label">Interior Photos (up to 10)</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="interiorPropertyPhotos" accept=".jpg,.jpeg,.png" multiple>
                        <label for="interiorPropertyPhotos" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Interior Photos</div>
                            <div class="file-upload-hint">JPG, PNG (Max 5MB each)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="interiorPropertyPhotosPreview"></div>
                </div>
                <div class="form-group">
                    <label class="form-label">Floor Plan (if available)</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="floorPlan" accept=".jpg,.jpeg,.png,.pdf">
                        <label for="floorPlan" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Floor Plan</div>
                            <div class="file-upload-hint">JPG, PNG, PDF (Max 5MB)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="floorPlanPreview"></div>
                </div>
            </div>
        `;
    }

    function createJobRequirementsSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-clipboard-check"></i> Job Requirements</h3>
                <div class="form-group">
                    <label class="form-label">Education Requirements</label>
                    <textarea class="form-control form-textarea" name="educationRequirements" placeholder="List required education qualifications"></textarea>
                </div>
                <div class="form-group">
                    <label class="form-label">Skills Required</label>
                    <textarea class="form-control form-textarea" name="skillsRequired" placeholder="List required skills"></textarea>
                </div>
                <div class="form-group">
                    <label class="form-label">Certifications (if any)</label>
                    <textarea class="form-control form-textarea" name="jobCertifications" placeholder="List any required certifications"></textarea>
                </div>
                <div class="form-group">
                    <label class="form-label">Physical Requirements</label>
                    <textarea class="form-control form-textarea" name="physicalRequirements" placeholder="List any physical requirements for the job"></textarea>
                </div>
                <div class="form-group">
                    <label class="form-label">Other Requirements</label>
                    <textarea class="form-control form-textarea" name="otherRequirements" placeholder="List any other requirements"></textarea>
                </div>
            </div>
        `;
    }

    function createJobContactSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-id-card"></i> Contact Information</h3>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label required">Contact Person</label>
                        <input type="text" class="form-control" name="contactPerson" placeholder="Name of contact person" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label required">Contact Number</label>
                        <input type="tel" class="form-control" name="contactNumber" placeholder="10-digit mobile number" required>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Alternate Number</label>
                        <input type="tel" class="form-control" name="alternateNumber" placeholder="Alternate contact number">
                    </div>
                    <div class="form-group">
                        <label class="form-label required">Email</label>
                        <input type="email" class="form-control" name="email" placeholder="Contact email address" required>
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Application Method</label>
                    <div class="form-checkbox-group">
                        <label class="form-checkbox">
                            <input type="checkbox" name="applicationMethods" value="Email"> Email
                        </label>
                        <label class="form-checkbox">
                            <input type="checkbox" name="applicationMethods" value="Phone"> Phone
                        </label>
                        <label class="form-checkbox">
                            <input type="checkbox" name="applicationMethods" value="In Person"> In Person
                        </label>
                        <label class="form-checkbox">
                            <input type="checkbox" name="applicationMethods" value="Website"> Website
                        </label>
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Application Instructions</label>
                    <textarea class="form-control form-textarea" name="applicationInstructions" placeholder="Provide instructions for applicants"></textarea>
                </div>
            </div>
        `;
    }

    function createDistributorDocumentsSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-file-contract"></i> Business Documents</h3>
                <div class="form-group">
                    <label class="form-label required">Business Registration Proof</label>
                    <select class="form-control" name="businessProofType" required>
                        <option value="">Select document type</option>
                        <option value="GST Certificate">GST Certificate</option>
                        <option value="Trade License">Trade License</option>
                        <option value="Company Registration">Company Registration</option>
                        <option value="Partnership Deed">Partnership Deed</option>
                        <option value="Other">Other</option>
                    </select>
                </div>
                <div class="form-group">
                    <label class="form-label required">Registration Document</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="registrationDoc" accept=".pdf,.jpg,.jpeg,.png" required>
                        <label for="registrationDoc" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Registration Document</div>
                            <div class="file-upload-hint">PDF, JPG, PNG (Max 5MB)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="registrationDocPreview"></div>
                </div>
                <div class="form-group">
                    <label class="form-label">Brand Authorization Letters (if any)</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="brandAuthLetters" accept=".pdf,.jpg,.jpeg,.png" multiple>
                        <label for="brandAuthLetters" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Authorization Letters</div>
                            <div class="file-upload-hint">PDF, JPG, PNG (Max 5MB each)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="brandAuthLettersPreview"></div>
                </div>
                <div class="form-group">
                    <label class="form-label">Product Catalog (if available)</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="productCatalog" accept=".pdf,.jpg,.jpeg,.png">
                        <label for="productCatalog" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Product Catalog</div>
                            <div class="file-upload-hint">PDF, JPG, PNG (Max 10MB)</div>
                        </label>
                    </div>
                    <div class="file-preview" id="productCatalogPreview"></div>
                </div>
            </div>
        `;
    }

    function createVoiceSamplesSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-headphones"></i> Voice Samples</h3>
                <div class="form-group">
                    <label class="form-label required">Commercial Sample</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="commercialSample" accept=".mp3,.wav,.ogg" required>
                        <label for="commercialSample" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Commercial Sample</div>
                            <div class="file-upload-hint">MP3, WAV, OGG (Max 10MB)</div>
                        </label>
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Narration Sample</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="narrationSample" accept=".mp3,.wav,.ogg">
                        <label for="narrationSample" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Narration Sample</div>
                            <div class="file-upload-hint">MP3, WAV, OGG (Max 10MB)</div>
                        </label>
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Character Sample</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="characterSample" accept=".mp3,.wav,.ogg">
                        <label for="characterSample" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Character Sample</div>
                            <div class="file-upload-hint">MP3, WAV, OGG (Max 10MB)</div>
                        </label>
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Other Sample</label>
                    <div class="file-upload">
                        <input type="file" class="file-upload-input" id="otherSample" accept=".mp3,.wav,.ogg">
                        <label for="otherSample" class="file-upload-label">
                            <i class="fas fa-cloud-upload-alt"></i>
                            <div class="file-upload-text">Upload Other Sample</div>
                            <div class="file-upload-hint">MP3, WAV, OGG (Max 10MB)</div>
                        </label>
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Demo Reel Link (if available)</label>
                    <input type="url" class="form-control" name="demoReelLink" placeholder="e.g. https://soundcloud.com/yourdemo">
                </div>
            </div>
        `;
    }

    function createVoiceContactSection() {
        return `
            <div class="form-section">
                <h3 class="form-section-title"><i class="fas fa-id-card"></i> Contact Information</h3>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label required">Contact Name</label>
                        <input type="text" class="form-control" name="contactName" placeholder="Your name" required>
                    </div>
                    <div class="form-group">
                        <label class="form-label required">Contact Number</label>
                        <input type="tel" class="form-control" name="contactNumber" placeholder="10-digit mobile number" required>
                    </div>
                </div>
                <div class="form-row">
                    <div class="form-group">
                        <label class="form-label">Alternate Number</label>
                        <input type="tel" class="form-control" name="alternateNumber" placeholder="Alternate contact number">
                    </div>
                    <div class="form-group">
                        <label class="form-label required">Email</label>
                        <input type="email" class="form-control" name="email" placeholder="Your email address" required>
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Website (if any)</label>
                    <input type="url" class="form-control" name="website" placeholder="e.g. https://yourwebsite.com">
                </div>
                <div class="form-group">
                    <label class="form-label">Social Media Links</label>
                    <div class="form-row">
                        <div class="form-group">
                            <input type="url" class="form-control" name="facebook" placeholder="Facebook URL">
                        </div>
                        <div class="form-group">
                            <input type="url" class="form-control" name="instagram" placeholder="Instagram URL">
                        </div>
                    </div>
                    <div class="form-row">
                        <div class="form-group">
                            <input type="url" class="form-control" name="youtube" placeholder="YouTube URL">
                        </div>
                        <div class="form-group">
                            <input type="url" class="form-control" name="linkedin" placeholder="LinkedIn URL">
                        </div>
                    </div>
                </div>
                <div class="form-group">
                    <label class="form-label">Availability</label>
                    <div class="form-checkbox-group">
                        <label class="form-checkbox">
                            <input type="checkbox" name="availability" value="Weekdays"> Weekdays
                        </label>
                        <label class="form-checkbox">
                            <input type="checkbox" name="availability" value="Weekends"> Weekends
                        </label>
                        <label class="form-checkbox">
                            <input type="checkbox" name="availability" value="Evenings"> Evenings
                        </label>
                        <label class="form-checkbox">
                            <input type="checkbox" name="availability" value="Flexible"> Flexible
                        </label>
                    </div>
                </div>
            </div>
        `;
    }

    // Form navigation functions
    function showForm(formId) {
        hideForms();
        document.getElementById(formId).classList.add('active-form');
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function hideForms() {
        const forms = document.querySelectorAll('.form-container');
        forms.forEach(form => form.classList.remove('active-form'));
    }

    function nextTab(currentTab, formType) {
        const currentTabElement = document.querySelector(`#${formType}Form [data-tab="${currentTab}"]`);
        const nextTabElement = document.querySelector(`#${formType}Form [data-tab="${currentTab + 1}"]`);
        
        if (validateTab(currentTab, formType)) {
            currentTabElement.classList.remove('active');
            nextTabElement.classList.add('active');
            
            // Update steps
            document.querySelector(`#${formType}Form [data-step="${currentTab}"]`).classList.remove('active');
            document.querySelector(`#${formType}Form [data-step="${currentTab + 1}"]`).classList.add('active');
            
            // Update progress bar
            const progressPercentage = ((currentTab) / 3) * 100;
            document.querySelector(`#${formType}Form .form-steps-progress`).style.width = `${progressPercentage}%`;
            
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }
    }

    function prevTab(currentTab, formType) {
        const currentTabElement = document.querySelector(`#${formType}Form [data-tab="${currentTab}"]`);
        const prevTabElement = document.querySelector(`#${formType}Form [data-tab="${currentTab - 1}"]`);
        
        currentTabElement.classList.remove('active');
        prevTabElement.classList.add('active');
        
        // Update steps
        document.querySelector(`#${formType}Form [data-step="${currentTab}"]`).classList.remove('active');
        document.querySelector(`#${formType}Form [data-step="${currentTab - 1}"]`).classList.add('active');
        
        // Update progress bar
        const progressPercentage = ((currentTab - 2) / 3) * 100;
        document.querySelector(`#${formType}Form .form-steps-progress`).style.width = `${progressPercentage}%`;
        
        window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    function validateTab(tabNumber, formType) {
        let isValid = true;
        const form = document.querySelector(`#${formType}Form [data-tab="${tabNumber}"]`);
        const requiredFields = form.querySelectorAll('[required]');
        
        requiredFields.forEach(field => {
            if (!field.value.trim()) {
                field.classList.add('error');
                isValid = false;
                
                const feedback = document.createElement('div');
                feedback.className = 'form-feedback error';
                feedback.textContent = 'This field is required';
                
                if (field.nextElementSibling && !field.nextElementSibling.classList.contains('form-feedback')) {
                    field.parentNode.insertBefore(feedback, field.nextSibling);
                } else if (!field.nextElementSibling) {
                    field.parentNode.appendChild(feedback);
                }
            } else {
                field.classList.remove('error');
                if (field.nextElementSibling && field.nextElementSibling.classList.contains('form-feedback')) {
                    field.nextElementSibling.remove();
                }
            }
        });
        
        return isValid;
    }

    // Confirmation modal functions
    function showConfirmation() {
        document.getElementById('confirmationModal').classList.add('active');
    }

    function hideConfirmation() {
        document.getElementById('confirmationModal').classList.remove('active');
        hideForms();
    }

    // Initialize event listeners
    function initEventListeners() {
        // File upload previews
        document.addEventListener('change', function(e) {
            if (e.target.classList.contains('file-upload-input')) {
                const previewId = e.target.id + 'Preview';
                const previewContainer = document.getElementById(previewId);
                
                if (previewContainer) {
                    previewContainer.innerHTML = '';
                    
                    if (e.target.files) {
                        Array.from(e.target.files).forEach(file => {
                            if (file.type.startsWith('image/')) {
                                const reader = new FileReader();
                                reader.onload = function(event) {
                                    const previewItem = document.createElement('div');
                                    previewItem.className = 'file-preview-item';
                                    
                                    previewItem.innerHTML = `
                                        <img src="${event.target.result}" alt="${file.name}">
                                        <div class="file-preview-item-remove" onclick="removePreview('${previewId}', this)">
                                            <i class="fas fa-times"></i>
                                        </div>
                                    `;
                                    
                                    previewContainer.appendChild(previewItem);
                                };
                                reader.readAsDataURL(file);
                            } else {
                                const previewItem = document.createElement('div');
                                previewItem.className = 'file-preview-item';
                                previewItem.style.display = 'flex';
                                previewItem.style.flexDirection = 'column';
                                previewItem.style.alignItems = 'center';
                                previewItem.style.justifyContent = 'center';
                                previewItem.style.backgroundColor = 'rgba(255,255,255,0.1)';
                                
                                previewItem.innerHTML = `
                                    <i class="fas fa-file" style="font-size: 24px; margin-bottom: 5px;"></i>
                                    <div style="font-size: 10px; text-align: center; word-break: break-all;">${file.name}</div>
                                    <div class="file-preview-item-remove" onclick="removePreview('${previewId}', this)">
                                        <i class="fas fa-times"></i>
                                    </div>
                                `;
                                
                                previewContainer.appendChild(previewItem);
                            }
                        });
                    }
                }
            }
        });
        
            // Form submissions - modified to use mailto
            const forms = document.querySelectorAll('form[id$="FormData"]');
            forms.forEach(form => {
                form.addEventListener('submit', function(e) {
                    e.preventDefault();
                    
                    // Collect all form data
                    const formData = new FormData(form);
                    const formEntries = Object.fromEntries(formData.entries());
                    
                    // Format the email content
                    let emailBody = `New Listing Submission:\n\n`;
                    emailBody += `Listing Type: ${form.id.replace('FormData', '')}\n\n`;
                    
                    for (const [key, value] of Object.entries(formEntries)) {
                        if (value) {
                            emailBody += `${key}: ${value}\n`;
                        }
                    }
                    
                    // Create mailto link
                    const subject = `New ${form.id.replace('FormData', '')} Listing Submission`;
                    const mailtoLink = `mailto:nysaworldofficial@gmail.com?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(emailBody)}`;
                    
                    // Open email client
                    window.location.href = mailtoLink;
                    
                    // Show confirmation after a delay to allow email client to open
                    setTimeout(showConfirmation, 1000);
                });
            });
            
            // Menu button (previous code remains the same)
            document.getElementById('menuButton').addEventListener('click', function() {
                alert('Menu functionality will be added here');
            });
        }

    // Remove file preview
    function removePreview(previewId, element) {
        const previewContainer = document.getElementById(previewId);
        const previewItem = element.closest('.file-preview-item');
        previewContainer.removeChild(previewItem);
    }
</script>
</body>
 </html>
