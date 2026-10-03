# Reading-Challenge--Words
<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>אתגר קריאה של כיתה ב' 🎯</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Canvas Confetti library for celebration effects -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <!-- Google Fonts: Rubik for clean Hebrew & Nikud rendering -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Rubik:wght@400;600;700;800;900&display=swap" rel="stylesheet">
    
    <style>
        body {
            font-family: 'Rubik', sans-serif;
            background: linear-gradient(135deg, #f0f9ff 0%, #e0f2fe 50%, #bae6fd 100%);
            min-height: 100vh;
            user-select: none;
        }

        /* Large readable vowelized Hebrew text style */
        .nikud-text {
            font-feature-settings: "liga" 1, "kern" 1;
            line-height: 1.3;
        }

        /* Smooth card transition animations */
        .card-pop {
            transition: transform 0.25s cubic-bezier(0.175, 0.885, 0.32, 1.275), box-shadow 0.25s ease;
        }
        .card-pop:hover {
            transform: translateY(-4px) scale(1.02);
        }

        /* Pulse glow animation for badges */
        @keyframes subtleGlow {
            0%, 100% { transform: scale(1); filter: drop-shadow(0 0 10px rgba(59, 130, 246, 0.4)); }
            50% { transform: scale(1.05); filter: drop-shadow(0 0 20px rgba(59, 130, 246, 0.7)); }
        }

        .target-glow {
            animation: subtleGlow 3s infinite ease-in-out;
        }

        /* Flip card animation when shuffling */
        .shuffle-anim {
            animation: flipIn 0.4s ease-out;
        }

        @keyframes flipIn {
            0% { transform: rotateX(-90deg) scale(0.9); opacity: 0; }
            100% { transform: rotateX(0deg) scale(1); opacity: 1; }
        }
    </style>
</head>
<body class="text-slate-800 flex flex-col justify-between min-h-screen">

    <!-- Top Header Navigation -->
    <header class="bg-white/90 backdrop-blur-md border-b border-sky-100 sticky top-0 z-30 shadow-sm">
        <div class="max-w-6xl mx-auto px-4 py-3 flex items-center justify-between">
            <div class="flex items-center gap-3 cursor-pointer" onclick="goToHome()">
                <div class="w-11 h-11 bg-gradient-to-tr from-blue-500 to-indigo-600 rounded-2xl flex items-center justify-center text-2xl shadow-md text-white font-bold">
                    🎯
                </div>
                <div>
                    <h1 class="text-xl md:text-2xl font-black text-slate-800 leading-none">אתגר קריאה</h1>
                    <p class="text-xs text-sky-600 font-semibold mt-0.5">כיתה ב' • שטף ודיוק</p>
                </div>
            </div>

            <!-- Stats and Controls Header Widgets -->
            <div class="flex items-center gap-3">
                <div id="stars-counter" class="hidden bg-amber-50 border border-amber-200 text-amber-700 px-3 py-1.5 rounded-full text-sm font-bold flex items-center gap-1.5 shadow-sm">
                    <span class="text-lg">⭐</span>
                    <span id="stars-count">0</span>
                    <span class="text-xs font-normal text-amber-600 hidden sm:inline">מילים שנקראו</span>
                </div>
                
                <button onclick="toggleAudio()" id="audio-toggle-btn" class="p-2 rounded-xl bg-slate-100 hover:bg-slate-200 text-slate-700 text-lg transition" title="צלילים והקראה">
                    🔊
                </button>
                
                <button onclick="goToHome()" id="home-btn" class="hidden px-3 py-1.5 bg-slate-100 hover:bg-slate-200 text-slate-700 text-sm font-bold rounded-xl transition flex items-center gap-1">
                    <span>🏠</span>
                    <span class="hidden sm:inline">בית</span>
                </button>
            </div>
        </div>
    </header>

    <main class="max-w-5xl mx-auto px-4 py-6 flex-grow flex flex-col justify-center w-full">

        <!-- ================= HOME SCREEN ================= -->
        <section id="home-screen" class="flex flex-col items-center text-center space-y-8 my-auto">
            
            <!-- Hero Badge & Title -->
            <div class="space-y-4 max-w-2xl">
                <div class="inline-flex items-center justify-center w-24 h-24 bg-gradient-to-tr from-amber-400 via-orange-400 to-red-500 rounded-3xl text-6xl shadow-xl target-glow mb-2 text-white">
                    🎯
                </div>
                <h2 class="text-3xl md:text-5xl font-black text-slate-800 tracking-tight">
                    אתגר קריאה של כיתה ב'
                </h2>
                <p class="text-base md:text-xl text-slate-600 font-medium leading-relaxed">
                    מתרגלים שטף ודיוק בשלושה שלבים קצרים ומדורגים בתחילת היום!
                </p>
            </div>

            <!-- Steps Visual Roadmap -->
            <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 w-full max-w-3xl py-2">
                <div class="bg-white/90 p-5 rounded-3xl border-2 border-emerald-200 text-center shadow-md flex flex-col items-center justify-center space-y-2">
                    <span class="text-3xl">🟢</span>
                    <span class="text-xs font-black text-emerald-800 bg-emerald-100 px-3 py-1 rounded-full">שלב ראשון</span>
                    <h3 class="font-extrabold text-slate-800 text-base">מילים קלות</h3>
                </div>
                <div class="bg-white/90 p-5 rounded-3xl border-2 border-amber-200 text-center shadow-md flex flex-col items-center justify-center space-y-2">
                    <span class="text-3xl">🟡</span>
                    <span class="text-xs font-black text-amber-800 bg-amber-100 px-3 py-1 rounded-full">שלב שני</span>
                    <h3 class="font-extrabold text-slate-800 text-base">מילים בינוניות</h3>
                </div>
                <div class="bg-white/90 p-5 rounded-3xl border-2 border-rose-200 text-center shadow-md flex flex-col items-center justify-center space-y-2">
                    <span class="text-3xl">🔴</span>
                    <span class="text-xs font-black text-rose-800 bg-rose-100 px-3 py-1 rounded-full">שלב שלישי</span>
                    <h3 class="font-extrabold text-slate-800 text-base">מילים מאתגרות</h3>
                </div>
            </div>

            <!-- Main Start Challenge Button -->
            <button onclick="startChallenge()" class="card-pop w-full max-w-xl bg-gradient-to-r from-emerald-500 via-teal-600 to-indigo-600 hover:from-emerald-600 hover:to-indigo-700 text-white p-5 rounded-3xl shadow-xl flex items-center justify-center gap-3 text-center font-black text-xl md:text-2xl transition">
                <span>🚀</span>
                <span>התחל את אתגר הקריאה (שלב ראשון)</span>
            </button>
            
        </section>


        <!-- ================= GAME / CHALLENGE SCREEN ================= -->
        <section id="game-screen" class="hidden flex-col space-y-6 my-auto">
            
            <!-- Current Step Info Bar & Stepper Indicator -->
            <div class="bg-white rounded-2xl p-4 border border-slate-200 shadow-sm flex flex-col md:flex-row items-center justify-between gap-4">
                <div class="flex items-center gap-3 w-full md:w-auto">
                    <span id="level-badge-icon" class="text-3xl">🟢</span>
                    <div>
                        <span id="step-badge" class="text-xs font-black px-2.5 py-0.5 rounded-full bg-emerald-100 text-emerald-800">שלב 1 מתוך 3</span>
                        <h2 id="level-title" class="font-black text-slate-800 text-xl mt-0.5">שלב ראשון: מילים קלות</h2>
                    </div>
                </div>

                <!-- 3 Steps Visual Progress Indicator -->
                <div class="flex items-center gap-2 bg-slate-50 px-4 py-2 rounded-2xl border border-slate-200">
                    <div id="step-dot-1" class="w-8 h-8 rounded-full flex items-center justify-center text-xs font-black bg-emerald-500 text-white shadow-sm transition-all">1</div>
                    <div class="w-6 h-0.5 bg-slate-300"></div>
                    <div id="step-dot-2" class="w-8 h-8 rounded-full flex items-center justify-center text-xs font-black bg-slate-200 text-slate-500 transition-all">2</div>
                    <div class="w-6 h-0.5 bg-slate-300"></div>
                    <div id="step-dot-3" class="w-8 h-8 rounded-full flex items-center justify-center text-xs font-black bg-slate-200 text-slate-500 transition-all">3</div>
                </div>

                <!-- Stopwatch / Timer Utility -->
                <div class="flex items-center gap-2">
                    <div id="timer-box" class="bg-slate-100 border border-slate-200 px-3 py-1.5 rounded-xl flex items-center gap-2 font-mono text-sm text-slate-700">
                        <span>⏱️</span>
                        <span id="timer-display" class="font-bold">00:00</span>
                    </div>
                    <button onclick="toggleTimer()" id="timer-toggle-btn" class="text-xs bg-slate-200 hover:bg-slate-300 font-bold text-slate-700 px-3 py-2 rounded-xl transition">
                        טיימר
                    </button>
                </div>
            </div>

            <!-- THE 3 WORDS DISPLAY CARDS CONTAINER -->
            <div id="words-container" class="grid grid-cols-1 md:grid-cols-3 gap-6 py-2">
                
                <!-- Word Card 1 -->
                <div id="card-0" class="card-pop shuffle-anim bg-white rounded-3xl p-6 md:p-8 border-4 border-sky-200 shadow-xl flex flex-col items-center justify-between text-center relative min-h-[220px] md:min-h-[260px]">
                    <span class="absolute top-4 right-4 w-8 h-8 rounded-full bg-sky-100 text-sky-700 text-sm font-black flex items-center justify-center">1</span>
                    <button onclick="speakWord(0)" class="absolute top-4 left-4 p-2 text-slate-400 hover:text-sky-600 transition text-lg" title="הקרא מילה">🔊</button>
                    
                    <div class="my-auto py-4">
                        <span id="word-text-0" class="nikud-text text-4xl sm:text-5xl md:text-6xl font-black text-slate-900 tracking-wide select-text">
                            תּוּת
                        </span>
                    </div>

                    <button onclick="toggleWordDone(0)" id="btn-done-0" class="w-full py-3 px-4 rounded-2xl bg-sky-50 hover:bg-sky-100 text-sky-700 font-bold border border-sky-200 transition flex items-center justify-center gap-2 text-base">
                        <span>✓</span>
                        <span>קראתי נכון!</span>
                    </button>
                </div>

                <!-- Word Card 2 -->
                <div id="card-1" class="card-pop shuffle-anim bg-white rounded-3xl p-6 md:p-8 border-4 border-indigo-200 shadow-xl flex flex-col items-center justify-between text-center relative min-h-[220px] md:min-h-[260px]">
                    <span class="absolute top-4 right-4 w-8 h-8 rounded-full bg-indigo-100 text-indigo-700 text-sm font-black flex items-center justify-center">2</span>
                    <button onclick="speakWord(1)" class="absolute top-4 left-4 p-2 text-slate-400 hover:text-indigo-600 transition text-lg" title="הקרא מילה">🔊</button>
                    
                    <div class="my-auto py-4">
                        <span id="word-text-1" class="nikud-text text-4xl sm:text-5xl md:text-6xl font-black text-slate-900 tracking-wide select-text">
                            חֻלְצָה
                        </span>
                    </div>

                    <button onclick="toggleWordDone(1)" id="btn-done-1" class="w-full py-3 px-4 rounded-2xl bg-indigo-50 hover:bg-indigo-100 text-indigo-700 font-bold border border-indigo-200 transition flex items-center justify-center gap-2 text-base">
                        <span>✓</span>
                        <span>קראתי נכון!</span>
                    </button>
                </div>

                <!-- Word Card 3 -->
                <div id="card-2" class="card-pop shuffle-anim bg-white rounded-3xl p-6 md:p-8 border-4 border-purple-200 shadow-xl flex flex-col items-center justify-between text-center relative min-h-[220px] md:min-h-[260px]">
                    <span class="absolute top-4 right-4 w-8 h-8 rounded-full bg-purple-100 text-purple-700 text-sm font-black flex items-center justify-center">3</span>
                    <button onclick="speakWord(2)" class="absolute top-4 left-4 p-2 text-slate-400 hover:text-purple-600 transition text-lg" title="הקרא מילה">🔊</button>
                    
                    <div class="my-auto py-4">
                        <span id="word-text-2" class="nikud-text text-4xl sm:text-5xl md:text-6xl font-black text-slate-900 tracking-wide select-text">
                            סַרְגֵּל
                        </span>
                    </div>

                    <button onclick="toggleWordDone(2)" id="btn-done-2" class="w-full py-3 px-4 rounded-2xl bg-purple-50 hover:bg-purple-100 text-purple-700 font-bold border border-purple-200 transition flex items-center justify-center gap-2 text-base">
                        <span>✓</span>
                        <span>קראתי נכון!</span>
                    </button>
                </div>

            </div>

            <!-- MAIN ACTION BUTTONS FOR STEP CONTROLS -->
            <div class="flex flex-col sm:flex-row items-center justify-center gap-4 pt-2">
                
                <!-- SHUFFLE FOR NEXT STUDENT BUTTON -->
                <button onclick="shuffleNextRound()" class="card-pop w-full sm:w-auto bg-gradient-to-r from-amber-500 to-orange-500 hover:from-amber-600 hover:to-orange-600 text-white font-black text-lg md:text-xl py-4 px-8 rounded-2xl shadow-lg flex items-center justify-center gap-3 transition">
                    <span class="text-2xl">🔄</span>
                    <span>ערבב 3 מילים לתלמיד הבא</span>
                </button>

                <!-- NEXT STEP OR VICTORY BUTTON -->
                <button onclick="goToNextStep()" id="next-step-btn" class="card-pop w-full sm:w-auto bg-indigo-600 hover:bg-indigo-700 text-white font-black text-lg md:text-xl py-4 px-8 rounded-2xl shadow-lg flex items-center justify-center gap-3 transition">
                    <span>עבור לשלב השני ←</span>
                </button>

            </div>

            <!-- Progress tracker text -->
            <div class="text-center text-xs sm:text-sm text-slate-500 font-semibold pt-1">
                נשארו <span id="remaining-words-count" class="text-slate-800 font-bold">0</span> מילים במאגר השלב הנוכחי
            </div>

        </section>


        <!-- ================= VICTORY & CELEBRATION SCREEN ================= -->
        <section id="victory-screen" class="hidden flex-col items-center text-center space-y-8 my-auto py-8">
            
            <div class="space-y-4 max-w-2xl">
                
                <!-- Trophy & Clapping Icons Header -->
                <div class="flex items-center justify-center gap-4 mb-2">
                    <span class="text-6xl md:text-7xl animate-bounce">👏</span>
                    <div class="w-28 h-28 bg-gradient-to-tr from-amber-300 via-amber-400 to-yellow-500 rounded-full flex items-center justify-center text-6xl shadow-2xl border-4 border-yellow-200">
                        🏆
                    </div>
                    <span class="text-6xl md:text-7xl animate-bounce" style="animation-delay: 0.15s">👏</span>
                </div>

                <!-- Main Victory Message requested by user -->
                <h2 class="text-4xl md:text-6xl font-black text-slate-900 tracking-tight leading-tight">
                    הידד!! אני אלוף/ת הקריאה
                </h2>
                
                <p class="text-lg md:text-2xl text-slate-600 font-bold">
                    סיימתם בהצלחה את כל 3 השלבים של אתגר הקריאה! 🌟
                </p>

            </div>

            <!-- Champion Summary Stats Card -->
            <div class="bg-white rounded-3xl p-6 md:p-8 border-2 border-amber-200 shadow-xl max-w-md w-full space-y-4 text-right">
                <h3 class="text-lg font-black text-slate-800 border-b border-slate-100 pb-3 flex items-center justify-between">
                    <span>סיכום אתגר הקריאה הכיתתי</span>
                    <span class="text-2xl">🎯</span>
                </h3>
                
                <div class="space-y-3">
                    <div class="flex justify-between items-center text-base">
                        <span class="text-slate-600">שלבים שהושלמו:</span>
                        <span class="font-black text-slate-800">3 מתוך 3 (מלא)</span>
                    </div>
                    <div class="flex justify-between items-center text-base">
                        <span class="text-slate-600">סך מילים שנקראו:</span>
                        <span id="summary-words-read" class="font-black text-amber-600 text-xl">0</span>
                    </div>
                    <div class="flex justify-between items-center text-base">
                        <span class="text-slate-600">דירוג קריאה:</span>
                        <span id="summary-stars" class="font-black text-amber-500 text-xl">🌟⭐🌟⭐🌟</span>
                    </div>
                </div>
            </div>

            <!-- Action Buttons on Victory -->
            <div class="flex flex-col sm:flex-row gap-4 w-full max-w-md">
                <button onclick="startChallenge()" class="card-pop flex-1 py-4 px-6 bg-gradient-to-r from-emerald-500 to-teal-600 hover:from-emerald-600 hover:to-teal-700 text-white font-black rounded-2xl shadow-lg transition text-lg flex items-center justify-center gap-2">
                    <span>🔄</span>
                    <span>סבב חדש מהתחלה</span>
                </button>

                <button onclick="goToHome()" class="card-pop flex-1 py-4 px-6 bg-slate-800 hover:bg-slate-900 text-white font-bold rounded-2xl shadow-md transition text-lg flex items-center justify-center gap-2">
                    <span>🏠</span>
                    <span>דף הבית</span>
                </button>
            </div>

        </section>

    </main>

    <!-- Footer -->
    <footer class="py-4 text-center text-xs text-slate-400 font-medium">
        אתגר קריאה יומי • כיתה ב' • מבוסס תכנית הלימודים בשפה
    </footer>

    <script>
        /* FULL DATABASE OF 76 WORDS CATEGORIZED INTO 3 STEPS */
        const ALL_WORDS = {
            1: {
                name: "שלב ראשון: מילים קלות",
                badgeIcon: "🟢",
                badgeClass: "bg-emerald-100 text-emerald-800",
                dotBg: "bg-emerald-500 text-white",
                words: [
                    "תּוּת", "דָּג", "יֶלֶד", "גּוּר", "סוּס", "שֶׁמֶשׁ", "בַּיִת", "כַּדּוּר", "רָץ", "עֵץ", 
                    "מַיִם", "פֶּרַח", "עֻגָה", "צָב", "חוּם", "שּׁוּק", "אָח", "לוּחַ", "סוֹד", "כּוֹס", 
                    "רוּחַ", "שָׁר", "חָתוּל", "שּׁוּעָל", "סוּפָה", "מָטָר"
                ]
            },
            2: {
                name: "שלב שני: מילים בינוניות",
                badgeIcon: "🟡",
                badgeClass: "bg-amber-100 text-amber-800",
                dotBg: "bg-amber-500 text-white",
                words: [
                    "חֻלְצָה", "סַרְגֵּל", "עָנָן", "תֻּכִּי", "מֶלֶךְ", "קֻפְסָה", "בַּלּוֹן", "דֻּבּוֹן", "שֻׁלְחָן", "סֻלָּם", 
                    "תַּפּוּחַ", "כֻּרְסָה", "מַחְשֵׁב", "לָלוּן", "גּוֹזָל", "מִפְתָּח", "חֻלְצוֹת", "עִפַּרוֹן", "יָרֵחַ", "מַמְתָּק", 
                    "רְחוֹב", "מַפְתֵּחַ", "תַּרְמִיל", "שׁוֹפָר", "צְהֻבִּים", "כּוֹכָב", "מַתָּנָה", "מֻפְלָא"
                ]
            },
            3: {
                name: "שלב שלישי: מילים מאתגרות",
                badgeIcon: "🔴",
                badgeClass: "bg-rose-100 text-rose-800",
                dotBg: "bg-rose-500 text-white",
                words: [
                    "מַחְבֶּרֶת", "סֻכָּרִיָּה", "כַּדּוּרַגְלָן", "מִשְׁפָּחָה", "תַּלְמִידִים", "מֻפְתָּעִים", "סַבְתוּשׁ", "יֹום הוּלֶדֶת", "חֲמוּדוֹת", "מֻמְחִיּוּת", 
                    "מִשְׁקָפַיִם", "קֻפְסָאוֹת", "סֻכָּרְיּוֹת", "מַחְשֵׁבוֹן", "צָהֳרַיִם", "מַסְכִּימִים", "גְּבוּרָה", "שֻׁתָּפִים", "כַּדּוּרְעַף", "מִסְפָּרַיִם", 
                    "עַגְבָנִיָּה", "תַּשְׁבֵּץ"
                ]
            }
        };

        // Sequential Step State
        let currentStep = 1;
        let poolWords = [];
        let currentTrio = [];
        let wordDoneStates = [false, false, false];
        let totalWordsReadCount = 0;
        let isAudioEnabled = true;

        // Timer state
        let timerInterval = null;
        let timerSeconds = 0;
        let isTimerRunning = false;

        const audioCtx = new (window.AudioContext || window.webkitAudioContext)();

        function playSoundEffect(type) {
            if (!isAudioEnabled) return;
            try {
                if (audioCtx.state === 'suspended') {
                    audioCtx.resume();
                }

                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.connect(gain);
                gain.connect(audioCtx.destination);

                const now = audioCtx.currentTime;

                if (type === 'check') {
                    osc.type = 'sine';
                    osc.frequency.setValueAtTime(523.25, now);
                    osc.frequency.exponentialRampToValueAtTime(659.25, now + 0.1);
                    gain.gain.setValueAtTime(0.15, now);
                    gain.gain.exponentialRampToValueAtTime(0.01, now + 0.25);
                    osc.start(now);
                    osc.stop(now + 0.25);
                } else if (type === 'shuffle') {
                    osc.type = 'triangle';
                    osc.frequency.setValueAtTime(300, now);
                    osc.frequency.exponentialRampToValueAtTime(700, now + 0.15);
                    gain.gain.setValueAtTime(0.1, now);
                    gain.gain.exponentialRampToValueAtTime(0.01, now + 0.2);
                    osc.start(now);
                    osc.stop(now + 0.2);
                } else if (type === 'fanfare') {
                    const notes = [523.25, 659.25, 783.99, 1046.50];
                    notes.forEach((freq, idx) => {
                        const noteOsc = audioCtx.createOscillator();
                        const noteGain = audioCtx.createGain();
                        noteOsc.connect(noteGain);
                        noteGain.connect(audioCtx.destination);
                        noteOsc.type = 'sine';
                        noteOsc.frequency.setValueAtTime(freq, now + idx * 0.12);
                        noteGain.gain.setValueAtTime(0.2, now + idx * 0.12);
                        noteGain.gain.exponentialRampToValueAtTime(0.01, now + idx * 0.12 + 0.3);
                        noteOsc.start(now + idx * 0.12);
                        noteOsc.stop(now + idx * 0.12 + 0.3);
                    });
                }
            } catch (e) {
                console.log("Audio not supported or blocked");
            }
        }

        function toggleAudio() {
            isAudioEnabled = !isAudioEnabled;
            const btn = document.getElementById('audio-toggle-btn');
            btn.innerHTML = isAudioEnabled ? '🔊' : '🔇';
            btn.classList.toggle('opacity-50', !isAudioEnabled);
        }

        function speakWord(cardIndex) {
            if (!('speechSynthesis' in window)) return;
            const word = currentTrio[cardIndex];
            if (!word) return;

            window.speechSynthesis.cancel();
            const cleanWord = word.replace(/[\u0591-\u05C7]/g, ""); 
            const utterance = new SpeechSynthesisUtterance(cleanWord);
            utterance.lang = 'he-IL';
            utterance.rate = 0.85;
            window.speechSynthesis.speak(utterance);
        }

        function goToHome() {
            stopTimer();
            document.getElementById('home-screen').classList.remove('hidden');
            document.getElementById('game-screen').classList.add('hidden');
            document.getElementById('victory-screen').classList.add('hidden');
            document.getElementById('stars-counter').classList.add('hidden');
            document.getElementById('home-btn').classList.add('hidden');
        }

        function startChallenge() {
            currentStep = 1;
            totalWordsReadCount = 0;
            updateStarsDisplay();

            document.getElementById('home-screen').classList.add('hidden');
            document.getElementById('victory-screen').classList.add('hidden');
            document.getElementById('game-screen').classList.remove('hidden');
            document.getElementById('game-screen').classList.add('flex');
            document.getElementById('stars-counter').classList.remove('hidden');
            document.getElementById('home-btn').classList.remove('hidden');

            loadStep(1);
        }

        function loadStep(stepNum) {
            currentStep = stepNum;
            const stepData = ALL_WORDS[stepNum];

            // Update UI step indicators
            document.getElementById('level-title').textContent = stepData.name;
            document.getElementById('level-badge-icon').textContent = stepData.badgeIcon;
            
            const badgeEl = document.getElementById('step-badge');
            badgeEl.textContent = `שלב ${stepNum} מתוך 3`;
            badgeEl.className = `text-xs font-black px-2.5 py-0.5 rounded-full ${stepData.badgeClass}`;

            // Update dots
            for (let i = 1; i <= 3; i++) {
                const dot = document.getElementById(`step-dot-${i}`);
                if (i === stepNum) {
                    dot.className = `w-8 h-8 rounded-full flex items-center justify-center text-xs font-black ${stepData.dotBg} shadow-md scale-110`;
                } else if (i < stepNum) {
                    dot.className = "w-8 h-8 rounded-full flex items-center justify-center text-xs font-black bg-emerald-100 text-emerald-800";
                } else {
                    dot.className = "w-8 h-8 rounded-full flex items-center justify-center text-xs font-black bg-slate-200 text-slate-500";
                }
            }

            // Next Step button text
            const nextBtn = document.getElementById('next-step-btn');
            if (stepNum === 1) {
                nextBtn.innerHTML = "<span>עבור לשלב השני ←</span>";
                nextBtn.className = "card-pop w-full sm:w-auto bg-indigo-600 hover:bg-indigo-700 text-white font-black text-lg md:text-xl py-4 px-8 rounded-2xl shadow-lg flex items-center justify-center gap-3 transition";
            } else if (stepNum === 2) {
                nextBtn.innerHTML = "<span>עבור לשלב השלישי ←</span>";
                nextBtn.className = "card-pop w-full sm:w-auto bg-rose-600 hover:bg-rose-700 text-white font-black text-lg md:text-xl py-4 px-8 rounded-2xl shadow-lg flex items-center justify-center gap-3 transition";
            } else {
                nextBtn.innerHTML = "<span>סיום והגעת לניצחון! 🏆</span>";
                nextBtn.className = "card-pop w-full sm:w-auto bg-emerald-600 hover:bg-emerald-700 text-white font-black text-lg md:text-xl py-4 px-8 rounded-2xl shadow-lg flex items-center justify-center gap-3 transition";
            }

            // Pool setup for this step
            poolWords = [...stepData.words];
            poolWords.sort(() => Math.random() - 0.5);

            shuffleNextRound();
        }

        function goToNextStep() {
            if (currentStep < 3) {
                loadStep(currentStep + 1);
            } else {
                triggerVictoryScreen();
            }
        }

        function shuffleNextRound() {
            playSoundEffect('shuffle');
            wordDoneStates = [false, false, false];

            if (poolWords.length < 3) {
                poolWords = [...ALL_WORDS[currentStep].words];
                poolWords.sort(() => Math.random() - 0.5);
            }

            currentTrio = [];
            for (let i = 0; i < 3; i++) {
                const randomIndex = Math.floor(Math.random() * poolWords.length);
                currentTrio.push(poolWords[randomIndex]);
                poolWords.splice(randomIndex, 1);
            }

            renderTrioCards();
        }

        function renderTrioCards() {
            for (let i = 0; i < 3; i++) {
                const cardEl = document.getElementById(`card-${i}`);
                const wordTextEl = document.getElementById(`word-text-${i}`);

                cardEl.classList.remove('shuffle-anim');
                void cardEl.offsetWidth;
                cardEl.classList.add('shuffle-anim');

                wordTextEl.textContent = currentTrio[i];
                resetCardStyle(i);
            }

            document.getElementById('remaining-words-count').textContent = poolWords.length;
        }

        function toggleWordDone(index) {
            wordDoneStates[index] = !wordDoneStates[index];
            const cardEl = document.getElementById(`card-${index}`);
            const btnDone = document.getElementById(`btn-done-${index}`);

            if (wordDoneStates[index]) {
                playSoundEffect('check');
                totalWordsReadCount++;
                updateStarsDisplay();

                cardEl.classList.add('bg-emerald-50', 'border-emerald-400');
                btnDone.className = "w-full py-3 px-4 rounded-2xl bg-emerald-500 text-white font-black transition flex items-center justify-center gap-2 text-base shadow-md";
                btnDone.innerHTML = "<span>✓</span><span>נקרא בהצלחה!</span>";
            } else {
                if (totalWordsReadCount > 0) totalWordsReadCount--;
                updateStarsDisplay();
                resetCardStyle(index);
            }
        }

        function resetCardStyle(index) {
            const cardEl = document.getElementById(`card-${index}`);
            const btnDone = document.getElementById(`btn-done-${index}`);
            
            cardEl.className = "card-pop shuffle-anim bg-white rounded-3xl p-6 md:p-8 border-4 border-sky-200 shadow-xl flex flex-col items-center justify-between text-center relative min-h-[220px] md:min-h-[260px]";
            btnDone.className = "w-full py-3 px-4 rounded-2xl bg-sky-50 hover:bg-sky-100 text-sky-700 font-bold border border-sky-200 transition flex items-center justify-center gap-2 text-base";
            btnDone.innerHTML = "<span>✓</span><span>קראתי נכון!</span>";
        }

        function updateStarsDisplay() {
            document.getElementById('stars-count').textContent = totalWordsReadCount;
        }

        function toggleTimer() {
            if (isTimerRunning) {
                stopTimer();
            } else {
                startTimer();
            }
        }

        function startTimer() {
            isTimerRunning = true;
            document.getElementById('timer-toggle-btn').textContent = "עצור טיימר";
            document.getElementById('timer-toggle-btn').className = "text-xs bg-rose-100 hover:bg-rose-200 font-bold text-rose-700 px-3 py-2 rounded-xl transition";
            
            timerInterval = setInterval(() => {
                timerSeconds++;
                const mins = String(Math.floor(timerSeconds / 60)).padStart(2, '0');
                const secs = String(timerSeconds % 60).padStart(2, '0');
                document.getElementById('timer-display').textContent = `${mins}:${secs}`;
            }, 1000);
        }

        function stopTimer() {
            isTimerRunning = false;
            clearInterval(timerInterval);
            document.getElementById('timer-toggle-btn').textContent = "הפעל טיימר";
            document.getElementById('timer-toggle-btn').className = "text-xs bg-slate-200 hover:bg-slate-300 font-bold text-slate-700 px-3 py-2 rounded-xl transition";
        }

        function triggerVictoryScreen() {
            stopTimer();
            playSoundEffect('fanfare');

            document.getElementById('game-screen').classList.add('hidden');
            document.getElementById('victory-screen').classList.remove('hidden');
            document.getElementById('victory-screen').classList.add('flex');

            document.getElementById('summary-words-read').textContent = totalWordsReadCount + " מילים";

            if (typeof confetti === 'function') {
                const duration = 3 * 1000;
                const end = Date.now() + duration;

                (function frame() {
                    confetti({
                        particleCount: 6,
                        angle: 60,
                        spread: 60,
                        origin: { x: 0 },
                        colors: ['#3b82f6', '#10b981', '#f59e0b', '#ec4899']
                    });
                    confetti({
                        particleCount: 6,
                        angle: 120,
                        spread: 60,
                        origin: { x: 1 },
                        colors: ['#3b82f6', '#10b981', '#f59e0b', '#ec4899']
                    });

                    if (Date.now() < end) {
                        requestAnimationFrame(frame);
                    }
                }());
            }
        }

        window.onload = function() {
            console.log("3-Step Reading Challenge Application Ready!");
        };
    </script>
</body>
</html>
