# Autonomous disproofs of the sum-product conjecture over $\mathbb{R}$ with GPT-5.5 Pro

This repository contains the code and AI-generated transcripts/proofs that accompany the [paper](https://doi.org/10.48550/arXiv.2607.20525). It presents a simple autonomous agent that robustly and efficiently disproves the Erdős–Szemerédi sum-product conjecture over $\mathbb{R}$ using GPT-5.5 Pro.

## Repository contents

- `sum-product.pdf`: The paper.
- `run.py`: The main script that runs the agent via the GPT-5.5 Pro API. It implements a problem-agnostic, three-round prompting pipeline (proof-plan proposal, proof construction, and review) to autonomously generate proofs.
- `md2html.py`: A utility script for converting math-heavy model outputs into readable HTML using MathJax.
- `outputs/`: A directory containing the outputs from 8 independent trials. The agent generated correct proofs in 7 of the 8 trials. The directory includes:
  - `transcript-$i$.html`: The complete conversation log, including all prompts and the model's outputs in all rounds.
  - `proof-$i$.html`: The model's final response containing the proof.
  
  Here, $i=1,2,\dots,8$ is the trial index. In trial 2, the agent did not complete the proof but correctly identified an unresolved gap in its argument; the complete log is available as `transcript-2.html`, but there is no `proof-2.html`.
  
  *Note: These files are obtained by converting the math-heavy raw model outputs into a more human-readable format. The conversion is strictly limited to formatting and done via `md2html.py` and a fixed piece of code inside `run.py`. Because GitHub displays HTML files as plain text by default, please download this repository ("Code" > "Download ZIP") and open the `.html` files in your local web browser to view the properly rendered math.*

## How to run

The pipeline requires standard Python packages and the official `openai` Python SDK.

To run the agent yourself:

1. Configure your OpenAI API key. You can do this by setting the environment variable:
   ```bash
   export OPENAI_API_KEY="your-api-key-here"
   ```
   Alternatively, you can enter your API key directly in the `API_KEY` variable near the top of `run.py`.

2. Run the script:
   ```bash
   python run.py
   ```

Running `run.py` produces three files in the `output/` directory:
- `raw_outputs.json`: The full, raw API responses.
- `transcript.html`: The complete conversation log.
- `proof.html`: The model's final response.

*Note: `proof.html` and `transcript.html` use exactly the same formatting as the corresponding HTML files in the repository's `outputs/` directory.*

`run.py` uses a checkpointing system. If the script is interrupted or fails due to network issues, running it again automatically resumes execution from the last completed round without losing progress.

## Citation

```bibtex
@unpublished{huang2026autonomous,
      title={Autonomous disproofs of the sum-product conjecture over $\mathbb{R}$ with {GPT-5.5 Pro}},
      author={Yichen Huang},
      note={arXiv:2607.20525}
}
```

## License

Please refer to the `LICENSE` file for detailed licensing information.
