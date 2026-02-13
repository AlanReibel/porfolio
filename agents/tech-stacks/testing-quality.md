# Testing & Quality Stack Documentation

## 🧪 Testing Frameworks

### Vitest
**Nivel:** Avanzado

**Setup:**
```typescript
// vitest.config.ts
import { defineConfig } from 'vitest/config';

export default defineConfig({
  test: {
    globals: true,
    environment: 'jsdom',
    coverage: {
      provider: 'v8',
      reporter: ['text', 'json', 'html'],
      exclude: ['node_modules/', 'dist/']
    }
  }
});
```

**Test Example:**
```typescript
import { describe, it, expect, beforeEach, vi } from 'vitest';

describe('UserService', () => {
  let service: UserService;
  
  beforeEach(() => {
    service = new UserService();
  });
  
  it('should create user', async () => {
    const user = await service.create({
      email: 'test@example.com',
      name: 'Test User'
    });
    
    expect(user).toBeDefined();
    expect(user.email).toBe('test@example.com');
  });
  
  it('should throw on invalid email', async () => {
    await expect(
      service.create({ email: 'invalid', name: 'Test' })
    ).rejects.toThrow('Invalid email');
  });
  
  it('should call API', async () => {
    const spy = vi.spyOn(service, 'fetchUser');
    await service.fetchUser('123');
    expect(spy).toHaveBeenCalledWith('123');
  });
});
```

**Test Utilities:**
```typescript
// test-utils.ts
export const createMockUser = (overrides = {}): User => ({
  id: '1',
  email: 'test@example.com',
  name: 'Test',
  ...overrides
});

export const mockApiResponse = <T>(data: T) => {
  return Promise.resolve({
    status: 200,
    json: () => Promise.resolve(data)
  });
};
```

### PHPUnit
**Nivel:** Avanzado

```php
<?php

namespace Tests\Unit;

use PHPUnit\Framework\TestCase;
use App\Models\User;

class UserTest extends TestCase
{
    public function test_user_creation()
    {
        $user = User::factory()->create([
            'email' => 'test@example.com',
        ]);
        
        $this->assertDatabaseHas('users', [
            'email' => 'test@example.com'
        ]);
    }
    
    public function test_invalid_email()
    {
        $this->expectException(\InvalidArgumentException::class);
        User::create(['email' => 'invalid']);
    }
    
    public function test_user_has_posts()
    {
        $user = User::factory()->has(Post::factory()->count(3))->create();
        $this->assertCount(3, $user->posts);
    }
}
```

## 📊 Testing Strategy

### Test Pyramid
```
        E2E Tests (10%)
        
     Integration Tests (30%)
     
   Unit Tests (60%)
```

**Distribution:**
- **Unit Tests (60%)**: Individual functions/methods
- **Integration Tests (30%)**: Component interaction
- **E2E Tests (10%)**: Full user workflows

### Coverage Goals
```
- Line coverage: >80%
- Branch coverage: >75%
- Function coverage: >80%
- Critical paths: 100%
```

## 🔍 Code Reviews

**Checklist:**
```markdown
## Code Quality
- [ ] Follows project conventions
- [ ] Clear variable/function names
- [ ] No code duplication
- [ ] Proper error handling

## Performance
- [ ] No N+1 queries
- [ ] Efficient algorithms
- [ ] Proper caching
- [ ] No memory leaks

## Security
- [ ] Input validation
- [ ] No hardcoded secrets
- [ ] Proper authorization
- [ ] XSS/CSRF protection

## Testing
- [ ] Unit tests written
- [ ] Edge cases covered
- [ ] Coverage maintained
- [ ] Integration tests pass

## Documentation
- [ ] Comments where needed
- [ ] Types documented
- [ ] API documented
- [ ] README updated
```

## 🏛️ Clean Architecture

### Layered Structure
```
Presentation Layer
    ↓
Application Layer (Use Cases)
    ↓
Domain Layer (Business Logic)
    ↓
Infrastructure Layer (External Services)
```

### Dependencies Rule
```
↓ Dependencies flow INWARD ↓
Outer layers depend on inner
Inner layers are independent
```

### Example Structure
```typescript
// Domain: User entity
export class User {
  constructor(
    public id: string,
    public email: string,
    public name: string
  ) {}
  
  isValid(): boolean {
    return this.email.includes('@');
  }
}

// Application: Create user use case
export class CreateUserUseCase {
  constructor(private repository: IUserRepository) {}
  
  async execute(email: string, name: string): Promise<User> {
    const user = new User(generateId(), email, name);
    if (!user.isValid()) throw new Error('Invalid user');
    return this.repository.save(user);
  }
}

// Infrastructure: Database implementation
export class TypeOrmUserRepository implements IUserRepository {
  async save(user: User): Promise<User> {
    return this.db.save({...user});
  }
}
```

## 📈 Quality Metrics

**Key Metrics:**
```yaml
Code Coverage: 85%
Cyclomatic Complexity: <5
Maintainability Index: >80
Technical Debt Ratio: <5%
Bugs per KLOC: <1
Code Duplication: <3%
```

**Tools:**
- SonarQube
- CodeClimate
- ESLint
- Prettier
- GitHub Actions

## 🐛 Debugging Strategies

**JavaScript Debugging:**
```javascript
// Console methods
console.log('Info:', data);
console.error('Error:', error);
console.table(array);
console.time('operation');
// ... code ...
console.timeEnd('operation');

// Debugger
debugger; // Sets breakpoint

// Error handling
try {
  //code
} catch (error) {
  console.error('Caught:', error);
  throw new CustomError('Context', error);
}
```

**PHP Debugging:**
```php
// Using xDebug
var_dump($variable);
dd($variable); // Laravel dump & die

// Logging
Log::info('Message', ['context' => $data]);
Log::error('Error', ['exception' => $e]);
```

---

**Last Updated:** February 13, 2025
