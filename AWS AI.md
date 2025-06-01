Overview of Amazon Bedrock Parameters
This screenshot is from Amazon Bedrock, where several parameters (or "knobs") can be configured to influence the behavior and output of the foundational model. Let’s walk through the key ones:

### 1. System Prompts
System prompts define how the model should behave and respond.

Example: You can instruct the model to "Reply as if you are a teacher in the AWS Cloud space."

This helps set the tone, style, and role the model adopts, which guides the nature of its response.

### 2. Temperature
Controls the creativity and randomness of the output.

Range: 0.0 to 1.0

Low values (e.g., 0.2):

More deterministic and repetitive

Focuses on the most likely responses

High values (e.g., 1.0):

More diverse and unpredictable

May lead to less coherent but more creative outputs

Think of temperature as a “creativity dial.” Higher values allow more variety in word choices.

### 3. Top P (Nucleus Sampling)
Top P controls the probability mass of words considered for output.

Range: 0.0 to 1.0

Low values (e.g., 0.25):

Only considers the top 25% of likely next words

Results in more coherent and focused output

High values (e.g., 0.99):

Considers a broader range of words

Leads to more diverse and potentially creative responses

### 4. Top K
Defines the number of most probable tokens to consider.

Low values (e.g., 10):

Model chooses from the top 10 likely next words

Promotes more controlled and coherent outputs

High values (e.g., 500):

Broadens the selection pool to the top 500 candidates

Increases variety and creativity in responses

Difference: Top P is based on probability distribution; Top K is a fixed number of tokens.

### 5. Length
Specifies the maximum length of the output.

Controls how long the model should continue generating text.

Useful to limit overly verbose responses.

### 6. Stop Sequences
Defines specific tokens or phrases that signal the model to stop generating further output.

Once the model hits a stop sequence, it halts the response.

## Prompt Latency
Prompt latency is the time it takes for the model to generate a response. It is affected by:

Model Size: Larger models are generally slower.

Model Type: Different models (e.g., Claude vs. Llama) have varying performance.


Input Tokens: More context (longer prompts) means more time to process.

Output Length: Longer responses take more time to generate.

Important Note: Latency is not impacted by Temperature, Top P, or Top K.

## Prompt Engineering Techniques
In this lecture, we explore several prompt engineering techniques that can be used to enhance the quality and precision of responses from generative AI models like those used in Amazon Bedrock.

### 1. Zero-Shot Prompting
Definition: Asking a model to perform a task without providing any examples.

Example Prompt:
"Write a short story about a dog that helps solve a mystery."

Behavior: The model relies entirely on its pretrained general knowledge.

Best Use: When the task is simple or the model is highly capable.

### 2. Few-Shot Prompting
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

### 3. Chain-of-Thought Prompting
Definition: Prompting the model to generate step-by-step reasoning or follow a structured process.

Prompt Example:
"First describe the setting and the dog, then introduce the mystery, next show how the dog discovers clues, and finally reveal how the dog solves the mystery."

Phrase Tip: Use “Think step by step” to trigger logical reasoning.

Behavior: Helps generate more coherent and logical outputs.

Best Use: For tasks that involve complex reasoning or multi-step logic.

### 4. Retrieval-Augmented Generation (RAG)
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

#### Summary of Techniques
Technique	Description	Best Use Case
Zero-Shot	No examples; uses general model knowledge	Simple or general tasks
Few-Shot	Guided with 1 or more examples	Tasks needing specific tone/format
Chain-of-Thought	Step-by-step reasoning or instructions	Tasks involving logic or structured output
RAG	Uses external data to enhance prompt context	Domain-specific or data-heavy tasks

## Amazon Q Business Overview
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

## Amazon Q Developer is a powerful new service from AWS that operates in two major areas: natural language interaction with AWS and AI-powered code assistance. On the one hand, it allows users to query AWS documentation and their own AWS accounts using plain English. For instance, a developer can ask, “List all my Lambda functions,” and Amazon Q Developer will respond with detailed information such as, “You have five Lambda functions in the us-east-1 region,” and list their names. This is especially useful for developers managing multiple resources across different regions. Beyond information retrieval, Amazon Q can suggest accurate AWS CLI commands to help execute actions like modifying function timeouts, without having to write commands from scratch. It also provides billing analysis and troubleshooting capabilities. For example, users can ask, “What were the top three highest cost services in Q1?” and receive a breakdown that might include Amazon SageMaker, ECS, and AWS Config, along with associated costs.

On the other hand, Amazon Q Developer acts as an AI coding assistant, similar to GitHub Copilot but specialized for AWS development. Developers can request code generation such as, “Write Python code to list files in an S3 bucket,” and Amazon Q will produce functional code with parameter support. It supports multiple programming languages, including Python, Java, JavaScript, TypeScript, and C#, with more to come. Integrated with popular IDEs like Visual Studio Code, Visual Studio, and JetBrains, Amazon Q Developer enhances productivity through real-time code suggestions, code completion, security scanning, debugging, optimization, and even project bootstrapping. It helps developers answer AWS-specific development questions, implement features, and generate documentation automatically, significantly accelerating the development process.

## 🔁 How AI Works – The Stack
Data Layer: Collect and prepare data (role of data engineers, data scientists)

ML Framework Layer: Define the algorithm and approach (e.g., regression, classification)

Model Layer: Train and fine-tune the model (adjust parameters)

Application Layer: Deploy and expose the model to users (API, UI)

## 🤖 Machine Learning (ML)
ML enables machines to learn from data without being explicitly programmed.

Examples:

Regression: Predicting trends from continuous data

Classification: Categorizing data based on learned boundaries

## 🧠 Deep Learning (DL)
A subset of ML using artificial neural networks inspired by the human brain.

Involves input, hidden, and output layers

Requires large datasets and high computational power (GPUs)

Enables tasks like:

Image recognition

Speech recognition

Natural language processing (NLP)

Neural Network Example:

Input: Pixel values of a handwritten digit

Hidden Layers: Learn features like lines or curves

Output: Predicts digit (e.g., “8”)

## 🔬 Generative AI (GenAI)
A subset of deep learning focused on generating new content.

Based on transformer models

Processes entire sentences efficiently

Learns patterns and relationships between words

Used in:

Text generation (ChatGPT, BERT)

Image generation (Diffusion models)

Multimodal models (combine text, audio, images, video)

### 🧩 Comparison: Traditional AI vs ML vs DL vs GenAI
Type	What it Does	Example
AI (Rules-Based)	If-then rules	Fire safety system
ML	Learns patterns	Dog vs. cat classifier
DL	Learns abstract patterns	Identify a tiger without seeing one before
GenAI	Generates creative content	Write a poem or generate a video from text and image

### 🧠 Final Thought
Humans display capabilities similar to all these AI levels:

We follow rules (AI)

We learn from experience (ML)

We generalize from patterns (DL)

We create new ideas (GenAI)

Text Models: GPT, BERT

Image Models: ResNet, GAN

Audio Models: WaveNet

Traditional ML: SVM, XGBoost

Sequence Data: RNN

In supervised learning, the goal is to train a machine learning model using labeled data, meaning each input has a known output. The model learns to predict outputs for new, unseen inputs by identifying patterns in the training data. Supervised learning includes two main types: regression, which predicts continuous numerical values (e.g., predicting weight from height or house prices from size), and classification, which assigns inputs to discrete categories (e.g., identifying an animal as a dog, cat, or giraffe based on features like height and weight, or classifying emails as spam or not spam). The data used in supervised learning is typically split into three sets: a training set (60–80%) to teach the model, a validation set (10–20%) to fine-tune parameters, and a test set (10–20%) to evaluate performance. Additionally, feature engineering plays a vital role by transforming raw data into meaningful inputs—like converting birth dates into age or extracting sentiment from text—to improve model performance. Feature engineering can be applied to both structured (like tabular data) and unstructured data (like text or images) and includes techniques such as feature extraction, selection, and transformation.

## 🔍 Unsupervised Learning
Unsupervised learning works with unlabeled data, meaning the model doesn’t know the "correct answers" but tries to uncover hidden patterns or groupings in the data on its own. The model outputs structures or clusters that humans can later interpret.

Key techniques:

Clustering: Groups similar data points (e.g., customer segmentation to target marketing).

Association Rule Learning: Finds relationships between items (e.g., "People who buy bread also buy butter" → used in retail placement).

Anomaly Detection: Identifies data points that differ significantly from the norm (e.g., spotting fraudulent transactions).

## 🧠 Semi-Supervised Learning
This is a mix between supervised and unsupervised learning. It starts with a small set of labeled data and a large set of unlabeled data. The process:

Train a model on the small labeled set.

Use that model to pseudo-label the unlabeled data.

Combine everything and retrain the model as if it were supervised learning.

This approach is practical when labeled data is expensive or scarce but unlabeled data is abundant.
 ## Reinforcement Learning (RL) – Executive Summary
#### 🧩 Basic Concept
Reinforcement Learning is a type of machine learning where an agent learns to make decisions by interacting with an environment to maximize cumulative reward over time.

###🎯 Key Terminology
Term	Meaning
Agent	The learner or decision-maker (e.g., robot in a maze).
Environment	Everything the agent interacts with (e.g., the maze).
Action	What the agent can do (e.g., move up/down/left/right).
State	The current situation the agent is in (e.g., its location).
Reward	Feedback from the environment (e.g., +100 for exit, -10 for wall).
Policy	The strategy the agent uses to decide which action to take.
Transition	Moving from one state to another based on an action.
Cumulative Reward	Total points accumulated over time — what the agent tries to maximize.

### 🔁 The Learning Loop
Observe current state.

Choose an action (based on current policy).

Perform the action → environment transitions to new state.

Receive a reward.

Update policy based on experience.

Repeat (many times) → agent improves over time.

### 🎮 Simple Example (Maze)
Move to a valid tile: -1 reward

Hit a wall: -10 reward

Find the exit: +100 reward

Goal: Learn to get to the exit efficiently (shortest path with least penalties).

### 📈 Real-World Applications
🕹️ Games: AI playing Go, Chess, or video games.

🤖 Robotics: Navigation and object manipulation.

💰 Finance: Optimizing trading strategies.

🚑 Healthcare: Personalized treatment planning.

🚗 Self-Driving Cars: Route planning and decision-making.

### 🔧 How RLHF Works (Step-by-Step)
#### 1. Pretraining (Supervised Learning)
The model (like GPT) is first trained on large text datasets from books, websites, etc.

It learns to predict the next word — basic language understanding.

#### 2. Collect Human Feedback
Humans interact with the model.

For a given input (prompt), the model generates multiple outputs (responses).

Human labelers rank these outputs from best to worst.

Example:

vbnet
Copy
Edit
Prompt: "How do I make tea?"
Responses:
1. "Boil water, steep a teabag..."
2. "Why would you want tea?"
3. "Tea is a popular beverage."

Labelers may rank (1) > (3) > (2).
#### 3. Train a Reward Model
A new model (called a reward model) is trained to predict these rankings.

It learns: What kind of output do humans prefer?

#### 4. Reinforcement Learning (PPO)
The original language model is now fine-tuned using reinforcement learning.

The reward model gives a reward score to outputs.

A technique like Proximal Policy Optimization (PPO) is used to adjust the model’s behavior to maximize human-like responses.


## 🔍 Evaluating Machine Learning Models
🟩 For Binary Classification Models
📊 Confusion Matrix
A 2x2 table to compare:

Predicted vs Actual values

Actual Positive (Spam)	Actual Negative (Not Spam)
##### Predicted Positive	                 ✅ True Positive (TP)	             ❌ False Positive (FP)
##### Predicted Negative	                 ❌ False Negative (FN)            	✅ True Negative (TN)

📐 Key Classification Metrics
Metric	Formula	When to Use
Precision	TP / (TP + FP)	When false positives are costly (e.g., spam filter)
Recall	TP / (TP + FN)	When false negatives are costly (e.g., disease detection)
F1 Score	2 × (Precision × Recall) / (Precision + Recall)	Good balance between precision and recall
Accuracy	(TP + TN) / (Total Samples)	Only reliable on balanced datasets

✅ Spam/Not Spam is an imbalanced dataset, so avoid relying on accuracy.

### 📈 AUC-ROC (Area Under the Receiver Operating Curve)
Sensitivity (TPR) = True Positives / (True Positives + False Negatives)

1 - Specificity (FPR) = False Positives / (False Positives + True Negatives)

### Interpretation:

AUC close to 1 = Strong model

AUC around 0.5 = Random model

Used to compare models across thresholds

🟦 For Regression Models
📏 Key Regression Metrics
Metric	Measures	Notes
MAE (Mean Absolute Error)	Avg. absolute difference between actual and predicted	Easy to interpret
MAPE (Mean Absolute Percentage Error)	Avg. percentage error	Good for comparing across scales
RMSE (Root Mean Squared Error)	Penalizes larger errors more than MAE	Smooths errors
R² (R-Squared)	Proportion of variance explained by the model	Close to 1 = good fit

💡 Example:

RMSE = 5 → Model is on average 5 points off

R² = 0.8 → 80% of score variation is explained by the model inputs

🔍 Inferencing in Machine Learning
Inferencing is when a trained model makes predictions on new data. There are different types of inferencing, each suited for specific use cases:

#### 1. ⚡ Real-Time Inferencing
Purpose: Immediate response to user input.

Use Case: Chatbots, recommendation engines, fraud detection.

Characteristics:

Prioritizes speed over perfect accuracy.

Needs to respond quickly to input as it happens.

Example: Typing into a chatbot and getting an instant response.

##### 2. 🧮 Batch Inferencing
Purpose: Analyze large volumes of data at once.

Use Case: Business intelligence, reporting, model evaluation.

Characteristics:

Prioritizes accuracy over speed.

Can take minutes, hours, or even days to process.

Results are returned after processing is complete.

#### 3. 🌐 Edge Inferencing
Purpose: Run models directly on devices near the data source.

Use Case: IoT devices, mobile apps, remote sensors.

Characteristics:

Edge devices (e.g., Raspberry Pi, mobile phones) typically have limited compute power.

Ideal for low-latency, offline usage.

Uses Small Language Models (SLMs) or compressed models.

Benefits:

Local processing = fast inference

No internet needed

Low power and compute footprint

#### 4. 🌍 Remote Inferencing (Cloud-Based)
Purpose: Use powerful models from remote servers.

Use Case: Using full-scale LLMs via APIs (e.g., Amazon Bedrock).

Characteristics:

Edge devices send requests to a server over the internet.

Supports larger, more accurate models.

Trade-offs:

Higher latency

Requires internet connection

Edge devices act as thin clients.

### AWS Managed AI Service

