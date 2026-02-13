# Currently Learning Stack

## 📚 PostgreSQL

**Current Level:** Beginner → Intermediate

### Setup & Basics
```bash
# Install (macOS)
brew install postgresql

# Start service
brew services start postgresql

# Connect
psql -U postgres -d mydb
```

**Learning Path:**
- [x] Basic queries (SELECT, INSERT, UPDATE, DELETE)
- [ ] Advanced queries (JOINs, subqueries, CTEs)
- [ ] Indexing strategies
- [ ] Window functions
- [ ] Optimization techniques

### Example Queries
```sql
-- Complex query
SELECT 
  u.name,
  COUNT(p.id) as post_count,
  AVG(p.views) as avg_views
FROM users u
LEFT JOIN posts p ON u.id = p.user_id
WHERE u.created_at > NOW() - INTERVAL '1 year'
GROUP BY u.id
HAVING COUNT(p.id) > 0
ORDER BY post_count DESC;

-- Window function
SELECT 
  name,
  salary,
  AVG(salary) OVER (PARTITION BY department) as dept_avg
FROM employees;
```

### Resources
- [PostgreSQL Official Docs](https://www.postgresql.org/docs/)
- [PgAdmin](https://www.pgadmin.org/)
- Interactive learning platforms

**Next Steps:**
- Master query optimization
- Learn query planner
- Implement proper indexes
- Study replication

---

## 📡 Apache Kafka

**Current Level:** Beginner

### What is Kafka?
- Distributed streaming platform
- Real-time data processing
- Event sourcing
- Message queue alternative

### Learning Path
- [ ] Basic concepts (topics, partitions, brokers)
- [ ] Producer/Consumer APIs
- [ ] Stream processing
- [ ] Exactly-once semantics
- [ ] Monitoring & scaling

### Basic Setup
```bash
# Start Kafka
bin/kafka-server-start.sh config/server.properties

# Create topic
kafka-topics.sh --create --topic events --partitions 3

# Produce message
kafka-console-producer.sh --topic events

# Consume messages
kafka-console-consumer.sh --topic events --from-beginning
```

### Node.js Example
```javascript
const kafka = require('kafkajs');

const producer = kafka.producer();
await producer.connect();

// Produce
await producer.send({
  topic: 'events',
  messages: [
    { key: 'user-1', value: JSON.stringify({action: 'login'}) }
  ]
});

// Consume
const consumer = kafka.consumer({ groupId: 'my-group' });
await consumer.subscribe({ topic: 'events' });

await consumer.run({
  eachMessage: async ({ topic, partition, message }) => {
    console.log('Message:', message.value.toString());
  }
});
```

**Next Steps:**
- Build real-time event system
- Explore Kafka Streams
- Learn monitoring tools
- Study at-least-once delivery

---

## ☁️ AWS S3

**Current Level:** Beginner

### What is S3?
- Simple Storage Service
- Object storage
- Highly scalable
- Cost-effective

### Use Cases
- Static website hosting
- Media storage
- Data backup
- CDN origin
- Log storage

### Basic Operations
```javascript
// AWS SDK v3
import { S3Client, PutObjectCommand } from "@aws-sdk/client-s3";

const client = new S3Client({ region: "us-east-1" });

// Upload file
const upload = new PutObjectCommand({
  Bucket: "my-bucket",
  Key: "image.jpg",
  Body: fileBuffer
});

await client.send(upload);
```

### Pricing Considerations
- Storage cost (per GB/month)
- Request cost (per 1000 requests)
- Data transfer cost
- Use S3 Lifecycle Management

**Next Steps:**
- S3 + CloudFront CDN
- S3 + Lambda
- S3 bucket policies
- Cost optimization

---

## 🧪 Test-Driven Development (TDD)

**Current Level:** Intermediate

### TDD Workflow (Red-Green-Refactor)
```
1. Write failing test (RED)
2. Write minimal code to pass (GREEN)
3. Refactor for quality (REFACTOR)
```

### Example
```typescript
// 1. WRITE TEST (RED)
test('should calculate total price with tax', () => {
  const cart = new Cart();
  cart.addItem({ price: 100 });
  expect(cart.totalWithTax(0.1)).toBe(110);
});

// 2. IMPLEMENT (GREEN)
class Cart {
  items: Item[] = [];
  
  addItem(item: Item) {
    this.items.push(item);
  }
  
  totalWithTax(taxRate: number) {
    const total = this.items.reduce((sum, item) => sum + item.price, 0);
    return total * (1 + taxRate);
  }
}

// 3. REFACTOR
class Cart {
  private items: Item[] = [];
  
  addItem(item: Item): void {
    this.items.push(item);
  }
  
  private getSubtotal(): number {
    return this.items.reduce((sum, item) => sum + item.price, 0);
  }
  
  getTotalWithTax(taxRate: number): number {
    return this.getSubtotal() * (1 + taxRate);
  }
}
```

### Benefits
- Better code design
- Fewer bugs
- Easier refactoring
- Living documentation
- Confidence in changes

**Next Steps:**
- Practice TDD in projects
- Learn testing patterns
- Master test utilities
- Achieve high coverage

---

## 🏛️ Domain-Driven Design (DDD)

**Current Level:** Intermediate

### Core Concepts

**Entities:** Objects with identity
```typescript
class User {
  constructor(
    public id: UserId,
    public email: Email,
    public name: Name
  ) {}
}
```

**Value Objects:** No identity, immutable
```typescript
class Email {
  constructor(public value: string) {
    if (!this.isValid(value)) throw new Error('Invalid email');
  }
  
  private isValid(email: string) {
    return email.includes('@');
  }
}
```

**Aggregates:** Clusters of entities
```typescript
class User {
  id: UserId;
  email: Email;
  posts: Post[] = [];
  
  addPost(post: Post) {
    this.posts.push(post);
  }
}
```

**Repositories:** Data access
```typescript
interface UserRepository {
  save(user: User): Promise<void>;
  findById(id: UserId): Promise<User | null>;
  delete(id: UserId): Promise<void>;
}
```

### Event Sourcing
```typescript
class User {
  private uncommittedEvents: DomainEvent[] = [];
  
  register(email: Email) {
    this.uncommittedEvents.push(
      new UserRegisteredEvent(this.id, email)
    );
  }
  
  getUncommittedEvents() {
    return this.uncommittedEvents;
  }
}
```

**Next Steps:**
- Apply DDD to projects
- Implement event sourcing
- Learn CQRS
- Master bounded contexts

---

## ⚡ FFB (Form-First Backend)

**Current Level:** Beginner

### Concept
- Design forms first
- Database schema derives from forms
- Backend validates form structure
- API follows form patterns

### Example
```typescript
// 1. Define form
const registerForm = z.object({
  email: z.string().email(),
  password: z.string().min(8),
  name: z.string().min(2)
});

type RegisterForm = z.infer<typeof registerForm>;

// 2. Database schema follows form
interface User {
  id: string;
  email: string;
  password: string;
  name: string;
}

// 3. API endpoint uses form
app.post('/register', async (req, res) => {
  const data = registerForm.parse(req.body);
  const user = await User.create(data);
  res.json(user);
});
```

**Benefits:**
- Type safety
- Validation consistency
- Simpler backend
- Better documentation

**Next Steps:**
- Implement in projects
- Combine with React/Vue forms
- Master validation libraries
- Explore form-driven frameworks

---

## 📊 Learning Progress

```
PostgreSQL     ████░░░░░░ 40%
Kafka          ██░░░░░░░░ 20%
AWS S3         ███░░░░░░░ 30%
TDD            ██████░░░░ 60%
DDD            █████░░░░░ 50%
FFB            ██░░░░░░░░ 20%
```

## 🎯 Learning Goals

**Q1 2025:**
- [ ] PostgreSQL intermediate proficiency
- [ ] Complete TDD project
- [ ] Design DDD system

**Q2 2025:**
- [ ] Kafka real-time app
- [ ] AWS S3 + CloudFront setup
- [ ] FFB-based backend

**Q3 2025:**
- [ ] PostgreSQL + Kafka integration
- [ ] Advanced DDD patterns
- [ ] Full-stack FFB application

---

**Last Updated:** February 13, 2025
