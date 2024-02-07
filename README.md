# MoneyPrinter

Automate the creation of YouTube Shorts locally, simply by providing a video topic to talk about.

> **Important** Please make sure you look through existing/closed issues before opening your own. If it's just a question, please join our [discord](https://dsc.gg/fuji-community) and ask there.

> **🎥** Watch the video on [YouTube](https://youtu.be/mkZsaDA2JnA?si=pNne3MnluRVkWQbE).

## Installation

```bash
git clone https://github.com/FujiwaraChoki/MoneyPrinter.git
cd MoneyPrinter

# Create virtual environment
python -m venv venv

# Activate virtual environment
venv\scripts\activate.ps1

# Install requirements
pip install -r requirements.txt

# Copy .env.example and fill out values
cp .env.example .env

# Run the backend server
cd Backend
python main.py

# Run the frontend server
cd ../Frontend
python -m http.server 3000
```

See [`.env.example`](.env.example) for the required environment variables.

If you need help, open [ENV.md](ENV.md) for more information.

## Usage

1. Copy the `.env.example` file to `.env` and fill in the required values
1. Open `http://localhost:3000` in your browser
1. Enter a topic to talk about
1. Click on the "Generate" button
1. Wait for the video to be generated
1. The video's location is `temp/output.mp4`

## Fonts

Add your fonts to the `fonts/` folder, and load them by specifying the font name on line `124` in `Backend/video.py`.

## Automatic YouTube Uploading
 
MoneyPrinter now includes functionality to automatically upload generated videos to YouTube.

To use this feature, you need to:
1. Create a project inside your Google Cloud Platform -> `https://console.cloud.google.com/`. 
1. Obtain `client_services.json` from the project and add it to the Backend/ directory.
1. Enable the YouTube v3 API in your project -> `https://console.cloud.google.com/apis/library/youtube.googleapis.com`
1. Create an `OAuth consent screen` and add yourself (the account of your youtube channel) to the testers.
1. Enable the following scopes in the `OAuth consent screen` for your project:

```
'https://www.googleapis.com/auth/youtube'
'https://www.googleapis.com/auth/youtube.upload'
'https://www.googleapis.com/auth/youtubepartner'
```

After this, you can generate the videos and you will be prompted to authenticate yourself. 

The authentication process creates and stores a `main.py-oauth2.json` file inside the Backend/ directory. Keep this to stay authenticated, remove this file to authenticate again (with another account if needed).

Videos are uploaded as private by default. For a complete automated workflow change : `main.py -> line 171`
`(privacyStatus = "private" # "public", "private", "unlisted")`

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=FujiwaraChoki/MoneyPrinter&type=Date)](https://star-history.com/#FujiwaraChoki/MoneyPrinter&Date)

## License

See [`LICENSE`](LICENSE) file for more information.
