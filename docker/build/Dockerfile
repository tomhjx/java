# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.185.0/containers/java/.devcontainer/base.Dockerfile
FROM mcr.microsoft.com/vscode/devcontainers/java:16

# openjdk 8
RUN set -eux; \
	\
	arch="$(dpkg --print-architecture)"; \
	case "$arch" in \
		'amd64') \
			downloadUrl='https://github.com/AdoptOpenJDK/openjdk8-upstream-binaries/releases/download/jdk8u302-b08/OpenJDK8U-jdk_x64_linux_8u302b08.tar.gz'; \
			;; \
		'arm64') \
			downloadUrl='https://github.com/AdoptOpenJDK/openjdk8-upstream-binaries/releases/download/jdk8u302-b08/OpenJDK8U-jdk_aarch64_linux_8u302b08.tar.gz'; \
			;; \
		*) echo >&2 "error: unsupported architecture: '$arch'"; exit 1 ;; \
	esac; \
	\
	wget --progress=dot:giga -O openjdk.tgz "$downloadUrl"; \
	\
    jdk8home="/usr/local/openjdk-8"; \
	mkdir -p "$jdk8home"; \
	tar --extract \
		--file openjdk.tgz \
		--directory "$jdk8home" \
		--strip-components 1 \
		--no-same-owner \
    ; \
	rm openjdk.tgz*;
    
# [Optional] Install Maven or Gradle
ARG INSTALL_MAVEN="true"
ARG MAVEN_VERSION=3.6.2
ARG INSTALL_GRADLE="true"
ARG GRADLE_VERSION=5.4.1
RUN if [ "${INSTALL_MAVEN}" = "true" ]; then su vscode -c "source /usr/local/sdkman/bin/sdkman-init.sh && sdk install maven \"${MAVEN_VERSION}\""; fi \
    && if [ "${INSTALL_GRADLE}" = "true" ]; then su vscode -c "source /usr/local/sdkman/bin/sdkman-init.sh && sdk install gradle \"${GRADLE_VERSION}\""; fi

# [Optional] Install a version of Node.js using nvm for front end dev
ARG INSTALL_NODE="true"
ARG NODE_VERSION="lts/*"
RUN if [ "${INSTALL_NODE}" = "true" ]; then su vscode -c "source /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi


COPY settings.xml ${MAVEN_HOME}/conf/settings.xml