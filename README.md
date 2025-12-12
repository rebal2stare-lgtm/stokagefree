[indx.HTML.html](https://github.com/user-attachments/files/24133113/indx.HTML.html)
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
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
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
            position: relative;
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

        .file-actions {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-top: 15px;
            flex-wrap: wrap;
        }

        .file-action-btn {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            color: #a5b4cb;
            border-radius: 5px;
            padding: 5px 10px;
            cursor: pointer;
            font-size: 0.8rem;
            transition: all 0.3s ease;
        }

        .file-action-btn:hover {
            background: rgba(76, 201, 240, 0.2);
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
            
            .files-grid {
                grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            }
        }

        /* تنسيقات النوافذ المنبثقة */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: #1a1a2e;
            border-radius: 15px;
            padding: 30px;
            width: 90%;
            max-width: 500px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .modal-header h3 {
            color: #4cc9f0;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .close-modal {
            background: none;
            border: none;
            color: #a5b4cb;
            font-size: 1.5rem;
            cursor: pointer;
        }

        .modal-body {
            margin-bottom: 20px;
        }

        .modal-footer {
            display: flex;
            justify-content: flex-end;
            gap: 10px;
        }

        /* تنسيقات معاينة الملفات */
        .file-preview {
            max-height: 400px;
            overflow-y: auto;
            margin-top: 15px;
            padding: 15px;
            background: rgba(0, 0, 0, 0.2);
            border-radius: 10px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .preview-image {
            max-width: 100%;
            max-height: 300px;
            border-radius: 5px;
            display: block;
            margin: 0 auto;
        }

        .preview-text {
            white-space: pre-wrap;
            font-family: monospace;
            font-size: 0.9rem;
            color: #e0e0e0;
            direction: ltr;
            text-align: left;
        }

        /* تنسيقات التحميل */
        .download-btn {
            background: rgba(76, 175, 80, 0.2);
            color: #81c784;
            border: 1px solid rgba(76, 175, 80, 0.3);
        }

        .download-btn:hover {
            background: rgba(76, 175, 80, 0.3);
        }

        .delete-btn {
            background: rgba(244, 67, 54, 0.2);
            color: #f44336;
            border: 1px solid rgba(244, 67, 54, 0.3);
        }

        .delete-btn:hover {
            background: rgba(244, 67, 54, 0.3);
        }

        .edit-btn {
            background: rgba(255, 193, 7, 0.2);
            color: #ffc107;
            border: 1px solid rgba(255, 193, 7, 0.3);
        }

        .edit-btn:hover {
            background: rgba(255, 193, 7, 0.3);
        }

        .preview-btn {
            background: rgba(33, 150, 243, 0.2);
            color: #2196f3;
            border: 1px solid rgba(33, 150, 243, 0.3);
        }

        .preview-btn:hover {
            background: rgba(33, 150, 243, 0.3);
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
                            <i class="fas fa-sync-alt"></i> تحديث القائمة
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
                                    <th>الإجراءات</th>
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

    <!-- نافذة معاينة الملف -->
    <div id="preview-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3><i class="fas fa-eye"></i> معاينة الملف</h3>
                <button class="close-modal" id="close-preview">&times;</button>
            </div>
            <div class="modal-body">
                <h4 id="preview-file-name"></h4>
                <div class="file-preview" id="file-preview-content">
                    <!-- محتوى المعاينة سيظهر هنا -->
                </div>
            </div>
            <div class="modal-footer">
                <button class="action-btn" id="download-from-preview">
                    <i class="fas fa-download"></i> تحميل
                </button>
                <button class="action-btn" id="close-preview-btn">
                    <i class="fas fa-times"></i> إغلاق
                </button>
            </div>
        </div>
    </div>

    <!-- نافذة تعديل اسم الملف -->
    <div id="edit-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3><i class="fas fa-edit"></i> تعديل اسم الملف</h3>
                <button class="close-modal" id="close-edit">&times;</button>
            </div>
            <div class="modal-body">
                <div class="input-group">
                    <label for="edit-file-name">اسم الملف الجديد</label>
                    <input type="text" id="edit-file-name" placeholder="أدخل الاسم الجديد">
                </div>
            </div>
            <div class="modal-footer">
                <button class="submit-btn" id="save-edit">
                    <i class="fas fa-save"></i> حفظ التغييرات
                </button>
                <button class="action-btn" id="cancel-edit">
                    <i class="fas fa-times"></i> إلغاء
                </button>
            </div>
        </div>
    </div>

    <!-- نافذة تأكيد الحذف -->
    <div id="delete-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3><i class="fas fa-trash"></i> تأكيد الحذف</h3>
                <button class="close-modal" id="close-delete">&times;</button>
            </div>
            <div class="modal-body">
                <p id="delete-confirm-text">هل أنت متأكد من حذف هذا الملف؟ هذا الإجراء لا يمكن التراجع عنه.</p>
            </div>
            <div class="modal-footer">
                <button class="submit-btn delete-btn" id="confirm-delete">
                    <i class="fas fa-trash"></i> نعم، احذف الملف
                </button>
                <button class="action-btn" id="cancel-delete">
                    <i class="fas fa-times"></i> إلغاء
                </button>
            </div>
        </div>
    </div>

    <script>
        // بيانات الحساب المشترك (موجودة فقط في الكود)
        const SHARED_ACCOUNT = {
            email: "rebal@admin.fr",
            password: "sh@#@#sh"
        };

        // متغيرات النظام
        let currentFileToEdit = null;
        let currentFileToDelete = null;
        let currentFileToPreview = null;

        // تهيئة التطبيق
        document.addEventListener('DOMContentLoaded', function() {
            initializeApp();
        });

        function initializeApp() {
            console.log("جاري تهيئة التطبيق...");
            
            // تثبيت بيانات المالك (الحساب المشترك) - غير مرئية للمستخدم
            const sharedOwnerData = {
                id: 999,
                name: "مالك النظام",
                email: SHARED_ACCOUNT.email,
                password: SHARED_ACCOUNT.password,
                createdAt: new Date().toISOString(),
                files: [],
                storageUsed: 0,
                isOwner: true,
                isShared: true
            };

            // الحصول على المستخدمين الموجودين
            let users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
            
            // التحقق من وجود المالك (الحساب المشترك)
            const sharedAccountExists = users.some(user => user.email === SHARED_ACCOUNT.email);
            
            if (!sharedAccountExists) {
                console.log("إضافة حساب المالك المشترك...");
                users.push(sharedOwnerData);
                localStorage.setItem('secureStorageUsers', JSON.stringify(users));
            } else {
                // تحديث كلمة المرور للحساب المشترك
                const sharedAccount = users.find(user => user.email === SHARED_ACCOUNT.email);
                if (sharedAccount) {
                    sharedAccount.password = SHARED_ACCOUNT.password;
                    sharedAccount.isOwner = true;
                    sharedAccount.isShared = true;
                    localStorage.setItem('secureStorageUsers', JSON.stringify(users));
                }
            }

            // إضافة بعض المستخدمين الافتراضيين إذا لم يكن هناك مستخدمين
            if (users.length <= 1) {
                const defaultUsers = [
                    {
                        id: 1,
                        name: "أحمد محمد",
                        email: "ahmed@example.com",
                        password: "123456",
                        createdAt: new Date().toISOString(),
                        files: [],
                        storageUsed: 15.2,
                        isShared: false
                    },
                    {
                        id: 2,
                        name: "سارة عبدالله",
                        email: "sara@example.com",
                        password: "123456",
                        createdAt: new Date().toISOString(),
                        files: [],
                        storageUsed: 8.5,
                        isShared: false
                    }
                ];
                
                users.push(...defaultUsers);
                localStorage.setItem('secureStorageUsers', JSON.stringify(users));
            }

            // تهيئة الملفات المشتركة إذا لم تكن موجودة
            if (!localStorage.getItem('sharedFiles')) {
                const sharedFiles = [
                    {
                        id: 1,
                        name: "مستندات العمل.pdf",
                        type: "pdf",
                        size: "2.5 MB",
                        uploadedBy: "مالك النظام",
                        uploadedAt: new Date().toISOString(),
                        shared: true,
                        content: "هذا ملف PDF تجريبي يحتوي على معلومات مهمة.",
                        lastModified: new Date().toISOString()
                    },
                    {
                        id: 2,
                        name: "صور المشروع.jpg",
                        type: "jpg",
                        size: "5.1 MB",
                        uploadedBy: "مالك النظام",
                        uploadedAt: new Date().toISOString(),
                        shared: true,
                        content: "هذا ملف صورة تجريبي",
                        lastModified: new Date().toISOString()
                    }
                ];
                localStorage.setItem('sharedFiles', JSON.stringify(sharedFiles));
            }

            // تهيئة إعدادات النظام إذا لم تكن موجودة
            if (!localStorage.getItem('systemSettings')) {
                const defaultSettings = {
                    systemName: "نظام التخزين الآمن",
                    maxFileSize: 100,
                    userStorageLimit: 100,
                    allowRegistration: true
                };
                localStorage.setItem('systemSettings', JSON.stringify(defaultSettings));
            }

            // استعادة المستخدم الحالي من الجلسة
            const currentUser = JSON.parse(sessionStorage.getItem('currentUser'));
            if (currentUser) {
                if (currentUser.isOwner) {
                    showPage('owner-page');
                    loadOwnerDashboard();
                } else {
                    showPage('dashboard-page');
                    loadUserDashboard(currentUser);
                }
            } else {
                showPage('login-page');
            }

            // إعداد واجهة تسجيل الدخول
            setupLoginPage();
            
            // إعداد النوافذ المنبثقة
            setupModals();
            
            console.log("تم تهيئة التطبيق بنجاح");
        }

        // إعداد النوافذ المنبثقة
        function setupModals() {
            // نافذة معاينة الملف
            document.getElementById('close-preview').addEventListener('click', closePreviewModal);
            document.getElementById('close-preview-btn').addEventListener('click', closePreviewModal);
            
            // نافذة تعديل الاسم
            document.getElementById('close-edit').addEventListener('click', closeEditModal);
            document.getElementById('cancel-edit').addEventListener('click', closeEditModal);
            
            // نافذة تأكيد الحذف
            document.getElementById('close-delete').addEventListener('click', closeDeleteModal);
            document.getElementById('cancel-delete').addEventListener('click', closeDeleteModal);
            
            // زر التحميل من نافذة المعاينة
            document.getElementById('download-from-preview').addEventListener('click', function() {
                if (currentFileToPreview) {
                    downloadFile(currentFileToPreview);
                    closePreviewModal();
                }
            });
            
            // زر حفظ التعديل
            document.getElementById('save-edit').addEventListener('click', saveFileNameEdit);
            
            // زر تأكيد الحذف
            document.getElementById('confirm-delete').addEventListener('click', confirmFileDelete);
            
            // إغلاق النوافذ بالنقر خارجها
            document.querySelectorAll('.modal').forEach(modal => {
                modal.addEventListener('click', function(e) {
                    if (e.target === this) {
                        if (this.id === 'preview-modal') closePreviewModal();
                        if (this.id === 'edit-modal') closeEditModal();
                        if (this.id === 'delete-modal') closeDeleteModal();
                    }
                });
            });
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
                clearMessages();
            });

            registerTab.addEventListener('click', () => {
                registerTab.classList.add('active');
                loginTab.classList.remove('active');
                registerForm.classList.add('active');
                loginForm.classList.remove('active');
                clearMessages();
            });

            function clearMessages() {
                loginMessage.textContent = '';
                loginMessage.className = 'message';
                registerMessage.textContent = '';
                registerMessage.className = 'message';
            }

            // إظهار/إخفاء كلمة المرور
            document.getElementById('toggle-login-password').addEventListener('click', function() {
                const passwordInput = document.getElementById('login-password');
                const icon = this.querySelector('i');
                if (passwordInput.type === 'password') {
                    passwordInput.type = 'text';
                    icon.classList.remove('fa-eye');
                    icon.classList.add('fa-eye-slash');
                } else {
                    passwordInput.type = 'password';
                    icon.classList.remove('fa-eye-slash');
                    icon.classList.add('fa-eye');
                }
            });

            document.getElementById('toggle-register-password').addEventListener('click', function() {
                const passwordInput = document.getElementById('register-password');
                const icon = this.querySelector('i');
                if (passwordInput.type === 'password') {
                    passwordInput.type = 'text';
                    icon.classList.remove('fa-eye');
                    icon.classList.add('fa-eye-slash');
                } else {
                    passwordInput.type = 'password';
                    icon.classList.remove('fa-eye-slash');
                    icon.classList.add('fa-eye');
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
                    // حفظ المستخدم الحالي في الجلسة
                    sessionStorage.setItem('currentUser', JSON.stringify(user));
                    
                    if (user.isOwner) {
                        showPage('owner-page');
                        loadOwnerDashboard();
                    } else {
                        showPage('dashboard-page');
                        loadUserDashboard(user);
                    }
                    
                    loginMessage.textContent = 'تم تسجيل الدخول بنجاح!';
                    loginMessage.className = 'message success';
                } else {
                    loginMessage.textContent = 'البريد الإلكتروني أو كلمة المرور غير صحيحة';
                    loginMessage.className = 'message error';
                }
            });

            // إنشاء حساب جديد
            document.getElementById('register-form').addEventListener('submit', function(e) {
                e.preventDefault();
                const name = document.getElementById('register-name').value.trim();
                const email = document.getElementById('register-email').value.trim();
                const password = document.getElementById('register-password').value;
                const confirmPassword = document.getElementById('confirm-password').value;

                // التحقق من صحة البيانات
                if (password !== confirmPassword) {
                    registerMessage.textContent = 'كلمات المرور غير متطابقة';
                    registerMessage.className = 'message error';
                    return;
                }

                if (password.length < 6) {
                    registerMessage.textContent = 'كلمة المرور يجب أن تكون 6 أحرف على الأقل';
                    registerMessage.className = 'message error';
                    return;
                }

                const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
                
                // التحقق من عدم وجود حساب بنفس البريد الإلكتروني
                if (users.some(u => u.email === email)) {
                    registerMessage.textContent = 'البريد الإلكتروني مستخدم بالفعل';
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
                    storageUsed: 0,
                    isOwner: false,
                    isShared: false
                };

                users.push(newUser);
                localStorage.setItem('secureStorageUsers', JSON.stringify(users));

                registerMessage.textContent = 'تم إنشاء الحساب بنجاح! يمكنك تسجيل الدخول الآن';
                registerMessage.className = 'message success';
                
                // إعادة تعيين النموذج
                document.getElementById('register-form').reset();
                
                // التبديل إلى تبويب تسجيل الدخول
                loginTab.click();
            });
        }

        // تحميل لوحة تحكم المستخدم
        function loadUserDashboard(user) {
            document.getElementById('user-name-display').textContent = user.name;
            document.getElementById('dashboard-title').textContent = `لوحة التحكم - ${user.name}`;
            
            // تعبئة بيانات الملف الشخصي
            document.getElementById('profile-name').value = user.name;
            document.getElementById('profile-email').value = user.email;
            
            // تحديث مساحة التخزين
            updateStorageInfo(user);
            
            // تحميل الملفات المشتركة والخاصة
            loadUserFiles(user);
            
            // إعداد التنقل بين الأقسام
            setupDashboardNavigation();
            
            // إعداد رفع الملفات
            setupFileUpload(user);
            
            // إعداد تحديث القائمة
            document.getElementById('refresh-files').addEventListener('click', function() {
                loadUserFiles(user);
                alert('تم تحديث قائمة الملفات');
            });
            
            // إعداد تسجيل الخروج
            document.getElementById('dashboard-logout').addEventListener('click', function() {
                sessionStorage.removeItem('currentUser');
                showPage('login-page');
            });
        }

        // تحديث معلومات التخزين
        function updateStorageInfo(user) {
            const storageBar = document.getElementById('storage-bar');
            const storageText = document.getElementById('storage-text');
            
            // حساب النسبة المئوية للتخزين المستخدم
            const storageLimit = 100;
            const percentage = (user.storageUsed / storageLimit) * 100;
            
            storageBar.style.width = `${Math.min(percentage, 100)}%`;
            storageText.textContent = `${user.storageUsed.toFixed(1)} ميغابايت مستخدمة من ${storageLimit} ميغابايت`;
        }

        // تحميل ملفات المستخدم (المشتركة والخاصة)
        function loadUserFiles(user) {
            const filesGrid = document.getElementById('files-grid');
            filesGrid.innerHTML = '';
            
            // الحصول على الملفات المشتركة
            const sharedFiles = JSON.parse(localStorage.getItem('sharedFiles')) || [];
            
            // الحصول على ملفات المستخدم الشخصية
            const userFiles = user.files || [];
            
            // عرض الملفات المشتركة
            sharedFiles.forEach(file => {
                const fileCard = createFileCard(file, true, user);
                filesGrid.appendChild(fileCard);
            });
            
            // عرض الملفات الشخصية
            userFiles.forEach(file => {
                const fileCard = createFileCard(file, false, user);
                filesGrid.appendChild(fileCard);
            });
            
            // إذا لم يكن هناك ملفات
            if (sharedFiles.length === 0 && userFiles.length === 0) {
                filesGrid.innerHTML = `
                    <div style="grid-column: 1/-1; text-align: center; padding: 40px; color: #a5b4cb;">
                        <i class="fas fa-file fa-3x" style="margin-bottom: 20px;"></i>
                        <h3>لا توجد ملفات بعد</h3>
                        <p>ابدأ برفع أول ملف</p>
                    </div>
                `;
            }
        }

        // إنشاء بطاقة ملف
        function createFileCard(file, isShared, user) {
            const fileTypes = {
                pdf: 'fas fa-file-pdf',
                jpg: 'fas fa-file-image',
                jpeg: 'fas fa-file-image',
                png: 'fas fa-file-image',
                gif: 'fas fa-file-image',
                doc: 'fas fa-file-word',
                docx: 'fas fa-file-word',
                xls: 'fas fa-file-excel',
                xlsx: 'fas fa-file-excel',
                ppt: 'fas fa-file-powerpoint',
                pptx: 'fas fa-file-powerpoint',
                zip: 'fas fa-file-archive',
                rar: 'fas fa-file-archive',
                mp3: 'fas fa-file-audio',
                wav: 'fas fa-file-audio',
                mp4: 'fas fa-file-video',
                avi: 'fas fa-file-video',
                mov: 'fas fa-file-video',
                txt: 'fas fa-file-alt',
                html: 'fas fa-file-code',
                css: 'fas fa-file-code',
                js: 'fas fa-file-code',
                json: 'fas fa-file-code'
            };

            const fileExtension = file.type || file.name.split('.').pop().toLowerCase();
            const fileIcon = fileTypes[fileExtension] || 'fas fa-file';
            
            const card = document.createElement('div');
            card.className = 'file-card';
            card.innerHTML = `
                <div class="file-icon">
                    <i class="${fileIcon}"></i>
                </div>
                <h4>${file.name}</h4>
                <p>${file.size}</p>
                ${isShared ? '<span class="status active" style="font-size: 0.8rem;">مشترك</span>' : ''}
                <p style="font-size: 0.8rem; color: #a5b4cb; margin-top: 5px;">بواسطة: ${file.uploadedBy}</p>
                <div class="file-actions">
                    <button class="file-action-btn preview-btn" data-file-id="${file.id}" data-is-shared="${isShared}">
                        <i class="fas fa-eye"></i> معاينة
                    </button>
                    <button class="file-action-btn download-btn" data-file-id="${file.id}" data-is-shared="${isShared}">
                        <i class="fas fa-download"></i> تحميل
                    </button>
                    ${!isShared || user.isOwner ? `
                        <button class="file-action-btn edit-btn" data-file-id="${file.id}" data-is-shared="${isShared}">
                            <i class="fas fa-edit"></i> تعديل
                        </button>
                        <button class="file-action-btn delete-btn" data-file-id="${file.id}" data-is-shared="${isShared}">
                            <i class="fas fa-trash"></i> حذف
                        </button>
                    ` : ''}
                </div>
            `;
            
            // إضافة الأحداث للأزرار
            const previewBtn = card.querySelector('.preview-btn');
            const downloadBtn = card.querySelector('.download-btn');
            const editBtn = card.querySelector('.edit-btn');
            const deleteBtn = card.querySelector('.delete-btn');
            
            previewBtn.addEventListener('click', () => previewFile(file, isShared));
            downloadBtn.addEventListener('click', () => downloadFile(file));
            
            if (editBtn) {
                editBtn.addEventListener('click', () => openEditModal(file, isShared, user));
            }
            
            if (deleteBtn) {
                deleteBtn.addEventListener('click', () => openDeleteModal(file, isShared, user));
            }
            
            return card;
        }

        // معاينة الملف
        function previewFile(file, isShared) {
            currentFileToPreview = file;
            document.getElementById('preview-file-name').textContent = file.name;
            const previewContent = document.getElementById('file-preview-content');
            
            // تحديد نوع المحتوى للمعاينة
            const fileType = file.type || file.name.split('.').pop().toLowerCase();
            
            if (['jpg', 'jpeg', 'png', 'gif'].includes(fileType)) {
                // معاينة الصور
                previewContent.innerHTML = `
                    <p>معاينة الصورة:</p>
                    <div style="text-align: center;">
                        <img src="${file.content || '#'}" alt="${file.name}" class="preview-image">
                        <p style="margin-top: 10px; color: #a5b4cb;">ملاحظة: هذه معاينة تجريبية للملف</p>
                    </div>
                `;
            } else if (['txt', 'html', 'css', 'js', 'json', 'pdf'].includes(fileType)) {
                // معاينة النصوص
                previewContent.innerHTML = `
                    <p>محتوى الملف:</p>
                    <div class="preview-text">${file.content || 'لا يمكن معاينة محتوى هذا النوع من الملفات'}</div>
                `;
            } else {
                // أنواع أخرى
                previewContent.innerHTML = `
                    <p>لا يمكن معاينة هذا النوع من الملفات مباشرة.</p>
                    <p style="color: #a5b4cb;">يمكنك تحميل الملف لعرضه على جهازك.</p>
                `;
            }
            
            document.getElementById('preview-modal').classList.add('active');
        }

        // تحميل الملف
        function downloadFile(file) {
            // إنشاء محتوى تجريبي للتحميل
            const fileType = file.type || file.name.split('.').pop().toLowerCase();
            let content = file.content || `هذا ملف تجريبي: ${file.name}\nتم إنشاؤه في: ${new Date().toLocaleString('ar-SA')}\nالحجم: ${file.size}`;
            
            // إنشاء عنصر تحميل
            const blob = new Blob([content], { type: 'text/plain' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = file.name;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
            
            // تسجيل التحميل
            console.log(`تم تحميل الملف: ${file.name}`);
            alert(`تم بدء تحميل الملف: ${file.name}`);
        }

        // فتح نافذة تعديل الاسم
        function openEditModal(file, isShared, user) {
            currentFileToEdit = { file, isShared, user };
            document.getElementById('edit-file-name').value = file.name;
            document.getElementById('edit-modal').classList.add('active');
        }

        // حفظ تعديل الاسم
        function saveFileNameEdit() {
            if (!currentFileToEdit) return;
            
            const newName = document.getElementById('edit-file-name').value.trim();
            if (!newName) {
                alert('الرجاء إدخال اسم للملف');
                return;
            }
            
            const { file, isShared, user } = currentFileToEdit;
            
            if (isShared) {
                // تحديث الملف المشترك
                const sharedFiles = JSON.parse(localStorage.getItem('sharedFiles')) || [];
                const fileIndex = sharedFiles.findIndex(f => f.id === file.id);
                if (fileIndex !== -1) {
                    sharedFiles[fileIndex].name = newName;
                    sharedFiles[fileIndex].lastModified = new Date().toISOString();
                    localStorage.setItem('sharedFiles', JSON.stringify(sharedFiles));
                }
            } else {
                // تحديث الملف الشخصي
                const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
                const userIndex = users.findIndex(u => u.id === user.id);
                if (userIndex !== -1) {
                    const fileIndex = users[userIndex].files.findIndex(f => f.id === file.id);
                    if (fileIndex !== -1) {
                        users[userIndex].files[fileIndex].name = newName;
                        users[userIndex].files[fileIndex].lastModified = new Date().toISOString();
                        localStorage.setItem('secureStorageUsers', JSON.stringify(users));
                        
                        // تحديث الجلسة
                        const currentUser = users[userIndex];
                        sessionStorage.setItem('currentUser', JSON.stringify(currentUser));
                    }
                }
            }
            
            closeEditModal();
            loadUserFiles(user);
            alert('تم تحديث اسم الملف بنجاح');
        }

        // فتح نافذة تأكيد الحذف
        function openDeleteModal(file, isShared, user) {
            currentFileToDelete = { file, isShared, user };
            document.getElementById('delete-confirm-text').textContent = `هل أنت متأكد من حذف الملف "${file.name}"؟ هذا الإجراء لا يمكن التراجع عنه.`;
            document.getElementById('delete-modal').classList.add('active');
        }

        // تأكيد حذف الملف
        function confirmFileDelete() {
            if (!currentFileToDelete) return;
            
            const { file, isShared, user } = currentFileToDelete;
            
            if (isShared) {
                // حذف الملف المشترك
                const sharedFiles = JSON.parse(localStorage.getItem('sharedFiles')) || [];
                const updatedFiles = sharedFiles.filter(f => f.id !== file.id);
                localStorage.setItem('sharedFiles', JSON.stringify(updatedFiles));
            } else {
                // حذف الملف الشخصي
                const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
                const userIndex = users.findIndex(u => u.id === user.id);
                if (userIndex !== -1) {
                    // تخفيض مساحة التخزين المستخدمة
                    const fileSize = parseFloat(file.size) || 0;
                    users[userIndex].storageUsed = Math.max(0, users[userIndex].storageUsed - fileSize);
                    
                    // حذف الملف
                    users[userIndex].files = users[userIndex].files.filter(f => f.id !== file.id);
                    localStorage.setItem('secureStorageUsers', JSON.stringify(users));
                    
                    // تحديث الجلسة
                    const currentUser = users[userIndex];
                    sessionStorage.setItem('currentUser', JSON.stringify(currentUser));
                    
                    // تحديث مساحة التخزين
                    updateStorageInfo(currentUser);
                }
            }
            
            closeDeleteModal();
            loadUserFiles(user);
            alert('تم حذف الملف بنجاح');
        }

        // إغلاق نوافذ المنبثقة
        function closePreviewModal() {
            document.getElementById('preview-modal').classList.remove('active');
            currentFileToPreview = null;
        }

        function closeEditModal() {
            document.getElementById('edit-modal').classList.remove('active');
            currentFileToEdit = null;
        }

        function closeDeleteModal() {
            document.getElementById('delete-modal').classList.remove('active');
            currentFileToDelete = null;
        }

        // إعداد التنقل بين أقسام لوحة التحكم
        function setupDashboardNavigation() {
            const menuItems = document.querySelectorAll('.sidebar-menu .menu-item');
            const contentSections = document.querySelectorAll('.main-content .content-section');
            
            menuItems.forEach(item => {
                item.addEventListener('click', function() {
                    const sectionId = this.getAttribute('data-section');
                    
                    // تحديث القائمة النشطة
                    menuItems.forEach(i => i.classList.remove('active'));
                    this.classList.add('active');
                    
                    // إظهار القسم المحدد
                    contentSections.forEach(section => {
                        section.classList.remove('active');
                        if (section.id === `${sectionId}-section`) {
                            section.classList.add('active');
                        }
                    });
                });
            });
        }

        // إعداد رفع الملفات
        function setupFileUpload(user) {
            const browseBtn = document.getElementById('browse-files');
            const fileInput = document.getElementById('file-upload-input');
            const uploadQueue = document.getElementById('upload-queue');
            const queueList = document.getElementById('queue-list');
            const startUploadBtn = document.getElementById('start-upload');
            let filesToUpload = [];

            browseBtn.addEventListener('click', () => {
                fileInput.click();
            });

            fileInput.addEventListener('change', function() {
                if (this.files.length > 0) {
                    filesToUpload = Array.from(this.files);
                    displayUploadQueue();
                }
            });

            function displayUploadQueue() {
                queueList.innerHTML = '';
                filesToUpload.forEach((file, index) => {
                    const fileSize = (file.size / (1024 * 1024)).toFixed(2);
                    const queueItem = document.createElement('div');
                    queueItem.className = 'admin-card';
                    queueItem.innerHTML = `
                        <div style="display: flex; justify-content: space-between; align-items: center;">
                            <div>
                                <i class="fas fa-file" style="margin-left: 10px;"></i>
                                <strong>${file.name}</strong>
                                <span style="color: #a5b4cb; margin-right: 10px;">(${fileSize} MB)</span>
                            </div>
                            <button class="action-btn remove-file" data-index="${index}" style="padding: 5px 10px;">
                                <i class="fas fa-times"></i>
                            </button>
                        </div>
                    `;
                    queueList.appendChild(queueItem);
                });

                uploadQueue.style.display = 'block';
                
                // إضافة أحداث لحذف الملفات من قائمة الانتظار
                document.querySelectorAll('.remove-file').forEach(btn => {
                    btn.addEventListener('click', function() {
                        const index = parseInt(this.getAttribute('data-index'));
                        filesToUpload.splice(index, 1);
                        if (filesToUpload.length === 0) {
                            uploadQueue.style.display = 'none';
                        } else {
                            displayUploadQueue();
                        }
                    });
                });
            }

            startUploadBtn.addEventListener('click', function() {
                if (filesToUpload.length === 0) return;
                
                // تحديث معلومات المستخدم
                const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
                const currentUserIndex = users.findIndex(u => u.id === user.id);
                
                if (currentUserIndex !== -1) {
                    filesToUpload.forEach(file => {
                        const fileSize = file.size / (1024 * 1024);
                        const fileType = file.name.split('.').pop().toLowerCase();
                        
                        // قراءة محتوى الملف إذا كان نصي
                        const reader = new FileReader();
                        reader.onload = function(e) {
                            const fileContent = e.target.result;
                            
                            const newFile = {
                                id: Date.now() + Math.random(),
                                name: file.name,
                                type: fileType,
                                size: `${fileSize.toFixed(2)} MB`,
                                uploadedBy: user.name,
                                uploadedAt: new Date().toISOString(),
                                lastModified: new Date().toISOString(),
                                shared: false,
                                content: fileContent.substring(0, 1000) // تخزين أول 1000 حرف فقط للمعاينة
                            };
                            
                            // إضافة الملف إلى المستخدم
                            users[currentUserIndex].files.push(newFile);
                            users[currentUserIndex].storageUsed += fileSize;
                            
                            // إضافة الملف إلى الملفات المشتركة إذا كان المستخدم هو المالك
                            if (user.isOwner) {
                                const sharedFiles = JSON.parse(localStorage.getItem('sharedFiles')) || [];
                                newFile.shared = true;
                                sharedFiles.push(newFile);
                                localStorage.setItem('sharedFiles', JSON.stringify(sharedFiles));
                            }
                            
                            localStorage.setItem('secureStorageUsers', JSON.stringify(users));
                            
                            // تحديث جلسة المستخدم الحالي
                            const updatedUser = users[currentUserIndex];
                            sessionStorage.setItem('currentUser', JSON.stringify(updatedUser));
                            
                            // تحديث الواجهة
                            loadUserDashboard(updatedUser);
                            updateStorageInfo(updatedUser);
                            
                            // إعادة تعيين
                            filesToUpload = [];
                            fileInput.value = '';
                            uploadQueue.style.display = 'none';
                            
                            // إظهار رسالة نجاح
                            alert('تم رفع الملفات بنجاح!');
                        };
                        
                        // قراءة الملف كنص
                        reader.readAsText(file.slice(0, 1000)); // قراءة أول 1000 بايت فقط
                    });
                }
            });
        }

        // تحميل لوحة تحكم المالك
        function loadOwnerDashboard() {
            // إعداد التنقل بين أقسام لوحة المالك
            const menuItems = document.querySelectorAll('#owner-page .sidebar-menu .menu-item');
            const contentSections = document.querySelectorAll('#owner-page .main-content .content-section');
            
            menuItems.forEach(item => {
                item.addEventListener('click', function() {
                    const sectionId = this.getAttribute('data-section');
                    
                    menuItems.forEach(i => i.classList.remove('active'));
                    this.classList.add('active');
                    
                    contentSections.forEach(section => {
                        section.classList.remove('active');
                        if (section.id === `${sectionId}-section`) {
                            section.classList.add('active');
                        }
                    });
                    
                    // تحميل البيانات حسب القسم
                    switch(sectionId) {
                        case 'overview':
                            loadOverviewStats();
                            break;
                        case 'users-manage':
                            loadUsersManagement();
                            break;
                        case 'all-files':
                            loadAllFiles();
                            break;
                        case 'system-settings':
                            loadSystemSettings();
                            break;
                    }
                });
            });
            
            // تحميل نظرة عامة
            loadOverviewStats();
            
            // إعداد تسجيل الخروج
            document.getElementById('owner-logout').addEventListener('click', function() {
                sessionStorage.removeItem('currentUser');
                showPage('login-page');
            });
        }

        // تحميل إحصائيات نظرة عامة
        function loadOverviewStats() {
            const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
            const sharedFiles = JSON.parse(localStorage.getItem('sharedFiles')) || [];
            
            // حساب إجمالي الملفات
            let totalFiles = sharedFiles.length;
            users.forEach(user => {
                totalFiles += (user.files || []).length;
            });
            
            // حساب إجمالي التخزين
            let totalStorage = 0;
            users.forEach(user => {
                totalStorage += user.storageUsed || 0;
            });
            
            // تحديث الإحصائيات
            document.getElementById('total-users-count').textContent = users.filter(u => !u.isOwner).length;
            document.getElementById('total-files-count').textContent = totalFiles;
            document.getElementById('total-storage-used').textContent = totalStorage.toFixed(1) + ' ميغابايت';
            
            // عرض المستخدمين الجدد
            const recentUsersDiv = document.getElementById('recent-users');
            const recentUsers = users
                .filter(u => !u.isOwner)
                .sort((a, b) => new Date(b.createdAt) - new Date(a.createdAt))
                .slice(0, 5);
            
            if (recentUsers.length > 0) {
                recentUsersDiv.innerHTML = '';
                recentUsers.forEach(user => {
                    const userEl = document.createElement('div');
                    userEl.className = 'admin-card';
                    userEl.innerHTML = `
                        <div style="display: flex; justify-content: space-between; align-items: center;">
                            <div>
                                <i class="fas fa-user"></i>
                                <strong>${user.name}</strong>
                                <span style="color: #a5b4cb; margin-right: 10px;">(${user.email})</span>
                            </div>
                            <span style="color: #a5b4cb; font-size: 0.9rem;">
                                ${new Date(user.createdAt).toLocaleDateString('ar-SA')}
                            </span>
                        </div>
                    `;
                    recentUsersDiv.appendChild(userEl);
                });
            }
        }

        // تحميل إدارة المستخدمين
        function loadUsersManagement() {
            const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
            const tbody = document.getElementById('users-table-body');
            tbody.innerHTML = '';
            
            users.forEach(user => {
                if (!user.isOwner) {
                    const tr = document.createElement('tr');
                    tr.innerHTML = `
                        <td>${user.name}</td>
                        <td>${user.email}</td>
                        <td>${new Date(user.createdAt).toLocaleDateString('ar-SA')}</td>
                        <td>${(user.files || []).length}</td>
                        <td>
                            <button class="action-btn" onclick="deleteUser(${user.id})" style="padding: 5px 10px;">
                                <i class="fas fa-trash"></i>
                            </button>
                        </td>
                    `;
                    tbody.appendChild(tr);
                }
            });
        }

        // تحميل جميع الملفات
        function loadAllFiles() {
            const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
            const sharedFiles = JSON.parse(localStorage.getItem('sharedFiles')) || [];
            const tbody = document.getElementById('all-files-body');
            tbody.innerHTML = '';
            
            // عرض الملفات المشتركة
            sharedFiles.forEach(file => {
                const tr = document.createElement('tr');
                tr.innerHTML = `
                    <td><i class="fas fa-file"></i> ${file.name}</td>
                    <td>${file.uploadedBy}</td>
                    <td>${file.type}</td>
                    <td>${file.size}</td>
                    <td>${new Date(file.uploadedAt).toLocaleDateString('ar-SA')}</td>
                    <td>
                        <button class="file-action-btn download-btn" onclick="ownerDownloadFile('${file.id}', true)" style="padding: 5px 10px; margin: 2px;">
                            <i class="fas fa-download"></i>
                        </button>
                        <button class="file-action-btn delete-btn" onclick="ownerDeleteFile('${file.id}', true)" style="padding: 5px 10px; margin: 2px;">
                            <i class="fas fa-trash"></i>
                        </button>
                    </td>
                `;
                tbody.appendChild(tr);
            });
            
            // عرض ملفات المستخدمين
            users.forEach(user => {
                if (!user.isOwner && user.files) {
                    user.files.forEach(file => {
                        const tr = document.createElement('tr');
                        tr.innerHTML = `
                            <td><i class="fas fa-file"></i> ${file.name}</td>
                            <td>${user.name}</td>
                            <td>${file.type}</td>
                            <td>${file.size}</td>
                            <td>${new Date(file.uploadedAt).toLocaleDateString('ar-SA')}</td>
                            <td>
                                <button class="file-action-btn download-btn" onclick="ownerDownloadFile('${file.id}', false, ${user.id})" style="padding: 5px 10px; margin: 2px;">
                                    <i class="fas fa-download"></i>
                                </button>
                                <button class="file-action-btn delete-btn" onclick="ownerDeleteFile('${file.id}', false, ${user.id})" style="padding: 5px 10px; margin: 2px;">
                                    <i class="fas fa-trash"></i>
                                </button>
                            </td>
                        `;
                        tbody.appendChild(tr);
                    });
                }
            });
        }

        // تحميل الملف من لوحة المالك
        function ownerDownloadFile(fileId, isShared, userId) {
            if (isShared) {
                const sharedFiles = JSON.parse(localStorage.getItem('sharedFiles')) || [];
                const file = sharedFiles.find(f => f.id === fileId);
                if (file) downloadFile(file);
            } else if (userId) {
                const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
                const user = users.find(u => u.id === userId);
                if (user && user.files) {
                    const file = user.files.find(f => f.id === fileId);
                    if (file) downloadFile(file);
                }
            }
        }

        // حذف الملف من لوحة المالك
        function ownerDeleteFile(fileId, isShared, userId) {
            if (confirm('هل أنت متأكد من حذف هذا الملف؟')) {
                if (isShared) {
                    const sharedFiles = JSON.parse(localStorage.getItem('sharedFiles')) || [];
                    const updatedFiles = sharedFiles.filter(f => f.id !== fileId);
                    localStorage.setItem('sharedFiles', JSON.stringify(updatedFiles));
                } else if (userId) {
                    const users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
                    const userIndex = users.findIndex(u => u.id === userId);
                    if (userIndex !== -1) {
                        const fileIndex = users[userIndex].files.findIndex(f => f.id === fileId);
                        if (fileIndex !== -1) {
                            users[userIndex].files.splice(fileIndex, 1);
                            localStorage.setItem('secureStorageUsers', JSON.stringify(users));
                        }
                    }
                }
                loadAllFiles();
                alert('تم حذف الملف بنجاح');
            }
        }

        // تحميل إعدادات النظام
        function loadSystemSettings() {
            const settings = JSON.parse(localStorage.getItem('systemSettings')) || {
                systemName: "نظام التخزين الآمن",
                maxFileSize: 100,
                userStorageLimit: 100,
                allowRegistration: true
            };
            
            document.getElementById('system-name').value = settings.systemName;
            document.getElementById('max-file-size').value = settings.maxFileSize;
            document.getElementById('user-storage-limit').value = settings.userStorageLimit;
            document.getElementById('allow-registration').checked = settings.allowRegistration;
            
            // حفظ الإعدادات
            document.getElementById('save-system-settings').addEventListener('click', function() {
                const updatedSettings = {
                    systemName: document.getElementById('system-name').value,
                    maxFileSize: parseInt(document.getElementById('max-file-size').value),
                    userStorageLimit: parseInt(document.getElementById('user-storage-limit').value),
                    allowRegistration: document.getElementById('allow-registration').checked
                };
                
                localStorage.setItem('systemSettings', JSON.stringify(updatedSettings));
                
                const messageDiv = document.getElementById('settings-message');
                messageDiv.textContent = 'تم حفظ الإعدادات بنجاح';
                messageDiv.className = 'message success';
                
                setTimeout(() => {
                    messageDiv.textContent = '';
                    messageDiv.className = 'message';
                }, 3000);
            });
        }

        // حذف المستخدم (وظيفة مساعدة)
        function deleteUser(userId) {
            if (confirm('هل أنت متأكد من حذف هذا المستخدم؟')) {
                let users = JSON.parse(localStorage.getItem('secureStorageUsers')) || [];
                users = users.filter(user => user.id !== userId);
                localStorage.setItem('secureStorageUsers', JSON.stringify(users));
                loadUsersManagement();
                loadOverviewStats();
            }
        }
    </script>
</body>
</html>
