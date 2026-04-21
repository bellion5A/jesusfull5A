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
  Send,
  ArrowLeft
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
const IntroSection = () => {
  const headTeachers = ['이종필 목자', '이기열 목자'];
  const teachers = [
    '차시윤 목자', '황미경 목자', '오창주 목자',
    '이권능 목자', '김은향 목자', '고혜미 목자', '선양희 목자',
    '김해성 목자', '신세정 목자', '이춘원 목자'
  ];

  return (
    <div className="space-y-6 animate-in fade-in slide-in-from-bottom-4 duration-500">
      <div className="bg-white rounded-xl shadow-sm p-6 md:p-8 border border-slate-100">
        <div className="flex items-center space-x-3 mb-6">
          <User className="w-6 h-6 text-blue-500" />
          <h2 className="text-xl font-bold text-slate-800">목장 소개 및 섬기는 분들</h2>
        </div>
        
        {/* 인사말 */}
        <div className="mb-8">
          <p className="text-slate-600 leading-relaxed bg-slate-50 p-5 rounded-lg border border-slate-100">
            안녕하세요. 충만한교회 운정 초등 5A 목장입니다. <br className="hidden md:block"/>
            우리 12명의 아이들이 하나님의 말씀 안에서 바르게 성장하고, 
            서로 사랑하며 기쁨이 넘치는 목장이 되기를 소망합니다. 
            가정에서도 많은 기도와 관심 부탁드립니다.
          </p>
        </div>

        <div className="space-y-8">
          {/* 부장 목자 */}
          <div>
            <h3 className="text-sm font-bold text-blue-600 mb-3 border-b border-slate-100 pb-2">부장 목자</h3>
            <div className="grid grid-cols-1 sm:grid-cols-2 gap-4">
              {headTeachers.map((teacher, index) => (
                <div key={index} className="flex items-center space-x-4">
                  <div className="w-14 h-14 bg-blue-100 rounded-full flex items-center justify-center flex-shrink-0">
                    <User className="w-6 h-6 text-blue-600" />
                  </div>
                  <div>
                    <h4 className="text-lg font-bold text-slate-800">{teacher}</h4>
                    <p className="text-sm text-slate-500 mt-0.5">초등 5A 목장 총괄</p>
                  </div>
                </div>
              ))}
            </div>
          </div>

          {/* 반 목자 */}
          <div>
            <h3 className="text-sm font-bold text-blue-600 mb-3 border-b border-slate-100 pb-2">반 목자</h3>
            <div className="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-3">
              {teachers.map((teacher, index) => (
                <div key={index} className="flex items-center space-x-3 bg-white border border-slate-200 p-3 rounded-lg shadow-sm transition-colors hover:bg-slate-50">
                  <div className="w-8 h-8 bg-slate-100 rounded-full flex items-center justify-center flex-shrink-0">
                    <User className="w-4 h-4 text-slate-500" />
                  </div>
                  <span className="text-sm font-medium text-slate-700">{teacher}</span>
                </div>
              ))}
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

// 2. 예배 섹션
const WorshipSection = () => (
  <div className="space-y-6 animate-in fade-in slide-in-from-bottom-4 duration-500">
    <div className="grid md:grid-cols-2 gap-6 items-start">
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
        <div className="space-y-2 mb-4">
          <p className="text-lg font-medium text-slate-700">충만한교회 운정 성전</p>
          <p className="text-slate-500">지하 1층 116호</p>
          <p className="text-slate-500 text-sm mt-2">경기 파주시 한빛로 5</p>
        </div>
        
        {/* 지도 이미지 */}
        <div className="mt-5 rounded-lg overflow-hidden border border-slate-200 shadow-sm">
          <img 
            src="image_76a2a1.jpg" 
            alt="충만한교회 위치 지도" 
            className="w-full h-auto object-cover"
          />
        </div>
      </div>
    </div>
  </div>
);

// 3. 활동 사진 섹션
const GallerySection = () => {
  const [filter, setFilter] = useState('weekly');
  const [selectedPhoto, setSelectedPhoto] = useState(null);

  const categories = [
    { id: 'weekly', name: '주간 활동', icon: <Camera className="w-4 h-4" /> },
    { id: 'birthday', name: '생일자', icon: <Gift className="w-4 h-4" /> },
    { id: 'newFriend', name: '새 친구', icon: <UserPlus className="w-4 h-4" /> },
    { id: 'bulletin', name: '온라인 주보', icon: <FileText className="w-4 h-4" /> },
  ];

  // 샘플 데이터 (내용과 작성자 추가)
  const photos = [
    { id: 1, category: 'weekly', title: '봄 소풍 다녀왔습니다', date: '2026-04-12', author: '이종필 목자', content: '아이들과 함께 즐거운 봄 소풍을 다녀왔습니다. 화창한 날씨 속에서 뛰어놀며 교제하는 귀한 시간이었습니다.' },
    { id: 2, category: 'weekly', title: '성경 퀴즈 대회 결승전', date: '2026-04-05', author: '이기열 목자', content: '초등부 전체 성경 퀴즈 대회에서 우리 5A 목장이 좋은 성적을 거두었습니다!' },
    { id: 3, category: 'birthday', title: '4월 생일 파티 (지민, 민준)', date: '2026-04-19', author: '황미경 목자', content: '4월에 태어난 지민이와 민준이의 생일을 축하했습니다. 하나님의 사랑 안에서 건강하게 자라도록 기도해주세요.' },
    { id: 4, category: 'newFriend', title: '새 친구 서연이를 환영합니다', date: '2026-04-19', author: '차시윤 목자', content: '오늘 우리 목장에 새로운 친구 서연이가 왔습니다. 5A 목장의 가족이 된 것을 진심으로 환영합니다.' },
    { id: 5, category: 'bulletin', title: '4월 3주차 목장 주보', date: '2026-04-19', author: '오창주 목자', content: '이번 주 목장 모임 나눔 질문과 공지사항이 담긴 온라인 주보입니다.' },
    { id: 6, category: 'weekly', title: '공과 공부 시간', date: '2026-03-28', author: '이권능 목자', content: '진지하게 하나님의 말씀을 배우고 나누는 아이들의 모습입니다.' },
  ];

  const filteredPhotos = photos.filter(p => p.category === filter);

  // 상세 페이지 뷰
  if (selectedPhoto) {
    return (
      <div className="space-y-4 animate-in fade-in slide-in-from-right-4 duration-300">
        <button 
          onClick={() => setSelectedPhoto(null)} 
          className="flex items-center space-x-2 text-slate-500 hover:text-blue-600 transition-colors"
        >
          <ArrowLeft className="w-5 h-5" />
          <span className="font-medium">목록으로 돌아가기</span>
        </button>

        <div className="bg-white rounded-xl shadow-sm border border-slate-100 overflow-hidden">
          <div className="p-6 md:p-8 border-b border-slate-100">
            <div className="flex items-center justify-between mb-4">
              <span className="text-sm font-medium text-blue-600 bg-blue-50 px-3 py-1 rounded-full">
                {categories.find(c => c.id === selectedPhoto.category)?.name}
              </span>
              <span className="text-sm text-slate-500">{selectedPhoto.date}</span>
            </div>
            <h2 className="text-2xl font-bold text-slate-800 mb-2">{selectedPhoto.title}</h2>
            <div className="flex items-center space-x-2 text-sm text-slate-500">
              <User className="w-4 h-4" />
              <span>{selectedPhoto.author}</span>
            </div>
          </div>
          
          <div className="p-6 md:p-8 bg-slate-50">
            {/* 이미지 영역 */}
            <div className="w-full h-64 sm:h-96 bg-slate-200 rounded-lg mb-6 flex items-center justify-center border border-slate-200 overflow-hidden">
              <div className="text-center">
                <ImageIcon className="w-12 h-12 text-slate-400 mx-auto mb-2" />
                <span className="text-sm text-slate-500">사진이 표시되는 영역입니다</span>
              </div>
            </div>
            {/* 본문 영역 */}
            <p className="text-slate-700 leading-relaxed whitespace-pre-line">
              {selectedPhoto.content}
            </p>
          </div>
        </div>
      </div>
    );
  }

  // 목록 뷰
  return (
    <div className="space-y-6 animate-in fade-in slide-in-from-bottom-4 duration-500">
      {/* 필터 버튼 */}
      <div className="flex flex-wrap gap-2 border-b border-slate-200 pb-4">
        {categories.map((cat) => (
          <button
            key={cat.id}
            onClick={() => {
              setFilter(cat.id);
              setSelectedPhoto(null);
            }}
            className={`flex items-center space-x-2 px-5 py-2.5 rounded-lg text-sm font-medium transition-colors ${
              filter === cat.id
                ? 'bg-blue-600 text-white shadow-sm'
                : 'bg-white text-slate-600 hover:bg-slate-50 border border-slate-200'
            }`}
          >
            {cat.icon}
            <span>{cat.name}</span>
          </button>
        ))}
      </div>

      {/* 사진 갤러리 그리드 */}
      {filteredPhotos.length > 0 ? (
        <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-5">
          {filteredPhotos.map((photo) => (
            <div 
              key={photo.id} 
              onClick={() => setSelectedPhoto(photo)}
              className="bg-white rounded-xl shadow-sm border border-slate-100 overflow-hidden group cursor-pointer hover:border-blue-300 hover:shadow-md transition-all flex flex-col"
            >
              <div className="h-48 bg-slate-100 flex items-center justify-center relative overflow-hidden">
                <ImageIcon className="w-8 h-8 text-slate-300 group-hover:scale-110 transition-transform duration-500" />
              </div>
              <div className="p-5 flex-1 flex flex-col justify-between">
                <div>
                  <h3 className="font-bold text-slate-800 line-clamp-2 mb-2 group-hover:text-blue-600 transition-colors">{photo.title}</h3>
                  <p className="text-sm text-slate-500 line-clamp-2 mb-3">{photo.content}</p>
                </div>
                <div className="flex items-center justify-between text-xs text-slate-400 mt-auto">
                  <span>{photo.author}</span>
                  <span>{photo.date}</span>
                </div>
              </div>
            </div>
          ))}
        </div>
      ) : (
        <div className="text-center py-16 bg-white rounded-xl border border-slate-100 shadow-sm flex flex-col items-center justify-center">
          <Camera className="w-12 h-12 text-slate-300 mb-3" />
          <p className="text-slate-500 font-medium">등록된 사진이 없습니다.</p>
        </div>
      )}

      {/* 사진 등록 버튼 (UI 목업) */}
      <div className="flex justify-end pt-2">
        <button className="flex items-center space-x-2 bg-slate-800 hover:bg-slate-900 text-white px-5 py-2.5 rounded-lg text-sm font-medium transition-colors shadow-sm">
          <Camera className="w-4 h-4" />
          <span>사진 올리기</span>
        </button>
      </div>
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
