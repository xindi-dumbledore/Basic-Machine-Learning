#LLM 
Two common methods for helping LLMs to remember conversations are:
1. Conversation buffer: simply put the conversation history into the new prompt
2. Windowded conversation buffer: only keep conversation history in the last `k` interactions
3. Conversation summary: have a separate LLM to create conversation summary at the same time the conversation is developing. And inject this summary to the prompt. This way we can keep memory even from a long time ago.