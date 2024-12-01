# URL Shortener Frontend

This is the frontend application for the URL Shortener service. The frontend is intentionally simple and minimal, as it serves only to interact with the backend. I chose [Svelte](https://svelte.dev/) for this project because it's lightweight, easy to learn, and perfectly suited for handling this small front-end use case without the complexity of larger frameworks.

---

## **Getting Started**

### **Prerequisites**
- [Node.js](https://nodejs.org/) installed on your machine.
- A running backend server for the URL shortener. You can find the backend repository here: [scalable_url_shortener](https://github.com/taman9333/scalable_url_shortener).

  To run the backend, use:
  ```bash
  docker-compose up url-shortener-1
  ```

---

### **Installation**
1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd url-shortener-frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

---

### **Running the Application**
Start the development server:
```bash
npm run dev
```

The application will be available at [http://localhost:8080](http://localhost:8080).
