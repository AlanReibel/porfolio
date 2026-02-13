# Backend Stack Documentation

## 🔧 Lenguajes & Runtime

### Node.js
**Nivel:** Avanzado
```javascript
// Express server
import express from 'express';
const app = express();

app.get('/api/users', async (req, res) => {
  try {
    const users = await User.find();
    res.json(users);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});

app.listen(3000, () => console.log('Server running'));
```

**Frameworks:**
- Express.js
- Fastify
- Nest.js

### PHP
**Nivel:** Experto
```php
<?php
namespace App\Controllers;

class UserController {
  public function index() {
    $users = User::all();
    return view('users.index', ['users' => $users]);
  }
}
```

**Features:**
- Object-oriented programming
- Namespacing
- Type hints

### Laravel
**Nivel:** Avanzado
```php
// routes/web.php
Route::apiResource('users', UserController::class);

// app/Http/Controllers/UserController.php
class UserController extends Controller {
  public function index() {
    return User::paginate();
  }
  
  public function store(Request $request) {
    return User::create($request->validated());
  }
}
```

**Key Features:**
- Eloquent ORM
- Query Builder
- Migrations
- Seeding
- Relationships
- Middleware

## 💾 Datos & Persistencia

### SQL (Relational Databases)
**Nivel:** Avanzado
```sql
-- User management
CREATE TABLE users (
  id INT PRIMARY KEY AUTO_INCREMENT,
  email VARCHAR(255) UNIQUE NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_email ON users(email);

SELECT u.*, COUNT(p.id) as posts_count
FROM users u
LEFT JOIN posts p ON u.id = p.user_id
GROUP BY u.id;
```

**Optimization Techniques:**
- Indexing strategy
- Query optimization
- Connection pooling
- Caching queries
- Normalization (3NF)

**Tools:**
- PostgreSQL
- MySQL
- MariaDB

### ORMs
**Eloquent (Laravel):**
```php
$users = User::where('active', true)
  ->with('posts')
  ->paginate(15);

$user->posts()->create(['title' => 'New Post']);
```

**Sequelize (Node.js):**
```javascript
const users = await User.findAll({
  include: [{ association: 'posts' }],
  limit: 15,
});
```

## 🌐 API Design

### REST APIs
**Nivel:** Experto
```
GET    /api/v1/users           - List users
GET    /api/v1/users/:id       - Get user
POST   /api/v1/users           - Create user
PUT    /api/v1/users/:id       - Update user
DELETE /api/v1/users/:id       - Delete user
```

**Best Practices:**
- HTTP status codes
- JSON responses
- Pagination
- Filtering & sorting
- Rate limiting
- API versioning

### SOAP
**Nivel:** Intermedio
```xml
<?xml version="1.0"?>
<soap:Envelope>
  <soap:Body>
    <GetUser><userid>123</userid></GetUser>
  </soap:Body>
</soap:Envelope>
```

**Use Cases:**
- Legacy integrations
- WSDL contracts
- Enterprise systems

## 🏗️ Architecture Patterns

### Clean Architecture
```
domain/
├── entities/          # Business logic
├── usecases/         # Application logic
└── repositories/     # Data access

infrastructure/
├── controllers/      # HTTP layer
├── database/        # DB implementation
└── external/        # External services

presentation/        # UI layer
```

### Design Patterns
- **Repository Pattern** - Data access abstraction
- **Service Layer** - Business logic
- **Factory Pattern** - Object creation
- **Dependency Injection** - Loose coupling
- **Strategy Pattern** - Algorithm selection

## 🔐 Security

**Essential Practices:**
- Input validation & sanitization
- SQL injection prevention
- CORS configuration
- JWT authentication
- Password hashing (bcrypt)
- HTTPS enforcement
- Rate limiting

```javascript
// Express middleware example
app.use(express.json());
app.use(helmet()); // Security headers
app.use(cors());
app.use(express.urlencoded({ extended: true }));
```

## 📊 Database Design

**Relationships:**
```sql
-- One-to-Many
user_id (FK) -> users.id

-- Many-to-Many
CREATE TABLE post_tags (
  post_id INT,
  tag_id INT,
  PRIMARY KEY (post_id, tag_id)
);

-- Polymorphic
morphable_type VARCHAR(255),
morphable_id INT
```

## 🧪 Testing

**PHPUnit Example:**
```php
public function test_user_creation() {
  $user = User::factory()->create();
  $this->assertDatabaseHas('users', ['id' => $user->id]);
}
```

**Node.js Testing:**
```javascript
describe('User API', () => {
  it('creates a user', async () => {
    const res = await request(app)
      .post('/api/users')
      .send({ email: 'test@example.com' });
    
    expect(res.status).toBe(201);
  });
});
```

---

**Last Updated:** February 13, 2025
