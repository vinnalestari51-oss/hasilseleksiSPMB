<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hasil Tes Kemampuan Akademik 2026 - SMPN 1 Lingga</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    
    <style>
        /* --- RESET & GLOBAL STYLES --- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Plus Jakarta Sans', sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background-color: #f0f7ff;
            color: #1e293b;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* --- CONTAINER MOBILE-FIRST (MAX 440PX) --- */
        .container-mobile {
            width: 100%;
            max-width: 440px;
            min-height: 100vh;
            background-color: #f8fafc;
            position: relative;
            padding: 24px 20px 100px 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.03);
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        /* --- UTILITY CLASS: MATERIAL 3 EXPRESSIVE GLASS --- */
        .m3-glass {
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.9);
            border-radius: 24px;
            padding: 20px;
            box-shadow: 0 8px 32px rgba(31, 38, 135, 0.04);
        }

        /* --- HEADER BRANDING --- */
        .header-brand {
            display: flex;
            align-items: center;
            gap: 14px;
            margin-bottom: 4px;
        }

        .header-brand .icon-edu {
            width: 48px;
            height: 48px;
            background: linear-gradient(135deg, #2563eb, #3b82f6);
            border-radius: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #ffffff;
            font-size: 20px;
            box-shadow: 0 4px 14px rgba(37, 99, 235, 0.2);
        }

        .header-brand h1 {
            font-size: 16px;
            font-weight: 800;
            color: #1e3a8a;
            line-height: 1.2;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .header-brand p {
            font-size: 11px;
            color: #64748b;
            font-weight: 500;
            margin-top: 2px;
        }

        /* --- APP PAGES STATE MANAGEMENT --- */
        .app-page {
            display: none;
            width: 100%;
            animation: fadeIn 0.4s ease-out;
        }

        .app-page.active {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(8px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* --- FIXED BOTTOM NAVBAR --- */
        .bottom-navbar {
            position: fixed;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 100%;
            max-width: 440px;
            height: 72px;
            background: rgba(255, 255, 255, 0.92);
            backdrop-filter: blur(15px);
            -webkit-backdrop-filter: blur(15px);
            border-top: 1px solid rgba(226, 232, 240, 0.8);
            display: flex;
            justify-content: space-around;
            align-items: center;
            z-index: 999;
            padding: 0 12px;
        }

        .nav-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 6px;
            background: none;
            border: none;
            cursor: pointer;
            width: 64px;
            height: 100%;
            color: #64748b;
            transition: all 0.25s ease;
            position: relative;
        }

        .nav-item i {
            font-size: 20px;
            transition: transform 0.2s ease;
        }

        .nav-item span {
            font-size: 11px;
            font-weight: 600;
            letter-spacing: 0.2px;
        }

        .nav-item.active {
            color: #2563eb;
        }

        .nav-item.active i {
            transform: translateY(-2px);
        }

        .nav-item.active::after {
            content: '';
            position: absolute;
            top: 0;
            width: 28px;
            height: 4px;
            background-color: #2563eb;
            border-radius: 0 0 4px 4px;
        }

        /* --- KONTEN LAMAN: HOME (STATISTIK ANONIM) --- */
        .stats-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 12px;
        }

        .stat-card {
            background: #ffffff;
            border-radius: 20px;
            padding: 16px;
            border: 1px solid #e2e8f0;
            display: flex;
            flex-direction: column;
            gap: 6px;
        }

        .stat-card .label {
            font-size: 11px;
            font-weight: 600;
            color: #64748b;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .stat-card .value {
            font-size: 24px;
            font-weight: 800;
            color: #1e293b;
        }

        .section-title {
            font-size: 14px;
            font-weight: 700;
            color: #334155;
            margin-bottom: 4px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        /* CUSTOM CSS MANUAL PROGRESS BAR (GRAFIK DISTRIBUSI) */
        .chart-group {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-top: 8px;
        }

        .chart-row {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }

        .chart-label-container {
            display: flex;
            justify-content: space-between;
            font-size: 11px;
            font-weight: 600;
            color: #475569;
        }

        .bar-container {
            width: 100%;
            height: 10px;
            background: #e2e8f0;
            border-radius: 10px;
            overflow: hidden;
        }

        .bar-fill {
            height: 100%;
            border-radius: 10px;
            transition: width 1s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .bar-baik { background: linear-gradient(90deg, #10b981, #34d399); }
        .bar-memadai { background: linear-gradient(90deg, #3b82f6, #60a5fa); }
        .bar-kurang { background: linear-gradient(90deg, #f59e0b, #fbbf24); }

        /* --- KONTEN LAMAN: NILAIKU (PENCARIAN AMPLUP) --- */
        .search-box {
            display: flex;
            flex-direction: column;
            gap: 14px;
        }

        .search-title {
            font-size: 15px;
            font-weight: 700;
            color: #1e3a8a;
            text-align: center;
            line-height: 1.4;
        }

        .input-wrapper {
            position: relative;
            width: 100%;
        }

        .input-wrapper i {
            position: absolute;
            left: 16px;
            top: 50%;
            transform: translateY(-50%);
            color: #94a3b8;
            font-size: 16px;
        }

        .input-nisn {
            width: 100%;
            height: 54px;
            background: #ffffff;
            border: 2px solid #e2e8f0;
            border-radius: 16px;
            padding: 0 16px 0 46px;
            font-size: 15px;
            font-weight: 600;
            color: #1e293b;
            outline: none;
            transition: all 0.2s ease;
        }

        .input-nisn:focus {
            border-color: #2563eb;
            box-shadow: 0 0 0 4px rgba(37, 99, 235, 0.1);
        }

        .btn-search {
            width: 100%;
            height: 52px;
            background: linear-gradient(135deg, #1e3a8a, #2563eb);
            border: none;
            border-radius: 16px;
            color: #ffffff;
            font-size: 15px;
            font-weight: 700;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            box-shadow: 0 4px 12px rgba(37, 99, 235, 0.2);
            transition: transform 0.1s ease, opacity 0.2s;
        }

        .btn-search:active {
            transform: scale(0.98);
        }

        /* --- ANIMASI LOADING DRAMATIS --- */
        .loading-container {
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 40px 20px;
            gap: 16px;
        }

        .spinner {
            width: 48px;
            height: 48px;
            border: 5px solid rgba(37, 99, 235, 0.1);
            border-top-color: #2563eb;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        .pulse-text {
            font-size: 13px;
            font-weight: 600;
            color: #2563eb;
            animation: pulse 1.2s infinite ease-in-out;
        }

        @keyframes spin { to { transform: rotate(360deg); } }
        @keyframes pulse {
            0%, 100% { opacity: 0.6; transform: scale(0.98); }
            50% { opacity: 1; transform: scale(1.02); }
        }

        /* --- SURPRISE BOUNCE EFFECT CARD --- */
        .result-envelope {
            display: none;
            width: 100%;
        }

        .result-card {
            width: 100%;
            border-radius: 24px;
            padding: 24px;
            display: flex;
            flex-direction: column;
            gap: 18px;
            position: relative;
            overflow: hidden;
            animation: surpriseBounce 0.65s cubic-bezier(0.175, 0.885, 0.32, 1.275) both;
        }

        @keyframes surpriseBounce {
            0% { opacity: 0; transform: scale(0.4) translateY(120px); }
            70% { transform: scale(1.05) translateY(-8px); }
            100% { opacity: 1; transform: scale(1) translateY(0); }
        }

        /* --- THEME VARIATION RANK KARTU INDIVIDU --- */
        
        /* RANK 1: GRADASI HIJAU PASTEL + SHIMMER EFFECT */
        .card-rank-1 {
            background: linear-gradient(135deg, #d1fae5, #a7f3d0);
            border: 3px solid #34d399;
            box-shadow: 0 12px 24px rgba(52, 211, 153, 0.25);
            background-size: 200% 200%;
            animation: surpriseBounce 0.65s cubic-bezier(0.175, 0.885, 0.32, 1.275) both, shimmerBackground 4s ease infinite;
        }
        @keyframes shimmerBackground {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* RANK 2: GRADASI BIRU PASTEL */
        .card-rank-2 {
            background: linear-gradient(135deg, #dbaefe, #bfdbfe);
            border: 2px solid #60a5fa;
            box-shadow: 0 10px 20px rgba(96, 165, 250, 0.2);
        }

        /* RANK 3: GRADASI ORANYE PASTEL WARM */
        .card-rank-3 {
            background: linear-gradient(135deg, #ffedd5, #fdbb74);
            border: 2px solid #fb923c;
            box-shadow: 0 10px 20px rgba(251, 146, 60, 0.2);
        }

        /* RANK GENERAL (4 KE BAWAH) */
        .card-rank-general {
            background: rgba(255, 255, 255, 0.9);
            border: 1px solid #e2e8f0;
            box-shadow: 0 8px 24px rgba(0, 0, 0, 0.02);
        }

        /* CARD ELEMENTS LAYOUT */
        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            border-bottom: 1px dashed rgba(0,0,0
