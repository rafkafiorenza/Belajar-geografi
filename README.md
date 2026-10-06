<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GeoResearch Master - Learning Portal Geografi</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: #f8fafc;
        }

        /* Perspective and 3D Flip Effects for Flashcards */
        .perspective-1000 {
            perspective: 1000px;
        }
        .transform-style-3d {
            transform-style: preserve-3d;
            transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .backface-hidden {
            backface-visibility: hidden;
            -webkit-backface-visibility: hidden;
        }
        .rotate-y-180 {
            transform: rotateY(180deg);
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f5f9;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 9999px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }

        /* Glassmorphic Cards */
        .glass-card {
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.5);
        }
    </style>
</head>
<body class="text-slate-800 min-h-screen flex flex-col">

    <!-- Top Header / Navigation -->
    <header class="sticky top-0 z-50 bg-gradient-to-r from-violet-600 via-indigo-600 to-pink-500 text-white shadow-lg">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <div class="flex items-center space-x-3 cursor-pointer" onclick="switchTab('materi')">
                    <div class="p-2 bg-white/20 backdrop-blur-md rounded-xl">
                        <i class="fa-solid font-bold fa-earth-americas text-2xl text-yellow-300"></i>
                    </div>
                    <div>
                        <h1 class="font-black text-lg sm:text-xl tracking-tight leading-tight">GeoResearch <span class="text-yellow-300">Master</span></h1>
                        <p class="text-xs text-violet-100 font-medium">Kisi-Kisi Penelitian Geografi (50 Soal)</p>
                    </div>
                </div>

                <!-- Navigation Tabs -->
                <nav class="hidden md:flex space-x-1 bg-black/10 p-1.5 rounded-2xl backdrop-blur-md">
                    <button onclick="switchTab('materi')" id="nav-materi" class="nav-btn px-4 py-2 rounded-xl text-sm font-bold transition-all duration-200 bg-white text-indigo-700 shadow-md">
                        <i class="fa-solid fa-book-open mr-1.5"></i> Ringkasan Materi
                    </button>
                    <button onclick="switchTab('flashcard')" id="nav-flashcard" class="nav-btn px-4 py-2 rounded-xl text-sm font-bold transition-all duration-200 text-white hover:bg-white/10">
                        <i class="fa-solid fa-clone mr-1.5"></i> Kartu Hafalan
                    </button>
                    <button onclick="switchTab('kuis')" id="nav-kuis" class="nav-btn px-4 py-2 rounded-xl text-sm font-bold transition-all duration-200 text-white hover:bg-white/10">
                        <i class="fa-solid fa-pen-to-square mr-1.5"></i> Kuis (50 Soal)
                    </button>
                    <button onclick="switchTab('skor')" id="nav-skor" class="nav-btn px-4 py-2 rounded-xl text-sm font-bold transition-all duration-200 text-white hover:bg-white/10">
                        <i class="fa-solid fa-chart-pie mr-1.5"></i> Progres & Hasil
                    </button>
                </nav>

                <!-- Mobile Menu Button -->
                <div class="md:hidden">
                    <button id="mobile-menu-btn" onclick="toggleMobileMenu()" class="p-2 rounded-lg bg-white/10 hover:bg-white/20 focus:outline-none">
                        <i class="fa-solid fa-bars text-xl"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Navigation Menu -->
        <div id="mobile-menu" class="hidden md:hidden bg-indigo-900/95 border-t border-white/10 px-4 pt-2 pb-4 space-y-2 backdrop-blur-md">
            <button onclick="switchTab('materi'); toggleMobileMenu()" class="w-full text-left px-4 py-2.5 rounded-xl text-sm font-bold bg-white/10 hover:bg-white/20">
                <i class="fa-solid fa-book-open mr-2 text-yellow-300"></i> Ringkasan Materi
            </button>
            <button onclick="switchTab('flashcard'); toggleMobileMenu()" class="w-full text-left px-4 py-2.5 rounded-xl text-sm font-bold bg-white/10 hover:bg-white/20">
                <i class="fa-solid fa-clone mr-2 text-yellow-300"></i> Kartu Hafalan
            </button>
            <button onclick="switchTab('kuis'); toggleMobileMenu()" class="w-full text-left px-4 py-2.5 rounded-xl text-sm font-bold bg-white/10 hover:bg-white/20">
                <i class="fa-solid fa-pen-to-square mr-2 text-yellow-300"></i> Kuis (50 Soal)
            </button>
            <button onclick="switchTab('skor'); toggleMobileMenu()" class="w-full text-left px-4 py-2.5 rounded-xl text-sm font-bold bg-white/10 hover:bg-white/20">
                <i class="fa-solid fa-chart-pie mr-2 text-yellow-300"></i> Progres & Hasil
            </button>
        </div>
    </header>

    <!-- Main Content Body -->
    <main class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-8">

        <!-- TAB 1: MATERI RINGKASAN (13 KISI-KISI) -->
        <section id="tab-materi" class="tab-content space-y-8">
            <!-- Hero Banner -->
            <div class="bg-gradient-to-r from-amber-400 via-rose-500 to-purple-600 rounded-3xl p-6 sm:p-8 text-white shadow-xl relative overflow-hidden">
                <div class="relative z-10 max-w-2xl">
                    <span class="inline-block px-3 py-1 bg-white/20 backdrop-blur-md text-xs font-bold rounded-full mb-3 uppercase tracking-wider">Modul Pembelajaran Interaktif</span>
                    <h2 class="text-2xl sm:text-4xl font-extrabold leading-tight mb-2">Panduan Super Lengkap Penelitian Geografi 🌍</h2>
                    <p class="text-amber-100 text-sm sm:text-base font-medium">Pelajari 13 poin kunci kisi-kisi ujian geografi dengan cepat, intuitif, dan siap menghadapi 50 soal studi kasus!</p>
                </div>
                <div class="absolute -right-8 -bottom-8 opacity-20 text-9xl">
                    <i class="fa-solid fa-compass"></i>
                </div>
            </div>

            <!-- Search & Filter Bar -->
            <div class="flex flex-col sm:flex-row items-center justify-between gap-4">
                <div class="relative w-full sm:w-96">
                    <i class="fa-solid fa-magnifying-glass absolute left-4 top-1/2 -translate-y-1/2 text-slate-400"></i>
                    <input type="text" id="materi-search" oninput="filterMateri()" placeholder="Cari topik (contoh: BMKG, Variabel, Citra)..." class="w-full pl-11 pr-4 py-3 rounded-2xl border border-slate-200 bg-white shadow-sm focus:outline-none focus:ring-2 focus:ring-indigo-500 text-sm">
                </div>
                <div class="text-sm font-semibold text-slate-500">
                    Menampilkan <span id="materi-count" class="text-indigo-600 font-bold">13</span> Topik Kisi-Kisi
                </div>
            </div>

            <!-- Material Grid Container -->
            <div id="materi-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- Cards injected via JavaScript -->
            </div>
        </section>

        <!-- TAB 2: KARTU HAFALAN (FLASHCARDS) -->
        <section id="tab-flashcard" class="tab-content hidden space-y-6">
            <div class="text-center max-w-xl mx-auto">
                <h2 class="text-2xl sm:text-3xl font-extrabold text-slate-800 mb-2">🎴 Kartu Hafalan (Flashcards)</h2>
                <p class="text-slate-600 text-sm">Klik kartu untuk memutar dan melihat definisi. Gunakan navigasi untuk berpindah kartu!</p>
            </div>

            <!-- Controls & Counter -->
            <div class="max-w-2xl mx-auto flex items-center justify-between bg-white p-4 rounded-2xl shadow-sm border border-slate-200">
                <div class="text-xs sm:text-sm font-bold text-slate-600">
                    Kartu ke <span id="fc-current-index" class="text-indigo-600 font-black text-base">1</span> dari <span id="fc-total-count" class="font-black text-base">13</span>
                </div>
                <div class="flex items-center space-x-2">
                    <button onclick="shuffleFlashcards()" class="px-3 py-1.5 text-xs font-bold bg-slate-100 hover:bg-slate-200 text-slate-700 rounded-xl transition">
                        <i class="fa-solid fa-shuffle mr-1"></i> Acak
                    </button>
                    <button onclick="resetFlashcards()" class="px-3 py-1.5 text-xs font-bold bg-indigo-50 hover:bg-indigo-100 text-indigo-600 rounded-xl transition">
                        <i class="fa-solid fa-rotate-left mr-1"></i> Reset
                    </button>
                </div>
            </div>

            <!-- Interactive 3D Flashcard Container -->
            <div class="max-w-2xl mx-auto perspective-1000 my-8">
                <div id="flashcard-element" onclick="flipCard()" class="relative w-full h-80 sm:h-96 rounded-3xl cursor-pointer transform-style-3d shadow-2xl transition-all duration-500">
                    
                    <!-- Front Side -->
                    <div class="absolute inset-0 w-full h-full backface-hidden bg-gradient-to-br from-indigo-600 via-purple-600 to-pink-500 text-white rounded-3xl p-8 flex flex-col justify-between border-4 border-white/20">
                        <div class="flex justify-between items-center">
                            <span id="fc-badge-front" class="px-3 py-1 bg-white/20 backdrop-blur-md rounded-full text-xs font-bold tracking-wider">Topik #1</span>
                            <span class="text-xs bg-black/20 px-3 py-1 rounded-full text-indigo-100"><i class="fa-solid fa-hand-pointer mr-1"></i> Klik untuk memutar</span>
                        </div>
                        <div class="text-center my-auto">
                            <h3 id="fc-title-front" class="text-xl sm:text-2xl font-black leading-snug">Definisi & Konsep Penelitian Geografi</h3>
                        </div>
                        <div class="text-center text-xs text-indigo-200 font-semibold">
                            GeoResearch Flashcard System
                        </div>
                    </div>

                    <!-- Back Side -->
                    <div class="absolute inset-0 w-full h-full backface-hidden rotate-y-180 bg-white text-slate-800 rounded-3xl p-8 flex flex-col justify-between border-4 border-indigo-200 shadow-2xl">
                        <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                            <span id="fc-badge-back" class="px-3 py-1 bg-indigo-100 text-indigo-700 rounded-full text-xs font-extrabold">Penjelasan & Definisi</span>
                            <span class="text-xs text-slate-400"><i class="fa-solid fa-lightbulb text-yellow-500 mr-1"></i> Kunci Hafalan</span>
                        </div>
                        <div class="my-auto overflow-y-auto max-h-48 pr-2">
                            <p id="fc-text-back" class="text-slate-700 font-medium text-sm sm:text-base leading-relaxed">
                                Penelitian geografi adalah kegiatan ilmiah yang bertujuan memecahkan masalah keruangan (spasial) dan fenomena geosfer secara sistematis.
                            </p>
                        </div>
                        <div class="pt-3 border-t border-slate-100 flex justify-between items-center text-xs text-slate-500">
                            <span>Ingat kata kunci utamanya!</span>
                            <span class="text-indigo-600 font-bold"><i class="fa-solid fa-rotate mr-1"></i> Putar Kembali</span>
                        </div>
                    </div>

                </div>
            </div>

            <!-- Flashcard Navigation Buttons -->
            <div class="max-w-2xl mx-auto flex items-center justify-between gap-4">
                <button onclick="prevCard()" class="flex-1 py-3 px-6 bg-white border border-slate-200 text-slate-700 font-bold rounded-2xl hover:bg-slate-50 transition shadow-sm flex items-center justify-center">
                    <i class="fa-solid fa-arrow-left mr-2"></i> Sebelumnya
                </button>
                <button onclick="flipCard()" class="py-3 px-6 bg-indigo-600 text-white font-bold rounded-2xl hover:bg-indigo-700 transition shadow-md">
                    <i class="fa-solid fa-rotate"></i>
                </button>
                <button onclick="nextCard()" class="flex-1 py-3 px-6 bg-gradient-to-r from-indigo-600 to-pink-500 text-white font-bold rounded-2xl hover:opacity-95 transition shadow-md flex items-center justify-center">
                    Berikutnya <i class="fa-solid fa-arrow-right ml-2"></i>
                </button>
            </div>
        </section>

        <!-- TAB 3: KUIS INTERAKTIF (50 SOAL DALAM 2 PAKET) -->
        <section id="tab-kuis" class="tab-content hidden space-y-6">
            
            <!-- Quiz Info & Category Selector Header -->
            <div class="bg-white rounded-3xl p-6 border border-slate-200 shadow-sm flex flex-col md:flex-row items-center justify-between gap-4">
                <div class="space-y-2">
                    <div class="flex flex-wrap items-center gap-2">
                        <span class="px-3 py-1 bg-amber-100 text-amber-800 font-bold text-xs rounded-full">Kuis Interaktif 50 Soal</span>
                        <span class="px-3 py-1 bg-purple-100 text-purple-800 font-bold text-xs rounded-full">20 PG Kompleks (Pilih 3)</span>
                        <span class="px-3 py-1 bg-emerald-100 text-emerald-800 font-bold text-xs rounded-full">30 PG Tunggal</span>
                    </div>
                    <h2 class="text-xl sm:text-2xl font-black text-slate-800">Uji Pemahaman Kisi-Kisi Geografi</h2>
                    <p class="text-slate-500 text-xs sm:text-sm">Pilih Paket Soal di samping dan atur mode pembahasan langsung!</p>
                </div>

                <!-- Category Switcher Dropdown & Instant Answer Toggle -->
                <div class="flex flex-col sm:flex-row items-stretch sm:items-center gap-3 w-full md:w-auto">
                    <!-- Toggle Switch for Instant Answer Key -->
                    <div class="bg-indigo-50 p-3 rounded-2xl border border-indigo-100 flex items-center justify-between sm:justify-start space-x-3">
                        <div class="text-left">
                            <p class="text-xs font-black text-indigo-900"><i class="fa-solid fa-key text-amber-500 mr-1"></i> Kunci Langsung</p>
                            <p class="text-[10px] text-indigo-600">Tampilkan pembahasan saat dijawab</p>
                        </div>
                        <label class="relative inline-flex items-center cursor-pointer shrink-0">
                            <input type="checkbox" id="toggle-instant-answer" onchange="toggleInstantAnswerMode(this.checked)" class="sr-only peer" checked>
                            <div class="w-11 h-6 bg-slate-300 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-slate-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-indigo-600"></div>
                        </label>
                    </div>

                    <!-- Category Selector -->
                    <div class="bg-slate-50 p-3 rounded-2xl border border-slate-200 space-y-1.5 shrink-0">
                        <label for="quiz-category-select" class="block text-xs font-black text-slate-600 uppercase tracking-wider">
                            <i class="fa-solid fa-layer-group text-indigo-600 mr-1"></i> Pilih Paket Kuis:
                        </label>
                        <select id="quiz-category-select" onchange="changeQuizCategory(this.value)" class="w-full bg-white border border-slate-300 rounded-xl px-3 py-2 text-xs font-bold text-indigo-900 focus:outline-none focus:ring-2 focus:ring-indigo-500">
                            <option value="paket1" selected>Paket 1: Kisi-Kisi Penelitian Dasar (Soal 1-25)</option>
                            <option value="paket2">Paket 2: Terapan & Analisis Spasial (Soal 26-50)</option>
                            <option value="all">Semua Paket (Soal 1-50)</option>
                        </select>
                    </div>
                </div>
            </div>

            <!-- Quiz Progress Indicator Bar -->
            <div class="bg-white p-4 rounded-2xl border border-slate-200 shadow-sm flex items-center justify-between gap-4">
                <div class="flex-grow">
                    <div class="flex justify-between text-xs font-bold mb-1">
                        <span class="text-slate-600" id="quiz-package-label">Progres Menjawab (Paket 1)</span>
                        <span id="quiz-progress-text" class="text-indigo-600">0 / 25</span>
                    </div>
                    <div class="w-full bg-slate-100 h-3 rounded-full overflow-hidden border border-slate-200">
                        <div id="quiz-progress-bar" class="bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500 h-full w-0 transition-all duration-300"></div>
                    </div>
                </div>
            </div>

            <!-- Quiz Navigation Grid -->
            <div class="bg-white p-4 rounded-2xl border border-slate-200 shadow-sm">
                <div class="flex items-center justify-between mb-2">
                    <p class="text-xs font-bold text-slate-500 uppercase tracking-wider">Navigasi Nomor Soal:</p>
                    <span class="text-xs text-slate-400 italic">Klik nomor untuk melompat</span>
                </div>
                <div id="quiz-nav-grid" class="flex flex-wrap gap-2">
                    <!-- Nav buttons generated dynamically -->
                </div>
            </div>

            <!-- Active Question Container -->
            <div id="quiz-card-container" class="bg-white rounded-3xl border border-slate-200 shadow-lg p-6 sm:p-8 space-y-6">
                <!-- Question Details rendered here -->
            </div>

            <!-- Bottom Navigation for Quiz -->
            <div class="flex items-center justify-between gap-4">
                <button onclick="prevQuestion()" id="btn-prev-q" class="py-3 px-6 bg-white border border-slate-200 text-slate-700 font-bold rounded-2xl hover:bg-slate-50 transition shadow-sm">
                    <i class="fa-solid fa-arrow-left mr-2"></i> Soal Sebelumnya
                </button>
                <button onclick="nextQuestion()" id="btn-next-q" class="py-3 px-6 bg-indigo-600 text-white font-bold rounded-2xl hover:bg-indigo-700 transition shadow-md">
                    Soal Berikutnya <i class="fa-solid fa-arrow-right ml-2"></i>
                </button>
                <button onclick="submitQuiz()" id="btn-finish-quiz" class="hidden py-3 px-8 bg-gradient-to-r from-emerald-500 to-teal-600 text-white font-extrabold rounded-2xl hover:opacity-95 transition shadow-lg">
                    <i class="fa-solid fa-check-double mr-2"></i> Selesaikan Kuis
                </button>
            </div>
        </section>

        <!-- TAB 4: SKOR & PROGRES EVALUASI (PAKET 1 & PAKET 2) -->
        <section id="tab-skor" class="tab-content hidden space-y-8">
            <div class="text-center max-w-xl mx-auto">
                <h2 class="text-3xl font-black text-slate-800">📊 Progres & Hasil Kuis Lengkap</h2>
                <p class="text-slate-600 text-sm mt-1">Evaluasi capaian belajar kamu dari Paket 1 (Soal 1-25) dan Paket 2 (Soal 26-50).</p>
            </div>

            <!-- Score Overview Cards (Combined + Paket 1 + Paket 2 Breakdown) -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-5 gap-4">
                <div class="bg-gradient-to-br from-indigo-600 to-violet-700 text-white p-5 rounded-3xl shadow-md text-center flex flex-col justify-between">
                    <span class="text-xs font-bold text-indigo-200 uppercase tracking-wider">Nilai Total (50 Soal)</span>
                    <div id="score-percentage" class="text-4xl font-black my-2">0%</div>
                    <p id="score-grade-label" class="text-xs font-semibold text-indigo-100">Belum Ada Progres</p>
                </div>

                <div class="bg-white p-5 rounded-3xl border border-slate-200 shadow-sm text-center flex flex-col justify-between">
                    <span class="text-xs font-bold text-slate-400 uppercase tracking-wider"><i class="fa-solid fa-bookmark text-amber-500 mr-1"></i> Paket 1 (Soal 1-25)</span>
                    <div id="score-p1-count" class="text-2xl font-black text-amber-600 my-2">0 / 25</div>
                    <p class="text-xs font-semibold text-slate-500">Dasar Penelitian</p>
                </div>

                <div class="bg-white p-5 rounded-3xl border border-slate-200 shadow-sm text-center flex flex-col justify-between">
                    <span class="text-xs font-bold text-slate-400 uppercase tracking-wider"><i class="fa-solid fa-map-location-dot text-indigo-500 mr-1"></i> Paket 2 (Soal 26-50)</span>
                    <div id="score-p2-count" class="text-2xl font-black text-indigo-600 my-2">0 / 25</div>
                    <p class="text-xs font-semibold text-slate-500">Terapan & Spasial</p>
                </div>

                <div class="bg-white p-5 rounded-3xl border border-slate-200 shadow-sm text-center flex flex-col justify-between">
                    <span class="text-xs font-bold text-slate-400 uppercase tracking-wider"><i class="fa-solid fa-list-check text-purple-500 mr-1"></i> PG Kompleks</span>
                    <div id="score-complex-count" class="text-2xl font-black text-purple-600 my-2">0 / 20</div>
                    <p class="text-xs font-semibold text-slate-500">3 Opsi Benar</p>
                </div>

                <div class="bg-white p-5 rounded-3xl border border-slate-200 shadow-sm text-center flex flex-col justify-between">
                    <span class="text-xs font-bold text-slate-400 uppercase tracking-wider">Status Evaluasi</span>
                    <div id="score-status-badge" class="my-auto py-2">
                        <span class="px-3 py-1.5 bg-slate-100 text-slate-600 font-bold text-xs rounded-full">Belum Diisi</span>
                    </div>
                    <p id="score-total-count" class="text-xs font-semibold text-slate-400">0 / 50 Dijawab</p>
                </div>
            </div>

            <!-- Comprehensive Review Section with Filter -->
            <div class="bg-white rounded-3xl border border-slate-200 shadow-sm p-6 sm:p-8 space-y-6">
                <div class="flex flex-col sm:flex-row items-center justify-between gap-4 border-b border-slate-100 pb-4">
                    <div>
                        <h3 class="text-xl font-bold text-slate-800"><i class="fa-solid fa-list-check text-indigo-600 mr-2"></i> Review & Pembahasan Laporan Soal</h3>
                        <p class="text-xs text-slate-500 mt-0.5">Filter pembahasan berdasarkan paket kuis di bawah ini.</p>
                    </div>

                    <!-- Filter Tabs for Review List -->
                    <div class="flex items-center space-x-1 bg-slate-100 p-1.5 rounded-2xl text-xs font-bold">
                        <button onclick="setScoreFilter('all')" id="score-filter-all" class="score-filter-btn px-3 py-1.5 rounded-xl transition bg-white text-indigo-700 shadow-sm">Semua (1-50)</button>
                        <button onclick="setScoreFilter('paket1')" id="score-filter-paket1" class="score-filter-btn px-3 py-1.5 rounded-xl transition text-slate-600 hover:text-indigo-600">Paket 1 (1-25)</button>
                        <button onclick="setScoreFilter('paket2')" id="score-filter-paket2" class="score-filter-btn px-3 py-1.5 rounded-xl transition text-slate-600 hover:text-indigo-600">Paket 2 (26-50)</button>
                    </div>
                </div>

                <div id="score-review-list" class="space-y-4">
                    <p class="text-slate-400 text-center py-8 text-sm italic">Selesaikan kuis di tab "Kuis (50 Soal)" untuk melihat detail pembahasan lengkap di sini.</p>
                </div>
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="bg-slate-900 text-slate-400 py-6 border-t border-slate-800 mt-auto text-xs text-center">
        <div class="max-w-7xl mx-auto px-4 space-y-2">
            <p class="font-medium text-slate-300">GeoResearch Master &copy; 2026 - Created by <span class="text-yellow-400 font-bold">Rafka Fiorenza Qursuy</span></p>
            <p class="text-slate-500">Media Pembelajaran Penelitian Geografi Interaktif (Total 50 Soal Interaktif &amp; Modul Pembelajaran).</p>
        </div>
    </footer>

    <script>
        // DATA 13 MATERI KISI-KISI
        const MATERI_DATA = [
            {
                id: 1,
                title: "1. Definisi & Konsep Penelitian Geografi",
                tag: "Dasar Penelitian",
                color: "from-blue-500 to-indigo-600",
                icon: "fa-vial",
                summary: "Penelitian geografi adalah kegiatan ilmiah yang dilakukan secara sistematis untuk memecahkan masalah keruangan (spasial) dan fenomena geosfer.",
                details: [
                    "<strong>Sifat Ilmiah:</strong> Berbasis data empiris, objektif, logis, dan dapat diuji ulang.",
                    "<strong>Objek Kajian:</strong> Fenomena geosfer (Litosfer, Atmosfer, Hidrosfer, Biosfer, Antroposfer).",
                    "<strong>Ciri Khusus:</strong> Selalu mengaitkan fenomena dengan lokasi, persebaran, dan interaksi keruangan."
                ]
            },
            {
                id: 2,
                title: "2. Klimatologi & Peran BMKG",
                tag: "Atmosfer & Iklim",
                color: "from-amber-500 to-orange-600",
                icon: "fa-cloud-sun-rain",
                summary: "Klimatologi adalah ilmu yang mempelajari rata-rata cuaca dalam jangka waktu panjang (>30 tahun) pada area luas.",
                details: [
                    "<strong>BMKG:</strong> Badan Meteorologi, Klimatologi, dan Geofisika.",
                    "<strong>Peran Utama:</strong> Menyediakan data cuaca/iklim resmi, prakiraan musim, sistem peringatan dini (mitigasi bencana).",
                    "<strong>Fungsi dalam Penelitian:</strong> Menyediakan data sekunder berupa rekaman curah hujan, suhu, angin, dan kelembapan."
                ]
            },
            {
                id: 3,
                title: "3. Langkah Sebelum Melakukan Penelitian",
                tag: "Metodologi",
                color: "from-emerald-500 to-teal-600",
                icon: "fa-list-check",
                summary: "Tahapan persiapan awal sangat krusial agar penelitian terarah dan efektif.",
                details: [
                    "<strong>1. Mengamati Fenomena:</strong> Menemukan isu/masalah keruangan yang menarik di lapangan.",
                    "<strong>2. Studi Literatur / Pustaka:</strong> Membaca teori, jurnal, dan penelitian terdahulu.",
                    "<strong>3. Observasi Lapangan Awal:</strong> Cek kondisi riil wilayah studi.",
                    "<strong>4. Memperjelas Masalah & Tujuan:</strong> Menyusun hipotesis awal dan batasan studi."
                ]
            },
            {
                id: 4,
                title: "4. Menentukan Rumusan Masalah",
                tag: "Perancangan",
                color: "from-purple-500 to-pink-600",
                icon: "fa-circle-question",
                summary: "Rumusan masalah adalah pertanyaan spesifik yang akan dijawab melalui proses pengumpulan data.",
                details: [
                    "<strong>Format Pertanyaan:</strong> Menggunakan kata tanya ilmiah (Apa, Di mana, Mengapa, Bagaimana).",
                    "<strong>Kriteria Baik:</strong> Jelas, terukur, memiliki aspek keruangan (lokasi spesifik), dan dapat dicari datanya.",
                    "<strong>Contoh:</strong> <em>'Bagaimana pola persebaran spasial titik erosi di DAS Musi Hulu?'</em>"
                ]
            },
            {
                id: 5,
                title: "5. Pendekatan Kualitatif vs Kuantitatif",
                tag: "Jenis Data",
                color: "from-sky-500 to-blue-600",
                icon: "fa-chart-simple",
                summary: "Dua paradigma utama dalam penelitian geografi sesuai dengan jenis data dan analisisnya.",
                details: [
                    "<strong>Kuantitatif:</strong> Berbentuk angka, statistik, pengukuran terukur (misal: debit air, mm curah hujan).",
                    "<strong>Kualitatif:</strong> Berbentuk kata-kata, deskripsi naratif, wawancara mendalam, atau kualitasi fenomena (misal: persepsi masyarakat adat)."
                ]
            },
            {
                id: 6,
                title: "6. Menentukan Variabel pada Judul",
                tag: "Struktur Judul",
                color: "from-rose-500 to-red-600",
                icon: "fa-sliders",
                summary: "Variabel adalah objek atau faktor yang nilainya bervariasi dan menjadi fokus penelitian.",
                details: [
                    "<strong>Variabel Bebas (X / Independent):</strong> Faktor yang memengaruhi atau menyebabkan perubahan.",
                    "<strong>Variabel Terikat (Y / Dependent):</strong> Faktor yang dipengaruhi atau diakibatkan oleh X.",
                    "<strong>Contoh Judul:</strong> <em>'Pengaruh Deforestasi (X) terhadap Frekuensi Banjir (Y)'</em>."
                ]
            },
            {
                id: 7,
                title: "7. Data Primer & Data Sekunder",
                tag: "Sumber Data",
                color: "from-indigo-500 to-purple-600",
                icon: "fa-database",
                summary: "Klasifikasi data berdasarkan cara perolehannya oleh peneliti.",
                details: [
                    "<strong>Data Primer:</strong> Diperoleh langsung di lapangan oleh peneliti (Wawancara, pengukuran PH tanah, kuesioner langsung).",
                    "<strong>Data Sekunder:</strong> Diperoleh dari pihak ketiga / instansi / dokumen resmi (Data BMKG, BPS, Peta RBI, Citra Satelit)."
                ]
            },
            {
                id: 8,
                title: "8. Apa itu Sumber Data",
                tag: "Konsep Data",
                color: "from-cyan-500 to-blue-600",
                icon: "fa-folder-tree",
                summary: "Subjek, objek, dokumen, atau tempat dari mana data penelitian diperoleh.",
                details: [
                    "<strong>Bentuk Sumber Data:</strong> Responden (manusia), Fisik (tanah, air, batuan), Lembaga (BPS, BMKG, Dinas Lingkungan Hidup), Citra & Peta."
                ]
            },
            {
                id: 9,
                title: "9. Etika Penelitian Geografi",
                tag: "Prinsip Morals",
                color: "from-yellow-500 to-amber-600",
                icon: "fa-scale-balanced",
                summary: "Aturan moral dan norma ilmiah yang wajib dipatuhi oleh setiap peneliti.",
                details: [
                    "<strong>Kejujuran Data:</strong> Dilarang merekayasa/memalsukan data (Fabrikasi/Falsifikasi).",
                    "<strong>Anti-Plagiarisme:</strong> Wajib mencantumkan sumber referensi asli.",
                    "<strong>Informed Consent:</strong> Meminta izin responden sebelum wawancara & menjaga privasi warga."
                ]
            },
            {
                id: 10,
                title: "10. Tiga Pendekatan Geografi",
                tag: "Pilar Geografi",
                color: "from-teal-500 to-emerald-600",
                icon: "fa-shapes",
                summary: "Kacamata khas geografi dalam menganalisis fenomena permukaan bumi.",
                details: [
                    "<strong>1. Pendekatan Spasial (Keruangan):</strong> Mengkaji persebaran, lokasi, dan pola fenomena di ruang.",
                    "<strong>2. Pendekatan Ekologi (Kelingkungan):</strong> Mengkaji interaksi antara makhluk hidup (manusia) dengan lingkungan fisik.",
                    "<strong>3. Pendekatan Kompleks Wilayah:</strong> Memadukan spasial & ekologi serta analisis interaksi antarwilayah."
                ]
            },
            {
                id: 11,
                title: "11. SIG Citra Satelit = Data Sekunder Mentah",
                tag: "Penginderaan Jauh",
                color: "from-purple-600 to-indigo-700",
                icon: "fa-satellite",
                summary: "Citra satelit (Landsat, Sentinel, dll) yang langsung direkam dari satelit adalah DATA SEKUNDER.",
                details: [
                    "<strong>Mengapa Data Sekunder?</strong> Karena citra merupakan rekaman mentah sensor alat wahana, bukan hasil olahan/analisis penalaran langsung manusia pada saat penangkapan.",
                    "<strong>Fungsi:</strong> Menjadi data mentah masukan (input) dalam analisis SIG."
                ]
            },
            {
                id: 12,
                title: "12. Metode Studi Kasus (Case Study)",
                tag: "Metode Spesifik",
                color: "from-pink-500 to-rose-600",
                icon: "fa-magnifying-glass-location",
                summary: "Pendekatan penelitian eksploratif yang mendalam pada satu kasus/lokasi unik tertentu.",
                details: [
                    "<strong>Karakteristik:</strong> Berfokus pada 'mengapa' dan 'bagaimana' fenomena terjadi secara spesifik di wilayah tersebut.",
                    "<strong>Pengumpulan Data:</strong> Menggunakan multi-sumber (wawancara, dokumen, peta lokal, sampel tanah)."
                ]
            },
            {
                id: 13,
                title: "13. Tahap Sebelum Menentukan Metode",
                tag: "Alur Ilmiah",
                color: "from-blue-600 to-violet-600",
                icon: "fa-diagram-project",
                summary: "Langkah-langkah yang wajib dipastikan sebelum peneliti memilih kuesioner, wawancara, atau SIG.",
                details: [
                    "<strong>Pertimbangan Utama:</strong> Pahami dengan tepat Tujuan Penelitian, Rumusan Masalah, dan Jenis Data yang dibutuhkan.",
                    "<strong>Evaluasi Kelayakan:</strong> Ketersediaan alat, ketersediaan data sekunder, biaya, dan batas waktu."
                ]
            }
        ];

        // PAKET 1: 25 SOAL KISI-KISI DASAR (10 PG KOMPLEKS + 15 PG TUNGGAL)
        const QUIZ_DATA_PAKET1 = [
            {
                id: 1,
                category: "paket1",
                type: "single",
                topic: "Definisi Penelitian Geografi",
                stimulus: "Seorang peneliti mengamati alih fungsi lahan pesisir menjadi tambak udang di Kabupaten Brebes yang memicu abrasi pantai dan penurunan resapan air bersih warga setempat.",
                question: "Mengapa kegiatan pengamatan tersebut tergolong sebagai penelitian geografi yang ilmiah?",
                options: [
                    "A. Karena berfokus pada analisis objek keruangan (spasial) serta interaksi manusia dengan lingkungan.",
                    "B. Karena dilakukan oleh pejabat dinas pemerintah daerah setempat.",
                    "C. Karena berfokus menghitung keuntungan finansial pemilik tambak udang secara komersial.",
                    "D. Karena tidak memerlukan bukti data empiris dari lapangan."
                ],
                correct: [0],
                explanation: "Penelitian geografi wajib memiliki ciri khas spasial (keruangan) dan mengkaji interaksi antara aktivitas manusia dengan lingkungan fisiknya."
            },
            {
                id: 2,
                category: "paket1",
                type: "complex",
                topic: "Klimatologi & BMKG",
                stimulus: "BMKG mengeluarkan peringatan fenomena El Niño yang berdampak pada kekeringan panjang dan penurunan curah hujan di Nusa Tenggara. Peneliti geografi memanfaatkan data BMKG untuk menganalisis risiko kegagalan panen.",
                question: "Pilihlah 3 pernyataan yang BENAR mengenai Klimatologi dan peran BMKG dalam studi geografi tersebut! (Pilih tepat 3 opsi)",
                options: [
                    "1. Klimatologi mengkaji kondisi rata-rata cuaca dalam jangka waktu panjang dan cakupan wilayah luas.",
                    "2. BMKG bertindak sebagai instansi penyedia data sekunder resmi terkait curah hujan dan iklim.",
                    "3. Data dari BMKG berguna untuk menyusun rekomendasi mitigasi bencana kekeringan.",
                    "4. BMKG adalah lembaga swasta yang tidak berwenang mengumpulkan data meteorologi.",
                    "5. Klimatologi hanya memprediksi cuaca per jam di area seluas satu ruangan."
                ],
                correct: [0, 1, 2],
                explanation: "Opsi 1, 2, dan 3 benar. Klimatologi mencakup waktu panjang, BMKG adalah lembaga pemerintah resmi penyedia data sekunder iklim untuk mitigasi."
            },
            {
                id: 3,
                category: "paket1",
                type: "single",
                topic: "Langkah Sebelum Penelitian",
                stimulus: "Aulia menemukan fenomena kemacetan parah akibat pasar tumpah di jalan lintas Sumatra. Sebelum ia menyusun teknik wawancara dan instrumen lapangan, tindakan awal apa yang harus dilakukan?",
                question: "Langkah mendasar apa yang wajib dilakukan Aulia di tahap awal?",
                options: [
                    "A. Mengidentifikasi fenomena masalah, melakukan studi literatur, dan menentukan rumusan masalah.",
                    "B. Membeli peralatan kamera paling mahal di toko.",
                    "C. Langsung menulis bab kesimpulan dan saran.",
                    "D. Mengirimkan laporan hasil penelitian ke jurnal nasional."
                ],
                correct: [0],
                explanation: "Sebelum memilih metode atau mengumpulkan data, peneliti harus mengidentifikasi fenomena, melakukan kajian pustaka, dan merumuskan masalah."
            },
            {
                id: 4,
                category: "paket1",
                type: "complex",
                topic: "Rumusan Masalah",
                stimulus: "Terjadi bencana tanah longsor berulang di Jalur Puncak Bogor saat hujan deras. Peneliti ingin membuat rumusan masalah ilmiah berperspektif geografi.",
                question: "Pilihlah 3 kriteria yang BENAR dalam menentukan rumusan masalah geografi yang baik! (Pilih tepat 3 opsi)",
                options: [
                    "1. Menggunakan kata tanya ilmiah seperti 'Mengapa' dan 'Bagaimana' fenomena terjadi.",
                    "2. Memuat aspek keruangan (spatial) yang jelas mengenai lokasi spesifik fenomena.",
                    "3. Bersifat terukur dan dapat dicari solusinya melalui pengumpulan data empiris.",
                    "4. Harus langsung berisi jawaban pasti sebelum penelitian dilaksanakan.",
                    "5. Dibuat sesering mungkin tanpa memperhatikan keterlibatan variabel."
                ],
                correct: [0, 1, 2],
                explanation: "Rumusan masalah geografi yang baik memakai kata tanya analisis, memiliki lokasi/spasial jelas, dan dapat diuji dengan data empiris."
            },
            {
                id: 5,
                category: "paket1",
                type: "single",
                topic: "Kualitatif vs Kuantitatif",
                stimulus: "Peneliti X mengukur debit air sungai dalam angka m³/detik, sedangkan Peneliti Y mengkaji kearifan lokal masyarakat Suku Baduy dalam melestarikan hutan melalui wawancara mendalam.",
                question: "Jenis pendekatan data yang digunakan Peneliti X dan Peneliti Y secara berurutan adalah...",
                options: [
                    "A. Kuantitatif dan Kualitatif",
                    "B. Kualitatif dan Kuantitatif",
                    "C. Primer dan Sekunder",
                    "D. Spasial dan Ekologi"
                ],
                correct: [0],
                explanation: "Peneliti X menggunakan angka/pengukuran (Kuantitatif), sedangkan Peneliti Y menggunakan deskripsi naratif/wawancara (Kualitatif)."
            },
            {
                id: 6,
                category: "paket1",
                type: "complex",
                topic: "Menentukan Variabel Penelitian",
                stimulus: "Judul proposal penelitian: 'Pengaruh Luas Alih Fungsi Lahan Hutan Mangrove (X) terhadap Tingkat Erosi Pesisir (Y) di Pantai Laguna'.",
                question: "Pilihlah 3 pernyataan yang BENAR mengenai variabel dalam judul penelitian tersebut! (Pilih tepat 3 opsi)",
                options: [
                    "1. Luas alih fungsi hutan mangrove berperan sebagai Variabel Bebas (X).",
                    "2. Tingkat erosi pesisir berperan sebagai Variabel Terikat (Y).",
                    "3. Perubahan pada variabel X diasumsikan memengaruhi tingkat variabel Y.",
                    "4. Tingkat erosi pesisir adalah variabel bebas yang memengaruhi alih fungsi mangrove.",
                    "5. Judul di atas tidak memiliki variabel terikat sama sekali."
                ],
                correct: [0, 1, 2],
                explanation: "Alih fungsi mangrove adalah faktor penyebab (Variabel Bebas X), dan tingkat erosi adalah akibat yang diukur (Variabel Terikat Y)."
            },
            {
                id: 7,
                category: "paket1",
                type: "single",
                topic: "Data Primer & Sekunder",
                stimulus: "Siti melakukan pengukuran pH tanah secara langsung menggunakan soil tester di lereng Gunung Merapi, lalu ia mengambil peta batas administrasi desa dari kantor Bappeda.",
                question: "Jenis data yang didapatkan Siti berturut-turut adalah...",
                options: [
                    "A. Data Primer dan Data Sekunder",
                    "B. Data Sekunder dan Data Primer",
                    "C. Data Kualitatif dan Data Naratif",
                    "D. Data Penginderaan Jauh dan Data BMKG"
                ],
                correct: [0],
                explanation: "Pengukuran pH tanah langsung = Data Primer. Peta dari instansi Bappeda = Data Sekunder."
            },
            {
                id: 8,
                category: "paket1",
                type: "complex",
                topic: "Sumber Data Penelitian",
                stimulus: "Peneliti geografi melakukan studi tentang tingkat kerawanan banjir di kawasan DAS Citarum. Ia memerlukan berbagai sumber data untuk memperkuat analisisnya.",
                question: "Pilihlah 3 bentuk sumber data yang TEPAT beserta contohnya dalam penelitian geografi! (Pilih tepat 3 opsi)",
                options: [
                    "1. Responden masyarakat lokal sebagai sumber data wawancara primer.",
                    "2. Institusi BPS dan BMKG sebagai sumber data sekunder statistik dan iklim.",
                    "3. Sampel fisik tanah dan air sungai sebagai sumber data material lapangan.",
                    "4. Opini tanpa fakta dari akun anonim media sosial sebagai sumber data baku.",
                    "5. Rumor masyarakat luar wilayah tanpa verifikasi sebagai sumber utama."
                ],
                correct: [0, 1, 2],
                explanation: "Sumber data sah berupa manusia (responden), lembaga resmi (BPS/BMKG), dan objek material fisik lapangan."
            },
            {
                id: 9,
                category: "paket1",
                type: "single",
                topic: "Etika Penelitian",
                stimulus: "Seorang peneliti mengambil paragraf utuh dan tabel data dari jurnal ilmiah orang lain lalu memasukkannya ke dalam laporannya tanpa menyantumkan nama penulis asli maupun sumber referensinya.",
                question: "Tindakan pelanggaran etika penelitian tersebut dinamakan...",
                options: [
                    "A. Plagiarisme (Plagiat)",
                    "B. Falsifikasi Data",
                    "C. Wawancara terstruktur",
                    "D. Observasi partisipatif"
                ],
                correct: [0],
                explanation: "Mengambil karya atau data orang lain tanpa menyantumkan kredit sumber resmi merupakan tindakan Plagiarisme."
            },
            {
                id: 10,
                category: "paket1",
                type: "complex",
                topic: "Tiga Pendekatan Geografi",
                stimulus: "Fenomena letusan Gunung Sinabung dianalisis dari segi persebaran abu vulkanik (lokasi), interaksi manusia dengan kerusakan ladang (ekologi), serta dampak pasokan pangan antarwilayah.",
                question: "Pilihlah 3 pernyataan yang BENAR terkait Tiga Pendekatan Utama Geografi! (Pilih tepat 3 opsi)",
                options: [
                    "1. Pendekatan Spasial fokus mengkaji persebaran dan pola fenomena di ruang muka bumi.",
                    "2. Pendekatan Ekologi mengkaji interaksi antara aktivitas manusia dengan lingkungan fisiknya.",
                    "3. Pendekatan Kompleks Wilayah memadukan spasial dan ekologi serta keterkaitan antarwilayah.",
                    "4. Pendekatan Spasial mengabaikan aspek letak geografis dan lokasi.",
                    "5. Pendekatan Kompleks Wilayah hanya berlaku untuk pengamatan sel mikroskopis."
                ],
                correct: [0, 1, 2],
                explanation: "Tiga pilar pendekatan geografi adalah Spasial (ruang/pola), Ekologi (lingkungan/manusia), dan Kompleks Wilayah (keterkaitan antarwilayah)."
            },
            {
                id: 11,
                category: "paket1",
                type: "single",
                topic: "SIG & Citra Satelit",
                stimulus: "Mahasiswa mengunduh citra satelit Sentinel-2 dari portal internet USGS untuk memetakan perubahan tutupan lahan di Palembang.",
                question: "Mengapa citra satelit yang belum diolah manusia dikategorikan sebagai DATA SEKUNDER?",
                options: [
                    "A. Karena merupakan produk rekaman otomatis dari sensor wahana pihak ketiga, bukan hasil analisis empiris peneliti langsung di lapangan.",
                    "B. Karena harganya gratis dan bisa diunduh kapan saja.",
                    "C. Karena citra satelit pasti selalu salah dan tidak akurat.",
                    "D. Karena dibuat oleh manusia secara manual menggunakan pensil warna."
                ],
                correct: [0],
                explanation: "Citra satelit mentah adalah data sekunder karena terekam otomatis oleh alat pihak ketiga dan tersedia sebelum dianalisis oleh peneliti."
            },
            {
                id: 12,
                category: "paket1",
                type: "complex",
                topic: "Metode Studi Kasus",
                stimulus: "Terjadi peristiwa fenomena tanah amblasan mendadak (sinkhole) yang langka di Desa Sukamaju. Peneliti geografi memutuskan memilih Metode Studi Kasus.",
                question: "Pilihlah 3 karakteristik BENAR mengenai metode Studi Kasus (Case Study)! (Pilih tepat 3 opsi)",
                options: [
                    "1. Berfokus pada eksplorasi mendalam terhadap fenomena spesifik di lokasi dan waktu tertentu.",
                    "2. Menggunakan multi-sumber data seperti observasi lapangan, wawancara warga, dan peta geologi.",
                    "3. Bertujuan memahami secara komprehensif latar belakang dan penyebab kasus tersebut secara detail.",
                    "4. Langsung menggeneralisasi fenomena tersebut berlaku sama di seluruh benua.",
                    "5. Dilarang menggunakan data kualitatif maupun data primer lapangan."
                ],
                correct: [0, 1, 2],
                explanation: "Studi kasus berfokus mendalam pada fenomena unik tertentu menggunakan berbagai sumber data pendukung."
            },
            {
                id: 13,
                category: "paket1",
                type: "single",
                topic: "Sebelum Menentukan Metode",
                stimulus: "Reno kebingungan apakah ia harus memilih metode kuesioner kuantitatif atau wawancara kualitatif untuk studinya.",
                question: "Apakah pertimbangan paling utama yang wajib dipastikan Reno sebelum menentukan metode penelitian?",
                options: [
                    "A. Memahami dengan jelas Tujuan Penelitian, Rumusan Masalah, dan Karakteristik Data yang dibutuhkan.",
                    "B. Memilih metode yang paling disukai oleh teman sekelasnya.",
                    "C. Mencari metode yang paling sedikit membutuhkan waktu penulisan tanpa peduli isi.",
                    "D. Menggunakan metode statistik rumit agar terlihat keren."
                ],
                correct: [0],
                explanation: "Pemilihan metode wajib disesuaikan dengan rumusan masalah, tujuan, serta jenis data yang ingin didapatkan."
            },
            {
                id: 14,
                category: "paket1",
                type: "complex",
                topic: "Definisi Penelitian Geografi",
                stimulus: "Peneliti mengkaji masalah intrusi air laut di Semarang akibat penurunan tanah (land subsidence) dan pengambilan air tanah berlebih.",
                question: "Pilihlah 3 Ciri Utama yang menandakan kajian tersebut merupakan penelitian geografi! (Pilih tepat 3 opsi)",
                options: [
                    "1. Memiliki objek kajian geosfer (hidrosfer & litosfer).",
                    "2. Menggunakan analisis keruangan untuk memetakan zonasi intrusi.",
                    "3. Bertujuan memberikan solusi pengelolaan lingkungan pesisir.",
                    "4. Hanya mengkaji suku bunga pinjaman modal usaha industri.",
                    "5. Menolak penggunaan peta dan data lokasi geografis."
                ],
                correct: [0, 1, 2],
                explanation: "Ciri penelitian geografi: mengkaji geosfer, ada pemetaan keruangan, dan memberikan solusi kelingkungan."
            },
            {
                id: 15,
                category: "paket1",
                type: "single",
                topic: "Peran BMKG",
                stimulus: "Tim peneliti gempa memanfaatkan data historis epicenter dan magnitudo gempa 10 tahun terakhir yang dirilis BMKG.",
                question: "Peran utama data BMKG dalam studi geofisika tersebut adalah...",
                options: [
                    "A. Sebagai Data Sekunder historis yang valid untuk analisis kerawanan bencana.",
                    "B. Sebagai Data Primer hasil wawancara tim peneliti.",
                    "C. Sebagai bukti data kualitatif berbasis persepsi pribadi.",
                    "D. Sebagai pelengkap dekorasi laporan penelitian."
                ],
                correct: [0],
                explanation: "Data resmi dari publikasi BMKG adalah data sekunder terverifikasi."
            },
            {
                id: 16,
                category: "paket1",
                type: "complex",
                topic: "Langkah Sebelum Penelitian",
                stimulus: "Sebelum menyusun proposal penataan kawasan kumuh, tim peneliti melakukan survei pra-lapangan dan membaca puluhan jurnal ilmiah.",
                question: "Mengapa tahapan pra-penelitian tersebut sangat penting? (Pilih tepat 3 opsi)",
                options: [
                    "1. Membantu memahami kondisi nyata dan dinamika fenomena di lapangan.",
                    "2. Menghindari terjadinya duplikasi atau pengulangan penelitian dari orang lain.",
                    "3. Menyediakan landasan teori yang kuat untuk merumuskan pertanyaan penelitian.",
                    "4. Memastikan peneliti langsung lulus tanpa perlu menulis laporan akhir.",
                    "5. Menghilangkan kebutuhan akan sampel data lapangan."
                ],
                correct: [0, 1, 2],
                explanation: "Pra-penelitian (survei & studi pustaka) mencegah plagiasi/duplikasi, memperkuat teori, dan memberi gambaran riil lapangan."
            },
            {
                id: 17,
                category: "paket1",
                type: "single",
                topic: "Pendekatan Kualitatif",
                stimulus: "Data berupa naskah wawancara tentang kearifan lokal nelayan tradisional dalam membaca tanda-tanda angin musim tergolong jenis data...",
                question: "Pilihan jenis data yang tepat adalah...",
                options: [
                    "A. Data Kualitatif",
                    "B. Data Kuantitatif Angka",
                    "C. Data Sensorik Satelit",
                    "D. Data Statistik Terstruktur"
                ],
                correct: [0],
                explanation: "Teks narasi hasil wawancara deskriptif tergolong data kualitatif."
            },
            {
                id: 18,
                category: "paket1",
                type: "complex",
                topic: "Variabel Penelitian",
                stimulus: "Judul: 'Analisis Pengaruh Intensitas Curah Hujan (X) terhadap Frekuensi Tanah Longsor (Y) di Kabupaten Garut'.",
                question: "Pilihlah 3 penafsiran variabel yang BENAR dari judul di atas! (Pilih tepat 3 opsi)",
                options: [
                    "1. Intensitas Curah Hujan adalah Variabel Bebas (Independent).",
                    "2. Frekuensi Tanah Longsor adalah Variabel Terikat (Dependent).",
                    "3. Curah hujan diasumsikan sebagai pemicu timbulnya tanah longsor.",
                    "4. Tanah longsor adalah variabel bebas yang menyebabkan hujan deras.",
                    "5. Judul di atas tidak memiliki variabel bebas sama sekali."
                ],
                correct: [0, 1, 2],
                explanation: "Curah hujan = Variabel Bebas (X), Frekuensi longsor = Variabel Terikat (Y) yang dipengaruhi oleh X."
            },
            {
                id: 19,
                category: "paket1",
                type: "single",
                topic: "Citra Satelit dalam SIG",
                stimulus: "Seorang geograf menggunakan citra foto udara untuk menganalisis kepadatan bangunan di Jakarta.",
                question: "Mengapa foto udara tersebut tergolong sebagai data sekunder dalam SIG?",
                options: [
                    "A. Karena direkam oleh instrumen wahana pesawat/satelit, bukan hasil olahan penalaran peneliti saat pengambilan.",
                    "B. Karena dibuat oleh tim geologi abad ke-15.",
                    "C. Karena foto udara tidak dapat dimasukkan ke dalam komputer.",
                    "D. Karena analisis foto udara tidak membutuhkan pengetahuan geografi."
                ],
                correct: [0],
                explanation: "Foto udara mentah direkam instrumen wahana/sensor sehingga berstatus sebagai data sekunder bagi peneliti."
            },
            {
                id: 20,
                category: "paket1",
                type: "complex",
                topic: "Etika Penelitian",
                stimulus: "Saat melakukan survei wawancara kepada warga terdampak bencana banjir bandang, peneliti wajib menjaga etika ilmiah.",
                question: "Pilihlah 3 tindakan yang SESUAI dengan etika penelitian geografi! (Pilih tepat 3 opsi)",
                options: [
                    "1. Meminta persetujuan responden (Informed Consent) sebelum wawancara.",
                    "2. Menjaga kerahasiaan identitas pribadi warga yang diwawancarai.",
                    "3. Menyajikan data secara jujur sesuai fakta lapangan tanpa rekayasa.",
                    "4. Memaksa warga menjawab kuesioner di bawah ancaman.",
                    "5. Mengubah angka hasil survei agar sesuai dengan keinginan peneliti."
                ],
                correct: [0, 1, 2],
                explanation: "Etika meliputi izin responden (consent), kerahasiaan identitas, dan kejujuran penyajikan data."
            },
            {
                id: 21,
                category: "paket1",
                type: "single",
                topic: "Pendekatan Ekologi",
                stimulus: "Peneliti mengkaji dampak penebangan hutan liar di hulu sungai terhadap meningkatnya erosi tanah dan pendangkalan waduk di bagian hilir.",
                question: "Pendekatan geografi yang paling dominan digunakan adalah...",
                options: [
                    "A. Pendekatan Ekologi (Kelingkungan)",
                    "B. Pendekatan Kompleks Wilayah",
                    "C. Pendekatan Spasial Murni",
                    "D. Pendekatan Ekonomi Makro"
                ],
                correct: [0],
                explanation: "Mengkaji dampak ulah manusia (penebangan) terhadap lingkungan fisik (erosi & pendangkalan) menggunakan Pendekatan Ekologi."
            },
            {
                id: 22,
                category: "paket1",
                type: "single",
                topic: "Studi Kasus Geografi",
                stimulus: "Peneliti memfokuskan studinya khusus pada fenomena kemunculan semburan lumpur panas di Sidoarjo secara spesifik dan mendalam.",
                question: "Metode penelitian yang digunakan adalah...",
                options: [
                    "A. Studi Kasus (Case Study)",
                    "B. Eksperimen Laboratorium Murni",
                    "C. Survei Sensus Nasional",
                    "D. Metode Historiografi Kuno"
                ],
                correct: [0],
                explanation: "Kajian mendalam pada lokasi dan fenomena spesifik unik adalah ciri khas Metode Studi Kasus."
            },
            {
                id: 23,
                category: "paket1",
                type: "single",
                topic: "Sebelum Menentukan Metode",
                stimulus: "Pertanyaan penelitian berbunyi: 'Seberapa besar persentase penurunan luas Danau Toba dari tahun 2015-2025?'",
                question: "Metode pengolahan data yang paling tepat dipilih peneliti adalah...",
                options: [
                    "A. Metode Kuantitatif Spasial dengan analisis Citra Satelit & SIG",
                    "B. Wawancara kualitatif kepada 5 nelayan",
                    "C. Metode sejarah kerajaan kuno",
                    "D. Kuesioner persepsi masyarakat"
                ],
                correct: [0],
                explanation: "Menghitung persentase luas danau membutuhkan data terukur (Kuantitatif) dan spasial (Citra & SIG)."
            },
            {
                id: 24,
                category: "paket1",
                type: "single",
                topic: "Sumber Data Sekinner Iklim",
                stimulus: "Seorang siswa memerlukan data rata-rata suhu udara bulanan Kota Palembang selama 10 tahun terakhir.",
                question: "Sumber data sekunder paling berwenang dan valid untuk dicari adalah...",
                options: [
                    "A. Badan Meteorologi, Klimatologi, dan Geofisika (BMKG)",
                    "B. Dinas Kependudukan dan Catatan Sipil",
                    "C. Pos Satpam Perumahan",
                    "D. Dinas Pariwisata Daerah"
                ],
                correct: [0],
                explanation: "BMKG adalah lembaga pemerintah resmi penyedia data meteorologi dan iklim."
            },
            {
                id: 25,
                category: "paket1",
                type: "single",
                topic: "Rumusan Masalah Spasial",
                stimulus: "Manakah di bawah ini contoh rumusan masalah geografi yang memuat aspek keruangan (spatial) secara tepat?",
                question: "Contoh rumusan masalah geografi yang paling tepat adalah...",
                options: [
                    "A. 'Bagaimana pola persebaran spasial kerawanan tanah longsor di Kecamatan Karanganyar?'",
                    "B. 'Berapa harga jual tanah di pusat Kota Jakarta saat ini?'",
                    "C. 'Siapakah nama bupati yang menjabat di daerah tersebut?'",
                    "D. 'Mengapa warna mobil pemadam kebakaran umumnya berwarna merah?'"
                ],
                correct: [0],
                explanation: "Opsi A memuat aspek pola persebaran keruangan (spasial) dan fenomena geografi (longsor) di wilayah spesifik."
            }
        ];

        // PAKET 2: 25 SOAL TERAPAN & ANALISIS SPASIAL ADVANCE (10 PG KOMPLEKS + 15 PG TUNGGAL)
        const QUIZ_DATA_PAKET2 = [
            {
                id: 26,
                category: "paket2",
                type: "single",
                topic: "Definisi Penelitian Geografi",
                stimulus: "Peneliti mengamati perubahan garis pantai di Pangandaran menggunakan peta multitemporal tahun 2010 dan 2024. Peneliti menemukan abrasi sepanjang 1,2 km yang mengancam pemukiman nelayan.",
                question: "Berdasarkan prinsip geografi, fokus utama dari penelitian ilmiah tersebut adalah...",
                options: [
                    "A. Menganalisis dinamika perubahan keruangan (spasial) garis pantai dan dampaknya bagi pemukiman.",
                    "B. Menghitung jumlah pendapatan nelayan saat menjual ikan di lelang.",
                    "C. Memprediksi harga jual tanah di kawasan wisata Pangandaran tahun depan.",
                    "D. Menentukan jenis bahan bangunan paling murah untuk tanggul pantai."
                ],
                correct: [0],
                explanation: "Penelitian geografi selalu berfokus pada dinamika aspek keruangan (spasial), perubahan wilayah, dan dampaknya bagi masyarakat."
            },
            {
                id: 27,
                category: "paket2",
                type: "complex",
                topic: "Klimatologi & BMKG",
                stimulus: "BMKG merilis peringatan dini fenomena La Niña dan Indian Ocean Dipole (IOD) Negatif yang memicu curah hujan ekstrem melebihi rata-rata bulanan di wilayah Jawa dan Sumatra, meningkatkan risiko banjir bah.",
                question: "Pilihlah 3 pernyataan yang BENAR mengenai fenomena iklim dan peran BMKG dalam studi geografi tersebut! (Pilih tepat 3 opsi)",
                options: [
                    "1. La Niña merupakan fenomena klimatologi karena melibatkan perubahan pola cuaca dan iklim jangka panjang skala makro.",
                    "2. Data curah hujan historis harian dan bulanan dari BMKG berfungsi sebagai data sekunder utama bagi peneliti.",
                    "3. Peringatan dini dari BMKG membantu pemerintah daerah merancang mitigasi struktural dan non-struktural bencana banjir.",
                    "4. BMKG bertugas melakukan privatisasi sungai agar masyarakat membayar air hujan.",
                    "5. Klimatologi hanya berlaku untuk ruang tertutup seperti rumah kaca pertanian."
                ],
                correct: [0, 1, 2],
                explanation: "La Nina merupakan kajian iklim makro (Klimatologi), BMKG menyediakan data sekunder curah hujan resmi, dan datanya digunakan untuk analisis mitigasi."
            },
            {
                id: 28,
                category: "paket2",
                type: "single",
                topic: "Langkah Sebelum Penelitian",
                stimulus: "Seorang mahasiswa ingin meneliti pencemaran limbah pabrik di DAS Ciliwung. Sebelum terjun membawa botol sampel air di sungai, ia menelaah 15 jurnal penelitian terdahulu mengenai baku mutu air sungai Ciliwung.",
                question: "Tujuan utama dari langkah pra-penelitian tersebut adalah...",
                options: [
                    "A. Mengidentifikasi kebaruan (novelty) serta kesenjangan penelitian (research gap) agar tidak mengulang kajian orang lain.",
                    "B. Mengulur waktu agar jadwal penelitian tertunda.",
                    "C. Mengganti judul penelitian menjadi penelitian ekonomi bisnis.",
                    "D. Memastikan pabrik limbah tersebut segera ditutup secara sepihak."
                ],
                correct: [0],
                explanation: "Studi literatur sebelum penelitian bertujuan mencari research gap (kesenjangan kajian) dan kebaruan serta memperkuat landasan teori."
            },
            {
                id: 29,
                category: "paket2",
                type: "complex",
                topic: "Menentukan Rumusan Masalah",
                stimulus: "Terjadi konversi lahan pertanian produktif seluas 500 hektar menjadi kawasan pabrik di Karawang yang memicu penurunan produksi beras lokal.",
                question: "Pilihlah 3 rumusan masalah geografi yang TEPAT dan berperspektif spasial terkait kasus tersebut! (Pilih tepat 3 opsi)",
                options: [
                    "1. 'Bagaimana pola persebaran spasial alih fungsi lahan sawah menjadi kawasan industri di Kabupaten Karawang?'",
                    "2. 'Seberapa besar dampak alih fungsi lahan terhadap penurunan ketahanan pangan di wilayah Karawang?'",
                    "3. 'Bagaimana strategi pengelolaan ruang yang berkelanjutan untuk mencegah konversi lahan sawah berlanjut?'",
                    "4. 'Berapakah harga tiket masuk bioskop terdekat dari kawasan pabrik Karawang?'",
                    "5. 'Siapakah pemilik saham terbesar dari pabrik tekstil di kawasan Karawang?'"
                ],
                correct: [0, 1, 2],
                explanation: "Rumusan masalah geografi yang baik memiliki fokus pola persebaran keruangan, analisis dampak lingkungan/wilayah, dan perumusan solusi spasial."
            },
            {
                id: 30,
                category: "paket2",
                type: "single",
                topic: "Kualitatif & Kuantitatif",
                stimulus: "Tim A mengukur debit air sungai dalam satuan m³/detik dan tingkat kekeruhan NTU, sedangkan Tim B mewawancarai ketua adat Subak untuk mendokumentasikan nilai filosofis pembagian air secara naratif.",
                question: "Jenis metodologi penelitian yang diterapkan oleh Tim A dan Tim B berturut-turut adalah...",
                options: [
                    "A. Kuantitatif (pengukuran numerik terukur) dan Kualitatif (deskripsi naratif kearifan lokal)",
                    "B. Kualitatif dan Kuantitatif",
                    "C. Data Sekunder dan Data Terunduh",
                    "D. Eksperimen dan Histori Kuno"
                ],
                correct: [0],
                explanation: "Tim A mengukur parameter angka terukur (Kuantitatif), sedangkan Tim B mengumpulkan penjelasan naratif kearifan lokal (Kualitatif)."
            },
            {
                id: 31,
                category: "paket2",
                type: "complex",
                topic: "Cara Menentukan Variabel",
                stimulus: "Judul Penelitian: 'Pengaruh Densitas Lalu Lintas Kendaraan Bermotor (X) terhadap Konsentrasi Gas Polutan NO2 di Udara Ambien (Y) di Koridor Jalan Sudirman'.",
                question: "Pilihlah 3 analisis variabel yang BENAR dari judul proposal penelitian tersebut! (Pilih tepat 3 opsi)",
                options: [
                    "1. Densitas lalu lintas kendaraan bermotor merupakan Variabel Bebas (Independent Variable).",
                    "2. Konsentrasi gas polutan NO2 di udara merupakan Variabel Terikat (Dependent Variable).",
                    "3. Peningkatan nilai variabel X diperkirakan berbanding lurus dengan peningkatan nilai variabel Y.",
                    "4. Konsentrasi gas polutan NO2 adalah variabel bebas yang menentukan jumlah mobil yang lewat.",
                    "5. Judul penelitian tersebut tidak memiliki indikator terukur."
                ],
                correct: [0, 1, 2],
                explanation: "Lalu lintas = Variabel Bebas (X), Konsentrasi NO2 = Variabel Terikat (Y) yang dipengaruhi oleh tingkat padatnya kendaraan."
            },
            {
                id: 32,
                category: "paket2",
                type: "single",
                topic: "Data Primer & Sekunder",
                stimulus: "Andi mengukur kelembapan tanah secara langsung menggunakan sensor soil moisture di kebun teh, sedangkan Budi mengunduh Peta Geologi Lembar Bandung dari situs resmi Badan Geologi ESDM.",
                question: "Klasifikasi data yang didapatkan Andi dan Budi adalah...",
                options: [
                    "A. Data Andi = Data Primer; Data Budi = Data Sekunder",
                    "B. Data Andi = Data Sekunder; Data Budi = Data Primer",
                    "C. Keduanya merupakan Data Kualitatif",
                    "D. Keduanya merupakan Data Sensor BMKG"
                ],
                correct: [0],
                explanation: "Pengukuran sensor langsung di lapangan oleh Andi = Data Primer. Peta terbitan instansi Badan Geologi ESDM yang diunduh Budi = Data Sekunder."
            },
            {
                id: 33,
                category: "paket2",
                type: "complex",
                topic: "Apa itu Sumber Data",
                stimulus: "Peneliti ingin menganalisis risiko bencana kekeringan lahan pertanian sawah tadah hujan di Kabupaten Gunungkidul.",
                question: "Pilihlah 3 sumber data yang relevan dan kredibel untuk penelitian kekeringan tersebut! (Pilih tepat 3 opsi)",
                options: [
                    "1. Stasiun Klimatologi BMKG setempat untuk data rekam curah hujan 10 tahun.",
                    "2. Kelompok Tani setempat sebagai responden wawancara dampak kekeringan tanaman.",
                    "3. Citra Satelit Landsat-8/Sentinel-2 untuk analisis indeks vegetasi (NDVI) & kelembapan.",
                    "4. Brosur promosi hotel resort bintang lima di Bali.",
                    "5. Cerita fiksi dari novel tentang musim kemarau di benua Afrika."
                ],
                correct: [0, 1, 2],
                explanation: "Sumber data sah mencakup instansi BMKG (data iklim), petani (responden lapangan), dan citra satelit (data geospasial)."
            },
            {
                id: 34,
                category: "paket2",
                type: "single",
                topic: "Etika Penelitian",
                stimulus: "Seorang peneliti mengambil foto wajah anak-anak korban trauma bencana erupsi gunung api tanpa persetujuan (informed consent) orang tua mereka dan mempublikasikannya secara terbuka beserta alamat lengkap.",
                question: "Berdasarkan etika penelitian geografi, pelanggaran utama yang dilakukan peneliti tersebut adalah...",
                options: [
                    "A. Mengabaikan prinsip privasi, perlindungan identitas subjek (anonymity), dan Informed Consent.",
                    "B. Menggunakan kamera beresolusi terlalu rendah.",
                    "C. Tidak memberikan imbalan uang tunai kepada media massa.",
                    "D. Menggunakan peta tanpa mencantumkan koordinat UTM."
                ],
                correct: [0],
                explanation: "Etika penelitian mewajibkan adanya izin persetujuan (Informed Consent) dan perlindungan privasi serta identitas responden/subjek."
            },
            {
                id: 35,
                category: "paket2",
                type: "complex",
                topic: "3 Pendekatan Geografi",
                stimulus: "Bencana banjir tahunan di Jakarta tidak dapat diselesaikan hanya dari satu sudut pandang. Peneliti geografi menggunakan 3 pendekatan sekaligus.",
                question: "Pilihlah 3 pengaplikasian pendekatan geografi yang TEPAT pada penanganan banjir Jakarta! (Pilih tepat 3 opsi)",
                options: [
                    "1. Pendekatan Spasial: Memetakan zonasi daerah rawan genangan banjir dan pola persebaran genangan.",
                    "2. Pendekatan Ekologi: Menganalisis perubahan tutupan lahan resapan air dan perilaku alih fungsi lahan.",
                    "3. Pendekatan Kompleks Wilayah: Mengkaji koordinasi antarwilayah hulu (Bogor), tengah (Depok), dan hilir (Jakarta).",
                    "4. Pendekatan Spasial: Menghapus seluruh peta tata ruang dan mengabaikan lokasi geografis.",
                    "5. Pendekatan Kompleks Wilayah: Hanya mengamati mikroba bakteri di dasar laut lepas."
                ],
                correct: [0, 1, 2],
                explanation: "Aplikasi 3 pendekatan: Spasial (zonasi/pola), Ekologi (perilaku manusia vs resapan lahan), Kompleks Wilayah (keterkaitan hulu-hilir Bogor-Jakarta)."
            },
            {
                id: 36,
                category: "paket2",
                type: "single",
                topic: "SIG & Citra Satelit",
                stimulus: "Citra Satelit Radar Sentinel-1 SAR memberikan tampilan rupa bumi berbasis pantulan gelombang mikro yang ditangkap oleh instrumen satelit ruang angkasa.",
                question: "Mengapa citra satelit radar tersebut dikategorikan sebagai DATA SEKUNDER MENTAH?",
                options: [
                    "A. Karena merupakan produk rekaman otomatis sensor wahana satelit, bukan hasil kalkulasi analisis langsung oleh peneliti saat di lapangan.",
                    "B. Karena radar satelit selalu diproduksi secara manual oleh kartografer abad pertengahan.",
                    "C. Karena gelombang mikro satelit tidak mengandung informasi spasial.",
                    "D. Karena citra satelit hanya boleh digunakan oleh astronaut."
                ],
                correct: [0],
                explanation: "Citra satelit mentah merupakan data sekunder karena berupa hasil rekaman sensor alat perekam otomatis instansi/pihak ketiga."
            },
            {
                id: 37,
                category: "paket2",
                type: "complex",
                topic: "Studi Kasus (Case Study)",
                stimulus: "Terjadi fenomena pelapukan dan erosi unik pada dinding batuan kapur Karst Rammang-Rammang di Maros yang mengancam keberadaan ekosistem goa prasejarah.",
                question: "Pilihlah 3 alasan mengapa Metode Studi Kasus (Case Study) sangat cocok diterapkan pada penelitian ini! (Pilih tepat 3 opsi)",
                options: [
                    "1. Kasus memiliki keunikan fisik dan lokasi geografis spesifik yang tidak dapat disamakan secara mentah dengan wilayah lain.",
                    "2. Memungkinkan penggunaan berbagai teknik pengumpulan data mendalam (peta geologi, uji laboratorium sampel kapur, wawancara warga).",
                    "3. Bertujuan mendeskripsikan dan mengeksplorasi fenomena 'mengapa' dan 'bagaimana' erosi karst terjadi di lokasi tersebut.",
                    "4. Bertujuan membuat hukum universal yang berlaku sama persis untuk seluruh jenis tanah pasir pantai.",
                    "5. Mengharuskan peneliti mengabaikan aspek sejarah dan kondisi fisik lingkungan setempat."
                ],
                correct: [0, 1, 2],
                explanation: "Studi kasus cocok untuk fenomena unik spesifik di lokasi tertentu dengan eksplorasi mendalam berbagai sumber data."
            },
            {
                id: 38,
                category: "paket2",
                type: "single",
                topic: "Sebelum Menentukan Metode",
                stimulus: "Rina ragu apakah harus memakai teknik pembobotan Sistem Informasi Geografis (SIG) atau pembagian kuesioner skala Likert untuk merumuskan tingkat kerentanan sosial bencana.",
                question: "Langkah terbaik yang harus dilakukan Rina sebelum menetapkan pilihan metodologinya adalah...",
                options: [
                    "A. Menelaah kembali Tujuan Penelitian, Rumusan Masalah, serta ketersediaan Data yang dibutuhkan.",
                    "B. Menentukan metode berdasarkan undian acak uang logam.",
                    "C. Menyuruh teman sekelas mengerjakan seluruh proposalnya.",
                    "D. Menghapus rumusan masalah agar metode tidak perlu dipikirkan."
                ],
                correct: [0],
                explanation: "Penentuan metode wajib mengacu pada keselarasan dengan Rumusan Masalah, Tujuan Penelitian, serta sifat Data yang ingin diperoleh."
            },
            {
                id: 39,
                category: "paket2",
                type: "complex",
                topic: "Definisi Penelitian & Geosfer",
                stimulus: "Peristiwa gempa bumi diikuti likuefaksi (tanah bergerak) di Petobo Palu tahun 2018 menghancurkan ratusan rumah dan infrastruktur wilayah.",
                question: "Pilihlah 3 lapisan objek material geosfer yang saling berinteraksi pada kasus likuefaksi tersebut! (Pilih tepat 3 opsi)",
                options: [
                    "1. Litosfer: Terjadinya pergeseran sesar aktif dan guncangan struktur tanah kapiler.",
                    "2. Hidrosfer: Tingginya muka air tanah jenuh yang memicu hilangnya kekuatan geser tanah.",
                    "3. Antroposfer: Dampak korban jiwa, permukiman warga, dan kerusakan tata ruang.",
                    "4. Barisfer: Lapisan inti bumi bagian dalam yang disentuh langsung oleh warga desa.",
                    "5. Eksosfer: Ruang angkasa hampa udara tempat lewatnya komet."
                ],
                correct: [0, 1, 2],
                explanation: "Kasus likuefaksi melibatkan Litosfer (tanah/batuan), Hidrosfer (air tanah jenuh), dan Antroposfer (manusia & permukiman)."
            },
            {
                id: 40,
                category: "paket2",
                type: "single",
                topic: "Klimatologi vs Meteorologi",
                stimulus: "Peneliti A menganalisis perubahan pola curah hujan rata-rata bulanan selama 35 tahun di Karawang untuk menentukan pergeseran awal musim tanam, sedangkan Peneliti B memprediksi potensi hujan sore hari ini di Bandara Soekarno-Hatta.",
                question: "Fokus ilmu yang digunakan oleh Peneliti A dan Peneliti B secara berurutan adalah...",
                options: [
                    "A. Klimatologi (iklim jangka panjang) dan Meteorologi (cuaca jangka pendek harian)",
                    "B. Meteorologi dan Geofisika",
                    "C. Hidrologi dan Oseanografi",
                    "D. Geomorfologi dan Kartografi"
                ],
                correct: [0],
                explanation: "Peneliti A mengkaji iklim jangka panjang (Klimatologi > 30 tahun), Peneliti B mengkaji prakiraan cuaca harian (Meteorologi)."
            },
            {
                id: 41,
                category: "paket2",
                type: "complex",
                topic: "Langkah Pra-Penelitian",
                stimulus: "Sebelum menyebar kuesioner ke 100 warga terdampak proyek jalan tol, peneliti melakukan uji coba (try out) kuesioner kepada 15 responden di luar sampel.",
                question: "Pilihlah 3 alasan ilmiah mengapa uji coba kuesioner pra-penelitian tersebut wajib dilakukan! (Pilih tepat 3 opsi)",
                options: [
                    "1. Menguji tingkat Validitas (kesesuaian pertanyaan dengan indikator variabel).",
                    "2. Menguji tingkat Reliabilitas (konsistensi hasil jawaban instrumen).",
                    "3. Memastikan kalimat dalam pertanyaan mudah dipahami dan tidak ambigu bagi masyarakat.",
                    "4. Memaksa responden memberikan jawaban yang menyenangkan peneliti.",
                    "5. Memalsukan hasil tanggapan agar kuesioner bernilai sempurna."
                ],
                correct: [0, 1, 2],
                explanation: "Uji coba instrumen kuesioner dilakukan untuk memastikan Validitas, Reliabilitas, dan kejelasan kebahasaan pertanyaan."
            },
            {
                id: 42,
                category: "paket2",
                type: "single",
                topic: "Menentukan Rumusan Masalah",
                stimulus: "Seorang siswa merumuskan pertanyaan: 'Apakah terdapat perbedaan tingkat erosi tanah antara lahan sawah terasering dan lahan kebun campuran di Lereng Gunung Ungaran?'",
                question: "Berdasarkan sifat hubungannya, pertanyaan penelitian tersebut tergolong ke dalam jenis rumusan masalah...",
                options: [
                    "A. Rumusan Masalah Komparatif (Membandingkan dua fenomena/wilayah)",
                    "B. Rumusan Masalah Deskriptif Tunggal",
                    "C. Rumusan Masalah Asosiatif Kausal Tanpa Lokasi",
                    "D. Rumusan Masalah Historis Kuno"
                ],
                correct: [0],
                explanation: "Pertanyaan yang membandingkan dua kondisi/wilayah ('Apakah terdapat perbedaan... antara A dan B') adalah Rumusan Masalah Komparatif."
            },
            {
                id: 43,
                category: "paket2",
                type: "single",
                topic: "Cara Menentukan Variabel",
                stimulus: "Peneliti menguji 'Pengaruh Luas Ruang Terbuka Hijau (X) terhadap Penurunan Suhu Udara Mikro (Y) di Kota Palembang'.",
                question: "Jika luas RTH terus ditingkatkan, apakah ekspektasi perubahan yang terjadi pada Variabel Terikat (Y)?",
                options: [
                    "A. Suhu udara mikro kota (Y) akan mengalami penurunan (menjadi lebih sejuk).",
                    "B. Luas RTH (X) akan berubah menjadi gedung pencakar langit secara otomatis.",
                    "C. Curah hujan bulanan akan berhenti total selamanya.",
                    "D. Nilai variabel Y tidak akan dapat diukur sama sekali."
                ],
                correct: [0],
                explanation: "Variabel Y (suhu udara mikro) dipengaruhi oleh Variabel X (luas RTH). Penambahan RTH diharapkan menurunkan suhu kota."
            },
            {
                id: 44,
                category: "paket2",
                type: "complex",
                topic: "Data Primer & Sumber Data",
                stimulus: "Peneliti geografi melakukan pemetaan partisipatif batas kawasan hutan adat Suku Anak Dalam dengan membawa GPS handheld dan mewawancarai pemangku adat.",
                question: "Pilihlah 3 karakteristik dari data yang diperoleh langsung oleh peneliti tersebut! (Pilih tepat 3 opsi)",
                options: [
                    "1. Koordinat lokasi titik batas hutan dari GPS tergolong sebagai Data Primer Geospasial.",
                    "2. Rekaman narasi penjelas batas adat dari pemangku adat tergolong sebagai Data Primer Kualitatif.",
                    "3. Pemangku adat dan lokasi fisik hutan berfungsi sebagai Sumber Data Utama.",
                    "4. Seluruh data tersebut merupakan data sekunder hasil publikasi kantor statistik BPS.",
                    "5. Pengambilan titik koordinat GPS tidak memerlukan kehadiran fisik di lokasi."
                ],
                correct: [0, 1, 2],
                explanation: "Titik GPS & wawancara di tempat = Data Primer. Tokoh adat & fisik lokasi = Sumber Data Utama."
            },
            {
                id: 45,
                category: "paket2",
                type: "single",
                topic: "Etika Penelitian",
                stimulus: "Saat melakukan pengujian sampel air di lab, hipotesis awal peneliti bahwa sungai tercemar berat ternyata TIDAK TERBUKTI (air sungai ternyata masih relatif bersih sesuai baku mutu). Peneliti tergoda untuk mengubah angka uji laboratorium agar sesuai hipotesis awalnya.",
                question: "Tindakan rekayasa/pengubahan angka data laboratorium tersebut dinamakan pelanggaran etika...",
                options: [
                    "A. Falsifikasi Data (Memalsukan/merekayasa data agar sesuai keinginan)",
                    "B. Observasi partisipatif",
                    "C. Analisis Spasial Komprehensif",
                    "D. Triangulasi Data Sah"
                ],
                correct: [0],
                explanation: "Mengubah atau merekayasa data lapangan/lab agar cocok dengan hipotesis merupakan pelanggaran etika serius bernama Falsifikasi Data."
            },
            {
                id: 46,
                category: "paket2",
                type: "complex",
                topic: "3 Pendekatan Geografi",
                stimulus: "Analisis fenomena komuter (ulang-alik pekerja) harian dari Bogor, Depok, Tangerang, dan Bekasi menuju pusat bisnis DKI Jakarta.",
                question: "Pilihlah 3 alasan mengapa Pendekatan Kompleks Wilayah paling tepat digunakan untuk kasus ini! (Pilih tepat 3 opsi)",
                options: [
                    "1. Adanya keterkaitan dan interaksi antarwilayah (interdependensi) antara wilayah pinggiran (suburban) dengan pusat kota.",
                    "2. Menggabungkan analisis persebaran keruangan tempat tinggal komuter dengan analisis kondisi sosial ekonomi wilayah.",
                    "3. Membutuhkan perencanaan pembangunan terpadu lintas batas administrasi pemerintah daerah (Jabodetabek).",
                    "4. Karena daerah Bodetabek dan Jakarta tidak memiliki hubungan jalan transportasi sama sekali.",
                    "5. Hanya berfokus mengamati struktur lapisan kawah gunung api."
                ],
                correct: [0, 1, 2],
                explanation: "Pendekatan Kompleks Wilayah mengkaji interaksi antarwilayah (Bodetabek-Jakarta), keterkaitan fungsi spasial, dan perencanaan lintas batas."
            },
            {
                id: 47,
                category: "paket2",
                type: "single",
                topic: "SIG & Citra Satelit",
                stimulus: "Siswa geografi memproses citra Landsat-9 mentah dengan melakukan koreksi radiometrik, geometrik, dan klasifikasi terbimbing (supervised classification) untuk menghasilkan Peta Tutupan Lahan.",
                question: "Status Peta Tutupan Lahan yang berhasil diproduksi oleh siswa tersebut adalah...",
                options: [
                    "A. Data/Peta Tematik Hasil Olahan Analisis SIG (Data Sekunder Terolah)",
                    "B. Citra Satelit Mentah dari NASA",
                    "C. Data Primer Hasil Wawancara",
                    "D. Peta Kuno Tanpa Skala"
                ],
                correct: [0],
                explanation: "Setelah citra satelit mentah diolah melalui tahapan analisis klasifikasi SIG, hasilnya menjadi Peta Tematik Olahan."
            },
            {
                id: 48,
                category: "paket2",
                type: "single",
                topic: "Studi Kasus Geografi",
                stimulus: "Keunggulan utama Metode Studi Kasus ketika digunakan untuk meneliti fenomena unik seperti 'Semburan Kawah Mud Volcano di Bleduk Kuwu' adalah...",
                question: "Keunggulan utamanya terletak pada...",
                options: [
                    "A. Kemampuannya menyajikan pemahaman yang sangat mendalam, rinci, dan komprehensif tentang fenomena spesifik di lokasi tersebut.",
                    "B. Kemampuannya menyelesaikan penelitian dalam waktu 5 menit tanpa perlu data.",
                    "C. Kemampuannya mengubah lokasi gunung menjadi laut secara langsung.",
                    "D. Tidak memerlukan laporan tertulis."
                ],
                correct: [0],
                explanation: "Metode studi kasus unggul dalam memberikan analisis mendalam, rincian kontekstual, dan pemahaman komprehensif mengenai fenomena unik."
            },
            {
                id: 49,
                category: "paket2",
                type: "complex",
                topic: "Sebelum Menentukan Metode",
                stimulus: "Peneliti ingin meneliti persepsi kualitatif masyarakat lokal terhadap revitalisasi danau.",
                question: "Pilihlah 3 faktor pertimbangan utama yang mendasari pemilihan metode wawancara mendalam kualitatif! (Pilih tepat 3 opsi)",
                options: [
                    "1. Rumusan masalah berfokus pada pemahaman sudut pandang, norma, dan persepsi mendalam masyarakat.",
                    "2. Data yang dibutuhkan bersifat naratif deskriptif, bukan sekadar angka statistik singkat.",
                    "3. Peneliti ingin mengeksplorasi alasan di balik sikap dan tindakan warga setempat secara fleksibel.",
                    "4. Peneliti hanya ingin mengukur luas danau dalam hektar menggunakan pita ukur.",
                    "5. Peneliti tidak ingin berbicara dengan manusia sama sekali."
                ],
                correct: [0, 1, 2],
                explanation: "Metode wawancara kualitatif dipilih jika rumusan masalah membutuhkan pemahaman persepsi mendalam, data bersifat naratif, dan perlu eksplorasi fleksibel."
            },
            {
                id: 50,
                category: "paket2",
                type: "single",
                topic: "Sintesis Proposal Penelitian",
                stimulus: "Dalam sebuah proposal penelitian geografi, terdapat ketidaksesuaian antara Judul ('Pengaruh Curah Hujan terhadap Erosi Lahan') dengan Metode Pengumpulan Data yang ditulis (hanya menyebar kuesioner wawancara tanpa pengukuran fisik hujan & tanah).",
                question: "Evaluasi dan perbaikan apakah yang paling tepat dilakukan peneliti?",
                options: [
                    "A. Menyesuaikan metode dengan menambahkan pengolahan data sekunder iklim BMKG dan pengukuran sampel erosi fisik tanah (atau menyesuaikan rumusan masalah/judul ke persepsi masyarakat).",
                    "B. Langsung mempublikasikan proposal yang tidak sesuai tersebut ke jurnal internasional.",
                    "C. Menghapus seluruh bab penelitian dan menyerah.",
                    "D. Menyoroti gambar di sampul depan agar lebih cerah."
                ],
                correct: [0],
                explanation: "Seluruh elemen proposal (Judul, Rumusan Masalah, Variabel, dan Metode) wajib selaras dan konsisten agar penelitian sah secara metodologis."
            }
        ];

        const MASTER_QUIZ_DATA = [...QUIZ_DATA_PAKET1, ...QUIZ_DATA_PAKET2];

        // APP STATE VARIABLES
        let currentFlashcardIndex = 0;
        let isCardFlipped = false;
        let userAnswers = {}; // { qId: [array of selected option indices] }
        let currentQuestionIndex = 0;
        let selectedQuizCategory = 'paket1'; // 'paket1', 'paket2', or 'all'
        let activeQuizList = QUIZ_DATA_PAKET1;
        let activeScoreFilter = 'all'; // 'all', 'paket1', or 'paket2'
        let showInstantAnswerMode = true; // TOGGLE: Immediate feedback key mode

        window.onload = function() {
            renderMateriGrid();
            renderFlashcard();
            updateActiveQuizList();
            renderQuizNav();
            renderQuestion(0);
        };

        // TAB NAVIGATION LOGIC
        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.getElementById(`tab-${tabId}`).classList.remove('hidden');

            document.querySelectorAll('.nav-btn').forEach(btn => {
                btn.classList.remove('bg-white', 'text-indigo-700', 'shadow-md');
                btn.classList.add('text-white', 'hover:bg-white/10');
            });

            const activeNav = document.getElementById(`nav-${tabId}`);
            if (activeNav) {
                activeNav.classList.add('bg-white', 'text-indigo-700', 'shadow-md');
                activeNav.classList.remove('text-white', 'hover:bg-white/10');
            }

            if (tabId === 'skor') {
                updateScoreSummary();
            }
        }

        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            menu.classList.toggle('hidden');
        }

        // MATERI SECTION RENDER
        function renderMateriGrid(materiList = MATERI_DATA) {
            const container = document.getElementById('materi-grid');
            document.getElementById('materi-count').textContent = materiList.length;

            if (materiList.length === 0) {
                container.innerHTML = `
                    <div class="col-span-full text-center py-12 bg-white rounded-3xl border border-slate-200">
                        <i class="fa-solid fa-magnifying-glass text-4xl text-slate-300 mb-3"></i>
                        <p class="text-slate-500 font-bold">Materi tidak ditemukan.</p>
                        <p class="text-xs text-slate-400 mt-1">Coba kata kunci pencarian yang lain.</p>
                    </div>
                `;
                return;
            }

            container.innerHTML = materiList.map(item => `
                <div class="bg-white rounded-3xl border border-slate-200 shadow-sm hover:shadow-xl transition-all duration-300 flex flex-col justify-between overflow-hidden group">
                    <div>
                        <div class="bg-gradient-to-r ${item.color} p-5 text-white flex items-center justify-between">
                            <span class="text-xs font-black uppercase tracking-wider bg-black/20 px-3 py-1 rounded-full">${item.tag}</span>
                            <i class="fa-solid ${item.icon} text-2xl opacity-80 group-hover:scale-110 transition-transform"></i>
                        </div>
                        <div class="p-6 space-y-4">
                            <h3 class="text-lg font-black text-slate-800 leading-snug">${item.title}</h3>
                            <p class="text-xs sm:text-sm text-slate-600 font-medium leading-relaxed bg-slate-50 p-3.5 rounded-2xl border border-slate-100">
                                ${item.summary}
                            </p>
                            <div class="space-y-2 text-xs text-slate-700">
                                ${item.details.map(d => `<div class="flex items-start"><i class="fa-solid fa-check text-emerald-500 mt-0.5 mr-2 shrink-0"></i><span>${d}</span></div>`).join('')}
                            </div>
                        </div>
                    </div>
                    <div class="px-6 pb-6 pt-2">
                        <button onclick="goToFlashcardById(${item.id})" class="w-full py-2.5 bg-slate-100 hover:bg-indigo-50 hover:text-indigo-600 text-slate-700 font-bold rounded-xl text-xs transition flex items-center justify-center">
                            <i class="fa-solid fa-clone mr-2"></i> Hafalkan di Flashcard
                        </button>
                    </div>
                </div>
            `).join('');
        }

        function filterMateri() {
            const query = document.getElementById('materi-search').value.toLowerCase();
            const filtered = MATERI_DATA.filter(m => 
                m.title.toLowerCase().includes(query) || 
                m.summary.toLowerCase().includes(query) ||
                m.tag.toLowerCase().includes(query)
            );
            renderMateriGrid(filtered);
        }

        // FLASHCARD SECTION RENDER
        function renderFlashcard() {
            const item = MATERI_DATA[currentFlashcardIndex];
            const fcElement = document.getElementById('flashcard-element');
            
            fcElement.classList.remove('rotate-y-180');
            isCardFlipped = false;

            setTimeout(() => {
                document.getElementById('fc-current-index').textContent = currentFlashcardIndex + 1;
                document.getElementById('fc-total-count').textContent = MATERI_DATA.length;

                document.getElementById('fc-badge-front').textContent = `Topik #${item.id} - ${item.tag}`;
                document.getElementById('fc-title-front').textContent = item.title;

                document.getElementById('fc-badge-back').textContent = `${item.tag} - Kata Kunci`;
                document.getElementById('fc-text-back').innerHTML = `
                    <strong class="block text-indigo-700 mb-2">${item.summary}</strong>
                    <ul class="space-y-1.5 text-xs text-slate-600">
                        ${item.details.map(d => `<li>• ${d}</li>`).join('')}
                    </ul>
                `;
            }, 150);
        }

        function flipCard() {
            const fcElement = document.getElementById('flashcard-element');
            isCardFlipped = !isCardFlipped;
            if (isCardFlipped) {
                fcElement.classList.add('rotate-y-180');
            } else {
                fcElement.classList.remove('rotate-y-180');
            }
        }

        function nextCard() {
            currentFlashcardIndex = (currentFlashcardIndex + 1) % MATERI_DATA.length;
            renderFlashcard();
        }

        function prevCard() {
            currentFlashcardIndex = (currentFlashcardIndex - 1 + MATERI_DATA.length) % MATERI_DATA.length;
            renderFlashcard();
        }

        function shuffleFlashcards() {
            MATERI_DATA.sort(() => Math.random() - 0.5);
            currentFlashcardIndex = 0;
            renderFlashcard();
        }

        function resetFlashcards() {
            MATERI_DATA.sort((a, b) => a.id - b.id);
            currentFlashcardIndex = 0;
            renderFlashcard();
        }

        function goToFlashcardById(id) {
            const index = MATERI_DATA.findIndex(m => m.id === id);
            if (index !== -1) {
                currentFlashcardIndex = index;
                switchTab('flashcard');
                renderFlashcard();
            }
        }

        // QUIZ CATEGORY LOGIC & INSTANT ANSWER MODE
        function toggleInstantAnswerMode(isCheck) {
            showInstantAnswerMode = isCheck;
            renderQuestion(currentQuestionIndex);
        }

        function updateActiveQuizList() {
            if (selectedQuizCategory === 'paket1') {
                activeQuizList = QUIZ_DATA_PAKET1;
                document.getElementById('quiz-package-label').textContent = "Progres (Paket 1: Soal 1-25)";
            } else if (selectedQuizCategory === 'paket2') {
                activeQuizList = QUIZ_DATA_PAKET2;
                document.getElementById('quiz-package-label').textContent = "Progres (Paket 2: Soal 26-50)";
            } else {
                activeQuizList = MASTER_QUIZ_DATA;
                document.getElementById('quiz-package-label').textContent = "Progres (Semua Soal 1-50)";
            }
        }

        function changeQuizCategory(val) {
            selectedQuizCategory = val;
            updateActiveQuizList();
            currentQuestionIndex = 0;
            renderQuizNav();
            renderQuestion(0);
        }

        function renderQuizNav() {
            const grid = document.getElementById('quiz-nav-grid');
            grid.innerHTML = activeQuizList.map((q, idx) => {
                const isAnswered = userAnswers[q.id] && userAnswers[q.id].length > 0;
                let bgClass = "bg-slate-100 text-slate-700 border-slate-200 hover:bg-slate-200";
                
                if (idx === currentQuestionIndex) {
                    bgClass = "bg-indigo-600 text-white font-black border-indigo-600 ring-2 ring-indigo-300";
                } else if (isAnswered) {
                    bgClass = "bg-emerald-100 text-emerald-800 border-emerald-300 font-bold";
                }

                return `
                    <button onclick="goToQuestion(${idx})" class="w-9 h-9 text-xs rounded-xl border transition flex items-center justify-center font-bold ${bgClass}">
                        ${q.id}
                    </button>
                `;
            }).join('');

            // Update Progress Bar
            const answeredCount = activeQuizList.filter(q => userAnswers[q.id] && userAnswers[q.id].length > 0).length;
            const totalCount = activeQuizList.length;
            document.getElementById('quiz-progress-text').textContent = `${answeredCount} / ${totalCount}`;
            document.getElementById('quiz-progress-bar').style.width = `${(answeredCount / totalCount) * 100}%`;
        }

        function renderQuestion(index) {
            currentQuestionIndex = index;
            const q = activeQuizList[index];
            const container = document.getElementById('quiz-card-container');
            const selected = userAnswers[q.id] || [];

            const isComplex = q.type === 'complex';
            const isAnswered = selected.length > 0;

            // Check correctness logic
            const isExactCorrect = isAnswered && selected.length === q.correct.length && selected.every(val => q.correct.includes(val));

            container.innerHTML = `
                <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2 border-b border-slate-100 pb-4">
                    <div class="flex items-center space-x-2">
                        <span class="px-3 py-1 bg-indigo-600 text-white font-black text-xs rounded-xl">Soal #${q.id}</span>
                        <span class="px-3 py-1 bg-slate-100 text-slate-700 font-bold text-xs rounded-xl">${q.topic}</span>
                    </div>
                    <div class="flex items-center space-x-2">
                        <span class="px-2.5 py-1 bg-amber-100 text-amber-800 font-bold text-xs rounded-lg uppercase">${q.category === 'paket1' ? 'Paket 1' : 'Paket 2'}</span>
                        ${isComplex 
                            ? `<span class="px-3 py-1 bg-purple-100 text-purple-700 font-extrabold text-xs rounded-xl"><i class="fa-solid fa-list-check mr-1"></i> PG Kompleks (Pilih Tepat 3 Opsi)</span>`
                            : `<span class="px-3 py-1 bg-blue-100 text-blue-700 font-extrabold text-xs rounded-xl"><i class="fa-solid fa-circle-dot mr-1"></i> PG Tunggal (Pilih 1 Opsi)</span>`
                        }
                    </div>
                </div>

                <!-- Stimulus / Case Study Box -->
                <div class="bg-gradient-to-r from-amber-50 via-orange-50 to-amber-50 p-5 rounded-2xl border-l-4 border-amber-500 text-slate-800 space-y-2">
                    <div class="flex items-center text-xs font-black text-amber-800 uppercase tracking-wider">
                        <i class="fa-solid fa-file-lines mr-2 text-amber-600"></i> Stimulus / Kasus Nyata:
                    </div>
                    <p class="text-sm font-medium leading-relaxed text-slate-700 italic">
                        "${q.stimulus}"
                    </p>
                </div>

                <!-- Question Text -->
                <div class="space-y-1">
                    <h3 class="text-base sm:text-lg font-black text-slate-800 leading-snug">${q.question}</h3>
                    ${isComplex 
                        ? `<p class="text-xs font-bold text-purple-600"><i class="fa-solid fa-triangle-exclamation mr-1"></i> Perhatian: Kamu harus memilih TEPAT 3 opsi jawaban!</p>`
                        : ``
                    }
                </div>

                <!-- Options Grid -->
                <div class="space-y-3 pt-2">
                    ${q.options.map((opt, optIdx) => {
                        const isChecked = selected.includes(optIdx);
                        const isCorrectOption = q.correct.includes(optIdx);
                        
                        let optionStyle = 'bg-white border-slate-200 text-slate-700 hover:border-slate-300 hover:bg-slate-50';

                        if (showInstantAnswerMode && isAnswered) {
                            if (isCorrectOption) {
                                optionStyle = 'bg-emerald-50 border-emerald-500 text-emerald-950 font-bold shadow-sm';
                            } else if (isChecked && !isCorrectOption) {
                                optionStyle = 'bg-rose-50 border-rose-400 text-rose-950 font-medium';
                            }
                        } else if (isChecked) {
                            optionStyle = 'bg-indigo-50 border-indigo-600 text-indigo-950 font-bold shadow-sm';
                        }

                        return `
                            <div onclick="selectOption(${q.id}, ${optIdx}, '${q.type}')" 
                                class="p-4 rounded-2xl border-2 cursor-pointer transition-all flex items-start space-x-3 ${optionStyle}">
                                <div class="mt-0.5 shrink-0">
                                    ${isComplex 
                                        ? `<div class="w-5 h-5 rounded-md border-2 flex items-center justify-center ${isChecked ? 'bg-indigo-600 border-indigo-600 text-white' : 'border-slate-300'}"><i class="fa-solid fa-check text-xs"></i></div>`
                                        : `<div class="w-5 h-5 rounded-full border-2 flex items-center justify-center ${isChecked ? 'border-indigo-600 bg-indigo-600 text-white' : 'border-slate-300'}"><div class="w-2 h-2 rounded-full bg-white"></div></div>`
                                    }
                                </div>
                                <div class="text-xs sm:text-sm leading-relaxed flex-grow">${opt}</div>
                                ${showInstantAnswerMode && isAnswered && isCorrectOption 
                                    ? `<span class="px-2 py-0.5 bg-emerald-100 text-emerald-800 text-[11px] font-black rounded-lg shrink-0"><i class="fa-solid fa-check mr-1"></i> Kunci</span>` 
                                    : ''
                                }
                            </div>
                        `;
                    }).join('')}
                </div>

                <!-- Instant Answer Key & Explanation Box (Appears when answered and mode is active) -->
                ${(showInstantAnswerMode && isAnswered) ? `
                    <div class="mt-6 p-5 rounded-2xl border ${isExactCorrect ? 'border-emerald-200 bg-emerald-50/70' : 'border-amber-200 bg-amber-50/70'} space-y-3 animate-fade-in">
                        <div class="flex items-center justify-between">
                            <div class="flex items-center space-x-2">
                                <span class="p-1.5 ${isExactCorrect ? 'bg-emerald-500' : 'bg-amber-500'} text-white rounded-xl text-xs font-black">
                                    <i class="fa-solid ${isExactCorrect ? 'fa-circle-check' : 'fa-lightbulb'}"></i>
                                </span>
                                <h4 class="font-extrabold text-sm ${isExactCorrect ? 'text-emerald-900' : 'text-amber-900'}">
                                    ${isExactCorrect ? 'Jawaban Kamu Tepat! 🎉' : (isComplex && selected.length < 3 ? 'Kunci Jawaban & Pembahasan Soal:' : 'Pembahasan & Kunci Jawaban Soal:')}
                                </h4>
                            </div>
                            <span class="text-xs font-bold ${isExactCorrect ? 'text-emerald-700' : 'text-amber-700'} uppercase tracking-wider">Kunci Jawaban Resmi</span>
                        </div>

                        <div class="bg-white p-4 rounded-xl border border-slate-200/80 space-y-2 text-xs">
                            <div class="font-bold text-slate-800">
                                <i class="fa-solid fa-key text-amber-500 mr-1.5"></i> Jawaban Benar:
                            </div>
                            <ul class="space-y-1 pl-4 list-disc text-slate-700">
                                ${q.correct.map(cIdx => `<li class="font-bold text-emerald-700">${q.options[cIdx]}</li>`).join('')}
                            </ul>
                        </div>

                        <div class="text-xs text-slate-700 leading-relaxed pt-1">
                            <strong class="text-indigo-900 block mb-1"><i class="fa-solid fa-graduation-cap text-indigo-600 mr-1"></i> Penjelasan Ilmiah:</strong>
                            ${q.explanation}
                        </div>
                    </div>
                ` : ''}
            `;

            // Handle Nav Buttons
            document.getElementById('btn-prev-q').disabled = (index === 0);
            document.getElementById('btn-prev-q').style.opacity = (index === 0) ? "0.5" : "1";

            if (index === activeQuizList.length - 1) {
                document.getElementById('btn-next-q').classList.add('hidden');
                document.getElementById('btn-finish-quiz').classList.remove('hidden');
            } else {
                document.getElementById('btn-next-q').classList.remove('hidden');
                document.getElementById('btn-finish-quiz').classList.add('hidden');
            }

            renderQuizNav();
        }

        function selectOption(qId, optIndex, type) {
            if (!userAnswers[qId]) {
                userAnswers[qId] = [];
            }

            if (type === 'single') {
                userAnswers[qId] = [optIndex];
            } else if (type === 'complex') {
                const currentArr = userAnswers[qId];
                if (currentArr.includes(optIndex)) {
                    userAnswers[qId] = currentArr.filter(i => i !== optIndex);
                } else {
                    if (currentArr.length < 3) {
                        userAnswers[qId].push(optIndex);
                    } else {
                        userAnswers[qId].shift();
                        userAnswers[qId].push(optIndex);
                    }
                }
            }

            renderQuestion(currentQuestionIndex);
        }

        function nextQuestion() {
            if (currentQuestionIndex < activeQuizList.length - 1) {
                renderQuestion(currentQuestionIndex + 1);
            }
        }

        function prevQuestion() {
            if (currentQuestionIndex > 0) {
                renderQuestion(currentQuestionIndex - 1);
            }
        }

        function goToQuestion(idx) {
            renderQuestion(idx);
        }

        function submitQuiz() {
            switchTab('skor');
        }

        // SCORE & PROGRESS SUMMARY CALCULATION (PAKET 1 & PAKET 2)
        function setScoreFilter(filterVal) {
            activeScoreFilter = filterVal;
            document.querySelectorAll('.score-filter-btn').forEach(btn => {
                btn.classList.remove('bg-white', 'text-indigo-700', 'shadow-sm');
                btn.classList.add('text-slate-600');
            });
            const activeBtn = document.getElementById(`score-filter-${filterVal}`);
            if (activeBtn) {
                activeBtn.classList.add('bg-white', 'text-indigo-700', 'shadow-sm');
                activeBtn.classList.remove('text-slate-600');
            }
            updateScoreSummary();
        }

        function updateScoreSummary() {
            let p1Correct = 0, p1Answered = 0, p1Total = QUIZ_DATA_PAKET1.length;
            let p2Correct = 0, p2Answered = 0, p2Total = QUIZ_DATA_PAKET2.length;
            let complexCorrect = 0, complexTotal = 0;

            MASTER_QUIZ_DATA.forEach(q => {
                if (q.type === 'complex') complexTotal++;

                const answers = userAnswers[q.id] || [];
                const isAnswered = answers.length > 0;
                const isExact = isAnswered && answers.length === q.correct.length && answers.every(val => q.correct.includes(val));

                if (q.category === 'paket1') {
                    if (isAnswered) p1Answered++;
                    if (isExact) p1Correct++;
                } else if (q.category === 'paket2') {
                    if (isAnswered) p2Answered++;
                    if (isExact) p2Correct++;
                }

                if (isExact && q.type === 'complex') {
                    complexCorrect++;
                }
            });

            const totalCorrect = p1Correct + p2Correct;
            const totalAnswered = p1Answered + p2Answered;
            const totalQuestions = MASTER_QUIZ_DATA.length;
            const percentage = Math.round((totalCorrect / totalQuestions) * 100);

            // Update Header Score Overview Cards
            document.getElementById('score-percentage').textContent = `${percentage}%`;
            document.getElementById('score-p1-count').textContent = `${p1Correct} / ${p1Total}`;
            document.getElementById('score-p2-count').textContent = `${p2Correct} / ${p2Total}`;
            document.getElementById('score-complex-count').textContent = `${complexCorrect} / ${complexTotal}`;
            document.getElementById('score-total-count').textContent = `${totalAnswered} / ${totalQuestions} Dijawab`;

            let gradeLabel = "Perlu Belajar Lagi 📚";
            let badgeHtml = `<span class="px-3 py-1.5 bg-rose-100 text-rose-700 font-bold text-xs rounded-full">Belum Lulus</span>`;

            if (percentage >= 85) {
                gradeLabel = "Sangat Luar Biasa! Master Penelitian Geografi 🏆";
                badgeHtml = `<span class="px-3 py-1.5 bg-emerald-100 text-emerald-800 font-bold text-xs rounded-full">Sangat Cerdas</span>`;
            } else if (percentage >= 70) {
                gradeLabel = "Bagus Sekali! Memahami Kisi-Kisi 👍";
                badgeHtml = `<span class="px-3 py-1.5 bg-blue-100 text-blue-800 font-bold text-xs rounded-full">Lulus Memuaskan</span>`;
            } else if (percentage >= 50) {
                gradeLabel = "Cukup Baik! Pelajari Lagi Beberapa Topik 💡";
                badgeHtml = `<span class="px-3 py-1.5 bg-amber-100 text-amber-800 font-bold text-xs rounded-full">Cukup</span>`;
            }

            document.getElementById('score-grade-label').textContent = gradeLabel;
            document.getElementById('score-status-badge').innerHTML = badgeHtml;

            // Filter Question Review List based on activeScoreFilter ('all', 'paket1', or 'paket2')
            let displayList = MASTER_QUIZ_DATA;
            if (activeScoreFilter === 'paket1') {
                displayList = QUIZ_DATA_PAKET1;
            } else if (activeScoreFilter === 'paket2') {
                displayList = QUIZ_DATA_PAKET2;
            }

            const reviewContainer = document.getElementById('score-review-list');
            if (displayList.length === 0) {
                reviewContainer.innerHTML = `<p class="text-slate-400 text-center py-8 text-sm italic">Belum ada data kuis.</p>`;
                return;
            }

            reviewContainer.innerHTML = displayList.map(q => {
                const answers = userAnswers[q.id] || [];
                const correct = q.correct;
                const isAnswered = answers.length > 0;
                const isExact = isAnswered && answers.length === correct.length && answers.every(val => correct.includes(val));

                return `
                    <div class="p-5 rounded-2xl border ${isExact ? 'border-emerald-200 bg-emerald-50/50' : 'border-rose-200 bg-rose-50/50'} space-y-3">
                        <div class="flex items-center justify-between text-xs">
                            <div class="flex items-center space-x-2">
                                <span class="px-2 py-0.5 bg-slate-800 text-white font-black rounded">${q.category === 'paket1' ? 'Paket 1' : 'Paket 2'}</span>
                                <span class="font-bold text-slate-700">Soal #${q.id} - ${q.topic} (${q.type === 'complex' ? 'PG Kompleks' : 'PG Tunggal'})</span>
                            </div>
                            <span class="font-black ${isExact ? 'text-emerald-600' : 'text-rose-600'}">
                                ${isExact ? '<i class="fa-solid fa-circle-check mr-1"></i> Benar' : (isAnswered ? '<i class="fa-solid fa-circle-xmark mr-1"></i> Kurang Tepat' : '<i class="fa-solid fa-circle-question mr-1"></i> Belum Dijawab')}
                            </span>
                        </div>
                        <p class="text-xs sm:text-sm font-bold text-slate-800">${q.question}</p>
                        
                        <div class="text-xs space-y-1 bg-white p-3 rounded-xl border border-slate-200">
                            <div><strong class="text-slate-600">Jawaban Kamu:</strong> ${answers.length > 0 ? answers.map(a => `<span class="inline-block bg-slate-100 px-2 py-0.5 rounded text-slate-800 font-medium mr-1">${q.options[a]}</span>`).join('') : '<span class="text-rose-500 italic">Belum diisi</span>'}</div>
                            <div><strong class="text-emerald-700">Kunci Jawaban Benar:</strong> ${correct.map(c => `<span class="inline-block bg-emerald-100 text-emerald-800 px-2 py-0.5 rounded font-bold mr-1">${q.options[c]}</span>`).join('')}</div>
                        </div>

                        <div class="text-xs text-slate-600 bg-indigo-50/70 p-3 rounded-xl border border-indigo-100">
                            <strong class="text-indigo-800"><i class="fa-solid fa-lightbulb text-yellow-500 mr-1"></i> Pembahasan:</strong> ${q.explanation}
                        </div>
                    </div>
                `;
            }).join('');
        }
    </script>
</body>
</html>