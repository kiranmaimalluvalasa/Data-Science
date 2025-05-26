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
