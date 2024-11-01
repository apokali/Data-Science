# Evelyn Write-Up

## Definition Prompt Engineering
You may see the advertisement for job from a company, say they want a prompt engineer, so what is prompt engineering?
The formal definition is that the practice of crafting input queries or instructions to more accurate and desirable outputs from large language models (LLMs).
We can think of an example. You make a wish to god, like please giving me 100,000 money.
Now, we did not specify the currency to god, god may give me 100,000 Japanese Yen, which is not I want, I want 100,000 dollars.
So the wish we made is like a prompt, and the god is ChatGpt.  In order to make the goal we actually want, we need to make good prompt to Chatgpt. The Prompt Engineering is discussing how to make a better prompt

## How it works (may delete if not time)

### Create a Prompt
You start with a prompt, which is like a question or a task instruction for the AI.  For example, if you want the AI to summarize articles, your prompt might be: "Summarize the following text in a few sentences."

### Introduce "Soft" Prompts
Prompt tuning introduces what are called soft prompts, which are not written in plain language but are instead learnable vectors (numerical representations) that are attached to the user's prompt.  These vectors help guide the AI model to perform better on a specific task.

### Train the Soft Prompts
Instead of training the entire model again, prompt tuning adjusts only these soft prompts.  This tuning is much faster and less resource-intensive because it focuses only on the small prompts, not the entire model.

### Generate Better Responses
Once trained, the model responds more accurately to that specific task because it has been "taught" how to handle similar prompts more effectively.  The model itself doesn't change;  only how it processes prompts does.


## Definition Fine-Tuning

Reference: [IBM on Fine-Tuning](https://www.ibm.com/topics/fine-tuning)

### Introduction
Fine-tuning in machine learning is the process of adapting a pre-trained model for specific tasks or use cases.
It's easier and cheaper deep learning models with millions or even billions of parameters, like the large language models (LLMs). Linton will give more specifically on this part. 

### How it works
We can have two kinds of ways doing it - one is called full fine-tuning, the other is Parameter efficient fine-tuning (PEFT)

### Full-Time Tuning
Fine-tuning can be used to update the weights of the entire network(also called , but for practical reasons this is not always the case.   

### Parameter-efficient fine-tuning (PEFT)
There exist a wide variety of alternate fine-tuning methods, we can summarize them using term Parameter-efficient fine-tuning (PEFT). This method updates only a select subset of model parameters.   PEFT methods can decrease computational demands and reduces catastrophic forgetting—the phenomenon in which fine-tuning causes the loss or destabilization of the model’s core knowledge—


Given the wide variety of fine-tuning techniques and the many variables inherent to each, achieving ideal model performance often requires multiple iterations of training strategies and setups, adjusting datasets and hyperparameters like batch size, learning rate and regularization terms until a satisfactory outcome—per whichever metrics are most relevant to your use case—has been reached.

There are some examples of PEFT (may delete if no time)

I list the two of them here due to time constrictions. 
Additive fine-tuning is a technique used to improve pre-trained AI models without changing their core.  Instead of adjusting the existing model's parameters, this method adds new layers or parameters to the model and only trains these new parts, while the original model stays untouched.  This approach helps maintain the model's stability while requiring less memory during training, which is especially useful for big models.

One variation of this method is called prompt tuning.  It's like giving the model special instructions (prompts) to guide its behavior.  Instead of modifying the model itself, prompt tuning focuses on improving these instructions, allowing the model to switch between tasks more easily, although it may make things harder to interpret.

Another method involves using adapters, which are small, task-specific layers added to the model.  These adapters allow the model to be trained for a new task without touching the main part of the model.  It's efficient, as it only requires training a tiny fraction of the model’s parameters.



## Definition RAG

### Introduction
RAG (Retrieval-Augmented Generation) is an AI method that combines two powerful techniques: retrieving information from external sources and generating responses using that information. 

### How it Works:

- **Retrieval**: When asked a question, the AI first looks for relevant information by searching a large database or knowledge base.  This is similar to how we would Google something or look up facts in a book.

- **Augmented Generation**: Once the AI has found this information, it uses a language model (like GPT) to generate a response.  But instead of just making something up based on what it already knows, it incorporates the newly retrieved data into its answer.

It’s improves a LLM to a better answers by pulling in relevant data from outside databases and then using that data to create more accurate responses.


## Linton’s Write-up

### Methods
- **Prompt engineering**
  - **Pros**: Essay-of-use, Cost-effectiveness, Utilized pre-trained models, Flexibility, Prompts can be quickly adjusted 
  - **Cons**: The model can only give back what it already knows from its training, Inconsistency, Limited customization, Dependency on model’s knowledge
  - **Use cases**: General inquiries

- **Fine-tuning**
  - **Pros**: Customization, Improved accuracy, Adaptability
  - **Cons**: Cost, Significant computational resources, Technical skills, Deeper understanding of machine learning and language model architecture, Data requirements, Requires a substantial and well-curated dataset
  - **Use cases**: Specialized applications, Industry specific needs

- **Retrieval Augmented Generation (RAG)**
  - **Pros**: Dynamic information (where you need the latest information or answers), Balance, Contextual relevance
  - **Cons**: Complexity (requires integration between language model and the retrieval system), Resource intensive, Demands intensive computational power, Data dependency, The quality of the data relies heavily on the relevance and accuracy of the retrieved information
  - **Use cases**: Situations requiring up-to-date information, and complex queries involving context


## Introduction to Extracting Outputs from Large Language Models (LLMs)
Since the release of Large Language Models (LLMs) and advanced chat models, various techniques have emerged to extract desired outputs effectively. These methods either alter the model's behavior to align it with expectations or enhance the way queries are crafted to extract precise and relevant information.
Some widely used techniques include Retrieval Augmented Generation (RAG), Prompting, and Fine-Tuning. On MyScale, topics like RAG and fine-tuning have already been discussed in detail, covering two primary approaches: fine-tuning with OpenAI and Hugging Face platforms.

**Note:**
If you haven’t read our blogs on RAG and fine-tuning, we highly recommend checking them out before diving into today’s topic.

## Comparison of Techniques: Prompting, Fine-Tuning, and RAG
Today's discussion moves from exploration to comparison, highlighting the pros and cons of each technique. Understanding these differences will help you decide when and how to use these techniques effectively.

### 1. Prompt Engineering
Prompting is the most basic way to interact with an LLM. It works by giving the model instructions, which allows it to return specific information. This process, known as prompt engineering, is similar to asking the right questions to get the best answers. However, the model's responses are limited to what it learned during its original training, meaning it can only retrieve pre-learned information.

**Prompt Engineering Overview:**
- **User-Friendly**: No technical expertise is needed, making it accessible to a broad audience.
- **Quick Adjustments**: Prompts can be modified easily without retraining the model.
- **Cost-Efficient**: Minimal computational resources are required since it uses the pre-trained model.

**Pros:**
- Ease of Use: Anyone can use it without advanced technical skills.
- Cost-Effective: No extra computational cost beyond using the model.
- Flexible: Quick changes to prompts allow users to explore different responses.

**Cons:**
- Inconsistent Results: Output quality varies based on the phrasing of prompts.
- Limited Customization: Responses depend heavily on the model’s original knowledge.
- Outdated Information: Cannot provide up-to-date or niche information.

### 2. Fine-Tuning
Fine-tuning involves customizing an LLM by updating it with new information or specialized data, similar to installing a software update to unlock new features. This process enhances the model’s understanding of specific topics but requires significant computing power and time.

**Overview of Fine-Tuning:**
- **Customization**: Adapts the model to perform well in specific domains.
- **Improved Accuracy**: Responses become more relevant due to domain-specific data.
- **Adaptable**: Fine-tuned models handle niche topics and recent developments better.

**Pros:**
- Tailored Responses: Perfect for generating highly customized outputs.
- Accurate: Produces domain-specific and precise responses.
- Adaptability: Handles topics not covered in the original training.

**Cons:**
- High Cost: Requires significant computational resources.
- Technical Expertise: Involves deeper knowledge of machine learning.
- Data Requirements: Needs large, well-curated datasets for effective tuning.

### 3. Retrieval Augmented Generation (RAG)
RAG combines the capabilities of language models with external knowledge bases. When the model receives a query, it first retrieves relevant data from an external database, then generates the answer based on the combined information. It works like checking a library for the latest information before responding.

**Overview of RAG:**
- **Dynamic Information**: Retrieves up-to-date content for more relevant responses.
- **Balanced Approach**: Provides a middle ground between prompting and fine-tuning.
- **Contextual Relevance**: Enhances responses with additional background data.

**Pros:**
- Real-Time Information: Access to external data ensures relevance.
- Balanced Complexity: Easier than fine-tuning but more powerful than basic prompting.
- Contextualized Answers: Delivers more nuanced and informative outputs.

**Cons:**
- Complex Setup: Requires integration with retrieval systems.
- Resource Demands: Though lighter than fine-tuning, it still requires computational resources.
- Data Dependency: The quality of answers depends on the relevance of retrieved information.

**MyScale’s Role in RAG Systems**
The performance of a RAG system depends heavily on the vector database it uses for retrieval. MyScale offers competitive advantages with 50% lower costs and 3x better performance compared to other vector databases. Moreover, developers can access MyScale through simple SQL syntax, eliminating the need to learn additional tools or languages.


## Yannis write-up

### Introduction
In this presentation, we are going to talk about the large language models, or LLMs. We will start by introducing the 3 main customizations techniques of LLMs, which are Prompt Engineering, Fine Tuning and RAG. Each technique offers their own advantages and challenges, and we will compare them in detail as well. Lastly, we will explore how these techniques can be applied in different scenarios, in order to effectively enhance the performance of LLMs

### What is LLM​

LLM is a type of AI program that are trained on huge sets of data, allowing them to do a number of tasks. For example, models like GPT and BERT, can recognize and generate human-like text.​ And they can also been trained by more complex data to do other tasks, including writing in programming language, online search, or other analysis work.​ However, the responses generated by these out-of-the-box models can be very general because they rely solely on their initial training data.​

To meet more specific requirement, such as how long you want the response to be? Or how deep you want the response to go to?, that's when customization comes into play​

Therefore, Customizing LLM is crucial for the following reasons:​
To generate responses that are more accurate and relevant to a specific field, such as in legal or medical field.​
To improve performance on specialized tasks where Out-of-the-box models may not be sufficient to our need.​
Now I will pass to Evelyn to go into the detail of the customization techniques.
