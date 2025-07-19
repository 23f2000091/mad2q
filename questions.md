---


---

<ol>
<li>
<p><strong>How does the application manage frontend routing?</strong></p>
<ul>
<li><strong>Answer:</strong> Frontend routing is handled by <strong>Vue Router</strong>, with defined routes including <code>/</code>, <code>/login</code>, <code>/register</code>, <code>/user</code>, and <code>/admin</code>.</li>
<li><strong>File:</strong> <code>script.js</code>, lines 28–38.</li>
</ul>
</li>
<li>
<p><strong>How does the application manage backend routing?</strong></p>
<ul>
<li><strong>Answer:</strong> Backend routing uses <strong>Flask</strong>. Routes are defined in <code>routes.py</code>, and APIs are registered in <code>resources.py</code>.</li>
<li><strong>File:</strong> <code>routes.py</code>, lines 19–144.</li>
<li><strong>File:</strong> <code>resources.py</code>, lines 18–545.</li>
</ul>
</li>
<li>
<p><strong>How does the application ensure role-based access control (RBAC)?</strong></p>
<ul>
<li><strong>Answer:</strong> <strong>Flask-Security</strong> implements RBAC, using decorators such as <code>@roles_required</code> and <code>@roles_accepted</code> to restrict access based on user roles.</li>
<li><strong>File:</strong> <code>resources.py</code>, lines 35, 158, 289.</li>
<li><strong>File:</strong> <code>routes.py</code>, lines 19–38.</li>
</ul>
</li>
<li>
<p><strong>How does the application implement authentication?</strong></p>
<ul>
<li><strong>Answer:</strong> Authentication is managed by <strong>Flask-Security</strong>. Users log in via the <code>/api/login</code> endpoint, and <strong>tokens</strong> are used for subsequent API access.</li>
<li><strong>File:</strong> <code>routes.py</code>, lines 57–99.</li>
<li><strong>Frontend:</strong> <code>Login.js</code>, line 60.</li>
</ul>
</li>
<li>
<p><strong>How does the application implement caching?</strong></p>
<ul>
<li><strong>Answer:</strong> Caching is implemented using <strong>Flask-Caching with Redis</strong>. API responses are cached using <code>@cache.cached(timeout=10)</code>.</li>
<li><strong>File:</strong> <code>cache.py</code>, <code>app.py</code>, lines 24–25.</li>
<li><strong>File:</strong> <code>resources.py</code>, lines 35, 86.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle database interactions?</strong></p>
<ul>
<li><strong>Answer:</strong> The application uses <strong>SQLAlchemy</strong> for database interactions. Models like <code>User</code>, <code>Role</code>, <code>ParkingLot</code>, and <code>ParkingSpot</code> are defined in <code>models.py</code>.</li>
<li><strong>File:</strong> <code>models.py</code>.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle background tasks?</strong></p>
<ul>
<li><strong>Answer:</strong> <strong>Celery</strong> manages background tasks. Examples include <code>monthly_report</code> and <code>daily_reminder_task</code>, defined in <code>tasks.py</code>.</li>
<li><strong>File:</strong> <code>tasks.py</code>, lines 23–151.</li>
<li><strong>File:</strong> <code>app.py</code>, lines 50–60.</li>
</ul>
</li>
<li>
<p><strong>How does the application schedule periodic tasks?</strong></p>
<ul>
<li><strong>Answer:</strong> Periodic tasks are scheduled using <strong>Celery’s crontab</strong>. For demonstration purposes, reports are generated every minute.</li>
<li><strong>File:</strong> <code>app.py</code>, lines 63–74.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle user registration?</strong></p>
<ul>
<li><strong>Answer:</strong> Users can register via the <code>/api/register</code> endpoint. The backend validates the email and creates a new user.</li>
<li><strong>File:</strong> <code>routes.py</code>, line 99.</li>
<li><strong>Frontend:</strong> <code>Register.js</code>.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle user login?</strong></p>
<ul>
<li><strong>Answer:</strong> Users log in via the <code>/api/login</code> endpoint. A <strong>successful login returns an authentication token</strong>.</li>
<li><strong>File:</strong> <code>routes.py</code>, lines 57–99.</li>
<li><strong>Frontend:</strong> <code>Login.js</code>, line 60.</li>
</ul>
</li>
<li>
<p><strong>How does the application manage parking lots?</strong></p>
<ul>
<li><strong>Answer:</strong> Parking lots are managed via <strong>APIs</strong>: <code>POST /api/parking_lots</code> (create), <code>PUT /api/parking_lots/&lt;lot_id&gt;</code> (update), and <code>DELETE /api/parking_lots/&lt;lot_id&gt;</code> (delete).</li>
<li><strong>File:</strong> <code>resources.py</code>, lines 35–186.</li>
<li><strong>Frontend:</strong> <code>Admin.js</code>, lines 321–386.</li>
</ul>
</li>
<li>
<p><strong>How does the application manage parking spots?</strong></p>
<ul>
<li><strong>Answer:</strong> Parking spots are associated with lots and managed through APIs like <code>GET /api/parking_lots/&lt;lot_id&gt;/spots</code>.</li>
<li><strong>File:</strong> <code>resources.py</code>, lines 209–231.</li>
<li><strong>Frontend:</strong> <code>Admin.js</code>, line 413.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle user reservations?</strong></p>
<ul>
<li><strong>Answer:</strong> Users can reserve, occupy, and release spots using APIs such as <code>POST /api/user/reserve</code> and <code>PUT /api/user/reservation/&lt;reservation_id&gt;</code>.</li>
<li><strong>File:</strong> <code>resources.py</code>, lines 319–377.</li>
<li><strong>Frontend:</strong> <code>User.js</code>, lines 215–241.</li>
</ul>
</li>
<li>
<p><strong>How does the application calculate parking costs?</strong></p>
<ul>
<li><strong>Answer:</strong> Parking costs are calculated based on the <strong>duration</strong> (from <code>parking_timestamp</code> to <code>leaving_timestamp</code>) multiplied by the <strong>hourly rate</strong>.</li>
<li><strong>File:</strong> <code>resources.py</code>, line 392.</li>
<li><strong>Frontend:</strong> <code>Admin.js</code>, line 548.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle analytics for administrators?</strong></p>
<ul>
<li><strong>Answer:</strong> Administrators can view parking statistics and revenue summaries via APIs like <code>/api/admin/analytics/parking_stats</code>.</li>
<li><strong>File:</strong> <code>resources.py</code>, lines 445–478.</li>
<li><strong>Frontend:</strong> <code>Admin.js</code>, lines 467–518.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle analytics for users?</strong></p>
<ul>
<li><strong>Answer:</strong> Users can access their parking history and cost per lot via APIs such as <code>/api/user/analytics/parking_history</code>.</li>
<li><strong>File:</strong> <code>resources.py</code>, lines 502–522.</li>
<li><strong>Frontend:</strong> <code>User.js</code>, lines 407–453.</li>
</ul>
</li>
<li>
<p><strong>How does the application send monthly reports?</strong></p>
<ul>
<li><strong>Answer:</strong> Monthly reports are generated and emailed using the <strong><code>monthly_report</code> Celery task</strong>.</li>
<li><strong>File:</strong> <code>tasks.py</code>, lines 97–112.</li>
<li><strong>File:</strong> <code>routes.py</code>, line 144.</li>
</ul>
</li>
<li>
<p><strong>How does the application send daily reminders?</strong></p>
<ul>
<li><strong>Answer:</strong> Daily reminders are sent using the <strong><code>daily_reminder_task</code> Celery task</strong>.</li>
<li><strong>File:</strong> <code>tasks.py</code>, lines 128–151.</li>
<li><strong>File:</strong> <code>routes.py</code>, line 144.</li>
</ul>
</li>
<li>
<p><strong>How does the application export data as CSV?</strong></p>
<ul>
<li><strong>Answer:</strong> Administrators can initiate a CSV export via the <code>/api/export/csv</code> endpoint. This task is processed <strong>asynchronously by Celery</strong>.</li>
<li><strong>File:</strong> <code>routes.py</code>, line 99.</li>
<li><strong>Frontend:</strong> <code>Admin.js</code>, line 252.</li>
</ul>
</li>
<li>
<p><strong>How does the application manage user data?</strong></p>
<ul>
<li><strong>Answer:</strong> User data is managed through the <code>/api/users</code> endpoint, allowing administrators to view all registered users.</li>
<li><strong>File:</strong> <code>resources.py</code>, line 231.</li>
<li><strong>Frontend:</strong> <code>Admin.js</code>, line 272.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle parking lot analytics?</strong></p>
<ul>
<li><strong>Answer:</strong> Analytics, including available and occupied spots, are retrieved via APIs like <code>/api/user/parking_lots</code>.</li>
<li><strong>File:</strong> <code>resources.py</code>, line 289.</li>
<li><strong>Frontend:</strong> <code>User.js</code>, line 190.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle revenue analytics?</strong></p>
<ul>
<li><strong>Answer:</strong> Revenue analytics are fetched via the <code>/api/admin/analytics/revenue_summary</code> API and displayed visually as charts.</li>
<li><strong>File:</strong> <code>resources.py</code>, line 478.</li>
<li><strong>Frontend:</strong> <code>Admin.js</code>, line 492.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle parking history analytics?</strong></p>
<ul>
<li><strong>Answer:</strong> Parking history analytics are fetched via the <code>/api/user/analytics/parking_history</code> API and displayed as charts.</li>
<li><strong>File:</strong> <code>resources.py</code>, line 502.</li>
<li><strong>Frontend:</strong> <code>User.js</code>, line 407.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle cost per lot analytics?</strong></p>
<ul>
<li><strong>Answer:</strong> Cost per lot analytics are retrieved via the <code>/api/user/analytics/cost_per_lot</code> API and presented as charts.</li>
<li><strong>File:</strong> <code>resources.py</code>, line 522.</li>
<li><strong>Frontend:</strong> <code>User.js</code>, line 453.</li>
</ul>
</li>
<li>
<p><strong>How does the application ensure data integrity?</strong></p>
<ul>
<li><strong>Answer:</strong> Data integrity is maintained through <strong>database constraints and validation within API endpoints</strong>. For instance, a parking lot with occupied spots cannot be deleted.</li>
<li><strong>File:</strong> <code>resources.py</code>, lines 158–186.</li>
</ul>
</li>
<li>
<p><strong>How does the application initialize the Flask app?</strong></p>
<ul>
<li><strong>Answer:</strong> The <strong><code>create_app</code> function</strong> initializes the Flask application, configures the database, sets up Flask-Security for authentication, and integrates Redis caching.</li>
<li><strong>File:</strong> <code>app.py</code>, lines 13–28.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle database migrations?</strong></p>
<ul>
<li><strong>Answer:</strong> The database is initialized using <strong>SQLAlchemy</strong>, and tables are created with <code>db.create_all()</code> during the application’s initialization.</li>
<li><strong>File:</strong> <code>app.py</code>, lines 43–44.</li>
</ul>
</li>
<li>
<p><strong>How does the application ensure default roles and users are created?</strong></p>
<ul>
<li><strong>Answer:</strong> Default roles (<code>admin</code>, <code>user</code>) and users are created during application initialization using <strong>Flask-Security’s <code>datastore</code></strong>.</li>
<li><strong>File:</strong> <code>app.py</code>, lines 46–57.</li>
</ul>
</li>
<li>
<p><strong>How does the application integrate Celery for background tasks?</strong></p>
<ul>
<li><strong>Answer:</strong> <strong>Celery</strong> is initialized using <code>celery_init_app</code>, and tasks are automatically discovered.</li>
<li><strong>File:</strong> <code>app.py</code>, lines 30–32.</li>
</ul>
</li>
<li>
<p><strong>How does the application schedule periodic tasks?</strong></p>
<ul>
<li><strong>Answer:</strong> Periodic tasks, such as <code>monthly_report</code> and <code>daily_reminder_task</code>, are scheduled using <strong>Celery’s <code>crontab</code></strong>.</li>
<li><strong>File:</strong> <code>app.py</code>, lines 63–74.</li>
</ul>
</li>
<li>
<p><strong>How does the application send emails?</strong></p>
<ul>
<li><strong>Answer:</strong> Emails are sent using the <strong><code>send_email</code> function in <code>mail.py</code></strong>. Formatting is applied using templates like <code>mail_details.html</code>.</li>
<li><strong>File:</strong> <code>application/mail.py</code>.</li>
<li><strong>Template:</strong> <code>templates/mail_details.html</code>.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle user roles?</strong></p>
<ul>
<li><strong>Answer:</strong> User roles are managed via <strong>Flask-Security</strong>. Roles are stored in the <code>Role</code> model and assigned when a user is created.</li>
<li><strong>File:</strong> <code>application/models.py</code>.</li>
<li><strong>File:</strong> <code>app.py</code>, lines 46–57.</li>
</ul>
</li>
<li>
<p><strong>How does the application manage frontend routing?</strong></p>
<ul>
<li><strong>Answer:</strong> Frontend routing is managed by <strong>Vue Router</strong>, with routes including <code>/</code>, <code>/login</code>, <code>/register</code>, <code>/user</code>, and <code>/admin</code>.</li>
<li><strong>File:</strong> <code>static/script.js</code>, lines 28–38.</li>
</ul>
</li>
<li>
<p><strong>How does the application manage backend routing?</strong></p>
<ul>
<li><strong>Answer:</strong> Backend routing is implemented using <strong>Flask</strong>. Routes are defined in <code>routes.py</code>, and APIs are registered in <code>resources.py</code>.</li>
<li><strong>File:</strong> <code>application/routes.py</code>, lines 19–144.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, lines 18–545.</li>
</ul>
</li>
<li>
<p><strong>How does the application ensure role-based access control (RBAC)?</strong></p>
<ul>
<li><strong>Answer:</strong> <strong>Flask-Security</strong> implements RBAC. Decorators like <code>@roles_required</code> and <code>@roles_accepted</code> restrict access to specific roles.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, lines 35, 158, 289.</li>
<li><strong>File:</strong> <code>application/routes.py</code>, lines 19–38.</li>
</ul>
</li>
<li>
<p><strong>How does the application implement authentication?</strong></p>
<ul>
<li><strong>Answer:</strong> Authentication is handled using <strong>Flask-Security</strong>. Users log in via the <code>/api/login</code> endpoint, and tokens are used for API access.</li>
<li><strong>File:</strong> <code>application/routes.py</code>, lines 57–99.</li>
<li><strong>Frontend:</strong> <code>static/components/Login.js</code>, line 60.</li>
</ul>
</li>
<li>
<p><strong>How does the application implement caching?</strong></p>
<ul>
<li><strong>Answer:</strong> Caching is implemented using <strong>Flask-Caching with Redis</strong>. APIs use <code>@cache.cached(timeout=10)</code> for caching responses.</li>
<li><strong>File:</strong> <code>application/cache.py</code>, <code>app.py</code>, lines 24–25.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, lines 35, 86.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle database interactions?</strong></p>
<ul>
<li><strong>Answer:</strong> The application uses <strong>SQLAlchemy</strong> for database interactions. Models such as <code>User</code>, <code>Role</code>, <code>ParkingLot</code>, and <code>ParkingSpot</code> are defined in <code>models.py</code>.</li>
<li><strong>File:</strong> <code>application/models.py</code>.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle background tasks?</strong></p>
<ul>
<li><strong>Answer:</strong> Background tasks are managed using <strong>Celery</strong>. Tasks like <code>monthly_report</code> and <code>daily_reminder_task</code> are defined in <code>tasks.py</code>.</li>
<li><strong>File:</strong> <code>application/tasks.py</code>, lines 23–151.</li>
<li><strong>File:</strong> <code>app.py</code>, lines 50–60.</li>
</ul>
</li>
<li>
<p><strong>How does the application send monthly reports?</strong></p>
<ul>
<li><strong>Answer:</strong> Monthly reports are generated using the <strong><code>monthly_report</code> Celery task</strong> and sent via email.</li>
<li><strong>File:</strong> <code>application/tasks.py</code>, lines 97–112.</li>
<li><strong>Template:</strong> <code>templates/mail_details.html</code>.</li>
</ul>
</li>
<li>
<p><strong>How does the application send daily reminders?</strong></p>
<ul>
<li><strong>Answer:</strong> Daily reminders are sent using the <strong><code>daily_reminder_task</code> Celery task</strong>, which notifies users with active reservations.</li>
<li><strong>File:</strong> <code>application/tasks.py</code>, lines 151–161.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle user registration?</strong></p>
<ul>
<li><strong>Answer:</strong> Users register via the <code>/api/register</code> endpoint, which validates the email and creates a new user.</li>
<li><strong>File:</strong> <code>application/routes.py</code>, line 99.</li>
<li><strong>Frontend:</strong> <code>static/components/Register.js</code>.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle user login?</strong></p>
<ul>
<li><strong>Answer:</strong> Users log in via the <code>/api/login</code> endpoint. An <strong>authentication token</strong> is returned upon successful login.</li>
<li><strong>File:</strong> <code>application/routes.py</code>, lines 57–99.</li>
<li><strong>Frontend:</strong> <code>static/components/Login.js</code>, line 60.</li>
</ul>
</li>
<li>
<p><strong>How does the application manage parking lots?</strong></p>
<ul>
<li><strong>Answer:</strong> Parking lots are managed via APIs such as <code>POST /api/parking_lots</code> (create), <code>PUT /api/parking_lots/&lt;lot_id&gt;</code> (update), and <code>DELETE /api/parking_lots/&lt;lot_id&gt;</code> (delete).</li>
<li><strong>File:</strong> <code>application/resources.py</code>, lines 35–186.</li>
<li><strong>Frontend:</strong> <code>static/components/Admin.js</code>, lines 321–386.</li>
</ul>
</li>
<li>
<p><strong>How does the application manage parking spots?</strong></p>
<ul>
<li><strong>Answer:</strong> Parking spots are linked to lots and managed via APIs like <code>GET /api/parking_lots/&lt;lot_id&gt;/spots</code>.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, lines 209–231.</li>
<li><strong>Frontend:</strong> <code>static/components/Admin.js</code>, line 413.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle user reservations?</strong></p>
<ul>
<li><strong>Answer:</strong> Users can reserve, occupy, and release spots via APIs like <code>POST /api/user/reserve</code> and <code>PUT /api/user/reservation/&lt;reservation_id&gt;</code>.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, lines 319–377.</li>
<li><strong>Frontend:</strong> <code>static/components/User.js</code>, lines 215–241.</li>
</ul>
</li>
<li>
<p><strong>How does the application calculate parking costs?</strong></p>
<ul>
<li><strong>Answer:</strong> Parking costs are calculated by multiplying the duration by the hourly rate, as defined in the <code>getRate</code> method.</li>
<li><strong>File:</strong> <code>static/components/User.js</code>, line 389.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle analytics for administrators?</strong></p>
<ul>
<li><strong>Answer:</strong> Administrators can view parking statistics and revenue summaries via APIs such as <code>/api/admin/analytics/parking_stats</code>.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, lines 445–478.</li>
<li><strong>Frontend:</strong> <code>static/components/Admin.js</code>, lines 467–518.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle analytics for users?</strong></p>
<ul>
<li><strong>Answer:</strong> Users can view their parking history and cost per lot via APIs like <code>/api/user/analytics/parking_history</code>.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, lines 502–522.</li>
<li><strong>Frontend:</strong> <code>static/components/User.js</code>, lines 407–453.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle parking lot analytics?</strong></p>
<ul>
<li><strong>Answer:</strong> Analytics, including total lots, available spots, and reservations, are retrieved via the <code>AnalyticsApi</code> class.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, lines 445–478.</li>
<li><strong>Frontend:</strong> <code>static/components/Admin.js</code>, lines 467–518.</li>
</ul>
</li>
<li>
<p><strong>Where is the administrator part of the frontend implemented?</strong></p>
<ul>
<li><strong>Answer:</strong> The administrator interface is implemented in <strong><code>Admin.js</code></strong>, handling parking lot management, user management, and analytics.</li>
<li><strong>File:</strong> <code>static/components/Admin.js</code>.</li>
</ul>
</li>
<li>
<p><strong>Where is the user part of the frontend implemented?</strong></p>
<ul>
<li><strong>Answer:</strong> The user interface is implemented in <strong><code>User.js</code></strong>, managing parking reservations, parking history, and user analytics.</li>
<li><strong>File:</strong> <code>static/components/User.js</code>.</li>
</ul>
</li>
<li>
<p><strong>How is the Vue.js CDN mounted in the application?</strong></p>
<ul>
<li><strong>Answer:</strong> Vue.js is mounted via a <code>&lt;script&gt;</code> tag in the HTML template, and the Vue instance is initialized in <code>script.js</code>.</li>
<li><strong>File:</strong> <code>templates/index.html</code>.</li>
<li><strong>File:</strong> <code>static/script.js</code>, lines 10–28.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle exporting parking data as CSV?</strong></p>
<ul>
<li><strong>Answer:</strong> Administrators can trigger a CSV export via the <code>/api/export/csv</code> endpoint. This task is processed <strong>asynchronously by Celery</strong>.</li>
<li><strong>File:</strong> <code>application/tasks.py</code>, lines 46–61.</li>
<li><strong>Frontend:</strong> <code>static/components/Admin.js</code>, line 221.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle user-triggered CSV exports?</strong></p>
<ul>
<li><strong>Answer:</strong> Users can export their parking history as CSV using the <strong><code>exportCsv</code> method</strong>, which polls the backend for task status.</li>
<li><strong>File:</strong> <code>static/components/User.js</code>, lines 315–372.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle parking spot statuses?</strong></p>
<ul>
<li><strong>Answer:</strong> Parking spots have statuses like <code>available</code>, <code>occupied</code>, and <code>reserved</code>, which are managed in the <code>ParkingSpot</code> model.</li>
<li><strong>File:</strong> <code>application/models.py</code>.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, lines 209–231.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle parking history analytics?</strong></p>
<ul>
<li><strong>Answer:</strong> Parking history analytics are fetched via the <code>/api/user/analytics/parking_history</code> API and displayed visually as charts.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, line 502.</li>
<li><strong>Frontend:</strong> <code>static/components/User.js</code>, line 453.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle cost per lot analytics?</strong></p>
<ul>
<li><strong>Answer:</strong> Cost per lot analytics are retrieved via the <code>/api/user/analytics/cost_per_lot</code> API and presented as charts.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, line 522.</li>
<li><strong>Frontend:</strong> <code>static/components/User.js</code>, line 453.</li>
</ul>
</li>
<li>
<p><strong>How does the application ensure data integrity?</strong></p>
<ul>
<li><strong>Answer:</strong> Data integrity is maintained through <strong>database constraints and validation within API endpoints</strong>. For example, a parking lot with occupied spots cannot be deleted.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, lines 158–186.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle user-triggered background tasks?</strong></p>
<ul>
<li><strong>Answer:</strong> User-triggered tasks, such as exporting parking history, are processed via <strong>Celery</strong> and monitored using task IDs.</li>
<li><strong>File:</strong> <code>application/tasks.py</code>, lines 46–61.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle periodic background tasks?</strong></p>
<ul>
<li><strong>Answer:</strong> Periodic tasks, like sending reminders and reports, are scheduled using <strong>Celery’s <code>crontab</code></strong>.</li>
<li><strong>File:</strong> <code>app.py</code>, lines 63–74.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle parking lot deletion?</strong></p>
<ul>
<li><strong>Answer:</strong> Parking lots can only be deleted if all spots are empty. This is validated in the <code>DELETE /api/parking_lots/&lt;lot_id&gt;</code> API.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, line 186.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle parking spot updates?</strong></p>
<ul>
<li><strong>Answer:</strong> Parking spots can be updated via the <code>PUT /api/parking_lots/&lt;lot_id&gt;</code> API.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, line 146.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle parking spot reservations?</strong></p>
<ul>
<li><strong>Answer:</strong> Parking spots are reserved via the <code>POST /api/user/reserve</code> API.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, line 322.</li>
</ul>
</li>
<li>
<p><strong>How does the application handle parking spot releases?</strong></p>
<ul>
<li><strong>Answer:</strong> Parking spots are released via the <code>PUT /api/user/reservation/&lt;reservation_id&gt;</code> API.</li>
<li><strong>File:</strong> <code>application/resources.py</code>, line 377.</li>
</ul>
</li>
</ol>

