# KinderwagenApp

 <!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kinderwagen Tracker</title>
    <style>
        :root {
            --color-primary: #38bdf8;
            --color-primary-hover: #0284c7;
            --color-bg: #0f172a;
            --color-surface: #1e293b;
            --color-text: #f1f5f9;
            --color-text-secondary: #cbd5e1;
            --color-success: #22c55e;
            --color-warning: #f97316;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif;
            background-color: var(--color-bg);
            color: var(--color-text);
            padding: 20px;
            line-height: 1.6;
        }

        .container {
            max-width: 600px;
            margin: 0 auto;
        }

        h1 {
            font-size: 28px;
            margin-bottom: 8px;
            text-align: center;
            color: var(--color-primary);
        }

        .subtitle {
            text-align: center;
            color: var(--color-text-secondary);
            margin-bottom: 24px;
            font-size: 14px;
        }

        .section {
            background-color: var(--color-surface);
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 20px;
            border: 1px solid rgba(148, 163, 184, 0.2);
        }

        .section-title {
            font-size: 16px;
            font-weight: 600;
            margin-bottom: 16px;
            color: var(--color-primary);
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .form-group {
            margin-bottom: 16px;
        }

        label {
            display: block;
            font-size: 14px;
            margin-bottom: 6px;
            color: var(--color-text-secondary);
            font-weight: 500;
        }

        input, textarea, select {
            width: 100%;
            padding: 12px;
            border: 1px solid rgba(148, 163, 184, 0.3);
            border-radius: 8px;
            background-color: rgba(30, 41, 59, 0.5);
            color: var(--color-text);
            font-size: 14px;
            font-family: inherit;
            transition: border-color 0.2s;
        }

        input:focus, textarea:focus, select:focus {
            outline: none;
            border-color: var(--color-primary);
            background-color: rgba(30, 41, 59, 0.8);
        }

        textarea {
            resize: vertical;
            min-height: 80px;
        }

        .button-group {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
            margin-top: 20px;
        }

        button {
            padding: 12px 24px;
            border: none;
            border-radius: 8px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
        }

        .btn-primary {
            background-color: var(--color-primary);
            color: #0f172a;
            grid-column: 1 / -1;
        }

        .btn-primary:hover {
            background-color: var(--color-primary-hover);
            transform: translateY(-2px);
        }

        .btn-secondary {
            background-color: var(--color-warning);
            color: white;
        }

        .btn-secondary:hover {
            opacity: 0.9;
        }

        .btn-danger {
            background-color: #ef4444;
            color: white;
        }

        .btn-danger:hover {
            opacity: 0.9;
        }

        .stats {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
            margin-bottom: 20px;
        }

        .stat-box {
            background-color: rgba(56, 189, 248, 0.1);
            border-left: 4px solid var(--color-primary);
            padding: 12px;
            border-radius: 6px;
            text-align: center;
        }

        .stat-value {
            font-size: 24px;
            font-weight: bold;
            color: var(--color-primary);
        }

        .stat-label {
            font-size: 12px;
            color: var(--color-text-secondary);
            margin-top: 4px;
        }

        .walk-entry {
            background-color: rgba(56, 189, 248, 0.05);
            border-left: 4px solid var(--color-success);
            padding: 12px;
            margin-bottom: 12px;
            border-radius: 6px;
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
        }

        .walk-info {
            flex: 1;
        }

        .walk-date {
            font-size: 12px;
            color: var(--color-text-secondary);
        }

        .walk-time {
            font-size: 14px;
            font-weight: 600;
            color: var(--color-primary);
            margin: 4px 0;
        }

        .walk-notes {
            font-size: 13px;
            color: var(--color-text-secondary);
            margin-top: 4px;
        }

        .walk-actions {
            display: flex;
            gap: 8px;
        }

        .btn-small {
            padding: 6px 12px;
            font-size: 12px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.2s;
        }

        .btn-small-danger {
            background-color: #dc2626;
            color: white;
        }

        .btn-small-danger:hover {
            background-color: #991b1b;
        }

        .empty-state {
            text-align: center;
            padding: 40px 20px;
            color: var(--color-text-secondary);
        }

        .empty-state-icon {
            font-size: 48px;
            margin-bottom: 16px;
        }

        .time-display {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
            margin-bottom: 16px;
        }

        .time-input-group {
            display: flex;
            gap: 8px;
            align-items: flex-end;
        }

        .time-input-group input {
            flex: 1;
        }

        .quick-action {
            display: flex;
            gap: 8px;
            margin-top: 12px;
        }

        .quick-action button {
            flex: 1;
            padding: 10px;
            font-size: 13px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>👶 Kinderwagen Tracker</h1>
        <p class="subtitle">Tracke deine Spaziergänge mit dem Kinderwagen</p>

        <!-- Tracking Section -->
        <div class="section">
            <div class="section-title">🕐 Neuer Spaziergang</div>
            
            <div class="form-group">
                <label>Startzeit</label>
                <input type="datetime-local" id="startTime">
            </div>

            <div class="form-group">
                <label>Transportmittel</label>
                <select id="transportType">
                    <option value="">-- Auswählen --</option>
                    <option value="Kinderwagen">🛏️ Kinderwagen</option>
                    <option value="Trage">👶 Trage</option>
                </select>
            </div>

            <div class="form-group">
                <label>Gewicht des Kindes (kg)</label>
                <input type="number" id="childWeight" placeholder="z.B. 7.5" step="0.1" min="0">
            </div>

            <div class="form-group">
                <label>Wetter</label>
                <select id="weather">
                    <option value="">-- Wetter auswählen --</option>
                    <option value="Sonnig">☀️ Sonnig</option>
                    <option value="Bewölkt">☁️ Bewölkt</option>
                    <option value="Regen">🌧️ Regen</option>
                    <option value="Schnee">❄️ Schnee</option>
                    <option value="Nebel">🌫️ Nebel</option>
                </select>
            </div>

            <div class="form-group">
                <label>Notizen (optional)</label>
                <textarea id="notes" placeholder="z.B. Kind war glücklich, unterwegs Eis gegessen..."></textarea>
            </div>

            <div class="form-group">
                <button class="btn-secondary" onclick="connectSpotify()" style="width: 100%;" id="spotifyBtn">🎵 Spotify verbinden</button>
                <div id="spotifyStatus" style="font-size: 12px; color: var(--color-text-secondary); padding: 8px; background-color: rgba(30, 200, 136, 0.1); border-radius: 6px; margin-top: 8px;">
                    Spotify-Verbindung wird hier angezeigt
                </div>
                <div id="spotifyNowPlaying" style="font-size: 12px; margin-top: 8px; padding: 8px; background-color: rgba(30, 41, 59, 0.5); border-radius: 6px; display: none;">
                    <div id="spotifyTrack">🎵 Aktueller Track: --</div>
                    <div id="spotifyArtist" style="margin-top: 4px;">👤 Künstler: --</div>
                </div>
            </div>

            <div class="form-group" id="locationGroup" style="display: none;">
                <label>📍 Route wird aufgezeichnet...</label>
                <div id="locationStatus" style="font-size: 12px; color: var(--color-success); padding: 8px; background-color: rgba(34, 197, 94, 0.1); border-radius: 6px; margin-top: 8px;">
                    Bereit zur Aufzeichnung
                </div>
                <div id="mapContainer" style="width: 100%; height: 300px; border-radius: 8px; margin-top: 12px; background-color: rgba(30, 41, 59, 0.5); border: 1px solid rgba(148, 163, 184, 0.3); display: none;"></div>
            </div>

            <div class="form-group" id="healthGroup" style="display: none;">
                <label>⌚ Apple Watch Health Daten</label>
                <button class="btn-secondary" onclick="connectHealthKit()" style="width: 100%; margin-top: 8px;" id="healthBtn">⌚ Health Daten verbinden</button>
                <div id="healthStatus" style="font-size: 12px; color: var(--color-text-secondary); padding: 8px; background-color: rgba(56, 189, 248, 0.1); border-radius: 6px; margin-top: 8px;">
                    Health-Daten werden hier angezeigt
                </div>
                <div id="healthData" style="font-size: 12px; margin-top: 8px;">
                    <div style="padding: 8px; background-color: rgba(30, 41, 59, 0.5); border-radius: 6px;">
                        <div id="heartRate">❤️ Puls: --</div>
                        <div id="calories" style="margin-top: 4px;">🔥 Kalorien: --</div>
                        <div id="steps" style="margin-top: 4px;">👟 Schritte: --</div>
                        <div id="distance" style="margin-top: 4px;">📏 Distanz: --</div>
                    </div>
                </div>
            </div>

            <div class="form-group">
                <label>📊 Aktuelle Sitzung</label>
                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-top: 8px;">
                    <div style="background-color: rgba(56, 189, 248, 0.1); padding: 12px; border-radius: 6px; text-align: center;">
                        <div style="font-size: 24px; font-weight: bold; color: var(--color-primary);" id="sessionTime">0:00</div>
                        <div style="font-size: 12px; color: var(--color-text-secondary); margin-top: 4px;">Zeit</div>
                    </div>
                    <div style="background-color: rgba(56, 189, 248, 0.1); padding: 12px; border-radius: 6px; text-align: center;">
                        <div style="font-size: 24px; font-weight: bold; color: var(--color-primary);" id="sessionDistance">0.0 km</div>
                        <div style="font-size: 12px; color: var(--color-text-secondary); margin-top: 4px;">Strecke</div>
                    </div>
                </div>
            </div>

            <div class="quick-action">
                <button class="btn-secondary" onclick="toggleTimer()" id="timerBtn" style="grid-column: 1 / -1; font-size: 16px;">▶️ START</button>
            </div>

            <div class="button-group">
                <button class="btn-primary" onclick="addWalk()">✓ Spaziergang speichern</button>
            </div>
        </div>

        <!-- Statistics Section -->
        <div class="section" id="statsSection" style="display: none;">
            <div class="section-title">📊 Statistiken</div>
            <div class="stats">
                <div class="stat-box">
                    <div class="stat-value" id="totalWalks">0</div>
                    <div class="stat-label">Spaziergänge gesamt</div>
                </div>
                <div class="stat-box">
                    <div class="stat-value" id="totalMinutes">0</div>
                    <div class="stat-label">Minuten total</div>
                </div>
                <div class="stat-box">
                    <div class="stat-value" id="avgMinutes">0</div>
                    <div class="stat-label">Ø Dauer (Min)</div>
                </div>
                <div class="stat-box">
                    <div class="stat-value" id="longestWalk">0</div>
                    <div class="stat-label">Längster (Min)</div>
                </div>
            </div>
        </div>

        <!-- History Section -->
        <div class="section">
            <div class="section-title">📝 Spaziergänge (aktuelle Sitzung)</div>
            <div id="walksList" class="empty-state">
                <div class="empty-state-icon">👶</div>
                <p>Noch keine Spaziergänge aufgezeichnet</p>
            </div>
        </div>

        <!-- Clear Data -->
        <div class="section">
            <button class="btn-danger" onclick="clearAllData()" style="width: 100%;">🗑️ Alle Daten löschen</button>
        </div>
    </div>

    <script>
        let walks = [];
        let isTimerRunning = false;
        let timerStartTime = null;
        let timerInterval = null;
        let trackingData = {
            locations: [],
            distance: 0,
            startTime: null
        };
        let sessionStartTime = null;
        let sessionInterval = null;
        let healthData = {
            heartRate: null,
            calories: null,
            steps: null,
            distance: null
        };
        let spotifyData = {
            isConnected: false,
            currentTrack: null,
            currentArtist: null
        };

        // Initialize
        function init() {
            setDefaultTimes();
            displayWalks();
            updateStats();
            checkGeolocationSupport();
        }

        // Check if geolocation is supported
        function checkGeolocationSupport() {
            if (navigator.geolocation) {
                document.getElementById('locationGroup').style.display = 'block';
            } else {
                alert('Geolokalisierung wird von deinem Browser nicht unterstützt');
            }
            
            // Check if on iOS and HealthKit is available
            if (/iPhone|iPad|iPod/.test(navigator.userAgent)) {
                document.getElementById('healthGroup').style.display = 'block';
            }
        }

        // Connect to Spotify
        function connectSpotify() {
            // Spotify OAuth would be implemented here in a real app
            // For this demo, we'll show simulated data
            alert('Spotify wird verbunden...\n\nIn einer echten App würde dies über Spotify OAuth erfolgen und den aktuell spielenden Track anzeigen.');
            
            // Simulate Spotify connection
            spotifyData.isConnected = true;
            spotifyData.currentTrack = 'Hush, Hush (Instrumental)';
            spotifyData.currentArtist = 'Pussycat Dolls';
            
            updateSpotifyDisplay();
            document.getElementById('spotifyBtn').textContent = '✓ Spotify verbunden';
            document.getElementById('spotifyBtn').disabled = true;
        }

        // Update Spotify display
        function updateSpotifyDisplay() {
            document.getElementById('spotifyStatus').textContent = '✓ Mit Spotify verbunden';
            document.getElementById('spotifyNowPlaying').style.display = 'block';
            document.getElementById('spotifyTrack').textContent = `🎵 Aktueller Track: ${spotifyData.currentTrack}`;
            document.getElementById('spotifyArtist').textContent = `👤 Künstler: ${spotifyData.currentArtist}`;
        }

        // Connect to Apple Health
        function connectHealthKit() {
            // For iOS devices with HealthKit support
            const isIOS = /iPhone|iPad|iPod/.test(navigator.userAgent);
            
            if (!isIOS) {
                alert('Apple Health ist nur auf iOS-Geräten verfügbar');
                return;
            }

            // Simulate Health Data - In einer echten App würde dies über HealthKit API erfolgen
            // Da Web-Apps keinen direkten Zugriff auf HealthKit haben, zeigen wir simulierte Daten
            alert('Health-Daten werden in einer echten App über die native HealthKit API abgerufen.\n\nFür diese Web-App werden realistische Beispieldaten verwendet.');
            
            // Generate realistic sample data
            healthData = {
                heartRate: Math.floor(Math.random() * 40 + 100), // 100-140 bpm
                calories: Math.floor(Math.random() * 150 + 100), // 100-250 kcal
                steps: Math.floor(Math.random() * 3000 + 2000), // 2000-5000 steps
                distance: (Math.random() * 3 + 1).toFixed(2) // 1-4 km
            };

            updateHealthDisplay();
            document.getElementById('healthBtn').textContent = '✓ Health Daten verbunden';
            document.getElementById('healthBtn').disabled = true;
        }

        // Update health display
        function updateHealthDisplay() {
            document.getElementById('heartRate').textContent = `❤️ Puls: ${healthData.heartRate} bpm`;
            document.getElementById('calories').textContent = `🔥 Kalorien: ${healthData.calories} kcal`;
            document.getElementById('steps').textContent = `👟 Schritte: ${healthData.steps}`;
            document.getElementById('distance').textContent = `📏 Distanz: ${healthData.distance} km`;
            document.getElementById('healthStatus').textContent = '✓ Health-Daten verbunden - Klick auf "Spaziergang speichern" um zu speichern';
        }

        // Toggle timer
        function toggleTimer() {
            if (!isTimerRunning) {
                startTimer();
            } else {
                stopTimer();
            }
        }

        // Start timer
        function startTimer() {
            timerStartTime = new Date();
            if (!sessionStartTime) {
                sessionStartTime = timerStartTime;
            }
            isTimerRunning = true;
            document.getElementById('timerBtn').textContent = '⏹️ STOP';
            document.getElementById('timerBtn').style.backgroundColor = '#ef4444';
            document.getElementById('startTime').value = formatDateTimeLocal(timerStartTime);

            // Update timer display every second
            timerInterval = setInterval(function() {
                const elapsed = Math.floor((new Date() - timerStartTime) / 1000);
                const minutes = Math.floor(elapsed / 60);
                const seconds = elapsed % 60;
                document.getElementById('timerBtn').textContent = `⏹️ ${minutes}:${String(seconds).padStart(2, '0')}`;
                updateSessionDisplay();
            }, 1000);
        }

        // Stop timer
        function stopTimer() {
            isTimerRunning = false;
            clearInterval(timerInterval);
            document.getElementById('timerBtn').textContent = '▶️ START';
            document.getElementById('timerBtn').style.backgroundColor = '';
        }

        // Update session display
        function updateSessionDisplay() {
            if (sessionStartTime) {
                const elapsed = Math.floor((new Date() - sessionStartTime) / 1000);
                const minutes = Math.floor(elapsed / 60);
                const seconds = elapsed % 60;
                document.getElementById('sessionTime').textContent = `${minutes}:${String(seconds).padStart(2, '0')}`;
            }
            document.getElementById('sessionDistance').textContent = `${trackingData.distance.toFixed(2)} km`;
        }

        // Calculate distance between two coordinates (Haversine formula)
        function calculateDistance(lat1, lon1, lat2, lon2) {
            const R = 6371; // Erdradius in km
            const dLat = (lat2 - lat1) * Math.PI / 180;
            const dLon = (lon2 - lon1) * Math.PI / 180;
            const a = Math.sin(dLat/2) * Math.sin(dLat/2) +
                      Math.cos(lat1 * Math.PI / 180) * Math.cos(lat2 * Math.PI / 180) *
                      Math.sin(dLon/2) * Math.sin(dLon/2);
            const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a));
            return R * c;
        }

        // Update location status
        function updateLocationStatus() {
            const locationCount = trackingData.locations.length;
            const distance = trackingData.distance.toFixed(2);
            document.getElementById('locationStatus').textContent = `🔴 Punkte: ${locationCount} • Strecke: ${distance} km`;
        }

        // Set default times
        function setDefaultTimes() {
            const now = new Date();
            document.getElementById('startTime').value = formatDateTimeLocal(now);
        }

        // Format date for datetime-local input
        function formatDateTimeLocal(date) {
            const year = date.getFullYear();
            const month = String(date.getMonth() + 1).padStart(2, '0');
            const day = String(date.getDate()).padStart(2, '0');
            const hours = String(date.getHours()).padStart(2, '0');
            const minutes = String(date.getMinutes()).padStart(2, '0');
            return `${year}-${month}-${day}T${hours}:${minutes}`;
        }

        // Set current time as start
        function setStartNow() {
            const now = new Date();
            document.getElementById('startTime').value = formatDateTimeLocal(now);
        }

        // Set current time as end
        function setEndNow() {
            const now = new Date();
            document.getElementById('endTime').value = formatDateTimeLocal(now);
        }

        // Add new walk
        function addWalk() {
            const startTime = document.getElementById('startTime').value;
            const weather = document.getElementById('weather').value;
            const notes = document.getElementById('notes').value;

            if (!startTime) {
                alert('Bitte Startzeit angeben');
                return;
            }

            const start = new Date(startTime);
            const end = new Date();

            const durationMinutes = Math.round((end - start) / 60000);

            const transportType = document.getElementById('transportType').value;
            const childWeight = document.getElementById('childWeight').value;

            if (!transportType) {
                alert('Bitte Transportmittel auswählen');
                return;
            }

            const walk = {
                id: Date.now(),
                startTime: start,
                endTime: end,
                durationMinutes: durationMinutes,
                transportType: transportType,
                childWeight: childWeight,
                weather: weather,
                notes: notes,
                date: new Date(),
                route: {
                    distance: trackingData.distance,
                    locations: trackingData.locations,
                    pointCount: trackingData.locations.length
                },
                health: healthData.heartRate ? healthData : null,
                spotify: spotifyData.isConnected ? spotifyData : null
            };

            walks.push(walk);
            displayWalks();
            updateStats();
            resetForm();
            alert(`✓ Spaziergang von ${durationMinutes} Minuten gespeichert!`);
        }

        // Reset form
        function resetForm() {
            document.getElementById('startTime').value = '';
            document.getElementById('transportType').value = '';
            document.getElementById('childWeight').value = '';
            document.getElementById('weather').value = '';
            document.getElementById('notes').value = '';
            setDefaultTimes();
            
            // Stop timer if running
            if (isTimerRunning) {
                stopTimer();
            }
            
            // Reset session
            sessionStartTime = null;
            trackingData = {
                locations: [],
                distance: 0,
                startTime: null
            };
            updateSessionDisplay();
        }

        // Display walks
        function displayWalks() {
            const walksList = document.getElementById('walksList');
            
            if (walks.length === 0) {
                walksList.innerHTML = `
                    <div class="empty-state-icon">👶</div>
                    <p>Noch keine Spaziergänge aufgezeichnet</p>
                `;
                document.getElementById('statsSection').style.display = 'none';
                return;
            }

            document.getElementById('statsSection').style.display = 'block';

            const html = walks.reverse().map(walk => `
                <div class="walk-entry">
                    <div class="walk-info">
                        <div class="walk-date">${walk.date.toLocaleDateString('de-DE', { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' })}</div>
                        <div class="walk-time">${walk.startTime.toLocaleTimeString('de-DE', { hour: '2-digit', minute: '2-digit' })} - ${walk.endTime.toLocaleTimeString('de-DE', { hour: '2-digit', minute: '2-digit' })}</div>
                        <div style="font-size: 13px; color: var(--color-primary); font-weight: 600; margin: 4px 0;">⏱️ ${walk.durationMinutes} Minuten</div>
                        <div style="font-size: 12px; color: var(--color-text-secondary);">🚗 ${walk.transportType}${walk.childWeight ? ` • Gewicht: ${walk.childWeight} kg` : ''}</div>
                        ${walk.route && walk.route.distance > 0 ? `<div style="font-size: 12px; color: var(--color-primary); font-weight: 600;">📍 Strecke: ${walk.route.distance.toFixed(2)} km (${walk.route.pointCount} Punkte)</div>` : ''}
                        ${walk.weather ? `<div style="font-size: 12px; color: var(--color-text-secondary);">Wetter: ${walk.weather}</div>` : ''}
                        ${walk.spotify ? `<div style="font-size: 12px; color: #1DB954; font-weight: 600;">🎵 ${walk.spotify.currentTrack} • ${walk.spotify.currentArtist}</div>` : ''}
                        ${walk.notes ? `<div class="walk-notes">📝 ${walk.notes}</div>` : ''}
                    </div>
                    <div class="walk-actions">
                        <button class="btn-small btn-small-danger" onclick="deleteWalk(${walk.id})">✕</button>
                    </div>
                </div>
            `).join('');

            walksList.innerHTML = html;
            walks.reverse();
        }

        // Update statistics
        function updateStats() {
            const totalWalks = walks.length;
            const totalMinutes = walks.reduce((sum, walk) => sum + walk.durationMinutes, 0);
            const avgMinutes = totalWalks > 0 ? Math.round(totalMinutes / totalWalks) : 0;
            const longestWalk = totalWalks > 0 ? Math.max(...walks.map(w => w.durationMinutes)) : 0;

            document.getElementById('totalWalks').textContent = totalWalks;
            document.getElementById('totalMinutes').textContent = totalMinutes;
            document.getElementById('avgMinutes').textContent = avgMinutes;
            document.getElementById('longestWalk').textContent = longestWalk;
        }

        // Delete walk
        function deleteWalk(id) {
            if (confirm('Spaziergang wirklich löschen?')) {
                walks = walks.filter(walk => walk.id !== id);
                displayWalks();
                updateStats();
            }
        }

        // Clear all data
        function clearAllData() {
            if (confirm('Alle Daten wirklich löschen? Dies kann nicht rückgängig gemacht werden.')) {
                walks = [];
                displayWalks();
                updateStats();
                alert('Alle Daten gelöscht');
            }
        }

        // Initialize on load
        window.addEventListener('DOMContentLoaded', init);
    </script>
</body>
</html>

