# Title: Create quantized model of llama2-7b-chat

Requirements: python3

- Clone the below 2 repos:

`git clone https://github.com/facebookresearch/llama.git`

`git clone https://github.com/ggerganov/llama.cpp.git`

`cd llama.cpp`

`make`

- Download the model from [https://huggingface.co/meta-llama/Llama-2-7b-chat-hf](https://huggingface.co/meta-llama/Llama-2-7b-chat-hf)
- Now we will convert the downloaded model(s). Its better to create a separate conda env or python virtual env to perform the same.

`cd llama.cpp`

`python3 -m pip install -r requirements.txt`

`python3 convert.py --outfile models/7B/ggml-model-f16.bin --outtype f16 ../../llama2/llama/llama-2-7b-chat --vocab-dir ../../llama2/llama`

`./quantize  ./models/7B/ggml-model-f16.bin ./models/7B/ggml-model-q4_0.bin q4_0`

`./main -m ./models/7B/ggml-model-q4_0.bin -n 1024 --repeat_penalty 1.0 --color -i -r "User:" -f ./prompts/chat-with-bob.txt`


# Credits:
- https://github.com/facebookresearch/llama
- https://github.com/ggerganov/llama.cpp
- https://medium.com/@karankakwani/build-and-run-llama2-llm-locally-a3b393c1570e

