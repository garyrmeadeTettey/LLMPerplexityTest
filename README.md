<h1 align="center">Perplexity-Inspired LLM Answer Engine</h1>

    

## Technologies Used

- **Next.js**: A React framework for building server-side rendered and static web applications.
- **Tailwind CSS**: A utility-first CSS framework for rapidly building custom user interfaces.
- **Vercel AI SDK**: The Vercel AI SDK is a library for building AI-powered streaming text and chat UIs.
- **Groq & Mixtral**: Technologies for processing and understanding user queries.
- **Langchain.JS**: A JavaScript library focused on text operations, such as text splitting and embeddings.
- **Brave Search**: A privacy-focused search engine used for sourcing relevant content and images.
- **Serper API**: Used for fetching relevant video and image results based on the user's query.
- **OpenAI Embeddings**: Used for creating vector representations of text chunks.
- **Cheerio**: Utilized for HTML parsing, allowing the extraction of content from web pages.
- **Ollama (Optional)**: Used for streaming inference and embeddings.
- **Upstash Redis Rate Limiting (Optional)**: Used for setting up rate limiting for the application.

## Getting Started


### Obtaining API Keys

- **OpenAI API Key**: [Generate your OpenAI API key here](https://platform.openai.com/account/api-keys).
- **Groq API Key**: [Get your Groq API key here](https://console.groq.com/keys).
- **Brave Search API Key**: [Obtain your Brave Search API key here](https://brave.com/search/api/).
- **Serper API Key**: [Get your Serper API key here](https://serper.dev/).

### Installation

1. Clone the repository:
    ```
    git clone https://github.com/developersdigest/llm-answer-engine.git
    ```
2. Install the required dependencies:
    ```
    npm install
    ```
    or
    ```
    bun install
    ```
3. Create a `.env` file in the root of your project and add your API keys:
    ```
    OPENAI_API_KEY=your_openai_api_key
    GROQ_API_KEY=your_groq_api_key
    BRAVE_SEARCH_API_KEY=your_brave_search_api_key
    SERPER_API=your_serper_api_key
    ```

### Running the Server

To start the server, execute:
```
npm run dev
```
or
```
bun run dev
```

the server will be listening on the specified port.

## Editing the Configuration

The configuration file is located in the `app/config.tsx` file. You can modify the following values

- useOllamaInference: false,
- useOllamaEmbeddings: false,
- inferenceModel: 'mixtral-8x7b-32768', 
- inferenceAPIKey: process.env.GROQ_API_KEY, 
- embeddingsModel: 'text-embedding-3-small', 
- textChunkSize: 800, 
- textChunkOverlap: 200, 
- numberOfSimilarityResults: 2,
- numberOfPagesToScan: 10, 
- nonOllamaBaseURL: 'https://api.groq.com/openai/v1'
- useFunctionCalling: true
- useRateLimiting: false

### Function Calling Support (Beta)
Currently, function calling is supported with the following capabilities:

- Maps and Locations (Serper Locations API)
- Shopping (Serper Shopping API)
- TradingView Stock Data (Free Widget)
- Any functionality that you would like to see here, please open an issue or submit a PR.
- To enable function calling and conditional streaming UI (currently in beta), ensure useFunctionCalling is set to true in the config file.

### Ollama Support (Partially supported)
Currently, streaming text responses are supported for Ollama, but follow-up questions are not yet supported.

Embeddings are supported, however, time-to-first-token can be quite long when using both a local embedding model as well as a local model for the streaming inference. I  recommended decreasing a number of the RAG values specified in the `app/config.tsx` file to decrease the time-to-first-token when using Ollama.

To get started, make sure you have the Ollama running model on your local machine and set within the config the model you would like to use and set use OllamaInference and/or useOllamaEmbeddings to true.

Note: When 'useOllamaInference' is set to true, the model will be used for both text generation, but it will skip the follow-up questions inference step when using Ollama.

More info: https://ollama.com/blog/openai-compatibility

### Roadmap

- [] Add AI Gateway to support multiple models and embeddings. (OpenAI, Azure OpenAI, Anyscale, Google Gemini & Palm, Anthropic, Cohere, Together AI, Perplexity, Mistral, Nomic, AI21, Stability AI, DeepInfra, Ollama, etc)
```https://github.com/Portkey-AI/gateway```
- [] Add a settings component to allow users to select the model, embeddings model, and other parameters from the UI
- [] Add support for follow-up questions when using Ollama
- [Complete - Beta] Add support for dynamic and conditionally rendered UI components based on the user's query

![Example](https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExN284d3p5azAyNHpubm9mb2F0cnB6MWdtcTdnd2Nkb2d1ZnRtMG0yYiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/OMpt8ZbBsjphZz6mue/giphy.gif)

 developer behind Developers Digest. If you find my work helpful or enjoy what I do, consider supporting me. Here are a few ways you can do that:

- **Patreon**: Support me on Patreon at [patreon.com/DevelopersDigest](https://www.patreon.com/DevelopersDigest)
- **Buy Me A Coffee**: You can buy me a coffee at [buymeacoffee.com/developersdigest](https://www.buymeacoffee.com/developersdigest)
- **Website**: Check out my website at [developersdigest.tech](https://developersdigest.tech)
- **Github**: Follow me on GitHub at [github.com/developersdigest](https://github.com/developersdigest)
- **Twitter**: Follow me on Twitter at [twitter.com/dev__digest](https://twitter.com/dev__digest)
