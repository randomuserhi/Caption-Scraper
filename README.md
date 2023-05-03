# Caption-Scraper
 
# AIMS
- WPF app (NOTE:: Code with foreshadowing of allowing webhosting for App to ALSO act as a server)
    - Coded in a way to support "plugins" => custom scrapers for getting video + transcript from other sites
        - We only supply the "youtube scraper plugin"
- AnimeDownloader-ish design (in app browser etc...)

# TECHNOLOGIES / TODO
- WPF customisation (making it not look shit)
- [CefSharp](https://github.com/chromiumembedded/cef)
    - Look into OffScreen (hide webview) 
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