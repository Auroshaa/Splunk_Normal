# 🚀 Splunk + Universal Forwarder (Docker Compose)
This project sets up a local Splunk Enterprise instance along with a Universal Forwarder using Docker Compose.  
The Universal Forwarder monitors a sample log file and forwards it to Splunk for indexing.

---

## 📁 Project Structure
- |----docker-compose.yml
- |----.env
- |----logs/
- |----app.log.

---

## ⚙️ Prerequisites

- [Docker](https://www.docker.com/products/docker-desktop)
- [Docker Compose](https://docs.docker.com/compose/)
- `.env` file with your Splunk admin password

---

## Installation

To deploy the Splunk environment, follow these steps:

1. Ensure you have Docker and Docker Compose installed on your system.
2. Clone the repository or copy the `docker-compose.yml` file to your local machine.
3. Create a `.env` file in the same directory as the `docker-compose.yml` file and add the following environment variable:
   ```
   SPLUNK_PASSWORD=<your_splunk_password>
   ```
   Replace `<your_splunk_password>` with a secure password of your choice.
4. Run the following command to start the Splunk environment:
   ```bash
   docker-compose up -d
   ```
   This will start the Splunk and Splunk Universal Forwarder containers.

## Usage

After the containers are running, you can access the Splunk Web UI by opening a web browser and navigating to `http://localhost:8000`. Use the following credentials to log in:
- Username: `admin`
- Password: The value you set for `SPLUNK_PASSWORD` in the `.env` file.

The Splunk Universal Forwarder container will monitor the `./logs/app.log` file and forward the logs to the Splunk container.

## API

The Splunk environment provides the following API endpoints:

- Splunk Web UI: `http://localhost:8000`
- Splunk Indexer port (TCP): `9997`

You can use these endpoints to interact with the Splunk environment programmatically or through the Splunk Web UI.

## 🔍 Search for Logs

After logging into the Splunk Web UI:
- Go to Search & Reporting.
- Use the following search to view logs:
```
index=main
```
- You should see entries from logs/app.log forwarded by the Universal Forwarder.

##  🛑 Stopping the Stack
To stop the containers:
```bash
docker-compose down
```
To stop and remove volumes (start clean):
```bash
docker-compose down -v
```

## Contributing

If you would like to contribute to this project, please follow these steps:

1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and commit them.
4. Push your changes to your forked repository.
5. Submit a pull request to the main repository.

## License

This project is licensed under the [MIT License](LICENSE).

## Testing

To test the Splunk environment, you can use the following steps:

1. Start the Splunk environment using the `docker-compose up -d` command.
2. Verify that the Splunk and Splunk Universal Forwarder containers are running using the `docker ps` command.
3. Check the Splunk Web UI at `http://localhost:8000` and ensure that you can log in with the correct credentials.
4. Verify that the `./logs/app.log` file is being monitored and the logs are being forwarded to the Splunk container.