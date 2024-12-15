# Description
This repo will explain, how to installing llama.cpp for arm64 device? then how to pull dataset (LLM) over Ollama library?.


Installing dependencies first.
```
apt install build-essential bc cmake ccache git python3-pip
```
Clone llamma.cpp repo & cd into it.
```
git clone https://github.com/ggerganov/llama.cpp.git
cd llama.cpp
```
Build & compile using cmake.
```
cmake -B build
cmake --build build --config Release -j$(nproc)
cd $HOME
```
Then clone the LLM downloader & cd into it.
```
https://github.com/akx/ollama-dl.git
cd ollama-dl
pip install uv
```
Clone LLM from Ollama library, the sample here qwen2.5:0.5b for other LLM you can browse over [Ollama](https://ollama.com/library).
```
uv run ollama_dl.py qwen2.5:0.5b
```
Run it!.
```
cd $HOME
./llama.cpp/build/bin/llama-cli -m ./ollama-dl/library-qwen2.5-0.5b/model-*.gguf -p "hello" -cnv -co
```
Also, here the sample benchmark that i've done on it, both of all using qwen2.5:0.5b LLM.
```
Orange Pi Zero 3 1GB H618 CPU  = 0.49 T/s
Tanix Tx6 4/32GB H6 CPU        = 4.40 T/s
H96 Max X3 4/32GB S905X3 CPU   = 6.57 T/s
```
## Feel free to Stargaze :D
