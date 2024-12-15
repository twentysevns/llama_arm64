# Description
That repo will explain, how to installing llama.cpp for arm64 device? then how to pull dataset (llm) over Ollama repo.

### Installing dependencies first
```
apt install build-essential bc cmake ccache git python3 python3-pip
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
### Then clone llm from Ollama repo, here the sample is qwen2.5:0.5b for other llm you can browse over ollama webapps.
```
uv run ollama_dl.py qwen2.5:0.5b
```
### Run it!
```
cd $HOME
./llama.cpp/build/bin/llama-cli -m ./ollama-dl/library-qwen2.5-0.5b/model-*.gguf -p "hello" -cnv -co
```

