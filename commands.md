# commands.md

## context

sed -i.bak "s|http://127\.0\.0\.1:5000/|/api/|g" react-frontend/src/services/todoService.ts

## Docker

docker compose -f docker-compose.dev.yml down

docker compose -f docker-compose.dev.yml up --build

docker compose -f docker-compose.dev.yml logs -f

