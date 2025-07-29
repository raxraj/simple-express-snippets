# Simple Express Snippets

The essential collection of Express Snippets and commands with full TypeScript support.

## Features

Comprehensive Express.js snippets for both JavaScript and TypeScript, covering:

- 🚀 Server setup and configuration
- 🛣️ Routing (GET, POST, PUT, DELETE, PATCH)
- 🔒 Security middleware (Helmet, CORS, Rate Limiting)
- 🔐 Authentication (JWT, Sessions)
- ✅ Validation and error handling
- 📁 File uploads and static files
- 🗄️ Database integration
- 🧪 Testing utilities
- 📝 Logging and monitoring
- 🎯 Full TypeScript support with proper typing

Simply, comprehensive Express snippets with everything you need.

## Snippets

### Core Server Setup
| Snippet      | Description                                    |
| ------------ | ---------------------------------------------- |
| `ess`        | Express simple server setup                   |
| `essfull`    | Complete Express server with middleware       |
| `ejson`      | Express JSON parsing middleware               |
| `eue`        | Express URL encoded middleware                |
| `estatic`    | Express static files middleware               |

### Routing
| Snippet      | Description                                    |
| ------------ | ---------------------------------------------- |
| `esrouter`   | Create Express router                         |
| `esgr`       | Simple GET route                              |
| `espr`       | Simple POST route                             |
| `esput`      | Simple PUT route                              |
| `esdel`      | Simple DELETE route                           |
| `espatch`    | Simple PATCH route                            |
| `ergr`       | Router GET request                            |
| `erpr`       | Router POST request                           |
| `erput`      | Router PUT request                            |
| `erdel`      | Router DELETE request                         |
| `erpatch`    | Router PATCH request                          |
| `eparams`    | Route with parameters (TypeScript typed)     |
| `equery`     | Route with query parameters (TypeScript typed)|

### Middleware
| Snippet      | Description                                    |
| ------------ | ---------------------------------------------- |
| `emiddleware`| Express middleware function                   |
| `easyncmw`   | Async Express middleware                      |
| `eerror`     | Error handling middleware                     |
| `e404`       | 404 error handler                             |
| `ecors`      | CORS configuration                            |
| `ehelmet`    | Helmet security middleware                    |
| `emorgan`    | Morgan logging middleware                     |
| `eratelimit` | Rate limiting setup                           |
| `esession`   | Session configuration                         |
| `ecookie`    | Cookie parser setup                           |

### Authentication & Security
| Snippet      | Description                                    |
| ------------ | ---------------------------------------------- |
| `ejwt`       | JWT authentication middleware                 |
| `ejwtgen`    | JWT token generation                          |
| `evalidate`  | Validation middleware (express-validator)     |

### Async Operations
| Snippet      | Description                                    |
| ------------ | ---------------------------------------------- |
| `easync`     | Async route handler with error handling      |

### Responses
| Snippet      | Description                                    |
| ------------ | ---------------------------------------------- |
| `eresj`      | JSON response                                 |
| `eresstat`   | Response with status                          |
| `eredirect`  | Redirect response                             |

### File Operations
| Snippet      | Description                                    |
| ------------ | ---------------------------------------------- |
| `efileupload`| File upload setup with Multer                |

### Database
| Snippet      | Description                                    |
| ------------ | ---------------------------------------------- |
| `edbconnect` | MongoDB connection setup                      |

### Testing
| Snippet      | Description                                    |
| ------------ | ---------------------------------------------- |
| `etest`      | Test setup with Jest and Supertest           |

### Architecture
| Snippet      | Description                                    |
| ------------ | ---------------------------------------------- |
| `econtroller`| Controller with multiple methods              |

### TypeScript Specific
| Snippet        | Description                                  |
| -------------- | -------------------------------------------- |
| `einterface`   | TypeScript interface for data models       |
| `ecustomreq`   | Custom request interface                    |
| `eenvtypes`    | Environment variables type definitions      |
| `eapiresponse` | Generic API response type                   |
| `etypedroute`  | Fully typed route handler                   |

## Full Expansions

### ess - Express simple server Setup

**JavaScript:**
```javascript
const express = require('express');

const app = express();

app.listen(3000, () => {
  console.log(`Server is Listening on 3000`);
});
```

**TypeScript:**
```typescript
import express, { Application } from 'express';

const app: Application = express();
const PORT: number = Number(process.env.PORT) || 3000;

app.listen(PORT, () => {
  console.log(`Server is listening on port ${PORT}`);
});
```

### essfull - Complete Express server setup

**JavaScript:**
```javascript
const express = require('express');
const cors = require('cors');
const helmet = require('helmet');
const morgan = require('morgan');

const app = express();
const PORT = process.env.PORT || 3000;

// Security middleware
app.use(helmet());
app.use(cors());

// Logging middleware
app.use(morgan('combined'));

// Body parsing middleware
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// Static files
app.use(express.static('public'));

// Routes
app.get('/', (req, res) => {
  res.json({ message: 'Server is running!' });
});

// Error handling middleware
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).json({ error: 'Something went wrong!' });
});

app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

### ejwt - JWT authentication middleware

**TypeScript:**
```typescript
import jwt from 'jsonwebtoken';
import { Request, Response, NextFunction } from 'express';

interface AuthenticatedRequest extends Request {
  user?: any;
}

const authenticateToken = (req: AuthenticatedRequest, res: Response, next: NextFunction): void => {
  const authHeader = req.headers['authorization'];
  const token = authHeader && authHeader.split(' ')[1];

  if (!token) {
    res.status(401).json({ error: 'Access token required' });
    return;
  }

  jwt.verify(token, process.env.JWT_SECRET as string, (err, user) => {
    if (err) {
      res.status(403).json({ error: 'Invalid token' });
      return;
    }
    req.user = user;
    next();
  });
};
```

### econtroller - Express controller

**TypeScript:**
```typescript
import { Request, Response, NextFunction } from 'express';

interface Controller {
  getAll: (req: Request, res: Response, next: NextFunction) => Promise<void>;
  getById: (req: Request, res: Response, next: NextFunction) => Promise<void>;
}

const controllerName: Controller = {
  getAll: async (req: Request, res: Response, next: NextFunction): Promise<void> => {
    try {
      // Your logic here
      res.json({ success: true, data: [] });
    } catch (error) {
      next(error);
    }
  },

  getById: async (req: Request, res: Response, next: NextFunction): Promise<void> => {
    try {
      const { id } = req.params;
      res.json({ success: true, data: { id } });
    } catch (error) {
      next(error);
    }
  }
};

export default controllerName;
```

## TypeScript Support

This extension provides comprehensive TypeScript support including:

- **Proper Type Imports**: All snippets include necessary type imports from Express
- **Type Annotations**: Request, Response, NextFunction, and custom interfaces
- **Generic Types**: Typed route handlers with custom parameter, body, and response types
- **Interface Definitions**: Ready-to-use interfaces for common patterns
- **Environment Variables**: Type-safe environment variable definitions
- **Custom Request Types**: Extended request interfaces for authentication and custom data

## Why This Extension?

- **Comprehensive**: 50+ snippets covering all aspects of Express development
- **Type-Safe**: Full TypeScript support with proper type annotations
- **Modern**: Uses latest Express patterns and best practices
- **Practical**: Based on real-world development needs
- **Consistent**: Uniform naming and structure across all snippets
- **Documented**: Detailed descriptions and examples for each snippet

## Installation

Install the extension from the VS Code marketplace and start using the snippets immediately in your JavaScript or TypeScript files.

## Contributing

Found a bug or want to suggest a new snippet? Please open an issue or pull request on our GitHub repository.

## Thank You! ❤️

Special thanks to the following individuals who have helped with this project:

- [@raxraj](https://twitter.com/raxrajtwit)
- [@anxxica](https://instagram.com/anxxica)
