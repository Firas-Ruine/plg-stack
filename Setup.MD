
# 🚀 Flexible PLG Stack with Docker Compose

A robust and flexible **Prometheus** + **Loki** + **Grafana** (PLG) stack for monitoring and log aggregation. This setup is designed to be easily adaptable to any project by simply changing the log path in the `.env` file. Integrated with **MinIO** for scalable object storage of logs.

---

## 🧰 Tech Stack

- 🐳 **Docker Compose** - Container orchestration
- 📈 **Prometheus** - Monitoring and alerting toolkit
- 📊 **Grafana** - Analytics & monitoring dashboards
- 📝 **Loki** - Log aggregation system
- 📦 **MinIO** - S3-compatible object storage for logs

---

## 📝 Features

- **Dynamic Configuration**: Environment variables are used for flexibility, allowing easy adaptation across projects.
- **Integrated MinIO**: MinIO acts as S3-compatible object storage for Loki's log data, ensuring scalable log retention.
- **Templated Dashboards**: Pre-configured dashboards for visualizing metrics and logs in Grafana.
- **Scalable & Resilient**: Prometheus and Loki configurations allow for long-term monitoring and logging capabilities.

---

## 🛠️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/Firas-Ruine/plg-stack
cd plg-stack
```

### 2. Configure the `.env` File

Copy the `.env.development` to `.env` and customize it according to your project:

```bash
cp .env.development .env
```

- Update the `LOG_PATH` to the location where your logs are stored.
- Customize `GRAFANA_ADMIN_USER`, `PROMETHEUS_JOB_NAME`, and `MINIO_ACCESS_KEY` as needed.


### 3. Start the Stack

Run the following command to spin up the PLG stack with MinIO:

```bash
docker-compose up -d
```

### 4. Access the Services

| Service      | URL                       | Default Credentials  |
| ------------ | ------------------------- | -------------------- |
| Prometheus   | [http://localhost:9090](http://localhost:9090) | N/A                  |
| Loki         | [http://localhost:3100](http://localhost:3100) | N/A                  |
| Grafana      | [http://localhost:3000](http://localhost:3000) | `admin` / `admin` (or as set in `.env`) |
| MinIO        | [http://localhost:9000](http://localhost:9000) | `minio` / `minio123` (or as set in `.env`) |

### 5. Set Up MinIO for Loki

1. Open [MinIO UI](http://localhost:9000).
2. Log in using the credentials from `.env`.
3. Create a new bucket named `loki-bucket` (or the bucket name you set in `.env`).

---

## 🔧 Customization

### 1. Change the Log Path

To use this setup with any project, simply update the `LOG_PATH` in the `.env` file:

```bash
LOG_PATH=/new/project/logs
```

### 2. Add New Prometheus Targets

To monitor new services with Prometheus, update the `PROMETHEUS_TARGET` in `.env`:

```bash
PROMETHEUS_TARGET=your-service:port
```

### 3. Modify Loki Retention

Control how long logs are kept by adjusting `LOKI_RETENTION` in `.env`:

```bash
LOKI_RETENTION=240h  # 10 days retention
```

---

## 🖼️ Pre-Built Dashboards

- **Grafana** comes pre-configured with data sources for Prometheus and Loki. You can easily create dashboards to visualize your metrics and logs.
- Explore and import community dashboards for various use cases.

---

## 🚀 Scaling & Extending

- **Prometheus Remote Storage**: Integrate with remote storage solutions like [Thanos](https://thanos.io/) for scalable and long-term metric storage.
- **Loki with MinIO**: Loki is configured to store logs in MinIO for persistent log storage across environments.
- **Alerting**: Configure alerts in Prometheus or Grafana for proactive monitoring of your services.

---

## 🛡️ Security

- Modify default credentials for **Grafana** and **MinIO** in the `.env` file.
- Set up **SSL/TLS** for secure communication between services.

---

## 🤝 Contributions

Feel free to submit issues, fork this repository, and open pull requests with new features or improvements!

---

Made with ❤️ by [Firas Ruine](https://github.com/Firas-Ruine)
