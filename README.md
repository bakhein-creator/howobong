<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>오봉댐 물 절약 앱</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f0f4f8;
        }
        .water-level-container {
            position: relative;
            width: 250px;
            height: 250px;
            background-color: #d1d5db;
            border-radius: 50%;
            overflow: hidden;
            border: 8px solid #9ca3af;
            display: flex;
            align-items: flex-end;
            justify-content: center;
        }
        .water {
            width: 100%;
            background-color: #3b82f6;
            transition: height 2s cubic-bezier(0.23, 1, 0.32, 1);
        }
        .water-text {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 2.5rem;
            font-weight: bold;
            color: #1f2937;
            text-shadow: 1px 1px 2px rgba(255, 255, 255, 0.7);
            z-index: 10;
        }
    </style>
</head>
<body class="bg-gray-100 flex items-center justify-center min-h-screen p-4">
    <div class="bg-white rounded-3xl shadow-2xl p-8 max-w-2xl w-full text-center">
        <h1 class="text-4xl font-bold text-gray-800 mb-2">오봉댐 저수율 현황</h1>
        <p class="text-gray-600 mb-8">물 절약을 통해 소중한 자원을 지켜주세요!</p>

        <div class="flex flex-col items-center mb-8">
            <!-- 물통 시각화 (Water tank visualization) -->
            <div class="water-level-container shadow-inner">
                <div id="water-fill" class="water"></div>
                <div id="water-percent" class="water-text">0%</div>
            </div>
            <p class="text-xl font-semibold mt-4 text-gray-700">현재 저수율</p>
        </div>

        <!-- 물 절약 팁 섹션 (Water saving tips section) -->
        <div class="mb-8">
            <h2 class="text-2xl font-bold text-gray-800 mb-4">💧 생활 속 물 절약 방법</h2>
            <div class="grid md:grid-cols-2 gap-4 text-left">
                <!-- 물 절약 팁 카드 (Water saving tips cards) -->
                <div class="bg-blue-50 p-4 rounded-xl shadow-md">
                    <h3 class="font-bold text-lg text-blue-700 mb-2">설거지할 때</h3>
                    <ul class="list-disc list-inside text-gray-700">
                        <li>물을 틀어놓고 하지 않고, 물을 받아서 사용하세요.</li>
                        <li>음식물 찌꺼기는 미리 제거하면 물 사용량이 줄어듭니다.</li>
                    </ul>
                </div>
                <div class="bg-blue-50 p-4 rounded-xl shadow-md">
                    <h3 class="font-bold text-lg text-blue-700 mb-2">양치할 때</h3>
                    <ul class="list-disc list-inside text-gray-700">
                        <li>양치컵을 사용하세요. 물을 그냥 흘려보내면 많은 양이 낭비됩니다.</li>
                        <li>양치컵 하나로도 5리터 이상의 물을 절약할 수 있습니다.</li>
                    </ul>
                </div>
                <div class="bg-blue-50 p-4 rounded-xl shadow-md">
                    <h3 class="font-bold text-lg text-blue-700 mb-2">샤워할 때</h3>
                    <ul class="list-disc list-inside text-gray-700">
                        <li>샤워 시간을 5분 이내로 줄여보세요.</li>
                        <li>비누칠할 때는 반드시 수도꼭지를 잠그는 습관을 들이세요.</li>
                    </ul>
                </div>
                <div class="bg-blue-50 p-4 rounded-xl shadow-md">
                    <h3 class="font-bold text-lg text-blue-700 mb-2">빨래할 때</h3>
                    <ul class="list-disc list-inside text-gray-700">
                        <li>세탁기는 빨랫감을 모아 한 번에 돌리는 것이 가장 효율적입니다.</li>
                        <li>소량의 빨래는 손세탁하여 물을 아낄 수 있습니다.</li>
                    </ul>
                </div>
            </div>
        </div>

        <p class="text-sm text-gray-500 mt-4">
            <span class="font-bold">참고:</span> 이 저수율 데이터는 데모용이며, 실제 실시간 데이터와는 다를 수 있습니다.
        </p>
    </div>

    <script>
        // 이 변수를 통해 실제 오봉댐의 최신 저수율을 업데이트하세요.
        // 데이터 소스: Google 검색 결과에 기반한 2025년 9월 22일 기준 60.0%
        // (Note: To get real-time data, you would need to use a public data API, but none were found for this specific dam.)
        const currentWaterLevel = 60.0;

        // DOM 요소 가져오기
        const waterFill = document.getElementById('water-fill');
        const waterPercent = document.getElementById('water-percent');

        /**
         * 물 높이를 애니메이션으로 업데이트하는 함수
         * @param {number} level 현재 저수율 (0-100)
         */
        function updateWaterLevel(level) {
            const percentage = Math.max(0, Math.min(100, level));
            const fillHeight = `${percentage}%`;

            // 물 높이와 텍스트를 동시에 업데이트
            waterFill.style.height = fillHeight;
            waterPercent.textContent = `${percentage.toFixed(1)}%`;
        }

        // 페이지 로드 시 저수율 업데이트 시작
        window.onload = () => {
            updateWaterLevel(currentWaterLevel);
        };
    </script>
</body>
</html>
