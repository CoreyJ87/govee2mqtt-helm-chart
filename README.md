# Govee2MQTT Helm Chart

This Helm chart deploys [govee2mqtt](https://github.com/wez/govee2mqtt) - a bridge that connects Govee smart home devices to MQTT.

## Features

- Connects Govee devices to MQTT broker
- Supports both API and LAN discovery
- Configurable via environment variables
- Kubernetes-native deployment

## Prerequisites

- Kubernetes cluster
- MQTT broker (like Mosquitto)
- Govee API key

## Installation

```bash
# Install the chart
helm install govee2mqtt ./govee2mqtt-helm-chart

# Install with custom values
helm install govee2mqtt ./govee2mqtt-helm-chart -f custom-values.yaml
```

## Configuration

Key configuration values:

| Parameter | Description | Default |
|-----------|-------------|---------|
| `env.GOVEE_EMAIL` | Govee account email | `""` |
| `env.GOVEE_PASSWORD` | Govee account password | `""` |
| `env.GOVEE_API_KEY` | Govee API key | `""` |
| `env.GOVEE_MQTT_HOST` | MQTT broker host | `mosquitto.mosquitto.svc.cluster.local` |
| `env.GOVEE_MQTT_PORT` | MQTT broker port | `1883` |
| `env.GOVEE_MQTT_USER` | MQTT username | `""` |
| `env.GOVEE_MQTT_PASSWORD` | MQTT password | `""` |

## Getting Govee API Key

1. Open the Govee App
2. Tap "Profile" (bottom right)  
3. Tap "About Us"
4. Tap "Apply for API Key"
5. Get the API key via email

## Usage

After deployment, govee2mqtt will:
1. Connect to your Govee account
2. Discover your Govee devices
3. Bridge them to MQTT topics
4. Publish device states and accept commands via MQTT

## Uninstalling

```bash
helm uninstall govee2mqtt
``` 