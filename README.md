# Solar Panel Defect Detection using YOLOv8

## Description

A full-stack web application for detecting defects in solar panels using YOLOv8 computer vision model. The system provides a user-friendly interface for uploading images and viewing detection results, with user authentication and admin capabilities.

## Features

- 🔍 **Defect Detection**: Advanced YOLOv8 model for accurate solar panel defect identification
- 📤 **Image Upload**: Easy drag-and-drop interface for uploading solar panel images
- 🔐 **User Authentication**: Secure authentication using Clerk
- 👨‍💼 **Admin Dashboard**: User management and system oversight
- 📊 **Detection History**: Track and review past detection results
- 📱 **Responsive Design**: Works seamlessly on desktop and mobile devices
- ⚡ **Real-time Processing**: Fast inference with optimized YOLOv8 model

## Tech Stack

### Backend
- **Python 3.8+**
- **FastAPI** - Modern, fast web framework
- **Ultralytics YOLOv8** - State-of-the-art object detection
- **SQLite** - Lightweight database
- **Clerk** - Authentication service
- **Svix** - Webhook verification

### Frontend
- **React 19** - Latest React with modern features
- **Vite** - Fast build tool and dev server
- **Clerk React SDK** - Authentication integration
- **React Router** - Client-side routing
- **Tailwind CSS** - Utility-first CSS framework

## Installation

### Prerequisites
- Python 3.8 or higher
- Node.js 16 or higher
- Git

### Backend Setup

1. **Navigate to backend directory:**
   ```bash
   cd backend
   ```

2. **Create virtual environment:**
   ```bash
   python -m venv venv
   # On Windows:
   # venv\Scripts\activate
   # On macOS/Linux:
   source venv/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set environment variables:**
   Create a `.env` file in the backend directory:
   ```
   CLERK_WEBHOOK_SECRET=your_clerk_webhook_secret_here
   ```

5. **Run the backend server:**
   ```bash
   uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
   ```

### Frontend Setup

1. **Navigate to frontend directory:**
   ```bash
   cd frontend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Set environment variables:**
   Create a `.env` file in the frontend directory:
   ```
   VITE_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key_here
   VITE_API_BASE_URL=http://localhost:8000
   ```

4. **Run the development server:**
   ```bash
   npm run dev
   ```

## Usage

1. **Start the Backend:**
   - Ensure the backend server is running on port 8000

2. **Start the Frontend:**
   - The frontend will be available at `http://localhost:5173`

3. **Access the Application:**
   - Open your browser and navigate to the frontend URL
   - Sign up or log in using Clerk authentication

4. **Upload Images:**
   - Use the detection page to upload solar panel images
   - The system will process the image and highlight detected defects

5. **View Results:**
   - Check the results page for processed images with bounding boxes
   - Access detection history in the history section

## API Documentation

The backend provides a REST API with the following endpoints:

### Core Endpoints
- `GET /` - Health check and system status
- `POST /predict` - Upload image for defect detection
- `GET /detections` - Retrieve detection history
- `GET /detections/{id}` - Get specific detection details

### Authentication
- `POST /webhooks/clerk` - Clerk authentication webhooks

### User Management
- `GET /users` - Get all users (admin only)
- `PUT /users/{id}/access` - Update user access level (admin only)

## Project Structure

```
solar-panel-defect-detection-using-yolo-v8/
├── backend/
│   ├── app/
│   │   ├── main.py              # FastAPI application entry point
│   │   ├── predictor.py         # YOLO model inference logic
│   │   ├── db.py                # Database operations
│   │   ├── detections.py        # Detection management
│   │   ├── model_loader.py      # Model loading utilities
│   │   ├── sync.py              # User synchronization
│   │   └── utils.py             # Helper functions
│   ├── models/
│   │   └── best.pt              # Trained YOLOv8 model weights
│   ├── requirements.txt         # Python dependencies
│   └── runs/                    # Detection results storage
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/          # Reusable React components
│   │   │   ├── ThemeToggle.jsx  # Dark/light theme switcher
│   │   ├── context/
│   │   │   └── ThemeContext.jsx # Theme context provider
│   │   ├── hooks/
│   │   │   └── useReveal.js     # Custom hooks
│   │   ├── pages/               # Application pages
│   │   │   ├── Home.jsx         # Landing page
│   │   │   ├── Detection.jsx    # Image upload and detection
│   │   │   ├── History.jsx      # Detection history
│   │   │   └── AdminDashboard.jsx # Admin panel
│   │   ├── App.jsx              # Main app component
│   │   ├── main.jsx             # React entry point
│   │   └── index.css            # Global styles
│   ├── package.json             # Node dependencies
│   ├── vite.config.js           # Vite configuration
│   └── eslint.config.js         # ESLint configuration
├── uml_diagrams/                # System architecture diagrams
├── module_descriptions.html     # Module documentation
├── README.md                    # This file
├── .gitignore                   # Git ignore rules
└── LICENSE                      # MIT License
```

## Configuration

### Environment Variables

#### Backend (.env)
```
CLERK_WEBHOOK_SECRET=your_webhook_secret_from_clerk
```

#### Frontend (.env)
```
VITE_CLERK_PUBLISHABLE_KEY=your_publishable_key_from_clerk
VITE_API_BASE_URL=http://localhost:8000
```

### Clerk Setup
1. Create a Clerk application at [clerk.com](https://clerk.com)
2. Copy the publishable key to frontend `.env`
3. Copy the webhook secret to backend `.env`
4. Configure webhook endpoints in Clerk dashboard

## Development

### Running Tests
```bash
# Backend tests
cd backend
pytest

# Frontend tests
cd frontend
npm test
```

### Building for Production
```bash
# Backend
cd backend
pip install -r requirements.txt
uvicorn app.main:app --host 0.0.0.0 --port 8000

# Frontend
cd frontend
npm run build
npm run preview
```

## Contributing

We welcome contributions! Please follow these steps:

1. **Fork the repository**
2. **Create a feature branch:**
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes**
4. **Commit your changes:**
   ```bash
   git commit -m "Add your feature description"
   ```
5. **Push to the branch:**
   ```bash
   git push origin feature/your-feature-name
   ```
6. **Create a Pull Request**

### Guidelines
- Follow PEP 8 for Python code
- Use ESLint rules for JavaScript/React
- Write clear, concise commit messages
- Add tests for new features
- Update documentation as needed

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics) for the object detection model
- [FastAPI](https://fastapi.tiangolo.com/) for the web framework
- [Clerk](https://clerk.com/) for authentication
- [React](https://reactjs.org/) for the frontend framework
- [Vite](https://vitejs.dev/) for the build tool

## Support

If you encounter any issues or have questions:

1. Check the [Issues](https://github.com/Jaswanth190/solar-panel-defect-detection-using-yolo-v8/issues) page
2. Create a new issue with detailed information
3. Contact the maintainers

---

**Note:** This project is for educational and demonstration purposes. For production use, additional security measures and optimizations may be required.