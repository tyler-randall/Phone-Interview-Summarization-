# Interview Summarization with Gemini API

## Overview
This project automates the summarization of two-way interview transcripts using the Gemini API. The script processes interview data stored in a CSV file, extracts the transcriptions, and generates concise summaries while preserving key names and important themes.

## Features
- Splits long interview transcripts into manageable chunks for processing.
- Sends text chunks to the Gemini API for summarization.
- Implements error handling and retry mechanisms.
- Batch processing to comply with API rate limits.
- Saves summaries back into the original CSV file to avoid redundant processing.

## Setup and Installation
### Prerequisites
Ensure you have the following installed:
- Python 3.x
- Google Colab (if running in Colab)
- A Google Gemini API key
- Required Python libraries:
  ```sh
  pip install pandas tqdm google-generativeai
  ```

### Google Drive Access
Since the CSV file is stored in Google Drive, you need to mount your drive if using Colab:
```python
from google.colab import drive
drive.mount('/content/drive')
```

## Configuration
1. Update the `csv_path` variable with the correct path to your CSV file:
   ```python
   csv_path = '/content/drive/MyDrive/Colab Notebooks/YOUR_FILE.csv'
   ```
2. Replace `GEMINI_API_KEY` with your actual API key:
   ```python
   GEMINI_API_KEY = "your-api-key-here"
   ```

## Usage
Run the script in Google Colab or a local environment:
```sh
python summarize_interviews.py
```

### Processing Workflow
1. Reads interview transcripts from a CSV file.
2. Splits long texts into smaller chunks (if necessary).
3. Sends each chunk to the Gemini API for summarization.
4. Merges summaries and saves them back into the CSV file.
5. Implements batch processing to adhere to API rate limits.

## API Rate Limits
- The script processes **15 requests per minute** and stops after **1500 requests** to avoid exceeding API quotas.
- Summaries are saved periodically to prevent data loss in case of an interruption.

## Potential Improvements
- Improve chunking logic to maintain context better.
- Implement parallel processing to speed up summarization.
- Add logging to track errors and processing status more effectively.
- Store API responses for auditing and debugging.

## Contributing
Contributions are welcome! Feel free to submit pull requests or report issues.

## License
This project is open-source. See the LICENSE file for details.
