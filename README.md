# Smart Recipe: Image-to-Recipe Generation with Dietary Preferences

Smart Recipe is an AI-powered application that lets users upload a **food image** and receive a **personalized recipe** tailored to their **dietary preferences** (e.g., no nuts, low sugar, low fat, etc.). Unlike generic AI-generated recipes, this system combines **trusted data sources**, **vector search**, and **fine-tuned models** to ensure **reliable and customized** recipe results.

---

## Features

* **Food Identification from Images** using Gemini Vision
* **Trusted Ingredient Source** via EDAMAM API (900,000+ verified dishes)
* **Diet-Aware Ingredient Search** using FAISS Vector DB
* **Recipe Generation** using fine-tuned T5 model on RecipeNLG (2.5M+ recipes)
* **Human-Friendly Formatting** using GPT-4 for final output
* **Streamlit UI** for real-time interaction

---

## How It Works

### 1. Image Upload & Dish Detection

The user uploads a food image. It is sent to **Gemini Vision** to detect the most likely dish name.

### 2. Ingredient Retrieval from EDAMAM

Using the detected dish name, the **EDAMAM API** is queried to retrieve:

* Ingredient lists
* Nutritional information
* 10–15 variations of the dish

> *Note: EDAMAM does not provide cooking instructions.*

### 3. Store & Search with FAISS

The ingredient variations are converted into **vector embeddings** and stored in a **FAISS** database for similarity-based filtering.

### 4. Personalized Dietary Filtering

When users specify dietary preferences (e.g., "no dairy", "low sugar"), relevant ingredient combinations are retrieved from FAISS.

### 5. Recipe Generation with T5

Filtered ingredients are passed into a **T5 model**, fine-tuned on **RecipeNLG**, to generate a structured recipe.

### 6. Final Recipe Enhancement with GPT-4

The raw recipe is refined using **GPT-4** to ensure clarity, coherence, and easy-to-follow instructions.

### 7. Display on Streamlit

The complete personalized recipe is presented to the user via a **Streamlit interface**.

---

## Tech Stack

| Component             | Tool/Library                 |
| --------------------- | ---------------------------- |
| Image Recognition     | Gemini Vision                |
| Ingredient Database   | EDAMAM API                   |
| Vector Storage/Search | FAISS                        |
| Recipe Generation     | T5 (fine-tuned on RecipeNLG) |
| Text Refinement       | GPT-4                        |
| Frontend UI           | Streamlit                    |

---

## Notes

* EDAMAM API is used only for **ingredients** and **nutrition**—not instructions.
* Recipes are generated **from scratch** using retrieved ingredients and a fine-tuned T5 model.
* GPT-4 is used only for **polishing the output**, not generating the recipe itself.
* FAISS enables fast filtering of ingredient variations based on dietary needs.

---

## Acknowledgements

* [EDAMAM API](https://developer.edamam.com/)
* [RecipeNLG Dataset](https://recipenlg.cs.put.poznan.pl/)
* [FAISS by Facebook AI](https://github.com/facebookresearch/faiss)
* [OpenAI GPT-4](https://platform.openai.com/)
* [Gemini by Google DeepMind](https://deepmind.google/technologies/gemini)
