```html
<!DOCTYPE html>
<html lang="en" class="dark scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Home Leave Command Center - My Personal Home Leave OS 2026</title>

    <!-- App Manifest for PWA functionality -->
    <link rel="manifest" href="data:application/manifest+json;base64,ewogICJuYW1lIjogIkhvbWUgTGVhdmUgQ29tbWFuZCBDZW50ZXIiLAogICJzaG9ydF9uYW1lIjogIkhvbWVMZWF2ZU9TIiwKICAic3RhcnRfdXJsIjogIi4iLAogICJkaXNwbGF5IjogInN0YW5kYWxvbmUiLAogICJiYWNrZ3JvdW5kX2NvbG9yIjogIiMwOTA5MGIiLAogICJ0aGVtZV9jb2xvcIjogIiNkNGFmMzciLAogICJpY29ucyI6IFsKICAgIHsKICAgICAgInNyYyI6ICJodHRwczovL3BsYWNlaG9sZC5jby8xOTJ4MTkyLzA5MDkwYi9kNGFmMzc/dGV4dD1IT00FIiwKICAgICAgInNpemVzIjogIjE5MngxOTIiLAogICAgICAidHlwZSI6ICJpbWFnZS9wbmciCiAgICB9CiAgXQp9">
    <meta name="theme-color" content="#09090b">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">

    <!-- Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&family=JetBrains+Mono:wght@400;600&display=swap" rel="stylesheet">

    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        gold: {
                            50: '#fffdf0',
                            100: '#fefab8',
                            200: '#fdf480',
                            300: '#fbe948',
                            400: '#f9da1b',
                            500: '#d4af37',
                            600: '#b88e1a',
                            700: '#8c680d',
                            800: '#674a0f',
                            900: '#48330d',
                            950: '#271904',
                        },
                        dark: {
                            bg: '#070709',
                            card: '#111115',
                            border: '#22222a',
                            elevated: '#181820',
                            hover: '#22222e'
                        }
                    },
                    fontFamily: {
                        sans: ['"Plus Jakarta Sans"', 'sans-serif'],
                        mono: ['"JetBrains Mono"', 'monospace']
                    }
                }
            }
        }
    </script>

    <!-- React & ReactDOM UMD -->
    <script src="https://unpkg.com/react@18/umd/react.production.min.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js" crossorigin></script>
    
    <!-- Babel for React JSX Compilation -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

    <!-- Canvas Confetti -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <style>
        /* Custom Styling & Scrollbar */
        body {
            background-color: #070709;
            color: #f3f4f6;
            font-family: 'Plus Jakarta Sans', sans-serif;
            overflow-x: hidden;
            -webkit-tap-highlight-color: transparent;
        }

        /* Gold Gradient Effects */
        .gold-gradient-text {
            background: linear-gradient(135deg, #fff2a1 0%, #d4af37 50%, #aa7c11 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .gold-gradient-bg {
            background: linear-gradient(135deg, #e5c158 0%, #d4af37 50%, #997008 100%);
        }

        .gold-glow {
            box-shadow: 0 0 25px -5px rgba(212, 175, 55, 0.25);
        }

        .gold-glow-sm {
            box-shadow: 0 0 12px -2px rgba(212, 175, 55, 0.20);
        }

        .glass-card {
            background: rgba(17, 17, 21, 0.75);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(212, 175, 55, 0.15);
        }

        .glass-card-hover {
            transition: all 0.3s ease;
        }
        
        .glass-card-hover:hover {
            border-color: rgba(212, 175, 55, 0.4);
            transform: translateY(-2px);
        }

        /* Custom Scrollbars */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #070709;
        }
        ::-webkit-scrollbar-thumb {
            background: #27272a;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #d4af37;
        }
    </style>
</head>
<body class="bg-dark-bg text-gray-100 min-h-screen selection:bg-gold-500 selection:text-black">
    
    <div id="root"></div>

    <!-- MAIN REACT APPLICATION CODE -->
    <script type="text/babel">
        const { useState, useEffect, useMemo, useRef } = React;

        // Default Preloaded 25 Seafarer Home Leave Tasks
        const DEFAULT_TASKS = [
            // CAREER
            { id: '1', name: 'Update DG Shipping profile', category: 'Career', project: 'Career', priority: 'High', importance: 40, urgency: 40, estimatedMinutes: 45, status: 'Not Started', deadline: '2026-10-08', dependencyId: null, notes: 'VERY IMPORTANT seafarer profile update.', isProtected: false },
            { id: '2', name: 'Transfer/update DG Shipping profile to eSamudra portal', category: 'Career', project: 'Career', priority: 'High', importance: 40, urgency: 40, estimatedMinutes: 60, status: 'Not Started', deadline: '2026-10-10', dependencyId: '1', notes: 'VERY IMPORTANT - depends on DG Shipping update completion.', isProtected: false },
            { id: '3', name: 'Visit Dockendale office', category: 'Career', project: 'Career', priority: 'High', importance: 30, urgency: 30, estimatedMinutes: 180, status: 'Not Started', deadline: '2026-10-12', dependencyId: null, notes: 'De-briefing and next contract planning.', isProtected: false },
            { id: '4', name: 'Tarbook assessment', category: 'Career', project: 'Career', priority: 'High', importance: 30, urgency: 30, estimatedMinutes: 120, status: 'Not Started', deadline: '2026-10-15', dependencyId: '3', notes: 'Depends on Dockendale office visit.', isProtected: false },
            { id: '5', name: 'Update CV / seafarer profile', category: 'Career', project: 'Career', priority: 'Medium', importance: 20, urgency: 20, estimatedMinutes: 30, status: 'Not Started', deadline: '2026-10-18', dependencyId: null, notes: 'Format latest sea service experience.', isProtected: false },
            
            // COURSES
            { id: '6', name: 'PSCRB course', category: 'Courses', project: 'Courses', priority: 'High', importance: 35, urgency: 30, estimatedMinutes: 240, status: 'Not Started', deadline: '2026-10-20', dependencyId: null, notes: 'Refresher training.', isProtected: false },
            { id: '7', name: 'ECDIS course', category: 'Courses', project: 'Courses', priority: 'High', importance: 35, urgency: 25, estimatedMinutes: 180, status: 'Not Started', deadline: '2026-10-25', dependencyId: null, notes: 'Type specific / refresher course.', isProtected: false },
            { id: '8', name: 'MFA course', category: 'Courses', project: 'Courses', priority: 'Medium', importance: 25, urgency: 20, estimatedMinutes: 180, status: 'Not Started', deadline: '2026-11-01', dependencyId: null, notes: 'Medical First Aid compliance.', isProtected: false },
            { id: '9', name: 'AFF course', category: 'Courses', project: 'Courses', priority: 'Medium', importance: 25, urgency: 20, estimatedMinutes: 180, status: 'Not Started', deadline: '2026-11-05', dependencyId: null, notes: 'Advanced Fire Fighting.', isProtected: false },

            // US VISA
            { id: '10', name: 'US visa application', category: 'US Visa', project: 'US Visa', priority: 'High', importance: 40, urgency: 35, estimatedMinutes: 90, status: 'Not Started', deadline: '2026-10-09', dependencyId: null, notes: 'Fill DS-160 and make payment.', isProtected: false },
            { id: '11', name: 'US visa biometrics', category: 'US Visa', project: 'US Visa', priority: 'High', importance: 40, urgency: 35, estimatedMinutes: 120, status: 'Not Started', deadline: '2026-10-22', dependencyId: '10', notes: 'Requires US visa application completed.', isProtected: false },
            { id: '12', name: 'US visa interview', category: 'US Visa', project: 'US Visa', priority: 'High', importance: 40, urgency: 35, estimatedMinutes: 180, status: 'Not Started', deadline: '2026-10-23', dependencyId: '10', notes: 'Requires application completed.', isProtected: false },

            // RELATIONSHIP
            { id: '13', name: 'Meet girlfriend for at least 7 days', category: 'Relationship', project: 'Personal / Family', priority: 'High', importance: 40, urgency: 30, estimatedMinutes: 420, status: 'Not Started', deadline: '2026-11-10', dependencyId: null, notes: 'PROTECTED TIME. Minimum 7 days dedicated uninterrupted quality time.', isProtected: true },

            // PERSONAL DEVELOPMENT
            { id: '14', name: 'Learn to drive', category: 'Personal', project: 'Driving', priority: 'Medium', importance: 30, urgency: 20, estimatedMinutes: 120, status: 'Not Started', deadline: '2026-11-15', dependencyId: null, notes: 'Enroll in driving school.', isProtected: false },
            { id: '15', name: 'Get driving licence', category: 'Personal', project: 'Driving', priority: 'Medium', importance: 30, urgency: 20, estimatedMinutes: 180, status: 'Not Started', deadline: '2026-11-25', dependencyId: '14', notes: 'Pass driving test.', isProtected: false },
            { id: '16', name: 'Learn swimming', category: 'Personal', project: 'Personal / Family', priority: 'Low', importance: 20, urgency: 10, estimatedMinutes: 60, status: 'Not Started', deadline: '2026-11-28', dependencyId: null, notes: 'Join swimming class.', isProtected: false },

            // FAMILY & FRIENDS
            { id: '17', name: 'Spend quality family time', category: 'Family', project: 'Personal / Family', priority: 'High', importance: 40, urgency: 30, estimatedMinutes: 300, status: 'Not Started', deadline: '2026-10-15', dependencyId: null, notes: 'Quality uninterrupted home time.', isProtected: true },
            { id: '18', name: 'Go on a trip with family', category: 'Family', project: 'Personal / Family', priority: 'Medium', importance: 30, urgency: 20, estimatedMinutes: 480, status: 'Not Started', deadline: '2026-11-05', dependencyId: null, notes: 'Plan a relaxing vacation trip.', isProtected: true },
            { id: '19', name: 'Go on a trip with school friends', category: 'Family', project: 'Personal / Family', priority: 'Low', importance: 20, urgency: 15, estimatedMinutes: 360, status: 'Not Started', deadline: '2026-11-20', dependencyId: null, notes: 'Catch up reunion trip.', isProtected: false },

            // BUSINESS / LEARNING
            { id: '20', name: 'Research/look for Naavik AI / AI-in-shipping course', category: 'Business', project: 'Mariner Wealth Pro', priority: 'Medium', importance: 25, urgency: 15, estimatedMinutes: 45, status: 'Not Started', deadline: '2026-10-28', dependencyId: null, notes: 'Explore maritime AI integrations.', isProtected: false },
            { id: '21', name: 'Work on Mariner Wealth Pro app development', category: 'Business', project: 'Mariner Wealth Pro', priority: 'High', importance: 35, urgency: 25, estimatedMinutes: 180, status: 'In Progress', deadline: '2026-10-30', dependencyId: null, notes: 'Core financial logic for seafarers.', isProtected: false },
            { id: '22', name: 'Prepare Mariner Wealth Pro for launch', category: 'Business', project: 'Mariner Wealth Pro', priority: 'High', importance: 35, urgency: 25, estimatedMinutes: 120, status: 'Not Started', deadline: '2026-11-12', dependencyId: '21', notes: 'Testing, graphics, app assets.', isProtected: false },
            { id: '23', name: 'Launch Mariner Wealth Pro on Google Play Store', category: 'Business', project: 'Mariner Wealth Pro', priority: 'High', importance: 40, urgency: 30, estimatedMinutes: 90, status: 'Not Started', deadline: '2026-11-18', dependencyId: '22', notes: 'Submit for review and publish.', isProtected: false },

            // FINANCE
            { id: '24', name: 'Visit HSBC Bank to book FD', category: 'Finance', project: 'Finance', priority: 'High', importance: 35, urgency: 30, estimatedMinutes: 60, status: 'Not Started', deadline: '2026-10-11', dependencyId: null, notes: 'Book NRE/NRO fixed deposit.', isProtected: false },
            { id: '25', name: 'Make SIP investment plan for future', category: 'Finance', project: 'Finance', priority: 'High', importance: 35, urgency: 25, estimatedMinutes: 45, status: 'Not Started', deadline: '2026-10-16', dependencyId: null, notes: 'Automate monthly mutual fund investments.', isProtected: false }
        ];

        // Intelligent Suggestion Checklist items (separate from main tasks)
        const FORGETTING_SUGGESTIONS = [
            { id: 's1', text: 'Check passport validity (at least 6 months remaining)', category: 'Documents' },
            { id: 's2', text: 'Prepare US visa supporting sea-service certificates', category: 'US Visa' },
            { id: 's3', text: 'Scan all physical certificates into cloud folder', category: 'Documents' },
            { id: 's4', text: 'Back up laptop & sea photos to external SSD', category: 'Tech' },
            { id: 's5', text: 'Check CDC / Discharge book stamps and entries', category: 'Career' },
            { id: 's6', text: 'Compare course fee structures across institutes', category: 'Courses' },
            { id: 's7', text: 'Review annual health insurance & seafarer policy', category: 'Finance' },
            { id: 's8', text: 'Organize sea gear, boots & uniform care', category: 'Personal' }
        ];

        function App() {
            // Persistent State Initialization
            const [signOffDate, setSignOffDate] = useState(() => {
                return localStorage.getItem('hl_signOffDate') || '2026-10-04';
            });
            const [leaveDuration, setLeaveDuration] = useState(() => {
                return localStorage.getItem('hl_leaveDuration') || '60'; // days
            });
            const [tasks, setTasks] = useState(() => {
                const saved = localStorage.getItem('hl_tasks');
                return saved ? JSON.parse(saved) : DEFAULT_TASKS;
            });
            const [suggestions, setSuggestions] = useState(FORGETTING_SUGGESTIONS);

            // Filter & Search States
            const [searchQuery, setSearchQuery] = useState('');
            const [selectedCategory, setSelectedCategory] = useState('All');
            const [selectedStatus, setSelectedStatus] = useState('All');

            // Interactive Modals / Drawers
            const [isAddModalOpen, setIsAddModalOpen] = useState(false);
            const [editingTask, setEditingTask] = useState(null);
            
            // "I Have X Hours" calculator state
            const [availableHours, setAvailableHours] = useState(2);
            
            // Pomodoro Timer State
            const [timerActive, setTimerActive] = useState(false);
            const [timerSeconds, setTimerSeconds] = useState(25 * 60);
            const [timerTask, setTimerTask] = useState(null);
            const [timerModalOpen, setTimerModalOpen] = useState(false);

            // Finance Calculator States
            const [fdAmount, setFdAmount] = useState(500000);
            const [fdRate, setFdRate] = useState(7.2);
            const [fdTenureMonths, setFdTenureMonths] = useState(12);

            const [sipMonthly, setSipMonthly] = useState(25000);
            const [sipRate, setSipRate] = useState(12);
            const [sipYears, setSipYears] = useState(5);

            // US Visa Checklist Workflow
            const [visaWorkflow, setVisaWorkflow] = useState(() => {
                const saved = localStorage.getItem('hl_visa_workflow');
                return saved ? JSON.parse(saved) : [
                    { id: 'v1', text: 'DS-160 Form Application', done: false },
                    { id: 'v2', text: 'Document Prep (Seaman Book, Contract)', done: false },
                    { id: 'v3', text: 'Visa Fee Payment', done: false },
                    { id: 'v4', text: 'Biometrics Scheduled', done: false },
                    { id: 'v5', text: 'Biometrics Completed', done: false },
                    { id: 'v6', text: 'Interview Scheduled', done: false },
                    { id: 'v7', text: 'Interview Attended', done: false },
                    { id: 'v8', text: 'Passport with C1/D Visa Received', done: false }
                ];
            });

            // Save to LocalStorage on changes
            useEffect(() => {
                localStorage.setItem('hl_signOffDate', signOffDate);
            }, [signOffDate]);

            useEffect(() => {
                localStorage.setItem('hl_leaveDuration', leaveDuration);
            }, [leaveDuration]);

            useEffect(() => {
                localStorage.setItem('hl_tasks', JSON.stringify(tasks));
            }, [tasks]);

            useEffect(() => {
                localStorage.setItem('hl_visa_workflow', JSON.stringify(visaWorkflow));
            }, [visaWorkflow]);

            useEffect(() => {
                let interval = null;
                if (timerActive && timerSeconds > 0) {
                    interval = setInterval(() => {
                        setTimerSeconds(prev => prev - 1);
                    }, 1000);
                } else if (timerSeconds === 0 && timerActive) {
                    setTimerActive(false);
                    if (window.confetti) window.confetti({ particleCount: 100, spread: 70, origin: { y: 0.6 } });
                }
                return () => clearInterval(interval);
            }, [timerActive, timerSeconds]);

            // Date & Countdown Calculations
            const countdownData = useMemo(() => {
                const target = new Date(signOffDate);
                const now = new Date();
                const diffTime = target - now;
                const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));

                const leaveDays = parseInt(leaveDuration, 10) || 60;
                const returnDateObj = new Date(target);
                returnDateObj.setDate(returnDateObj.getDate() + leaveDays);

                const options = { day: 'numeric', month: 'short', year: 'numeric' };
                
                return {
                    daysUntil: diffDays > 0 ? diffDays : 0,
                    signOffFormatted: target.toLocaleDateString('en-GB', options),
                    returnFormatted: returnDateObj.toLocaleDateString('en-GB', options),
                    leaveDays: leaveDays
                };
            }, [signOffDate, leaveDuration]);

            // Dependency Resolution Helper
            const isTaskBlocked = (task) => {
                if (!task.dependencyId) return false;
                const parent = tasks.find(t => t.id === task.dependencyId);
                return parent && parent.status !== 'Completed';
            };

            const getParentTaskName = (task) => {
                if (!task.dependencyId) return null;
                const parent = tasks.find(t => t.id === task.dependencyId);
                return parent ? parent.name : null;
            };

            const calculatedTasks = useMemo(() => {
                return tasks.map(task => {
                    const blocked = isTaskBlocked(task);
                    let priorityScore = 0;

                    if (task.status === 'Completed' || task.status === 'Cancelled') {
                        priorityScore = 0;
                    } else if (blocked) {
                        priorityScore = 5; // Low priority when blocked
                    } else {
                        // Priority Weighting Engine
                        const impScore = task.importance || 20;
                        const urgScore = task.urgency || 20;
                        priorityScore += impScore + urgScore;

                        // Check if other tasks depend on THIS task
                        const hasDependents = tasks.some(t => t.dependencyId === task.id && t.status !== 'Completed');
                        if (hasDependents) priorityScore += 30; // High strategic weight

                        if (task.isProtected) priorityScore += 25; // Protected time (Family/Girlfriend)

                        // Deadline approaching boost
                        if (task.deadline) {
                            const today = new Date();
                            const due = new Date(task.deadline);
                            const diffDays = Math.ceil((due - today) / (1000 * 60 * 60 * 24));
                            if (diffDays < 0) priorityScore += 40; // Overdue!
                            else if (diffDays <= 3) priorityScore += 25;
                            else if (diffDays <= 7) priorityScore += 10;
                        }
                    }

                    return {
                        ...task,
                        isBlocked: blocked,
                        parentName: getParentTaskName(task),
                        priorityScore
                    };
                });
            }, [tasks]);

            // Next Best Action Algorithm
            const nextBestAction = useMemo(() => {
                const uncompleted = calculatedTasks.filter(t => t.status !== 'Completed' && t.status !== 'Cancelled' && !t.isBlocked);
                if (uncompleted.length === 0) return null;

                // Sort descending by score
                const sorted = [...uncompleted].sort((a, b) => b.priorityScore - a.priorityScore);
                return sorted[0];
            }, [calculatedTasks]);

            // Top Next 3 Actions
            const top3NextActions = useMemo(() => {
                const uncompleted = calculatedTasks.filter(t => t.status !== 'Completed' && t.status !== 'Cancelled' && !t.isBlocked);
                const sorted = [...uncompleted].sort((a, b) => b.priorityScore - a.priorityScore);
                return sorted.slice(1, 4);
            }, [calculatedTasks]);

            // Quick Wins (Tasks <= 30 mins)
            const quickWins = useMemo(() => {
                return calculatedTasks
                    .filter(t => t.status !== 'Completed' && t.status !== 'Cancelled' && !t.isBlocked && t.estimatedMinutes <= 30)
                    .sort((a, b) => b.priorityScore - a.priorityScore)
                    .slice(0, 3);
            }, [calculatedTasks]);

            // "I Have X Hours" recommendations
            const hourRecommendations = useMemo(() => {
                const maxMins = availableHours * 60;
                let currentSum = 0;
                const result = [];

                const availableTasks = calculatedTasks
                    .filter(t => t.status !== 'Completed' && t.status !== 'Cancelled' && !t.isBlocked)
                    .sort((a, b) => b.priorityScore - a.priorityScore);

                for (let task of availableTasks) {
                    if (currentSum + task.estimatedMinutes <= maxMins) {
                        result.push(task);
                        currentSum += task.estimatedMinutes;
                    }
                }
                return { tasks: result, totalMinutes: currentSum };
            }, [calculatedTasks, availableHours]);

            // KPI Stats
            const stats = useMemo(() => {
                const total = tasks.length;
                const completed = tasks.filter(t => t.status === 'Completed').length;
                const highPriority = tasks.filter(t => t.priority === 'High' && t.status !== 'Completed').length;
                const blocked = calculatedTasks.filter(t => t.isBlocked && t.status !== 'Completed').length;
                const percent = total > 0 ? Math.round((completed / total) * 100) : 0;
                return { total, completed, highPriority, blocked, percent };
            }, [tasks, calculatedTasks]);

            // Home Leave Gamification Score (0 - 1000)
            const homeLeaveScore = useMemo(() => {
                if (tasks.length === 0) return 0;
                const baseScore = stats.percent * 8; // Max 800
                const visaProgress = Math.round((visaWorkflow.filter(v => v.done).length / visaWorkflow.length) * 100);
                const bonus = Math.round(visaProgress * 2); // Max 200
                return baseScore + bonus;
            }, [stats, visaWorkflow]);

            const handleToggleTaskComplete = (id) => {
                setTasks(prev => prev.map(t => {
                    if (t.id === id) {
                        const newStatus = t.status === 'Completed' ? 'Not Started' : 'Completed';
                        if (newStatus === 'Completed' && window.confetti) {
                            window.confetti({ particleCount: 50, spread: 60, origin: { y: 0.7 } });
                        }
                        return { ...t, status: newStatus };
                    }
                    return t;
                }));
            };

            const handleDeleteTask = (id) => {
                if (window.confirm("Are you sure you want to delete this task?")) {
                    setTasks(prev => prev.filter(t => t.id !== id));
                }
            };

            const handleSaveTask = (taskData) => {
                if (taskData.id) {
                    // Edit existing
                    setTasks(prev => prev.map(t => t.id === taskData.id ? taskData : t));
                } else {
                    // Create new
                    const newTask = {
                        ...taskData,
                        id: Date.now().toString(),
                        status: 'Not Started'
                    };
                    setTasks(prev => [newTask, ...prev]);
                }
                setIsAddModalOpen(false);
                setEditingTask(null);
            };

            const handleAddSuggestionAsTask = (sugg) => {
                const newTask = {
                    id: Date.now().toString(),
                    name: sugg.text,
                    category: sugg.category || 'Personal',
                    project: 'Personal / Family',
                    priority: 'Medium',
                    importance: 25,
                    urgency: 20,
                    estimatedMinutes: 30,
                    status: 'Not Started',
                    deadline: '',
                    dependencyId: null,
                    notes: 'Added from intelligent suggestions.',
                    isProtected: false
                };
                setTasks(prev => [newTask, ...prev]);
                setSuggestions(prev => prev.filter(s => s.id !== sugg.id));
            };

            // Start Pomodoro Timer
            const handleStartTimerForTask = (task) => {
                setTimerTask(task);
                setTimerSeconds((task.estimatedMinutes || 25) * 60);
                setTimerModalOpen(true);
                setTimerActive(true);
            };

            // Export / Import Data
            const handleExportJSON = () => {
                const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify({ tasks, signOffDate, leaveDuration, visaWorkflow }, null, 2));
                const downloadAnchor = document.createElement('a');
                downloadAnchor.setAttribute("href", dataStr);
                downloadAnchor.setAttribute("download", `home_leave_backup_${new Date().toISOString().slice(0,10)}.json`);
                document.body.appendChild(downloadAnchor);
                downloadAnchor.click();
                downloadAnchor.remove();
            };

            const handleExportCSV = () => {
                let csv = 'ID,Name,Category,Project,Priority,Status,Deadline,EstimatedMinutes,Protected\n';
                tasks.forEach(t => {
                    csv += `"${t.id}","${t.name.replace(/"/g, '""')}","${t.category}","${t.project}","${t.priority}","${t.status}","${t.deadline || ''}",${t.estimatedMinutes},${t.isProtected}\n`;
                });
                const blob = new Blob([csv], { type: 'text/csv' });
                const url = window.URL.createObjectURL(blob);
                const a = document.createElement('a');
                a.setAttribute('href', url);
                a.setAttribute('download', `home_leave_tasks_${new Date().toISOString().slice(0,10)}.csv`);
                a.click();
            };

            const handleImportJSON = (e) => {
                const fileReader = new FileReader();
                if (e.target.files && e.target.files[0]) {
                    fileReader.readAsText(e.target.files[0], "UTF-8");
                    fileReader.onload = (event) => {
                        try {
                            const parsed = JSON.parse(event.target.result);
                            if (parsed.tasks) setTasks(parsed.tasks);
                            if (parsed.signOffDate) setSignOffDate(parsed.signOffDate);
                            if (parsed.leaveDuration) setLeaveDuration(parsed.leaveDuration);
                            if (parsed.visaWorkflow) setVisaWorkflow(parsed.visaWorkflow);
                            alert("Data successfully restored from backup!");
                        } catch (err) {
                            alert("Invalid backup JSON file.");
                        }
                    };
                }
            };

            const handleResetDefaults = () => {
                if (window.confirm("Reset all tasks back to initial 25 home leave tasks?")) {
                    setTasks(DEFAULT_TASKS);
                    localStorage.removeItem('hl_tasks');
                }
            };

            // Filtered tasks for Master Task Table/Cards
            const filteredTasks = useMemo(() => {
                return calculatedTasks.filter(t => {
                    const matchesSearch = t.name.toLowerCase().includes(searchQuery.toLowerCase()) ||
                                          t.category.toLowerCase().includes(searchQuery.toLowerCase()) ||
                                          (t.notes && t.notes.toLowerCase().includes(searchQuery.toLowerCase()));
                    const matchesCategory = selectedCategory === 'All' || t.category === selectedCategory;
                    const matchesStatus = selectedStatus === 'All' || 
                        (selectedStatus === 'Blocked' ? t.isBlocked : t.status === selectedStatus);
                    return matchesSearch && matchesCategory && matchesStatus;
                });
            }, [calculatedTasks, searchQuery, selectedCategory, selectedStatus]);

            return (
                <div className="pb-24 pt-4 px-3 sm:px-6 max-w-7xl mx-auto space-y-8">
                    
                    <!-- STICKY TOP NAVIGATION BAR -->
                    <header className="sticky top-2 z-40 bg-dark-card/90 backdrop-blur-md border border-gold-500/20 rounded-2xl px-4 py-3 flex items-center justify-between shadow-2xl">
                        <div className="flex items-center space-x-3">
                            <div className="w-9 h-9 rounded-xl gold-gradient-bg flex items-center justify-center text-black font-extrabold text-lg shadow-md">
                                ⚓
                            </div>
                            <div>
                                <h1 className="text-sm sm:text-base font-bold tracking-tight text-white flex items-center gap-2">
                                    HOME LEAVE <span className="gold-gradient-text">OS</span>
                                </h1>
                                <p className="text-[10px] sm:text-xs text-gray-400">Yash's Command Center • 2026</p>
                            </div>
                        </div>

                        <!-- Navigation Anchor Links for Smooth Scrolling -->
                        <nav className="hidden md:flex items-center space-x-6 text-xs font-semibold text-gray-300">
                            <a href="#hero" className="hover:text-gold-400 transition-colors">Overview</a>
                            <a href="#today" className="hover:text-gold-400 transition-colors">Today</a>
                            <a href="#tasks" className="hover:text-gold-400 transition-colors">Master Tasks</a>
                            <a href="#projects" className="hover:text-gold-400 transition-colors">Projects</a>
                            <a href="#finance" className="hover:text-gold-400 transition-colors">Finance</a>
                            <a href="#analytics" className="hover:text-gold-400 transition-colors">Analytics</a>
                        </nav>

                        <div className="flex items-center space-x-2">
                            <button 
                                onClick={() => { setEditingTask(null); setIsAddModalOpen(true); }}
                                className="gold-gradient-bg text-black font-bold px-3 py-1.5 rounded-xl text-xs sm:text-sm flex items-center space-x-1 hover:brightness-110 transition-all gold-glow-sm"
                            >
                                <span className="text-base leading-none">+</span>
                                <span className="hidden sm:inline">Add Task</span>
                            </button>
                        </div>
                    </header>

                    <!-- 1. HERO / COUNTDOWN SECTION -->
                    <section id="hero" className="glass-card rounded-3xl p-5 sm:p-8 relative overflow-hidden">
                        <!-- Decorative ambient gold light -->
                        <div className="absolute -top-24 -right-24 w-72 h-72 bg-gold-500/10 rounded-full blur-3xl pointer-events-none"></div>

                        <div className="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center relative z-10">
                            <div className="lg:col-span-7 space-y-3">
                                <div className="inline-flex items-center space-x-2 px-3 py-1 rounded-full bg-gold-500/10 border border-gold-500/30 text-gold-400 text-xs font-semibold">
                                    <span>⚓ SEAFARER FIRST CONTRACT FINISH</span>
                                </div>
                                <h2 className="text-2xl sm:text-4xl font-extrabold text-white tracking-tight leading-tight">
                                    HOME LEAVE <span className="gold-gradient-text">COMMAND CENTER</span>
                                </h2>
                                <p className="text-gray-400 text-xs sm:text-sm max-w-xl">
                                    Your time. Your priorities. Your next move. Maximizing career compliance, courses, US visa, relationship, family, driving & Mariner Wealth Pro startup launch.
                                </p>
                            </div>

                            <!-- Live Countdown Display -->
                            <div className="lg:col-span-5 bg-dark-bg/80 border border-gold-500/20 rounded-2xl p-4 sm:p-5 flex flex-col justify-between space-y-4">
                                <div className="flex justify-between items-start">
                                    <div>
                                        <p className="text-[11px] font-semibold tracking-wider text-gold-400 uppercase">Sign-Off Countdown</p>
                                        <p className="text-xs text-gray-400">Expected: {countdownData.signOffFormatted}</p>
                                    </div>
                                    <div className="flex items-center space-x-1 text-xs">
                                        <label className="text-gray-500 text-[10px]">Date:</label>
                                        <input 
                                            type="date" 
                                            value={signOffDate} 
                                            onChange={(e) => setSignOffDate(e.target.value)}
                                            className="bg-dark-card text-gold-400 border border-gold-500/30 rounded px-2 py-0.5 text-xs focus:outline-none"
                                        />
                                    </div>
                                </div>

                                <div className="flex items-center justify-around bg-dark-card/90 rounded-xl p-3 border border-neutral-800">
                                    <div className="text-center">
                                        <span className="text-3xl sm:text-4xl font-black text-white font-mono">{countdownData.daysUntil}</span>
                                        <p className="text-[10px] text-gray-400 font-semibold uppercase mt-1">Days To Sign-off</p>
                                    </div>
                                    <div className="h-8 w-[1px] bg-neutral-800"></div>
                                    <div className="text-center">
                                        <span className="text-3xl sm:text-4xl font-black text-gold-400 font-mono">{leaveDuration}</span>
                                        <p className="text-[10px] text-gray-400 font-semibold uppercase mt-1">Leave Days</p>
                                    </div>
                                </div>

                                <div className="grid grid-cols-2 gap-2 text-[11px] text-gray-300 pt-1">
                                    <div className="bg-dark-card/50 p-2 rounded-lg border border-neutral-800/80">
                                        <span className="text-gray-500 block text-[9px]">RETURN TO SEA:</span>
                                        <span className="font-semibold text-white">{countdownData.returnFormatted}</span>
                                    </div>
                                    <div className="bg-dark-card/50 p-2 rounded-lg border border-neutral-800/80">
                                        <span className="text-gray-500 block text-[9px]">HOME LEAVE SCORE:</span>
                                        <span className="font-semibold text-gold-400">{homeLeaveScore} / 1000 pts</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </section>

                    <!-- 2. QUICK STATS (5 KPI CARDS) -->
                    <section className="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-5 gap-3">
                        <div className="glass-card rounded-2xl p-4 border border-gold-500/10 flex flex-col justify-between">
                            <span className="text-[11px] font-semibold text-gray-400 uppercase tracking-wider">📋 TOTAL TASKS</span>
                            <div className="mt-2 flex items-baseline justify-between">
                                <span className="text-2xl sm:text-3xl font-black text-white font-mono">{stats.total}</span>
                                <span className="text-xs text-gray-500">Items</span>
                            </div>
                        </div>

                        <div className="glass-card rounded-2xl p-4 border border-emerald-500/20 flex flex-col justify-between">
                            <span className="text-[11px] font-semibold text-emerald-400 uppercase tracking-wider">✅ COMPLETED</span>
                            <div className="mt-2 flex items-baseline justify-between">
                                <span className="text-2xl sm:text-3xl font-black text-emerald-400 font-mono">{stats.completed}</span>
                                <span className="text-xs text-emerald-500/80">{stats.percent}% Done</span>
                            </div>
                        </div>

                        <div className="glass-card rounded-2xl p-4 border border-amber-500/20 flex flex-col justify-between">
                            <span className="text-[11px] font-semibold text-amber-400 uppercase tracking-wider">🔥 HIGH PRIORITY</span>
                            <div className="mt-2 flex items-baseline justify-between">
                                <span className="text-2xl sm:text-3xl font-black text-amber-400 font-mono">{stats.highPriority}</span>
                                <span className="text-xs text-amber-500/80">Action Needed</span>
                            </div>
                        </div>

                        <div className="glass-card rounded-2xl p-4 border border-rose-500/20 flex flex-col justify-between">
                            <span className="text-[11px] font-semibold text-rose-400 uppercase tracking-wider">🚧 BLOCKED</span>
                            <div className="mt-2 flex items-baseline justify-between">
                                <span className="text-2xl sm:text-3xl font-black text-rose-400 font-mono">{stats.blocked}</span>
                                <span className="text-xs text-rose-500/80">Waiting Deps</span>
                            </div>
                        </div>

                        <div className="glass-card col-span-2 sm:col-span-1 rounded-2xl p-4 border border-gold-500/20 flex flex-col justify-between">
                            <span className="text-[11px] font-semibold text-gold-400 uppercase tracking-wider">📈 PROGRESS</span>
                            <div className="mt-2 space-y-1">
                                <div className="flex justify-between text-xs font-mono">
                                    <span className="text-gray-300">Overall</span>
                                    <span className="text-gold-400 font-bold">{stats.percent}%</span>
                                </div>
                                <div className="w-full bg-dark-bg h-2 rounded-full overflow-hidden border border-gold-500/20">
                                    <div className="gold-gradient-bg h-full rounded-full transition-all duration-500" style={{ width: `${stats.percent}%` }}></div>
                                </div>
                            </div>
                        </div>
                    </section>

                    <!-- 25. DAILY BRIEFING -->
                    <section className="bg-dark-elevated/80 border border-gold-500/20 rounded-2xl p-4 sm:p-5 flex items-start space-x-3 shadow-lg">
                        <div className="text-2xl">☀️</div>
                        <div className="space-y-1">
                            <h3 className="text-sm font-bold text-gold-400 uppercase tracking-wider">TODAY'S BRIEFING • Yash</h3>
                            <p className="text-xs sm:text-sm text-gray-300 leading-relaxed">
                                {nextBestAction ? (
                                    <span>
                                        Your highest strategic priority today is <strong className="text-white">{nextBestAction.name}</strong> ({nextBestAction.category}). 
                                        {nextBestAction.parentName ? ` (Note: Unlocks dependent step: ${nextBestAction.parentName})` : ''} 
                                        Keep focused on high leverage tasks!
                                    </span>
                                ) : (
                                    <span>Outstanding job, Yash! All critical pending tasks are currently completed or up to date. Review project updates below!</span>
                                )}
                            </p>
                        </div>
                    </section>

                    <!-- 3. "WHAT SHOULD I DO NOW?" (SMART PRIORITY ENGINE) -->
                    <section className="glass-card rounded-3xl p-5 sm:p-7 border-2 border-gold-500/40 gold-glow relative">
                        <div className="flex items-center justify-between mb-4">
                            <div className="flex items-center space-x-2">
                                <span className="text-xl">🎯</span>
                                <h2 className="text-base sm:text-xl font-bold tracking-tight text-white">WHAT SHOULD I DO RIGHT NOW?</h2>
                            </div>
                            <span className="text-[10px] font-mono px-2.5 py-1 rounded-full bg-gold-500/10 border border-gold-500/30 text-gold-400 uppercase font-semibold">
                                AI PRIORITY ENGINE
                            </span>
                        </div>

                        {nextBestAction ? (
                            <div className="space-y-5">
                                <div className="bg-dark-bg/90 border border-gold-500/30 rounded-2xl p-4 sm:p-6 space-y-4">
                                    <div className="flex flex-wrap items-center justify-between gap-2">
                                        <span className="text-xs font-bold text-gold-400 tracking-wider uppercase">⚡ NEXT BEST ACTION</span>
                                        <div className="flex items-center space-x-2 text-xs">
                                            <span className="px-2 py-0.5 rounded bg-amber-500/20 border border-amber-500/40 text-amber-300 font-semibold">
                                                🔥 Score: {nextBestAction.priorityScore}
                                            </span>
                                            <span className="px-2 py-0.5 rounded bg-dark-card text-gray-300 font-mono">
                                                ⏱ {nextBestAction.estimatedMinutes} mins
                                            </span>
                                        </div>
                                    </div>

                                    <div>
                                        <h3 className="text-lg sm:text-2xl font-black text-white">{nextBestAction.name}</h3>
                                        <p className="text-xs text-gray-400 mt-1">
                                            Category: <strong className="text-gold-400">{nextBestAction.category}</strong> • Project: <strong className="text-gray-200">{nextBestAction.project}</strong>
                                            {nextBestAction.deadline && ` • Due: ${nextBestAction.deadline}`}
                                        </p>
                                    </div>

                                    {nextBestAction.notes && (
                                        <p className="text-xs text-gray-300 bg-dark-card/80 p-3 rounded-xl border border-neutral-800 font-mono">
                                            💡 Reason/Notes: "{nextBestAction.notes}"
                                        </p>
                                    )}

                                    <div className="flex flex-wrap items-center gap-3 pt-2">
                                        <button 
                                            onClick={() => handleStartTimerForTask(nextBestAction)}
                                            className="gold-gradient-bg text-black font-extrabold px-5 py-2 rounded-xl text-xs sm:text-sm hover:brightness-110 transition-all flex items-center space-x-2 shadow-md"
                                        >
                                            <span>▶ START TIMER</span>
                                        </button>
                                        <button 
                                            onClick={() => handleToggleTaskComplete(nextBestAction.id)}
                                            className="bg-emerald-600/20 border border-emerald-500/40 text-emerald-400 font-bold px-4 py-2 rounded-xl text-xs sm:text-sm hover:bg-emerald-600/30 transition-all"
                                        >
                                            ✓ COMPLETE
                                        </button>
                                        <button 
                                            onClick={() => { setEditingTask(nextBestAction); setIsAddModalOpen(true); }}
                                            className="bg-dark-card border border-neutral-700 text-gray-300 font-medium px-4 py-2 rounded-xl text-xs sm:text-sm hover:text-white transition-all"
                                        >
                                            ✏️ EDIT
                                        </button>
                                    </div>
                                </div>

                                <!-- NEXT 3 ACTIONS -->
                                {top3NextActions.length > 0 && (
                                    <div className="space-y-2">
                                        <h4 className="text-xs font-bold uppercase text-gray-400 tracking-wider">NEXT 3 QUEUED ACTIONS</h4>
                                        <div className="grid grid-cols-1 sm:grid-cols-3 gap-3">
                                            {top3NextActions.map((task, idx) => (
                                                <div key={task.id} className="bg-dark-card/80 border border-neutral-800 rounded-xl p-3 flex flex-col justify-between space-y-2 hover:border-gold-500/30 transition-colors">
                                                    <div className="flex items-center justify-between">
                                                        <span className="text-[10px] font-bold text-gold-400">#{idx + 1} QUEUED</span>
                                                        <span className="text-[10px] text-gray-400 font-mono">{task.estimatedMinutes}m</span>
                                                    </div>
                                                    <p className="text-xs font-semibold text-white line-clamp-2">{task.name}</p>
                                                    <div className="flex justify-between items-center text-[10px] text-gray-400 pt-1">
                                                        <span>{task.category}</span>
                                                        <button 
                                                            onClick={() => handleToggleTaskComplete(task.id)}
                                                            className="text-emerald-400 hover:underline"
                                                        >
                                                            ✓ Done
                                                        </button>
                                                    </div>
                                                </div>
                                            ))}
                                        </div>
                                    </div>
                                )}
                            </div>
                        ) : (
                            <div className="text-center py-8 text-gray-400 text-sm">
                                🎉 All pending tasks are complete! Add new goals or relax!
                            </div>
                        )}
                    </section>

                    <!-- 4. TODAY & 9. QUICK WINS -->
                    <div id="today" className="grid grid-cols-1 lg:grid-cols-2 gap-6">
                        <!-- TODAY SECTION -->
                        <div className="glass-card rounded-3xl p-5 border border-gold-500/20 space-y-4">
                            <div className="flex items-center justify-between">
                                <div className="flex items-center space-x-2">
                                    <span className="text-lg">☀️</span>
                                    <h3 className="text-sm font-bold uppercase text-white tracking-wider">TODAY'S HIGHLIGHTS</h3>
                                </div>
                                <span className="text-[11px] font-mono text-gray-400">{new Date().toLocaleDateString('en-GB', { weekday: 'short', day: 'numeric', month: 'short' })}</span>
                            </div>

                            <div className="space-y-2">
                                {calculatedTasks.filter(t => t.status !== 'Completed' && (t.priority === 'High' || t.isProtected)).slice(0, 4).map(task => (
                                    <div key={task.id} className="bg-dark-card/90 border border-neutral-800 hover:border-gold-500/30 rounded-xl p-3 flex items-center justify-between transition-colors">
                                        <div className="flex items-center space-x-3">
                                            <input 
                                                type="checkbox" 
                                                checked={task.status === 'Completed'}
                                                onChange={() => handleToggleTaskComplete(task.id)}
                                                className="w-4 h-4 accent-gold-500 rounded cursor-pointer"
                                            />
                                            <div>
                                                <p className="text-xs font-semibold text-white">{task.name}</p>
                                                <p className="text-[10px] text-gray-400">{task.category} • {task.estimatedMinutes}m</p>
                                            </div>
                                        </div>
                                        {task.isProtected ? (
                                            <span className="text-[10px] px-2 py-0.5 rounded bg-rose-500/20 text-rose-300 border border-rose-500/30 font-semibold">❤️ PROTECTED</span>
                                        ) : (
                                            <span className="text-[10px] px-2 py-0.5 rounded bg-amber-500/20 text-amber-300 font-semibold">🔥 HIGH</span>
                                        )}
                                    </div>
                                ))}
                            </div>
                        </div>

                        <!-- 9. QUICK WINS (≤ 30 MINS) -->
                        <div className="glass-card rounded-3xl p-5 border border-gold-500/20 space-y-4">
                            <div className="flex items-center justify-between">
                                <div className="flex items-center space-x-2">
                                    <span className="text-lg">⚡</span>
                                    <h3 className="text-sm font-bold uppercase text-white tracking-wider">QUICK WINS (≤ 30 MINS)</h3>
                                </div>
                                <span className="text-[10px] text-gold-400 font-mono">Productive Gaps</span>
                            </div>

                            <div className="space-y-2">
                                {quickWins.length > 0 ? quickWins.map(task => (
                                    <div key={task.id} className="bg-dark-card/90 border border-neutral-800 hover:border-gold-500/30 rounded-xl p-3 flex items-center justify-between transition-colors">
                                        <div>
                                            <p className="text-xs font-semibold text-white">{task.name}</p>
                                            <p className="text-[10px] text-gray-400">{task.category} • ⏱ {task.estimatedMinutes} mins</p>
                                        </div>
                                        <button 
                                            onClick={() => handleToggleTaskComplete(task.id)}
                                            className="text-xs bg-gold-500/10 border border-gold-500/30 text-gold-400 px-2.5 py-1 rounded-lg hover:bg-gold-500/20 font-bold"
                                        >
                                            ✓ Complete
                                        </button>
                                    </div>
                                )) : (
                                    <p className="text-xs text-gray-500 py-4 text-center">No quick wins remaining right now!</p>
                                )}
                            </div>
                        </div>
                    </div>

                    <!-- 10. "I HAVE X HOURS" INTERACTIVE CALCULATOR -->
                    <section className="glass-card rounded-3xl p-5 sm:p-6 border border-gold-500/20 space-y-4">
                        <div className="flex flex-wrap items-center justify-between gap-3">
                            <div className="flex items-center space-x-2">
                                <span className="text-xl">⏱</span>
                                <h3 className="text-sm sm:text-base font-bold uppercase text-white tracking-wider">I HAVE X HOURS AVAILABLE</h3>
                            </div>
                            <div className="flex items-center space-x-2">
                                <span className="text-xs text-gray-400">Time window:</span>
                                <select 
                                    value={availableHours} 
                                    onChange={(e) => setAvailableHours(parseFloat(e.target.value))}
                                    className="bg-dark-bg border border-gold-500/40 text-gold-400 rounded-xl px-3 py-1 text-xs font-bold font-mono focus:outline-none"
                                >
                                    <option value={0.5}>30 Minutes</option>
                                    <option value={1}>1 Hour</option>
                                    <option value={1.5}>1.5 Hours</option>
                                    <option value={2}>2 Hours</option>
                                    <option value={3}>3 Hours</option>
                                    <option value={4}>4 Hours</option>
                                </select>
                            </div>
                        </div>

                        <p className="text-xs text-gray-400">
                            Select how much time you have right now. The engine fits maximum high-value tasks into your window:
                        </p>

                        <div className="bg-dark-bg/80 border border-neutral-800 rounded-2xl p-4 space-y-3">
                            <div className="flex items-center justify-between text-xs font-mono">
                                <span className="text-gray-300">Recommended Plan ({hourRecommendations.tasks.length} tasks)</span>
                                <span className="text-gold-400 font-bold">Total: {Math.floor(hourRecommendations.totalMinutes / 60)}h {hourRecommendations.totalMinutes % 60}m / {availableHours}h</span>
                            </div>

                            <div className="grid grid-cols-1 md:grid-cols-3 gap-3">
                                {hourRecommendations.tasks.map((task, idx) => (
                                    <div key={task.id} className="bg-dark-card border border-neutral-800 p-3 rounded-xl space-y-1">
                                        <div className="flex justify-between items-center text-[10px] text-gold-400 font-bold">
                                            <span>#{idx + 1} FIT</span>
                                            <span>{task.estimatedMinutes}m</span>
                                        </div>
                                        <p className="text-xs font-semibold text-white">{task.name}</p>
                                        <p className="text-[10px] text-gray-400">{task.category}</p>
                                    </div>
                                ))}
                            </div>
                        </div>
                    </section>

                    <!-- 5 & 6. MASTER TASKS SECTION (WITH SEARCH & FILTERS) -->
                    <section id="tasks" className="glass-card rounded-3xl p-5 sm:p-7 border border-gold-500/20 space-y-5">
                        <div className="flex flex-col sm:flex-row sm:items-center justify-between gap-4">
                            <div>
                                <h2 className="text-base sm:text-xl font-extrabold text-white tracking-tight flex items-center gap-2">
                                    📋 MASTER TASKS ENGINE <span className="text-xs font-mono font-normal text-gold-400">({filteredTasks.length} items)</span>
                                </h2>
                                <p className="text-xs text-gray-400">Full 25 preloaded home-leave tasks with smart priority and dependencies.</p>
                            </div>

                            <button 
                                onClick={() => { setEditingTask(null); setIsAddModalOpen(true); }}
                                className="gold-gradient-bg text-black font-extrabold px-4 py-2 rounded-xl text-xs flex items-center justify-center space-x-1 hover:brightness-110 shadow-md"
                            >
                                <span>+ Add Custom Task</span>
                            </button>
                        </div>

                        <!-- SEARCH & FILTERS -->
                        <div className="grid grid-cols-1 sm:grid-cols-3 gap-3">
                            <input 
                                type="text"
                                placeholder="🔍 Search task name or notes..."
                                value={searchQuery}
                                onChange={(e) => setSearchQuery(e.target.value)}
                                className="bg-dark-bg border border-neutral-800 focus:border-gold-500/50 text-xs rounded-xl px-3 py-2 text-white placeholder-gray-500 focus:outline-none"
                            />

                            <select 
                                value={selectedCategory} 
                                onChange={(e) => setSelectedCategory(e.target.value)}
                                className="bg-dark-bg border border-neutral-800 focus:border-gold-500/50 text-xs rounded-xl px-3 py-2 text-gray-300 focus:outline-none"
                            >
                                <option value="All">All Categories</option>
                                <option value="Career">Career</option>
                                <option value="Courses">Courses</option>
                                <option value="US Visa">US Visa</option>
                                <option value="Relationship">Relationship</option>
                                <option value="Personal">Personal Development</option>
                                <option value="Family">Family & Friends</option>
                                <option value="Business">Business / Learning</option>
                                <option value="Finance">Finance</option>
                            </select>

                            <select 
                                value={selectedStatus} 
                                onChange={(e) => setSelectedStatus(e.target.value)}
                                className="bg-dark-bg border border-neutral-800 focus:border-gold-500/50 text-xs rounded-xl px-3 py-2 text-gray-300 focus:outline-none"
                            >
                                <option value="All">All Statuses</option>
                                <option value="Not Started">🟡 Not Started</option>
                                <option value="In Progress">🔵 In Progress</option>
                                <option value="Blocked">🔴 Blocked</option>
                                <option value="Completed">🟢 Completed</option>
                            </select>
                        </div>

                        <!-- TASK LIST / CARDS -->
                        <div className="space-y-3">
                            {filteredTasks.map(task => (
                                <div 
                                    key={task.id} 
                                    className={`bg-dark-card/90 border ${task.isBlocked ? 'border-rose-500/30' : task.status === 'Completed' ? 'border-emerald-500/20 opacity-70' : 'border-neutral-800'} rounded-2xl p-4 flex flex-col md:flex-row md:items-center justify-between gap-4 transition-all hover:border-gold-500/30`}
                                >
                                    <div className="flex items-start space-x-3">
                                        <input 
                                            type="checkbox" 
                                            checked={task.status === 'Completed'}
                                            onChange={() => handleToggleTaskComplete(task.id)}
                                            className="mt-1 w-4 h-4 accent-gold-500 rounded cursor-pointer"
                                        />
                                        <div className="space-y-1">
                                            <div className="flex flex-wrap items-center gap-2">
                                                <h4 className={`text-sm font-bold ${task.status === 'Completed' ? 'line-through text-gray-400' : 'text-white'}`}>
                                                    {task.name}
                                                </h4>

                                                {/* Smart Dependency Badges */}
                                                {task.isBlocked ? (
                                                    <span className="text-[10px] px-2 py-0.5 rounded bg-rose-500/20 border border-rose-500/40 text-rose-300 font-bold">
                                                        🔴 BLOCKED (Requires: {task.parentName})
                                                    </span>
                                                ) : task.parentName ? (
                                                    <span className="text-[10px] px-2 py-0.5 rounded bg-emerald-500/20 border border-emerald-500/40 text-emerald-300 font-bold">
                                                        🟢 READY (Dep Completed)
                                                    </span>
                                                ) : null}

                                                {task.isProtected && (
                                                    <span className="text-[10px] px-2 py-0.5 rounded bg-rose-500/20 border border-rose-500/40 text-rose-300 font-bold">
                                                        ❤️ PROTECTED TIME
                                                    </span>
                                                )}
                                            </div>

                                            <div className="flex flex-wrap items-center gap-3 text-[11px] text-gray-400 font-mono">
                                                <span>Tag: <strong className="text-gold-400">{task.category}</strong></span>
                                                <span>Est: <strong>{task.estimatedMinutes}m</strong></span>
                                                {task.deadline && <span>Due: <strong>{task.deadline}</strong></span>}
                                                <span>Priority Score: <strong className="text-amber-400">{task.priorityScore}</strong></span>
                                            </div>

                                            {task.notes && (
                                                <p className="text-xs text-gray-400 bg-dark-bg/60 p-2 rounded-lg border border-neutral-800 font-mono">
                                                    {task.notes}
                                                </p>
                                            )}
                                        </div>
                                    </div>

                                    {/* Action buttons */}
                                    <div className="flex items-center space-x-2 self-end md:self-center pt-2 md:pt-0">
                                        <button 
                                            onClick={() => handleStartTimerForTask(task)}
                                            className="text-xs bg-dark-bg border border-neutral-700 hover:border-gold-500/50 text-gray-300 px-3 py-1.5 rounded-xl font-mono"
                                        >
                                            ⏱ Timer
                                        </button>
                                        <button 
                                            onClick={() => { setEditingTask(task); setIsAddModalOpen(true); }}
                                            className="text-xs bg-dark-bg border border-neutral-700 hover:border-gold-500/50 text-gray-300 px-3 py-1.5 rounded-xl"
                                        >
                                            ✏️ Edit
                                        </button>
                                        <button 
                                            onClick={() => handleDeleteTask(task.id)}
                                            className="text-xs bg-rose-500/10 border border-rose-500/30 text-rose-400 px-2.5 py-1.5 rounded-xl hover:bg-rose-500/20"
                                        >
                                            🗑
                                        </button>
                                    </div>
                                </div>
                            ))}
                        </div>
                    </section>

                    <!-- 13. PROTECTED TIME - PEOPLE & LIFE -->
                    <section className="glass-card rounded-3xl p-5 sm:p-7 border border-rose-500/30 space-y-4">
                        <div className="flex items-center space-x-2">
                            <span className="text-xl">❤️</span>
                            <h2 className="text-base sm:text-lg font-bold uppercase text-white tracking-wider">PROTECTED TIME: PEOPLE & LIFE BALANCE</h2>
                        </div>

                        <p className="text-xs text-gray-400">
                            Home leave is not strictly work and compliance. Key personal relationships are guarded with mandatory protected time limits.
                        </p>

                        <div className="grid grid-cols-1 md:grid-cols-3 gap-4">
                            <div className="bg-dark-card border border-rose-500/30 rounded-2xl p-4 space-y-2">
                                <div className="flex justify-between items-center">
                                    <span className="text-xs font-bold text-rose-400 uppercase">Girlfriend</span>
                                    <span className="text-[10px] px-2 py-0.5 rounded bg-rose-500/20 text-rose-300 font-mono">Min 7 Days</span>
                                </div>
                                <h4 className="text-sm font-semibold text-white">Meet girlfriend for at least 7 days</h4>
                                <p className="text-xs text-gray-400">Uninterrupted quality time together scheduled during leave.</p>
                            </div>

                            <div className="bg-dark-card border border-rose-500/30 rounded-2xl p-4 space-y-2">
                                <div className="flex justify-between items-center">
                                    <span className="text-xs font-bold text-rose-400 uppercase">Family Time</span>
                                    <span className="text-[10px] px-2 py-0.5 rounded bg-rose-500/20 text-rose-300 font-mono">Protected</span>
                                </div>
                                <h4 className="text-sm font-semibold text-white">Family Quality Time & Trip</h4>
                                <p className="text-xs text-gray-400">Dedicated family trip and quality presence at home.</p>
                            </div>

                            <div className="bg-dark-card border border-rose-500/30 rounded-2xl p-4 space-y-2">
                                <div className="flex justify-between items-center">
                                    <span className="text-xs font-bold text-rose-400 uppercase">School Friends</span>
                                    <span className="text-[10px] px-2 py-0.5 rounded bg-neutral-800 text-gray-300 font-mono">Reunion</span>
                                </div>
                                <h4 className="text-sm font-semibold text-white">School Friends Trip</h4>
                                <p className="text-xs text-gray-400">Reconnect with childhood friends before next contract.</p>
                            </div>
                        </div>
                    </section>

                    <!-- 14, 15, 16, 17. EXPANDABLE PROJECTS & TRACKERS -->
                    <section id="projects" className="space-y-6">
                        <div className="flex items-center space-x-2">
                            <span className="text-xl">⚓</span>
                            <h2 className="text-base sm:text-xl font-extrabold text-white tracking-tight">PROJECTS & SPECIAL TRACKERS</h2>
                        </div>

                        <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <!-- 16. US VISA TRACKER -->
                            <div className="glass-card rounded-3xl p-5 border border-gold-500/20 space-y-4">
                                <div className="flex items-center justify-between">
                                    <div className="flex items-center space-x-2">
                                        <span className="text-lg">🛂</span>
                                        <h3 className="text-sm font-bold uppercase text-white tracking-wider">US VISA WORKFLOW TRACKER</h3>
                                    </div>
                                    <span className="text-xs font-mono font-bold text-gold-400">
                                        {Math.round((visaWorkflow.filter(v => v.done).length / visaWorkflow.length) * 100)}%
                                    </span>
                                </div>

                                <div className="w-full bg-dark-bg h-2 rounded-full overflow-hidden border border-neutral-800">
                                    <div 
                                        className="gold-gradient-bg h-full rounded-full transition-all duration-300"
                                        style={{ width: `${(visaWorkflow.filter(v => v.done).length / visaWorkflow.length) * 100}%` }}
                                    ></div>
                                </div>

                                <div className="space-y-2">
                                    {visaWorkflow.map(item => (
                                        <label key={item.id} className="flex items-center justify-between bg-dark-card/80 p-2.5 rounded-xl border border-neutral-800 cursor-pointer hover:border-gold-500/30">
                                            <span className={`text-xs ${item.done ? 'line-through text-gray-400' : 'text-gray-200'}`}>{item.text}</span>
                                            <input 
                                                type="checkbox"
                                                checked={item.done}
                                                onChange={() => {
                                                    setVisaWorkflow(prev => prev.map(v => v.id === item.id ? { ...v, done: !v.done } : v));
                                                }}
                                                className="w-4 h-4 accent-gold-500 rounded"
                                            />
                                        </label>
                                    ))}
                                </div>
                            </div>

                            <!-- 15. MARINER WEALTH PRO APP LAUNCH TRACKER -->
                            <div className="glass-card rounded-3xl p-5 border border-gold-500/20 space-y-4">
                                <div className="flex items-center justify-between">
                                    <div className="flex items-center space-x-2">
                                        <span className="text-lg">🚀</span>
                                        <h3 className="text-sm font-bold uppercase text-white tracking-wider">MARINER WEALTH PRO LAUNCH</h3>
                                    </div>
                                    <span className="text-xs font-mono px-2.5 py-0.5 rounded bg-gold-500/20 border border-gold-500/30 text-gold-400 font-bold">
                                        Startup Stage
                                    </span>
                                </div>

                                <p className="text-xs text-gray-400">
                                    Track progress for releasing your flagship financial application for seafarers on Google Play Store.
                                </p>

                                <div className="space-y-2 font-mono text-xs">
                                    <div className="flex justify-between items-center bg-dark-card p-2.5 rounded-xl border border-emerald-500/30 text-emerald-400">
                                        <span>1. Planning & Logic Design</span>
                                        <span>✓ Completed</span>
                                    </div>
                                    <div className="flex justify-between items-center bg-dark-card p-2.5 rounded-xl border border-amber-500/30 text-amber-300">
                                        <span>2. Core App Development</span>
                                        <span>⚡ In Progress</span>
                                    </div>
                                    <div className="flex justify-between items-center bg-dark-card p-2.5 rounded-xl border border-neutral-800 text-gray-400">
                                        <span>3. Play Store Assets & Testing</span>
                                        <span>⏳ Queued</span>
                                    </div>
                                    <div className="flex justify-between items-center bg-dark-card p-2.5 rounded-xl border border-neutral-800 text-gray-400">
                                        <span>4. Official Google Play Release</span>
                                        <span>⏳ Target: Nov 2026</span>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </section>

                    <!-- 18. FINANCE CALCULATOR -->
                    <section id="finance" className="glass-card rounded-3xl p-5 sm:p-7 border border-gold-500/20 space-y-5">
                        <div className="flex items-center space-x-2">
                            <span className="text-xl">💰</span>
                            <h2 className="text-base sm:text-xl font-bold uppercase text-white tracking-wider">FINANCE & WEALTH COMMAND</h2>
                        </div>

                        <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <!-- HSBC Fixed Deposit Calculator -->
                            <div className="bg-dark-card border border-neutral-800 rounded-2xl p-4 space-y-3">
                                <h3 className="text-xs font-bold text-gold-400 uppercase tracking-wider">HSBC FIXED DEPOSIT (FD) CALCULATOR</h3>
                                
                                <div className="space-y-2 text-xs">
                                    <div>
                                        <label className="text-gray-400 block mb-1">Principal Amount (₹):</label>
                                        <input 
                                            type="number" 
                                            value={fdAmount} 
                                            onChange={(e) => setFdAmount(Number(e.target.value))}
                                            className="w-full bg-dark-bg border border-neutral-700 rounded-lg px-3 py-1.5 text-white font-mono"
                                        />
                                    </div>
                                    <div className="grid grid-cols-2 gap-2">
                                        <div>
                                            <label className="text-gray-400 block mb-1">Interest Rate (% p.a.):</label>
                                            <input 
                                                type="number" 
                                                step="0.1"
                                                value={fdRate} 
                                                onChange={(e) => setFdRate(Number(e.target.value))}
                                                className="w-full bg-dark-bg border border-neutral-700 rounded-lg px-3 py-1.5 text-white font-mono"
                                            />
                                        </div>
                                        <div>
                                            <label className="text-gray-400 block mb-1">Tenure (Months):</label>
                                            <input 
                                                type="number" 
                                                value={fdTenureMonths} 
                                                onChange={(e) => setFdTenureMonths(Number(e.target.value))}
                                                className="w-full bg-dark-bg border border-neutral-700 rounded-lg px-3 py-1.5 text-white font-mono"
                                            />
                                        </div>
                                    </div>
                                </div>

                                {(() => {
                                    const interest = (fdAmount * fdRate * (fdTenureMonths / 12)) / 100;
                                    const maturity = fdAmount + interest;
                                    return (
                                        <div className="bg-dark-bg p-3 rounded-xl border border-gold-500/20 text-xs font-mono space-y-1 mt-2">
                                            <div className="flex justify-between text-gray-400">
                                                <span>Est. Interest Earned:</span>
                                                <span className="text-emerald-400 font-bold">₹{Math.round(interest).toLocaleString()}</span>
                                            </div>
                                            <div className="flex justify-between text-white font-bold pt-1 border-t border-neutral-800">
                                                <span>Estimated Maturity Value:</span>
                                                <span className="text-gold-400">₹{Math.round(maturity).toLocaleString()}</span>
                                            </div>
                                        </div>
                                    );
                                })()}
                            </div>

                            <!-- SIP Investment Calculator -->
                            <div className="bg-dark-card border border-neutral-800 rounded-2xl p-4 space-y-3">
                                <h3 className="text-xs font-bold text-gold-400 uppercase tracking-wider">SIP MUTUAL FUND INVESTMENT PLANNER</h3>

                                <div className="space-y-2 text-xs">
                                    <div>
                                        <label className="text-gray-400 block mb-1">Monthly Investment (₹):</label>
                                        <input 
                                            type="number" 
                                            value={sipMonthly} 
                                            onChange={(e) => setSipMonthly(Number(e.target.value))}
                                            className="w-full bg-dark-bg border border-neutral-700 rounded-lg px-3 py-1.5 text-white font-mono"
                                        />
                                    </div>
                                    <div className="grid grid-cols-2 gap-2">
                                        <div>
                                            <label className="text-gray-400 block mb-1">Exp. Return (% p.a.):</label>
                                            <input 
                                                type="number" 
                                                step="0.5"
                                                value={sipRate} 
                                                onChange={(e) => setSipRate(Number(e.target.value))}
                                                className="w-full bg-dark-bg border border-neutral-700 rounded-lg px-3 py-1.5 text-white font-mono"
                                            />
                                        </div>
                                        <div>
                                            <label className="text-gray-400 block mb-1">Horizon (Years):</label>
                                            <input 
                                                type="number" 
                                                value={sipYears} 
                                                onChange={(e) => setSipYears(Number(e.target.value))}
                                                className="w-full bg-dark-bg border border-neutral-700 rounded-lg px-3 py-1.5 text-white font-mono"
                                            />
                                        </div>
                                    </div>
                                </div>

                                {(() => {
                                    const months = sipYears * 12;
                                    const i = sipRate / 12 / 100;
                                    const invested = sipMonthly * months;
                                    const futureVal = sipMonthly * ((Math.pow(1 + i, months) - 1) / i) * (1 + i);
                                    return (
                                        <div className="bg-dark-bg p-3 rounded-xl border border-gold-500/20 text-xs font-mono space-y-1 mt-2">
                                            <div className="flex justify-between text-gray-400">
                                                <span>Total Invested:</span>
                                                <span className="text-gray-200">₹{Math.round(invested).toLocaleString()}</span>
                                            </div>
                                            <div className="flex justify-between text-white font-bold pt-1 border-t border-neutral-800">
                                                <span>Estimated Future Value:</span>
                                                <span className="text-gold-400">₹{Math.round(futureVal).toLocaleString()}</span>
                                            </div>
                                        </div>
                                    );
                                })()}
                            </div>
                        </div>
                    </section>

                    <!-- 12. HOME LEAVE VISUAL TIMELINE -->
                    <section className="glass-card rounded-3xl p-5 sm:p-7 border border-gold-500/20 space-y-4">
                        <div className="flex items-center space-x-2">
                            <span className="text-xl">📅</span>
                            <h2 className="text-base sm:text-lg font-bold uppercase text-white tracking-wider">HOME LEAVE ROADMAP TIMELINE</h2>
                        </div>

                        <div className="flex items-center space-x-2 overflow-x-auto pb-4 pt-2 no-scrollbar">
                            {[
                                { stage: 'SIGN-OFF', icon: '⚓', desc: 'Vessel sign-off & travel home' },
                                { stage: 'DOCUMENTATION', icon: '📄', desc: 'DG Shipping & eSamudra transfer' },
                                { stage: 'COURSES', icon: '📚', desc: 'PSCRB, ECDIS, MFA & AFF' },
                                { stage: 'US VISA', icon: '🛂', desc: 'Biometrics & C1/D interview' },
                                { stage: 'PEOPLE & LIFE', icon: '❤️', desc: 'Girlfriend (7d) & Family trips' },
                                { stage: 'PERSONAL DEV', icon: '🚗', desc: 'Driving license & Swimming' },
                                { stage: 'MARINER WEALTH', icon: '💻', desc: 'App finish & Play Store launch' },
                                { stage: 'RETURN TO SEA', icon: '🚢', desc: 'Prepare for next sea contract' }
                            ].map((item, idx) => (
                                <div key={idx} className="min-w-[170px] bg-dark-card border border-neutral-800 hover:border-gold-500/40 rounded-2xl p-3 flex flex-col justify-between space-y-2 flex-shrink-0">
                                    <div className="flex items-center justify-between">
                                        <span className="text-lg">{item.icon}</span>
                                        <span className="text-[9px] font-mono font-bold text-gold-400">STAGE {idx + 1}</span>
                                    </div>
                                    <p className="text-xs font-extrabold text-white">{item.stage}</p>
                                    <p className="text-[10px] text-gray-400">{item.desc}</p>
                                </div>
                            ))}
                        </div>
                    </section>

                    <!-- 20. "WHAT AM I FORGETTING?" INTELLIGENT SUGGESTIONS -->
                    <section className="glass-card rounded-3xl p-5 sm:p-7 border border-gold-500/20 space-y-4">
                        <div className="flex items-center justify-between">
                            <div className="flex items-center space-x-2">
                                <span className="text-xl">💡</span>
                                <h2 className="text-base sm:text-lg font-bold uppercase text-white tracking-wider">WHAT AM I FORGETTING?</h2>
                            </div>
                            <span className="text-[10px] text-gray-400 font-mono">1-Click Convert To Task</span>
                        </div>

                        <p className="text-xs text-gray-400">
                            Smart seafarer reminder suggestions. Click <strong>"+ Add Task"</strong> to adopt any item as an official task.
                        </p>

                        <div className="grid grid-cols-1 sm:grid-cols-2 gap-3">
                            {suggestions.map(sugg => (
                                <div key={sugg.id} className="bg-dark-card/90 border border-neutral-800 p-3 rounded-xl flex items-center justify-between space-x-2">
                                    <div>
                                        <p className="text-xs text-gray-200 font-medium">{sugg.text}</p>
                                        <span className="text-[10px] text-gold-400 font-mono">{sugg.category}</span>
                                    </div>
                                    <button 
                                        onClick={() => handleAddSuggestionAsTask(sugg)}
                                        className="text-xs bg-gold-500/10 border border-gold-500/30 text-gold-400 px-2.5 py-1 rounded-lg hover:bg-gold-500/20 font-bold flex-shrink-0"
                                    >
                                        + Add Task
                                    </button>
                                </div>
                            ))}
                        </div>
                    </section>

                    <!-- 27. DATA STORAGE / BACKUP & RESTORE -->
                    <section id="more" className="glass-card rounded-3xl p-5 border border-gold-500/20 space-y-4">
                        <div className="flex items-center space-x-2">
                            <span className="text-xl">⚙️</span>
                            <h2 className="text-base sm:text-lg font-bold uppercase text-white tracking-wider">DATA MANAGEMENT & BACKUP</h2>
                        </div>

                        <div className="flex flex-wrap items-center gap-3 pt-1">
                            <button 
                                onClick={handleExportJSON}
                                className="bg-dark-bg border border-gold-500/30 text-gold-400 font-semibold px-4 py-2 rounded-xl text-xs hover:bg-gold-500/10 transition-all"
                            >
                                💾 Export Backup (JSON)
                            </button>
                            <button 
                                onClick={handleExportCSV}
                                className="bg-dark-bg border border-gold-500/30 text-gold-400 font-semibold px-4 py-2 rounded-xl text-xs hover:bg-gold-500/10 transition-all"
                            >
                                📊 Export Tasks (CSV)
                            </button>
                            <label className="bg-dark-bg border border-neutral-700 text-gray-300 font-semibold px-4 py-2 rounded-xl text-xs hover:text-white cursor-pointer">
                                📥 Restore Backup JSON
                                <input type="file" accept=".json" onChange={handleImportJSON} className="hidden" />
                            </label>
                            <button 
                                onClick={handleResetDefaults}
                                className="bg-rose-500/10 border border-rose-500/30 text-rose-400 font-semibold px-4 py-2 rounded-xl text-xs hover:bg-rose-500/20 transition-all ml-auto"
                            >
                                🔄 Reset Initial 25 Tasks
                            </button>
                        </div>
                    </section>

                    <!-- FLOATING ACTION BUTTON (MOBILE FAB) -->
                    <button 
                        onClick={() => { setEditingTask(null); setIsAddModalOpen(true); }}
                        className="fixed bottom-20 right-5 z-40 w-14 h-14 rounded-full gold-gradient-bg text-black text-3xl font-extrabold shadow-2xl flex items-center justify-center gold-glow hover:scale-105 active:scale-95 transition-transform"
                        title="Add Task"
                    >
                        +
                    </button>

                    <!-- MOBILE BOTTOM NAVIGATION BAR -->
                    <div className="md:hidden fixed bottom-0 left-0 right-0 z-40 bg-dark-card/95 backdrop-blur-lg border-t border-gold-500/20 px-4 py-2 flex justify-around items-center text-center">
                        <a href="#hero" className="flex flex-col items-center text-gray-400 hover:text-gold-400 text-[10px] font-semibold">
                            <span className="text-base">🏠</span>
                            <span>Home</span>
                        </a>
                        <a href="#today" className="flex flex-col items-center text-gray-400 hover:text-gold-400 text-[10px] font-semibold">
                            <span className="text-base">☀️</span>
                            <span>Today</span>
                        </a>
                        <a href="#tasks" className="flex flex-col items-center text-gray-400 hover:text-gold-400 text-[10px] font-semibold">
                            <span className="text-base">📋</span>
                            <span>Tasks</span>
                        </a>
                        <a href="#projects" className="flex flex-col items-center text-gray-400 hover:text-gold-400 text-[10px] font-semibold">
                            <span className="text-base">📊</span>
                            <span>Projects</span>
                        </a>
                        <a href="#more" className="flex flex-col items-center text-gray-400 hover:text-gold-400 text-[10px] font-semibold">
                            <span className="text-base">⚙️</span>
                            <span>More</span>
                        </a>
                    </div>

                    <!-- TASK EDIT / CREATE MODAL -->
                    {isAddModalOpen && (
                        <div className="fixed inset-0 z-50 bg-black/80 backdrop-blur-sm flex items-center justify-center p-4">
                            <div className="bg-dark-card border border-gold-500/30 rounded-3xl p-6 max-w-lg w-full space-y-4 max-h-[90vh] overflow-y-auto">
                                <div className="flex justify-between items-center border-b border-neutral-800 pb-3">
                                    <h3 className="text-base font-bold text-white">
                                        {editingTask ? '✏️ EDIT TASK' : '＋ ADD NEW TASK'}
                                    </h3>
                                    <button onClick={() => setIsAddModalOpen(false)} className="text-gray-400 hover:text-white text-lg">✕</button>
                                </div>

                                <form onSubmit={(e) => {
                                    e.preventDefault();
                                    const formData = new FormData(e.target);
                                    handleSaveTask({
                                        id: editingTask ? editingTask.id : null,
                                        name: formData.get('name'),
                                        category: formData.get('category'),
                                        project: formData.get('project'),
                                        priority: formData.get('priority'),
                                        importance: Number(formData.get('importance')),
                                        urgency: Number(formData.get('urgency')),
                                        estimatedMinutes: Number(formData.get('estimatedMinutes')),
                                        deadline: formData.get('deadline'),
                                        dependencyId: formData.get('dependencyId') || null,
                                        notes: formData.get('notes'),
                                        isProtected: formData.get('isProtected') === 'on',
                                        status: editingTask ? editingTask.status : 'Not Started'
                                    });
                                }} className="space-y-3 text-xs">

                                    <div>
                                        <label className="text-gray-300 block mb-1 font-semibold">Task Name *</label>
                                        <input 
                                            type="text" 
                                            name="name" 
                                            defaultValue={editingTask?.name || ''} 
                                            required 
                                            className="w-full bg-dark-bg border border-neutral-700 rounded-xl p-2.5 text-white focus:outline-none focus:border-gold-500"
                                        />
                                    </div>

                                    <div className="grid grid-cols-2 gap-3">
                                        <div>
                                            <label className="text-gray-300 block mb-1 font-semibold">Category</label>
                                            <select name="category" defaultValue={editingTask?.category || 'Career'} className="w-full bg-dark-bg border border-neutral-700 rounded-xl p-2.5 text-white">
                                                <option value="Career">Career</option>
                                                <option value="Courses">Courses</option>
                                                <option value="US Visa">US Visa</option>
                                                <option value="Relationship">Relationship</option>
                                                <option value="Personal">Personal</option>
                                                <option value="Family">Family</option>
                                                <option value="Business">Business</option>
                                                <option value="Finance">Finance</option>
                                            </select>
                                        </div>

                                        <div>
                                            <label className="text-gray-300 block mb-1 font-semibold">Project</label>
                                            <select name="project" defaultValue={editingTask?.project || 'Career'} className="w-full bg-dark-bg border border-neutral-700 rounded-xl p-2.5 text-white">
                                                <option value="Career">Career</option>
                                                <option value="Courses">Courses</option>
                                                <option value="US Visa">US Visa</option>
                                                <option value="Driving">Driving</option>
                                                <option value="Mariner Wealth Pro">Mariner Wealth Pro</option>
                                                <option value="Finance">Finance</option>
                                                <option value="Personal / Family">Personal / Family</option>
                                            </select>
                                        </div>
                                    </div>

                                    <div className="grid grid-cols-3 gap-3">
                                        <div>
                                            <label className="text-gray-300 block mb-1 font-semibold">Importance (10-40)</label>
                                            <input type="number" name="importance" defaultValue={editingTask?.importance || 30} min="10" max="40" className="w-full bg-dark-bg border border-neutral-700 rounded-xl p-2 text-white font-mono" />
                                        </div>
                                        <div>
                                            <label className="text-gray-300 block mb-1 font-semibold">Urgency (10-40)</label>
                                            <input type="number" name="urgency" defaultValue={editingTask?.urgency || 30} min="10" max="40" className="w-full bg-dark-bg border border-neutral-700 rounded-xl p-2 text-white font-mono" />
                                        </div>
                                        <div>
                                            <label className="text-gray-300 block mb-1 font-semibold">Est. Mins</label>
                                            <input type="number" name="estimatedMinutes" defaultValue={editingTask?.estimatedMinutes || 45} className="w-full bg-dark-bg border border-neutral-700 rounded-xl p-2 text-white font-mono" />
                                        </div>
                                    </div>

                                    <div className="grid grid-cols-2 gap-3">
                                        <div>
                                            <label className="text-gray-300 block mb-1 font-semibold">Deadline</label>
                                            <input type="date" name="deadline" defaultValue={editingTask?.deadline || ''} className="w-full bg-dark-bg border border-neutral-700 rounded-xl p-2 text-white" />
                                        </div>

                                        <div>
                                            <label className="text-gray-300 block mb-1 font-semibold">Prerequisite Task</label>
                                            <select name="dependencyId" defaultValue={editingTask?.dependencyId || ''} className="w-full bg-dark-bg border border-neutral-700 rounded-xl p-2 text-white">
                                                <option value="">None</option>
                                                {tasks.filter(t => !editingTask || t.id !== editingTask.id).map(t => (
                                                    <option key={t.id} value={t.id}>{t.name}</option>
                                                ))}
                                            </select>
                                        </div>
                                    </div>

                                    <div>
                                        <label className="text-gray-300 block mb-1 font-semibold">Notes / Reason</label>
                                        <textarea name="notes" rows="2" defaultValue={editingTask?.notes || ''} className="w-full bg-dark-bg border border-neutral-700 rounded-xl p-2.5 text-white"></textarea>
                                    </div>

                                    <label className="flex items-center space-x-2 pt-1 cursor-pointer">
                                        <input type="checkbox" name="isProtected" defaultChecked={editingTask?.isProtected || false} className="accent-gold-500 w-4 h-4 rounded" />
                                        <span className="text-rose-400 font-bold">❤️ Mark as Protected Time (Girlfriend / Family)</span>
                                    </label>

                                    <div className="flex justify-end space-x-2 pt-3">
                                        <button type="button" onClick={() => setIsAddModalOpen(false)} className="px-4 py-2 rounded-xl bg-dark-bg text-gray-300 hover:text-white">Cancel</button>
                                        <button type="submit" className="gold-gradient-bg text-black font-bold px-5 py-2 rounded-xl">Save Task</button>
                                    </div>
                                </form>
                            </div>
                        </div>
                    )}

                    <!-- POMODORO TIMER OVERLAY MODAL -->
                    {timerModalOpen && timerTask && (
                        <div className="fixed inset-0 z-50 bg-black/85 backdrop-blur-md flex items-center justify-center p-4">
                            <div className="bg-dark-card border border-gold-500/40 rounded-3xl p-6 max-w-sm w-full text-center space-y-5 gold-glow">
                                <div className="flex justify-between items-center">
                                    <span className="text-xs font-bold text-gold-400 uppercase tracking-wider">FOCUS TIMER</span>
                                    <button onClick={() => setTimerModalOpen(false)} className="text-gray-400 hover:text-white">✕</button>
                                </div>

                                <div>
                                    <h3 className="text-base font-bold text-white line-clamp-2">{timerTask.name}</h3>
                                    <p className="text-xs text-gray-400 mt-0.5">{timerTask.category}</p>
                                </div>

                                <div className="text-5xl font-black font-mono text-gold-400 tracking-wider py-4 bg-dark-bg rounded-2xl border border-neutral-800">
                                    {Math.floor(timerSeconds / 60).toString().padStart(2, '0')}:{(timerSeconds % 60).toString().padStart(2, '0')}
                                </div>

                                <div className="flex justify-center space-x-3">
                                    <button 
                                        onClick={() => setTimerActive(!timerActive)}
                                        className="gold-gradient-bg text-black font-bold px-6 py-2 rounded-xl text-xs"
                                    >
                                        {timerActive ? 'PAUSE' : 'START'}
                                    </button>
                                    <button 
                                        onClick={() => handleToggleTaskComplete(timerTask.id)}
                                        className="bg-emerald-600/20 border border-emerald-500/40 text-emerald-400 font-bold px-4 py-2 rounded-xl text-xs"
                                    >
                                        ✓ Complete
                                    </button>
                                </div>
                            </div>
                        </div>
                    )}

                </div>
            );
        }

        <!-- Render App to DOM -->
        ReactDOM.createRoot(document.getElementById('root')).render(<App />);
    </script>
</body>
</html>
```
