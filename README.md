## Prototype Development for Image Generation Using the Stable Diffusion Model and Gradio Framework

### AIM:
To design and deploy a prototype application for image generation utilizing the Stable Diffusion model, integrated with the Gradio UI framework for interactive user engagement and evaluation.

### PROBLEM STATEMENT:
To design and develop a prototype application for generating images using the Stable Diffusion model. The application uses the Gradio framework to provide an interactive user interface where users can enter prompts, configure image generation parameters, and generate images.
### DESIGN STEPS:

#### STEP 1:
Import the required libraries and define the functions needed to communicate with the Stable Diffusion API and convert the generated image into a displayable format.
#### STEP 2:
Create the Gradio interface using gr.Blocks(). Add input fields for the prompt, negative prompt, inference steps, guidance scale, width, and height.
#### STEP 3:
Connect the Submit button with the image generation function and display the generated image in the output section.
### PROGRAM:
```
import gradio as gr 

#A helper function to convert the PIL image to base64 
# so you can send it to the API
def base64_to_pil(img_base64):
    base64_decoded = base64.b64decode(img_base64)
    byte_stream = io.BytesIO(base64_decoded)
    pil_image = Image.open(byte_stream)
    return pil_image

def generate(prompt, negative_prompt, steps, guidance, width, height):
    params = {
        "negative_prompt": negative_prompt,
        "num_inference_steps": steps,
        "guidance_scale": guidance,
        "width": width,
        "height": height
    }
    
    output = get_completion(prompt, params)
    pil_image = base64_to_pil(output)
    return pil_image
gr.close_all()
```
### OUTPUT:
<img width="1711" height="919" alt="image" src="https://github.com/user-attachments/assets/ac764b09-b490-49c0-86d7-b47f056098e6" />


### RESULT:
Thus, the Stable Diffusion image generation prototype was successfully designed and deployed using the Gradio UI framework.
