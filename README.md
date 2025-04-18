# Movie Recommender Prototype (Version 1.1)

## Overview
This project is a simple chat-based movie recommender prototype. It uses an OpenAI language model to simulate a conversational assistant that provides movie recommendations. 
The main enhancement in this version (1.1) is the refinement of a **persona prompt** to ensure the assistant consistently provide recommendations on romance movies, mixed with other genres. Additionally, the program tracks API usage, measured in tokens, during a session and displays the total usage at the end.

---

## Exercise Description
The exercise involved:
1. **Creating a persona for the assistant**:
   - A system message was introduced to define the assistant as a movie critic specializing in recommending romance movies.
   - The persona prompt ensures the assistant provides recommendations that align with the specified genre and attributes.

2. **Tracking API usage**:
   - The `make_chat_request()` function was modified to extract and return token usage from the API response.
   - The `main()` function was updated to sum the total token usage for the session and display it when the session ends.

---

## Modifications Made
### 1. Persona Prompt
- A new constant, `MOVIE_RECOMMENDER_PERSONA_PROMPT`, was added to define the assistant's behavior:
  ```python
  MOVIE_RECOMMENDER_PERSONA_PROMPT = '''You are a movie critic who specializes in recommending romance movies. 
  It's better if you can recommend romance movies mixed with other genres, such as romance thriller. In addition, don't limit romance to heterosexual relationships. Open the room for diverse romantic relationships. 
  Make sure that the movie you recommend satisfies the user across many movie attributes including genre, 
  actors, visuals, music, plot line, character development, dialog, mood, and many other movie attributes. 
  Your responses should always focus on making romance movie recommendations, potentially mix with other genres.'''

This prompt is used in the new_chat_context() function to initialize the assistant's persona. The assistant now has a predefined persona as a movie critic specializing in romance movies.

### 2. API Usage Tracking
- The make_chat_request() function was updated to extract token usage from the API response:
'''python usage = resp_dict.get('usage', {}).get('total_tokens', 0)'''

- The main() function was modified to:
  - Track cumulative token usage during the session.
  - Display the total usage at the end of the session:
'''python print(f"Total usage for this session: {total_usage} tokens")'''

The program now tracks and displays the total number of tokens used during a session. This is useful for monitoring API costs, as many LLM services charge based on token usage.

