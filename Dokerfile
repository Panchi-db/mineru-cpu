FROM python:3.12-slim

RUN apt-get update && apt-get install -y --no-install-recommends \
    libgl1 libglib2.0-0 libgomp1 fonts-noto-core fonts-noto-cjk fontconfig curl \
  && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir -U pip \
 && pip install --no-cache-dir "mineru[core]"

ENV MINERU_DEVICE_MODE=cpu \
    MINERU_MODEL_SOURCE=huggingface \
    HF_HOME=/data/hf \
    CUDA_VISIBLE_DEVICES="" \
    OMP_NUM_THREADS=2 \
    MKL_NUM_THREADS=2 \
    OPENBLAS_NUM_THREADS=2 \
    MINERU_API_MAX_CONCURRENT_REQUESTS=1

EXPOSE 8000
CMD ["mineru-api", "--host", "0.0.0.0", "--port", "8000"]
