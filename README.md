# News2Sentiment - Financial News Sentiment Analysis

[![Python](https://img.shields.io/badge/Python-3.9.15-blue.svg)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.8.0-orange.svg)](https://tensorflow.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.15.1-red.svg)](https://streamlit.io/)

A deep learning-powered web application that performs sentiment analysis on financial news headlines to classify them as positive or negative. Built with TensorFlow and Streamlit, this project leverages transfer learning with the Universal Sentence Encoder for accurate sentiment classification.

## 🎯 Project Overview

News2Sentiment analyzes financial news headlines in real-time to determine their sentiment, providing valuable insights for investment decisions, market analysis, and risk assessment. The system uses a sophisticated deep learning model trained on a comprehensive dataset of Indian financial news from 2017-2021.

### Key Features

- **Real-time Sentiment Analysis**: Instant classification of financial news headlines
- **High Accuracy**: ~80% accuracy using transfer learning and bidirectional LSTM
- **User-friendly Interface**: Clean Streamlit web application
- **Confidence Scoring**: Provides confidence levels for each prediction
- **Transfer Learning**: Uses Universal Sentence Encoder for robust text understanding
- **Deployment Ready**: Complete configuration for cloud deployment

## 📊 Dataset

The model is trained on the **India Financial News Headlines Sentiments Dataset**:

- **Date Range**: January 1, 2017 to April 15, 2021
- **Sources**: Economic Times, Money Control, Livemint, Business Today, Financial Express, NY Times, WSJ, Washington Post
- **Keywords**: Economy, markets, inflation, Indian economy, Indian businesses
- **Sentiment Analysis**: Performed using Flair NLP model
- **Data Cleanup**: Removed repetitive headlines and headlines < 30 characters

## 🏗️ Technical Architecture

### Model Architecture
```
Input Layer (Text) 
    ↓
Universal Sentence Encoder (Transfer Learning)
    ↓
Expand Dimensions
    ↓
Bidirectional LSTM (72 units, return_sequences=True)
    ↓
Dropout (0.5)
    ↓
Bidirectional LSTM (72 units, return_sequences=True)
    ↓
Dropout (0.5)
    ↓
Bidirectional LSTM (72 units)
    ↓
Dropout (0.5)
    ↓
Dense Output Layer (1 unit, sigmoid activation)
```

### Technology Stack
- **Backend**: Python 3.9.15
- **Deep Learning**: TensorFlow 2.8.0
- **Web Framework**: Streamlit 1.15.1
- **Transfer Learning**: Universal Sentence Encoder
- **Data Processing**: Pandas, NumPy
- **Model Architecture**: Bidirectional LSTM with Dropout

## 🚀 Installation

### Prerequisites
- Python 3.9.15
- pip package manager

### Step 1: Clone the Repository
```bash
git clone <repository-url>
cd News2Sentiment
```

### Step 2: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 3: Download the Pre-trained Model
The application requires a pre-trained model file (`best_model.h5`). You can either:
- Train the model using the Jupyter notebook (`News2Sentiment.ipynb`)
- Download the pre-trained model from the releases section

## 📖 Usage

### Running the Web Application

1. **Start the Streamlit app**:
```bash
streamlit run main.py
```

2. **Open your browser** and navigate to the provided URL (usually `http://localhost:8501`)

3. **Enter a financial news headline** in the text input field

4. **Click "Check"** to get the sentiment analysis results

### Example Usage

```
Input: "Student loan forgiveness has scammers 'on the move,' warns FTC"
Output: "It's a Negative News. Confidence Level is 96.459% Beware!! It's a Fake News."
```

### Training Your Own Model

1. **Open the Jupyter notebook**:
```bash
jupyter notebook News2Sentiment.ipynb
```

2. **Follow the notebook cells** to:
   - Download and preprocess the dataset
   - Train the deep learning model
   - Evaluate model performance
   - Save the trained model

## 🎯 Model Performance

### Training Results
- **Training Accuracy**: 80.41%
- **Validation Accuracy**: 79.52%
- **Loss Function**: Binary Crossentropy
- **Optimizer**: Adam
- **Training Epochs**: 10

### Model Evaluation
The model uses:
- **Confusion Matrix** for performance analysis
- **Confidence Scoring** for prediction reliability
- **Binary Classification** (Positive/Negative)

## 🌐 Deployment

### Local Deployment
```bash
streamlit run main.py
```

### Cloud Deployment

The project includes configuration files for cloud deployment:

#### Heroku Deployment
1. **Setup script** (`setup.sh`) configures Streamlit for deployment
2. **Runtime specification** (`runtime.txt`) specifies Python version
3. **Requirements** (`requirements.txt`) lists all dependencies

#### Deployment Steps
1. Create a new Heroku app
2. Push the code to Heroku
3. The setup script will automatically configure the environment

### Environment Variables
- `PORT`: Server port (automatically set by deployment platform)
- Streamlit credentials can be configured in `~/.streamlit/credentials.toml`

## 📁 Project Structure

```
News2Sentiment/
├── main.py                 # Streamlit web application
├── News2Sentiment.ipynb    # Jupyter notebook for model development
├── requirements.txt        # Python dependencies
├── runtime.txt            # Python version specification
├── setup.sh              # Deployment configuration script
├── best_model.h5         # Pre-trained model (not included in repo)
└── README.md             # This file
```

## 🔧 Configuration

### Streamlit Configuration
The `setup.sh` script creates the following configuration:

```toml
# ~/.streamlit/config.toml
[server]
headless = true
enableCORS = false
port = $PORT
```

### Model Configuration
- **Input Shape**: String input
- **Output**: Binary classification (0/1)
- **Activation**: Sigmoid
- **Custom Objects**: KerasLayer for TensorFlow Hub integration

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Dataset Source**: [India Financial News Headlines Sentiments](https://www.kaggle.com/datasets/harshrkh/india-financial-news-headlines-sentiments) on Kaggle
- **GDELT Headline Scrape**: Prof. Ken Blake's script for news headline scraping
- **Helper Functions**: TensorFlow Deep Learning helper functions by mrdbourke
- **Universal Sentence Encoder**: Google's pre-trained text embedding model

## 📞 Support

If you encounter any issues or have questions:

1. Check the [Issues](https://github.com/yourusername/News2Sentiment/issues) page
2. Create a new issue with detailed description
3. Include error messages and system information

## 🔮 Future Enhancements

- [ ] Add neutral sentiment category
- [ ] Implement ensemble methods
- [ ] Add market-specific features
- [ ] Include temporal analysis
- [ ] Mobile-responsive design
- [ ] API endpoints for integration
- [ ] Real-time market data integration
- [ ] Multi-language support

---

**Note**: This project is for educational and research purposes. Always verify financial decisions with professional advisors and multiple sources.
