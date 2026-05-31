# 🤖 Josh Kenya LLM

A production-ready 50M parameter language model with long conversation memory, built entirely in **Pure Python with NumPy**, and trainable on free GPU resources.

### 📋 Features

- **50M Parameter Transformer Model**: Efficient architecture optimized for consumer GPUs
- **Long Conversation Memory**: Maintains up to 10 conversation turns with context window of 4096 tokens
- **Web UI**: Beautiful Flask-based chat interface with real-time interaction
- **Free GPU Training**: Trainable on Google Colab, local GPUs, or CPU
- **Model Persistence**: Saves model weights and configuration for inference
- **Production Ready**: Proper error handling, logging, and inference optimization
- **WikiText-2 Training**: Trained on the popular WikiText-2 dataset from Hugging Face

### 🏗️ Architecture

#### Model Components

1. **Rotary Positional Embeddings (RoPE)**: Modern position encoding for better generalization
2. **Multi-Head Attention**: 12 attention heads with causal masking for autoregressive generation
3. **Feed-Forward Network**: SwiGLU activation functions for improved performance
4. **Layer Normalization**: Pre-normalization architecture for stable training

#### Model Specs

```
Total Parameters: 50M
Hidden Size: 768
Attention Heads: 12
Layers: 12
Vocabulary Size: 50,257
Max Sequence Length: 2,048
```

### 📦 Installation

```bash
# Clone repository
git clone https://github.com/aipulse54-svg/Llm_kenya.git
cd Llm_kenya

# Install dependencies
pip install -r requirements.txt

# Optional: For CUDA support
# pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```

### 🎓 Training

#### Quick Start

```python
from src.trainer import LLMTrainer

# Initialize trainer
trainer = LLMTrainer(config_path='config.yaml', device='cuda')

# Train model
trainer.train()
```

#### Training on Google Colab

1. Open: `Colab_Training_Notebook.ipynb`
2. Click "Open in Colab"
3. Set Runtime to GPU (T4)
4. Run all cells
5. Download trained model

#### Configuration

Edit `config.yaml` to customize training:

```yaml
training:
  batch_size: 32           # Batch size per GPU
  learning_rate: 5e-4      # Learning rate
  num_epochs: 3            # Number of epochs
  gradient_accumulation_steps: 4
  max_grad_norm: 1.0

dataset:
  name: "wikitext"         # Dataset name
  config: "wikitext-2"     # Dataset config
  max_seq_length: 2048     # Sequence length
```

### 🚀 Inference

#### Chat Interface

```python
from src.inference import JoshKenyaInference

# Load model
model = JoshKenyaInference(model_dir='models', device='cuda')

# Answer questions
response = model.answer_question("What is machine learning?")
print(response)

# Check model info
info = model.get_model_info()
print(f"Model: {info['name']} ({info['parameters_millions']})")  
```

#### Web UI

```bash
# Start Flask server
python src/app.py

# Open browser to http://localhost:5000
```

Features:
- Real-time chat interface
- Conversation history (10 turns)
- Clear memory function
- Model information display
- Responsive design for mobile

### 💾 Model Files

After training, the following files are saved:

```
models/
├── josh_kenya_lm.pt      # Model weights
├── config.yaml           # Model configuration
└── tokenizer.json        # Tokenizer (if applicable)

checkpoints/
├── checkpoint_epoch_0.pt
├── checkpoint_epoch_1.pt
└── checkpoint_epoch_2.pt
```

### 🔧 Hardware Requirements

#### Minimum
- GPU: 8GB VRAM (RTX 2060, GTX 1080 Ti, etc.)
- CPU: 4 cores
- RAM: 16GB
- Storage: 10GB

#### Recommended
- GPU: 12GB+ VRAM (RTX 3060, RTX 3080, etc.)
- CPU: 8+ cores
- RAM: 32GB
- Storage: 20GB SSD

#### CPU-Only
- CPU: 16+ cores
- RAM: 64GB+
- Training time: ~8 hours per epoch

### 🎯 Conversation Memory

The model maintains context from previous conversations:

```python
# Memory is automatically managed
memory = model.memory

# Access history
history = memory.get_history()
for turn in history:
    print(f"User: {turn['user']}")
    print(f"Josh Kenya: {turn['assistant']}")

# Clear memory
memory.clear()
```

### 📝 Example Usage

#### Training
```python
from src.trainer import LLMTrainer

trainer = LLMTrainer()
trainer.train()  # Trains for 3 epochs by default
```

#### Inference
```python
from src.inference import JoshKenyaInference

# Initialize
model = JoshKenyaInference()

# Single question
answer = model.answer_question("Tell me about AI")

# Multiple turns (memory preserved)
answer1 = model.answer_question("What is machine learning?")
answer2 = model.answer_question("Can you explain it more simply?")  # Remembers context
```

#### Web Interface
```bash
python src/app.py
```

### 🤝 Architecture Details

#### Attention Mechanism
- Uses Rotary Positional Embeddings for better generalization
- Causal masking for autoregressive generation
- Dropout for regularization

#### Generation
- Top-k sampling: Filter top-50 tokens
- Top-p (nucleus) sampling: 0.9 probability mass
- Temperature scaling: 0.7 by default
- Repetition penalty: 1.2 to reduce repetition

#### Memory System
- Last 10 conversation turns stored
- 4096 token context window
- Automatic turn management

### 🐛 Troubleshooting

**Out of Memory Error**
- Reduce batch size in config.yaml
- Reduce max_seq_length
- Use gradient accumulation

**Slow Training**
- Ensure CUDA is available: `torch.cuda.is_available()`
- Use mixed precision training (future update)
- Reduce validation frequency

**Model Not Found**
- Ensure you've completed training: `python train.py`
- Check that models/ directory exists

### 📚 Dependencies

- **PyTorch**: Deep learning framework
- **Transformers**: Hugging Face library for datasets
- **Datasets**: Download WikiText-2 training data
- **Flask**: Web framework
- **NumPy**: Numerical computing

### 📄 License

MIT License - See LICENSE file for details

### 🙏 Acknowledgments

- Transformer architecture based on "Attention is All You Need"
- RoPE embeddings from Su et al.
- WikiText-2 dataset from Salesforce
- Hugging Face for the Transformers library

### 📧 Support

For issues or questions:
1. Check troubleshooting section
2. Review config.yaml settings
3. Check model directory exists
4. Verify dependencies installed

---

**Happy Chatting with Josh Kenya! 🚀**

Built with ❤️ for efficient LLM training and inference
