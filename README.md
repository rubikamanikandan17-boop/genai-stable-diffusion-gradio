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
with gr.Blocks() as demo:
    gr.Markdown("# Image Generation with Stable Diffusion")
    prompt = gr.Textbox(label="Your prompt")
    with gr.Row():
        with gr.Column():
            negative_prompt = gr.Textbox(label="Negative prompt")
            steps = gr.Slider(label="Inference Steps", minimum=1, maximum=100, value=25,
                      info="In many steps will the denoiser denoise the image?")
            guidance = gr.Slider(label="Guidance Scale", minimum=1, maximum=20, value=7,
                      info="Controls how much the text prompt influences the result")
            width = gr.Slider(label="Width", minimum=64, maximum=512, step=64, value=512)
            height = gr.Slider(label="Height", minimum=64, maximum=512, step=64, value=512)
            btn = gr.Button("Submit")
        with gr.Column():
            output = gr.Image(label="Result")

    btn.click(fn=generate, inputs=[prompt,negative_prompt,steps,guidance,width,height], outputs=[output])

demo.launch()


with gr.Blocks() as demo:
    gr.Markdown("# Image Generation with Stable Diffusion")
    with gr.Row():
        with gr.Column(scale=4):
            prompt = gr.Textbox(label="Your prompt") #Give prompt some real estate
        with gr.Column(scale=1, min_width=50):
            btn = gr.Button("Submit") #Submit button side by side!
    with gr.Accordion("Advanced options", open=False): #Let's hide the advanced options!
            negative_prompt = gr.Textbox(label="Negative prompt")
            with gr.Row():
                with gr.Column():
                    steps = gr.Slider(label="Inference Steps", minimum=1, maximum=100, value=25,
                      info="In many steps will the denoiser denoise the image?")
                    guidance = gr.Slider(label="Guidance Scale", minimum=1, maximum=20, value=7,
                      info="Controls how much the text prompt influences the result")
                with gr.Column():
                    width = gr.Slider(label="Width", minimum=64, maximum=512, step=64, value=512)
                    height = gr.Slider(label="Height", minimum=64, maximum=512, step=64, value=512)
    output = gr.Image(label="Result") #Move the output up too
            
    btn.click(fn=generate, inputs=[prompt,negative_prompt,steps,guidance,width,height], outputs=[output])

gr.close_all()
demo.launch()
```
### OUTPUT:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/09af4bc1-c1d5-40bc-9787-12b4817b3881" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5ef4189a-ff6f-49ae-a9e8-053fe5f10901" />

### RESULT:
Thus, the Stable Diffusion image generation prototype was successfully designed and deployed using the Gradio UI framework.
