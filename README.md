# 🔐 SecureShare - Encrypted File Sharing Platform

A secure file sharing platform built with Flask that uses AES-256 encryption to protect your files. Share files securely with password protection and expiring links.

## ✨ Features

- **🔒 AES-256 Encryption**: Military-grade encryption for all uploaded files
- **🔗 Secure Links**: Generate unique, secure download links
- **🛡️ Password Protection**: Each file is protected with a custom password
- **⏰ Expiry Control**: Set download limits and expiry dates
- **📊 File Management**: Track downloads and manage shared files
- **👤 User Dashboard**: Personal dashboard for file management
- **📱 Responsive Design**: Works on desktop and mobile devices

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- pip package manager

### Installation

1. **Clone or download the project**
2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the application**:
   ```bash
   python app.py
   ```

4. **Open your browser** and navigate to `http://localhost:5000`

## 📁 Project Structure

```
secure file sharing/
├── app.py                 # Main Flask application
├── requirements.txt       # Python dependencies
├── uploads/              # Encrypted file storage
├── static/
│   └── css/
│       └── style.css     # Styling
├── templates/
│   ├── index.html        # Landing page
│   ├── login.html        # Login page
│   ├── signup.html       # Registration page
│   ├── dashboard.html    # User dashboard
│   ├── profile.html      # User profile
│   └── download.html     # File download page
└── README.md             # This file
```

## 🔧 How It Works

### File Upload Process

1. **User Authentication**: Login or create an account
2. **File Selection**: Drag & drop or browse to select a file
3. **Password Protection**: Set a strong password for encryption
4. **AES Encryption**: File is encrypted using PBKDF2 key derivation and AES-256
5. **Secure Link**: Generate a unique download link
6. **Share**: Share the link and password with recipients

### File Download Process

1. **Access Link**: Recipient opens the secure download link
2. **Password Entry**: Enter the correct file password
3. **Decryption**: Server decrypts the file using the provided password
4. **Download**: File is downloaded in its original format

## 🔒 Security Features

- **PBKDF2 Key Derivation**: 100,000 iterations for secure key generation
- **AES-256 Encryption**: Industry-standard symmetric encryption
- **Secure Password Hashing**: Using Werkzeug's security functions
- **Session Management**: Secure Flask sessions
- **File Expiry**: Automatic link expiration
- **Download Limits**: Prevent unlimited downloads

## 📊 Database Schema

### Users Table
- `id`: Primary key
- `username`: Unique username
- `email`: Unique email address
- `password_hash`: Hashed password
- `created_at`: Account creation date

### Files Table
- `id`: Primary key
- `filename`: Encrypted filename
- `original_filename`: Original file name
- `file_path`: Path to encrypted file
- `file_size`: File size in bytes
- `encryption_key`: Encrypted key for file
- `file_password`: Hashed file password
- `secure_link`: Unique download link
- `upload_date`: Upload timestamp
- `expiry_date`: Link expiration date
- `download_count`: Number of downloads
- `max_downloads`: Maximum allowed downloads
- `user_id`: Foreign key to users table

## 🎨 UI/UX Features

- **Modern Design**: Clean, gradient-based design
- **Responsive Layout**: Works on all device sizes
- **Drag & Drop**: Intuitive file upload
- **Real-time Feedback**: Flash messages and alerts
- **Smooth Animations**: CSS transitions and hover effects
- **Modal Windows**: User-friendly dialogs

## 🔧 Configuration

### Environment Variables

You can configure the application by modifying the `app.py` file:

```python
app.config['SECRET_KEY'] = 'your-secret-key'
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///secure_share.db'
app.config['UPLOAD_FOLDER'] = 'uploads'
app.config['MAX_CONTENT_LENGTH'] = 100 * 1024 * 1024  # 100MB
```

### Customization

- **File Size Limit**: Modify `MAX_CONTENT_LENGTH`
- **Database**: Change `SQLALCHEMY_DATABASE_URI`
- **Upload Folder**: Modify `UPLOAD_FOLDER`

## 🚀 Deployment

### Production Setup

1. **Set up a production database** (PostgreSQL/MySQL)
2. **Configure environment variables**
3. **Use a production WSGI server** (Gunicorn/uWSGI)
4. **Set up reverse proxy** (Nginx)
5. **Configure HTTPS** (SSL certificate)

### Docker Deployment

```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["python", "app.py"]
```

## 🛠️ Development

### Adding New Features

1. **Backend**: Add routes in `app.py`
2. **Frontend**: Create new templates in `templates/`
3. **Styling**: Modify `static/css/style.css`
4. **Database**: Update models and run migrations

### Testing

```bash
# Run the application in development mode
python app.py
```

## 📝 License

This project is for educational purposes. Use at your own risk.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📞 Support

For issues and questions, please refer to the code documentation or create an issue.

---

**⚠️ Important Security Note**: This application handles sensitive file data. Ensure you:
- Use strong, unique passwords
- Keep the application updated
- Use HTTPS in production
- Regularly backup your database
- Monitor file uploads for malicious content
