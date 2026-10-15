<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Live USA Weather Monitor</title>
    <!-- Fixed Tailwind CSS CDN link -->
    <script src="https://jsdelivr.net"></script>
    <!-- Fixed Lucide Icons Package CDN Link -->
    <script src="https://unpkg.com"></script>
    <style>
        .weather-bg-clear { background: linear-gradient(to bottom, #7dd3fc, #38bdf8); }
        .weather-bg-rain { background: linear-gradient(to bottom, #94a3b8, #475569); }
        .weather-bg-storm { background: linear-gradient(to bottom, #475569, #1e293b); }
        .animate-pulse-slow { animation: pulse 3s cubic-bezier(0.4, 0, 0.6, 1) infinite; }
    </style>
</head>
<body class="bg-slate-900 text-white min-h-screen flex flex-col items-center p-4 sm:p-6 transition-all duration-500 weather-bg-clear" id="appBackground">

    <div class="w-full max-w-md bg-slate-950/80 backdrop-blur-md rounded-3xl p-6 shadow-2xl border border-white/10 space-y-6">
        
        <!-- Header & Branding Wrapper -->
        <div class="flex justify-between items-center border-b border-white/10 pb-4">
            <div>
                <h1 class="text-xl font-bold tracking-tight flex items-center gap-2">
                    <i data-lucide="cloud-lightning" class="text-sky-400"></i> PulseWeather
                </h1>
                <p class="text-xs text-slate-400 mt-0.5">Aggregated High-Fidelity Data & NWS Active Alerts</p>
            </div>
            <div class="bg-sky-500/20 text-sky-300 text-[10px] font-semibold px-2 py-1 rounded-full uppercase tracking-wider animate-pulse-slow flex items-center gap-1">
                <span class="w-1.5 h-1.5 bg-sky-400 rounded-full"></span> Live Updates
            </div>
        </div>

        <!-- Location Controls Context Wrapper -->
        <div class="space-y-3">
            <button onclick="getUserLocation()" class="w-full bg-sky-600 hover:bg-sky-500 active:scale-[0.98] transition-all font-medium py-3 px-4 rounded-xl flex items-center justify-center gap-2 shadow-lg shadow-sky-600/20">
                <i data-lucide="map-pin" class="w-5 h-5"></i> Use Phone GPS Location
            </button>
            
            <div class="relative flex items-center">
                <div class="absolute inset-0 flex items-center"><div class="w-full border-t border-white/5"></div></div>
                <div class="relative w-full text-center"><span class="bg-slate-950 px-2 text-xs text-slate-500 uppercase tracking-widest">or search manually</span></div>
            </div>

            <div class="flex gap-2">
                <input type="text" id="cityInput" placeholder="Enter City or 5-digit ZIP..." class="w-full bg-slate-900 border border-white/10 rounded-xl px-4 py-2.5 text-sm focus:outline-none focus:border-sky-500 transition-colors placeholder:text-slate-500">
                <button onclick="getManualLocation()" class="bg-slate-800 hover:bg-slate-700 px-4 rounded-xl transition-colors">
                    <i data-lucide="search" class="w-5 h-5 text-slate-300"></i>
                </button>
            </div>
        </div>

        <!-- Dynamic Weather Payload Cards -->
        <div id="weatherDisplay" class="space-y-6 hidden">
            <!-- Core Metric Card -->
            <div class="text-center py-4 space-y-2">
                <h2 id="locationName" class="text-2xl font-bold tracking-wide">Helena, MT</h2>
                <div class="flex justify-center items-center gap-4">
                    <div id="weatherIconContainer">
                        <i data-lucide="sun" class="w-16 h-16 text-amber-400"></i>
                    </div>
                    <span id="currentTemp" class="text-6xl font-black tracking-tighter">72°</span>
                </div>
                <p id="weatherCondition" class="text-lg font-medium text-sky-200 capitalize">Clear Sky</p>
            </div>

            <!-- Contextual Grid Attributes -->
            <div class="grid grid-cols-2 gap-3 bg-white/5 p-4 rounded-2xl border border-white/5 text-sm">
                <div class="flex items-center gap-3 p-2">
                    <i data-lucide="droplets" class="text-blue-400 w-5 h-5"></i>
                    <div>
                        <p class="text-xs text-slate-400">Humidity</p>
                        <p id="humidityVal" class="font-semibold">45%</p>
                    </div>
                </div>
                <div class="flex items-center gap-3 p-2">
                    <i data-lucide="wind" class="text-teal-400 w-5 h-5"></i>
                    <div>
                        <p class="text-xs text-slate-400">Wind Velocity</p>
                        <p id="windVal" class="font-semibold">12 mph</p>
                    </div>
                </div>
            </div>

            <!-- Active Alerts Container Framework -->
            <div id="alertBox" class="hidden border rounded-2xl p-4 bg-amber-500/10 border-amber-500/30 text-amber-200 space-y-2">
                <div class="flex items-center gap-2 font-bold text-sm">
                    <i data-lucide="alert-triangle" class="text-amber-400 animate-bounce"></i>
                    <span id="alertTitle">Active Hazardous Weather Alert</span>
                </div>
                <p id="alertDesc" class="text-xs text-amber-300/90 leading-relaxed">No critical hazards flagged for this coordinates sector.</p>
            </div>
        </div>

        <!-- Informational Status Indicators -->
        <div id="statusMessage" class="text-center text-sm text-slate-400 py-8 flex flex-col items-center gap-3">
            <i data-lucide="cloud-sun" class="w-12 h-12 text-slate-600 animate-pulse-slow"></i>
            <span>Grant browser location authorization or enter a city context above to mount active weather indices.</span>
        </div>

    </div>

    <!-- Scripting Engine Logic for API Pipeline Orchestration -->
    <script>
        // Initialize Lucide iconography structures
        lucide.createIcons();

        // High frequency continuous background updating (every 5 minutes)
        let autoUpdateInterval = null;
        let currentLatitude = null;
        let currentLongitude = null;

        // Corrected base production API endpoints
        const METEO_URL = "https://open-meteo.com";
        const NOMINATIM_URL = "https://openstreetmap.org";
        const NWS_ALERT_URL = "https://weather.gov";

        async function getUserLocation() {
            showLoading(true);
            if (!navigator.geolocation) {
                alert("Geolocation mapping is unsupported on this mobile hardware profile.");
                showLoading(false);
                return;
            }
            navigator.geolocation.getCurrentPosition(
                async (position) => {
                    currentLatitude = position.coords.latitude;
                    currentLongitude = position.coords.longitude;
                    await fetchUnifiedWeatherData(currentLatitude, currentLongitude, "Your Current Sector");
                    setupContinuousSync();
                },
                (error) => {
                    alert("Unable to fetch location configuration. Please grant system permissions or input manually.");
                    showLoading(false);
                },
                { enableHighAccuracy: true, timeout: 10000 }
            );
        }

        async function getManualLocation() {
            const query = document.getElementById('cityInput').value.trim();
            if (!query) return;
            showLoading(true);

            try {
                const res = await fetch(`${NOMINATIM_URL}?q=${encodeURIComponent(query)}&countrycodes=us&format=json&limit=1`);
                const data = await res.json();
                if (data && data.length > 0) {
                    currentLatitude = parseFloat(data[0].lat);
                    currentLongitude = parseFloat(data[0].lon);
                    await fetchUnifiedWeatherData(currentLatitude, currentLongitude, data[0].display_name.split(',')[0]);
                    setupContinuousSync();
                } else {
                    alert("Location context could not be parsed. Ensure lookup is limited to US entities.");
                    showLoading(false);
                }
            } catch (err) {
                console.error("Geocoding transaction failed:", err);
                showLoading(false);
            }
        }

        async function fetchUnifiedWeatherData(lat, lon, displayName) {
            try {
                // Fixed query parameter injection mapping
                const [weatherRes, alertRes] = await Promise.all([
                    fetch(`${METEO_URL}?latitude=${lat}&longitude=${lon}&current=temperature_2m,relative_humidity_2m,apparent_temperature,is_day,precipitation,rain,showers,snowfall,weather_code,wind_speed_10m&temperature_unit=fahrenheit&wind_speed_unit=mph&precipitation_unit=inch`),
                    fetch(`${NWS_ALERT_URL}?point=${lat.toFixed(4)},${lon.toFixed(4)}`, { headers: { 'User-Agent': 'PulseWeatherWebClient/1.0' } })
                ]);

                const weatherData = await weatherRes.json();
                const alertData = await alertRes.json();

                renderWeatherMetrics(weatherData.current, displayName);
                renderActiveAlerts(alertData);
                showLoading(false);
            } catch (error) {
                console.error("Unified network request pipeline dropped context:", error);
                alert("Synchronization error pipeline exception. Displaying cached elements if present.");
                showLoading(false);
            }
        }

        function renderWeatherMetrics(current, label) {
            document.getElementById('statusMessage').classList.add('hidden');
