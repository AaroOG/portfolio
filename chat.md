# Portfolio Architecture & State Document
**Project:** Personal Portfolio Website for College Admissions (Computer Science)
**Developer:** Aaron Varghese
**Target Audience:** University Admissions Committees & Technical Recruiters

---

## 1. Core Infrastructure & Deployment
*   **Domain:** `aarongvarghese.com` (Registered and managed via Cloudflare)
*   **Hosting Strategy:** GitHub Pages (Pending initial push)
*   **DNS & Security:** Cloudflare (Proxied, Full SSL/TLS enforcement)
*   **Tech Stack:** Native HTML5, Tailwind CSS (via CDN), Vanilla CSS Keyframes

## 2. Design System & UI/UX
*   **Aesthetic Theme:** "Modern Terminal Hybrid" – Blends a macOS-style command-line interface with a clean, responsive card-based grid (Bento Box style).
*   **Color Palette:** Deep Zinc (`bg-zinc-950`) canvas with sharp Blue (`blue-400`) and Sky Blue (`sky-400`) accents for syntax highlighting and hover states.
*   **Animations:** Staggered vertical fade-ins on initial load (`animate-fade-in-up`), subtle breathing glows on text, and interactive CSS hover lifts/shadows on project cards. Accordion drop-downs (`<details>`) for inline media viewing.

---

## 3. Content Architecture

### A. The Hero / Intro (Terminal Interface)
*   **Concept:** A simulated boot sequence executing `./initialize_portfolio.sh` and `cat whoami.txt` to introduce the developer.
*   **Hook:** High school senior, endurance runner, and aspiring CS major focused on optimizing systems and building software.

### B. Academic Profile
*   **Graduation Year:** Class of 2027
*   **Coursework Focus:** AP Physics 1, AP Precalculus, AP U.S. History
*   **Societies:** National Honor Society (NHS), National Spanish Honor Society (NSHS)

### C. Technical Projects Showcase (The 3 Pillars)
1.  **Library Resource Automator (Automation/Backend)**
    *   *Tech:* Python, Playwright
    *   *Summary:* Headless web scraper parsing local library databases to bypass UI friction and instantly extract open study room availability.
2.  **Minimalist Weather Utility (Frontend/Mobile)**
    *   *Tech:* Flutter, Dart, REST APIs
    *   *Summary:* Lightweight, cross-platform mobile app fetching real-time atmospheric data into a highly responsive, zero-telemetry UI.
3.  **Bare-Metal Systems Lab (Infrastructure/Hardware)**
    *   *Tech:* Proxmox VE, Docker, Linux, JVM Tuning
    *   *Summary:* Local homelab built from repurposed deprecated consumer computers. Operates a redundant NAS and orchestrates isolated Linux containers to host dedicated Minecraft server clusters with customized memory allocation.

### D. Athletic Discipline & Grit
*   **Concept:** Framing varsity endurance sports as a demonstration of elite time management and the obsessive persistence required for complex software engineering.
*   **Key Metrics:** 
    *   1,000+ competitive training miles logged.
    *   Participant in the Texas Distance Festival and Nike Cross Regionals (NXR).
    *   Utilizes Garmin biometric tracking systems for workload optimization.

---

## 4. Current Codebase (index.html)
*The following block contains the active, production-ready source code for the landing page.*

```html
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aaron Varghese | Software Developer Portfolio</title>
    <!-- Tailwind CSS CDN -->
    <script src="[https://cdn.tailwindcss.com](https://cdn.tailwindcss.com)"></script>
    <style>
        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes blinker { 50% { opacity: 0; } }
        .animate-fade-in-up {
            animation: fadeInUp 0.8s cubic-bezier(0.16, 1, 0.3, 1) forwards;
            opacity: 0;
        }
        .animate-blink { animation: blinker 1s step-start infinite; }
        details[open] summary ~ * { animation: fadeInUp 0.4s ease-out; }
    </style>
</head>
<body class="bg-zinc-950 text-zinc-100 font-sans selection:bg-blue-500/30 selection:text-blue-200 overflow-x-hidden">

    <!-- Navigation -->
    <nav class="max-w-6xl mx-auto px-6 py-6 flex justify-between items-center opacity-0 animate-fade-in-up" style="animation-delay: 100ms;">
        <span class="text-xl font-bold tracking-tight text-blue-400 hover:scale-105 transition-transform duration-300 cursor-pointer">aarongvarghese.com</span>
        <div class="space-x-6 text-sm font-medium text-zinc-400">
            <a href="#education" class="hover:text-blue-400 transition-colors duration-300">Education</a>
            <a href="#projects" class="hover:text-blue-400 transition-colors duration-300">Projects</a>
            <a href="#athletics" class="hover:text-blue-400 transition-colors duration-300">Athletics</a>
            <a href="[https://github.com/YOUR-GITHUB-USERNAME](https://github.com/YOUR-GITHUB-USERNAME)" target="_blank" class="text-zinc-200 hover:text-blue-400 transition-colors duration-300 inline-block hover:-translate-y-0.5 transform">GitHub ↗</a>
        </div>
    </nav>

    <!-- Terminal Hero Section -->
    <header class="max-w-6xl mx-auto px-6 py-12 md:py-16 opacity-0 animate-fade-in-up" style="animation-delay: 200ms;">
        <div class="bg-zinc-950 border border-zinc-800 rounded-xl overflow-hidden shadow-2xl">
            <div class="bg-zinc-900 border-b border-zinc-800 px-4 py-3 flex items-center gap-2">
                <div class="w-3 h-3 rounded-full bg-red-500/80"></div>
                <div class="w-3 h-3 rounded-full bg-amber-500/80"></div>
                <div class="w-3 h-3 rounded-full bg-green-500/80"></div>
                <div class="ml-4 text-xs font-mono text-zinc-500 flex-1 text-center pr-10">aaron@varghese: ~</div>
            </div>
            <div class="p-6 md:p-10 font-mono text-sm md:text-base">
                <div class="mb-4 text-zinc-400">
                    <span class="text-blue-400">aaron@varghese</span>:<span class="text-sky-400">~</span>$ cat whoami.txt
                </div>
                <div class="pl-4 border-l-2 border-zinc-800 mb-6 mt-4">
                    <h1 class="text-4xl md:text-6xl font-extrabold tracking-tight text-zinc-100 mb-4 font-sans">Aaron Varghese.</h1>
                    <h2 class="text-2xl md:text-3xl font-bold text-zinc-400 mb-4 font-sans">Building software & pushing limits.</h2>
                    <p class="max-w-2xl text-zinc-400 leading-relaxed font-sans text-base">
                        I'm a high school senior, competitive endurance runner, and aspiring computer science major. Whether I'm logging miles on the trail or optimization testing codebase frameworks, I love pushing systems—and myself—to their absolute limits.
                    </p>
                </div>
                <div class="text-zinc-400 flex items-center">
                    <span class="text-blue-400">aaron@varghese</span>:<span class="text-sky-400">~</span>$ <span class="ml-2 w-2.5 h-5 bg-zinc-400 animate-blink inline-block"></span>
                </div>
            </div>
        </div>
    </header>

    <!-- Academic Education Section -->
    <section id="education" class="max-w-6xl mx-auto px-6 py-12 border-t border-zinc-800 opacity-0 animate-fade-in-up" style="animation-delay: 300ms;">
        <h2 class="text-2xl font-bold text-zinc-200 mb-8 flex items-center font-mono">
            <span class="text-blue-400 text-base mr-3">~/</span> Academic Profile
        </h2>
        <div class="grid md:grid-cols-3 gap-6">
            <div class="bg-zinc-900/40 border border-zinc-800 rounded-xl p-6 md:col-span-2">
                <h3 class="text-xl font-bold text-zinc-100 mb-1">High School Senior</h3>
                <p class="text-blue-400 font-mono text-sm mb-4">Class of 2027 &bull; Computer Science Track</p>
                <p class="text-zinc-400 text-sm leading-relaxed mb-4">Maintaining a rigorous academic course load specializing in advanced mathematics and scientific disciplines to build the foundational analytical skills required for higher-tier computer science paths.</p>
                <div class="flex flex-wrap gap-2 text-xs font-mono text-zinc-300">
                    <span class="bg-zinc-800/60 px-2.5 py-1 rounded">AP Physics 1</span>
                    <span class="bg-zinc-800/60 px-2.5 py-1 rounded">AP Precalculus</span>
                    <span class="bg-zinc-800/60 px-2.5 py-1 rounded">AP U.S. History</span>
                </div>
            </div>
            <div class="bg-zinc-900/40 border border-zinc-800 rounded-xl p-6 flex flex-col justify-center gap-4">
                <div class="flex items-start gap-3">
                    <span class="text-xl mt-0.5">🎖️</span>
                    <div>
                        <h4 class="font-bold text-zinc-200 text-sm">National Honor Society</h4>
                        <p class="text-xs text-zinc-500 font-mono mt-0.5">Selected Member</p>
                    </div>
                </div>
                <div class="flex items-start gap-3 border-t border-zinc-800/60 pt-4">
                    <span class="text-xl mt-0.5">🇪🇸</span>
                    <div>
                        <h4 class="font-bold text-zinc-200 text-sm">National Spanish Honor Society</h4>
                        <p class="text-xs text-zinc-500 font-mono mt-0.5">Active Member</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Technical Projects Showcase -->
    <section id="projects" class="max-w-6xl mx-auto px-6 py-16 border-t border-zinc-800 opacity-0 animate-fade-in-up" style="animation-delay: 400ms;">
        <h2 class="text-2xl font-bold text-zinc-200 mb-10 flex items-center group font-mono">
            <span class="text-blue-400 text-base mr-3 group-hover:translate-x-1 transition-transform duration-300">~/</span> Technical Projects & Systems
        </h2>
        <div class="grid md:grid-cols-3 gap-6 items-start">
            
            <!-- App 1: Library -->
            <div class="bg-zinc-900/50 border border-zinc-800 rounded-xl p-6 transition-all duration-500 hover:border-blue-500/40 hover:bg-zinc-800/80 hover:shadow-[0_10px_30px_-15px_rgba(59,130,246,0.15)] flex flex-col justify-between h-full group">
                <div>
                    <div class="flex justify-between items-start mb-4">
                        <span class="text-2xl group-hover:scale-125 transition-transform duration-300">🤖</span>
                        <a href="#" class="text-zinc-400 hover:text-blue-400 transition-colors duration-300 text-sm font-mono flex items-center gap-1">[Repository] ↗</a>
                    </div>
                    <h3 class="text-xl font-bold text-zinc-100 mb-2 group-hover:text-blue-400 transition-colors duration-300">Library Resource Automator</h3>
                    <p class="text-zinc-400 text-sm leading-relaxed mb-4">Engineered an automation utility that headlessly parses a local library database to isolate and display open study room allocations, eliminating manual scheduling friction.</p>
                    <details class="mb-6 group/media">
                        <summary class="text-xs font-mono text-zinc-500 hover:text-blue-400 cursor-pointer list-none flex items-center gap-1 select-none outline-none"><span>▶</span> View Demo Video</summary>
                        <div class="mt-3 overflow-hidden rounded-lg bg-zinc-950 border border-zinc-800"><video controls class="w-full h-auto max-h-48 object-cover" preload="none"><source src="assets/library-demo.mp4" type="video/mp4"></video></div>
                    </details>
                </div>
                <div class="flex flex-wrap gap-2 text-xs font-mono text-blue-400">
                    <span class="bg-zinc-950 px-2.5 py-1 rounded border border-zinc-800">Python</span>
                    <span class="bg-zinc-950 px-2.5 py-1 rounded border border-zinc-800">Playwright</span>
                </div>
            </div>

            <!-- App 2: Weather -->
            <div class="bg-zinc-900/50 border border-zinc-800 rounded-xl p-6 transition-all duration-500 hover:border-blue-500/40 hover:bg-zinc-800/80 hover:shadow-[0_10px_30px_-15px_rgba(59,130,246,0.15)] flex flex-col justify-between h-full group">
                <div>
                    <div class="flex justify-between items-start mb-4">
                        <span class="text-2xl group-hover:scale-125 transition-transform duration-300">📱</span>
                        <a href="#" class="text-zinc-400 hover:text-blue-400 transition-colors duration-300 text-sm font-mono flex items-center gap-1">[Repository] ↗</a>
                    </div>
                    <h3 class="text-xl font-bold text-zinc-100 mb-2 group-hover:text-blue-400 transition-colors duration-300">Minimalist Weather Utility</h3>
                    <p class="text-zinc-400 text-sm leading-relaxed mb-4">Designed and compiled a lightweight cross-platform mobile utility that interfaces with public REST APIs to fetch real-time atmospheric data into an adaptive, telemetry-free UI.</p>
                    <details class="mb-6 group/media">
                        <summary class="text-xs font-mono text-zinc-500 hover:text-blue-400 cursor-pointer list-none flex items-center gap-1 select-none outline-none"><span>▶</span> View App Screenshots</summary>
                        <div class="mt-3 overflow-hidden rounded-lg bg-zinc-950 p-2 grid grid-cols-2 gap-2"><img src="assets/weather-ui-1.jpg" class="rounded border border-zinc-800"><img src="assets/weather-ui-2.jpg" class="rounded border border-zinc-800"></div>
                    </details>
                </div>
                <div class="flex flex-wrap gap-2 text-xs font-mono text-blue-400">
                    <span class="bg-zinc-950 px-2.5 py-1 rounded border border-zinc-800">Flutter</span>
                    <span class="bg-zinc-950 px-2.5 py-1 rounded border border-zinc-800">Dart</span>
                </div>
            </div>

            <!-- App 3: Homelab -->
            <div class="bg-zinc-900/50 border border-zinc-800 rounded-xl p-6 transition-all duration-500 hover:border-blue-500/40 hover:bg-zinc-800/80 hover:shadow-[0_10px_30px_-15px_rgba(59,130,246,0.15)] flex flex-col justify-between h-full group">
                <div>
                    <div class="flex justify-between items-start mb-4">
                        <span class="text-2xl group-hover:scale-125 transition-transform duration-300">🖥️</span>
                        <span class="text-zinc-500 text-sm font-mono">[Infrastructure]</span>
                    </div>
                    <h3 class="text-xl font-bold text-zinc-100 mb-2 group-hover:text-blue-400 transition-colors duration-300">Bare-Metal Systems Lab</h3>
                    <p class="text-zinc-400 text-sm leading-relaxed mb-4">Deployed an enterprise virtualization hypervisor to optimize hardware bounds. Repurposed deprecated consumer computers into redundant NAS nodes and orchestrated high-concurrency dedicated Minecraft server clusters.</p>
                    <details class="mb-6 group/media">
                        <summary class="text-xs font-mono text-zinc-500 hover:text-blue-400 cursor-pointer list-none flex items-center gap-1 select-none outline-none"><span>▶</span> View System Topology</summary>
                        <div class="mt-3 overflow-hidden rounded-lg bg-zinc-950 border border-zinc-800 p-1"><img src="Screenshot 2026-06-27 at 12.41.42 AM.jpg" alt="Lab Dashboard View" class="w-full h-auto rounded"></div>
                    </details>
                </div>
                <div class="flex flex-wrap gap-2 text-xs font-mono text-blue-400">
                    <span class="bg-zinc-950 px-2.5 py-1 rounded border border-zinc-800">Proxmox VE</span>
                    <span class="bg-zinc-950 px-2.5 py-1 rounded border border-zinc-800">JVM Tuning</span>
                    <span class="bg-zinc-950 px-2.5 py-1 rounded border border-zinc-800">NAS</span>
                </div>
            </div>
        </div>
    </section>

    <!-- Structured Athletics Section -->
    <section id="athletics" class="max-w-6xl mx-auto px-6 py-16 border-t border-zinc-800 mb-20 opacity-0 animate-fade-in-up" style="animation-delay: 500ms;">
        <h2 class="text-2xl font-bold text-zinc-200 mb-8 flex items-center font-mono">
            <span class="text-blue-400 text-base mr-3">~/</span> Athletic Discipline & Grit
        </h2>
        <div class="grid md:grid-cols-3 gap-6 items-stretch">
            <div class="bg-zinc-900/30 border border-zinc-800 rounded-xl p-6 md:p-8 hover:border-zinc-700 transition-all duration-300 md:col-span-2 flex flex-col justify-center">
                <p class="text-zinc-400 leading-relaxed mb-4">Beyond software engineering, I dedicate a massive portion of my lifecycle to competitive high school **Cross Country and Track**. Balancing demanding morning and evening practice workloads with deep programming pipelines requires extreme mental endurance.</p>
                <p class="text-zinc-400 leading-relaxed">Surviving grueling multi-mile training blocks and dawn workouts has forged structured time-management skills and a stubborn resilience. When facing complex system latency spikes or deep debugging errors, the discipline acquired on the track translates directly into absolute persistence at the computer console.</p>
            </div>
            <div class="bg-gradient-to-br from-zinc-900 via-zinc-900 to-zinc-800/50 border border-zinc-800 rounded-xl p-6 flex flex-col justify-between">
                <div class="border-b border-zinc-800 pb-4">
                    <span class="text-xs font-mono text-blue-400 uppercase tracking-wider">Log Volume</span>
                    <div class="text-3xl font-extrabold text-zinc-100 mt-1">1,000+</div>
                    <span class="text-xs text-zinc-500 font-mono">Competitive Training Miles</span>
                </div>
                <div class="border-b border-zinc-800 py-4">
                    <span class="text-xs font-mono text-blue-400 uppercase tracking-wider">Key Circuits</span>
                    <div class="text-sm font-bold text-zinc-200 mt-1">Texas Distance Festival</div>
                    <div class="text-xs text-zinc-500 font-mono mt-0.5">Nike Cross Regionals (NXR)</div>
                </div>
                <div class="pt-4">
                    <span class="text-xs font-mono text-blue-400 uppercase tracking-wider">Biometric Telemetry</span>
                    <div class="text-xs text-zinc-400 font-mono mt-1">Garmin Wearable Tracking Systems</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="max-w-6xl mx-auto px-6 py-8 border-t border-zinc-800/50 text-center text-xs font-mono text-zinc-500">
        EOF &bull; Built by Aaron Varghese &bull; Powered by Cloudflare DNS
    </footer>

</body>
</html>