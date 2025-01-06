# Slim 4 API

Simple API using Slim v4 MySQL and optionnaly S3 Storage

## Installation

### Using Docker (Recommended)

1. Clone the repository:
```bash
git clone https://github.com/SachaDodane/automatisation.git
cd automatisation
```

2. Create `.env` file:
```bash
cp immo-api-php/.env.example immo-api-php/.env
```

3. Build and start the Docker containers:
```bash
docker-compose up -d
```

The API will be available at `http://localhost:8080`

### Manual Installation

1. Create `.env` from `.env.exemple`
2. Update environment variables
3. Run `php -S localhost:<PORT> -t ./public`

## Environment Variables

The following environment variables need to be set in your `.env` file:

- `DB_HOST`: Database host (default: "db" for Docker)
- `DB_USER`: Database user (default: "root")
- `DB_PASSWORD`: Database password (default: "root")
- `DB_NAME`: Database name (default: "immo_db")

## API Documentation

[Documentation to be added]

## Contributing

1. Create a new feature branch from `develop`:
```bash
git checkout -b feature/your-feature-name
```

2. Make your changes and commit them:
```bash
git commit -m "feat: your feature description"
```

3. Push your changes and create a pull request:
```bash
git push origin feature/your-feature-name
```

## License

[License information to be added]
