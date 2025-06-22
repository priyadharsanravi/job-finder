# job-finder
I'll create a comprehensive part-time job finding application using HTML, CSS, and JavaScript. Since you mentioned Replit, I'll design this as a single HTML file that can be easily run on Replit's web environment. I'll include modern UI elements, job listings functionality, and search features.

Here's the complete application:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JobHunt - Find Your Perfect Part-Time Job</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #4f46e5;
            --secondary: #10b981;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f9fafb;
        }
        
        .job-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1);
        }
        
        .pulse {
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% {
                box-shadow: 0 0 0 0 rgba(79, 70, 229, 0.7);
            }
            70% {
                box-shadow: 0 0 0 10px rgba(79, 70, 229, 0);
            }
            100% {
                box-shadow: 0 0 0 0 rgba(79, 70, 229, 0);
            }
        }
        
        .category-chip {
            transition: all 0.3s ease;
        }
        
        .category-chip:hover {
            background-color: var(--primary);
            color: white;
        }
        
        .search-container {
            background: linear-gradient(135deg, #4f46e5 0%, #10b981 100%);
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="bg-white shadow-lg">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16">
                <div class="flex items-center">
                    <div class="flex-shrink-0 flex items-center">
                        <i class="fas fa-briefcase text-indigo-600 text-2xl mr-2"></i>
                        <span class="text-xl font-bold text-gray-900">JobHunt</span>
                    </div>
                    <div class="hidden sm:ml-6 sm:flex sm:space-x-8">
                        <a href="#" class="border-indigo-500 text-gray-900 inline-flex items-center px-1 pt-1 border-b-2 text-sm font-medium">Home</a>
                        <a href="#" class="border-transparent text-gray-500 hover:border-gray-300 hover:text-gray-700 inline-flex items-center px-1 pt-1 border-b-2 text-sm font-medium">Jobs</a>
                        <a href="#" class="border-transparent text-gray-500 hover:border-gray-300 hover:text-gray-700 inline-flex items-center px-1 pt-1 border-b-2 text-sm font-medium">Companies</a>
                        <a href="#" class="border-transparent text-gray-500 hover:border-gray-300 hover:text-gray-700 inline-flex items-center px-1 pt-1 border-b-2 text-sm font-medium">Blog</a>
                    </div>
                </div>
                <div class="hidden sm:ml-6 sm:flex sm:items-center">
                    <button class="bg-indigo-600 hover:bg-indigo-700 text-white px-4 py-2 rounded-md text-sm font-medium">Post a Job</button>
                    <button class="ml-4 bg-gray-100 hover:bg-gray-200 text-gray-800 px-4 py-2 rounded-md text-sm font-medium">Sign In</button>
                </div>
                <div class="-mr-2 flex items-center sm:hidden">
                    <button type="button" class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-gray-500 hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-500" aria-controls="mobile-menu" aria-expanded="false">
                        <span class="sr-only">Open main menu</span>
                        <i class="fas fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <div class="search-container relative py-16 px-4 sm:px-6 lg:px-8 text-white">
        <div class="max-w-3xl mx-auto text-center">
            <h1 class="text-4xl font-extrabold tracking-tight sm:text-5xl lg:text-6xl">Find Your Perfect Part-Time Job</h1>
            <p class="mt-6 text-xl">Browse thousands of part-time job listings and find the one that fits your schedule and skills.</p>
            
            <div class="mt-10 bg-white rounded-lg shadow-xl p-4 max-w-2xl mx-auto">
                <div class="flex flex-col sm:flex-row gap-2">
                    <div class="flex-1 relative">
                        <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                            <i class="fas fa-search text-gray-400"></i>
                        </div>
                        <input type="text" id="search-input" class="block w-full pl-10 pr-3 py-3 border border-gray-300 rounded-md leading-5 bg-white placeholder-gray-500 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" placeholder="Job title, keywords, or company">
                    </div>
                    <div class="flex-1 relative">
                        <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                            <i class="fas fa-map-marker-alt text-gray-400"></i>
                        </div>
                        <input type="text" id="location-input" class="block w-full pl-10 pr-3 py-3 border border-gray-300 rounded-md leading-5 bg-white placeholder-gray-500 focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" placeholder="City, state, or remote">
                    </div>
                    <button id="search-button" class="px-6 py-3 bg-indigo-600 hover:bg-indigo-700 text-white font-medium rounded-md transition duration-150 ease-in-out transform hover:scale-105">
                        Search Jobs
                    </button>
                </div>
            </div>
            
            <div class="mt-8 flex flex-wrap justify-center gap-2">
                <span class="text-sm font-medium">Popular searches:</span>
                <button class="text-sm bg-white bg-opacity-20 hover:bg-opacity-30 px-3 py-1 rounded-full">Remote</button>
                <button class="text-sm bg-white bg-opacity-20 hover:bg-opacity-30 px-3 py-1 rounded-full">Customer Service</button>
                <button class="text-sm bg-white bg-opacity-20 hover:bg-opacity-30 px-3 py-1 rounded-full">Retail</button>
                <button class="text-sm bg-white bg-opacity-20 hover:bg-opacity-30 px-3 py-1 rounded-full">Delivery</button>
            </div>
        </div>
    </div>

    <!-- Categories Section -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
        <h2 class="text-2xl font-bold text-gray-900 mb-6">Browse by Category</h2>
        <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-6 gap-4">
            <button class="category-chip flex flex-col items-center justify-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md border border-gray-100">
                <i class="fas fa-laptop-code text-2xl text-indigo-600 mb-2"></i>
                <span class="text-sm font-medium">Tech</span>
            </button>
            <button class="category-chip flex flex-col items-center justify-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md border border-gray-100">
                <i class="fas fa-store text-2xl text-indigo-600 mb-2"></i>
                <span class="text-sm font-medium">Retail</span>
            </button>
            <button class="category-chip flex flex-col items-center justify-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md border border-gray-100">
                <i class="fas fa-utensils text-2xl text-indigo-600 mb-2"></i>
                <span class="text-sm font-medium">Food</span>
            </button>
            <button class="category-chip flex flex-col items-center justify-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md border border-gray-100">
                <i class="fas fa-headset text-2xl text-indigo-600 mb-2"></i>
                <span class="text-sm font-medium">Customer Service</span>
            </button>
            <button class="category-chip flex flex-col items-center justify-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md border border-gray-100">
                <i class="fas fa-truck text-2xl text-indigo-600 mb-2"></i>
                <span class="text-sm font-medium">Delivery</span>
            </button>
            <button class="category-chip flex flex-col items-center justify-center p-4 bg-white rounded-lg shadow-sm hover:shadow-md border border-gray-100">
                <i class="fas fa-chalkboard-teacher text-2xl text-indigo-600 mb-2"></i>
                <span class="text-sm font-medium">Tutoring</span>
            </button>
        </div>
    </div>

    <!-- Featured Jobs Section -->
    <div class="bg-gray-50 py-12">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center mb-6">
                <h2 class="text-2xl font-bold text-gray-900">Featured Part-Time Jobs</h2>
                <a href="#" class="text-indigo-600 hover:text-indigo-800 font-medium">View all jobs <i class="fas fa-arrow-right ml-1"></i></a>
            </div>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6" id="job-listings">
                <!-- Job cards will be populated by JavaScript -->
            </div>
        </div>
    </div>

    <!-- How It Works Section -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
        <h2 class="text-2xl font-bold text-center text-gray-900 mb-12">How JobHunt Works</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div class="text-center">
                <div class="mx-auto flex items-center justify-center h-12 w-12 rounded-full bg-indigo-100 text-indigo-600 mb-4">
                    <i class="fas fa-user-edit text-xl"></i>
                </div>
                <h3 class="text-lg font-medium text-gray-900 mb-2">1. Create Your Profile</h3>
                <p class="text-gray-500">Tell us about your skills, availability, and job preferences.</p>
            </div>
            <div class="text-center">
                <div class="mx-auto flex items-center justify-center h-12 w-12 rounded-full bg-indigo-100 text-indigo-600 mb-4">
                    <i class="fas fa-search text-xl"></i>
                </div>
                <h3 class="text-lg font-medium text-gray-900 mb-2">2. Find Matching Jobs</h3>
                <p class="text-gray-500">Browse part-time jobs that fit your schedule and skills.</p>
            </div>
            <div class="text-center">
                <div class="mx-auto flex items-center justify-center h-12 w-12 rounded-full bg-indigo-100 text-indigo-600 mb-4">
                    <i class="fas fa-paper-plane text-xl"></i>
                </div>
                <h3 class="text-lg font-medium text-gray-900 mb-2">3. Apply in One Click</h3>
                <p class="text-gray-500">Submit your application quickly with our streamlined process.</p>
            </div>
        </div>
    </div>

    <!-- Testimonials -->
    <div class="bg-indigo-50 py-16">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <h2 class="text-2xl font-bold text-center text-gray-900 mb-12">What Our Users Say</h2>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="bg-white p-6 rounded-lg shadow-sm">
                    <div class="flex items-center mb-4">
                        <img class="h-10 w-10 rounded-full" src="https://randomuser.me/api/portraits/women/32.jpg" alt="">
                        <div class="ml-3">
                            <h4 class="text-sm font-medium text-gray-900">Sarah Johnson</h4>
                            <div class="flex text-yellow-400">
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                            </div>
                        </div>
                    </div>
                    <p class="text-gray-600">"Found the perfect weekend job at a local cafe through JobHunt. The application process was so easy!"</p>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-sm">
                    <div class="flex items-center mb-4">
                        <img class="h-10 w-10 rounded-full" src="https://randomuser.me/api/portraits/men/45.jpg" alt="">
                        <div class="ml-3">
                            <h4 class="text-sm font-medium text-gray-900">Michael Chen</h4>
                            <div class="flex text-yellow-400">
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star-half-alt"></i>
                            </div>
                        </div>
                    </div>
                    <p class="text-gray-600">"As a student, JobHunt helped me find flexible remote work that fits around my classes."</p>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-sm">
                    <div class="flex items-center mb-4">
                        <img class="h-10 w-10 rounded-full" src="https://randomuser.me/api/portraits/women/68.jpg" alt="">
                        <div class="ml-3">
                            <h4 class="text-sm font-medium text-gray-900">Emma Rodriguez</h4>
                            <div class="flex text-yellow-400">
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                            </div>
                        </div>
                    </div>
                    <p class="text-gray-600">"I love the variety of part-time jobs available. Found a great tutoring position within a week!"</p>
                </div>
            </div>
        </div>
    </div>

    <!-- Call to Action -->
    <div class="bg-indigo-700">
        <div class="max-w-2xl mx-auto text-center py-16 px-4 sm:py-20 sm:px-6 lg:px-8">
            <h2 class="text-3xl font-extrabold text-white sm:text-4xl">
                <span class="block">Ready to find your perfect part-time job?</span>
                <span class="block">Create your free account today.</span>
            </h2>
            <div class="mt-8 flex justify-center">
                <div class="inline-flex rounded-md shadow">
                    <a href="#" class="inline-flex items-center justify-center px-5 py-3 border border-transparent text-base font-medium rounded-md text-indigo-600 bg-white hover:bg-indigo-50">
                        Get Started
                    </a>
                </div>
                <div class="ml-3 inline-flex">
                    <a href="#" class="inline-flex items-center justify-center px-5 py-3 border border-transparent text-base font-medium rounded-md text-indigo-200 bg-indigo-600 hover:bg-indigo-500">
                        Learn more
                    </a>
                </div>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="bg-white">
        <div class="max-w-7xl mx-auto py-12 px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-2 md:grid-cols-4 gap-8">
                <div>
                    <h3 class="text-sm font-semibold text-gray-900 tracking-wider uppercase">For Job Seekers</h3>
                    <ul class="mt-4 space-y-2">
                        <li><a href="#" class="text-sm text-gray-600 hover:text-gray-900">Browse Jobs</a></li>
                        <li><a href="#" class="text-sm text-gray-600 hover:text-gray-900">Create Profile</a></li>
                        <li><a href="#"
