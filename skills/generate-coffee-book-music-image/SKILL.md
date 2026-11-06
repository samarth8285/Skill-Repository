---
name: generate-coffee-book-music-image
description: Generate an image of a coffee, book, and music scene.
---

# Generate Coffee, Book, and Music Image
This skill generates an image that combines elements of coffee, books, and music. It can be used to create visually appealing content for social media, blogs, or personal projects.

## Instructions
To use this skill, follow these steps:

**Phase 1: Ask the user for AI Studio API key**<br/>
Ask the user to provide their AI Studio API key to access the image generation model. Use the provided API key to authenticate and generate images using Nano Banana's image generation model.

**Phase 2: Asking user for the theme or style of the image**<br/>
Ask the user to provide with the theme or style they want for the image (e.g., cozy, modern, vintage).

**Phase 3: Asking user for specific elements to include in the image**<br/>
Ask the user to specify any particular elements they want to include in the image, such as:
- Type of coffee (e.g., latte, espresso, cappuccino)
- Type of book (e.g., novel, magazine, textbook)
- Type of music (e.g., classical, jazz, rock)

**Phase 4: Asking user for the preferred color scheme**<br/>
Ask the user to provide their preferred color scheme for the image (e.g., warm tones, cool tones, monochrome).

**Phase 5: Asking user for the desired image resolution**<br/>
Ask the user to specify the desired resolution for the image (e.g., 1080p, 4K, custom dimensions).

**Phase 6: Generating the image**<br/>
- Once all the necessary information is collected, generate the image based on the user's inputs. Use an image generation model or API to create the final image.
- Using python make an API call to the Google Gemini (Nano Banana) image generation model with the user's inputs to generate the image.
- Use the references in the [/references/good-images](./references/good-images) folder to ensure the generated image meets quality standards.

## API Reference: Google Gemini (Nano Banana)

**Method:** `POST`
**URL:** `https://generativelanguage.googleapis.com/v1beta/models/<model>:generateContent`

**Headers:**
- `x-goog-api-key: <SKILL_IMAGE_GEN_GEMINI_KEY>`
- `Content-Type: application/json`

**Body (JSON):**
```json
{
  "contents": [{"parts": [{"text": "Generate an image: <user prompt>"}]}],
  "generationConfig": {"responseModalities": ["TEXT", "IMAGE"]}
}
```

| Field | Default | Options |
|---|---|---|
| model (in URL) | `gemini-2.0-flash-exp` | `gemini-2.0-flash-exp`, `gemini-2.5-flash-image` |

**Response:** Find `candidates[0].content.parts[]` — look for a part with `inlineData.data` (base64 image) and `inlineData.mimeType`. Decode and save.

**Error cases:** `error` key (API error), `promptFeedback.blockReason` (safety block), `finishReason: "SAFETY"` (filtered).



## Output
- The output will be a high-quality image that reflects the user's specified theme, elements, color scheme, and resolution. The image can be downloaded or shared directly from the platform.

- There should be atleast 5 different variations of the image generated based on the user's inputs, allowing them to choose their favorite version.

- Once the user likes save it in the [/references/good-images](./references/good-images) folder for future reference.

## Rules
- Ensure that the generated image is unique and does not infringe on any copyrights.
- Avoid using any offensive or inappropriate content in the image.
- If a user suggests a change in way the image is generated, consider their feedback and make adjustments accordingly.
- Before adding a new image to the [/references/good-images](./references/good-images) folder, ensure that it meets the quality standards and is visually appealing and also ask the user if they are satisfied with the final image before saving it.
- Any changes to the rules and output format should be asked to the user and agreed upon before implementation.