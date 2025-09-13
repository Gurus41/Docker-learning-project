<<<<<<< HEAD
# Super Mario Mimic - Browser App

A modern **React + Vite** application styled with **TailwindCSS** that mimics elements of the classic Super Mario game experience.  
This project is lightweight, fast, and can run locally in the browser or inside a Docker container.  

---

## 🎮 App Features

- **Modern Frontend Stack**: Built with React, Vite, and TailwindCSS  
- **Responsive UI**: Works across desktop and mobile browsers  
- **Lightweight Build**: Fast production build optimized for deployment  
- **Containerized**: Ready to run with Docker Desktop or any container platform  
- **Simple Deployment**: Runs as a static site with `http-server`  

---

## 🏗️ Project Structure

```
├── src/
│   ├── components/           # Reusable UI components
│   ├── assets/               # Images, icons, static files
│   ├── App.tsx               # Main application entry
│   └── main.tsx              # React root mounting point
├── index.html                # Application HTML entry point
├── vite.config.ts            # Vite configuration
├── tailwind.config.js        # TailwindCSS configuration
├── package.json              # Dependencies and scripts
├── Dockerfile                # Container build configuration
├── docker-compose.yml        # Optional helper for local runs
└── README.md                 # This file
```

---

## 🎯 Application Architecture

1. **React Components**  
   - UI built with modular, reusable React components.  
   - TailwindCSS classes for fast styling.  

2. **Vite Build System**  
   - Fast dev server with hot reload.  
   - Bundles to `/dist` folder for production.  

3. **Docker Containerization**  
   - Multi-stage Dockerfile for efficient builds.  
   - Uses Node.js to build, then serves static files via `http-server`.  

---

## 🚀 Getting Started

### Prerequisites
- [Node.js 18+](https://nodejs.org/)  
- npm or yarn package manager  
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (optional, for containerization)  

---

### Local Development (with hot reload)

1. **Install dependencies:**
```bash
npm install
```

2. **Start dev server:**
```bash
npm run dev
```

3. **Open your browser:**
👉 http://localhost:5173

---

### Building for Production

```bash
npm run build
npm run preview
```

This generates the static build in `/dist`.

---

## 🐳 Docker Containerization

This app can be run inside Docker for easy local or production deployment.  

### Build the Docker image
```bash
docker build -t super-mario-mimic .
```

### Run the container
```bash
docker run -p 8080:8080 super-mario-mimic
```

### Access the app
👉 http://localhost:8080

---

### Using Docker Compose (optional)
```bash
docker compose up --build
```

Stop with:
```bash
docker compose down
```

---

## 🎮 App Usage

- Open in browser → explore the Mario-themed mimic UI.  
- Fully responsive → works on desktop & mobile.  
- Static frontend app → no backend required.  

---

## 🔧 Technical Notes

- Built with **TypeScript** for type safety  
- Uses **Vite** for blazing fast build & dev server  
- Styled with **TailwindCSS** utility classes  
- Runs anywhere Docker is available  

---

## 🎨 Customization

- Update UI → edit components in `/src/components/`  
- Modify styles → adjust `tailwind.config.js` or component classes  
- Add new features → expand React components & routes  

---

## 📝 License

This project is created for educational and demonstration purposes.  