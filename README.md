# Qwen Image 2.1 — 16 ComfyUI workflows for a 6 GB graphics card

Every workflow here was run on a 6 GB graphics card with 16 GB of RAM. Each one has a **How to use** note inside: what to load, what to type, what to change.

## The files (ComfyUI 0.37 or newer)
| File | Folder | Size |
|---|---|---|
| [qwen_image_2.1_int8_convrot.safetensors](https://huggingface.co/Comfy-Org/Qwen-Image-2.1/resolve/main/diffusion_models/qwen_image_2.1_int8_convrot.safetensors) | `models/diffusion_models` | 7.3 GB |
| [qwen3vl_8b_int8_convrot.safetensors](https://huggingface.co/Comfy-Org/Qwen-Image-2.1/resolve/main/text_encoders/qwen3vl_8b_int8_convrot.safetensors) | `models/text_encoders` | 9.3 GB |
| [qwen_image_2.1_vae_bf16.safetensors](https://huggingface.co/Comfy-Org/Qwen-Image-2.1/resolve/main/vae/qwen_image_2.1_vae_bf16.safetensors) | `models/vae` | 0.7 GB |
| [p_qwen_image_2.1_8step_v0.1.safetensors](https://huggingface.co/PrunaAI/Pruna-Qwen-Image-2.1/blob/main/p_qwen_image_2.1_8step_v0.1.safetensors) (speed add-on) | `models/loras` | 0.3 GB |
| [bfs_head_v1.1_alternative_qwen_2.1.safetensors](https://huggingface.co/Alissonerdx/BFS-Best-Face-Swap/blob/main/bfs_head_v1.1_alternative_qwen_2.1.safetensors) (Identity Swap only; BFS by Alissonerdx, MIT) | `models/loras` | |

Custom nodes: [RES4LYF](https://github.com/ClownsharkBatwing/RES4LYF) (the `deis_2m` sampler; or switch the sampler to `euler`) and [ComfyUI-Pixaroma](https://workflows.pixaroma.com/help/) (Masked Edit and Expand use its Inpaint Crop/Stitch and Outpaint nodes). Install both from the ComfyUI Manager.

## The workflows
| Workflow | What it does | Time on 6 GB |
|---|---|---|
| Text to Image | a picture from a sentence, up to native 2K | ~32 s at 1 MP |
| One-Picture Edit | change a picture with one sentence: what to change + what to keep | ~54 s |
| Two-Picture Edit | picture 1 + a reference (product, outfit, style), with an output size | ~1 min |
| Multi-Picture Edit 5 | up to 5 pictures in one edit | ~1:40 |
| Masked Edit | paint over a part in the mask editor; only that part changes | ~35–55 s |
| Expand | pad to a new shape (16:9, 9:16…); the original goes back untouched | ~55 s |
| Upscale 2K | rebuild a small picture at ~2048 px | ~4 min |
| Pro Camera | a written camera move (close-up, low angle, from above) | ~55 s |
| Relight | neon, candle, golden hour, moonlight… only the light changes | ~55 s |
| Old Photo Restore | repair in black and white, then colour from the repaired photo | ~3 min |
| Transparent Sticker | a real transparent PNG from a sentence | ~32 s |
| Background Removal | cut-out with real transparency (glass stays see-through) | ~54 s |
| Character Sheet | front, three-quarter, side and back views on one sheet | ~1 min |
| Anime to Real Photo · by the creator | any cartoon or anime picture becomes an ordinary phone photo | ~1:35 |
| Outfit Swap · by the creator | picture 1 = the person, picture 2 = the outfit; the face and pose stay | ~1:10 |
| Identity Swap · by the creator | picture 1 = the body, picture 2 = the head (uses the BFS head LoRA) | ~1:10 |

## 6 GB settings already inside
8-bit model and text encoder · the 8-step speed add-on (CFG 1) · comfy kitchen attention · pictures scaled to 1 MP · for edits, the Qwen Image 2.1 Cache node on CPU / int8. The first run after starting ComfyUI is slower while the files load.

## Tips that came out of the tests
- Edits: say **what to change**, in detail, then **what to keep** (face, pose, angle).
- Camera moves: name the subject ("an extreme close-up of his face"). Turning around the subject barely works.
- Old photos: the speed add-on at full strength looks crunchy; the restore workflow uses it at 0.5 with 12 steps.
- People: start from a sharp, well-lit photo.
- Anime to Real: if the drawing hides the eyes (under a hat brim or bangs), add "keep the eyes hidden in that shadow" to the prompt, or the real version shows them.

## Licence
The workflow files in this repo are MIT (see LICENSE). The models and LoRAs they load have their own licences:
Qwen Image 2.1 is released under the [Qwen Research License](https://huggingface.co/Qwen/Qwen-Image-2.1/blob/main/LICENSE): research and non-commercial use. For client work or selling the pictures you need a separate licence from Qwen. Not legal advice.

