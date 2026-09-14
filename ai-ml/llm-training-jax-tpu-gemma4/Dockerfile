# Copyright 2026 Google LLC
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM us-docker.pkg.dev/cloud-tpu-images/jax-ai-image/tpu:jax0.7.2-rev1
RUN apt-get update && apt-get install -y wget && rm -rf /var/lib/apt/lists/*

RUN pip install --upgrade pip
RUN pip install "gemma>=4.0.0" grain sentencepiece dialog bagz
RUN pip uninstall -y tensorflow tensorflow-cpu tf-keras keras && rm -rf /opt/venv/lib/python3.12/site-packages/tensorflow*
RUN pip install --no-cache-dir tensorflow-cpu==2.18.0
RUN pip install --no-cache-dir --upgrade "ml_dtypes>=0.5.1"

WORKDIR /app

# Copy your training script into the container
COPY Gemma4LLMTrain.py .
