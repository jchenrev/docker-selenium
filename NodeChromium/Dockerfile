# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# NOTE: DO *NOT* EDIT THIS FILE.  IT IS GENERATED.
# PLEASE UPDATE Dockerfile.txt INSTEAD OF THIS FILE
# !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
FROM selenium/node-base:3.141.59-20210422
LABEL authors=SeleniumHQ

USER root

#============================================
# Chromium
#============================================
RUN  wget http://snapshot.debian.org/archive/debian/20210111T000000Z/pool/main/c/chromium/chromium_87.0.4280.88-0.4~deb10u1_arm64.deb \
  && wget http://snapshot.debian.org/archive/debian/20210111T000000Z/pool/main/c/chromium/chromium-common_87.0.4280.88-0.4~deb10u1_arm64.deb \
  && wget http://snapshot.debian.org/archive/debian/20210111T000000Z/pool/main/c/chromium/chromium-driver_87.0.4280.88-0.4~deb10u1_arm64.deb \
  && apt-get -qqy update \
  && apt-get -qqy install \
    ./chromium_87.0.4280.88-0.4~deb10u1_arm64.deb \
    ./chromium-common_87.0.4280.88-0.4~deb10u1_arm64.deb \
    ./chromium-driver_87.0.4280.88-0.4~deb10u1_arm64.deb \
  && rm \
    ./chromium_87.0.4280.88-0.4~deb10u1_arm64.deb \
    ./chromium-common_87.0.4280.88-0.4~deb10u1_arm64.deb \
    ./chromium-driver_87.0.4280.88-0.4~deb10u1_arm64.deb \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*

#=================================
# Chromium Launch Script Wrapper
#=================================
COPY wrap_chromium_binary /opt/bin/wrap_chromium_binary
RUN /opt/bin/wrap_chromium_binary

USER 1200

COPY generate_config /opt/bin/generate_config

# Generating a default config during build time
RUN /opt/bin/generate_config > /opt/selenium/config.json
