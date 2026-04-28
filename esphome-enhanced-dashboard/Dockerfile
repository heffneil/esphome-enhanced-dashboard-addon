ARG BUILD_FROM=ghcr.io/esphome/esphome-hassio:2026.4.3
FROM ${BUILD_FROM}

# Overlay enhanced dashboard files on top of the official ESPHome add-on image.
# Keeps all the HA-specific bits (nginx ingress, s6-overlay, discovery, bashio) intact.
COPY overlays/const.py            /esphome/esphome/dashboard/const.py
COPY overlays/core.py             /esphome/esphome/dashboard/core.py
COPY overlays/models.py           /esphome/esphome/dashboard/models.py
COPY overlays/web_server.py       /esphome/esphome/dashboard/web_server.py
COPY overlays/status/ping.py      /esphome/esphome/dashboard/status/ping.py
COPY overlays/templates/          /esphome/esphome/dashboard/templates/

ARG BUILD_ARCH
ARG BUILD_VERSION
LABEL \
    io.hass.name="ESPHome Enhanced Dashboard" \
    io.hass.description="Modern dashboard overlay for ESPHome with search, tags, archive, and batch actions" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version="${BUILD_VERSION}" \
    maintainer="heffneil" \
    org.opencontainers.image.title="ESPHome Enhanced Dashboard (HA Add-on)" \
    org.opencontainers.image.source="https://github.com/heffneil/esphome-enhanced-dashboard-addon"
