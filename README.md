<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pembelajaran Ikatan Kovalen - Storyboard Digital</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: #333;
            min-height: 100vh;
            padding: 20px;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.3);
            overflow: hidden;
            transform: translateY(0);
            animation: containerFloat 6s ease-in-out infinite;
        }

        @keyframes containerFloat {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .header {
            background: linear-gradient(135deg, #ff6b6b 0%, #ff8e8e 100%);
            color: white;
            padding: 30px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" width="100" height="100" opacity="0.1"><circle cx="50" cy="50" r="2" fill="white"/></svg>');
            animation: floatParticles 20s linear infinite;
        }

        @keyframes floatParticles {
            0% { transform: translateY(0) translateX(0); }
            100% { transform: translateY(-100px) translateX(20px); }
        }

        .header h1 {
            font-size: 2.8rem;
            margin-bottom: 15px;
            position: relative;
            z-index: 2;
            text-shadow: 0 2px 10px rgba(0,0,0,0.3);
            animation: titleGlow 3s ease-in-out infinite alternate;
        }

        @keyframes titleGlow {
            from { text-shadow: 0 0 10px rgba(255,255,255,0.5); }
            to { text-shadow: 0 0 20px rgba(255,255,255,0.8), 0 0 30px rgba(255, 107, 107, 0.6); }
        }

        .header-subtitle {
            font-size: 1.3rem;
            margin-bottom: 10px;
            position: relative;
            z-index: 2;
            opacity: 0.9;
        }

        .header-info {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 20px;
            margin-top: 20px;
            position: relative;
            z-index: 2;
        }

        .info-item {
            background: rgba(255, 255, 255, 0.15);
            padding: 10px 20px;
            border-radius: 25px;
            font-size: 0.9rem;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.2);
            animation: fadeInUp 0.8s ease-out;
        }

        .scene-container {
            display: none;
            padding: 30px;
            min-height: 550px;
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.5s ease;
        }

        .scene-container.active {
            display: block;
            opacity: 1;
            transform: translateY(0);
            animation: sceneAppear 0.6s ease-out;
        }

        @keyframes sceneAppear {
            0% { opacity: 0; transform: translateY(30px) scale(0.98); }
            100% { opacity: 1; transform: translateY(0) scale(1); }
        }

        .scene-title {
            color: #ff6b6b;
            border-bottom: 3px solid #4ecdc4;
            padding-bottom: 15px;
            margin-bottom: 25px;
            font-size: 2rem;
            position: relative;
            animation: fadeInLeft 0.8s ease-out;
        }

        .scene-title::after {
            content: "";
            position: absolute;
            bottom: -3px;
            left: 0;
            width: 100px;
            height: 3px;
            background: #ff6b6b;
            animation: titleUnderline 2s ease-in-out infinite alternate;
        }

        @keyframes titleUnderline {
            0% { width: 100px; }
            100% { width: 200px; }
        }

        .scene-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-bottom: 35px;
        }

        @media (max-width: 768px) {
            .scene-content {
                grid-template-columns: 1fr;
            }
        }

        .visual-section, .audio-section {
            background: white;
            padding: 25px;
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
            animation: cardAppear 0.8s ease-out;
            border: 1px solid rgba(255,255,255,0.8);
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
        }

        .visual-section:hover, .audio-section:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.15);
        }

        @keyframes cardAppear {
            0% { opacity: 0; transform: translateY(20px) scale(0.95); }
            100% { opacity: 1; transform: translateY(0) scale(1); }
        }

        .section-title {
            color: #ff6b6b;
            margin-bottom: 20px;
            font-size: 1.4rem;
            display: flex;
            align-items: center;
            gap: 12px;
            animation: fadeInLeft 0.8s ease-out 0.2s both;
        }

        .section-title i {
            background: #4ecdc4;
            color: white;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            animation: iconPulse 2s infinite;
        }

        @keyframes iconPulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        @keyframes fadeInLeft {
            0% { opacity: 0; transform: translateX(-30px); }
            100% { opacity: 1; transform: translateX(0); }
        }

        @keyframes fadeInUp {
            0% { opacity: 0; transform: translateY(30px); }
            100% { opacity: 1; transform: translateY(0); }
        }

        .controls {
            display: flex;
            justify-content: space-between;
            margin-top: 35px;
            padding-top: 25px;
            border-top: 2px solid #e9ecef;
            animation: fadeInUp 0.8s ease-out 0.4s both;
        }

        .btn {
            padding: 14px 28px;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.4s ease;
            display: flex;
            align-items: center;
            gap: 10px;
            position: relative;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        .btn::before {
            content: "";
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
            transition: left 0.5s;
        }

        .btn:hover::before {
            left: 100%;
        }

        .btn:disabled {
            background: #bdc3c7 !important;
            color: #7f8c8d !important;
            cursor: not-allowed;
            transform: none !important;
            box-shadow: 0 3px 8px rgba(0,0,0,0.1) !important;
        }

        .btn:disabled::before {
            display: none;
        }

        .btn-prev {
            background: linear-gradient(135deg, #45b7d1 0%, #4ecdc4 100%);
            color: white;
        }

        .btn-next {
            background: linear-gradient(135deg, #ff6b6b 0%, #ff8e8e 100%);
            color: white;
        }

        .btn-save {
            background: linear-gradient(135deg, #96ceb4 0%, #7ac5a8 100%);
            color: white;
        }

        .btn-restart {
            background: linear-gradient(135deg, #ffa726 0%, #ff9800 100%);
            color: white;
        }

        .btn-prev:hover:not(:disabled) {
            background: linear-gradient(135deg, #4ecdc4 0%, #45b7d1 100%);
            transform: translateX(-5px) scale(1.05);
            box-shadow: 0 8px 20px rgba(69, 183, 209, 0.4);
        }

        .btn-next:hover:not(:disabled) {
            background: linear-gradient(135deg, #ff8e8e 0%, #ff6b6b 100%);
            transform: translateX(5px) scale(1.05);
            box-shadow: 0 8px 20px rgba(255, 107, 107, 0.4);
        }

        .btn-save:hover:not(:disabled) {
            background: linear-gradient(135deg, #7ac5a8 0%, #96ceb4 100%);
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 8px 20px rgba(122, 197, 168, 0.4);
        }

        .btn-restart:hover:not(:disabled) {
            background: linear-gradient(135deg, #ff9800 0%, #ffa726 100%);
            transform: scale(1.05);
            box-shadow: 0 8px 20px rgba(255, 152, 0, 0.4);
        }

        .tips-box {
            background: linear-gradient(135deg, #4ecdc4 0%, #45b7d1 100%);
            color: white;
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 25px;
            animation: pulseGlow 3s infinite;
            box-shadow: 0 8px 20px rgba(78, 205, 196, 0.3);
            position: relative;
            overflow: hidden;
        }

        @keyframes pulseGlow {
            0%, 100% { box-shadow: 0 8px 20px rgba(78, 205, 196, 0.3); }
            50% { box-shadow: 0 8px 30px rgba(78, 205, 196, 0.6); }
        }

        .tips-box::before {
            content: "💡";
            position: absolute;
            top: 10px;
            right: 15px;
            font-size: 2rem;
            opacity: 0.3;
        }

        .investigation-guide {
            background: linear-gradient(135deg, #ff6b6b 0%, #ff8e8e 100%);
            color: white;
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 25px;
            animation: slideInDown 0.8s ease-out;
        }

        .instruction-box {
            background: linear-gradient(135deg, #96ceb4 0%, #7ac5a8 100%);
            color: white;
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 25px;
            animation: slideInDown 0.8s ease-out;
        }

        .conclusion-template {
            background: linear-gradient(135deg, #ff6b6b 0%, #ff8e8e 100%);
            color: white;
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 25px;
            animation: slideInDown 0.8s ease-out;
        }

        @keyframes slideInDown {
            0% { opacity: 0; transform: translateY(-30px); }
            100% { opacity: 1; transform: translateY(0); }
        }

        .phet-button {
            display: inline-block;
            background: linear-gradient(135deg, #4ecdc4 0%, #45b7d1 100%);
            color: white;
            padding: 15px 30px;
            border-radius: 50px;
            text-decoration: none;
            font-weight: bold;
            margin-top: 20px;
            transition: all 0.4s ease;
            box-shadow: 0 5px 15px rgba(78, 205, 196, 0.4);
            position: relative;
            overflow: hidden;
            animation: phetPulse 2s infinite;
        }

        @keyframes phetPulse {
            0%, 100% { transform: scale(1); box-shadow: 0 5px 15px rgba(78, 205, 196, 0.4); }
            50% { transform: scale(1.05); box-shadow: 0 5px 25px rgba(78, 205, 196, 0.7); }
        }

        .phet-button:hover {
            background: linear-gradient(135deg, #45b7d1 0%, #4ecdc4 100%);
            transform: translateY(-3px) scale(1.05);
            box-shadow: 0 10px 25px rgba(78, 205, 196, 0.6);
        }

        .progress-bar {
            height: 12px;
            background: #e3f2fd;
            border-radius: 10px;
            margin: 25px 0;
            overflow: hidden;
            box-shadow: inset 0 2px 5px rgba(0,0,0,0.1);
        }

        .progress {
            height: 100%;
            background: linear-gradient(90deg, #4ecdc4, #ff6b6b, #96ceb4);
            width: 0%;
            transition: width 0.8s ease;
            position: relative;
            overflow: hidden;
            border-radius: 10px;
        }

        .progress::after {
            content: "";
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.6), transparent);
            animation: progressShine 2s infinite;
        }

        @keyframes progressShine {
            0% { left: -100%; }
            100% { left: 100%; }
        }

        .narration {
            background: linear-gradient(135deg, #f1f2f6 0%, #e9ecef 100%);
            padding: 20px;
            border-radius: 12px;
            border-left: 5px solid #4ecdc4;
            font-style: italic;
            margin-bottom: 20px;
            animation: fadeInRight 0.8s ease-out 0.2s both;
            box-shadow: 0 3px 10px rgba(0,0,0,0.05);
        }

        @keyframes fadeInRight {
            0% { opacity: 0; transform: translateX(30px); }
            100% { opacity: 1; transform: translateX(0); }
        }

        .completion-message {
            background: linear-gradient(135deg, #96ceb4 0%, #7ac5a8 100%);
            color: white;
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            margin-top: 20px;
            display: none;
            animation: popIn 0.5s ease-out;
            box-shadow: 0 5px 15px rgba(150, 206, 180, 0.4);
        }

        @keyframes popIn {
            0% { opacity: 0; transform: scale(0.8); }
            100% { opacity: 1; transform: scale(1); }
        }

        .attendance-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(160px, 1fr));
            gap: 12px;
            margin-top: 20px;
        }

        .student-name {
            padding: 15px;
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            border-radius: 10px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            animation: studentAppear 0.5s ease-out;
            border: 2px solid transparent;
            box-shadow: 0 3px 8px rgba(0,0,0,0.1);
        }

        @keyframes studentAppear {
            0% { opacity: 0; transform: scale(0.8) rotate(-5deg); }
            100% { opacity: 1; transform: scale(1) rotate(0); }
        }

        .student-name.present {
            background: linear-gradient(135deg, #96ceb4 0%, #7ac5a8 100%);
            color: white;
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(150, 206, 180, 0.4);
            border-color: #7ac5a8;
            animation: studentSelected 0.5s ease-out;
        }

        @keyframes studentSelected {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1.05); }
        }

        .student-name:nth-child(1) { animation-delay: 0.1s; }
        .student-name:nth-child(2) { animation-delay: 0.2s; }
        .student-name:nth-child(3) { animation-delay: 0.3s; }
        .student-name:nth-child(4) { animation-delay: 0.4s; }
        .student-name:nth-child(5) { animation-delay: 0.5s; }
        .student-name:nth-child(6) { animation-delay: 0.6s; }
        .student-name:nth-child(7) { animation-delay: 0.7s; }
        .student-name:nth-child(8) { animation-delay: 0.8s; }

        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 20px;
            margin-top: 25px;
        }

        .menu-item {
            padding: 25px;
            background: linear-gradient(135deg, #4ecdc4 0%, #45b7d1 100%);
            color: white;
            border-radius: 15px;
            text-align: center;
            cursor: pointer;
            transition: all 0.4s ease;
            font-weight: 700;
            animation: menuItemPop 0.6s ease-out;
            box-shadow: 0 8px 20px rgba(78, 205, 196, 0.3);
            position: relative;
            overflow: hidden;
        }

        @keyframes menuItemPop {
            0% { opacity: 0; transform: scale(0.5) rotate(-10deg); }
            100% { opacity: 1; transform: scale(1) rotate(0); }
        }

        .menu-item:hover {
            background: linear-gradient(135deg, #45b7d1 0%, #4ecdc4 100%);
            transform: translateY(-8px) scale(1.05);
            box-shadow: 0 15px 30px rgba(78, 205, 196, 0.5);
        }

        .menu-item:nth-child(1) { animation-delay: 0.1s; }
        .menu-item:nth-child(2) { animation-delay: 0.2s; }
        .menu-item:nth-child(3) { animation-delay: 0.3s; }
        .menu-item:nth-child(4) { animation-delay: 0.4s; }
        .menu-item:nth-child(5) { animation-delay: 0.5s; }

        .text-input {
            width: 100%;
            padding: 15px;
            border: 2px solid #e9ecef;
            border-radius: 10px;
            margin-top: 15px;
            font-size: 1rem;
            resize: vertical;
            min-height: 140px;
            transition: all 0.3s ease;
            animation: inputFocus 0.5s ease-out;
            box-shadow: 0 3px 10px rgba(0,0,0,0.05);
        }

        @keyframes inputFocus {
            0% { box-shadow: 0 0 0 0 rgba(78, 205, 196, 0.5); }
            100% { box-shadow: 0 0 0 10px rgba(78, 205, 196, 0); }
        }

        .text-input:focus {
            outline: none;
            border-color: #4ecdc4;
            box-shadow: 0 0 0 3px rgba(78, 205, 196, 0.3), 0 5px 15px rgba(0,0,0,0.1);
            transform: translateY(-2px);
        }

        .atom-animation {
            width: 100%;
            height: 220px;
            background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%);
            border-radius: 15px;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            overflow: hidden;
            animation: pulseBackground 4s infinite alternate;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
        }

        @keyframes pulseBackground {
            0% { background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%); }
            100% { background: linear-gradient(135deg, #b2ebf2 0%, #e0f7fa 100%); }
        }

        .nucleus {
            width: 50px;
            height: 50px;
            background: #ff6b6b;
            border-radius: 50%;
            position: relative;
            z-index: 2;
            animation: nucleusPulse 2s infinite alternate;
            box-shadow: 0 0 20px rgba(255, 107, 107, 0.5);
        }

        @keyframes nucleusPulse {
            0% { transform: scale(1); box-shadow: 0 0 0 0 rgba(255, 107, 107, 0.7); }
            70% { transform: scale(1.1); box-shadow: 0 0 0 20px rgba(255, 107, 107, 0); }
            100% { transform: scale(1); box-shadow: 0 0 0 0 rgba(255, 107, 107, 0); }
        }

        .electron {
            position: absolute;
            width: 18px;
            height: 18px;
            background: #4ecdc4;
            border-radius: 50%;
            animation: orbit 3s linear infinite;
            box-shadow: 0 0 10px #4ecdc4;
        }

        .electron:nth-child(2) {
            animation-delay: -1s;
        }

        .electron:nth-child(3) {
            animation-delay: -2s;
        }

        @keyframes orbit {
            0% {
                transform: rotate(0deg) translateX(80px) rotate(0deg);
            }
            100% {
                transform: rotate(360deg) translateX(80px) rotate(-360deg);
            }
        }

        .molecule {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 15px;
            margin-top: 25px;
            animation: moleculeForm 2s ease-out;
        }

        @keyframes moleculeForm {
            0% { opacity: 0; transform: scale(0.8); }
            100% { opacity: 1; transform: scale(1); }
        }

        .atom {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-weight: bold;
            animation: atomBounce 2s infinite alternate;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        @keyframes atomBounce {
            0% { transform: translateY(0); }
            100% { transform: translateY(-10px); }
        }

        .hydrogen {
            background: linear-gradient(135deg, #45b7d1 0%, #4ecdc4 100%);
        }

        .oxygen {
            background: linear-gradient(135deg, #ff6b6b 0%, #ff8e8e 100%);
        }

        .nitrogen {
            background: linear-gradient(135deg, #96ceb4 0%, #7ac5a8 100%);
        }

        .bond {
            width: 40px;
            height: 5px;
            background: #ff8e8e;
            animation: bondExtend 1.5s ease-out;
            border-radius: 2px;
        }

        @keyframes bondExtend {
            0% { width: 0; opacity: 0; }
            100% { width: 40px; opacity: 1; }
        }

        .double-bond {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }

        .double-bond .bond {
            height: 3px;
        }

        .triple-bond {
            display: flex;
            flex-direction: column;
            gap: 3px;
        }

        .triple-bond .bond {
            height: 2px;
        }

        .split-screen {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 25px;
            margin-top: 25px;
        }

        @media (max-width: 768px) {
            .split-screen {
                grid-template-columns: 1fr;
            }
        }

        .simulation-area, .observation-area {
            background: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            animation: cardAppear 0.8s ease-out 0.2s both;
            border: 1px solid rgba(255,255,255,0.8);
        }

        .timer {
            background: linear-gradient(135deg, #ff6b6b 0%, #ff8e8e 100%);
            color: white;
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            font-weight: bold;
            margin-top: 20px;
            animation: pulse 2s infinite;
            box-shadow: 0 5px 15px rgba(255, 107, 107, 0.4);
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.02); }
        }

        .reference-box {
            background: linear-gradient(135deg, #ff8e8e 0%, #ff6b6b 100%);
            color: white;
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            animation: cardAppear 0.8s ease-out;
            box-shadow: 0 8px 25px rgba(0,0,0,0.2);
        }

        .table-container {
            overflow-x: auto;
            margin-top: 20px;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.05);
        }

        .observation-table {
            width: 100%;
            border-collapse: collapse;
            animation: fadeInUp 0.8s ease-out 0.3s both;
        }

        .observation-table th, .observation-table td {
            border: 1px solid #e9ecef;
            padding: 15px;
            text-align: left;
            transition: all 0.3s ease;
        }

        .observation-table th {
            background: linear-gradient(135deg, #4ecdc4 0%, #45b7d1 100%);
            color: white;
            font-weight: 600;
        }

        .observation-table tr:nth-child(even) {
            background: #f8f9fa;
        }

        .observation-table tr:hover {
            background: #e3f2fd;
            transform: translateX(5px);
        }

        .observation-table input {
            width: 100%;
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 5px;
            transition: all 0.3s ease;
        }

        .observation-table input:focus {
            outline: none;
            border-color: #4ecdc4;
            box-shadow: 0 0 0 2px rgba(78, 205, 196, 0.2);
        }

        .comparison-container {
            display: flex;
            justify-content: space-around;
            margin-top: 25px;
            flex-wrap: wrap;
            gap: 20px;
        }

        .molecule-card {
            background: white;
            border-radius: 15px;
            padding: 20px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            text-align: center;
            width: 200px;
            transition: all 0.3s ease;
        }

        .molecule-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.15);
        }

        .molecule-card h4 {
            color: #ff6b6b;
            margin-bottom: 15px;
        }

        .molecule-card .bond-visual {
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 15px 0;
        }

        .molecule-card .properties {
            text-align: left;
            margin-top: 15px;
        }

        .molecule-card .properties p {
            margin: 5px 0;
            font-size: 0.9rem;
        }

        .quiz-container {
            background: white;
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            margin-top: 25px;
        }

        .quiz-question {
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid #e9ecef;
        }

        .quiz-question h4 {
            color: #ff6b6b;
            margin-bottom: 10px;
        }

        .quiz-options {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .quiz-option {
            padding: 12px 15px;
            background: #f8f9fa;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .quiz-option:hover {
            background: #e3f2fd;
            transform: translateX(5px);
        }

        .quiz-option.selected {
            background: #4ecdc4;
            color: white;
        }

        /* Notifikasi */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            background: white;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            padding: 15px 20px;
            z-index: 1000;
            transform: translateX(100%);
            transition: transform 0.3s ease;
            border-left: 4px solid #4ecdc4;
        }
        .notification.show {
            transform: translateX(0);
        }
        .notification.info {
            border-left-color: #4ecdc4;
        }
        .notification.success {
            border-left-color: #96ceb4;
        }
        .notification-content {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .notification i {
            font-size: 1.2rem;
        }
        .notification.info i {
            color: #4ecdc4;
        }
        .notification.success i {
            color: #96ceb4;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>Pembelajaran Interaktif Ikatan Kovalen</h1>
            <div class="header-subtitle">Menjelajahi Dunia Mikroskopis Atom dan Molekul</div>
            <div class="header-info">
                <div class="info-item">Nama: Al Amin</div>
                <div class="info-item">Sub Topik: Ikatan Kovalen</div>
                <div class="info-item">Kelas: X IPA</div>
                <div class="info-item">Waktu: 60 Menit</div>
            </div>
        </div>

        <div class="progress-bar">
            <div class="progress" id="progress"></div>
        </div>

        <!-- Scene 1: Pembuka -->
        <div class="scene-container active" id="scene-1">
            <h2 class="scene-title">Scene 1: Pembukaan Pembelajaran</h2>
            <div class="scene-content">
                <div class="visual-section">
                    <h3 class="section-title"><i class="fas fa-eye"></i> Visual Pembelajaran</h3>
                    <div class="atom-animation">
                        <div class="nucleus"></div>
                        <div class="electron"></div>
                        <div class="electron"></div>
                        <div class="electron"></div>
                    </div>
                    <div class="molecule">
                        <div class="atom hydrogen">H</div>
                        <div class="bond"></div>
                        <div class="atom oxygen">O</div>
                        <div class="bond"></div>
                        <div class="atom hydrogen">H</div>
                    </div>
                    <p style="text-align: center; margin-top: 15px; font-weight: 600; color: #ff6b6b;">Pembentukan Molekul Air (H<sub>2</sub>O)</p>
                </div>
                <div class="audio-section">
                    <h3 class="section-title"><i class="fas fa-volume-up"></i> Pengantar Pembelajaran</h3>
                    <div class="narration">
                        "Selamat datang, para ilmuwan muda! Dalam pembelajaran interaktif ini, kita akan menjelajahi misteri ikatan kovalen. Pernahkah kalian bertanya-tanya bagaimana atom-atom bergabung membentuk molekul? Mari kita selidiki bersama melalui simulasi digital yang menarik!"
                    </div>
                    <h3 class="section-title"><i class="fas fa-text-height"></i> Tujuan Pembelajaran</h3>
                    <div style="padding: 20px; background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%); border-radius: 12px; border-left: 5px solid #4ecdc4;">
                        <h3 style="color: #ff6b6b; margin-bottom: 15px; text-align: center;">TUJUAN PEMBELAJARAN</h3>
                        <p style="text-align: center; font-size: 1.1rem;">Peserta didik dapat menjelaskan konsep ikatan kovalen, proses pembentukan molekul, dan mengidentifikasi jenis-jenis ikatan kovalen melalui simulasi interaktif.</p>
                    </div>
                </div>
            </div>
            <div class="controls">
                <button class="btn btn-prev" disabled>
                    <i class="fas fa-arrow-left"></i> Sebelumnya
                </button>
                <div>
                    <button class="btn btn-save" id="save-1">
                        <i class="fas fa-save"></i> Simpan Progress
                    </button>
                </div>
                <button class="btn btn-next" id="next-1">
                    Selanjutnya <i class="fas fa-arrow-right"></i>
                </button>
            </div>
        </div>

        <!-- Scene 2: Absensi -->
        <div class="scene-container" id="scene-2">
            <h2 class="scene-title">Scene 2: Absensi Kelas</h2>
            
            <div class="instruction-box">
                <p><strong>Klik pada nama Anda untuk menandai kehadiran, lalu simpan untuk melanjutkan!</strong></p>
            </div>
            
            <div class="scene-content">
                <div class="visual-section">
                    <h3 class="section-title"><i class="fas fa-clipboard-list"></i> Daftar Hadir Siswa</h3>
                    <p style="margin-bottom: 15px; color: #555;">Pilih nama Anda dari daftar berikut:</p>
                    <div class="attendance-list" id="attendance-list">
                        <!-- Student names will be added here by JavaScript -->
                    </div>
                    <div class="completion-message" id="attendance-complete">
                        <i class="fas fa-check-circle"></i> Kehadiran telah dicatat! Anda dapat melanjutkan.
                    </div>
                </div>
                <div class="audio-section">
                    <h3 class="section-title"><i class="fas fa-volume-up"></i> Petunjuk Absensi</h3>
                    <div class="narration">
                        "Silakan tandai kehadiran Anda dengan mengklik nama Anda sendiri. Setelah itu, simpan progress untuk melanjutkan pembelajaran. Pastikan Anda memilih nama yang benar untuk pencatatan kehadiran."
                    </div>
                    <h3 class="section-title"><i class="fas fa-info-circle"></i> Informasi Kelas</h3>
                    <div style="padding: 20px; background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%); border-radius: 12px; border-left: 5px solid #4ecdc4;">
                        <h3 style="color: #ff6b6b; margin-bottom: 10px; text-align: center;">KELAS X IPA</h3>
                        <p style="text-align: center;">Mata Pelajaran: Kimia</p>
                        <p style="text-align: center;">Topik: Ikatan Kovalen</p>
                        <p style="text-align: center;">Waktu: 60 Menit</p>
                    </div>
                </div>
            </div>
            <div class="controls">
                <button class="btn btn-prev" id="prev-2">
                    <i class="fas fa-arrow-left"></i> Sebelumnya
                </button>
                <div>
                    <button class="btn btn-save" id="save-2" disabled>
                        <i class="fas fa-save"></i> Simpan Progress
                    </button>
                </div>
                <button class="btn btn-next" id="next-2" disabled>
                    Selanjutnya <i class="fas fa-arrow-right"></i>
                </button>
            </div>
        </div>

        <!-- Scene 3: Menu Pembelajaran -->
        <div class="scene-container" id="scene-3">
            <h2 class="scene-title">Scene 3: Menu Pembelajaran</h2>
            <div class="scene-content">
                <div class="visual-section">
                    <h3 class="section-title"><i class="fas fa-bars"></i> Menu Interaktif Pembelajaran</h3>
                    <div class="menu-grid">
                        <div class="menu-item">1. Orientasi Pembelajaran</div>
                        <div class="menu-item">2. Merumuskan Masalah</div>
                        <div class="menu-item">3. Merencanakan Penyelidikan</div>
                        <div class="menu-item">4. Melakukan Penyelidikan</div>
                        <div class="menu-item">5. Menganalisis & Menyimpulkan</div>
                    </div>
                </div>
                <div class="audio-section">
                    <h3 class="section-title"><i class="fas fa-volume-up"></i> Panduan Menu</h3>
                    <div class="narration">
                        "Ini adalah menu pembelajaran kita. Kita akan mengikuti langkah-langkah penyelidikan ilmiah secara berurutan. Setiap fase akan membawa kita lebih dekat kepada pemahaman tentang ikatan kovalen. Pilih fase yang ingin Anda pelajari atau lanjutkan secara berurutan."
                    </div>
                    <h3 class="section-title"><i class="fas fa-road"></i> Alur Pembelajaran</h3>
                    <div style="padding: 20px; background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%); border-radius: 12px; border-left: 5px solid #4ecdc4;">
                        <h3 style="color: #ff6b6b; margin-bottom: 15px; text-align: center;">ALUR PEMBELAJARAN</h3>
                        <p>1. Orientasi: Memahami konsep dasar ikatan kovalen</p>
                        <p>2. Merumuskan Masalah: Mengidentifikasi pertanyaan penelitian</p>
                        <p>3. Merencanakan: Menyusun rencana penyelidikan</p>
                        <p>4. Menyelidiki: Melakukan eksperimen digital</p>
                        <p>5. Menyimpulkan: Menganalisis hasil dan membuat kesimpulan</p>
                    </div>
                </div>
            </div>
            <div class="controls">
                <button class="btn btn-prev" id="prev-3">
                    <i class="fas fa-arrow-left"></i> Sebelumnya
                </button>
                <div>
                    <button class="btn btn-save" id="save-3">
                        <i class="fas fa-save"></i> Simpan Progress
                    </button>
                </div>
                <button class="btn btn-next" id="next-3">
                    Selanjutnya <i class="fas fa-arrow-right"></i>
                </button>
            </div>
        </div>

        <!-- Scene 4: Orientasi -->
        <div class="scene-container" id="scene-4">
            <h2 class="scene-title">Scene 4: Orientasi Pembelajaran</h2>
            <div class="scene-content">
                <div class="visual-section">
                    <h3 class="section-title"><i class="fas fa-atom"></i> Visualisasi Konsep</h3>
                    <div class="atom-animation">
                        <div class="nucleus"></div>
                        <div class="electron"></div>
                        <div class="electron"></div>
                    </div>
                    <div class="molecule">
                        <div class="atom oxygen">O</div>
                        <div class="double-bond">
                            <div class="bond"></div>
                            <div class="bond"></div>
                        </div>
                        <div class="atom oxygen">O</div>
                    </div>
                    <p style="text-align: center; margin-top: 15px; font-weight: 600; color: #ff6b6b;">Molekul Oksigen (O<sub>2</sub>) dengan Ikatan Rangkap</p>
                </div>
                <div class="audio-section">
                    <h3 class="section-title"><i class="fas fa-volume-up"></i> Pengantar Konsep</h3>
                    <div class="narration">
                        "Selamat datang, Ilmuwan Muda! Pernahkah kalian bertanya... Mengapa oksigen (O<sub>2</sub>) yang kita hirup tersusun dari 2 atom? Bagaimana atom-atom yang sama-sama bermuatan negatif bisa bersatu membentuk molekul? Mari kita jelajahi misteri ini bersama-sama!"
                    </div>
                    <h3 class="section-title"><i class="fas fa-question-circle"></i> Pertanyaan Pemantik</h3>
                    <div style="padding: 20px; background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%); color: #ff6b6b; border-radius: 12px; margin-top: 15px;">
                        <strong>Pertanyaan Fenomena:</strong><br>
                        "Bagaimana atom-atom yang sama-sama bermuatan negatif bisa bersatu membentuk molekul yang stabil?"
                    </div>
                    <div style="padding: 15px; background: #e3f2fd; border-radius: 8px; margin-top: 15px;">
                        <p><strong>Fakta Menarik:</strong> Setiap atom oksigen memiliki 8 elektron, dan ketika berikatan, mereka berbagi elektron untuk mencapai konfigurasi yang stabil!</p>
                    </div>
                </div>
            </div>
            <div class="controls">
                <button class="btn btn-prev" id="prev-4">
                    <i class="fas fa-arrow-left"></i> Sebelumnya
                </button>
                <div>
                    <button class="btn btn-save" id="save-4">
                        <i class="fas fa-save"></i> Simpan Progress
                    </button>
                </div>
                <button class="btn btn-next" id="next-4">
                    Selanjutnya <i class="fas fa-arrow-right"></i>
                </button>
            </div>
        </div>

        <!-- Scene 5: Merumuskan Masalah -->
        <div class="scene-container" id="scene-5">
            <h2 class="scene-title">Scene 5: Merumuskan Masalah Penelitian</h2>
            
            <div class="instruction-box">
                <p><strong>Petunjuk:</strong> Bersiaplah untuk menyelidiki misteri ikatan kimia melalui simulasi digital!</p>
                <p><strong>Instruksi:</strong> Diskusikan dengan kelompokmu dan tuliskan dugaan sementara (hipotesis) di LKPD digital!</p>
            </div>
            
            <div class="scene-content">
                <div class="visual-section">
                    <h3 class="section-title"><i class="fas fa-question"></i> Pertanyaan Pemandu Penelitian</h3>
                    <div style="padding: 20px; background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%); border-radius: 12px;">
                        <p><strong>1.</strong> Bagaimana proses terbentuknya ikatan pada molekul H<sub>2</sub>, O<sub>2</sub>, dan N<sub>2</sub>?</p>
                        <p><strong>2.</strong> Berapa banyak pasangan elektron yang digunakan bersama pada masing-masing molekul?</p>
                        <p><strong>3.</strong> Apa hubungan antara jumlah pasangan elektron dengan kekuatan ikatan?</p>
                        <p><strong>4.</strong> Mengapa beberapa molekul membentuk ikatan tunggal, rangkap dua, atau rangkap tiga?</p>
                    </div>
                    <h3 class="section-title" style="margin-top: 20px;"><i class="fas fa-lightbulb"></i> Hipotesis Sementara</h3>
                    <textarea class="text-input" id="hypothesis-input" placeholder="Tuliskan dugaan sementara (hipotesis) berdasarkan pengetahuan awal Anda tentang ikatan kimia..."></textarea>
                    <div class="completion-message" id="hypothesis-complete">
                        <i class="fas fa-check-circle"></i> Hipotesis telah disimpan! Anda dapat melanjutkan.
                    </div>
                </div>
                <div class="audio-section">
                    <h3 class="section-title"><i class="fas fa-volume-up"></i> Panduan Perumusan Masalah</h3>
                    <div class="narration">
                        "Mari Merumuskan Pertanyaan Penelitian! Diskusikan dengan kelompokmu dan tuliskan dugaan sementara (hipotesis) di LKPD digital! Gunakan pertanyaan-pertanyaan pemandu sebagai panduan untuk mengembangkan hipotesis Anda."
                    </div>
                    <h3 class="section-title"><i class="fas fa-clipboard-check"></i> Kriteria Hipotesis yang Baik</h3>
                    <div style="padding: 20px; background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%); border-radius: 12px;">
                        <p><strong>Hipotesis yang baik harus:</strong></p>
                        <p>• Dapat diuji melalui eksperimen</p>
                        <p>• Berdasarkan pengetahuan ilmiah</p>
                        <p>• Jelas dan spesifik</p>
                        <p>• Menjelaskan hubungan sebab-akibat</p>
                    </div>
                </div>
            </div>
            <div class="controls">
                <button class="btn btn-prev" id="prev-5">
                    <i class="fas fa-arrow-left"></i> Sebelumnya
                </button>
                <div>
                    <button class="btn btn-save" id="save-5">
                        <i class="fas fa-save"></i> Simpan Progress
                    </button>
                </div>
                <button class="btn btn-next" id="next-5" disabled>
                    Selanjutnya <i class="fas fa-arrow-right"></i>
                </button>
            </div>
        </div>

        <!-- Scene 6: Merencanakan Penyelidikan -->
        <div class="scene-container" id="scene-6">
            <h2 class="scene-title">Scene 6: Merencanakan Penyelidikan Ilmiah</h2>
            
            <div class="investigation-guide">
                <p><strong>Rencana Penyelidikan Ilmiah Kita</strong></p>
            </div>
            
            <!-- Tips dipindahkan ke atas -->
            <div class="tips-box">
                <p><strong>Tips Penting:</strong> "Perhatikan baik-baik bagaimana elektron-elektron berperilaku saat atom-atom saling mendekat! Amati perubahan energi dan stabilitas sistem ketika ikatan terbentuk."</p>
            </div>
            
            <div class="scene-content">
                <!-- Audio Section dipindahkan ke atas/sebelah kiri -->
                <div class="audio-section">
                    <h3 class="section-title"><i class="fas fa-volume-up"></i> Panduan Penyelidikan</h3>
                    <div class="narration">
                        "Sekarang kita akan merencanakan penyelidikan ilmiah kita. Ikuti langkah-langkah yang telah disiapkan untuk menyelidiki ikatan kovalen pada berbagai molekul. Jangan lupa perhatikan tips yang diberikan sebelum memulai simulasi. Persiapan yang baik akan membantu Anda mendapatkan hasil yang optimal."
                    </div>
                    <h3 class="section-title"><i class="fas fa-cogs"></i> Panduan Simulasi PhET</h3>
                    <div style="padding: 20px; background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%); border-radius: 12px;">
                        <p><strong>Cara menggunakan simulasi PhET:</strong></p>
                        <p>1. Klik tombol "Buka Simulasi PhET" di sebelah kanan</p>
                        <p>2. Pilih atom yang ingin Anda gabungkan dari panel kiri</p>
                        <p>3. Tarik atom-atom tersebut mendekati satu sama lain</p>
                        <p>4. Amati bagaimana ikatan terbentuk dan elektron berbagi</p>
                        <p>5. Catat hasil pengamatan Anda dalam tabel observasi</p>
                        <p>6. Ulangi untuk molekul H<sub>2</sub>, O<sub>2</sub>, dan N<sub>2</sub></p>
                    </div>
                    
                    <div style="padding: 15px; background: #e3f2fd; border-radius: 8px; margin-top: 15px;">
                        <p><strong>Pertanyaan untuk Dipantau Selama Investigasi:</strong></p>
                        <p>• Bagaimana elektron berperilaku saat atom mendekat?</p>
                        <p>• Apa yang terjadi ketika ikatan kimia terbentuk?</p>
                        <p>• Mengapa beberapa molekul memiliki ikatan rangkap?</p>
                        <p>• Bagaimana kekuatan ikatan terkait dengan jumlah pasangan elektron?</p>
                    </div>
                </div>
                
                <!-- Visual Section dipindahkan ke kanan -->
                <div class="visual-section">
                    <h3 class="section-title"><i class="fas fa-list-ol"></i> Langkah-langkah Penyelidikan</h3>
                    <div style="padding: 20px; background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%); border-radius: 12px;">
                        <p><strong>1.</strong> Buka simulasi PhET "Build a Molecule"</p>
                        <p><strong>2.</strong> Bentuk molekul: H<sub>2</sub>, O<sub>2</sub>, dan N<sub>2</sub></p>
                        <p><strong>3.</strong> Amati jumlah pasangan elektron yang digunakan bersama</p>
                        <p><strong>4.</strong> Catat hasil pengamatan dalam tabel observasi</p>
                        <p><strong>5.</strong> Bandingkan kekuatan ikatan masing-masing molekul</p>
                        <p><strong>6.</strong> Analisis hubungan antara jenis ikatan dan stabilitas molekul</p>
                    </div>
                    
                    <!-- Tombol PhET dipindahkan ke paling bawah -->
                    <div style="margin-top: 30px; text-align: center;">
                        <a href="https://phet.colorado.edu/sims/html/build-a-molecule/latest/build-a-molecule_id.html" target="_blank" class="phet-button">
                            <i class="fas fa-external-link-alt"></i> Buka Simulasi PhET "Build a Molecule"
                        </a>
                    </div>
                    
                    <div class="completion-message" id="scene6-complete">
                        <i class="fas fa-check-circle"></i> Progress telah disimpan! Anda dapat melanjutkan ke investigasi.
                    </div>
                </div>
            </div>
            <div class="controls">
                <button class="btn btn-prev" id="prev-6">
                    <i class="fas fa-arrow-left"></i> Sebelumnya
                </button>
                <div>
                    <button class="btn btn-save" id="save-6">
                        <i class="fas fa-save"></i> Simpan Progress
                    </button>
                </div>
                <button class="btn btn-next" id="next-6" disabled>
                    Selanjutnya <i class="fas fa-arrow-right"></i>
                </button>
            </div>
        </div>

        <!-- Scene 7: Melakukan Penyelidikan -->
        <div class="scene-container" id="scene-7">
            <h2 class="scene-title">Scene 7: Melakukan Penyelidikan Ilmiah</h2>
            
            <div class="investigation-guide">
                <p><strong>Waktunya Menyelidiki! Lakukan Eksperimen Digital dengan Simulasi PhET</strong></p>
            </div>
            
            <div class="split-screen">
                <div class="simulation-area">
                    <h3 class="section-title"><i class="fas fa-desktop"></i> Area Simulasi Digital</h3>
                    <div style="background: #e3f2fd; padding: 25px; border-radius: 12px; text-align: center; min-height: 250px; display: flex; flex-direction: column; justify-content: center; border: 2px dashed #4ecdc4;">
                        <i class="fas fa-atom" style="font-size: 3.5rem; color: #4ecdc4; margin-bottom: 20px;"></i>
                        <h4 style="color: #ff6b6b; margin-bottom: 10px;">Simulasi PhET "Build a Molecule"</h4>
                        <p style="color: #555; margin-bottom: 15px;">Bentuk dan amati molekul H<sub>2</sub>, O<sub>2</sub>, dan N<sub>2</sub></p>
                        <p style="color: #555;">Perhatikan pembentukan ikatan dan perilaku elektron</p>
                    </div>
                    
                    <div class="timer">
                        <i class="fas fa-clock"></i> Waktu Investigasi: <span id="countdown">25:00</span>
                    </div>

                    <div style="margin-top: 20px; text-align: center;">
                        <a href="https://phet.colorado.edu/sims/html/build-a-molecule/latest/build-a-molecule_id.html" target="_blank" class="phet-button">
                            <i class="fas fa-external-link-alt"></i> Buka Simulasi PhET
                        </a>
                    </div>
                </div>
                
                <div class="observation-area">
                    <h3 class="section-title"><i class="fas fa-clipboard-list"></i> Lembar Observasi dan Data</h3>
                    <div class="table-container">
                        <table class="observation-table">
                            <thead>
                                <tr>
                                    <th>Molekul</th>
                                    <th>Jumlah Pasangan Elektron</th>
                                    <th>Jenis Ikatan</th>
                                    <th>Kekuatan Ikatan</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>H<sub>2</sub></td>
                                    <td><input type="text" placeholder="Isi hasil pengamatan" style="width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 5px;"></td>
                                    <td><input type="text" placeholder="Jenis ikatan" style="width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 5px;"></td>
                                    <td><input type="text" placeholder="Kekuatan ikatan" style="width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 5px;"></td>
                                </tr>
                                <tr>
                                    <td>O<sub>2</sub></td>
                                    <td><input type="text" placeholder="Isi hasil pengamatan" style="width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 5px;"></td>
                                    <td><input type="text" placeholder="Jenis ikatan" style="width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 5px;"></td>
                                    <td><input type="text" placeholder="Kekuatan ikatan" style="width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 5px;"></td>
                                </tr>
                                <tr>
                                    <td>N<sub>2</sub></td>
                                    <td><input type="text" placeholder="Isi hasil pengamatan" style="width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 5px;"></td>
                                    <td><input type="text" placeholder="Jenis ikatan" style="width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 5px;"></td>
                                    <td><input type="text" placeholder="Kekuatan ikatan" style="width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 5px;"></td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                    
                    <h4 style="margin-top: 20px; color: #ff6b6b;">Pertanyaan Pemandu Selama Investigasi:</h4>
                    <div style="padding: 15px; background: #e3f2fd; border-radius: 8px; margin-top: 10px;">
                        <p>• Apa yang terjadi ketika dua atom Hidrogen didekatkan? Bagaimana ikatan terbentuk?</p>
                        <p>• Mengapa ikatan N<sub>2</sub> lebih kuat daripada O<sub>2</sub>? Apa hubungannya dengan jumlah pasangan elektron?</p>
                        <p>• Bagaimana perbedaan ikatan tunggal, rangkap dua, dan rangkap tiga dalam hal kekuatan dan stabilitas?</p>
                    </div>
                </div>
            </div>
            
            <div class="controls">
                <button class="btn btn-prev" id="prev-7">
                    <i class="fas fa-arrow-left"></i> Sebelumnya
                </button>
                <div>
                    <button class="btn btn-save" id="save-7">
                        <i class="fas fa-save"></i> Simpan Progress
                    </button>
                </div>
                <button class="btn btn-next" id="next-7">
                    Selanjutnya <i class="fas fa-arrow-right"></i>
                </button>
            </div>
        </div>

        <!-- Scene 8: Analisis Komparatif Molekul -->
        <div class="scene-container" id="scene-8">
            <h2 class="scene-title">Scene 8: Analisis Komparatif Molekul</h2>
            
            <div class="conclusion-template">
                <p><strong>Perbandingan Sifat Molekul Berdasarkan Jenis Ikatan Kovalen</strong></p>
            </div>
            
            <div class="scene-content">
                <div class="visual-section">
                    <h3 class="section-title"><i class="fas fa-chart-bar"></i> Visualisasi Perbandingan Molekul</h3>
                    
                    <div class="comparison-container">
                        <div class="molecule-card">
                            <h4>Hidrogen (H<sub>2</sub>)</h4>
                            <div class="bond-visual">
                                <div class="atom hydrogen">H</div>
                                <div class="bond"></div>
                                <div class="atom hydrogen">H</div>
                            </div>
                            <div class="properties">
                                <p><strong>Jenis Ikatan:</strong> Tunggal</p>
                                <p><strong>Pasangan Elektron:</strong> 1</p>
                                <p><strong>Energi Ikatan:</strong> 436 kJ/mol</p>
                                <p><strong>Panjang Ikatan:</strong> 74 pm</p>
                            </div>
                        </div>
                        
                        <div class="molecule-card">
                            <h4>Oksigen (O<sub>2</sub>)</h4>
                            <div class="bond-visual">
                                <div class="atom oxygen">O</div>
                                <div class="double-bond">
                                    <div class="bond"></div>
                                    <div class="bond"></div>
                                </div>
                                <div class="atom oxygen">O</div>
                            </div>
                            <div class="properties">
                                <p><strong>Jenis Ikatan:</strong> Rangkap Dua</p>
                                <p><strong>Pasangan Elektron:</strong> 2</p>
                                <p><strong>Energi Ikatan:</strong> 498 kJ/mol</p>
                                <p><strong>Panjang Ikatan:</strong> 121 pm</p>
                            </div>
                        </div>
                        
                        <div class="molecule-card">
                            <h4>Nitrogen (N<sub>2</sub>)</h4>
                            <div class="bond-visual">
                                <div class="atom nitrogen">N</div>
                                <div class="triple-bond">
                                    <div class="bond"></div>
                                    <div class="bond"></div>
                                    <div class="bond"></div>
                                </div>
                                <div class="atom nitrogen">N</div>
                            </div>
                            <div class="properties">
                                <p><strong>Jenis Ikatan:</strong> Rangkap Tiga</p>
                                <p><strong>Pasangan Elektron:</strong> 3</p>
                                <p><strong>Energi Ikatan:</strong> 945 kJ/mol</p>
                                <p><strong>Panjang Ikatan:</strong> 110 pm</p>
                            </div>
                        </div>
                    </div>
                    
                    <div style="margin-top: 30px; padding: 20px; background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%); border-radius: 12px;">
                        <h4 style="color: rgba(17, 16, 16, 1)ff; margin-bottom: 15px;">Pola yang Dapat Diamati:</h4>
                        <p>• Semakin banyak pasangan elektron yang digunakan bersama, semakin kuat ikatan yang terbentuk</p>
                        <p>• Ikatan rangkap tiga (N<sub>2</sub>) lebih kuat daripada ikatan rangkap dua (O<sub>2</sub>)</p>
                        <p>• Ikatan rangkap dua (O<sub>2</sub>) lebih kuat daripada ikatan tunggal (H<sub>2</sub>)</p>
                        <p>• Panjang ikatan cenderung lebih pendek pada ikatan yang lebih kuat</p>
                    </div>
                </div>
                
                <div class="audio-section">
                    <h3 class="section-title"><i class="fas fa-lightbulb"></i> Kuis Pemahaman Konsep</h3>
                    
                    <div class="quiz-container">
                        <div class="quiz-question">
                            <h4>1. Mengapa ikatan rangkap tiga pada N<sub>2</sub> lebih kuat daripada ikatan tunggal pada H<sub>2</sub>?</h4>
                            <div class="quiz-options">
                                <div class="quiz-option" data-correct="false">Karena atom nitrogen lebih besar</div>
                                <div class="quiz-option" data-correct="true">Karena jumlah pasangan elektron yang digunakan bersama lebih banyak</div>
                                <div class="quiz-option" data-correct="false">Karena nitrogen memiliki lebih banyak elektron</div>
                                <div class="quiz-option" data-correct="false">Karena ikatan rangkap tiga selalu lebih kuat</div>
                            </div>
                        </div>
                        
                        <div class="quiz-question">
                            <h4>2. Apa yang terjadi ketika dua atom hidrogen membentuk molekul H<sub>2</sub>?</h4>
                            <div class="quiz-options">
                                <div class="quiz-option" data-correct="false">Mereka saling menolak elektronnya</div>
                                <div class="quiz-option" data-correct="true">Mereka berbagi sepasang elektron untuk mencapai konfigurasi stabil</div>
                                <div class="quiz-option" data-correct="false">Salah satu atom memberikan elektron kepada yang lain</div>
                                <div class="quiz-option" data-correct="false">Tidak terjadi apa-apa karena hidrogen tidak dapat berikatan</div>
                            </div>
                        </div>
                        
                        <div class="quiz-question">
                            <h4>3. Bagaimana hubungan antara jumlah pasangan elektron dan kekuatan ikatan?</h4>
                            <div class="quiz-options">
                                <div class="quiz-option" data-correct="false">Tidak ada hubungan</div>
                                <div class="quiz-option" data-correct="false">Semakin banyak pasangan elektron, semakin lemah ikatan</div>
                                <div class="quiz-option" data-correct="true">Semakin banyak pasangan elektron, semakin kuat ikatan</div>
                                <div class="quiz-option" data-correct="false">Hanya ikatan tunggal yang kuat</div>
                            </div>
                        </div>
                    </div>
                    
                    <div style="margin-top: 25px; text-align: center;">
                        <button class="btn btn-save" id="check-quiz">
                            <i class="fas fa-check-circle"></i> Periksa Jawaban
                        </button>
                    </div>
                    
                    <div class="completion-message" id="quiz-result" style="display: none;">
                        <!-- Hasil kuis akan ditampilkan di sini -->
                    </div>
                </div>
            </div>
            <div class="controls">
                <button class="btn btn-prev" id="prev-8">
                    <i class="fas fa-arrow-left"></i> Sebelumnya
                </button>
                <div>
                    <button class="btn btn-save" id="save-8">
                        <i class="fas fa-save"></i> Simpan Progress
                    </button>
                </div>
                <button class="btn btn-next" id="next-8">
                    Selanjutnya <i class="fas fa-arrow-right"></i>
                </button>
            </div>
        </div>

        <!-- Scene 9: Daftar Pustaka -->
        <div class="scene-container" id="scene-9">
            <h2 class="scene-title">Scene 9: Sumber Referensi & Penutup</h2>
            
            <div class="reference-box">
                <h3><i class="fas fa-book"></i> Sumber Referensi Pembelajaran</h3>
                <p>Interactive Simulations project at the University of Colorado Boulder</p>
                <p>Menciptakan simulasi matematika dan sains interaktif gratis.</p>
                
                <div style="margin-top: 25px;">
                    <a href="https://phet.colorado.edu" target="_blank" class="phet-button">
                        <i class="fas fa-external-link-alt"></i> Kunjungi PhET Colorado
                    </a>
                </div>
            </div>
            
            <div class="scene-content" style="margin-top: 25px;">
                <div class="visual-section">
                    <h3 class="section-title"><i class="fas fa-graduation-cap"></i> Sumber Belajar Lainnya</h3>
                    <div style="padding: 20px; background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%); border-radius: 12px;">
                        <p>• Buku Teks Kimia Kelas X - Kementerian Pendidikan dan Kebudayaan</p>
                        <p>• Modul Pembelajaran Ikatan Kimia - Direktorat Pembinaan SMA</p>
                        <p>• Video Pembelajaran Ikatan Kovalen - Channel Edukasi Kimia</p>
                        <p>• Simulasi Interaktif Lainnya - PhET Interactive Simulations</p>
                        <p>• Jurnal Ilmiah Kimia Pendidikan - Perhimpunan Pendidikan Kimia</p>
                    </div>

                    <div style="margin-top: 20px; padding: 20px; background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%); border-radius: 12px;">
                        <h4 style="color: #ff6b6b; margin-bottom: 15px;">Evaluasi Pembelajaran</h4>
                        <p>Setelah menyelesaikan modul ini, Anda diharapkan dapat:</p>
                        <p>• Menjelaskan konsep ikatan kovalen dengan benar</p>
                        <p>• Mengidentifikasi jenis-jenis ikatan kovalen</p>
                        <p>• Menganalisis hubungan antara jumlah pasangan elektron dan kekuatan ikatan</p>
                        <p>• Menerapkan pengetahuan tentang ikatan kovalen dalam konteks kehidupan sehari-hari</p>
                    </div>
                </div>
                
                <div class="audio-section">
                    <h3 class="section-title"><i class="fas fa-user"></i> Profil Pengembang Media</h3>
                    <div style="padding: 20px; background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%); border-radius: 12px;">
                        <p><strong>Nama Pengembang:</strong> Al Amin</p>
                        <p><strong>Instansi:</strong> Guru Kimia SMA</p>
                        <p><strong>Topik Pembelajaran:</strong> Ikatan Kovalen</p>
                        <p><strong>Model Pembelajaran:</strong> Inquiry Terstruktur</p>
                        <p><strong>Media Pembelajaran:</strong> Digital Interaktif</p>
                        <p><strong>Tahun Pengembangan:</strong> 2024</p>
                    </div>
                    
                    <div style="margin-top: 25px; text-align: center;">
                        <div class="completion-message" style="display: block;">
                            <i class="fas fa-graduation-cap"></i> Selamat! Anda telah menyelesaikan pembelajaran interaktif tentang Ikatan Kovalen.
                        </div>
                    </div>

                    <div style="margin-top: 20px; padding: 15px; background: #e3f2fd; border-radius: 8px; text-align: center;">
                        <p><strong>Aplikasi dalam Kehidupan Sehari-hari:</strong></p>
                        <p>Pengetahuan tentang ikatan kovalen membantu kita memahami sifat-sifat materi di sekitar kita, dari air yang kita minum hingga udara yang kita hirup!</p>
                    </div>
                </div>
            </div>
            <div class="controls">
                <button class="btn btn-prev" id="prev-9">
                    <i class="fas fa-arrow-left"></i> Sebelumnya
                </button>
                <div>
                    <button class="btn btn-save" id="save-9">
                        <i class="fas fa-save"></i> Simpan Progress
                    </button>
                </div>
                <button class="btn btn-restart" id="restart-learning">
                    <i class="fas fa-redo"></i> Kembali ke Awal
                </button>
            </div>
        </div>
    </div>

    <script>
        // Data siswa untuk absensi
        const students = ["Rasya", "Risky", "Ubed", "Defin", "Al Amin", "Siti", "Budi", "Ani"];

        // State aplikasi
        const appState = {
            currentScene: 1,
            totalScenes: 9,
            progress: 0,
            attendance: {},
            selectedStudent: null,
            hypothesis: "",
            completedScenes: {},
            timerRunning: false,
            timerInterval: null,
            timerValue: 25 * 60, // 25 menit dalam detik
            observations: {
                h2: { pairs: "", type: "", strength: "" },
                o2: { pairs: "", type: "", strength: "" },
                n2: { pairs: "", type: "", strength: "" }
            },
            conclusion: "",
            quizAnswers: {}
        };

        // Inisialisasi aplikasi
        document.addEventListener('DOMContentLoaded', function() {
            initializeApp();
            setupEventListeners();
            updateProgressBar();
            loadStateFromStorage();
        });

        function initializeApp() {
            // Inisialisasi daftar absensi
            const attendanceList = document.getElementById('attendance-list');
            attendanceList.innerHTML = ''; // Kosongkan dulu
            
            students.forEach((student, index) => {
                const studentElement = document.createElement('div');
                studentElement.className = 'student-name';
                studentElement.textContent = student;
                studentElement.style.animationDelay = `${index * 0.1}s`;
                studentElement.addEventListener('click', function() {
                    // Reset semua siswa ke state tidak terpilih
                    document.querySelectorAll('.student-name').forEach(el => {
                        el.classList.remove('present');
                    });
                    
                    // Tandai siswa yang dipilih
                    this.classList.add('present');
                    appState.selectedStudent = student;
                    
                    // Aktifkan tombol save
                    document.getElementById('save-2').disabled = false;
                });
                attendanceList.appendChild(studentElement);
            });

            // Setup timer
            setupTimer();
            
            // Setup input observers untuk scene 7
            setupObservationInputs();
            
            // Setup kuis untuk scene 8
            setupQuiz();
        }

        function setupEventListeners() {
            // Tombol navigasi
            document.getElementById('next-1').addEventListener('click', () => navigateToScene(2));
            document.getElementById('prev-2').addEventListener('click', () => navigateToScene(1));
            document.getElementById('next-2').addEventListener('click', () => navigateToScene(3));
            document.getElementById('prev-3').addEventListener('click', () => navigateToScene(2));
            document.getElementById('next-3').addEventListener('click', () => navigateToScene(4));
            document.getElementById('prev-4').addEventListener('click', () => navigateToScene(3));
            document.getElementById('next-4').addEventListener('click', () => navigateToScene(5));
            document.getElementById('prev-5').addEventListener('click', () => navigateToScene(4));
            document.getElementById('next-5').addEventListener('click', () => navigateToScene(6));
            document.getElementById('prev-6').addEventListener('click', () => navigateToScene(5));
            document.getElementById('next-6').addEventListener('click', () => navigateToScene(7));
            document.getElementById('prev-7').addEventListener('click', () => navigateToScene(6));
            document.getElementById('next-7').addEventListener('click', () => navigateToScene(8));
            document.getElementById('prev-8').addEventListener('click', () => navigateToScene(7));
            document.getElementById('next-8').addEventListener('click', () => navigateToScene(9));
            document.getElementById('prev-9').addEventListener('click', () => navigateToScene(8));
            document.getElementById('restart-learning').addEventListener('click', resetApp);

            // Tombol save
            document.getElementById('save-1').addEventListener('click', () => saveScene(1));
            document.getElementById('save-2').addEventListener('click', () => saveScene(2));
            document.getElementById('save-3').addEventListener('click', () => saveScene(3));
            document.getElementById('save-4').addEventListener('click', () => saveScene(4));
            document.getElementById('save-5').addEventListener('click', () => saveScene(5));
            document.getElementById('save-6').addEventListener('click', () => saveScene(6));
            document.getElementById('save-7').addEventListener('click', () => saveScene(7));
            document.getElementById('save-8').addEventListener('click', () => saveScene(8));
            document.getElementById('save-9').addEventListener('click', () => saveScene(9));

            // Validasi input hipotesis
            const hypothesisInput = document.getElementById('hypothesis-input');
            if (hypothesisInput) {
                hypothesisInput.addEventListener('input', function() {
                    appState.hypothesis = this.value;
                    const saveButton = document.getElementById('save-5');
                    const nextButton = document.getElementById('next-5');
                    
                    if (this.value.trim().length > 0) {
                        saveButton.disabled = false;
                        nextButton.disabled = false;
                    } else {
                        saveButton.disabled = true;
                        nextButton.disabled = true;
                    }
                });
            }

            // Tombol periksa kuis
            document.getElementById('check-quiz').addEventListener('click', checkQuizAnswers);
        }

        function setupObservationInputs() {
            // Setup untuk scene 7 - observasi
            const observationInputs = document.querySelectorAll('#scene-7 .observation-table input');
            observationInputs.forEach(input => {
                input.addEventListener('input', function() {
                    const row = this.closest('tr');
                    const molecule = row.cells[0].textContent.toLowerCase().replace(/[^a-z0-9]/g, '');
                    const field = this.closest('td').cellIndex === 1 ? 'pairs' : 
                                 this.closest('td').cellIndex === 2 ? 'type' : 'strength';
                    
                    appState.observations[molecule][field] = this.value;
                    
                    // Simpan state otomatis
                    saveStateToStorage();
                });
            });
        }

        function setupQuiz() {
            // Setup untuk scene 8 - kuis
            const quizOptions = document.querySelectorAll('.quiz-option');
            quizOptions.forEach(option => {
                option.addEventListener('click', function() {
                    // Reset pilihan untuk pertanyaan yang sama
                    const question = this.closest('.quiz-question');
                    const options = question.querySelectorAll('.quiz-option');
                    options.forEach(opt => opt.classList.remove('selected'));
                    
                    // Pilih opsi ini
                    this.classList.add('selected');
                    
                    // Simpan jawaban
                    const questionIndex = Array.from(document.querySelectorAll('.quiz-question')).indexOf(question);
                    appState.quizAnswers[questionIndex] = this.getAttribute('data-correct') === 'true';
                    
                    // Simpan state otomatis
                    saveStateToStorage();
                });
            });
        }

        function checkQuizAnswers() {
            let correctCount = 0;
            const totalQuestions = document.querySelectorAll('.quiz-question').length;
            
            // Hitung jawaban yang benar
            for (let i = 0; i < totalQuestions; i++) {
                if (appState.quizAnswers[i] === true) {
                    correctCount++;
                }
            }
            
            // Tampilkan hasil
            const resultElement = document.getElementById('quiz-result');
            const percentage = (correctCount / totalQuestions) * 100;
            
            let message = '';
            if (percentage >= 80) {
                message = `<i class="fas fa-star"></i> Excellent! Anda menjawab ${correctCount} dari ${totalQuestions} pertanyaan dengan benar (${percentage}%)`;
            } else if (percentage >= 60) {
                message = `<i class="fas fa-thumbs-up"></i> Bagus! Anda menjawab ${correctCount} dari ${totalQuestions} pertanyaan dengan benar (${percentage}%)`;
            } else {
                message = `<i class="fas fa-redo"></i> Coba lagi! Anda menjawab ${correctCount} dari ${totalQuestions} pertanyaan dengan benar (${percentage}%)`;
            }
            
            resultElement.innerHTML = message;
            resultElement.style.display = 'block';
            
            // Scroll ke hasil
            resultElement.scrollIntoView({ behavior: 'smooth' });
        }

        function setupTimer() {
            // Timer untuk scene 7
            const countdownElement = document.getElementById('countdown');
            if (countdownElement) {
                updateTimerDisplay();
            }
        }

        function startTimer() {
            if (appState.timerRunning) return;
            
            appState.timerRunning = true;
            appState.timerInterval = setInterval(function() {
                if (appState.timerValue <= 0) {
                    clearInterval(appState.timerInterval);
                    appState.timerRunning = false;
                    document.getElementById('countdown').textContent = "00:00";
                    document.getElementById('countdown').style.color = "#ffa726";
                    
                    // Tampilkan notifikasi waktu habis
                    showNotification("Waktu investigasi telah habis! Silakan lanjutkan ke analisis data.", "info");
                } else {
                    appState.timerValue--;
                    updateTimerDisplay();
                }
            }, 1000);
        }

        function pauseTimer() {
            if (appState.timerInterval) {
                clearInterval(appState.timerInterval);
                appState.timerRunning = false;
            }
        }

        function updateTimerDisplay() {
            const countdownElement = document.getElementById('countdown');
            if (countdownElement) {
                const minutes = Math.floor(appState.timerValue / 60);
                const seconds = appState.timerValue % 60;
                countdownElement.textContent = `${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`;
            }
        }

        function navigateToScene(sceneNumber) {
            // Jika pindah dari scene 7, pause timer
            if (appState.currentScene === 7) {
                pauseTimer();
            }
            
            // Jika pindah ke scene 7, start timer
            if (sceneNumber === 7 && !appState.timerRunning && appState.timerValue > 0) {
                startTimer();
            }
            
            // Sembunyikan scene aktif
            document.querySelector('.scene-container.active').classList.remove('active');
            
            // Tampilkan scene yang dituju
            document.getElementById(`scene-${sceneNumber}`).classList.add('active');
            
            // Update state
            appState.currentScene = sceneNumber;
            
            // Simpan state ke localStorage
            saveStateToStorage();
            
            // Update progress bar
            updateProgressBar();
            
            // Scroll ke atas
            window.scrollTo(0, 0);
        }

        function saveScene(sceneNumber) {
            // Tandai scene sebagai selesai
            appState.completedScenes[sceneNumber] = true;
            
            // Simpan data scene berdasarkan nomor scene
            switch(sceneNumber) {
                case 1:
                    enableNextButton(1);
                    break;
                case 2:
                    if (appState.selectedStudent) {
                        enableNextButton(2);
                        document.getElementById('attendance-complete').style.display = 'block';
                        appState.attendance[appState.selectedStudent] = true;
                    }
                    break;
                case 3:
                    enableNextButton(3);
                    break;
                case 4:
                    enableNextButton(4);
                    break;
                case 5:
                    if (appState.hypothesis.trim().length > 0) {
                        enableNextButton(5);
                        const completeElement = document.getElementById('hypothesis-complete');
                        if (completeElement) completeElement.style.display = 'block';
                    }
                    break;
                case 6:
                    enableNextButton(6);
                    const scene6Complete = document.getElementById('scene6-complete');
                    if (scene6Complete) scene6Complete.style.display = 'block';
                    break;
                case 7:
                    enableNextButton(7);
                    break;
                case 8:
                    enableNextButton(8);
                    break;
                case 9:
                    // Scene 9 tidak perlu enable next button
                    break;
            }
            
            // Simpan state ke localStorage
            saveStateToStorage();
            
            // Tampilkan notifikasi sukses
            showSaveNotification(sceneNumber);
        }

        function enableNextButton(sceneNumber) {
            const nextButton = document.getElementById(`next-${sceneNumber}`);
            if (nextButton) {
                nextButton.disabled = false;
            }
        }

        function updateProgressBar() {
            const progress = (appState.currentScene / appState.totalScenes) * 100;
            document.getElementById('progress').style.width = `${progress}%`;
        }

        function saveStateToStorage() {
            localStorage.setItem('ikatanKovalenAppState', JSON.stringify(appState));
        }

        function loadStateFromStorage() {
            const savedState = localStorage.getItem('ikatanKovalenAppState');
            if (savedState) {
                const parsedState = JSON.parse(savedState);
                Object.assign(appState, parsedState);
                
                // Restore UI berdasarkan state yang disimpan
                restoreUIFromState();
            }
        }

        function restoreUIFromState() {
            // Restore absensi
            if (appState.selectedStudent) {
                const studentElements = document.querySelectorAll('.student-name');
                studentElements.forEach(element => {
                    if (element.textContent === appState.selectedStudent) {
                        element.classList.add('present');
                        document.getElementById('save-2').disabled = false;
                        document.getElementById('attendance-complete').style.display = 'block';
                    }
                });
            }
            
            // Restore hipotesis
            if (appState.hypothesis) {
                const hypothesisInput = document.getElementById('hypothesis-input');
                if (hypothesisInput) {
                    hypothesisInput.value = appState.hypothesis;
                    document.getElementById('save-5').disabled = false;
                    document.getElementById('next-5').disabled = false;
                    document.getElementById('hypothesis-complete').style.display = 'block';
                }
            }
            
            // Restore observasi
            if (appState.observations) {
                const observationInputs = document.querySelectorAll('#scene-7 .observation-table input');
                observationInputs.forEach(input => {
                    const row = input.closest('tr');
                    const molecule = row.cells[0].textContent.toLowerCase().replace(/[^a-z0-9]/g, '');
                    const field = input.closest('td').cellIndex === 1 ? 'pairs' : 
                                 input.closest('td').cellIndex === 2 ? 'type' : 'strength';
                    
                    if (appState.observations[molecule] && appState.observations[molecule][field]) {
                        input.value = appState.observations[molecule][field];
                    }
                });
            }
            
            // Restore jawaban kuis
            if (appState.quizAnswers) {
                const quizQuestions = document.querySelectorAll('.quiz-question');
                quizQuestions.forEach((question, index) => {
                    if (appState.quizAnswers[index] !== undefined) {
                        const options = question.querySelectorAll('.quiz-option');
                        // Hanya simpan state, tidak perlu menandai opsi karena akan dilakukan saat interaksi
                    }
                });
            }
            
            // Restore status scene yang sudah diselesaikan
            for (let scene in appState.completedScenes) {
                if (appState.completedScenes[scene]) {
                    enableNextButton(parseInt(scene));
                    
                    // Tampilkan pesan penyelesaian
                    if (parseInt(scene) === 2) {
                        document.getElementById('attendance-complete').style.display = 'block';
                    } else if (parseInt(scene) === 5) {
                        const completeElement = document.getElementById('hypothesis-complete');
                        if (completeElement) completeElement.style.display = 'block';
                    } else if (parseInt(scene) === 6) {
                        const scene6Complete = document.getElementById('scene6-complete');
                        if (scene6Complete) scene6Complete.style.display = 'block';
                    }
                }
            }
            
            // Restore timer
            updateTimerDisplay();
            
            // Navigate ke scene terakhir yang diakses
            navigateToScene(appState.currentScene);
        }

        function showSaveNotification(sceneNumber) {
            const saveButton = document.getElementById(`save-${sceneNumber}`);
            const originalText = saveButton.innerHTML;
            const originalBackground = saveButton.style.background;
            
            saveButton.innerHTML = '<i class="fas fa-check"></i> Tersimpan!';
            saveButton.style.background = 'linear-gradient(135deg, #96ceb4 0%, #7ac5a8 100%)';
            
            setTimeout(() => {
                saveButton.innerHTML = originalText;
                saveButton.style.background = originalBackground;
            }, 2000);
        }

        function showNotification(message, type = 'info') {
            // Buat elemen notifikasi
            const notification = document.createElement('div');
            notification.className = `notification ${type}`;
            notification.innerHTML = `
                <div class="notification-content">
                    <i class="fas fa-${type === 'info' ? 'info-circle' : 'check-circle'}"></i>
                    <span>${message}</span>
                </div>
            `;
            
            // Tambahkan ke body
            document.body.appendChild(notification);
            
            // Animasi masuk
            setTimeout(() => {
                notification.classList.add('show');
            }, 100);
            
            // Hapus setelah 3 detik
            setTimeout(() => {
                notification.classList.remove('show');
                setTimeout(() => {
                    document.body.removeChild(notification);
                }, 300);
            }, 3000);
        }

        function resetApp() {
            // Konfirmasi reset
            if (confirm('Apakah Anda yakin ingin mengulang pembelajaran dari awal? Semua progress akan dihapus.')) {
                // Hapus state dari localStorage
                localStorage.removeItem('ikatanKovalenAppState');
                
                // Reset state aplikasi
                appState.currentScene = 1;
                appState.progress = 0;
                appState.attendance = {};
                appState.selectedStudent = null;
                appState.hypothesis = "";
                appState.completedScenes = {};
                appState.timerRunning = false;
                appState.timerValue = 25 * 60;
                appState.observations = {
                    h2: { pairs: "", type: "", strength: "" },
                    o2: { pairs: "", type: "", strength: "" },
                    n2: { pairs: "", type: "", strength: "" }
                };
                appState.conclusion = "";
                appState.quizAnswers = {};
                
                // Hentikan timer jika berjalan
                if (appState.timerInterval) {
                    clearInterval(appState.timerInterval);
                }
                
                // Navigasi ke scene 1
                navigateToScene(1);
                
                // Tampilkan notifikasi
                showNotification("Pembelajaran telah direset. Mulai dari awal!", "info");
            }
        }
    </script>

    <!-- Font Awesome untuk ikon -->
    <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
</body>
</html>
