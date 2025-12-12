[indx.HTML.html](https://github.com/user-attachments/files/24131581/indx.HTML.html)
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نظام التخزين الآمن</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Cairo', sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%);
            color: #f1f1f1;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
        }

        .page {
            display: none;
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .page.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* تنسيقات تسجيل الدخول */
        .container {
            width: 100%;
            max-width: 500px;
            margin: 50px auto;
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .header h1 {
            font-size: 2.2rem;
            margin-bottom: 10px;
            color: #4cc9f0;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
        }

        .form-container {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(255, 255, 255, 0.1);
            margin-bottom: 30px;
        }

        .form-tabs {
            display: flex;
            margin-bottom: 30px;
            border-bottom: 2px solid rgba(255, 255, 255, 0.1);
        }

        .tab-btn {
            padding: 15px 30px;
            background: transparent;
            border: none;
            color: #a5b4cb;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
        }

        .tab-btn.active {
            color: #4cc9f0;
            font-weight: 600;
        }

        .tab-btn.active::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 100%;
            height: 3px;
            background: #4cc9f0;
        }

        .form-content {
            display: none;
        }

        .form-content.active {
            display: block;
        }

        .input-group {
            margin-bottom: 25px;
            position: relative;
        }

        .input-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: #a5b4cb;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .input-group input {
            width: 100%;
            padding: 15px 45px 15px 20px;
            background: rgba(255, 255, 255, 0.07);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            color: #ffffff;
            font-size: 1rem;
        }

        .input-group input:focus {
            outline: none;
            border-color: #4cc9f0;
            box-shadow: 0 0 0 3px rgba(76, 201, 240, 0.2);
        }

        .toggle-password {
            position: absolute;
            left: 15px;
            top: 42px;
            cursor: pointer;
            color: #a5b4cb;
        }

        .checkbox-group {
            margin: 25px 0;
            display: flex;
            align-items: flex-start;
            gap: 10px;
        }

        .checkbox-group label {
            color: #a5b4cb;
            font-size: 0.95rem;
        }

        .terms-link {
            color: #4cc9f0;
            text-decoration: none;
        }

        .submit-btn {
            width: 100%;
            padding: 17px;
            background: linear-gradient(135deg, #4361ee 0%, #3a0ca3 100%);
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .submit-btn:hover {
            background: linear-gradient(135deg, #3a56d4 0%, #2d0b8a 100%);
            transform: translateY(-3px);
        }

        .message {
            margin-top: 20px;
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            font-weight: 500;
        }

        .message.success {
            background: rgba(76, 175, 80, 0.2);
            border: 1px solid rgba(76, 175, 80, 0.5);
            color: #81c784;
        }

        .message.error {
            background: rgba(244, 67, 54, 0.2);
            border: 1px solid rgba(244, 67, 54, 0.5);
            color: #f44336;
        }

        /* تنسيقات لوحة التحكم */
        .navbar {
            background: rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            width: 100%;
            padding: 15px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 20px;
        }

        .nav-logo {
            display: flex;
            align-items: center;
            gap: 15px;
            font-size: 1.5rem;
            font-weight: 700;
            color: #4cc9f0;
        }

        .nav-user {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 10px;
            background: rgba(255, 255, 255, 0.05);
            padding: 8px 15px;
            border-radius: 50px;
        }

        .logout-btn {
            background: rgba(244, 67, 54, 0.2);
            color: #f44336;
            border: 1px solid rgba(244, 67, 54, 0.3);
            padding: 8px 20px;
            border-radius: 50px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .logout-btn:hover {
            background: rgba(244, 67, 54, 0.3);
        }

        .dashboard-container {
            display: flex;
            width: 100%;
            gap: 30px;
            margin-top: 30px;
        }

        .sidebar {
            width: 250px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .sidebar-menu {
            display: flex;
            flex-direction: column;
            gap: 10px;
            margin-bottom: 30px;
        }

        .menu-item {
            padding: 15px;
            background: transparent;
            border: none;
            color: #a5b4cb;
            text-align: right;
            border-radius: 10px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .menu-item:hover {
            background: rgba(255, 255, 255, 0.05);
            color: #ffffff;
        }

        .menu-item.active {
            background: rgba(76, 201, 240, 0.2);
            color: #4cc9f0;
            font-weight: 600;
        }

        .main-content {
            flex: 1;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 25px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .section-header h2 {
            display: flex;
            align-items: center;
            gap: 15px;
            color: #4cc9f0;
        }

        .action-btn {
            padding: 10px 20px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            color: #a5b4cb;
            border-radius: 8px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .content-section {
            display: none;
        }

        .content-section.active {
            display: block;
        }

        /* تنسيقات لوحة المالك */
        .admin-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            padding: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            margin-bottom: 20px;
        }

        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 40px;
        }

        .stats-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            padding: 25px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .stats-icon {
            width: 60px;
            height: 60px;
            background: rgba(76, 201, 240, 0.2);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .stats-icon i {
            font-size: 1.8rem;
            color: #4cc9f0;
        }

        .stats-info h3 {
            font-size: 1.8rem;
            margin-bottom: 5px;
            color: #ffffff;
        }

        .stats-info p {
            color: #a5b4cb;
            font-size: 0.9rem;
        }

        /* تنسيقات الجداول */
        .table-container {
            overflow-x: auto;
            margin-bottom: 30px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            overflow: hidden;
        }

        th, td {
            padding: 15px;
            text-align: right;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        th {
            background: rgba(76, 201, 240, 0.1);
            color: #4cc9f0;
            font-weight: 600;
        }

        tr:hover {
            background: rgba(255, 255, 255, 0.03);
        }

        .status {
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
        }

        .status.active {
            background: rgba(76, 175, 80, 0.2);
            color: #81c784;
        }

        .status.pending {
            background: rgba(255, 152, 0, 0.2);
            color: #ff9800;
        }

        /* تنسيقات الملفات */
        .files-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 20px;
        }

        .file-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            padding: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.3s ease;
            cursor: pointer;
            text-align: center;
        }

        .file-card:hover {
            transform: translateY(-5px);
            border-color: #4cc9f0;
        }

        .file-icon {
            font-size: 2.5rem;
            margin-bottom: 15px;
            color: #4cc9f0;
        }

        /* تصميم متجاوب */
        @media (max-width: 768px) {
            .dashboard-container {
                flex-direction: column;
            }
            
            .sidebar {
                width: 100%;
            }
            
            .header h1 {
                font-size: 1.8rem;
            }
            
            .nav-container {
                flex-direction: column;
                gap: 15px;
            }
            
            .section-header {
                flex-direction: column;
                align-items: flex-start;
                gap: 15px;
            }
        }
    </style>
</head>
<body>
    <!-- صفحة تسجيل الدخول -->
    <div id="login-page" class="page active">
        <div class="container">
            <div class="header">
                <h1><i class="fas fa-lock"></i> نظام التخزين الآمن</h1>
                <p>سجل دخولك للوصول إلى ملفاتك المخزنة بشكل آمن</p>
            </div>
            
            <div class="form-container">
                <div class="form-tabs">
                    <button class="tab-btn active" id="login-tab">تسجيل الدخول</button>
                    <button class="tab-btn" id="register-tab">إنشاء حساب جديد</button>
                </div>
                
                <form id="login-form" class="form-content active">
                    <div class="input-group">
                        <label for="login-email"><i class="fas fa-envelope"></i> البريد الإلكتروني</label>
                        <input type="email" id="login-email" required placeholder="أدخل بريدك الإلكتروني">
                    </div>
                    
                    <div class="input-group">
                        <label for="login-password"><i class="fas fa-key"></i> كلمة المرور</label>
                        <input type="password" id="login-password" required placeholder="أدخل كلمة المرور">
                        <span class="toggle-password" id="toggle-login-password">
                            <i class="fas fa-eye"></i>
                        </span>
                    </div>
                    
                    <div class="form-footer">
                        <button type="submit" class="submit-btn">
                            <i class="fas fa-sign-in-alt"></i> تسجيل الدخول
                        </button>
                        <div class="message" id="login-message"></div>
                    </div>
                </form>
                
                <form id="register-form" class="form-content">
                    <div class="input-group">
                        <label for="register-name"><i class="fas fa-user"></i> الاسم الكامل</label>
                        <input type="text" id="register-name" required placeholder="أدخل اسمك الكامل">
                    </div>
                    
                    <div class="input-group">
                        <label for="register-email"><i class="fas fa-envelope"></i> البريد الإلكتروني</label>
                        <input type="email" id="register-email" required placeholder="أدخل بريدك الإلكتروني">
                    </div>
                    
                    <div class="input-group">
                        <label for="register-password"><i class="fas fa-key"></i> كلمة المرور</label>
                        <input type="password" id="register-password" required placeholder="أنشئ كلمة مرور قوية">
                        <span class="toggle-password" id="toggle-register-password">
                            <i class="fas fa-eye"></i>
                        </span>
                    </div>
                    
                    <div class="input-group">
                        <label for="confirm-password"><i class="fas fa-key"></i> تأكيد كلمة المرور</label>
                        <input type="password" id="confirm-password" required placeholder="أعد إدخال كلمة المرور">
                    </div>
                    
                    <div class="checkbox-group">
                        <input type="checkbox" id="age-consent" required>
                        <label for="age-consent">أؤكد أن عمري فوق 18 سنة</label>
                    </div>
                    
                    <div class="form-footer">
                        <button type="submit" class="submit-btn">
                            <i class="fas fa-user-plus"></i> إنشاء حساب
                        </button>
                        <div class="message" id="register-message"></div>
                    </div>
                </form>
                
                <div class="owner-access" style="margin-top: 20px; padding: 15px; background: rgba(76, 201, 240, 0.1); border-radius: 10px;">
                    <h3><i class="fas fa-crown"></i> وصول خاص للمالك</h3>
                    <p><strong>البريد:</strong> admin@admin.com</p>
                    <p><strong>كلمة المرور:</strong> admin123</p>
                </div>
            </div>
        </div>
    </div>

    <!-- لوحة تحكم المستخدم -->
    <div id="dashboard-page" class="page">
        <nav class="navbar">
            <div class="nav-container">
                <div class="nav-logo">
                    <i class="fas fa-lock"></i>
                    <span id="dashboard-title">لوحة التحكم</span>
                </div>
                
                <div class="nav-user">
                    <div class="user-info">
                        <i class="fas fa-user-circle"></i>
                        <span id="user-name-display">المستخدم</span>
                    </div>
                    <button class="logout-btn" id="dashboard-logout">
                        <i class="fas fa-sign-out-alt"></i> تسجيل الخروج
                    </button>
                </div>
            </div>
        </nav>
        
        <div class="dashboard-container">
            <aside class="sidebar">
                <div class="sidebar-menu">
                    <button class="menu-item active" data-section="files">
                        <i class="fas fa-file"></i> ملفاتي
                    </button>
                    <button class="menu-item" data-section="upload">
                        <i class="fas fa-upload"></i> رفع ملف
                    </button>
                    <button class="menu-item" data-section="folders">
                        <i class="fas fa-folder"></i> مجلداتي
                    </button>
                    <button class="menu-item" data-section="profile">
                        <i class="fas fa-user"></i> حسابي
                    </button>
                </div>
                
                <div class="storage-info" style="padding: 15px; background: rgba(0,0,0,0.2); border-radius: 10px;">
                    <h4><i class="fas fa-database"></i> مساحة التخزين</h4>
                    <div style="height: 10px; background: rgba(255,255,255,0.1); border-radius: 5px; margin: 10px 0;">
                        <div id="storage-bar" style="height: 100%; background: #4cc9f0; width: 15%; border-radius: 5px;"></div>
                    </div>
                    <p id="storage-text">15.2 ميغابايت مستخدمة من 100 ميغابايت</p>
                </div>
            </aside>
            
            <main class="main-content">
                <!-- قسم الملفات -->
                <section id="files-section" class="content-section active">
                    <div class="section-header">
                        <h2><i class="fas fa-file"></i> ملفاتي</h2>
                        <button class="action-btn" id="refresh-files">
                            <i class="fas fa-sync-alt"></i> تحديث
                        </button>
                    </div>
                    
                    <div class="files-grid" id="files-grid">
                        <!-- الملفات ستظهر هنا -->
                    </div>
                </section>
                
                <!-- قسم رفع الملف -->
                <section id="upload-section" class="content-section">
                    <div class="section-header">
                        <h2><i class="fas fa-upload"></i> رفع ملف جديد</h2>
                    </div>
                    
                    <div style="border: 2px dashed #4cc9f0; border-radius: 15px; padding: 40px; text-align: center;">
                        <i class="fas fa-cloud-upload-alt fa-3x" style="color: #4cc9f0; margin-bottom: 20px;"></i>
                        <h3>اسحب وأفلت الملفات هنا</h3>
                        <p style="margin: 10px 0 20px; color: #a5b4cb;">أو انقر لاختيار الملفات</p>
                        <input type="file" id="file-upload-input" multiple style="display: none;">
                        <button class="submit-btn" id="browse-files" style="width: auto; padding: 10px 30px;">
                            <i class="fas fa-folder-open"></i> تصفح الملفات
                        </button>
                    </div>
                    
                    <div id="upload-queue" style="margin-top: 20px; display: none;">
                        <h3><i class="fas fa-list"></i> قائمة الانتظار</h3>
                        <div id="queue-list"></div>
                        <button class="submit-btn" id="start-upload" style="margin-top: 20px;">
                            <i class="fas fa-upload"></i> بدء الرفع
                        </button>
                    </div>
                </section>
                
                <!-- قسم المجلدات -->
                <section id="folders-section" class="content-section">
                    <div class="section-header">
                        <h2><i class="fas fa-folder"></i> مجلداتي</h2>
                        <button class="action-btn" id="create-folder">
                            <i class="fas fa-plus"></i> مجلد جديد
                        </button>
                    </div>
                    
                    <div class="files-grid" id="folders-grid">
                        <!-- المجلدات ستظهر هنا -->
                    </div>
                </section>
                
                <!-- قسم الملف الشخصي -->
                <section id="profile-section" class="content-section">
                    <div class="section-header">
                        <h2><i class="fas fa-user"></i> حسابي</h2>
                    </div>
                    
                    <div class="form-container" style="max-width: 600px;">
                        <div class="input-group">
                            <label for="profile-name"><i class="fas fa-user"></i> الاسم الكامل</label>
                            <input type="text" id="profile-name">
                        </div>
                        
                        <div class="input-group">
                            <label for="profile-email"><i class="fas fa-envelope"></i> البريد الإلكتروني</label>
                            <input type="email" id="profile-email" readonly>
                        </div>
                        
                        <div class="input-group">
                            <label for="current-password"><i class="fas fa-key"></i> كلمة المرور الحالية</label>
                            <input type="password" id="current-password">
                        </div>
                        
                        <div class="input-group">
                            <label for="new-password"><i class="fas fa-key"></i> كلمة المرور الجديدة</label>
                            <input type="password" id="new-password">
                        </div>
                        
                        <div class="input-group">
                            <label for="confirm-new-password"><i class="fas fa-key"></i> تأكيد كلمة المرور الجديدة</label>
                            <input type="password" id="confirm-new-password">
                        </div>
                        
                        <button class="submit-btn" id="save-profile">
                            <i class="fas fa-save"></i> حفظ التغييرات
                        </button>
                        <div id="profile-message" class="message"></div>
                    </div>
                </section>
            </main>
        </div>
    </div>

    <!-- لوحة تحكم المالك -->
    <div id="owner-page" class="page">
        <nav class="navbar">
            <div class="nav-container">
                <div class="nav-logo">
                    <i class="fas fa-crown"></i>
                    <span>لوحة تحكم المالك</span>
                </div>
                
                <div class="nav-user">
                    <div class="user-info">
                        <i class="fas fa-crown"></i>
                        <span>مالك النظام</span>
                    </div>
                    <button class="logout-btn" id="owner-logout">
                        <i class="fas fa-sign-out-alt"></i> تسجيل الخروج
                    </button>
                </div>
            </div>
        </nav>
        
        <div class="dashboard-container">
            <aside class="sidebar">
                <div class="sidebar-menu">
                    <button class="menu-item active" data-section="overview">
                        <i class="fas fa-tachometer-alt"></i> نظرة عامة
                    </button>
                    <button class="menu-item" data-section="users-manage">
                        <i class="fas fa-users"></i> إدارة المستخدمين
                    </button>
                    <button class="menu-item" data-section="all-files">
                        <i class="fas fa-file"></i> جميع الملفات
                    </button>
                    <button class="menu-item" data-section="system-settings">
                        <i class="fas fa-cog"></i> إعدادات النظام
                    </button>
                </div>
            </aside>
            
            <main class="main-content">
                <!-- نظرة عامة -->
                <section id="overview-section" class="content-section active">
                    <div class="section-header">
                        <h2><i class="fas fa-tachometer-alt"></i> نظرة عامة على النظام</h2>
                    </div>
                    
                    <div class="stats-container">
                        <div class="stats-card">
                            <div class="stats-icon">
                                <i class="fas fa-users"></i>
                            </div>
                            <div class="stats-info">
                                <h3 id="total-users-count">0</h3>
                                <p>إجمالي المستخدمين</p>
                            </div>
                        </div>
                        
                        <div class="stats-card">
                            <div class="stats-icon">
                                <i class="fas fa-file"></i>
                            </div>
                            <div class="stats-info">
                                <h3 id="total-files-count">0</h3>
                                <p>إجمالي الملفات</p>
                            </div>
                        </div>
                        
                        <div class="stats-card">
                            <div class="stats-icon">
                                <i class="fas fa-database"></i>
                            </div>
                            <div class="stats-info">
                                <h3 id="total-storage-used">0 ميغابايت</h3>
                                <p>إجمالي التخزين</p>
                            </div>
                        </div>
                    </div>
                    
                    <div class="admin-card">
                        <h3><i class="fas fa-user-clock"></i> المستخدمون الجدد</h3>
                        <div id="recent-users"></div>
                    </div>
                </section>
                
                <!-- إدارة المستخدمين -->
                <section id="users-manage-section" class="content-section">
                    <div class="section-header">
                        <h2><i class="fas fa-users"></i> إدارة المستخدمين</h2>
                    </div>
                    
                    <div class="table-container">
                        <table id="users-table">
                            <thead>
                                <tr>
                                    <th>الاسم</th>
                                    <th>البريد الإلكتروني</th>
                                    <th>تاريخ التسجيل</th>
                                    <th>عدد الملفات</th>
                                    <th>الإجراءات</th>
                                </tr>
                            </thead>
                            <tbody id="users-table-body">
                                <!-- بيانات المستخدمين -->
                            </tbody>
                        </table>
                    </div>
                </section>
                
                <!-- جميع الملفات -->
                <section id="all-files-section" class="content-section">
                    <div class="section-header">
                        <h2><i class="fas fa-file"></i> جميع الملفات</h2>
                    </div>
                    
                    <div class="table-container">
                        <table id="all-files-table">
                            <thead>
                                <tr>
                                    <th>اسم الملف</th>
                                    <th>المالك</th>
                                    <th>النوع</th>
                                    <th>الحجم</th>
                                    <th>تاريخ الرفع</th>
                                </tr>
                            </thead>
                            <tbody id="all-files-body">
                                <!-- جميع الملفات -->
                            </tbody>
                        </table>
                    </div>
                </section>
                
                <!-- إعدادات النظام -->
                <section id="system-settings-section" class="content-section">
                    <div class="section-header">
                        <h2><i class="fas fa-cog"></i> إعدادات النظام</h2>
                    </div>
                    
                    <div class="form-container">
                        <div class="input-group">
                            <label>اسم النظام</label>
                            <input type="text" id="system-name" value="نظام التخزين الآمن">
                        </div>
                        
                        <div class="input-group">
                            <label>الحد الأقصى لحجم الملف (ميغابايت)</label>
                            <input type="number" id="max-file-size" value="100" min="1" max="1024">
                        </div>
                        
                        <div class="input-group">
                            <label>الحد الأقصى للتخزين لكل مستخدم (ميغابايت)</label>
                            <input type="number" id="user-storage-limit" value="100" min="10" max="10240">
                        </div>
                        
                        <div class="checkbox-group">
                            <input type="checkbox" id="allow-registration" checked>
                            <label for="allow-registration">السماح بالتسجيل للمستخدمين الجدد</label>
                        </div>
                        
                        <button class="submit-btn" id="save-system-settings">
                            <i class="fas fa-save"></i> حفظ الإعدادات
                        </button>
                        <div id="settings-message" class="message"></div>
                    </div>
                </section>
            </main>
        </div>
    </div>

    <script>
        // تهيئة التطبيق
        document.addEventListener('DOMContentLoaded', function() {
            initializeApp();
        });

        function initializeApp() {
            // تهيئة بيانات التخزين إذا لم تكن موجودة
            if (!localStorage.getItem('secureStorageUsers')) {
                const defaultUsers = [
                    {
                        id: 1,
                        name: "أحمد محمد",
                        email: "ahmed@example.com",
                        password: "123456",
                        createdAt: new Date().toISOString(),
                        files: [],
                        storageUsed: 15.2
                    },
                    {
                        id: 2,
                        name: "سارة عبدالله",
                        email: "sara@example.com",
                        password: "123456",
                        createdAt: new Date().toISOString(),
                        files: [],
                        storageUsed: 8.5
                    },
                    {
                        id: 0,
                        name: "مالك النظام",
                        email: "admin@admin.com",
                        password: "admin123",
                        createdAt: new Date().toISOString(),
                        files: [],
                        storageUsed: 0,
                        isOwner: true
                    }
                ];
                localStorage.setItem('secureStorageUsers', JSON.stringify(defaultUsers));
            }

            if (!localStorage.getItem('systemSettings')) {
                const defaultSettings = {
                    systemName: "نظام التخزين الآمن",
                    maxFileSize: 100,
                    userStorageLimit: 100,
                    allowRegistration: true
                };
                localStorage.setItem('systemSettings', JSON.stringify(defaultSettings));
            }

            // استعادة المستخدم الحالي
            const currentUser = JSON.parse(sessionStorage.getItem('currentUser'));
            if (currentUser) {
                if (currentUser.isOwner) {
                    showPage('owner-page');
                    loadOwnerDashboard();
                } else {
                    showPage('dashboard-page');
                    loadUserDashboard(currentUser);
                }
            }

            // إعداد واجهة تسجيل الدخول
            setupLoginPage();
        }

        // إدارة الصفحات
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
            });
            document.getElementById(pageId).classList.add('active');
        }

        // تسجيل الدخول وإنشاء الحساب
        function setupLoginPage() {
            const loginTab = document.getElementById('login-tab');
            const registerTab = document.getElementById('register-tab');
            const loginForm = document.getElementById('login-form');
            const registerForm = document.getElementById('register-form');
            const loginMessage = document.getElementById('login-message');
            const registerMessage = document.getElementById('register-message');

            // تبديل التبويبات
            loginTab.addEventListener('click', () => {
                loginTab.classList.add('active');
                registerTab.classList.remove('active');
                loginForm.classList.add('active');
                registerForm.classList.remove('active');
            });

            registerTab.addEventListener('click', () => {
                registerTab.classList.add('active');
                loginTab.classList.remove('active');
                registerForm.classList.add('active');
                loginForm.classList.remove('active');
            });

            // إظهار/إخفاء كلمة المرور
            document.getElementById('toggle-login-password').addEventListener('click', function() {
                const passwordInput = document.getElementById('login-password');
                const icon = this.querySelector('i');
                if (passwordInput.type === 'password') {
                    passwordInput.type = 'text';
                    icon.classList.replace('fa-eye', 'fa-eye-slash');
                } else {
                    passwordInput.type = 'password';
                    icon.classList.replace('fa-eye-slash', 'fa-eye');
                }
            });

            document.getElementById('toggle-register-password').addEventListener('click', function() {
                const passwordInput = document.getElementById('register-password');
                const icon = this.querySelector('i');
                if (passwordInput.type === 'password') {
                    passwordInput.type = 'text';
                    icon.classList.replace('fa-eye', 'fa-eye-slash');
                } else {
                    passwordInput.type = 'password';
                    icon.classList.replace('fa-eye-slash', 'fa-eye');
                }
            });

            // تسجيل الدخول
            document.getElementById('login-form').addEventListener('submit', function(e) {
                e.preventDefault();
                const email = document.getElementById('login-email').value.trim();
                const password = document.getElementById('login-password').value;
                
                const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
                const user = users.find(u => u.email === email && u.password === password);
                
                if (user) {
                    // حفظ بيانات الجلسة
                    sessionStorage.setItem('currentUser', JSON.stringify(user));
                    
                    // توجيه حسب نوع المستخدم
                    if (user.isOwner) {
                        showPage('owner-page');
                        loadOwnerDashboard();
                    } else {
                        showPage('dashboard-page');
                        loadUserDashboard(user);
                    }
                    
                    loginMessage.textContent = 'جاري التوجيه...';
                    loginMessage.className = 'message success';
                } else {
                    loginMessage.textContent = 'البريد الإلكتروني أو كلمة المرور غير صحيحة';
                    loginMessage.className = 'message error';
                }
                
                setTimeout(() => {
                    loginMessage.textContent = '';
                    loginMessage.className = 'message';
                }, 3000);
            });

            // إنشاء حساب جديد
            document.getElementById('register-form').addEventListener('submit', function(e) {
                e.preventDefault();
                const name = document.getElementById('register-name').value.trim();
                const email = document.getElementById('register-email').value.trim();
                const password = document.getElementById('register-password').value;
                const confirmPassword = document.getElementById('confirm-password').value;
                
                // التحقق من البيانات
                if (password !== confirmPassword) {
                    registerMessage.textContent = 'كلمتا المرور غير متطابقتين';
                    registerMessage.className = 'message error';
                    return;
                }
                
                if (password.length < 6) {
                    registerMessage.textContent = 'كلمة المرور يجب أن تكون 6 أحرف على الأقل';
                    registerMessage.className = 'message error';
                    return;
                }
                
                const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
                
                // التحقق من عدم تكرار البريد الإلكتروني
                if (users.some(u => u.email === email)) {
                    registerMessage.textContent = 'هذا البريد الإلكتروني مسجل بالفعل';
                    registerMessage.className = 'message error';
                    return;
                }
                
                // إنشاء حساب جديد
                const newUser = {
                    id: Date.now(),
                    name: name,
                    email: email,
                    password: password,
                    createdAt: new Date().toISOString(),
                    files: [],
                    storageUsed: 0
                };
                
                users.push(newUser);
                localStorage.setItem('secureStorageUsers', JSON.stringify(users));
                
                registerMessage.textContent = 'تم إنشاء الحساب بنجاح! يمكنك تسجيل الدخول الآن';
                registerMessage.className = 'message success';
                
                // تفريغ الحقول
                document.getElementById('register-form').reset();
                loginTab.click();
                
                setTimeout(() => {
                    registerMessage.textContent = '';
                    registerMessage.className = 'message';
                }, 3000);
            });
        }

        // لوحة تحكم المستخدم
        function loadUserDashboard(user) {
            // تحديث المعلومات
            document.getElementById('user-name-display').textContent = user.name;
            document.getElementById('dashboard-title').textContent = `لوحة تحكم ${user.name}`;
            document.getElementById('profile-name').value = user.name;
            document.getElementById('profile-email').value = user.email;
            
            // تحديث مساحة التخزين
            updateStorageInfo(user);
            
            // إعداد القوائم الجانبية
            setupUserMenu();
            
            // تحميل الملفات
            loadUserFiles(user);
            
            // تحميل المجلدات
            loadUserFolders(user);
            
            // إعداد زر تسجيل الخروج
            document.getElementById('dashboard-logout').addEventListener('click', logout);
            
            // إعداد رفع الملفات
            setupFileUpload(user);
            
            // إعداد تحديث الملفات
            document.getElementById('refresh-files').addEventListener('click', () => loadUserFiles(user));
            
            // إعداد إنشاء مجلد جديد
            document.getElementById('create-folder').addEventListener('click', () => createNewFolder(user));
            
            // إعداد حفظ الملف الشخصي
            document.getElementById('save-profile').addEventListener('click', () => saveUserProfile(user));
        }

        function setupUserMenu() {
            document.querySelectorAll('#dashboard-page .menu-item').forEach(item => {
                item.addEventListener('click', function() {
                    document.querySelectorAll('#dashboard-page .menu-item').forEach(i => {
                        i.classList.remove('active');
                    });
                    this.classList.add('active');
                    
                    document.querySelectorAll('#dashboard-page .content-section').forEach(section => {
                        section.classList.remove('active');
                    });
                    
                    const sectionId = this.dataset.section + '-section';
                    document.getElementById(sectionId).classList.add('active');
                });
            });
        }

        function loadUserFiles(user) {
            const filesGrid = document.getElementById('files-grid');
            const userFiles = JSON.parse(localStorage.getItem(`userFiles_${user.email}`)) || [];
            
            if (userFiles.length === 0) {
                filesGrid.innerHTML = `
                    <div style="grid-column: 1/-1; text-align: center; padding: 50px;">
                        <i class="fas fa-file-alt fa-3x" style="color: rgba(255,255,255,0.1); margin-bottom: 20px;"></i>
                        <p>لا توجد ملفات مخزنة بعد</p>
                        <p>قم برفع أول ملف باستخدام قسم "رفع ملف"</p>
                    </div>
                `;
                return;
            }
            
            let html = '';
            userFiles.forEach(file => {
                html += `
                    <div class="file-card">
                        <div class="file-icon">
                            <i class="fas fa-file${file.type === 'pdf' ? '-pdf' : file.type === 'image' ? '-image' : ''}"></i>
                        </div>
                        <h4>${file.name}</h4>
                        <p style="color: #a5b4cb; font-size: 0.9rem; margin: 5px 0;">${file.size} ميغابايت</p>
                        <p style="color: #a5b4cb; font-size: 0.8rem;">${file.date}</p>
                    </div>
                `;
            });
            
            filesGrid.innerHTML = html;
        }

        function loadUserFolders(user) {
            const foldersGrid = document.getElementById('folders-grid');
            const userFolders = JSON.parse(localStorage.getItem(`userFolders_${user.email}`)) || [
                { name: 'الملفات العامة', fileCount: 0 },
                { name: 'الملفات الشخصية', fileCount: 0 }
            ];
            
            let html = '';
            userFolders.forEach(folder => {
                html += `
                    <div class="file-card">
                        <div class="file-icon" style="color: #ff9800;">
                            <i class="fas fa-folder"></i>
                        </div>
                        <h4>${folder.name}</h4>
                        <p style="color: #a5b4cb; font-size: 0.9rem; margin: 5px 0;">${folder.fileCount} ملف</p>
                    </div>
                `;
            });
            
            foldersGrid.innerHTML = html;
        }

        function updateStorageInfo(user) {
            const storageUsed = user.storageUsed || 0;
            const storageLimit = 100; // يمكن جعلها من الإعدادات
            
            const percentage = (storageUsed / storageLimit) * 100;
            document.getElementById('storage-bar').style.width = `${percentage}%`;
            document.getElementById('storage-text').textContent = 
                `${storageUsed.toFixed(1)} ميغابايت مستخدمة من ${storageLimit} ميغابايت`;
        }

        function setupFileUpload(user) {
            const browseBtn = document.getElementById('browse-files');
            const fileInput = document.getElementById('file-upload-input');
            const uploadQueue = document.getElementById('upload-queue');
            const queueList = document.getElementById('queue-list');
            const startUploadBtn = document.getElementById('start-upload');
            
            let filesToUpload = [];
            
            browseBtn.addEventListener('click', () => fileInput.click());
            
            fileInput.addEventListener('change', function() {
                if (this.files.length > 0) {
                    filesToUpload = Array.from(this.files);
                    displayUploadQueue();
                }
            });
            
            function displayUploadQueue() {
                let html = '';
                filesToUpload.forEach((file, index) => {
                    const size = (file.size / (1024 * 1024)).toFixed(2);
                    html += `
                        <div style="background: rgba(255,255,255,0.05); padding: 10px; margin: 10px 0; border-radius: 5px;">
                            <div style="display: flex; justify-content: space-between; align-items: center;">
                                <div>
                                    <i class="fas fa-file" style="margin-left: 10px;"></i>
                                    <span>${file.name}</span>
                                </div>
                                <div>
                                    <span style="color: #a5b4cb; margin-left: 20px;">${size} ميغابايت</span>
                                    <button onclick="removeFromQueue(${index})" style="background: #f44336; color: white; border: none; padding: 5px 10px; border-radius: 5px; cursor: pointer;">
                                        <i class="fas fa-times"></i>
                                    </button>
                                </div>
                            </div>
                        </div>
                    `;
                });
                
                queueList.innerHTML = html;
                uploadQueue.style.display = 'block';
            }
            
            window.removeFromQueue = function(index) {
                filesToUpload.splice(index, 1);
                if (filesToUpload.length > 0) {
                    displayUploadQueue();
                } else {
                    uploadQueue.style.display = 'none';
                }
            };
            
            startUploadBtn.addEventListener('click', function() {
                if (filesToUpload.length === 0) {
                    alert('لا توجد ملفات للرفع');
                    return;
                }
                
                // محاكاة رفع الملفات
                let uploadedCount = 0;
                const userFiles = JSON.parse(localStorage.getItem(`userFiles_${user.email}`)) || [];
                
                filesToUpload.forEach(file => {
                    const fileSize = (file.size / (1024 * 1024)).toFixed(2);
                    const newFile = {
                        id: Date.now(),
                        name: file.name,
                        size: fileSize,
                        type: getFileType(file),
                        date: new Date().toLocaleDateString('ar-SA'),
                        folder: 'الملفات العامة'
                    };
                    
                    userFiles.push(newFile);
                    uploadedCount++;
                });
                
                // تحديث تخزين المستخدم
                const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
                const userIndex = users.findIndex(u => u.email === user.email);
                if (userIndex !== -1) {
                    users[userIndex].storageUsed += filesToUpload.reduce((total, file) => 
                        total + (file.size / (1024 * 1024)), 0);
                    localStorage.setItem('secureStorageUsers', JSON.stringify(users));
                    
                    // تحديث الجلسة
                    const updatedUser = users[userIndex];
                    sessionStorage.setItem('currentUser', JSON.stringify(updatedUser));
                }
                
                localStorage.setItem(`userFiles_${user.email}`, JSON.stringify(userFiles));
                
                alert(`تم رفع ${uploadedCount} ملف بنجاح`);
                filesToUpload = [];
                uploadQueue.style.display = 'none';
                fileInput.value = '';
                
                // تحديث العرض
                loadUserFiles(user);
                updateStorageInfo(user);
            });
        }

        function getFileType(file) {
            if (file.type.includes('pdf')) return 'pdf';
            if (file.type.includes('image')) return 'image';
            if (file.type.includes('video')) return 'video';
            if (file.type.includes('text') || file.type.includes('document')) return 'document';
            return 'other';
        }

        function createNewFolder(user) {
            const folderName = prompt('أدخل اسم المجلد الجديد:');
            if (folderName && folderName.trim()) {
                const userFolders = JSON.parse(localStorage.getItem(`userFolders_${user.email}`)) || [];
                userFolders.push({
                    name: folderName.trim(),
                    fileCount: 0
                });
                localStorage.setItem(`userFolders_${user.email}`, JSON.stringify(userFolders));
                loadUserFolders(user);
                alert('تم إنشاء المجلد بنجاح');
            }
        }

        function saveUserProfile(user) {
            const newName = document.getElementById('profile-name').value.trim();
            const currentPassword = document.getElementById('current-password').value;
            const newPassword = document.getElementById('new-password').value;
            const confirmNewPassword = document.getElementById('confirm-new-password').value;
            const messageElement = document.getElementById('profile-message');
            
            const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
            const userIndex = users.findIndex(u => u.email === user.email);
            
            if (userIndex === -1) return;
            
            let hasChanges = false;
            
            // تحديث الاسم
            if (newName && newName !== user.name) {
                users[userIndex].name = newName;
                hasChanges = true;
            }
            
            // تحديث كلمة المرور
            if (currentPassword && newPassword && confirmNewPassword) {
                if (users[userIndex].password !== currentPassword) {
                    messageElement.textContent = 'كلمة المرور الحالية غير صحيحة';
                    messageElement.className = 'message error';
                    return;
                }
                
                if (newPassword !== confirmNewPassword) {
                    messageElement.textContent = 'كلمتا المرور الجديدة غير متطابقتين';
                    messageElement.className = 'message error';
                    return;
                }
                
                if (newPassword.length < 6) {
                    messageElement.textContent = 'كلمة المرور يجب أن تكون 6 أحرف على الأقل';
                    messageElement.className = 'message error';
                    return;
                }
                
                users[userIndex].password = newPassword;
                hasChanges = true;
            }
            
            if (hasChanges) {
                localStorage.setItem('secureStorageUsers', JSON.stringify(users));
                
                // تحديث الجلسة
                const updatedUser = users[userIndex];
                sessionStorage.setItem('currentUser', JSON.stringify(updatedUser));
                
                messageElement.textContent = 'تم حفظ التغييرات بنجاح';
                messageElement.className = 'message success';
                
                // تحديث العرض
                document.getElementById('user-name-display').textContent = updatedUser.name;
                document.getElementById('dashboard-title').textContent = `لوحة تحكم ${updatedUser.name}`;
                
                // تفريغ حقول كلمة المرور
                document.getElementById('current-password').value = '';
                document.getElementById('new-password').value = '';
                document.getElementById('confirm-new-password').value = '';
            } else {
                messageElement.textContent = 'لم تقم بإجراء أي تغييرات';
                messageElement.className = 'message';
            }
            
            setTimeout(() => {
                messageElement.textContent = '';
                messageElement.className = 'message';
            }, 3000);
        }

        // لوحة تحكم المالك
        function loadOwnerDashboard() {
            setupOwnerMenu();
            loadOwnerOverview();
            loadAllUsers();
            loadAllFiles();
            setupSystemSettings();
            
            document.getElementById('owner-logout').addEventListener('click', logout);
        }

        function setupOwnerMenu() {
            document.querySelectorAll('#owner-page .menu-item').forEach(item => {
                item.addEventListener('click', function() {
                    document.querySelectorAll('#owner-page .menu-item').forEach(i => {
                        i.classList.remove('active');
                    });
                    this.classList.add('active');
                    
                    document.querySelectorAll('#owner-page .content-section').forEach(section => {
                        section.classList.remove('active');
                    });
                    
                    const sectionId = this.dataset.section + '-section';
                    document.getElementById(sectionId).classList.add('active');
                });
            });
        }

        function loadOwnerOverview() {
            const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
            const regularUsers = users.filter(u => !u.isOwner);
            
            // تحديث الإحصائيات
            document.getElementById('total-users-count').textContent = regularUsers.length;
            
            let totalFiles = 0;
            let totalStorage = 0;
            
            users.forEach(user => {
                const userFiles = JSON.parse(localStorage.getItem(`userFiles_${user.email}`)) || [];
                totalFiles += userFiles.length;
                totalStorage += user.storageUsed || 0;
            });
            
            document.getElementById('total-files-count').textContent = totalFiles;
            document.getElementById('total-storage-used').textContent = totalStorage.toFixed(1) + ' ميغابايت';
            
            // عرض المستخدمين الجدد
            const recentUsersDiv = document.getElementById('recent-users');
            const recentUsers = [...regularUsers]
                .sort((a, b) => new Date(b.createdAt) - new Date(a.createdAt))
                .slice(0, 5);
            
            if (recentUsers.length === 0) {
                recentUsersDiv.innerHTML = '<p style="color: #a5b4cb; text-align: center; padding: 20px;">لا يوجد مستخدمون</p>';
                return;
            }
            
            let html = '';
            recentUsers.forEach(user => {
                const date = new Date(user.createdAt).toLocaleDateString('ar-SA');
                html += `
                    <div style="display: flex; justify-content: space-between; align-items: center; padding: 10px; border-bottom: 1px solid rgba(255,255,255,0.1);">
                        <div>
                            <strong>${user.name}</strong>
                            <p style="color: #a5b4cb; font-size: 0.9rem; margin: 5px 0;">${user.email}</p>
                        </div>
                        <span style="color: #a5b4cb; font-size: 0.9rem;">${date}</span>
                    </div>
                `;
            });
            
            recentUsersDiv.innerHTML = html;
        }

        function loadAllUsers() {
            const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
            const regularUsers = users.filter(u => !u.isOwner);
            const tbody = document.getElementById('users-table-body');
            
            if (regularUsers.length === 0) {
                tbody.innerHTML = `
                    <tr>
                        <td colspan="5" style="text-align: center; padding: 30px; color: #a5b4cb;">
                            لا يوجد مستخدمون مسجلون
                        </td>
                    </tr>
                `;
                return;
            }
            
            let html = '';
            regularUsers.forEach(user => {
                const userFiles = JSON.parse(localStorage.getItem(`userFiles_${user.email}`)) || [];
                const date = new Date(user.createdAt).toLocaleDateString('ar-SA');
                
                html += `
                    <tr>
                        <td>${user.name}</td>
                        <td>${user.email}</td>
                        <td>${date}</td>
                        <td>${userFiles.length}</td>
                        <td>
                            <button onclick="deleteUser('${user.email}')" style="background: #f44336; color: white; border: none; padding: 5px 10px; border-radius: 5px; cursor: pointer;">
                                <i class="fas fa-trash"></i> حذف
                            </button>
                        </td>
                    </tr>
                `;
            });
            
            tbody.innerHTML = html;
        }

        function loadAllFiles() {
            const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
            const tbody = document.getElementById('all-files-body');
            
            let allFiles = [];
            users.forEach(user => {
                const userFiles = JSON.parse(localStorage.getItem(`userFiles_${user.email}`)) || [];
                userFiles.forEach(file => {
                    allFiles.push({
                        ...file,
                        owner: user.name
                    });
                });
            });
            
            if (allFiles.length === 0) {
                tbody.innerHTML = `
                    <tr>
                        <td colspan="5" style="text-align: center; padding: 30px; color: #a5b4cb;">
                            لا توجد ملفات
                        </td>
                    </tr>
                `;
                return;
            }
            
            let html = '';
            allFiles.forEach(file => {
                html += `
                    <tr>
                        <td>${file.name}</td>
                        <td>${file.owner}</td>
                        <td>${file.type}</td>
                        <td>${file.size} ميغابايت</td>
                        <td>${file.date}</td>
                    </tr>
                `;
            });
            
            tbody.innerHTML = html;
        }

        function setupSystemSettings() {
            const settings = JSON.parse(localStorage.getItem('systemSettings')) || {};
            
            document.getElementById('system-name').value = settings.systemName || 'نظام التخزين الآمن';
            document.getElementById('max-file-size').value = settings.maxFileSize || 100;
            document.getElementById('user-storage-limit').value = settings.userStorageLimit || 100;
            document.getElementById('allow-registration').checked = settings.allowRegistration !== false;
            
            document.getElementById('save-system-settings').addEventListener('click', function() {
                const newSettings = {
                    systemName: document.getElementById('system-name').value,
                    maxFileSize: parseInt(document.getElementById('max-file-size').value),
                    userStorageLimit: parseInt(document.getElementById('user-storage-limit').value),
                    allowRegistration: document.getElementById('allow-registration').checked
                };
                
                localStorage.setItem('systemSettings', JSON.stringify(newSettings));
                
                const messageElement = document.getElementById('settings-message');
                messageElement.textContent = 'تم حفظ الإعدادات بنجاح';
                messageElement.className = 'message success';
                
                setTimeout(() => {
                    messageElement.textContent = '';
                    messageElement.className = 'message';
                }, 3000);
            });
        }

        // وظائف عامة
        function logout() {
            sessionStorage.removeItem('currentUser');
            showPage('login-page');
            document.getElementById('login-form').reset();
            document.getElementById('register-form').reset();
        }

        // وظيفة حذف المستخدم (للمالك)
        window.deleteUser = function(email) {
            if (confirm(`هل أنت متأكد من حذف المستخدم ${email}؟ سيتم حذف جميع ملفاته.`)) {
                const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
                const filteredUsers = users.filter(u => u.email !== email);
                localStorage.setItem('secureStorageUsers', JSON.stringify(filteredUsers));
                
                // حذف ملفات المستخدم
                localStorage.removeItem(`userFiles_${email}`);
                localStorage.removeItem(`userFolders_${email}`);
                
                // إعادة تحميل البيانات
                loadOwnerOverview();
                loadAllUsers();
                loadAllFiles();
                
                alert('تم حذف المستخدم بنجاح');
            }
        };
    </script>
</body>
</html>
