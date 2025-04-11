<h1>This is an attempt to use the ROCM packages for AMD video cards and linux. I am not an expert and this is what I did to get it to work.</h1>
<h2>If you don't have ROCM installed already:</h2>

```bash
git clone https://github.com/CerealNumberer/DiffRhythm-ROCM
cd DiffRhythm-ROCM

## espeak-ng
# For Debian-like distribution (e.g. Ubuntu, Mint, etc.)
sudo apt-get install espeak-ng

python3 -m venv venv
source ./venv/bin/activate

## install requirements
pip install -r requirements.txt

pip uninstall torch torchvision torchaudio
```
<h2>Then go to:</h2>
<h2><a href="https://pytorch.org/get-started/locally/">https://pytorch.org/get-started/locally/</a></h2>
<h2>Grab the installation prompt for your setup. Stable version suggested.</h2>
<h2>Then run it (my example):</h2> 
    
```bash
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/rocm6.2.4
```

<h2>Next install pytorch-triton-rocm==3.1.0 (It doesn't like 3.2 for some reason):</h2>

```bash
pip uninstall triton
pip install --pre --no-deps --force-reinstall pytorch-triton-rocm==3.1.0 --index-url https://download.pytorch.org/whl/nightly/rocm6.3
```
<h2>It should now run when you use: </h2>

```bash
#There is an issue running the infer_promp_ref.sh
bash scripts/infer_wav_ref.sh
```

<h1>Configuration</h1>

<p>The scripts/infer_wav_ref.sh and scripts/infer_prompt_ref.sh files contain the settings for 95 or 285 second generations. Stick with 285 as the 95 is having issues with attention.</p>
<p>They also contain the reference audio file, and the text timestamps & lyrics </p>
<p>infer.py contains the <bold>STEPS</bold> and <bold>CFG</bold></p>

<br>
<h1>Credit to:</h1>
<a href="https://huggingface.co/ASLP-lab/DiffRhythm">DiffRhythm Official Repo</a> </a>
