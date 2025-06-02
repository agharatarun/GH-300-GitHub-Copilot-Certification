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
