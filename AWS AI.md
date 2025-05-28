Overview of Amazon Bedrock Parameters
This screenshot is from Amazon Bedrock, where several parameters (or "knobs") can be configured to influence the behavior and output of the foundational model. Let’s walk through the key ones:

1. System Prompts
System prompts define how the model should behave and respond.

Example: You can instruct the model to "Reply as if you are a teacher in the AWS Cloud space."

This helps set the tone, style, and role the model adopts, which guides the nature of its response.

2. Temperature
Controls the creativity and randomness of the output.

Range: 0.0 to 1.0

Low values (e.g., 0.2):

More deterministic and repetitive

Focuses on the most likely responses

High values (e.g., 1.0):

More diverse and unpredictable

May lead to less coherent but more creative outputs

Think of temperature as a “creativity dial.” Higher values allow more variety in word choices.

3. Top P (Nucleus Sampling)
Top P controls the probability mass of words considered for output.

Range: 0.0 to 1.0

Low values (e.g., 0.25):

Only considers the top 25% of likely next words

Results in more coherent and focused output

High values (e.g., 0.99):

Considers a broader range of words

Leads to more diverse and potentially creative responses

4. Top K
Defines the number of most probable tokens to consider.

Low values (e.g., 10):

Model chooses from the top 10 likely next words

Promotes more controlled and coherent outputs

High values (e.g., 500):

Broadens the selection pool to the top 500 candidates

Increases variety and creativity in responses

Difference: Top P is based on probability distribution; Top K is a fixed number of tokens.

5. Length
Specifies the maximum length of the output.

Controls how long the model should continue generating text.

Useful to limit overly verbose responses.

6. Stop Sequences
Defines specific tokens or phrases that signal the model to stop generating further output.

Once the model hits a stop sequence, it halts the response.

Prompt Latency
Prompt latency is the time it takes for the model to generate a response. It is affected by:

Model Size: Larger models are generally slower.

Model Type: Different models (e.g., Claude vs. Llama) have varying performance.


Input Tokens: More context (longer prompts) means more time to process.

Output Length: Longer responses take more time to generate.

Important Note: Latency is not impacted by Temperature, Top P, or Top K.

Prompt Engineering Techniques
In this lecture, we explore several prompt engineering techniques that can be used to enhance the quality and precision of responses from generative AI models like those used in Amazon Bedrock.

1. Zero-Shot Prompting
Definition: Asking a model to perform a task without providing any examples.

Example Prompt:
"Write a short story about a dog that helps solve a mystery."

Behavior: The model relies entirely on its pretrained general knowledge.

Best Use: When the task is simple or the model is highly capable.

2. Few-Shot Prompting
Definition: Providing a few examples of the task to guide the model’s output.

Example:

Provide two example stories:

Whiskers the Cat solving a mystery.

Buddy the Bird solving a mystery.

Then prompt:
"Write a short story about a dog that helps solve a mystery."

Behavior: The model learns from patterns in the examples.

Variants:

One-Shot Prompting: Providing one example.

Few-Shot Prompting: Providing multiple examples.

Best Use: When you want the model to follow a specific format or tone.

3. Chain-of-Thought Prompting
Definition: Prompting the model to generate step-by-step reasoning or follow a structured process.

Prompt Example:
"First describe the setting and the dog, then introduce the mystery, next show how the dog discovers clues, and finally reveal how the dog solves the mystery."

Phrase Tip: Use “Think step by step” to trigger logical reasoning.

Behavior: Helps generate more coherent and logical outputs.

Best Use: For tasks that involve complex reasoning or multi-step logic.

4. Retrieval-Augmented Generation (RAG)
Definition: Combines the model’s generation capabilities with external data sources.

Workflow:

User prompt is issued.

Relevant information is retrieved from external data (e.g., documents, databases).

The data is injected into the prompt.

The model generates a response using both its knowledge and the augmented context.

Example:

Prompt:
"Write a story about a dog solving a mystery using the following information:"

Context:

Dogs have an excellent sense of smell.

Neighborhood thefts often involve missing items.

Dogs can track scents over long distances.

Behavior: The output reflects contextual knowledge from the external data.

Best Use: When domain-specific or up-to-date knowledge is required.

Summary of Techniques
Technique	Description	Best Use Case
Zero-Shot	No examples; uses general model knowledge	Simple or general tasks
Few-Shot	Guided with 1 or more examples	Tasks needing specific tone/format
Chain-of-Thought	Step-by-step reasoning or instructions	Tasks involving logic or structured output
RAG	Uses external data to enhance prompt context	Domain-specific or data-heavy tasks

Amazon Q Business Overview
Amazon Q Business is a fully managed generative AI assistant designed specifically for organizations. It helps employees interact with internal company knowledge and data securely and intelligently.

Key Features and Capabilities
Company-Specific Knowledge: Trained on your internal data (not general internet knowledge).

Use Cases:

Writing job postings or social media content.

Summarizing meetings or querying internal documents.

Automating tasks like submitting time-off requests or creating meeting invites.

Built on Amazon Bedrock:

Uses multiple foundation models behind the scenes.

Foundation model selection is abstracted away from the user.

Retrieval-Augmented Generation (RAG):

Amazon Q searches internal documents (e.g., PDFs) to find and present accurate answers with source references.

Amazon Q Developer is a powerful new service from AWS that operates in two major areas: natural language interaction with AWS and AI-powered code assistance. On the one hand, it allows users to query AWS documentation and their own AWS accounts using plain English. For instance, a developer can ask, “List all my Lambda functions,” and Amazon Q Developer will respond with detailed information such as, “You have five Lambda functions in the us-east-1 region,” and list their names. This is especially useful for developers managing multiple resources across different regions. Beyond information retrieval, Amazon Q can suggest accurate AWS CLI commands to help execute actions like modifying function timeouts, without having to write commands from scratch. It also provides billing analysis and troubleshooting capabilities. For example, users can ask, “What were the top three highest cost services in Q1?” and receive a breakdown that might include Amazon SageMaker, ECS, and AWS Config, along with associated costs.

On the other hand, Amazon Q Developer acts as an AI coding assistant, similar to GitHub Copilot but specialized for AWS development. Developers can request code generation such as, “Write Python code to list files in an S3 bucket,” and Amazon Q will produce functional code with parameter support. It supports multiple programming languages, including Python, Java, JavaScript, TypeScript, and C#, with more to come. Integrated with popular IDEs like Visual Studio Code, Visual Studio, and JetBrains, Amazon Q Developer enhances productivity through real-time code suggestions, code completion, security scanning, debugging, optimization, and even project bootstrapping. It helps developers answer AWS-specific development questions, implement features, and generate documentation automatically, significantly accelerating the development process.
