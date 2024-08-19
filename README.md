# Grafana Dashboards Project

This repository contains a collection of Grafana dashboards, exported as JSON files, which can be imported into any Grafana instance. These dashboards are designed to demonstrate a wide range of Grafana’s visualization capabilities using various data sources.

## Getting Started

### Prerequisites

- [Grafana](https://grafana.com/docs/grafana/latest/setup-grafana/installation/) installed on your system (locally or via Docker).
- Basic knowledge of Grafana and Git.
- Access to data sources like Prometheus, a JSON API, or Graphite, which are used in the dashboards.

### Installation

#### 1. Clone the Repository

First, clone this repository to your local machine:

```bash
git clone https://github.com/yourusername/grafana-dashboards.git
cd grafana-dashboards
```

#### 2. Set Up Data Sources in Grafana

Before importing the dashboards, you need to set up the data sources. Below are instructions for setting up Prometheus, JSON, and Graphite data sources in Grafana.

##### Setting Up Prometheus as a Data Source

1. **Install and Start Prometheus:**
   - Download Prometheus from the [official website](https://prometheus.io/download/).
   - Start Prometheus by running the following command in the Prometheus installation directory:
     ```bash
     ./prometheus --config.file=prometheus.yml
     ```
   - Prometheus should be running on `http://localhost:9090`.

2. **Add Prometheus as a Data Source in Grafana:**
   - Open Grafana (`http://localhost:3000`) and log in.
   - Go to **Configuration > Data Sources** from the left-hand sidebar.
   - Click on **Add data source** and select **Prometheus**.
   - Set the **URL** to `http://localhost:9090` and click **Save & Test**.

##### Setting Up a JSON Data Source

1. **Install SimpleJson Data Source Plugin:**
   - Run the following command to install the SimpleJson plugin:
     ```bash
     grafana-cli plugins install grafana-simple-json-datasource
     ```
   - Restart Grafana:
     ```bash
     sudo service grafana-server restart
     ```

2. **Set Up a Simple JSON API (Optional):**
   - Use a simple Flask app to serve JSON data. Refer to the project’s instructions on setting up a basic Flask app.
   
3. **Add JSON Data Source in Grafana:**
   - In Grafana, go to **Configuration > Data Sources**.
   - Click **Add data source** and select **SimpleJson**.
   - Configure the URL to your JSON API (e.g., `http://localhost:5000`), then click **Save & Test**.

##### Setting Up Graphite as a Data Source

1. **Install and Start Graphite:**
   - Install Graphite on your system:
     ```bash
     sudo apt-get install graphite-web graphite-carbon
     sudo apt-get install libapache2-mod-wsgi
     ```
   - Start the Graphite services.

2. **Add Graphite as a Data Source in Grafana:**
   - In Grafana, go to **Configuration > Data Sources**.
   - Click **Add data source** and select **Graphite**.
   - Set the **URL** to `http://localhost:8080` and click **Save & Test**.

#### 3. Import Dashboards into Grafana

Once the data sources are configured:

1. Go to **Dashboards > Manage** in Grafana.
2. Click **Import**.
3. Upload the JSON files from the `dashboards/` directory of this repository.
4. Assign the correct data source for each imported dashboard.

### Dashboard Descriptions

- **dashboard1.json**: Visualizes real-time metrics from Prometheus, including CPU usage, memory consumption, and network statistics.
- **dashboard2.json**: Uses the JSON data source to display custom metrics from a simple API, including sample data points and trends.
- **dashboard3.json**: Displays historical data trends using Graphite as the data source, including system uptime and application performance.

### Contributing

Contributions are welcome! To contribute:

1. Fork this repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes or add new dashboards.
4. Commit your changes (`git commit -m "Add new dashboard"`).
5. Push to your branch (`git push origin feature-branch`).
6. Submit a pull request.

### License

This project is licensed under the MIT License - see the `LICENSE.md` file for details.

## Additional Enhancements

### Automate Dashboard Exports (Optional)

You can automate the process of exporting dashboards by creating a script that exports the dashboards as JSON files and commits them to the repository on a scheduled basis.

### Version Control for Dashboards

Implement version control practices by tagging releases or using branches to manage different versions of dashboards. This ensures that changes are tracked and can be rolled back if necessary.

---

By following these steps, you'll be able to set up and manage Grafana dashboards effectively, visualizing data from various sources and leveraging Git for collaboration and version control.