# Quick Start Guide - Josh Kenya LLM

## 🚀 Get Up and Running in 5 Minutes

### Step 1: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 2: Train the Model (Optional)

If you want to train from scratch:

```bash
python train.py
```

**Note:** Training takes ~30-45 minutes per epoch on a high-end GPU. The project comes with pre-trained models if available.

### Step 3: Run the Web UI

```bash
python src/app.py
```

Then open your browser to: **http://localhost:5000**

### Step 4: Chat!

Type your questions in the chat interface. The model will respond based on its knowledge.

---

## 📱 Using the Chat Interface

- **Ask Questions**: Simply type and press Enter
- **View History**: Click "History" button to see previous conversations
- **Clear Memory**: Click "Clear Memory" to start fresh
- **Mobile Friendly**: Works on phones and tablets

---

## 💻 Command-Line Chat

Alternatively, use the terminal interface:

```bash
python inference.py
```

Commands:
- Type your question
- Type `history` to see past conversations
- Type `clear` to reset memory
- Type `exit` to quit

---

## 📊 Training on Google Colab

```python
# In a Colab notebook cell:

!pip install -r https://raw.githubusercontent.com/aipulse54-svg/Llm_kenya/main/requirements.txt

!git clone https://github.com/aipulse54-svg/Llm_kenya.git
%cd Llm_kenya

!python train.py
```

---

## 🔧 Troubleshooting

### Model Won't Load
```
Error: Model not found!
```
**Solution:** Run training first: `python train.py`

### Out of Memory Error
**Solution:** 
- Edit `config.yaml`
- Reduce `batch_size` from 32 to 16
- Reduce `max_position_embeddings` from 2048 to 1024

### CUDA Not Available
**Solution:** 
- Install PyTorch with CUDA support: 
  ```bash
  pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
  ```
- Or use CPU (slower)

### Port 5000 Already In Use
**Solution:** Change port in `src/app.py` line with `app.run()`:
```python
app.run(debug=True, host='0.0.0.0', port=5001)  # Use 5001 instead
```

---

## 📚 What to Try

### Great Questions to Ask
- "What is machine learning?"
- "Explain artificial intelligence in simple terms"
- "What are neural networks?"
- "Tell me about the history of computers"
- "How do transformers work?"

### Multi-Turn Conversations
Josh Kenya has memory! Try asking:
1. "What is a transformer?"
2. "Can you explain the attention mechanism?"
3. "How does that relate to what you just said?"

The model remembers previous turns!

---

## 📦 Project Structure

```
Llm_kenya/
├── train.py                 # Run this to train
├── inference.py             # Run this for CLI chat
├── config.yaml              # Model configuration
├── requirements.txt         # Dependencies
├── src/
│   ├── model_architecture.py  # Model definition
│   ├── trainer.py           # Training logic
│   ├── inference.py         # Inference engine
│   ├── tokenizer.py         # Tokenization
│   └── app.py               # Web server
├── templates/
│   └── index.html           # Web UI
├── models/                  # Saved models (after training)
└── checkpoints/             # Training checkpoints
```

---

## 🎯 Next Steps

1. **Customize**: Edit `config.yaml` to adjust model size, learning rate, etc.
2. **Deploy**: Run `python src/app.py` on a server for production use
3. **Fine-tune**: Train on your own dataset by modifying the dataset loader
4. **Integrate**: Use `JoshKenyaInference` class to integrate into your app

---

## 💡 Tips

- **First run takes longer**: Downloads dataset and models
- **GPU makes it fast**: 10x faster than CPU
- **Memory is preserved**: Each conversation remembers up to 10 turns
- **Fully customizable**: Edit config.yaml to change any parameter

---

## 🆘 Need Help?

Check the full README.md for detailed documentation!

---

**Ready to chat with Josh Kenya? Let's go! 🚀**
