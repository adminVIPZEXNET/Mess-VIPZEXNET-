# Mess-VIPZEXNET-
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>VIPZEXNET - پیام‌رسان پیشرفته</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        :root {
            --primary-color: #6a11cb;
            --secondary-color: #2575fc;
            --admin-color: #ff4d4d;
            --text-color: #333;
            --light-gray: #f5f5f5;
            --border-color: #ddd;
            --online-status: #4CAF50;
            --offline-status: #ccc;
        }
        
        body {
            background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
            color: var(--text-color);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            width: 100%;
            max-width: 1200px;
            height: 90vh;
            background-color: white;
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
            display: flex;
        }
        
        /* نوار کناری */
        .sidebar {
            width: 280px;
            background-color: var(--light-gray);
            border-left: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;
        }
        
        .profile {
            padding: 20px;
            text-align: center;
            border-bottom: 1px solid var(--border-color);
        }
        
        .profile-img {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--secondary-color);
            margin-bottom: 10px;
        }
        
        .profile-name {
            font-weight: bold;
            font-size: 18px;
            margin-bottom: 5px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 5px;
        }
        
        .verified-badge {
            color: var(--secondary-color);
        }
        
        .admin-badge {
            color: var(--admin-color);
        }
        
        .profile-status {
            color: #666;
            font-size: 14px;
        }
        
        .sidebar-menu {
            padding: 15px;
            flex-grow: 1;
            overflow-y: auto;
        }
        
        .menu-item {
            padding: 12px 15px;
            border-radius: 10px;
            margin-bottom: 8px;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .menu-item:hover {
            background-color: rgba(106, 17, 203, 0.1);
        }
        
        .menu-item.active {
            background-color: var(--primary-color);
            color: white;
        }
        
        .menu-item i {
            font-size: 18px;
        }
        
        /* محتوای اصلی */
        .main-content {
            flex-grow: 1;
            display: flex;
            flex-direction: column;
        }
        
        .header {
            padding: 15px 20px;
            background-color: white;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .search-box {
            display: flex;
            align-items: center;
            background-color: var(--light-gray);
            border-radius: 20px;
            padding: 8px 15px;
            width: 250px;
        }
        
        .search-box input {
            border: none;
            background: transparent;
            outline: none;
            flex-grow: 1;
            margin-right: 10px;
        }
        
        .header-actions {
            display: flex;
            gap: 15px;
        }
        
        .header-action {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: var(--light-gray);
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .header-action:hover {
            background-color: var(--primary-color);
            color: white;
        }
        
        .content-area {
            flex-grow: 1;
            padding: 20px;
            overflow-y: auto;
            background-color: #f9f9f9;
        }
        
        .section-title {
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid var(--primary-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .btn {
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 10px;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        
        .btn:hover {
            opacity: 0.9;
            transform: translateY(-2px);
        }
        
        .chat-list, .group-list, .channel-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 15px;
        }
        
        .chat-item, .group-item, .channel-item {
            background-color: white;
            border-radius: 15px;
            padding: 15px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.08);
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .chat-item:hover, .group-item:hover, .channel-item:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .chat-header, .group-header, .channel-header {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
        }
        
        .chat-avatar, .group-avatar, .channel-avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            object-fit: cover;
            margin-left: 10px;
        }
        
        .chat-info, .group-info, .channel-info {
            flex-grow: 1;
        }
        
        .chat-name, .group-name, .channel-name {
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .chat-last-msg, .group-last-msg, .channel-last-msg {
            font-size: 13px;
            color: #666;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        
        .chat-time, .group-time, .channel-time {
            font-size: 12px;
            color: #999;
        }
        
        .online {
            width: 10px;
            height: 10px;
            background-color: var(--online-status);
            border-radius: 50%;
            display: inline-block;
            margin-right: 5px;
        }
        
        /* پنل ادمین */
        .admin-panel {
            display: none;
            background-color: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .admin-panel.active {
            display: block;
        }
        
        .admin-controls {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 20px;
        }
        
        .admin-control {
            background-color: var(--light-gray);
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .admin-control:hover {
            background-color: var(--primary-color);
            color: white;
        }
        
        .admin-control i {
            font-size: 24px;
            margin-bottom: 10px;
        }
        
        .user-list {
            margin-top: 20px;
        }
        
        .user-item {
            display: flex;
            align-items: center;
            padding: 15px;
            border-bottom: 1px solid var(--border-color);
        }
        
        .user-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            object-fit: cover;
            margin-left: 15px;
        }
        
        .user-info {
            flex-grow: 1;
        }
        
        .user-name {
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .user-actions {
            display: flex;
            gap: 10px;
        }
        
        .user-action {
            padding: 5px 10px;
            border-radius: 5px;
            font-size: 12px;
            cursor: pointer;
        }
        
        .ban-user {
            background-color: #ff4d4d;
            color: white;
        }
        
        .unban-user {
            background-color: #4CAF50;
            color: white;
        }
        
        /* چت */
        .chat-container {
            display: none;
            flex-direction: column;
            height: 100%;
        }
        
        .chat-container.active {
            display: flex;
        }
        
        .chat-header {
            padding: 15px;
            background-color: white;
            border-bottom: 1px solid var(--border-color);
        }
        
        .chat-messages {
            flex-grow: 1;
            padding: 15px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .message {
            max-width: 70%;
            padding: 10px 15px;
            border-radius: 15px;
            position: relative;
        }
        
        .message-incoming {
            background-color: var(--light-gray);
            align-self: flex-start;
            border-bottom-right-radius: 0;
        }
        
        .message-outgoing {
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            color: white;
            align-self: flex-end;
            border-bottom-left-radius: 0;
        }
        
        .message-time {
            font-size: 11px;
            margin-top: 5px;
            text-align: right;
            opacity: 0.8;
        }
        
        .chat-input {
            padding: 15px;
            background-color: white;
            border-top: 1px solid var(--border-color);
            display: flex;
            gap: 10px;
        }
        
        .chat-input input {
            flex-grow: 1;
            padding: 12px 15px;
            border: 1px solid var(--border-color);
            border-radius: 20px;
            outline: none;
        }
        
        .attachment-btn {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: var(--light-gray);
            cursor: pointer;
        }
        
        .attachment-options {
            display: flex;
            gap: 10px;
            margin-top: 10px;
        }
        
        .attachment-option {
            padding: 8px 15px;
            background-color: var(--light-gray);
            border-radius: 15px;
            font-size: 13px;
            display: flex;
            align-items: center;
            gap: 5px;
            cursor: pointer;
        }
        
        /* رسپانسیو */
        @media (max-width: 768px) {
            .container {
                flex-direction: column;
                height: auto;
            }
            
            .sidebar {
                width: 100%;
                order: 2;
            }
            
            .main-content {
                order: 1;
            }
            
            .chat-list, .group-list, .channel-list {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- نوار کناری -->
        <div class="sidebar">
            <div class="profile">
                <img src="https://randomuser.me/api/portraits/men/32.jpg" alt="Profile" class="profile-img">
                <div class="profile-name">
                    مدیر سیستم
                    <i class="fas fa-check-circle verified-badge"></i>
                    <i class="fas fa-crown admin-badge"></i>
                </div>
                <div class="profile-status">آنلاین</div>
            </div>
            
            <div class="sidebar-menu">
                <div class="menu-item active" data-target="chats">
                    <i class="fas fa-comment"></i>
                    <span>چت‌ها</span>
                </div>
                <div class="menu-item" data-target="groups">
                    <i class="fas fa-users"></i>
                    <span>گروه‌ها</span>
                </div>
                <div class="menu-item" data-target="channels">
                    <i class="fas fa-broadcast-tower"></i>
                    <span>کانال‌ها</span>
                </div>
                <div class="menu-item" data-target="bots">
                    <i class="fas fa-robot"></i>
                    <span>ربات‌ها</span>
                </div>
                <div class="menu-item" data-target="admin">
                    <i class="fas fa-cog"></i>
                    <span>پنل مدیریت</span>
                </div>
                <div class="menu-item" data-target="contacts">
                    <i class="fas fa-address-book"></i>
                    <span>مخاطبین</span>
                </div>
                <div class="menu-item" data-target="settings">
                    <i class="fas fa-cog"></i>
                    <span>تنظیمات</span>
                </div>
            </div>
        </div>
        
        <!-- محتوای اصلی -->
        <div class="main-content">
            <div class="header">
                <div class="search-box">
                    <input type="text" placeholder="جستجو...">
                    <i class="fas fa-search"></i>
                </div>
                
                <div class="header-actions">
                    <div class="header-action">
                        <i class="fas fa-bell"></i>
                    </div>
                    <div class="header-action">
                        <i class="fas fa-plus"></i>
                    </div>
                </div>
            </div>
            
            <div class="content-area">
                <!-- بخش چت‌ها -->
                <div class="content-section" id="chats">
                    <div class="section-title">
                        <h2>چت‌های اخیر</h2>
                        <button class="btn">
                            <i class="fas fa-plus"></i>
                            چت جدید
                        </button>
                    </div>
                    
                    <div class="chat-list">
                        <div class="chat-item" data-chat="1">
                            <div class="chat-header">
                                <img src="https://randomuser.me/api/portraits/women/44.jpg" alt="Avatar" class="chat-avatar">
                                <div class="chat-info">
                                    <div class="chat-name">
                                        <span class="online"></span>
                                        سارا محمدی
                                        <i class="fas fa-check-circle verified-badge"></i>
                                    </div>
                                    <div class="chat-last-msg">سلام چطوری؟</div>
                                </div>
                                <div class="chat-time">10:45</div>
                            </div>
                        </div>
                        
                        <div class="chat-item" data-chat="2">
                            <div class="chat-header">
                                <img src="https://randomuser.me/api/portraits/men/22.jpg" alt="Avatar" class="chat-avatar">
                                <div class="chat-info">
                                    <div class="chat-name">
                                        <span class="online"></span>
                                        علی رضایی
                                    </div>
                                    <div class="chat-last-msg">فایل رو برات فرستادم</div>
                                </div>
                                <div class="chat-time">دیروز</div>
                            </div>
                        </div>
                        
                        <div class="chat-item" data-chat="3">
                            <div class="chat-header">
                                <img src="https://randomuser.me/api/portraits/women/68.jpg" alt="Avatar" class="chat-avatar">
                                <div class="chat-info">
                                    <div class="chat-name">
                                        <span class="online" style="background-color: var(--offline-status);"></span>
                                        نازنین کریمی
                                        <i class="fas fa-check-circle verified-badge"></i>
                                    </div>
                                    <div class="chat-last-msg">个体户通过通过通过</div>
                                </div>
                                <div class="chat-time">سه شنبه</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- بخش گروه‌ها -->
                <div class="content-section" id="groups" style="display: none;">
                    <div class="section-title">
                        <h2>گروه‌ها</h2>
                        <button class="btn">
                            <i class="fas fa-plus"></i>
                            گروه جدید
                        </button>
                    </div>
                    
                    <div class="group-list">
                        <div class="group-item">
                            <div class="group-header">
                                <img src="https://randomuser.me/api/portraits/lego/2.jpg" alt="Avatar" class="group-avatar">
                                <div class="group-info">
                                    <div class="group-name">گروه دوستان</div>
                                    <div class="group-last-msg">حسین: فردا جلسه داریم</div>
                                </div>
                                <div class="group-time">10:45</div>
                            </div>
                        </div>
                        
                        <div class="group-item">
                            <div class="group-header">
                                <img src="https://randomuser.me/api/portraits/lego/5.jpg" alt="Avatar" class="group-avatar">
                                <div class="group-info">
                                    <div class="group-name">گروه فامیلی</div>
                                    <div class="group-last-msg">مادر: عید امسال کجا بریم؟</div>
                                </div>
                                <div class="group-time">دیروز</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- بخش کانال‌ها -->
                <div class="content-section" id="channels" style="display: none;">
                    <div class="section-title">
                        <h2>کانال‌ها</h2>
                        <button class="btn">
                            <i class="fas fa-plus"></i>
                            کانال جدید
                        </button>
                    </div>
                    
                    <div class="channel-list">
                        <div class="channel-item">
                            <div class="channel-header">
                                <img src="https://randomuser.me/api/portraits/lego/7.jpg" alt="Avatar" class="channel-avatar">
                                <div class="channel-info">
                                    <div class="channel-name">اخبار فناوری</div>
                                    <div class="channel-last-msg">جدیدترین گوشی سامسونگ رونمایی شد</div>
                                </div>
                                <div class="channel-time">10:45</div>
                            </div>
                        </div>
                        
                        <div class="channel-item">
                            <div class="channel-header">
                                <img src="https://randomuser.me/api/portraits/lego/3.jpg" alt="Avatar" class="channel-avatar">
                                <div class="channel-info">
                                    <div class="channel-name">آموزش برنامه‌نویسی</div>
                                    <div class="channel-last-msg">آموزش React.js - جلسه پنجم</div>
                                </div>
                                <div class="channel-time">دیروز</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- پنل ادمین -->
                <div class="content-section" id="admin" style="display: none;">
                    <div class="section-title">
                        <h2>پنل مدیریت سیستم</h2>
                    </div>
                    
                    <div class="admin-panel active">
                        <div class="admin-controls">
                            <div class="admin-control">
                                <i class="fas fa-users"></i>
                                <span>مدیریت کاربران</span>
                            </div>
                            <div class="admin-control">
                                <i class="fas fa-bullhorn"></i>
                                <span>ارسال تبلیغات</span>
                            </div>
                            <div class="admin-control">
                                <i class="fas fa-shield-alt"></i>
                                <span>مدیریت امنیت</span>
                            </div>
                            <div class="admin-control">
                                <i class="fas fa-chart-bar"></i>
                                <span>آمار و گزارشات</span>
                            </div>
                        </div>
                        
                        <h3>مدیریت کاربران</h3>
                        <div class="user-list">
                            <div class="user-item">
                                <img src="https://randomuser.me/api/portraits/men/32.jpg" alt="Avatar" class="user-avatar">
                                <div class="user-info">
                                    <div class="user-name">
                                        علی احمدی
                                        <i class="fas fa-check-circle verified-badge"></i>
                                    </div>
                                    <div>آخرین فعالیت: ۲ ساعت پیش</div>
                                </div>
                                <div class="user-actions">
                                    <div class="user-action ban-user">تعلیق کاربر</div>
                                    <div class="user-action">ارتباط</div>
                                </div>
                            </div>
                            
                            <div class="user-item">
                                <img src="https://randomuser.me/api/portraits/women/44.jpg" alt="Avatar" class="user-avatar">
                                <div class="user-info">
                                    <div class="user-name">
                                        سارا محمدی
                                        <i class="fas fa-check-circle verified-badge"></i>
                                    </div>
                                    <div>آخرین فعالیت: همین حالا</div>
                                </div>
                                <div class="user-actions">
                                    <div class="user-action ban-user">تعلیق کاربر</div>
                                    <div class="user-action">ارتباط</div>
                                </div>
                            </div>
                            
                            <div class="user-item">
                                <img src="https://randomuser.me/api/portraits/men/22.jpg" alt="Avatar" class="user-avatar">
                                <div class="user-info">
                                    <div class="user-name">علی رضایی</div>
                                    <div>آخرین فعالیت: ۱ روز پیش</div>
                                </div>
                                <div class="user-actions">
                                    <div class="user-action unban-user">رفع تعلیق</div>
                                    <div class="user-action">ارتباط</div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- چت فعال -->
                <div class="chat-container" id="chat-window">
                    <div class="chat-header">
                        <img src="https://randomuser.me/api/portraits/women/44.jpg" alt="Avatar" class="chat-avatar">
                        <div class="chat-info">
                            <div class="chat-name">
                                <span class="online"></span>
                                سارا محمدی
                                <i class="fas fa-check-circle verified-badge"></i>
                            </div>
                            <div class="chat-last-msg">آنلاین</div>
                        </div>
                        <div class="header-actions">
                            <div class="header-action">
                                <i class="fas fa-phone"></i>
                            </div>
                            <div class="header-action">
                                <i class="fas fa-video"></i>
                            </div>
                            <div class="header-action">
                                <i class="fas fa-ellipsis-v"></i>
                            </div>
                        </div>
                    </div>
                    
                    <div class="chat-messages">
                        <div class="message message-incoming">
                            <div class="message-text">سلام چطوری؟</div>
                            <div class="message-time">۱۰:۴۲</div>
                        </div>
                        
                        <div class="message message-outgoing">
                            <div class="message-text">سلام خوبم ممنون. تو چطوری؟</div>
                            <div class="message-time">۱۰:۴۳</div>
                        </div>
                        
                        <div class="message message-incoming">
                            <div class="message-text">من هم خوبم. یه فایل برات فرستادم ببین</div>
                            <div class="message-time">۱۰:۴۵</div>
                        </div>
                        
                        <div class="message message-incoming">
                            <div class="message-text">
                                <i class="fas fa-file-pdf"></i> سند.pdf
                                <div class="message-time">۱۰:۴۵</div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="chat-input">
                        <div class="attachment-btn">
                            <i class="fas fa-paperclip"></i>
                        </div>
                        <input type="text" placeholder="پیام خود را بنویسید...">
                        <button class="btn" style="padding: 10px 20px;">
                            <i class="fas fa-paper-plane"></i>
                        </button>
                    </div>
                    
                    <div class="attachment-options">
                        <div class="attachment-option">
                            <i class="fas fa-image"></i> عکس
                        </div>
                        <div class="attachment-option">
                            <i class="fas fa-video"></i> ویدیو
                        </div>
                        <div class="attachment-option">
                            <i class="fas fa-file"></i> فایل
                        </div>
                        <div class="attachment-option">
                            <i class="fas fa-map-marker-alt"></i> موقعیت
                        </div>
                        <div class="attachment-option">
                            <i class="fas fa-music"></i> موسیقی
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // تغییر بین بخش‌های مختلف
        document.querySelectorAll('.menu-item').forEach(item => {
            item.addEventListener('click', function() {
                // غیرفعال کردن همه منوها
                document.querySelectorAll('.menu-item').forEach(i => {
                    i.classList.remove('active');
                });
                
                // فعال کردن منوی انتخاب شده
                this.classList.add('active');
                
                // مخفی کردن همه بخش‌ها
                document.querySelectorAll('.content-section').forEach(section => {
                    section.style.display = 'none';
                });
                
                // نمایش بخش انتخاب شده
                const target = this.getAttribute('data-target');
                document.getElementById(target).style.display = 'block';
                
                // اگر چت باز است، آن را ببند
                document.getElementById('chat-window').classList.remove('active');
            });
        });
        
        // باز کردن چت
        document.querySelectorAll('.chat-item').forEach(item => {
            item.addEventListener('click', function() {
                // مخفی کردن همه بخش‌ها
                document.querySelectorAll('.content-section').forEach(section => {
                    section.style.display = 'none';
                });
                
                // نمایش پنجره چت
                document.getElementById('chat-window').classList.add('active');
            });
        });
        
        // مدیریت دکمه‌های تعلیق کاربر
        document.querySelectorAll('.ban-user').forEach(btn => {
            btn.addEventListener('click', function(e) {
                e.stopPropagation();
                const userName = this.closest('.user-item').querySelector('.user-name').textContent;
                alert(`کاربر ${userName} تعلیق شد.`);
                this.textContent = "رفع تعلیق";
                this.classList.remove('ban-user');
                this.classList.add('unban-user');
            });
        });
        
        document.querySelectorAll('.unban-user').forEach(btn => {
            btn.addEventListener('click', function(e) {
                e.stopPropagation();
                const userName = this.closest('.user-item').querySelector('.user-name').textContent;
                alert(`تعلیق کاربر ${userName} لغو شد.`);
                this.textContent = "تعلیق کاربر";
                this.classList.remove('unban-user');
                this.classList.add('ban-user');
            });
        });
    </script>
</body>
</html>
