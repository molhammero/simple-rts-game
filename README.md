# حرب البساطة - Simple RTS Game 🎮

لعبة استراتيجية قتال في الوقت الفعلي (RTS) مبنية بالكامل بـ HTML5 Canvas و JavaScript — بدون أي مكتبات خارجية.

![Game Type](https://img.shields.io/badge/Type-RTS-blue)
![Language](https://img.shields.io/badge/Language-JavaScript-yellow)
![Platform](https://img.shields.io/badge/Platform-Web-green)
![Arabic](https://img.shields.io/badge/RTL-Arabic-red)

---

## 📊 نظرة عامة

| المعيار | القيمة |
|---|---|
| **حجم الملف** | ~130KB (ملف واحد) |
| **أسطر الكود** | ~3,700 سطر |
| **اللغة** | JavaScript (ES6 Modules) |
| **الرسومات** | HTML5 Canvas 2D |
| **دعم اللمس** | ✅ Mobile + Desktop |
| **الاتجاه** | RTL (عربي) |

---

## 🎯 الميزات الرئيسية

### ⚔️ أنواع الوحدات (9 أنواع)

| الوحدة | HP | السرعة | المدى | الضرر | التكلفة |
|---|---|---|---|---|---|
| **TANK** (دبابة) | 120 | 0.5 | 160 | 12 | 50 |
| **SCOUT** (كشاف) | 60 | 0.8 | 120 | 6 | 30 |
| **ARTILLERY** (مدفعية) | 80 | 0.35 | 280 | 25 | 80 |
| **INFANTRY** (مشاة) | 40 | 0.6 | 100 | 5 | 15 |
| **BULLDOZER** (جرافة) | 100 | 0.3 | — | — | 100 |
| **FACTORY** (مقر رئيسي) | 800 | — | — | — | 300 |
| **VEHICLE_FACTORY** (مصنع مركبات) | 500 | — | — | — | 200 |
| **BARRACKS** (ثكنة) | 400 | — | — | — | 150 |
| **TURRET** (برج دفاعي) | 300 | — | 200 | 15 | 100 |

### 🛠️ ميكانيكا اللعبة

- ✅ **نظام مسارات A*** — بحث عن المسار الأمثل باستخدام heuristic و priority queue
- ✅ **ذكاء اصطناعي (AI)** — يبني وحدات، يهاجم بموجات، يوسع قواعده
- ✅ **إدارة الموارد** — نظام Credits و Supply
- ✅ **نظام القتال** — أضرار، مدى، سرعة هجوم، قذائف
- ✅ **نظام البناء** — بناء مصانع وثكنات وبراج دفاعية
- ✅ **نظام التحديد** — تحديد فردي وجماعي (drag selection)
- ✅ **كاميرا ديناميكية** — تحريك وتكبير (zoom) مع تحديد الحدود
- ✅ **خريطة مصغرة (Minimap)** — عرض شامل للعالم
- ✅ **Object Pooling** — إعادة استخدام القذائف لتحسين الأداء
- ✅ **Texture Atlas** — توليد النسيج برمجياً
- ✅ **شريط الصحة** — لكل وحدة وكل مبنى
- ✅ **انفجارات** — تأثيرات بصرية للقذائف
- ✅ **دعم اللمس** — يعمل على الهاتف والكمبيوتر
- ✅ **نظام شبكي** — تحويل الإحداثيات بين العالم والشبكة

---

## 🏗️ البنية المعمارية

```
index.html (ملف واحد)
├── <style>          — CSS (35 قاعدة)
├── <importmap>      — خريطة وحدات ES6
└── <script module>  — JavaScript (~3,064 سطر)
    ├── CONFIG          — إعدادات اللعبة (وحدات، ألوان، إنتاج)
    ├── ObjectPool      — تجمع الكائنات (قذائف)
    ├── Atlas           — توليد نسيج Sprite
    ├── Unit            — الوحدات القتالية
    ├── Projectile      — القذائف والانفجارات
    ├── Factory         — المصانع والإنتاج
    ├── ConstructionSite— مواقع البناء
    └── Game            — المحرك الرئيسي (65+ طريقة)
        ├── update()         — حلقة اللعبة
        ├── updateUnits()    — تحديث الوحدات
        ├── updateAI()       — الذكاء الاصطناعي
        ├── findPath()       — A* Pathfinding
        ├── drawMinimap()    — الخريطة المصغرة
        ├── setupInput()     — إدخال اللمس والفأرة
        └── ...              — 58 طريقة أخرى
```

### 🎮 كلاس Game — الطرق الرئيسية (65)

#### الإدخال والتحكم
- `setupInput`, `onPointerDown`, `onPointerMove`, `onPointerUp`
- `handleTap`, `hitTest`, `hitTestRect`

#### التحديد
- `selectUnit`, `selectFactory`, `clearSelection`
- `selectAllUnits`, `selectVisibleUnits`, `selectUnitsOfTypeOnScreen`
- `completeSelectionDrag`

#### الأوامر
- `commandMove`, `commandAttackMove`, `commandGuard`, `commandAttack`
- `addDestinationMarker`

#### البناء
- `enterBuildMode`, `cancelBuildMode`, `confirmBuild`, `startConstruction`
- `isValidBuildSpot`, `findNearestBuildSpot`, `drawBuildGhost`

#### التحديث
- `update`, `updateUnits`, `updateAI`, `updateFactories`
- `updateProjectiles`, `updateConstructionSites`, `updateResources`
- `cleanupDead`, `checkGameOver`, `endGame`

#### الرسم
- `drawMinimap`, `drawMarker`, `drawBuildGhost`, `updateBuildPreviews`

#### المسارات
- `buildNavGrid`, `findPath` (A* algorithm)

#### الكاميرا
- `centerCamera`, `applyCamera`, `screenToWorld`, `worldToScreen`, `clampCamera`

---

## ⚡ الأداء

| الميزة | الحالة |
|---|---|
| Object Pooling (Projectiles) | ✅ |
| Texture Atlas | ✅ |
| Camera Culling | ✅ |
| Grid Navigation | ✅ |
| Delta Time | ✅ |
| Canvas Resize | ✅ |
| Minimap | ✅ |

---

## 🎯 عالم اللعبة

- **حجم العالم**: 3200 × 3200 بكسل
- **حجم البلاطة**: 32 بكسل
- **فريقان**: اللاعب (أزرق) والعدو (أحمر)
- **موارد**: بلورات موزعة على الخريطة

---

## 🚀 طريقة التشغيل

1. افتح ملف `index.html` في أي متصفح حديث
2. أو استخدم خادم محلي:
   ```bash
   python3 -m http.server 8000
   ```
   ثم افتح `http://localhost:8000`

---

## 📜 الترخيص

مشروع مفتوح المصدر — استخدمه وعدّله بحرية.
