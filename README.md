# Description
This repo will explain, how to installing llama.cpp for arm64 device? then how to pull dataset (llm) over Ollama library?.

### Installing dependencies first
```
apt install build-essential bc cmake ccache git python3-pip
```
### Clone llamma.cpp repo & cd into it
```
git clone https://github.com/ggerganov/llama.cpp.git
cd llama.cpp
```
### Build & compile using cmake
```
cmake -B build
cmake --build build --config Release -j$(nproc)
cd $HOME
```
### Then clone the llm downloader & cd into it
```
https://github.com/akx/ollama-dl.git
cd ollama-dl
pip install uv
```
### Then clone llm from Ollama library, the sample here qwen2.5:0.5b for other llm you can browse over [ollama](https://ollama.com/library).
```
uv run ollama_dl.py qwen2.5:0.5b
```
### Run it!
```
cd $HOME
./llama.cpp/build/bin/llama-cli -m ./ollama-dl/library-qwen2.5-0.5b/model-*.gguf -p "hello" -cnv -co
```
### Also, here the sample benchmark that i've done work on it, both of all using is qwen2.5:0.5b llm.
```
Orange pi Zero 3 1GB h618 cpu  = 0.49 T/s
Tanix tx6 4/32GB h6 cpu        = 4.40 T/s
H96 Max X3 4/33GB s905x3 cpu   = 6.57 T/s
```
## Feel free to Stargaze :D
