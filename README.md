# Speaker Isolator API

This tool allows you to isolate speakers from a YouTube video using AssemblyAI's Speaker Diarization API.

## Prerequisites

- Python 3.x
- AssemblyAI API key

## Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/shahirtaj/speaker-isolator.git
    ```

2. Navigate to the project directory:

    ```bash
    cd speaker-isolator
    ```

3. Create a virtual environment:

    ```bash
    python3 -m venv venv
    ```

4. Activate the virtual environment:
    - For Windows:

        ```powershell
        venv\Scripts\activate
        ```

    - For macOS and Linux:

        ```bash
        source venv/bin/activate
        ```

5. Install the required dependencies:

    ```bash
    python3 -m pip install -r requirements.txt
    ```

## Configuration

1. Create a `.env` file in the project root directory.

2. Add your AssemblyAI API key to the `.env` file:

    ```
    ASSEMBLY_AI_API_KEY="YOUR_API_KEY"
    ```

    Replace `"YOUR_API_KEY"` with your actual AssemblyAI API key, including the double quotes.

## Usage

1. Run the Flask application:

    ```bash
    python3 main.py
    ```

2. Make a `POST` request to the `/process_video` endpoint with the following JSON payload:

    ```json
    {
        "youtube_url": "YOUR_YOUTUBE_VIDEO_URL"
    }
    ```

    You can use the following `curl` command to make the request:

    ```bash
    curl -X POST -H "Content-Type: application/json" -d '{"youtube_url": "YOUR_YOUTUBE_VIDEO_URL"}' -o speaker_segments.zip http://localhost:8000/process_video
    ```

    Replace `YOUR_YOUTUBE_VIDEO_URL` with the actual URL of the YouTube video you want to process.

3. The API will process the YouTube video, isolate speaker segments, and return a ZIP file named `speaker_segments.zip` containing the output audio files.

## Error Handling

The tool includes error handling for the following scenarios:

- Invalid request payload
- Invalid YouTube URL
- Missing API key
- Errors during YouTube video download
- Errors during audio upload to AssemblyAI
- Errors during transcription process
- Errors during speaker segment creation

In case of an error, an appropriate HTTP status code and error description will be returned.

## Logging

The tool uses Python's `logging` module for logging. Log messages are output to the console with timestamps and log levels.

## License

This project is distributed under the MIT License. See the [LICENSE](LICENSE) file for more information.
