# pollinations-n8n-image-demo

Minimal, ready‑to‑use n8n workflow for **image generation via the Pollinations API**.

## How to use

1. Download `My workflow.json` from this repo.  
2. In your n8n instance, open the editor and choose **Import from File**, then select `My workflow.json`.

## Set your Pollinations API key

Open the imported workflow and locate the HTTP Request node that sends the API call.  
In the `Authorization` header, replace the placeholder value and paste your own token directly after `Bearer`, so the final format looks like this:

```text
Authorization: Bearer YOUR_API_TOKEN
```

You can get your API key from the Pollinations dashboard at `https://enter.pollinations.ai` (API keys are created and managed there).

## Change prompt, model and size

In the **Body** of the HTTP Request node (JSON) you control what is generated.  
What to change:

- `prompt` - the text description of the image you want to generate.  
- `model` - the image model used for rendering, such as `flux` or another supported image model listed in the Pollinations image examples.
- `size` - the resolution of the final image; if your workflow stores this as `width` and `height` instead, simply adjust those values accordingly, since the original image node examples use explicit width and height dimensions.

### Example (single size field)

```json
{
  "prompt": "space cat",
  "model": "flux",
  "size": "1024x1024"
}
```

Run the workflow - n8n will request an image from Pollinations using your custom prompt, model and size and return it back into your automation.
