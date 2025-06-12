Handwritten text recognition with in-context few-shot learning. 

# Guidelines
For any image depicting handwritten text, 
1. fetch $n$ similar images,
2. prompt a model such as [BLIP](https://huggingface.co/docs/transformers/en/model_doc/blip) with task instructions and the similar images along with their machine-readable text,
3. let it decode the text of that line,
4. assess using [CER and WER](https://pypi.org/project/pywer/) by comparing the decoded text with the transcribed one (the ground truth).

Try the above for $n=0$ to get zero-shot learning performance (no examples given) and then experiment by adding one image (1-shot), two, and so on till you hit a limit due to resources.
