# What is Responsible AI?
Responsible AI is an approach to developing, assessing, and deploying artificial intelligent systems in a safe, trustworthy, and ethical way. Microsoft is a global leader in Responsible AI, identifying six key principles that should guide AI development and usage. These principles are:

1. **Fairness**: AI systems should treat all people fairly. 
    * AI systems should treat everyone fairly, avoiding differential impacts on similarly situated groups. In contexts like medical treatment, loan applications, or employment, AI should provide consistent recommendations to individuals with similar symptoms, financial situations, or qualifications.
2. **Reliability and safety**: AI systems should perform reliably and safely.
3. **Privacy and security**: AI systems should be secure and respect privacy.
4. **Inclusiveness**: AI systems should empower everyone and engage people. Examples of inclusive AI include:
    * Facial recognition that works across skin tones, ages, and genders.
    * Interfaces that support screen readers for the visually impaired.
    * Language translation that supports small regional dialects.
    * Teams that seek diverse perspectives when designing systems.

5. **Transparency**: AI systems should be understandable.
6. **Accountability**: People should be accountable for AI systems.
-----
# Introduction to GitHub Copilot
OpenAI created the generative pretrained language model in GitHub Copilot, powered by OpenAI Codex. An extension is available for **Visual Studio Code (VS Code), Visual Studio, Neovim, and the JetBrains suite of integrated development environments (IDEs).**

### benefits while using GitHub Copilot:

* 46% of new code now written by AI
* 55% faster overall developer productivity
* 74% of developers feeling more focused on satisfying work

### GitHub Copilot features
* Copilot for chat
* Copilot for pull requests
* Copilot for the CLI

### Subscription plans
* GitHub Copilot Free
    * The GitHub Copilot Free tier includes 2000 code completions per month, 50 chat requests per month, and access to both GPT-4o and Claude 3.5 Sonnet models.
* GitHub Copilot Business
    * GitHub Copilot Business allows you to control who can use GitHub Copilot in your company. After you give access to an organization, its admins can give access to individuals and teams.
    * Code completions
    * Chat in IDE and mobile
    * Filter for security vulnerabilities
    * Code referencing
    * Filter for public code
    * IP indemnity
    * Enterprise-grade security, safety, and privacy

* GitHub Copilot Enterprise
    * GitHub Copilot Enterprise includes everything in GitHub Copilot Business, plus a layer of personalization for organizations.
    * GitHub Copilot Enterprise is available for organizations through GitHub Enterprise Cloud. 
    * GitHub Copilot Enterprise can index an organization's codebase for a deeper understanding and for suggestions that are more tailored. 
    * It offers access to GitHub Copilot customization to fine-tune private models for code completion.

### Interact with Copilot
* Inline suggestions
* Command palette
* Copilot chat
* Inline chat
    * Press CTRL+I to activate the inline chat.
    * You can use this feature to request code modifications or explanations without switching contexts.
    * Here are some common slash commands and their usage:
    * /explain - Provides an explanation of the selected code.
    * /suggest - Offers code suggestions based on the current context.
    * /tests - Generates unit tests for the selected function or class.
    * /comment - Converts comments into code snippets.
* Comments to code
* Multiple suggestions
* Explanations: Explain This feature
* Automated test generation

**Keep in mind that Copilot learns from context. Keeping your code well structured and commented helps Copilot provide more accurate and relevant assistance. The more you interact with Copilot, the better it becomes at understanding your coding style and preferences.**

### Troubleshoot GitHub Copilot in VS Code
* You can find the log files by opening the command palette and then entering either **Developer: Open Log File or Developer: Open Extensions Logs Folder.**
*  If you encounter errors and nothing is in the logs, you might try to view the logs from the process that's running VS Code and the extension. This process enables you to view the Electron logs. You can find these logs by selecting **Help > Toggle Developer Tools in VS Code.**
* Network restrictions, firewalls, or your proxy might cause problems when you're connecting to GitHub Copilot. **Enter Diagnostics, and then select GitHub Copilot: Collect Diagnostics from the list.**
-----
# Introduction to prompt engineering with GitHub Copilot

Prompt engineering is how you tell GitHub Copilot what you need. The quality of the code it gives back depends on how clear and accurate your prompts are.

**Principles of prompt engineering**
Before we explore specific strategies, let's first understand the basic principles of prompt engineering, summed up in the 4 Ss below. These core rules are the basis for creating effective prompts.

* **Single**: Always focus your prompt on a single, well-defined task or question. This clarity is crucial for eliciting accurate and useful responses from Copilot.
* **Specific**: Ensure that your instructions are explicit and detailed. Specificity leads to more applicable and precise code suggestions.
* **Short**: While being specific, keep prompts concise and to the point. This balance ensures clarity without overloading Copilot or complicating the interaction.
* **Surround**: Utilize descriptive filenames and keep related files open. This provides Copilot with rich context, leading to more tailored code suggestions.

**Best practices in prompt engineering**

* Provide enough clarity: Building on the 'Single' and 'Specific' principles, always aim for explicitness in your prompts. 
* Provide enough context with details: For example, by adding some comments at the top of your code to give more details to what you want, you can give more context to Copilot to understand your prompt, and provide better code suggestions.
* Provide examples for learning: Using examples can clarify your requirements and expectations, illustrating abstract concepts and making the prompts more tangible for Copilot.
* Assert and iterate: Your first prompt might not always yield the perfect code, and that's perfectly okay. If the first output isn't quite what you're looking for, treat it as a step in a dialogue. 

**How Copilot learns from your prompts**

* Zero-shot learning: GitHub Copilot generates code without any specific examples, relying solely on its foundational training. 
* One-shot learning: A single example is given, aiding the model in generating a more context-aware response. 
* Few-shot learning: Copilot is presented with several examples, which strike a balance between zero-shot unpredictability and the precision of fine-tuning. Let's say you want to generate code that sends you a greeting depending on the time of the day

**GitHub Copilot user prompt process flow**
1. Secure prompt transmission and context gathering: secure transmission of the user prompt over HTTPS. Copilot collects context details:
    * Code before and after the cursor position, which helps it understand the immediate context of the prompt.
    * Filename and type of the file being edited, allowing it to tailor code suggestions to the specific file type.
    * Information about adjacent open tabs, ensuring that the generated code aligns with other code segments in the same project.
    * Information on project structure and file paths
    * Information on programming languages and frameworks
    * **Pre-processing using Fill-in-the-Middle (FIM) technique** to consider both the preceding and following code context, effectively expanding the model's understanding allowing Copilot to generate more accurate and relevant code suggestions by leveraging a broader context.
2. Proxy filter: Once the context is gathered and the prompt is built, it passes securely to a proxy server hosted in a GitHub-owned Microsoft Azure tenant. The proxy filters traffic, blocking attempts to hack the prompt or manipulate the system into revealing details about how the model generates code suggestions.
3. Toxicity filtering: Copilot incorporates content filtering mechanisms before proceeding with intent extraction and code generation, to ensure that the generated code and responses don't include or promote:
    * Hate speech and inappropriate content: Copilot employs algorithms to detect and prevent the intake of hate speech, offensive language, or inappropriate content that could be harmful or offensive.
    * Personal data: Copilot actively filters out any personal data, such as names, addresses, or identification numbers, to protect user privacy and data security.
4. Code generation with LLM: Finally, the filtered and analyzed prompt is passed to LLM Models, which generate appropriate code suggestions.
5. Post-processing and response validation: Once the model produces its responses, the toxicity filter removes any harmful or offensive generated content. The proxy server then applies a final layer of checks to ensure code quality, security, and ethical standards. These checks include:
    * Code quality: Responses are checked for common bugs or vulnerabilities, such as cross-site scripting (XSS) or SQL injection, ensuring that the generated code is robust and secure.
    * **Matching public code (optional): Optionally, administrators can enable a filter that prevents Copilot from returning suggestions over ~150 characters if they closely resemble existing public code on GitHub. This prevents coincidental matches from being suggested as original content. If any part of the response fails these checks, it is either truncated or discarded.**
6. Suggestion delivery and feedback loop initiation: Only responses that pass all filters are delivered to the user. Copilot then initiates a feedback loop based on your actions
7. Repeat for subsequent prompts

**GitHub Copilot data**
* Data handling for GitHub Copilot code suggestions
    * GitHub Copilot in the code editor does not retain any prompts like code or other context used for the purposes of providing suggestions to train the foundational models. It discards the prompts once a suggestion is returned.
    * GitHub Copilot Individual subscribers can opt-out of sharing their prompts with GitHub which will otherwise be used to finetune GitHub’s foundational model.
* Data handling for GitHub Copilot chat: GitHub Copilot Chat operates as an interactive platform, allowing developers to engage in conversational interactions with the AI assistant to receive coding assistance. 
    * Formatting: Copilot meticulously formats the generated response for optimal presentation within the chat interface.
    * User engagement: You can actively engage with the response by asking follow-up questions, requesting clarifications, or providing additional input. 
    * Data retention: For Copilot Chat used outside the code editor, GitHub typically retains prompts, suggestions, and supporting context for 28 days. Specific retention policies for Copilot Chat within the code editor may vary.
* The same goes for CLI, Mobile, and GitHub Copilot Chat on GitHub.com.

* Prompt types supported by GitHub Copilot Chat
    * Direct Questions: You can ask specific questions about coding concepts, libraries, or troubleshooting issues. 
    * Code-Related Requests: You can request code generation, modification, or explanation.
    * Open-Ended Queries: You can explore coding concepts or seek general guidance by asking open-ended questions like "What are the best practices for writing clean code?" 
    * Contextual Prompts: You can provide code snippets or describe specific coding scenarios to seek tailored assistance.
* Copilot Chat's ability to process diverse input types enhances its utility as a comprehensive coding companion.

**Limited context windows**
* GitHub Copilot's context window typically ranges from approximately 200-500 lines of code or up to a few thousand tokens. This limitation can vary depending on the specific implementation and version of Copilot being used.
* Copilot Chat currently operates with a context window of 4k tokens, providing a broader scope for understanding and responding to user queries compared to the standard Copilot.
* Despite these advancements, you should be mindful of context window limitations when crafting prompts. Breaking down complex problems into smaller, more focused queries or providing relevant code snippets can significantly enhance the model's ability to provide accurate and helpful responses.

**GitHub Copilot Large Language Models (LLMs)**
* Fine-tuning is a critical process that allows us to tailor pretrained large language models (LLMs) for specific tasks or domains. It involves training the model on a smaller, task-specific dataset, known as the target dataset, while using the knowledge and parameters gained from a large pretrained dataset, referred to as the source model. Fine-tuning is essential to adapt LLMs for specific tasks, enhancing their performance. 
* **LoRA fine-tuning**
    * Traditional full fine-tuning means to train all parts of a neural network, which can be slow and heavily reliant on resources. But LoRA (Low-Rank Adaptation) fine-tuning is a clever alternative. It's used to make large pretrained language models (LLMs) work better for specific tasks without redoing all the training.
    * LoRA adds smaller trainable parts to each layer of the pretrained model, instead of changing everything.
    * The original model remains the same, which saves time and resources.
    * It beats other adaptation methods like adapters and prefix-tuning.
    * It's like getting great results with fewer moving parts.
-----
# Using advanced GitHub Copilot features 
* When GitHub Copilot is enabled, it provides you with suggestions. These suggestions are called **ghost text**. You can either ignore the ghost text, or accept it by pressing the Tab key.
* Access the **inline chat** by using the inline chat by using Ctrl+i on Windows or Command+i on a Mac. One of the benefits of using the inline chat is that you don't have to switch context by going to a different pane. 
* Within the chat pane or when using the inline chat, you can use **slash commands**. e.g. /tests, /doc, /explain, /generate, /help, /optimize, /fix
* Visual Studio Code has a feature called **agents** that allows you to interact with GitHub Copilot. These agents allow you to ask questions using a specific context. 
    * @terminal: Provides suggestions based on the terminal output.
    * @file: Focuses on the content of a specific file.
    * @directory: Considers the contents of a specific directory.
        * Example: @directory How can I optimize the scripts in the utils directory? or generate Dockerfile for given project
-----
# GitHub Copilot Across Environments: IDE, Chat, and Command Line Techniques
* GitHub Copilot supported languages: python, javascript, java, typescript, ruby, go, c#, c++. While these languages receive exceptional support, GitHub Copilot can assist with many other languages and frameworks as well.
* GitHub Copilot offers a free tier with 2,000 code autocompletes and 50 chat messages per month. 
* Method Implementation: When you start typing a method name, Copilot can suggest the entire implementation, following your established coding style.
* Naming Conventions: It picks up on your preferred naming conventions for variables, functions, and classes.
* Formatting: Copilot adapts to your indentation style, bracket placement, and other formatting preferences.
* Comment Style: It can mimic your comment style, whether you prefer inline comments, block comments, or doc strings.
* Design Patterns: When your project consistently uses certain design patterns, Copilot suggests code that aligns with these patterns.
* Types of comments utilized
    * Inline comments: Short explanations next to specific lines of code.
    * Block comments: Longer explanations that might describe a function or class.
    * Docstrings: Formal documentation strings in languages like Python.
    * TODO comments: Notes about future implementations or improvements.
    * API Documentation: Comments that describe the usage and parameters of functions or methods.
* @workspace /explain the #file:controller.js
* You can use the "@workspace /new" smart action which allows you to generate a completely new project from scratch based on your requirements. 
* @terminal: This agent is useful for command-line related questions. For example, you could ask it to find the largest file in a directory or explain the last command you ran.
* @vscode: Use this agent to ask questions related to Visual Studio Code, such as how to debug or change settings within the IDE.
* **GitHub Copilot for the Command Line**
    * you can ask Copilot to explain: ``gh copilot explain "sudo apt-get"``
    * Need help with constructing a command?: ``gh copilot suggest "Undo the last commit"``
    * **Executing suggested commands**: After receiving a suggestion, you can choose the ``Execute command`` option. You can also allow Copilot to execute commands on your behalf only if you configure the ghcs alias.
    * **Revise suggested command**: choose ``Revise command`` option
    * **Alias Configuration**: If you want Copilot to execute commands on your behalf directly, you need to set up the ghcs alias. Using an alias allows you to bypass copying and pasting commands manually, and instead Copilot does it for you.
        * ``echo 'eval "$(gh copilot alias -- bash)"' >> ~/.bashrc``
    * Feedback mechanism: ``Rate response`` option
    * **Data handling**: GitHub Copilot CLI doesn't retain your prompts, but it keeps your usage analytics. You can configure whether you want GitHub Copilot to keep and use your usage data to improve the product. Enter the command ``gh copilot config`` , select ``Optional Usage Analytics``, then select ``No`` if you want to opt out.


| Feature | Free & Pro | Business | Enterprise |
| ---------- | ---------- | --------- | --------- |
| Tailor chat conversations to your private codebase | ❌ | ❌ | ✅ |
| Unlimited integrations with Copilot Extensions (public beta) | ✅ | ✅ | ✅ |
| Build a private extension for internal tooling (public beta) | ✅ | ✅ | ✅ |
| Attach knowledge bases to chat for organizational context | ❌ | ❌ | ✅ |


* Contractual protections
    * IP indemnity: The GitHub Copilot Business and Enterprise plans include IP indemnity, which provides legal protection against intellectual property claims related to the use of Copilot suggestions. With IP indemnity, if any suggestion from GitHub Copilot is challenged as infringing on third-party IP rights, GitHub assumes legal responsibility. **For GitHub to assume legal responsibility, the Matching public code setting must be blocked.**
    * Data Protection Agreement (DPA): GitHub offers a DPA that outlines the measures taken to protect your data and ensure compliance with data privacy regulations. These agreements provide transparency and assurance that your data is handled securely and responsibly.
    * GitHub Copilot Trust Center: The GitHub Copilot Trust Center provides detailed information about how GitHub Copilot works, including security, privacy, compliance, and intellectual property safeguards. This resource helps organizations feel confident using GitHub Copilot while adhering to best practices and legal requirements.

* Filtering out matching public code:
    * This feature is essential for maintaining the originality and security of your codebase. It can reduce the risk of incorporating nonsecure or noncompliant code into your projects.

* You can use content exclusions to configure GitHub Copilot to ignore certain files. When you exclude content from GitHub Copilot:
    * Code completion is no longer available in the affected files.
    * The content in affected files won't inform code completion suggestions in other files.
    * The content in affected files won't inform GitHub Copilot Chat responses.

* Limitations of content exclusions
    * IDE limitations: In some integrated development environments (IDEs), content exclusions might not apply when you're using certain features, such as Copilot Chat. For example, in Visual Studio Code and Visual Studio, content exclusions are not applied when you use the @github chat participant in your question.
    * Semantic information: Copilot might still use semantic information from an excluded file if the IDE provides the information in a nonexcluded file. This includes type information and hover-over definitions for symbols or function calls used in code.
    * Policy scope: Content exclusion settings apply only to members of the organization in which you configure the content exclusion. Anyone else who can access the specified files can still see code completion suggestions and Copilot Chat responses referencing the specified files.

* After you add or change content exclusions, the changes can take up to 30 minutes to take effect in IDEs where the settings are already loaded. To apply changes immediately, reload the content exclusion settings in your IDE.

* Check the GitHub Copilot icon on the status bar. If a GitHub Copilot content exclusion applies to the file, the GitHub Copilot icon has a diagonal line through it. Hover over the icon to see whether an organization or the parent repository disabled GitHub Copilot for the file.
-----
# Align with developer preferences
* Code generation and completion
    * Multiple suggestions
    * Language-specific idioms
* Writing unit tests and documentation
    * Test case generation
    * Documentation stubs
    * Comment expansion
* Code refactoring
    * Pattern recognition
    * Modern syntax suggestions
    * Consistency maintenance
* Debugging assistance
    * Error explanation
    * Log statement generation
    * Test case suggestions: For bugs that are difficult to reproduce, GitHub Copilot can suggest additional test cases that might help isolate the issue.
* Data science support
    * Statistical functions
    * Data visualization
    * Data preprocessing
    * Model evaluation
* **AI in the Software Development Lifecycle (SDLC)**
    * Requirement analysis
        * Rapid prototyping: Quickly generate code snippets based on high-level descriptions
        * User story implementation
        * API design: Suggest API structures based on described functionality
    * Design & development
        * Boilerplate code generation
        * Design pattern implementation
        * Code optimization
        * Cross-language translation
    * Testing & quality assurance
        * Unit test creation
        * Test data generation
        * Edge case identification
        * Assertion suggestions
    * Deployment
        * Configuration file generation
        * Deployment script assistance
        * Documentation updates
    * Maintenance & support
        * Bug fix suggestions
        * Code refactoring
        * Documentation updates
        * Legacy code understanding
* **Identify limitations of GitHub Copilot**
    * Code quality and correctness
        * Potential for errors
        * Security concerns
        * Context misinterpretation
    * Language and framework specificity
        * Varying performance: for different languages
        * Niche technologies: For less common or newer technologies, suggestions may be less accurate or relevant.
    * Dependency on training data
        * Bias suggestions
        * Copyright concerns: There's ongoing debate about the copyright implications of code generated from trained models.
    * Complex problem solving
        * Limitation in high-level design
        * Creativity constraints: While helpful, GitHub Copilot cannot replace human creativity in solving novel problems.

* **Measure productivity gains**
    * GitHub provides a **REST API to access GitHub Copilot usage metrics** for enterprise members, teams, and organization members. These metrics offer insights into daily usage of GitHub Copilot, including completions, chat interactions, and user engagement across different editors and languages.
        * Get a summary of GitHub Copilot usage for enterprise members `Endpoint: GET /enterprises/{enterprise}/GitHub Copilot/usage`
        * Get a summary of GitHub Copilot usage for an enterprise team `Endpoint: GET /enterprises/{enterprise}/team/{team_slug}/GitHub Copilot/usage`
        * Get a summary of GitHub Copilot usage for organization members `Endpoint: GET /orgs/{org}/GitHub Copilot/usage`

* **Implementing a measurement framework**
To systematically assess GitHub Copilot's impact, consider the following framework, using the GitHub Copilot usage metric API at each stage:

    * **Evaluation**: During the initial phase of adopting GitHub Copilot, focus on leading indicators such as developer satisfaction and task completion rates. Use the API to collect metrics like **Average Daily Active Users, Total Acceptance Rate, and Lines of Code Accepted**
    * **Adoption**: As GitHub Copilot becomes more integrated into your team's workflow, continue to **monitor productivity metrics and enablement indicators**. The API can provide insights into user engagement and identify areas where further training may be needed.
    * **Optimization**: Once GitHub Copilot is fully adopted, use the REST API for GitHub Copilot usage metrics to **fine-tune its impact on broader organizational goals**, such as reducing time-to-market or improving code quality across the team.
    * **Sustained efficiency**: Continuously evaluate GitHub Copilot's effectiveness as your organization evolves. The API allows for ongoing monitoring and adjustment to ensure long-term productivity gains.

* Short-form survey: Can be conducted every two weeks if frequent feedback is needed, especially when coupled with other feedback channels like online or in-person discussions.
* Long-form survey: Recommended to be conducted no more than once every four weeks, particularly at the end of the evaluation and adoption stages, to capture comprehensive feedback.
* Analyzing survey results
    * Privacy considerations: Ensure that survey responses are anonymized and cannot be traced back to individual developers, meeting privacy obligations.
    * Data tracking: Collate the survey responses into existing Business Intelligence (BI) tools or spreadsheets for ease of analysis. Over time, track the results to identify trends and make informed decisions about GitHub Copilot's implementation.