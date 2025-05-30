<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pensamiento</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #0f172a, #1e293b);
            color: #e2e8f0;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            padding: 20px;
            overflow-x: hidden;
            position: relative;
        }
        
        .container {
            max-width: 900px;
            width: 100%;
            margin: 0 auto;
            flex: 1;
        }
        
        header {
            text-align: center;
            padding: 40px 20px 20px;
            position: relative;
            z-index: 10;
        }
        
        .logo {
            font-size: 3.5rem;
            margin-bottom: 20px;
            color: #60a5fa;
            text-shadow: 0 0 20px rgba(96, 165, 250, 0.7);
        }
        
        h1 {
            font-size: 3rem;
            background: linear-gradient(to right, #93c5fd, #60a5fa);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 15px;
        }
        
        .subtitle {
            font-size: 1.3rem;
            opacity: 0.9;
            max-width: 600px;
            margin: 0 auto;
            line-height: 1.6;
        }
        
        .main-content {
            background: rgba(15, 23, 42, 0.8);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            margin: 30px 0;
            border: 1px solid rgba(96, 165, 250, 0.3);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
        }
        
        .input-group {
            margin-bottom: 30px;
        }
        
        textarea {
            width: 100%;
            background: rgba(30, 41, 59, 0.7);
            border: 2px solid rgba(96, 165, 250, 0.5);
            border-radius: 15px;
            padding: 20px;
            color: white;
            font-size: 1.2rem;
            resize: vertical;
            min-height: 150px;
            transition: all 0.3s ease;
        }
        
        textarea:focus {
            outline: none;
            border-color: #60a5fa;
            box-shadow: 0 0 20px rgba(96, 165, 250, 0.5);
        }
        
        textarea::placeholder {
            color: #94a3b8;
        }
        
        .btn-container {
            display: flex;
            justify-content: center;
            margin-top: 20px;
        }
        
        button {
            background: linear-gradient(90deg, #3b82f6, #60a5fa);
            color: white;
            border: none;
            padding: 15px 40px;
            font-size: 1.2rem;
            border-radius: 50px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(59, 130, 246, 0.4);
        }
        
        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(59, 130, 246, 0.6);
        }
        
        button:disabled {
            opacity: 0.7;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }
        
        .response-container {
            margin-top: 40px;
            display: none;
        }
        
        .response-header {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .response-header i {
            font-size: 2rem;
            color: #60a5fa;
        }
        
        .response-content {
            background: rgba(30, 41, 59, 0.7);
            border-radius: 15px;
            padding: 30px;
            border-left: 4px solid #3b82f6;
            font-size: 1.2rem;
            line-height: 1.8;
            position: relative;
            min-height: 150px;
        }
        
        .thinking {
            display: none;
            text-align: center;
            padding: 30px;
        }
        
        .thinking .dot-flashing {
            display: inline-block;
            position: relative;
            width: 10px;
            height: 10px;
            border-radius: 5px;
            background-color: #60a5fa;
            color: #60a5fa;
            animation: dotFlashing 1s infinite linear alternate;
            animation-delay: 0.5s;
            margin: 0 5px;
        }
        
        .thinking .dot-flashing::before, .thinking .dot-flashing::after {
            content: '';
            display: inline-block;
            position: absolute;
            top: 0;
            width: 10px;
            height: 10px;
            border-radius: 5px;
            background-color: #60a5fa;
            color: #60a5fa;
        }
        
        .thinking .dot-flashing::before {
            left: -15px;
            animation: dotFlashing 1s infinite alternate;
            animation-delay: 0s;
        }
        
        .thinking .dot-flashing::after {
            left: 15px;
            animation: dotFlashing 1s infinite alternate;
            animation-delay: 1s;
        }
        
        @keyframes dotFlashing {
            0% { background-color: #60a5fa; }
            50%, 100% { background-color: rgba(96, 165, 250, 0.2); }
        }
        
        .history-container {
            margin-top: 40px;
            display: none;
        }
        
        .history-title {
            font-size: 1.5rem;
            margin-bottom: 20px;
            color: #93c5fd;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .history-item {
            background: rgba(30, 41, 59, 0.7);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 15px;
            border-left: 3px solid #3b82f6;
        }
        
        .history-question {
            font-weight: bold;
            margin-bottom: 10px;
            color: #93c5fd;
        }
        
        .history-answer {
            line-height: 1.6;
        }
        
        .signature {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 30px;
            margin: 40px 0;
            flex-wrap: wrap;
        }
        
        .credits {
            font-size: 1.3rem;
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .instagram {
            display: flex;
            align-items: center;
            gap: 10px;
            background: linear-gradient(45deg, #405de6, #5851db, #833ab4, #c13584, #e1306c, #fd1d1d);
            padding: 12px 25px;
            border-radius: 50px;
            text-decoration: none;
            color: white;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .instagram:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 20px rgba(253, 29, 29, 0.4);
        }
        
        footer {
            text-align: center;
            padding: 30px 0;
            color: #94a3b8;
            font-size: 0.9rem;
        }
        
        .decoration {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: 1;
            overflow: hidden;
        }
        
        .particle {
            position: absolute;
            border-radius: 50%;
            background: rgba(96, 165, 250, 0.1);
            animation: float 15s infinite linear;
        }
        
        @keyframes float {
            0% { transform: translateY(0) translateX(0) rotate(0deg); }
            100% { transform: translateY(-100vh) translateX(100px) rotate(360deg); }
        }
        
        @media (max-width: 768px) {
            h1 {
                font-size: 2.5rem;
            }
            
            .main-content {
                padding: 30px 20px;
            }
            
            .logo {
                font-size: 2.5rem;
            }
        }
    </style>
</head>
<body>
    <div class="decoration" id="particles"></div>
    
    <div class="container">
        <header>
            <div class="logo">
                <i class="fas fa-brain"></i>
            </div>
            <h1>Pensamiento</h1>
            <p class="subtitle">Una inteligencia avanzada para explorar las grandes preguntas de la existencia, la mente y el universo</p>
        </header>
        
        <div class="main-content">
            <div class="input-group">
                <textarea id="questionInput" placeholder="Escribe tu pregunta filosófica, científica o existencial..."></textarea>
                <div class="btn-container">
                    <button id="askButton">
                        <i class="fas fa-paper-plane"></i>
                        Consultar al Pensamiento
                    </button>
                </div>
            </div>
            
            <div class="thinking" id="thinkingIndicator">
                <div class="dot-flashing"></div>
                <p>El Pensamiento está reflexionando...</p>
            </div>
            
            <div class="response-container" id="responseContainer">
                <div class="response-header">
                    <i class="fas fa-robot"></i>
                    <h2>Respuesta del Pensamiento</h2>
                </div>
                <div class="response-content" id="responseContent">
                    <!-- La respuesta aparecerá aquí -->
                </div>
            </div>
            
            <div class="history-container" id="historyContainer">
                <h3 class="history-title">
                    <i class="fas fa-history"></i>
                    Historial de Consultas
                </h3>
                <div id="historyList">
                    <!-- El historial aparecerá aquí -->
                </div>
            </div>
        </div>
        
        <div class="signature">
            <div class="credits">
                <i class="fas fa-code"></i>
                <span>Creado por: Alexander</span>
            </div>
            
            <a href="https://www.instagram.com/7alex.07/" class="
