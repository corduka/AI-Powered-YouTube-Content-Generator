# Pre-entrega-2-Fast-Prompting-en-Accion
import requests
import openai
import os
from PIL import Image

# OpenAI API key (replace with your actual key)
openai.api_key = "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"

# Function to generate image for YouTube thumbnails or content
def generate_image(prompt):
    client_response = openai.Image.create(
        model="dall-e-3",
        size="1024x1024",
        prompt=prompt,
        n=1,
        response_format="url"
    )
    print(client_response.data[0].url)

# Function to generate script for a video based on a prompt
def generate_script(prompt):
    client_response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[
            {"role": "user", "content": prompt}
        ]
    )
    print(client_response.choices[0].message["content"])

# Example function to generate YouTube video ideas for niches like motivational or fitness content
def generate_youtube_video_idea():
    video_prompt = "Create an interesting script for a motivational video about overcoming challenges in life. Keep it inspiring and positive, with a focus on actionable steps that people can take."
    generate_script(video_prompt)

# Example function to generate a thumbnail idea for the video
def generate_youtube_thumbnail():
    thumbnail_prompt = "Design a thumbnail for a YouTube motivational video with bold text saying 'Stay Strong' and a background image of a person running at sunrise."

