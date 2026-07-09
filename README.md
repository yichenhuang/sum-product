# Autonomous Disproofs of the Sum-Product Conjecture over $\mathbb{R}$ with GPT-5.5 Pro

This repository contains the scripts and AI-generated transcripts/proofs that accompany the paper. It presents a simple autonomous agent that robustly and efficiently disproves the Erdős–Szemerédi sum-product conjecture over $\mathbb{R}$ using GPT-5.5 Pro.

## Repository Contents

- `sum-product.pdf`: The paper.
- `run.py`: The core script that interacts with the GPT-5.5 Pro API. It uses a problem-agnostic, three-round prompting pipeline (proof-plan proposal, proof construction, and review) to autonomously generate the proofs.
- `md2html.py`: A utility script used to convert the math-heavy model outputs into readable HTML formats using MathJax.
- `outputs/`: A directory containing 8 independent trials. The agent successfully generated a correct proof in 7 out of the 8 trials. This directory includes:
  - `transcript-$i$.html`: The complete conversation log, including all prompts and the model's outputs in all rounds.
  - `proof-$i$.html`: The model's final response containing the proof in its finalized form.
  
  Here, $i \in \{1, 2, \dots, 8\}$ is the trial index. Trial 2 did not complete the proof but correctly identified its own unresolved gap; the complete log is available as `transcript-2.html`, but there is no `proof-2.html`.
  
  *Note: These files are obtained by converting the raw model outputs into a more human-readable format. This conversion is purely formatting-based to make the math-heavy raw outputs easier to read, done via `md2html.py` and a fixed piece of code inside `run.py`. Because GitHub displays HTML files as plain text by default, please download this repository ("Code" > "Download ZIP") and open the `.html` files in your local web browser to view the properly rendered math.*

## How to Run

The core pipeline requires standard Python packages and the official `openai` Python SDK.

To execute the agent yourself:

1. Configure your OpenAI API key. You can do this by setting the environment variable:
   ```bash
   export OPENAI_API_KEY="your-api-key-here"
   ```
   Alternatively, you can edit the `API_KEY` placeholder directly at the top of `run.py`.

2. Run the script:
   ```bash
   python run.py
   ```

Executing `run.py` will produce three files in the `output/` directory:
- `raw_outputs.json`: The full, raw API responses.
- `transcript.html`: The complete conversation log.
- `proof.html`: The model's final response.

*Note: `proof.html` and `transcript.html` share the exact same format as the HTML files provided in the `outputs/` folder of this repository. Additionally, `run.py` uses a checkpointing system. If the script is interrupted or fails due to network issues, running it again will automatically resume execution from the last completed round without losing progress.*

## License

Please refer to the `LICENSE` file for detailed licensing information.
