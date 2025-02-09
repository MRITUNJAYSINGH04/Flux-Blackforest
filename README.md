# Flux-Blackforest
Usage
We provide a reference implementation of FLUX.1 [dev], as well as sampling code, in a dedicated github repository. Developers and creatives looking to build on top of FLUX.1 [dev] are encouraged to use this as a starting point.

API Endpoints
The FLUX.1 models are also available via API from the following sources

bfl.ml (currently FLUX.1 [pro])
replicate.com
fal.ai
mystic.ai
ComfyUI
FLUX.1 [dev] is also available in Comfy UI for local inference with a node-based workflow.

Diffusers
To use FLUX.1 [dev] with the 🧨 diffusers python library, first install or upgrade diffusers

pip install -U diffusers

Then you can use FluxPipeline to run the model

import torch
from diffusers import FluxPipeline

pipe = FluxPipeline.from_pretrained("black-forest-labs/FLUX.1-dev", torch_dtype=torch.bfloat16)
pipe.enable_model_cpu_offload() #save some VRAM by offloading the model to CPU. Remove this if you have enough GPU power

prompt = "A cat holding a sign that says hello world"
image = pipe(
    prompt,
    height=1024,
    width=1024,
    guidance_scale=3.5,
    num_inference_steps=50,
    max_sequence_length=512,
    generator=torch.Generator("cpu").manual_seed(0)
).images[0]
image.save("flux-dev.png")

To learn more check out the diffusers documentation

Limitations
This model is not intended or able to provide factual information.
As a statistical model this checkpoint might amplify existing societal biases.
The model may fail to generate output that matches the prompts.
Prompt following is heavily influenced by the prompting-style.
Out-of-Scope Use
The model and its derivatives may not be used

In any way that violates any applicable national, federal, state, local or international law or regulation.
For the purpose of exploiting, harming or attempting to exploit or harm minors in any way; including but not limited to the solicitation, creation, acquisition, or dissemination of child exploitative content.
To generate or disseminate verifiably false information and/or content with the purpose of harming others.
To generate or disseminate personal identifiable information that can be used to harm an individual.
To harass, abuse, threaten, stalk, or bully individuals or groups of individuals.
To create non-consensual nudity or illegal pornographic content.
For fully automated decision making that adversely impacts an individual's legal rights or otherwise creates or modifies a binding, enforceable obligation.
Generating or facilitating large-scale disinformation campaigns.
