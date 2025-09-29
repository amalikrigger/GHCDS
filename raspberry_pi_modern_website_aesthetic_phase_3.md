# Phase 3 — Upgrade Your Dashboard (Using Thonny)

## Overview
You will replace the simple HTML page you built in Phase 1 with a modern, styled dashboard. The backend stays the same; you only change the look. The new dashboard will fetch data from your Flask `/api/stats` endpoint and update live.

## Prerequisites
- Phase 1 app is working (Flask runs, `/api/stats` returns `{ cpu, mem_percent, disk_percent, temp_c }`).
- Virtual environment is set up at `~/pihealth/` with Flask and psutil installed.
- You know how to run `system_monitor.py`.

## Steps

### 1. Open in Thonny
- On the Raspberry Pi, launch **Thonny** (Menu → Programming → Thonny)
- In Thonny, open `~/pi-health-web/system_monitor.py`.

### 2. Find the HTML Page String
Inside your code, locate the triple-quoted string assigned to `PAGE` that holds the current HTML page.

### 3. Replace HTML Content
Remove everything between the triple quotes of that HTML string.

👉 **Paste the new HTML code here in Thonny when provided.**

```html 
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Raspberry Pi Health Monitor</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
    
    body {
      font-family: 'Inter', sans-serif;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      min-height: 100vh;
    }
    
    .metric-card {
      backdrop-filter: blur(10px);
      background: rgba(255, 255, 255, 0.1);
      border: 1px solid rgba(255, 255, 255, 0.2);
      transition: all 0.3s ease;
    }
    
    .metric-card:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
    }
    
    .progress-circle {
      transform: rotate(-90deg);
      transition: stroke-dasharray 0.5s ease;
    }
    
    .status-ok { color: #10b981; }
    .status-warning { color: #f59e0b; }
    .status-critical { color: #ef4444; }
    
    .pulse-dot {
      animation: pulse 2s infinite;
    }
    
    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.5; }
    }
    
    .refresh-indicator {
      animation: spin 2s linear infinite;
    }
    
    @keyframes spin {
      from { transform: rotate(0deg); }
      to { transform: rotate(360deg); }
    }
  </style>
</head>
<body class="p-4 md:p-8">
  <div class="max-w-6xl mx-auto">
    <!-- Header -->
    <div class="text-center mb-8">
      <div class="flex items-center justify-center mb-4">
        <svg class="w-12 h-12 mr-3 text-white" viewBox="0 0 24 24" fill="currentColor">
          <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.94-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93zm6.9-2.54c-.26-.81-1-1.39-1.9-1.39h-1v-3c0-.55-.45-1-1-1H8v-2h2c.55 0 1-.45 1-1V7h2c1.1 0 2-.9 2-2v-.41c2.93 1.19 5 4.06 5 7.41 0 2.08-.8 3.97-2.1 5.39z"/>
        </svg>
        <h1 class="text-4xl md:text-5xl font-bold text-white">Raspberry Pi Health Monitor</h1>
      </div>
      <div class="flex items-center justify-center text-white/80">
        <div class="pulse-dot w-2 h-2 bg-green-400 rounded-full mr-2"></div>
        <span class="text-sm">Auto-refreshes every 2 seconds</span>
        <svg class="refresh-indicator w-4 h-4 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"/>
        </svg>
      </div>
    </div>

    <!-- Main Metrics Grid -->
    <div class="grid grid-cols-1 md-grid-cols-2 lg:grid-cols-4 gap-6 mb-8 md:grid-cols-2">
      <!-- CPU -->
      <div class="metric-card rounded-2xl p-6 text-center">
        <div class="flex items-center justify-center mb-4">
          <svg class="w-8 h-8 text-blue-400 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 3v2m6-2v2M9 19v2m6-2v2M5 9H3m2 6H3m18-6h-2m2 6h-2M7 19h10a2 2 0 002-2V7a2 2 0 00-2-2H7a2 2 0 00-2 2v10a2 2 0 002 2zM9 9h6v6H9V9z"/>
          </svg>
          <h3 class="text-lg font-semibold text-white">CPU Usage</h3>
        </div>
        <div class="relative w-32 h-32 mx-auto mb-4">
          <svg class="w-32 h-32" viewBox="0 0 120 120">
            <circle cx="60" cy="60" r="50" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="8"/>
            <circle id="cpu-progress" cx="60" cy="60" r="50" fill="none" stroke="#10b981" stroke-width="8" class="progress-circle" stroke-dasharray="0 314" stroke-linecap="round"/>
          </svg>
          <div class="absolute inset-0 flex items-center justify-center">
            <span id="cpu-value" class="text-2xl font-bold text-white">--%</span>
          </div>
        </div>
        <div id="cpu-status" class="font-medium text-white/80">--</div>
      </div>

      <!-- Memory -->
      <div class="metric-card rounded-2xl p-6 text-center">
        <div class="flex items-center justify-center mb-4">
          <svg class="w-8 h-8 text-purple-400 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"/>
          </svg>
          <h3 class="text-lg font-semibold text-white">Memory Used</h3>
        </div>
        <div class="relative w-32 h-32 mx-auto mb-4">
          <svg class="w-32 h-32" viewBox="0 0 120 120">
            <circle cx="60" cy="60" r="50" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="8"/>
            <circle id="memory-progress" cx="60" cy="60" r="50" fill="none" stroke="#8b5cf6" stroke-width="8" class="progress-circle" stroke-dasharray="0 314" stroke-linecap="round"/>
          </svg>
          <div class="absolute inset-0 flex items-center justify-center">
            <span id="memory-value" class="text-2xl font-bold text-white">--%</span>
          </div>
        </div>
        <div id="memory-status" class="font-medium text-white/80">--</div>
      </div>

      <!-- Disk -->
      <div class="metric-card rounded-2xl p-6 text-center">
        <div class="flex items-center justify-center mb-4">
          <svg class="w-8 h-8 text-cyan-400 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 7v10c0 2.21 3.582 4 8 4s8-1.79 8-4V7M4 7c0 2.21 3.582 4 8 4s8-1.79 8-4M4 7c0-2.21 3.582-4 8-4s8 1.79 8 4m0 5c0 2.21-3.582 4-8 4s-8-1.79-8-4"/>
          </svg>
          <h3 class="text-lg font-semibold text-white">Disk Used (/)</h3>
        </div>
        <div class="relative w-32 h-32 mx-auto mb-4">
          <svg class="w-32 h-32" viewBox="0 0 120 120">
            <circle cx="60" cy="60" r="50" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="8"/>
            <circle id="disk-progress" cx="60" cy="60" r="50" fill="none" stroke="#06b6d4" stroke-width="8" class="progress-circle" stroke-dasharray="0 314" stroke-linecap="round"/>
          </svg>
          <div class="absolute inset-0 flex items-center justify-center">
            <span id="disk-value" class="text-2xl font-bold text-white">--%</span>
          </div>
        </div>
        <div id="disk-status" class="font-medium text-white/80">--</div>
      </div>

      <!-- Temperature -->
      <div class="metric-card rounded-2xl p-6 text-center">
        <div class="flex items-center justify-center mb-4">
          <svg class="w-8 h-8 text-orange-400 mr-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a6 6 0 0012 0v-3"/>
          </svg>
          <h3 class="text-lg font-semibold text-white">Temperature</h3>
        </div>
        <div class="mb-4">
          <div id="temp-value" class="text-4xl font-bold text-white mb-2">--°C</div>
          <div class="w-full bg-white/20 rounded-full h-3">
            <div id="temp-bar" class="h-3 rounded-full transition-all duration-500" style="width:0%"></div>
          </div>
        </div>
        <div id="temp-status" class="font-medium text-white/80">--</div>
      </div>
    </div>

    <!-- System Status -->
    <div class="metric-card rounded-2xl p-6 mb-6">
      <div class="flex items-center justify-between">
        <div class="flex items-center">
          <div class="w-3 h-3 bg-green-400 rounded-full mr-3 pulse-dot"></div>
          <h3 class="text-xl font-semibold text-white">System Status</h3>
        </div>
        <div class="text-white/60 text-sm">
          Last updated: <span id="last-updated">--</span>
        </div>
      </div>
    </div>

    <!-- Footer -->
    <div class="text-center text-white/60 text-sm">
      Raspberry Pi Health Monitor Dashboard • Real-time system monitoring
    </div>
  </div>

  <script>
    // Helper for circular progress
    function updateCircularProgress(elementId, percentage, color) {
      const circle = document.getElementById(elementId);
      const circumference = 2 * Math.PI * 50;
      const strokeDasharray = (percentage / 100) * circumference;
      circle.style.strokeDasharray = strokeDasharray + ' ' + circumference;
      circle.style.stroke = color;
    }

    // Color/status helpers (same thresholds you used)
    function getCpuColor(cpu){ if(cpu<30)return'#10b981'; if(cpu<70)return'#f59e0b'; return'#ef4444'; }
    function getCpuStatus(cpu){ if(cpu<30)return'Normal'; if(cpu<70)return'Moderate'; return'High'; }
    function getCpuStatusClass(cpu){ if(cpu<30)return'status-ok'; if(cpu<70)return'status-warning'; return'status-critical'; }

    function getMemoryColor(m){ if(m<60)return'#8b5cf6'; if(m<80)return'#f59e0b'; return'#ef4444'; }
    function getMemoryStatus(m){ if(m<60)return'Normal'; if(m<80)return'Moderate'; return'High'; }
    function getMemoryStatusClass(m){ if(m<60)return'status-ok'; if(m<80)return'status-warning'; return'status-critical'; }

    function getDiskColor(d){ if(d<70)return'#06b6d4'; if(d<85)return'#f59e0b'; return'#ef4444'; }
    function getDiskStatus(d){ if(d<70)return'Healthy'; if(d<85)return'Warning'; return'Critical'; }
    function getDiskStatusClass(d){ if(d<70)return'status-ok'; if(d<85)return'status-warning'; return'status-critical'; }

    function getTempColor(t){ if(t<40)return'#06b6d4'; if(t<50)return'#f59e0b'; return'#ef4444'; }
    function getTempStatus(t){ if(t<40)return'Cool'; if(t<50)return'Warm'; return'Hot'; }
    function getTempStatusClass(t){ if(t<40)return'status-ok'; if(t<50)return'status-warning'; return'status-critical'; }

    // Fetch stats from Flask
    async function updateMetrics(){
      try{
        const res=await fetch('/api/stats',{cache:'no-store'});
        const s=await res.json();
        const cpu=Math.round(s.cpu??0);
        const memory=Math.round(s.mem_percent??0);
        const disk=Math.round(s.disk_percent??0);
        const temp=(s.temp_c===null||s.temp_c===undefined)?null:Number(s.temp_c);

        // CPU
        updateCircularProgress('cpu-progress',cpu,getCpuColor(cpu));
        document.getElementById('cpu-value').textContent=cpu+'%';
        document.getElementById('cpu-status').textContent=getCpuStatus(cpu);
        document.getElementById('cpu-status').className=getCpuStatusClass(cpu)+' font-medium';

        // Memory
        updateCircularProgress('memory-progress',memory,getMemoryColor(memory));
        document.getElementById('memory-value').textContent=memory+'%';
        document.getElementById('memory-status').textContent=getMemoryStatus(memory);
        document.getElementById('memory-status').className=getMemoryStatusClass(memory)+' font-medium';

        // Disk
        updateCircularProgress('disk-progress',disk,getDiskColor(disk));
        document.getElementById('disk-value').textContent=disk+'%';
        document.getElementById('disk-status').textContent=getDiskStatus(disk);
        document.getElementById('disk-status').className=getDiskStatusClass(disk)+' font-medium';

        // Temp
        if(temp===null||Number.isNaN(temp)){
          document.getElementById('temp-value').textContent='--°C';
          document.getElementById('temp-bar').style.width='0%';
          document.getElementById('temp-bar').style.backgroundColor='#94a3b8';
          document.getElementById('temp-status').textContent='Unavailable';
          document.getElementById('temp-status').className='font-medium';
        }else{
          document.getElementById('temp-value').textContent=temp.toFixed(1)+'°C';
          const pct=Math.max(0,Math.min(100,(temp-30)*2));
          document.getElementById('temp-bar').style.width=pct+'%';
          document.getElementById('temp-bar').style.backgroundColor=getTempColor(temp);
          document.getElementById('temp-status').textContent=getTempStatus(temp);
          document.getElementById('temp-status').className=getTempStatusClass(temp)+' font-medium';
        }

        // Timestamp
        document.getElementById('last-updated').textContent=new Date().toLocaleTimeString();
      }catch(e){console.error(e);}
    }

    updateMetrics();
    setInterval(updateMetrics,2000);
  </script>
</body>
</html>
```

### 4. Save and Run
- Save the modified file (File → Save).
- Ensure Thonny is configured to use the project interpreter (`/home/pi/pihealth/bin/python3`) under **Tools → Options → Interpreter**.
- Click **Run**. The Shell should show something like `Running on http://0.0.0.0:5000`.

### 5. View & Test
- In Chromium on the Pi: open `http://localhost:5000`
- From another device: `http://raspberrypi.local:5000` or `http://<Pi-IP>:5000`
- Verify that CPU, memory, disk, and temperature show live values and refresh every ~2 seconds.
- If temperature shows `--°C` or “Unavailable”, that’s acceptable on some hardware.

### 6. Stop the Server
- In Thonny: press the **Stop** button
- If you ran from Terminal: press **Ctrl + C**

## Deliverables
1. Screenshot of the new dashboard running in a browser.
2. Screenshot of Thonny (or Terminal) showing the server running.
3. The URL you used to access the dashboard (e.g. `localhost:5000`, `raspberrypi.local:5000`, or `192.168.x.x:5000`).

## Student Checklist
- [ ] Opened `system_monitor.py` in Thonny
- [ ] Located and removed old HTML string content
- [ ] Inserted placeholder or marker for new HTML
- [ ] Saved file and ran server successfully
- [ ] Confirmed live update of all metrics
- [ ] Viewed dashboard from correct URL
- [ ] Took and submitted required screenshots
