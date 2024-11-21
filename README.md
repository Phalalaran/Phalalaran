#!/bin/bash

# Set the service name to monitor
SERVICE_NAME="docker"

# Function to check service status
function check_service_status() {
    systemctl is-active $SERVICE_NAME
}

# Function to restart the service
function restart_service() {
    systemctl restart $SERVICE_NAME
}

# Main script logic
if ! check_service_status; then
    echo "$(date +"%Y-%m-%d %H:%M:%S") - $SERVICE_NAME service is not running. Restarting..."
    restart_service
    echo "$(date +"%Y-%m-%d %H:%M:%S") - $SERVICE_NAME service restarted."
else
    echo "$(date +"%Y-%m-%d %H:%M:%S") - $SERVICE_NAME service is running."
fi
