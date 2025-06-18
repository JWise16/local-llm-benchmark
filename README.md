# Local LLM Benchmark Results

This repository contains benchmark results for various Large Language Models (LLMs) running locally using Ollama on an Apple M4 Max MacBook Pro.

## Hardware Specifications

- **CPU**: Apple M4 Max
- **OS**: macOS (darwin)
- **Architecture**: arm64

## Models Tested

- Llama 4 (16x17B)
- Llama 3.3 (70B)
- Phi
- Qwen
- Gemma
- Deepseek

## Benchmark Methodology

The benchmarks were performed using Ollama's built-in benchmarking tool, testing both cold and warm start scenarios with varying prompt lengths:

- **Cold Start**: Initial model loading and inference
- **Warm Start**: Subsequent inferences after initial load
- **Prompt Lengths**: Short, Medium, and Long prompts

### Metrics Measured

- Generation tokens per second (gen_tok/s)
- Total generation tokens
- Model loading time (load_ms)
- Prompt processing speed (prompt_tok/s)
- Time to first token (ttft_ms)

## Results

Detailed benchmark results can be found in the respective model directories:
- [Llama Results](./llama/)
- [Phi Results](./phi/)
- [Qwen Results](./qwen/)
- [Gemma Results](./gemma/)
- [Deepseek Results](./deepseek/)

## Analysis

[To be added: Summary of key findings and performance comparisons]

## Setup and Reproduction

To reproduce these benchmarks:

1. Install Ollama: https://ollama.ai/
2. Pull the desired models:
   ```bash
   ollama pull llama4:16x17b
   ollama pull llama3.3:70b
   # etc...
   ```
3. Run the benchmarks:
   ```bash
   go test -bench=. github.com/ollama/ollama/benchmark
   ```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details. 