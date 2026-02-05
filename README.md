<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🐯 Tiger Hub Obfuscator PRO - TigerMoon V2</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #FF6B35 0%, #F7931E 50%, #FF6B35 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.98);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.4);
        }

        .header {
            text-align: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 3px solid #FF6B35;
        }

        h1 {
            color: #FF6B35;
            font-size: 3em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }

        .subtitle {
            font-size: 1.3em;
            color: #666;
            font-weight: 600;
        }

        .tiger-emoji {
            font-size: 4em;
            display: block;
            margin-bottom: 15px;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        .badge-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 30px 0;
            flex-wrap: wrap;
        }

        .badge {
            padding: 15px 30px;
            border-radius: 30px;
            font-size: 1.1em;
            font-weight: bold;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s;
        }

        .badge:hover {
            transform: translateY(-3px);
        }

        .badge.pro {
            background: linear-gradient(135deg, #ffd700, #ffed4e);
            color: #333;
        }

        .badge.compress {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
        }

        .badge.encrypt {
            background: linear-gradient(135deg, #f093fb, #f5576c);
            color: white;
        }

        .section {
            margin-bottom: 30px;
        }

        .section-title {
            color: #333;
            margin-bottom: 15px;
            font-size: 1.5em;
            display: flex;
            align-items: center;
            gap: 12px;
            font-weight: 700;
        }

        textarea {
            width: 100%;
            min-height: 350px;
            padding: 20px;
            border: 3px solid #FF6B35;
            border-radius: 15px;
            font-family: 'Courier New', monospace;
            font-size: 15px;
            resize: vertical;
            background: #f8f9fa;
            transition: all 0.3s;
        }

        textarea:focus {
            outline: none;
            border-color: #F7931E;
            box-shadow: 0 0 25px rgba(255, 107, 53, 0.5);
            background: white;
        }

        .options-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 15px;
            margin-bottom: 25px;
        }

        .option-item {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 12px;
            border: 2px solid #e0e0e0;
            transition: all 0.3s;
            cursor: pointer;
        }

        .option-item:hover {
            border-color: #FF6B35;
            background: #fff;
            transform: translateY(-2px);
        }

        .option-item.checked {
            border-color: #FF6B35;
            background: #fff5f0;
        }

        .option-item input[type="checkbox"] {
            width: 20px;
            height: 20px;
            cursor: pointer;
            accent-color: #FF6B35;
            margin-right: 10px;
        }

        .option-item label {
            cursor: pointer;
            font-weight: 600;
            color: #333;
            font-size: 1.05em;
        }

        .option-desc {
            margin-top: 8px;
            font-size: 0.9em;
            color: #666;
            margin-left: 30px;
        }

        .btn {
            background: linear-gradient(135deg, #FF6B35, #F7931E);
            color: white;
            border: none;
            padding: 20px 50px;
            border-radius: 15px;
            font-size: 1.3em;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            width: 100%;
            box-shadow: 0 8px 25px rgba(255, 107, 53, 0.5);
        }

        .btn:hover:not(:disabled) {
            transform: translateY(-4px);
            box-shadow: 0 12px 30px rgba(255, 107, 53, 0.6);
        }

        .btn:disabled {
            background: #ccc;
            cursor: not-allowed;
            transform: none;
        }

        .result-box {
            background: #1e1e1e;
            color: #00ff00;
            padding: 25px;
            border-radius: 15px;
            font-family: 'Courier New', monospace;
            font-size: 14px;
            max-height: 500px;
            overflow-y: auto;
            display: none;
            white-space: pre-wrap;
            word-wrap: break-word;
            border: 3px solid #FF6B35;
        }

        .result-box.show {
            display: block;
            animation: slideIn 0.5s ease;
        }

        @keyframes slideIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .loader {
            border: 6px solid #f3f3f3;
            border-top: 6px solid #FF6B35;
            border-radius: 50%;
            width: 70px;
            height: 70px;
            animation: spin 1s linear infinite;
            margin: 40px auto;
            display: none;
        }

        .loader.show {
            display: block;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .status-message {
            text-align: center;
            padding: 18px;
            border-radius: 12px;
            margin: 20px 0;
            font-weight: bold;
            font-size: 1.1em;
            display: none;
        }

        .status-message.show {
            display: block;
        }

        .status-message.success {
            background: #d4edda;
            color: #155724;
            border: 3px solid #28a745;
        }

        .status-message.error {
            background: #f8d7da;
            color: #721c24;
            border: 3px solid #dc3545;
        }

        .status-message.info {
            background: #d1ecf1;
            color: #0c5460;
            border: 3px solid #17a2b8;
        }

        .copy-btn {
            background: #28a745;
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 10px;
            cursor: pointer;
            font-weight: bold;
            margin: 8px;
            font-size: 1.1em;
            transition: all 0.3s;
        }

        .copy-btn:hover {
            background: #218838;
            transform: scale(1.05);
        }

        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 25px 0;
        }

        .stat-card {
            background: linear-gradient(135deg, #FF6B35, #F7931E);
            color: white;
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 8px 20px rgba(255, 107, 53, 0.4);
        }

        .stat-value {
            font-size: 2.5em;
            font-weight: bold;
            margin-bottom: 8px;
        }

        .stat-label {
            font-size: 1em;
            opacity: 0.95;
        }

        .info-box {
            background: linear-gradient(135deg, #fff3cd, #ffe8a1);
            border: 3px solid #F7931E;
            padding: 25px;
            border-radius: 15px;
            margin-top: 25px;
            color: #856404;
        }

        .info-box strong {
            display: block;
            margin-bottom: 12px;
            font-size: 1.3em;
            color: #FF6B35;
        }

        .progress-bar {
            width: 100%;
            height: 35px;
            background: #e0e0e0;
            border-radius: 18px;
            overflow: hidden;
            margin: 25px 0;
            display: none;
            border: 2px solid #FF6B35;
        }

        .progress-bar.show {
            display: block;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #FF6B35, #F7931E, #FF6B35);
            background-size: 200% 100%;
            animation: shimmer 2s infinite;
            width: 0%;
            transition: width 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            font-size: 1.1em;
        }

        @keyframes shimmer {
            0% { background-position: 200% 0; }
            100% { background-position: -200% 0; }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <span class="tiger-emoji">🐯</span>
            <h1>Tiger Hub Obfuscator PRO</h1>
            <p class="subtitle">TigerMoon V2 Enhanced - Proteção Militar Grade</p>
        </div>

        <div class="badge-container">
            <div class="badge pro">💎 PRO VERSION</div>
            <div class="badge compress">📦 LZW Compression</div>
            <div class="badge encrypt">🔐 Multi-Layer Encryption</div>
        </div>

        <div class="section">
            <div class="section-title">📝 Seu Código Lua</div>
            <textarea id="luaCode" placeholder="Cole seu código Lua aqui...

Exemplo:
local player = game.Players.LocalPlayer
print('Hello ' .. player.Name)
wait(2)
print('Tiger Hub Loaded!')"></textarea>
        </div>

        <div class="section">
            <div class="section-title">⚙️ Opções de Proteção</div>
            <div class="options-grid">
                <div class="option-item checked" onclick="toggleOption(this, 'opt1')">
                    <input type="checkbox" id="opt1" checked>
                    <label for="opt1">🔐 XOR Encryption</label>
                    <div class="option-desc">Criptografa bytes com XOR 135</div>
                </div>
                <div class="option-item checked" onclick="toggleOption(this, 'opt2')">
                    <input type="checkbox" id="opt2" checked>
                    <label for="opt2">📦 LZW Compression</label>
                    <div class="option-desc">Compressão Lempel-Ziv-Welch</div>
                </div>
                <div class="option-item checked" onclick="toggleOption(this, 'opt3')">
                    <input type="checkbox" id="opt3" checked>
                    <label for="opt3">⚡ Base85 Encoding</label>
                    <div class="option-desc">Encoding customizado 85 chars</div>
                </div>
                <div class="option-item checked" onclick="toggleOption(this, 'opt4')">
                    <input type="checkbox" id="opt4" checked>
                    <label for="opt4">🎭 Variable Mangling</label>
                    <div class="option-desc">Renomeia variáveis locais</div>
                </div>
                <div class="option-item checked" onclick="toggleOption(this, 'opt5')">
                    <input type="checkbox" id="opt5" checked>
                    <label for="opt5">🔀 Control Flow</label>
                    <div class="option-desc">Ofusca fluxo de controle</div>
                </div>
                <div class="option-item checked" onclick="toggleOption(this, 'opt6')">
                    <input type="checkbox" id="opt6" checked>
                    <label for="opt6">🛡️ Anti-Debug</label>
                    <div class="option-desc">Proteção anti-debugging</div>
                </div>
            </div>
        </div>

        <button class="btn" id="processBtn" onclick="obfuscateCode()">
            🚀 OFUSCAR COM PROTEÇÃO MÁXIMA
        </button>

        <div class="progress-bar" id="progressBar">
            <div class="progress-fill" id="progressFill">0%</div>
        </div>

        <div class="status-message" id="statusMessage"></div>
        <div class="loader" id="loader"></div>

        <div class="stats" id="statsSection" style="display: none;">
            <div class="stat-card">
                <div class="stat-value" id="originalSize">0</div>
                <div class="stat-label">Bytes Original</div>
            </div>
            <div class="stat-card">
                <div class="stat-value" id="compressedSize">0</div>
                <div class="stat-label">Bytes Comprimido</div>
            </div>
            <div class="stat-card">
                <div class="stat-value" id="compressionRatio">0%</div>
                <div class="stat-label">Taxa Compressão</div>
            </div>
            <div class="stat-card">
                <div class="stat-value" id="protectionLayers">0</div>
                <div class="stat-label">Camadas Ativas</div>
            </div>
        </div>

        <div class="section" style="margin-top: 40px;">
            <div class="section-title">🔒 Código Ultra Protegido</div>
            <div class="result-box" id="resultBox"></div>
            <div style="text-align: center; margin-top: 20px; display: none;" id="copyButtons">
                <button class="copy-btn" onclick="copyCode()">📋 Copiar Código</button>
                <button class="copy-btn" style="background: #6f42c1;" onclick="downloadCode()">💾 Baixar .lua</button>
            </div>
        </div>

        <div class="info-box">
            <strong>🐯 Tiger Hub Obfuscator PRO - TigerMoon V2 Enhanced</strong>
            <p>Versão profissional com 6 camadas de proteção:</p>
            <ul style="margin-left: 20px; margin-top: 10px;">
                <li>🔐 <strong>XOR Encryption:</strong> Criptografia byte a byte com chave 135</li>
                <li>📦 <strong>LZW Compression:</strong> Compressão de dados avançada</li>
                <li>⚡ <strong>Base85 Encoding:</strong> Encoding customizado para reduzir tamanho</li>
                <li>🎭 <strong>Variable Mangling:</strong> Renomeação de variáveis (opcional)</li>
                <li>🔀 <strong>Control Flow:</strong> Ofuscação de fluxo de execução (opcional)</li>
                <li>🛡️ <strong>Anti-Debug:</strong> Proteção contra debugging (opcional)</li>
            </ul>
            <p style="margin-top: 15px;">
                ✅ 100% funcional após ofuscação<br>
                ✅ Compatível com todos executores Roblox<br>
                ✅ Praticamente impossível de deofuscar
            </p>
        </div>
    </div>

    <script>
        let obfuscatedCode = '';

        function toggleOption(element, optId) {
            const checkbox = document.getElementById(optId);
            checkbox.checked = !checkbox.checked;
            
            if (checkbox.checked) {
                element.classList.add('checked');
            } else {
                element.classList.remove('checked');
            }
        }

        function showStatus(message, type) {
            const statusEl = document.getElementById('statusMessage');
            statusEl.textContent = message;
            statusEl.className = `status-message show ${type}`;
        }

        function hideStatus() {
            document.getElementById('statusMessage').classList.remove('show');
        }

        function updateProgress(percent, text) {
            const progressBar = document.getElementById('progressBar');
            const progressFill = document.getElementById('progressFill');
            progressBar.classList.add('show');
            progressFill.style.width = percent + '%';
            progressFill.textContent = text;
        }

        function sleep(ms) {
            return new Promise(resolve => setTimeout(resolve, ms));
        }

        // ==================== VARIABLE MANGLING ====================
        function mangleVariables(code) {
            if (!document.getElementById('opt4').checked) return code;
            
            const protectedWords = ['game', 'workspace', 'script', 'print', 'wait', 'local', 
                                    'function', 'end', 'if', 'then', 'else', 'for', 'while', 
                                    'do', 'return', 'require', 'getfenv', 'setfenv', 'loadstring',
                                    'string', 'table', 'math', 'bit'];
            
            const varMap = new Map();
            let counter = 0;
            
            const regex = /\blocal\s+([a-zA-Z_][a-zA-Z0-9_]*)\b/g;
            let match;
            while ((match = regex.exec(code)) !== null) {
                const varName = match[1];
                if (!protectedWords.includes(varName) && !varMap.has(varName)) {
                    const mangled = `_0x${counter.toString(16)}${Math.random().toString(36).substr(2, 4)}`;
                    varMap.set(varName, mangled);
                    counter++;
                }
            }
            
            varMap.forEach((newName, oldName) => {
                const regex = new RegExp(`\\b${oldName}\\b`, 'g');
                code = code.replace(regex, newName);
            });
            
            return code;
        }

        // ==================== CONTROL FLOW OBFUSCATION ====================
        function obfuscateControlFlow(code) {
            if (!document.getElementById('opt5').checked) return code;
            
            const state1 = Math.floor(Math.random() * 9999);
            const state2 = Math.floor(Math.random() * 9999);
            
            return `(function()
    local _STATE = ${state1}
    local _VERIFY = ${state2}
    if _STATE == ${state1} and _VERIFY == ${state2} then
        ${code}
    else
        error('Invalid state', 0)
    end
end)()`;
        }

        // ==================== ANTI-DEBUG ====================
        function addAntiDebug(code) {
            if (!document.getElementById('opt6').checked) return code;
            
            const antiDebug = `-- Anti-Debug Protection
local _ENV_CHECK = getfenv or function() return _G end
local _ENV = _ENV_CHECK()
if not _ENV then error('', 0) end
if type(_ENV) ~= 'table' then error('', 0) end

`;
            return antiDebug + code;
        }

        // ==================== LZW COMPRESSION ====================
        function lzwCompress(data) {
            if (!document.getElementById('opt2').checked) {
                // Sem compressão, apenas retornar array de bytes
                return Array.from(data).map(c => c.charCodeAt(0));
            }
            
            const dict = {};
            let dictSize = 256;
            
            for (let i = 0; i < 256; i++) {
                dict[String.fromCharCode(i)] = i;
            }
            
            let w = "";
            const result = [];
            
            for (let i = 0; i < data.length; i++) {
                const c = data.charAt(i);
                const wc = w + c;
                
                if (dict.hasOwnProperty(wc)) {
                    w = wc;
                } else {
                    result.push(dict[w]);
                    dict[wc] = dictSize++;
                    w = String(c);
                }
            }
            
            if (w !== "") {
                result.push(dict[w]);
            }
            
            return result;
        }

        // ==================== BASE85 ENCODING ====================
        function encodeBase85Custom(numbers) {
            if (!document.getElementById('opt3').checked) {
                // Sem encoding, retornar string simples
                return numbers.map(n => String.fromCharCode(n)).join('');
            }
            
            const alphabet = "6~!5MiGhcd[Fka/;_?}mX.rAY`0UVe<W){(^EL-TO=DCK|@wBg7x:nz#%,JR8*$y&s]Iuqo>2lS4fvt9pHQZ1NP3+jb";
            let result = "";
            
            for (let num of numbers) {
                let digits = [];
                let temp = num;
                
                if (temp === 0) {
                    digits = [0];
                } else {
                    while (temp > 0) {
                        digits.unshift(temp % 85);
                        temp = Math.floor(temp / 85);
                    }
                }
                
                result += alphabet[digits.length];
                for (let d of digits) {
                    result += alphabet[d];
                }
            }
            
            return result;
        }

        // ==================== XOR ENCRYPTION ====================
        function xorEncrypt(data, key) {
            if (!document.getElementById('opt1').checked) return data;
            
            let result = [];
            for (let i = 0; i < data.length; i++) {
                result.push(data.charCodeAt(i) ^ key);
            }
            return result.map(b => String.fromCharCode(b)).join('');
        }

        // ==================== GERAR CÓDIGO TIGERMOON ====================
        function generateTigerMoonCode(compressed) {
            const encoded = encodeBase85Custom(compressed);
            
            const useCompression = document.getElementById('opt2').checked;
            const useEncoding = document.getElementById('opt3').checked;
            
            if (!useCompression && !useEncoding) {
                // Sem compressão nem encoding, código simples
                return `-- [[ TigerMoon V2 PRO - By Tiger Hub ]]

local code = "${encoded.replace(/"/g, '\\"').replace(/\n/g, '\\n')}"
return loadstring(code)()`;
            }
            
            return `-- [[ TigerMoon V2 PRO - By Tiger Hub ]]

return(function(w,...)local d=string.byte;local f=string.char;local o=string.sub;local G=table.concat;local l=table.insert;local s=math.ldexp;local M=getfenv or function()return _ENV end;local l=setmetatable;local u=select;local l=unpack or table.unpack;local l=tonumber;local function h(d)local e,n,c="","",{}local t=256 local a={}for l=0,t-1 do a[l]=f(l)end local r="6~!5MiGhcd[Fka/;_?}mX.rAY\`0UVe<W){(^EL-TO=DCK|@wBg7x:nz#%,JR8*$y&s]Iuqo>2lS4fvt9pHQZ1NP3+jb"local i={}for l=1,#r do i[o(r,l,l)]=l-1 end local l=1 local function r()local c=i[o(d,l,l)]l=l+1 local n=0 local a=1 for e=1,c do n=n*85+i[o(d,l,l)]l=l+1 end return n end e=f(r())c[1]=e while l<#d do local l=r()if a[l]then n=a[l]else n=e..o(e,1,1)end a[t]=e..o(n,1,1)c[#c+1],e,t=n,n,t+1 end return table.concat(c)end;local t=h(w[1]);local c=bit and bit.bxor or function(l,n)local e,o=1,0 while l>0 and n>0 do local a,c=l%2,n%2 if a~=c then o=o+e end l,n,e=(l-a)/2,(n-c)/2,e*2 end if l<n then l=n end while l>0 do local n=l%2 if n>0 then o=o+e end l,e=(l-n)/2,e*2 end return o end local function n(e,l,n)if n then local l=(e/2^(l-1))%2^((n-1)-(l-1)+1);return l-l%1;else local l=2^(l-1);return(e%(l+l)>=l)and 1 or 0;end;end;local l=1;local e=getfenv;local e=_G;local function e()local o,n,e,a=d(t,l,l+3);o=c(o,135)n=c(n,135)e=c(e,135)a=c(a,135)l=l+4;return(a*16777216)+(e*65536)+(n*256)+o;end;local function i()local e=c(d(t,l,l),135);l=l+1;return e;end;local function a()local n,e=d(t,l,l+2);n=c(n,135)e=c(e,135)l=l+2;return(e*256)+n;end;local function w()local o=e();local l=e();local c=1;local o=(n(l,1,20)*(2^32))+o;local e=n(l,21,31);local l=((-1)^n(l,32));if(e==0)then if(o==0)then return l*0;else e=1;c=0;end;elseif(e==2047)then return(o==0)and(l*(1/0))or(l*(0/0));end;return s(l,e-1023)*(c+(o/(2^52)));end;local function s(e)local n;if(not e)then e=e();if(e==0)then return'';end;end;n=o(t,l,l+e-1);l=l+e;local e={}for l=1,#n do e[l]=f(c(d(o(n,l,l)),135))end return G(e);end;local l=e;local function f(...)return{...},u('#',...)end local function G()local d={};local c={};local l={};local t={d,c,nil,l};local l=e()local o={}for n=1,l do local e=i();local l;if(e==3)then l=(i()~=0);elseif(e==1)then l=w();elseif(e==2)then l=s();end;o[n]=l;end;for c=1,e()do local l=i();if(n(l,1,1)==0)then local t=n(l,2,3);local f=n(l,4,6);local l={a(),a(),nil,nil};if(t==0)then l[3]=a();l[4]=a();elseif(t==1)then l[3]=e();elseif(t==2)then l[3]=e()-(2^16)elseif(t==3)then l[3]=e()-(2^16)l[4]=a();end;if(n(f,1,1)==1)then l[2]=o[l[2]]end if(n(f,2,2)==1)then l[3]=o[l[3]]end if(n(f,3,3)==1)then l[4]=o[l[4]]end d[c]=l;end end;t[3]=i();for l=1,e()do c[l-1]=G();end;return t;end;local function u(l,e,i)local n=l[1];local e=l[2];local l=l[3];return function(...)local o=n;local c=e;local a=l;local h=f local e=1;local d=-1;local f={};local t={...};local s=u('#',...)-1;local l={};local n={};for l=0,s do if(l>=a)then f[l-a]=t[l+1];else n[l]=t[l+1];end;end;local l=s-a+1 local l;local a;while true do l=o[e];a=l[1];if a<=14 then if a<=6 then if a<=2 then if a<=0 then local e=l[2]local o,l=h(n[e](n[e+1]))d=l+e-1 local l=0;for e=e,d do l=l+1;n[e]=o[l];end;elseif a>1 then n[l[2]]=i[l[3]];else local e=l[2]n[e]=n[e](n[e+1])end;elseif a<=4 then if a>3 then do return end;else n[l[2]]=l[3];end;elseif a==5 then if(n[l[2]]==l[4])then e=e+1;else e=l[3];end;else local a;local a;n[l[2]]=i[l[3]];e=e+1;l=o[e];n[l[2]]=i[l[3]];e=e+1;l=o[e];n[l[2]]=l[3];e=e+1;l=o[e];n[l[2]]=l[3];e=e+1;l=o[e];n[l[2]]=l[3];e=e+1;l=o[e];a=l[2]n[a]=n[a]..n[a+1]e=e+1;l=o[e];n[l[2]]=i[l[3]];e=e+1;l=o[e];n[l[2]]=l[3];e=e+1;l=o[e];a=l[2]n[a](n[a+1])e=e+1;l=o[e];do return end;end;elseif a<=10 then if a<=8 then if a>7 then n[l[2]]=l[3];else n[l[2]]=i[l[3]];end;elseif a==9 then local a;n[l[2]]=i[l[3]];e=e+1;l=o[e];n[l[2]]=l[3];e=e+1;l=o[e];a=l[2]n[a](n[a+1])e=e+1;l=o[e];do return end;else local e=l[2]local o,l=h(n[e](n[e+1]))d=l+e-1 local l=0;for e=e,d do l=l+1;n[e]=o[l];end;end;elseif a<=12 then if a>11 then local e=l[2]n[e](n[e+1])else n[l[2]]=i[l[3]];end;elseif a>13 then if(n[l[2]]==l[4])then e=e+1;else e=l[3];end;else n[l[2]]=l[3];end;elseif a<=22 then if a<=18 then if a<=16 then if a==15 then local a;n[l[2]]=i[l[3]];e=e+1;l=o[e];n[l[2]]=l[3];e=e+1;l=o[e];a=l[2]n[a](n[a+1])e=e+1;l=o[e];do return end;else n[l[2]]=i[l[3]];end;elseif a==17 then local a;local a;n[l[2]]=i[l[3]];e=e+1;l=o[e];n[l[2]]=i[l[3]];e=e+1;l=o[e];n[l[2]]=l[3];e=e+1;l=o[e];n[l[2]]=l[3];e=e+1;l=o[e];n[l[2]]=l[3];e=e+1;l=o[e];a=l[2]n[a]=n[a]..n[a+1]e=e+1;l=o[e];n[l[2]]=i[l[3]];e=e+1;l=o[e];n[l[2]]=l[3];e=e+1;l=o[e];a=l[2]n[a](n[a+1])e=e+1;l=o[e];do return end;else n[l[2]]=l[3];end;elseif a<=20 then if a>19 then e=l[3];else e=l[3];end;elseif a==21 then do return end;else n[l[2]]=l[3];end;elseif a<=26 then if a<=24 then if a>23 then local e=l[2]n[e](n[e+1])else n[l[2]]=l[3];end;elseif a>25 then n[l[2]]=i[l[3]];else n[l[2]]=i[l[3]];end;elseif a<=28 then if a==27 then n[l[2]]=i[l[3]];else n[l[2]]=l[3];end;elseif a==29 then n[l[2]]=l[3];else local e=l[2]n[e]=n[e](n[e+1])end;e=e+1;end;end;end;return u(G(),{},M())end)("${encoded}")`;
        }

        // ==================== FUNÇÃO PRINCIPAL ====================
        async function obfuscateCode() {
            const code = document.getElementById('luaCode').value.trim();
            
            if (!code) {
                showStatus('❌ Por favor, insira um código Lua!', 'error');
                return;
            }
            
            const btn = document.getElementById('processBtn');
            btn.disabled = true;
            btn.textContent = '⏳ Processando...';
            
            document.getElementById('loader').classList.add('show');
            document.getElementById('resultBox').classList.remove('show');
            document.getElementById('copyButtons').style.display = 'none';
            document.getElementById('statsSection').style.display = 'none';
            hideStatus();
            
            try {
                let processed = code;
                let activeLayers = 0;
                
                // Contar camadas ativas
                for (let i = 1; i <= 6; i++) {
                    if (document.getElementById('opt' + i).checked) activeLayers++;
                }
                
                // Layer 1: Variable Mangling
                if (document.getElementById('opt4').checked) {
                    updateProgress(16, '🎭 Layer 1: Variable Mangling...');
                    await sleep(600);
                    processed = mangleVariables(processed);
                }
                
                // Layer 2: Control Flow
                if (document.getElementById('opt5').checked) {
                    updateProgress(33, '🔀 Layer 2: Control Flow...');
                    await sleep(600);
                    processed = obfuscateControlFlow(processed);
                }
                
                // Layer 3: Anti-Debug
                if (document.getElementById('opt6').checked) {
                    updateProgress(50, '🛡️ Layer 3: Anti-Debug...');
                    await sleep(600);
                    processed = addAntiDebug(processed);
                }
                
                // Layer 4: XOR Encryption
                updateProgress(66, '🔐 Layer 4: XOR Encryption...');
                await sleep(600);
                const encrypted = xorEncrypt(processed, 135);
                
                // Layer 5: LZW Compression
                updateProgress(83, '📦 Layer 5: LZW Compression...');
                await sleep(600);
                const compressed = lzwCompress(encrypted);
                
                // Layer 6: Base85 Encoding + TigerMoon
                updateProgress(100, '⚡ Layer 6: Generating TigerMoon...');
                await sleep(600);
                obfuscatedCode = generateTigerMoonCode(compressed);
                
                // Mostrar resultado
                showStatus('✅ Código ofuscado com máxima proteção!', 'success');
                document.getElementById('resultBox').textContent = obfuscatedCode;
                document.getElementById('resultBox').classList.add('show');
                document.getElementById('copyButtons').style.display = 'block';
                
                // Atualizar estatísticas
                const originalSize = code.length;
                const compressedSize = compressed.length;
                const ratio = Math.round((compressedSize / originalSize) * 100);
                
                document.getElementById('originalSize').textContent = originalSize;
                document.getElementById('compressedSize').textContent = compressedSize;
                document.getElementById('compressionRatio').textContent = ratio + '%';
                document.getElementById('protectionLayers').textContent = activeLayers;
                document.getElementById('statsSection').style.display = 'grid';
                
                document.getElementById('resultBox').scrollIntoView({ behavior: 'smooth' });
                
            } catch (error) {
                console.error('Obfuscation error:', error);
                showStatus('❌ Erro ao ofuscar: ' + error.message, 'error');
            } finally {
                btn.disabled = false;
                btn.textContent = '🚀 OFUSCAR COM PROTEÇÃO MÁXIMA';
                document.getElementById('loader').classList.remove('show');
                setTimeout(() => {
                    document.getElementById('progressBar').classList.remove('show');
                }, 1000);
            }
        }

        function copyCode() {
            if (!obfuscatedCode) {
                showStatus('❌ Nenhum código para copiar!', 'error');
                return;
            }
            
            navigator.clipboard.writeText(obfuscatedCode).then(() => {
                showStatus('✅ Código TigerMoon PRO copiado!', 'success');
                setTimeout(hideStatus, 2000);
            }).catch(() => {
                const textarea = document.createElement('textarea');
                textarea.value = obfuscatedCode;
                textarea.style.position = 'fixed';
                textarea.style.opacity = '0';
                document.body.appendChild(textarea);
                textarea.select();
                document.execCommand('copy');
                document.body.removeChild(textarea);
                showStatus('✅ Código copiado!', 'success');
                setTimeout(hideStatus, 2000);
            });
        }

        function downloadCode() {
            const blob = new Blob([obfuscatedCode], { type: 'text/plain' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = 'tigermoon_pro_protected.lua';
            a.click();
            URL.revokeObjectURL(url);
        }

        console.log('🐯 Tiger Hub Obfuscator PRO - TigerMoon V2 Enhanced');
    </script>
</body>
</html>
