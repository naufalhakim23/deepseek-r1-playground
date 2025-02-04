# VLLM Deepseek Playground for Google Colab

A streamlined implementation for running DeepSeek models using VLLM in Google Colab. This playground allows you to easily deploy and interact with DeepSeek-R1-Distill-Qwen-1.5B and other DeepSeek models in a Colab environment.

## 🚀 Features

- Easy deployment of DeepSeek models in Google Colab
- Real-time server monitoring and status checks
- Optimized for Colab's GPU environment
- Interactive interface for model interactions
- Memory-efficient model serving with VLLM
- Support for various DeepSeek model variants

## 📋 Prerequisites

Before running the playground, ensure you have:
- A Google account with access to Google Colab
- GPU runtime enabled in your Colab notebook

## 🛠️ Quick Start

1. **Open in Colab**
   ```
   [Add Colab badge/link here]
   ```

2. **Install Dependencies**
   ```python
   !pip install fastapi nest-asyncio pyngrok uvicorn

   !pip install vllm
   ```

3. **Launch the Server**
   ```python
   import subprocess
   model = 'deepseek-ai/DeepSeek-R1-Distill-Qwen-1.5B' # Specify your model here.

   
   vllm_process = subprocess.Popen([
       'vllm',
       'serve',
       'deepseek-ai/DeepSeek-R1-Distill-Qwen-1.5B',
       '--trust-remote-code',
       '--dtype', 'half',
       '--max-model-len', '16384',
       '--enable-chunked-prefill', 'false',
       '--tensor-parallel-size', '1'
   ], stdout=subprocess.PIPE, stderr=subprocess.PIPE, start_new_session=True)
   ```

4. **Monitor Server Status**
   ```python
   # [Include the monitoring code from previous implementation]
   ```

## ⚙️ Configuration Options

### Model Parameters
- `--dtype`: Set to 'half' for optimal Colab performance
- `--max-model-len`: Maximum sequence length (default: 16384)
- `--tensor-parallel-size`: GPU parallelism setting
- `--enable-chunked-prefill`: Prefill optimization setting

### Server Settings
- Default port: 8000
- Health check endpoint: `/health`
- Generate endpoint: `/generate`

## 🔍 Monitoring and Debugging

The playground includes built-in monitoring functionality:
- Real-time server status checks
- Output logging (stdout/stderr)
- Error handling and recovery
- Process management

## 📊 Performance Tips

1. **Memory Management**
   - Use `dtype=half` for efficient memory usage
   - Adjust `max-model-len` based on your needs
   - Monitor Colab GPU memory usage

2. **Optimization**
   - Batch requests when possible
   - Use appropriate temperature settings
   - Monitor token usage

## 🚧 Troubleshooting

Common issues and solutions:

1. **Server Won't Start**
   - Check GPU availability in Colab
   - Verify VLLM installation
   - Check memory usage

2. **Slow Response Times**
   - Reduce `max_tokens`
   - Adjust batch size
   - Check network connectivity

3. **Out of Memory**
   - Reduce model parameters
   - Clear Colab runtime
   - Restart runtime with GPU

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- [VLLM Project](https://github.com/vllm-project/vllm)
- [DeepSeek AI](https://github.com/deepseek-ai)
- Google Colab team

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues and pull requests.