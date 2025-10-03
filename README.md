<!DOCTYPE html>
<html lang="ms">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portal Rasmi Kuiz Papan Suis Utama (PSU)</title>
    <!-- Muatkan Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Konfigurasi Tailwind untuk fon Inter -->
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f7f7f7; /* Latar belakang yang lembut */
        }
        /* Gaya bintang untuk visual "Taraf Bintang" */
        .star-icon {
            color: #FFD700; /* Emas */
            filter: drop-shadow(0 0 4px rgba(255, 215, 0, 0.7));
        }
    </style>
</head>
<body class="min-h-screen flex items-center justify-center p-4 bg-gray-100">

    <div id="quiz-portal" class="bg-white p-8 md:p-12 rounded-xl shadow-2xl w-full max-w-lg border-t-8 border-indigo-700">
        
        <!-- Tajuk & Taraf Bintang -->
        <header class="text-center mb-8">
            <div class="flex justify-center mb-4 space-x-1">
                <svg class="w-8 h-8 star-icon" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"></path></svg>
                <svg class="w-8 h-8 star-icon" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"></path></svg>
                <svg class="w-8 h-8 star-icon" fill="currentColor" viewBox="0 0 20 20"><path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"></path></svg>
            </div>
            <h1 class="text-3xl font-extrabold text-gray-800 mb-2">Kuiz Papan Suis Utama (PSU)</h1>
            <p class="text-lg text-indigo-700 font-semibold">Taraf Penting 3 Bintang</p>
            <p class="text-sm text-gray-500 mt-2">Untuk Pelajar P40 Semester 6 Sahaja</p>
        </header>

        <!-- Bahagian Kod Akses -->
        <section id="access-section" class="space-y-6">
            <p class="text-gray-600 text-center">Sila masukkan Kod Akses rasmi di bawah untuk memulakan kuiz:</p>

            <div class="flex flex-col sm:flex-row gap-3">
                <input 
                    type="text" 
                    id="access-code" 
                    placeholder="Masukkan Kod Akses di sini"
                    class="flex-grow p-3 border-2 border-gray-300 rounded-lg focus:ring-indigo-500 focus:border-indigo-500 text-center text-lg font-mono tracking-wider uppercase transition duration-300"
                    maxlength="10"
                />
                <button 
                    id="submit-button" 
                    onclick="checkAccessCode()"
                    class="w-full sm:w-auto px-6 py-3 bg-indigo-700 text-white font-bold rounded-lg hover:bg-indigo-800 focus:outline-none focus:ring-4 focus:ring-indigo-500 focus:ring-opacity-50 transition duration-300 shadow-md transform hover:scale-[1.02]"
                >
                    Sahkan Kod
                </button>
            </div>
            
            <p id="message" class="text-center font-medium h-6"></p>
        </section>

        <!-- Bahagian Kuiz (Tersembunyi pada mulanya) -->
        <section id="quiz-link-section" class="hidden text-center bg-green-50 p-6 rounded-xl border-2 border-green-300 shadow-inner">
            <div id="timer-box" class="mb-4">
                 <!-- Paparan Pemasa -->
                <p id="timer-status" class="text-sm font-semibold text-gray-700 mb-1">Masa Kuiz Tinggal:</p>
                <div id="timer-display" class="p-2 bg-red-600 text-white font-extrabold text-4xl rounded-lg shadow-xl tracking-wider">
                    55:00
                </div>
            </div>

            <p class="text-xl font-bold text-green-700 mb-4">Kod Akses Diterima! ✅</p>
            <p id="quiz-instruction" class="text-gray-700 mb-6">Anda kini boleh mengakses kuiz rasmi. Sila klik pautan di bawah:</p>
            <a 
                href="https://forms.gle/gz6pDcVsYpFFD5Ws8" 
                target="_blank" 
                rel="noopener noreferrer"
                id="quiz-link"
                class="inline-block px-8 py-3 text-lg bg-green-600 text-white font-extrabold rounded-full hover:bg-green-700 transition duration-300 transform hover:shadow-lg hover:scale-105 disabled:bg-gray-400"
                onclick="markAsAttempted()"
            >
                MULAKAN KUIZ SEKARANG
            </a>
            <p class="text-xs text-gray-500 mt-4">Kuiz akan dibuka dalam tetingkap baharu.</p>
        </section>

    </div>

    <script>
        // Kod Akses Rasmi
        const CORRECT_CODE = "psukuiz1";
        const QUIZ_DURATION_SECONDS = 55 * 60; // 3300 saat
        const TIMER_KEY = 'psuQuizStartTime';

        // Elemen DOM
        const messageElement = document.getElementById('message');
        const accessSection = document.getElementById('access-section');
        const quizLinkSection = document.getElementById('quiz-link-section');
        const inputElement = document.getElementById('access-code');
        const timerDisplay = document.getElementById('timer-display');
        const timerStatus = document.getElementById('timer-status');
        const quizLink = document.getElementById('quiz-link');
        const quizInstruction = document.getElementById('quiz-instruction');
        
        let timerInterval = null;
        // Objek untuk menjejaki amaran suara supaya ia hanya dimainkan sekali
        let alertsSent = { 900: false, 600: false, 300: false, 60: false };

        /**
         * Helper function to write a string to DataView
         */
        function writeString(view, offset, string) {
            for (let i = 0; i < string.length; i++) {
                view.setUint8(offset + i, string.charCodeAt(i));
            }
        }

        /**
         * Fungsi untuk menukar base64 kepada ArrayBuffer (untuk audio TTS)
         */
        function base64ToArrayBuffer(base64) {
            const binary_string = window.atob(base64);
            const len = binary_string.length;
            const bytes = new Uint8Array(len);
            for (let i = 0; i < len; i++) {
                bytes[i] = binary_string.charCodeAt(i);
            }
            return bytes.buffer;
        }

        /**
         * Fungsi untuk memproses PCM ke format WAV (untuk audio TTS)
         */
        function pcmToWav(pcm16, sampleRate) {
            const numChannels = 1;
            const bytesPerSample = 2; 

            const buffer = new ArrayBuffer(44 + pcm16.length * bytesPerSample);
            const view = new DataView(buffer);

            // Tulis header WAV
            writeString(view, 0, 'RIFF'); 
            view.setUint32(4, 36 + pcm16.length * bytesPerSample, true); 
            writeString(view, 8, 'WAVE'); 
            writeString(view, 12, 'fmt '); 
            view.setUint32(16, 16, true); 
            view.setUint16(20, 1, true); 
            view.setUint16(22, numChannels, true); 
            view.setUint32(24, sampleRate, true); 
            view.setUint32(28, sampleRate * numChannels * bytesPerSample, true); 
            view.setUint16(32, numChannels * bytesPerSample, true); 
            view.setUint16(34, 16, true); 
            writeString(view, 36, 'data'); 
            view.setUint32(40, pcm16.length * bytesPerSample, true); 

            // Tulis data PCM
            let offset = 44;
            for (let i = 0; i < pcm16.length; i++) {
                view.setInt16(offset, pcm16[i], true);
                offset += bytesPerSample;
            }

            return new Blob([view], { type: 'audio/wav' });
        }

        /**
         * Fungsi untuk menjana dan memainkan audio TTS (dengan backoff eksponen)
         */
        async function speakConfirmation(text, voiceName = "Kore") {
            const apiKey = "" 
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-tts:generateContent?key=${apiKey}`;

            const payload = {
                contents: [{ parts: [{ text: text }] }],
                generationConfig: {
                    responseModalities: ["AUDIO"],
                    speechConfig: { voiceConfig: { prebuiltVoiceConfig: { voiceName: voiceName } } }
                },
                model: "gemini-2.5-flash-preview-tts"
            };

            const maxRetries = 3;
            let currentDelay = 1000; 

            for (let i = 0; i < maxRetries; i++) {
                try {
                    const response = await fetch(apiUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });

                    if (!response.ok) {
                        throw new Error(`HTTP error! status: ${response.status}`);
                    }

                    const result = await response.json();
                    const part = result?.candidates?.[0]?.content?.parts?.[0];
                    const audioData = part?.inlineData?.data;
                    const mimeType = part?.inlineData?.mimeType;

                    if (audioData && mimeType && mimeType.startsWith("audio/")) {
                        const rateMatch = mimeType.match(/rate=(\d+)/);
                        const sampleRate = rateMatch ? parseInt(rateMatch[1], 10) : 24000;
                        
                        const pcmData = base64ToArrayBuffer(audioData);
                        const pcm16 = new Int16Array(pcmData);
                        const wavBlob = pcmToWav(pcm16, sampleRate);
                        const audioUrl = URL.createObjectURL(wavBlob);

                        const audio = new Audio(audioUrl);
                        audio.play();
                        break; 
                    } else {
                        throw new Error("Tiada data audio yang sah diterima.");
                    }
                } catch (error) {
                    console.error("Ralat dalam panggilan TTS API. Mencuba semula...", error);
                    if (i < maxRetries - 1) {
                        await new Promise(resolve => setTimeout(resolve, currentDelay));
                        currentDelay *= 2; 
                    } else {
                        console.error("Gagal menjana TTS selepas percubaan maksimum.");
                    }
                }
            }
        }
        
        /**
         * Fungsi untuk menghasilkan bunyi buzzer menggunakan Web Audio API
         */
        function playBeep() {
            try {
                const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
                const oscillator = audioCtx.createOscillator();
                const gainNode = audioCtx.createGain();

                oscillator.connect(gainNode);
                gainNode.connect(audioCtx.destination);

                oscillator.type = 'square';
                oscillator.frequency.setValueAtTime(880, audioCtx.currentTime); // Nada lebih tinggi
                gainNode.gain.setValueAtTime(0.5, audioCtx.currentTime);
                gainNode.gain.exponentialRampToValueAtTime(0.001, audioCtx.currentTime + 0.5); 

                oscillator.start();
                oscillator.stop(audioCtx.currentTime + 0.5); 
            } catch (e) {
                console.warn("Web Audio API tidak tersedia atau disekat.");
            }
        }

        /**
         * Fungsi untuk mengemas kini paparan pemasa dan menguruskan amaran
         */
        function updateTimerDisplay() {
            const startTime = parseInt(localStorage.getItem(TIMER_KEY), 10);
            if (!startTime) {
                clearInterval(timerInterval);
                return;
            }

            const elapsedTime = Math.floor((Date.now() - startTime) / 1000);
            let remainingTime = QUIZ_DURATION_SECONDS - elapsedTime;

            // Pastikan masa tidak negatif
            if (remainingTime < 0) {
                remainingTime = 0;
                clearInterval(timerInterval);
                handleQuizExpiry();
            }

            const minutes = Math.floor(remainingTime / 60);
            const seconds = remainingTime % 60;
            
            // Format paparan MM:SS
            const displayMinutes = String(minutes).padStart(2, '0');
            const displaySeconds = String(seconds).padStart(2, '0');
            timerDisplay.textContent = `${displayMinutes}:${displaySeconds}`;

            // Tetapkan warna pemasa berdasarkan masa yang tinggal
            if (remainingTime <= 300) { // 5 minit terakhir
                timerDisplay.classList.remove('bg-red-600', 'bg-orange-500');
                timerDisplay.classList.add('bg-red-800');
            } else if (remainingTime <= 900) { // 15 minit terakhir
                timerDisplay.classList.remove('bg-red-600', 'bg-red-800');
                timerDisplay.classList.add('bg-orange-500');
            } else {
                timerDisplay.classList.remove('bg-orange-500', 'bg-red-800');
                timerDisplay.classList.add('bg-red-600');
            }


            // --- Logik Amaran Suara (TTS) ---
            
            // Amaran 15 Minit (900 saat)
            if (remainingTime === 900 && !alertsSent[900]) {
                speakConfirmation("Masa tinggal 15 minit.");
                alertsSent[900] = true;
            }
            
            // Amaran 10 Minit (600 saat)
            if (remainingTime === 600 && !alertsSent[600]) {
                speakConfirmation("Masa tinggal 10 minit untuk 10 minit yang terakhir.");
                alertsSent[600] = true;
            }

            // Amaran 5 Minit (300 saat)
            if (remainingTime === 300 && !alertsSent[300]) {
                speakConfirmation("Masa tinggal 5 minit.");
                alertsSent[300] = true;
            }
            
            // Amaran 1 Minit (60 saat) - Bunyi Buzzer
            if (remainingTime === 60 && !alertsSent[60]) {
                speakConfirmation("Masa tinggal 1 minit. Kuiz akan tamat sebentar lagi.");
                playBeep(); // Buzzer
                alertsSent[60] = true;
            }
            
            // Amaran Tamat Masa (0 saat)
            if (remainingTime === 0) {
                handleQuizExpiry();
            }
        }

        /**
         * Mengendalikan penamatan kuiz apabila pemasa mencapai 0:00
         */
        function handleQuizExpiry() {
            clearInterval(timerInterval);
            timerDisplay.textContent = "00:00";
            timerDisplay.classList.remove('bg-red-800');
            timerDisplay.classList.add('bg-gray-500');
            
            timerStatus.textContent = "MASA SUDAH TAMAT! Kuiz ditutup.";
            timerStatus.classList.remove('text-red-500');
            timerStatus.classList.add('text-gray-700');

            quizInstruction.textContent = "Masa kuiz telah tamat. Anda tidak lagi dibenarkan untuk menghantar jawapan.";
            quizLink.textContent = "MASA TAMAT";
            quizLink.classList.add('disabled', 'cursor-not-allowed');
            quizLink.removeAttribute('href'); // Menyatakan tidak boleh diakses

            localStorage.removeItem('psuQuizAccessed'); // Boleh alih keluar kunci akses tempatan
            localStorage.setItem('psuQuizExpired', 'true');
        }

        /**
         * Fungsi untuk memulakan pemasa undur
         */
        function startTimer() {
            // Jika masa telah tamat sebelum ini, jangan mulakan
            if (localStorage.getItem('psuQuizExpired') === 'true') {
                handleQuizExpiry();
                return;
            }
            
            // Mulakan pemasa hanya jika ia belum berjalan
            if (!timerInterval) {
                updateTimerDisplay(); // Panggilan segera untuk mengemas kini UI
                timerInterval = setInterval(updateTimerDisplay, 1000);
            }
        }

        /**
         * Fungsi untuk menyemak kod akses
         */
        function checkAccessCode() {
            const enteredCode = inputElement.value.toLowerCase().trim();
            messageElement.textContent = '';
            
            if (enteredCode === CORRECT_CODE) {
                // Kod Sah
                messageElement.classList.remove('text-red-600');
                messageElement.classList.add('text-green-600');
                messageElement.textContent = 'Kod sah. Sila tunggu sebentar...';
                
                // Tetapkan masa mula hanya jika ia belum ditetapkan (kali pertama)
                if (!localStorage.getItem(TIMER_KEY)) {
                    localStorage.setItem(TIMER_KEY, Date.now());
                }

                speakConfirmation("Kod akses sah. Anda boleh memulakan kuiz sekarang.");
                
                setTimeout(() => {
                    accessSection.classList.add('hidden');
                    quizLinkSection.classList.remove('hidden');
                    localStorage.setItem('psuQuizAccessed', 'true');
                    startTimer(); // Mulakan pemasa
                }, 1500);

            } else {
                // Kod Tidak Sah
                messageElement.classList.remove('text-green-600');
                messageElement.classList.add('text-red-600');
                messageElement.textContent = 'Kod Akses Tidak Sah. Sila cuba lagi.';
                speakConfirmation("Kod akses tidak sah. Sila cuba lagi.", "Achernar"); 
            }
        }

        /**
         * Fungsi untuk menanda kuiz telah diakses (menggunakan localStorage)
         */
        function markAsAttempted() {
            // Ini hanyalah untuk UI/rekod tempatan. Kuiz sebenar diuruskan oleh Google Form.
            localStorage.setItem('psuQuizAttempted', 'true');
        }

        /**
         * Logik permulaan: Semak status akses tempatan
         */
        window.onload = function() {
            // Tambahkan event listener untuk butang 'Enter'
            inputElement.addEventListener('keypress', function(event) {
                if (event.key === 'Enter') {
                    event.preventDefault(); 
                    checkAccessCode();
                }
            });

            // Semak status akses tempatan
            if (localStorage.getItem('psuQuizAccessed') === 'true') {
                accessSection.classList.add('hidden');
                quizLinkSection.classList.remove('hidden');
                messageElement.textContent = ''; 
                startTimer(); // Terus mulakan pemasa
            } else if (localStorage.getItem('psuQuizExpired') === 'true') {
                 // Jika pemasa telah tamat, tunjukkan keadaan tamat masa
                accessSection.classList.add('hidden');
                quizLinkSection.classList.remove('hidden');
                handleQuizExpiry();
            }
        }
    </script>

</body>
</html>
