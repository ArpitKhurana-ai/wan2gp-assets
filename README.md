# wan2gp-assets

Public mirror for **Wan 2.2 Animate LoRAs** used by the ProbeAI RunPod template.

This repo hosts GitHub **Releases** containing large binary artifacts (e.g., `.safetensors`) that would otherwise require a Hugging Face token. The app’s container downloads these files at boot from the published release URLs.

## Current release

- **Tag:** `v1.0`
- **Assets:**
  - `lightx2v_I2V_14B_480p_cfg_step_distill_rank64_bf16.safetensors` (~704 MB)
  - `Wan2.1_I2V_14B_FusionX_LoRA.safetensors` (~354 MB)

## How the app pulls these files

The runtime reads a `manifest.json` (baked or mounted into the container) and downloads each listed asset into the working `/workspace` directory:

```jsonc
{
  "items": [
    {
      "name": "lightx2v_....safetensors",
      "url": "https://github.com/ArpitKhurana-ai/wan2gp-assets/releases/download/v1.0/lightx2v_....safetensors",
      "dest": "loras/wan2.2-animate-lightning/lightx2v_....safetensors",
      "size_mb": 704
    }
  ]
}
