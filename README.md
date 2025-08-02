<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>1879골프과정 - 골프 열정이 시작되는 곳</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Font: Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8fafc; /* Tailwind gray-50 */
            color: #1e293b; /* Tailwind slate-800 */
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 1rem;
        }
        .section-title {
            position: relative;
            display: inline-block;
            padding-bottom: 0.5rem;
            margin-bottom: 2rem;
            font-weight: 700;
            font-size: 2.25rem; /* text-4xl */
            color: #1e293b;
        }
        .section-title::after {
            content: '';
            position: absolute;
            left: 0;
            bottom: 0;
            width: 60px;
            height: 4px;
            background-color: #ef4444; /* Tailwind red-500 */
            border-radius: 9999px; /* rounded-full */
        }
        /* Style for the success message box */
        .success-message {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            background-color: #4CAF50; /* Green */
            color: white;
            padding: 15px 20px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
            z-index: 1000;
            opacity: 0;
            transition: opacity 0.5s ease-in-out;
        }
        .success-message.show {
            opacity: 1;
        }

        /* Modal Styles */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 999;
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.3s ease, visibility 0.3s ease;
        }
        .modal-overlay.show {
            opacity: 1;
            visibility: visible;
        }
        .modal-content {
            background-color: white;
            padding: 2rem;
            border-radius: 0.75rem; /* rounded-lg */
            box-shadow: 0 10px 15px rgba(0, 0, 0, 0.2);
            position: relative;
            max-width: 700px; /* Increased max-width for image/video */
            width: 90%;
            transform: translateY(-20px);
            transition: transform 0.3s ease;
        }
        .modal-overlay.show .modal-content {
            transform: translateY(0);
        }
        .modal-close-button {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: #4b5563; /* Tailwind gray-600 */
            transition: color 0.2s ease;
        }
        .modal-close-button:hover {
            color: #1e293b; /* Tailwind slate-800 */
        }
        /* Responsive video container */
        .video-container {
            position: relative;
            width: 100%;
            padding-bottom: 56.25%; /* 16:9 aspect ratio */
            height: 0;
            overflow: hidden;
            margin-top: 1rem;
        }
        .video-container iframe,
        .video-container video {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }
    </style>
</head>
<body class="antialiased">

    <!-- Header Section -->
    <header class="bg-white shadow-md py-4">
        <div class="container flex justify-between items-center">
            <div class="flex items-center space-x-2">
                <!-- Golf Ball Icon -->
                <svg class="w-8 h-8 text-green-600" fill="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
                    <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zM12 6c-3.31 0-6 2.69-6 6s2.69 6 6 6 6-2.69 6-6-2.69-6-6-6zm0 10c-2.21 0-4-1.79-4-4s1.79-4 4-4 4 1.79 4 4-1.79 4-4 4z"/>
                </svg>
                <span class="text-2xl font-bold text-gray-900">1879골프과정</span>
            </div>
            <nav class="hidden md:flex space-x-6">
                <a href="#home" class="text-gray-600 hover:text-red-600 font-medium transition duration-300 rounded-md py-2 px-3">홈</a>
                <a href="#" onclick="openModal('courseRegistrationModal')" class="text-gray-600 hover:text-red-600 font-medium transition duration-300 rounded-md py-2 px-3">수강신청</a>
                <a href="#" onclick="openModal('signupModal')" class="text-gray-600 hover:text-red-600 font-medium transition duration-300 rounded-md py-2 px-3">회원가입</a>
                <a href="#" onclick="openModal('loginModal')" class="text-gray-600 hover:text-red-600 font-medium transition duration-300 rounded-md py-2 px-3">로그인</a>
            </nav>
            <button class="md:hidden p-2 rounded-md text-gray-600 hover:text-red-600 focus:outline-none focus:ring-2 focus:ring-red-500">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path></svg>
            </button>
        </div>
    </header>

    <!-- Hero Section -->
    <section id="home" class="bg-gradient-to-r from-red-700 to-green-600 text-white py-20 md:py-32">
        <div class="container text-center">
            <h1 class="text-4xl md:text-6xl font-extrabold leading-tight mb-6 animate-fade-in-up">
                프리미엄 골프 경험
            </h1>
            <p class="text-lg md:text-xl mb-10 max-w-3xl mx-auto opacity-90 animate-fade-in-up delay-100">
                아름다운 1879골프과정과 모든 레벨의 골퍼를 위한 전문 강좌를 만나보세요.
            </p>
            <a href="#" onclick="openModal('courseContentModal')" class="inline-block bg-white text-red-700 hover:bg-red-100 font-bold py-3 px-8 rounded-full shadow-lg transition duration-300 transform hover:scale-105 animate-fade-in-up delay-200">
                과정 보기
            </a>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-16 bg-gray-50">
        <div class="container text-center">
            <h2 class="section-title mx-auto">저희 1879골프과정에 대해</h2>
            <p class="text-lg text-gray-700 leading-relaxed max-w-4xl mx-auto">
                저희 1879골프과정은 웅장한 자연 경관과 현대적인 시설을 갖춘 독특한 골프 경험을 제공합니다. 저희는 여러분이 기술을 발전시키고, 휴식을 취하며, 골프에 대한 열정을 즐길 수 있는 이상적인 환경을 제공하기 위해 최선을 다하고 있습니다.
            </p>
        </div>
    </section>

    <!-- Courses Section (now Golf Lessons) -->
    <section id="courses" class="py-16 bg-white">
        <div class="container">
            <h2 class="section-title">골프 강좌</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-10 mt-10">
                <!-- Individual Golf Lesson Program -->
                <div class="bg-green-50 rounded-lg shadow-lg p-8 transform hover:scale-105 transition duration-300">
                    <h3 class="text-3xl font-bold text-green-700 mb-4">개인 골프 강좌</h3>
                    <p class="text-gray-700 mb-4">
                        초보자부터 상급자까지 모든 레벨에 적합한 전문 코치와의 1:1 훈련 프로그램입니다.
                    </p>
                    <ul class="list-disc list-inside text-gray-600 space-y-2 mb-6">
                        <li><span class="font-semibold">기간:</span> 17기 (학생 일정에 따라 유연하게 조절)</li>
                        <li><span class="font-semibold">비용:</span> 3,900,000 KRW</li>
                        <li><span class="font-semibold">주요 내용:</span>
                            <ul class="list-circle list-inside ml-4">
                                <li>개인 스윙 기술 분석 및 교정.</li>
                                <li>퍼팅, 칩샷, 피칭 등 기본 기술 훈련.</li>
                                <li>코스 플레이 전략 및 경기 관리.</li>
                                <li>실습 및 진행 상황 추적.</li>
                            </ul>
                        </li>
                    </ul>
                    <button id="registerIndividual" class="bg-green-600 text-white font-bold py-3 px-6 rounded-full hover:bg-green-700 active:scale-95 transition duration-300 shadow-md" onclick="openModal('courseRegistrationModal')">
                        개인 강좌 등록
                    </button>
                </div>

                <!-- Premium Membership Package -->
                <div class="bg-red-50 rounded-lg shadow-lg p-8 transform hover:scale-105 transition duration-300">
                    <h3 class="text-3xl font-bold text-red-700 mb-4">프리미엄 회원권 패키지</h3>
                    <p class="text-gray-700 mb-4">
                        저희 프리미엄 회원을 위한 무제한 이용 특권과 독점 혜택을 누리세요.
                    </p>
                    <ul class="list-disc list-inside text-gray-600 space-y-2 mb-6">
                        <li><span class="font-semibold">기간:</span> 4개월</li>
                        <li><span class="font-semibold">비용:</span>  4,000,000 KRW</li>
                        <li><span class="font-semibold">주요 내용:</span>
                            <ul class="list-circle list-inside ml-4">
                                <li>1879골프과정 무제한 이용.</li>
                                <li>강좌 및 프로샵 특별 할인.</li>
                                <li>티타임 우선 예약 및 내부 대회 참가.</li>
                                <li>프리미엄 편의시설 (VIP 라운지, 헬스장) 무료 이용.</li>
                            </ul>
                        </li>
                    </ul>
                    <button id="registerPremium" class="bg-red-600 text-white font-bold py-3 px-6 rounded-full hover:bg-red-700 active:scale-95 transition duration-300 shadow-md" onclick="openModal('signupModal')">
                        회원등록 신청
                    </button>
                </div>
            </div>
        </div>
    </section>

    <!-- Added Image Section -->
    <section id="promo-image" class="py-16 bg-gray-100">
        <div class="container text-center">
            <img src="http://googleusercontent.com/file_content/1" alt="Golf CEO Master Course" class="w-full h-auto rounded-lg shadow-lg mb-8 mx-auto max-w-2xl">
        </div>
    </section>

    <!-- Instructor Section -->
    <section id="instructors" class="py-16 bg-white">
        <div class="container">
            <h2 class="section-title mx-auto text-center">강사 소개</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 mt-10">
                <!-- Instructor 1 -->
                <div class="bg-gray-50 rounded-lg shadow-md p-6 text-center hover:shadow-xl transition duration-300">
                    <img src="https://placehold.co/150x150/e0e0e0/ffffff?text=강사+1" alt="강사 1" class="w-32 h-32 rounded-full mx-auto mb-4 object-cover">
                    <h3 class="text-xl font-semibold text-gray-800 mb-2">이훈성 원장</h3>
                    <p class="text-red-600 font-medium mb-2">PGA 공인 프로</p>
                    <p class="text-gray-600 text-sm">골프CEO과정 원장,USGTF PRO방송인.엔터터이너
가수/영화배우</p>
                </div>
                <!-- Instructor 2 -->
                <div class="bg-gray-50 rounded-lg shadow-md p-6 text-center hover:shadow-xl transition duration-300">
                    <img src="https://placehold.co/150x150/e0e0e0/ffffff?text=강사+2" alt="강사 2" class="w-32 h-32 rounded-full mx-auto mb-4 object-cover">
                    <h3 class="text-xl font-semibold text-gray-800 mb-2">이정용 부원장</h3>
                    <p class="text-green-600 font-medium mb-2">골프 피트니스 전문가</p>
                    <p class="text-gray-600 text-sm">골프CEO과정 부원장,1879홍보 모델
방송인.</p>
                </div>
                <!-- Instructor 3 -->
                <div class="bg-gray-50 rounded-lg shadow-md p-6 text-center hover:shadow-xl transition duration-300">
                    <img src="https://placehold.co/150x150/e0e0e0/ffffff?text=강사+3" alt="강사 3" class="w-32 h-32 rounded-full mx-auto mb-4 object-cover">
                    <h3 class="text-xl font-semibold text-gray-800 mb-2">안재모 팀장</h3>
                    <p class="text-red-600 font-medium mb-2">주니어 골프 전문 코치</p>
                    <p class="text-gray-600 text-sm">골프CEO과정 프로,IPGA PRO,호서대 골프지도학과 석사
1879골프 담당프로</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-16 bg-white">
        <div class="container">
            <h2 class="section-title"> 문의하세요</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-10 mt-10">
                <div>
                    <p class="text-lg text-gray-700 mb-4">
                        질문이 있거나 예약하고 싶으신가요? 언제든지 저희에게 연락하세요.
                    </p>
                    <div class="space-y-4 text-gray-700">
                        <p class="flex items-center">
                            <svg class="w-6 h-6 text-red-600 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path></svg>
                            이메일: <a href="mailto:info@sangolf.com" class="text-red-600 hover:underline">ceo@csfood.com</a>
                        </p>
                        <p class="flex items-center">
                            <svg class="w-6 h-6 text-red-600 mr-3" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path></svg>
                           연락처:
                          
                          팀장:안재모 010-0000-1879 
                        </p>
                        <p class="flex items-start">
                            <svg class="w-6 h-6 text-red-600 mr-3 mt-1" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                            주소: 서울특별시 서초구 양재동 215 6층
                        </p>
                    </div>
                </div>
                <!-- Placeholder for map or contact form -->
                <div class="bg-gray-100 rounded-lg p-6 flex items-center justify-center min-h-[250px] md:min-h-full">
                    <p class="text-gray-500 text-center">
                        [지도 또는 문의 양식이 여기에 배치됩니다]
                    </p>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer Section -->
    <footer class="bg-gray-800 text-white py-8">
        <div class="container text-center text-gray-400">
            <p>&copy; 2025 1879골프과정. 모든 권리 보유.</p>
            <div class="mt-4 flex justify-center space-x-6">
                <a href="#" class="hover:text-red-400 transition duration-300">개인정보처리방침</a>
                <a href="#" class="hover:text-red-400 transition duration-300">이용 약관</a>
                <!-- Social Media Icons -->
                <a href="#" class="text-gray-400 hover:text-blue-500 transition duration-300">
                    <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                        <path fill-rule="evenodd" d="M22 12c0-5.523-4.477-10-10-10S2 6.477 2 12c0 4.991 3.657 9.128 8.438 9.878v-6.987h-2.54V12h2.54V9.797c0-2.506 1.492-3.89 3.777-3.89 1.094 0 2.238.195 2.238.195v2.46h-1.26c-1.243 0-1.63.771-1.63 1.562V12h2.773l-.443 2.89h-2.33V22C18.343 21.128 22 16.991 22 12z" clip-rule="evenodd" />
                    </svg>
                </a>
                <a href="#" class="text-gray-400 hover:text-pink-500 transition duration-300">
                    <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                        <path fill-rule="evenodd" d="M12 0C8.74 0 8.333.014 7.053.072 5.775.132 4.92.333 4.067.732c-.975.45-1.774 1.15-2.524 1.9-.75.75-1.45 1.55-1.9 2.525-.399.853-.6 1.708-.662 2.986-.058 1.28-.072 1.676-.072 4.004s.014 2.724.072 4.004c.06 1.278.261 2.133.662 2.986.45 1.006 1.15 1.805 1.9 2.556.75.75 1.549 1.45 2.524 1.9.853.399 1.708.6 2.986.662 1.28.058 1.676.072 4.004.072s2.724-.014 4.004-.072c1.278-.06 2.133-.261 2.986-.662 1.006-.45 1.805-1.15 2.556-1.9.75-.75 1.45-1.549 1.9-2.524.399-.853.6-1.708.662-2.986.058-1.28.072-1.676.072-4.004s-.014-2.724-.072-4.004c-.06-1.278-.261-2.133-.662-2.986-.45-1.006-1.15-1.805-1.9-2.556-.75-.75-1.549-1.45-2.524-1.9-.853-.399-1.708-.6-2.986-.662C15.667.014 15.26 0 12 0zm0 2.16c3.2 0 3.585.016 4.85.071 1.17.055 1.7.249 2.05.409.76.346 1.24.68 1.79 1.23.55.55 1.05 1.03 1.23 1.79.16.35.354.88.409 2.05.056 1.265.07 1.65.07 4.85s-.016 3.585-.071 4.85c-.055 1.17-.249 1.7-.409 2.05-.346.76-.68 1.24-1.23 1.79-.55.55-1.03 1.05-1.79 1.23-.35.16-.88.354-2.05.409-1.265.056-1.65.07-4.85.07s-3.585-.016-4.85-.071c-1.17-.055-1.7-.249-2.05-.409-.76-.346-1.24-.68-1.79-1.23-.55-.55-1.05-1.03-1.23-1.79-.16-.35-.354-.88-.409-2.05-.056-1.265-.07-1.65-.07-4.85s.016-3.585.071-4.85c.055-1.17.249-1.7.409-2.05.346-.76.68-1.24 1.23-1.79.55-.55 1.03-1.05 1.79-1.23.35-.16.88-.354 2.05-.409C8.415 2.16 8.8 2.16 12 2.16zm0 3.635c-3.463 0-6.265 2.802-6.265 6.265S8.537 18.325 12 18.325s6.265-2.802 6.265-6.265S15.463 5.795 12 5.795zM12 16a4 4 0 110-8 4 4 0 010 8zm4.728-9.042a1.2 1.2 0 11-2.4 0 1.2 1.2 0 012.4 0z" clip-rule="evenodd" />
                    </svg>
                </a>
                <a href="#" class="text-gray-400 hover:text-red-600 transition duration-300">
                    <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
                        <path d="M19.61 12.296c-.11-.47-.41-1.01-.89-1.49-.48-.48-1.02-.78-1.49-.89-1.1-.26-2.2-.35-3.3-.35-1.1 0-2.2.09-3.3.35-.47.11-1.01.41-1.49.89-.48.48-.78 1.02-.89 1.49-.26 1.1-.35 2.2-.35 3.3s.09 2.2.35 3.3c.11.47.41 1.01.89 1.49.48.48 1.02.78 1.49.89 1.1.26 2.2.35 3.3.35s2.2-.09 3.3-.35c.47-.11 1.01-.41 1.49-.89.48-.48.78-1.02.89-1.49.26-1.1.35-2.2.35-3.3s-.09-2.2-.35-3.3zM12 18.2c-3.41 0-6.2-2.79-6.2-6.2s2.79-6.2 6.2-6.2 6.2 2.79 6.2 6.2-2.79 6.2-6.2 6.2zM12 8.3c-2.04 0-3.7 1.66-3.7 3.7s1.66 3.7 3.7 3.7 3.7-1.66 3.7-3.7-1.66-3.7-3.7-3.7zM12 14.7c-1.49 0-2.7-1.21-2.7-2.7s1.21-2.7 2.7-2.7 2.7 1.21 2.7 2.7-1.21 2.7-2.7 2.7z"/>
                        <path d="M21.94 6.23c-.22-.84-.5-1.57-.89-2.21-.39-.64-.88-1.15-1.49-1.76-.61-.61-1.12-1.1-1.76-1.49-.64-.39-1.37-.67-2.21-.89C15.51 0 12 0 12 0s-3.51 0-4.34.22c-.84.22-1.57.5-2.21.89-.64.39-1.15.88-1.76 1.49-.61.61-1.1 1.12-1.49 1.76-.39.64-.67 1.37-.89 2.21C0 8.49 0 12 0 12s0 3.51.22 4.34c.22.84.5 1.57.89 2.21.39.64.88 1.15 1.49 1.76.61.61 1.12 1.1 1.76 1.49.64.39 1.37.67 2.21.89C8.49 24 12 24 12 24s3.51 0 4.34-.22c.84-.22 1.57-.5 2.21-.89.64-.39 1.15-.88 1.76-1.49.61-.61 1.1-1.12 1.49-1.76.39-.64.67-1.37.89-2.21C24 15.51 24 12 24 12s0-3.51-.22-4.34zM12 21.94c-3.41 0-6.2-2.79-6.2-6.2s2.79-6.2 6.2-6.2 6.2 2.79 6.2 6.2-2.79 6.2-6.2 6.2z"/>
                    </svg>
                </a>
            </div>
        </div>
    </footer>

    <!-- Modals -->
    <!-- Course Registration Modal -->
    <div id="courseRegistrationModal" class="modal-overlay">
        <div class="modal-content">
            <button class="modal-close-button" onclick="closeModal('courseRegistrationModal')">&times;</button>
            <h2 class="text-2xl font-bold text-gray-900 mb-6 text-center">수강신청</h2>
            <form class="space-y-6">
                <div>
                    <label for="modalRegName" class="block text-sm font-medium text-gray-700">이름</label>
                    <input type="text" id="modalRegName" name="modalRegName" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-red-500 focus:border-red-500 sm:text-sm" placeholder="이름을 입력하세요">
                </div>
                <div>
                    <label for="modalRegPhone" class="block text-sm font-medium text-gray-700">전화번호</label>
                    <input type="tel" id="modalRegPhone" name="modalRegPhone" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-red-500 focus:border-red-500 sm:text-sm" placeholder="전화번호를 입력하세요">
                </div>
                <div>
                    <label for="modalRegEmail" class="block text-sm font-medium text-gray-700">이메일</label>
                    <input type="email" id="modalRegEmail" name="modalRegEmail" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-red-500 focus:border-red-500 sm:text-sm" placeholder="이메일을 입력하세요">
                </div>
                <div>
                    <label for="modalCourseSelect" class="block text-sm font-medium text-gray-700">강좌 선택</label>
                    <select id="modalCourseSelect" name="modalCourseSelect" class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-red-500 focus:border-red-500 sm:text-sm rounded-md">
                        <option value="">강좌를 선택하세요</option>
                        <option value="individual">개인 골프 강좌 (3,900,000 KRW)</option>
                        <option value="premium">프리미엄 회원권 패키지 (4,000,000 KRW/년)</option>
                    </select>
                </div>
                <button id="submitModalCourseRegistration" type="submit" class="w-full flex justify-center py-3 px-4 border border-transparent rounded-md shadow-sm text-lg font-medium text-white bg-red-600 hover:bg-red-700 active:scale-95 transition duration-300 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500">
                    수강신청 완료
                </button>
            </form>
        </div>
    </div>

    <!-- Signup Modal -->
    <div id="signupModal" class="modal-overlay">
        <div class="modal-content">
            <button class="modal-close-button" onclick="closeModal('signupModal')">&times;</button>
            <h2 class="text-2xl font-bold text-gray-900 mb-6 text-center">회원등록 신청</h2>
            <form class="space-y-6">
                <div>
                    <label for="modalSignupUsername" class="block text-sm font-medium text-gray-700">사용자 이름</label>
                    <input type="text" id="modalSignupUsername" name="modalSignupUsername" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm" placeholder="사용자 이름을 입력하세요">
                </div>
                <div>
                    <label for="modalSignupEmail" class="block text-sm font-medium text-gray-700">이메일</label>
                    <input type="email" id="modalSignupEmail" name="modalSignupEmail" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm" placeholder="이메일을 입력하세요">
                </div>
                <div>
                    <label for="modalSignupPassword" class="block text-sm font-medium text-gray-700">비밀번호</label>
                    <input type="password" id="modalSignupPassword" name="modalSignupPassword" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm" placeholder="비밀번호를 입력하세요">
                </div>
                <div>
                    <label for="modalConfirmPassword" class="block text-sm font-medium text-gray-700">비밀번호 확인</label>
                    <input type="password" id="modalConfirmPassword" name="modalConfirmPassword" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-green-500 focus:border-green-500 sm:text-sm" placeholder="비밀번호를 다시 입력하세요">
                </div>
                <button id="submitModalSignup" type="submit" class="w-full flex justify-center py-3 px-4 border border-transparent rounded-md shadow-sm text-lg font-medium text-white bg-green-600 hover:bg-green-700 active:scale-95 transition duration-300 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-green-500">
                    회원신청
                </button>
            </form>
        </div>
    </div>

    <!-- Login Modal -->
    <div id="loginModal" class="modal-overlay">
        <div class="modal-content">
            <button class="modal-close-button" onclick="closeModal('loginModal')">&times;</button>
            <h2 class="text-2xl font-bold text-gray-900 mb-6 text-center">로그인</h2>
            <form class="space-y-6">
                <div>
                    <label for="modalLoginUser" class="block text-sm font-medium text-gray-700">사용자 이름 또는 이메일</label>
                    <input type="text" id="modalLoginUser" name="modalLoginUser" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-red-500 focus:border-red-500 sm:text-sm" placeholder="사용자 이름 또는 이메일을 입력하세요">
                </div>
                <div>
                    <label for="modalLoginPassword" class="block text-sm font-medium text-gray-700">비밀번호</label>
                    <input type="password" id="modalLoginPassword" name="modalLoginPassword" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-red-500 focus:border-red-500 sm:text-sm" placeholder="비밀번호를 입력하세요">
                </div>
                <button id="submitModalLogin" type="submit" class="w-full flex justify-center py-3 px-4 border border-transparent rounded-md shadow-sm text-lg font-medium text-white bg-red-600 hover:bg-red-700 active:scale-95 transition duration-300 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500">
                    로그인
                </button>
            </form>
        </div>
    </div>

    <!-- Course Content Modal -->
    <div id="courseContentModal" class="modal-overlay">
        <div class="modal-content">
            <button class="modal-close-button" onclick="closeModal('courseContentModal')">&times;</button>
            <h2 class="text-2xl font-bold text-gray-900 mb-6 text-center">과정 내용</h2>
            <div class="space-y-4">
                <img src="http://googleusercontent.com/file_content/1" alt="C:\Users\User\OneDrive\사진\Screenshots" class="w-full h-auto rounded-lg shadow-md">
                <div class="video-container">
                    <!-- Updated YouTube video embed -->
                    <iframe width="560" height="315" src="https://www.youtube.com/embed/yTKsMQzyq2M" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen class="rounded-lg shadow-md"></iframe>
                </div>
                <p class="text-gray-700 text-center">
                    1879  골프대회
                </p>
            </div>
        </div>
    </div>

    <!-- Success Message Box -->
    <div id="successMessageBox" class="success-message hidden">
        <p>신청완료</p>
    </div>

    <script>
        // Function to show a temporary success message
        function showSuccessMessage() {
            const messageBox = document.getElementById('successMessageBox');
            messageBox.classList.remove('hidden');
            messageBox.classList.add('show');

            // Hide the message after 3 seconds
            setTimeout(() => {
                messageBox.classList.remove('show');
                messageBox.classList.add('hidden');
            }, 3000);
        }

        // Function to open a specific modal
        function openModal(modalId) {
            document.getElementById(modalId).classList.add('show');
        }

        // Function to close a specific modal
        function closeModal(modalId) {
            document.getElementById(modalId).classList.remove('show');
        }

        // Add event listeners to the registration buttons (within sections)
        document.getElementById('registerIndividual').addEventListener('click', (event) => {
            event.preventDefault(); // Prevent default button behavior
            openModal('courseRegistrationModal'); // Open course registration modal
        });
        document.getElementById('registerPremium').addEventListener('click', (event) => {
            event.preventDefault(); // Prevent default button behavior
            openModal('signupModal'); // Open signup modal
        });

        // Add event listeners to the modal form submission buttons
        document.getElementById('submitModalCourseRegistration').addEventListener('click', (event) => {
            event.preventDefault(); // Prevent form submission for this example
            showSuccessMessage();
            closeModal('courseRegistrationModal'); // Close modal after submission
        });
        document.getElementById('submitModalSignup').addEventListener('click', (event) => {
            event.preventDefault(); // Prevent form submission for this example
            showSuccessMessage();
            closeModal('signupModal'); // Close modal after submission
        });
        document.getElementById('submitModalLogin').addEventListener('click', (event) => {
            event.preventDefault(); // Prevent form submission for this example
            showSuccessMessage();
            closeModal('loginModal'); // Close modal after submission
        });
    </script>
</body>
</html>

