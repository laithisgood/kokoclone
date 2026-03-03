# 🎙️ KokoClone

[![Hugging Face Space](https://img.shields.io/badge/🤗%20Hugging%20Face-Live%20Demo-blue)](https://huggingface.co/spaces/PatnaikAshish/kokoclone)
[![Hugging Face Models](https://img.shields.io/badge/🤗%20Models-Repository-orange)](https://huggingface.co/PatnaikAshish/kokoclone)
[![Python 3.12.12](https://img.shields.io/badge/Python-3.12.12-3776AB.svg?logo=python&logoColor=white)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-Apache_2.0-green.svg)](https://opensource.org/licenses/Apache-2.0)

**KokoClone** is a powerful, zero-shot multilingual Text-to-Speech (TTS) and Voice Cloning pipeline. 

By combining the natural, emotional prosody of **Kokoro-ONNX** with the zero-shot acoustic matching of the **Kanade Tokenizer**, KokoClone allows you to type text in almost any language and seamlessly speak it using *any* reference voice—all from a single 3-to-10 second audio sample.

---

## ✨ Features

- 🌍 **Multilingual Support:** Generate speech natively in English (`en`), Hindi (`hi`), French (`fr`), Japanese (`ja`), Chinese (`zh`), Italian (`it`), Portuguese (`pt`), and Spanish (`es`).
- 🎯 **Zero-Shot Voice Cloning:** No fine-tuning or training required. Just upload a short `.wav` file of a voice, and KokoClone maps its timbre onto the generated speech.
- 📦 **Smart Auto-Download:** No need to manually hunt down massive `.onnx` or `.bin` files. On your first run, KokoClone automatically fetches the required models from our [Hugging Face Model Repo](https://huggingface.co/PatnaikAshish/kokoclone) and places them in the right folders.
- 💻 **Hardware Agnostic:** Automatically detects and utilizes your GPU (CUDA) for blazing-fast inference, while falling back gracefully to CPU if you are on a standard laptop or Mac.
- 🎨 **Beautiful Web UI:** Comes with a built-in, fully styled Gradio interface (`app.py`) for easy testing.

---

## 🚀 Try it Live
Don't want to install it locally yet? Try the live web demo here:  
👉 **[KokoClone on Hugging Face Spaces](https://huggingface.co/spaces/PatnaikAshish/kokoclone)**

---

## 🛠️ Installation

We highly recommend using `conda` to keep your environment clean. KokoClone is tested and optimized for **Python 3.12.12**.

### 1. Clone the Repository
```bash
git clone [https://github.com/Ashish-Patnaik/kokoclone.git](https://github.com/Ashish-Patnaik/kokoclone.git)
cd kokoclone
```

2. Set Up the Conda Environment
```bash
conda create -n kokoclone python=3.12.12 -y
conda activate kokoclone
```

3. Install Dependencies
Because AI libraries handle hardware differently, choose the installation command that matches your machine:

### Option A: CPU Installation (Mac, standard laptops without Nvidia GPUs)
This prevents downloading gigabytes of useless CUDA drivers.

```bash
pip install torch torchaudio --index-url [https://download.pytorch.org/whl/cpu](https://download.pytorch.org/whl/cpu)
pip install -r requirements.txt
```

### Option B: GPU Installation (Windows/Linux with Nvidia GPUs)
This unlocks much faster generation times using your graphics card.

```bash
pip install -r requirements.txt
pip install kokoro-onnx[gpu]
```

## 🎮 Usage
KokoClone is designed to be as flexible as possible. You can run it via a Web UI, a Terminal command, or integrate it directly into your own Python projects.

1. The Web UI (Gradio)
To launch the beautiful, interactive web interface, simply run:

```bash
python app.py
```
This will automatically open a tab in your web browser. You can type text, select your language, and upload/record a reference voice directly in the UI.

2. Command Line Interface (CLI)
Need to run a quick generation from your terminal? Use cli.py:

```bash
python cli.py --text "Hello, this is my cloned voice." --lang en --ref reference_audio.wav --out cloned_voice.wav
```

3. Python API (For Developers)
Integrating KokoClone into your own code is incredibly simple. Check out inference.py for a working example, or use the snippet below:

```python
from core.cloner import KokoClone

# 1. Initialize (Auto-downloads models & detects CPU/GPU)
cloner = KokoClone()

# 2. Clone!
cloner.generate(
    text="Hello this is voice cloning by kokoclone",
    lang="en",
    reference_audio="your_target_voice.wav", 
    output_path="english_output.wav"
)
```

## 📂 Project Structure
1. app.py - The main Gradio Web UI application.

2. core/cloner.py - The hidden engine that handles model loading, inference, and smart downloading.

3. cli.py - Command-line interface tool.

4. inference.py - A clean example script for developers.

5. model/ & voice/ - Directories where the heavy AI weights are automatically downloaded and stored.

## 🙏 Acknowledgments
This project stands on the shoulders of giants. A huge thank you to the creators of:

1. Kokoro-ONNX for the lightning-fast TTS engine.

2. Kanade Tokenizer for the brilliant zero-shot voice conversion architecture.

## 📄 License
This project is open-source and licensed under the Apache 2.0 License. See the LICENSE file for more details.
