# نُطقي AI — NutqAI 🎤
**تطبيق تعليم التخاطب بالذكاء الاصطناعي | AI-Powered Speech Therapy App**

---

## 🗂️ هيكل المشروع | Project Structure

```
nutqai/
├── frontend/                  # React + Vite + Tailwind
│   └── src/
│       ├── components/        # Layout, LoadingScreen, shared UI
│       ├── pages/             # Dashboard, Exercises, Chat, Progress, Login
│       ├── context/           # AuthContext (JWT state)
│       ├── services/          # api.js (Axios + all service helpers)
│       ├── hooks/             # Custom React hooks
│       ├── i18n.js            # Arabic / English translations
│       ├── App.jsx            # Routes + providers
│       └── main.jsx           # React entry point
│
├── backend/                   # Node.js + Express
│   ├── models/
│   │   ├── User.js            # User schema (auth + gamification)
│   │   ├── Recording.js       # Audio recordings + analysis results
│   │   ├── Progress.js        # Sessions + letter stats + badges
│   │   └── Chat.js            # Chat history with AI therapist
│   ├── routes/
│   │   ├── auth.js            # Register, Login, Me, Profile
│   │   ├── recordings.js      # Upload audio, list, delete
│   │   ├── analysis.js        # Whisper transcription + Azure pronunciation
│   │   ├── chat.js            # OpenAI GPT speech therapist chat
│   │   └── progress.js        # Session tracking, badges, leaderboard
│   ├── middleware/
│   │   ├── auth.js            # JWT verification
│   │   └── upload.js          # Multer audio file handling
│   └── server.js              # Express app entry point
│
└── package.json               # Root (concurrently dev runner)
```

---

## ⚙️ الإعداد | Setup

### 1. متطلبات النظام
- Node.js >= 18
- MongoDB (local or Atlas)
- OpenAI API Key
- Azure Speech Key

### 2. تثبيت المكتبات
```bash
# من المجلد الرئيسي
npm run install:all
```

### 3. إعداد المتغيرات البيئية
```bash
cd backend
cp .env.example .env
# عدّل الملف وأضف مفاتيحك
```

### 4. تشغيل المشروع
```bash
# من المجلد الرئيسي — يشغّل Frontend + Backend معاً
npm run dev
```
- **Frontend:** http://localhost:3000
- **Backend:**  http://localhost:5000/api/health

---

## 🔌 API Endpoints

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/auth/register | إنشاء حساب جديد |
| POST | /api/auth/login | تسجيل الدخول |
| GET  | /api/auth/me | بيانات المستخدم الحالي |
| PATCH| /api/auth/profile | تحديث الملف الشخصي |

### Recordings
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/recordings/upload | رفع ملف صوتي |
| GET  | /api/recordings | قائمة التسجيلات |
| GET  | /api/recordings/:id | تسجيل محدد |
| DELETE | /api/recordings/:id | حذف تسجيل |

### Analysis
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/analysis/transcribe/:id | تحويل صوت → نص (Whisper) |
| POST | /api/analysis/pronunciation | تحليل النطق (Azure) |

### Chat
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/chat/message | إرسال رسالة للمعالج AI |
| GET  | /api/chat/history | سجل المحادثات |

### Progress
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET  | /api/progress | بيانات التقدم |
| POST | /api/progress/session | حفظ نتائج جلسة |
| GET  | /api/progress/leaderboard | المتصدرون |

---

## 🗺️ خريطة المراحل | Roadmap

- [x] **المرحلة 1** — هيكل المشروع + Auth + Models + Routes
- [ ] **المرحلة 2** — تسجيل الصوت (MediaRecorder API)
- [ ] **المرحلة 3** — رفع الصوت إلى Firebase Storage
- [ ] **المرحلة 4** — تحويل الصوت إلى نص (Whisper)
- [ ] **المرحلة 5** — تحليل النطق (Azure Speech)
- [ ] **المرحلة 6** — Chat مع المعالج الذكي (GPT)
- [ ] **المرحلة 7** — Dashboard التقدم (Chart.js)
- [ ] **المرحلة 8** — UI/UX كامل + دعم الأطفال
- [ ] **المرحلة 9** — Gamification + مستويات
