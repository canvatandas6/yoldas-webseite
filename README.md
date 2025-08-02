<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RafIQ Agency - Personal Branding & Organisches Wachstum</title>
    <script src="https://cdn.tailwindcss.com"></script>

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#8b5cf6',
                        secondary: '#7c3aed',
                        accent: '#06d6a0',
                        dark: '#0f0f23',
                        darker: '#0a0a1a',
                        light: '#1a1a2e',
                        lighter: '#16213e'
                    }
                }
            }
        }
    </script>
    <style>
        .gradient-bg {
            background: linear-gradient(135deg, #8b5cf6 0%, #7c3aed 100%);
        }
        .text-gradient {
            background: linear-gradient(135deg, #8b5cf6, #06d6a0);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        /* Glow Effects */
        .glow-primary {
            box-shadow: 0 0 20px rgba(139, 92, 246, 0.3);
        }
        .glow-accent {
            box-shadow: 0 0 20px rgba(6, 214, 160, 0.3);
        }
        .glow-hover:hover {
            box-shadow: 0 0 30px rgba(139, 92, 246, 0.5);
            transform: translateY(-2px);
        }
        .glow-button {
            box-shadow: 0 0 15px rgba(139, 92, 246, 0.4);
            transition: all 0.3s ease;
        }
        .glow-button:hover {
            box-shadow: 0 0 25px rgba(139, 92, 246, 0.6);
            transform: scale(1.05);
        }
        
        /* Floating Animation */
        .floating {
            animation: floating 3s ease-in-out infinite;
        }
        @keyframes floating {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
        
        /* Pulse Animation */
        .pulse-glow {
            animation: pulseGlow 2s ease-in-out infinite;
        }
        @keyframes pulseGlow {
            0%, 100% { box-shadow: 0 0 20px rgba(139, 92, 246, 0.3); }
            50% { box-shadow: 0 0 40px rgba(139, 92, 246, 0.6); }
        }
        
        /* Interactive Hover Effects */
        .hover-scale {
            transition: all 0.3s ease;
        }
        .hover-scale:hover {
            transform: scale(1.05) translateY(-5px);
            box-shadow: 0 10px 30px rgba(139, 92, 246, 0.3);
        }
        
        .hover-glow:hover {
            box-shadow: 0 0 30px rgba(6, 214, 160, 0.5);
            border-color: #06d6a0;
        }
        
        /* Success Animation */
        .success-animation {
            animation: successPulse 0.6s ease-out;
        }
        @keyframes successPulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); box-shadow: 0 0 30px rgba(6, 214, 160, 0.6); }
            100% { transform: scale(1); }
        }
        
        /* Quiz Completion Animation */
        .quiz-completion {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.9);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 2000;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
        }
        .quiz-completion.active {
            opacity: 1;
            visibility: visible;
        }
        .completion-content {
            text-align: center;
            color: white;
            transform: scale(0.8);
            transition: transform 0.3s ease;
        }
        .quiz-completion.active .completion-content {
            transform: scale(1);
        }
        .checkmark-circle {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            background: linear-gradient(135deg, #06d6a0, #04a777);
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 2rem;
            animation: checkmarkPop 0.6s ease-out 0.3s both;
        }
        @keyframes checkmarkPop {
            0% { transform: scale(0); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }
        .checkmark {
            width: 60px;
            height: 60px;
            stroke: white;
            stroke-width: 4;
            fill: none;
            stroke-linecap: round;
            stroke-linejoin: round;
            animation: checkmarkDraw 0.8s ease-out 0.6s both;
        }
        .checkmark path {
            stroke-dasharray: 100;
            stroke-dashoffset: 100;
            animation: checkmarkDraw 0.8s ease-out 0.6s both;
        }
        @keyframes checkmarkDraw {
            0% { 
                stroke-dashoffset: 100;
                opacity: 0;
            }
            50% {
                opacity: 1;
            }
            100% { 
                stroke-dashoffset: 0;
                opacity: 1;
            }
        }
        
        /* Calendar Styles */
        .calendar-container {
            background: #1a1a2e;
            border-radius: 1rem;
            padding: 1.5rem;
            border: 1px solid rgba(139, 92, 246, 0.3);
        }
        .calendar-header {
            display: flex;
            justify-content: between;
            align-items: center;
            margin-bottom: 1rem;
        }
        .calendar-grid {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 0.5rem;
            margin-bottom: 1rem;
        }
        .calendar-day {
            aspect-ratio: 1;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 0.5rem;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.9rem;
        }
        .calendar-day.header {
            font-weight: bold;
            color: #8b5cf6;
            cursor: default;
        }
        .calendar-day.available {
            background: rgba(139, 92, 246, 0.1);
            color: white;
            border: 1px solid rgba(139, 92, 246, 0.3);
        }
        .calendar-day.available:hover {
            background: rgba(139, 92, 246, 0.2);
            border-color: #8b5cf6;
        }
        .calendar-day.selected {
            background: #06d6a0;
            color: #0a0a1a;
            border-color: #06d6a0;
        }
        .calendar-day.unavailable {
            color: #666;
            cursor: not-allowed;
        }
        .time-slots {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
            gap: 0.5rem;
            margin-top: 1rem;
        }
        .time-slot {
            padding: 0.5rem;
            background: rgba(139, 92, 246, 0.1);
            border: 1px solid rgba(139, 92, 246, 0.3);
            border-radius: 0.5rem;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            color: white;
        }
        .time-slot:hover {
            background: rgba(139, 92, 246, 0.2);
            border-color: #8b5cf6;
        }
        .time-slot.selected {
            background: #06d6a0;
            color: #0a0a1a;
            border-color: #06d6a0;
        }
        
        /* Fade In Animation */
        .fade-in {
            opacity: 0;
            transform: translateY(20px);
            animation: fadeIn 0.6s ease forwards;
        }
        @keyframes fadeIn {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        /* Quiz Styles */
        .quiz-container {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            border: 1px solid rgba(139, 92, 246, 0.3);
        }
        
        .quiz-option, .quiz-option-multi {
            transition: all 0.3s ease;
            border: 2px solid transparent;
        }
        .quiz-option:hover, .quiz-option-multi:hover {
            border-color: #8b5cf6;
            box-shadow: 0 0 15px rgba(139, 92, 246, 0.3);
            transform: translateX(5px);
        }
        .quiz-option.selected, .quiz-option-multi.selected {
            border-color: #06d6a0;
            background: rgba(6, 214, 160, 0.1);
            box-shadow: 0 0 20px rgba(6, 214, 160, 0.3);
        }
        
        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.7);
            backdrop-filter: blur(5px);
        }
        .modal.active {
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .modal-content {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            color: white;
            padding: 2rem;
            border-radius: 1rem;
            max-width: 90%;
            max-height: 90%;
            overflow-y: auto;
            border: 1px solid rgba(139, 92, 246, 0.3);
            box-shadow: 0 0 40px rgba(139, 92, 246, 0.3);
        }
        
        /* Tab Styles */
        .tab-button {
            transition: all 0.3s ease;
            border-bottom: 2px solid transparent;
        }
        .tab-button.active {
            border-bottom-color: #06d6a0;
            color: #06d6a0;
            box-shadow: 0 0 15px rgba(6, 214, 160, 0.3);
        }
        .tab-button:hover {
            color: #8b5cf6;
            transform: translateY(-2px);
        }
        
        /* Contact Tab Styles */
        .contact-tab-button {
            color: #9ca3af;
        }
        .contact-tab-button.active {
            background: rgba(139, 92, 246, 0.2);
            color: #06d6a0;
            border: 1px solid rgba(6, 214, 160, 0.3);
        }
        .contact-tab-button:hover:not(.active) {
            color: #8b5cf6;
            background: rgba(139, 92, 246, 0.1);
        }
        
        /* Progress Bar */
        .progress-bar {
            background: linear-gradient(90deg, #8b5cf6, #06d6a0);
            box-shadow: 0 0 10px rgba(139, 92, 246, 0.5);
            transition: width 0.5s ease;
        }
    </style>
</head>
<body class="bg-dark text-white">
    <!-- Navigation -->
    <nav class="bg-light shadow-lg fixed w-full top-0 z-50 border-b border-lighter glow-primary">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-16">
                <div class="flex items-center">
                    <div class="flex-shrink-0 h-8 w-32">
                        <!-- OPTION 1: SVG Logo (Empfohlen) - Ersetze den gesamten <div> unten mit deinem SVG -->
                        <!-- <svg class="h-8 w-auto" viewBox="0 0 200 50" fill="none" xmlns="http://www.w3.org/2000/svg">
                             Hier dein SVG-Code einfügen
                        </svg> -->
                        
                        <!-- OPTION 2: PNG/JPG Logo - Ersetze den <div> unten mit diesem <img> Tag -->
                        <!-- <img src="dein-logo.png" alt="RafIQ Agency Logo" class="h-8 w-auto"> -->
                        
                        <!-- OPTION 3: Base64 Logo - Ersetze den <div> unten -->
                        <!-- <img src="data:image/png;base64,DEIN_BASE64_CODE_HIER" alt="RafIQ Agency Logo" class="h-8 w-auto"> -->
                        
                        <!-- TEMPORÄRER PLATZHALTER - Lösche diese Zeilen wenn du dein Logo einfügst -->
                        <div class="h-8 w-32 bg-primary rounded flex items-center justify-center glow-button">
                            <span class="text-white font-bold text-lg">RafIQ Agency</span>
                        </div>
                    </div>
                </div>
                <div class="hidden md:block">
                    <div class="ml-10 flex items-baseline space-x-8">
                        <a href="#home" class="text-white hover:text-primary transition-all duration-300 hover:scale-110">Home</a>
                        <a href="#services" class="text-white hover:text-primary transition-all duration-300 hover:scale-110">Services</a>
                        <a href="#about" class="text-white hover:text-primary transition-all duration-300 hover:scale-110">Über uns</a>
                        <a href="#contact" class="text-white hover:text-primary transition-all duration-300 hover:scale-110">Kontakt</a>
                        <button onclick="openModal('consultation')" class="bg-accent text-dark px-6 py-2 rounded-full glow-button">Kostenloses Erstgespräch</button>
                    </div>
                </div>
                <div class="md:hidden">
                    <button onclick="toggleMobileMenu()" class="text-white hover:text-primary">
                        <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
                        </svg>
                    </button>
                </div>
            </div>
        </div>
        <!-- Mobile menu -->
        <div id="mobile-menu" class="md:hidden hidden bg-light border-t border-lighter">
            <div class="px-2 pt-2 pb-3 space-y-1">
                <a href="#home" class="block px-3 py-2 text-white hover:text-primary">Home</a>
                <a href="#services" class="block px-3 py-2 text-white hover:text-primary">Services</a>
                <a href="#about" class="block px-3 py-2 text-white hover:text-primary">Über uns</a>
                <a href="#contact" class="block px-3 py-2 text-white hover:text-primary">Kontakt</a>
                <button onclick="openModal('consultation')" class="block w-full text-left px-3 py-2 bg-accent text-dark rounded">Kostenloses Erstgespräch</button>
            </div>
        </div>
    </nav>

    <!-- Hero Section with Tabs -->
    <section id="home" class="gradient-bg text-white pt-20 pb-16">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <!-- Tab Navigation -->
            <div class="flex justify-center mb-8">
                <div class="bg-light rounded-full p-1 glow-primary">
                    <button onclick="switchTab('hero')" id="hero-tab" class="tab-button active px-6 py-3 rounded-full font-semibold">Willkommen</button>
                    <button onclick="switchTab('quiz')" id="quiz-tab" class="tab-button px-6 py-3 rounded-full font-semibold">Bedarfs-Quiz</button>
                </div>
            </div>
            
            <!-- Hero Content -->
            <div id="hero-content" class="text-center fade-in">
                <h1 class="text-4xl md:text-6xl font-bold mb-6 floating">
                    Baue deine <span class="text-accent pulse-glow">Personal Brand</span><br>
                    mit organischem Content
                </h1>
                <p class="text-xl md:text-2xl mb-8 max-w-3xl mx-auto opacity-90">
                    Wir helfen dir dabei, eine authentische Personal Brand aufzubauen und durch strategischen, organischen Content nachhaltiges Wachstum zu erzielen.
                </p>
                <div class="flex flex-col sm:flex-row gap-4 justify-center">
                    <button onclick="switchTab('quiz')" class="bg-accent text-dark px-8 py-4 rounded-full text-lg font-semibold glow-button">
                        Kostenloses Bedarfs-Quiz starten
                    </button>
                    <button onclick="openModal('consultation')" class="bg-primary text-white px-8 py-4 rounded-full text-lg font-semibold glow-button">
                        Direktes Erstgespräch buchen
                    </button>
                    <a href="#services" class="border-2 border-white text-white px-8 py-4 rounded-full text-lg font-semibold hover:bg-white hover:text-primary transition-all duration-300 hover-glow">
                        Unsere Services
                    </a>
                </div>
            </div>
            
            <!-- Quiz Content -->
            <div id="quiz-content" class="hidden">
                <div class="max-w-4xl mx-auto">
                    <div class="quiz-container rounded-2xl p-8 glow-primary">
                        <div class="text-center mb-8">
                            <h2 class="text-3xl font-bold mb-4">🎯 Personal Brand Bedarfs-Quiz</h2>
                            <p class="text-gray-300 mb-6">Finde heraus, welche Strategie perfekt für dich ist! Beantworte 8 kurze Fragen und erhalte eine maßgeschneiderte Empfehlung.</p>
                            
                            <!-- Progress Bar -->
                            <div class="w-full bg-gray-700 rounded-full h-3 mb-6">
                                <div id="progress-bar" class="progress-bar h-3 rounded-full" style="width: 12.5%"></div>
                            </div>
                            <p class="text-sm text-gray-400">Frage <span id="current-question">1</span> von 8</p>
                        </div>
                        
                        <!-- Quiz Questions -->
                        <div id="quiz-questions">
                            <!-- Question 1 -->
                            <div class="quiz-question active" data-question="1">
                                <h3 class="text-xl font-semibold mb-6">In welcher Branche bist du tätig?</h3>
                                <div class="grid md:grid-cols-2 gap-4">
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="tech">
                                        <div class="font-semibold">💻 Tech & IT</div>
                                        <div class="text-sm text-gray-400">Software, Development, IT-Services</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="business">
                                        <div class="font-semibold">💼 Business & Consulting</div>
                                        <div class="text-sm text-gray-400">Beratung, Coaching, Unternehmensführung</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="creative">
                                        <div class="font-semibold">🎨 Kreativ & Design</div>
                                        <div class="text-sm text-gray-400">Design, Marketing, Content Creation</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="health">
                                        <div class="font-semibold">🏥 Gesundheit & Wellness</div>
                                        <div class="text-sm text-gray-400">Medizin, Fitness, Ernährung</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="finance">
                                        <div class="font-semibold">💰 Finanzen & Investment</div>
                                        <div class="text-sm text-gray-400">Banking, Investment, Versicherung</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="gastronomy">
                                        <div class="font-semibold">🍽️ Gastronomie & Food</div>
                                        <div class="text-sm text-gray-400">Restaurant, Catering, Food-Business</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="other">
                                        <div class="font-semibold">🌟 Andere Branche</div>
                                        <div class="text-sm text-gray-400">Sonstige Bereiche</div>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- Question 2 -->
                            <div class="quiz-question hidden" data-question="2">
                                <h3 class="text-xl font-semibold mb-6">Wie würdest du deine aktuelle Online-Präsenz bewerten?</h3>
                                <div class="space-y-4">
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="none">
                                        <div class="font-semibold">🚀 Ich fange gerade erst an</div>
                                        <div class="text-sm text-gray-400">Wenig bis keine Online-Präsenz</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="basic">
                                        <div class="font-semibold">📱 Grundlagen sind da</div>
                                        <div class="text-sm text-gray-400">Profile vorhanden, aber wenig aktiv</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="active">
                                        <div class="font-semibold">💪 Bereits aktiv</div>
                                        <div class="text-sm text-gray-400">Regelmäßige Posts, aber wenig Strategie</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="advanced">
                                        <div class="font-semibold">🎯 Strategisch unterwegs</div>
                                        <div class="text-sm text-gray-400">Klare Strategie, aber Optimierung gewünscht</div>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- Question 3 -->
                            <div class="quiz-question hidden" data-question="3">
                                <h3 class="text-xl font-semibold mb-6">Welche Plattformen sind für dich am wichtigsten? <span class="text-sm text-accent">(Mehrfachauswahl möglich)</span></h3>
                                <div class="grid md:grid-cols-2 gap-4">
                                    <div class="quiz-option-multi p-4 rounded-lg bg-lighter cursor-pointer" data-value="linkedin">
                                        <div class="font-semibold">💼 LinkedIn</div>
                                        <div class="text-sm text-gray-400">Professional Networking</div>
                                    </div>
                                    <div class="quiz-option-multi p-4 rounded-lg bg-lighter cursor-pointer" data-value="instagram">
                                        <div class="font-semibold">📸 Instagram</div>
                                        <div class="text-sm text-gray-400">Visual Content & Stories</div>
                                    </div>
                                    <div class="quiz-option-multi p-4 rounded-lg bg-lighter cursor-pointer" data-value="youtube">
                                        <div class="font-semibold">🎥 YouTube</div>
                                        <div class="text-sm text-gray-400">Video Content & Tutorials</div>
                                    </div>
                                    <div class="quiz-option-multi p-4 rounded-lg bg-lighter cursor-pointer" data-value="twitter">
                                        <div class="font-semibold">🐦 Twitter/X</div>
                                        <div class="text-sm text-gray-400">News & Quick Updates</div>
                                    </div>
                                    <div class="quiz-option-multi p-4 rounded-lg bg-lighter cursor-pointer" data-value="tiktok">
                                        <div class="font-semibold">🎵 TikTok</div>
                                        <div class="text-sm text-gray-400">Short-Form Video Content</div>
                                    </div>
                                    <div class="quiz-option-multi p-4 rounded-lg bg-lighter cursor-pointer" data-value="facebook">
                                        <div class="font-semibold">📘 Facebook</div>
                                        <div class="text-sm text-gray-400">Community Building & Events</div>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- Question 4 -->
                            <div class="quiz-question hidden" data-question="4">
                                <h3 class="text-xl font-semibold mb-6">Wie viel Zeit kannst du wöchentlich für Content investieren?</h3>
                                <div class="space-y-4">
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="minimal">
                                        <div class="font-semibold">⏰ 1-2 Stunden</div>
                                        <div class="text-sm text-gray-400">Wenig Zeit, maximale Effizienz gewünscht</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="moderate">
                                        <div class="font-semibold">📅 3-5 Stunden</div>
                                        <div class="text-sm text-gray-400">Regelmäßige Content-Erstellung möglich</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="extensive">
                                        <div class="font-semibold">💪 6-10 Stunden</div>
                                        <div class="text-sm text-gray-400">Content ist hohe Priorität</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="fulltime">
                                        <div class="font-semibold">🚀 10+ Stunden</div>
                                        <div class="text-sm text-gray-400">Personal Branding ist Vollzeit-Fokus</div>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- Question 5 -->
                            <div class="quiz-question hidden" data-question="5">
                                <h3 class="text-xl font-semibold mb-6">Was ist dein Hauptziel mit Personal Branding?</h3>
                                <div class="space-y-4">
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="leads">
                                        <div class="font-semibold">🎯 Mehr Kunden gewinnen</div>
                                        <div class="text-sm text-gray-400">Lead-Generierung und Kundenakquise</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="authority">
                                        <div class="font-semibold">👑 Thought Leadership</div>
                                        <div class="text-sm text-gray-400">Als Experte wahrgenommen werden</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="network">
                                        <div class="font-semibold">🤝 Netzwerk aufbauen</div>
                                        <div class="text-sm text-gray-400">Connections und Partnerschaften</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="career">
                                        <div class="font-semibold">📈 Karriere vorantreiben</div>
                                        <div class="text-sm text-gray-400">Bessere Job-Opportunities</div>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- Question 6 -->
                            <div class="quiz-question hidden" data-question="6">
                                <h3 class="text-xl font-semibold mb-6">Welcher Content-Typ liegt dir am meisten?</h3>
                                <div class="grid md:grid-cols-2 gap-4">
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="writing">
                                        <div class="font-semibold">✍️ Schreiben</div>
                                        <div class="text-sm text-gray-400">Blog-Posts, LinkedIn-Artikel</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="video">
                                        <div class="font-semibold">🎥 Video</div>
                                        <div class="text-sm text-gray-400">YouTube, Reels, Stories</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="visual">
                                        <div class="font-semibold">🎨 Visueller Content</div>
                                        <div class="text-sm text-gray-400">Infografiken, Designs</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="mixed">
                                        <div class="font-semibold">🌈 Mix aus allem</div>
                                        <div class="text-sm text-gray-400">Verschiedene Content-Formate</div>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- Question 7 -->
                            <div class="quiz-question hidden" data-question="7">
                                <h3 class="text-xl font-semibold mb-6">Wie ist dein Budget für Personal Branding?</h3>
                                <div class="space-y-4">
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="starter">
                                        <div class="font-semibold">🌱 Starter (400-600€/Monat)</div>
                                        <div class="text-sm text-gray-400">Grundlagen und erste Schritte</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="growth">
                                        <div class="font-semibold">📈 Growth (600-1.200€/Monat)</div>
                                        <div class="text-sm text-gray-400">Strategische Entwicklung</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="enterprise">
                                        <div class="font-semibold">🚀 Enterprise (1.200€+/Monat)</div>
                                        <div class="text-sm text-gray-400">Maßgeschneiderte Premium-Lösungen</div>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- Question 8 -->
                            <div class="quiz-question hidden" data-question="8">
                                <h3 class="text-xl font-semibold mb-6">Wann möchtest du starten?</h3>
                                <div class="space-y-4">
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="immediately">
                                        <div class="font-semibold">🚀 Sofort</div>
                                        <div class="text-sm text-gray-400">Ich bin bereit loszulegen</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="soon">
                                        <div class="font-semibold">📅 In den nächsten 2-4 Wochen</div>
                                        <div class="text-sm text-gray-400">Kurze Vorbereitungszeit</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="planning">
                                        <div class="font-semibold">🤔 In 1-3 Monaten</div>
                                        <div class="text-sm text-gray-400">Noch in der Planungsphase</div>
                                    </div>
                                    <div class="quiz-option p-4 rounded-lg bg-lighter cursor-pointer" data-value="exploring">
                                        <div class="font-semibold">👀 Nur am Erkunden</div>
                                        <div class="text-sm text-gray-400">Sammle erstmal Informationen</div>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- Contact Form -->
                            <div id="quiz-contact" class="hidden">
                                <h3 class="text-xl font-semibold mb-6">Fast geschafft! Deine Kontaktdaten für die Auswertung:</h3>
                                
                                <!-- Tab Navigation -->
                                <div class="flex mb-6 bg-dark rounded-lg p-1">
                                    <button onclick="switchContactTab('contact')" id="contact-tab" class="contact-tab-button active flex-1 py-3 px-4 rounded-md font-semibold transition-all duration-300">
                                        📝 Kontaktdaten
                                    </button>
                                    <button onclick="switchContactTab('appointment')" id="appointment-tab" class="contact-tab-button flex-1 py-3 px-4 rounded-md font-semibold transition-all duration-300">
                                        📅 Erstgespräch (optional)
                                    </button>
                                </div>
                                
                                <form id="quiz-form" action="https://formspree.io/f/mvgqklog" method="POST" class="space-y-4">
                                    <!-- Hidden Quiz Answers (will be populated by JavaScript) -->
                                    <input type="hidden" name="quiz_branche" id="hidden-question1">
                                    <input type="hidden" name="quiz_online_presence" id="hidden-question2">
                                    <input type="hidden" name="quiz_platforms" id="hidden-question3">
                                    <input type="hidden" name="quiz_time_available" id="hidden-question4">
                                    <input type="hidden" name="quiz_main_goal" id="hidden-question5">
                                    <input type="hidden" name="quiz_content_type" id="hidden-question6">
                                    <input type="hidden" name="quiz_budget" id="hidden-question7">
                                    <input type="hidden" name="quiz_start_time" id="hidden-question8">
                                    <input type="hidden" name="submission_type" value="Personal Brand Quiz">
                                    <input type="hidden" name="quiz_summary" id="hidden-quiz-summary">
                                    
                                    <!-- Contact Data Tab -->
                                    <div id="contact-data" class="space-y-4">
                                        <div class="grid md:grid-cols-2 gap-4">
                                            <div>
                                                <label class="block text-sm font-medium text-gray-300 mb-2">Vorname *</label>
                                                <input type="text" name="firstName" required class="w-full px-4 py-3 bg-dark border border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent text-white hover-glow">
                                            </div>
                                            <div>
                                                <label class="block text-sm font-medium text-gray-300 mb-2">Nachname *</label>
                                                <input type="text" name="lastName" required class="w-full px-4 py-3 bg-dark border border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent text-white hover-glow">
                                            </div>
                                        </div>
                                        <div>
                                            <label class="block text-sm font-medium text-gray-300 mb-2">E-Mail *</label>
                                            <input type="email" name="email" required class="w-full px-4 py-3 bg-dark border border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent text-white hover-glow">
                                        </div>
                                        <div>
                                            <label class="block text-sm font-medium text-gray-300 mb-2">Telefon (optional)</label>
                                            <input type="tel" name="phone" class="w-full px-4 py-3 bg-dark border border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent text-white hover-glow">
                                        </div>
                                        <div>
                                            <label class="block text-sm font-medium text-gray-300 mb-2">Unternehmen *</label>
                                            <input type="text" name="company" required class="w-full px-4 py-3 bg-dark border border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent text-white hover-glow">
                                        </div>
                                    </div>
                                    
                                    <!-- Appointment Tab -->
                                    <div id="appointment-data" class="hidden space-y-4">
                                        <div class="text-center mb-4">
                                            <h4 class="text-lg font-semibold text-white mb-2">Möchtest du direkt einen Termin vereinbaren?</h4>
                                            <p class="text-gray-400 text-sm">Wähle einen Tag und eine Uhrzeit für dein kostenloses Erstgespräch (optional)</p>
                                        </div>
                                        
                                        <div class="calendar-container">
                                            <div class="calendar-header">
                                                <button type="button" onclick="changeMonth(-1)" class="p-2 hover:bg-primary hover:bg-opacity-20 rounded-lg transition-colors">
                                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path>
                                                    </svg>
                                                </button>
                                                <h4 id="calendar-month" class="text-lg font-semibold text-white flex-1 text-center"></h4>
                                                <button type="button" onclick="changeMonth(1)" class="p-2 hover:bg-primary hover:bg-opacity-20 rounded-lg transition-colors">
                                                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
                                                    </svg>
                                                </button>
                                            </div>
                                            
                                            <div class="calendar-grid" id="calendar-grid">
                                                <!-- Calendar will be generated by JavaScript -->
                                            </div>
                                            
                                            <div id="time-slots-container" class="hidden">
                                                <h5 class="text-white font-semibold mb-3">Verfügbare Zeiten:</h5>
                                                <div class="time-slots" id="time-slots">
                                                    <!-- Time slots will be generated by JavaScript -->
                                                </div>
                                            </div>
                                        </div>
                                        
                                        <div id="selected-appointment" class="hidden bg-accent bg-opacity-10 border border-accent rounded-lg p-4">
                                            <div class="flex items-center">
                                                <svg class="w-5 h-5 text-accent mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"></path>
                                                </svg>
                                                <span class="text-accent font-semibold">Gewählter Termin: </span>
                                                <span id="appointment-display" class="text-white ml-2"></span>
                                                <button type="button" onclick="clearAppointment()" class="ml-auto text-gray-400 hover:text-white">
                                                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                                                    </svg>
                                                </button>
                                            </div>
                                        </div>
                                        
                                        <input type="hidden" name="appointmentDate" id="appointment-date">
                                        <input type="hidden" name="appointmentTime" id="appointment-time">
                                    </div>
                                    
                                    <button type="submit" class="w-full bg-accent text-dark py-4 rounded-lg font-semibold glow-button text-lg">
                                        🎉 Quiz abschließen & Auswertung erhalten
                                    </button>
                                </form>
                            </div>
                        </div>
                        
                        <!-- Navigation Buttons -->
                        <div class="flex justify-between mt-8">
                            <button id="prev-btn" onclick="previousQuestion()" class="bg-gray-600 text-white px-6 py-3 rounded-lg font-semibold hover:bg-gray-500 transition-colors duration-300 hidden">
                                ← Zurück
                            </button>
                            <button id="next-btn" onclick="nextQuestion()" class="bg-primary text-white px-6 py-3 rounded-lg font-semibold glow-button ml-auto hidden">
                                Weiter →
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Quiz Completion Animation -->
    <div id="quiz-completion" class="quiz-completion">
        <div class="completion-content">
            <div class="checkmark-circle">
                <svg class="checkmark" viewBox="0 0 100 100">
                    <path d="M20,50 L40,70 L80,30" fill="none" stroke="white" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
            </div>
            <h2 class="text-3xl font-bold mb-4">Danke für die Teilnahme am Quiz!</h2>
            <p class="text-xl text-gray-300 mb-6">Bestätigungs-Mail zum ausgewählten Erstgespräch erfolgt in Kürze.</p>
            <div class="text-accent font-semibold">Vielen Dank für dein Interesse! 🎉</div>
        </div>
    </div>

    <!-- Services Section -->
    <section id="services" class="py-20 bg-light">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16 fade-in">
                <h2 class="text-4xl font-bold mb-4 text-white">Unsere <span class="text-gradient">Services</span></h2>
                <p class="text-xl text-gray-300 max-w-3xl mx-auto">
                    Von der Strategie bis zur Umsetzung - wir begleiten dich auf deinem Weg zur erfolgreichen Personal Brand
                </p>
            </div>
            
            <div class="grid md:grid-cols-3 gap-8">
                <div class="bg-lighter p-8 rounded-2xl shadow-lg hover-scale fade-in border border-gray-700 glow-hover">
                    <div class="w-16 h-16 bg-primary rounded-full flex items-center justify-center mb-6 pulse-glow">
                        <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"></path>
                        </svg>
                    </div>
                    <h3 class="text-2xl font-bold mb-4 text-white">Personal Brand Strategie</h3>
                    <p class="text-gray-300 mb-6">
                        Entwicklung einer authentischen und zielgerichteten Personal Brand Strategie, die deine Einzigartigkeit hervorhebt und deine Zielgruppe anspricht.
                    </p>
                    <ul class="text-gray-300 space-y-2">
                        <li>✓ Brand Positioning & Messaging</li>
                        <li>✓ Zielgruppenanalyse</li>
                        <li>✓ Content-Strategie Entwicklung</li>
                        <li>✓ Competitive Analysis</li>
                    </ul>
                </div>

                <div class="bg-lighter p-8 rounded-2xl shadow-lg hover-scale fade-in border border-gray-700 glow-hover">
                    <div class="w-16 h-16 bg-accent rounded-full flex items-center justify-center mb-6 pulse-glow">
                        <svg class="w-8 h-8 text-dark" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z"></path>
                        </svg>
                    </div>
                    <h3 class="text-2xl font-bold mb-4 text-white">Content Creation</h3>
                    <p class="text-gray-300 mb-6">
                        Professionelle Content-Erstellung für alle relevanten Plattformen mit Fokus auf Authentizität und Engagement.
                    </p>
                    <ul class="text-gray-300 space-y-2">
                        <li>✓ Social Media Posts</li>
                        <li>✓ Blog-Artikel & LinkedIn-Posts</li>
                        <li>✓ Video-Content Konzeption</li>
                        <li>✓ Grafik-Design & Visuals</li>
                    </ul>
                </div>

                <div class="bg-lighter p-8 rounded-2xl shadow-lg hover-scale fade-in border border-gray-700 glow-hover">
                    <div class="w-16 h-16 bg-secondary rounded-full flex items-center justify-center mb-6 pulse-glow">
                        <svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6"></path>
                        </svg>
                    </div>
                    <h3 class="text-2xl font-bold mb-4 text-white">Organisches Wachstum</h3>
                    <p class="text-gray-300 mb-6">
                        Nachhaltiges Wachstum durch authentische Interaktionen und strategische Community-Building-Maßnahmen.
                    </p>
                    <ul class="text-gray-300 space-y-2">
                        <li>✓ Community Management</li>
                        <li>✓ Engagement-Strategien</li>
                        <li>✓ Influencer Networking</li>
                        <li>✓ Performance Analytics</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-20 bg-dark">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16 fade-in">
                <h2 class="text-4xl font-bold mb-4 text-white">Über <span class="text-gradient">RafIQ Agency</span></h2>
                <p class="text-xl text-gray-300 max-w-3xl mx-auto">
                    Wir sind Experten im Bereich Personal Branding und organisches Social Media Wachstum
                </p>
            </div>
            
            <div class="grid lg:grid-cols-2 gap-12 items-center">
                <div class="fade-in">
                    <h3 class="text-3xl font-bold mb-6 text-white">Unsere Mission</h3>
                    <p class="text-gray-300 mb-6 text-lg">
                        Bei RafIQ Agency glauben wir daran, dass jede Person eine einzigartige Geschichte zu erzählen hat. Unser Team aus erfahrenen Strategen, Content-Creators und Social Media Experten entwickelt gemeinsam mit dir authentische Personal Brands, die deine Persönlichkeit und Expertise widerspiegeln.
                    </p>
                    <p class="text-gray-300 mb-6 text-lg">
                        Als Full-Service-Agentur bieten wir dir alle Leistungen aus einer Hand - von der ersten Strategieentwicklung über die Content-Erstellung bis hin zur langfristigen Betreuung deiner Personal Brand. Unsere kreativen Köpfe arbeiten Hand in Hand, um maßgeschneiderte Lösungen zu entwickeln, die deine Ziele erreichen.
                    </p>
                </div>
                
                <div class="fade-in">
                    <div class="bg-lighter p-8 rounded-2xl shadow-lg border border-gray-700 glow-primary">
                        <h4 class="text-2xl font-bold mb-6 text-white">Warum RafIQ Agency?</h4>
                        <div class="space-y-4">
                            <div class="flex items-start hover-scale">
                                <div class="w-6 h-6 bg-primary rounded-full flex items-center justify-center mr-4 mt-1 pulse-glow">
                                    <svg class="w-3 h-3 text-white" fill="currentColor" viewBox="0 0 20 20">
                                        <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"></path>
                                    </svg>
                                </div>
                                <div>
                                    <h5 class="font-semibold mb-1 text-white">Authentizität im Fokus</h5>
                                    <p class="text-gray-300">Wir entwickeln Strategien, die deine echte Persönlichkeit widerspiegeln</p>
                                </div>
                            </div>
                            <div class="flex items-start hover-scale">
                                <div class="w-6 h-6 bg-accent rounded-full flex items-center justify-center mr-4 mt-1 pulse-glow">
                                    <svg class="w-3 h-3 text-dark" fill="currentColor" viewBox="0 0 20 20">
                                        <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"></path>
                                    </svg>
                                </div>
                                <div>
                                    <h5 class="font-semibold mb-1 text-white">Organisches Wachstum</h5>
                                    <p class="text-gray-300">Nachhaltiger Aufbau ohne künstliche Tricks oder Abkürzungen</p>
                                </div>
                            </div>
                            <div class="flex items-start hover-scale">
                                <div class="w-6 h-6 bg-secondary rounded-full flex items-center justify-center mr-4 mt-1 pulse-glow">
                                    <svg class="w-3 h-3 text-white" fill="currentColor" viewBox="0 0 20 20">
                                        <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"></path>
                                    </svg>
                                </div>
                                <div>
                                    <h5 class="font-semibold mb-1 text-white">Individuelle Betreuung</h5>
                                    <p class="text-gray-300">Persönliche Beratung und maßgeschneiderte Lösungen für jeden Kunden</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-20 bg-light">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16 fade-in">
                <h2 class="text-4xl font-bold mb-4 text-white">Bereit für deine <span class="text-gradient">Personal Brand</span>?</h2>
                <p class="text-xl text-gray-300 max-w-3xl mx-auto">
                    Lass uns in einem kostenlosen Erstgespräch über deine Ziele sprechen
                </p>
            </div>
            
            <div class="max-w-4xl mx-auto">
                <div class="bg-lighter p-8 rounded-2xl shadow-lg fade-in border border-gray-700 glow-primary">
                    <div class="grid md:grid-cols-2 gap-8">
                        <div>
                            <h3 class="text-2xl font-bold mb-6 text-white">Kontaktiere uns</h3>
                            <div class="space-y-4">
                                <div class="flex items-center hover-scale">
                                    <div class="w-10 h-10 bg-primary rounded-full flex items-center justify-center mr-4 pulse-glow">
                                        <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
                                        </svg>
                                    </div>
                                    <div>
                                        <p class="font-semibold text-white">E-Mail</p>
                                        <p class="text-gray-300">hello@rafiq-agency.com</p>
                                    </div>
                                </div>

                                <div class="flex items-center hover-scale">
                                    <div class="w-10 h-10 bg-secondary rounded-full flex items-center justify-center mr-4 pulse-glow">
                                        <svg class="w-5 h-5 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path>
                                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path>
                                        </svg>
                                    </div>
                                    <div>
                                        <p class="font-semibold text-white">Standort</p>
                                        <p class="text-gray-300">Berlin, Deutschland</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                        
                        <div>
                            <form id="contact-form" action="https://formspree.io/f/mvgqklog" method="POST" class="space-y-4" onsubmit="handleContactForm(event)">
                                <input type="hidden" name="submission_type" value="Kontaktanfrage">
                                <div>
                                    <label class="block text-sm font-medium text-gray-300 mb-2">Name</label>
                                    <input type="text" name="name" required class="w-full px-4 py-3 bg-dark border border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent text-white hover-glow">
                                </div>
                                <div>
                                    <label class="block text-sm font-medium text-gray-300 mb-2">E-Mail</label>
                                    <input type="email" name="email" required class="w-full px-4 py-3 bg-dark border border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent text-white hover-glow">
                                </div>
                                <div>
                                    <label class="block text-sm font-medium text-gray-300 mb-2">Nachricht</label>
                                    <textarea rows="4" name="message" required class="w-full px-4 py-3 bg-dark border border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent text-white hover-glow"></textarea>
                                </div>
                                <button type="submit" class="w-full bg-primary text-white py-3 rounded-lg font-semibold glow-button">
                                    Nachricht senden
                                </button>
                                <p class="text-sm text-gray-400 text-center">
                                    Deine Nachricht wird direkt an unser Team weitergeleitet.
                                </p>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-darker text-white py-12">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid md:grid-cols-4 gap-8">
                <div>
                    <div class="h-8 w-32 mb-4">
                        <!-- FOOTER LOGO - Verwende hier die gleiche Methode wie oben, aber in weiß/hell -->
                        <!-- OPTION 1: SVG Logo (weiße Version) -->
                        <!-- <svg class="h-8 w-auto" viewBox="0 0 200 50" fill="white" xmlns="http://www.w3.org/2000/svg">
                             Hier dein SVG-Code einfügen (mit fill="white" oder stroke="white")
                        </svg> -->
                        
                        <!-- OPTION 2: PNG/JPG Logo (helle Version) -->
                        <!-- <img src="dein-logo-weiss.png" alt="RafIQ Agency Logo" class="h-8 w-auto"> -->
                        
                        <!-- TEMPORÄRER PLATZHALTER -->
                        <div class="h-8 w-32 bg-primary rounded flex items-center justify-center glow-button">
                            <span class="text-white font-bold text-lg">RafIQ Agency</span>
                        </div>
                    </div>
                    <p class="text-gray-400 mb-4">
                        Deine Agentur für authentisches Personal Branding und organisches Wachstum.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold mb-4 text-white">Services</h4>
                    <ul class="space-y-2 text-gray-400">
                        <li><a href="#services" class="hover:text-primary transition-colors hover-scale">Personal Brand Strategie</a></li>
                        <li><a href="#services" class="hover:text-primary transition-colors hover-scale">Content Creation</a></li>
                        <li><a href="#services" class="hover:text-primary transition-colors hover-scale">Organisches Wachstum</a></li>
                    </ul>
                </div>
                
                <div>
                    <h4 class="font-semibold mb-4 text-white">Unternehmen</h4>
                    <ul class="space-y-2 text-gray-400">
                        <li><a href="#about" class="hover:text-primary transition-colors hover-scale">Über uns</a></li>
                        <li><a href="#contact" class="hover:text-primary transition-colors hover-scale">Kontakt</a></li>
                        <li><button onclick="openModal('consultation')" class="hover:text-primary transition-colors hover-scale">Erstgespräch</button></li>
                    </ul>
                </div>
                
                <div>
                    <h4 class="font-semibold mb-4 text-white">Rechtliches</h4>
                    <ul class="space-y-2 text-gray-400">
                        <li><button onclick="openModal('impressum')" class="hover:text-primary transition-colors hover-scale">Impressum</button></li>
                        <li><button onclick="openModal('datenschutz')" class="hover:text-primary transition-colors hover-scale">Datenschutz</button></li>
                        <li><button onclick="openModal('agb')" class="hover:text-primary transition-colors hover-scale">AGB</button></li>
                    </ul>
                </div>
            </div>
            
            <div class="border-t border-gray-700 mt-8 pt-8 text-center text-gray-400">
                <p>&copy; 2024 RafIQ Agency. Alle Rechte vorbehalten.</p>
            </div>
        </div>
    </footer>

    <!-- Modals -->
    <!-- Consultation Modal -->
    <div id="consultation-modal" class="modal">
        <div class="modal-content max-w-2xl">
            <div class="flex justify-between items-center mb-6">
                <h3 class="text-2xl font-bold">Kostenloses Erstgespräch buchen</h3>
                <button onclick="closeModal('consultation')" class="text-gray-500 hover:text-gray-300">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
            <p class="text-gray-300 mb-6">
                Lass uns in einem 30-minütigen Gespräch über deine Ziele sprechen und herausfinden, wie wir dir beim Aufbau deiner Personal Brand helfen können.
            </p>
            <form action="https://formspree.io/f/mvgqklog" method="POST" onsubmit="handleConsultationForm(event)" class="space-y-4">
                <input type="hidden" name="submission_type" value="Erstgespräch Anfrage">
                <div class="grid md:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-sm font-medium text-gray-300 mb-2">Vorname</label>
                        <input type="text" name="firstName" required class="w-full px-4 py-3 bg-dark border border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent text-white hover-glow">
                    </div>
                    <div>
                        <label class="block text-sm font-medium text-gray-300 mb-2">Nachname</label>
                        <input type="text" name="lastName" required class="w-full px-4 py-3 bg-dark border border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent text-white hover-glow">
                    </div>
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-2">E-Mail</label>
                    <input type="email" name="email" required class="w-full px-4 py-3 bg-dark border border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent text-white hover-glow">
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-2">Branche/Bereich</label>
                    <input type="text" name="industry" required class="w-full px-4 py-3 bg-dark border border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent text-white hover-glow">
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-300 mb-2">Beschreibe kurz deine Ziele</label>
                    <textarea rows="3" name="goals" required class="w-full px-4 py-3 bg-dark border border-gray-600 rounded-lg focus:ring-2 focus:ring-primary focus:border-transparent text-white hover-glow"></textarea>
                </div>
                <button type="submit" class="w-full bg-primary text-white py-3 rounded-lg font-semibold glow-button">
                    Erstgespräch anfragen
                </button>
                <p class="text-sm text-gray-400 text-center">
                    Deine Anfrage wird direkt an unser Team weitergeleitet.
                </p>
            </form>
        </div>
    </div>

    <!-- Success Modal -->
    <div id="success-modal" class="modal">
        <div class="modal-content max-w-md text-center">
            <div class="mb-6">
                <div class="w-20 h-20 bg-accent rounded-full flex items-center justify-center mx-auto mb-4 pulse-glow">
                    <svg class="w-10 h-10 text-dark" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path>
                    </svg>
                </div>
                <h3 class="text-2xl font-bold mb-4">🎉 Erfolgreich abgeschickt!</h3>
                <p class="text-gray-300 mb-6">
                    Vielen Dank! Deine Anfrage wurde erfolgreich übermittelt. Wir melden uns innerhalb von 24 Stunden bei dir.
                </p>
                <button onclick="closeModal('success')" class="bg-primary text-white px-6 py-3 rounded-lg font-semibold glow-button">
                    Schließen
                </button>
            </div>
        </div>
    </div>

    <!-- Impressum Modal -->
    <div id="impressum-modal" class="modal">
        <div class="modal-content max-w-4xl">
            <div class="flex justify-between items-center mb-6">
                <h3 class="text-2xl font-bold">Impressum</h3>
                <button onclick="closeModal('impressum')" class="text-gray-500 hover:text-gray-300">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
            <div class="space-y-6 text-gray-300">
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">Angaben gemäß § 5 TMG</h4>
                    <p>
                        RafIQ Agency<br>
                        Sardaar Enis-Khan Rafiq<br>
                        Hindenburgstraße 161<br>
                        22297 Hamburg<br>
                        Deutschland
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">Kontakt</h4>
                    <p>
                        E-Mail: info@rafiq-agency.de<br>
                        Website: rafiq-agency.de
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">Umsatzsteuer-ID</h4>
                    <p>
                        Umsatzsteuer-Identifikationsnummer gemäß § 27 a Umsatzsteuergesetz:<br>
                        DE123456789
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">Verantwortlich für den Inhalt nach § 55 Abs. 2 RStV</h4>
                    <p>
                        Sardaar Enis-Khan Rafiq<br>
                        Hindenburgstraße 161<br>
                        22297 Hamburg<br>
                        Deutschland
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">Haftungsausschluss</h4>
                    <p class="mb-4">
                        <strong>Haftung für Inhalte:</strong><br>
                        Als Diensteanbieter sind wir gemäß § 7 Abs.1 TMG für eigene Inhalte auf diesen Seiten nach den allgemeinen Gesetzen verantwortlich. Nach §§ 8 bis 10 TMG sind wir als Diensteanbieter jedoch nicht unter der Verpflichtung, übermittelte oder gespeicherte fremde Informationen zu überwachen oder nach Umständen zu forschen, die auf eine rechtswidrige Tätigkeit hinweisen.
                    </p>
                    <p class="mb-4">
                        <strong>Haftung für Links:</strong><br>
                        Unser Angebot enthält Links zu externen Websites Dritter, auf deren Inhalte wir keinen Einfluss haben. Deshalb können wir für diese fremden Inhalte auch keine Gewähr übernehmen. Für die Inhalte der verlinkten Seiten ist stets der jeweilige Anbieter oder Betreiber der Seiten verantwortlich.
                    </p>
                </div>
            </div>
        </div>
    </div>

    <!-- Datenschutz Modal -->
    <div id="datenschutz-modal" class="modal">
        <div class="modal-content max-w-4xl">
            <div class="flex justify-between items-center mb-6">
                <h3 class="text-2xl font-bold">Datenschutzerklärung</h3>
                <button onclick="closeModal('datenschutz')" class="text-gray-500 hover:text-gray-300">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
            <div class="space-y-6 text-gray-300">
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">1. Verantwortlicher</h4>
                    <p class="mb-4">
                        Verantwortlicher im Sinne der Datenschutz-Grundverordnung (DSGVO) und anderer nationaler Datenschutzgesetze der Mitgliedsstaaten sowie sonstiger datenschutzrechtlicher Bestimmungen ist:<br><br>
                        <strong>Sardaar Enis-Khan Rafiq</strong><br>
                        RafIQ Agency<br>
                        Hindenburgstraße 161<br>
                        22297 Hamburg<br>
                        Deutschland<br>
                        E-Mail: hello@rafiq-agency.com
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">2. Allgemeine Hinweise zur Datenverarbeitung</h4>
                    <p class="mb-4">
                        <strong>Umfang der Verarbeitung personenbezogener Daten:</strong><br>
                        Wir verarbeiten personenbezogene Daten unserer Nutzer grundsätzlich nur, soweit dies zur Bereitstellung einer funktionsfähigen Website sowie unserer Inhalte und Leistungen erforderlich ist. Die Verarbeitung personenbezogener Daten unserer Nutzer erfolgt regelmäßig nur nach Einwilligung des Nutzers. Eine Ausnahme gilt in solchen Fällen, in denen eine vorherige Einholung einer Einwilligung aus tatsächlichen Gründen nicht möglich ist und die Verarbeitung der Daten durch gesetzliche Vorschriften gestattet ist.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">3. Rechtsgrundlage für die Verarbeitung personenbezogener Daten</h4>
                    <p class="mb-4">
                        Soweit wir für Verarbeitungsvorgänge personenbezogener Daten eine Einwilligung der betroffenen Person einholen, dient Art. 6 Abs. 1 lit. a EU-Datenschutzgrundverordnung (DSGVO) als Rechtsgrundlage.<br><br>
                        Bei der Verarbeitung von personenbezogenen Daten, die zur Erfüllung eines Vertrages, dessen Vertragspartei die betroffene Person ist, erforderlich ist, dient Art. 6 Abs. 1 lit. b DSGVO als Rechtsgrundlage.<br><br>
                        Soweit eine Verarbeitung personenbezogener Daten zur Erfüllung einer rechtlichen Verpflichtung erforderlich ist, der unser Unternehmen unterliegt, dient Art. 6 Abs. 1 lit. c DSGVO als Rechtsgrundlage.<br><br>
                        Ist die Verarbeitung zur Wahrung eines berechtigten Interesses unseres Unternehmens oder eines Dritten erforderlich und überwiegen die Interessen, Grundrechte und Grundfreiheiten des Betroffenen das erstgenannte Interesse nicht, so dient Art. 6 Abs. 1 lit. f DSGVO als Rechtsgrundlage für die Verarbeitung.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">4. Datenlöschung und Speicherdauer</h4>
                    <p class="mb-4">
                        Die personenbezogenen Daten der betroffenen Person werden gelöscht oder gesperrt, sobald der Zweck der Speicherung entfällt. Eine Speicherung kann darüber hinaus erfolgen, wenn dies durch den europäischen oder nationalen Gesetzgeber in unionsrechtlichen Verordnungen, Gesetzen oder sonstigen Vorschriften, denen der Verantwortliche unterliegt, vorgesehen wurde. Eine Sperrung oder Löschung der Daten erfolgt auch dann, wenn eine durch die genannten Normen vorgeschriebene Speicherfrist abläuft, es sei denn, dass eine Erforderlichkeit zur weiteren Speicherung der Daten für einen Vertragsabschluss oder eine Vertragserfüllung besteht.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">5. Bereitstellung der Website und Erstellung von Logfiles</h4>
                    <p class="mb-4">
                        <strong>Beschreibung und Umfang der Datenverarbeitung:</strong><br>
                        Bei jedem Aufruf unserer Internetseite erfasst unser System automatisiert Daten und Informationen vom Computersystem des aufrufenden Rechners. Folgende Daten werden hierbei erhoben:<br>
                        - Informationen über den Browsertyp und die verwendete Version<br>
                        - Das Betriebssystem des Nutzers<br>
                        - Den Internet-Service-Provider des Nutzers<br>
                        - Die IP-Adresse des Nutzers<br>
                        - Datum und Uhrzeit des Zugriffs<br>
                        - Websites, von denen das System des Nutzers auf unsere Internetseite gelangt<br>
                        - Websites, die vom System des Nutzers über unsere Website aufgerufen werden<br><br>
                        <strong>Rechtsgrundlage:</strong> Art. 6 Abs. 1 lit. f DSGVO. Unser berechtigtes Interesse folgt aus den oben aufgelisteten Zwecken zur Datenerhebung.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">6. Verwendung von Kontaktformularen</h4>
                    <p class="mb-4">
                        <strong>Beschreibung und Umfang der Datenverarbeitung:</strong><br>
                        Auf unserer Internetseite sind Kontaktformulare vorhanden, welche für die elektronische Kontaktaufnahme genutzt werden können. Nimmt ein Nutzer diese Möglichkeit wahr, so werden die in der Eingabemaske eingegeben Daten an uns übermittelt und gespeichert. Diese Daten sind:<br>
                        - Vor- und Nachname<br>
                        - E-Mail-Adresse<br>
                        - Telefonnummer (optional)<br>
                        - Unternehmen<br>
                        - Nachrichteninhalt<br>
                        - Quiz-Antworten (bei Bedarfs-Quiz)<br>
                        - Terminwünsche (bei Erstgespräch)<br><br>
                        <strong>Zweck der Datenverarbeitung:</strong><br>
                        Die Verarbeitung der personenbezogenen Daten aus der Eingabemaske dient uns allein zur Bearbeitung der Kontaktaufnahme. Die sonstigen während des Absendevorgangs verarbeiteten personenbezogenen Daten dienen dazu, einen Missbrauch des Kontaktformulars zu verhindern und die Sicherheit unserer informationstechnischen Systeme sicherzustellen.<br><br>
                        <strong>Rechtsgrundlage:</strong> Art. 6 Abs. 1 lit. a DSGVO (Einwilligung) und Art. 6 Abs. 1 lit. f DSGVO (berechtigtes Interesse).
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">7. E-Mail-Verkehr und Newsletter</h4>
                    <p class="mb-4">
                        <strong>Beschreibung und Umfang der Datenverarbeitung:</strong><br>
                        Wenn Sie uns per E-Mail kontaktieren oder sich für unseren Newsletter anmelden, verarbeiten wir Ihre E-Mail-Adresse und weitere von Ihnen mitgeteilte Daten zur Bearbeitung Ihrer Anfrage bzw. zum Versand des Newsletters.<br><br>
                        <strong>Zweck der Datenverarbeitung:</strong><br>
                        - Bearbeitung von Anfragen<br>
                        - Versendung von Informationen über unsere Dienstleistungen<br>
                        - Marketing und Kundenbetreuung<br><br>
                        <strong>Rechtsgrundlage:</strong> Art. 6 Abs. 1 lit. a DSGVO (Einwilligung) und Art. 6 Abs. 1 lit. f DSGVO (berechtigtes Interesse).
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">8. Externe Dienstleister</h4>
                    <p class="mb-4">
                        <strong>Formspree:</strong><br>
                        Zur Verarbeitung von Kontaktformularen nutzen wir den Dienst Formspree. Dabei werden Ihre Formulardaten an Formspree übertragen und von dort an unsere E-Mail-Adresse weitergeleitet. Formspree speichert diese Daten entsprechend ihrer Datenschutzrichtlinien.<br><br>
                        <strong>Social Media Plattformen:</strong><br>
                        Im Rahmen unserer Dienstleistungen können wir in Ihrem Auftrag Content auf verschiedenen Social Media Plattformen (LinkedIn, Instagram, YouTube, etc.) erstellen und veröffentlichen. Dabei gelten die jeweiligen Datenschutzbestimmungen der Plattformen.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">9. Rechte der betroffenen Person</h4>
                    <p class="mb-4">
                        Werden personenbezogene Daten von Ihnen verarbeitet, sind Sie Betroffener i.S.d. DSGVO und es stehen Ihnen folgende Rechte gegenüber dem Verantwortlichen zu:<br><br>
                        <strong>Auskunftsrecht (Art. 15 DSGVO):</strong> Sie haben das Recht, eine Bestätigung darüber zu verlangen, ob betreffende personenbezogene Daten verarbeitet werden.<br><br>
                        <strong>Recht auf Berichtigung (Art. 16 DSGVO):</strong> Sie haben ein Recht auf unverzügliche Berichtigung Sie betreffender unrichtiger personenbezogener Daten.<br><br>
                        <strong>Recht auf Löschung (Art. 17 DSGVO):</strong> Sie haben das Recht, zu verlangen, dass Sie betreffende personenbezogene Daten unverzüglich gelöscht werden.<br><br>
                        <strong>Recht auf Einschränkung der Verarbeitung (Art. 18 DSGVO):</strong> Sie haben das Recht, die Einschränkung der Verarbeitung zu verlangen.<br><br>
                        <strong>Recht auf Datenübertragbarkeit (Art. 20 DSGVO):</strong> Sie haben das Recht, die Sie betreffenden personenbezogenen Daten in einem strukturierten, gängigen und maschinenlesbaren Format zu erhalten.<br><br>
                        <strong>Widerspruchsrecht (Art. 21 DSGVO):</strong> Sie haben das Recht, aus Gründen, die sich aus Ihrer besonderen Situation ergeben, jederzeit gegen die Verarbeitung der Sie betreffenden personenbezogenen Daten Widerspruch einzulegen.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">10. Recht auf Beschwerde bei einer Aufsichtsbehörde</h4>
                    <p class="mb-4">
                        Unbeschadet eines anderweitigen verwaltungsrechtlichen oder gerichtlichen Rechtsbehelfs steht Ihnen das Recht auf Beschwerde bei einer Aufsichtsbehörde, insbesondere in dem Mitgliedstaat ihres Aufenthaltsorts, ihres Arbeitsplatzes oder des Orts des mutmaßlichen Verstoßes, zu, wenn Sie der Ansicht sind, dass die Verarbeitung der Sie betreffenden personenbezogenen Daten gegen die DSGVO verstößt.<br><br>
                        Die Aufsichtsbehörde, bei der die Beschwerde eingereicht wurde, unterrichtet den Beschwerdeführer über den Stand und die Ergebnisse der Beschwerde einschließlich der Möglichkeit eines gerichtlichen Rechtsbehelfs nach Art. 78 DSGVO.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">11. SSL-Verschlüsselung</h4>
                    <p class="mb-4">
                        Diese Seite nutzt aus Sicherheitsgründen und zum Schutz der Übertragung vertraulicher Inhalte, wie zum Beispiel Bestellungen oder Anfragen, die Sie an uns als Seitenbetreiber senden, eine SSL-bzw. TLS-Verschlüsselung. Eine verschlüsselte Verbindung erkennen Sie daran, dass die Adresszeile des Browsers von "http://" auf "https://" wechselt und an dem Schloss-Symbol in Ihrer Browserzeile.
                    </p>
                </div>
            </div>
        </div>
    </div>

    <!-- AGB Modal -->
    <div id="agb-modal" class="modal">
        <div class="modal-content max-w-4xl">
            <div class="flex justify-between items-center mb-6">
                <h3 class="text-2xl font-bold">Allgemeine Geschäftsbedingungen</h3>
                <button onclick="closeModal('agb')" class="text-gray-500 hover:text-gray-300">
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                    </svg>
                </button>
            </div>
            <div class="space-y-6 text-gray-300">
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">§ 1 Geltungsbereich und Vertragspartner</h4>
                    <p class="mb-4">
                        <strong>1.1</strong> Diese Allgemeinen Geschäftsbedingungen (AGB) gelten für alle Verträge zwischen Sardaar Enis-Khan Rafiq, handelnd unter "RafIQ Agency" (nachfolgend "Auftragnehmer"), und seinen Kunden (nachfolgend "Auftraggeber") über die Erbringung von Dienstleistungen im Bereich Personal Branding, Social Media Marketing, Content Creation und verwandten Dienstleistungen.<br><br>
                        <strong>1.2</strong> Abweichende, entgegenstehende oder ergänzende Allgemeine Geschäftsbedingungen des Auftraggebers werden nicht Vertragsbestandteil, es sei denn, ihrer Geltung wird ausdrücklich schriftlich zugestimmt.<br><br>
                        <strong>1.3</strong> Diese AGB gelten auch für alle künftigen Geschäftsbeziehungen, auch wenn sie nicht nochmals ausdrücklich vereinbart werden.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">§ 2 Vertragsschluss und Leistungsbeschreibung</h4>
                    <p class="mb-4">
                        <strong>2.1</strong> Angebote des Auftragnehmers sind freibleibend und unverbindlich, sofern sie nicht ausdrücklich als verbindlich bezeichnet sind.<br><br>
                        <strong>2.2</strong> Der Vertrag kommt durch die schriftliche Auftragsbestätigung des Auftragnehmers oder durch Beginn der Leistungserbringung zustande.<br><br>
                        <strong>2.3</strong> Der Umfang der zu erbringenden Leistungen ergibt sich aus der jeweiligen Leistungsbeschreibung im Angebot oder Vertrag. Mündliche Nebenabreden bedürfen zu ihrer Wirksamkeit der schriftlichen Bestätigung.<br><br>
                        <strong>2.4</strong> Änderungen und Ergänzungen des Vertrags bedürfen der Schriftform. Dies gilt auch für die Aufhebung des Schriftformerfordernisses.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">§ 3 Leistungserbringung und Mitwirkungspflichten</h4>
                    <p class="mb-4">
                        <strong>3.1</strong> Der Auftragnehmer erbringt seine Leistungen nach den anerkannten Regeln der Technik und den branchenüblichen Standards.<br><br>
                        <strong>3.2</strong> Der Auftraggeber ist verpflichtet, alle für die ordnungsgemäße Durchführung des Auftrags erforderlichen Informationen, Unterlagen, Zugangsdaten und sonstigen Materialien vollständig und rechtzeitig zur Verfügung zu stellen.<br><br>
                        <strong>3.3</strong> Verzögerungen, Mehraufwand oder Schäden, die durch unvollständige, verspätete oder fehlerhafte Mitwirkung des Auftraggebers entstehen, gehen zu dessen Lasten und können gesondert berechnet werden.<br><br>
                        <strong>3.4</strong> Der Auftraggeber stellt sicher, dass alle von ihm zur Verfügung gestellten Inhalte, Materialien und Informationen frei von Rechten Dritter sind und deren Verwendung nicht gegen geltendes Recht verstößt.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">§ 4 Vergütung und Zahlungsbedingungen</h4>
                    <p class="mb-4">
                        <strong>4.1</strong> Die Vergütung richtet sich nach der jeweiligen Vereinbarung. Alle Preise verstehen sich zuzüglich der gesetzlichen Umsatzsteuer.<br><br>
                        <strong>4.2</strong> Rechnungen sind innerhalb von 14 Tagen nach Rechnungsstellung ohne Abzug zur Zahlung fällig. Bei Zahlungsverzug werden Verzugszinsen in Höhe von 9 Prozentpunkten über dem Basiszinssatz berechnet.<br><br>
                        <strong>4.3</strong> Bei Dauerschuldverhältnissen erfolgt die Abrechnung monatlich im Voraus, sofern nicht anders vereinbart.<br><br>
                        <strong>4.4</strong> Der Auftraggeber kann nur mit unbestrittenen oder rechtskräftig festgestellten Forderungen aufrechnen. Ein Zurückbehaltungsrecht kann nur wegen Gegenansprüchen aus demselben Vertragsverhältnis geltend gemacht werden.<br><br>
                        <strong>4.5</strong> Bei Zahlungsverzug oder begründeten Zweifeln an der Zahlungsfähigkeit des Auftraggebers kann der Auftragnehmer die weitere Leistungserbringung bis zur Zahlung einstellen und Vorauszahlung verlangen.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">§ 5 Urheberrecht und Nutzungsrechte</h4>
                    <p class="mb-4">
                        <strong>5.1</strong> Alle im Rahmen der Leistungserbringung erstellten Werke (insbesondere Texte, Grafiken, Videos, Konzepte, Strategien) unterliegen dem Urheberrecht des Auftragnehmers.<br><br>
                        <strong>5.2</strong> Der Auftraggeber erhält nach vollständiger Bezahlung der Vergütung die vereinbarten Nutzungsrechte. Soweit nicht anders vereinbart, werden einfache, zeitlich und räumlich unbeschränkte Nutzungsrechte für den vereinbarten Verwendungszweck eingeräumt.<br><br>
                        <strong>5.3</strong> Eine Weitergabe, Veränderung oder anderweitige Nutzung der Werke über den vereinbarten Zweck hinaus ist ohne ausdrückliche Zustimmung des Auftragnehmers nicht gestattet.<br><br>
                        <strong>5.4</strong> Der Auftragnehmer behält sich das Recht vor, die erstellten Werke zu Referenz- und Marketingzwecken zu verwenden, sofern keine berechtigten Geheimhaltungsinteressen des Auftraggebers entgegenstehen.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">§ 6 Geheimhaltung und Datenschutz</h4>
                    <p class="mb-4">
                        <strong>6.1</strong> Der Auftragnehmer verpflichtet sich, alle ihm im Rahmen der Geschäftsbeziehung bekannt gewordenen Geschäfts- und Betriebsgeheimnisse des Auftraggebers vertraulich zu behandeln.<br><br>
                        <strong>6.2</strong> Die Geheimhaltungspflicht besteht auch nach Beendigung des Vertragsverhältnisses fort.<br><br>
                        <strong>6.3</strong> Der Auftragnehmer verarbeitet personenbezogene Daten entsprechend den geltenden datenschutzrechtlichen Bestimmungen, insbesondere der DSGVO.<br><br>
                        <strong>6.4</strong> Soweit der Auftragnehmer personenbezogene Daten im Auftrag des Auftraggebers verarbeitet, wird eine separate Auftragsverarbeitungsvereinbarung geschlossen.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">§ 7 Haftung und Haftungsbeschränkung</h4>
                    <p class="mb-4">
                        <strong>7.1</strong> Der Auftragnehmer haftet unbeschränkt für Schäden aus der Verletzung des Lebens, des Körpers oder der Gesundheit, die auf einer vorsätzlichen oder fahrlässigen Pflichtverletzung beruhen.<br><br>
                        <strong>7.2</strong> Für sonstige Schäden haftet der Auftragnehmer nur bei Vorsatz und grober Fahrlässigkeit sowie bei der Verletzung wesentlicher Vertragspflichten (Kardinalpflichten).<br><br>
                        <strong>7.3</strong> Bei der Verletzung wesentlicher Vertragspflichten durch leichte Fahrlässigkeit ist die Haftung auf den vertragstypischen, vorhersehbaren Schaden begrenzt.<br><br>
                        <strong>7.4</strong> Die Haftung für mittelbare Schäden, Folgeschäden, entgangenen Gewinn und Vermögensschäden ist ausgeschlossen, soweit nicht Vorsatz oder grobe Fahrlässigkeit vorliegt.<br><br>
                        <strong>7.5</strong> Die Haftung für den Verlust von Daten ist auf den typischen Wiederherstellungsaufwand beschränkt, der bei regelmäßiger und gefahrentsprechender Anfertigung von Sicherungskopien entstanden wäre.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">§ 8 Kündigung und Vertragsbeendigung</h4>
                    <p class="mb-4">
                        <strong>8.1</strong> Verträge über Einzelleistungen enden mit vollständiger Erfüllung der vereinbarten Leistungen.<br><br>
                        <strong>8.2</strong> Dauerschuldverhältnisse können von beiden Parteien mit einer Frist von 4 Wochen zum Monatsende gekündigt werden, soweit nicht anders vereinbart.<br><br>
                        <strong>8.3</strong> Das Recht zur außerordentlichen Kündigung aus wichtigem Grund bleibt unberührt. Ein wichtiger Grund liegt insbesondere vor bei:<br>
                        - Zahlungsverzug von mehr als 30 Tagen<br>
                        - Verletzung wesentlicher Vertragspflichten<br>
                        - Insolvenz einer Vertragspartei<br><br>
                        <strong>8.4</strong> Kündigungen bedürfen der Schriftform.<br><br>
                        <strong>8.5</strong> Bei Kündigung durch den Auftraggeber ohne wichtigen Grund ist die vereinbarte Vergütung bis zum ordentlichen Kündigungstermin zu zahlen.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">§ 9 Gewährleistung und Mängelhaftung</h4>
                    <p class="mb-4">
                        <strong>9.1</strong> Der Auftragnehmer gewährleistet die vertragsgemäße Erbringung seiner Leistungen entsprechend dem vereinbarten Leistungsumfang.<br><br>
                        <strong>9.2</strong> Mängel sind unverzüglich nach Entdeckung schriftlich anzuzeigen. Offensichtliche Mängel sind innerhalb von 14 Tagen nach Leistungserbringung zu rügen.<br><br>
                        <strong>9.3</strong> Bei berechtigten Mängelrügen wird der Auftragnehmer nach seiner Wahl den Mangel beseitigen oder die Leistung wiederholen (Nacherfüllung).<br><br>
                        <strong>9.4</strong> Schlägt die Nacherfüllung fehl, kann der Auftraggeber nach seiner Wahl Minderung verlangen oder vom Vertrag zurücktreten.<br><br>
                        <strong>9.5</strong> Gewährleistungsansprüche verjähren in 12 Monaten ab Abnahme der Leistung.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">§ 10 Höhere Gewalt und außergewöhnliche Umstände</h4>
                    <p class="mb-4">
                        <strong>10.1</strong> Höhere Gewalt und andere außergewöhnliche Umstände (wie Pandemien, Naturkatastrophen, Streiks, behördliche Anordnungen), die die Leistungserbringung unmöglich oder unzumutbar erschweren, befreien die Parteien für die Dauer der Behinderung von ihren Leistungspflichten.<br><br>
                        <strong>10.2</strong> Die betroffene Partei hat die andere Partei unverzüglich über den Eintritt und das voraussichtliche Ende der Behinderung zu informieren.<br><br>
                        <strong>10.3</strong> Dauert die Behinderung länger als 3 Monate, können beide Parteien den Vertrag mit sofortiger Wirkung kündigen.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">§ 11 Abtretung und Aufrechnung</h4>
                    <p class="mb-4">
                        <strong>11.1</strong> Die Abtretung von Forderungen durch den Auftraggeber ist nur mit vorheriger schriftlicher Zustimmung des Auftragnehmers zulässig.<br><br>
                        <strong>11.2</strong> Der Auftraggeber kann nur mit unbestrittenen oder rechtskräftig festgestellten Forderungen aufrechnen.<br><br>
                        <strong>11.3</strong> Der Auftragnehmer ist berechtigt, seine Rechte und Pflichten aus diesem Vertrag ganz oder teilweise auf Dritte zu übertragen.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">§ 12 Salvatorische Klausel und Schlussbestimmungen</h4>
                    <p class="mb-4">
                        <strong>12.1</strong> Sollten einzelne Bestimmungen dieses Vertrags unwirksam oder undurchführbar sein oder werden, so wird dadurch die Wirksamkeit der übrigen Bestimmungen nicht berührt.<br><br>
                        <strong>12.2</strong> Unwirksame oder undurchführbare Bestimmungen sind durch solche zu ersetzen, die dem wirtschaftlichen Zweck der unwirksamen Bestimmung am nächsten kommen.<br><br>
                        <strong>12.3</strong> Auf diesen Vertrag findet ausschließlich deutsches Recht unter Ausschluss des UN-Kaufrechts Anwendung.<br><br>
                        <strong>12.4</strong> Erfüllungsort und ausschließlicher Gerichtsstand für alle Streitigkeiten aus diesem Vertragsverhältnis ist Hamburg, sofern der Auftraggeber Kaufmann, juristische Person des öffentlichen Rechts oder öffentlich-rechtliches Sondervermögen ist.<br><br>
                        <strong>12.5</strong> Änderungen und Ergänzungen dieser AGB bedürfen der Schriftform.
                    </p>
                </div>
                
                <div>
                    <h4 class="font-semibold text-lg mb-2 text-white">§ 13 Besondere Bestimmungen für Social Media und Content Marketing</h4>
                    <p class="mb-4">
                        <strong>13.1</strong> Der Auftragnehmer übernimmt keine Gewähr für die Erreichung bestimmter Reichweiten, Engagement-Raten oder sonstiger Kennzahlen in sozialen Medien.<br><br>
                        <strong>13.2</strong> Algorithmus-Änderungen der Plattformen, die sich auf die Leistung auswirken, liegen außerhalb des Einflussbereichs des Auftragnehmers.<br><br>
                        <strong>13.3</strong> Der Auftraggeber ist für die Einhaltung der Nutzungsbedingungen der jeweiligen Plattformen verantwortlich.<br><br>
                        <strong>13.4</strong> Bei Sperrungen oder anderen Maßnahmen der Plattformen gegen den Auftraggeber besteht kein Anspruch auf Rückerstattung bereits erbrachter Leistungen.
                    </p>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Quiz Variables
        let currentQuestionIndex = 1;
        let quizAnswers = {};
        const totalQuestions = 8;
        
        // Calendar Variables
        let currentDate = new Date();
        let selectedDate = null;
        let selectedTime = null;

        // Tab Switching
        function switchTab(tab) {
            const heroContent = document.getElementById('hero-content');
            const quizContent = document.getElementById('quiz-content');
            const heroTab = document.getElementById('hero-tab');
            const quizTab = document.getElementById('quiz-tab');
            
            if (tab === 'hero') {
                heroContent.classList.remove('hidden');
                quizContent.classList.add('hidden');
                heroTab.classList.add('active');
                quizTab.classList.remove('active');
            } else {
                heroContent.classList.add('hidden');
                quizContent.classList.remove('hidden');
                heroTab.classList.remove('active');
                quizTab.classList.add('active');
            }
        }

        // Quiz Functions
        function selectOption(element, questionNum, value) {
            // Remove selection from other options in the same question
            const questionDiv = element.closest('.quiz-question');
            questionDiv.querySelectorAll('.quiz-option').forEach(opt => {
                opt.classList.remove('selected');
            });
            
            // Add selection to clicked option
            element.classList.add('selected');
            
            // Store answer
            quizAnswers[`question${questionNum}`] = value;
            
            // Show next button
            document.getElementById('next-btn').classList.remove('hidden');
        }

        function nextQuestion() {
            if (currentQuestionIndex < totalQuestions) {
                // Hide current question
                document.querySelector(`[data-question="${currentQuestionIndex}"]`).classList.add('hidden');
                
                // Show next question
                currentQuestionIndex++;
                document.querySelector(`[data-question="${currentQuestionIndex}"]`).classList.remove('hidden');
                
                // Update progress
                updateProgress();
                
                // Show/hide navigation buttons
                document.getElementById('prev-btn').classList.remove('hidden');
                
                // Check if answer exists for current question
                const currentAnswer = quizAnswers[`question${currentQuestionIndex}`];
                if (currentAnswer && (Array.isArray(currentAnswer) ? currentAnswer.length > 0 : true)) {
                    document.getElementById('next-btn').classList.remove('hidden');
                } else {
                    document.getElementById('next-btn').classList.add('hidden');
                }
            } else {
                // Show contact form
                document.querySelector(`[data-question="${currentQuestionIndex}"]`).classList.add('hidden');
                document.getElementById('quiz-contact').classList.remove('hidden');
                document.getElementById('next-btn').classList.add('hidden');
                document.getElementById('current-question').textContent = 'Kontaktdaten';
            }
        }

        function previousQuestion() {
            if (currentQuestionIndex > 1) {
                // Hide current question or contact form
                if (currentQuestionIndex <= totalQuestions) {
                    document.querySelector(`[data-question="${currentQuestionIndex}"]`).classList.add('hidden');
                } else {
                    document.getElementById('quiz-contact').classList.add('hidden');
                }
                
                // Show previous question
                currentQuestionIndex--;
                document.querySelector(`[data-question="${currentQuestionIndex}"]`).classList.remove('hidden');
                
                // Update progress
                updateProgress();
                
                // Show/hide navigation buttons
                if (currentQuestionIndex === 1) {
                    document.getElementById('prev-btn').classList.add('hidden');
                }
                document.getElementById('next-btn').classList.remove('hidden');
                document.getElementById('current-question').textContent = currentQuestionIndex;
            }
        }

        function updateProgress() {
            const progress = (currentQuestionIndex / totalQuestions) * 100;
            document.getElementById('progress-bar').style.width = progress + '%';
            document.getElementById('current-question').textContent = currentQuestionIndex;
        }

        // Multi-select function for platforms question
        function selectMultiOption(element, questionNum, value) {
            // Toggle selection
            element.classList.toggle('selected');
            
            // Initialize array if not exists
            if (!quizAnswers[`question${questionNum}`]) {
                quizAnswers[`question${questionNum}`] = [];
            }
            
            // Add or remove value from array
            const currentAnswers = quizAnswers[`question${questionNum}`];
            const index = currentAnswers.indexOf(value);
            
            if (index > -1) {
                currentAnswers.splice(index, 1);
            } else {
                currentAnswers.push(value);
            }
            
            // Show next button if at least one option is selected
            if (currentAnswers.length > 0) {
                document.getElementById('next-btn').classList.remove('hidden');
            } else {
                document.getElementById('next-btn').classList.add('hidden');
            }
        }

        // Add click event listeners to quiz options
        document.addEventListener('DOMContentLoaded', function() {
            document.querySelectorAll('.quiz-option').forEach(option => {
                option.addEventListener('click', function() {
                    const questionNum = this.closest('.quiz-question').dataset.question;
                    const value = this.dataset.value;
                    selectOption(this, questionNum, value);
                });
            });
            
            // Multi-select options for platforms question
            document.querySelectorAll('.quiz-option-multi').forEach(option => {
                option.addEventListener('click', function() {
                    const questionNum = this.closest('.quiz-question').dataset.question;
                    const value = this.dataset.value;
                    selectMultiOption(this, questionNum, value);
                });
            });
        });

        // Quiz Form Submission - Formspree Integration
        document.addEventListener("DOMContentLoaded", function () {
            // Hauptformular Event Listener
            document.getElementById('quiz-form').addEventListener('submit', function(e) {
                e.preventDefault();
                
                console.log('📤 Quiz wird über Formspree gesendet...');
                
                const formData = new FormData(e.target);
                const contactData = {
                    firstName: formData.get('firstName'),
                    lastName: formData.get('lastName'),
                    email: formData.get('email'),
                    phone: formData.get('phone') || 'Nicht angegeben',
                    company: formData.get('company'),
                    appointmentDate: formData.get('appointmentDate') || 'Nicht gewählt',
                    appointmentTime: formData.get('appointmentTime') || 'Nicht gewählt'
                };
                
                // Sammle Quiz-Antworten
                const answers = {
                    question1: quizAnswers.question1 || 'Nicht beantwortet',
                    question2: quizAnswers.question2 || 'Nicht beantwortet',
                    question3: quizAnswers.question3 || 'Nicht beantwortet',
                    question4: quizAnswers.question4 || 'Nicht beantwortet',
                    question5: quizAnswers.question5 || 'Nicht beantwortet',
                    question6: quizAnswers.question6 || 'Nicht beantwortet',
                    question7: quizAnswers.question7 || 'Nicht beantwortet',
                    question8: quizAnswers.question8 || 'Nicht beantwortet'
                };
                
                // Validierung
                if (!contactData.firstName || !contactData.lastName || !contactData.email) {
                    alert("Bitte fülle alle Pflichtfelder aus.");
                    return;
                }
                
                // Fülle versteckte Felder mit Quiz-Antworten
                populateHiddenFields(answers, contactData);
                
                // Show completion animation
                showQuizCompletion();
                
                console.log('📋 Sende folgende Daten:', {
                    contact: contactData,
                    answers: answers
                });
                
                // Submit form to Formspree
                fetch('https://formspree.io/f/mvgqklog', {
                    method: 'POST',
                    body: new FormData(e.target),
                    headers: {
                        'Accept': 'application/json'
                    }
                })
                .then(response => {
                    console.log('✅ Formspree Response Status:', response.status);
                    if (response.ok) {
                        console.log('✅ Quiz erfolgreich über Formspree gesendet!');
                        
                        // Bestätigung anzeigen
                        setTimeout(() => {
                            alert("🎉 Danke! Deine Quiz-Auswertung wird dir bald per E-Mail zugeschickt.");
                        }, 1000);
                        
                        // Reset quiz after animation
                        setTimeout(() => {
                            resetQuiz();
                            hideQuizCompletion();
                        }, 3000);
                    } else {
                        console.error('❌ Formspree Fehler - Status:', response.status);
                        response.json().then(data => {
                            console.error('❌ Formspree Error Details:', data);
                            alert('Es gab ein Problem beim Senden. Bitte versuche es erneut.');
                            hideQuizCompletion();
                        });
                    }
                })
                .catch(error => {
                    console.error('❌ Netzwerk-Fehler bei Formspree:', error);
                    alert('Verbindungsfehler. Bitte überprüfe deine Internetverbindung und versuche es erneut.');
                    hideQuizCompletion();
                });
            });
            
            // Fallback für quizForm ID (falls vorhanden)
            const quizFormFallback = document.querySelector("#quizForm");
            if (quizFormFallback) {
                quizFormFallback.addEventListener("submit", function (e) {
                    e.preventDefault();

                    const contactData = {
                        firstName: document.querySelector("#firstName").value,
                        lastName: document.querySelector("#lastName").value,
                        email: document.querySelector("#email").value,
                        company: document.querySelector("#company").value,
                        phone: 'Nicht angegeben',
                        appointmentDate: 'Nicht gewählt',
                        appointmentTime: 'Nicht gewählt'
                    };

                    const answers = {
                        question1: document.querySelector('input[name="question1"]:checked')?.value,
                        question2: document.querySelector('input[name="question2"]:checked')?.value,
                        question3: document.querySelector('input[name="question3"]:checked')?.value,
                        question4: document.querySelector('input[name="question4"]:checked')?.value,
                        question5: document.querySelector('input[name="question5"]:checked')?.value,
                        question6: document.querySelector('input[name="question6"]:checked')?.value,
                        question7: document.querySelector('input[name="question7"]:checked')?.value
                    };

                    sendQuizData(contactData, answers);

                    // Bestätigung anzeigen
                    alert("Danke! Deine Auswertung wird dir bald per E-Mail zugeschickt.");
                });
            }
        });
        
        // Helper function to populate hidden fields for Formspree
        function populateHiddenFields(answers, contactData) {
            // Quiz answers
            document.getElementById('hidden-question1').value = answers.question1 || 'Nicht beantwortet';
            document.getElementById('hidden-question2').value = answers.question2 || 'Nicht beantwortet';
            document.getElementById('hidden-question3').value = Array.isArray(answers.question3) ? answers.question3.join(', ') : (answers.question3 || 'Nicht beantwortet');
            document.getElementById('hidden-question4').value = answers.question4 || 'Nicht beantwortet';
            document.getElementById('hidden-question5').value = answers.question5 || 'Nicht beantwortet';
            document.getElementById('hidden-question6').value = answers.question6 || 'Nicht beantwortet';
            document.getElementById('hidden-question7').value = answers.question7 || 'Nicht beantwortet';
            document.getElementById('hidden-question8').value = answers.question8 || 'Nicht beantwortet';
            
            // Generate summary
            const summary = generateFormspreeQuizSummary(contactData, answers);
            document.getElementById('hidden-quiz-summary').value = summary;
            
            console.log('📝 Versteckte Felder gefüllt:', {
                question1: answers.question1,
                question2: answers.question2,
                question3: answers.question3,
                summary: summary.substring(0, 100) + '...'
            });
        }
        
        function generateFormspreeQuizSummary(contactData, answers) {
            const questionLabels = {
                question1: 'Branche',
                question2: 'Online-Präsenz',
                question3: 'Wichtigste Plattformen',
                question4: 'Verfügbare Zeit pro Woche',
                question5: 'Hauptziel',
                question6: 'Bevorzugter Content-Typ',
                question7: 'Budget',
                question8: 'Gewünschter Start'
            };
            
            let summary = `PERSONAL BRAND QUIZ - NEUE AUSWERTUNG\n\n`;
            summary += `KONTAKTDATEN:\n`;
            summary += `Name: ${contactData.firstName} ${contactData.lastName}\n`;
            summary += `E-Mail: ${contactData.email}\n`;
            summary += `Telefon: ${contactData.phone}\n`;
            summary += `Unternehmen: ${contactData.company}\n`;
            
            if (contactData.appointmentDate !== 'Nicht gewählt') {
                summary += `\nGEWÜNSCHTER TERMIN:\n`;
                summary += `${contactData.appointmentDate} um ${contactData.appointmentTime}\n`;
            }
            
            summary += `\nQUIZ-ANTWORTEN:\n`;
            Object.keys(answers).forEach(key => {
                const answer = answers[key];
                const displayAnswer = Array.isArray(answer) ? answer.join(', ') : answer;
                summary += `${questionLabels[key]}: ${displayAnswer}\n`;
            });
            
            summary += `\nZeitpunkt: ${new Date().toLocaleString('de-DE')}\n`;
            
            return summary;
        }

        function sendQuizData(contactData, answers) {
            // Zapier Webhook URL für Quiz-Daten
            const zapierWebhookUrl = 'https://hooks.zapier.com/hooks/catch/23908078/uu6tzg1/';
            
            // Flache Datenstruktur für bessere Zapier-Kompatibilität
            const emailData = {
                type: 'Quiz Submission',
                timestamp: new Date().toLocaleString('de-DE'),
                // Kontaktdaten direkt als Felder
                firstName: contactData.firstName,
                lastName: contactData.lastName,
                email: contactData.email,
                phone: contactData.phone,
                company: contactData.company,
                appointmentDate: contactData.appointmentDate,
                appointmentTime: contactData.appointmentTime,
                // Quiz-Antworten als einzelne Felder
                branche: answers.question1 || 'Nicht beantwortet',
                onlinePresence: answers.question2 || 'Nicht beantwortet',
                platforms: Array.isArray(answers.question3) ? answers.question3.join(', ') : (answers.question3 || 'Nicht beantwortet'),
                timeAvailable: answers.question4 || 'Nicht beantwortet',
                mainGoal: answers.question5 || 'Nicht beantwortet',
                contentType: answers.question6 || 'Nicht beantwortet',
                budget: answers.question7 || 'Nicht beantwortet',
                startTime: answers.question8 || 'Nicht beantwortet',
                // Formatierte Zusammenfassung
                summary: generateQuizSummary(contactData, answers)
            };
            
            console.log('Sende Quiz-Daten an Zapier:', emailData);
            
            // Sende an Zapier
            fetch(zapierWebhookUrl, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(emailData)
            })
            .then(response => {
                console.log('Zapier Response Status:', response.status);
                if (response.ok) {
                    console.log('Quiz-Daten erfolgreich an Zapier gesendet');
                } else {
                    console.error('Fehler beim Senden an Zapier - Status:', response.status);
                    return response.text().then(text => {
                        console.error('Response Text:', text);
                    });
                }
            })
            .catch(error => {
                console.error('Netzwerk-Fehler beim Quiz-Versand:', error);
            });
        }
        
        function generateQuizSummary(contactData, answers) {
            const questionLabels = {
                question1: 'Branche',
                question2: 'Online-Präsenz',
                question3: 'Wichtigste Plattformen',
                question4: 'Verfügbare Zeit pro Woche',
                question5: 'Hauptziel',
                question6: 'Bevorzugter Content-Typ',
                question7: 'Budget',
                question8: 'Gewünschter Start'
            };
            
            let summary = `NEUE QUIZ-AUSWERTUNG\n\n`;
            summary += `KONTAKTDATEN:\n`;
            summary += `Name: ${contactData.firstName} ${contactData.lastName}\n`;
            summary += `E-Mail: ${contactData.email}\n`;
            summary += `Telefon: ${contactData.phone}\n`;
            summary += `Unternehmen: ${contactData.company}\n`;
            
            if (contactData.appointmentDate !== 'Nicht gewählt') {
                summary += `\nGEWÜNSCHTER TERMIN:\n`;
                summary += `${contactData.appointmentDate} um ${contactData.appointmentTime}\n`;
            }
            
            summary += `\nQUIZ-ANTWORTEN:\n`;
            Object.keys(answers).forEach(key => {
                const answer = answers[key];
                const displayAnswer = Array.isArray(answer) ? answer.join(', ') : answer;
                summary += `${questionLabels[key]}: ${displayAnswer}\n`;
            });
            
            return summary;
        }

        function generateQuizReport(contactData, answers) {
            let report = `NEUE QUIZ-AUSWERTUNG\n\n`;
            report += `KONTAKTDATEN:\n`;
            report += `Name: ${contactData.firstName} ${contactData.lastName}\n`;
            report += `E-Mail: ${contactData.email}\n`;
            report += `Telefon: ${contactData.phone}\n`;
            report += `Unternehmen: ${contactData.company}\n`;
            
            if (contactData.appointmentDate !== 'Nicht gewählt') {
                report += `Gewünschter Termin: ${contactData.appointmentDate} um ${contactData.appointmentTime}\n`;
            }
            report += `\n`;
            
            report += `QUIZ-ANTWORTEN:\n`;
            
            const questionTexts = {
                question1: 'Branche',
                question2: 'Online-Präsenz',
                question3: 'Wichtigste Plattformen',
                question4: 'Verfügbare Zeit',
                question5: 'Hauptziel',
                question6: 'Bevorzugter Content-Typ',
                question7: 'Budget',
                question8: 'Starttermin'
            };
            
            Object.keys(answers).forEach(key => {
                const answer = answers[key];
                const displayAnswer = Array.isArray(answer) ? answer.join(', ') : answer;
                report += `${questionTexts[key]}: ${displayAnswer}\n`;
            });
            
            return report;
        }

        function resetQuiz() {
            currentQuestionIndex = 1;
            quizAnswers = {};
            selectedDate = null;
            selectedTime = null;
            
            // Hide all questions except first
            document.querySelectorAll('.quiz-question').forEach((q, index) => {
                if (index === 0) {
                    q.classList.remove('hidden');
                } else {
                    q.classList.add('hidden');
                }
            });
            
            // Hide contact form
            document.getElementById('quiz-contact').classList.add('hidden');
            
            // Reset contact tabs
            switchContactTab('contact');
            
            // Reset progress
            updateProgress();
            
            // Reset buttons
            document.getElementById('prev-btn').classList.add('hidden');
            document.getElementById('next-btn').classList.add('hidden');
            
            // Clear selections
            document.querySelectorAll('.quiz-option, .quiz-option-multi').forEach(opt => {
                opt.classList.remove('selected');
            });
            
            // Clear form
            document.getElementById('quiz-form').reset();
            
            // Switch back to hero tab
            switchTab('hero');
        }
        
        // Quiz Completion Animation Functions
        function showQuizCompletion() {
            document.getElementById('quiz-completion').classList.add('active');
            document.body.style.overflow = 'hidden';
        }
        
        function hideQuizCompletion() {
            document.getElementById('quiz-completion').classList.remove('active');
            document.body.style.overflow = 'auto';
        }
        
        // Contact Tab Functions
        function switchContactTab(tab) {
            const contactTab = document.getElementById('contact-tab');
            const appointmentTab = document.getElementById('appointment-tab');
            const contactData = document.getElementById('contact-data');
            const appointmentData = document.getElementById('appointment-data');
            
            if (tab === 'contact') {
                contactTab.classList.add('active');
                appointmentTab.classList.remove('active');
                contactData.classList.remove('hidden');
                appointmentData.classList.add('hidden');
            } else {
                contactTab.classList.remove('active');
                appointmentTab.classList.add('active');
                contactData.classList.add('hidden');
                appointmentData.classList.remove('hidden');
                
                // Initialize calendar when switching to appointment tab
                if (!document.getElementById('calendar-grid').innerHTML) {
                    generateCalendar();
                }
            }
        }
        
        // Calendar Functions
        function generateCalendar() {
            const grid = document.getElementById('calendar-grid');
            const monthDisplay = document.getElementById('calendar-month');
            
            const year = currentDate.getFullYear();
            const month = currentDate.getMonth();
            
            const monthNames = [
                'Januar', 'Februar', 'März', 'April', 'Mai', 'Juni',
                'Juli', 'August', 'September', 'Oktober', 'November', 'Dezember'
            ];
            
            monthDisplay.textContent = `${monthNames[month]} ${year}`;
            
            // Clear grid
            grid.innerHTML = '';
            
            // Add day headers
            const dayHeaders = ['Mo', 'Di', 'Mi', 'Do', 'Fr', 'Sa', 'So'];
            dayHeaders.forEach(day => {
                const dayElement = document.createElement('div');
                dayElement.className = 'calendar-day header';
                dayElement.textContent = day;
                grid.appendChild(dayElement);
            });
            
            // Get first day of month and number of days
            const firstDay = new Date(year, month, 1);
            const lastDay = new Date(year, month + 1, 0);
            const daysInMonth = lastDay.getDate();
            
            // Adjust for Monday start (0 = Sunday, 1 = Monday, etc.)
            let startDay = firstDay.getDay();
            startDay = startDay === 0 ? 6 : startDay - 1;
            
            // Add empty cells for days before month starts
            for (let i = 0; i < startDay; i++) {
                const emptyDay = document.createElement('div');
                emptyDay.className = 'calendar-day';
                grid.appendChild(emptyDay);
            }
            
            // Add days of the month
            const today = new Date();
            for (let day = 1; day <= daysInMonth; day++) {
                const dayElement = document.createElement('div');
                const dayDate = new Date(year, month, day);
                const dayOfWeek = dayDate.getDay();
                
                // Check if it's a weekday and not in the past
                const isWeekday = dayOfWeek >= 1 && dayOfWeek <= 5;
                const isFuture = dayDate >= today || 
                    (dayDate.toDateString() === today.toDateString());
                
                dayElement.textContent = day;
                dayElement.className = 'calendar-day';
                
                if (isWeekday && isFuture) {
                    dayElement.className += ' available';
                    dayElement.onclick = () => selectDate(year, month, day);
                } else {
                    dayElement.className += ' unavailable';
                }
                
                grid.appendChild(dayElement);
            }
        }
        
        function changeMonth(direction) {
            currentDate.setMonth(currentDate.getMonth() + direction);
            generateCalendar();
            
            // Clear selected date if it's no longer visible
            if (selectedDate) {
                const selectedMonth = selectedDate.getMonth();
                const currentMonth = currentDate.getMonth();
                if (selectedMonth !== currentMonth) {
                    clearAppointment();
                }
            }
        }
        
        function selectDate(year, month, day) {
            // Clear previous selection
            document.querySelectorAll('.calendar-day.selected').forEach(el => {
                el.classList.remove('selected');
            });
            
            // Select new date
            event.target.classList.add('selected');
            selectedDate = new Date(year, month, day);
            
            // Show time slots
            generateTimeSlots();
            document.getElementById('time-slots-container').classList.remove('hidden');
        }
        
        function generateTimeSlots() {
            const container = document.getElementById('time-slots');
            container.innerHTML = '';
            
            // Generate time slots from 10:00 to 18:00
            for (let hour = 10; hour <= 17; hour++) {
                for (let minute = 0; minute < 60; minute += 30) {
                    const timeString = `${hour.toString().padStart(2, '0')}:${minute.toString().padStart(2, '0')}`;
                    
                    const timeSlot = document.createElement('div');
                    timeSlot.className = 'time-slot';
                    timeSlot.textContent = timeString;
                    timeSlot.onclick = () => selectTime(timeString);
                    
                    container.appendChild(timeSlot);
                }
            }
        }
        
        function selectTime(time) {
            // Clear previous selection
            document.querySelectorAll('.time-slot.selected').forEach(el => {
                el.classList.remove('selected');
            });
            
            // Select new time
            event.target.classList.add('selected');
            selectedTime = time;
            
            // Update hidden inputs and display
            document.getElementById('appointment-date').value = selectedDate.toLocaleDateString('de-DE');
            document.getElementById('appointment-time').value = selectedTime;
            
            const displayText = `${selectedDate.toLocaleDateString('de-DE', { 
                weekday: 'long', 
                year: 'numeric', 
                month: 'long', 
                day: 'numeric' 
            })} um ${selectedTime} Uhr`;
            
            document.getElementById('appointment-display').textContent = displayText;
            document.getElementById('selected-appointment').classList.remove('hidden');
        }
        
        function clearAppointment() {
            selectedDate = null;
            selectedTime = null;
            
            document.querySelectorAll('.calendar-day.selected, .time-slot.selected').forEach(el => {
                el.classList.remove('selected');
            });
            
            document.getElementById('appointment-date').value = '';
            document.getElementById('appointment-time').value = '';
            document.getElementById('selected-appointment').classList.add('hidden');
            document.getElementById('time-slots-container').classList.add('hidden');
        }

        function showSuccessAnimation() {
            const form = document.getElementById('quiz-form');
            form.classList.add('success-animation');
            setTimeout(() => {
                form.classList.remove('success-animation');
            }, 600);
        }

        // Mobile menu toggle
        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            menu.classList.toggle('hidden');
        }

        // Modal functions
        function openModal(modalName) {
            document.getElementById(modalName + '-modal').classList.add('active');
            document.body.style.overflow = 'hidden';
        }

        function closeModal(modalName) {
            document.getElementById(modalName + '-modal').classList.remove('active');
            document.body.style.overflow = 'auto';
        }

        // Close modal when clicking outside
        document.addEventListener('click', function(event) {
            if (event.target.classList.contains('modal')) {
                event.target.classList.remove('active');
                document.body.style.overflow = 'auto';
            }
        });

        // Form handlers
        function handleContactForm(event) {
            event.preventDefault();
            
            console.log('📤 Kontaktformular wird über Formspree gesendet...');
            
            // Add success animation
            const form = event.target;
            form.classList.add('success-animation');
            
            // Submit to Formspree
            fetch('https://formspree.io/f/mvgqklog', {
                method: 'POST',
                body: new FormData(event.target),
                headers: {
                    'Accept': 'application/json'
                }
            })
            .then(response => {
                console.log('✅ Kontakt Formspree Response Status:', response.status);
                if (response.ok) {
                    console.log('✅ Kontaktformular erfolgreich über Formspree gesendet!');
                    setTimeout(() => {
                        form.classList.remove('success-animation');
                        openModal('success');
                        form.reset();
                    }, 600);
                } else {
                    console.error('❌ Kontakt Formspree Fehler - Status:', response.status);
                    alert('Es gab ein Problem beim Senden. Bitte versuche es erneut.');
                    form.classList.remove('success-animation');
                }
            })
            .catch(error => {
                console.error('❌ Kontakt Netzwerk-Fehler bei Formspree:', error);
                alert('Verbindungsfehler. Bitte überprüfe deine Internetverbindung und versuche es erneut.');
                form.classList.remove('success-animation');
            });
        }

        function handleConsultationForm(event) {
            event.preventDefault();
            
            console.log('📤 Erstgespräch-Formular wird über Formspree gesendet...');
            
            // Add success animation
            const form = event.target;
            form.classList.add('success-animation');
            
            // Submit to Formspree
            fetch('https://formspree.io/f/mvgqklog', {
                method: 'POST',
                body: new FormData(event.target),
                headers: {
                    'Accept': 'application/json'
                }
            })
            .then(response => {
                console.log('✅ Erstgespräch Formspree Response Status:', response.status);
                if (response.ok) {
                    console.log('✅ Erstgespräch-Formular erfolgreich über Formspree gesendet!');
                    setTimeout(() => {
                        form.classList.remove('success-animation');
                        closeModal('consultation');
                        openModal('success');
                        form.reset();
                    }, 600);
                } else {
                    console.error('❌ Erstgespräch Formspree Fehler - Status:', response.status);
                    alert('Es gab ein Problem beim Senden. Bitte versuche es erneut.');
                    form.classList.remove('success-animation');
                }
            })
            .catch(error => {
                console.error('❌ Erstgespräch Netzwerk-Fehler bei Formspree:', error);
                alert('Verbindungsfehler. Bitte überprüfe deine Internetverbindung und versuche es erneut.');
                form.classList.remove('success-animation');
            });
        }
        
        function sendContactData(data) {
            // Zapier Webhook URL für Kontaktformular
            const zapierWebhookUrl = 'https://hooks.zapier.com/hooks/catch/23908078/uu6tzg1/';
            
            console.log('Sende Kontaktdaten an Zapier:', data);
            
            fetch(zapierWebhookUrl, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(data)
            })
            .then(response => {
                console.log('Zapier Response Status:', response.status);
                if (response.ok) {
                    console.log('Kontaktdaten erfolgreich an Zapier gesendet');
                } else {
                    console.error('Fehler beim Senden an Zapier - Status:', response.status);
                    return response.text().then(text => {
                        console.error('Response Text:', text);
                    });
                }
            })
            .catch(error => {
                console.error('Netzwerk-Fehler beim Kontakt-Versand:', error);
            });
        }
        
        function sendConsultationData(data) {
            // Zapier Webhook URL für Erstgespräch
            const zapierWebhookUrl = 'https://hooks.zapier.com/hooks/catch/23908078/uu6tzg1/';
            
            console.log('Sende Beratungsdaten an Zapier:', data);
            
            fetch(zapierWebhookUrl, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(data)
            })
            .then(response => {
                console.log('Zapier Response Status:', response.status);
                if (response.ok) {
                    console.log('Beratungsdaten erfolgreich an Zapier gesendet');
                } else {
                    console.error('Fehler beim Senden an Zapier - Status:', response.status);
                    return response.text().then(text => {
                        console.error('Response Text:', text);
                    });
                }
            })
            .catch(error => {
                console.error('Netzwerk-Fehler beim Beratungs-Versand:', error);
            });
        }

        // Test Webhook Function (für Debugging)
        function testWebhook() {
            console.log('🧪 Teste Webhook-Verbindung...');
            
            const testData = {
                submission_type: 'test',
                timestamp: new Date().toISOString(),
                test_message: 'Dies ist ein Test vom Quiz-System',
                first_name: 'Test',
                last_name: 'User',
                email: 'test@example.com'
            };
            
            const zapierWebhookUrl = 'https://hooks.zapier.com/hooks/catch/23908078/uu6tzg1/';
            
            fetch(zapierWebhookUrl, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                    'Accept': 'application/json'
                },
                body: JSON.stringify(testData)
            })
            .then(response => {
                console.log('🧪 Test Response Status:', response.status);
                console.log('🧪 Test Response OK:', response.ok);
                return response.text();
            })
            .then(text => {
                console.log('🧪 Test Response Text:', text);
                alert(`Test-Status: ${text ? 'Erfolgreich' : 'Fehler'}\nDetails in der Console (F12)`);
            })
            .catch(error => {
                console.error('🧪 Test Error:', error);
                alert(`Test-Fehler: ${error.message}\nDetails in der Console (F12)`);
            });
        }

        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
                // Close mobile menu if open
                document.getElementById('mobile-menu').classList.add('hidden');
            });
        });

        // Fade in animation on scroll
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver(function(entries) {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.animationDelay = '0.1s';
                    entry.target.classList.add('fade-in');
                }
            });
        }, observerOptions);

        // Observe all elements that should fade in
        document.addEventListener('DOMContentLoaded', function() {
            document.querySelectorAll('.fade-in').forEach(el => {
                observer.observe(el);
            });
        });
    </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'96896e15d5144480',t:'MTc1NDA5NDI0Mi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
