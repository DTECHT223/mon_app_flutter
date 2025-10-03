# Dockerfile Gitpod pour Flutter

FROM gitpod/workspace-full

USER gitpod

# Installer les dépendances système pour Flutter
RUN sudo apt-get update && \
    sudo apt-get install -y curl git unzip xz-utils zip libglu1-mesa

# Installer Flutter
ENV FLUTTER_VERSION=3.22.0
RUN curl -O https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_${FLUTTER_VERSION}-stable.tar.xz && \
    tar xf flutter_linux_${FLUTTER_VERSION}-stable.tar.xz && \
    rm flutter_linux_${FLUTTER_VERSION}-stable.tar.xz && \
    sudo mv flutter /opt/flutter

ENV PATH="/opt/flutter/bin:${PATH}"

# Vérifier l'installation
RUN flutter --version

# Accepter la licence Android (optionnel, si l'app utilise Android)
RUN yes | flutter doctor --android-licenses || true

# Préparer le cache pub
RUN flutter pub cache repair || true

# Fin de configuration
