# clean base image containing only comfyui, comfy-cli and comfyui-manager
FROM runpod/worker-comfyui:5.5.1-base-flux1-dev

# install custom nodes into comfyui (first node with --mode remote to fetch updated cache)
# The workflow lists only unknown_registry custom nodes and no aux_id (GitHub repo) was provided for any.
# Therefore these nodes could not be resolved automatically and are NOT installed. If you have GitHub repos
# for these packages, add RUN git clone lines like:
# RUN git clone https://github.com/<owner>/<repo> /comfyui/custom_nodes/<repo>
# Unresolved custom nodes:
# - CheckpointLoaderSimple (no aux_id provided)
# - LatentUpscale (no aux_id provided)
# - SaveLatent (no aux_id provided)
# - ConditioningSetArea (no aux_id provided)
# - ConditioningSetArea (no aux_id provided)
# - ConditioningSetArea (no aux_id provided)
# - ConditioningCombine (no aux_id provided)
# - ConditioningCombine (no aux_id provided)
# - ConditioningCombine (no aux_id provided)

# download models into comfyui

# update SSL
RUN apt-get update && \
    apt-get install -y --no-install-recommends ca-certificates && \
    update-ca-certificates && \
    rm -rf /var/lib/apt/lists/*

ENV SSL_CERT_FILE=/etc/ssl/certs/ca-certificates.crt
ENV SSL_CERT_DIR=/etc/ssl/certs

# copy all input data (like images or videos) into comfyui (uncomment and adjust if needed)
# COPY input/ /comfyui/input/
