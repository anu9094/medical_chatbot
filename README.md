# Medical Health Management System with RAG

A Flask-based web application that combines user authentication, medical health tracking, and an AI-powered Retrieval-Augmented Generation (RAG) system for health-related queries.

## Features

- **User Authentication**: Secure signup and login system with password hashing
- **Medical Profile Management**: Store personal health information including age, allergies, and medical history
- **RAG-Based AI Assistant**: Upload medical documents (PDFs) and query them using LLaMA language model
- **Vector Database**: Chroma vector database for efficient document retrieval
- **Responsive UI**: Modern Bootstrap-based frontend
- **Local LLM Integration**: Uses Ollama with LLaMA 3.2 for privacy-preserving AI

## Tech Stack

- **Backend**: Flask 3.0.3
- **Database**: SQLite
- **Vector Store**: Chroma
- **LLM Framework**: LangChain
- **Language Model**: Ollama (LLaMA 3.2)
- **Frontend**: HTML5, CSS3, Bootstrap 5
- **File Processing**: PyPDF for PDF parsing
- **Environment Management**: Python-dotenv

## Prerequisites

- Python 3.8+
- [Ollama](https://ollama.ai/) installed and running with LLaMA 3.2 model
- pip for package management

## Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd Code
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   Create a `.env` file in the root directory:
   ```
   SECRET_KEY=your-secret-key-here
   ```

5. **Ensure Ollama is running**
   ```bash
   ollama serve
   ```
   In another terminal, pull the LLaMA model:
   ```bash
   ollama pull llama3.2
   ```

## Running the Application

1. **Start the Flask app**
   ```bash
   python app.py
   ```

2. **Access the application**
   Open your browser and navigate to:
   ```
   http://localhost:5000
   ```

## Project Structure

```
Code/
├── app.py                 # Main Flask application
├── requirements.txt       # Python dependencies
├── .env                   # Environment variables (create this)
├── .gitignore            # Git ignore rules
├── static/               # Static files (CSS, JS, images)
│   ├── css/             # Stylesheets
│   ├── js/              # JavaScript files
│   ├── img/             # Images
│   └── vendor/          # Third-party libraries
├── templates/           # HTML templates
├── uploads/             # User-uploaded documents (ignored by git)
├── chroma_medical_db/   # Vector database (ignored by git)
├── instance/            # Flask instance folder (ignored by git)
└── data/                # Data files

```

## Usage

### User Registration & Login
1. Navigate to the registration page
2. Create an account with username and password
3. Log in with your credentials

### Adding Medical Information
1. After login, fill in your medical profile
2. Add allergies, medical history, and age information

### Using the RAG Assistant
1. Upload medical documents (PDF format)
2. Ask questions about the uploaded documents
3. The AI assistant will search through your documents and provide answers

## Key Endpoints

- `GET /` - Home page
- `POST /register` - User registration
- `POST /login` - User login
- `GET /logout` - User logout
- `GET /dashboard` - User dashboard
- `POST /query` - Query the RAG system
- `POST /upload` - Upload medical documents

## Configuration

### Ollama Models
The application is configured to use `llama3.2` for both language generation and embeddings. To use a different model:

1. Open `app.py`
2. Locate lines with `model="llama3.2"`
3. Replace with your desired model name (e.g., `mistral`, `neural-chat`)
4. Pull the model with: `ollama pull <model-name>`

### Database
- SQLite is used for user data
- Vector store: Chroma database for embeddings

## Security Considerations

- Never commit `.env` files with sensitive information
- Always use strong `SECRET_KEY` values in production
- Ensure passwords are properly hashed (handled by werkzeug)
- Keep dependencies updated regularly

## Performance Notes

- Initial model loading may take time
- Large PDF uploads will be processed asynchronously
- Vector embeddings are cached for faster queries

## Troubleshooting

**Issue**: "Connection refused" when connecting to Ollama
- **Solution**: Ensure Ollama is running (`ollama serve`)

**Issue**: Model not found
- **Solution**: Pull the required model (`ollama pull llama3.2`)

**Issue**: Slow performance on first query
- **Solution**: This is normal as the model loads into memory

## Future Enhancements

- Multi-file RAG support with cross-document queries
- User-specific document management
- Email notifications
- Advanced medical data visualization
- Integration with public health APIs

## Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For issues or questions, please open an issue on the repository or contact the development team.

---

**Last Updated**: June 2026
