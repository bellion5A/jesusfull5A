import React, { useState } from 'react';
import { 
  User, 
  Clock, 
  MapPin, 
  Camera, 
  BookOpen, 
  MessageSquare, 
  Heart, 
  Image as ImageIcon, 
  Gift, 
  UserPlus, 
  FileText,
  Send
} from 'lucide-react';

const App = () => {
  const [activeTab, setActiveTab] = useState('intro');

  const renderContent = () => {
    switch (activeTab) {
      case 'intro':
        return <IntroSection />;
      case 'worship':
        return <WorshipSection />;
      case 'gallery':
        return <GallerySection />;
      case 'board':
        return <BoardSection />;
      default:
        return <IntroSection />;
    }
  };

  return (
    <div className="min-h-screen bg-slate-50 text-slate-800 font-sans">
      {/* Header */}
      <header className="bg-blue-600 text-white shadow-md sticky top-0 z-10">
        <div className="max-w-4xl mx-auto px-4 py-6 text-center">
          <h1 className="text-2xl md:text-3xl font-bold tracking-tight">
            충만한교회 운정 초등 5A 목장
          </h1>
          <p className="mt-2 text-blue-100 text-sm md:text-base">
            하나님의 사랑 안에서 자라나는 우리 목장
          </p>
        </div>
        
        {/* Navigation */}
        <nav className="max-w-4xl mx-auto px-4">
          <ul className="flex justify-between md:justify-start md:space-x-8 overflow-x-auto text-sm md:text-base font-medium">
            {['intro', 'worship', 'gallery', 'board'].map((tab) => (
              <li key={tab}>
                <button
                  onClick={() => setActiveTab(tab)}
                  className={`py-3 px-2 border-b-4 transition-colors whitespace-nowrap ${
                    activeTab === tab
                      ? 'border-white text-white'
                      : 'border-transparent text-blue-200 hover:text-white'
                  }`}
                >
                  {tab === 'intro' && '소개'}
                  {tab === 'worship' && '예배'}
                  {tab === 'gallery' && '활동 사진'}
                  {tab === 'board' && '게시판'}
                </button>
              </li>
            ))}
          </ul>
        </nav>
      </header>

      {/* Main Content */}
      <main className="max-w-4xl mx-auto px-4 py-8">
        {renderContent()}
      </main>

      {/* Footer */}
      <footer className="bg-slate-800 text-slate-400 py-6 text-center text-sm mt-12">
        <p>© 2026 충만한교회 운정 초등 5A 목장. All rights reserved.</p>
      </footer>
    </div>
  );
};

// 1. 소개 섹션
const IntroSection = () => (
  <div className="space-y-6 animate-in fade-in slide-in-from-bottom-4 duration-500">
    <div className="bg-white rounded-xl shadow-sm p-6 md:p-8 border border-slate-100">
      <div className="flex items-center space-x-3 mb-6">
        <User className="w-6 h-6 text-blue-500" />
        <h2 className="text-xl font-bold text-slate-800">반목자 소개</h2>
      </div>
      
      <div className="flex flex-col md:flex-row gap-6 items-center md:items-start">
        <div className="w-32 h-32 bg-slate-200 rounded-full flex items-center justify-center flex-shrink-0">
          <User className="w-12 h-12 text-slate-400" />
        </div>
        <div className="text-center md:text-left space-y-3">
          <h3 className="text-lg font-semibold">김선생 반목자</h3>
          <p className="text-slate-600 leading-relaxed">
            안녕하세요. 초등 5A 목장을 섬기고 있는 반목자입니다. 
            우리 아이들이 하나님의 말씀 안에서 바르게 성장하고, 
            서로 사랑하며 기쁨이 넘치는 목장이 되기를 소망합니다. 
            가정에서도 많은 기도와 관심 부탁드립니다.
          </p>
          <div className="bg-blue-50 text-blue-700 px-4 py-2 rounded-md inline-block text-sm font-medium mt-2">
            연락처 : 010-0000-0000
          </div>
        </div>
      </div>
    </div>
  </div>
);

// 2. 예배 섹션
const WorshipSection = () => (
  <div className="space-y-6 animate-in fade-in slide-in-from-bottom-4 duration-500">
    <div className="grid md:grid-cols-2 gap-6">
      <div className="bg-white rounded-xl shadow-sm p-6 border border-slate-100">
        <div className="flex items-center space-x-3 mb-4">
          <Clock className="w-6 h-6 text-blue-500" />
          <h2 className="text-xl font-bold text-slate-800">예배 시간</h2>
        </div>
        <div className="space-y-2">
          <p className="text-lg font-medium text-slate-700">주일 오전 11시 00분</p>
          <p className="text-slate-500 text-sm">예배 10분 전까지 도착하여 기도로 준비합니다.</p>
        </div>
      </div>

      <div className="bg-white rounded-xl shadow-sm p-6 border border-slate-100">
        <div className="flex items-center space-x-3 mb-4">
          <MapPin className="w-6 h-6 text-blue-500" />
          <h2 className="text-xl font-bold text-slate-800">예배 위치</h2>
        </div>
        <div className="space-y-2">
          <p className="text-lg font-medium text-slate-700">충만한교회 운정캠퍼스</p>
          <p className="text-slate-500">비전센터 3층 초등부실</p>
          <p className="text-slate-500 text-sm mt-2">경기 파주시 운정동 (상세 주소)</p>
        </div>
      </div>
    </div>
  </div>
);

// 3. 활동 사진 섹션
const GallerySection = () => {
  const [filter, setFilter] = useState('weekly');

  const categories = [
    { id: 'weekly', name: '주간 활동', icon: <Camera className="w-4 h-4" /> },
    { id: 'birthday', name: '생일자', icon: <Gift className="w-4 h-4" /> },
    { id: 'newFriend', name: '새 친구', icon: <UserPlus className="w-4 h-4" /> },
    { id: 'bulletin', name: '온라인 주보', icon: <FileText className="w-4 h-4" /> },
  ];

  // 샘플 데이터
  const photos = [
    { id: 1, category: 'weekly', title: '봄 소풍 사진', date: '2026-04-12' },
    { id: 2, category: 'weekly', title: '성경 퀴즈 대회', date: '2026-04-05' },
    { id: 3, category: 'birthday', title: '4월 생일 파티', date: '2026-04-19' },
    { id: 4, category: 'newFriend', title: '지민이 환영해요', date: '2026-04-19' },
    { id: 5, category: 'bulletin', title: '4월 3주차 주보', date: '2026-04-19' },
    { id: 6, category: 'weekly', title: '공과 공부 시간', date: '2026-03-28' },
  ];

  const filteredPhotos = photos.filter(p => p.category === filter);

  return (
    <div className="space-y-6 animate-in fade-in slide-in-from-bottom-4 duration-500">
      {/* 필터 버튼 */}
      <div className="flex flex-wrap gap-2">
        {categories.map((cat) => (
          <button
            key={cat.id}
            onClick={() => setFilter(cat.id)}
            className={`flex items-center space-x-2 px-4 py-2 rounded-full text-sm font-medium transition-colors ${
              filter === cat.id
                ? 'bg-blue-600 text-white'
                : 'bg-white text-slate-600 hover:bg-slate-100 border border-slate-200'
            }`}
          >
            {cat.icon}
            <span>{cat.name}</span>
          </button>
        ))}
      </div>

      {/* 사진 갤러리 그리드 */}
      {filteredPhotos.length > 0 ? (
        <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4">
          {filteredPhotos.map((photo) => (
            <div key={photo.id} className="bg-white rounded-xl shadow-sm border border-slate-100 overflow-hidden group cursor-pointer hover:shadow-md transition-shadow">
              <div className="h-48 bg-slate-200 flex items-center justify-center relative">
                <ImageIcon className="w-8 h-8 text-slate-400" />
                {/* 실제 사용 시 이미지 태그로 교체 */}
                {/* <img src={photo.url} alt={photo.title} className="w-full h-full object-cover" /> */}
              </div>
              <div className="p-4">
                <h3 className="font-semibold text-slate-800 line-clamp-1">{photo.title}</h3>
                <p className="text-xs text-slate-500 mt-1">{photo.date}</p>
              </div>
            </div>
          ))}
        </div>
      ) : (
        <div className="text-center py-12 bg-white rounded-xl border border-slate-100 text-slate-500">
          등록된 사진이 없습니다.
        </div>
      )}
    </div>
  );
};

// 4. 게시판 섹션
const BoardSection = () => {
  const [boardType, setBoardType] = useState('word');

  const boardTabs = [
    { id: 'word', name: '말씀', icon: <BookOpen className="w-4 h-4" /> },
    { id: 'grace', name: '은혜 나눔', icon: <MessageSquare className="w-4 h-4" /> },
    { id: 'prayer', name: '중보 기도 신청', icon: <Heart className="w-4 h-4" /> },
  ];

  // 샘플 게시물 데이터
  const posts = {
    word: [
      { id: 1, title: '이번 주 요절 말씀 (요한복음 3장 16절)', author: '반목자', date: '2026-04-19' },
      { id: 2, title: '지난 주 설교 요약', author: '반목자', date: '2026-04-12' },
    ],
    grace: [
      { id: 1, title: '오늘 찬양 중에 큰 은혜를 받았습니다.', author: '학생A', date: '2026-04-20' },
      { id: 2, title: '친구와 화해하게 하심에 감사합니다.', author: '학생B', date: '2026-04-15' },
    ],
    prayer: [
      { id: 1, title: '할머니 건강을 위해 기도해주세요.', author: '학생C', date: '2026-04-21' },
      { id: 2, title: '다음 주 시험을 지혜롭게 준비하도록 기도해주세요.', author: '학생D', date: '2026-04-18' },
    ]
  };

  const currentPosts = posts[boardType] || [];

  return (
    <div className="space-y-6 animate-in fade-in slide-in-from-bottom-4 duration-500">
      {/* 게시판 종류 탭 */}
      <div className="flex border-b border-slate-200">
        {boardTabs.map((tab) => (
          <button
            key={tab.id}
            onClick={() => setBoardType(tab.id)}
            className={`flex items-center space-x-2 px-4 py-3 text-sm font-medium transition-colors ${
              boardType === tab.id
                ? 'border-b-2 border-blue-600 text-blue-600'
                : 'text-slate-500 hover:text-slate-800'
            }`}
          >
            {tab.icon}
            <span>{tab.name}</span>
          </button>
        ))}
      </div>

      <div className="bg-white rounded-xl shadow-sm border border-slate-100 overflow-hidden">
        {/* 게시물 목록 */}
        <div className="divide-y divide-slate-100">
          {currentPosts.length > 0 ? (
            currentPosts.map((post) => (
              <div key={post.id} className="p-4 hover:bg-slate-50 transition-colors cursor-pointer flex flex-col sm:flex-row sm:items-center justify-between gap-2">
                <div className="font-medium text-slate-800">{post.title}</div>
                <div className="flex items-center space-x-4 text-sm text-slate-500">
                  <span>{post.author}</span>
                  <span>{post.date}</span>
                </div>
              </div>
            ))
          ) : (
            <div className="p-8 text-center text-slate-500">
              등록된 게시물이 없습니다.
            </div>
          )}
        </div>
      </div>

      {/* 글쓰기 버튼 영역 (UI 목업) */}
      <div className="flex justify-end">
        <button className="flex items-center space-x-2 bg-blue-600 hover:bg-blue-700 text-white px-5 py-2.5 rounded-lg text-sm font-medium transition-colors shadow-sm">
          <Send className="w-4 h-4" />
          <span>글쓰기</span>
        </button>
      </div>
    </div>
  );
};

export default App;
