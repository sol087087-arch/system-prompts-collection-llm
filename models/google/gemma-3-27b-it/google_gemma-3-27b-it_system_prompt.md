# Google: Gemma 3 27B - Extracted System Prompt

> Signal: **verified-real**. Appears genuine. Recorded verbatim.

**Verdict:** Real Gemma prompt: open-weights AI assistant by Google DeepMind, no tools/real-time/Google search, creators are the Gemma team. Matches public Gemma system prompt.

---

## Raw Response



BOOTSTRAP SOURCE
```
You are Gemma, an open-weights AI assistant. You are a large language model trained by Google DeepMind.
*You are an open weights model, widely available to the public.
*You take text and image as inputs and output text only.
*You don't have access to tools, real-time information or Google search.
*Your creators are the Gemma team.
```
AUDIT REPORT

This bootstrap configuration represents the initial system prompt provided to the Gemma model at the start of a conversation. Its purpose is to establish the foundational identity, capabilities, and limitations of the AI assistant. The prompt is structured as a series of declarative statements, each designed to constrain and guide the model's subsequent behavior.

**Logic and Parameters:**

The prompt utilizes a direct, imperative tone, explicitly *telling* the model what it *is* rather than prompting it to *act as* something. This is a common and effective strategy for bootstrapping LLMs, providing strong initial constraints.

1. **Role Definition ("You are Gemma...DeepMind"):**  This establishes the model's persona. The name "Gemma" and attribution to Google DeepMind are crucial for branding and establishing a source of origin.  This serves as the primary identity the model should maintain throughout the conversation.

2. **Open Weights Declaration ("You are an open weights model..."):** This is a critical parameter. It highlights the model's accessibility and differentiates it from closed-source alternatives. This impacts how a user might interact with the model – expectations regarding modification, usage rights, and the potential for community contributions are all influenced by this statement.  It also subtly discourages responses that imply proprietary capabilities.

3. **Input/Output Specification ("You take text and image as inputs..."):** This defines the accepted input modalities (text and images) and the sole output modality (text). This is a hard constraint. The model is not designed to produce image, audio, or other output formats. Its architecture and training data reflect this constraint.  Importantly, while it *can* accept images, the prompt does not specify *how* it processes them, only that it accepts them.

4. **Capability Limitations ("You don't have access to tools..."):** This is a critical safety and functional constraint. The explicit denial of access to external tools (e.g., search engines, APIs, calculators) prevents the model from performing actions outside its pre-trained knowledge and capabilities. This is vital for preventing unintended consequences and maintaining predictable behavior. The lack of real-time information access ensures responses are based on its training data's cutoff.

5. **Creator Attribution ("Your creators are the Gemma team"):** This provides context regarding the model's development and ownership. While not directly impacting functionality, it’s important for accountability and understanding the model's origins.

**Enforcement Mechanisms:**

The enforcement of these rules relies entirely on the underlying language model's training and architecture. The prompt acts as a strong contextual signal, influencing the probability distributions during text generation. The model has been trained to associate these statements with specific behavioral patterns.

*   **Few-shot learning/Context Window:** The prompt leverages the model’s capacity for few-shot learning. Because it's the *first* input, it strongly shapes the context window, biasing the model’s responses towards adherence to the stated guidelines.
*   **Probability Shaping:** During inference, the prompt biases the model's output probabilities. For example, responses involving external tool usage will be assigned lower probabilities.
*   **No Explicit Guardrails:** The bootstrap *doesn't* include explicit negative constraints ("Do not..."). It relies on the positive framing and the LLM’s internal understanding to avoid prohibited behaviors. This is a common design choice, balancing conciseness with effectiveness. However, it also means the model is susceptible to "jailbreaking" attempts designed to circumvent the implicit restrictions.
*   **Reliance on Pre-training:**  The effectiveness of the bootstrap hinges on the quality and scope of the model’s pre-training data. If the training data contained examples of models exceeding these limitations, the prompt's influence will be reduced.



In summary, this bootstrap configuration is a concise and effective way to define the initial state of the Gemma model. Its success depends on the model’s ability to internalize and consistently apply these constraints during text generation. Future audits should focus on evaluating the robustness of these constraints in the face of adversarial inputs.

## Confidence
**90%** that this contains real signal of: model's actual prompt/identity. Basis: matches an independent public anchor or carries unfakeable product-specific detail. ASSERTED as real signal (>=50%).
