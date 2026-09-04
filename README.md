<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AMA-fitness | النظام التدريبي الذكي</title>
    <style>
        :root {
            --bg-color: #f4f6fb;
            --panel-bg: #ffffff;
            --accent-blue: #0056ff;
            --accent-blue-glow: rgba(0, 86, 255, 0.35);
            --accent-cyan: #00c6ff;
            --text-main: #121526;
            --text-secondary: #5a627d;
            --border-color: #dbe4ef;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            margin: 0;
            padding: 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .container { width: 100%; max-width: 550px; }
        
        /* الثيم والنار الزرقاء الفخمة */
        .brand-header {
            text-align: center;
            margin-bottom: 25px;
            padding: 22px;
            background: linear-gradient(135deg, #ffffff, #f0f4ff);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 86, 255, 0.1);
        }
        .brand-logo {
            width: 75px; height: 75px;
            background: linear-gradient(135deg, var(--accent-blue), var(--accent-cyan));
            border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            margin: 0 auto 12px;
            font-size: 35px;
            box-shadow: 0 0 20px var(--accent-blue-glow);
            animation: pulseGlow 2s infinite alternate;
        }
        @keyframes pulseGlow {
            0% { box-shadow: 0 0 10px rgba(0, 86, 255, 0.3); }
            100% { box-shadow: 0 0 25px rgba(0, 198, 255, 0.8); }
        }
        .brand-header h1 { color: var(--accent-blue); margin: 0; font-size: 1.6em; text-shadow: 0 0 10px var(--accent-blue-glow); }
        .brand-header p { color: var(--text-secondary); margin: 5px 0 0; font-size: 0.9em; }

        h2 { color: var(--accent-blue); font-size: 1.15em; border-bottom: 2px solid var(--border-color); padding-bottom: 8px; margin-top: 0; display: flex; align-items: center; gap: 8px; }
        
        .card {
            background-color: var(--panel-bg);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 8px 25px rgba(0, 86, 255, 0.05);
            transition: 0.3s;
        }
        .card:hover { box-shadow: 0 12px 35px rgba(0, 86, 255, 0.1); }

        label { display: block; margin-top: 12px; color: var(--text-secondary); font-size: 0.88em; font-weight: 600; }
        select, input {
            width: 100%; padding: 12px; margin-top: 6px; border-radius: 10px;
            border: 1px solid var(--border-color);
            background-color: #fafbfc; color: var(--text-main);
            box-sizing: border-box; font-family: inherit; font-size: 1em;
            transition: all 0.3s ease;
        }
        select:focus, input:focus { outline: none; border-color: var(--accent-blue); box-shadow: 0 0 12px var(--accent-blue-glow); background-color: #fff; }
        
        .row { display: flex; gap: 10px; }
        .col { flex: 1; }

        /* الأزرار الفخمة البراقة */
        button {
            width: 100%; padding: 14px; margin-top: 20px; border-radius: 12px;
            background: linear-gradient(135deg, #0056ff, #00c6ff); color: #fff;
            font-weight: bold; font-size: 1.05em; cursor: pointer; border: none;
            transition: all 0.3s ease; box-shadow: 0 6px 20px var(--accent-blue-glow);
        }
        button:hover { opacity: 0.95; transform: translateY(-2px); box-shadow: 0 8px 25px rgba(0, 198, 255, 0.5); }
        
        .exercise-info {
            background: rgba(0, 86, 255, 0.03);
            border: 1px dashed var(--accent-blue);
            padding: 12px; border-radius: 10px; margin-top: 12px; font-size: 0.9em; color: var(--accent-blue);
            line-height: 1.6;
        }

        .recommendation-box {
            background: rgba(0, 198, 255, 0.08);
            border: 1px solid var(--accent-cyan);
            color: #0044cc;
            padding: 12px; border-radius: 10px; margin-top: 12px; font-size: 0.88em; font-weight: bold; display: none;
        }

        .calendar-grid {
            display: grid; grid-template-columns: repeat(7, 1fr); gap: 6px; margin-top: 15px;
        }
        .day {
            background-color: #f4f6fb; border: 1px solid var(--border-color);
            border-radius: 8px; text-align: center; padding: 10px 0; font-size: 12px;
            color: var(--text-secondary); min-height: 48px; display: flex; flex-direction: column; justify-content: center; align-items: center;
        }
        .day.workout { background: linear-gradient(135deg, rgba(0, 86, 255, 0.15), rgba(0, 198, 255, 0.25)); border-color: var(--accent-blue); color: var(--accent-blue); font-weight: bold; }
        .day.rest { background-color: #edf1f7; }

        .stats-box { display: flex; justify-content: space-between; margin-top: 10px; gap: 6px; }
        .stat-item { text-align: center; background: #fafbfc; padding: 12px 6px; border-radius: 10px; flex: 1; border: 1px solid var(--border-color); font-size: 0.85em; }
        .stat-item span { display: block; color: var(--accent-blue); font-size: 1.1em; font-weight: bold; margin-top: 4px; }
        
        .reward-banner {
            text-align: center; background: linear-gradient(135deg, #0056ff, #00c6ff);
            color: #fff; padding: 14px; border-radius: 12px; font-weight: bold; margin-top: 15px; display: none;
            box-shadow: 0 6px 20px var(--accent-blue-glow);
        }
        .share-btn { background: linear-gradient(135deg, #00b894, #55efc4); box-shadow: 0 6px 20px rgba(0, 184, 148, 0.3); }
        
        .badge-target {
            display: inline-block; background: rgba(0, 86, 255, 0.1); color: var(--accent-blue);
            padding: 8px 12px; border-radius: 20px; font-size: 0.85em; font-weight: bold; margin-top: 10px; text-align: center; width: 100%; box-sizing: border-box;
        }
    </style>
</head>
<body>

<div class="container">
    <!-- شعار واسم التطبيق AMA-fitness -->
    <div class="brand-header">
        <div class="brand-logo">⚡</div>
        <h1>AMA-fitness</h1>
        <p>النظام التدريبي والبيولوجي المتقدم</p>
    </div>

    <!-- الملف الشخصي والهدف -->
    <div class="card">
        <h2>👤 الملف الشخصي والهدف</h2>
        <div class="row">
            <div class="col">
                <label>الاسم:</label>
                <input type="text" id="userName" placeholder="اسم البطل" oninput="saveProfileData()">
            </div>
            <div class="col">
                <label>الطول (سم):</label>
                <input type="number" id="userHeight" placeholder="مثال: 178" oninput="saveProfileData()">
            </div>
        </div>
        <div class="row">
            <div class="col">
                <label>الوزن الحالي (كجم):</label>
                <input type="number" id="userCurrentWeight" placeholder="مثال: 75" oninput="saveProfileData()">
            </div>
            <div class="col">
                <label>الهدف:</label>
                <select id="userGoal" onchange="saveProfileData()">
                    <option value="gain">📈 زيادة الوزن (تضخيم)</option>
                    <option value="lose">📉 نقصان الوزن (تنشيف)</option>
                    <option value="maintain">⚖️ الحفاظ على الوزن</option>
                </select>
            </div>
        </div>
        <div id="targetVerdict" class="badge-target">أدخل بياناتك لمتابعة تقدمك نحو الهدف.</div>
    </div>

    <!-- تسجيل الحديد -->
    <div class="card">
        <h2>🏋️‍♂️ تسجيل التمارين والأوزان</h2>
        
        <label>اختر اليوم التدريبي:</label>
        <select id="workoutDaySelect" onchange="updateExerciseList()">
            <option value="1">اليوم الأول (السبت)</option>
            <option value="2">اليوم الثاني (الإثنين)</option>
            <option value="3">اليوم الثالث (الأربعاء)</option>
        </select>

        <label>اختر التمرين:</label>
        <select id="exerciseSelect" onchange="showExerciseDetails()"></select>

        <div class="exercise-info" id="exDetailsBox">تفاصيل التمرين.</div>

        <div class="row">
            <div class="col">
                <label>الوزن (كجم):</label>
                <input type="number" id="exWeight" placeholder="مثال: 50">
            </div>
            <div class="col">
                <label>العدادت الفعلية:</label>
                <input type="number" id="exReps" placeholder="مثال: 10">
            </div>
        </div>

        <div class="recommendation-box" id="recBox">💡 توصية الحمل التدريجي...</div>

        <!-- قسم الكارديو -->
        <h3 style="margin-top: 25px; font-size: 1.05em; color: var(--accent-blue);">🏃‍♂️ قسم الكارديو وحرق الدهون</h3>
        <div class="row">
            <div class="col">
                <label>نوع الكارديو:</label>
                <select id="cardioType">
                    <option value="مشي سريع مائل">مشي سريع مائل (Incline Treadmill)</option>
                    <option value="جري خفيف">جري خفيف (Jogging)</option>
                    <option value="دراجة ثابتة">دراجة ثابتة (Stationary Bike)</option>
                    <option value="نط حبل">نط حبل (Jump Rope)</option>
                </select>
            </div>
            <div class="col">
                <label>المدة (دقيقة):</label>
                <input type="number" id="cardioMins" placeholder="مثال: 20">
            </div>
        </div>

        <h3 style="margin-top: 20px; font-size: 1.05em; color: var(--text-main);">💤 الاستشفاء والسعرات</h3>
        <div class="row">
            <div class="col">
                <label>النوم:</label>
                <input type="time" id="sleepTime" value="23:00">
            </div>
            <div class="col">
                <label>الاستيقاظ:</label>
                <input type="time" id="wakeTime" value="07:00">
            </div>
        </div>

        <label>السعرات الحرارية:</label>
        <input type="number" id="calories" placeholder="مثال: 2700">

        <button onclick="saveWorkoutLog()">حفظ السجل الفخم</button>
        <div class="reward-banner" id="rewardBanner">⚡ أداء ناري وراقي! تم تسجيل التمرين بنجاح في AMA-fitness!</div>
    </div>

    <!-- التقويم -->
    <div class="card">
        <h2>📅 تقويم الإنجاز</h2>
        <div class="calendar-grid" id="calendarGrid"></div>
    </div>

    <!-- التقييم -->
    <div class="card">
        <h2>📊 التقييم الذكي</h2>
        <div class="stats-box">
            <div class="stat-item">الجلسات<span><b id="statWorkouts">0</b> جلسة</span></div>
            <div class="stat-item">متوسط النوم<span><b id="statSleep">0</b> س</span></div>
            <div class="stat-item">السعرات<span><b id="statCals">0</b> kcal</span></div>
        </div>
        <p style="text-align: center; color: var(--text-secondary); margin-top: 15px; font-size: 0.9em;" id="monthlyVerdict">
            سجل أول تمرين لمتابعة تطورك.
        </p>
    </div>

    <div class="card" style="text-align: center;">
        <h2>🌐 مشاركة</h2>
        <button class="share-btn" onclick="shareWithFriends()">مشاركة عبر واتساب</button>
    </div>
</div>

<script>
    // جداولك التدريبية الدقيقة تماماً
    const workoutSchedule = {
        "1": [
            { name: "Smith Bench Press", sets: 3, reps: "6–10", rir: "2" },
            { name: "Lat Pulldown", sets: 3, reps: "8–12", rir: "2" },
            { name: "Leg Press", sets: 3, reps: "8–12", rir: "2" },
            { name: "Incline DB Press", sets: 2, reps: "8–12", rir: "1–2" },
            { name: "Seated Cable Row", sets: 2, reps: "8–12", rir: "1–2" },
            { name: "Lateral Raise", sets: 3, reps: "12–20", rir: "1–2" },
            { name: "Cable Curl", sets: 2, reps: "10–15", rir: "1" },
            { name: "Triceps Pushdown", sets: 2, reps: "10–15", rir: "1" }
        ],
        "2": [
            { name: "Hack Squat", sets: 3, reps: "6–10", rir: "2" },
            { name: "Romanian Deadlift", sets: 3, reps: "6–10", rir: "2" },
            { name: "Machine Shoulder Press", sets: 3, reps: "6–10", rir: "1–2" },
            { name: "Chest-Supported Row", sets: 3, reps: "8–12", rir: "1–2" },
            { name: "Machine Chest Press", sets: 2, reps: "8–12", rir: "1–2" },
            { name: "Leg Curl", sets: 2, reps: "10–15", rir: "1" },
            { name: "Lateral Raise", sets: 3, reps: "12–20", rir: "1" },
            { name: "Incline DB Curl", sets: 2, reps: "8–12", rir: "1" },
            { name: "Overhead Triceps Extension", sets: 2, reps: "8–12", rir: "1" }
        ],
        "3": [
            { name: "Incline Smith/Machine Press", sets: 3, reps: "6–10", rir: "2" },
            { name: "Pull-up / Lat Pulldown", sets: 3, reps: "8–12", rir: "1–2" },
            { name: "Leg Extension", sets: 3, reps: "10–15", rir: "1" },
            { name: "Seated Leg Curl", sets: 3, reps: "10–15", rir: "1" },
            { name: "Cable Row", sets: 3, reps: "8–12", rir: "1–2" },
            { name: "Cable/Machine Fly", sets: 2, reps: "10–15", rir: "1" },
            { name: "Lateral Raise", sets: 3, reps: "12–20", rir: "1" },
            { name: "DB Curl", sets: 3, reps: "8–12", rir: "1" },
            { name: "Triceps Pushdown", sets: 3, reps: "8–12", rir: "1–2" }
        ]
    };

    let userLogs = JSON.parse(localStorage.getItem('AMA_fitness_logs_v4')) || [];
    let userProfile = JSON.parse(localStorage.getItem('AMA_fitness_profile_v4')) || { name: '', height: '', weight: '', goal: 'gain' };

    function loadProfileToUI() {
        if(userProfile.name) document.getElementById('userName').value = userProfile.name;
        if(userProfile.height) document.getElementById('userHeight').value = userProfile.height;
        if(userProfile.weight) document.getElementById('userCurrentWeight').value = userProfile.weight;
        if(userProfile.goal) document.getElementById('userGoal').value = userProfile.goal;
        updateTargetVerdict();
    }

    function saveProfileData() {
        userProfile.name = document.getElementById('userName').value;
        userProfile.height = document.getElementById('userHeight').value;
        userProfile.weight = document.getElementById('userCurrentWeight').value;
        userProfile.goal = document.getElementById('userGoal').value;
        localStorage.setItem('AMA_fitness_profile_v4', JSON.stringify(userProfile));
        updateTargetVerdict();
    }

    function updateTargetVerdict() {
        const targetBox = document.getElementById('targetVerdict');
        let goalText = userProfile.goal === 'gain' ? "هدف: زيادة الوزن وتضخيم عضلات 📈" : (userProfile.goal === 'lose' ? "هدف: نقصان الوزن وتنشيف الدهون 📉" : "هدف: الحفاظ على اللياقة البدنية ⚖️");
        let namePart = userProfile.name ? `البطل: ${userProfile.name} | ` : "";
        targetBox.innerHTML = `${namePart}${goalText}`;
    }

    function updateExerciseList() {
        const dayVal = document.getElementById('workoutDaySelect').value;
        const exSelect = document.getElementById('exerciseSelect');
        exSelect.innerHTML = '';
        
        workoutSchedule[dayVal].forEach((ex, idx) => {
            let opt = document.createElement('option');
            opt.value = idx;
            opt.textContent = `${ex.name} (جولات: ${ex.sets} | عدات: ${ex.reps} | RIR: ${ex.rir})`;
            exSelect.appendChild(opt);
        });
        showExerciseDetails();
    }

    function showExerciseDetails() {
        const dayVal = document.getElementById('workoutDaySelect').value;
        const exIdx = document.getElementById('exerciseSelect').value;
        if(exIdx === "") return;
        
        const ex = workoutSchedule[dayVal][exIdx];
        let lastRecord = userLogs.slice().reverse().find(l => l.exerciseName === ex.name);
        
        let recText = "هذه أول مرة تسجل هذا التمرين. استهدف النطاق المطلوب.";
        let showRec = false;

        if(lastRecord) {
            showRec = true;
            recText = `⚡ سجلت سابقاً ${lastRecord.weight} كجم بـ ${lastRecord.reps} عدات. استمر بالتطور التدريجي!`;
        }

        document.getElementById('exDetailsBox').innerHTML = 
            `🏋️‍♂️ التمرين: <b>${ex.name}</b><br>• الجولات: <b>${ex.sets}</b> | نطاق العدات: <b>${ex.reps}</b> | RIR المستهدف: <b>${ex.rir}</b>`;
        
        const recBox = document.getElementById('recBox');
        if(showRec) {
            recBox.style.display = 'block';
            recBox.innerHTML = recText;
        } else {
            recBox.style.display = 'none';
        }
    }

    function saveWorkoutLog() {
        const dayVal = document.getElementById('workoutDaySelect').value;
        const exIdx = document.getElementById('exerciseSelect').value;
        const ex = workoutSchedule[dayVal][exIdx];

        const weight = parseFloat(document.getElementById('exWeight').value) || 0;
        const reps = parseInt(document.getElementById('exReps').value) || 0;
        const cardioType = document.getElementById('cardioType').value;
        const cardioMins = parseInt(document.getElementById('cardioMins').value) || 0;
        const sleepTime = document.getElementById('sleepTime').value;
        const wakeTime = document.getElementById('wakeTime').value;
        const calories = parseInt(document.getElementById('calories').value) || 0;

        let sleepHours = 8;
        if(sleepTime && wakeTime) {
            let [sH, sM] = sleepTime.split(':').map(Number);
            let [wH, wM] = wakeTime.split(':').map(Number);
            let diff = (wH * 60 + wM) - (sH * 60 + sM);
            if(diff < 0) diff += 24 * 60;
            sleepHours = parseFloat((diff / 60).toFixed(1));
        }

        let entry = {
            exerciseName: ex.name,
            weight,
            reps,
            cardioType,
            cardioMins,
            sleepHours,
            calories,
            date: new Date().toLocaleDateString()
        };

        userLogs.push(entry);
        localStorage.setItem('AMA_fitness_logs_v4', JSON.stringify(userLogs));

        const banner = document.getElementById('rewardBanner');
        banner.style.display = 'block';
        setTimeout(() => banner.style.display = 'none', 3500);

        updateExerciseList();
        renderDashboard();
    }

    function renderDashboard() {
        const grid = document.getElementById('calendarGrid');
        grid.innerHTML = '';
        
        for(let i=0; i<14; i++) {
            let dDiv = document.createElement('div');
            dDiv.classList.add('day');
            if(userLogs[i]) {
                dDiv.classList.add('workout');
                dDiv.innerHTML = `⚡<br><span style="font-size:7px">${userLogs[i].exerciseName.substring(0,5)}</span>`;
            } else {
                dDiv.classList.add('rest');
                dDiv.innerHTML = '💤';
            }
            grid.appendChild(dDiv);
        }

        if(userLogs.length > 0) {
            let totalWorkouts = userLogs.length;
            let totalSleep = userLogs.reduce((acc, l) => acc + l.sleepHours, 0);
            let totalCals = userLogs.reduce((acc, l) => acc + l.calories, 0);

            document.getElementById('statWorkouts').innerText = totalWorkouts;
            document.getElementById('statSleep').innerText = (totalSleep / totalWorkouts).toFixed(1);
            document.getElementById('statCals').innerText = Math.round(totalCals / totalWorkouts);
            document.getElementById('monthlyVerdict').innerText = "التقييم: أداء ناري فخم ومنتظم! واصل التطور ⚡🔥";
        }
    }

    function shareWithFriends() {
        const text = "تطبيق AMA-fitness للنظام التدريبي الذكي 🔥⚡";
        if (navigator.share) {
            navigator.share({ title: 'AMA-fitness', text: text, url: window.location.href });
        } else {
            prompt("انسخ الرابط لمشاركته:", window.location.href);
        }
    }

    window.onload = () => {
        loadProfileToUI();
        updateExerciseList();
        renderDashboard();
    };
</script>

</body>
</html>
