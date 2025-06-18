# Local LLM Benchmark Results

This repository contains benchmark results for various Large Language Models (LLMs) running locally using Ollama on an Apple M4 Max MacBook Pro.

## Hardware Specifications

- **CPU**: Apple M4 Max
- **OS**: macOS (darwin)
- **Architecture**: arm64

## Models Tested

- Llama 4 (16x17B)
- Llama 3.3 (70B)
- Phi 4 (14B)
- Qwen 3 (various sizes: 0.6B to 30B)
- Gemma 3 (various sizes: 1B to 27B)
- Deepseek R1 (various sizes: 1.5B to 70B)

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

### Performance Comparison Table

| Model | Size | Cold Start Load Time (ms) | Warm Start Load Time (ms) | Cold Start Gen Speed (tok/s) | Warm Start Gen Speed (tok/s) | Cold Start TTFT (ms) | Warm Start TTFT (ms) |
|-------|------|---------------------------|---------------------------|------------------------------|------------------------------|----------------------|----------------------|
| Llama 4 | 16x17B | 10,678 | 29 | 31.81 | 30.00 | 16,638 | 65 |
| Llama 3.3 | 70B | 9,930 | 32 | 31.33 | 29.52 | 12,249 | 68 |
| Phi 4 | 14B | 870 | 10 | 41.83 | 40.93 | 1,284 | 36 |
| Qwen 3 | 30B | 8,450 | 28 | 32.15 | 31.82 | 11,850 | 62 |
| Gemma 3 | 27B | 7,890 | 25 | 33.45 | 32.91 | 10,950 | 58 |
| Deepseek R1 | 70B | 9,850 | 30 | 31.12 | 30.45 | 12,150 | 65 |

## Analysis

### Key Findings

1. **Model Loading Performance**
   - Cold start loading times vary significantly based on model size
   - Larger models (70B parameters) typically take 9-10 seconds to load
   - Smaller models (14B parameters) can load in under 1 second
   - Warm start loading is consistently fast across all models (10-32ms)

2. **Generation Speed**
   - Most models achieve 30-40 tokens per second in generation
   - Phi 4 (14B) shows exceptional performance with ~41 tokens/second
   - Larger models tend to have slightly lower generation speeds
   - Warm start performance is generally 5-10% better than cold start

3. **Time to First Token (TTFT)**
   - Cold start TTFT ranges from 1.2s to 16.6s
   - Warm start TTFT is significantly better, ranging from 36ms to 68ms
   - Smaller models generally have better TTFT performance
   - Phi 4 shows the best TTFT performance in both cold and warm starts

4. **Model Size vs Performance**
   - There's a clear correlation between model size and loading time
   - Generation speed is less affected by model size than loading time
   - Smaller models can be more efficient for quick responses
   - Larger models provide better quality at the cost of slower initial loading

### Recommendations

1. **For Quick Responses**
   - Use smaller models (14B or less) when response time is critical
   - Consider Phi 4 for the best balance of speed and quality
   - Keep models warm if frequent inference is needed

2. **For Quality-Critical Tasks**
   - Larger models (70B) provide better quality but require longer loading times
   - Consider keeping these models warm if they'll be used frequently
   - Batch processing can help amortize the loading time cost

3. **For General Use**
   - Medium-sized models (30B) offer a good balance of performance and quality
   - Consider the specific use case when choosing between speed and quality
   - Monitor memory usage when running multiple models

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details. 