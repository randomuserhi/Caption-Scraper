# Caption-Scraper

# New Notes
- Fine tune GPT-3 (Cheaper than GPT4, less performant)
- Unsure of effectiveness could be very good, raw GPT-3/3.5 proving difficult
- Probably should just use GPT-4 if we can get API access
- Very easy to switch, just change model name, add option

- Use Whisper (OpenAI speech2text) as performance >> youtube auto gen
- Need to scrape audio? (Should be possible, many bootleg yt2mp3 services already exist)
- Can run locally, tiny requires about 1GB VRAM 
- (likely similar performance to youtube auto maybe just scrape)
- Medium requires only about 5GB VRAM <- best option for our pcs
- Large is 10GB VRAM so not horrific but more than our GPUs
- ^ https://github.com/openai/whisper (Open Source)

- Whisper is python backend, can also be run via OpenAI API
- https://platform.openai.com/docs/guides/speech-to-text
- 25MB upload limit, can segment though so somewhat non issue

# AIMS
- WPF app (NOTE:: Code with foreshadowing of allowing webhosting for App to ALSO act as a server)
    - Coded in a way to support "plugins" => custom scrapers for getting video + transcript from other sites
        - We only supply the "youtube scraper plugin"
- AnimeDownloader-ish design (in app browser etc...)

# TECHNOLOGIES / TODO
- WPF customisation (making it not look shit)
- [CefSharp](https://github.com/chromiumembedded/cef)
    - Look into OffScreen (hide webview) 
    - https://stackoverflow.com/questions/35471261/using-cefsharp-offscreen-to-retrieve-a-web-page-that-requires-javascript-to-rend
    - https://github.com/cefsharp/CefSharp/wiki/Quick-Start-For-MS-.Net-5.0-or-greater
- LLama language model
    - Prompt engineering (supplying title / description etc...)
- Web Scraping with CefSharp for obtaining transcripts
- Key word extractor (compressing transcript for language model)
    - Lots of testing required to retain information
        - E.g Big transcript => get language model to summarise transcript => feed it back in with title
            - Experiment with iterative feeding...

# MUST HAVE
- Auto updater

# Possible Features
- OpenGL in wpf => to do cool physics based stuff / animated things...
- UI => Select time stamps in video to summarise
- Pass multiple videos to language model as context => or summarise multiple
- Chatbot (tad extra)
- Let use put in keywords => or negative keywords
    - Keyword binning
        - Users are provided keywords from extractor (idk) 
            - Users drag keywords into "correct" or "wrong" bin
            - these bins are given to language model so it knows which words are "wrong" etc...
- Let users customise "recipe" => this can also be coded as well similar to "plugins"
    - A "recipe" is just the algorithm the program uses to create the summary
        - Allows users to use different summary generation algorithms

# Things to consider
- Allow the UI to show prompts feeding into language model
    - Allow custom prompt engeneering ?
- Code Style wise, support terminal only interface for creating summary from transcript
    - `summarise.exe transcript.txt -title SOMETITLE`
- Possibly make it also be a chatbot => it watches video and pretends to be its creator
    - A tad extra...
    - E.g "How did this video differ to another video"