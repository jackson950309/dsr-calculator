# dsr-calculator
dsr-calculator
[DSR_Calculator.html](https://github.com/user-attachments/files/22400319/DSR_Calculator.html)
<!doctype html>
<html lang="zh-Hans">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>DSR 在线计算器</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');
    body { font-family: 'Inter', sans-serif; }
    .gradient-bg { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); }
    .glass { backdrop-filter: blur(10px); background: rgba(255, 255, 255, 0.95); }
    .input-focus:focus { box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1); }
    .pulse-animation { animation: pulse 2s infinite; }
    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.8; }
    }
  </style>
</head>
<body class="gradient-bg min-h-screen">
  <div class="container mx-auto px-4 py-8">
    <!-- Header -->
    <div class="text-center mb-8">
      <h1 class="text-4xl font-bold text-white mb-2">💰 DSR 在线计算器</h1>
      <p class="text-white/80 text-lg">债务服务比率 (Debt Service Ratio) 快速计算工具</p>
    </div>

    <div class="max-w-4xl mx-auto grid md:grid-cols-2 gap-8">
      <!-- Input Card -->
      <div class="glass rounded-2xl p-8 shadow-2xl">
        <h2 class="text-2xl font-semibold text-gray-800 mb-6 flex items-center">
          📊 收入与债务信息
        </h2>
        
        <div class="space-y-6">
          <div>
            <label for="income" class="block text-sm font-medium text-gray-700 mb-2">
              💵 月收入 (RM)
            </label>
            <input id="income" type="number" value="9900" 
                   class="w-full px-4 py-3 border-2 border-gray-200 rounded-xl input-focus transition-all duration-200 text-lg font-medium">
          </div>

          <div>
            <label for="mortgage" class="block text-sm font-medium text-gray-700 mb-2">
              🏠 房贷月供 (RM)
            </label>
            <input id="mortgage" type="number" value="1548"
                   class="w-full px-4 py-3 border-2 border-gray-200 rounded-xl input-focus transition-all duration-200 text-lg font-medium">
          </div>

          <div>
            <label for="car" class="block text-sm font-medium text-gray-700 mb-2">
              🚗 车贷月供 (RM)
            </label>
            <input id="car" type="number" value="0"
                   class="w-full px-4 py-3 border-2 border-gray-200 rounded-xl input-focus transition-all duration-200 text-lg font-medium">
          </div>

          <div>
            <label for="cc" class="block text-sm font-medium text-gray-700 mb-2">
              💳 信用卡还款 (RM)
            </label>
            <input id="cc" type="number" value="0"
                   class="w-full px-4 py-3 border-2 border-gray-200 rounded-xl input-focus transition-all duration-200 text-lg font-medium">
          </div>

          <div>
            <label for="personal" class="block text-sm font-medium text-gray-700 mb-2">
              📋 个人贷款月供 (RM)
            </label>
            <input id="personal" type="number" value="0"
                   class="w-full px-4 py-3 border-2 border-gray-200 rounded-xl input-focus transition-all duration-200 text-lg font-medium">
          </div>

          <button id="calc" class="w-full bg-gradient-to-r from-blue-600 to-purple-600 text-white font-semibold py-4 px-6 rounded-xl hover:from-blue-700 hover:to-purple-700 transition-all duration-200 transform hover:scale-105 shadow-lg">
            🧮 重新计算 DSR
          </button>
        </div>
      </div>

      <!-- Results Card -->
      <div class="glass rounded-2xl p-8 shadow-2xl">
        <h2 class="text-2xl font-semibold text-gray-800 mb-6 flex items-center">
          📈 计算结果
        </h2>
        
        <div class="space-y-6">
          <!-- Total Debt -->
          <div class="bg-gradient-to-r from-orange-50 to-red-50 p-6 rounded-xl border-l-4 border-orange-400">
            <div class="text-sm font-medium text-gray-600 mb-1">每月总债务</div>
            <div class="text-3xl font-bold text-orange-600" id="total">RM 0.00</div>
          </div>

          <!-- DSR Result -->
          <div class="bg-gradient-to-r from-blue-50 to-indigo-50 p-6 rounded-xl border-l-4 border-blue-400">
            <div class="text-sm font-medium text-gray-600 mb-1">债务服务比率 (DSR)</div>
            <div class="text-4xl font-bold text-blue-600 pulse-animation" id="dsr">0%</div>
          </div>

          <!-- DSR Status -->
          <div id="status" class="p-6 rounded-xl border-l-4">
            <div class="font-semibold mb-2" id="status-title">DSR 状态</div>
            <div class="text-sm" id="status-desc">输入数据以查看评估</div>
          </div>

          <!-- Info Box -->
          <div class="bg-gray-50 p-6 rounded-xl">
            <h3 class="font-semibold text-gray-800 mb-3">💡 DSR 参考标准</h3>
            <div class="space-y-2 text-sm text-gray-600">
              <div class="flex justify-between">
                <span>🟢 优秀:</span>
                <span class="font-medium">≤ 30%</span>
              </div>
              <div class="flex justify-between">
                <span>🟡 良好:</span>
                <span class="font-medium">30% - 40%</span>
              </div>
              <div class="flex justify-between">
                <span>🟠 一般:</span>
                <span class="font-medium">40% - 60%</span>
              </div>
              <div class="flex justify-between">
                <span>🔴 偏高:</span>
                <span class="font-medium">> 60%</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Footer -->
    <div class="text-center mt-12">
      <p class="text-white/70 text-sm">
        ⚠️ 此计算器仅供参考，实际贷款审批请咨询银行专业人士
      </p>
    </div>
  </div>

  <script>
    function money(v){return Number(v).toLocaleString(undefined,{minimumFractionDigits:2,maximumFractionDigits:2});}
    function pct(v){return v.toFixed(2)+'%';}

    function updateStatus(ratio) {
      const statusDiv = document.getElementById('status');
      const statusTitle = document.getElementById('status-title');
      const statusDesc = document.getElementById('status-desc');
      
      if (ratio <= 30) {
        statusDiv.className = 'p-6 rounded-xl border-l-4 border-green-400 bg-gradient-to-r from-green-50 to-emerald-50';
        statusTitle.textContent = '🟢 优秀状态';
        statusDesc.textContent = '您的债务比率很健康，有良好的财务管理能力！';
      } else if (ratio <= 40) {
        statusDiv.className = 'p-6 rounded-xl border-l-4 border-yellow-400 bg-gradient-to-r from-yellow-50 to-amber-50';
        statusTitle.textContent = '🟡 良好状态';
        statusDesc.textContent = '债务比率在可接受范围内，建议继续保持良好的财务习惯。';
      } else if (ratio <= 60) {
        statusDiv.className = 'p-6 rounded-xl border-l-4 border-orange-400 bg-gradient-to-r from-orange-50 to-red-50';
        statusTitle.textContent = '🟠 需要注意';
        statusDesc.textContent = '债务比率偏高，建议减少不必要支出或增加收入来源。';
      } else {
        statusDiv.className = 'p-6 rounded-xl border-l-4 border-red-400 bg-gradient-to-r from-red-50 to-pink-50';
        statusTitle.textContent = '🔴 风险较高';
        statusDesc.textContent = '债务负担过重，强烈建议制定债务减免计划或寻求专业建议。';
      }
    }

    function compute(){
      const i = parseFloat(document.getElementById('income').value)||0;
      const m = parseFloat(document.getElementById('mortgage').value)||0;
      const c = parseFloat(document.getElementById('car').value)||0;
      const cc = parseFloat(document.getElementById('cc').value)||0;
      const p = parseFloat(document.getElementById('personal').value)||0;
      const total = m+c+cc+p;
      const ratio = i===0?0:(total/i*100);
      
      document.getElementById('total').textContent = 'RM '+money(total);
      document.getElementById('dsr').textContent = pct(ratio);
      
      updateStatus(ratio);
    }

    document.getElementById('calc').addEventListener('click', compute);
    
    // Auto-calculate when any input changes
    ['income', 'mortgage', 'car', 'cc', 'personal'].forEach(id => {
      document.getElementById(id).addEventListener('input', compute);
    });
    
    compute();
  </script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'980ec235d4185664',t:'MTc1ODE3NjY0OC4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
