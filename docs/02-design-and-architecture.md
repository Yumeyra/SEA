1. Тип на приложението
EventAura е уеб приложение, разработено с ASP.NET Core MVC.  
То представлява платформа за откриване, разглеждане и резервиране на билети за събития в различни градове.

Приложението работи по модела MVC (Model–View–Controller) и включва:
- Backend логика (Controllers + Services)
- Frontend визуализация (Razor Views + Bootstrap)
- ORM слой (Entity Framework Core)
- Релационна база данни (SQL Server)

2.Структура на проекта:
src/
│
├── Controllers/          → MVC контролери
├── Models/               → Модели и ентитита
├── Data/                 → DbContext, миграции, seeders
├── Services/             → Бизнес логика (интерфейси + имплементации)
├── Views/                → Razor страници
├── wwwroot/              → CSS, JS, изображения
├── Migrations/           → EF Core миграции
└── Program.cs            → Конфигурация на приложението


3.Основни модули / слоеве

| Слой              | Роля |
|------|------|
| Controllers | Приемат заявки, валидират вход, връщат View или JSON |
| Services | Съдържат бизнес логика (EventService, CartService, AdminEventService и др.) |
| Data Layer | DbContext, миграции, seed данни |
| Models | Ентитита за база данни + ViewModels |
| Views | HTML + Razor за визуализация |
| wwwroot | CSS, JS, изображения |


4.Основни ентитита

| Ентити     | Описание |
|--------|----------|
| Event | Събитие – заглавие, описание, дата, цена, капацитет, град, категория |
| Category | Категория на събитие (Концерт, Театър, Кино…) |
| City | Град, в който се провежда събитието |
| Ticket | Закупен билет от потребител |
| Review | Ревю/оценка за събитие |
| Favorite | Любими събития на потребителя |
| Order / OrderItem | Поръчка и артикули в поръчката |
| IdentityUser | ASP.NET Core Identity потребители |



5. Таблици и основни полета

 +Event
- Id  
- Title  
- Description  
- Date  
- Price  
- Capacity  
- CityId  
- CategoryId  
- ImageUrl  

 +Category
- Id  
- Name  

 +City
- Id  
- Name  
- Region  

 +Ticket
- Id  
- EventId  
- UserId  
- Quantity  
- UnitPrice  

 +Favorite
- UserId  
- EventId  

 +Order / OrderItem
- Order → UserId, TotalAmount  
- OrderItem → OrderId, EventId, Quantity, UnitPrice  



Връзки между таблиците

- Event – Category → Many-to-One  
- Event – City → Many-to-One  
- Event – Ticket → One-to-Many  
- Event – Review → One-to-Many  
- User – Ticket → One-to-Many  
- User – Favorite – Event → Many-to-Many  
- Order – OrderItem → One-to-Many  



 3. Диаграма или структурирано описание
    
Снимката на диаграмата е качена в папката assets в репозиторито. 


7. Потребителски поток

 Основни страници

- Начална страница  
- Списък със събития  
- Детайли за събитие  
- Любими  
- Кошница  
- Поръчка  
- Моите билети  
- Админ панел  
- Вход / Регистрация  


 User Flow

1. Потребителят влиза в сайта  
2. Разглежда събития по град, категория или търсене  
3. Отваря детайли за събитие  
4. Може да:  
   - добави в любими  
   - добави в кошница  
5. Преминава към поръчка  
6. Потвърждава и получава билет  
7. Може да остави ревю  
8. В профила си вижда:  
   - любими  
   - билети  
   - поръчки  

Администраторът може да:

- създава събития  
- редактира  
- изтрива  
- управлява категории и градове  

8. Използвани технологии

 Backend
- C#
- ASP.NET Core MVC
- Entity Framework Core
- ASP.NET Identity

 Frontend
- Razor Views
- Bootstrap 5
- Custom CSS (Dark Mode + UI/UX)

 Database
- SQL Server

 Други
- LINQ
- Dependency Injection
- Session
- Toast Notifications
- Seeders


 6. Защо са избрани тези технологии

- ASP.NET Core MVC – модерен, бърз, стабилен framework  
- EF Core – автоматично управление на база данни, миграции, LINQ  
- SQL Server – надеждна релационна база  
- Bootstrap – бързо изграждане на UI  
- Identity – готова система за потребители  
- Razor Views – лесна интеграция с backend  

Технологиите са избрани, защото позволяват:

- добра архитектура  
- лесна поддръжка  
- бързо развитие  
- сигурност  
- мащабируемост  

